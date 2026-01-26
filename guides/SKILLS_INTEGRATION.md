# Agent Skills Integration Guide / Panduan Integrasi Agent Skills

This guide explains how to transform project documentation into "Superpower" Agent Skills for OpenCode.
Panduan ini menjelaskan cara mengubah dokumentasi proyek menjadi Agent Skills yang "Superpower" untuk OpenCode.

---

## [ID] Bahasa Indonesia

### 1. Mengapa Menggunakan Agent Skills?
Mengintegrasikan dokumen proyek seperti **Functional Specification Document (FSD)** dan **README** standar kantor ke dalam *Agent Skills* memastikan agen AI bekerja sesuai dengan aturan bisnis dan standar teknis yang tepat. Agen AI tidak lagi hanya menebak, tetapi bekerja berdasarkan instruksi spesifik proyek Anda.

### 2. Strategi Pembuatan Skill
Jangan hanya menyalin seluruh isi dokumen mentah. Gunakan strategi berikut:
*   **Ubah Narasi Menjadi Instruksi:** Ubah paragraf panjang menjadi aturan teknis (misal: "Jika audit gagal, field Fakta wajib diisi").
*   **Gunakan Skills Lokal:** Simpan di folder `.opencode/skills/` di dalam proyek agar instruksi hanya aktif untuk proyek tersebut.
*   **Self-Contained:** Pastikan `SKILL.md` berisi semua informasi penting sehingga AI tidak perlu mencari file dokumen asli lagi.

### 3. Struktur Folder
Buat struktur folder berikut di root proyek Anda:
```text
.opencode/
└── skills/
    ├── audit-project-analyst/
    │   └── SKILL.md (Berisi logika bisnis dari FSD,PRD,DLL)
    └── code-standard-expert/
        └── SKILL.md (Berisi standar kode dari README)
```

### 4. Keamanan (Penting!)
Karena *skills* sering berisi logika bisnis sensitif, **jangan unggah folder ini ke GitHub**. Tambahkan baris berikut ke `.gitignore` Anda:
```text
# OpenCode Skills
.opencode/
```

---

## [EN] English Version

### 1. Why Use Agent Skills?
Integrating project documents like the **Functional Specification Document (FSD)** and office **README** standards into *Agent Skills* ensures the AI agent operates within precise business rules and technical standards. The AI agent no longer guesses; it works based on your project's specific instructions.

### 2. Skill Creation Strategy
Do not simply copy-paste raw documents. Use the following strategy:
*   **Transform Narrative into Instructions:** Convert long paragraphs into technical rules (e.g., "If an audit fails, the Fact field is mandatory").
*   **Use Local Skills:** Store them in the `.opencode/skills/` folder within the project so instructions are only active for that specific project.
*   **Self-Contained:** Ensure `SKILL.md` contains all critical information so the AI doesn't need to reference the original document files.

### 3. Folder Structure
Create the following folder structure in your project root:
```text
.opencode/
└── skills/
    ├── audit-project-analyst/
    │   └── SKILL.md (Contains business logic from FSD)
    └── code-standard-expert/
        └── SKILL.md (Contains code standards from README)
```

### 4. Security (Important!)
Since *skills* often contain sensitive business logic, **do not upload this folder to GitHub**. Add the following line to your `.gitignore`:
```text
# OpenCode Skills
.opencode/
```

---

## Summary Table / Tabel Ringkasan

| Component / Komponen | Location / Lokasi | Description / Deskripsi |
| :--- | :--- | :--- |
| **FSD Skill** | `.opencode/skills/audit-project-analyst/SKILL.md` | Business logic & system workflows. |
| **Code Skill** | `.opencode/skills/code-standard-expert/SKILL.md` | Tech stack & folder structures. |
| **Git Ignore** | `.gitignore` | Exclude `.opencode/` for data security. |

---

## SKILL.md Templates / Template SKILL.md

Below are ready-to-use templates. Copy and customize for your project.
Berikut adalah template siap pakai. Salin dan sesuaikan untuk proyek Anda.

---

### Template 1: Business Logic Skill (FSD/PRD)

Create file: `.opencode/skills/business-logic-expert/SKILL.md`

```markdown
# Business Logic Expert

## Metadata
- **Name:** business-logic-expert
- **Description:** Expert in [PROJECT_NAME] business rules and domain logic
- **Triggers:** business logic, domain rules, validation, workflow, [PROJECT_NAME]

---

## Context

This skill contains the business rules and domain logic for [PROJECT_NAME].
The AI must follow these rules strictly when implementing features.

---

## Domain Entities

### Entity: User
| Field | Type | Rules |
|-------|------|-------|
| id | UUID | Auto-generated, immutable |
| email | string | Required, unique, valid email format |
| role | enum | Values: 'admin', 'manager', 'staff'. Default: 'staff' |
| status | enum | Values: 'active', 'suspended', 'deleted' |

### Entity: Order
| Field | Type | Rules |
|-------|------|-------|
| id | UUID | Auto-generated |
| user_id | UUID | Required, FK to User |
| status | enum | Values: 'draft', 'pending', 'approved', 'rejected', 'completed' |
| total | decimal | Calculated, min: 0 |

---

## Business Rules

### Rule 1: Order Approval Workflow
```text
IF order.total < 1000 THEN
  → Auto-approve (status = 'approved')
ELSE IF order.total >= 1000 AND order.total < 10000 THEN
  → Requires Manager approval
ELSE
  → Requires Admin approval
```

### Rule 2: User Suspension
```text
IF user has 3+ rejected orders in 30 days THEN
  → Auto-suspend user
  → Send notification email
  → Log to audit_trail
```

### Rule 3: Data Validation
- Email must be verified before user can create orders
- Order cannot be edited after status = 'approved'
- Deleted users cannot login but data is retained for audit

---

## API Response Standards

### Success Response
```json
{
  "success": true,
  "data": { ... },
  "message": "Operation completed"
}
```

### Error Response
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Email already exists",
    "field": "email"
  }
}
```

---

## Instructions for AI

1. **ALWAYS** validate against business rules before implementing
2. **NEVER** skip validation even for "quick fixes"
3. **ASK** if a requirement conflicts with existing rules
4. **LOG** all state changes to audit_trail table
5. **USE** transactions for multi-step operations
```

---

### Template 2: Code Standards Skill

Create file: `.opencode/skills/code-standards/SKILL.md`

```markdown
# Code Standards Expert

## Metadata
- **Name:** code-standards
- **Description:** Enforces coding standards and architectural patterns for [PROJECT_NAME]
- **Triggers:** code review, refactor, new feature, best practices

---

## Tech Stack

| Layer | Technology | Version |
|-------|------------|---------|
| Frontend | Next.js (App Router) | 14.x |
| UI Library | Shadcn/ui + Tailwind CSS | Latest |
| Backend | Next.js API Routes / Server Actions | - |
| Database | Supabase (PostgreSQL) | - |
| Auth | Supabase Auth | - |
| Language | TypeScript | 5.x (strict mode) |

---

## Folder Structure

```text
src/
├── app/                    # Next.js App Router
│   ├── (auth)/            # Auth group routes
│   ├── (dashboard)/       # Protected routes
│   ├── api/               # API routes
│   └── layout.tsx
├── components/
│   ├── ui/                # Shadcn components (DO NOT EDIT)
│   ├── forms/             # Form components
│   ├── layouts/           # Layout components
│   └── [feature]/         # Feature-specific components
├── lib/
│   ├── supabase/          # Supabase client & queries
│   ├── utils/             # Utility functions
│   └── validations/       # Zod schemas
├── hooks/                 # Custom React hooks
├── types/                 # TypeScript types & interfaces
└── constants/             # App constants
```

---

## Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Components | PascalCase | `UserProfile.tsx` |
| Hooks | camelCase with 'use' prefix | `useAuth.ts` |
| Utils | camelCase | `formatDate.ts` |
| Types | PascalCase with suffix | `UserType.ts`, `OrderSchema.ts` |
| Constants | SCREAMING_SNAKE_CASE | `API_ENDPOINTS.ts` |
| CSS Classes | kebab-case (Tailwind) | `bg-primary text-white` |

---

## Component Template

```tsx
// components/features/UserCard.tsx
import { cn } from "@/lib/utils"
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card"
import type { User } from "@/types/user"

interface UserCardProps {
  user: User
  className?: string
  onSelect?: (user: User) => void
}

export function UserCard({ user, className, onSelect }: UserCardProps) {
  return (
    <Card 
      className={cn("cursor-pointer hover:shadow-md", className)}
      onClick={() => onSelect?.(user)}
    >
      <CardHeader>
        <CardTitle>{user.name}</CardTitle>
      </CardHeader>
      <CardContent>
        <p className="text-muted-foreground">{user.email}</p>
      </CardContent>
    </Card>
  )
}
```

---

## Server Action Template

```tsx
// app/actions/user.ts
"use server"

import { createClient } from "@/lib/supabase/server"
import { revalidatePath } from "next/cache"
import { userSchema } from "@/lib/validations/user"

export async function updateUser(formData: FormData) {
  const supabase = await createClient()
  
  // 1. Validate input
  const validated = userSchema.safeParse({
    name: formData.get("name"),
    email: formData.get("email"),
  })
  
  if (!validated.success) {
    return { success: false, error: validated.error.flatten() }
  }
  
  // 2. Execute query
  const { data, error } = await supabase
    .from("users")
    .update(validated.data)
    .eq("id", formData.get("id"))
    .select()
    .single()
  
  if (error) {
    return { success: false, error: error.message }
  }
  
  // 3. Revalidate & return
  revalidatePath("/dashboard/users")
  return { success: true, data }
}
```

---

## Prohibited Patterns ❌

1. **NO** `any` type - use `unknown` and narrow
2. **NO** inline styles - use Tailwind classes
3. **NO** direct DOM manipulation - use React state
4. **NO** console.log in production - use proper logging
5. **NO** hardcoded strings - use constants or i18n
6. **NO** barrel exports (index.ts re-exports) - import directly

---

## Required Patterns ✅

1. **ALWAYS** use TypeScript strict mode
2. **ALWAYS** validate with Zod before DB operations
3. **ALWAYS** handle loading & error states
4. **ALWAYS** use Server Components by default
5. **ALWAYS** add `"use client"` only when needed
6. **ALWAYS** use Suspense boundaries for async components
```

---

## How to Use / Cara Menggunakan

### Activating the Skill
Once you've created the skill files, OpenCode will automatically detect them. You can invoke them by:

1. **Automatic:** OpenCode loads skills based on context
2. **Manual:** Type `/use-skill business-logic-expert` in chat

### Customization Tips
- Replace `[PROJECT_NAME]` with your actual project name
- Add/remove entities based on your domain
- Update tech stack versions as needed
- Add more specific rules from your FSD/PRD document

---

*Tip: Start with a minimal skill and expand as you discover more rules during development.*
