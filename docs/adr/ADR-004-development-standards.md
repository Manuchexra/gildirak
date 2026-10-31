# ADR-004: Development Standards

**Status:** Accepted
**Date:** 2026-10-31
**Decision Makers:** Startup Founder / CTO

## Context
G'ildirak loyihasida backend (Java), web (React/TS) va mobile (Flutter/Dart) qismlari bor. Turli dasturchilar (yoki kelajakda jamoa) bir xil uslubda kod yozishi va loyiha tartibli rivojlanishi uchun umumiy qoidalar kerak.

## Problem
Agar qoidalar belgilanmasa, kod chalkashadi, fayllar juda kattalashib ketadi, xatoliklarni topish qiyinlashadi va yangi dasturchi loyihaga kirishda qiynaladi.

## Alternatives
1. **Qoidasiz ishlash:** Har kim o'zicha yozadi. (Rad etildi: loyiha tezda boshqarib bo'lmaydigan holatga tushadi).
2. **Juda qattiq qoidalar:** Har bir satr uchun alohida qoidalar. (Rad etildi: ishlab chiqishni sekinlashtiradi).
3. **Balanslangan standartlar:** Asosiy qoidalar + avtomatik tekshiruv (linter). (Tanlandi).

## Decision

### 1. Fayl va Papka Tuzilmasi
*   Har bir papkada **maksimal 5 ta bevosita element** bo'ladi (papka yoki fayl).
*   Har bir kod fayli **1000 qatordan kam** bo'lishi kerak. Agar oshsa, uni kichikroq fayllarga bo'lish zarur.

### 2. Naming Convention (Nomlash qoidalari)
*   **Java (Backend):** Paketlar `kichik harflar`, klasslar `PascalCase`, o'zgaruvchilar va metodlar `camelCase`.
*   **React/TypeScript (Frontend):** Komponentlar `PascalCase`, funksiyalar va o'zgaruvchilar `camelCase`, fayllar `PascalCase.tsx` (komponentlar uchun) yoki `camelCase.ts` (util funksiyalar uchun).
*   **Flutter/Dart (Mobile):** Fayllar `snake_case.dart`, klasslar `PascalCase`, o'zgaruvchilar `camelCase`.
*   **Database:** Jadvallar va ustunlar `snake_case`.

### 3. API Naming Convention
*   URL'lar `kebab-case` bo'ladi: `/api/v1/product-catalog`
*   Resurs nomlari ko'plikda: `/products`, `/orders`, `/users`
*   Versiyalash: `/api/v1/...`

### 4. Error Handling (Xatoliklarni boshqarish)
*   Backend'da barcha xatolar `GlobalExceptionHandler` orqali ushlanadi.
*   Xato javoblari standart formatda bo'ladi:
    ```json
    {
      "timestamp": "2026-10-31T12:00:00Z",
      "status": 400,
      "error": "Bad Request",
      "message": "Mahsulot topilmadi",
      "path": "/api/v1/products/123"
    }
