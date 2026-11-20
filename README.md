Poster Hidup AR

Mini project AR berbasis web: arahkan kamera ke poster, lalu model 3D muncul di atasnya lengkap dengan panel informasi. Berjalan langsung di browser tanpa instalasi aplikasi.

Ada dua target poster:

Tata Surya: model 3D dengan animasi orbit. Ketuk planet untuk melihat informasinya.
Save The Orangutans: model orang utan low-poly dengan pesan pelestarian hutan.

Dibangun dengan three.js 0.160 dan MindAR 1.2.5 (image tracking), keduanya dimuat lewat CDN.

Cara Menjalankan

Kamera hanya bisa diakses lewat HTTPS atau localhost, jadi file tidak bisa dibuka dengan klik dua kali (file://).
Lokal (komputer):
# pilih salah satu
python -m http.server 5500
# atau pakai ekstensi "Live Server" di VS Code

Buka http://localhost:5500/index.html, izinkan akses kamera, lalu arahkan kamera ke gambar target (gambar yang dipakai untuk membuat assets/targets/targets.mind).

Lewat HP: Proyek dapat dijalankan melalui GitHub Pages yang menyediakan akses HTTPS.
Link Demo: https://imagetracker.github.io/arvr-miniproject-posterhidup/
Buka tautan tersebut melalui browser HP, izinkan akses kamera, lalu arahkan kamera ke gambar target untuk memulai pengalaman Augmented Reality (AR).

Tambahkan ?debug di akhir URL untuk menampilkan info debug di layar.
Cara Menggunakan

|              Aksi                 |                  Hasil                 |
| Arahkan kamera ke poster          | Model dan panel informasi muncul       |
| Ketuk planet (Tata Surya)         | Zoom ke planet dan tampil datanya      |
| Ketuk area kosong                 | Kembali ke tampilan tata surya penuh   |
| Seret satu jari                   | Menggeser model                        |
| Cubit dua jari                    | Zoom model                             |
| Tombol − / +                      | Memperlambat / mempercepat animasi     |
| Tombol latar                      | Menyalakan / mematikan latar angkasa   |
| Tombol ✕ di panel, lalu ℹ️ Info  | Menyembunyikan / memunculkan panel     |
| Tombol Reset                      | Mengembalikan posisi dan ukuran model  |
| Ketuk orang utan                  | Memutar animasi dan suara              |

Fitur
Image tracking: model muncul dan hilang mengikuti poster, panel ikut muncul dan hilang.
Tata Surya: Matahari, 8 planet, Bulan, dan Pluto, masing-masing dengan diameter, jarak ke Matahari, kala revolusi, dan fakta singkat. Warna panel mengikuti planet.
Lencana penjelajah: bilah progres "Dijelajahi n/11" yang disimpan di localStorage, notifikasi saat objek baru dilihat, gelar yang naik (Pemula, Penjelajah, Astronot, Master Tata Surya), dan tombol reset progres.
Latar angkasa: bintang 3D berkelip, cahaya berdenyut di Matahari, dan kamera meredup saat zoom ke planet.
Orang utan: animasi, suara "No forest, no future", serta panel status konservasi, habitat, dan ancaman utama.
Getaran singkat di HP saat mengetuk planet atau orang utan.
Penghitung target yang sudah dipindai ("Dipindai 1/2") disimpan di localStorage.
Semua konten (teks, planet, kecepatan, suara) diatur dari data/targets.json, tanpa mengubah kode.

STRUKTUR
index.html            # aplikasi (HTML, CSS, JS)
data/targets.json     # konfigurasi target, planet, kecepatan, suara
assets/models/        # model 3D (.glb)
assets/targets/       # file tracking MindAR (targets.mind)
docs/device-matrix.md # catatan hasil uji perangkat
LICENSES.md           # lisensi dan atribusi aset

Batasan yang Diketahui
Butuh internet: three.js dan MindAR dimuat dari CDN, jadi tidak jalan offline.
Hanya satu target dilacak sekaligus (maxTrack: 1).
Planet kecil di layar: model diperkecil agar seluruh orbit muat, sehingga planet kecil seperti Merkurius dan Pluto sulit diketuk. Ketukan dibantu toleransi 48 px, tetapi Bumi dan Bulan yang berdekatan bisa tertukar.
Suara orang utan memakai suara bicara bawaan browser (Web Speech) selama belum ada file rekaman, sehingga bunyinya berbeda antar perangkat, baru keluar setelah ketukan pertama, dan bisa tidak tersedia di sebagian browser HP.
Getaran tidak didukung di iOS Safari.
Efek latar menambah beban grafis; di HP lama matikan dengan tombol 🌌 jika animasi terasa patah-patah.
Ukuran model besar (sekitar 11 MB total), sehingga muat pertama bisa lambat di jaringan lemah.
Data planet dibulatkan dan hanya untuk edukasi umum, bukan nilai presisi astronomi.

Lisensi dan Atribusi
Daftar lisensi dan pembuat model 3D dicatat di LICENSES.md.
