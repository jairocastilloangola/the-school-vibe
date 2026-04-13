# TheSchoolVibe

> Multi-tenant SaaS platform for music schools — built for **PY Rock Music School** (5 New Jersey locations, 1,500+ students, 40+ teachers).

[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)](https://nextjs.org)
[![Expo](https://img.shields.io/badge/Expo-SDK_54-000020?logo=expo)](https://expo.dev)
[![tRPC](https://img.shields.io/badge/tRPC-v11-398CCB)](https://trpc.io)
[![Neon](https://img.shields.io/badge/PostgreSQL-Neon-00E5BF)](https://neon.tech)
[![Vercel](https://img.shields.io/badge/Deployed-Vercel-black?logo=vercel)](https://vercel.com)
[![Status](https://img.shields.io/badge/Status-Production-brightgreen)]()

---

## Overview

TheSchoolVibe is a full-stack SaaS platform that digitizes the complete operational lifecycle of a music school: student enrollment (with digital signatures), class scheduling, teacher management, payment tracking, and a native mobile app for parents, teachers, and admins.

Architected as a **Turborepo monorepo** with a shared type system across web and mobile.

---

## The Problem

PY Rock Music School managed 1,500+ students across 5 locations using spreadsheets and manual processes — no centralized enrollment, no digital signatures, no mobile access for teachers or parents, and no cross-location visibility.

---

## Key Features

### 🌐 Web Admin Panel (`apps/web`)
- **Dashboard** — cross-location KPIs and activity feed
- **Students** — full CRUD with photo upload (Cloudflare R2), enrollment history, and parent contacts
- **Teachers** — profile management, schedule assignment, availability
- **Schedules** — class creation with multi-student enrollment, room and instrument assignment
- **Payments** — payment tracking per student, due dates, and status
- **CRM Kanban** — lead pipeline for prospect students
- **Tickets** — internal issue tracking
- **Landing Pages** — `/rock-academy`, `/py-rock` per-tenant public pages

### 📱 Mobile App (`apps/mobile`) — 17 Screens
Role-based native experience for three user types:

| Role | Key Screens |
|---|---|
| **Parent** | Student dashboard, schedule view, payment history, notifications |
| **Teacher** | Daily schedule, class roster, attendance, student notes |
| **Admin** | Full visibility across all roles, approval actions |

Delivered via **Expo Go** with live tunnel through **ngrok**.

### ✍️ Digital Enrollment Flow
- Multi-step enrollment form
- Digital signature capture
- Policy acceptance with timestamp
- PDF generation for records

### 📸 Photo Management
- Student profile photos uploaded to **Cloudflare R2**
- Optimized delivery via signed URLs

---

## Tech Stack

| Layer | Technology |
|---|---|
| Monorepo | Turborepo |
| Web Frontend | Next.js 14 (App Router) |
| Mobile | Expo SDK 54 (React Native) |
| API Layer | tRPC v11 |
| Database | Neon PostgreSQL |
| Auth | NextAuth.js |
| Storage | Cloudflare R2 |
| Web Hosting | Vercel (branch: `develop`) |
| Mobile Dev | Expo Go via ngrok tunnel |

---

## Architecture

```
theschoolvibe/
├── apps/
│   ├── web/          # Next.js 14 admin panel
│   └── mobile/       # Expo SDK 54 mobile app
├── packages/
│   ├── db/           # Prisma schema + Neon client
│   ├── trpc/         # Shared tRPC router
│   └── ui/           # Shared component library
```

The shared tRPC layer enforces a **single source of truth** for types and business logic across both platforms — changes to the API schema are immediately reflected in both web and mobile.

---

## Multi-Tenancy

Each music school operates as an isolated tenant with:
- Scoped database queries per `tenantId`
- Custom landing pages per tenant slug
- Per-tenant branding and configuration
- Isolated student/teacher/schedule data

---

## Status

✅ **Deployed to Vercel** — web admin panel live on `develop` branch.
📱 **Mobile app** running via Expo Go across iOS and Android devices.

---

*Built solo as a full-stack engineer using Next.js 14, Expo SDK 54, tRPC, and Claude Code as the primary AI development accelerator.*
