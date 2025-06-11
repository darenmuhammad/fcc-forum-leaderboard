# 📘 Async, Await, dan Try...Catch di JavaScript

JavaScript menyediakan cara penanganan kode asynchronous (kode yang berjalan tidak langsung selesai) menggunakan `async`, `await`, dan `try...catch`. Ini membuat kode asynchronous lebih mudah dibaca dibandingkan dengan callback atau `.then()`.


## 🔁 Async

Kata kunci `async` digunakan untuk mendefinisikan sebuah **fungsi asynchronous**. Fungsi ini secara otomatis akan mengembalikan **Promise**.

```javascript
async function fetchData() {
  return "Data berhasil diambil!";
}

fetchData().then(console.log); // Output: Data berhasil diambil!
```


## ⏳ Await

`await` hanya bisa digunakan di dalam fungsi yang diberi `async`. Ini akan **menunggu Promise diselesaikan** (fulfilled/rejected) sebelum melanjutkan ke baris berikutnya.

```javascript
async function getUser() {
  const response = await fetch("https://api.example.com/user");
  const data = await response.json();
  console.log(data);
}
```

Tanpa `await`, kita harus menggunakan `.then()`, yang bisa membuat kode berlapis-lapis dan sulit dibaca.


## 🫯 Try...Catch

Blok `try...catch` digunakan untuk **menangkap error** dalam eksekusi kode, termasuk error dari operasi asynchronous saat menggunakan `await`.

```javascript
async function getUser() {
  try {
    const response = await fetch("https://api.example.com/user");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Terjadi error:", error.message);
  }
}
```

Tanpa `try...catch`, jika terjadi error (misalnya koneksi gagal), aplikasi bisa crash atau tidak memberikan feedback yang baik ke pengguna.

---

## ✅ Ringkasan

| Konsep        | Fungsi                                                          |
| ------------- | --------------------------------------------------------------- |
| `async`       | Membuat fungsi asynchronous yang mengembalikan Promise.         |
| `await`       | Menunggu hasil Promise sebelum melanjutkan eksekusi.            |
| `try...catch` | Menangani error secara elegan, terutama dalam kode async/await. |