# Panduan Menjalankan grok2api

> Panduan menjalankan `grok2api` menggunakan Docker, Google Cloud Console atau VPS, lalu mempublikasikannya ke internet dengan ngrok.

Panduan ini menjelaskan cara menjalankan `grok2api` dengan bantuan Google Cloud Console atau VPS pribadi.

Proses ini memanfaatkan fitur dari Google Cloud Console:
https://console.cloud.google.com

Google Cloud Console menyediakan quota untuk mengakses terminal selama 50 jam per bulan.

Jika kamu sudah memiliki VPS, langkah-langkah di bawah juga bisa langsung diterapkan di VPS masing-masing.

## 1. Clone repository
Jalankan perintah berikut untuk mengunduh project:

```bash
git clone git@github.com:sodikinnaa/grok2api.git
cd grok2api
```

## 2. Jalankan service dengan Docker
Setelah masuk ke folder project, jalankan:

```bash
docker compose up -d
```

## 3. Install ngrok
Buka situs resmi ngrok untuk mendapatkan token dan informasi instalasi:

https://ngrok.com/

Kemudian instal ngrok dengan perintah berikut:

```bash
curl -sSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
  | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
  && echo "deb https://ngrok-agent.s3.amazonaws.com bookworm main" \
  | sudo tee /etc/apt/sources.list.d/ngrok.list \
  && sudo apt update \
  && sudo apt install ngrok
```

## 4. Tambahkan authtoken ngrok
Setelah mendapatkan token dari dashboard ngrok, jalankan:

```bash
ngrok config add-authtoken xxxxxx
```

Ganti `xxxxxx` dengan token milik kamu.

## 5. Publish port ke publik
Untuk membuat aplikasi bisa diakses dari internet, jalankan:

```bash
ngrok http 8000
```

Jika berhasil, ngrok akan memberikan URL publik yang bisa dibagikan.

## Catatan
- Pastikan service berjalan normal sebelum menjalankan `ngrok`.
- Jika port aplikasi bukan `8000`, sesuaikan perintah `ngrok http` dengan port yang digunakan.

## 6. Cara Menggunakan grok2api

1. Ambil cookie dari Grok seperti pada gambar berikut:

   ![Ambil cookie Grok](images/Get_Cookies.png)

2. Paste token pada kolom yang tersedia seperti pada gambar berikut:

   ![Paste token](images/Paste-token.png)

3. Generate bearer token untuk digunakan saat mengakses API seperti pada gambar berikut:

   ![Generate bearer token](images/Get-token-api-key.png)