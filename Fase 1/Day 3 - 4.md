# Day 3 - 4 — Control Flow

Tags: Journey
author: Bulan Nurlaela
Last Update: June 11, 2025 10:45 PM
Cats: Data, Manajemen

# **Disclaimer!**

> Karena beberapa sumber menggunakan istilah yang berbeda. Hal yang mana sering disebut sebagai ‘debat terminologi’— di beberapa saat ketika saya bertanya kepada DeepSeek, hal itu tentunya membingungkan saya sebagai pemula. Jujur saja saya merasa frustasi dengan berbedanya istilah yang digunakan. Namun saya berusaha membuatnya sesederhana mungkin dengan: control flow → conditional statement.
> 

# 📌 Topik Hari Ini

## Hubungan dan analogi istilah

### Konsep

Dalam Teori Ilmu Komputer:

- **Control Flow (Alur Kendali)**: Konsep luas (universal) yang mencakup semua mekanisme untuk mengatur urutan eksekusi program.
    - **Termasuk**:
        - Sequence (alur linear eksekusi berurutan)
        - Selection (conditional statements)
        - Iteration/looping (`for`, `while`)
        - Recursion
        - Concurrency
- **Conditional Statements**: Subset dari control flow yang khusus menangani percabangan logika (`if-else`).

Dalam dokumentasi Python (resmi):

- `if-elif-else` = **Compound Statements** (Pernyataan Majemuk).
- `for/while` = **Looping Statements**.
- Keduanya dikategorikan di bawah **"Control Flow Tools"**.
- Contoh Dokumen Resmi:

```python
# Dari Python Docs:
if x < 0:
    print("Negatif")
elif x == 0:
    print("Nol")
else:
    print("Positif")

```

### Analogi

Bayangkan seperti alur air:

- `if-else` = **Percabangan sungai** (air memilih jalur).
- `for` = **Siklus air terjun** (pengulangan terprediksi).
- `while` = **Air pasang-surut** (berulang sampai kondisi terpenuhi).

## Conditional statement (`if`, `elif`, `else`)

### If Statement

- `If`
    
    Struktur paling dasar untuk mengeksekusi blok kod hanya jika kondisi bernilai `True`.
    
    Syntax dasar dari if adalah seperti ini:
    
    ```python
    if kondisi:
       # kode yang dijalankan jika kondisi bernilai benar
    ```
    
    Contoh kode:
    
    ```python
    nilai = 85
    if nilai >= 80:
       print("Lulus")
       
    # output: Lulus
    ```
    
    Mekanisme di Balik Layar:
    
    - Python mengevaluasi ekspresi setelah `if` (`nilai >= 80`).
    - Jika hasil evaluasi `True`, blok kode di bawahnya dijalankan.
    - Jika `False`, blok kode dilewati.
    
    Selain itu, penggunaan `if` juga bisa dilakukan untuk satu atau dua kondisi
    
    ```python
    # Cara Tidak Efisien (4 pengecekan terpisah)
    nilai = 85
    if nilai >= 90:
        print("A")
    if 80 <= nilai < 89:
        print("B")
    if 70 <= nilai < 80:
        print("C")
    if nilai < 70:
        print("D")
    ```
    

Pada syntax di atas fungsi `if` digunakan untuk memeriksa kondisi nilai yang di masukkan. Dalam hal ini, fungsi `if` bekerja dengan:

- Apakah nilai ≥ 90?
    - Jika kondisi ini benar, `print(”A”)` akan dieksekusi dan huruf “A” akan dicetak.
    - Jika kondisi ini salah, `print(”A”)` tidak akan dieksekusi
- Apakah nilai lebih besar atau sama dengan dari 80 dan lebih kecil dari 90 di antara 80 dan 89?
    - Jika kondisi ini benar, `print(”B”)` akan dieksekusi dan huruf “B” akan dicetak.
    - Jika kondisi ini salah, `print(”B”)` tidak akan dieksekusi
- Apakah nilai di antara 70 dan 79?
    - Jika kondisi ini benar, `print(”C”)` akan dieksekusi dan huruf “C” akan dicetak.
    - Jika kondisi ini salah, `print(”C”)` tidak akan dieksekusi
- Apakah nilai kurang dari 70?
    - Jika kondisi ini benar, `print(”D”)` akan dieksekusi dan huruf “D” akan dicetak.
    - Jika kondisi ini salah, `print(”D”)` tidak akan dieksekusi

Dengan melihatnya kita mungkin dapat langsung menjawab bahwa nilai berada di antara 80 hingga 89, atau akan mencetak “B”. Namun bukan itu masalahnya. Di sini if berdiri sendiri dan penulisan fungsi `if` yang berulang empat kali (atau sebanyak `if` digunakan) akan mengecek setiap kondisi `if` dari atas ke bawah, terlepas dari kondisi sebelumnya benar atau salah dan nilai sudah ditemukan di awal.

Sekarang mungkin tidak ada masalah karena blok kode yang dijalankan terhitung sedikit, tetapi bagaimana jika baris nilai yang harus diperiksa adalah 200 atau lebih? Hal tersebut tentu saja merepotkan, bukan? Dan karena itu, fungsi `else` dan `elif` memulai perkenalannya.

### Else Statement (Alternatif)

Menambahkan **blok kode alternatif** yang dijalankan jika kondisi `if` bernilai `False`. `else` **tidak bisa berdiri sendiri,**  harus dipasangkan dengan `if` dan tidak ada kondisi yang ditulis setelah `else`.

Syntax dasarnya:

```python
if kondisi:
    # Kode jika kondisi True
else:
    # Kode jika kondisi False

```

Contoh nyata:

```python
umur = 15
if umur >= 18:
    print("Anda dewasa")
else:
    print("Anda masih di bawah umur")
```

Pada titik ini, jika kita menggunakan contoh sebelumnya dengan mengganti beberapa blok kode `if`, hasilnya akan jauh lebih efisien. Tetapi, tetap saja ada if lain yang akan selalu diperiksa walaupun jawabannya sudah diketahui, kalaupun kita ingin mempertahankan empat kategori penilaian. Di sinilah, peran `elif` dibutuhkan.

### Elif Statement (Kondisi bertingkat**

Singkatan dari *"else if"*. Digunakan untuk **menangani multiple kondisi secara berurutan.**

Syntax dasar:

```python
if kondisi1:
    # Kode jika kondisi1 True
elif kondisi2:
    # Kode jika kondisi2 True
else:
    # Kode jika semua kondisi False
```

Contoh nyatanya:

```python
nilai = 85
if nilai >= 90:
   print("A")
elif 80 <= nilai < 90:
   print("B")
elif 70 <= nilai < 80:
   print("C")
else:
   print("D")
```

Atau juga bisa ditulis dengan:

```python
nilai = 85
if nilai >= 90:
   print("A")
elif nilai >= 80:
   print("B")
elif nilai >= 70:
   print("C")
else:
   print("D")
```

keduanya pada dasarnya sama dan akan menghasilkan output yang juga sama. Bedanya ada di efisiensi penulisannya. Pada contoh pertama kondisi ditulis dengan menjabarkan nilai secara detail, lebih kecil dari apa dan lebih besar dari apa. Dalam hal itu, ketika kita menuliskannya dalam bentuk kedua, pada dasarnya kita menuliskan kode pertama tetapi hanya lebih singkat dan ringan dengan 1 operasi (≥) dari pada gabungan operasi (≥ dan <). Seperti ini, ketika pengecekan `nilai ≥ 90` sudah false, otomatis `nilai < 90`. Jadi `elif nilai ≥ 80` sama artinya dengan `80 ≤ nilai ≤ 90`.

### Level Teknis Lebih Dalam

- Short-Circuit Evaluation
    
    Jika kondisi sudah bisa ditentukan dari bagian awal, Python **tidak melanjutkan evaluasi**.
    
    ```python
    if x > 0 and y > 0:  # Jika x <= 0, y > 0 tidak dievaluasi
        print("Kedua positif")
    
    ```
    
- Nesting **`if`** (Bersarang)
    
    `if` bisa berada di dalam `if` lain (tapi hindari lebih dari 3 level).
    
    ```python
    if x > 0:
        if y > 0:
            print("Kedua positif")
        else:
            print("x positif, y tidak")
    
    ```
    
- Ternary Operator (Pernyataan 1 Baris) adalah Bentuk ringkas dari `if-else`.

```python
status = "Lulus" if nilai >= 80 else "Gagal"

```

## Iteration/Looping (`for`, `while`)

Adalah proses menjalankan blok kode secara berulang selama kondisi tertentu terpenuhi. Python menyediakan dua jenis perulangan utama, yaitu `for` loop dan `while` loop.

### `For` Looping

Adalah perulangan yang digunakan untuk mengulang suatu proses yang urutannya (koleksi data) sudah diketahui.

Struktur dasar

```python
for item in iterable:    # Kode yang akan dijalankan
```

- Iterable adalah **objek yang bisa di-iterasi** karena berisi kumpulan item. Python memeriksa apakah suatu objek iterable dengan metode `__iter__()`.
    
     jenis-jenis iterable:
    
    - Sequence (Urutan Teratur)
        - **List**: `[1, 2, 3]`
        - **Tuple**: `(1, 2, 3)`
        - **String**: `"abc"` (setiap karakter dianggap item)
    - Non-Sequence (Tanpa Urutan)
        - **Set**: `{1, 2, 3}`
        - **Dictionary**: `{"a": 1, "b": 2}` (yang diiterasi adalah *keys*nya)
- Item adalah **satu elemen individual**  dalam suatu kumpulan data (iterable) yang mewakili saat iterasi.
    
    Contoh Nyata:
    
    - Dalam list `["apel", "jeruk", "pisang"]`:
        - `"apel"` = item 1
        - `"jeruk"` = item 2
        - `"pisang"` = item 3
    
    Analog Python:
    

```python
for buah in ["apel", "jeruk", "pisang"]:
    print(buah)  # 'buah' adalah variabel yang menyimpan item saat ini
    
# output: apel, jeruk, pisang
```

Bayangkan Anda memiliki:

- **Sebuah kotak kelereng** (ini **iterable**)
- **Setiap kelereng individual** di dalamnya (ini **item**)

Saat Anda mengeluarkan kelereng **satu per satu** dari kotak, itulah yang disebut **iterasi/looping**.

```
ITERABLE (Kotak Kelereng)
│
├── ITEM 1 (Kelereng Merah)
├── ITEM 2 (Kelereng Biru)
└── ITEM 3 (Kelereng Hijau)
```

Karakteristik Penting `for`:

- **Iterasi pasti**: Berjalan untuk setiap item dalam urutan yang diketahui
- **Iterasi otomatis**: Pindah ke item berikutnya secara otomatis
- **Tanpa penghitung manual**: Tidak perlu mengelola indeks secara eksplisit

Iterasi dengan Range:

```python
for i in range(5):  # 0-4
    print(i * 2)
    
# output: 0, 2, 4, 6, 8
```

Iterasi Dictionary:

```python
orang = {'nama': 'Budi', 'umur': 25}
for kunci, nilai in orang.items():
    print(f"{kunci}: {nilai}")
    
# output:
nama: budi
umur: 25
```

### `While` Looping

Adalah perulangan yang terus berjalan selama kondisi bernilai `True`. Berbeda dengan `for` loop yang beriterasi pada sequence, `while` loop bergantung pada kondisi boolean.

Syntax dasar:

```python
while kondisi:
    # Blok kode yang diulang
    # Perlu memodifikasi variabel kondisi agar loop bisa berhenti
```

Contoh nyata:

```python
counter = 0
while counter < 5:
    print(f"Loop ke-{counter}")
    counter += 1  # Increment counter

# output:    
Loop ke-0
Loop ke-1
Loop ke-2
Loop ke-3
Loop ke-4
```

While loop akan **terus berjalan selamanya** jika kondisi tidak pernah menjadi `False`.

Contoh Berbahaya:

```python
# ❌ Jangan dicoba!
while True:
    print("Ini tidak akan berhenti!")

```

Cara Menghentikannya adalah dengan menekan `Ctrl + C` di terminal atau restart kernel.

- Validasi Input User

```python
password = ""
while password != "rahasia123":
    password = input("Masukkan password: ")
print("Login berhasil!")

# akan terus meminta input password sampai memasukkan password yang benar
```

- Menghitung Mundur

```python
countdown = 5
while countdown > 0:
    print(countdown)
    countdown -= 1
print("Go!")

# akan terus looping sampai countdown menjadi <= 0
# output: 5 4 3 2 1 Go! 
```

- Pemrosesan Data

```python
data = [10, 20, 30]
while data:  # Selama list tidak kosong
    print(data.pop())  # Hapus & print item terakhir
# Output: 30, 20, 10
```

### Kontrol Loop di Python

Digunakan untuk mengendalikan alur perulangan, Teknik ini mengatur eksekusi perulangan dengan presisi.

- Break: **Menghentikan loop secara paksa**
Fungsinya untuk menghentikan loop sepenuhnya meskipun kondisi masih `True`.
    
    Contoh:
    
    ```python
    for i in range(10):
        if i == 5:
            break  # Loop berhenti di sini
        print(i)
    
    # output:
    0
    1
    2
    3
    4
    ```
    
    Analogi: Seperti tombol darurat yang menghentikan mesin seketika.
    
- Continue: **Melompati Iterasi**
    
    Fungsi adalah untuk Melewati iterasi saat ini dan lanjut ke iterasi berikutnya.
    
    Contoh:
    
    ```python
    for i in range(5):
        if i == 2:
            continue  # Jika sudah sampai di i == 2, maka lewati angka 2 dan lanjut ke angka berikutnya yaitu 3
        print(i)
    
    # output;
    0
    1
    3 # angka 2 dilewati dan langsung ke 3
    4
    ```
    
    Analog: Seperti melewatkan lagu yang tidak disukai dalam playlist.
    
- **Else pada Loop**
    
    Blok `else` pada loop akan dieksekusi **hanya jika loop selesai secara normal** (tidak dihentikan paksa oleh `break`).
    
    - Analogi Sederhana: Bayangkan Anda sedang mencari sebuah kunci di dalam tas:
        - Jika menemukan kunci (`break`), Anda langsung berhenti mencari.
        - Jika sudah mencari semua kantong (`loop selesai`) tapi tidak menemukan, Anda melakukan aksi alternatif (`else`).
    
    Contoh:
    
    ```python
    for i in range(3):
        print(i)
    else:
        print("Loop selesai tanpa break")
        
    # output:
    0
    1
    2
    Loop selesai tanpa break
    ```
    
    Contoh Nyata:
    
    ```python
    for item in cart:
        if item == "buku":
            print("Item ditemukan!")
            break
    else:
        print("Item tidak ada")  # Jika tidak ditemukan
    
    ```
    
    Contoh pada `while` Loop
    
    ```python
    count = 0
    while count < 3:
        print(f"Count: {count}")
        count += 1
    else:
        print("Loop selesai alami")
    
    ```
    
    Terdapat Perbedaan Penting dalam penggunaan else pada looping:
    
    | Scenario | Perilaku `else` |
    | --- | --- |
    | Loop selesai normal | `else` dijalankan |
    | Loop dihentikan `break` | `else` **tidak** dijalankan |
    | Loop error/exception | `else` **tidak** dijalankan |
    
    Contoh lain, mengenai pencarian data:
    
    ```python
    names = ['Andi', 'Budi', 'Citra']
    search = 'Dodi'
    
    for name in names:
        if name == search:
            print(f"Found {search}!")
            break
    else:
        print(f"{search} not found in list")  # Akan dieksekusi
    ```
    
    - Kasus Khusus
        - **Loop kosong**: `else` tetap dijalankan
        
        ```python
        for i in []:
            print(i)
        else:
            print("Loop kosong tetap jalan else")
            
        # ouput: Loop kosong tetap jalan else 
        ```
        
        Ketika Anda mencoba iterable (koleksi data) yang diberikan ke loop `for` kosong, loop itu sendiri tidak akan pernah dieksekusi barang sekali pun. Artinya `print(i)` tidak pernah dijalankan dan loop selesai secara normal (tidak ada elemen untuk iterasi dan tidak ada break untuk dipicu), jadi blok `else` yang akan dieksekusi.
        
        - **Nested loop**: `else` hanya terkait dengan loop terdekat
            
            ```python
            for i in range(2):
                for j in range(2):
                    if i == j == 1:
                        break
                else:
                    print(f"Inner loop {i} selesai")
                    
            # output; inner loop 0 selesai 
            ```
            
    - Alternatif Tanpa `else` pada Loop (flag variabel)
        
        Bayangkan Anda sedang bermain *game treasure hunt*:
        
        - **Flag variable** = **Bendera kecil** yang Anda angkat ketika menemukan harta karun
        - Tanpa bendera, Anda tidak tahu apakah harta sudah ditemukan atau belum
        
        Contoh Nyata Flag Variable, Pencarian Data Tanpa **`else`:**
        
        ```python
        found = False  # Inisialisasi flag sebagai False
        
        for item in ['apel', 'jeruk', 'pisang']:
            if item == 'jeruk':
                found = True  # Set flag jadi True ketika ditemukan
                break
        
        if found:  # Cek status flag
            print("Jeruk ditemukan!")
        else:
            print("Jeruk tidak ada")
        
        ```
        
        Cara Kerja:
        
        - Mulai dengan asumsi `found = False` (belum ditemukan)
        - Jika ketemu, ubah `found = True`
        - Setelah loop, cek status `found`
        
        Validasi Input User
        
        ```python
        valid = False  # Flag untuk menandai input valid/tidak
        
        while not valid:
            age = input("Masukkan usia: ")
            if age.isdigit() and int(age) > 0:
                valid = True  # Input valid, ubah flag
            else:
                print("Input salah!")
        
        print(f"Usia Anda: {age}")
        
        ```
        
- Pass: **Placeholder Kosong**

Fungsinya ****adalah sebagai *null operation—*tidak melakukan apa-apa, hanya berfungsi sebagai placeholder untuk menjaga sintaks Python tetap valid.

**Kapan digunakan?**

- Saat membutuhkan blok kode secara sintaksis tapi belum ingin menulis logika
- Sebagai penanda untuk implementasi yang akan ditambahkan later

Contoh:

```python
for i in range(5):
    if i == 3:
        pass  # Tidak lakukan apa-apa, lanjut ke iterasi berikutnya
    print(i)
    
# output:
0
1
2
3
4
```

Bedakan:

- `continue`: Lompat ke iterasi berikutnya
- `pass`: Lanjut eksekusi seperti biasa

Perbedaan Utama: `pass` vs `continue`

| Aspek | `pass` | `continue` |
| --- | --- | --- |
| **Efek pada loop** | Tidak melakukan apa-apa | Langsung ke iterasi berikutnya |
| **Gunakan ketika** | Butuh placeholder sintaks | Ingin melewati iterasi tertentu |
| **Eksekusi kode** | Kode setelah `pass` tetap jalan | Kode setelah `continue` dilewati |
| **Analog** | Tempat duduk kosong | Lompati rintangan |

Contoh Praktis Perbedaan

- Kasus 1: Menggunakan **`pass`**
    
    ```python
    for item in data:
        if item is None:
            pass  # TODO: Handle None values later
        process(item)  # Tetap diproses meski item None
    
    ```
    
- Kasus 2: Menggunakan **`continue`**
    
    ```python
    for item in data:
        if item is None:
            continue  # Lewati item None
        process(item)  # Hanya diproses jika bukan None
    
    ```
    

## 📘 Ringkasan

- Perbandingan kontrol loop:
    
    
    | Statement | Pengaruh | Contoh Use Case |
    | --- | --- | --- |
    | `break` | Hentikan seluruh loop | Keluar saat kondisi khusus terpenuhi |
    | `continue` | Lewati 1 iterasi | Skip data yang tidak valid |
    | `else` | Eksekusi setelah loop normal | Handle case "not found" |
    | `pass` | Tidak lakukan apa-apa | Template fungsi belum siap |
    

## 🔧 Tools Digunakan

- Python
- Notion
- Chrome

## 📈 Progress

- Kode atau Proyek Mini: still editing

## 📎 Resource

- -

## 🗣️ Refleksi
