# Catatan penyimpanan duitw

## Perilaku yang diharapkan

Aplikasi menyimpan satu snapshot state pada `localStorage` dengan key `duitw_v1`. Setiap transaksi menambah satu record ke array `transactions`, sehingga ukuran **Data aplikasi** memang bertambah seiring jumlah transaksi. `localStorage.setItem()` mengganti nilai key yang sama; aplikasi tidak membuat salinan snapshot baru pada setiap penyimpanan.

## Perbaikan pada versi ini

- Menambahkan guard pada submit transaksi, rekening, piutang/kewajiban, dan pembayaran agar submit berulang ketika dialog yang sama masih terbuka tidak menambahkan record ganda.
- Guard di-reset saat dialog dibuka kembali sehingga pengguna tetap dapat mencatat transaksi berikutnya.
- Tidak menghapus atau membatasi riwayat transaksi. Tidak ada data lama yang dibuang demi mengecilkan ukuran penyimpanan.

## Batasan

Ukuran data masih akan naik secara wajar saat pengguna menambahkan transaksi. Mengurangi ukuran absolut lebih jauh memerlukan perubahan format penyimpanan/migrasi dan pengujian restore; jangan menghapus data atau membersihkan WebView storage untuk mengatasi kenaikan normal ini.
