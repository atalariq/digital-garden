# Panduan Belajar Python: Persiapan UAS & Competitive Programming

Sebagai seorang dosen dan pelatih _competitive programming_, saya sering melihat mahasiswa dan peserta pelatihan menghadapi tantangan yang sama: menjembatani pemahaman akademis fundamental dengan kecepatan dan efisiensi yang dibutuhkan dalam kompetisi. Panduan ini dirancang untuk dua tujuan tersebut. Bagian "Intisari Akademis" akan memperkuat konsep inti yang krusial untuk Ujian Akhir Semester (UAS), sementara bagian "Pythonic CP Tricks" akan membekali Anda dengan teknik-teknik canggih untuk menulis kode yang lebih cepat, ringkas, dan efektif—keterampilan yang sangat berharga di arena _competitive programming_ (CP).

Mari kita mulai perjalanan ini untuk mengubah Anda dari seorang praktisi yang mahir menjadi seorang ahli pemrograman Python berkinerja tinggi.

## 1. Input dan Output

### 1.1. Intisari Akademis (UAS Prep)

Menguasai operasi _Input/Output_ (I/O) adalah fondasi fundamental dalam pemrograman. Baik untuk tugas akademis sederhana yang memerlukan interaksi pengguna maupun untuk membaca _test case_ dari _platform_ CP, kemampuan program untuk menerima data dan menampilkan hasil adalah prasyarat mutlak. Tanpa I/O, sebuah program hanyalah kotak hitam yang tidak dapat berinteraksi dengan dunia luar.

**Konsep**

Di Python, operasi I/O dasar ditangani oleh dua fungsi utama:

- `input()`: Fungsi ini membaca satu baris data dari _standard input_ (biasanya keyboard Anda) dan mengembalikannya sebagai sebuah _string_.
- `print()`: Fungsi ini menulis data yang diberikan ke _standard output_ (biasanya layar terminal Anda).

**Syntax Dasar**

Berikut adalah contoh paling dasar yang menunjukkan bagaimana menerima input dari pengguna dan menampilkan sapaan:

```python
# Menerima input dari pengguna dan menyimpannya sebagai string
nama: str = input("Masukkan nama Anda: ")

# Menampilkan output ke konsol
print("Halo,", nama)
```

Meskipun `print()` sangat berguna, ada cara yang lebih canggih dan efisien untuk menyusun dan memformat output, yang akan menjadi kunci untuk menyajikan data dengan jelas dan ringkas.

### 1.2. Pythonic CP Tricks (Advanced)

Dalam konteks CP, di mana setiap detik berharga, teknik I/O yang efisien tidak hanya menghemat waktu pengetikan tetapi juga meningkatkan kejelasan kode. Kode yang ringkas lebih cepat dibaca, lebih mudah di-debug, dan memungkinkan Anda untuk fokus pada logika algoritma yang lebih kompleks. Menguasai I/O secara akademis adalah satu hal; menggunakannya di bawah tekanan waktu adalah hal lain.

**The "Pro" Way**

- **Gunakan f-string untuk Formatting**: _Formatted String Literals_ atau **f-string** (diperkenalkan di Python 3.6) adalah cara modern, cepat, dan sangat mudah dibaca untuk memformat string. Cukup awali string dengan huruf `f` dan sisipkan variabel atau ekspresi di dalam kurung kurawal `{}`.
- Hasil _benchmark_ menunjukkan f-string lebih cepat daripada metode lama seperti `%` atau `.format()`. f-string lebih cepat karena diurai menjadi serangkaian operasi penyambungan string yang sangat efisien di tingkat bytecode, menghindari _overhead_ pemanggilan fungsi seperti `.format()`.
- **Debugging Cepat dengan f-string**: Sejak Python 3.8, Anda dapat menggunakan trik f-string untuk men-debug variabel dengan cepat. Sintaks `f"{variable=}"` secara otomatis akan mencetak nama variabel beserta nilainya.
- **Mencetak Beberapa Item dalam Satu Baris**: Trik umum di CP untuk mencetak serangkaian angka yang dipisahkan spasi adalah dengan menggunakan operator `*` (_unpacking_).

**Common Pitfalls**

- `input()` **Selalu Mengembalikan String**: Kesalahan umum pemula adalah lupa bahwa `input()` mengembalikan _string_. Jika Anda mengharapkan angka, konversi tipe eksplisit seperti `int(input())` atau `float(input())` wajib dilakukan. Kegagalan melakukan ini akan menyebabkan `TypeError` saat operasi matematis atau logika yang salah.
- **I/O adalah Operasi yang Lambat**: Operasi I/O memiliki _overhead_ yang signifikan. Dalam soal CP dengan input yang sangat besar (jutaan baris), membaca baris per baris dengan `input()` di dalam _loop_ bisa menyebabkan _Time Limit Exceeded_ (TLE). Jika memungkinkan, pertimbangkan untuk membaca seluruh data sekaligus atau menggunakan metode I/O yang lebih cepat (seperti `sys.stdin.readline`), meskipun itu di luar cakupan panduan dasar ini.

Setelah data berhasil diterima melalui operasi input, langkah selanjutnya adalah memilih wadah yang tepat untuk menyimpan dan mengolahnya menggunakan tipe dan struktur data yang efisien.

### 1.3. Complexity Note

Kompleksitas waktu untuk operasi I/O dasar seperti `print()` dan `input()` biasanya tidak dianalisis menggunakan notasi Big-O dalam konteks algoritma. Namun, penting untuk diingat bahwa operasi ini memiliki **overhead dunia nyata yang signifikan** karena melibatkan interaksi dengan sistem operasi dan perangkat keras. Pada masalah dengan input atau output yang sangat besar, total waktu yang dihabiskan untuk I/O bisa menjadi _bottleneck_ performa yang menentukan apakah solusi Anda diterima atau ditolak (TLE).

## 2. Tipe Data dan Struktur Data Dasar

### 2.1. Intisari Akademis (UAS Prep)

Tipe data dan struktur data adalah blok bangunan esensial dalam pemrograman. Mereka menyediakan cara untuk merepresentasikan, mengorganisir, dan menyimpan informasi secara efisien. Pemilihan tipe dan struktur data yang tepat tidak hanya memengaruhi kebenaran program tetapi juga efisiensi dan performanya.

**Konsep**

Python menyediakan tipe data primitif dan struktur data _built-in_ yang kuat:

- **Tipe Primitif**:
    - `int`: Bilangan bulat (contoh: `10`, `-5`).
    - `float`: Bilangan desimal (contoh: `3.14`, `-0.001`).
    - `str`: Teks atau sekuens karakter (contoh: `"Halo Dunia"`).
    - `bool`: Nilai kebenaran, `True` atau `False`.
- **Struktur Data Dasar**:
    - `list`: Kumpulan item yang **terurut** dan **dapat diubah** (_mutable_). Duplikat diizinkan.
    - `tuple`: Kumpulan item yang **terurut** dan **tidak dapat diubah** (_immutable_).
    - `dict`: Kumpulan pasangan **kunci-nilai** (_key-value_) yang tidak terurut (pada Python < 3.7) dan dapat diubah. Kunci harus unik.
    - `set`: Kumpulan item yang **tidak terurut** dan tidak mengizinkan **elemen duplikat**.

**Syntax Dasar**

```python
# Primitif
angka_int: int = 42
angka_float: float = 3.14
teks: str = "Python"
kondisi: bool = True

# Struktur Data
my_list: list[int] = [1, 2, 3]
my_tuple: tuple[str, ...] = ("a", "b", "c")
my_dict: dict[str, int] = {"satu": 1, "dua": 2}
my_set: set[int] = {1, 2, 3, 3} # my_set akan menjadi {1, 2, 3}
```

Pemilihan struktur data yang tepat memiliki implikasi performa yang sangat besar, sebuah fakta yang menjadi sangat krusial dalam skenario _competitive programming_.

### 2.2. Pythonic CP Tricks (Advanced)

Di CP, memilih struktur data yang salah bisa langsung berakibat fatal (TLE). Memahami kompleksitas waktu O(n) dari pencarian `list` adalah teori akademis. Menggunakannya di CP pada data besar akan menyebabkan TLE. Inilah cara menerapkan teori tersebut untuk membuat pilihan yang benar: gunakan `set` untuk pencarian O(1) rata-rata.

**The "Pro" Way**

- **Membership Testing (**`in`**)**: Saat Anda perlu memeriksa keanggotaan, buang `list` dan gunakan `set`. Perbedaan kecepatannya adalah antara solusi yang diterima dan TLE. `set` diimplementasikan menggunakan _hash table_, yang membuat pencarian menjadi sangat cepat.

|                         |                                    |                                      |                                                                                             |
| ----------------------- | ---------------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------- |
| Operasi                 | `my_list = list(range(1_000_000))` | `my_set = set(my_list)`              | Alasan Performa                                                                             |
| `999_999 in collection` | Sangat Lambat (Kompleksitas O(n))  | **Sangat Cepat** (Kompleksitas O(1)) | `list` harus memindai setiap elemen; `set` menggunakan _hash table_ untuk pencarian instan. |

_**Coach's Corner:**_ Saya telah melihat lebih banyak TLE yang disebabkan oleh penggunaan `list` untuk uji keanggotaan daripada hampir semua kesalahan pemula lainnya. Jadikan `set` sebagai refleks Anda.

- **Operasi Antrian (Queue)**: Menggunakan `list` sebagai antrian dengan `list.pop(0)` sangat tidak efisien. Setiap kali elemen pertama dihapus, semua elemen lain harus digeser, menghasilkan operasi O(n). Solusi yang benar adalah menggunakan `collections.deque` (dibaca "deck"), yang dioptimalkan untuk penambahan dan penghapusan cepat dari kedua ujungnya (O(1)).
- **Tukar Variabel (Swapping)**: Python memungkinkan pertukaran nilai dua variabel secara elegan tanpa memerlukan variabel sementara.

**Common Pitfalls**

- Kesalahan terbesar adalah menggunakan `list` untuk pengujian keanggotaan (`x in my_list`) pada data besar. Ini akan menyebabkan pencarian linear yang sangat lambat. Selalu konversi ke `set` terlebih dahulu jika Anda perlu melakukan banyak pencarian.
- Menggunakan `list.pop(0)` atau `list.insert(0, ...)` di dalam _loop_ besar adalah anti-pola performa. Gunakan `collections.deque` untuk operasi antrian.

Dengan data yang tersimpan dalam struktur yang tepat, kita sekarang dapat beralih ke bagaimana memprosesnya menggunakan logika kontrol seperti percabangan dan perulangan.

### 2.3. Complexity Note

Memahami kompleksitas waktu dari operasi struktur data dasar sangat penting:

- Pencarian elemen (`in`) pada `list`: **O(n)**
- Pencarian elemen (`in`) pada `set` dan `dict` (berdasarkan _key_): **O(1)** rata-rata.
- Menambah/menghapus dari akhir `list` (`append`, `pop`): **O(1)** _amortized_.
- Menambah/menghapus dari awal `list` (`insert(0, ...)`): **O(n)**.
- Menambah/menghapus dari kedua ujung `collections.deque`: **O(1)**.

## 3. Percabangan dan Perulangan (Conditional & Loops)

### 3.1. Intisari Akademis (UAS Prep)

Struktur kontrol seperti percabangan (`if`) dan perulangan (`for`, `while`) adalah inti dari hampir semua algoritma. Mereka memungkinkan program untuk membuat keputusan berdasarkan kondisi dan melakukan tugas-tugas berulang secara efisien. Tanpa mereka, program hanya akan menjalankan serangkaian instruksi linear dari atas ke bawah.

**Konsep**

- **Percabangan (**`**if-elif-else**`**)**: Mengeksekusi blok kode yang berbeda berdasarkan apakah suatu kondisi bernilai `True` atau `False`. `elif` memungkinkan pengecekan beberapa kondisi secara berurutan.
- **Perulangan** `**for**`: Mengiterasi setiap elemen dalam sebuah sekuens (seperti `list`, `tuple`, atau `string`) atau objek _iterable_ lainnya.
- **Perulangan** `**while**`: Mengeksekusi blok kode secara berulang selama suatu kondisi tetap `True`.

**Syntax Dasar**

```python
# Contoh if-elif-else
nilai: int = 85
if nilai > 90:
    print("Sangat Baik")
elif nilai > 75:
    print("Baik")
else:
    print("Cukup")

# Contoh for loop
buah: list[str] = ["apel", "pisang", "ceri"]
for b in buah:
    print(b)

# Contoh while loop
counter: int = 0
while counter < 3:
    print(f"Hitungan: {counter}")
    counter += 1
```

Meskipun sintaks di atas jelas dan fundamental, Python menyediakan cara yang lebih ringkas dan ekspresif untuk menulis banyak pola perulangan umum, yang sangat berguna dalam praktik.

### 3.2. Pythonic CP Tricks (Advanced)

Dalam CP, kecepatan menulis kode yang benar sangat penting. Menulis _loop_ secara ringkas dan efisien tidak hanya menghemat waktu ketik tetapi juga dapat mengurangi potensi _bug_ dan sering kali memanfaatkan implementasi C yang sangat dioptimalkan dari fungsi _built-in_ Python.

**The "Pro" Way**

- **Operator Ternary**: Pengganti satu baris untuk blok `if-else` sederhana.
- **List Comprehensions**: Cara Pythonic yang sangat kuat dan cepat untuk membuat `list` dari sebuah _loop_.
    - _Loop sederhana_: `[i**2 for i in range(10)]`
    - _Loop dengan kondisi_ `_if_`: `[i**2 for i in range(10) if i % 2 == 0]`
    - _Loop dengan_ `_if-else_` _(ternary)_: `['genap' if i % 2 == 0 else 'ganjil' for i in range(10)]`
- **Walrus Operator (**`:=`**)**: Sejak Python 3.8, operator `:=` memungkinkan Anda untuk menetapkan nilai ke variabel sebagai bagian dari ekspresi. Ini sangat berguna untuk menyederhanakan _loop_ `while` yang memerlukan inisialisasi dan pengecekan dalam satu langkah, menghindari duplikasi kode.
- **Pembantu Perulangan (Looping Helpers)**:
    - `zip()`: Untuk iterasi paralel atas beberapa sekuens.
    - `enumerate()`: Untuk mendapatkan indeks dan nilai secara bersamaan.
- **Iterasi yang Dioptimalkan (**`**itertools**`**)**: Untuk _loop for_ bersarang yang tujuannya adalah menghasilkan produk Kartesian, `itertools.product` adalah alternatif yang jauh lebih cepat dan efisien memori. Ini adalah contoh pertama dari kekuatan modul `itertools`, yang akan kita lihat diimplementasikan dalam C untuk kecepatan maksimum.

**Common Pitfalls**

- **Memodifikasi List Saat Iterasi**: Mengubah `list` saat Anda mengulanginya dapat menyebabkan perilaku tak terduga (misalnya, melewatkan elemen). Jauh lebih aman untuk membuat `list` baru, misalnya dengan _list comprehension_.
- **Panggilan Fungsi Berulang dalam Loop**: Jika sebuah fungsi dipanggil berulang kali di dalam _loop_ dan hasilnya selalu sama, ini adalah pemborosan. Hitung hasilnya sekali di luar _loop_ dan simpan dalam variabel (_caching_).

Setelah memahami cara mengontrol alur program, mari kita fokus pada operasi spesifik yang sering kita lakukan di dalam _loop_, seperti manipulasi `list` dan `string`.

### 3.3. Complexity Note

- _List comprehension_ umumnya lebih cepat daripada _loop_ `for` eksplisit yang menggunakan `.append()`. Ini karena proses pembuatan _list_ dioptimalkan di tingkat interpreter C Python, dan menghindari _overhead_ dari pemanggilan metode `.append()` berulang kali di dalam loop Python, yang merupakan proses yang lebih lambat di tingkat interpreter.
- Fungsi dari modul `itertools` hampir selalu lebih cepat daripada ekuivalennya yang ditulis dalam Python murni. Mereka diimplementasikan dalam C dan dirancang untuk efisiensi memori dan kecepatan maksimum, menjadikannya pilihan utama untuk tugas-tugas kombinatorial atau iterasi kompleks.

## 4. List & String Manipulation

### 4.1. Intisari Akademis (UAS Prep)

`List` dan `string` adalah dua tipe data sekuensial yang paling umum digunakan dalam Python. Kemampuan untuk memanipulasi keduanya secara efisien—mengambil sebagian data, mengubah, menggabungkan, atau memecahnya—adalah keterampilan inti yang fundamental bagi setiap programmer Python.

**Konsep**

Operasi dasar pada `list` dan `string` sering kali serupa, tetapi ada satu perbedaan krusial:

- `list` bersifat **mutable** (dapat diubah). Operasi seperti `append` atau `sort` mengubah _list_ itu sendiri.
- `string` bersifat **immutable** (tidak dapat diubah). Operasi seperti `strip` atau `split` tidak mengubah _string_ asli, melainkan mengembalikan _string_ atau `list` baru.

Operasi umum meliputi:

- **Slicing**: Mengambil sebagian dari sekuens. `my_list[1:3]`
- **List Methods**: `append`, `insert`, `sort` (in-place).
- **String Methods**: `strip` (menghapus spasi di awal/akhir), `split` (memecah string menjadi list), `join` (menggabungkan list string menjadi satu string).

**Syntax Dasar**

```python
numbers: list[int] = [10, 20, 30, 40, 50]
# Slicing: mengambil elemen dari indeks 1 hingga 2
print(numbers[1:3]) # Output: [20, 30]

# Menambahkan elemen ke list
numbers.append(60)
print(numbers) # Output: [10, 20, 30, 40, 50, 60]

kalimat: str = "   halo dunia python   "
# Memecah string menjadi list
kata_kata: list[str] = kalimat.strip().split(' ')
print(kata_kata) # Output: ['halo', 'dunia', 'python']

# Menggabungkan list string menjadi satu string
kalimat_baru: str = "-".join(kata_kata)
print(kalimat_baru) # Output: "halo-dunia-python"
```

Selanjutnya, kita akan melihat bagaimana melakukan operasi-operasi ini dengan cara yang paling optimal untuk performa.

### 4.2. Pythonic CP Tricks (Advanced)

Teknik manipulasi yang buruk, seperti membangun sebuah _string_ panjang dengan menggabungkan potongan-potongan kecil secara berulang di dalam _loop_, adalah salah satu _bottleneck_ performa paling umum dan serius dalam Python. Memahami cara yang benar untuk melakukannya sangatlah penting.

**The "Pro" Way**

- **Pra-alokasi List**: Jika Anda tahu ukuran akhir dari sebuah `list`, menginisialisasinya dengan ukuran tersebut (`result = [0] * N`) dan kemudian mengisi nilainya berdasarkan indeks jauh lebih cepat daripada menggunakan `append` secara berulang. Ini menghindari proses realokasi memori dinamis yang mahal yang terjadi di latar belakang saat `list` tumbuh.
- **Membangun String Secara Efisien**: **Jangan pernah** menggunakan operator `+` untuk menggabungkan banyak string di dalam _loop_. Karena _string_ bersifat _immutable_, setiap operasi `+` membuat _string_ baru dan menyalin konten, yang sangat tidak efisien. Cara yang benar adalah menambahkan semua potongan _string_ ke dalam sebuah `list`, lalu memanggil `''.join(list_of_strings)` sekali di akhir.
- **Operasi** _**In-place**_ **vs. Salinan**: Pahami perbedaan antara operasi yang memodifikasi objek secara langsung (_in-place_) dan yang mengembalikan salinan baru. Misalnya, `list.sort()` mengurutkan _list_ secara _in-place_ dan mengembalikan `None`. Ini sangat efisien karena menghindari pembuatan salinan _list_ yang besar. Sebaliknya, `sorted(my_list)` mengembalikan _list_ baru yang terurut. Gunakan operasi _in-place_ jika Anda tidak memerlukan salinan asli untuk menghemat memori dan waktu.

**Common Pitfalls**

- Menggunakan `+` untuk menggabungkan string di dalam _loop_ besar adalah kesalahan performa nomor satu bagi banyak programmer Python pemula.
- Tidak menyadari biaya penyalinan saat melewatkan _list_ besar ke fungsi. Jika fungsi tidak perlu memodifikasi _list_ atau dapat melakukannya secara _in-place_, hindari pembuatan salinan yang tidak perlu.

Dari manipulasi data, sekarang kita beralih ke cara mengorganisir logika kita ke dalam blok-blok kode yang dapat digunakan kembali, yaitu fungsi.

### 4.3. Complexity Note

Penting untuk mengetahui kompleksitas dari operasi-operasi ini:

- `list.append()`: **O(1)** _amortized_.
- `str1 + str2`: **O(len(str1) + len(str2))**. Ini menjadi O(n^2) jika dilakukan berulang kali dalam _loop_ untuk membangun _string_ dengan panjang akhir n.
- `''.join(list_of_strings)`: **O(N)** di mana N adalah total panjang semua _string_ di dalam _list_.
- `list.sort()` (menggunakan Timsort): **O(n \log n)**.

## 5. Functions: Argument, Parameter, Return, Recursive

### 5.1. Intisari Akademis (UAS Prep)

Fungsi adalah unit kode yang dapat digunakan kembali yang membantu mengorganisir program menjadi bagian-bagian yang logis dan modular. Penggunaan fungsi meningkatkan keterbacaan, mengurangi duplikasi kode, dan menyederhanakan proses pemeliharaan dan _debugging_.

**Konsep**

- **Parameter vs. Argumen**:
    - **Parameter**: Variabel yang didefinisikan dalam deklarasi fungsi (misalnya, `def sapa(nama):`).
    - **Argumen**: Nilai aktual yang dilewatkan ke fungsi saat dipanggil (misalnya, `sapa("Andi")`).
- **Pernyataan** `**return**`: Mengirimkan nilai kembali dari fungsi ke pemanggil. Jika tidak ada `return`, fungsi secara implisit mengembalikan `None`.
- **Rekursi**: Sebuah konsep di mana sebuah fungsi memanggil dirinya sendiri untuk menyelesaikan masalah. Ini sering digunakan untuk masalah yang dapat dipecah menjadi sub-masalah yang lebih kecil dan identik.

**Syntax Dasar**

```python
# Fungsi sederhana dengan parameter dan return
def tambah(a: int, b: int) -> int:
    """Fungsi ini menjumlahkan dua angka."""
    return a + b

# Fungsi rekursif untuk menghitung faktorial
def faktorial(n: int) -> int:
    if n <= 1:
        return 1
    else:
        return n * faktorial(n - 1)

print(faktorial(5)) # Output: 120
```

Di Python, fungsi adalah _first-class objects_, yang berarti mereka dapat diperlakukan seperti variabel lain (dilewatkan sebagai argumen, dikembalikan dari fungsi lain). Ini membuka pintu untuk teknik-teknik pemrograman yang sangat kuat.

### 5.2. Pythonic CP Tricks (Advanced)

Dalam CP, fungsi sering kali digunakan secara lebih dinamis. Kemampuan untuk mendefinisikan fungsi kecil "on-the-fly" atau mengoptimalkan panggilan fungsi berulang dapat memberikan keunggulan kompetitif, baik dalam kecepatan penulisan kode maupun eksekusi.

**The "Pro" Way**

- **Fungsi Lambda**: Ini adalah cara untuk membuat fungsi anonim kecil dalam satu baris. Penggunaan paling umum adalah sebagai argumen `key` dalam fungsi pengurutan seperti `sorted()` atau `list.sort()` untuk mendefinisikan logika pengurutan kustom.
- **One-liner Rekursif (Peringatan!)**: Secara akademis, menarik untuk melihat bagaimana algoritma rekursif seperti Fibonacci atau bahkan Quicksort dapat ditulis dalam satu baris menggunakan `lambda`. Namun, ini **sangat tidak disarankan** untuk kode nyata karena mengorbankan keterbacaan secara drastis.
- **Fungsi Lokal (Nested Functions)**: Mendefinisikan fungsi di dalam fungsi lain dapat sedikit meningkatkan performa untuk logika yang dipanggil berulang kali di dalam _loop_. Python mencari variabel dalam lingkup lokal lebih cepat daripada lingkup global, sehingga mengurangi _overhead_ resolusi nama.

**Common Pitfalls**

- **Mencapai Batas Rekursi**: Python memiliki batas kedalaman rekursi (_recursion depth limit_) untuk mencegah _stack overflow_. Pada masalah CP yang memerlukan rekursi dalam, solusi ini bisa gagal. Solusi iteratif sering kali lebih aman dan lebih cepat.
- **Lambda yang Terlalu Rumit**: Jika `lambda` Anda menjadi sulit dibaca, itu adalah tanda bahwa Anda harus menggunakan fungsi `def` biasa. Mengikuti Zen of Python, "Readability counts."

Dari pengorganisasian kode ke dalam fungsi, mari kita lihat beberapa algoritma fundamental yang sering diimplementasikan di dalamnya, yaitu pengurutan dan pencarian.

### 5.3. Complexity Note

- Kompleksitas fungsi Fibonacci rekursif naif adalah eksponensial (**O(2^n)**). Ini menjadikannya contoh yang sangat buruk untuk implementasi praktis karena perhitungan yang berlebihan, tetapi merupakan contoh yang bagus untuk memahami konsep rekursi.
- Setiap pemanggilan fungsi memiliki _overhead_. Dalam _loop_ yang sangat ketat (_hot loops_), meminimalkan jumlah pemanggilan fungsi (misalnya, dengan melakukan _inlining_ logika secara manual atau menggunakan fungsi lokal) dapat memberikan sedikit peningkatan performa.

## 6. Sorting & Searching Algorithms

### 6.1. Intisari Akademis (UAS Prep)

Pengurutan (sorting) dan pencarian (searching) adalah dua masalah paling fundamental dalam ilmu komputer. Hampir setiap aplikasi perangkat lunak yang kompleks, mulai dari basis data hingga mesin pencari web, mengandalkan algoritma pengurutan dan pencarian yang efisien sebagai intinya.

**Konsep**

- **Pengurutan**: Python menyediakan dua mekanisme utama untuk mengurutkan data:
    - `list.sort()`: Metode ini mengurutkan `list` **secara** _**in-place**_, yang berarti `list` asli diubah. Metode ini tidak mengembalikan nilai (atau lebih tepatnya, mengembalikan `None`).
    - `sorted(iterable)`: Fungsi _built-in_ ini mengembalikan `**list**` **baru yang terurut** dari elemen-elemen dalam _iterable_ yang diberikan, tanpa mengubah sumber aslinya.
- **Pencarian Linear**: Ini adalah metode pencarian paling dasar. Algoritma ini memeriksa setiap elemen dalam sekuens satu per satu sampai elemen yang dicari ditemukan atau seluruh sekuens telah diperiksa.

**Syntax Dasar**

```python
angka: list[int] = [29, 99, 27, 41, 66]

# Mengurutkan menggunakan sorted() untuk mendapatkan list baru
angka_terurut: list[int] = sorted(angka)
print(f"Asli: {angka}")
print(f"Terurut: {angka_terurut}")

# Pencarian linear sederhana
target: int = 41
for elemen in angka:
    if elemen == target:
        print(f"Elemen {target} ditemukan!")
        break
```

Pencarian linear bekerja dengan baik untuk data kecil dan tidak terurut. Namun, untuk data yang sudah diurutkan, ada metode pencarian yang jauh lebih efisien.

### 6.2. Pythonic CP Tricks (Advanced)

Dalam CP, memanfaatkan struktur data yang terurut adalah kunci untuk membuka pintu ke algoritma yang sangat efisien. Pencarian biner adalah contoh utama, yang secara drastis mengurangi waktu pencarian pada data besar. Python menyediakan alat _built-in_ yang sangat dioptimalkan untuk tugas-tugas ini.

**The "Pro" Way**

- **Pencarian Biner dengan** `**bisect**`: Jangan pernah mengimplementasikan pencarian biner secara manual jika Anda bisa menghindarinya. Modul `bisect` adalah cara standar dan bebas _bug_ di Python untuk melakukan operasi pada _list_ yang terurut.
    - `bisect.bisect_left(a, x)`: Menemukan titik penyisipan untuk `x` di `a` sambil mempertahankan urutan. Ini secara efektif menemukan indeks pertama di mana elemen `x` bisa disisipkan.
    - `bisect.insort(a, x)`: Menyisipkan `x` ke dalam `a` secara efisien sambil menjaga _list_ tetap terurut. Ini jauh lebih cepat daripada `a.append(x)` diikuti oleh `a.sort()`.
- **Quicksort One-Liner (Hanya untuk Pengetahuan)**: Seperti yang disebutkan sebelumnya, Quicksort dapat ditulis sebagai _one-liner_ rekursif. Ini adalah contoh akademis yang menarik tentang bagaimana _list comprehension_ dan rekursi dapat digabungkan, tetapi sekali lagi, **jangan gunakan ini dalam kode praktis** karena tidak dapat dibaca dan tidak efisien untuk kasus terburuk.

**Common Pitfalls**

- Melakukan pencarian linear berulang kali pada data besar yang bisa diurutkan sekali di awal dan kemudian dicari menggunakan pencarian biner (`bisect`). Perbedaan performanya sangat besar.
- Mengurutkan ulang seluruh _list_ setiap kali satu elemen baru ditambahkan. Jika Anda perlu mempertahankan urutan, gunakan `bisect.insort` untuk penyisipan yang jauh lebih efisien.

Dari bekerja dengan data dalam memori, mari kita perluas cakupan kita ke data yang disimpan secara persisten di dalam file.

### 6.3. Complexity Note

Perbandingan kompleksitas waktu untuk algoritma pencarian dan pengurutan sangatlah penting:

- Pencarian Linear: **O(n)**
- Operasi modul `bisect` (Pencarian Biner): **O(\log n)**
- Penyisipan dengan `bisect.insort`: **O(n)**. Penting untuk dipahami bahwa meskipun `bisect` menemukan posisi penyisipan dalam waktu O(\log n), operasi penyisipan ke dalam `list` itu sendiri yang memakan waktu O(n) karena semua elemen setelahnya harus digeser. Jadi, `bisect.insort` bukanlah solusi ajaib untuk penyisipan yang sering.
- Pengurutan bawaan Python (`sort()` atau `sorted()`, menggunakan Timsort): **O(n \log n)**.

## 7. File Handling

### 7.1. Intisari Akademis (UAS Prep)

Penanganan file sangat penting untuk persistensi data. Ini memungkinkan program untuk membaca data konfigurasi, memproses _dataset_ besar yang tidak muat di memori, dan menyimpan hasil atau status program sehingga data tidak hilang saat program berhenti berjalan.

**Konsep**

- **Fungsi** `**open()**`: Ini adalah fungsi utama untuk membuka file. Ia memerlukan _path_ file dan mode:
    - `'r'`: _Read_ (baca) - mode default.
    - `'w'`: _Write_ (tulis) - menimpa file yang ada atau membuat file baru.
    - `'a'`: _Append_ (tambah) - menambahkan data ke akhir file.
- **Metode** `**close()**`: Setelah selesai bekerja dengan file, sangat penting untuk menutupnya menggunakan `file.close()`. Ini memastikan semua data yang di-buffer ditulis ke disk dan sumber daya sistem dilepaskan.
- **Pernyataan** `**with**` **(Context Manager)**: Cara modern dan paling aman untuk menangani file. Pernyataan `with` secara otomatis memastikan file ditutup dengan benar, bahkan jika terjadi _error_ di dalam blok `with`. Ini menghilangkan kebutuhan untuk memanggil `close()` secara manual.

**Syntax Dasar**

Contoh kanonik menggunakan `with open(...)` untuk menulis dan membaca file adalah praktik terbaik yang harus selalu diikuti.

```python
file_path: str = "data.txt"

# Menulis beberapa baris ke file
with open(file_path, 'w') as f:
    f.write("Baris pertama\n")
    f.write("Baris kedua\n")

# Membaca semua konten dari file
with open(file_path, 'r') as f:
    konten = f.read()
    print(konten)
```

Selain hanya membaca dan menulis, mengelola _path_ file secara andal dan lintas platform juga merupakan aspek penting dari penanganan file yang baik.

### 7.2. Pythonic CP Tricks (Advanced)

Meskipun I/O file jarang menjadi fokus utama dalam soal CP standar (yang biasanya menggunakan _standard I/O_), mengelola _path_ dan menulis kode yang bersih tetap merupakan praktik yang baik. Python modern menawarkan alat yang jauh lebih unggul daripada sekadar manipulasi _string_ untuk menangani _path_ file.

**The "Pro" Way**

- **Path Berorientasi Objek dengan** `pathlib`: Sejak Python 3.4, modul `pathlib` menyediakan cara modern dan berorientasi objek untuk bekerja dengan _path_ sistem file. Ini menyelesaikan banyak masalah portabilitas dan keterbacaan.
    - Gunakan operator `/` untuk menggabungkan _path_ secara intuitif dan aman di semua sistem operasi (Windows, macOS, Linux).
    - Gunakan `Path.expanduser()` untuk menangani _path_ yang dimulai dengan `~` (direktori _home_ pengguna).
    - Gunakan `Path.resolve()` untuk mendapatkan _path_ absolut kanonik dari sebuah _path_.
- **One-Liner untuk Menulis File**: Trik ini menggunakan fungsi `print` untuk menulis ke file. Meskipun ringkas, penggunaannya terbatas dan `with open(...)` tetap menjadi standar untuk kejelasan dan keamanan.

**Common Pitfalls**

- **Lupa Menutup File**: Kesalahan paling umum saat tidak menggunakan pernyataan `with` adalah lupa memanggil `file.close()`. Ini dapat menyebabkan kehilangan data (karena data mungkin masih di-buffer) atau kebocoran sumber daya sistem.
- **Menggabungkan Path dengan String**: Menggunakan `+` untuk menggabungkan _path_ file (`folder + '/' + file`) adalah praktik yang buruk karena tidak portabel antara Windows (yang menggunakan `\`) dan sistem berbasis Unix (yang menggunakan `/`). Selalu gunakan `pathlib` atau `os.path.join`.

Dari operasi I/O yang berhasil, mari kita beralih ke cara menangani situasi ketika operasi (termasuk I/O) gagal, yaitu melalui penanganan _error_.

### 7.3. Complexity Note

Operasi file didominasi oleh kecepatan I/O disk, bukan oleh kompleksitas algoritmik CPU. Oleh karena itu, notasi Big-O biasanya tidak relevan di sini. Tujuan utama dalam optimasi file adalah meminimalkan jumlah operasi baca/tulis ke disk, karena ini adalah operasi yang jauh lebih lambat dibandingkan operasi dalam memori.

## 8. Error Handling (Exceptions)

### 8.1. Intisari Akademis (UAS Prep)

Penanganan eksepsi (_exceptions_) adalah mekanisme Python untuk merespons kesalahan yang terjadi saat program berjalan (_runtime errors_) secara terstruktur. Alih-alih membuat program _crash_, eksepsi memungkinkan Anda untuk "menangkap" kesalahan dan menjalankan kode pemulihan yang elegan.

**Konsep**

- **Blok** `try...except`: Kode yang berpotensi menimbulkan _error_ ditempatkan di dalam blok `try`. Jika _error_ terjadi, eksekusi blok `try` berhenti dan Python mencari blok `except` yang cocok.
- **Menangkap Eksepsi Spesifik**: Praktik terbaik adalah menangkap tipe _error_ yang spesifik (misalnya, `ValueError`, `KeyError`, `FileNotFoundError`) daripada menangkap semua _error_ sekaligus. Ini memungkinkan Anda menangani setiap jenis kesalahan secara berbeda dan menghindari penyembunyian _bug_ yang tidak terduga.
- **Blok** `finally`: Blok `finally` berisi kode yang **harus selalu dieksekusi**, terlepas dari apakah _error_ terjadi atau tidak. Ini sangat berguna untuk membersihkan sumber daya, seperti menutup koneksi jaringan atau file.

**Syntax Dasar**

```python
# Menangani input non-numerik
try:
    angka = int(input("Masukkan sebuah angka: "))
except ValueError:
    print("Itu bukan angka yang valid!")

# Menunjukkan eksekusi blok finally
try:
    f = open("file_yang_mungkin_tidak_ada.txt", 'r')
    # ... proses file
except FileNotFoundError:
    print("File tidak ditemukan.")
finally:
    # Kode ini akan selalu berjalan
    print("Eksekusi blok try-except selesai.")
```

Meskipun penanganan eksepsi memberikan keamanan dan ketahanan, ada _trade-off_ performa yang harus dipertimbangkan, terutama dalam kode yang sangat sensitif terhadap kecepatan.

### 8.2. Pythonic CP Tricks (Advanced)

Dalam kode yang kritis terhadap performa seperti di CP, bagaimana dan kapan Anda menangani _error_ bisa menjadi keputusan optimisasi yang penting. Menggunakan eksepsi untuk alur kontrol normal adalah sebuah anti-pola yang harus dihindari.

**The "Pro" Way**

- **Pemeriksaan Proaktif (LBYL vs. EAFP)**: Ada dua idiom penanganan error di Python: "Look Before You Leap" (LBYL) dan "Easier to Ask for Forgiveness than Permission" (EAFP).
    - **LBYL (misalnya** `dict.get()`**)**: `if key in dict: ...` atau `dict.get(key, default)`. Ini cepat jika kunci _sering tidak ada_, karena menghindari _overhead_ eksepsi yang mahal.
    - **EAFP (misalnya** `try...except`**)**: `try: ... dict[key] ... except KeyError: ...`. Ini lebih Pythonic dan bisa lebih cepat jika kunci _hampir selalu ada_, karena biaya `try` rendah.
- Dalam CP, untuk _loop_ yang sangat ketat (_hot loops_), pendekatan LBYL dengan `dict.get()` sering kali merupakan taruhan yang lebih aman untuk menghindari penurunan performa akibat eksepsi.
- **Gunakan** `breakpoint()` **untuk Debugging**: Sejak Python 3.7, `breakpoint()` adalah cara modern untuk masuk ke mode _debugger_ interaktif (PDB). Cukup letakkan `breakpoint()` di kode Anda, dan eksekusi akan berhenti di sana, memungkinkan Anda memeriksa variabel dan mengeksekusi kode baris per baris. Ini jauh lebih kuat daripada menggunakan `print` secara sporadis.

**Common Pitfalls**

- **Menggunakan Eksepsi untuk Alur Kontrol**: **Jangan pernah** menggunakan blok `try...except` untuk mengontrol alur program normal di dalam _loop_ yang sering dieksekusi (_hot loops_). _Overhead_ dari menaikkan dan menangkap eksepsi jauh lebih besar daripada pengecekan `if` sederhana.
- **Menangkap** `**except**` **Kosong**: Menulis `except:` tanpa menentukan tipe _error_ adalah praktik yang sangat buruk. Ini akan menangkap _semua_ eksepsi, termasuk yang tidak Anda harapkan seperti `SystemExit` atau `KeyboardInterrupt` (dari Ctrl+C), yang dapat membuat program sulit dihentikan dan menyembunyikan _bug_ yang sebenarnya.

### 8.3. Complexity Note

Operasi `raise` dan blok `try...except` memiliki **overhead performa yang signifikan** dibandingkan dengan pernyataan kondisional seperti `if-else`. Mekanisme eksepsi melibatkan pembongkaran _stack_ dan peralihan konteks, yang merupakan operasi yang mahal bagi interpreter. Oleh karena itu, eksepsi harus dicadangkan untuk kasus-kasus yang benar-benar **luar biasa (exceptional)**, bukan untuk kondisi yang dapat diprediksi dan sering terjadi.
