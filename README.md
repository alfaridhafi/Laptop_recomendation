# Laporan Proyek Machine Learning - Muhammad Dhafi Alfaridzi

## Project Overview

Di zaman yang sudah modern ini, sudah pasti memiliki laptop adalah salah satu opsi terbaik. Laptop merupakan perangkat komputer portable yang mudah digunakan, mudah dibawa kemanapun orang pergi, dan telah menjadi kebutuhan dalam membantu pekerjaan sehari-hari.

Namun, tak jarang bagi masyarakat untuk menentukan laptop terbaik bagi mereka. berbagai kebutuhan merupakan salah satu aspek penting dalam menentukan laptop yang akan digunakan. ada yang menggunakan laptop untuk mengerjakan tugas, bermain game, menonton film, dan lainnya. Dalam hal tersebut, tipe laptop yang digunakan pun akan berbeda-beda tergantung bagaimana pengguna menggunakannya.

untuk itulah penulis tertarik untuk mengambil topik ini dalam laporan akhir. dengan menggunakan _content based filtering_, diharapkan calon pembeli laptop tidak kebingungan dalam menentukan laptop yang akan dibeli. dengan menggunakan sistem rekomendasi, penulis akan memberikan rekomendasi terbaik tentang laptop berdasarkan tipe laptop tersebut.

## Business Understanding

### Problem Statement

berdasarkan latar belakang tersebut, adapun permasalahan yang akan diselesaikan pada proyek ini adalah:

* Bagaimana merekomendasikan produk laptop berdasarkan tipe laptop?
* Bagaimana membuat sistem rekomendasi berdasarkan aktivitas pada masa lalu?

### Goals 

dari permasalahan tersebut. adapun tujuan yang akan dicapai, diantaranya:

* Dapat merekomendasikan produk laptop berdasarkan tipe laptop
* Dapat membuat sistem rekomendasi berdasarkan aktivitas masa lalu

### Solution Approach

* Dengan menggunakan algoritma _content based filtering_, pengguna akan mendapatkan rekomendasi berdasarkan apa yang mereka suka, atau berdasarkan aktivitas di masa lalu

* Membuat analisa berapa jumlah tipe laptop yang paling banyak digunakan

## Data Understanding

Dataset yang digunakan pada proyek ini adalah **Laptop Price**. dataset ini didapatkan dari situs kaggle dengan link : https://www.kaggle.com/datasets/muhammetvarl/laptop-price

Dataset ini memiliki total 1303 data dengan 13 kolom, dan memiliki 4 missing value, adapun variabel yang digunakan pada dataset ini, adalah : 

* Laptop_id : kode untuk identifikasi laptop
* Company : Produsen laptop
* Product : Merek dan Model nya
* TypeName : Tipe laptop tersebut 
* Inches : ukuran layar pada laptop tersebut
* ScreenResolution : Resolusi Layar pada laptop tersebut
* CPU : _Central Processing Unit_ pada laptop tersebut
* Ram : _Random Accces Memory_ pada laptop tersebut
* Memory : penyimpanan pada laptop tersebut
* GPU : _Graphics Processing Units_ pada laptop tersebut
* OpSys : _Operating System_ pada laptop tersebut
* Weight : berat laptop tersebut
* Price_euros : harga laptop tersebut berdasarkan mata uang euro

### Exploratory Data Analysis

* membuat analisa terkait jumlah produk berdasarkan tipe laptop

![image](https://user-images.githubusercontent.com/93527916/191031043-ce96abf6-6b24-4fb6-8fea-dee8c0561294.png)

dari grafik tersebut, dapat disimpulkan bahwa Notebook memiliki jumlah terbanyak, yaitu sekitar 700 unit. dan dapat dilihat bahwa Netbook memiliki jumlah paling sedikit, yaitu sekitar 30 unit

### Data Preparation

* Sort_Values : mengurutkan dataframe laptop berdasarkan Product. Hal ini untuk memudahkan kita dalam mencari data berdasarkan abjadnya

![image](https://user-images.githubusercontent.com/93527916/191127327-d0068133-8184-44f2-8e28-f5410d1495a9.png)

dari gambar tersebut, dataframe Product sudah terurut sesuai abjad. Dapat dilihat bahwa data pertama kali yang muncul adalah '110-15ACL (A6-7310/4GB/500GB/W10)'

* Drop_Duplicate : untuk menghapus data duplikasi pada laptop. dalam laporan ini, penulis menghapus duplikasi pada dataframe Product

![image](https://user-images.githubusercontent.com/93527916/191127565-66cf883c-7cd4-45ff-b392-a0ab70b15d1a.png)

dari gambar tersebut, dapat dilihat bahwa jumlah data kita berkurang. yang semulanya adalah 1303 sekarang menjadi 618. hal tersebut terjadi karena data yang terduplikat akan terhapus.

* Tolist : untuk mengubah beberapa dataframe menjadi list. di laporan ini penulis mengubah Company, Product, dan TypeName menjadi list. 

![image](https://user-images.githubusercontent.com/93527916/191127817-b6f51f9e-7c6d-4291-933e-d932d980e3ea.png)

dari gambar tersebut, penulis mengecek apakah ke tiga dataframe tersebut memiliki jumlah yang sama dan apakah sudah berubah menjadi list

* Membuat Dictionary : ambil data yang sudah dikonversikan tersebut lalu satukan dalam dictionary. hal ini berguna agar dataframe yang terpanggil hanya lah yang sudah dikonversi

![image](https://user-images.githubusercontent.com/93527916/191128007-40728441-fc71-4100-93a1-31c2c2316e48.png)

dari gambar tersebut, sekarang ada satu tabel yang hanya memiliki 3 dataframe yang telah kita ubah menjadi list. yaitu Company, Product, TypeName

### Modeling and Result

* penulis menggunakan TF-IDF Vectorizer. Teknik tersebut digunakan untuk menemukan representasi fitur penting dari setiap kategori laptop

![image](https://user-images.githubusercontent.com/93527916/191034856-a1426d43-10d4-45c1-9341-422f657bc8c8.png)

* penulis juga menggunakan algoritma cosine similarity. hal tersebut bertujuan untuk menghitung kesamaan (similarity) antar product

![image](https://user-images.githubusercontent.com/93527916/191035314-eb116a6c-38e7-4ca8-a785-6969580c533b.png)

* lalu untuk hasil akhir nya, ketika penulis mencoba mencari rekomendasi laptop dengan tipe laptop 'Netbook'. maka akan muncul rekomendasi produk lainnya dengan tipe laptop yang sama

![image](https://user-images.githubusercontent.com/93527916/191035702-79e90fc7-0ce0-490f-a39b-b783659fa2e4.png)

### Evaluation

Disini penulis menggunakan metric **Precision** untuk mengukur jumlah prediksi. adapun hasil yang saya dapatkan adalah 

![image](https://user-images.githubusercontent.com/93527916/191041571-6f2c556c-5e7f-41c8-a9ae-1bd4297a2eae.png)

dapat dilihat pada gambar tersebut bahwa prediksi saya tentang tipe laptop tersebut adalah 100%

#### Conclusion 

berdasarkan hasil laporan tersebut, hasil yang penulis dapatkan sesuai dengan apa yang diinginkan. dengan menggunakan _content based filtering_ . penulis berhasil mengembangkan sistem rekomendasi berdasarkan aktivitas masa lalu. mungkin jika penulis menerapkan _collaborative based filtering_, mungkin nantinya penulis dapat merekomendasikan laptop tidak hanya berdasarkan tipe laptopnya saja

### References

Koo Ping Shung(2018). Accuracy, Precision, Recall or F1?. [https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9]
