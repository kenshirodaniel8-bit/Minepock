# MinePock Champions

Game 3D browser bergaya voxel. Kamu menjelajahi dunia terbuka yang bisa ditambang dan dibangun, lalu menangkap, merawat, dan mengadu makhluk blocky dalam battle turn-based. Ada juga sistem **Nyawa** yang ketat dan bisa dicuri musuh.

* **Satu file:** `index.html` (Three.js r128 dari CDN + Web Audio API).
* **Semua aset prosedural:** tekstur block, model 3D, musik, efek suara, cry makhluk, dan suara NPC dibuat oleh kode. Tidak ada file gambar atau audio eksternal.
* **Cara menjalankan:** buka `index.html` di Chrome, Edge, atau Firefox (perlu internet untuk memuat Three.js dari CDN). Bisa juga lewat server lokal, misalnya `npx serve .` atau `python3 -m http.server`.

---

## 1. Cara bermain dari awal sampai akhir

1. **Title Screen.** Pulau voxel melayang dengan makhluk yang berjalan dan terbang. Tekan **PLAY**. Klik ini juga mengaktifkan audio, karena browser mewajibkan interaksi dulu.
2. **Main Room.** Pilih **starter**: Flamecube (Api), Aquablock (Air), atau Leafling (Rumput). Kamu bisa klik kartunya atau model 3D di pedestal.
3. Klik salah satu dari **5 portal** (atau tombol di kanan bawah) untuk membaca deskripsi bahayanya, lalu tekan **MASUK PORTAL**.
4. **Open World.** Kamu muncul di Desa Kubus. Bicara dengan NPC, beli barang, lalu jelajahi biome, tangkap makhluk, tambang bahan, crafting, kalahkan monster, dan cari serangga hitam rahasia.
5. Run disimpan otomatis tiap 60 detik dan setelah battle. **Lanjutkan Run** tersedia di Title dan Main Room. Kalau nyawa habis atau hilang 7 sekaligus, kamu **OUT DEAD**: run terhapus dan kamu mulai lagi dari Main Room.

### Kontrol PC
| Aksi | Tombol |
|---|---|
| Jalan / lari / lompat (berenang naik) | `W A S D` / `Shift` / `Spasi` |
| Putar kamera / zoom | Drag mouse (kiri atau kanan), atau `Q` / `E` / Scroll |
| Menambang | Tahan klik kiri pada block |
| Menaruh block | Klik kanan (pilih block di hotbar `1`–`9`) |
| Serang makhluk atau monster | Klik kiri pada target |
| Bicara NPC, buka chest, mulai battle | Klik NPC, atau tekan `F` |
| Lempar Pock Ball di open world | `G` (target harus HP < 40%) |
| Tas / Crafting / My Creatures / Menu | `I` / `C` / `P` / `Esc` |
| Aksi battle | Tombol di layar, atau angka `1`–`7` |

### Kontrol sentuh (HP/tablet)
Joystick kiri untuk berjalan. Geser layar untuk memutar kamera. Ketuk atau tahan untuk menyerang dan menambang. Tombol **LARI, F, G, TARUH** (mode menaruh block), **LOMPAT**, dan **KAM** ada di kanan bawah.

---

## 2. Daftar makhluk (26 spesies)

Base stats: HP / Attack / Defense / Speed / Special. Setiap makhluk menyimpan maksimal 4 skill.

| # | Nama | Tipe | Base Stats | Skill (level belajar) | Evolusi |
|---|---|---|---|---|---|
| 1 | **Flamecube** | Api | 45 / 56 / 42 / 64 / 60 | Hantam Blok, Bara Kubus, Panaskan (6), Ledakan Api (11), Pilar Inferno (20) | → Pyroblok (Lv 16) |
| 2 | **Pyroblok** | Api | 72 / 86 / 66 / 82 / 90 | + Sayap Membara (16), Pilar Inferno (24) | — |
| 3 | **Aquablock** | Air | 50 / 48 / 62 / 46 / 56 | Hantam Blok, Gelembung, Selubung Kabut (6), Semprot Kilat (10), Hempasan Ombak (20) | → Tidalith (Lv 16) |
| 4 | **Tidalith** | Air | 82 / 72 / 94 / 60 / 82 | Gelembung, Selubung Kabut, Semprot Kilat, Hempasan Ombak (22) | — |
| 5 | **Leafling** | Rumput | 48 / 50 / 52 / 50 / 58 | Hantam Blok, Panah Daun, Spora Racun (6), Cambuk Sulur (10), Fotosintesis (14), Sinar Mekar (21) | → Grassaur (Lv 16) |
| 6 | **Grassaur** | Rumput | 80 / 80 / 84 / 66 / 92 | Panah Daun, Cambuk Sulur, Fotosintesis, Sinar Mekar (18) | — |
| 7 | **Voltbit** | Listrik | 40 / 45 / 38 / 88 / 70 | Hantam Blok, Percikan, Isi Daya (7), Tanduk Petir (13), Badai Statis (22) | → Voltagon (Lv 20) |
| 8 | **Voltagon** | Listrik | 66 / 72 / 62 / 116 / 102 | Percikan, Isi Daya, Tanduk Petir, Badai Statis (20) | — |
| 9 | **Rockmon** | Tanah | 60 / 70 / 85 / 30 / 35 | Lempar Kerikil, Mengeras (5), Hantaman Batu (11), Semburan Pasir (15), Gempa Injak (24) | → Bouldron (Lv 22) |
| 10 | **Bouldron** | Tanah | 96 / 106 / 122 / 40 / 55 | Lempar Kerikil, Mengeras, Hantaman Batu, Semburan Pasir, Gempa Injak (26) | — |
| 11 | **Shadowbit** | Bayangan | 45 / 62 / 40 / 80 / 58 | Gigitan Bayang, Tatapan Ngeri (5), Lompat Kilat (9), Tebasan Malam (14), Mimpi Buruk (24) | → Nightfang (Lv 26 **atau** Happiness 170) |
| 12 | **Nightfang** | Bayangan | 72 / 100 / 64 / 112 / 82 | Gigitan Bayang, Tatapan Ngeri, Tebasan Malam, Mimpi Buruk | — |
| 13 | **Crystalith** | Es | 55 / 40 / 75 / 45 / 72 | Serpih Beku, Perisai Kristal (6), Hujan Serpih Es (12), Badai Salju Kubus (24) | → Glaciarch (Lv 25) |
| 14 | **Glaciarch** | Es | 86 / 60 / 112 / 58 / 112 | Serpih Beku, Perisai Kristal, Hujan Serpih Es, Badai Salju Kubus | — |
| 15 | **Mossylox** | Rumput / Air | 60 / 52 / 58 / 40 / 55 | Gelembung, Panah Daun (4), Spora Racun (8), Cambuk Sulur (12), Hempasan Ombak (22) | → Bogmaw (Lv 20) |
| 16 | **Bogmaw** | Rumput / Air | 94 / 86 / 82 / 50 / 80 | Gelembung, Cambuk Sulur, Spora Racun, Hempasan Ombak | — |
| 17 | **Darkpuff** | Bayangan / Kosmik | 48 / 35 / 45 / 60 / 75 | Nina Bobo (4), Denyut Bintang (8), Tatapan Ngeri (12), Mimpi Buruk (18), Sinar Bulan (26) | → Gloomcloud (**Evolution Stone**) |
| 18 | **Gloomcloud** | Bayangan / Kosmik | 80 / 56 / 72 / 86 / 114 | Nina Bobo, Denyut Bintang, Mimpi Buruk, Sinar Bulan | — |
| 19 | **Sandpincer** | Tanah | 50 / 70 / 72 / 45 / 30 | Lempar Kerikil, Mengeras (6), Semburan Pasir (10), Hantaman Batu (16), Gempa Injak (26) | → Dunecrusher (Lv 22) |
| 20 | **Dunecrusher** | Tanah | 82 / 114 / 110 / 58 / 45 | Lempar Kerikil, Mengeras, Hantaman Batu, Semburan Pasir, Gempa Injak | — |
| 21 | **Embird** | Api | 45 / 58 / 40 / 86 / 52 | Hembusan, Bara Kubus (4), Lompat Kilat (9), Sayap Membara (14), Ledakan Api (20) | → Blazewing (Lv 24) |
| 22 | **Blazewing** | Api / Kosmik | 74 / 94 / 64 / 114 / 88 | Hembusan, Bara Kubus, Sayap Membara, Ledakan Api, Sinar Bulan (30) | — |
| 23 | **Fluffhop** | Normal | 55 / 45 / 45 / 62 / 45 | Lompat Kilat, Nina Bobo (5), Tarian Riang (9), Tubuh Kubus (14) | → Bunburst (**Happiness 160**) |
| 24 | **Bunburst** | Normal | 90 / 82 / 72 / 96 / 72 | Lompat Kilat, Nina Bobo, Tarian Riang, Tubuh Kubus | — |
| 25 | **Lunarix** (langka) | Kosmik | 92 / 86 / 92 / 102 / 122 | Denyut Bintang, Sinar Bulan, Penyembuhan Bulan, Sinar Gerhana (40) | — |
| 26 | **Eclipsar** (boss) | Kosmik / Bayangan | 150 / 118 / 110 / 90 / 135 | Sinar Bulan, Mimpi Buruk, Penyembuhan Bulan, Sinar Gerhana | — |

* **Tipe elemen:** Normal, Api, Air, Rumput, Listrik, Tanah, Es, Bayangan, Kosmik.
  * Efektivitas: 2× jika kuat dan 0,5× jika lemah. Contoh: Api > Rumput/Es, Air > Api/Tanah, Listrik > Air/Kosmik, Bayangan > Kosmik/Normal.
  * Ada bonus STAB 1,5× jika tipe skill sama dengan tipe makhluk.
* **Status:** Terbakar, Racun, Lumpuh, Tidur, dan Beku.
* **Shiny:** peluang 1/128. Warnanya berbeda dan ada efek kilau saat muncul.
* **Spawn per biome:**
  * Fluffhop: padang dan hutan
  * Sandpincer: gurun
  * Rockmon dan Crystalith: gunung
  * Mossylox: rawa
  * Shadowbit dan Darkpuff: malam hari dan Tanah Gelap
  * Lunarix: hanya di Tanah Gelap saat malam
  * Eclipsar: boss khusus mode Expert Moon

---

## 3. Main Room & tingkat kesulitan

Main Room adalah ruangan voxel yang nyaman: ada perapian dengan api berkedip, karpet, rak buku, lentera, dan pedestal starter. Di dalamnya ada **5 portal** dengan shader pusaran, papan nama, ikon tengkorak, dan partikel. Klik sebuah portal untuk melihat deskripsi bahaya. Avatar kamu lalu berjalan masuk ke portal itu.

| Mode | Nyawa | Kehilangan nyawa | Ciri utama |
|---|---|---|---|
| **Normal** | 12 | 1 per kematian | Monster hanya muncul malam hari. Klinik gratis. Tangkap lebih mudah. |
| **Medium** | 10 | ½ jika kalah battle, 1 jika HP habis | Monster lebih ganas. Klinik berbayar. |
| **Hard** | 8 | ½–2 | Soul Strike aktif. Rival trainer AI. Monster muncul siang dan malam. Starter Lv 8. |
| **Hardmon** (tersulit no. 2) | 7 | ½–3 | AI hampir sempurna. Malam lebih panjang. Monster sangat agresif. Starter Lv 11. |
| **Expert Moon** (tersulit) | 10 | **½ sampai 7** per serangan | Bulan merah. Desa tidak aman di malam hari. Boss Eclipsar. **−7 sekaligus = OUT DEAD**. Starter Lv 14. |

Difficulty juga mempengaruhi:
* level makhluk liar,
* jumlah monster,
* kecerdasan AI,
* peluang tangkap,
* harga toko,
* regenerasi HP,
* jumlah serangga rahasia.

---

## 4. Sistem nyawa & Expert Moon

* **Nyawa terpisah dari HP.** Hati piksel di HUD bisa tampil penuh, setengah, atau kosong.
* **Penyebab nyawa berkurang:**
  * HP pemain habis karena monster atau jatuh,
  * kalah battle (Medium ke atas),
  * **Soul Strike**. Monster bersinar merah dan muncul cincin peringatan selama 1 detik. Kalau kamu masih dalam jangkauan, nyawa langsung diambil. Kamu bisa menghindar dengan menjauh, atau menggagalkannya dengan memukul monster itu.
* **Jumlah nyawa yang hilang** diacak sesuai distribusi tiap difficulty. Di Expert Moon nilainya ½, 1, 2, 3, 4, 5, 6, atau 7. Kehilangan **7 sekaligus berarti OUT DEAD seketika**.
* **Nyawa tidak pernah pulih secara normal.** Satu-satunya cara memulihkannya adalah **Potion Rahasia**.
* **Pencurian nyawa (Steal Heart).** Jika nyawa diambil oleh monster, Rival trainer, atau boss Eclipsar, nyawa itu **dicuri** dan disimpan si penyerang. Jumlahnya tampil sebagai label "❤×N nyawa curian".
  * Saat kamu dihidupkan kembali di desa, nyawa itu tetap milik mereka.
  * Monster pencuri bisa **bangkit lagi memakai nyawa curian** saat dikalahkan, jadi harus dikalahkan berkali-kali.

---

## 5. Potion Rahasia + Armor Gogil

1. Serangga hitam yang sangat kecil (sekitar 0,1 block) merayap di atas tanah, jauh dari desa. Teksturnya hitam pekat tanpa pencahayaan, jadi sulit dilihat, terutama di malam hari.
2. Dekati dan **dengarkan bunyi tik-tik halus**. Volumenya makin keras saat kamu makin dekat. **Nenek Sari** bisa memberi petunjuk arah dan jarak ke serangga terdekat.
3. **Hancurkan block tepat di bawah serangga.** Sebuah **Chest** akan naik dari tanah dengan cahaya emas.
4. Buka chest (klik atau `F`):
   * **Chest pertama:** Potion Rahasia + **Armor Gogil**.
   * **Chest berikutnya:** Potion Rahasia + Ultra Pock ×2 + Emas ×2.
5. **Potion Rahasia** (minum dari Tas): permanen untuk run itu. Memberi **+2 nyawa maksimum** dan **memulihkan semua nyawa yang hilang**.
6. **Armor Gogil** (pakai dari Tas):
   * mengurangi 70% damage monster,
   * mengurangi 72% peluang kehilangan nyawa parah (≥3),
   * memancarkan **aura Gogil**: cincin kubus emas-ungu yang berputar, cahaya, dan partikel.

---

## 6. Tangkap, pelihara, evolusi, crafting

### Tangkap
* **Di battle:** tombol **Catch** baru aktif saat HP lawan < 40%.
* **Di open world:** pukul makhluk liar sampai HP < 40%, lalu tekan `G`.
* **Animasi tangkap:**
  1. Bola terbang melengkung.
  2. Bola membuka dan makhluk tersedot masuk.
  3. Bola jatuh, memantul, lalu bergoyang 1–3 kali.
  4. Berhasil: cahaya dan tulisan **GOTCHA!** Gagal: bola pecah dan makhluk keluar lagi.
* **Peluang tangkap dipengaruhi oleh:**
  * sisa HP,
  * status lawan (tidur/beku ×2, lainnya ×1,5),
  * jenis bola: Pock ×1, Great ×1,6, Ultra ×2,3, Moon ×3,2 di malam hari,
  * Happiness pemimpin tim,
  * difficulty.
* Tim berisi maksimal 6 makhluk. Sisanya masuk **Storage**.

### Pelihara (My Creatures, `P`)
* **Panel My Creatures** menampilkan:
  * preview 3D yang bisa diputar,
  * stats,
  * bar EXP, Happiness, Kenyang, dan Energi,
  * status: Healthy, Hungry, Tired, atau Fainted.
* **Aksi perawatan:**
  * **Beri Makan:** menambah kenyang dan Happiness.
  * **Istirahat:** menambah energi dan sedikit HP.
  * **Bermain:** menambah Happiness.
  * **Latih:** menambah EXP, tapi menguras energi dan kenyang.
* **Pengaruh Happiness:**
  * damage ±10%,
  * peluang kritis,
  * kepatuhan (Happiness rendah, lapar, atau lelah bisa membuat makhluk menolak perintah),
  * peluang evolusi.
* Makhluk yang **Fainted** tidak bisa dipakai sampai disembuhkan dengan Revive atau di Klinik Suster Mira.

### Evolusi
Ada tiga cara: mencapai level tertentu, Happiness tinggi, atau **Evolution Stone**. Batu ini juga mempercepat evolusi level jika makhluk sudah dekat dengan level syaratnya.

Animasi evolusi:
1. Muncul panggung khusus dengan sinar cahaya.
2. Model berubah putih.
3. Bentuk lama dan baru bergantian makin cepat.
4. Kilatan cahaya dan ledakan partikel.
5. Bentuk baru muncul dengan cry-nya.

### Crafting (`C`)
Ada 30 resep. Resep bertanda ⚒ butuh **Meja Crafting** di dekatmu. Meja ada di desa, atau kamu bisa membuatnya lalu menaruhnya sendiri.

| Kategori | Item |
|---|---|
| Dasar | papan, tongkat, meja, obor, lentera, kaca, bata |
| Peleburan | batang besi, batang emas |
| Pock Ball | Pock, Great, Ultra, Moon |
| Ramuan | Potion, Super Potion, Revive, Elixir, Penawar, Perban |
| Makanan | Camilan Beri, Sup Hangat, Kue Manis |
| Spesial | Evolution Stone |
| Alat | beliung kayu/batu/besi, pedang kayu/besi |
| Armor | Armor Besi, Armor Kristal |

Bahan didapat dengan menambang (bara, besi, emas, kristal, pecahan bulan), mengalahkan makhluk atau monster (esensi), atau membeli di toko Pak Rudi.

---

## 7. Suara NPC & makhluk (Web Audio API)

* **Cry makhluk.** Sintesis FM dengan parameter unik per spesies: frekuensi dasar, gelombang, rasio FM, kontur (rise, fall, warble, chirp, growl, trill, meow, chime, croak, click, screech, roar, ethereal), noise, dan jumlah suku kata. Cry berubah sesuai momen: muncul, menyerang, terkena hit, pingsan, dan berhasil ditangkap.
* **Suara NPC (formant synthesis).** Teks dialog dipecah menjadi suku kata:
  * vokal diubah menjadi filter formant F1/F2/F3 (a-e-i-o-u),
  * konsonan menjadi burst noise (desis s, letupan p/t/k, dan lain-lain),
  * kontur pitch dan ritme mengikuti kepribadian,
  * vibrato dan suara napas ditambahkan, lalu disinkronkan dengan teks typewriter.

| NPC | Karakter suara |
|---|---|
| Pak Bram | pria dewasa, dalam & tenang (≈92 Hz, intonasi menurun) |
| Lila | wanita muda ceria (≈285 Hz, naik-turun riang) |
| Tito | anak laki-laki (≈340 Hz, cepat, melompat-lompat) |
| Nenek Sari | nenek tua (lambat, vibrato bergetar kuat, banyak napas, jeda panjang) |
| Pak Rudi | pedagang ramah (sangat cepat, sing-song) |
| Kapten Garda | penjaga tegas (staccato, tekanan di awal kata) |
| Suster Mira | penyembuh lembut (attack halus, sedikit napas) |

  Di Pengaturan ada opsi alternatif **Text-to-Speech browser** (id-ID) dan tombol tes suara.
* **BGM prosedural.** Step sequencer berisi progresi akor, melodi dari seed, pad, bass, arpeggio, dan drum. Ada lagu terpisah untuk Title, Main Room, Open World (siang), malam, Bulan Merah, Battle, dan Boss.
* **SFX:** lempar bola, bola membuka, goyang, sukses/gagal tangkap, serangan per elemen (fase cast & impact), kritis, super efektif, meleset, level up, evolusi, menambang per material, menaruh block, buka chest, minum potion, langkah kaki per material, lompat, terluka, nyawa hilang (lonceng), nyawa dicuri, peringatan Soul Strike, OUT DEAD, koin, crafting, makan, dan lain-lain.
* **Volume** master, musik, SFX, dan suara bisa diatur di Pengaturan.

---

## 8. Animasi 3D yang diimplementasikan

* **Makhluk:**
  * idle (bernapas, bob, ekor bergoyang, kepala menoleh, telinga berkedut),
  * berjalan (kaki berayun),
  * kepak sayap,
  * orbit kristal/kubus,
  * nyala api berkedip,
  * attack/lunge, hurt (kilat merah + knockback), faint (jatuh memantul + memudar), happy, cast, spin, sleep, appear.
* **Pemain & NPC:** jalan dan lari (ayunan kaki/tangan), lompat, ayunan beliung saat menambang, ayunan pedang, berkedip saat terluka, berbicara, dan aura Gogil.
* **Monster:** Gloomling yang meloncat, Moon Wraith yang melayang dengan partikel, telegraph Soul Strike (cincin merah + glow), dan kebangkitan dengan nyawa curian.
* **Tangkap:** urutan lengkap (lihat bagian 6).
* **Evolusi:** urutan lengkap (lihat bagian 6).
* **Level up:** cincin emas naik dan teks LEVEL UP.
* **Efek skill:** projectile, beam, burst, pillar, rain, wave, slash, quake, dan aura dengan partikel warna elemen.
* **Kamera & dunia:**
  * kamera sinematik battle (sweep intro, over-the-shoulder, shake saat kritis),
  * transisi flash/fade,
  * retakan block saat ditambang dan partikel pecahan,
  * chest naik dari tanah dengan tutup terbuka,
  * siklus siang-malam (matahari, bulan, bintang, awan),
  * portal shader berputar di Main Room, api perapian, kamera title yang mengorbit.

---

## 9. Struktur kode (`index.html`)

| Modul | Isi |
|---|---|
| CORE | util matematika, RNG ber-seed, Perlin noise 2D/3D, Tween |
| DATA | `TYPES`, `SKILLS`, `SPECIES`, `HOSTILES`, `BLOCKS`, `ITEMS`, `RECIPES`, `DIFFICULTIES`, `NPCS`, `SPAWNS` |
| `AudioManager` (`AudioMgr`) + `Music` | SFX, cry, suara formant, sequencer BGM |
| `Atlas`, `ParticleSystem` (`Particles`), ModelFactory, `Portraits` | grafis |
| `CreatureInstance` + `Creature3D` | logika makhluk + visual & animasi |
| `LifeSystem`, `Inventory`, `CraftingSystem` (`Crafting`) | nyawa, tas, crafting |
| `VoxelWorld` + `generateWorld` | dunia voxel: chunk mesher dengan ambient occlusion, raycast DDA, fisika AABB, 6 biome + gua + desa |
| `WorldManager` (`WorldMode`) + entity | Player, makhluk liar, monster, Rival, NPC, serangga, Chest |
| `BattleSystem` (`Battle`) + `Evolution` | battle & evolusi |
| `UIManager` (`UI`) + `Preview` | HUD, menu, dialog |
| `SceneManager` (`Title`, `Room`, `Game`) + `Input` | adegan, loop utama, simpan/muat (localStorage), input |

Performa: dunia 144×56×144 dibagi 81 chunk dengan face culling (sekitar 130 draw call). Partikel memakai `InstancedMesh`. Pixel ratio dan jarak pandang bisa diatur di Pengaturan.

---

## 10. Saran pengembangan selanjutnya

* Pencahayaan voxel sungguhan (obor menerangi block sekitar) dan bayangan dinamis.
* Dunia tak terbatas dengan chunk streaming dan generasi di Web Worker.
* Multiplayer (WebRTC/WebSocket) agar "pencurian nyawa" juga terjadi antar pemain sungguhan.
* Pokédex-style "Kubusdex" dengan halaman per makhluk, plus quest dan gym/arena di tiap biome.
* Sistem breeding/telur, held item, dan ability pasif.
* Battle ganda (2 vs 2) dan turnamen Champion sebagai tujuan akhir.
* Kustomisasi avatar pemain dan rumah pemain.
* Ekspor/impor save ke file.
