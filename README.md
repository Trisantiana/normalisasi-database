# Normalisasi Database
Normalisasi database merupakan suatu pendekatan sistematis untuk meminimalkan redundansi data pada suatu database agar database tersebut dapat bekerja dengan optimal. Teori ini pertama kali ditemukan oleh Dr. Codd kira-kira sekitar tahun 1970-an. 
Dalam melakukan normalisasi harus dilakukan funcional dependency(FD). FD dapat disimbolkan dengan X->Y yang artinya Y meiliki ketergantungan dengan X atau X secsara functional memiliki ketergantungan dengan Y.

**Normalisasi harus dilakukan apabila :**
- Data yang sama tersimpan di beberapa tempat.
- Ketidakmampuan untuk menghasilkan informasi yang dibutuhkan.
- Terjadi kehilangan data yang tidak disengaja.
- Terjadi adanya redudansi atau duplikasi data sehingga memboroskan ruang dan menyulitkan proses updating data.
- Adanya NULL Value.

#### Tujuan Normalisasi Database

- Menghilangkan dan mengurangi redudansi data.
- Memastikan dependensi data (Data berada pada tabel yang tepat).
- Mempermudah pemodifikasian data

Jika data dalam database tersebut belum di normalisasi maka akan terjadi 3 kemungkinan yang akan merugikan sistem secara keseluruhan.

- *INSERT* Anomali : Situasi dimana tidak memungkinkan memasukkan beberapa jenis data secara langsung di database.
- *DELETE* Anomali : Penghapusan data yang tidak sesuai dengan yang diharapkan, artinya data yang harusnya tidak terhapus mungkin ikut terhapus.
- *UPDATE* Anomali : Situasi dimana nilai yang diubah menyebabkan inkonsistensi database, dalam artian data yang diubah tidak sesuai dengan yang diperintahkan atau yang diinginkan.

## TAHAPAN NORMALISASI : 

Tahapan Normalisasi dimulai dari tahap ringan (1NF) hingga paling ketat (5NF).

1. Bentuk Normal Pertama (1NF) : Menghilangkan Perulangan Grup
2. Bentuk Normal Kedua (2NF)   : Menghilangkan Ketergantungan Parsial
3. Bentuk Normal Ketiga (3NF)  : Menghilangkan Ketergantungan Transitif
4. Bentuk Normal Boyce-Code Form (BCNF) : Menghilangkan anomali-anomali hasil dari ketergantungan fungsional
5. Bentuk Normal Keempat (4NF) : Menghilangkan ketergantungan multivalue
6. Bentuk Normal Kelima (5NF)  : Menghilangkan anomali-anomali yang tersisa.

[![Tahapan-_Normalisasi.jpg](https://s1.postimg.org/5nyhs6wxu7/Tahapan-_Normalisasi.jpg)](https://postimg.org/image/8bny2jpz63/)


#### Tahapan Normalisasi

__Functional Dependency__
Sebelum melakukan normalisasi harus menentukan dulu functional dependency atau ketergantungan fungsional.
Disimbolkan : `A -> B` (maka `B` bergantung pada `A` dan `A` menentukan `B`)
Dan jika diberikan dalam 2 rows dalam table T maka pasti A kesatu sama dengan A kedua begitu juga dengan B 

__Bentuk Unnormalized__
* Mempunyai penggandaan file yang sejenis, jika diisikan data maka kemungkinan akan terjadi null value atau multivalue
* Isi tabel memungkinkan terjadinya null value.
Cara merubah table dari tidak normal kebentuk normal ke1 : <br>
a). Penulisan berulang sesuai dengan atribut key-nya yg masih dalam 1 relasi (tapi tidak dianjurkan, karena menybabkan redudancy dengan penulisan berualng-ulang).<br>
b). Mencari nilai max, misal disebuah alamat ada 3 value, maka ditulis ALAMAT1, ALAMAT2, ALAMAT3, ALAMAT-N (tidak dianjurkan karena bisa menyebabkan terjadinya null value).<br>
c). Hapus sebuah atribut yang memiliki lebih dari 1 value, lalu pisahakkan dengan membuat table baru (yang paling dianjurkan).


1. Bentuk Normal Tahap Pertama (1NF)

Bentuk normal yang pertama atau 1NF mensyaratkan beberapa kondisi dalam sebuah database, berikut adalah fungsi dari bentuk normal pertama ini.

* Bentuk normal 1NF terpenuhi jika sebuah tabel tidak memiliki atribut bernilai banyak (multivalued attribute), atribut composite atau kombinasinya dalam domain data yang sama.
* Setiap atribut dalam tabel tersebut harus bernilai atomic (tidak dapat dibagi-bagi lagi).
* Isi table tidak memungkinkan terjadinya null value
* Menjaga setiap entry data dari relasi (perpotongan baris-kolom) memiliki maksimal satu nilai tunggal.

[![image.jpg](https://s1.postimg.org/4srj52x9wv/image.jpg)](https://postimg.org/image/9btk822quj/)

2. Bentuk Normal Tahap Kedua (2NF)

* Bentuk Normal 2NF terpenuhi dalam sebuah tabel jika telah memenuhi bentuk 1NF, dan semua atribut selain primary key, secara utuh memiliki Functional dependency pada primary key.
* Sebuah tabel tidak memenuhi 2NF, jika ada atribut yang ketergantungannya (Functional Dependency) hanya bersifat parsial saja (hanya tergantung pada sebagian dari primary key).
* Jika terdapat atribut yang tidak memiliki ketergantungan terhadap primary key, maka atribut tersebut harus dipindah atau dihilangkan.

**Tujuan**

- Menghapus beberapa subset data yang ada pada tabel dan menempatkan mereka pada tabel terpisah.
- Menciptakan hubungan antara tabel baru dan tabel lama dengan menciptakan foreign key.
- Tidak ada atribut dalam tabel yang secara fungsional bergantung pada candidate key tabel tersebut.

[![image.jpg](https://s1.postimg.org/7nwyp16yun/image.jpg)](https://postimg.org/image/5hxk39fb3f/)

3. Bentuk Normal Tahap Ketiga (3NF)

* Bentuk normal 3NF terpenuhi jika telah memenuhi bentuk 2NF, dan jika tidak ada atribut non primary key yang memiliki ketergantungan terhadap atribut non primary key yang lainnya,
* Untuk setiap Functional Dependency dengan notasi X-->A, maka : X harus menjadi superkey pada tabel tersebut. Atau A bergantung pada X.
* Harus tidak ada ketergantungan secara transitif(tidak langsung). Jadi kergantungan field-field yang bukan primary key harus mutlak.
* Tidak dijumpai ketergantungan Transitive dependency (ketergantungan fungsional antara 2 lebih atribut bukan Primary Key)


##### Penjelasan Gambar 

pada gambar dibawah ini adalah contoh 3Nf. pada gambar normal ke 2 disitu terdapat field __No.Order, tgl.order, item, dan deskripsi__. disitu belum terjadi bentuk normal 3 karena masih ada field yang belum mutlak atau masih samar-samar. pada gambar normal ke 2 field __no.order__ adalah sebagi PK dan yang bergantung pada PK adalah field __tgl.order__ dan field __item__ sedangkan field __deskripsi__ itu tergantung pada field __item__ tetapi field __item__ bergantung pada field __no.order__ sehingga field __deskripsi__ juga menjadi bergantung pada field __no.order__ tapi belum mutlak. sehingga pada gambar normal ke 3 di uraikan lagi bahwa field __deskripsi__ bergantung pada field __item__ dan field __deskripsi__ tidak perlu ditulis pada normal ke 3. jadi terbentuk normal 3 (3NF) seperti pada gambar sebelah normal ke 3 isi fieldnya cukup __no.order, tgl.order, dan item__.

[![image.jpg](https://s1.postimg.org/1ybmdgniu7/image.jpg)](https://postimg.org/image/4pkolj9mvv/)

4. Boyce-Code Normal Form (BCNF)

BCNF ditemukan oleh: R.F. Boyce dan E.F. Codd. BCNF merupakan sebuah teknik normalisasi database yang sering disebut 3.5NF, BCNF memiliki hubungan yang sangat erat dengan bentuk 3NF. Pada dasarnya adalah untuk menghandle anomali dan overlooping yang tidak dapat di handle dalam bentuk 3NF. Normalisasi database bentuk ini tergantung dari kasus yang disediakan. Tidak semua tabel wajib di normalisasi dalam bentuk BCNF, tetapi demi mendapatkan rancangan yang baik BCNF perlu dilakukan.

* Bentuk BCNF terpenuhi dalam sebuah tabel, jika untuk setiap Functional Dependency terhadap setiap atribut atau gabungan atribut dalam bentuk : X --> Y maka X adalah Super Key.
* Tabel tersebut harus di dekomposisi berdasarkan Functional Dependency yang ada, sehingga X menjadi super key dari tabel-tabel hasil dekomposisi.
* Setiap tabel dalam BCNF merupakan 3NF. Akan tetapi setiap 3NF belum tentu termasuk BCNF. Perbedaannya, untuk Functional Dependency X--> A, BCNF tidak membolehkan A sebagai bagian dari primary key.

![image.jpg](http://slideplayer.info/slide/3770094/12/images/4/Cara+medekomposisi+relasi+yang+telah+dalam+bentuk+normal+ketiga+kedalam+bentuk+normal+BCNF+adalah:+Carilah+semua+determinan+Bila+terdapat+penentu+yang+bukan+kunci+kandidat,+maka+Pisahkan+relasi+tersebut,+dan+Buat+penentu+tersebut+sebagai+kunci+primer.jpg)

5. Bentuk Normal Tahap Keempat (4NF) atau MVD dan PJNF

* Bentuk normal 4NF terpenuhi dalam sebuah tabel jika telah memenuhi bentuk BCNF, dan tabel tersebut tidak boleh memiliki lebih dari sebuah multivalued attribute.
* Untuk setiap  multivalued attribute (MVD) juga harus merupakan Functional Dependency

6. Bentuk Normal Tahap Kelima (5NF)

* Bentuk normal 5NF terpenuhi jika memiliki sebuah loseloss decomposition menjadi tabel-tabel yang lebih kecil.
* Jika 4 bentuk normal sebelumnya dibentuk berdasarkan Functional Dependency, 5NF dibentuk berdasarkan konsep Join Dependence. Yakni apabila sebuah tabel telah di dekomposisi menjadi tabel-tabel lebih kecil, harus bisa digabungkan lagi untuk membentuk tabel semula.
