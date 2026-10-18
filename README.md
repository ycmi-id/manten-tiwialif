# Website Panitia Manten Tiwi & Alif

Website statis responsif untuk GitHub Pages, tema biru dan kuning dengan latar putih.

## Isi
- Ringkasan progres agenda
- Agenda panitia (status dapat diubah, agenda dapat ditambah/edit)
- Rundown detail seserahan & akad nikah serta resepsi
- Susunan kepanitiaan dan vendor dari dokumen yang diberikan
- Catatan update progres
- Bagian layout sengaja dikosongkan untuk gambar yang akan ditambahkan
- Ekspor/impor cadangan JSON
- Footer order website menuju WhatsApp Mr. Glempho

## Cara upload ke GitHub Pages
1. Ekstrak ZIP ini.
2. Buat repository GitHub baru (misalnya `panitia-manten-tiwi-alif`).
3. Upload semua isi folder ini ke root repository. Pastikan `index.html`, `README.md`, dan folder `assets/` berada di root.
4. Buka **Settings → Pages**.
5. Pada **Build and deployment**, pilih **Deploy from a branch**, branch `main`, folder `/ (root)`, lalu Save.
6. Tunggu proses deploy, lalu buka URL GitHub Pages yang diberikan.

## Catatan penting tentang update antarperangkat
Versi dasar menyimpan perubahan pada browser/perangkat yang dipakai (localStorage). Karena GitHub Pages hanya hosting statis, perubahan status atau catatan yang dilakukan satu panitia **tidak otomatis terlihat** oleh panitia lain. Untuk berbagi, gunakan menu **Kelola Data → Unduh cadangan JSON**, lalu panitia lain mengimpor file tersebut.

Jika ingin semua panitia langsung melihat update yang sama dari HP masing-masing, perlu backend bersama seperti Supabase. Form konfigurasi pada website menyimpan URL/key saja; integrasi database real-time belum aktif pada paket dasar ini. Jangan menaruh `service_role` key pada website publik.

## Supabase (opsi lanjutan)
Untuk membuat sinkronisasi bersama, buat project Supabase, buat tabel untuk agenda dan update progres, atur Row Level Security (RLS) dengan kebijakan akses yang sesuai, lalu integrasikan client Supabase dan operasi CRUD pada `index.html`. Jika data akan diakses publik tanpa login, pertimbangkan risiko siapa pun bisa mengubah data; lebih aman menambahkan autentikasi panitia dan pembatasan hak akses.

## Catatan data
- Agenda tambahan mengikuti instruksi yang diberikan.
- Rundown detail disalin dan dirapikan dari PDF panitia yang diunggah.
- Beberapa detail dalam dokumen sumber masih kosong/berpotensi perlu konfirmasi (misalnya nama saksi CPP dan waktu rundown yang berbeda antara agenda umum dan detail). Tidak diisi dengan tebakan.
- Bagian layout sengaja tidak menampilkan denah dari PDF, sesuai permintaan agar area layout dikosongkan.


## Pembaruan tema dan status otomatis
- Palet warna diperbarui menjadi biru, kuning, dan putih.
- Font utama menggunakan Open Sans (memerlukan koneksi internet untuk memuat Google Fonts; fallback sistem tetap tersedia).
- Hover tombol dan kartu menyesuaikan palet biru-kuning.
- Saat website dibuka atau dirender, status agenda diperbarui berdasarkan tanggal lokal perangkat: tanggal yang sudah lewat otomatis menjadi **Selesai**, agenda pada tanggal hari ini menjadi **Berjalan / On Progress**, dan agenda mendatang menjadi **Belum**. Status **Selesai** yang ditandai manual tetap dipertahankan.
- Status otomatis diproses saat halaman dibuka/diperbarui; website statis tidak berjalan di latar belakang ketika halaman ditutup.
