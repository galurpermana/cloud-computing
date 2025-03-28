# 🚀 Panduan Instalasi Flask

## 🛠️ Prasyarat

Pastikan Python 3.6+ terinstal di sistem Anda.

Anda dapat memeriksa versi Python dengan menjalankan:

```bash
python --version
```

Jika Python belum terinstal, Anda dapat mengunduh dan menginstalnya dari situs web resmi Python: [python.org](https://www.python.org/downloads/)

## 📥 Langkah Instalasi

1. **🔖 Siapkan virtual environment (disarankan tapi opsional)**:
   Sangat disarankan untuk menginstal Flask dalam virtual environment agar terhindar dari konflik dengan paket Python lainnya.

   Untuk membuat virtual environment:

   ```bash
   python -m venv venv
   ```

2. **🔌 Aktifkan virtual environment**:

   - Pada Windows:
     ```bash
     venv\Scripts\activate
     ```
   - Pada MacOS/Linux:
     ```bash
     source venv/bin/activate
     ```

3. **📦 Instal Flask**:
   Setelah virtual environment aktif, instal Flask menggunakan pip:

   ```bash
   pip install Flask
   ```

4. **🔍 Verifikasi Instalasi**:
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

## 🛡️ Penanganan Error saat Instalasi

Saat menginstal Flask, Anda mungkin akan menemui beberapa masalah umum. Berikut adalah solusi untuk mengatasi masalah tersebut:

### 1. **⚠️ Error: `pip: command not found`**

- Error ini terjadi jika pip belum terinstal. Untuk mengatasi masalah ini, unduh dan instal pip dengan mengikuti panduan resmi: [pip.pypa.io](https://pip.pypa.io/en/stable/installation/).

### 2. **🔒 Error: `Permission denied`**

- Jika Anda mendapatkan error izin saat menginstal Flask, Anda bisa mencoba menjalankan perintah instalasi dengan hak akses yang lebih tinggi:
  - Pada Linux/MacOS:
    ```bash
    sudo pip install Flask
    ```
  - Pada Windows, jalankan Command Prompt sebagai Administrator.

### 3. **❌ Error: `ModuleNotFoundError: No module named 'flask'`**

- Error ini berarti Flask belum terinstal di lingkungan Anda. Pastikan Anda sudah mengaktifkan virtual environment jika menggunakan satu.
- Jalankan kembali perintah instalasi:
  ```bash
  pip install Flask
  ```

### 4. **🔄 Error: `Flask module version is incompatible`**

- Jika Anda memiliki versi Flask yang lebih lama, perbarui Flask dengan menjalankan:
  ```bash
  pip install --upgrade Flask
  ```

### 5. **🔧 Masalah Virtual Environment**

- Jika Anda mengalami masalah saat mengaktifkan virtual environment, pastikan Anda berada di direktori yang benar tempat `venv` berada. Untuk pemecahan masalah lebih lanjut, periksa versi Python dan pastikan file `Scripts/activate` ada.

## &nbsp;

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
import React, { useState, useEffect } from "react";

function App() {
  const [apiData, setApiData] = useState(null);

  useEffect(() => {
    fetch("http://localhost:5000/api/data")
      .then((response) => response.json())
      .then((data) => {
        setApiData(data.data);
      })
      .catch((error) => console.error(error));
  }, []);

  return (
    <div style={{ textAlign: "center", marginTop: "50px" }}>
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

## &nbsp;

# 🐘 Koneksi PostgreSQL & Operasi CRUD dengan Flask

## 🔌 Setup Koneksi Database

```python
import psycopg2

def get_db_connection():
    conn = psycopg2.connect(
        host="localhost",
        database="test_db",
        user="student",
        password="password"
    )
    return conn
```

## 🔄 Operasi CRUD

### ➕ Create (POST)

```python
@app.route('/api/items', methods=['POST'])
def create_item():
    data = request.json
    name = data['name']
    description = data['description']

    conn = get_db_connection()
    cur = conn.cursor()
    cur.execute("INSERT INTO items (name, description) VALUES (%s, %s) RETURNING id;",
                (name, description))
    new_id = cur.fetchone()[0]
    conn.commit()
    cur.close()
    conn.close()

    return jsonify({"id": new_id, "name": name, "description": description}), 201
```

### 📖 Read (GET)

```python
@app.route('/api/items', methods=['GET'])
def get_items():
    conn = get_db_connection()
    cur = conn.cursor()
    cur.execute("SELECT id, name, description FROM items;")
    rows = cur.fetchall()
    cur.close()
    conn.close()

    items = [{"id": row[0], "name": row[1], "description": row[2]} for row in rows]
    return jsonify(items)
```

### 📝 Update (PUT)

```python
@app.route('/api/items/<int:id>', methods=['PUT'])
def update_item(id):
    data = request.json
    name = data['name']
    description = data['description']

    conn = get_db_connection()
    cur = conn.cursor()
    cur.execute("UPDATE items SET name = %s, description = %s WHERE id = %s RETURNING id;",
                (name, description, id))

    if cur.rowcount == 0:
        cur.close()
        conn.close()
        return jsonify({"error": "Item tidak ditemukan"}), 404

    conn.commit()
    cur.close()
    conn.close()

    return jsonify({"id": id, "name": name, "description": description})
```

### ❌ Delete (DELETE)

```python
@app.route('/api/items/<int:id>', methods=['DELETE'])
def delete_item(id):
    conn = get_db_connection()
    cur = conn.cursor()

    cur.execute("SELECT id FROM items WHERE id = %s;", (id,))
    if cur.fetchone() is None:
        cur.close()
        conn.close()
        return jsonify({"error": "Item tidak ditemukan"}), 404

    cur.execute("DELETE FROM items WHERE id = %s;", (id,))
    conn.commit()
    cur.close()
    conn.close()

    return jsonify({"message": f"Item dengan id {id} telah dihapus"}), 200
```

## 🧪 Pengujian di Postman

### 🔍 Request GET

- URL: `http://localhost:5000/api/items`
- Method: GET

### ➕ Request POST

- URL: `http://localhost:5000/api/items`
- Method: POST
- Body (raw JSON):
  ```json
  {
    "name": "Item Baru",
    "description": "Ini adalah item baru"
  }
  ```

### 📝 Request PUT

- URL: `http://localhost:5000/api/items/1`
- Method: PUT
- Body (raw JSON):
  ```json
  {
    "name": "Item Diupdate",
    "description": "Item ini telah diperbarui"
  }
  ```

### ❌ Request DELETE

- URL: `http://localhost:5000/api/items/1`
- Method: DELETE

## 📊 Struktur Tabel Database

```sql
CREATE TABLE items (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT
);
```

&nbsp;
---
# 🐳 Dokumentasi Deployment Docker Untuk Flask

## 🔍 Prasyarat
- Docker Desktop terinstal pada sistem 
- Kode aplikasi Flask dalam direktori `backend`

## 🚀 Proses Deployment

### 1️⃣ Verifikasi Lingkungan Docker
Sebelum memulai, pastikan Docker Desktop berjalan dengan baik:

```bash
docker info
```

Jika Docker tidak berjalan, Anda akan melihat pesan error berikut:
```
Server:
ERROR: error during connect: Get "http://%2F%2F.%2Fpipe%2FdockerDesktopLinuxEngine/v1.47/info": open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.
```

#### ✅ Memulai Docker Desktop
1. Buka aplikasi Docker Desktop
2. Tunggu hingga Anda melihat status "Docker is running"

### 2️⃣ Konfigurasi Proyek

#### 📄 Membuat Dockerfile
Buat file `Dockerfile` di folder `backend` dengan konten berikut:

```dockerfile
# backend/Dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5000
CMD ["python", "app.py"]
```

#### 📦 Menyiapkan Dependensi
Buat atau perbarui file `requirements.txt` dengan dependensi yang diperlukan:

```
flask
flask-cors
psycopg2-binary
```

### 3️⃣ Membangun dan Menjalankan

#### 🏗️ Membangun Image Docker
Navigasi ke direktori backend dan bangun image Docker:

```bash
cd backend
docker build -t flask-backend:1.0 .
```

#### 🚢 Menjalankan Container
Luncurkan container Docker dari image yang sudah dibuat:

```bash
docker run -d -p 5000:5000 --name flask-container flask-backend:1.0
```

Penjelasan parameter:
- `-d`: Jalankan dalam mode detached (background)
- `-p 5000:5000`: Memetakan port 5000 dari container ke port 5000 pada host
- `--name flask-container`: Memberikan nama pada container
- `flask-backend:1.0`: Image yang akan digunakan

### 4️⃣ Verifikasi

#### 🌐 Pengujian Browser
Buka browser web Anda dan akses:
**http://localhost:5000**

Anda seharusnya melihat aplikasi Flask Anda berjalan dengan sukses.

## 🔧 Perintah Umum

### Manajemen Container
```bash
# Melihat daftar container yang sedang berjalan
docker ps

# Menghentikan container
docker stop flask-container

# Memulai container yang sudah ada
docker start flask-container

# Menghapus container
docker rm flask-container
```

### Manajemen Image
```bash
# Melihat daftar semua image
docker images

# Menghapus image
docker rmi flask-backend:1.0
```

### Log dan Debugging
```bash
# Melihat log container
docker logs flask-container

# Masuk ke shell container
docker exec -it flask-container bash
```

## 📝 Pemecahan Masalah

### Container gagal dijalankan
Periksa log untuk melihat error:
```bash
docker logs flask-container
```

### Konflik port
Jika port 5000 sudah digunakan, ubah pemetaan port:
```bash
docker run -d -p 8080:5000 --name flask-container flask-backend:1.0
```
Kemudian akses aplikasi Anda di **http://localhost:8080**

&nbsp;
---

 # 🐳 Dokumentasi Deployment Docker Untuk React

## 📋 Prasyarat
- Docker Desktop telah terinstal
- Aplikasi React.js (menggunakan Vite)
- Node.js dan npm terinstal


### 1️⃣ Persiapan Awal

- 🚀 Cara memulai Docker Desktop:
  1. Buka aplikasi Docker Desktop
  2. Tunggu hingga status "Docker is running" muncul

### 2️⃣ Membuat Dockerfile
- 📄 Buat file bernama `Dockerfile` di folder `frontend/my-react-app` dengan konten:

```dockerfile
# frontend/my-react-app/Dockerfile
FROM node:14-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Build untuk production menggunakan Vite
RUN npm run build

# Gunakan Nginx untuk serve static file
FROM nginx:stable-alpine
COPY --from=0 /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

### 3️⃣ Build Docker Image
- ⚙️ Sebelum membangun image Docker, buat folder build terlebih dahulu:

```bash
npm run build
```

- 🏗️ Bangun image Docker dengan perintah:

```bash
cd frontend/my-react-app
docker build -t react-frontend-vite:1.0 .
```

### 4️⃣ Menjalankan Docker Container
- 🚢 Jalankan container Docker dengan perintah:

```bash
docker run -d -p 3000:80 --name react-container-vite react-frontend-vite:1.0
```

### 5️⃣ Verifikasi Aplikasi
- 🌐 Buka browser dan akses **http://localhost:3000** untuk memastikan aplikasi berjalan dengan baik

## ❗ Penanganan Error

### 1. Docker Desktop Tidak Berjalan
- **Error**: `ERROR: error during connect...`
- **Solusi**: 
  1. Pastikan Docker Desktop sudah diinstal dengan benar
  2. Jalankan Docker Desktop dari menu aplikasi
  3. Periksa status Docker dengan perintah `docker info`

### 2. Error saat Build Image
- **Error**: `npm ERR! code ENOENT`
- **Solusi**:
  1. Pastikan berada di direktori yang benar (`frontend/my-react-app`)
  2. Periksa apakah file `package.json` ada
  3. Jalankan `npm install` sebelum build

### 3. Port Sudah Digunakan
- **Error**: `Error response from daemon: driver failed programming external connectivity on endpoint react-container-vite: Bind for 0.0.0.0:3000 failed: port is already allocated`
- **Solusi**:
  1. Periksa port yang sudah digunakan dengan `docker ps`
  2. Hentikan container yang menggunakan port tersebut: `docker stop [CONTAINER_ID]`
  3. Atau gunakan port lain, misal: `docker run -d -p 3001:80 --name react-container-vite react-frontend-vite:1.0`

### 4. Error Nginx Configuration
- **Error**: Halaman "502 Bad Gateway" saat mengakses aplikasi
- **Solusi**:
  1. Periksa log container: `docker logs react-container-vite`
  2. Pastikan build Vite menghasilkan file di folder `/dist`
  3. Jika folder output berbeda, sesuaikan path pada Dockerfile

## 🔍 Perintah - perintah Docker 
- Melihat container yang berjalan: `docker ps`
- Menghentikan container: `docker stop react-container-vite`
- Menghapus container: `docker rm react-container-vite`
- Melihat daftar image: `docker images`
- Menghapus image: `docker rmi react-frontend-vite:1.0`


&nbsp;
=
# 🐳 Integrasi Full Stack dengan Docker Compose

## 📂 Struktur Proyek
```
cloud-project/
│
├── backend/
│   └── app.py
│
├── frontend/
│   └── my-react-cc-app/
│       └── src/
│           └── App.jsx
│
├── docker-compose.yml
└── init.sql
```

## 🛠️ Konfigurasi Docker Compose

### Membuat `docker-compose.yml`
```yaml
version: '3.7'
services:
  backend:
    build: 
      context: ./backend
    container_name: flask_container
    ports:
      - "5000:5000"
    depends_on:
      - db
    environment:
      - DB_HOST=db
      - DB_NAME=test_db
      - DB_USER=student
      - DB_PASSWORD=password

  frontend:
    build:
      context: ./frontend/my-react-app
    container_name: react_container
    ports:
      - "3000:80"
    depends_on:
      - backend

  db:
    image: postgres:12-alpine
    container_name: postgres_container
    environment:
      - POSTGRES_DB=test_db
      - POSTGRES_USER=student
      - POSTGRES_PASSWORD=password
    ports:
      - "5432:5432"
    volumes:
      - db_data:/var/lib/postgresql/data
      - ./init.sql:/docker-entrypoint-initdb.d/init.sql

volumes:
  db_data:
```

### Membuat `init.sql`
```sql
CREATE TABLE IF NOT EXISTS items (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT
);

INSERT INTO items (name, description) VALUES
('Test Item', 'This is a test description'),
('Test Item 2', 'This is a test description 2');
```

## 🚀 Menjalankan Proyek

### Membangun dan Menjalankan Container
```bash
# Membangun dan menjalankan container
docker compose up -d --build

# Melihat log
docker compose logs -f
```

## 🔍 Verifikasi Integrasi
1. Buka `http://localhost:3000` untuk memverifikasi frontend React
2. Pastikan React dapat berkomunikasi dengan backend Flask
3. Periksa persistensi data di PostgreSQL

