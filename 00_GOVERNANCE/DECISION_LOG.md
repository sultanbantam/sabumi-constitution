---
document_id: GOV-003
title: Architecture Decision Register
version: 1.0.0
status: APPROVED
owner: Chief Architect
repository: sabumi-constitution
last_updated: 2026-06-27
depends_on:
  - GOV-001
  - GOV-002
---

# ARCHITECTURE DECISION REGISTER (ADR)

## Purpose
Dokumen ini mencatat seluruh keputusan arsitektur resmi pada proyek SABUMI.
Setiap keputusan memiliki nomor ADR yang unik.
Tidak diperbolehkan mengubah keputusan tanpa membuat ADR baru.

---

## ADR-001
* **Title**: SABUMI is a Digital Bamboo Civilization Platform
* **Status**: Accepted
* **Decision**:
  * SABUMI bukan sekadar permainan (game).
  * SABUMI adalah platform Digital Bamboo Civilization.
  * Game hanyalah salah satu antarmuka.
* **Reason**: Dengan pendekatan ini, seluruh modul seperti Marketplace, Carbon, Bamboo Academy, Research, Tourism, dan Governance dapat menggunakan dunia yang sama.

---

## ADR-002
* **Title**: Documentation First Development
* **Status**: Accepted
* **Decision**:
  * Dokumentasi merupakan sumber utama.
  * Source Code mengikuti dokumentasi.
  * Bukan sebaliknya.

---

## ADR-003
* **Title**: AI Native Specification
* **Status**: Accepted
* **Decision**:
  * Seluruh spesifikasi wajib dapat dibaca AI.
  * Semua aturan bisnis harus berada di repository.
  * AI tidak diperbolehkan menebak aturan.

---

## ADR-004
* **Title**: Single Source of Truth
* **Status**: Accepted
* **Decision**:
  * Repository **sabumi-constitution** merupakan satu-satunya sumber kebenaran.
  * Tidak diperbolehkan membuat dokumentasi lain di luar repository.

---

## ADR-005
* **Title**: Domain Driven Design
* **Status**: Accepted
* **Decision**:
  * Seluruh software menggunakan pendekatan Domain Driven Design.
  * Entity mengikuti bahasa bisnis.

---

## ADR-006
* **Title**: API First
* **Status**: Accepted
* **Decision**:
  * Seluruh komunikasi antar modul dilakukan menggunakan kontrak API.

---

## ADR-007
* **Title**: Modular Monolith First
* **Status**: Accepted
* **Decision**:
  * Versi pertama menggunakan Modular Monolith.
  * Microservices dilakukan setelah domain stabil.

---

## ADR-008
* **Title**: Git Repository Strategy
* **Status**: Accepted
* **Decision**:
  * Spesifikasi dipisahkan dari source code.
  * Repository:
    * `sabumi-constitution`
    * `sabumi-backend`
    * `sabumi-frontend`
    * `sabumi-game`
    * `sabumi-assets`
    * `sabumi-infra`

---

## ADR-009
* **Title**: Documentation Language
* **Status**: Accepted
* **Decision**:
  * Dokumen ditulis menggunakan Markdown.
  * Diagram menggunakan Mermaid.
  * Spesifikasi API menggunakan OpenAPI.
  * Diagram UML menggunakan PlantUML.

---

## ADR-010
* **Title**: AI Development Policy
* **Status**: Accepted
* **Decision**:
  * AI Agent wajib:
    * membaca seluruh Constitution;
    * mengikuti Glossary;
    * tidak membuat asumsi;
    * meminta klarifikasi bila spesifikasi belum tersedia.

---

## Future ADR
Seluruh keputusan berikutnya **WAJIB** menggunakan format yang sama.

Nomor:
* ADR-011
* ADR-012
* ADR-013
* dan seterusnya.

---

## Approval
Status: **APPROVED**

*Dokumen ini merupakan register resmi seluruh keputusan arsitektur SABUMI.*
