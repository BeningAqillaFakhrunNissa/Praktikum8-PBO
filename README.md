# PRAKTIKUM PEMROGRAMAN BERORIENTASI OBJEK 8


Nama: Bening Aqilla Fakhrun Nissa
NIM: L0325018
Kelas: 3A

---
## Deskripsi Program
Program **Praktikum 8** merupakan kumpulan program berbasis console (CLI) yang dibuat dengan bahasa **Java** untuk mengimplementasikan tiga konsep lanjutan dalam Pemrograman Berorientasi Objek (OOP) sesuai dengan modul praktikum. Program ini terbagi menjadi tiga kegiatan utama, yaitu:
1. Kegiatan 1 yang mendemonstrasikan **Polymorphism (Method Overriding)** melalui hierarki kelas `Hewan` dengan subclass `Kucing` dan `Anjing` untuk melihat *Dynamic Binding* pada runtime
2. Kegiatan 2 yang mengimplementasikan **Abstract Class** dan **Abstract Method** melalui kelas `BangunDatar` dan subclass `Lingkaran` sebagai kerangka dasar hierarki kelas
3. Kegiatan 3 yang menerapkan **Interface** melalui antarmuka `AlatElektronik` dan `Kamera` yang diimplementasikan secara ganda (*multiple implementation*) oleh kelas `Smartphone`, untuk menciptakan kontrak arsitektur perangkat lunak sekaligus menyimulasikan pewarisan ganda yang tidak didukung oleh class di Java.

---
## Struktur Program

```
com.praktikum8/
├── AlatElektronik.java
├── Anjing.java
├── BangunDatar.java
├── Hewan.java
├── Kamera.java
├── Kucing.java
├── Lingkaran.java
├── PoliTester.java
├── Smartphone.java
├── TesBangunDatar.java
└── TesSmartphone.java
```
<img width="237" height="265" alt="image" src="https://github.com/user-attachments/assets/8d03d938-c287-420d-9a64-474d8769f9ad" />

Pada program ini, struktur program terdiri dari sebelas file Java yang saling berkaitan dan dikelompokkan ke dalam tiga kegiatan praktikum, yaitu `Hewan.java`, `Kucing.java`, `Anjing.java`, `PoliTester.java`, `BangunDatar.java`, `Lingkaran.java`, `TesBangunDatar.java`, `AlatElektronik.java`, `Kamera.java`, `Smartphone.java`, dan `TesSmartphone.java`.

File `Hewan.java` berisi class `Hewan` yang berfungsi sebagai superclass dasar dengan method `bersuara()`. File `Kucing.java` dan `Anjing.java` berisi subclass yang meng-override method tersebut untuk mendemonstrasikan polimorfisme. File `PoliTester.java` berisi method `main()` untuk menguji perilaku *Dynamic Binding* dari objek-objek hewan tersebut.

File `BangunDatar.java` berisi abstract class yang menjadi kerangka dasar bangun datar dengan abstract method `hitungLuas()`. File `Lingkaran.java` berisi subclass yang mengimplementasikan abstract method tersebut, dan file `TesBangunDatar.java` berisi method `main()` untuk menguji perhitungan luas lingkaran beserta method turunannya.

File `AlatElektronik.java` dan `Kamera.java` merupakan interface yang berfungsi sebagai kontrak arsitektur perangkat lunak. File `Smartphone.java` berisi class yang mengimplementasikan kedua interface tersebut secara ganda (*multiple implementation*). File `TesSmartphone.java` berisi method `main()` sebagai titik awal eksekusi untuk mensimulasikan penggunaan fitur-fitur smartphone.

---

## Kegiatan 1
 

### Kelas Hewan
Kelas `Hewan` merupakan superclass yang berfungsi sebagai kelas induk bagi kelas-kelas turunannya.

<img width="847" height="158" alt="image" src="https://github.com/user-attachments/assets/78b84e2f-c4a0-4b76-bc2e-ba91cfa168c4" />

Kelas ini memiliki satu method, yaitu `bersuara()` yang bertipe `void` dan tidak menerima parameter. Method ini berisi implementasi default yang mencetak pesan "Hewan ini mengeluarkan suara yang tidak spesifik" ke layar. Method ini nantinya akan di-override oleh subclass `Kucing` dan `Anjing`.

### Kelas Kucing
Kelas `Kucing` merupakan subclass dari `Hewan` yang meng-override method `bersuara()`.

<img width="605" height="183" alt="image" src="https://github.com/user-attachments/assets/e5820285-dca3-4cc6-89f8-12677a4cdbc7" />

Kelas ini menggunakan kata kunci `extends Hewan` untuk mewarisi kelas `Hewan`. Di dalamnya terdapat `@Override` yang bersifat opsional tetapi direkomendasikan, berfungsi sebagai penanda bahwa method `bersuara()` menimpa method dengan nama yang sama di superclass. Method ini mencetak pesan "Kucing: Meow meow!" ke layar.

### Kelas Anjing
Kelas `Anjing` juga merupakan subclass dari `Hewan` yang meng-override method `bersuara()`.

<img width="536" height="182" alt="image" src="https://github.com/user-attachments/assets/64e0721a-29bf-48cb-b18e-94f571cdaa0a" />

Kelas ini menggunakan `extends Hewan` dan `@Override`. Method `bersuara()` di kelas ini mencetak pesan "Anjing: Guk guk!" ke layar. Perbedaan cara kerja method ini bukti penerapan dari polimorfisme, yaitu kemampuan sebuah method yang sama untuk menghasilkan output berbeda sesuai dengan objek yang menggunakannya.

### Kelas PoliTester
Kelas `PoliTester` berisi method `main()` yang berfungsi untuk mengeksekusi program dan menguji penerapan polimorfisme pada kelas `Hewan`, `Kucing`, dan `Anjing`.

<img width="897" height="365" alt="image" src="https://github.com/user-attachments/assets/77e95e41-9e4c-492d-b090-d1772b48a550" />

Pada awal method, dibuat sebuah array bertipe `Hewan` dengan nama `daftarHewan` yang berukuran 3. Array ini kemudian diisi dengan tiga objek, yaitu objek `Hewan`, objek `Kucing`, dan objek `Anjing`. Proses memasukkan objek subclass ke dalam variabel bertipe superclass disebut **Upcasting**.

Selanjutnya, dilakukan perulangan `for-each` untuk menelusuri setiap elemen di dalam array. Setiap elemen dipanggil method `bersuara()`. Karena Java menggunakan mekanisme **Dynamic Binding**, method yang dipanggil ditentukan berdasarkan tipe objek aktual (bukan tipe referensinya), sehingga:
- Objek `Hewan` memanggil method `bersuara()` milik `Hewan`
- Objek `Kucing` memanggil method `bersuara()` milik `Kucing`
- Objek `Anjing` memanggil method `bersuara()` milik `Anjing`

Hal ini membuktikan bahwa satu method yang sama dapat memiliki banyak bentuk perilaku.

---

## Kegiatan 2

### Kelas BangunDatar
Kelas `BangunDatar` merupakan **abstract class** yang berfungsi sebagai kerangka dasar bagi bangun datar.

<img width="767" height="385" alt="image" src="https://github.com/user-attachments/assets/c5351422-bc55-4fbc-af96-afb246fc8493" />

Kelas ini dibuat dengan kata kunci `abstract`, sehingga tidak dapat diinstansiasi secara langsung menggunakan `new`. Kelas ini memiliki atribut `warna` bertipe `String` dan sebuah constructor yang menerima parameter `warna` untuk mengisi atribut tersebut.

Selain itu, terdapat dua method:
1. `hitungLuas()` yang merupakan **abstract method** (tidak memiliki body/isi). Method ini wajib di-override oleh setiap subclass.
2. `cetakWarna()` yang merupakan **concrete method** (memiliki isi). Method ini dapat langsung digunakan oleh subclass tanpa perlu di-override.

### Kelas Lingkaran
Kelas `Lingkaran` merupakan subclass dari `BangunDatar` yang mengimplementasikan abstract method `hitungLuas()`.

<img width="598" height="336" alt="image" src="https://github.com/user-attachments/assets/f33d7d12-669d-45d2-b21d-188d701ba6ff" />

Kelas ini memiliki atribut tambahan `jariJari` bertipe `double`. Constructor-nya menerima parameter `warna` dan `jariJari`, kemudian memanggil `super(warna)` untuk meneruskan nilai warna ke constructor superclass, dan mengisi `jariJari` dengan nilai yang diberikan.

Method `hitungLuas()` di-override dan diimplementasikan dengan rumus luas lingkaran, yaitu `Math.PI * jariJari * jariJari`. Jika method ini tidak di-override, IDE akan menampilkan error karena kelas `Lingkaran` dianggap abstract.

### Kelas TesBangunDatar
Kelas `TesBangunDatar` berisi method `main()` yang berfungsi untuk mengeksekusi program sekaligus menguji perhitungan luas pada kelas `Lingkaran`.

<img width="792" height="228" alt="image" src="https://github.com/user-attachments/assets/2140074d-77e8-43bc-90c7-4747d430a9a0" />

Pada method ini, dibuat objek `Lingkaran` dengan warna "Merah" dan jari-jari 5. Kemudian dipanggil method `cetakWarna()` yang diwarisi dari `BangunDatar` dan method `hitungLuas()` yang diimplementasikan di `Lingkaran`. Hasilnya ditampilkan ke layar.

---

## Kegiatan 3

### Interface AlatElektronik
Interface `AlatElektronik` merupakan kontrak untuk perangkat elektronik.

<img width="395" height="132" alt="image" src="https://github.com/user-attachments/assets/d35fb0e8-2e3f-40b9-8b94-01c5eef56d99" />

Interface ini dibuat dengan kata kunci `interface` dan berisi dua method, yaitu `nyalakan()` dan `matikan()`. Kedua method ini tidak memiliki body karena interface hanya mendefinisikan kontrak yang harus dipenuhi oleh kelas yang mengimplementasikannya.

### Interface Kamera
Interface `Kamera` merupakan kontrak untuk perangkat yang memiliki fitur kamera.

<img width="322" height="112" alt="image" src="https://github.com/user-attachments/assets/a32d25e5-7be5-4274-80b4-aff4e3c40827" />

Interface ini berisi satu method signature, yaitu `ambilFoto()`. Method ini juga tidak memiliki body.

### Kelas Smartphone
Kelas `Smartphone` merupakan kelas konkret yang mengimplementasikan **kedua interface** sekaligus, yaitu `AlatElektronik` dan `Kamera`.

<img width="680" height="410" alt="image" src="https://github.com/user-attachments/assets/8dd5efbf-4a5e-4f27-bd27-aa943dd82655" />
<img width="917" height="130" alt="image" src="https://github.com/user-attachments/assets/c1751e41-3b23-41b7-a286-f593955b1f87" />

Kelas ini dideklarasikan dengan `implements AlatElektronik, Kamera`, yang menunjukkan bahwa Java mendukung **multiple implementation** yang berarti sebuah kelas dapat mengimplementasikan lebih dari satu interface, meskipun Java tidak mendukung multiple inheritance untuk class.

Kelas ini memiliki atribut `merk` bertipe `String` dan constructor yang menerima parameter `merk`. Selain itu, terdapat tiga method yang di-override dari kedua interface:
1. `nyalakan()` mencetak pesan bahwa perangkat menyala dan sedang booting OS.
2. `matikan()` mencetak pesan bahwa perangkat dimatikan.
3. `ambilFoto()` mencetak pesan bahwa foto berhasil disimpan.

Ketiga method ini menggunakan simbol `@Override` dan memanfaatkan atribut `merk` untuk menyesuaikan output.

### Kelas TesSmartphone
Kelas `TesSmartphone` berisi method `main()` yang berfungsi untuk mengeksekusi program sekaligus mensimulasikan penggunaan fitur-fitur pada kelas `Smartphone`.

<img width="575" height="246" alt="image" src="https://github.com/user-attachments/assets/9928f902-5618-4c03-a0b1-1341e2b0ea7d" />

Pada method ini, dibuat objek `Smartphone` dengan merk "Samsung". Kemudian dipanggil method `nyalakan()`, `ambilFoto()`, dan `matikan()` secara berurutan untuk melihat hasil interaksinya.

---

## Hasil Eksekusi Program

Setelah program dijalankan, masing-masing kelas menampilkan hasil output.

### Output PoliTester (Polymorphism)

<img width="406" height="120" alt="image" src="https://github.com/user-attachments/assets/52052da1-8266-451e-8b42-2409f9e1516c" />

Program menampilkan tiga baris output yang berbeda, yaitu "Hewan ini mengeluarkan suara yang tidak spesifik" dari objek `Hewan`, lalu "Kucing: Meow meow!" dari objek `Kucing`, dan "Anjing: Guk guk!" dari objek `Anjing`. 

Hal ini membuktikan bahwa polimorfisme berjalan dengan baik, di mana pemanggilan method `bersuara()` yang sama dapat menghasilkan output yang berbeda sesuai dengan objek aktual yang memanggilnya.

### Output TesBangunDatar (Abstract Class)

<img width="352" height="97" alt="image" src="https://github.com/user-attachments/assets/13c58348-27b0-4bcd-b42c-942f49d00405" />

Program menampilkan pesan "Warna bangun ini adalah: Merah" yang dihasilkan dari method `cetakWarna()` warisan superclass, serta "Luas lingkaran: 78.53981633974483" yang dihasilkan dari method `hitungLuas()` yang diimplementasikan di kelas `Lingkaran`.

Hal ini membuktikan bahwa abstract class dapat menyediakan concrete method yang bisa langsung dipakai, sekaligus memaksa subclass untuk mengimplementasikan abstract method-nya.

### Output TesSmartphone (Interface)

<img width="411" height="122" alt="image" src="https://github.com/user-attachments/assets/84664792-e6e2-4f58-a8b7-55df4ba01cfc" />

Program menampilkan tiga baris output, yaitu "Samsung menyala. Booting OS..." dari method `nyalakan()`, lalu "Cekrek! Foto berhasil disimpan di galeri Samsung." dari method `ambilFoto()`, dan "Samsung dimatikan. Goodbye." dari method `matikan()`.

Hal ini membuktikan bahwa kelas `Smartphone` berhasil menerapkan aturan dari kedua interface (`AlatElektronik` dan `Kamera`) sekaligus, sehingga objek tersebut dapat memiliki perilaku dari keduanya.

---

## Kesimpulan

Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa:
1. **Polymorphism (Method Overriding)** memungkinkan sebuah method yang sama memiliki perilaku berbeda tergantung objek yang memanggilnya. Java menggunakan mekanisme *Dynamic Binding* untuk menentukan method mana yang dieksekusi saat program berjalan.
2. **Abstract Class** tidak dapat diinstansiasi secara langsung. Kelas ini sangat cocok dijadikan kerangka dasar hierarki karena dapat menampung kombinasi abstract method yang wajib di-override dan concrete method yang bisa langsung digunakan oleh subclass.
3. **Interface** berfungsi mendefinisikan aturan fungsi murni yang harus dipenuhi oleh kelas yang mengimplementasikannya. Java memungkinkan satu kelas untuk mengimplementasikan lebih dari satu interface sebagai simulasi pewarisan ganda (*multiple inheritance*) yang tidak didukung oleh class.


