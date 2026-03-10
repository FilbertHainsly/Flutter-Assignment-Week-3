# Flutter Widget Explanation 

## Deskripsi Project

Aplikasi Flutter sederhana yang menampilkan layout menggunakan **Column**, **Row**, **Container**, **Image**, dan **StatefulWidget** untuk membuat **counter interaktif**.
Aplikasi ini juga menggunakan **MediaQuery** untuk menyesuaikan ukuran komponen dengan ukuran layar perangkat.

---

# Struktur Widget

## 1. main()

```dart
void main() {
  runApp(const MyApp());
}
```

### Penjelasan

* `main()` adalah **entry point** dari aplikasi Flutter.
* `runApp()` digunakan untuk menjalankan widget utama aplikasi.
* `MyApp` menjadi **root widget** dari seluruh aplikasi.

---

# 2. MyApp (StatelessWidget)

```dart
class MyApp extends StatelessWidget
```

### Penjelasan

`MyApp` adalah widget utama yang tidak memiliki state (data yang berubah).

Widget yang digunakan di dalamnya:

### MaterialApp

```dart
MaterialApp(
  title: 'Flutter Demo',
)
```

Fungsi:

* Widget utama untuk aplikasi berbasis **Material Design**.
* Mengatur tema, routing, dan halaman utama aplikasi.

### ThemeData

```dart
theme: ThemeData(
  colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
  useMaterial3: true,
)
```

Fungsi:

* Mengatur **tema aplikasi** seperti warna dan style.
* `ColorScheme.fromSeed` membuat skema warna otomatis dari satu warna dasar.

### Home

```dart
home: const RowColumnPage(),
```

Fungsi:

* Menentukan **halaman pertama** yang ditampilkan saat aplikasi dibuka.

---

# 3. RowColumnPage (StatelessWidget)

Widget ini berfungsi sebagai **halaman utama aplikasi**.

```dart
class RowColumnPage extends StatelessWidget
```

Karena tidak ada data yang berubah, maka menggunakan **StatelessWidget**.

---

# 4. MediaQuery

```dart
MediaQueryData mediaQueryData = MediaQuery.of(context);
double screenWidth = mediaQueryData.size.width;
double screenHeight = mediaQueryData.size.height;
```

### Fungsi

Digunakan untuk mendapatkan **ukuran layar perangkat** seperti:

* Lebar layar
* Tinggi layar

Hal ini membantu membuat **layout yang responsif**.

---

# 5. Scaffold

```dart
return Scaffold(
```

### Fungsi

`Scaffold` adalah **struktur dasar halaman Material Design**.

Biasanya berisi:

* `AppBar`
* `Body`
* `FloatingActionButton`
* `Drawer`

---

# 6. AppBar

```dart
appBar: AppBar(
  title: Text('My First App')
)
```

### Fungsi

Menampilkan **header / bar bagian atas aplikasi**.

Properti yang digunakan:

| Properti          | Fungsi                       |
| ----------------- | ---------------------------- |
| `title`           | Judul aplikasi               |
| `backgroundColor` | Warna AppBar                 |
| `centerTitle`     | Memposisikan judul di tengah |

---

# 7. Column

```dart
body: Column(
```

### Fungsi

`Column` digunakan untuk menyusun widget **secara vertikal (atas ke bawah)**.

Properti:

| Properti             | Fungsi                     |
| -------------------- | -------------------------- |
| `mainAxisAlignment`  | Mengatur posisi vertikal   |
| `crossAxisAlignment` | Mengatur posisi horizontal |

---

# 8. Container

Contoh penggunaan:

```dart
Container(
  padding: EdgeInsets.all(20.0),
  margin: EdgeInsets.fromLTRB(20,5,20,10),
  color: Colors.lightBlue[100],
)
```

### Fungsi

`Container` adalah widget **serbaguna** untuk:

* Mengatur ukuran
* Memberi warna background
* Padding
* Margin
* Menampung widget lain

---

# 9. AspectRatio

```dart
AspectRatio(
  aspectRatio: 1.0
)
```

### Fungsi

Menjaga **perbandingan ukuran widget**.

Contoh:

```
aspectRatio: 1.0
```

artinya **lebar = tinggi (kotak)**.

---

# 10. Image.network

```dart
Image.network(
  'https://picsum.photos/200'
)
```

### Fungsi

Menampilkan gambar dari **URL internet**.

Properti:

| Properti | Fungsi                                   |
| -------- | ---------------------------------------- |
| `fit`    | Menentukan cara gambar mengisi container |
| `width`  | Lebar gambar                             |

---

# 11. Text

```dart
Text('What image is that')
```

### Fungsi

Menampilkan **teks** di layar.

Properti yang digunakan:

| Properti | Fungsi                           |
| -------- | -------------------------------- |
| `style`  | Mengatur ukuran font, warna, dll |

---

# 12. Row

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly
)
```

### Fungsi

`Row` digunakan untuk menyusun widget **secara horizontal (kiri ke kanan)**.

Properti:

| Properti             | Fungsi                    |
| -------------------- | ------------------------- |
| `mainAxisAlignment`  | Mengatur jarak horizontal |
| `crossAxisAlignment` | Mengatur posisi vertikal  |

---

# 13. Icon

```dart
Icon(Icons.food_bank)
```

### Fungsi

Menampilkan **ikon dari Material Icons**.

Contoh ikon yang digunakan:

* `Icons.food_bank`
* `Icons.landscape`
* `Icons.people`

---

# 14. CounterCard (StatefulWidget)

```dart
class CounterCard extends StatefulWidget
```

### Fungsi

Digunakan karena terdapat **data yang dapat berubah (counter)**.

State disimpan di:

```
_CounterCardState
```

---

# 15. State

```dart
int _counter = 0;
```

### Fungsi

Menyimpan **nilai counter** yang akan berubah ketika tombol ditekan.

---

# 16. setState()

```dart
setState(() {
  _counter++;
});
```

### Fungsi

Digunakan untuk:

* Mengubah data state
* Meminta Flutter **membangun ulang UI**

Jika `setState()` tidak digunakan, UI **tidak akan diperbarui**.

---

# 17. IconButton

```dart
IconButton(
  onPressed: _incrementCounter
)
```

### Fungsi

Tombol berbentuk **ikon**.

Properti:

| Properti    | Fungsi                              |
| ----------- | ----------------------------------- |
| `onPressed` | Fungsi yang dijalankan saat ditekan |
| `icon`      | Ikon yang ditampilkan               |

---

# Alur Aplikasi

1. Aplikasi dijalankan melalui `main()`.
2. `MyApp` memuat `MaterialApp`.
3. Halaman utama adalah `RowColumnPage`.
4. Layout dibuat menggunakan **Column dan Row**.
5. Gambar ditampilkan menggunakan **Image.network**.
6. Terdapat widget **CounterCard** dengan tombol.
7. Saat tombol ditekan:

   * `_incrementCounter()` dijalankan
   * `setState()` memperbarui `_counter`
   * UI menampilkan nilai counter terbaru.

---

# Widget yang Digunakan

| Widget         | Fungsi                           |
| -------------- | -------------------------------- |
| MaterialApp    | Root aplikasi                    |
| Scaffold       | Struktur halaman                 |
| AppBar         | Header aplikasi                  |
| Column         | Layout vertikal                  |
| Row            | Layout horizontal                |
| Container      | Layout box fleksibel             |
| Text           | Menampilkan teks                 |
| Image.network  | Menampilkan gambar dari internet |
| Icon           | Menampilkan ikon                 |
| IconButton     | Tombol dengan ikon               |
| AspectRatio    | Menjaga rasio ukuran             |
| StatefulWidget | Widget dengan state              |
| setState       | Memperbarui UI                   |

---

