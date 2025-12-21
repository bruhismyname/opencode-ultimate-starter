# 🤖 Automate AI Discipline with `AGENTS.md`

Salah satu fitur tersembunyi namun sangat powerful dari `oh-my-opencode` adalah **Directory Agents Injector**.

Fitur ini memungkinkan Anda "menanamkan" aturan kerja (SOP) ke dalam setiap project secara otomatis. AI akan membaca file ini sebelum mulai bekerja, sehingga ia akan selalu patuh pada workflow yang Anda tentukan.

## 📋 Cara Menggunakannya

### Langkah 1: Buat File di Project Anda
Di dalam folder root **project aplikasi** yang sedang Anda kerjakan (bukan folder config OpenCode), buat file baru bernama:

`AGENTS.md`

### Langkah 2: Isi dengan "Rules of Engagement"
Salin template aturan di bawah ini. Aturan ini dirancang agar AI (Planner-Sisyphus) otomatis membuat rencana kerja (`todos.md`), mencatat perubahan (`CHANGELOG.md`), dan melakukan commit git secara rapi.

```markdown
# Project Workflow Rules

You are strictly required to follow these workflow rules for every task.

## 1. Master Plan (todos.md)
- **Initiation**: If `todos.md` does not exist, CREATE IT immediately using `Planner-Sisyphus`.
- **Structure**: The file must contain a comprehensive list of tasks from development start to finish.
- **Status**: Use `[ ]` for pending and `[x]` for completed tasks.
- **Update**: You MUST mark tasks as `[x]` immediately after completion.

## 2. Change Tracking (CHANGELOG.md)
- **Initiation**: If `CHANGELOG.md` does not exist, create it.
- **Format**: Use Keep A Changelog format (Unreleased, Added, Changed, Fixed).
- **Update**: Every time you complete a meaningful task or modify code behavior, append a bullet point to the `Unreleased` section.

## 3. Version Control (Git)
- **Commit**: You must commit changes after every logical unit of work (e.g., after completing a single item in `todos.md`).
- **Message**: Commit messages must be descriptive (e.g., `feat: implement login page UI`, `fix: resolve jwt token error`).
- **History**: Ensure the git history tells a clear story of the development process.

## 4. Execution Protocol
- BEFORE starting coding: Check `todos.md`.
- AFTER coding:
  1. Run tests/verification.
  2. Update `CHANGELOG.md`.
  3. Mark item in `todos.md` as `[x]`.
  4. Git add & commit.
```

### Langkah 3: Restart Sesi
Tutup sesi OpenCode Anda saat ini atau ketik `/reset` (jika didukung), lalu buka kembali. `oh-my-opencode` akan mendeteksi file `AGENTS.md` tersebut dan menyuntikkan instruksi di atas ke dalam system prompt AI.

Sekarang, setiap kali Anda menyuruh AI bekerja, dia akan otomatis mengecek `todos.md` dan `CHANGELOG.md` tanpa perlu diingatkan!

---