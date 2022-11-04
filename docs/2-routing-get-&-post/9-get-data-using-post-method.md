---
sidebar_position: 9
---

# 9. Get Blog Post Data

import useBaseUrl from '@docusaurus/useBaseUrl';

Pertama kita akan membuat routing untuk tampilan formulir blog menggunakan metode GET

```go {11,21-33} title="main.go"
// this code same like before
func main() {
    route := mux.NewRouter()

    route.PathPrefix("/public/").Handler(http.StripPrefix("/public/", http.FileServer(http.Dir("./public/"))))

    route.HandleFunc("/", helloWorld).Methods("GET")
    route.HandleFunc("/home", home).Methods("GET")
    route.HandleFunc("/blog", blogs).Methods("GET")
    route.HandleFunc("/blog/{id}", blogDetail).Methods("GET")
    route.HandleFunc("/add-blog", formBlog).Methods("GET")
    route.HandleFunc("/contact-me", contactMe).Methods("GET")

    fmt.Println("Server running on port 5000")
    http.ListenAndServe("localhost:5000", route)
}

// continuation this code same like before

// this code below func blogDetail(w http.ResponseWriter, r *http.Request) {
func formBlog(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html; charset=utf-8")

	var tmpl, err = template.ParseFiles("views/form-blog.html")
	if err != nil {
		w.WriteHeader(http.StatusInternalServerError)
		w.Write([]byte("message : " + err.Error()))
		return
	}

	w.WriteHeader(http.StatusOK)
	tmpl.Execute(w, Data)
}

// continuation this code same like before
```

Kali ini kita akan menggunakan method `POST`. **Method POST** adalah metode request yang didukung oleh HTTP yang digunakan oleh World Wide Web. Metode HTTP POST mengirimkan data ke server.

Hal pertama yang kita lakukan ketika akan menerima data dari client adalah menyiapkan routing endpointnya

```go {12} title="main.go"
// this code same like before
func main() {
    route := mux.NewRouter()

    route.PathPrefix("/public/").Handler(http.StripPrefix("/public/", http.FileServer(http.Dir("./public/"))))

    route.HandleFunc("/", helloWorld).Methods("GET")
    route.HandleFunc("/home", home).Methods("GET")
    route.HandleFunc("/blog", blogs).Methods("GET")
    route.HandleFunc("/blog/{id}", blogDetail).Methods("GET")
    route.HandleFunc("/add-blog", formBlog).Methods("GET")
    route.HandleFunc("/blog", addBlog).Methods("POST")
    route.HandleFunc("/contact-me", contactMe).Methods("GET")

    fmt.Println("Server running on port 5000")
    http.ListenAndServe("localhost:5000", route)
}
// continuation this code same like before
```

Kita akan menambahkan sebuah function baru untuk menangani proses menerima data inputan dari formulir blog.

```go title="main.go"
func addBlog(w http.ResponseWriter, r *http.Request) {
}
```

selanjutnya kita akan menampilkan data yang kita terima dari formulir blog melalui request kedalam console.

```go
func addBlog(w http.ResponseWriter, r *http.Request) {
	err := r.ParseForm()
	if err != nil {
		log.Fatal(err)
	}

	fmt.Println("Title : " + r.PostForm.Get("title"))
	fmt.Println("Content : " + r.PostForm.Get("content"))

	http.Redirect(w, r, "/blog", http.StatusMovedPermanently)
}
```

Untuk mengambil data dari inputan form, kita menggunakan ` r.PostForm.Get()` diisikan dengan name inputan yang ada pada formulir. Pada formulir name inputannya adalah `title` dan `content` sehingga kita untuk menerima inputannya menggunakan code

```go
r.PostForm.Get("title")
```

dan

```go
r.PostForm.Get("content")
```

<img alt="image1" src={useBaseUrl('img/docs/image-2-5.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-2-git-day2-8post-data-demo-dumbways.vercel.app/add-blog">
Demo
</a>
</div>
