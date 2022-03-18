---
sidebar_position: 6
---

# 6. Routing for Home

import useBaseUrl from '@docusaurus/useBaseUrl';

**Routing** adalah sebuah metode yang menggambarkan bagaimana aplikasi melakukan respon terhadap request dari client pada endpoint tertentu. **End point** adalah alamat uri atau path yang diakses oleh client. End point tersebut akan diakses dengan metode request tertentu seperti : `GET. POST, PUT ,DELETE` ataupun yang lainnya

Pertama kita akan mencoba membuat routing untuk tampilan home menggunakan metode GET. **Metode GET** adalah metode yang digunakan untuk mengirim request data dari suatu resource.

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day2-1.routing-home">
Contoh code
</a>

<br />
<br />

```js {2,6-7,13-16,23-26} title="index.js"
const express = require('express')
const path = require("path");

const app = express()

app.set('view engine', 'hbs');
app.set("views", path.join(__dirname, "../views"));

app.get('/', function (req, res) {
  res.send("Hello World")
})

app.get('/home', function (req, res) {
  setHeader(res)
  res.render('index')
})

const port = 5000
app.listen(port, function () {
  console.debug(`Server running on port ${port}`)
})

function setHeader(res) {
  res.setHeader("Content-Type", "text/html");
  res.setHeader("Cache-Control", "s-max-age=1, stale-while-revalidate");
}
```
<img alt="image1" src={useBaseUrl('img/docs/image-2-0.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-2-git-day2-1rout-10f41e-demo-dumbways.vercel.app/home">
Demo
</a>
</div>
<br />

ketika membuat routing, ada dua parameter yang dibutuhkan yakni `endpoint` yang akan diakses dan sebuah function untuk menerima request dan mengirim kan response. Menampilkan sebuah view melalui response, kita bisa menggunakan metode `render`.

Karna kita menggunakan styling external pada views yang tersimpan di folder `public`, maka kita perlu menambahkan code berikut yang bertujuan untuk memberitahu ke package express bahwasanya ada folder lain yang harus dirender pada project kita.

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day2-2.add-public-folder">
Contoh code
</a>

<br />
<br />

```js {9}
const express = require('express')
const path = require("path");

const app = express()

app.set('view engine', 'hbs');
app.set("views", path.join(__dirname, "../views"));

app.use("/public", express.static(path.join(__dirname, "../public"))); 

app.get('/', function (req, res) {
  res.send("Hello World")
})

app.get('/home', function (req, res) {
  setHeader(res)
  res.render('index')
})

const port = 5000
app.listen(port, function () {
  console.debug(`Server running on port ${port}`)
})

function setHeader(res) {
  res.setHeader("Content-Type", "text/html");
  res.setHeader("Cache-Control", "s-max-age=1, stale-while-revalidate");
}
```

<img alt="image1" src={useBaseUrl('img/docs/image-2-1.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-2-git-day2-2add-068004-demo-dumbways.vercel.app/home">
Demo
</a>
</div>
