## Modul 2 Pekerjaan Rumah

Dalam pekerjaan rumah ini, kami akan menggabungkan data dari berbagai sumber untuk memprosesnya di Pandas dan menghasilkan kolom tambahan.

Jika tidak dinyatakan sebaliknya, harap gunakan [Colab](https://github.com/DataTalksClub/stock-markets-analytics-zoomcamp/blob/main/02-dataframe-lysis/Module2_Colab_Working_with_the_data.ipynb) yang tercakup dalam livestream untuk meninjau kembali -gunakan cuplikan kode.

---
### Pertanyaan 1: Pengarsipan IPO Pengikisan Web dan Pemrosesan Data

**Berapa jumlah total ($m) pengajuan tahun 2023 yang dilakukan pada hari Jumat?**

Gunakan kembali contoh [Cuplikan Kode 1] untuk mendapatkan data dari web untuk titik akhir ini: https://stockanalisis.com/ipos/filings/
Ubah 'Tanggal Pengajuan' menjadi datetime(), 'Saham Ditawarkan' menjadi float64 (jika '-' ditemukan, isi dengan NaN).
Tentukan kolom baru 'Avg_price' berdasarkan "Kisaran Harga", yang sama dengan NaN jika tidak ada harga yang ditentukan, harga (jika hanya satu angka yang diberikan), atau rata-rata dari 2 harga (jika rentang diberikan) ).
Anda mungkin terinspirasi oleh fungsi `extract_numbers()` di [Cuplikan Kode 4], atau Anda dapat menulis fungsi Anda sendiri untuk "mengurai" sebuah string.
Tentukan kolom "Shares_offered_value", yang sama dengan "Shares Offered" * "Avg_price" (jika kedua kolom ditentukan; jika tidak, maka NaN)

Temukan jumlah total dalam $m (jutaan USD, bilangan INTEGER terdekat) untuk semua pengisian selama tahun 2023, yang terjadi pada hari Jumat (`Tanggal.dt.hari minggu()==4`). Anda akan melihat total 32 catatan, 24 di antaranya bukan nol.

(tambahan: Anda dapat membaca tentang [pengajuan IPO S-1](https://www.dfinsolutions.com/knowledge-hub/thinkt-leadership/knowledge-resources/what-s-1-ipo-filing) untuk memahami konteks)

---
Pertanyaan 2: Strategi IPO "Fixed Days Hold".
Temukan jumlah hari X yang optimal (antara 1 dan 30), dimana pertumbuhan kuantil 75% adalah yang tertinggi?

Gunakan kembali [Cuplikan Kode 1] untuk mengambil daftar IPO dari tahun 2023 dan 2024 (dari URL: https://stockanalisis.com/ipos/2023/ dan https://stockanalisis.com/ipos/2024/). Dapatkan semua harga harian OHLCV untuk semua saham dengan "tanggal IPO" sebelum 1 Maret 2024 ("< 01-03-2024") - 184 ticker (tanpa 'RYZB'). Harap hapus 'RYZB', karena tidak lagi tersedia di Yahoo Finance.

Terkadang Anda mungkin perlu menyesuaikan nama simbol (misalnya, 'IBAC' di stockanalisis.com -> 'IBACU' di Yahoo Finance) untuk menemukan harga OHLCV untuk semua saham. Beberapa ticker seperti 'DYCQ' dan 'LEGT' berada di pasar kurang dari 30 hari (masing-masing 11 dan 21 hari). Biarkan saja di kumpulan data; itu hanya berarti Anda tidak dapat menyimpannya lebih lama dari yang tercantum.

Anggaplah Anda berhasil membeli saham baru (tercatat saat IPO) pada hari pertama dengan harga [Adj Close]]. Strategi Anda adalah menahan tepat selama X hari penuh (di mana X berada di antara 1 dan 30) dan menjual pada harga "Adj. Close" dalam X hari (misalnya, jika X=1, Anda menjual pada hari berikutnya). Temukan X, ketika pertumbuhan kuantil 75% (di antara 185 investasi) adalah yang tertinggi.

PETUNJUK:

Anda dapat membuat 30 kolom tambahan: growth_future_1d ... growth_future_30d, gabungkan dengan tabel min_dates (hari pertama ketika setiap saham memiliki data di Yahoo Finance), dan lakukan operasi vektor pada kumpulan data yang dihasilkan.
Anda dapat menggunakan fungsi DataFrame.describe() untuk mendapatkan kuantil mean, min, max, 25-50-75%.
Tambahan:

Anda juga dapat memastikan bahwa rata-rata dan hasil investasi persentil ke-50 (median) adalah negatif untuk sebagian besar nilai X, sehingga menyiratkan taruhan bagi investor yang "beruntung" yang mungkin berada di 25% teratas.
Apa rekomendasi Anda: Apakah Anda menyarankan untuk menerapkan strategi ini untuk mendapatkan X yang optimal?

---
### Pertanyaan 3: Apakah Pertumbuhan Terkonsentrasi pada Saham Terbesar?

**Dapatkan pembagian hari (persentase sebagai int) ketika Saham Besar berkinerja lebih baik (pertumbuhan_7d - pertumbuhan selama 7 periode ke belakang) saham Terbesar?**


Gunakan kembali [Cuplikan Kode 5] untuk mendapatkan statistik OHLCV untuk 33 saham
untuk data 10 tahun penuh (01-01-2014 hingga 31-12-2023):

`US_STOCKS = ['MSFT', 'AAPL', 'GOOG', 'NVDA', 'AMZN', 'META', 'BRK-B', 'LLY', 'AVGO','V', 'JPM'] `

`EU_STOCKS = ['NVO','MC.PA', 'ASML', 'RMS.PA', 'OR.PA', 'SAP', 'ACN', 'TTE', 'SIE.DE','IDEXY ','CDI.PA']`

`INDIA_STOCKS = ['RELIANCE.NS','TCS.NS','HDB','BHARTIARTL.NS','IBN','SBIN.NS','LICI.NS','INFY','ITC.NS ','HINDUNILVR.NS','LT.NS']`

`STOCKS_TERBESAR = US_STOCKS + EU_STOCKS + INDIA_STOCKS`
<br/>

Sekarang mari kita tambahkan 12-22 saham teratas (per akhir April 2024):
<br/>

`NEW_US = ['TSLA','WMT','XOM','UNH','MA','PG','JNJ','MRK','HD','COST','ORCL']`

`NEW_EU = ['PRX.AS','CDI.PA','AIR.PA','SU.PA','ETN','SNY','BUD','DTE.DE','ALV.DE ','MDT','AI.PA','EL.PA']`

`NEW_INDIA = ['BAJFINANCE.NS','MARUTI.NS','HCLTECH.NS','TATAMOTORS.NS','SUNPHARMA.NS','ONGC.NS','ADANIENT.NS','ADANIENT.NS ','NTPC.NS','KOTAKBANK.NS','TITAN.NS']`

`LARGE_STOCKS = NEW_EU + NEW_US + NEW_INDIA`

Anda seharusnya dapat memperoleh statistik untuk 33 SAHAM TERBESAR dan 32 SAHAM BESAR.

Hitung `growth_7d` untuk setiap saham dan setiap hari.
Dapatkan rata-rata `pertumbuhan_7 hari` harian untuk grup LARGEST_STOCKS vs. grup LARGE_STOCKS.

Misalnya, untuk data pertama Anda harus memiliki:
| Tanggal | kategori_ticker | pertumbuhan_7d |
|----------|:-------------:|------:|
| 01-01-2014 | BESAR | 1.011684 |
| 01-01-2014 | TERBESAR | 1.011797 |

Pada hari itu, kelompok TERBESAR tumbuh lebih cepat dibandingkan kelompok BESAR (saham baru).

Hitung jumlah hari ketika KELOMPOK BESAR (saham baru yang lebih kecil) mengungguli KELOMPOK TERBESAR, div

---
### Pertanyaan 4: Mencoba strategi Indikator Teknis Lain

Berapa total keuntungan kotor (dalam RIBUAN $) yang akan Anda peroleh dari trading di CCI (tanpa asumsi biaya)?

Pertama, jalankan seluruh Colab untuk mendapatkan DataFrame data lengkap (setelah [Cuplikan Kode 9]), dan potong menjadi data 10 tahun penuh terakhir (01-01-2014 hingga 31-12-2023). Jika Anda mengalami kesulitan dalam menjalankan Colab - Anda dapat mengunduhnya menggunakan tautan ini.

Anggaplah Anda telah mempelajari indikator CCI (Indeks Saluran Komoditas) yang mengagumkan, dan memutuskan untuk hanya menggunakannya untuk operasi Anda.

Anda menentukan nilai "defensif" dari ambang batas tinggi 200, dan Anda berdagang hanya pada hari Jumat (Tanggal.dt.dayofweek()==4).

Artinya, setiap kali Anda melihat bahwa CCI >200 untuk saham mana pun (dari 33 saham tersebut), Anda akan menginvestasikan $1000 (setiap catatan ketika CCI>200) pada harga Adj.Close dan menahannya selama 1 minggu (5 hari perdagangan). ) untuk dijual di Adj. Tutup harga.

Berapa laba kotor yang diharapkan (tanpa biaya) yang Anda peroleh dalam RIBUAN $ (nilai bilangan bulat terdekat) pada banyak operasi dalam 10 tahun? Perhitungan satu operasi: jika Anda menginvestasikan $1000 dan menerima $1010 dalam 5 hari - Anda menambahkan $10 ke laba kotor, jika Anda menerima $980 - tambahkan -$20 ke laba kotor. Anda perlu menjumlahkan hasil ini pada semua perdagangan (460 kali dalam 10 tahun).

Tambahan:

Tambahkan perkiraan penghitungan biaya untuk 460 perdagangan dari kalkulator ini https://www.degiro.ie/fees/calculator (Produk:"Saham, AS dan Kanada;" Jumlah per transaksi: "1000 EUR"; Transaksi per tahun: " 460")
apakah Anda masih mendapat untung dari perdagangan itu?
[EKSPLORASI] 

---
### Pertanyaan 5: Menemukan Strategi Anda untuk IPO

Anda telah melihat di pertanyaan pertama bahwa median dan rata-rata investasi dalam IPO adalah negatif, dan Anda tidak bisa begitu saja berinvestasi di semua transaksi.

Bagaimana Anda memperbaiki/memperbaiki pendekatan ini? Jelaskan secara singkat langkah-langkah dan data yang akan Anda coba dapatkan (secara umum hal tersebut dapat dilakukan dari sumber publik - tidak ada akses ke data internal perusahaan)?

Misalnya. (beberapa ide) Apakah Anda ingin fokus pada vertikal tertentu? Apakah Anda ingin membuat perbandingan cerdas vs. saham-saham yang ada di pasar? Atau Anda hanya ingin mendapatkan beberapa fitur (fitur apa?) seperti jumlah total orang di suatu perusahaan untuk menemukan segmen IPO yang "sukses"?
