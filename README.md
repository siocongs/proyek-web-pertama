# 🚀 Panduan Lengkap Git & GitHub untuk Pemula

Selamat datang! Repositori ini berisi panduan dasar yang dirancang untuk membantu Anda memahami alur kerja Git dan GitHub, mulai dari instalasi hingga kolaborasi dalam tim.

## 📜 Daftar Isi
- [Bagian 1: Instalasi & Konfigurasi Awal](#bagian-1-instalasi--konfigurasi-awal-git)
- [Bagian 2: Alur Kerja Dasar Git (Lokal)](#bagian-2-alur-kerja-dasar-git-lokal)
- [Bagian 3: Integrasi dengan GitHub](#bagian-3-integrasi-dengan-github)
- [Bagian 4: Alur Kerja Kolaborasi Tim](#bagian-4-alur-kerja-kolaborasi-tim-feature-branch-workflow)

---

## Bagian 1: Instalasi & Konfigurasi Awal Git

### 1. 💻 Instalasi Git

#### Untuk Pengguna Windows
1. Unduh *installer* dari situs resmi: [git-scm.com/download/win](https://git-scm.com/download/win).
2. Jalankan file `.exe` yang telah diunduh.
3. Biarkan pengaturan *default*, klik **Next** hingga proses instalasi selesai.
4. Buka **Command Prompt (CMD)** atau **Git Bash** dan lakukan verifikasi:
   ```bash
   git --version
   ```

#### Untuk Pengguna MacOS
1. Buka Terminal dan install **Homebrew** (jika belum ada):
   ```bash
   /bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"
   ```
2. Gunakan Homebrew untuk menginstall Git:
   ```bash
   brew install git
   ```
3. Lakukan verifikasi instalasi:
   ```bash
   git --version
   ```

#### Untuk Pengguna Ubuntu/Debian
1. Buka Terminal dan perbarui daftar *package*:
   ```bash
   sudo apt update
   sudo apt install git
   ```
2. Lakukan verifikasi instalasi:
   ```bash
   git --version
   ```

### 2. 🔧 Konfigurasi Awal (Wajib Dilakukan)
> Ini adalah pengaturan **satu kali**. Nama dan email Anda akan terekam di setiap `commit` yang Anda buat.

Buka terminal Anda dan jalankan perintah berikut dengan data diri Anda:
```bash
git config --global user.name "Nama Kamu"
git config --global user.email "email@kamu.com"
```

---

## Bagian 2: Alur Kerja Dasar Git (Lokal)

### 1. Buat Folder & Inisialisasi Git
> `git init` mengubah folder biasa menjadi sebuah **repository Git** yang bisa melacak perubahan.
```bash
mkdir proyek-web
cd proyek-web
git init
```

### 2. Buat Beberapa File Contoh
```bash
echo "<h1>Selamat Datang</h1>" > index.html
mkdir css
echo "body { font-family: sans-serif; }" > css/style.css
```

### 3. Cek Status & Masuk ke Staging Area
> `git add .` memasukkan semua perubahan ke "Staging Area", yaitu tempat Anda mengumpulkan perubahan sebelum disimpan secara permanen.
```bash
git status
git add .
```

### 4. Simpan Perubahan (Commit)
> Anggap `commit` seperti membuat **"save point"** dalam game. Pesan commit harus jelas dan deskriptif.
```bash
git commit -m "feat: Inisialisasi proyek dengan file Index dan CSS"
```

### 5. Buat Branch Baru
> `branch` memungkinkan Anda mengerjakan fitur baru tanpa mengganggu kode utama yang stabil.
```bash
git checkout -b fitur-kontak
```

### 6. Buat File Baru di Branch
```bash
echo "<h1>Halaman Kontak</h1>" > kontak.html
```

### 7. Staging & Commit di Branch
> Setiap branch memiliki riwayat commit-nya sendiri.
```bash
git add .
git commit -m "feat: Menambahkan halaman kontak"
```

### 8. Gabungkan Branch (Merge)
> Setelah fitur selesai, gabungkan kembali ke branch utama (biasanya `main`).
```bash
git checkout main
git merge fitur-kontak
```

---

## Bagian 3: Integrasi dengan GitHub

### 1. Buat Akun & Repository di GitHub
1.  Masuk ke [GitHub](https://github.com).
2.  Di pojok kanan atas, klik **+ → New repository**.
3.  Beri nama repositori (misal: `proyek-web-pertama`).
4.  **Penting:** Jangan centang opsi "Add a README file".
5.  Klik **Create repository**.

### 2. Hubungkan & Push Proyek Lokal ke GitHub
> Perintah di bawah ini memberi tahu Git lokal di mana "rumah online"-nya (remote) dan mengunggah semua commit Anda.

Salin perintah yang disediakan oleh GitHub, yang akan terlihat seperti ini:
```bash
# Menghubungkan repositori lokal ke remote di GitHub
git remote add origin [https://github.com/NamaUserKamu/proyek-web-pertama.git](https://github.com/NamaUserKamu/proyek-web-pertama.git)

# Mengubah nama branch default menjadi 'main' (praktik terbaik saat ini)
git branch -M main

# Mengirim (push) semua commit dari branch 'main' ke GitHub
git push -u origin main
```

---

## Bagian 4: Alur Kerja Kolaborasi Tim (Feature Branch Workflow)

Ini adalah alur kerja standar yang digunakan oleh banyak tim profesional.

### 1. Clone Repository (Hanya sekali di awal)
> Mengunduh seluruh proyek dari GitHub ke komputer Anda.
```bash
git clone <URL_REPOSITORY_DARI_GITHUB>
```

### 2. Selalu Mulai dari `main` Terbaru
> Sebelum mulai mengerjakan fitur baru, pastikan kode lokal Anda sama dengan versi terbaru di GitHub.
```bash
git checkout main
git pull origin main
```

### 3. Buat Branch Baru untuk Setiap Fitur
> Beri nama branch yang deskriptif sesuai fitur yang Anda kerjakan.
```bash
git checkout -b nama-fitur-baru
```

### 4. Kerjakan, Add, dan Commit
> Lakukan perubahan kode, lalu simpan pekerjaan Anda secara berkala dengan commit.
```bash
# Setelah selesai membuat perubahan...
git add .
git commit -m "pesan commit yang jelas dan spesifik"
```

### 5. Push Branch Fitur ke GitHub
> Unggah branch Anda ke GitHub agar bisa dilihat oleh tim.
```bash
git push origin nama-fitur-baru
```

### 6. Buat Pull Request (PR)
> **Pull Request** adalah inti dari kolaborasi. Anda meminta agar pekerjaan Anda ditinjau dan digabungkan ke branch `main`.
1.  Buka halaman repositori di GitHub.
2.  Anda akan melihat notifikasi untuk branch baru Anda, klik **Compare & pull request**.
3.  Isi judul, deskripsi, dan tetapkan **Reviewers** (anggota tim yang akan meninjau kode Anda).
4.  Klik **Create pull request**.

### 7. Review, Diskusi, dan Merge
-   Anggota tim lain akan meninjau perubahan, memberikan komentar, atau meminta perbaikan.
-   Setelah disetujui, ketua tim atau pemilik repositori akan menekan tombol **Merge pull request**.

### 8. Sinkronisasi Ulang Setelah Merge
> Setelah PR Anda atau orang lain di-merge, perbarui kembali branch `main` di komputer Anda.
```bash
git checkout main
git pull origin main
```
Ulangi dari langkah 3 untuk mengerjakan fitur berikutnya!

Berikut link docs laporan Prak01 Muhamad Bachtiar :
https://docs.google.com/document/d/1HACoyKDQSwZlK7j32lnSMmuY4K2XIwjsFz50YWeU1Vc/edit?usp=sharing
