# Bookshelf-API
# Bookshelf API

Bookshelf API adalah aplikasi backend sederhana untuk mengelola daftar buku menggunakan Hapi.js.

## Fitur

1. **Menambahkan Buku**
   - Endpoint: `POST /books`
   - Request Body:
     ```json
     {
       "name": "Nama Buku",
       "year": 2024,
       "author": "Nama Penulis",
       "summary": "Ringkasan Buku",
       "publisher": "Nama Penerbit",
       "pageCount": 350,
       "readPage": 100,
       "reading": true
     }
     ```
   - Response (Success):
     ```json
     {
       "status": "success",
       "message": "Buku berhasil ditambahkan",
       "data": {
         "bookId": "nanoid"
       }
     }
     ```
   - Response (Failure - Nama tidak diisi):
     ```json
     {
       "status": "fail",
       "message": "Gagal menambahkan buku. Mohon isi nama buku"
     }
     ```
   - Response (Failure - readPage > pageCount):
     ```json
     {
       "status": "fail",
       "message": "Gagal menambahkan buku. readPage tidak boleh lebih besar dari pageCount"
     }
     ```

2. **Mendapatkan Semua Buku**
   - Endpoint: `GET /books`
   - Query Parameters:
     - `name`: Filter berdasarkan nama buku
     - `reading`: Filter berdasarkan status membaca (`1` untuk sedang membaca, `0` untuk tidak)
     - `finished`: Filter berdasarkan status selesai membaca (`1` untuk selesai, `0` untuk belum selesai)
   - Response:
     ```json
     {
       "status": "success",
       "data": {
         "books": [
           {
             "id": "nanoid",
             "name": "Nama Buku",
             "publisher": "Nama Penerbit"
           }
         ]
       }
     }
     ```

3. **Mendapatkan Detail Buku**
   - Endpoint: `GET /books/{bookId}`
   - Response (Success):
     ```json
     {
       "status": "success",
       "data": {
         "book": {
           "id": "nanoid",
           "name": "Nama Buku",
           "year": 2024,
           "author": "Nama Penulis",
           "summary": "Ringkasan Buku",
           "publisher": "Nama Penerbit",
           "pageCount": 350,
           "readPage": 100,
           "finished": false,
           "reading": true,
           "insertedAt": "timestamp",
           "updatedAt": "timestamp"
         }
       }
     }
     ```
   - Response (Failure - Buku tidak ditemukan):
     ```json
     {
       "status": "fail",
       "message": "Buku tidak ditemukan"
     }
     ```

4. **Memperbarui Buku**
   - Endpoint: `PUT /books/{bookId}`
   - Request Body: Sama seperti `POST /books`
   - Response (Success):
     ```json
     {
       "status": "success",
       "message": "Buku berhasil diperbarui"
     }
     ```
   - Response (Failure - Id tidak ditemukan):
     ```json
     {
       "status": "fail",
       "message": "Gagal memperbarui buku. Id tidak ditemukan"
     }
     ```
   - Response (Failure - Nama tidak diisi):
     ```json
     {
       "status": "fail",
       "message": "Gagal memperbarui buku. Mohon isi nama buku"
     }
     ```
   - Response (Failure - readPage > pageCount):
     ```json
     {
       "status": "fail",
       "message": "Gagal memperbarui buku. readPage tidak boleh lebih besar dari pageCount"
     }
     ```

5. **Menghapus Buku**
   - Endpoint: `DELETE /books/{bookId}`
   - Response (Success):
     ```json
     {
       "status": "success",
       "message": "Buku berhasil dihapus"
     }
     ```
   - Response (Failure - Id tidak ditemukan):
     ```json
     {
       "status": "fail",
       "message": "Buku gagal dihapus. Id tidak ditemukan"
     }
     ```

## Cara Menjalankan Server
1. Pastikan Node.js telah terinstal di komputer Anda.
2. Clone repository ini dan masuk ke direktori proyek.
3. Jalankan perintah berikut untuk menginstal dependensi:
   ```sh
   npm install
   ```
4. Jalankan server dengan perintah:
   ```sh
   npm start
   ```
5. Server akan berjalan di `http://localhost:9000`.

## Dependensi
- `@hapi/hapi`: Framework Hapi.js untuk membuat API
- `nanoid`: Untuk membuat ID unik pada setiap buku

## Struktur Proyek
```
📦 bookshelf-api
├── 📂 src
│   ├── 📄 books.js
│   ├── 📄 handler.js
│   ├── 📄 routes.js
│   ├── 📄 server.js
├── 📄 package.json
├── 📄 README.md
```


