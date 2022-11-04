---
sidebar_position: 7
---

# 7. Conditional Rendering

import useBaseUrl from '@docusaurus/useBaseUrl';

**Conditional rendering** dapat menentukan sebuah komponen atau tag html dirender atau tidak pada kondisi tertentu. Pada case ini kita akan membuat conditional rendering untuk button `add new blog, edit,` dan `delete` yang ada pada tampilan blog berdasarkan apakah pengunjung sudah login atau belum.

Maka langkah pertama yang kita lakukan adalah mengirimkan data terkait kondisi telah login atau belum melalui `response` route blog.

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2-golang/blob/day2-6-conditional-rendering/main.go">
Contoh code
</a>

<br />
<br />

```go {15} title="main.go"
// this code same like before
package main

import (
    "fmt"
    "html/template"
    "net/http"


    "github.com/gorilla/mux"
)

var Data = map[string]interface{}{
    "Title": "Personal Web",
    "IsLogin": false,
}

func main() {
    route := mux.NewRouter()

    route.PathPrefix("/public/").Handler(http.StripPrefix("/public/", http.FileServer(http.Dir("./public/"))))

    route.HandleFunc("/", helloWorld).Methods("GET")
    route.HandleFunc("/home", home).Methods("GET")
    route.HandleFunc("/blog", blogs).Methods("GET")
    route.HandleFunc("/contact-me", contactMe).Methods("GET")

    fmt.Println("Server running on port 5000")
    http.ListenAndServe("localhost:5000", route)
}
// continuation this code same like before
```

selanjutnya kita akan melakukan pengecakan pada view blog terkait kondisi yang telah dikirimkan secara bersamaan ketika mengirimkan response.

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2-golang/blob/day2-6-conditional-rendering/views/blog.html">
Contoh code
</a>

<br />
<br />

```html {37,41,48,53} title="blog.html"
<html>

<head>
  <title>Creating Blog Page</title>
  <link rel="stylesheet" href="/public/style.css" />
  <!-- linking boostrap css cdn  -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
</head>

<body>
  <!-- NavBar -->
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-lg">
      <a class="navbar-brand me-5" href="/home">
        <img src="/public/assets/logo.png" alt="logo" />
      </a>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link" href="/home">Home</a>
          </li>
          <li class="nav-item">
            <a href="/blog" class="nav-link list-active">Blog</a>
          </li>
        </ul>
      </div>
      <div class="d-flex contact-me">
        <a href="/contact-me">Contact Me</a>
      </div>
    </div>
  </nav>

  <!-- Blog list -->
  <div id="contents" class="blog-list">
    <!-- conditional post blog -->
    {{if .IsLogin}}
    <div class="button-group w-100">
      <a href="/add-blog" class="btn-post">Add New Blog</a>
    </div>
    {{end}}
    <!-- dynamic content would be here -->
    <div class="blog-list-item">
      <div class="blog-image">
        <img src="/public/assets/blog-img.png" alt="Pasar Coding di Indonesia Dinilai Masih Menjanjikan" />
      </div>
      <div class="blog-content">
        {{if .IsLogin}}
        <div class="button-group">
          <a class="btn-edit">Edit Post</button>
            <a class="btn-post">Delete Blog</a>
        </div>
        {{end}}
        <h1>
          <a href="/blog/1" target="_blank">
            Pasar Coding di Indonesia Dinilai Masih Menjanjikan
          </a>
        </h1>
        <div class="detail-blog-content">
          12 Jul 2021 22:30 WIB | Ichsan Emrald Alamsyah
        </div>
        <p>
          Ketimpangan sumber daya manusia (SDM) di sektor digital masih
          menjadi isu yang belum terpecahkan. Berdasarkan penelitian
          ManpowerGroup, ketimpangan SDM global, termasuk Indonesia,
          meningkat dua kali lipat dalam satu dekade terakhir. Lorem ipsum,
          dolor sit amet consectetur adipisicing elit. Quam, molestiae
          numquam! Deleniti maiores expedita eaque deserunt quaerat! Dicta,
          eligendi debitis?
        </p>
      </div>
    </div>
  </div>
</body>

</html>
```

<img alt="image1" src={useBaseUrl('img/docs/image-2-4.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="">
Demo
</a>
</div>
