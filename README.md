# Customer-Personality-Analysis
![image](https://github.com/chasanah35/Customer-Personality-Analysis/assets/153416978/cd2a68f5-279d-4259-809a-0db03bb3b1ad)

This project was created to fulfill the final assignment supervised by Academy Bootcamp Data Science Batch 23B

## **⚙ Background ⚙**
Customer personality analysis helps a business to modify its product based on its target customers from different types of customer segments

## **⚙ Data PreProcessing ⚙**

About The Dataset

[Marketing campaign]( https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis)


![image](https://github.com/chasanah35/Customer-Personality-Analysis/assets/153416978/f9dfcf24-0883-40da-a745-b77913b07f9d)

Data contains 29 columns with 2240 rows

Dataset Description:
 * People
   - ID
   - Year_Birth
   - Education
   - Marital_Status
   - IncomeKidhome
   - Teenhome
   - Dt_Customer
   - Recency
   - Complain
  
* ProductsID
  - MntWines
  - MntFruits
  - MntMeatProducts
  - MntFishProducts
  - MntSweetProducts
  - MntGoldProds
    
* Promotion
  - NumDealsPurchases
  - AcceptedCmp1
  - AcceptedCmp2
  - AcceptedCmp3
  - AcceptedCmp4
  - AcceptedCmp5

* Place
  - NumWebPurchases
  - NumCatalogPurchases
  - NumStorePurchases
  - NumWebVisitsMonth


 ## **⚙ Drop Missing Value and Duplicates ⚙**

Observation:

Data contains 29 columns with 2240 rows

missing value ada di kolom income sebanyak 24
menggunakan median untuk mengisi nilai yang hilang dikolom income,
 
lalu, duplicate data checking  >> clean

 ## **⚙ Simplifying the features ⚙**

 menyederhanakan beberapa fitur agar memudahkan dalam menentukan clutering, sebagai berikut :
 
 fitur "shopping" adalah kumpulan dari data penjualan produk selama 2 tahun terahir
 
 fitur "relationship" adalah kumpulan data dari "marital status" yaitu dengan menggati beberapa kategori didalamnya menjadi
 
    "in_relationship" jika hidup dengan pasangan
    "single" jika hanya hidup sendiri
    
 fitur "Children" adalah kumpulan dari data Kidhome dan teenhome
 
 fitur "members_home" adalah fitur baru yang dibuat untuk mengetahui berapa banyak anggota yang tinggal bersama dalam satu rumah
 
 fitur "Is_Parent" untuk mengetahui apakah mereka mempunyai anak dirumahnya
 
 fitur "Purchases" adalah kumpulan dari produk yang dibeli customer pada saat ada campaign
 
 fitur "num_purchases" adalah kumpulan dari dimana pelanggan membeli produk, seperti dari store, situs web dan lain-lain


 **⚙ Outliers ⚙**

 dari beberapa fitur diatas, terdapat outlier di income dan age,

 mengambil tindakan untuk menghapus outliers, karena kurang relevan dan mengkhawatirkan akan menjadi bias.

  **⚙ melakukan korelasi antar fitur ⚙**

  untuk mengetahui korelasi antar fitur menggunakan 'sns.heatmap', dengan hasil :

  semua fitur mempunyai korelasi yang bagus, ada beberapa fitur yang mempunyai nilai diatas 0.80, yaitu (**Childreen**), (**shopping**) dan (**members_home**)

  dalam hal ini saya masih mempertahankan fitur tersebut, karena data tersebut masih diperlukan dan berpengaruh dalam proses selanjutnya.



  ## **⚙ Clustering ⚙** ##

  menggunakan metode elbow untuk menentukan jumlah cluster, metode elbow digunakan untuk mencari titik di grafik dimana penurunan skor inertia tidak lagi signifikan dalam       variasi data.

  dari hasil yang didapat, idealnya adalah 5 cluster,


  **⚙ Visualisasi dengan scatterplot ⚙**
  
  dari 5 cluster tersebut, lalu divisualisasikan dengan scatterplot, dan dapat dilihat diagram tersebut menunjukan sebaran data pelanggan yang dibagi berdasarkan masing-      masing cluster sesuai dengan algoritma K-Means Clustering

  dilihat dari jumlahnya, cluster 3 mempunyai jumlah paling banyak

  **⚙ visualisasi dari beberapa sampel cluster ⚙**

  1. shopping dan income :
     
     - cluster 1: high shopping & high income
     - cluster 2: most are low shopping and income, but some are in high.
     - cluster 3 & 4: most are low shopping and income
     - cluster 5 : high shopping & low income

       
  2. Usia
     
     - cluster 1 : usia sekitar <30 tahun s/d <80 tahun
     - cluster 2 : usia sekitar >30 tahun s/d <80 tahun
     - cluster 3 : usia sekitar >30 tahun s/d <80 tahun
     - cluster 4 : usia sekitar <30 tahun s/d <80 tahun
     - cluster 5 : usia sekitar >40 tahun s/d <80 tahun
    
 3. relationship
    
    - cluster 1 : mayoritas single
    - cluster 2 : mayoritas single
    - cluster 3 : mayoritas in_relationship
    - cluster 4 : mayoritas in_relationship
    - cluster 5 : mayoritas single
   
 ## **⚙ Profiling ⚙** ##    

   **⚙ Cluster 1 ⚙**
   
   - usia sekitar <30 - <80
   - mayoritas adalah orang yang hidup sendiri (single)
   - beberapa mempunyai anak kecil di rumah
   - beberapa mempunyai 4 anggota di keluarganya
   - High income and spent

  **⚙ Cluster 2 ⚙**

  - usia antara >30- <80
  - mayoritas adalah orang yang hidup sendiri (single)
  - kapabilitas tertinggi pada pembelanjaan produk dalam 2 tahun terahir
  - beberapa mempunyai 4 anggota di keluarganya

 **⚙ Cluster 3 ⚙**
 
  - usia sekitar >30- <80
  - mayoritas adalah orang yang hidup berpasangan
  - the majority of these people are in relationship not single living
  - beberapa mempunyai 4 anggota di keluarganya
  - cluster dengan jumlah terbanyak

 **⚙ Cluster 4 ⚙**
 
  - usia sekitar <30 - <80
  - mayoritas adalah orang yang hidup berpasangan
  - beberapa mempunyai 3 anggota
  - kebanyakan mempunyai anak remaja di keluarganya
  - cluster dengan jumlah paling sedikit

**⚙ Cluster 5 ⚙**

 - usia sekitar >40 s/d <80 tahun
 - mayoritas adalah orang yang hidup sendiri (single)
 - anggota anak-anak dan remaja lebih dominan di cluster ini


 ## **⚙ CONCLUSION & RECOMMENDATION ⚙** ## 

 - memanfaatkan cluster 2 untuk memperbanyak penawaran produk, karena dari hasil penjualan terahir, cluster 2 paling tinggi diantara cluster yang lain
   dan mayoritas cluster 2 mempunyai anggota keluarga yang banyak
   
- cluster 3 harus menjadi perhatian khusus, karena penjualan di cluster ini cukup rendah, dapat dengan mengadakan beberapa promo diproduk-produk yang sering dibeli.
 



 






 




  

 

 

















