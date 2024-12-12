# BatikLens

Ini adalah repository publik aplikasi mobile BatikLens yang di kembangkan oleh tim **C242-PS249** program bangkit<br>
Beberapa direktori di repository yang berisi file **delete_this.txt** adalah direktori kosong, file tersebut di sematkan untuk memuat template struktur folder repository. Karena git tidak dapat menyimpan folder kosong. 


## Deskripsi Aplikasi
**BatikLens** adalah aplikasi berbasis Android yang memanfaatkan teknologi machine learning untuk mengenali dan mengklasifikasikan motif batik secara akurat. Aplikasi ini memungkinkan pengguna untuk mengetahui jenis batik seperti Batik Cendrawasih, Batik Dayak, Batik Geblek Renteng, Batik Megamendung, Batik Parang, Batik Pring Sedapur, Batik Tambal, dan Batik Truntum hanya dengan mengambil foto menggunakan kamera ponsel. Sebagai alat edukasi interaktif, BatikLens memberikan informasi mendetail tentang sejarah dan makna setiap motif, sekaligus mendorong apresiasi terhadap warisan budaya Indonesia.


## Arsitektur Aplikasi
Aplikasi BatikLens yang ditampilkan dalam gambar di atas memanfaatkan model ResNet50 yang dikembangkan menggunakan bahasa pemrograman Python. Model ini kemudian dikonversi ke dalam format TensorFlow Lite (TFLite) agar dapat digunakan pada platform mobile. Setelah konversi, model TFLite diintegrasikan ke dalam proyek Android yang sudah ada, sehingga aplikasi ini dapat secara akurat mengklasifikasikan berbagai jenis batik.


## Dataset
### Deskripsi Dataset BatikLens
Dataset BatikLens terdiri dari 8 jenis batik tradisional Indonesia yang digunakan untuk melatih model klasifikasi. Setiap jenis batik memiliki jumlah data yang sama, yaitu 101 gambar, dengan total keseluruhan dataset sebanyak 808 gambar. Berikut adalah rincian jumlah data untuk setiap jenis batik:

```markdown
| Jenis Batik            | Jumlah Data |
|------------------------|-------------|
| Batik Cendrawasih      | 101         |
| Batik Dayak            | 101         |
| Batik Geblek Renteng   | 101         |
| Batik Megamendung      | 101         |
| Batik Parang           | 101         |
| Batik Pring Sedawung   | 101         |
| Batik Tambal           | 101         |
| Batik Truntum          | 101         |


## Model Deep Learning
### Algoritma ResNet50
Model yang diimplementasikan dalam kode ini menggunakan pendekatan transfer learning dengan TensorFlow dan Keras, khususnya memanfaatkan arsitektur ResNet50 untuk tugas klasifikasi gambar, terutama dalam mengenali berbagai pola batik dari dataset yang tersedia. Model ini dimulai dengan mengimpor pustaka yang diperlukan dan memuat dataset batik dari Google Drive, kemudian membagi dataset menjadi set pelatihan dan validasi. ResNet50, yang diambil dengan bobot yang telah dilatih sebelumnya dari ImageNet, digunakan sebagai model dasar tanpa lapisan atas untuk memungkinkan penyesuaian pada lapisan output sesuai dengan jumlah kelas batik yang ada. Setelah menambahkan beberapa lapisan kustom seperti GlobalAveragePooling2D, Dense, dan Dropout, model dikompilasi menggunakan optimizer Adam dan fungsi loss categorical crossentropy. Selama pelatihan, model ini dilatih selama 10 epoch dan divalidasi terhadap dataset pengujian. Setelah proses pelatihan, model dapat digunakan untuk memprediksi gambar baru, dan evaluasi kinerjanya dilakukan dengan membuat confusion matrix.

