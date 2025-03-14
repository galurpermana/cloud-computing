# backend/Dockerfile
# Image berbasis python 3.9
FROM python:3.9-slim

# Membuat direktori kerja di dalam container
WORKDIR /app

# Copy file requirements.txt ke dalam container
COPY requirements.txt requirements.txt

# Install package yang dibutuhkan dengan pip
RUN pip install --no-cache-dir -r requirements.txt

# Copy semua file di direktori saat ini ke dalam container
COPY . .

# Membuka port 5000 untuk akses dari luar
EXPOSE 5000
# Menjalankan aplikasi dengan perintah python app.py
CMD ["python", "app.py"]

