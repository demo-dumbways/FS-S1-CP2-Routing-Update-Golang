---
sidebar_position: 6
---

# 6. Routing for Blog & Contact Me (Challange)

import useBaseUrl from '@docusaurus/useBaseUrl';


Membuat routing untuk halaman blog & contact me sama saja seperti yang kita lakukan pada routing home. Kita akan menggunakan metode GET.

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2-golang/blob/day2-5-routing-for-blog-and-contact/main.go">
Contoh code
</a>

<br />
<br />

```go {20-21,47-73} title="main.go"
package main

import (
    "fmt"
    "html/template"
    "net/http"

    "github.com/gorilla/mux"
)

var Data = map[string]interface{}{
	"Title": "Personal Web",
}

func main() {
    route := mux.NewRouter()
    
    route.HandleFunc("/", helloWorld).Methods("GET")
    route.HandleFunc("/home", home).Methods("GET")
    route.HandleFunc("/blog", blogs).Methods("GET")
    route.HandleFunc("/contact-me", contactMe).Methods("GET")

    fmt.Println("Server running on port 5000")
    http.ListenAndServe("localhost:5000", route)
}

func helloWorld(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    w.WriteHeader(http.StatusOK)
    w.Write([]byte("Hello World!"))
}

func home(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "text/html; charset=utf-8")

    var tmpl, err = template.ParseFiles("views/index.html")
    if err != nil {
        w.WriteHeader(http.StatusInternalServerError)
        w.Write([]byte("message : " + err.Error()))
        return
    }

    w.WriteHeader(http.StatusOK)
    tmpl.Execute(w, Data)
}

func blogs(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html; charset=utf-8")

	var tmpl, err = template.ParseFiles("views/blog.html")
	if err != nil {
		w.WriteHeader(http.StatusInternalServerError)
		w.Write([]byte("message : " + err.Error()))
		return
	}

	w.WriteHeader(http.StatusOK)
	tmpl.Execute(w, Data)
}

func contactMe(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "text/html; charset=utf-8")

	var tmpl, err = template.ParseFiles("views/contact.html")
	if err != nil {
		w.WriteHeader(http.StatusInternalServerError)
		w.Write([]byte("message : " + err.Error()))
		return
	}

	w.WriteHeader(http.StatusOK)
	tmpl.Execute(w, Data)
}
```

<img alt="image1" src={useBaseUrl('img/docs/image-2-2.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="">
Demo
</a>
</div>