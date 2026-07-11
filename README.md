# Portofolio — Rifan Eko Candra Maulana

<a href="https://portofolio-korifcan.vercel.app" target="_blank">**Live Demo**</a>

Website portofolio interaktif dengan fitur lengkap: sistem autentikasi, testimoni & masukan real-time, rating berbintang, komentar, dark/light mode, multilanguage (ID/EN), dan panel admin terintegrasi.

---

## Daftar Isi

- [Fitur](#fitur)
  - [Halaman Utama](#halaman-utama-indexhtml)
  - [Fitur Real-time (Firebase)](#fitur-real-time-firebase)
  - [Panel Admin](#panel-admin)
  - [Pengguna](#pengguna)
  - [Keamanan](#keamanan)
- [Teknologi yang Digunakan](#teknologi-yang-digunakan)
- [Struktur File](#struktur-file)
- [Cara Menjalankan](#cara-menjalankan)
- [Konfigurasi Firebase](#konfigurasi-firebase)
- [Firestore Security Rules](#firestore-security-rules)
- [Deployment](#deployment)
- [Screenshot](#screenshot)

---

## Fitur

### Halaman Utama (`index.html`)

| Fitur | Deskripsi |
|-------|-----------|
| **Hero Section** | Foto profil dengan animasi pulse ring, teks sambutan, tombol CTA, dan tautan media sosial (GitHub, LinkedIn, Instagram, TikTok, YouTube) |
| **About** | Bio singkat, foto profil, dan statistik (6+ tahun pengalaman, 7+ posisi kerja, 20+ software dikuasai) |
| **Skills** | 20 keahlian dengan ikon: kerja tim, etika kerja, adaptasi, komunikasi, edit foto/video, desain grafis, fotografi, videografi, jaringan/LAN, troubleshooting Windows, flash Android, instalasi Windows, Microsoft Office, Canva, CorelDRAW, CapCut, Alight Motion, Picsart, Mi Flash Tool, Mi Unlock Tool |
| **Experience** | Timeline 7 pengalaman kerja dari 2018–2026 (Service Center Samsung, Klinik Android, Collection Officer, Train Attendant KAI, Quality Control, Administrasi BPN) |
| **Certificates** | 5 sertifikat dengan tautan verifikasi (Microsoft Office, Train Attendant, Samsung Tech Institute, PRAKERIN, Kerja Praktek) |
| **Projects** | Kartu proyek dengan slider perbandingan before/after (dark vs light mode), rating, dan komentar |
| **Testimonials** | Testimoni real-time dengan filter bintang, pagination, tombol like, dan fitur balas |
| **Contact** | Form kontak terintegrasi Web3Forms dengan hCaptcha, redirect ke halaman terima kasih |

### Fitur Real-time (Firebase)

| Fitur | Detail |
|-------|--------|
| **Autentikasi** | Login/daftar via email & password, verifikasi email, reset password, deteksi email sekali pakai (80+ domain diblokir) |
| **Profil Pengguna** | Edit nama, nomor HP, email, foto profil (upload via kamera/gallery, disimpan sebagai data URL di Firestore) |
| **Testimoni & Masukan** | CRUD real-time dengan rating bintang (1–5), opsi visibilitas email (sembunyi/sensor/tampil), filter, pagination, dan fitur like |
| **Komentar** | Per proyek, pagination, verifikasi email wajib, dan fitur balas |
| **Rating** | Rating bintang real-time per proyek, rata-rata otomatis, satu rating per user per proyek |
| **Balasan** | Subcollection replies di testimoni & komentar, real-time |

### Panel Admin

Tersedia dalam dua bentuk:

#### 1. Inline Panel (`index.html`)
Akses dari menu profil (jika role admin). 4 tab dengan dukungan swipe:
- **Dashboard** — Statistik total testimoni, komentar, pengguna, rating
- **Testimoni** — Tambah, filter, cari, urutkan, sembunyikan/tampilkan, hapus, balas
- **Komentar** — Filter per proyek, cari, urutkan, hapus, balas
- **Pengguna** — Cari, urutkan, nonaktifkan/aktifkan, hapus akun + data terkait

#### 2. Halaman Admin Khusus (`admin.html`)
7 section dengan sidebar navigasi:

| Section | Fungsi |
|---------|--------|
| **Dashboard** | Statistik grid real-time (total/hidden/active testimonials, comments, users, ratings) |
| **Testimoni** | CRUD lengkap + filter (all/pending/visible + bintang) + search + sort + pagination + hide/show + delete + reply + clear all |
| **Komentar** | Filter proyek + search + sort + pagination + delete + reply + clear all |
| **Rating** | Ringkasan rating per proyek (rata-rata + jumlah) + filter bintang + filter proyek + search + delete + clear all |
| **Pengguna** | Filter (all/admin/user/blocked/active) + search + sort + disable/enable + delete user + cascade delete |
| **Verifikasi** | Filter (all/verified/unverified) + search + verifikasi manual email / hapus verifikasi |
| **Role** | Filter (all/admin/verified/user) + search + ubah role user (user/verified/admin) + cascade update ke testimoni & komentar |

### Pengguna

| Role | Kemampuan |
|------|-----------|
| **User** | Login/daftar, edit profil, beri rating, tulis komentar, tulis testimoni, like testimoni, hapus konten sendiri |
| **Verified** | Semua kemampuan User + badge verifikasi (diberikan admin setelah verifikasi email) |
| **Admin** | Semua kemampuan + panel admin, kelola testimoni/komentar/rating/user, ubah role, verifikasi email manual |

### Keamanan

- Blokir akses F12, Ctrl+Shift+I/J/C (DevTools)
- Blokir klik kanan
- Proteksi email sekali pakai (80+ domain disposable)
- Verifikasi email wajib untuk komentar & testimoni
- Firestore Security Rules role-based (baca selengkapnya di [Firestore Rules](#firestore-security-rules))
- Rate limiting Firebase Auth (too-many-requests)

---

## Teknologi yang Digunakan

### Frontend
- **HTML5** — Struktur halaman
- **CSS3** — Styling dengan CSS variables, animasi keyframes, IntersectionObserver reveal, responsive design, dark/light mode
- **JavaScript (Vanilla)** — Semua interaktivitas tanpa framework

### Backend & Layanan
| Teknologi | Versi | Fungsi |
|-----------|-------|--------|
| Firebase Authentication | 12.15.0 | Login/register, verifikasi email, reset password |
| Cloud Firestore | 12.15.0 | Database real-time (testimoni, komentar, rating, user profiles, replies) |
| Web3Forms | — | Contact form handler dengan hCaptcha |
| Font Awesome | 6.5.0 | Ikon UI |
| Google Fonts (Inter) | — | Tipografi utama |

### Deployment
- **Vercel** — Hosting utama: `https://portofolio-korifcan.vercel.app`
- **GitHub Pages** — Hosting cadangan: `https://korifcan.github.io/Portofolio/`

---

## Struktur File

```
Portofolio/
├── index.html           # Halaman utama (portofolio + semua fitur)
├── admin.html           # Panel admin terpisah
├── thank-you.html       # Halaman setelah submit form kontak
├── firestore.rules      # Firestore security rules (copy ke Firebase Console)
├── robots.txt           # Konfigurasi crawler (blokir AI scraping)
├── IMG_Profil.png       # Foto profil
├── screenshot-light.png # Screenshot light mode (slider proyek)
└── screenshot-dark.png  # Screenshot dark mode (slider proyek)
```

---

## Cara Menjalankan

### 1. Clone repositori

```bash
git clone https://github.com/KoRifCan/Portofolio.git
cd Portofolio
```

### 2. Buka dengan browser

Karena ini website statis (tanpa bundler/build tool), cukup buka langsung:

```bash
# Via file system
open index.html   # macOS
start index.html  # Windows
xdg-open index.html  # Linux

# Atau jalankan server lokal
python3 -m http.server 8000
# Lalu buka http://localhost:8000
```

### 3. Firebase (diperlukan untuk fitur interaktif)

Fitur autentikasi, testimoni, komentar, dan rating membutuhkan koneksi ke Firebase. Konfigurasi sudah tersemat di `index.html` dan `admin.html`, namun pastikan project Firestore sudah aktif.

> **Catatan:** Untuk pengembangan lokal, fitur login akan tetap berfungsi karena Firebase API key bersifat publik (aman untuk client-side SDK).

---

## Konfigurasi Firebase

Project Firebase saat ini: **portofolio-korifcan**

Konfigurasi sudah tersemat di kode:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyBQkb3mKlnC6gzRuufRcnqBEFY_KJ1RKSM",
  authDomain: "portofolio-korifcan.firebaseapp.com",
  projectId: "portofolio-korifcan",
  storageBucket: "portofolio-korifcan.firebasestorage.app",
  messagingSenderId: "344306005362",
  appId: "1:344306005362:web:1ed35ceb391f0cb15fd9eb",
  measurementId: "G-5NNH1ZPH6M"
};
```

### Mengganti dengan Project Sendiri

1. Buat project di [Firebase Console](https://console.firebase.google.com)
2. Aktifkan Authentication (Email/Password) dan Firestore Database
3. Salin konfigurasi project ke `firebaseConfig` di `index.html` (baris 839–847) dan `admin.html` (baris 561–568)

---

## Firestore Security Rules

Salin rules berikut ke **Firebase Console → Firestore Database → Rules**:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    function isAdmin() {
      return request.auth != null
        && get(/databases/$(database)/documents/userProfiles/$(request.auth.uid)).data.role == 'admin';
    }

    function isOwner(userId) {
      return request.auth != null && request.auth.uid == userId;
    }

    match /testimonials/{doc} {
      allow read;
      allow create: if request.auth != null;
      allow update, delete: if isOwner(resource.data.userId) || isAdmin();
    }

    match /comments/{doc} {
      allow read;
      allow create: if request.auth != null;
      allow update, delete: if isOwner(resource.data.userId) || isAdmin();
    }

    match /ratings/{doc} {
      allow read;
      allow create: if request.auth != null;
      allow delete: if isOwner(resource.data.userId) || isAdmin();
    }

    match /userProfiles/{userId} {
      allow read;
      allow create, update: if isOwner(userId);
      allow delete: if isAdmin();
    }

    match /{path=**}/replies/{reply} {
      allow read;
      allow create: if request.auth != null;
      allow delete: if isOwner(resource.data.userId) || isAdmin();
    }
  }
}
```

### Penjelasan Rules:
- **Semua orang** (tidak login pun) bisa **membaca** data publik
- **User login** bisa **membuat** testimoni, komentar, rating, balasan
- **Pemilik data** atau **admin** bisa **mengedit/menghapus**
- **Admin** bisa **mengubah role** dan **menghapus akun user**
- **User** hanya bisa **mengubah/menghapus profile sendiri**

---

## Deployment

### Deploy ke Vercel (Rekomendasi)

1. Push repositori ke GitHub
2. Import di [Vercel](https://vercel.com/new)
3. Setting:
   - Framework: **Other**
   - Build Command: (kosongkan)
   - Output Directory: (biarkan default)
4. Deploy

### Deploy ke GitHub Pages

1. Buka repositori → **Settings** → **Pages**
2. Pilih source: **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)**
4. Simpan, website otomatis terdeploy ke `https://<username>.github.io/Portofolio/`

---

## Screenshot

![Light Mode](screenshot-light.png)
*Tampilan Light Mode*

![Dark Mode](screenshot-dark.png)
*Tampilan Dark Mode*

---

## Lisensi

Hak cipta © 2026 Rifan Eko Candra Maulana. Seluruh konten dan kode dalam repositori ini adalah milik pribadi.

---

## Kontak

- **Email:** rifan.eko25@gmail.com
- **LinkedIn:** [rifan-eko-candra-maulana](https://www.linkedin.com/in/rifan-eko-candra-maulana)
- **GitHub:** [@KoRifCan](https://github.com/KoRifCan)
