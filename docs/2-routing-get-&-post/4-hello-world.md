---
sidebar_position: 4
---

# 4. Hello World using Node.Js

import useBaseUrl from '@docusaurus/useBaseUrl';

Setelah adanya file entry point, maka kita bisa melakukan segala proses logika menggunakan file ini. Hal pertama yang akan kita lakukan adalah mengirimkan string `Hello World` kedalam tampilan browser menggunakan Node.js

Mengirimkan sesuati kedalam tampilan browser membutuhkan sebuah `endpoint` yang nantinya akan diakses. **Endpoint** adalah jalur komunikasi yang bisa diakses untuk menampilkan sesuatu sesuai dengan yang dikirimkan.

<br/>
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day1-6.set-endpoint">
Contoh code
</a>
<br/>
<br/>

```js {5-7} title="index.js"
const express = require('express');

const app = express();

app.get('/', function (req, res) {
  res.send('Hello World');
});

const port = 5000;
app.listen(port, function () {
  console.debug(`Server running on port ${port}`);
});
```

<img alt="image1" src={useBaseUrl('img/docs/image-1-1.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-2-git-day1-6set-c414f6-demo-dumbways.vercel.app/">
Demo
</a>
</div>
<br />

untuk mengakses pada browser, maka ketikkan url berikut

```
http://localhost:5000/
```
