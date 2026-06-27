---
document_id: WORLD-005
title: World Specification - Parcel System
version: 1.0.0
status: DRAFT
owner: Founder & Chief Architect
repository: sabumi-constitution
last_updated: 2026-06-27
depends_on:
  - WORLD-004
---

# WORLD SPECIFICATION - PARCEL SYSTEM

---

## PART E: PARCEL SYSTEM

### 64. PARCEL PHILOSOPHY
* Parcel merupakan unit operasional terkecil yang dapat digunakan Citizen untuk melakukan aktivitas ekonomi, pembangunan, produksi, konservasi, penelitian, maupun pelayanan publik.
* Land adalah kepemilikan. Parcel adalah pemanfaatannya.
* Dengan memisahkan Land dan Parcel, perubahan penggunaan lahan tidak akan mengubah identitas Land.

### 65. PARCEL PURPOSE
* Parcel digunakan sebagai dasar seluruh gameplay.
* Semua aktivitas berikut selalu terjadi pada Parcel:
  * membangun rumah
  * menanam bambu
  * menanam padi
  * menanam sayuran
  * kolam ikan
  * peternakan
  * workshop
  * pabrik
  * sekolah
  * klinik
  * marketplace
  * taman
  * jalan
  * utilitas
* Tidak ada gameplay yang langsung terjadi pada Land.

### 66. PARCEL RELATIONSHIP
```text
World → District → Region → Land → Parcel → Tile → Object
```
* Land memiliki banyak Parcel.
* Parcel memiliki banyak Tile.
* Tile memiliki banyak Object.

### 67. PARCEL ENTITY
Parcel merupakan Aggregate Root pada modul Parcel. Minimal memiliki atribut berikut:
* ParcelID
* LandID
* ParcelNumber
* DistrictID
* RegionID
* Coordinate
* Width
* Length
* Area
* ParcelType
* CurrentUsage
* OwnerID
* DevelopmentLevel
* TerrainType
* Slope
* Elevation
* SoilType
* WaterAvailability
* ElectricityAvailable
* RoadAccess
* InternetCoverage
* CarbonScore
* EcologyScore
* ProductivityScore
* ConstructionStatus
* CurrentBuildingID
* CreatedAt
* UpdatedAt

### 68. PARCEL TYPES
Versi pertama mendukung tipe berikut:
* Residential Parcel
* Agriculture Parcel
* Bamboo Plantation Parcel
* Livestock Parcel
* Fishery Parcel
* Industrial Parcel
* Education Parcel
* Tourism Parcel
* Conservation Parcel
* Commercial Parcel
* Infrastructure Parcel
* Utility Parcel
* Public Facility Parcel

### 69. PARCEL STATE
Parcel memiliki lifecycle:
```text
Available → Reserved → Developing → Operational → Productive → Upgradeable → Advanced
```
State menentukan aksi yang diperbolehkan.

### 70. SINGLE PRIMARY FUNCTION RULE
* Satu Parcel hanya memiliki satu fungsi utama. Contoh: Parcel → Agriculture (tidak boleh menjadi Factory secara bersamaan).
* Namun Parcel dapat memiliki objek pendukung. Contoh: **Sawah + Sumur + Gudang kecil + Panel Surya**.

### 71. BUILDABLE RULE
Tidak semua Parcel dapat dibangun. Contoh:
* **River Parcel** → Tidak dapat dibangun rumah.
* **Mountain Cliff** → Tidak dapat dibangun sawah.
* **Protected Forest** → Tidak dapat dibangun pabrik.
* **Mangrove** → Tidak dapat menjadi kawasan industri.

### 72. PARCEL LEVEL
Setiap Parcel mempunyai Level:
* Level 1: Natural
* Level 2: Developed
* Level 3: Optimized
* Level 4: Modernized
* Level 5: Smart Parcel
* Semakin tinggi level, semakin besar efisiensi.

### 73. PARCEL PRODUCTIVITY
Productivity dihitung berdasarkan:
```text
Soil × Water × Technology × Knowledge × Ecology × Maintenance × Infrastructure
```
Nilai akhir berada pada rentang **0 – 100**.

### 74. PARCEL ECOLOGY
Parcel memiliki Ecology Score. Dipengaruhi oleh:
* Vegetation
* Tree Density
* Bamboo Density
* Waste
* Water Quality
* Renewable Energy
* Pollution
* Carbon Storage

### 75. PARCEL SERVICES
Parcel dapat memperoleh layanan:
* Road
* Electricity
* Clean Water
* Internet
* Drainage
* Waste Collection
* Emergency Service
* Security
* Education
* Healthcare
* *Aturan*: Semakin lengkap layanan, semakin tinggi nilai Parcel.

### 76. PARCEL IMPROVEMENT
Parcel dapat ditingkatkan. Contoh:
* Irrigation
* Solar Panel
* Smart Sensor
* Greenhouse
* Automatic Watering
* Composting Area
* Rain Water Harvesting
* Storage
* Cold Storage
* Drone Landing Pad

### 77. PARCEL VALIDATION RULES
AI **SHALL** validate:
* Building Type
* Land Ownership
* District Rule
* Road Access
* Water Access
* Parcel Status
* Parcel Capacity
* Ecology Limit
* Carbon Policy
* Government Policy
* *Aturan*: Semua validasi dilakukan sebelum pembangunan.

### 78. PARCEL EVENTS
Parcel dapat mengalami:
* Harvest
* Construction
* Upgrade
* Fire
* Flood
* Disease
* Pest Attack
* Technology Upgrade
* Research Trial
* Festival
* Inspection
* Carbon Audit

### 79. PARCEL ANALYTICS
Setiap Parcel menghasilkan data:
* Production
* Maintenance Cost
* Income
* Carbon Storage
* Energy Usage
* Water Usage
* Waste Generation
* Ecology Trend
* Citizen Activity
* Building Utilization
* *Aturan*: Semua data menjadi dasar AI Analytics.

### 80. PARCEL DOMAIN EVENTS
Perubahan Parcel menghasilkan Domain Event:
* ParcelClaimed
* ParcelReleased
* ParcelReserved
* ParcelConstructionStarted
* ParcelConstructionCompleted
* ParcelHarvested
* ParcelImproved
* ParcelDamaged
* ParcelRecovered
* ParcelTransferred
* ParcelInspected
* ParcelAudited
* *Aturan*: Semua event disimpan permanen.

### 81. PARCEL DATABASE DRAFT
Entity utama:
* Parcel
* ParcelHistory
* ParcelEvent
* ParcelService
* ParcelImprovement
* ParcelEcology
* ParcelAnalytics
* ParcelOwnership
* ParcelBuilding

### 82. PARCEL API CONTRACT (DRAFT)
REST Endpoint:
* `GET /api/parcels`
* `GET /api/parcels/{id}`
* `POST /api/parcels`
* `PATCH /api/parcels/{id}`
* `DELETE /api/parcels/{id}`
* `POST /api/parcels/{id}/claim`
* `POST /api/parcels/{id}/upgrade`
* `POST /api/parcels/{id}/construct`
* `POST /api/parcels/{id}/harvest`
* `POST /api/parcels/{id}/inspect`

### 83. AI IMPLEMENTATION CONTRACT
AI **SHALL** generate:
* Parcel Aggregate
* Parcel Entity
* Parcel Repository
* Parcel Domain Service
* Parcel Application Service
* Parcel Controller
* Parcel Event Publisher
* Parcel Validation Service
* Parcel Analytics Service
* Parcel Ecology Service
* Parcel Upgrade Service
* Parcel History Service

AI **SHALL NOT**:
* Store business logic inside Controller.
* Mix Parcel logic with Building logic.
* Bypass Validation.
* Hardcode Parcel Type.
* Skip Domain Events.

### 84. TRACEABILITY
Parcel System menjadi dasar:
* Building System
* Housing System
* Farming System
* Livestock System
* Fishery System
* Factory System
* Marketplace
* NPC AI
* Quest System
* Analytics Engine
* Carbon Engine

### 85. ACCEPTANCE CRITERIA
Parcel System dianggap selesai apabila:
* ✓ Parcel Entity tersedia.
* ✓ Parcel Aggregate tersedia.
* ✓ Repository tersedia.
* ✓ Domain Event tersedia.
* ✓ Validation tersedia.
* ✓ REST API tersedia.
* ✓ Database Schema tersedia.
* ✓ Analytics tersedia.
* ✓ Ecology tersedia.
* ✓ AI dapat menghasilkan implementasi tanpa asumsi tambahan.
