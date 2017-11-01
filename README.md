# Normalisasi Database
Normalisasi database merupakan suatu pendekatan sistematis untuk meminimalkan redundansi data pada suatu database agar database tersebut dapat bekerja dengan optimal.

#### Tujuan Normalisasi Database

Tujuan normalisasi database adalah untuk menghilangkan dan mengurangi redudansi data dan tujuan yang kedua adalah memastikan dependensi data (Data berada pada tabel yang tepat).

Jika data dalam database tersebut belum di normalisasi maka akan terjadi 3 kemungkinan yang akan merugikan sistem secara keseluruhan.

    * INSERT Anomali : Situasi dimana tidak memungkinkan memasukkan beberapa jenis data secara langsung di database.
    * DELETE Anomali : Penghapusan data yang tidak sesuai dengan yang diharapkan, artinya data yang harusnya tidak terhapus mungkin ikut terhapus.
    * UPDATE Anomali : Situasi dimana nilai yang diubah menyebabkan inkonsistensi database, dalam artian data yang diubah tidak sesuai dengan yang diperintahkan atau yang diinginkan.

## TAHAPAN NORMALISASI : 

Tahapan Normalisasi dimulai dari tahap ringan (1NF) hingga paling ketat (5NF).

1. Bentuk Normal Pertama (1NF) : Menghilangkan Perulangan Grup
2. Bentuk Normal Kedua (2NF) : Menghilangkan Ketergantungan Parsial
3. Bentuk Normal Ketiga (3NF) : Menghilangkan Ketergantungan Transitif
4. Bentuk Normal Boyce-Code Form (BCNF) : Menghilangkan anomali-anomali hasil dari ketergantungan fungsional
5. Bentuk Normal Keempat (4NF) : Menghilangkan ketergantungan multivalue
6. Bentuk Normal Kelima : Menghilangkan anomali-anomali yang tersisa.

#### Tahapan Normalisasi
1. Bentuk Normal Tahap Pertama (1NF)

Bentuk normal yang pertama atau 1NF mensyaratkan beberapa kondisi dalam sebuah database, berikut adalah fungsi dari bentuk normal pertama ini.

* Bentuk normal 1NF terpenuhi jika sebuah tabel tidak memiliki atribut bernilai banyak (multivalued attribute), atribut composite atau kombinasinya dalam domain data yang sama.
* Setiap atribut dalam tabel tersebut harus bernilai atomic (tidak dapat dibagi-bagi lagi).

Gambar 1

![nf1.jpg](https://s1.postimg.org/7x4qxi0ny7/nf1.jpg)

gambar tersebut adalah contoh bentuk normal 1NF. yang menandainya adalah setiap kolom atau baris harus terisi dan setiap kolom harus mengandung satu nilai.

2. Bentuk Normal Tahap Kedua (2NF)

* Bentuk Normal 2NF terpenuhi dalam sebuah tabel jika telah memenuhi bentuk 1NF, dan semua atribut selain primary key, secara utuh memiliki Functional dependency pada primary key.
* Sebuah tabel tidak memenuhi 2NF, jika ada atribut yang ketergantungannya (Functional Dependency) hanya bersifat parsial saja (hanya tergantung pada sebagian dari primary key).
* Jika terdapat atribut yang tidak memiliki ketergantungan terhadap primary key, maka atribut tersebut harus dipindah atau dihilangkan.

Gambar 2

![2.NF.png](https://s1.postimg.org/8xylxjigz3/2.NF.png)

![2_NF.png](https://s1.postimg.org/4la9xnjcm7/2_NF.png)

![2.NF1.png](https://s1.postimg.org/8fvsuslqcv/2.NF1.png)

3. Bentuk Normal Tahap Ketiga (3NF)

* Bentuk normal 3NF terpenuhi jika telah memenuhi bentuk 2NF, dan jika tidak ada atribut non primary key yang memiliki ketergantungan terhadap atribut non primary key yang lainnya,
* Untuk setiap Functional Dependency dengan notasi X-->A, maka : X harus menjadi superkey pada tabel tersebut. Atau A merupakan bagian dari primary key pada tabel tersebut.

Gambar 3

![3.NF.png](https://s1.postimg.org/6vvknnh6f3/3.NF.png)

![3_NF.png](https://s1.postimg.org/530bm8xdfz/3_NF.png)

4. Boyce-Code Normal Form (BCNF)

* Bentuk BCNF terpenuhi dalam sebuah tabel, jika untuk setiap Functional Dependency terhadap setiap atribut atau gabungan atribut dalam bentuk : X --> Y maka X adalah Super Key.
* Tabel tersebut harus di dekomposisi berdasarkan Functional Dependency yang ada, sehingga X menjadi super key dari tabel-tabel hasil dekomposisi.
* Setiap tabel dalam BCNF merupakan 3NF. Akan tetapi setiap 3NF belum tentu termasuk BCNF. Perbedaannya, untuk Functional Dependency X--> A, BCNF tidak membolehkan A sebagai bagian dari primary key.

5. Bentuk Normal Tahap Keempat (4NF) atau MVD dan PJNF

* Bentuk normal 4NF terpenuhi dalam sebuah tabel jika telah memenuhi bentuk BCNF, dan tabel tersebut tidak boleh memiliki lebih dari sebuah multivalued attribute.
* Untuk setiap  multivalued attribute (MVD) juga harus merupakan Functional Dependency

6. Bentuk Normal Tahap Kelima (5NF)

* Bentuk normal 5NF terpenuhi jika memiliki sebuah loseloss decomposition menjadi tabel-tabel yang lebih kecil.
* Jika 4 bentuk normal sebelumnya dibentuk berdasarkan Functional Dependency, 5NF dibentuk berdasarkan konsep Join Dependence. Yakni apabila sebuah tabel telah di dekomposisi menjadi tabel-tabel lebih kecil, harus bisa digabungkan lagi untuk membentuk tabel semula.
