---
sidebar_position: 4
---

# 4. Hello World using Golang

import useBaseUrl from '@docusaurus/useBaseUrl';

Setelah adanya file entry point, maka kita bisa melakukan segala proses logika menggunakan file ini. Hal pertama yang akan kita lakukan adalah mengirimkan string `Hello World` kedalam tampilan browser menggunakan Golang

Mengirimkan sesuatu kedalam tampilan browser membutuhkan sebuah `endpoint` yang nantinya akan diakses. **Endpoint** adalah jalur komunikasi yang bisa diakses untuk menampilkan sesuatu sesuai dengan yang dikirimkan.

<br/>
<a class="btn-example-code" href="">
Contoh code
</a>
<br/>
<br/>

```go {11-17} title="main.go"
package main

import (
    "fmt"
    "net/http"

    "github.com/gorilla/mux"
)

func main() {
    route := mux.NewRouter()
    
    route.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
      w.Header().Set("Content-Type", "application/json")
      w.WriteHeader(http.StatusOK)
      w.Write([]byte("Hello World"))
    }).Methods("GET")

    fmt.Println("Server running on port 5000")
    http.ListenAndServe("localhost:5000", route)
}
```

:::tip saran
agar tampak rapi dalam menuliskan code, kita juga bisa memisahkan function yang dieksekusi oleh route kedalam function yang terpisah
:::

```go {13,19-24} title="main.go"
package main

import (
    "fmt"
    "net/http"

    "github.com/gorilla/mux"
)

func main() {
    route := mux.NewRouter()
    
    route.HandleFunc("/", helloWorld).Methods("GET")

    fmt.Println("Server running on port 5000")
    http.ListenAndServe("localhost:5000", route)
}

func helloWorld(w http.ResponseWriter, r *http.Request) {
	w.Header().Set("Content-Type", "application/json")
	w.WriteHeader(http.StatusOK)
	w.Write([]byte("Hello World!"))
}
```

<img alt="image1" src={useBaseUrl('img/docs/image-1-1.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="">
Demo
</a>
</div>
<br />

untuk mengakses pada browser, maka ketikkan url berikut

```
http://localhost:5000/
```
