---
sidebar_position: 2
---

# 2. Introduction Node.Js using Express JS

Hal pertama yang kita lakukan untuk bekerja dengan Node JS adalah membuat file `package.json` untuk proyek yang dijalankan. Membuat file ini kita bisa memanfaatkan `Node Package Manager (NPM)`. **Node Package Manager** adalah merupakan pengelola package untuk JavaScript yang dapat memudahkan kita dalam mengelola package yang telah terinstall secara langsung ketika menginstall Node.Js.

Membuat sebuah project menggunakan NPM bisa dilakukan dengan command berikut

```shell
npm init
```

ketika menjalankan command diatas maka nantinya kita akan diminta mengisikan metadata project yang dibuat, metadata yang diisikan antara lain
- Nama Project
- Versi
- Deskripsi
- Entry Point
- Test Command
- Repository Git
- Keyword
- Lisensi
- Dependensi
- devDependensi

Setelah melakukan init project dan mengisikan metadatanya, kita akan menginstal salah satu framework dari Node.JS yakni `express js`. 
**Express JS** adalah framework dari NodeJS yang dirancang secara fleksibel dan sederhana untuk membantu tahap pengembangan aplikasi back end. Menginstall express js juga dilakukan menggunakan NPM dengan command berikut:

```shell
npm install express
```
atau
```shell
npm i express
```