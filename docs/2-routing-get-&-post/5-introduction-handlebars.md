---
sidebar_position: 5
---

# 5. Introduction Handlebars

**Express Handlebars** biasa disebut juga HBS, adalah package node js yang memudahkan setiap web developer untuk mengirim data dari backend (server) ke frontend (client). Oleh karena itu maka kita perlu menginstall package HBS melalui npm dengan command berikut 

```shell
npm install hbs
```
atau
```shell
npm i hbs
```

**Cara kerja dari HBS** adalah seluruh `logika (function)` yang ingin ditampilkan di halaman web dibungkus dalam sebuah object json. Kemudian HBS tinggal memanggil data tersebut dengan kurung kurawal seperti berikut 

```handlebars
{{your-data}}
```

## Alasan Menggunakan Handlebars

1. Pemisahan File Logika dan Tampilan
   Membuat project menggunakan template handlebars memungkinkan kita untuk memisahkan logika berbasis kode dari tampilan sebenarnya, sehingga membantu kita untuk mengikuti pattern View/Controller

2. Clean Code & Maintainable
   Hal ini berkaitan dengan point pertama, dimana ketika code kita sudah terpisah antara logika dengan tampilan maka pada saat melakukan update akan lebih mudah untuk dilakukan.


## Refactor File HTML Menjadi File HBS
   Pada study case kali ini dan seterusnya, kita akan menggunakan Handlebars sebagai template engine view, sehingga seluruh tampilan pada chapter 1 berekstensi `.html` akan kita refactor menjadi berekstensikan `.hbs` dan akan kita simpan kedalam folder `views`.

   File - file html yang akan kita refactor meliputi :
   - index
   - form-blog
   - contact
   - blog
   - blog-detail

Akses hasil refactor file HTML menjadi HBS pada file index, contact, blog, dan blog detail pada button berikut
   <a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day1-2.navbar">
   Full code
   </a>

   <br />   
   
