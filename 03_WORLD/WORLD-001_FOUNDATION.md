---
document_id: WORLD-001
title: World Specification - Foundation & Architecture
version: 1.0.0
status: DRAFT
owner: Founder & Chief Architect
repository: sabumi-constitution
last_updated: 2026-06-27
depends_on:
  - GOV-001
  - GOV-002
  - GOV-003
  - EXEC-001
---

# WORLD SPECIFICATION - FOUNDATION & ARCHITECTURE

---

## PART A: FOUNDATION

### 1. PURPOSE
Dokumen ini mendefinisikan seluruh spesifikasi resmi dunia virtual SABUMI.

Dokumen ini menjadi referensi utama bagi:
* Game Designer
* Gameplay Engineer
* Backend Engineer
* AI Agent
* World Builder
* Database Engineer
* Economy Designer
* NPC Designer
* UI/UX Designer

Semua implementasi dunia virtual **WAJIB** mengikuti spesifikasi ini.

### 2. WORLD DEFINITION
* SABUMI bukan sekadar peta permainan.
* SABUMI adalah sebuah **Digital Bamboo Civilization**.
* Seluruh dunia merupakan simulasi kehidupan masyarakat yang berkembang secara terus menerus.
* Dunia tetap hidup meskipun pemain sedang offline.
* Semua perubahan dunia bersifat persisten.

### 3. WORLD PHILOSOPHY
SABUMI dibangun berdasarkan lima filosofi utama:

#### Living World
* Dunia tidak menunggu pemain.
* NPC tetap bekerja.
* Cuaca tetap berubah.
* Tanaman tetap tumbuh.
* Pasar tetap berjalan.
* Ekonomi tetap bergerak.

#### Sustainable World
* Seluruh pembangunan harus memperhatikan keseimbangan alam.
* Eksploitasi sumber daya secara berlebihan akan memberikan dampak negatif terhadap dunia.

#### Knowledge Driven World
* Kemajuan dunia ditentukan oleh pengetahuan.
* Teknologi baru hanya dapat dibuka melalui proses pembelajaran, penelitian, dan inovasi.

#### Collaborative Civilization
* Perkembangan desa lebih penting daripada perkembangan individu.
* Sistem permainan mendorong kolaborasi antar Citizen.

#### Persistent Civilization
* Semua hasil pembangunan bersifat permanen.
* Rumah yang dibangun tetap ada.
* Jalan yang dibuat tetap digunakan.
* Pohon yang ditanam akan terus tumbuh.

### 4. WORLD OBJECTIVES
Dunia SABUMI dirancang agar mampu:
* mensimulasikan kehidupan desa;
* membangun ekonomi bambu;
* mengembangkan industri;
* mendukung penelitian;
* membangun komunitas;
* menghubungkan aktivitas virtual dengan aktivitas nyata.

### 5. HIGH LEVEL WORLD MODEL
Secara konseptual dunia SABUMI terdiri atas beberapa lapisan:

```text
Civilization
  ↓
District
  ↓
Region
  ↓
Land
  ↓
Parcel
  ↓
Tile
  ↓
Object
```

#### Penjelasan:
* **Civilization**: Seluruh dunia SABUMI.
* **District**: Zona besar dengan fungsi tertentu. Contoh: Living District, Green Belt, Industrial District, Knowledge District, Innovation District, Eco Tourism District.
* **Region**: Sub-area dalam District. Digunakan untuk pengelompokan administrasi dan optimasi sistem. (Lihat detail di [WORLD-003_REGION_SPECIFICATION.md](file:///c:/Users/dummy/Documents/Projects/sabumi/constitution/03_WORLD/WORLD-003_REGION_SPECIFICATION.md))
* **Land**: Lahan yang dapat dimiliki Citizen.
* **Parcel**: Bagian kecil dari Land. Semua pembangunan dilakukan pada Parcel.
* **Tile**: Unit koordinat terkecil dunia.
* **Object**: Objek yang berada pada Tile. Contoh: Bamboo, House, Tree, Bridge, River, Rock, Road.

### 6. WORLD SCALE
* SABUMI dirancang sebagai dunia yang dapat berkembang tanpa batas (Expandable World).
* Versi pertama hanya membuka sebagian kecil wilayah.
* Wilayah lain dapat dibuka secara bertahap.
* Konsep ini memungkinkan ekspansi dunia tanpa mengubah struktur dasar.

### 7. WORLD PRINCIPLES
Seluruh dunia mengikuti prinsip berikut:
* **Rule 1**: No Dead Area. Tidak boleh ada wilayah kosong tanpa fungsi.
* **Rule 2**: Everything Has Purpose. Seluruh objek harus mempunyai fungsi.
* **Rule 3**: Everything Can Grow. Seluruh sistem harus mendukung perkembangan.
* **Rule 4**: Everything Connected. Semua distrik saling terhubung.
* **Rule 5**: Everything Has Economy. Seluruh aktivitas menghasilkan nilai ekonomi.
* **Rule 6**: Everything Generates Knowledge. Seluruh aktivitas memberikan pengetahuan.
* **Rule 7**: Everything Leaves Impact. Semua tindakan pemain memberikan dampak terhadap dunia.

### 8. WORLD LIFECYCLE
Dunia memiliki siklus hidup:
```text
Planning → Settlement → Expansion → Development → Industrialization → Innovation → Civilization
```
Seluruh sistem permainan mengikuti urutan tersebut.

### 9. WORLD COMPONENTS
Dunia terdiri atas komponen utama berikut:

#### Natural Components
* Bamboo Forest
* River
* Lake
* Mountain
* Waterfall
* Valley
* Grassland
* Wetland

#### Human Components
* Village
* House
* Road
* Marketplace
* Workshop
* Factory
* School
* Mosque
* Clinic
* Gallery

#### Production Components
* Rice Field
* Vegetable Farm
* Bamboo Plantation
* Fish Pond
* Shrimp Pond
* Goat Farm
* Cow Farm
* Chicken Farm

#### Knowledge Components
* Bamboo Academy
* Research Center
* Laboratory
* Library
* Training Center

#### Innovation Components
* Startup Hub
* Digital Marketplace
* BMC Exchange
* NFT Gallery

### 10. AI IMPLEMENTATION NOTES
AI Agent **SHALL**:
* menganggap dunia sebagai sistem persisten;
* tidak menghapus objek permanen tanpa aturan;
* menghasilkan struktur kode berbasis `World` → `District` → `Region` → `Land` → `Parcel` → `Tile` → `Object`;
* menggunakan prinsip Domain Driven Design;
* menghindari hardcoded coordinate;
* mendukung ekspansi dunia tanpa migrasi besar.

### 11. TRACEABILITY
Dokumen ini menjadi dasar bagi:
* WORLD-002 District Specification
* WORLD-003 Region System
* WORLD-004 Land System
* WORLD-005 Parcel System
* WORLD-006 Tile System
* WORLD-007 Object System
* WORLD-008 Simulation Engine
* WORLD-009 Event Engine
* WORLD-010 Save Engine
* WORLD-011 Network Engine

---

## PART B: WORLD ARCHITECTURE

### 12. WORLD ARCHITECTURE OVERVIEW
* SABUMI menggunakan arsitektur dunia yang dirancang untuk terus berkembang (Expandable Persistent World).
* Seluruh dunia tidak dimuat sekaligus ke memori perangkat.
* Dunia dibagi menjadi unit-unit kecil yang dapat dimuat (load) dan dilepas (unload) secara dinamis sesuai posisi Citizen.
* Pendekatan ini memastikan SABUMI dapat berjalan pada perangkat mobile tanpa mengorbankan ukuran dunia.

### 13. WORLD HIERARCHY
Seluruh struktur dunia mengikuti hirarki berikut:
```text
World
 └── District
      └── Region
           └── Land
                └── Parcel
                     └── Tile
                          └── Object
```
* Setiap level memiliki tanggung jawab yang jelas.
* Tidak diperbolehkan melompati hirarki.

### 14. WORLD ENTITY
* Hanya terdapat satu World aktif.
* Entity World menyimpan:
  * World ID
  * World Name
  * World Seed
  * World Version
  * Civilization Level
  * Current Season
  * Current Weather
  * Current Day
  * Global Economy State
  * Global Event State
* World merupakan root entity seluruh permainan.

### 15. WORLD COORDINATE SYSTEM
SABUMI menggunakan koordinat dunia berbasis grid:
```text
World → District → Region → Land → Parcel → Tile
```
Setiap Tile mempunyai koordinat unik.
* **Contoh**: District (Living District), Region (03), Land (0045), Parcel (12), Tile (X=18, Y=26).
* Koordinat harus bersifat deterministik.
* AI Agent tidak diperbolehkan menggunakan posisi acak tanpa seed.

### 16. WORLD SEED
* Seluruh dunia dibuat berdasarkan World Seed.
* World Seed digunakan untuk:
  * penempatan vegetasi
  * distribusi batu
  * bentuk sungai
  * kontur bukit
  * variasi biome
  * variasi pohon
  * spawn object
* Dengan seed yang sama maka dunia harus identik.

### 17. CHUNK SYSTEM
* Dunia dibagi menjadi Chunk.
* Chunk merupakan unit streaming. Contoh: **64 x 64 Tile**.
* Setiap Chunk mempunyai:
  * Chunk ID
  * Position
  * Loaded State
  * Active Object
  * NPC Count

### 18. STREAMING SYSTEM
* Perangkat hanya memuat Chunk di sekitar Citizen.
* **Contoh**: Player → **3 x 3 Chunk** or **5 x 5 Chunk** (tergantung kemampuan perangkat).
* Chunk di luar radius akan dilepas dari memori.

### 19. WORLD STREAMING RULES
* **Rule 001**: Chunk terdekat selalu diprioritaskan.
* **Rule 002**: Chunk yang berisi Citizen lain diprioritaskan.
* **Rule 003**: Chunk yang berisi Event tidak boleh di-unload.
* **Rule 004**: Chunk Marketplace tetap aktif.
* **Rule 005**: Chunk Village Center memiliki prioritas tertinggi.

### 20. DISTRICT ARCHITECTURE
* Setiap District bersifat modular.
* District memiliki:
  * District ID
  * Name
  * Category
  * Population
  * Prosperity
  * Ecology Index
  * Economy Index
  * Knowledge Index
* District dapat berkembang secara independen.

### 21. REGION ARCHITECTURE
Detail arsitektur Region dapat dilihat pada [WORLD-003_REGION_SPECIFICATION.md](file:///c:/Users/dummy/Documents/Projects/sabumi/constitution/03_WORLD/WORLD-003_REGION_SPECIFICATION.md).

### 22. LAND ARCHITECTURE
Detail arsitektur Land dapat dilihat pada [WORLD-004_LAND_SPECIFICATION.md](file:///c:/Users/dummy/Documents/Projects/sabumi/constitution/03_WORLD/WORLD-004_LAND_SPECIFICATION.md).

### 23. PARCEL ARCHITECTURE
Detail arsitektur Parcel dapat dilihat pada [WORLD-005_PARCEL_SPECIFICATION.md](file:///c:/Users/dummy/Documents/Projects/sabumi/constitution/03_WORLD/WORLD-005_PARCEL_SPECIFICATION.md).

### 24. TILE ARCHITECTURE
Detail arsitektur Tile dapat dilihat pada [WORLD-006_TILE_SPECIFICATION.md](file:///c:/Users/dummy/Documents/Projects/sabumi/constitution/03_WORLD/WORLD-006_TILE_SPECIFICATION.md).

### 25. OBJECT ARCHITECTURE
Detail arsitektur Object dapat dilihat pada [WORLD-007_OBJECT_SPECIFICATION.md](file:///c:/Users/dummy/Documents/Projects/sabumi/constitution/03_WORLD/WORLD-007_OBJECT_SPECIFICATION.md).

### 26. WORLD STATE
Dunia mempunyai State:
```text
Planning → Settlement → Growth → Industrialization → Innovation → Civilization
```
State menentukan fitur yang tersedia.

### 27. PERFORMANCE TARGET
Target minimum:
* **Loading World**: < 5 detik
* **Chunk Loading**: < 100 ms
* **Frame Rate**: 60 FPS (target), 30 FPS minimum
* **Memory**: ≤ 2 GB RAM
* **Storage**: World Data harus dapat dikompresi.

### 28. AI IMPLEMENTATION RULES
AI **SHALL**:
* membuat WorldManager
* membuat ChunkManager
* membuat StreamingManager
* membuat DistrictManager
* membuat RegionManager
* membuat TileManager
* membuat WorldStateManager

AI **SHALL NOT**:
* menyimpan seluruh dunia di memori
* menggunakan koordinat acak
* menghubungkan gameplay langsung ke Tile tanpa melalui Domain Layer

### 29. TRACEABILITY
Dokumen ini menjadi dasar bagi:
* WORLD-002 District Specification
* WORLD-003 Region System
* WORLD-004 Land System
* WORLD-005 Tile System
* WORLD-006 Chunk System
* WORLD-007 Streaming System
* WORLD-008 Object System
* WORLD-009 Pathfinding
* WORLD-010 Navigation
* WORLD-011 NPC AI
* WORLD-012 Performance Optimization
