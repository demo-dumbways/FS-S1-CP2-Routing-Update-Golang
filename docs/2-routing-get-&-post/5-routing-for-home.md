---
sidebar_position: 5
---

# 5. Routing for Home

import useBaseUrl from '@docusaurus/useBaseUrl';

**Routing** adalah sebuah metode yang menggambarkan bagaimana aplikasi melakukan respon terhadap request dari client pada endpoint tertentu. **End point** adalah alamat uri atau path yang diakses oleh client. End point tersebut akan diakses dengan metode request tertentu seperti : `GET. POST, PUT ,DELETE` ataupun yang lainnya

Pertama kita akan mencoba membuat routing untuk tampilan home menggunakan metode GET. **Metode GET** adalah metode yang digunakan untuk mengirim request data dari suatu resource.

<br />

<a class="btn-example-code" href="">
Contoh code
</a>

<br />
<br />

```go {10-12,18,30-42} title="main.go"
package main

import (
    "fmt"
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
```
<img alt="image1" src={useBaseUrl('img/docs/image-2-0.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="">
Demo
</a>
</div>
<br />

ketika membuat routing, ada dua parameter yang dibutuhkan yakni `endpoint` yang akan diakses dan sebuah function untuk menerima request dan mengirim kan response. Menampilkan sebuah view melalui response, kita bisa menggunakan metode `Execute`.

Karna kita menggunakan styling external pada views yang tersimpan di folder `public`, maka kita perlu menambahkan code berikut yang bertujuan untuk memberitahu ke package express bahwasanya ada folder lain yang harus dirender pada project kita.

<br />

<a class="btn-example-code" href="">
Contoh code
</a>

<br />
<br />

```go {5} title="main.go"
// this code same like above
func main() {
	route := mux.NewRouter()

	route.PathPrefix("/public/").Handler(http.StripPrefix("/public/", http.FileServer(http.Dir("./public/"))))

	route.HandleFunc("/", helloWorld).Methods("GET")
	route.HandleFunc("/home", home).Methods("GET").Name("home")

	fmt.Println("Server running on port 5000")
	http.ListenAndServe("localhost:5000", route)
}
```

<img alt="image1" src={useBaseUrl('img/docs/image-2-1.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="">
Demo
</a>
</div>
