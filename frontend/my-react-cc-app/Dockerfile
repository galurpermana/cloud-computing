# frontend/my-react-app/Dockerfile
# Build image berbasis NodeJS 14 Alpine
FROM node:14-alpine

# Membuat direktori kerja di dalam container
WORKDIR /app

# Copy file package.json ke dalam container
COPY package*.json ./

# Install package yang dibutuhkan dengan npm
RUN npm install

# Copy semua file di direktori saat ini ke dalam container
COPY . .

# Build untuk production menggunakan Vite
RUN npm run build

# Gunakan Nginx untuk serve static file
FROM nginx:stable-alpine
COPY --from=0 /app/dist /usr/share/nginx/html

# Membuka port 80 untuk akses dari luar
EXPOSE 80
# Menjalankan Nginx dengan perintah daemon off
CMD ["nginx", "-g", "daemon off;"]
