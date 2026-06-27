---
document_id: GOV-002
title: SABUMI Official Glossary
version: 1.0.0
status: APPROVED
owner: Chief Architect
repository: sabumi-constitution
last_updated: 2026-06-27
depends_on:
  - GOV-001
---

# OFFICIAL GLOSSARY

## Purpose
Dokumen ini mendefinisikan seluruh istilah resmi yang digunakan dalam proyek SABUMI.
Seluruh dokumen, source code, database, API, UI, AI Agent, dan dokumentasi lainnya **WAJIB** menggunakan istilah yang terdapat pada dokumen ini.
Tidak diperbolehkan membuat sinonim tanpa perubahan resmi melalui Architecture Decision Record (ADR).

## Naming Rules
1. Gunakan istilah ini secara konsisten.
2. Jangan menerjemahkan nama entity.
3. Hindari singkatan yang tidak didefinisikan.
4. Setiap istilah baru harus ditambahkan ke Glossary terlebih dahulu.

---

## Core Terms

### SABUMI
* Digital Bamboo Civilization Platform.
* Bukan sekadar game.
* Merupakan ekosistem digital yang menghubungkan simulasi, edukasi, ekonomi, industri, konservasi, dan komunitas.

### Citizen
* Entity utama yang dikendalikan pemain.
* Citizen mempunyai identitas permanen.
* Citizen dapat memiliki:
  * Land
  * House
  * Skill
  * Inventory
  * Profession
  * Reputation
* Citizen bukan User.
* Citizen bukan Account.

### User
* Pemilik akun.
* Satu User dapat memiliki satu atau lebih Citizen (fitur masa depan).

### Account
* Identitas autentikasi.
* Digunakan untuk Login.
* Tidak memiliki gameplay.

### Land
* Sebidang lahan yang dapat dimiliki Citizen.
* Land mempunyai:
  * koordinat
  * ukuran
  * zona
  * status
  * owner

### Parcel
* Unit terkecil pembagian Land.
* Semua pembangunan dilakukan pada Parcel.

### Building
* Objek permanen yang dibangun pada Parcel.
* Contoh:
  * House
  * School
  * Workshop
  * Factory
  * Clinic
  * Mosque

### District
* Wilayah besar dalam dunia SABUMI.
* Contoh:
  * Green Belt
  * Living District
  * Industrial District
  * Knowledge District
  * Innovation District
  * Eco Tourism District

### Green Belt
* Kawasan konservasi.
* Area utama penyerapan karbon.
* Area ini mempunyai aturan khusus.

### Knowledge Point (KP)
* Poin yang diperoleh melalui belajar.
* Digunakan membuka teknologi.
* Bukan mata uang.

### Experience Point (XP)
* Digunakan meningkatkan level Citizen.

### BMC
* BaMbooChain Utility Token.
* Digunakan sebagai aset digital dalam ekosistem.

### Marketplace
* Tempat transaksi digital.
* Mendukung:
  * barang
  * jasa
  * hasil panen
  * material
  * aset digital

### NPC
* Non Player Character.
* Dikendalikan AI.
* Memiliki jadwal hidup.
* Memiliki profesi.
* Memiliki kebutuhan.

### Profession
* Peran utama Citizen.
* Contoh:
  * Farmer
  * Fisherman
  * Builder
  * Researcher
  * Teacher
  * Doctor
  * Entrepreneur

### Inventory
* Daftar seluruh aset Citizen.

### Resource
* Material dasar.
* Contoh:
  * Bamboo
  * Water
  * Soil
  * Stone
  * Food

### Product
* Barang hasil produksi.
* Contoh:
  * Bamboo Panel
  * Furniture
  * House Module
  * Food

### Factory
* Bangunan produksi.
* Mengubah Resource menjadi Product.

### Quest
* Tugas yang diberikan sistem.
* Quest menghasilkan:
  * XP
  * KP
  * Reward

### Technology
* Pengetahuan yang sudah berhasil diteliti.
* Technology membuka fitur baru.

### Civilization Level
* Indikator perkembangan dunia SABUMI.
* Bukan level pemain.

### Reputation
* Ukuran kepercayaan masyarakat kepada Citizen.

### Carbon Credit
* Representasi digital hasil konservasi lingkungan.

### Event
* Kegiatan yang berlangsung pada waktu tertentu.

### Season
* Periode permainan.
* Digunakan untuk:
  * kompetisi
  * festival
  * leaderboard

---

## Reserved Terms
Istilah berikut tidak boleh digunakan sebagai nama entity:
* Object
* Data
* ItemData
* Manager
* Utils
* Helper
* Common

*Gunakan nama domain yang jelas.*

---

## AI Naming Rules
AI Agent **WAJIB**:
* menggunakan istilah pada Glossary;
* tidak membuat sinonim;
* tidak mengubah nama entity;
* tidak menerjemahkan nama entity;
* meminta klarifikasi apabila istilah belum tersedia.

---

## Change Procedure
Penambahan istilah baru harus:
1. Masuk ke Glossary.
2. Mendapatkan Document ID.
3. Direview.
4. Disetujui.
5. Baru boleh digunakan pada spesifikasi lain.

---

## Approval
Status: **APPROVED**

*Glossary ini merupakan kamus resmi SABUMI.*
