# Modul 1 Pekerjaan Rumah

Dalam pekerjaan rumah ini, kita akan mengunduh data keuangan dari berbagai sumber dan membuat perhitungan/analisis sederhana.

## Pertanyaan 1: [Makro] Rata-rata pertumbuhan PDB pada tahun 2023

Berapa rata-rata pertumbuhan (dalam %) PDB pada tahun 2023?

Unduh rangkaian waktu Produk Domestik Bruto Riil (GDPC1) dari FRED (https://fred.stlouisfed.org/series/GDPC1). Hitung tingkat pertumbuhan tahun-ke-tahun (YoY) (yaitu, bagi nilai saat ini dengan 4 kuartal yang lalu). Temukan rata-rata pertumbuhan YoY pada tahun 2023 (rata-rata dari 4 angka YoY). Pembulatan menjadi 1 digit setelah koma desimal: mis. jika Anda mendapat pertumbuhan 5,66% => Anda harus menjawab 5,7

## Pertanyaan 2. [Makro] Invers "Imbal Hasil Treasury"

Temukan nilai min (dgs10-dgs2) setelah tahun 2000 (01-01-2000) dan tuliskan sebagai jawaban, bulatkan menjadi 1 digit setelah koma.

Unduh seri suku bunga DGS2 dan DGS10 (https://fred.stlouisfed.org/series/DGS2, https://fred.stlouisfed.org/series/DGS10). Gabungkan keduanya ke satu kerangka data pada tanggal (Anda mungkin perlu membaca tentang pandas.DataFrame.join()), hitung selisihnya dgs10-dgs2 setiap hari.

(Tambahan: pikirkan apa arti "kurva imbal hasil terbalik" bagi pasar dan investor? apakah Anda melihat hal yang sama di negara/pasar yang Anda minati? Apakah menurut Anda ini bisa menjadi fitur prediksi yang baik untuk model tersebut?)

## Pertanyaan 3. [Indeks] Indeks manakah yang lebih baik akhir-akhir ini?

Bandingkan indeks S&P 500 dan IPC Meksiko berdasarkan pertumbuhan 5 tahun dan tuliskan nilai terbesar sebagai jawabannya (%)

Unduh di Yahoo Finance dua harga indeks harian untuk S&P 500 (^GSPC, https://finance.yahoo.com/quote/%5EGSPC/) dan IPC Meksiko (^MXX, https://finance.yahoo.com/quote/ %5EMXX/). Bandingkan pertumbuhan 5 tahun untuk keduanya (antara 09-04-2019 dan 09-04-2024). Pilih indeks pertumbuhan yang lebih tinggi dan tuliskan pertumbuhannya dalam % (% bilangan bulat terdekat). Misalnya. jika rasio akhir/awal adalah 2,0925 (atau pertumbuhan 109,25%), Anda perlu menuliskan 109 sebagai jawaban Anda.

(Tambahan: pikirkan indeks lain dan coba unduh statistik dan bandingkan pertumbuhannya? Buatlah statistik pertumbuhan 10 tahun dan 20 tahun. Berapa rata-rata tingkat pertumbuhan tahunan (CAGR) untuk setiap indeks yang Anda pilih?)

## Pertanyaan 4. [Saham OHLCV] Rasio kisaran 52 minggu (2023) untuk saham yang dipilih

Temukan rasio kisaran terbesar [=(max-min)/max] dari harga Adj.Close pada tahun 2023

Unduh data OHLCV harian tahun 2023 di Yahoo Finance untuk mengetahui 5 saham teratas berdasarkan pendapatan (https://companiesmarketcap.com/most-profitable-companies/): 2222.SR,BRK-B, AAPL, MSFT, GOOG, JPM.

Berikut adalah contoh data yang akan Anda lihat di Pandas untuk "2222.SR": https://finance.yahoo.com/quote/2222.SR/history

Hitung harga maksimum-minim "Adj.Close" untuk setiap saham dan bagi dengan nilai maksimum "Adj.Close". Bulatkan hasilnya menjadi dua angka desimal (misalnya 0,1575 akan menjadi 0,16)

(Tambahan: mengapa hal ini penting untuk penelitian Anda?)

## Pertanyaan 5. [Saham] Hasil Dividen

Temukan hasil dividen terbesar untuk kumpulan saham yang sama

Gunakan daftar perusahaan yang sama (2222.SR,BRK-B, AAPL, MSFT, GOOG, JPM) dan unduh semua dividen yang dibayarkan pada tahun 2023. Anda dapat menggunakan metode get_actions() atau kolom .dividends di perpustakaan yfinance (https:// github.com/ranaroussi/yfinance?tab=readme-ov-file#quick-start)

Jumlahkan seluruh dividen yang dibayarkan pada tahun 2023 per perusahaan dan bagi setiap nilai dengan harga penutupan (Adj.Close) pada hari perdagangan terakhir tahun tersebut.

Temukan nilai maksimum dalam % dan bulatkan menjadi 1 digit setelah koma. (Misalnya, jika Anda memperoleh pembayaran dividen $1,25 dan harga saham akhir tahun adalah $100, hasil dividennya adalah 1,25% -- dan jawaban Anda harus sama dengan 1,3)

## Pertanyaan 6. [Eksplorasi] Selidiki metrik baru

Jawaban teks bebas

Unduh dan jelajahi beberapa metrik atau rangkaian waktu tambahan yang mungkin berharga untuk proyek Anda dan tuliskan alasannya (secara singkat).

## Pertanyaan 7. [Eksplorasi] Deskripsi strategi berbasis waktu seputar rilis pendapatan

Jawaban teks bebas

Jelajahi tanggal penghasilan sepanjang bulan April - mis. menggunakan kalender penghasilan YahooFinance (https://finance.yahoo.com/calendar/earnings?from=2024-04-21&to=2024-04-27&day=2024-04-23). Bandingkan dengan pendapatan yang ditutup sebelumnya (misalnya, tanggal terkini dengan data lengkap https://finance.yahoo.com/calendar/earnings?from=2024-04-07&to=2024-04-13&day=2024-04-08).

Jelaskan strategi/ide analitis (Anda tidak diharuskan untuk menerapkannya) untuk memilih subset perusahaan yang diminati berdasarkan data kejadian di masa depan.
