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

Dataset ini memiliki total 1303 data dengan 13 kolom, dan memiliki 0 missing value, adapun variabel yang digunakan pada dataset ini, adalah : 

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

<table>
    <tr>
        <td> Laptop_Id </td> 
        <td> Company </td> 
        <td> Product </td> 
        <td> TypeName </td> 
        <td> Inches </td> 
        <td> ScreenResolution </td>
        <td> CPU </td>
        <td> RAM </td>
        <td> Memory </td>
        <td> GPU </td>
        <td> OpSys </td>
        <td> Weight </td>
        <td> price_euros </td>
    </tr>
    <tr>
        <td> 725 </td> 
        <td> Lenovo </td> 
        <td> 110-15ACL (A6-7310/4GB/500GB/W10) 	 </td> 
        <td> Notebook</td> 
        <td> 15.6 </td> 
        <td> 1366x768 </td>
        <td> AMD A6-Series 7310 2GHz 	 </td>
        <td> 4GB 	 </td>
        <td> 500GB HDD </td>
        <td> AMD Radeon R4 </td>
        <td> Windows 10 	 </td>
        <td> 2.19kg </td>
        <td> 298.0 </td>
    </tr>
     <tr>
        <td> 578 </td> 
        <td> HP </td> 
        <td> 14-am079na (N3710/8GB/2TB/W10) 	 </td> 
        <td> Notebook</td> 
        <td> 14.0 </td> 
        <td> 1366x768 </td>
        <td> Intel Pentium Quad Core N3710 1.6GHz  </td>
        <td> 8GB 	 </td>
        <td> 2TB HDD </td>
        <td> Intel HD Graphics 405 </td>
        <td> Windows 10 	 </td>
        <td> 1.94kg </td>
        <td> 389.0 </td>
    </tr>
    <tr>
        <td> 1291 </td> 
        <td> HP </td> 
        <td> 15-AC110nv (i7-6500U/6GB/1TB/Radeon) </td> 
        <td> Notebook</td> 
        <td> 15.6 </td> 
        <td> 1366x768 </td>
        <td> Intel Core i7 6500U 2.5GHz  </td>
        <td> 6GB 	 </td>
        <td> 1TB HDD </td>
        <td> AMD Radeon R5 M330 </td>
        <td> Windows 10 	 </td>
        <td> 2.19kg </td>
        <td> 764.0 </td>
    </tr>
    <tr>
        <td> 1305 </td> 
        <td> HP </td> 
        <td> 15-AC110nv (i7-6500U/6GB/1TB/Radeon) </td> 
        <td> Notebook</td> 
        <td> 15.6 </td> 
        <td> 1366x768 </td>
        <td> Intel Core i7 6500U 2.5GHz  </td>
        <td> 6GB 	 </td>
        <td> 1TB HDD </td>
        <td> AMD Radeon R5 M330 </td>
        <td> Windows 10 	 </td>
        <td> 2.19kg </td>
        <td> 764.0 </td>
    </tr>
    <tr>
        <td> 1319 </td> 
        <td> HP </td> 
        <td> 15-AC110nv (i7-6500U/6GB/1TB/Radeon) </td> 
        <td> Notebook</td> 
        <td> 15.6 </td> 
        <td> 1366x768 </td>
        <td> Intel Core i7 6500U 2.5GHz  </td>
        <td> 6GB 	 </td>
        <td> 1TB HDD </td>
        <td> AMD Radeon R5 M330 </td>
        <td> Windows 10 	 </td>
        <td> 2.19kg </td>
        <td> 764.0 </td>
    </tr>
        
        
        
 </table>

dari gambar tersebut, dataframe Product sudah terurut sesuai abjad. Dapat dilihat bahwa data pertama kali yang muncul adalah '110-15ACL (A6-7310/4GB/500GB/W10)'. namun pada data tersebut masih ada duplikat nya. jadi tahap selanjutnya akan dihapus

* Drop_Duplicate : untuk menghapus data duplikasi pada laptop. dalam laporan ini, penulis menghapus duplikasi pada dataframe Product

<table>
    <tr>
        <td> Laptop_Id </td> 
        <td> Company </td> 
        <td> Product </td> 
        <td> TypeName </td> 
        <td> Inches </td> 
        <td> ScreenResolution </td>
        <td> CPU </td>
        <td> RAM </td>
        <td> Memory </td>
        <td> GPU </td>
        <td> OpSys </td>
        <td> Weight </td>
        <td> price_euros </td>
    </tr>
    <tr>
        <td> 1 </td> 
        <td> Apple </td> 
        <td> MacBook Pro</td> 
        <td> Ultrabook</td> 
        <td> 13.3 </td> 
        <td> IPS Panel Retina Display 2560x1600 </td>
        <td> Intel Core i5 2.3GHz</td>
        <td> 8GB 	 </td>
        <td> 128GB SSD </td>
        <td> Intel Iris Plus Graphics 640 	 </td>
        <td> macOS </td>
        <td> 1.37kg 	 </td>
        <td> 1339.69 </td>
    </tr>
     <tr>
        <td> 2 </td> 
        <td> Apple </td> 
        <td> Macbook Air </td> 
        <td> Notebook</td> 
        <td> 13.3 </td> 
        <td> 1440x900 </td>
        <td> Intel Core i5 1.8GHz  </td>
        <td> 8GB 	 </td>
        <td> 128GB Flash Storage </td>
        <td> Intel HD Graphics 6000 </td>
        <td> macOS 	 </td>
        <td> 1.34kg </td>
        <td> 898.94 </td>
    </tr>
    <tr>
     <tr>
        <td> 3 </td> 
        <td> HP </td> 
        <td> 250 G6 </td> 
        <td> Notebook</td> 
        <td> 15.6 </td> 
        <td> Full HD 1920x1080 </td>
        <td> Intel Core i5 7200U 2.5GHzz  </td>
        <td> 8GB 	 </td>
        <td> 256GB SSD </td>
        <td> Intel HD Graphics 620 </td>
        <td> No OS </td>
        <td> 1.86kg </td>
        <td> 575.00 </td>
    </tr>
        <td> 6 </td> 
        <td> Acer </td> 
        <td> Aspire 3 </td> 
        <td> Notebook</td> 
        <td> 15.6 </td> 
        <td> 1366x768 </td>
        <td> AMD A9-Series 9420 3GHz  </td>
        <td> 4GB 	 </td>
        <td> 500GB HDD </td>
        <td> AMD Radeon R5  </td>
        <td> Windows 10 	 </td>
        <td> 2.1kg </td>
        <td> 400.00 </td>
    </tr>
    <tr>
        <td> 9 </td> 
        <td> Asus </td> 
        <td> ZenBook UX430UN </td> 
        <td> Ultrabook </td> 
        <td> 14.0 </td> 
        <td> Full HD 1920x1080 </td>
        <td> Intel Core i7 8550U 1.8GH  </td>
        <td> 16GB 	 </td>
        <td> 512GB SSD </td>
        <td> Nvidia GeForce MX150 </td>
        <td> Windows 10 	 </td>
        <td> 1.3kg </td>
        <td> 1495.0 </td>
    </tr>
        
        
        
 </table>

dari gambar tersebut, dapat dilihat bahwa jumlah data kita berkurang. yang semulanya adalah 1303 sekarang menjadi 618. hal tersebut terjadi karena data yang terduplikat akan terhapus.

* Tolist : untuk mengubah beberapa dataframe menjadi list. cara kerja nya cukup mudah, pilih dataframe yang ingin dikonversi, lalu tambahkan tolist() di belakangnya. otomatis tipe data nya akan berubah ke tipe list. Di laporan ini penulis mengubah Company, Product, dan TypeName menjadi list. 

* Membuat Dictionary : ambil data yang sudah dikonversikan tersebut lalu satukan dalam dictionary. hal ini berguna agar dataframe yang terpanggil hanya lah yang sudah dikonversi

<table>
    <tr>
        <td> Company </td> 
        <td> Product </td> 
        <td> TypeName </td> 
     </tr>
      <tr>
        <td> Apple </td> 
        <td> Macbook pro </td> 
        <td> Ultrabook </td> 
     </tr>
     <tr>
        <td> Apple </td> 
        <td> Macbook Air </td> 
        <td> Ultrabook </td> 
     </tr>
      <tr>
        <td> Hp </td> 
        <td> 250 G6 </td> 
        <td> Notebook </td> 
     </tr>
     <tr>
        <td> Acer </td> 
        <td> Aspire 3 </td> 
        <td> Notebook </td> 
     </tr>
     <tr>
        <td> Asus </td> 
        <td> ZenBook UX430UN </td> 
        <td> Ultrabook </td> 
     </tr>
</table>

dari gambar tersebut, sekarang ada satu tabel yang hanya memiliki 3 dataframe yang telah kita ubah menjadi list. yaitu Company, Product, TypeName

### Modeling and Result

* pertama penulis membuat variabel 'data' yang berisi data dari 'laptop_new' yang telah dibuat sebelumnya. lalu ambil 5 sample 

<table>
    <tr>
        <td> Company </td> 
        <td> Product </td> 
        <td> TypeName </td> 
     </tr>
      <tr>
        <td> Asus </td> 
        <td> ZenBook UX410UA-GV183T </td> 
        <td> Notebook 	 </td> 
     </tr>
     <tr>
        <td> HP </td> 
        <td> 7-ak002nv (A10-9620P/6GB/2TB/Radeon </td> 
        <td> Notebook </td> 
     </tr>
      <tr>
        <td> Samsung 	 </td> 
        <td> Chromebook 3 	 </td> 
        <td> Netbook </td> 
     </tr>
     <tr>
        <td> HP </td> 
        <td> ProBook 450 </td> 
        <td> Notebook </td> 
     </tr>
     <tr>
        <td> Asus </td> 
        <td> ZenBook UX530UQ-PRO </td> 
        <td> Ultrabook </td> 
     </tr>
</table>




* penulis menggunakan TF-IDF Vectorizer. Teknik tersebut digunakan untuk menemukan representasi fitur penting dari setiap kategori laptop. algoritma ini menggabungkan 2 konsep, yaitu Term Frequency (TM) dan Invers Document Frequncy (IDF). setelah itu diubah dalam bentuk vektor

* penulis juga menggunakan algoritma cosine similarity. hal tersebut bertujuan untuk menghitung kesamaan (similarity) antar product. cara kerja dari algoritma ini adalah mencari tingkat kemiripan teks pada  sentence/kalimat. lalu Kemiripan teks bisa kita gunakan untuk membuat steganografi ataupun steganalysis linguistik

* lalu untuk hasil akhir nya, ketika penulis mencoba mencari rekomendasi laptop dengan tipe laptop 'Netbook'. maka akan muncul rekomendasi produk lainnya dengan tipe laptop yang sama

<table>
    <tr>
        <td> Product </td> 
        <td> Company </td> 
        <td> TypeName </td> 
     </tr>
      <tr>
        <td> TravelMate B117-M </td> 
        <td> Acer 	 </td> 
        <td> Netbook 	 </td> 
     </tr>
     <tr>
        <td> Chromebook 3</td> 
        <td> Samsung  </td> 
        <td> Netbook </td> 
     </tr>
     <tr>
        <td>  	VivoBook E201NA </td> 
        <td> Asus </td> 
        <td> Netbook </td> 
     </tr>
     <tr>
        <td> Chromebook N23 </td> 
        <td> Lenovo </td> 
        <td> Netbook </td> 
     </tr>
</table>

### Evaluation

Pertama penulis mengambil sample product 'Latitude 3180' untuk mengetahui tipe laptop tersebut.

<table>
    <tr>
        <td> Company </td> 
        <td> Product </td> 
        <td> TypeName </td> 
     </tr>
      <tr>
        <td> Lenovo </td> 
        <td> Latitude 3180 	 </td> 
        <td> Netbook 	 </td> 
     </tr>
</table>


Disini penulis menggunakan metric **Precision** untuk mengukur jumlah prediksi. adapun hasil yang saya dapatkan adalah 

![image](https://user-images.githubusercontent.com/93527916/191041571-6f2c556c-5e7f-41c8-a9ae-1bd4297a2eae.png)

dapat dilihat pada gambar tersebut bahwa prediksi saya tentang tipe laptop tersebut adalah 100%

#### Conclusion 

berdasarkan hasil laporan tersebut, hasil yang penulis dapatkan sesuai dengan apa yang diinginkan. dengan menggunakan _content based filtering_ . penulis berhasil mengembangkan sistem rekomendasi berdasarkan aktivitas masa lalu. mungkin jika penulis menerapkan _collaborative based filtering_, mungkin nantinya penulis dapat merekomendasikan laptop tidak hanya berdasarkan tipe laptopnya saja

### References

* Koo Ping Shung(2018). Accuracy, Precision, Recall or F1?. [https://towardsdatascience.com/accuracy-precision-recall-or-f1-331fb37c5cb9]
* Luthfi Ramadhan(2020). TF-IDF Simplified. [https://towardsdatascience.com/tf-idf-simplified-aba19d5f5530]
* Hendroprasetyo(2020). Perbedaan Cosine Similarity dan Cosine Distance [https://hendroprasetyo.com/perbedaan-cosine-similarity-dan-cosine-distance/#.YykJQ7RBw2w]
