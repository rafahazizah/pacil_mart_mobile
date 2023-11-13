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

# TUGAS 8
## Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!
1. Navigator.push(): Metode ini digunakan untuk menavigasi ke halaman baru dan menambahkannya ke tumpukan halaman (stack) yang ada. Hal ini berarti halaman sebelumnya tetap ada di tumpukan dan dapat kembali ke halaman tersebut jika diperlukan.
```dart
  if (item.name == "Lihat Item") {
      Navigator.push(context,
        MaterialPageRoute(builder: (context) => ItemListPage(itemList: itemList)));
    }

```

2. Navigator.pushReplacement(): Metode ini digunakan untuk menavigasi ke halaman baru dan menggantikan halaman saat ini di tumpukan halaman. Jadi, halaman sebelumnya dihapus dari tumpukan dan Anda tidak dapat kembali ke halaman tersebut. 
```dart
 if (item.name == "Tambah Item") {
    Navigator.pushReplacement(
        context,
        MaterialPageRoute(
          builder: (context) => ShopFormPage(),
        ));
  }
```

## Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!
1. Container: Widget ini memungkinkan Anda untuk menyesuaikan widget anak dengan menambahkan padding, margin, border, atau warna latar belakang

2. Row dan Column: Widget ini digunakan untuk menata widget anak secara horizontal (Row) atau vertikal (Column)

3. Stack: Widget ini berguna jika Anda ingin menumpuk beberapa widget anak, misalnya memiliki beberapa teks dan gambar, yang ditumpuk dengan widget lain2

4. GridView: Widget ini digunakan untuk menampilkan widget anak dalam pola grid

5. ListView: Widget ini adalah widget scrolling yang paling umum digunakan. Ia menampilkan widget anaknya satu per satu dalam arah scroll

## Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!
1. Elemen Nama Item menggunakan TextFormField dengan Data Type String. Ini digunakan untuk mengambil nama item yang akan ditambahkan. Validasi diterapkan untuk memastikan bahwa input tidak kosong.

2. Elemen Jumlah menggunakan TextFormField dengan Data Type int. Walaupun menggunakan TextFormField tapi bisa dikoversikan ke bentuk int karena jumlah biasanya merupakan angka. Validasi diterapkan untuk memastikan bahwa input tidak hanya angka, tetapi juga tidak boleh kosong.

3. Elemen Deskripsi menggunakan TextFormField dengan Data Type String. Ini digunakan untuk mengambil deskripsi item yang akan ditambahkan. Validasi ini diterapkan berfungsi untuk memastikan bahwa input tidak kosong.

4. TextFormField: Ini ideal untuk mengumpulkan input teks dengan kemungkinan validasi yang ada.


## Bagaimana penerapan clean architecture pada aplikasi Flutter?
Penerapan Clean Architecture pada aplikasi Flutter melibatkan pembagian aplikasi menjadi beberapa lapisan berdasarkan prinsip-prinsip Clean Architecture. 
  1. Data & Platform Layer: Lapisan data terletak di lapisan paling luar. Lapisan ini terdiri dari kode sumber data seperti konsumsi Rest API, akses ke database lokal, Firebase, atau sumber lain. Juga, pada lapisan ini, biasanya ada kode platform yang membangun UI (widget)

  2. Presentation Layer: Lapisan presentasi terdiri dari kode untuk mengakses data aplikasi dari repositori. Juga, ada kode untuk manajemen state seperti provider, BLoC, dan sebagainya.

  3. Domain Layer: Lapisan domain adalah yang terdalam dalam arsitektur bersih. Lapisan ini berisi kode untuk logika bisnis aplikasi seperti entitas dan use case

## Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)
1. Membuat new folder dengan nama widget lal buat file baru di dalamnya dnegan nama left_drawer.dart dan masukkan kode ini di dalamnya dan tambhakan pada bagian drawer header.
```dart
import 'package:flutter/material.dart';
import 'package:pacil_mart/screens/menu.dart';
import 'package:pacil_mart/screens/pacil_mart_form.dart';

class LeftDrawer extends StatelessWidget {
  const LeftDrawer({super.key});

  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            // TODO: Bagian drawer header
            decoration: BoxDecoration(
              color: Color.fromARGB(255, 0, 0, 0),
            ),
            child: Column(
              children: [
                Text(
                  'Pacil Mart',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
                Padding(padding: EdgeInsets.all(10)),
                Text(
                "Catat seluruh keperluan belanjamu di sini!",
                style: TextStyle(
                  fontSize: 15,  // Ukuran font 15
                  color: Colors.white,  // Warna teks putih
                  fontWeight: FontWeight.normal,  // Weight biasa (tidak bold)
                ),
                textAlign: TextAlign.center,  // Center alignment
              )
              ],
            ),
          ),
        ]
      ),
    );
  }
}

```
2. kemudian tambhakan routing ke page yang sudah diimport tadi 
```dart
  // TODO: Bagian routing
  ListTile(
    leading: const Icon(Icons.home_outlined),
    title: const Text('Halaman Utama'),
    // Bagian redirection ke MyHomePage
    onTap: () {
      Navigator.pushReplacement(
          context,
          MaterialPageRoute(
            builder: (context) => MyHomePage(),
          ));
    },
  ),
  ListTile(
    leading: const Icon(Icons.add_shopping_cart),
    title: const Text('Tambah Item'),
    // Bagian redirection ke ShopFormPage
    onTap: () {
        Navigator.pushReplacement(
          context,
          MaterialPageRoute(
            builder: (context) => ShopFormPage(),
          ));
    },
  ),
  ...
```
3. Tambahkan import darwer widget pada file menu.dart
```dart
import 'package:flutter/material.dart';
import 'package:pacil_mart/widgets/left_drawer.dart';
import 'package:pacil_mart/widgets/pacil_mart_card.dart';

class MyHomePage extends StatelessWidget {
  MyHomePage ({Key? key}) : super(key: key);
    final List<ShopItem> items = [
      ShopItem("Lihat Item", Icons.checklist, Color.fromARGB(255, 54, 54, 54)),
      ShopItem("Tambah Item", Icons.add_shopping_cart,Color.fromARGB(255, 95, 95, 95)),
      ShopItem("Logout", Icons.logout,Color.fromARGB(255, 150, 150, 150)),
  ];
  @override
    Widget build(BuildContext context) {
        return Scaffold(
            appBar: AppBar(
              title: const Text(
                'Pacil Mart',
                style: TextStyle(color: Colors.white),
              ),
              backgroundColor: const Color.fromARGB(255, 0, 0, 0),
              foregroundColor: Colors.white,
            ),
            drawer: const LeftDrawer(),
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
                        'Pacil Mart', // Text yang menandakan toko
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
        }
  
}
```
4. Setelah itu buat file baru dengan nama pacil_mart_form.dart dan isi filenye dengan kode ini
```dart
import 'package:flutter/material.dart';
import 'package:pacil_mart/widgets/left_drawer.dart';
import 'package:pacil_mart/models/pacil_mart_models.dart';

List<Item> itemList = [];

// TODO: Impor drawer yang sudah dibuat sebelumnya

class ShopFormPage extends StatefulWidget {
  const ShopFormPage({super.key});

  @override
  State<ShopFormPage> createState() => _ShopFormPageState();
}

class _ShopFormPageState extends State<ShopFormPage> {
  final _formKey = GlobalKey<FormState>();
  String _name = "";
  int _amount = 0;
  String _description = "";
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Center(
          child: Text(
            'Form Tambah Item',
          ),
        ),
        backgroundColor: const Color.fromARGB(255, 0, 0, 0),
        foregroundColor: Colors.white,
      ),
      // TODO: Tambahkan drawer yang sudah dibuat di sini
      drawer: const LeftDrawer(),
      body: Form(
        key: _formKey,
        child: SingleChildScrollView(
            child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: TextFormField(
                decoration: InputDecoration(
                  hintText: "Nama Produk",
                  labelText: "Nama Produk",
                  border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(5.0),
                  ),
                ),
                onChanged: (String? value) {
                  setState(() {
                    _name = value!;
                  });
                },
                validator: (String? value) {
                  if (value == null || value.isEmpty) {
                    return "Nama tidak boleh kosong!";
                  }
                  return null;
                },
              ),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: TextFormField(
                decoration: InputDecoration(
                  hintText: "Amount",
                  labelText: "Amount",
                  border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(5.0),
                  ),
                ),
                // TODO: Tambahkan variabel yang sesuai
                onChanged: (String? value) {
                  setState(() {
                    _amount = int.parse(value!);
                  });
                },
                validator: (String? value) {
                  if (value == null || value.isEmpty) {
                    return "Amount tidak boleh kosong!";
                  }
                  if (int.tryParse(value) == null) {
                    return "Amount harus berupa angka!";
                  }
                  return null;
                },
              ),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: TextFormField(
                decoration: InputDecoration(
                  hintText: "Deskripsi",
                  labelText: "Deskripsi",
                  border: OutlineInputBorder(
                    borderRadius: BorderRadius.circular(5.0),
                  ),
                ),
                onChanged: (String? value) {
                  setState(() {
                    // TODO: Tambahkan variabel yang sesuai
                    _description = value!;
                  });
                },
                validator: (String? value) {
                  if (value == null || value.isEmpty) {
                    return "Deskripsi tidak boleh kosong!";
                  }
                  return null;
                },
              ),
            ),
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: Align(
                alignment: Alignment.bottomCenter,
                child: Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: ElevatedButton(
                    style: ButtonStyle(
                      backgroundColor: MaterialStateProperty.all(
                          Color.fromARGB(255, 126, 125, 126)),
                    ),
                    onPressed: () {
                      if (_formKey.currentState!.validate()) {
                        Item newItem = Item(
                          name: _name,
                          amount: _amount,
                          description: _description,
                        );
                        itemList.add(newItem);
                        showDialog(
                          context: context,
                          builder: (context) {
                            return AlertDialog(
                              title: const Text('Item berhasil tersimpan'),
                              content: SingleChildScrollView(
                                child: Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: [
                                    // TODO: Munculkan value-value lainnya
                                    Text('Nama: $_name'),
                                    Text('Jumlah: $_amount'),
                                    Text('Deskripsi: $_description'),
                                  ],
                                ),
                              ),
                              actions: [
                                TextButton(
                                  child: const Text('OK'),
                                  onPressed: () {
                                    Navigator.pop(context);
                                  },
                                ),
                              ],
                            );
                          },
                        );
                      }
                      _formKey.currentState!.reset();
                    },
                    child: const Text(
                      "Save",
                      style: TextStyle(color: Colors.white),
                    ),
                  ),
                ),
              ),
            ),
          ],
        )),
      ),
    );
  }
}
```
5. Dan buat variabel baru dnegan nama _formkey. dan tambahkan _formkey ke dalam atribut key pada widget formnya dan isi widget formnya dengan varibel nama , amount, dan description 
```dart
...
class _ShopFormPageState extends State<ShopFormPage> {
  final _formKey = GlobalKey<FormState>();
  String _name = "";
  int _amount = 0;
  String _description = "";
...
```
```dart
...
body: Form(
    key: _formKey,
    child: SingleChildScrollView(),
),
...
```
6. Buat widget TextFormField yang dibungkus oleh padding dan merupakan children dari widget column. dan tambahkan crossAxisAlignment untuk atur alignment children, kemudian tambahkan child dari column untuk amount dan description . dan juga buat tombol yang dibungkus Padding dan Align untuk membuat pop-up kemudian tambahkan showDialog() di bagian onPressed(). Setelah itu, munculkan AlertDialog dan menambahkan fungsi reset form.
```dart
 child: Column(
      crossAxisAlignment: CrossAxisAlignment.start,
      children: [
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: TextFormField(
            decoration: InputDecoration(
              hintText: "Nama Item",
              labelText: "Nama Item",
              border: OutlineInputBorder(
                borderRadius: BorderRadius.circular(5.0),
              ),
            ),
            onChanged: (String? value) {
              setState(() {
                _name = value!;
              });
            },
            validator: (String? value) {
              if (value == null || value.isEmpty) {
                return "Nama tidak boleh kosong!";
              }
              return null;
            },
          ),
        ),
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: TextFormField(
            decoration: InputDecoration(
              hintText: "Amount",
              labelText: "Amount",
              border: OutlineInputBorder(
                borderRadius: BorderRadius.circular(5.0),
              ),
            ),
            // TODO: Tambahkan variabel yang sesuai
            onChanged: (String? value) {
              setState(() {
                _amount = int.parse(value!);
              });
            },
            validator: (String? value) {
              if (value == null || value.isEmpty) {
                return "Amount tidak boleh kosong!";
              }
              if (int.tryParse(value) == null) {
                return "Amount harus berupa angka!";
              }
              return null;
            },
          ),
        ),
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: TextFormField(
            decoration: InputDecoration(
              hintText: "Deskripsi",
              labelText: "Deskripsi",
              border: OutlineInputBorder(
                borderRadius: BorderRadius.circular(5.0),
              ),
            ),
            onChanged: (String? value) {
              setState(() {
                // TODO: Tambahkan variabel yang sesuai
                _description = value!;
              });
            },
            validator: (String? value) {
              if (value == null || value.isEmpty) {
                return "Deskripsi tidak boleh kosong!";
              }
              return null;
            },
          ),
        ),
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: Align(
            alignment: Alignment.bottomCenter,
            child: Padding(
              padding: const EdgeInsets.all(8.0),
              child: ElevatedButton(
                style: ButtonStyle(
                  backgroundColor: MaterialStateProperty.all(
                      Color.fromARGB(255, 126, 125, 126)),
                ),
                onPressed: () {
                  if (_formKey.currentState!.validate()) {
                    Item newItem = Item(
                      name: _name,
                      amount: _amount,
                      description: _description,
                    );
                    itemList.add(newItem);
                    showDialog(
                      context: context,
                      builder: (context) {
                        return AlertDialog(
                          title: const Text('Item berhasil tersimpan'),
                          content: SingleChildScrollView(
                            child: Column(
                              crossAxisAlignment: CrossAxisAlignment.start,
                              children: [
                                // TODO: Munculkan value-value lainnya
                                Text('Nama: $_name'),
                                Text('Jumlah: $_amount'),
                                Text('Deskripsi: $_description'),
                              ],
                            ),
                          ),
                          actions: [
                            TextButton(
                              child: const Text('OK'),
                              onPressed: () {
                                Navigator.pop(context);
                              },
                            ),
                          ],
                        );
                      },
                    );
                  }
                  _formKey.currentState!.reset();
                },
                child: const Text(
                  "Save",
                  style: TextStyle(color: Colors.white),
                ),
              ),
            ),
          ),
        ),
      ],
    ),
```
7. buat file baru dengan nama pacil_mart_card.dart pada folder widget dan oindahkan ShopItem yang ada di menu.dart ke dalamnya
```dart
import 'package:flutter/material.dart';
import 'package:pacil_mart/screens/pacil_mart_form.dart';
import 'package:pacil_mart/screens/pacil_mart_page.dart';

class ShopItem {
  final String name;
  final IconData icon;
  final Color color;

  ShopItem(this.name, this.icon, this.color);
}

class ShopCard extends StatelessWidget {
  final ShopItem item;

  const ShopCard(this.item, {super.key}); // Constructor

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      child: InkWell(
        // Area responsive terhadap sentuhan
        onTap: () {
          // Memunculkan SnackBar ketika diklik
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
          if (item.name == "Tambah Item") {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => ShopFormPage(),
                  ));
          // TODO: Gunakan Navigator.push untuk melakukan navigasi ke MaterialPageRoute yang mencakup ShopFormPage.
        }
        if (item.name == "Lihat Item") {
            Navigator.push(context,
              MaterialPageRoute(builder: (context) => ItemListPage(itemList: itemList)));
          }
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
8. tambhakan kode file pacil_mart_card.dart pada widget ShopItem agar bisa melakukan navigasi ke route lain
```dart
// Area responsive terhadap sentuhan
      onTap: () {
        // Memunculkan SnackBar ketika diklik
        ScaffoldMessenger.of(context)
          ..hideCurrentSnackBar()
          ..showSnackBar(SnackBar(
            content: Text("Kamu telah menekan tombol ${item.name}!")));
          if (item.name == "Tambah Item") {
          // TODO: Gunakan Navigator.push untuk melakukan navigasi ke MaterialPageRoute yang mencakup ShopFormPage.
            Navigator.push(context,
          MaterialPageRoute(builder: (context) => const ShopFormPage()));
        }
        
      },
```
9. buat file baru dengan nama pacil_mart_page.dart dan masukkan kode ini, yang berfungsi untuk memperlihatkan item yang sudah ditemabahkan
```dart
import 'package:flutter/material.dart';
import 'package:pacil_mart/models/pacil_mart_models.dart';
import 'package:pacil_mart/widgets/left_drawer.dart';

class ItemListPage extends StatelessWidget {
  final List<Item> itemList; 

  const ItemListPage({Key? key, required this.itemList})
      : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Daftar Item'),
        backgroundColor: Color.fromARGB(255, 0, 0, 0),
        foregroundColor: Colors.white,
      ),
      drawer: const LeftDrawer(),
      body: ListView.builder(
        itemCount: itemList.length,
        itemBuilder: (context, index) {
          return Card(
            elevation: 5,
            margin: const EdgeInsets.symmetric(vertical: 10, horizontal: 16),
            child: ListTile(
              title: Text(itemList[index].name),
              subtitle: Text('Jumlah: ${itemList[index].amount}'),
              onTap: () {
                // Menampilkan popup dengan informasi barang yang di-klik
                showDialog(
                  context: context,
                  builder: (context) {
                    return AlertDialog(
                      title: Text(itemList[index].name),
                      content: Column(
                        crossAxisAlignment: CrossAxisAlignment.start,
                        mainAxisSize: MainAxisSize.min,
                        children: [
                          Text('Jumlah: ${itemList[index].amount}'),
                          Text('Deskripsi: ${itemList[index].description}'),
                        ],
                      ),
                      actions: [
                        TextButton(
                          onPressed: () {
                            Navigator.pop(context);
                          },
                          child: const Text('Tutup'),
                        ),
                      ],
                    );
                  },
                );
              },
            ),
          );
        },
      ),
    );
  }
}
```
10. Pada folder lib buat folder baru dengan nama screen lalu pindahkan file menu.dart , pacil_mart_form.dart , dan pacil_mart_page.dart ke dalamnya.
11. buat folder models pada folder lib kemudian buat file dengan nama pacil_mart_models.dart isi dengan kode ini 
```dart
class Item {
  String name;
  int amount;
  String description;

  Item({
    required this.name,
    required this.amount,
    required this.description,
  });
}
```
12. 