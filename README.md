
# Panduan Instalasi Flask

## Prasyarat

Pastikan Python 3.6+ terinstal di sistem Anda.

Anda dapat memeriksa versi Python dengan menjalankan:
```bash
python --version
```

Jika Python belum terinstal, Anda dapat mengunduh dan menginstalnya dari situs web resmi Python: https://www.python.org/downloads/

## Langkah Instalasi

1. **Siapkan virtual environment (disarankan tapi opsional)**:
   Sangat disarankan untuk menginstal Flask dalam virtual environment agar terhindar dari konflik dengan paket Python lainnya.

   Untuk membuat virtual environment:
   ```bash
   python -m venv venv
   ```

2. **Aktifkan virtual environment**:
   - Pada Windows:
     ```bash
     venv\Scripts\activate
     ```
   - Pada MacOS/Linux:
     ```bash
     source venv/bin/activate
     ```

3. **Instal Flask**:
   Setelah virtual environment aktif, instal Flask menggunakan pip:
   ```bash
   pip install Flask
   ```

4. **Verifikasi Instalasi**:
   Untuk memverifikasi Flask terinstal dengan benar, Anda dapat membuat aplikasi sederhana "Hello, World!". Buat file `app.py` dengan konten berikut:

   ```python
   from flask import Flask
   app = Flask(__name__)

   @app.route('/')
   def hello_world():
       return 'Hello, World!'

   if __name__ == '__main__':
       app.run(debug=True)
   ```

   Jalankan aplikasi:
   ```bash
   python app.py
   ```

   Buka browser dan buka `http://127.0.0.1:5000/` untuk melihat hasilnya.

## Penanganan Error saat Instalasi

Saat menginstal Flask, Anda mungkin akan menemui beberapa masalah umum. Berikut adalah solusi untuk mengatasi masalah tersebut:

### 1. **Error: `pip: command not found`**
   - Error ini terjadi jika pip belum terinstal. Untuk mengatasi masalah ini, unduh dan instal pip dengan mengikuti panduan resmi: https://pip.pypa.io/en/stable/installation/.

### 2. **Error: `Permission denied`**
   - Jika Anda mendapatkan error izin saat menginstal Flask, Anda bisa mencoba menjalankan perintah instalasi dengan hak akses yang lebih tinggi:
     - Pada Linux/MacOS:
       ```bash
       sudo pip install Flask
       ```
     - Pada Windows, jalankan Command Prompt sebagai Administrator.

### 3. **Error: `ModuleNotFoundError: No module named 'flask'`**
   - Error ini berarti Flask belum terinstal di lingkungan Anda. Pastikan Anda sudah mengaktifkan virtual environment jika menggunakan satu.
   - Jalankan kembali perintah instalasi:
     ```bash
     pip install Flask
     ```

### 4. **Error: `Flask module version is incompatible`**
   - Jika Anda memiliki versi Flask yang lebih lama, perbarui Flask dengan menjalankan:
     ```bash
     pip install --upgrade Flask
     ```

### 5. **Masalah Virtual Environment**
   - Jika Anda mengalami masalah saat mengaktifkan virtual environment, pastikan Anda berada di direktori yang benar tempat `venv` berada. Untuk pemecahan masalah lebih lanjut, periksa versi Python dan pastikan file `Scripts/activate` ada.

&nbsp;
---
# 🚀 Instalasi React + Vite


## 🛠️ Prasyarat
Pastikan **Node.js** sudah terinstal di sistem Anda. Cek versi Node.js dan npm dengan perintah:

```bash
node -v
npm -v
```

Jika belum terinstal, unduh dari [nodejs.org](https://nodejs.org/).

## 📦 Membuat Proyek React dengan Vite

1. Jalankan perintah berikut untuk membuat proyek baru:

```bash
npm create vite@latest nama-proyek --template react
```

Atau jika menggunakan **yarn**:

```bash
yarn create vite nama-proyek --template react
```

Atau jika menggunakan **pnpm**:

```bash
pnpm create vite nama-proyek --template react
```

2. Masuk ke direktori proyek:

```bash
cd nama-proyek
```

3. Instal dependensi proyek:

```bash
# Dengan npm
npm install

# Dengan yarn
yarn

# Dengan pnpm
pnpm install
```

## ▶️ Menjalankan Proyek

Jalankan server:

```bash
# Dengan npm
npm run dev

# Dengan yarn
yarn dev

# Dengan pnpm
pnpm dev
```

Akses aplikasi di browser di [http://localhost:5173](http://localhost:5173).


# 🖥️ Integrasi Flask & React

## 🔗 Integrasi Backend (Flask) dengan Frontend (React)

### 1️⃣ Pastikan Backend Flask Berjalan
Backend Flask harus berjalan di `http://localhost:5000` agar bisa diakses oleh frontend React.

🔹 Jalankan Flask:
   ```sh
   python app.py
   ```

🔹 Aktifkan CORS dalam `app.py` untuk memungkinkan komunikasi antara domain berbeda:
   ```python
   from flask_cors import CORS
   CORS(app)
   ```

### 2️⃣ Fetch Data di React ⚛️
React akan mengambil data dari Flask API menggunakan `fetch` dalam `useEffect`.

```jsx
import React, { useState, useEffect } from 'react';

function App() {
  const [apiData, setApiData] = useState(null);

  useEffect(() => {
    fetch('http://localhost:5000/api/data')
      .then(response => response.json())
      .then(data => {
        setApiData(data.data);
      })
      .catch(error => console.error(error));
  }, []);

  return (
    <div style={{ textAlign: 'center', marginTop: '50px' }}>
      <h1>⚛️ React & Flask Integration 🔥</h1>
      <p>{apiData ? apiData : "Loading data..."}</p>
    </div>
  );
}

export default App;
```

### 3️⃣ Menjalankan Aplikasi 🚀
1. 🔥 Jalankan Flask:
   ```sh
   python app.py
   ```
2. ⚛️ Jalankan React:
   ```sh
   npm run dev
   ```
3. 🌐 Akses aplikasi di browser: `http://localhost:5713/`

### 4️⃣ Catatan Tambahan 📝
✅ Pastikan backend berjalan di `http://localhost:5000` agar bisa diakses oleh frontend.
✅ Gunakan `flask-cors` untuk menghindari masalah CORS.
✅ Jika terjadi error, pastikan backend sudah berjalan sebelum menjalankan frontend.


