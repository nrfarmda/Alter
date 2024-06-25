# Alter
SEBELUM 
![](ALTER.png)
# Menambahkan Kolom
## Struktur
```sql
ALTER TABLE nama_tabel ADD nama_colom varchar(10) AFTER nama_colom;
```
## Contoh
```sql
ALTER TABLE mobil ADD batas_peminjaman varchar(10) AFTER peminjam;
```
## Hasil
![](BATAS.png)
## Analisis
`AFTER`: opsional untuk digunakan, jika tidak menggunakan klausa ini maka secara default kolom yang dibuat akan berada di akhir. Jika kolom ingin ditaruh pada awal kolommakagunakan klausa FIRST.
## Kesimpulan
- Perintah ini adalah sebuah ALTER TABLE query yang dilakukan pada tabel "mobil".
- Tujuan dari perintah ini adalah untuk menambahkan sebuah kolom baru bernama "batas_peminjaman" pada tabel "mobil".
- Kolom "batas_peminjaman" akan memiliki tipe data "varchar(10)", yang berarti dapat menyimpan string dengan panjang maksimal 10 karakter.
- Posisi kolom "batas_peminjaman" akan ditempatkan setelah kolom "peminjam" dalam struktur tabel.
- Setelah perintah ini dijalankan, tabel "mobil" akan memiliki kolom baru bernama "batas_peminjaman" yang dapat digunakan untuk menyimpan informasi terkait batas waktu peminjaman setiap mobil.
- Langkah yang disarankan sebelum menjalankan perintah ini adalah membuat backup data terlebih dahulu untuk berjaga-jaga, dan memastikan bahwa perintah ini sesuai dengan kebutuhan Anda.
## Tambahan update
### Struktur
```sql
 UPDATE naam_tabel SET nama_colom = "nama_data" WHERE nama_colom IS NOT NULL;
```
### Contoh
```sql
 UPDATE mobil SET batas_peminjaman = "2024-04-24" WHERE peminjam IS NOT NULL;
```
### Hasil
![](UPDATE.png)
### Analisis
- `UPDATE`: Ini adalah sebuah pernyataan SQL yang digunakan untuk memperbarui data pada tabel yang ada.
- `mobil`: Ini adalah nama tabel yang akan diperbarui.
- `SET batas_peminjaman = "2024-04-24"`: Kolom "batas_peminjaman" pada tabel "mobil" akan diperbarui dengan nilai "2024-04-24" untuk setiap baris yang memenuhi kondisi di WHERE.
- `WHERE peminjam IS NOT NULL`: Kondisi ini akan membatasi pembaruan hanya pada baris-baris yang memiliki nilai NOT NULL pada kolom "peminjam". Jadi, hanya baris-baris yang memiliki nilai pada kolom "peminjam" yang akan diperbarui.
### Kesimpulan
- Perintah ini adalah sebuah UPDATE query yang dilakukan pada tabel "mobil".
- Tujuan dari perintah ini adalah untuk memperbarui nilai kolom "batas_peminjaman" pada tabel "mobil" menjadi tanggal "2024-04-24" untuk setiap baris yang memiliki nilai NOT NULL pada kolom "peminjam".
- Kondisi "WHERE peminjam IS NOT NULL" akan memastikan bahwa hanya baris-baris yang sedang dipinjam (memiliki nilai pada kolom "peminjam") yang akan diperbarui.
- Setelah perintah ini dijalankan, tanggal "batas_peminjaman" untuk setiap mobil yang sedang dipinjam akan diperbarui menjadi "2024-04-24".
- Langkah yang disarankan sebelum menjalankan perintah ini adalah membuat backup data terlebih dahulu untuk berjaga-jaga, dan memastikan bahwa perintah ini sesuai dengan kebutuhan Anda.
# Mengubah Nama kolom
## Struktur Query
```sql
ALTER TABLE nama_tabel CHANGE nama_colom nama_colom_baru;
```
## Contoh
```sql
ALTER TABLE mobil CHANGE batas_peminjaman deadline varchar(10);
```
## Hasil
![](MENGUBAH.png)
## Analisis
- **`ALTER TABLE mobil`:** Mengidentifikasi tabel yang ingin dimodifikasi, yaitu tabel `mobil`.
- **`CHANGE batas_peminjaman deadline`:** Mengubah nama kolom `batas_peminjaman` menjadi `deadline`.
- **`varchar(10)`:** Menentukan tipe data baru untuk kolom `deadline`. Tipe data `varchar(10)` memungkinkan penyimpanan string hingga 10 karakter.
## Kesimpulan
- Mengubah nama kolom: Kolom `batas_peminjaman` diubah namanya menjadi `deadline`.
- Mengubah tipe data kolom: Tipe data kolom `deadline` diubah dari format tanggal menjadi `varchar(10)`.
# Mengubah tipe data
## Struktur
```sql
ALTER TABLE nama_tabel modify nama_colom date;
```
## Contoh
```sql
ALTER TABLE mobil modify deadline DATE;
```
## Hasil
![](TIPE1.png)
## Analisis
- Perintah `ALTER TABLE` diawali dengan kata kunci `ALTER TABLE` diikuti dengan nama tabel yang ingin diubah, dalam hal ini `mobil`.
- Kata kunci `MODIFY` digunakan untuk menentukan kolom yang ingin diubah. Dalam hal ini, kolom `deadline` akan dimodifikasi.
- Tipe data baru untuk kolom `deadline` ditentukan setelah kata kunci `MODIFY`, yaitu `DATE`.
## Kesimpulan
Kesimpulan dari perintah `ALTER TABLE mobil MODIFY deadline DATE;` adalah bahwa perintah ini digunakan untuk mengubah tipe data kolom `deadline` dalam tabel `mobil` menjadi tipe data `DATE`. Tujuannya adalah untuk memastikan bahwa kolom tersebut hanya menyimpan tanggal yang valid, yang dapat meningkatkan integritas dan konsistensi data serta memudahkan pengolahan dan operasi yang melibatkan tanggal.
# Menambahkan constraint
LINK WEB https://revou.co/panduan-teknis/sql-constraint
## Struktur
```sql
 ALTER TABLE nama_tabel
    -> ALTER nama_colom SET DEFAULT 'nilai_default';
```
## Contoh
```sql
 ALTER TABLE mobil
    -> ALTER deadline SET DEFAULT 'Ready';
```
## Hasil
![](CONSTRAINT.png)
## Analisis
- Perintah diawali dengan `ALTER TABLE` diikuti nama tabel yang ingin diubah, yaitu `mobil`.
- Baris kedua menggunakan `ALTER` lagi untuk menargetkan kolom spesifik yang ingin diubah, yaitu `deadline`.
- `SET DEFAULT 'Ready'` digunakan untuk mengatur nilai default yang akan otomatis terisi pada kolom `deadline` jika tidak ada nilai lain yang dimasukkan secara manual.
## Kesimpulan
Kesimpulan dari perintah `ALTER TABLE mobil ALTER deadline SET DEFAULT 'Ready';` adalah bahwa perintah ini mencoba mengubah nilai default untuk kolom `deadline` dalam tabel `mobil` menjadi `'Ready'`.
## Tambahan constraint
### Struktur
```sql
INSERT INTO nama_tabel
    -> (colom1,colom2,colom3,colom4,colom5,colom6,colom7)
    -> VALUES (6, "nama_colom1", "nama_colom2","nama_colom3","nama_colo 3",NULL,500000);
```
### Contoh
```sql
INSERT INTO mobil
->(id_mobil,no_plat,no_mesin,warna,pemilik,peminjam,harga_rental)
-> VALUES (6, "DD 2378 AZ", "ACFDT","PUTIH","MADA",NULL,500000);
```
### Hasil
![](tambahan1.png)
### Analisis    
- Perintah `INSERT INTO` digunakan untuk menambahkan baris baru ke tabel `mobil`.
- **(id_mobil, no_plat, no_mesin, warna, pemilik, peminjam, harga_rental)**:
- Bagian ini menentukan kolom-kolom di tabel `mobil` yang akan diisi dengan nilai baru.
- `VALUES` digunakan untuk memberikan nilai yang akan dimasukkan ke kolom-kolom yang ditentukan.
- Nilai-nilai tersebut diurutkan sesuai dengan kolom yang disebutkan sebelumnya.
### Kesimpulan
Perintah `INSERT INTO mobil (id_mobil, no_plat, no_mesin, warna, pemilik, peminjam, harga_rental) VALUES (6, 'DD 2378 AZ', 'ACFDT', 'PUTIH', 'MADA', NULL, 500000);` berfungsi untuk menambahkan baris baru ke tabel `mobil`. Nilai-nilai yang dimasukkan harus sesuai dengan tipe data dan batasan kolom yang ada dalam tabel. Perintah ini akan berhasil jika semua nilai memenuhi kriteria dan batasan yang telah ditetapkan dalam definisi tabel `mobil`.
## Menghapus constraint
LINK WEB: https://www.geeksforgeeks.org/sql-drop-constraint/
### Struktur
```sql
ALTER TABLE nama_tabel
-> ALTER nama_colom DROP nama_default;
```
### Contoh
```sql
ALTER TABLE mobil
-> ALTER deadline DROP DEFAULT;
```
### Hasil
![](MENGHAPUS1.png)
### Analisis    
- Perintah `ALTER TABLE` digunakan untuk mengubah struktur tabel.
- `mobil` adalah nama tabel yang akan diubah.
- Bagian `ALTER deadline` menunjukkan bahwa kolom yang akan diubah adalah `deadline`.
- `DROP DEFAULT` menginstruksikan untuk menghapus nilai default yang sebelumnya ditetapkan pada kolom `deadline`.
### Kesimpulan
Perintah `ALTER TABLE mobil ALTER deadline DROP DEFAULT;` digunakan untuk menghapus nilai default dari kolom `deadline` dalam tabel `mobil`. Setelah perintah ini dijalankan, kolom `deadline` tidak akan memiliki nilai default, sehingga nilai `NULL` akan digunakan jika tidak ada nilai yang diberikan saat operasi `INSERT`. Perintah ini tidak mempengaruhi baris yang sudah ada, tetapi penting untuk memastikan bahwa operasi berikutnya dan aplikasi yang menggunakan tabel tersebut dapat menangani ketiadaan nilai default dengan benar.
# Menghapus kolom
### Struktur
```sql
ALTER TABLE nama_tabel DROP COLUMN nama_colom;
```
### Contoh
```sql
ALTER TABLE mobil DROP COLUMN deadline;
```
### Hasil
![](KOLOM1.png)
### Analisis
- Perintah `ALTER TABLE` digunakan untuk mengubah struktur tabel.
- `mobil` adalah nama tabel yang akan diubah.
- Bagian `DROP COLUMN` menginstruksikan untuk menghapus kolom yang ditentukan.
- `deadline` adalah nama kolom yang akan dihapus dari tabel `mobil`.
### Kesimpulan
Perintah `ALTER TABLE mobil DROP COLUMN deadline;` digunakan untuk menghapus kolom `deadline` dari tabel `mobil`. Operasi ini menghapus semua data dalam kolom tersebut dan mengubah struktur tabel. Sebelum menjalankan perintah ini, penting untuk memastikan bahwa tidak ada dependensi pada kolom `deadline` dan bahwa data penting telah dicadangkan. Selain itu, semua aplikasi dan query terkait perlu diperbarui untuk mencerminkan perubahan struktur tabel.
## Mengganti nama tabel
LINK WEB: https://www.techonthenet.com/mysql/tables/alter_table.php
### Struktur
```sql
ALTER TABLE nama_tabel RENAME TO nama_colo;
```
### Contoh
```sql
ALTER TABLE mobil RENAME TO data_mobil;
```
### Hasil
![](RENAME1.png)
### Analisis
- Perintah `ALTER TABLE` digunakan untuk mengubah struktur atau nama tabel yang ada.
- `mobil` adalah nama tabel yang akan diubah.
- Bagian `RENAME TO` menginstruksikan untuk mengganti nama tabel.
- `data_mobil` adalah nama baru yang akan diberikan kepada tabel `mobil`.
### Kesimpulan
Perintah `ALTER TABLE mobil RENAME TO data_mobil;` digunakan untuk mengganti nama tabel `mobil` menjadi `data_mobil`. Meskipun data dan struktur tabel tidak terpengaruh, semua referensi ke tabel tersebut dalam aplikasi dan skrip perlu diperbarui agar menggunakan nama baru. Operasi ini biasanya dilakukan untuk meningkatkan keterbacaan atau menyesuaikan dengan standar penamaan yang lebih baik.