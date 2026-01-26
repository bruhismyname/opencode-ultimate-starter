# CLIProxyAPI Docker Installation Guide / Panduan Instalasi Docker CLIProxyAPI

This guide explains the step-by-step process to set up CLIProxyAPI using Docker and connect your Antigravity account via OAuth.
Panduan ini menjelaskan langkah demi langkah cara memasang CLIProxyAPI menggunakan Docker dan menghubungkan akun Antigravity Anda melalui OAuth.

---

## [ID] Bahasa Indonesia

### 1. Clone Repository
Langkah pertama adalah menyalin repositori resmi CLIProxyAPI ke komputer lokal Anda:
```bash
git clone https://github.com/router-for-me/CLIProxyAPI.git
cd CLIProxyAPI
```

### 2. Konfigurasi File
Salin file contoh konfigurasi menjadi file konfigurasi aktif:
```bash
cp config.example.yaml config.yaml
```

### 3. Edit `config.yaml`
Buka file `config.yaml` dan sesuaikan bagian berikut agar sesuai dengan kebutuhan Anda (terutama bagian `api-keys` dan `oauth-model-alias` untuk Antigravity):
```yaml
# Management API settings
remote-management:
  allow-remote: true
  secret-key: "" # Ganti jika perlu

# API keys untuk autentikasi di OpenCode
api-keys:
  - "YOUR_CLIPROXY_API_KEY"

# Mapping Model Antigravity (Penting untuk OpenCode)
oauth-model-alias:
  antigravity:
    - name: rev19-uic3-1p
      alias: gemini-2.5-computer-use-preview-10-2025
    - name: gemini-3-pro-high
      alias: gemini-3-pro-preview
    - name: claude-sonnet-4-5
      alias: gemini-claude-sonnet-4-5
```

### 4. Jalankan Docker
Gunakan Docker Compose untuk menjalankan server di latar belakang:
```bash
docker compose up -d
```

### 5. Akses Dashboard Manajemen
Buka browser dan akses alamat berikut untuk mengelola proxy Anda:
`http://localhost:8317/management.html`

### 6. Login Antigravity OAuth
1. Di Dashboard, cari menu **OAuth Login**.
2. Pilih **Antigravity**.
3. Ikuti instruksi login yang muncul untuk menghubungkan akun Anda.
4. Setelah berhasil, proxy siap digunakan oleh OpenCode menggunakan API Key `YOUR_CLIPROXY_API_KEY`.

---

## [EN] English Version

### 1. Clone Repository
The first step is to clone the official CLIProxyAPI repository to your local machine:
```bash
git clone https://github.com/router-for-me/CLIProxyAPI.git
cd CLIProxyAPI
```

### 2. File Configuration
Copy the example configuration file to create an active configuration file:
```bash
cp config.example.yaml config.yaml
```

### 3. Edit `config.yaml`
Open `config.yaml` and adjust the following sections to match your needs (especially `api-keys` and `oauth-model-alias` for Antigravity):
```yaml
# Management API settings
remote-management:
  allow-remote: true
  secret-key: "" # Change if needed

# API keys for OpenCode authentication
api-keys:
  - "YOUR_CLIPROXY_API_KEY"

# Antigravity Model Mapping (Critical for OpenCode)
oauth-model-alias:
  antigravity:
    - name: rev19-uic3-1p
      alias: gemini-2.5-computer-use-preview-10-2025
    - name: gemini-3-pro-high
      alias: gemini-3-pro-preview
    - name: claude-sonnet-4-5
      alias: gemini-claude-sonnet-4-5
```

### 4. Run Docker
Use Docker Compose to start the server in the background:
```bash
docker compose up -d
```

### 5. Access Management Dashboard
Open your browser and navigate to the following address to manage your proxy:
`http://localhost:8317/management.html`

### 6. Antigravity OAuth Login
1. In the Dashboard, look for the **OAuth Login** menu.
2. Select **Antigravity**.
3. Follow the login instructions to connect your account.
4. Once successful, the proxy is ready for OpenCode using the API Key `YOUR_CLIPROXY_API_KEY`.

---

## Summary / Ringkasan

| Step / Langkah | Command / Perintah |
| :--- | :--- |
| Clone Repo | `git clone https://github.com/router-for-me/CLIProxyAPI.git` |
| Copy Config | `cp config.example.yaml config.yaml` |
| Run Docker | `docker compose up -d` |
| Dashboard | `http://localhost:8317/management.html` |

---

## Troubleshooting

### Docker not running?
Pastikan Docker Desktop sudah berjalan sebelum menjalankan `docker compose up -d`.

### Dashbord can not login acces?
Coba lakukan restart Docker Desktop yang sudah berjalan dengan menjalankan `docker compose restart` 

### Port 8317 sudah dipakai?
Edit `docker-compose.yml` dan ganti port mapping ke port lain, misalnya `8318:8317`.

### OAuth gagal?
Coba refresh halaman dashboard dan login ulang. Pastikan koneksi internet stabil.
