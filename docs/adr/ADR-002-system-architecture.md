# ADR-002: System Architecture

**Status:** Accepted
**Date:** 2026-10-31
**Decision Makers:** Startup Founder / CTO

## Context
G'ildirak platformasi uchta asosiy qismdan iborat: Web (React), Mobile (Flutter) va Backend. Backend qanday arxitekturada qurilishi kerak? Microservices yoki Monolith?

## Problem
Microservices juda murakkab, kichik jamoa uchun DevOps yuklamasini oshiradi va dastlabki bosqichda ortiqcha xarajat qiladi. Ammo, kelajakda loyiha 100,000+ foydalanuvchiga xizmat ko'rsatishi kerak.

## Alternatives
1. **Microservices:** Har bir modul alohida servis. (Rad etildi: jamoa kichik, infratuzilma murakkablashadi).
2. **Classic Monolith:** Bitta katta loyiha, lekin ichki tuzilishi tartibsiz. (Rad etildi: kelajakda kod chalkashadi).
3. **Modular Monolith + DDD + Hexagonal Architecture:** Bitta ilova, lekin ichki modullar (Identity, Marketplace, Commerce) qat'iy ajratilgan. (Tanlandi).

## Decision
Backend **Java 21 + Spring Boot** yordamida **Modular Monolith** sifatida quriladi. Har bir biznes modul o'zining ichki qatlamlariga ega bo'ladi: `api`, `application`, `domain`, `infrastructure`, `web`. 

Web va Mobile ilovalar bitta **REST API** orqali backend bilan ishlaydi. Ular ma'lumotlar bazasiga to'g'ridan-to'g'ri ulanmaydi.

## Consequences
*   **Afzallik:** Dastlabki bosqichda deploy qilish oson (bitta Docker image). Kelajakda kerak bo'lsa, modullarni oson ajratib, microservice'ga o'tkazish mumkin.
*   **Kamchilik:** Bitta moduldagi xato butun tizimni to'xtatib qo'yishi mumkin (lekin yaxshi testlar bilan buni oldini olish mumkin).

## Implementation Plan
1. `backend/modules/` papkasida 5 ta asosiy modul yaratiladi: Identity, Marketplace, Commerce, Logistics, Engagement.
2. Modullar orasidagi bog'liqlik faqat `api` interfeyslari orqali bo'ladi (bir-birining ichki repository'siga kirmaydi).
3. Database (PostgreSQL) va Cache (Redis) uchun umumiy infratuzilma `shared/` papkasida bo'ladi.