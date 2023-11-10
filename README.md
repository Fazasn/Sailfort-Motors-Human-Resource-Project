# Sailfort-Motors-Human-Resource-Project

## Understand The Business Scenario and Problem

### Context
Departemen HRD di Salifort Motors ingin mengambil beberapa inisiatif untuk meningkatkan tingkat kepuasan karyawan di perusahaan. Mereka telah mengumpulkan data dari karyawan, tetapi sekarang mereka tidak tahu apa yang harus dilakukan dengannya. Mereka meminta saya sebagai seorang profesional analisis data untuk memberikan saran berdasarkan data berdasarkan pemahaman saya tentang data tersebut. Mereka memiliki pertanyaan berikut: apa yang kemungkinan besar membuat karyawan meninggalkan perusahaan?

Tujuan saya dalam proyek ini adalah untuk menganalisis data yang dikumpulkan oleh departemen HRD dan untuk membangun model yang memprediksi apakah iya atau tidak seorang karyawan akan meninggalkan perusahaan.

Jika saya dapat memprediksi karyawan yang kemungkinan besar akan berhenti, saya mungkin dapat mengidentifikasi faktor-faktor yang berkontribusi pada kepergian mereka. Karena menemukan, mewawancarai, dan mempekerjakan karyawan baru membutuhkan waktu dan biaya, meningkatkan retensi karyawan akan bermanfaat bagi perusahaan.

Target :

0 : Karyawan tidak ingin berhenti bekerja.

1 : Karyawan berhenti bekerja.

Pada dataset yang diberikan perusahaan, berisikan data yang mewakili profil karyawan yang telah meninggalkan perusahaan.

### Problem Statement 
Perusahaan ingin mengidentifikasi karyawan yang berpotensi atau berisiko untuk pergi meninggalkan perusahaan dengan cara melihat faktor - faktor apa saja yang mungkin mendorong seorang karyawan untuk meninggalkan perusahaan dan tentunya hal ini dapat membuat perusahaan mengetahui bagaimana agar karyawan yang ada dapat betah dan tidak ada keinginan untuk keluar (*Employee Retention*).

### Goals 
Dalam proyek ini, tujuan kami berputar di sekitar analisis mendalam data yang dikumpulkan oleh departemen SDM perusahaan Sailfort Motors untuk mengetahui faktor apa saja yang membuat seorang karyawan betah atau ingin keluar agar dapat membuat rencana yang membuat karyawan betah dan juga pembuatan model untuk menentukan apakah seorang karyawan mungkin akan meninggalkan perusahaan dan juga tentunya tetap di perusahaan.

### Analytic Approach
Jadi yang akan kita lakukan adalah menganalisis data untuk menemukan pola yang membedakan karyawan yang mau keluar dari perusahaan dan yang tidak.
Kemudian kita akan membangun model klasifikasi yang akan membantu perusahaan untuk dapat memprediksi probabilitas seorang karyawan akan/ingin keluar dari perusahaan tersebut atau tidak.

### Metric Evaluation

<img src='https://www.researchgate.net/profile/Mohammad-Haque-41/publication/333499920/figure/fig1/AS:767004050980864@1559879424238/A-confusion-matrix-summarises-all-possible-outcomes-in-a-binaryclassification-problem.png'>

Type 1 error : False Positive  diprediksi keluar padahal tidak
Konsekuensi: perusahaan kehilangan pegawai loyal, mengeluarkan cost untuk mentreat pegawai yang sebenarnya tidak ingin keluar atau justru dapat membuat pegawai memiliki perasaan kebingungan atau ketidaknyamanan akibat diprediksi mau keluar.

Type 2 error : False Negative  ketika diprediksi tidak keluar padahal keluar
Konsekuensi: terganggunya flow pekerjaan dan perusahaan harus menemukan, mewawancarai, dan mempekerjakan karyawan baru yang membutuhkan waktu dan biaya.

Berdasarkan konsekuensinya, maka sebisa mungkin yang akan kita lakukan adalah membuat model yang dapat mengurangi cost perekrutan dari perusahaan tersebut, tetapi sebisa mungkin tidak mengurangi pegawai yang loyal dengan perusahaan sehingga harus seimbang antara keduanya oleh karena itu kami disini menggunakan metric roc_auc.

## Familiarize with the HR dataset

Kumpulan data yang akan Anda gunakan dalam laboratorium ini berisi 15.000 baris dan 10 kolom untuk variabel yang tercantum di bawah ini.

**Catatan:** lihat sumbernya di [Kaggle](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv).

| Variabel  | Data Type, Length | Deskripsi  |
| --- | --- | --- |
| satisfaction_level | int64 | Tingkat kepuasan kerja yang dilaporkan oleh karyawan 0~1 |
| last_evaluation | int64 | Nilai penilaian kinerja terakhir karyawan 0~1 |
| number_project | int64 | Jumlah proyek yang diambil oleh karyawan |
| average_monthly_hours | int64 | Rata-rata jumlah jam kerja karyawan per bulan |
| time_spend_company | int64 | Lama karyawan telah bekerja di perusahaan (tahun) |
| Work_accident | int64 | Apakah karyawan mengalami kecelakaan saat bekerja |
| left | int64 | Apakah karyawan telah meninggalkan perusahaan |
| promotion_last_5years | int64 | Apakah karyawan telah dipromosikan dalam 5 tahun terakhir |
| Department | str | Departemen karyawan |
| salary | str | Gaji karyawan (dalam dolar Amerika Serikat) |

![Confusion Matrix](https://github.com/Fazasn/Sailfort-Motors-Human-Resource-Project/assets/120705804/69d2118e-85f2-4637-a062-f402e29c0ad0)

![Screenshot 2023-11-10 170932](https://github.com/Fazasn/Sailfort-Motors-Human-Resource-Project/assets/120705804/676f709a-00f9-4c13-bdae-5c3329111610)

## Conclusion

Berdasarkan hasil classification report dari model ini, dapat disimpulkan bahwa bila seandainya nanti kita menggunakan model ini untuk melihat list karyawan yang akan keluar/tetap, maka model ini dapat mengetahui 99% karyawan yang tetap bekerja dengan perusahaan, dan model ini dapat mendapatkan 93% karyawan yang ingin keluar dari perusahaan. (semua ini berdasarkan recallnya)

Model ini memiliki ketepatan prediksi karyawan yang ingin keluar sebesar 93% (precisionnya), jadi setiap model kita memprediksi bahwa seorang karyawan itu ingin keluar, maka kemungkinan tebakannya benar itu sebesar kurang lebih 93%. Maka masih akan ada karyawan yang sebenarnya tidak keluar tetapi diprediksi sebagai karyawan yang keluar sekitar 6% dari keseluruhan karyawan yang keluar (berdasarkan recall).

## Recommendation

Model dan feature importance yang diambil dari model mengonfirmasi bahwa karyawan di perusahaan tersebut tidak puas bekerja di perusahaan.

Untuk mempertahankan karyawan, rekomendasi berikut dapat disampaikan kepada pemangku kepentingan:

* Tingkatkan kepuasaan karyawan yang bekerja.
* Batasi jumlah proyek yang dikerjakan oleh setiap karyawan.
* Pertimbangkan untuk mempromosikan karyawan yang telah bekerja di perusahaan setidaknya selama empat tahun, atau lakukan penyelidikan lebih lanjut tentang mengapa karyawan dengan masa kerja empat tahun merasa sangat tidak puas.
* Berikan penghargaan kepada karyawan yang bekerja lebih lama, atau tidak mengharuskan mereka melakukannya.
* Jika karyawan tidak memahami kebijakan upah lembur perusahaan, beri tahu mereka tentang hal ini. Jika ekspektasi seputar beban kerja dan waktu istirahat tidak eksplisit, jelaskan.
* Mengadakan diskusi di seluruh perusahaan dan dalam tim untuk memahami dan mengatasi budaya kerja perusahaan, secara menyeluruh dan dalam konteks tertentu.
* Nilai evaluasi yang tinggi tidak boleh diberikan kepada karyawan yang bekerja 200+ jam per bulan. Pertimbangkan skala proporsional untuk memberi penghargaan kepada karyawan yang berkontribusi lebih banyak/berusaha lebih keras.

**Untuk Modeling**
* Mencoba algorithm ML yang lain dan juga mencoba hyperparameter tuning kembali, coba gunakan teknik oversampling yang berbeda juga selain Random Over Sampling, seperti SMOTENC, dll. 
* Menganalisa data-data yang model kita masih salah tebak untuk mengetahui alasannya dan karakteristiknya bagaimana.
* mengurangi fitur yang tidak berpengaruh terhadap target (keluar atau tidak)

**tambahan**:

Jika memang terdapat kekhawatiran tentang kebocoran data. Sebaiknya pertimbangkan bagaimana prediksi berubah ketika `last_evaluation` dihapus dari data. Ada kemungkinan bahwa evaluasi tidak dilakukan terlalu sering, sehingga akan berguna jika dapat memprediksi retensi karyawan tanpa fitur ini. Mungkin juga skor evaluasi menentukan apakah seorang karyawan akan keluar atau tetap tinggal, sehingga berguna untuk melakukan pivot dan mencoba memprediksi skor kinerja. Hal yang sama juga berlaku untuk skor kepuasan.
