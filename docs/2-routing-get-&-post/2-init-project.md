---
sidebar_position: 2
---

# 2. Introduction Golang using Gorilla/Mux

Hal pertama yang kita lakukan untuk bekerja dengan Golang adalah membuat file `go.mod` untuk proyek yang dijalankan. Membuat file ini kita bisa memanfaatkan `Go Modules`. **Go Modules** merupakan manajemen dependensi resmi untuk Go. Modules ini diperkenalkan pertama kali di `go1.11` yang telah terinstall secara langsung ketika menginstall Golang.

Modules digunakan untuk menginisialisasi sebuah project, sekaligus melakukan manajemen terhadap 3rd party atau library lain yang dipergunakan. 
:::info
Modules atau Module di sini merupakan istilah untuk project
:::

Membuat sebuah project menggunakan NPM bisa dilakukan dengan command berikut

```shell
go mod init nama-project
```

Untuk nama project, umumnya adalah disamakan dengan nama direktori, tapi bisa saja sebenarnya menggunakan nama yang lain.

:::info
Nama project dan Nama module merupakan istilah yang sama
:::

Eksekusi perintah go mod init menghasilkan satu buah file baru bernama go.mod. File ini digunakan oleh Go toolchain untuk menandai bahwa folder di mana file tersebut berada adalah folder project. Jadi jangan di hapus ya file tersebut.

<br/>

Setelah melakukan init project dan mengisikan metadatanya, kita akan menginstal salah satu framework dari Golang yakni `Gorilla/Mux`. 
**Package gorilla/mux** adalah` HTTP router` dan `URL matcher` yang memiliki fitur tambahan dibandingkan standard library Golang. Menginstall gorilla/mux juga dilakukan menggunakan CLI dengan command berikut:

```shell
go get -u github.com/gorilla/mux
```
<br/>

Berikut fitur-fitur penting dari gorilla/mux:

1. Mengimplementasikan HTTP.Handler interface, compatible dengan standard HTTP.ServeMux.
2. Requests matching berdasarkanURL host, path, path prefix, schemes, header dan query values, HTTP methods atau menggunakan custom matchers.
3. Support regular expression.
4. Support subrouters