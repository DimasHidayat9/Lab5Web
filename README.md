# Laporan Praktikum 5 – JavaScript

Pada praktikum ini saya membuat sebuah form pendaftaran sederhana dengan menggunakan HTML, CSS, dan JavaScript.
Form tersebut memiliki tiga input, yaitu Nama, Email, dan Umur, yang akan divalidasi menggunakan fungsi JavaScript sebelum data dikirim.

- Validasi ini bertujuan untuk memastikan:

- Semua kolom wajib diisi.

- Email yang dimasukkan sesuai format.

Umur minimal 17 tahun.

Jika ada kesalahan, sistem akan menampilkan pesan peringatan (alert).
Jika semua benar, sistem akan menampilkan pesan sukses.

# Code
```
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Validasi Form - Praktikum 5</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      font-family: "Poppins", Arial, sans-serif;
      background: linear-gradient(135deg, #6e8efb, #a777e3);
      height: 100vh;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .form-container {
      background: #fff;
      padding: 30px 40px;
      border-radius: 15px;
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
      width: 380px;
      text-align: center;
      animation: fadeIn 0.8s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h2 {
      color: #444;
      margin-bottom: 20px;
    }

    label {
      display: block;
      text-align: left;
      margin-top: 10px;
      font-weight: 500;
      color: #555;
    }

    input {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 8px;
      transition: border-color 0.3s;
    }

    input:focus {
      border-color: #6e8efb;
      outline: none;
    }

    button {
      margin-top: 20px;
      width: 100%;
      background: linear-gradient(90deg, #6e8efb, #a777e3);
      color: white;
      border: none;
      padding: 12px;
      font-size: 16px;
      border-radius: 8px;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    }

    .footer {
      margin-top: 15px;
      font-size: 12px;
      color: #888;
    }
  </style>
</head>
<body>

  <div class="form-container">
    <h2>Form Validasi Data</h2>
    <form onsubmit="return validasiForm()">
      <label for="nama">Nama Lengkap</label>
      <input type="text" id="nama" placeholder="Masukkan nama lengkap">

      <label for="email">Email</label>
      <input type="text" id="email" placeholder="contoh@email.com">

      <label for="umur">Umur</label>
      <input type="number" id="umur" placeholder="Masukkan umur">

      <button type="submit">Kirim Data</button>
    </form>

    <div class="footer">
      © 2025 | Praktikum 5 - JavaScript | Universitas Pelita Bangsa
    </div>
  </div>

  <script>
    function validasiForm() {
      let nama = document.getElementById("nama").value.trim();
      let email = document.getElementById("email").value.trim();
      let umur = document.getElementById("umur").value.trim();

      if (nama === "" || email === "" || umur === "") {
        alert("⚠️ Semua field harus diisi!");
        return false;
      }

      let polaEmail = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (!email.match(polaEmail)) {
        alert("📧 Format email tidak valid!");
        return false;
      }

      if (umur < 17) {
        alert("👶 Umur minimal 17 tahun!");
        return false;
      }

      alert("✅ Data berhasil dikirim!");
      return true;
    }
  </script>

</body>
</html>
```
# Output
<img width="1914" height="1010" alt="Cuplikan layar 2025-10-20 191349" src="https://github.com/user-attachments/assets/2df58128-1aee-44d2-b98b-c32f1529564d" />

# Struktur dan Penjelasan Kode
# 1. Bagian `<head>`

Bagian ini berisi:

- Informasi meta dan judul halaman.

- Elemen `<style>` untuk mendesain tampilan form agar lebih menarik dan responsif.
```
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Validasi Form - Praktikum 5</title>
  <style>
    /* CSS di sini */
  </style>
</head>
```
Penjelasan:

- `meta charset="UTF-8"` memastikan teks bisa menampilkan karakter bahasa Indonesia dengan benar.

- `meta viewport` membuat tampilan menyesuaikan ukuran layar (responsif).

- `<style>` digunakan untuk menulis kode CSS langsung dalam file HTML.

# 2. Bagian CSS (Desain Tampilan)

Kode CSS digunakan untuk mengatur posisi, warna, dan gaya form agar terlihat menarik.
```
body {
  font-family: "Poppins", Arial, sans-serif;
  background: linear-gradient(135deg, #6e8efb, #a777e3);
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
```
# Penjelasan:

- `display: flex` dengan `justify-content: center` dan `align-items: center` membuat form berada tepat di tengah layar.

- `linear-gradient` memberikan efek gradasi warna biru ke ungu pada background.

- `height: 100vh` memastikan tinggi halaman menyesuaikan tinggi layar penuh.

Form utama dibungkus oleh div dengan class `.form-container`, yang diberi padding, radius, dan efek bayangan agar tampak modern:
```
.form-container {
  background: #fff;
  padding: 30px 40px;
  border-radius: 15px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
  width: 380px;
  text-align: center;
}
```
# Efek tambahan:

- Efek animasi `fadeIn` membuat form muncul perlahan saat halaman dibuka.

- Tombol dibuat dengan gradasi warna dan efek hover agar interaktif.

# 3. Bagian `<body>`

Bagian ini menampilkan konten utama halaman, yaitu form validasi.
```
<body>
  <div class="form-container">
    <h2>Form Validasi Data</h2>
    <form onsubmit="return validasiForm()">
      <label for="nama">Nama Lengkap</label>
      <input type="text" id="nama" placeholder="Masukkan nama lengkap">

      <label for="email">Email</label>
      <input type="text" id="email" placeholder="contoh@email.com">

      <label for="umur">Umur</label>
      <input type="number" id="umur" placeholder="Masukkan umur">

      <button type="submit">Kirim Data</button>
    </form>
    <div class="footer">
      © 2025 | Praktikum 5 - JavaScript | Universitas Pelita Bangsa
    </div>
  </div>
</body>
```
# Penjelasan:

- `onsubmit="return validasiForm()"` adalah event handler yang akan memanggil fungsi JavaScript validasiForm() setiap kali tombol submit diklik.

- Setiap input memiliki id unik (`nama`, `email`, `umur`) agar bisa diakses oleh JavaScript.

- Elemen `<button>` digunakan untuk mengirim data setelah validasi berhasil.

# 4. Bagian JavaScript

Bagian JavaScript berfungsi sebagai logika utama untuk memvalidasi data sebelum dikirim.
```
<script>
  function validasiForm() {
    let nama = document.getElementById("nama").value.trim();
    let email = document.getElementById("email").value.trim();
    let umur = document.getElementById("umur").value.trim();

    if (nama === "" || email === "" || umur === "") {
      alert("⚠️ Semua field harus diisi!");
      return false;
    }

    let polaEmail = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
    if (!email.match(polaEmail)) {
      alert("📧 Format email tidak valid!");
      return false;
    }

    if (umur < 17) {
      alert("👶 Umur minimal 17 tahun!");
      return false;
    }

    alert("✅ Data berhasil dikirim!");
    return true;
  }
</script>
```
# Penjelasan:

1. Mengambil nilai input

- `document.getElementById("nama").value` mengambil data dari form.

- `.trim()` digunakan untuk menghapus spasi berlebih.

2. Validasi kosong
```
if (nama === "" || email === "" || umur === "") {
    alert("Semua field harus diisi!");
    return false;
}
```
Jika ada kolom kosong, tampil peringatan dan form tidak dikirim.

3. Validasi format email
```
let polaEmail = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
if (!email.match(polaEmail)) {
    alert("Format email tidak valid!");
    return false;
}
```
Email dicek dengan pola sederhana agar memiliki karakter `@` dan domain.

4. Validasi umur
```
if (umur < 17) {
    alert("Umur minimal 17 tahun!");
    return false;
}
```
5. Pesan sukses
```
alert("Data berhasil dikirim!");
return true;
```
Jika semua validasi benar, form akan menampilkan pesan “✅ Data berhasil dikirim!” dan data bisa diproses lebih lanjut.

# - Alert jika umur kurang dari 17
<img width="1919" height="1007" alt="image" src="https://github.com/user-attachments/assets/c224a2d7-a1dd-4f85-9cc3-6ce79d29197f" />
Jika umur dibawah 17 tahun, maka muncul "Umur minimal 17 tahun!"

# - Alert jika field kosong
<img width="1918" height="1011" alt="image" src="https://github.com/user-attachments/assets/7250831f-03eb-4a53-95fb-5498795bb93e" />
Jika salah satu input kosong, maka muncul pesan "Semua field harus diisi!"

# - Jika pesan sukses
<img width="1919" height="1009" alt="image" src="https://github.com/user-attachments/assets/a9d2e521-726c-47cc-a6f6-e84c4cbada51" />
Jika semua benar, maka muncul "Data berhasil dikirm!"



