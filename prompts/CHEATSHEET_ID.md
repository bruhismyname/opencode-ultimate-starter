# Contekan Prompt OpenCode: Mode Planner-Sisyphus (Hemat Token) 🇮🇩

Mode ini menjadikan AI sebagai **"Arsitek"** (Otak) dan Anda sebagai **"Tukang"** (Tangan).
AI **tidak** mengedit file secara langsung (yang memakan ribuan token), tetapi memberikan kode final untuk Anda copy-paste.

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