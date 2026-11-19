Poster Hidup AR

Mini project AR berbasis web: arahkan kamera ke poster, lalu model 3D muncul di atasnya lengkap dengan panel informasi. Berjalan langsung di browser tanpa instalasi aplikasi.

Ada dua target poster:

Tata Surya: model 3D dengan animasi orbit. Ketuk planet untuk melihat informasinya.
Save Orangutan – Let Them Breathe: model orang utan low-poly dengan pesan pelestarian hutan.

Dibangun dengan three.js 0.160 dan MindAR 1.2.5 (image tracking), keduanya dimuat lewat CDN.

Cara Menjalankan

Kamera hanya bisa diakses lewat HTTPS atau localhost, jadi file tidak bisa dibuka dengan klik dua kali (file://).
Lokal (komputer):
# pilih salah satu
python -m http.server 5500
# atau pakai ekstensi "Live Server" di VS Code

Buka http://localhost:5500/index.html, izinkan akses kamera, lalu arahkan kamera ke gambar target (gambar yang dipakai untuk membuat assets/targets/targets.mind).

Lewat HP: deploy ke GitHub Pages (otomatis HTTPS), lalu buka tautannya di HP.

Tambahkan ?debug di akhir URL untuk menampilkan info debug di layar.

Fitur
Image tracking: model muncul dan hilang mengikuti poster.
Panel informasi muncul saat target ditemukan dan hilang saat target hilang.
Panel bisa disembunyikan (tombol ✕) dan dimunculkan lagi (tombol ℹ️ Info).
Tata Surya: ketuk Matahari, 8 planet, Bulan, atau Pluto untuk zoom ke objek dan melihat diameter, jarak ke Matahari, serta kala revolusi. Warna panel mengikuti planet.
Kecepatan animasi tata surya bisa diatur dengan tombol − / +.
Seret satu jari untuk menggeser model, cubit dua jari untuk zoom, dan tombol reset untuk mengembalikan posisi dan ukuran.
Orang utan: ketuk model untuk memulai animasi dan suara "No forest, no future".
Penghitung target yang sudah dipindai ("Dipindai 1/2") disimpan di localStorage.
Semua konten (teks, planet, kecepatan, suara) diatur dari data/targets.json, tanpa mengubah kode.

index.html            # aplikasi (HTML, CSS, JS)
data/targets.json     # konfigurasi target, planet, kecepatan, suara
assets/models/        # model 3D (.glb)
assets/targets/       # file tracking MindAR (targets.mind)

Batasan yang Diketahui
Butuh internet: three.js dan MindAR dimuat dari CDN, jadi tidak jalan offline.
Hanya satu target dilacak sekaligus (maxTrack: 1).
Planet kecil di layar: model diperkecil agar seluruh orbit muat, sehingga planet kecil seperti Merkurius dan Pluto sulit diketuk. Ketukan dibantu toleransi 48 px, tetapi Bumi dan Bulan yang berdekatan bisa tertukar.
Suara orang utan memakai suara bicara bawaan browser (Web Speech), sehingga bunyinya berbeda antar perangkat, baru keluar setelah ketukan pertama, dan bisa tidak tersedia di sebagian browser HP. Belum ada file rekaman. Untuk memakainya, taruh file di assets/audio/ dan isi "suara" di targets.json.
Panel informasi orang utan masih sederhana (belum ada data statistik seperti planet).
Ukuran model besar (sekitar 11 MB total), sehingga muat pertama bisa lambat di jaringan lemah.
Data planet dibulatkan dan hanya untuk edukasi umum, bukan nilai presisi astronomi.
Belum diuji menyeluruh di banyak perangkat; docs/device-matrix.md belum diisi.
Lisensi dan atribusi model 3D belum dicantumkan di LICENSES.md.