---
sidebar_position: 9
---

# 9. Query String for Blog Detail

import useBaseUrl from '@docusaurus/useBaseUrl';

Nama route yang kita gunakan untuk menghandle proses menampilkan blog detail yaitu `/blog`, kemudian diikuti `/:index` agar kita dapat menangkap index yang dikirim melalui route/url. Mengambil index yang dikirim, kita gunakan req.params.index, jadi index tersebut tersimpan didalam req.params.

Sementara untuk saat ini kita akan mengirimkan response dalam bentuk konten statis

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day2-4.query-string">
Contoh code
</a>

<br />
<br />

```js {7-29} title="index.js"
//this code below endpoint /blog
app.get('/blog', function (req, res) {
  setHeader(res)
  res.render('blog', {isLogin: isLogin})
})

app.get('/blog/:id', function (req, res) {
  // get selected blog id with params
  const blogId = req.params.id

  setHeader(res)

  // render blog-detail page and send data to view
  res.render('blog-detail', {
    blog: {
      id: blogId,
      title: 'Pasar Coding di Indonesia Dinilai Masih Menjanjikan',
      post_date: '12 Jul 2021 22:30 WIB',
      author: 'Ichsan Emrald Alamsyah',
      content: `Ketimpangan sumber daya manusia (SDM) di sektor digital masih
                menjadi isu yang belum terpecahkan. Berdasarkan penelitian
                ManpowerGroup, ketimpangan SDM global, termasuk Indonesia,
                meningkat dua kali lipat dalam satu dekade terakhir. Lorem ipsum,
                dolor sit amet consectetur adipisicing elit. Quam, molestiae
                numquam! Deleniti maiores expedita eaque deserunt quaerat! Dicta,
                eligendi debitis?`
    }
  })
})

app.get('/contact-me', function (req, res) {
  setHeader(res)
  res.render('contact')
})
```

Response yang dikirimkan bukan hanya sekedar view saja, namun bisa juga mengirimkan data yang dibungkus kedalam object. Data yang dikirimkan melalui response ini bisa kita gunakan pada view yang dituju, dalam case ini view tersebut adalah blog detail.

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/blob/day2-4.query-string/views/blog-detail.hbs">
Contoh code
</a>

<br />
<br />

```html {32-39} title="blog-detail.hbs"
<html>
  <head>
    <title>Creating Blog Page - detail</title>
    <link rel="stylesheet" href="/public/style.css" />
    <!-- linking boostrap css cdn  -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
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
          <a href="/contact"> Contact Me </a>
        </div>
      </div>
    </nav>

    <!-- Blog -->
    <div class="blog-detail">
      <div class="blog-detail-container">
        <h1>{{blog.title}}</h1>
        <div class="author">{{blog.post_date}} | {{blog.author}}</div>
        <img src="/public/assets/blog-img-detail.png" alt="detail" />
        <p>{{blog.content}}</p>
      </div>
    </div>
  </body>
</html>
```

<img alt="image1" src={useBaseUrl('img/docs/image-2-3.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-2-git-day2-4quer-6bd630-demo-dumbways.vercel.app/blog/1">
Demo
</a>
</div>