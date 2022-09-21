---
sidebar_position: 3
---

# 3. Creating Entry Point

**Entry Point** adalah file golang yang akan dipanggil ketika project pertama kali dijalankan. File ini menyertakan logika utama dari project yang dibuat. Secara default nama file entry point adalah `main.go`.

Pada file entry point, kita akan menambahkan code untuk pemanggilan/import `package gorilla/mux` yang sudah diinstal kedalam project kita.

<br/>
<a class="btn-example-code" href="">
Contoh code
</a>
<br/>
<br/>

```go title="main.go"
package main

import (
	"github.com/gorilla/mux"
)
```

setelah kita import package gorilla/mux, kita membutuhkan sebuah `port` untuk menjalankan project. **Port** adalah mekanisme/jalur yang mengizinkan Golang membuat koneksi dalam menjalankan project kita. Dalam proses pembuatan port ini dan seluruh logic project, kita akan menyimpannya kedalam sebuah `function` default yang diberi nama `main`

<br/>
<a class="btn-example-code" href="">
Contoh code
</a>
<br/>
<br/>

```go {4-5,10-13} title="main.go"
package main

import (
	"fmt"
	"net/http"

	"github.com/gorilla/mux"
)

func main() {
	fmt.Println("Server running on port 5000")
	http.ListenAndServe("localhost:5000", route)
}
```

package `fmt` dan `http` merupakan package default dari Golang, sehingga tidak perlu untuk diinstal seperti gorilla/mux. **fmt** merupakan sebuah package golang yang berfungsi untuk melakukan format I/O atau disebut juga input output. Sedangkan **http** adalah package golang yang berfungsi untuk menyediakan implementasi klien dan server HTTP.

