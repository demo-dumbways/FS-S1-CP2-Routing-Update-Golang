---
sidebar_position: 10
---

# 10. Get Blog Post Data

import useBaseUrl from '@docusaurus/useBaseUrl';

Pertama kita akan membuat routing untuk tampilan formulir blog menggunakan metode GET

```js
app.get('/add-blog', function (req, res) {
  setHeader(res)
  res.render("form-blog")
})
```

Kali ini kita akan menggunakan method `POST`. **Method POST** adalah metode request yang didukung oleh HTTP yang digunakan oleh World Wide Web. Metode HTTP POST mengirimkan data ke server. 

Hal pertama yang kita lakukan ketika akan menerima data dari client adalah menambahkan code berikut dengan tujuan agar inputan yang kita terima diubah terlebih dahulu oleh express yang awalnya berupa `JSON Object` menjadi `string` atau `array`

```js
app.use(express.urlencoded({ extended: false }))
```

Kita akan menambahkan sebuah route baru untuk menangani proses menerima data inputan dari formulir blog. Tentunya metode yang digunakan pada route ini adalah post.

```js
app.post('/blog', (req, res) => {
})
```

selanjutnya kita akan menampilkan data yang kita terima dari formulir blog melalui request kedalam console.

```js
app.post('/blog', (req, res) => {
  res.send(`<script>alert('title : ${req.body.title}, content : ${req.body.content}')</script>`)
})
```

Untuk mengambil data dari inputan form, kita menggunakan `req.body` dilanjutkan dengan name inputan yang ada pada formulir. Pada formulir name inputannya adalah `title` dan `content` sehingga kita untuk menerima inputannya menggunakan code 

```
req.body.title
```

dan

```
req.body.content
``` 

<img alt="image1" src={useBaseUrl('img/docs/image-2-5.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-2-git-day2-8post-data-demo-dumbways.vercel.app/add-blog">
Demo
</a>
</div>