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

adapun variabel yang digunakan pada dataset ini, adalah : 

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

### Data Preparation

* Sort_Values : mengurutkan dataframe laptop berdasarkan Product. Hal ini untuk memudahkan kita dalam mencari data berdasarkan abjadnya
* Drop_Duplicate : untuk menghapus data duplikasi pada laptop. dalam laporan ini, penulis menghapus duplikasi pada dataframe Product
* Konversi Data : mengubah beberapa dataframe menjadi list. di laporan ini penulis mengubah Company, Product, dan TypeName menjadi list. 
* Membuat Dictionary : ambil data yang sudah dikonversikan tersebut lalu satukan dalam dictionary. hal ini berguna agar dataframe yang terpanggil hanya lah yang sudah dikonversi

### Modeling and Result

* penulis menggunakan TF-IDF Vectorizer. Teknik tersebut digunakan untuk menemukan representasi fitur penting dari setiap kategori laptop

![image](https://user-images.githubusercontent.com/93527916/191034856-a1426d43-10d4-45c1-9341-422f657bc8c8.png)

* penulis juga menggunakan algoritma cosine similarity. hal tersebut bertujuan untuk menghitung kesamaan (similarity) antar product

![image](https://user-images.githubusercontent.com/93527916/191035314-eb116a6c-38e7-4ca8-a785-6969580c533b.png)

* lalu untuk hasil akhir nya, ketika penulis mencoba mencari rekomendasi laptop dengan tipe laptop 'Netbook'. maka akan muncul rekomendasi produk lainnya dengan tipe laptop yang sama

![image](https://user-images.githubusercontent.com/93527916/191035702-79e90fc7-0ce0-490f-a39b-b783659fa2e4.png)

