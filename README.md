# Classroom Hub

Website informasi kelas yang bisa dibaca publik dan hanya bisa diedit oleh satu akun admin.

## Yang dibutuhkan
- Akun Supabase untuk database + login admin.
- Akun GitHub untuk menyimpan project.
- Akun Vercel untuk publikasi.
- Jangan bagikan password admin atau Supabase secret/service_role key.

## 1. Buat project dan akun admin Supabase
1. Buat project baru di https://supabase.com/.
2. Buka **Authentication > Users**.
3. Tambahkan satu user untuk akun admin (email dan password yang hanya diketahui admin).
4. Salin nilai **User UID** akun itu.
5. Jangan bagikan akun admin ke teman sekelas.

## 2. Siapkan database dan hubungkan website
1. Buka **SQL Editor** > **New query**.
2. Di file `supabase.sql`, ganti semua teks `UUID_DI_SINI` dengan User UID akun admin yang tadi dibuat.
3. Salin seluruh isi `supabase.sql` yang sudah diubah, lalu jalankan.
4. Buka **Project Settings > API**. Salin **Project URL** dan **anon/public key**.
5. Buka `index.html`, cari `SUPABASE_URL` dan `SUPABASE_ANON_KEY`, lalu ganti nilai placeholder dengan URL dan anon/public key tadi. Jangan gunakan `service_role` key.

## 3. Publikasikan dengan Vercel
Cara sederhana:
1. Buat repository GitHub baru, misalnya `classroom-hub`.
2. Upload `index.html` ke root repository.
3. Upload file lain jika perlu untuk dokumentasi (jangan upload password atau secret).
4. Masuk ke https://vercel.com/ dan pilih **Add New > Project**.
5. Import repository GitHub tadi dan klik **Deploy**. Untuk website HTML statis, tidak perlu build command.
6. Vercel akan memberikan alamat website. Bagikan alamat itu ke grup kelas.

## 4. Cara menggunakan
- Semua teman bisa membuka alamat website tanpa login.
- Admin klik **Login Admin** dan masuk dengan akun Supabase.
- Pilih tab Tugas, Materi, Pengumuman, Jadwal, atau Arsip.
- Klik **Tambah** untuk membuat informasi.
- Pada tugas, admin bisa klik **Arsipkan** setelah tugas selesai.
- Edit dan hapus hanya tersedia saat admin login.

## Catatan keamanan dan privasi
- Kebijakan database membatasi tambah/edit/hapus ke satu User UID.
- Pengunjung publik hanya dapat membaca data.
- Jangan masukkan data pribadi siswa, nomor telepon, alamat, nilai pribadi, atau informasi sensitif.
- Untuk materi berupa file, unggah ke penyimpanan sekolah/Drive dengan izin berbagi yang sesuai, lalu tempel tautannya di kolom Link materi.
- Jika ingin mengganti admin, ubah UUID pada tiga policy insert/update/delete di `supabase.sql`.
