# Modul 3 Pekerjaan Rumah

Dalam pekerjaan rumah ini, kita akan bekerja dengan variabel kategori, model ML pertama (Pohon Keputusan), dan penyesuaian hyperparameter.

Harap gunakan Colab Modul 3 untuk semua tugas guna memastikan Anda memiliki kerangka data yang sama dengan yang digunakan untuk bagian Pemodelan, seperti yang dibahas selama kuliah. Kami menyarankan untuk menyalin dan memperluasnya (di sekitar komentar "TODO").

## Pertanyaan 1 (1 poin): Dummies tentang Bulan dan Minggu dalam Bulan

Temukan NILAI KORELASI MUTLAK dari boneka <bulan-minggu_bulan_> yang paling berkorelasi dengan variabel hasil biner is_positif_pertumbuhan_5d_masa depan?

Anda melihat dalam analisis korelasi dan pemodelan bahwa bulan September dan Oktober mungkin merupakan bulan musiman yang penting. Dalam tugas ini, kita akan melangkah lebih jauh dan mencoba membuat boneka untuk Bulan dan Minggu dalam sebulan (mulai dari 1). Misalnya, minggu pertama bulan Oktober harus diberi kode seperti ini: 'Oktober_w1'. Setelah Anda membuat kumpulan variabel baru, temukan variabel yang paling berkorelasi (dalam nilai absolut) dengan is_positif_growth_5d_future dan bulatkan menjadi 3 digit setelah koma.

Jalur yang disarankan menuju solusi:

[Sumber] Gunakan rumus ini untuk mendapatkan minggu dalam bulan untuk variabel tanggal dan waktu d: (d.hari-1)//7+1
Tentukan variabel string baru untuk semua kombinasi bulan-minggu_dari_bulan. Tambahkan ke kumpulan fitur CATEGORICAL. Anda seharusnya memiliki 5 variabel yang diperlakukan sebagai KATEGORIS sekarang: 'Bulan', 'Hari Kerja', 'Ticker', 'ticker_type', 'month_wom'. Pada akhirnya, Anda akan mendapatkan 115 fitur tiruan, termasuk 60 (=12*5) boneka minggu_bulan_minggu.
Gunakan pandas.get_dummies() untuk menghasilkan boneka.
Gunakan fungsi pandas.DataFrame.corr() (juga digunakan dalam [Cuplikan Kode 1]) untuk mendapatkan korelasi dengan is_positif_growth_5d_future, filter hanya variabel yang mewakili kumpulan dummy baru, dan urutkan berdasarkan nilai absolut (Anda dapat menentukan kolom baru "abs_corr " dalam kerangka data dengan korelasi), dan temukan nilai tertinggi (di antara kumpulan fitur boneka baru).
CATATAN: boneka baru akan digunakan sebagai fitur dalam tugas berikutnya, harap tinggalkan di kumpulan data.

## Pertanyaan 2 (2 poin): Tentukan aturan "tangan" baru pada variabel indikator makro dan teknis

Berapa skor presisi untuk prediksi BARU terbaik (pred3 atau pred4), yang dibulatkan menjadi 3 digit setelah koma?

Mari kita manfaatkan pengetahuan dari pohon yang divisualisasikan (clf10) (Cuplikan Kode 5: 1.4.4 Visualisasi):

Anda diminta untuk mendefinisikan dua aturan 'tangan' baru (mengarah ke subpohon 'positif'):

pred3_manual_gdp_fastd: (gdppot_us_yoy <= 0,027) & (fastd >= 0,251)
pred4_manual_gdp_wti_oil: (gdppot_us_yoy >= 0,027) & (growth_wti_oil_30d <= 1,005)
Perluas Cuplikan Kode 3 (Prediksi "aturan tangan" manual): Hitung dan tambahkan aturan baru (pred3 dan pred4) ke kerangka data. Anda akan melihat bahwa salah satu prediksi tidak memiliki prediksi positif pada kumpulan data TEST (meskipun sudah banyak di TRAIN+VALIDASI).

Debug: periksa di new_df dan dataset asli/proses pembuatan data bahwa kami tidak melakukan kesalahan apa pun selama langkah transformasi data.

Jelaskan mengapa hal ini bisa terjadi meskipun tidak ada kesalahan pada fitur data.

Hasilnya, tuliskan skor presisi untuk prediktor yang tersisa (dibulatkan menjadi tiga koma desimal). Misalnya. jika Anda memiliki 0,57897, jawaban Anda seharusnya 0,579.

## Pertanyaan 3 (1 poin): Prediksi unik yang benar dari Pengklasifikasi Pohon Keputusan sedalam 10 tingkat (pred5_clf_10)

Berapa jumlah total catatan dalam kumpulan data TEST ketika prediksi baru pred5_clf_10 lebih baik daripada semua aturan 'tangan' (pred0..pred4)?

CATATAN: harap sertakan random_state=42 ke fungsi init Decision Tree Classifier (baris clf = DecisionTreeClassifier(max_kedalaman=max_kedalaman, random_state=42)) untuk memastikan semua orang mendapatkan hasil yang sama.

Solusi yang disarankan:

Langkah 1: Tulis ulang bagian '1.4.3 Inferensi untuk pohon keputusan' untuk Pengklasifikasi Pohon Keputusan dengan max_ depth = 10 (clf_10), sehingga Anda sesuai dengan model pada set TRAIN+VALIDATION (tidak berubah dari kuliah), tetapi prediksi pada seluruh set X_all (untuk dapat mendefinisikan kolom baru 'pred5_clf_10' dalam kerangka data new_df). Berikut tautan beserta penjelasannya. Ini akan menyelesaikan masalah di 1.4.5 ketika prediksi dibuat hanya untuk kumpulan data Uji dan tidak dapat dengan mudah digabungkan dengan kumpulan data lengkap.

Langkah 2: Setelah Anda memilikinya, tentukan kolom baru 'only_pred5_is_true' mirip dengan aturan prediksi 'tangan' dengan beberapa ketentuan: is_positif_growth_5d_future DAN is_true_pred5 harus sama dengan 1, sedangkan semua prediksi lainnya is_true_pred0..is_true_pred4 harus sama dengan 0.

Langkah3: Ubah kolom 'only_pred5_is_true' dari bool menjadi int, dan temukan berapa kali kolom tersebut sama dengan 1 di set TEST. Tuliskan ini sebagai jawabannya.

LANJUTAN: mendefinisikan fungsi yang dapat diterapkan ke seluruh baris prediksi (beberapa contoh fungsi baris penerapan panda) dan dapat menemukan apakah beberapa prediksi 'predX' (di mana X adalah salah satu prediksinya) benar secara unik. Ini akan berfungsi meskipun ada 100 prediksi yang tersedia, sehingga Anda tidak menentukan kondisi untuk 'predX' secara manual.

## Pertanyaan 4: (2 poin) Penyetelan hyperparameter untuk Pohon Keputusan

Berapa kedalaman pohon optimal (dari 1 hingga 20) untuk DecisionTreeClassifier?

CATATAN: harap sertakan random_state=42 ke fungsi init Decision Tree Classifier (baris clf = DecisionTreeClassifier(max_kedalaman=max_kedalaman, random_state=42)) untuk memastikan konsistensi dalam hasil.

Ikuti langkah-langkah berikut untuk menemukan kedalaman_maks yang optimal:

Ulangi nilai max_kedalaman dari 1 hingga 20.
Latih Pengklasifikasi Pohon Keputusan dengan parameter max_kedalaman saat ini.
Secara opsional, visualisasikan bagaimana 'kepala' setiap pohon yang dipasang berubah dengan pohon yang lebih maju (=dalam). Anda dapat menggunakan fungsi sklearn.tree.plot_tree(), atau cara ringkas dengan fungsionalitas ekspor_teks() (contoh Stack Overflow):
dari sklearn.tree impor ekspor_teks
aturan_pohon = ekspor_teks(model, nama_fitur=daftar(X_train), kedalaman_maks=3)
cetak(aturan_pohon)
Hitung skor presisi (Anda dapat menggunakan fungsi sklearn.metrics.precision_score()) pada kumpulan data TEST untuk setiap pohon yang dipasang. Anda juga dapat membandingkannya dengan skor presisi pada kumpulan data VALIDASI, yang disertakan dalam fase pelatihan (agar memiliki lebih banyak data untuk dilatih). Anda akan melihat bahwa skor presisi pada set VALIDASI mulai bertambah seiring dengan kompleksitas pohon (overfit), yang tidak terlihat pada skor presisi pada TEST.
Identifikasi max_kedalaman optimal, dengan skor presisi tertinggi pada kumpulan data TEST. Catat nilai ini sebagai best_max_ depth dan kirimkan sebagai jawaban.
Buat prediksi pada semua catatan (LATIHAN+VALIDASI+UJI) dan tambahkan prediksi baru pred6_clf_best ke kerangka data new_df.
Selain itu, bandingkan skor presisi pohon keputusan yang disesuaikan dengan prediksi sebelumnya. Anda harus mengamati peningkatan (>0,58, atau presisi lebih dari 58%), yang menunjukkan bahwa pohon yang disetel mengungguli aturan "tangan" manual dan prediksi Pohon Keputusan sebelumnya.

LANJUTAN: Baca selengkapnya tentang berbagai aspek Pohon Keputusan scikit-learn. Gambarkan garis presisi/akurasi vs. max_kedalaman dan catat apakah ada titik jenuh presisi/akurasi seiring bertambahnya max_kedalaman. Secara teori, harus ada trade-off antara penyesuaian yang lebih baik (=pohon yang lebih kompleks) dan generalisasi.

## [EKSPLORASI] Pertanyaan 5: Data apa yang hilang?

Sekarang setelah Anda memiliki wawasan dari analisis korelasi dan Pohon Keputusan mengenai variabel yang paling berpengaruh, sarankan indikator baru yang ingin Anda sertakan dalam kumpulan data dan jelaskan alasannya.

Anda juga dapat mengusulkan sesuatu yang sama sekali berbeda berdasarkan intuisi Anda, namun hal tersebut harus relevan dengan kumpulan data bersama dari saham-saham terbesar di India, UE, dan AS. Jika Anda memilih pendekatan ini, harap tentukan juga sumber datanya.

