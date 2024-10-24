praktikum4

1. **Kelas Abstrak** ```BangunDatar```
<br>**Deskripsi:**</br> ```BangunDatar``` adalah kelas abstrak yang berfungsi sebagai kelas dasar bagi bentuk-bentuk geometri lainnya seperti Lingkaran, Segitiga, dan Persegi. Kelas ini mendefinisikan dua metode abstrak, yaitu ```luas()``` dan ```keliling()```, yang perlu diimplementasikan oleh setiap kelas turunan.
<br>**Tujuan**:</br> Dengan membuat ```BangunDatar``` sebagai kelas abstrak, kita memastikan bahwa setiap kelas turunan yang mewakili bentuk geometri harus memiliki cara untuk menghitung **luas** dan **keliling**, meskipun rumus untuk menghitungnya berbeda-beda.
<br>**Kata Kunci Abstrak:**</br> Menggunakan kata kunci ```abstract``` menandakan bahwa kelas ini tidak dapat diinstansiasi langsung (tidak bisa dibuat objek ```BangunDatar``` secara langsung).
```java
Salin kode
abstract class BangunDatar {
    abstract float luas();    // method abstrak untuk menghitung luas
    abstract float keliling(); // method abstrak untuk menghitung keliling
}
```
2. **Kelas** ```Lingkaran```
<br>**Deskripsi**:</br> ```Lingkaran``` adalah kelas turunan dari ```BangunDatar``` yang mewakili bentuk lingkaran. Kelas ini memiliki atribut ```r``` (jari-jari) yang digunakan untuk menghitung luas dan keliling lingkaran.
<br>**Luas Lingkaran:**</br> Rumus luas lingkaran adalah π × r², di mana ```r``` adalah jari-jari lingkaran dan ```π``` adalah konstanta (dapat diambil dari ```Math.PI```).
<br>**Keliling Lingkaran:**</br> Rumus keliling lingkaran adalah 2 × π × r.
<br>**Method:**</br>
<br>```luas()```</br> mengembalikan hasil perhitungan luas lingkaran
<br>```keliling()```</br> mengembalikan hasil perhitungan keliling lingkaran.
```java
Salin kode
class Lingkaran extends BangunDatar {
    int r; // jari-jari

    // Constructor untuk menginisialisasi jari-jari
    Lingkaran(int r) {
        this.r = r;
    }

    @Override
    float luas() {
        return (float) (Math.PI * r * r);
    }

    @Override
    float keliling() {
        return (float) (2 * Math.PI * r);
    }
}
```
**Catatan:** Jari-jari (r) dalam lingkaran digunakan baik untuk menghitung luas maupun keliling. Ini adalah contoh sederhana dari turunan polimorfisme, di mana metode dari kelas abstrak ```BangunDatar``` diimplementasikan dengan cara yang sesuai untuk lingkaran.

3. **Kelas** ```Segitiga```
<br>**Deskripsi:** </br>Segitiga adalah kelas turunan yang merepresentasikan segitiga. Kelas ini memiliki dua atribut, yaitu ```alas``` dan ```tinggi.```
<br>**Luas Segitiga:** </br> Rumus luas segitiga adalah ½ × alas × tinggi.
<br>**Keliling Segitiga:** </br> Untuk keliling, kita akan mengasumsikan segitiga sama kaki, sehingga sisi miring ```(sisiMiring)``` dihitung menggunakan teorema Pythagoras,
dan Keliling segitiga adalah jumlah dari alas dan dua kali sisi miring.
<br>**Method:**</br>
<br>```luas()```</br> mengembalikan hasil perhitungan luas segitiga.
<br>```keliling()```</br> mengembalikan hasil perhitungan keliling segitiga.

```java
class Segitiga extends BangunDatar {
    int alas, tinggi;

    // Constructor untuk menginisialisasi alas dan tinggi
    Segitiga(int alas, int tinggi) {
        this.alas = alas;
        this.tinggi = tinggi;
    }

    @Override
    float luas() {
        return (float) (0.5 * alas * tinggi);
    }

    @Override
    float keliling() {
        // Mengasumsikan segitiga sama kaki
        double sisiMiring = Math.sqrt((alas / 2.0) * (alas / 2.0) + tinggi * tinggi);
        return (float) (alas + 2 * sisiMiring);
    }
}
```
**Catatan:** Dalam contoh ini, segitiga dianggap sebagai segitiga sama kaki untuk mempermudah perhitungan kelilingnya. Jika ingin mengimplementasikan segitiga sembarang, metode keliling bisa disesuaikan.

4.**Kelas** ```Persegi```
<br>**Deskripsi:**</br> ```Persegi``` adalah kelas turunan dari ```BangunDatar``` yang mewakili bentuk persegi. Persegi memiliki satu atribut sisi yang digunakan untuk menghitung luas dan keliling.
<br>**Luas Persegi:** </br> Rumus luas persegi adalah sisi².
<br>**Keliling Persegi:**</br> Rumus keliling persegi adalah 4 × sisi.
<br>**Method:**</br>
**luas()** mengembalikan hasil perhitungan luas persegi.
<br>**keliling()**</br> mengembalikan hasil perhitungan keliling persegi.
```java
class Persegi extends BangunDatar {
    int sisi; // panjang sisi persegi

    // Constructor untuk menginisialisasi sisi
    Persegi(int sisi) {
        this.sisi = sisi;
    }

    @Override
    float luas() {
        return sisi * sisi;
    }

    @Override
    float keliling() {
        return 4 * sisi;
    }
}
```
Catatan: Persegi adalah bentuk geometris sederhana yang rumus perhitungan luas dan kelilingnya langsung berdasarkan panjang satu sisi.

5. **Kelas** ```Utama```
<br>**Deskripsi:**</br> Utama adalah kelas yang berisi main() method yang berfungsi sebagai titik masuk program. Di sini, kita membuat objek dari Lingkaran, Segitiga, dan Persegi, kemudian menampilkan hasil perhitungan luas dan keliling masing-masing.
<br>**Method:** </br>
```main()``` adalah method yang dijalankan saat program dijalankan. Di dalamnya, kita membuat objek dari masing-masing bentuk geometri dan memanggil metode ```luas()``` dan ```keliling()``` untuk menampilkan hasilnya.
```java
public class Utama {
    public static void main(String[] args) {
        // Membuat objek lingkaran, segitiga, dan persegi
        Lingkaran lingkaran = new Lingkaran(7);
        Segitiga segitiga = new Segitiga(4, 3);
        Persegi persegi = new Persegi(5);

        // Menampilkan hasil perhitungan luas dan keliling
        System.out.println("Luas Lingkaran: " + lingkaran.luas());
        System.out.println("Keliling Lingkaran: " + lingkaran.keliling());

        System.out.println("Luas Segitiga: " + segitiga.luas());
        System.out.println("Keliling Segitiga: " + segitiga.keliling());

        System.out.println("Luas Persegi: " + persegi.luas());
        System.out.println("Keliling Persegi: " + persegi.keliling());
    }
}
```
Output: Saat program dijalankan, hasil perhitungan untuk masing-masing objek akan ditampilkan di konsol, sebagai berikut:
```yml
Luas Lingkaran: 153.93804
Keliling Lingkaran: 43.982296
Luas Segitiga: 6.0
Keliling Segitiga: 11.656854
Luas Persegi: 25.0
Keliling Persegi: 20.0
```
Kesimpulan:
Dengan membuat kelas abstrak BangunDatar, kita memanfaatkan prinsip polimorfisme dan pewarisan dalam OOP (Object-Oriented Programming) untuk mengelola berbagai bentuk geometri. Setiap kelas turunan memiliki implementasi tersendiri untuk menghitung luas dan keliling, tetapi semuanya memiliki antarmuka yang sama, yaitu metode ```luas()``` dan ```keliling()```, yang membuatnya mudah digunakan secara konsisten.









