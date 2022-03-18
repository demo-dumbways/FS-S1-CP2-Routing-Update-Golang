---
sidebar_position: 3
---

# 3. Creating Entry Point

**Entry Point** adalah file javascript yang akan dipanggil ketika project pertama kali dijalankan. File ini menyertakan logika utama dari project yang dibuat. Secara default nama file entry point adalah `index.js`.

Pada file entry point, kita akan menambahkan code untuk pemanggilan `package express` yang sudah diinstal kedalam project kita dan menginisialisasinya kedalam sebuah `variabel sebagai app` dari project kita

<br/>
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day1-4.use-express">
Contoh code
</a>
<br/>
<br/>

```js title="index.js"
const express = require('express');

const app = express();
```

setelah kita menginisialisasi app project, kita membutuhkan sebuah `port` untuk menjalankan app project. **Port** adalah mekanisme/jalur yang mengizinkan node.js membuat koneksi dalam menjalankan app project kita.

<br/>
<a class="btn-example-code" href="https://github.com/demo-dumbways/ebook-code-result-chapter-2/tree/day1-5.set-port">
Contoh code
</a>
<br/>
<br/>

```js {5-8} title="index.js"
const express = require('express');

const app = express();

const port = 5000;
app.listen(port, function () {
  console.debug(`Server running on port ${port}`);
});
```
