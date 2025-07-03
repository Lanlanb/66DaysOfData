# Day 7 — Pengantar Numpy

Tags: Journey
author: Bulan Nurlaela
Last Update: July 3, 2025 2:58 PM
Cats: Data, Manajemen

# 📌 Topik Hari Ini

### Konsep Dasar: kenapa belajar Numpy?

Sebelumnya kita sudah belajar mengenai `list` di Python, kan?

Contoh:

```python
data = [1, 2, 3, 4]
```

Itu adalah *list biasa* yang akan mengembalikan variabel data (tempat penyimpanan) menjadi `[1, 2, 3, 4]`.

Tapi kalau mau:

- menjumlahkan semua isi `list`
- mengalikan seluruh isinya dengan angka
- bekerja dengan data dalam jumlah besar

maka `list` mulai terasa lelet dan tidak fleksibel untuk digunakan.

```python
# List Python (lambat untuk operasi besar)
list_a = [1, 2, 3]
list_b = [4, 5, 6]
hasil_list = [a + b for a, b in zip(list_a, list_b)]  # Perlahan

# NumPy (cepat!)
arr_a = np.array([1, 2, 3])
arr_b = np.array([4, 5, 6])
hasil_numpy = arr_a + arr_b  # Cepat dan mudah
```

Maka, di sinilah NumPy muncul.

- **Apa itu Numpy dan Array?**
    - **NumPy** (singkatan dari *Numerical Python*) adalah pustaka (library) Python yang digunakan untuk:
        - Membuat array (struktur data seperti `list` tapi lebih cepat dan efisien untuk angka)
        - Melakukan perhitungan matematika, statistik, dan operasi vektor/matriks
        - Digunakan sebagai dasar untuk pustaka data lainnya seperti *Pandas*, *Scikit-learn*, *TensorFlow*
    
    NumPy sangat berguna dalam pengolahan data dan machine learning karena **kecepatannya dalam bekerja dengan angka dalam jumlah besar**.
    

- **`Array`** sendiri adalah **wadah seperti `list`**, **tapi lebih** teratur, lebih cepat, dan khusus untuk angka dan notasi ilmiah dalam python.

**Analoginya**, bayangkan saja `array` itu seperti kotak telur:

> Kalau `list` itu seperti tas kresek (acak isinya: ada telur, roti, minuman), maka `array` seperti karton isi telur 6 biji yang teratur, satu jenis, gampang ditumpuk dan diproses cepat.
> 

- **Instalasi Numpy**
    
    Jika memakai Google Colab, NumPy sudah tersedia otomatis. Tapi kalau offline, dapat melakukan instalasi pada terminal atau cmd:
    
    ```bash
    pip install numpy
    ```
    
    pip adalah alat untuk menginstal pustaka python, kemudian import library-nya untuk mulai menggunakan:
    
    ```python
    import numpy as np
    ```
    

### Penggunaan Numpy

Membuat array dapat dilakukan dengan beberapa cara, sepert:

```
# dari list python
arr1 = np.array([1, 2, 3])          # 1D array (vektor)
arr2 = np.array([[1, 2], [3, 4]])    # 2D array (matriks)

# dari fungsi bawaan numpy
arr_zeros = np.zeros((3, 3))    # Matriks 3x3 isi 0
arr_ones = np.ones((2, 2))      # Matriks 2x2 isi 1
arr_range = np.arange(0, 10, 2) # Array [0, 2, 4, 6, 8]
```

- **Array 1 Dimensi** itu Seperti Barisan
    
    Untuk pembuktian efektivitas Numpy di bandingin menggunakan list biasa, perhatikan syntax berikut:
    
    ```python
    angka = np.array([10, 20, 30])
    print(angka)
    ```
    
    Output: `[10 20 30]`
    
    Ini adalah array 1 dimensi → seperti satu baris angka. Bisa dibayangkan seperti: 10 → 20 → 30
    
    Kenapa array ini harus digunakan? Tentu saja karena dapat langsung melakukan operasi matematika terhadap array tersebut. Contohnya saja `angka + 5` akan menghasilkan `[15 25 35]`. Hal ini tentunya lebih efisien dibandingkan menggunakan perulangan `for` pada list biasa. 
    
    ```python
    # gambaran kalau menggunakan list python biasa
    data = [10, 20, 30]
    for i in range(len(data)):
        data[i] += 5
    print(data) # output: [15, 25, 35]
    
    # atau membuat sebuah list kosong untuk menampung hasilnya
    hasil = []
    for angka in data:    hasil.append(angka + 5)
    print(hasil) # output: [15, 25, 35]
    ```
    
    Tapi array cukup satu baris dan semua elemen langsung ditambahkan 5!
    

- **2 Dimensi** itu Seperti Tabel atau Matriks— memiliki bentuk,  yakni seperti baris dan kolom

```python
data = np.array([[1, 2], [3, 4]])
print(data)
```

Output:

```python
[[1 2]
[3 4]]
```

Analoginya:

> Bayangkan seperti tabel atau Excel, 2 baris × 2 kolom. Inilah yang disebut dengan array 2 dimensi.
> 

Kemudian, dari array 2 dimensi ini sifat-sifat array akan menjadi lebih jelas perbedaannya dibandingkan dengan menggunakan array 1 dimensi sebagai model pembelajaran. Sifat-sifat ini dikenal juga sebagai **properties** array numpy.

- Sifat/atribut suatu array
    
    
    | Sifat (Atribut) | Penjelasan Singkat |
    | --- | --- |
    | `.shape` | Bentuk (baris, kolom) |
    | `.ndim` | Jumlah dimensi array (1D, 2D, 3D, dst.) |
    | `.size` | Jumlah total elemen |
    | `.dtype` | Tipe data elemen |
    | `.itemsize` | Ukuran **satu elemen** (dalam byte) |
    | `.nbytes` | Total memori array (`size` × `itemsize`) |
    | `.T` | Transpose (baris ↔ kolom) |
    
    Untuk lebih jelasnya, saya akan memperlihatkannya secara langsung.
    
    ```python
    arr.array([[1, 2, 3], [4, 5, 6]])
    
    print("1. shape      :", arr.shape)
    print("2. ndim       :", arr.ndim)
    print("3. size       :", arr.size)
    print("4. dtype      :", arr.dtype)
    print("5. itemsize   :", arr.itemsize)
    print("6. nbytes     :", arr.nbytes)
    print("7. transpose  :\n", arr.T)
    ```
    
    jika syntax di atas dijalankan, hasilnya akan seperti ini:
    
    ```python
    1. shape      : (2, 3)
    2. ndim       : 2
    3. size       : 6
    4. dtype      : int64
    5. itemsize   : 8
    6. nbytes     : 48
    7. transpose  :
     [[1 4]
     [2 5]
     [3 6]]
    ```
    
    `arr` sendiri akan menghasilkan array:
    
    ```python
    [[1 2 3]
    [4 5 6]]
    ```
    
    Yang jika dijabarkan akan menjadi seperti ini:
    
    - `shape` : Array ini berbentuk tabel 2x3 → 2 baris dan 3 kolom.
    - `ndim` : Array ini punya **2 dimensi →** baris dan kolom. Kalau hanya baris saja (array 1D), hasilnya 1.
    - `size` : Ada **6 angka/elemen total** di dalam array itu → 2 baris × 3 kolom = 6
    - `dtype` : Semua isi array ini bertipe **integer 64-bit.** Bisa juga `float64` kalau isinya ada angka desimal.
    - `itemsize` : Setiap angka di dalam array ini butuh **8 byte** memori.
        
        Biasanya:
        
        - `int64` dan `float64` → 8 byte
        - `int32` → 4 byte
    - `nbytes` : Total memori yang dipakai array → 6 elemen × 8 byte = **48 byte**
    - `transpose` : Menggunakan baris sebagai kolom dan/atau sebaliknya.

### Operasi pada Numpy Array

- **Arithmetic Operations** (paling sering dipakai)
    
    Adalah operasi matematika dasar yang dilakukan per-element (element wise) pada array. 
    
    Jenis-jenisnya:
    
    | Operator | Keterangan | Function | Contoh Input | Output |
    | --- | --- | --- | --- | --- |
    | `+` | Pertambahan | `np.add()` | `[1,2] + [3,4]` | `[4,6]` |
    | `-` | Pengurangan | `np.subtract()` | `[5,3] - [1,2]` | `[4,1]` |
    | `*` | Perkalian | `np.multiply()` | `[2,3] * [4,5]` | `[8,15]` |
    | `/` | Pembagian | `np.divide()` | `[10,8] / [2,4]` | `[5,2]` |
    | `**` | Pangkat | `np.power()` | `[3,2] ** [2,3]` | `[9,8]` |
    | `%` | Modulus (Sisa hasil bagi) | `np.mod()` | `[7,10] % [3,4]` | `[1,2]` |
    
    Sekilas, terlihat mirip dengan operasi aritmatika di day 1. Namun perbedaannya bukan pada simbol/syntax-nya, melainkan pada skala eksekusi dan tipe data yang diolah, seperti yang telah dijelaskan sebelumnya (harus menggunakan loop).
    
    Terlihat membingungkan? Saya akan mencobanya secara langsung. Pertama-tama saya membagi array sebelumnya menjadi 2 variabel atau array yang berbeda.
    
    ```python
    a = np.array([1, 2, 3])
    b = np.array([4, 5, 6])
    ```
    

Dua array tersebut, yakni `a` dan `b` akan menghasilkan array 1 dimensi yang masing-masing memiliki bentuk 1 baris dan 3 kolom. Dari keduanya, saya menerapkan operasi aritmatika.

```python
# penerapan operasi aritmatika pada array
print(a + b) # addition
print(a - b) # subtraction
print(a * b) # multiplication
print(a / b) # distribution
print(a ** b) # exponential
print(a % b) # modulus
```

Yang menghasilkan output:

```python
[5 7 9]
[-3 -3 -3]
[ 4 10 18]
[0.25 0.4  0.5 ]
[  1  32 729]
[1 2 3]
```

Dari `a` dan `b` juga dapat dilakukan dengan menggunakan fungsi bawaan Numpy. Seperti `np.add()` atau sejenisnya:

```python
# menggunakan fungsi bawaan Numpy untuk arithmetic
print(np.add(a, b)) # addition
print(np.subtract(a, b)) # subtraction
print(np.multiply(a, b)) # multiplication
print(np.divide(a, b)) # distribution
print(np.power(a, b)) # exponential
print(np.mod(a, b)) # modulus
```

Dan hasilnya akan tetap sama:

```python
[5 7 9]
[-3 -3 -3]
[ 4 10 18]
[0.25 0.4  0.5 ]
[  1  32 729]
[1 2 3]
```

Selain itu, pada penerapan operasi aritmatika dalam Numpy juga terdapat konsep atau fitur yang menawarkan perhitungan matematika yang lebih mudah. Sebut saja seperti broadcasting dan sebagainya.

- **Broadcasting**: operasi aritmatika dengan **skalar** (angka tunggal)
    
    Adalah suatu cara dalam Numpy yang memungkinkan kita untuk melakukan operasi aritmatika pada array dengan bentuk yang berbeda tanpa harus membentuknya ulang (menghindari pemakaian loop atau memperbesar ukuran array secara manual).
    
    **Analoginya seperti ini:**
    
    > Bayangkan Anda punya **1 kotak** pizza (skalar) dan **3 teman** (array). Bagaimana membagi pizza secara adil? Inilah konsep broadcasting!
    > 
    
    Dengan menggunakan pengandaian seperti itu, kita dapat memecahnya menjadi kotak-kotak kecil:
    
    - **Skalar** = 1 kotak pizza
    - **Array** = [Teman1, Teman2, Teman3]
    - **Operasi** = "Berikan 1 potong pizza ke setiap teman"
    
    Di Numpy:
    
    ```python
    # analogi broadcasting
    jumlah_pizza = 1  # skalar
    teman = a  # 3 teman yang juga memiliki pizza → array
    
    total_pizza = teman + jumlah_pizza  # operasi
    print(total_pizza)  # Output: [2 3 4] (masing-masing dapat 1)
    ```
    
    Bagaimana? Cara kerja broadcasting adalah dengan menyesuaikan array yang lebih kecil agar sesuai dengan bentuk array yang lebih besar dengan mereplikasi/menyebarkan (broadcast) nilainya (skalar) di sepanjang dimensi (array) yang diperlukan. 
    
    Dalam hal ini:
    
    - Nilai skalar `1` pizza disiarkan agar sesuai dengan array `teman` yang memiiki 1 dimensi.
    - Hasilnya, elemen baru dibuat skalar ditambahkan ke setiap elemen `teman` yang menciptakan elemen baru di mana setiap `teman` di tambahkan sebesar `1` nilai.
    
    Pada titik ini, konsep dan cara pengerjaannya hampir terlihat mirip dengan perkalian pada matriks. Namun keduanya pada dasarnya berbeda. Sehingga ada aturan tertentu dalam penggunaan broadcasting:
    
    - Dimensi array harus compatible
        - Jika dua array memiliki **jumlah dimensi berbeda**, array dengan dimensi lebih kecil akan **ditambahkan dimensi "1" di depannya** sampai dimensinya sama.
            
            Contoh:
            
            ```python
            A = np.array([1, 2, 3])       # Shape (3,)
            B = np.array([[10], [20]])    # Shape (2, 1)
            
            # A dianggap sebagai shape (1, 3) untuk broadcasting
            print(A + B)
            
            ```
            
            Output:
            
            ```
            [[11 12 13]
             [21 22 23]]
            
            ```
            
    - Ukuran setiap **dimensi** harus sama atau salah satunya = **1**
        
        Contoh Valid:
        
        ```python
        A = np.array([[1], [2], [3]])  # Shape (3, 1)  
        B = np.array([10, 20, 30])     # Shape (3,) dalam broadcasting dianggap seperti (1, 3) saat dioperasikan dalam array 2D
        
        # A (3,1) + B (,3) → B dianggap (1,3) → Hasil (3,3)
        print(A + B)
        ```
        
        Output:
        
        ```
        [[11 21 31]
         [12 22 32]
         [13 23 33]]
        
        ```
        
        `(3,)` adalah bentuk (shape) dari **array 1D** (vekto) dengan 3 elemen. Di mana dalam NumPy, bentuk array selalu ditulis dengan dimensi yang ada dan  sengaja dibuat sebagai **array 1D** (`(3,)`) untuk menunjukkan bagaimana NumPy melakukan broadcasting antara array 1D dan 2D. Walaupun jika ingin menyatakan ke daam 2D, dengan 1 baris dan 3 kolom, `(1, 3)`, prosesnya tetap mirip,
        
        **Q: Mengapa NumPy membiarkan `(3,)` di-broadcast dengan `(3, 1)` (menjadi bentuk 2D)?**
        
        A: Untuk memudahkan operasi antara vektor dan matriks tanpa harus selalu mengubah bentuk array.
        
        Visualisasi proses:
        
        ```
        A asli:     B asli:
        [[1]        [10, 20, 30]
         [2]
         [3]]
         
        Setelah broadcasting:
        A:          B:
        [[1,1,1]    [[10,20,30]
         [2,2,2]     [10,20,30]
         [3,3,3]]    [10,20,30]]
        ```
        
        Aturan yang Terjadi:
        
        - **Expand Dimensions**: B (3,) → (1,3)
        - **Broadcast Rules**:
            - Axis 0: 3 vs 1 → expand B ke 3
            - Axis 1: 1 vs 3 → expand A ke 3
        - **Result Shape**: (3,3)
        
        Contoh Error:
        
        ```python
        A = np.array([1, 2, 3])  # Shape (1, 3)
        B = np.array([4, 5])     # Shape (1, 2)
        
        # A + B → Error: shapes (3,) and (2,) mismatch
        
        ```
        
    - Selalu di mulai dari kanan → kiri
        
        Contohnya, kita akan membuat 2 array dengan dimensi yang berbeda:
        
        ```python
        A = np.ones((2, 3, 4))  # Shape (2, 3, 4)
        B = np.ones((3, 1))     # Shape (3, 1)
        ```
        
        Kedua array tersebut dibuat menggunakan `numpy.ones()` yang fungsinya mengembalikan array baru dengan angka 1 yang memiliki bentuk dan tipe tertentu.
        
        **Syntax :** `numpy.ones(shape, dtype = None, order = 'C')`.
        
        Dengan parameternya:
        
        - `shape`(int atau sequence dari int). Pada contoh ini, array yang diminta berdimensi 3, sehingga kode yang diambil adalah `(depth, rows, columns)`.
        - `dtype` yang ingin dinyatakan
        - `order` yang menyatakan urutan
        
        Ngomong-ngomong, kedua array akan membentuk seperti ini:
        
        ```
        A:
        [[[1. 1. 1. 1.]
          [1. 1. 1. 1.]
          [1. 1. 1. 1.]]
          
         [[1. 1. 1. 1.]
          [1. 1. 1. 1.]
          [1. 1. 1. 1.]]]
        
        B:
        [[1.]
         [1.]
         [1.]]
        ```
        
        Sehingga ketika perintah `print((A + B).shape)` dijalankan, hasilnya akan mencetak `(2, 3, 4)`.
        
        **Dengan analog**i:
        
        A adalah kotak besar berisi 2 laci, yang masing-masing memiliki 3 rak dan tiap raknya mempunyai 4 kotak kecil. Sedangkan B adalah stiker dengan 3 baris dan 1 kolom.
        
        Jika dirincikan, **prosesnya** kurang lebih menjadi seperti ini:
        
        - Langkah 1: Menyamakan ukuran kemasan
            - Kotak A punya 3 dimensi (2 laci, 3 rak, 4 kotak)
            - Stiker B hanya 2 dimensi (3 baris 1 kolom)
            - Kita tambahkan 1 dimensi kosong di depan B, sehingga menjadi (1, 3, 1) → yakni 1 laci.
        - Langkah 2: Proses penempatan stiker
            - Untuk dimensi rak (3 vs 3):
                - Ukuran sama (3 rak), jadi stiker pas tepat
                - Tidak perlu penyesuaian
            - Untuk dimensi laci (2 vs 1):
                - Stiker hanya punya 1 laci, tapi kotak punya 2
                - Solusi: **duplikasi** stiker untuk laci kedua
                - Hasilnya stiker sekarang berukuran (2, 3, 1) dari (1, 3, 1).
            - Untuk dimensi kotak kecil (4 vs 1):
                - Stiker hanya cover 1 kotak, tapi ada 4 kotak
                - Solusi: **perlebar** stiker ke 4 kotak
                - Hasil: stiker sekarang (2, 3, 4)
            
        
        Dan inilah A dan B setelah di broadcast:
        
        ```
        [
          [
            [1,1,1,1],  # Dimensi 0 ke-0
            [1,1,1,1],
            [1,1,1,1]
          ],
          [
            [1,1,1,1],  # Dimensi 0 ke-1
            [1,1,1,1],
            [1,1,1,1]
          ]
        ]
        ```
        
        Atau bisa dicek menggunakan `numpy.broadcast_arrays()` untuk melihat hasil dari broadcasting. Dan ini adalah hasil dari A + B:
        
        ```python
        array([[[2., 2., 2., 2.],
                [2., 2., 2., 2.],
                [2., 2., 2., 2.]],
        
               [[2., 2., 2., 2.],
                [2., 2., 2., 2.],
                [2., 2., 2., 2.]]])
        ```
        
    - Hasil Operasi Memiliki Shape Maksimal dari Setiap Dimensi
        - Shape output adalah **keluasan maksimal** setiap dimensi dari input.
        
        Contoh:
        
        ```python
        A = np.ones((5, 1, 3))  # Shape (5, 1, 3)
        B = np.ones((4, 3))     # Shape (4, 3)
        
        # Hasil: (5, 4, 3)
        print((A + B).shape)
        ```
        
        Pada contoh tersebut, shape output `(5, 3, 4)` lebih besar dibandingkan dengan kedua inputan `(5, 1, 3)` dan `(4, 3)` → `(1, 4, 3)`.
        
        Sekarang saya akan menunjukkan proses broadcastnya:
        
        - **Langkah 1: Menyamakan Jumlah Dimensi**
            - A: (5, 1, 3) → sudah 3 dimensi
            - B: (4, 3) → ditambah 1 dimensi di depan → (1, 4, 3)
        - **Langkah 2: Membandingkan Dimensi Satu per Satu** (dari kanan ke kiri)
            - **Dimensi ke-2 (kolom)**:
                - A: 3
                - B: 3
                → Cocok! Tidak perlu broadcasting
            - **Dimensi ke-1 (baris)**:
                - A: 1
                - B: 4
                → A akan di-broadcast menjadi 4 (diulang 4 kali)
            - **Dimensi ke-0 (lapisan)**:
                - A: 5
                - B: 1
                → B akan di-broadcast menjadi 5 (diulang 5 kali)
        - **Shape Hasil Akhir**:
            - Ambil nilai maksimum dari setiap dimensi:
                - Dimensi 0: max(5, 1) = 5
                - Dimensi 1: max(1, 4) = 4
                - Dimensi 2: max(3, 3) = 3
                → Jadi shape akhir: (5, 4, 3)
        
    
- **Matematika functions**
    - Kategori Fungsi Matematika
        - Fungsi Dasar
            
            ```python
            arr = np.array([1, 4, 9])
            
            # Akar kuadrat
            print(np.sqrt(arr))  # [1. 2. 3.]
            
            # Eksponensial (e^x)
            print(np.exp(arr))   # [2.71828183e+00 5.45981500e+01 8.10308393e+03]
            
            # Logaritma
            print(np.log(arr))   # [0. 1.38629436 2.19722458]
            
            ```
            
        - Trigonometri
            
            ```python
            angles = np.array([0, np.pi/2, np.pi])
            print(np.sin(angles))  # [0.0000000e+00 1.0000000e+00 1.2246468e-16]
            ```
            
        - Pembulatan
            
            ```python
            decimals = np.array([1.234, 5.678, 9.012])
            print(np.round(decimals, 1))  # [1.2 5.7 9.0]
            ```
            
        
    
    **Cara Kerja Internal**
    NumPy mengoptimalkan operasi dengan:
    
    - **Vectorization**: Proses seluruh array sekaligus
        - **Loop C-level**: Lebih cepat daripada Python loop
    - **SIMD Instructions**: Menggunakan instruksi processor khusus
    
    Contoh benchmark:
    
    ```python
    # Python murni vs NumPy
    data = range(1_000_000)
    
    # Python loop
    %timeit [math.sqrt(x) for x in data]  # ~200ms
    
    # NumPy vectorized
    arr = np.array(data)
    %timeit np.sqrt(arr)  # ~5ms (40x lebih cepat!)
    
    ```
    
    **Aplikasi Nyata**
    
    - Normalisasi Data
        
        ```python
        data = np.random.normal(10, 5, 100)  # Mean=10, SD=5
        normalized = (data - np.mean(data)) / np.std(data)
        
        ```
        
    - Transformasi Feature
        
        ```python
        # Transformasi log untuk data eksponensial
        price_data = np.array([100, 1000, 10000])
        log_prices = np.log10(price_data)  # [2, 3, 4]
        
        ```
        
    - Engineering Fisika
        
        ```python
        # Menghitung gaya gravitasi
        masses = np.array([5.97e24, 7.35e22])  # Bumi, Bulan
        distances = np.array([6.371e6, 3.844e8])  # Radius bumi, jarak bumi-bulan
        G = 6.67430e-11
        
        forces = G * (masses[0] * masses[1]) / distances**2
        
        ```
        
         
        
    
    Untuk informasi lebih lanjut mengenai operator fungsi matematika di Numpy Array, saya sarankan untuk membaca dokumentasi resminya. Atau Anda dapat memeriksanya di [Geeksforgeeks](https://www.geeksforgeeks.org/python/numpy-mathematical-function/), tempat saya belajar.
    
- **Comparison and Logical Operations**
    - Comparison operator
        
        Sama seperti pada hari pertama, operator perbandingan mengembalikan nilai/array boolean dalam bentuk yang sama. Sehingga operator yang digunakan adalah:
        
        ```python
        ==  # Sama dengan
        !=  # Tidak sama dengan
        >   # Lebih besar
        <   # Lebih kecil
        >=  # Lebih besar atau sama
        <=  # Lebih kecil atau sama
        ```
        
        Contoh:
        
        ```python
        a = np.array([3, 5, 7])
        
        print(a > 4)    # [False  True  True]
        print(a == 5)   # [False  True  False]
        print(a != 7)   # [ True  True False]
        ```
        
    - Logical operators
        
        Juga seperti operator perbandingan, Logical operators pada Numpy Array memiliki kesamaan dengan python di hari pertama. Letak perbedaannya adalah penggunaan tanda (operator) yang akan digunakan dan pemakaiannya yang haram.
        
        Haram? Apakah Anda penasaran mengapa?
        
        Ya, mari kita pelajari ini bersama!
        
        Seperti yang telah diketahui, operator logika digunakan untuk menggabungkan kondisi— dua atau mungkin lebih. Di mana pada python terdapat 3 operator logika yakni `and`, `or` dan `not`.
        
        Tapi dalam Numpy juga sama, terdapat 3 operator logika yang dapat digunakan, yakni:
        
        | Fungsi Numpy | Arti | Contoh |
        | --- | --- | --- |
        | `np.logical_and()` | Kedua kondisi harus True | `np.logical_and(a > 3, a < 7)` |
        | `np.logical_or()` | Salah satu kondisi cukup True | `np.logical_or(a < 4, a > 6)` |
        | `np.logical_not()` | Membalik kondisi | `np.logical_not(a > 5)` |
        
        	
        Sebagai contoh:
        
        ```python
        # Logical operators pada Numpy
        a = np.array([3, 5, 7])
        
        print(np.logical_and(a > 3, a < 7))  # [False  True False]
        print(np.logical_or(a < 4, a > 6))   # [ True False  True]
        print(np.logical_not(a == 5))        # [ True False  True]
        ```
        
        Syntax di atas adalah contoh  penggunaan operator logika pada Numpy. Jika diperjelas, masing-masing perintah `print()` ingin menampilkan operasi (wise element ) terhadap semua elemen di aray `a`. Sebagai referensi, saya juga melampirkan tabel kebenaran.
        
        ![Tabel kebenaran](Day%207%20%E2%80%94%20Pengantar%20Numpy%2021ec813f9c548003b018f078c748c696/IMG-20250625-WA0003.jpg)
        
        Sumber: pribadi
        
        Karena itu, kita akan memecah syntax-nya menjadi bagian-bagian kecil.
        
        ```python
        print(np.logical_and(a > 3, a < 7))
        ```
        
        - `a > 3`:
            - `3 > 3` menghasilkan `False`
            - `5 > 3` menghasilkan `True`
            - `7 > 3` menghasilkan `True`
            
            Menghasilkan array boolean sementara: `[False True True]`.
            
        - `a < 7`:
            - `3 < 7` menghasilkan `True`
            - `5 < 7` menghasilkan `True`
            - `7 < 7` menghasilkan `False`
            
            Menghasilkan array boolean sementara: `[True True False]`.
            
        - Mendapatkan list boolean
        
        ```python
        np.logical_and([False True True], [True True False]) 
        ```
        
        Fungsi `logical_and` kemudian mengambil kedua array boolean sementara ini dan melakukan operasi `AND` :
        
        - `True AND True` menghasilkan `True`
        - `False AND True` menghasilkan `False`
        - `True AND False` menghasilkan `False`
        
        Output: `[False True False]`.
        
        ```python
        print(np.logical_or(a < 4, a > 6))
        ```
        
        - `a < 4`:
            - `3 < 4` menghasilkan `True`
            - `5 < 4` menghasilkan `False`
            - `7 < 4` menghasilkan `False`
            
            Menghasilkan array boolean sementara: `[True False False]`.
            
        - `a > 6`: Operasi perbandingan ini juga dilakukan pada setiap elemen di array a.
            - `3 > 6` menghasilkan `False`
            - `5 > 6` menghasilkan `False`
            - `7 > 6` menghasilkan `True`
            
            Menghasilkan boolean sementara: `[False False True]`.
            
        - Mendapatkan list boolean
        
        ```python
        np.logical_or([True False False], [False False True])
        ```
        
        - `True OR False` menghasilkan `True`
        - `False OR False` menghasilkan `False`
        - `False OR True` menghasilkan `True`
        
        Output: `[True False True]`.
        
        ```python
        print(np.logical_not(a == 5))
        ```
        
        - `a == 5`:
            - `3 == 5` menghasilkan `False`
            - `5 == 5` menghasilkan `True`
            - `7 == 5` menghasilkan `False`
            
            Menghasilkan array boolean sementara: `[False True False]`.
            
        - Mendapatkan list boolean
        
        ```python
        np.logical_not([False True False])
        ```
        
        - `NOT False` menghasilkan `True`
        - `NOT True` menghasilkan `False`
        - `NOT False` menghasilkan `True`
        
        Output: `[True False True]`
        
        Selain itu terdapat beberapa hal yang harus diperhatikan dalam penulisan operator binary dalam Numpy Array:
        
        ⚠️ **Peringatan Penting!**
        
        - **Jangan tertukar operator**:
            
            ```python
            # Salah (and/or Python tidak bekerja di array)
            (arr > 5) and (arr < 10)
            
            # Benar (gunakan &/|)
            (arr > 5) & (arr < 10)
            
            ```
            
        - **Urutan operasi**:
            
            ```python
            # Evaluasi: 5 & arr dilakukan sebelum >
            arr > 5 & arr < 10  # Salah!
            
            # Gunakan tanda kurung
            (arr > 5) & (arr < 10)  # Benar
            
            ```
            
        
        Sudah mendapatkannya? Yaps, itulah yang haram.
        
        Selanjutnya, logical operations juga dapat digunakan menggunakan fungsi-fungsi seperti di bawah ini:
        
        - `bitwise_and()` or `&`
        - `bitwise_or()` or `|`
        - `bitwise_xor()` or `^`
        - `left_shift()` or `<<`
        - `right_shift()` or `>>`
        
        Namun sayangnya akan dijelaskan secara terpisah → [klik di sini].
        
- String Operations (menggunakan modul khusus `numpy.char`)
NumPy didesain untuk komputasi numerik, sehingga operasi string ditempatkan di sub-modul khusus:
    
    ```python
    text_arr = np.array(["hello", "world", "numpy"])
    ```
    
    - Fungsi String Dasar yang Paling Sering Dipakai
        - Konversi Case
            
            ```python
            np.char.upper(text_arr)   # ['HELLO' 'WORLD' 'NUMPY']
            np.char.lower(text_arr)   # ['hello' 'world' 'numpy']
            np.char.title(text_arr)   # ['Hello' 'World' 'Numpy']
            ```
            
        - Operasi Pencarian
            
            ```python
            # Hitung panjang string
            np.char.str_len(text_arr) # [5 5 5]
            
            # Cek awalan/akhiran
            np.char.startswith(text_arr, "h") # [True, False, False]
            np.char.endswith(text_arr, "y")   # [False, False, True]
            
            ```
            
        - Manipulasi String
            
            ```python
            # Gabungkan dengan delimiter
            np.char.join(",", text_arr) # 'h,e,l,l,o', 'w,o,r,l,d', 'n,u,m,p,y'
            
            # Pisahkan string
            np.char.split(text_arr, "l") # [['he', '', 'o'], ['wor', 'd'], ['numpy']]
            
            ```
            
    - Contoh Aplikasi Nyata
        - Case 1: Membersihkan Data Teks
            
            ```python
            data = np.array(["  hello ", "WORLD ", "  PyThOn  "])
            cleaned = np.char.strip(np.char.lower(data))
            # ['hello', 'world', 'python']
            
            ```
            
        - Case 2: Ekstrak Substring
            
            ```python
            emails = np.array(["user1@gmail.com", "user2@yahoo.com"])
            usernames = np.char.split(emails, "@")[:, 0]  # Ambil bagian sebelum @
            # ['user1', 'user2']
            ```
            
    - Fungsi Lanjutan untuk NLP Dasar
        
        ```python
        # Ganti substring
        np.char.replace(text_arr, "l", "X") # ['heXXo', 'worXd', 'numpy']
        
        # Cari posisi substring
        np.char.find(text_arr, "o") # [4, 1, -1] (-1 jika tidak ditemukan)
        ```
        
    - Perbandingan dengan Python Standar
        
        
        | Operasi | Python Native | NumPy (`np.char`) |
        | --- | --- | --- |
        | Upper Case | `"text".upper()` | `np.char.upper(arr)` |
        | Split | `"text".split()` | `np.char.split(arr)` |
        | Replace | `"text".replace()` | `np.char.replace(arr)` |
        
        Keunggulan NumPy:
        
        - Operasi **vektorisasi** (lebih cepat untuk array besar)
        - Integrasi dengan array multidimensi
    
    - Keterbatasan
        - Tidak mendukung operasi teks kompleks seperti:
            - Regex advance
            - Stemming/Lemmatization
        - Untuk NLP berat, lebih baik gunakan library khusus seperti:
        
        ```python
        from nltk import word_tokenize
        import spacy
        ```
        
    - Tips Penting
        - Konversi ke String:
        Pastikan array bertipe string:
            
            ```python
            arr = np.array(["1", "2"], dtype="<U10")  # Unicode string max 10 char
            ```
            
        - Gabung dengan Operasi Lain:
            
            ```python
            # Filter teks yang mengandung 'lo'
            filtered = text_arr[np.char.find(text_arr, "lo") >= 0]
            ```
            
        - Performance:
        Untuk array kecil, operasi Python native bisa lebih cepat:
            
            ```python
            [s.upper() for s in text_arr]  # Alternatif jika array kecil
            ```
            
    
    Contoh Integrasi: Preprocessing Data Teks
    
    ```python
    # Dataset contoh
    reviews = np.array(["Great product!", "Bad experience.", "Okay lah..."])
    
    # 1. Normalisasi
    normalized = np.char.lower(np.char.replace(reviews, ".", ""))
    
    # 2. Hitung jumlah kata
    word_counts = np.char.str_len(np.char.split(normalized))
    ```
    

## Index dan Slicing

Indexing dan slicing adalah cara untuk mengakses dan memodifikasi elemen array NumPy.

- Basic Indexing (Akses Elemen Tunggal)
    
    ```python
    import numpy as np
    arr = np.array([10, 20, 30, 40, 50])
    
    # Syntax indexing
    elemen = arr[index]
    
    # Contoh:
    print(arr[0])   # 10 (indeks pertama)
    print(arr[-1])  # 50 (indeks terakhir)
    ```
    
- Slicing (Akses Sub-Array)
    
    ```python
    # Syntax slicing
    sub_arr = arr[start:stop:step]
    
    # Contoh:
    print(arr[1:4])    # [20 30 40] (indeks 1-3)
    print(arr[::2])    # [10 30 50] (loncat 2 langkah)
    ```
    
    Visualisasi Slicing:
    
    ```
    Index: [0] [1] [2] [3] [4]
    Value: 10  20  30  40  50
           ^   ^---^---^   ^
           |      slice    |
           first           last
    ```
    
- Multi-Dimensional Arrays
    
    ```python
    mat = np.array([[1, 2, 3],
                   [4, 5, 6],
                   [7, 8, 9]])
    
    # Syntax indexing 2D
    nilai = mat[row_index, col_index]
    
    # Contoh:
    print(mat[1, 2])  # 6 (baris 1, kolom 2)
    
    # Syntax slicing 2D
    sub_mat = mat[row_slice, col_slice]
    
    # Contoh:
    print(mat[:2, 1:])  # Baris 0-1, kolom 1-akhir
    # Output: [[2 3]
    #          [5 6]]
    ```
    
- Kombinasi Indexing & Slicing

```python
# Akses kolom tertentu di semua baris
print(mat[:, 1])  # [2 5 8] (kolom 1 semua baris)

# Akses baris tertentu dengan step
print(mat[::2, ::2])  # Baris genap, kolom genap
# Output: [[1 3]
#          [7 9]]

```

- Slicing dengan Step

```python
# Syntax lengkap
arr[start:stop:step]

# Contoh:
print(arr[1:4:2])  # [20 40] (indeks 1 dan 3)
print(arr[::-1])   # [50 40 30 20 10] (reverse)
```

- Aturan Penting
    - Start inklusif, stop eksklusif
        
        ```python
        arr[1:3]  # Mengambil indeks 1 dan 2
        ```
        
    - Default value:
        - `start` = 0
        - `stop` = panjang array
        - `step` = 1
    - Indeks negatif:
        
        ```python
        arr[-3:]  # 3 elemen terakhir: [30, 40, 50]
        ```
        
- Contoh Praktis
    
    ```python
    # Dataset suhu harian
    suhu = np.array([25, 28, 30, 22, 27])
    
    # Akses hari kerja (indeks 0-4, step 1)
    hari_kerja = suhu[:5]  # [25 28 30 22 27]
    
    # Akses hari genap
    hari_genap = suhu[::2]  # [25 30 27]
    ```
    
    **Tips**: Gunakan `:` tanpa angka untuk mengambil seluruh axis:
    
    ```python
    mat[:, 0]  # Ambil kolom pertama semua baris
    
    ```
    

## 📘 Ringkasan

Cheetsheet Numpy Array

[IMG-20250628-WA0006.jpg](https://drive.google.com/file/d/12RrLGuRDBGNffeUK0uX-xm_iti1EpI2P/view?usp=drivesdk)

## 🔧 Tools Digunakan

- Python
- Google Colab

## 📈 Progress

- Durasi: Sebenarnya lebih dari sehari
- Kode atau Proyek Mini:

[Google Colab](https://colab.research.google.com/drive/1SPXxxtzOdCLU8ux7rO6gn8BXArftGOUL)

## 📎 Resource

- [Geeksforgeeks](https://www.geeksforgeeks.org)
- [Numpy Official](https://numpy.org/)
- [DeepSeek](https://www.deepseek.com/)

## 🗣️ Refleksi

- Mengapa Numpy begitu membingungkan? Karena itulah belajar.