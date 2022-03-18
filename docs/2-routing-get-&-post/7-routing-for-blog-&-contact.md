---
sidebar_position: 7
---

# 7. Routing for Blog & Contact Me (Challange)

import useBaseUrl from '@docusaurus/useBaseUrl';


Membuat routing untuk halaman blog & contact me sama saja seperti yang kita lakukan pada routing home. Kita akan menggunakan metode GET.

<br />

<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day2-3.challenge">
Contoh code
</a>

<br />
<br />

```js {20-28} title="index.js"
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

app.get('/blog', function (req, res) {
    setHeader(res)
    res.render('blog')
})

app.get('/contact-me', function (req, res) {
    setHeader(res)
    res.render('contact')
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

<img alt="image1" src={useBaseUrl('img/docs/image-2-2.png')} height="500px"/>

<br />
<br />

<div>
<a class="btn-demo" href="https://ebook-code-result-chapter-2-git-day2-3challenge-demo-dumbways.vercel.app/blog">
Demo
</a>
</div>