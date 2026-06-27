---
document_id: WORLD-006
title: World Specification - Tile System
version: 1.0.0
status: DRAFT
owner: Founder & Chief Architect
repository: sabumi-constitution
last_updated: 2026-06-27
depends_on:
  - WORLD-005
---

# WORLD SPECIFICATION - TILE SYSTEM

---

## PART F: TILE SYSTEM

### 86. TILE PHILOSOPHY
* Tile merupakan unit simulasi terkecil dalam dunia SABUMI.
* Seluruh perubahan dunia terjadi pada Tile.
* Tile bukan sekadar koordinat.
* Tile merupakan "Simulation Cell" yang menyimpan kondisi fisik, ekologi, aktivitas, dan histori lingkungan.
* Seluruh sistem dunia dibangun di atas Tile.

### 87. TILE OBJECTIVES
Tile dirancang untuk:
* menjalankan simulasi dunia
* menyimpan kondisi lingkungan
* menjadi dasar pembangunan
* menjadi dasar pertanian
* menjadi dasar ekologi
* menjadi dasar AI Navigation
* menjadi dasar Pathfinding
* menjadi dasar Carbon Simulation
* menjadi dasar Resource Simulation

### 88. TILE RELATIONSHIP
```text
World → District → Region → Land → Parcel → Tile → Object
```
* Tile merupakan child dari Parcel.
* Object berada di atas Tile.

### 89. TILE ENTITY
Tile memiliki atribut minimal:
* TileID
* ParcelID
* CoordinateX
* CoordinateY
* GlobalCoordinate
* TerrainType
* Height
* Slope
* Temperature
* Humidity
* Moisture
* Fertility
* Sunlight
* WindExposure
* WaterLevel
* CarbonStorage
* EcologyScore
* Occupied
* Walkable
* Buildable
* MovementCost
* CurrentObjectID
* CreatedAt
* UpdatedAt

### 90. TILE TYPES
Tile dibagi menjadi beberapa kategori:
* Grass
* Forest
* Bamboo
* Road
* River
* Lake
* Bridge
* Farm
* RiceField
* Garden
* Rock
* Sand
* Mountain
* Wetland
* Village
* Industrial
* Marketplace
* Tourism
* Public Area
* Future Expansion

### 91. TILE STATE
Tile memiliki kondisi:
* Empty
* Occupied
* Reserved
* UnderConstruction
* Growing
* HarvestReady
* Flooded
* Burned
* Protected
* Inactive
* *Aturan*: Tile State berubah secara dinamis.

### 92. TILE ENVIRONMENT
Setiap Tile memiliki kondisi lingkungan:
* Temperature
* Humidity
* Rainfall
* Water Flow
* Soil Quality
* Fertility
* Wind
* Light
* Shadow
* Pollution
* Carbon
* *Aturan*: Seluruh parameter diperbarui oleh World Simulation.

### 93. TILE RESOURCE
Tile dapat menyimpan Resource. Contoh:
* Bamboo
* Tree
* Water
* Stone
* Food
* Fish
* Soil
* Grass
* Wild Plant
* Mineral
* *Aturan*: Setiap Resource mempunyai lifecycle.

### 94. TILE BUILDING RULES
Building hanya dapat dibangun apabila:
* Tile Buildable = TRUE
* Ecology memenuhi syarat.
* Slope memenuhi syarat.
* Tidak berada di River.
* Tidak berada di Protected Area.
* Road Access tersedia.
* Water tersedia.
* *Aturan*: Validation dilakukan sebelum pembangunan.

### 95. TILE ECOLOGY
Tile menyimpan data ekologi:
* Vegetation Density
* Carbon
* Tree Cover
* Water Absorption
* Bamboo Density
* Wildlife
* Waste
* Air Quality
* *Aturan*: Ecology berubah setiap simulasi.

### 96. TILE GROWTH ENGINE
Pertumbuhan tanaman dihitung berdasarkan:
```text
Growth = Species × Sunlight × Water × Temperature × Fertility × Technology Bonus × Knowledge Bonus
```
Nilai diperbarui setiap World Tick.

### 97. TILE WATER SYSTEM
Tile menyimpan:
* Water Level
* Ground Water
* Surface Water
* Drainage
* Flood Risk
* Irrigation
* Rain Collection
* *Aturan*: Semua saling mempengaruhi.

### 98. TILE ENERGY SYSTEM
Tile dapat menghasilkan energi:
* Solar
* Wind
* Biomass
* Hydro
* *Aturan*: Energy digunakan oleh Building.

### 99. TILE CARBON SYSTEM
Tile menyimpan:
* Carbon Storage
* Carbon Capture
* Carbon Release
* Carbon Balance
* *Aturan*: Semua Bamboo Tile meningkatkan Carbon Storage.

### 100. TILE MOVEMENT
Movement Cost:
* Grass: **1**
* Road: **0.5**
* Bridge: **0.7**
* Forest: **2**
* Mountain: **5**
* River: **∞**
* *Aturan*: Movement digunakan AI Pathfinding.

### 101. TILE COLLISION
Tile menyimpan status collision:
* Walkable
* Blocked
* Water
* Bridge
* Building
* Temporary Object
* *Aturan*: Collision diperiksa sebelum perpindahan.

### 102. TILE OBJECT OCCUPANCY
Satu Tile dapat memiliki:
* Ground Layer
* Vegetation Layer
* Object Layer
* Effect Layer
* Visual Layer
* *Aturan*: Pendekatan ini memungkinkan beberapa objek berada pada Tile yang sama.

### 103. TILE SIMULATION TICK
World berjalan menggunakan Tick.
* **Default**: 1 Tick = 1 menit dunia.
* Setiap Tick memperbarui: Weather, Plant, Animal, Citizen, NPC, Market, Carbon, Energy, Quest, Analytics.

### 104. TILE DOMAIN EVENTS
Tile menghasilkan event:
* TileCreated
* TileUpdated
* TileOccupied
* TileFreed
* TileFlooded
* TileRecovered
* TileHarvested
* TilePlanted
* TileBurned
* TileRestored
* TileCarbonUpdated
* TileEcologyUpdated

### 105. TILE DATABASE DRAFT
Entity:
* Tile
* TileEnvironment
* TileHistory
* TileResource
* TileCarbon
* TileEcology
* TileOccupancy
* TileAnalytics
* TileEvent

### 106. TILE API DRAFT
* `GET /api/tiles`
* `GET /api/tiles/{id}`
* `PATCH /api/tiles/{id}`
* `POST /api/tiles/{id}/plant`
* `POST /api/tiles/{id}/harvest`
* `POST /api/tiles/{id}/construct`
* `POST /api/tiles/{id}/inspect`
* `GET /api/tiles/{id}/environment`
* `GET /api/tiles/{id}/history`

### 107. AI IMPLEMENTATION CONTRACT
AI **SHALL** generate:
* Tile Entity
* Tile Aggregate
* Tile Repository
* Tile Simulation Engine
* Tile Ecology Engine
* Tile Carbon Engine
* Tile Water Engine
* Tile Growth Engine
* Tile Analytics
* Tile API
* Tile Domain Events
* Tile Validation

AI **SHALL NOT**:
* Store Tile logic inside Parcel.
* Store Ecology inside Building.
* Hardcode Movement Cost.
* Bypass Simulation Tick.

### 108. PERFORMANCE REQUIREMENTS
Target:
* **Update 100.000 Tile**: < 200 ms
* **Chunk Loading**: < 100 ms
* **Memory**: Optimized for Mobile
* **Paralel**: Simulation harus dapat diproses secara paralel.

### 109. TILE TRACEABILITY
Tile menjadi dasar:
* Weather Engine
* Farming Engine
* Carbon Engine
* Water Engine
* Building Engine
* NPC AI
* Pathfinding
* Collision
* Quest Engine
* Analytics

### 110. ACCEPTANCE CRITERIA
Tile System dianggap selesai apabila:
* ✓ Tile Entity tersedia.
* ✓ Tile Repository tersedia.
* ✓ Simulation Tick tersedia.
* ✓ Ecology tersedia.
* ✓ Carbon tersedia.
* ✓ Water tersedia.
* ✓ Growth tersedia.
* ✓ Domain Event tersedia.
* ✓ REST API tersedia.
* ✓ AI dapat membangun implementasi tanpa asumsi tambahan.
