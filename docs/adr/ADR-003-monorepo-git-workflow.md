# ADR-003: Monorepo and Git Workflow

**Status:** Accepted
**Date:** 2026-10-31
**Decision Makers:** Startup Founder / CTO

## Context
G'ildirak loyihasi backend, frontend va mobile qismlaridan iborat. Ushbu qismlarni bitta repozitoriyada (Monorepo) saqlashmi yoki har biri uchun alohida repozitoriya ochishmi? Jamoa qanday qilib kod yozishi va versiyalarni boshqarishi kerak?

## Problem
Agar alohida repozitoriyalar ochilsa, API o'zgarishlarini sinxronlash qiyinlashadi va umumiy dokumentatsiyani yuritish qiyin bo'ladi. Tartibsiz Git ishlatilsa, kod tarixi chalkashadi va xatoliklarni topish qiyinlashadi.

## Alternatives
1. **Polyrepo (Alohida repozitoriyalar):** Har bir qism uchun alohida repo. (Rad etildi: kichik jamoa uchun ortiqcha murakkablik va sinxronlash muammosi).
2. **Monorepo + Tartibsiz Git:** Bitta repo, lekin branch va commit qoidalarisiz. (Rad etildi: kod tarixi chalkashadi).
3. **Monorepo + Git Flow + Conventional Commits:** Bitta repo, qat'iy branch strategiyasi va commit qoidalari bilan. (Tanlandi).

## Decision
Barcha kodlar bitta **Monorepo** (`gildirak/`) ichida saqlanadi. Biz quyidagi Git strategiyasini qo'llaymiz:

**Branch Strategiyasi:**
*   `main` — Production muhiti uchun. Faqat `develop` dan merge qilinadi.
*   `develop` — Asosiy ishlab chiqish branch'i.
*   `feature/<nomi>` — Yangi funksiyalar uchun (masalan: `feature/product-catalog`).
*   `bugfix/<nomi>` — Xatoliklarni tuzatish uchun.
*   `hotfix/<nomi>` — Production'dagi shoshilinch xatolar uchun.

**Commit Convention:**
Biz **Conventional Commits** standartidan foydalanamiz:
*   `feat:` — Yangi funksiya
*   `fix:` — Xatolik tuzatish
*   `docs:` — Hujjatlar
*   `style:` — Kod formati
*   `refactor:` — Kodni qayta yozish
*   `test:` — Testlar
*   `chore:` — Build va kutubxonalar

## Consequences
*   **Afzallik:** Bitta joyda barcha kod, oson deploy, tartibli tarix. CI/CD sozlash osonlashadi (path filter bilan).
*   **Kamchilik:** Repozitoriya hajmi kattalashadi, lekin zamonaviy Git buni bemalol ko'taradi.

## Implementation Plan
1. GitHub'da `main` va `develop` branch'larini yaratish.
2. Har bir yangi ish uchun `feature/` yoki `bugfix/` branch'ini ochish qoidasini joriy qilish.
3. Pull Request ochishda kamida 1 kishi (yoki o'zingiz) tomonidan ko'rib chiqilishini ta'minlash.
4. Commit yozishda yuqoridagi prefikslardan foydalanish.
