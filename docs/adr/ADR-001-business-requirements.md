# ADR-001: Business Requirements and MVP Scope

**Status:** Accepted
**Date:** 2026-10-31 (Sanani o'zingizga moslang)
**Decision Makers:** Startup Founder / CTO

## Context
G'ildirak platformasi O'zbekiston avtomobil bozori uchun mo'ljallangan. Hozirda ehtiyot qismlarini topish, ularning mosligini tekshirish va narxlarni taqqoslash jarayoni tarqoq (Telegram guruhlari, bozorlar). Platforma ushbu muammoni bitta joyda hal qilishi kerak.

## Problem
Biznes talablari juda keng (Marketplace, Servislar, Roadside Assistance, B2B, B2C). Agar hammasini birinchi versiyada qilishga urinsak, loyiha cho'zilib ketadi va bozorga chiqish kechikadi.

## Alternatives
1. **Full-Scope Launch:** Barcha funksiyalarni (3D model, onlayn to'lov, roadside assistance) birinchi kundan qilish. (Rad etildi: juda ko'p vaqt va resurs talab qiladi).
2. **MVP (Minimum Viable Product):** Faqat eng kerakli funksiyalarni qilib, bozorga tez chiqish. (Tanlandi).

## Decision
Loyihaning birinchi versiyasi (MVP) uchun quyidagi funksiyalar kiritiladi:
*   **Identity:** Customer va Seller ro'yxatdan o'tishi, Admin tasdiqlashi.
*   **Marketplace:** Avtomobil tanlash, mahsulot katalogi, moslikni tekshirish (asosiy darajada).
*   **Commerce:** Savat, Buyurtma yaratish (To'lov hozircha naqd yoki yetkazib berishda).
*   **Logistics:** Yetkazib berish manzilini kiritish (asosiy).
*   **Web Frontend & Flutter Mobile:** Asosiy sahifalar (Home, Catalog, Product, Cart, Profile).

**MVP ga KIRMAYDI (Keyingi bosqichlar uchun):**
*   3D avtomobil modeli (dastlab oddiy rasmlar bilan ishlaymiz).
*   Onlayn to'lov (Click/Payme) integratsiyasi.
*   Roadside Assistance (Yo'lda yordam).
*   B2B uchun murakkab narxlash tizimi.

## Consequences
*   **Afzallik:** Mahsulotni tezroq bozorga chiqarish, real foydalanuvchilardan fikr-mulohaza olish.
*   **Kamchilik:** Ba'zi foydalanuvchilar 3D yoki onlayn to'lovni kutishi mumkin, lekin keyingi versiyalarda qo'shiladi.

## Implementation Plan
1. Dizayn (Figma) faqat MVP doirasida sahifalarni tayyorlaydi.
2. Backend va Frontend MVP funksiyalariga fokuslanadi.
3. 3D va to'lov modullari MVP chiqqandan keyin rejalashtiriladi.