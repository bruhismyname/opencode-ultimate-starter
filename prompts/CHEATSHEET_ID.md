# Contekan Prompt OpenCode: Mode Planner-Sisyphus (Hemat Token) 🇮🇩

Mode ini menjadikan AI sebagai **"Arsitek"** (Otak) dan Anda sebagai **"Tukang"** (Tangan).
AI **tidak** mengedit file secara langsung (yang memakan ribuan token), tetapi memberikan kode final untuk Anda copy-paste.

## Prinsip Utama
1. **Architect Mode:** Biarkan AI berpikir dulu, jangan langsung coding.
2. **Use Tools:** Paksa AI menggunakan MCP (Database/Terminal) daripada menebak-nebak.
3. **No Edit:** Minta output final di chat untuk copy-paste (kecuali task kecil).

### Kunci Utama
Tambahkan kalimat ini di akhir setiap prompt Anda:
> **"Jangan jalankan perintah terminal atau edit file apapun. Cukup berikan rencana/kode lengkap di chat agar bisa saya copy-paste."**

### Tabel Skenario

| Tujuan | Prompt Sakti (Copy-Paste) |
| :--- | :--- |
| **Mulai Project / Ide Baru** | "Bertindaklah sebagai **Sisyphus**. Saya punya ide untuk [Nama Fitur]. Gunakan skill **`brainstorming`** untuk mewawancarai saya tentang kebutuhan fiturnya. Setelah sepakat, buatkan rencana implementasi detail." |
| **Membuat Logika Backend** | "Bertindaklah sebagai **@oracle**. Saya butuh fungsi untuk [Jelaskan Logika]. Tuliskan **kode lengkap** dengan error handling. Jelaskan cara pakainya." |
| **Membuat Tampilan (UI)** | "Bertindaklah sebagai **@frontend-ui-ux-engineer**. Buatkan komponen [Nama UI] dengan [Tailwind/CSS]. Fokus pada hierarki visual. Berikan kode lengkap siap copy-paste." |
| **Analisis Error** | "Saya dapat error: `[Paste Error]`. Gunakan logika **`systematic-debugging`**. Jangan jalankan tes sendiri. Analisis errornya dan beritahu saya baris mana yang salah." |
| **Review Kode** | "Bertindaklah sebagai **@oracle**. Review kode di bawah ini. Cari masalah keamanan dan performa, lalu berikan versi perbaikannya." |

---

## Bagian 1: Workflow Otomatis (Wajib `AGENTS.md`)
*Gunakan ini jika kamu sudah memasang `AGENTS.md` di project.*

| Tujuan | Prompt Sakti |
| :--- | :--- |
| **Mulai Fitur Baru** | "Saya ingin membuat fitur [Nama Fitur]. Sesuai aturan `AGENTS.md`, tolong: <br>1. Analisis kebutuhan.<br>2. Update `todos.md` dengan list tugas detail.<br>3. Jangan coding dulu, konfirmasi rencana ke saya." |
| **Update Progress** | "Saya sudah menyelesaikan [Nama Tugas]. Tolong update `todos.md` (tandai selesai) dan tambahkan entry ke `CHANGELOG.md` bagian Unreleased." |

---

## Bagian 2: Penggunaan MCP (Superpowers)
*Gunakan ini untuk memanfaatkan tool Shadcn, Supabase, dan Web Search.*

| Tool | Skenario | Prompt Sakti |
| :--- | :--- | :--- |
| **Supabase** | **Cek Database** | "Gunakan **Supabase MCP** untuk melihat struktur tabel `[nama_tabel]`. Berdasarkan skema itu, buatkan query SQL/fungsi TypeScript untuk mengambil data X." |
| **Supabase** | **Debug Data** | "Ada error saat insert data. Cek 5 baris terakhir dari tabel `[nama_tabel]` lewat Supabase MCP untuk melihat format data yang benar." |
| **Shadcn** | **Install UI** | "Gunakan **Shadcn MCP** untuk menambahkan komponen `[nama-komponen]` (misal: button, card). Jangan edit manual, gunakan toolnya." |
| **Web Search** | **Cari Info Terkini** | "Gunakan **Web Search** untuk mencari solusi terbaru tentang error `[Paste Error]`. Jangan pakai pengetahuan lama, cari solusi tahun 2024/2025." |
| **Grep** | **Cari Referensi** | "Saya butuh contoh implementasi [Nama Library]. Gunakan **Grep Tool** untuk mencari contoh kodingan nyata di GitHub." |

---

## Bagian 3: Coding & Planner (Hemat Token)

| Tujuan | Prompt Sakti |
| :--- | :--- |
| **Backend Logic** | "Bertindaklah sebagai **@oracle**. Saya butuh fungsi API untuk [Jelaskan Logika]. Tuliskan **kode lengkap** dengan error handling. Jangan pakai placeholder." |
| **Frontend UI** | "Bertindaklah sebagai **@frontend-ui-ux-engineer**. Buatkan komponen [Nama UI] menggunakan komponen Shadcn yang sudah terinstall. Fokus pada hierarki visual." |
| **Refactoring** | "Kode di file [Nama File] terlalu berantakan. Refactor agar lebih bersih (Clean Code) tanpa mengubah fungsi utamanya. Jelaskan apa yang diubah." |

### Tips Pro
* **Jika Supabase Error:** Pastikan token di `opencode.json` masih valid.
* **Jika Shadcn Error:** Pastikan project kamu sudah terinit `npx shadcn@latest init` sebelumnya.