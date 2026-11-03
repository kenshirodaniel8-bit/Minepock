# MinePock Champions

Game 3D browser bergaya voxel yang dimainkan dalam **3 tahap**:

1. **Tahap 1 – Buat Karakter.** Karakter voxel realistis yang tersusun dari ribuan kubus kecil.
2. **Tahap 2 – Survival Blok.** Menebang, menambang, crafting, berburu, memasak, membangun, dan bertahan di malam hari.
3. **Tahap 3 – Era Monster.** Menangkap, merawat, dan mengadu makhluk kotak-kotak ciptaan baru.

Info teknis:
* **Satu file:** `index.html` (Three.js r128 dari CDN + Web Audio API).
* **Semua aset prosedural:** tidak ada file gambar atau suara eksternal.
* **Cara menjalankan:** buka `index.html` di Chrome, Edge, atau Firefox (butuh internet untuk memuat Three.js). Bisa juga lewat server lokal, misalnya `python3 -m http.server`.

---

## 1. Alur bermain

1. **Title → PLAY.**
2. **Tahap 1: Buat Karakter.** Atur nama, warna kulit, 8 gaya rambut, warna rambut & mata, model baju (kaos/hoodie/jaket/jubah/gaun), celana, sepatu, topi, kacamata, dan ransel. Geser model untuk memutarnya. Tombol 🎲 mengacak penampilan.
3. **Main Room.** Pilih 1 dari 5 portal: Normal, Medium, Hard, Hardmon, Expert Moon.
4. **Tahap 2: Survival Blok.** Ikuti panel tugas di kiri:
   1. Tebang pohon (4 kayu)
   2. Buat Meja Crafting
   3. Buat Beliung Kayu
   4. Tambang 6 batu
   5. Berburu hewan (2 daging)
   6. Masak & makan Daging Panggang
   7. Bangun (taruh 12 block)
   8. Buat Obor

   Setiap tugas memberi hadiah. Tombol **⏭ Lewati** tersedia kalau ingin langsung ke Tahap 3.
5. **Temui Pak Bram di desa.** Pilih makhluk pertama. **Tahap 3: Era Monster** dimulai: makhluk liar muncul di seluruh dunia, dan battle, tangkap, rawat, evolusi, serta rival terbuka.
6. Bertahanlah! Kalau **nyawa** habis (atau hilang 7 sekaligus di Expert Moon) kamu **OUT DEAD**.

### Kontrol
| Aksi | PC | HP/Tablet |
|---|---|---|
| Jalan / lari / lompat | `WASD` / `Shift` / `Spasi` | joystick / LARI / LOMPAT |
| Kamera | drag mouse, `Q`/`E`, scroll | geser layar, KAM |
| Tambang / taruh block | tahan klik kiri / klik kanan | tahan layar / mode TARUH |
| Serang hewan, monster, makhluk | klik | ketuk |
| Interaksi / battle / lempar bola | `F` / `F` / `G` | F / F / G |
| **Makan** | `R` | Tas → Makan |
| Tas / Crafting / Makhluk / Menu | `I` / `C` / `P` / `Esc` | tombol di layar |

---

## 2. Model "kotak-kotak kecil" (micro-voxel)
Semua model tidak lagi memakai satu kotak besar. Setiap bagian tubuh dipahat dari ribuan kubus kecil (±3–5 cm per kubus) memakai bentuk dasar:
* elips / superelips untuk badan dan kepala,
* kapsul meruncing untuk kaki, ekor, tanduk, dan paruh,
* torus untuk cincin dan kerah.

Kubus-kubus itu digabung menjadi satu mesh per bagian (sisi tersembunyi dibuang), dengan warna per-kubus (bulu, bintik, garis, belang) dan mata berlapis (putih, iris, pupil, kilau). Geometri di-cache per spesies, jadi tetap ringan. Bagian tubuh tetap punya sendi sendiri, sehingga bisa dianimasikan: jalan, merumput, kepakan sayap, ekor, telinga, serangan, terluka, pingsan, dan evolusi.

## 3. Hewan (13 jenis, dengan HP, suara, animasi, dan drop)
| Hewan | Biome | Perilaku | Drop |
|---|---|---|---|
| Sapi (belang) | padang, desa, sabana | merumput, kawanan | daging, kulit |
| Domba (wol bergelombang) | padang, gunung, tundra | kawanan | daging, wol |
| Ayam | desa, padang | berkokok | daging, bulu |
| Babi Hutan (taring) | hutan, rawa | **melawan** jika diserang | daging |
| Rusa (bertanduk cabang) | hutan, tundra | penakut, lari cepat | daging, kulit |
| Kelinci | padang, tundra, gurun | melompat, penakut | daging |
| Serigala | hutan, tundra, gunung | **menyerang di malam hari**, melolong | tulang |
| Bebek (kepala hijau) | rawa, pantai | **berenang** | daging, bulu |
| Kambing (tanduk melengkung, janggut) | pegunungan | — | daging |
| Unta (punuk) | gurun, sabana | — | daging, kulit |
| Kuda (surai, belang putih) | padang, sabana | penakut, lari cepat | kulit |
| Beruang | tundra, hutan, gunung | **sangat kuat** & melawan | daging, kulit |
| Katak | rawa | melompat | — |

Setiap hewan punya **suara khas** (melenguh, mengembik, berkokok, mendengus, melolong, menguik, meringkik, menggeram, dll.). Suara dibuat dengan sintesis formant dan berubah saat diam, marah, terluka, atau mati, dengan volume yang mengikuti jarak. Hewan juga punya **HP bar**, kabur bersama kawanannya saat salah satu diserang, menundukkan kepala saat merumput, dan muncul kembali sesuai biome.

## 4. Makhluk Era Monster (26 spesies)
Ada 12 garis evolusi ditambah 2 makhluk langka/boss. Semuanya dibuat dari kubus kecil:

> Flamecube→Pyroblok, Aquablock→Tidalith, Leafling→Grassaur, Voltbit→Voltagon, Rockmon→Bouldron, Shadowbit→Nightfang, Crystalith→Glaciarch, Mossylox→Bogmaw, Darkpuff→Gloomcloud, Sandpincer→Dunecrusher, Embird→Blazewing, Fluffhop→Bunburst, Lunarix (langka), Eclipsar (boss Expert Moon)

Tipe elemen: Normal, Api, Air, Rumput, Listrik, Tanah, Es, Bayangan, Kosmik. Setiap makhluk punya stats, 3–4 skill, cry unik, dan evolusi (level, Happiness, atau Evolution Stone).

## 5. Biome (9 + gua)
| Biome | Isi |
|---|---|
| Padang Rumput | dataran terbuka |
| Hutan | pohon lebat, daun berguguran |
| Gurun | kaktus, debu |
| **Sabana** (baru) | rumput kering, pohon akasia |
| Rawa | air, pohon rawa, kunang-kunang |
| Pegunungan | salju, kristal |
| **Tundra Salju** (baru) | danau beku, pinus, salju turun |
| Tanah Gelap | kristal bulan |
| Pantai | tepi laut |
| Gua | bijih: bara, besi, emas, kristal |

Di tengah peta ada **Desa Kubus** dengan 7 NPC bersuara.

## 6. Nyawa, HP & rasa lapar
* **HP** dan **Nyawa** terpisah. Nyawa yang hilang tidak pulih, kecuali dengan **Potion Rahasia**.
* Monster, rival, dan boss **mencuri nyawa**. Monster yang menyimpan nyawa curian bisa bangkit lagi.
* Di **Expert Moon**, satu serangan bisa mengambil ½ sampai 7 nyawa. Kehilangan 7 sekaligus = **OUT DEAD**.
* **Kenyang (20 poin)** berkurang saat berjalan, berlari, dan menambang.
  * Di bawah 6: HP tidak pulih.
  * 0: HP terkuras karena kelaparan.
  * Makan dengan **R**: daging panggang +8, apel +4, beri +2, daging mentah +3.
* **Potion Rahasia + Armor Gogil:** cari serangga hitam kecil (dengarkan bunyi *tik-tik*), hancurkan block di bawahnya, lalu buka chest yang muncul.

## 7. Realisme visual & suara
* **Bayangan matahari dan bulan** real-time (bisa dimatikan di Pengaturan untuk perangkat lemah).
* **Kubah langit** bergradasi dengan cahaya matahari, senja, malam berbintang, dan bulan merah.
* **Air** beriak, bergerak, dan memantulkan kilau.
* **Partikel suasana:** kunang-kunang malam, daun berguguran, salju, debu gurun, percikan Tanah Gelap.
* **Suara alam:** kicau burung, jangkrik, burung hantu, angin di pegunungan, gemericik air.
* Pencahayaan ambient occlusion pada block, kabut jarak, siklus siang-malam, cahaya lentera & kristal.

## 8. Struktur kode (`index.html`)
| Modul | Isi |
|---|---|
| CORE & DATA | `TYPES`, `SKILLS`, `SPECIES`, `ANIMALS`, `ITEMS`, `RECIPES`, `QUESTS`, `DIFFICULTIES`, `NPCS`, `SPAWNS` |
| `AudioManager` | SFX, cry makhluk, suara hewan (`animal()`), suara NPC formant, suara alam, BGM sequencer |
| `Sculpt` + `sculptPart` | mesin micro-voxel; `buildHumanoid`, `buildCreature`, `buildAnimal` |
| `Creature3D` | animasi makhluk & hewan |
| `LifeSystem`, `Inventory`, `CraftingSystem`, `Quests` | nyawa, tas, crafting, tugas |
| `VoxelWorld`, `generateWorld` | dunia: chunk mesher dengan ambient occlusion, raycast, fisika, biome, desa |
| `WorldManager` (`WorldMode`) + entity | `Player` (lapar), `AnimalEnt`, `WildEnt`, `HostileEnt`, `RivalEnt`, `NPCEnt`, `BugEnt`, `ChestEnt` |
| `BattleSystem`, `Evolution` | battle & evolusi |
| `UIManager`, `Creator` (Tahap 1) | antarmuka & pembuat karakter |
| `SceneManager` (`Title`, `Room`, `Game`) | adegan, loop utama, simpan/muat |

## 9. Saran pengembangan
* Cahaya obor dinamis.
* Dunia tak terbatas.
* Multiplayer, supaya pencurian nyawa terjadi antar pemain.
* Kandang & beternak hewan.
* Menunggangi kuda.
* Ensiklopedia makhluk.
* Gym per biome.
