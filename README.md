# pacil_mart

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

# TUGAS 7
#### Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?
###### Stateless Widget:
Stateless widget tidak memiliki keadaan internal (state). Ini berarti bahwa setelah widget stateless dibangun, ia tidak dapat berubah atau merespons perubahan apa pun. Sebagai contoh, widget ini berguna untuk menggambar tampilan yang tidak perlu mengubah dirinya sepanjang waktu.
Stateless widget diimplementasikan dengan meng-override method build. Mereka dapat menerima data sebagai argumen tetapi tidak bisa menyimpan atau mengubahnya dalam keadaan internal.
Stateful Widget:

###### Stateful Widget
memiliki keadaan internal yang dapat berubah sepanjang waktu. Mereka digunakan ketika Anda ingin memperbarui tampilan berdasarkan perubahan data atau kejadian tertentu. Misalnya, dalam aplikasi yang memerlukan pembaruan data secara real-time.
Stateful widget mengandung dua kelas: kelas widget itu sendiri (stateful) dan kelas state terkait yang mengatur keadaan internal. Keadaan ini dapat diperbarui dan mengubah tampilan widget saat keadaan berubah. Stateful widget diimplementasikan dengan meng-override method createState.

#### Seluruh widget yang saya gunakan untuk menyelesaikan tugas ini dan penjelasan fungsinya masing-masing:
Kode yang Anda berikan adalah kode Flutter yang digunakan untuk membangun antarmuka aplikasi. Berikut adalah daftar widget yang digunakan dalam kode tersebut beserta penjelasan fungsinya:

1. MaterialApp : Ini adalah root widget dari aplikasi Flutter. Ini menginisialisasi aplikasi dan mendefinisikan berbagai properti konfigurasi seperti judul aplikasi, tema, dan penggunaan Material Design 3 (Material You).

2. Scaffold: Scaffold adalah widget yang menyediakan kerangka kerja untuk aplikasi Anda. Ini mendefinisikan struktur umum dari aplikasi, termasuk AppBar, Drawer, dan banyak elemen tata letak lainnya.

3. AppBar : AppBar adalah widget yang digunakan untuk membuat bilah aplikasi di bagian atas layar. Ini biasanya berisi judul aplikasi, tindakan, dan widget lain yang terkait dengan aplikasi.

4. MyHomePage : Ini adalah widget yang mewakili halaman utama aplikasi. Ini adalah tampilan beranda aplikasi yang berisi daftar item toko.

5. ListView : ListView adalah widget yang digunakan untuk membuat daftar item yang dapat digulir. Ini membantu dalam menampilkan daftar item toko dengan cara yang dapat digulir oleh pengguna.

6. GridView : GridView.count digunakan untuk membuat tata letak grid dengan jumlah kolom yang ditentukan (dalam kasus ini, 3 kolom). Ini digunakan untuk menampilkan item toko dalam bentuk grid.

7. ShopItem : Ini adalah kelas yang digunakan untuk merepresentasikan item toko. Setiap item toko memiliki nama dan ikon yang sesuai.

8. ShopCard : Ini adalah widget yang digunakan untuk menampilkan setiap item toko dalam bentuk kartu. Ini termasuk ikon, teks, dan respons ketika diklik. Ketika item toko diklik, SnackBar muncul dengan pesan yang sesuai.

#### Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)
Berikut adalah langkah-langkah yang ada dalam tutorial "Getting Started with Flutter" yang telah Anda berikan:

###### Buat Flutter
1. Buka Terminal atau Command Prompt.
2. Masuk ke direktori untuk menyimpan proyek Flutter.
3. Generate proyek Flutter baru dengan nama pacil_mart_mobile, kemudian masuk ke dalam direktori proyek tersebut.
    ```dart
    flutter create pacil_mart_mobile
    cd pacil_mart_mobile
    ```
    
4. Jalankan proyek melalui Terminal atau Command Prompt.
   ```dart
   flutter run
   ```
###### Merapikan struktur 
5. Merapikan struktur proyek dengan membuat file baru bernama menu.dart pada direktori pacil_mart_mobile/lib dan memindahkan kode yang ada dalam class MyHomePage ke file menu.dart. Kemudian tambhakn import pada menu.dart
    ```dart
    import 'package:flutter/material.dart';
    ```

6. Cut baris ke 39 sampai bawah dan pindahkan ke menu.dart
    ```dart
    class MyHomePage ... {
        ...
    }

    class _MyHomePageState ... {
        ...
    }
    ```
7. pada main.dart tambahkan import seperti ini 
    ```dart
    import 'package:pacil_mart_mobile/menu.dart';
    ```
8. kemudian jalankan program pada CMD

###### Membuat Widget
9. Pada file main.dart ubah kode colornya dengan menggunakan kode ini
    ```dart
    colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
    ```
10. Kemudian ubah sifat widget menjadi stateless, pada main.dart hapus bagian MyHomePage(title: 'Flutter Demo Home Page') menjadi seperti ini
    ```dart
    MyHomePage()
    ```
11. dan pada menu.dart ubah bagian ({super.key, required this.title}) menjadi ({Key? key}) : super(key: key); dan Hapus final String title; menjadi seperti ini 
    ```dart
        class MyHomePage extends StatelessWidget {
        MyHomePage({Key? key}) : super(key: key);

        @override
        Widget build(BuildContext context) {
            return Scaffold(
                ...
            );
        }
    }
    ```
12. Memperlihatkan card , define tipe pada list seperti ini 
    ```dart
    class ShopItem {
    final String name;
    final IconData icon;

    ShopItem(this.name, this.icon);
    }
    ```
13. dan pada bagian bawah  MyHomePage({Key? key}) : super(key: key); tambhakan kode ini 
    ```dart
        final List<ShopItem> items = [
        ShopItem("Lihat Item", Icons.checklist),
        ShopItem("Tambah Item", Icons.add_shopping_cart),
        ShopItem("Logout", Icons.logout),
    ];
    ```
14. dan tambahkan kode di dalam Widget Build seperti ini
    ```dart
    return Scaffold(
            appBar: AppBar(
              title: const Text(
                'Pacil Mart',
              ),
            ),
            body: SingleChildScrollView(
              // Widget wrapper yang dapat discroll
              child: Padding(
                padding: const EdgeInsets.all(10.0), // Set padding dari halaman
                child: Column(
                  // Widget untuk menampilkan children secara vertikal
                  children: <Widget>[
                    const Padding(
                      padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                      // Widget Text untuk menampilkan tulisan dengan alignment center dan style yang sesuai
                      child: Text(
                        'Pacil Shop', // Text yang menandakan toko
                        textAlign: TextAlign.center,
                        style: TextStyle(
                          fontSize: 30,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                    ),
                    // Grid layout
                    GridView.count(
                      // Container pada card kita.
                      primary: true,
                      padding: const EdgeInsets.all(20),
                      crossAxisSpacing: 10,
                      mainAxisSpacing: 10,
                      crossAxisCount: 3,
                      shrinkWrap: true,
                      children: items.map((ShopItem item) {
                        // Iterasi untuk setiap item
                        return ShopCard(item);
                      }).toList(),
                    ),
                  ],
                ),
              ),
            ),
          );
    
    ```
15. tambahkan widget stateless baru untuk menampilkan card seperti ini
    ```dart
    class ShopCard extends StatelessWidget {
    final ShopItem item;

    const ShopCard(this.item, {super.key}); // Constructor

    @override
    Widget build(BuildContext context) {
        return Material(
        color: Colors.indigo,
        child: InkWell(
            // Area responsive terhadap sentuhan
            onTap: () {
            // Memunculkan SnackBar ketika diklik
            ScaffoldMessenger.of(context)
                ..hideCurrentSnackBar()
                ..showSnackBar(SnackBar(
                    content: Text("Kamu telah menekan tombol ${item.name}!")));
            },
            child: Container(
            // Container untuk menyimpan Icon dan Text
            padding: const EdgeInsets.all(8),
            child: Center(
                child: Column(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                    Icon(
                    item.icon,
                    color: Colors.white,
                    size: 30.0,
                    ),
                    const Padding(padding: EdgeInsets.all(3)),
                    Text(
                    item.name,
                    textAlign: TextAlign.center,
                    style: const TextStyle(color: Colors.white),
                    ),
                ],
                ),
            ),
            ),
        ),
        );
    }
    }
    ```