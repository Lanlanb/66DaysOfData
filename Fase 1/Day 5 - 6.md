# Day 5 - 6 — Fungsi & Import Modul

Tags: Journey
author: Bulan Nurlaela
Last Update: June 20, 2025 1:27 PM

> **Disc!** saya mengalami distraksi selama beberapa waktu, melupakan progress harian saya dan dalam prosesnya membuat saya terserang flu selama seminggu. Jadi di sinilah saya berusaha memulainya kembali.
> 

# 📌 Topik Hari Ini

## Fungsi dasar

- **Apa itu fungsi?**
    - Blok kode yang dirancang untuk melakukan tugas spesifik.
    - Dapat dipanggil berulang kali.
- **Struktur fungsi**:
    
    ```python
    def nama_fungsi(parameter):
        # Isi fungsi
        return nilai_balik
    
    ```
    

Contoh Fungsi Sederhana:

```python
# Fungsi tanpa parameter
def sapa():
    print("Halo, Selamat belajar!")

sapa()  # Output: Halo, Selamat belajar!

# Fungsi dengan parameter
def tambah(a, b):
    return a + b

hasil = tambah(3, 5)
print(hasil)  # Output: 8

```

## **Parameter vs Argumen**

- **Parameter**: Variabel yang didefinisikan dalam fungsi.
- **Argumen**: Nilai yang diberikan saat memanggil fungsi.

### **Default Parameter**

```python
def pangkat(angka, eksponen=2):
    return angka ** eksponen

print(pangkat(3))      # Output: 9 (eksponen default=2)
print(pangkat(3, 4))   # Output: 81
```

## **Import Modul**

- **Modul**: File Python yang berisi fungsi/variabel yang bisa digunakan di file lain.
- Contoh modul bawaan Python: `math`, `random`, `datetime`.

```python
# Menggunakan modul math
import math
print(math.sqrt(16))  # Output: 4.0

# Menggunakan alias
import pandas as pd

# Import fungsi spesifik
from random import randint
print(randint(1, 10))  # Output: angka acak 1-10
```

### **Praktik**

- **Membuat Modul Sendiri**
    - Buat file `my_module.py`:
        
        ```python
        def greet(name):
            return f"Halo, {name}!"
        ```
        
    - Gunakan di file lain:
        
        ```python
        import my_module
        print(my_module.greet("Budi"))  # Output: Halo, Budi!
        
        ```
        
- **Buat fungsi** `hitung_luas_lingkaran(radius)` yang mengembalikan luas lingkaran.
    
    ```python
    def hitung_luas_lingkaran(radius):
        return 3.14 * radius ** 2
    ```
    

- **Buat fungsi** `cek_genap_ganjil(angka)` yang mengecek apakah angka genap atau ganjil.
    
    ```python
    def cek_genap_ganjil(angka):
        return "Genap" if angka % 2 == 0 else "Ganjil"
    ```
    
- **Gunakan modul `datetime`** untuk menampilkan tanggal hari ini.
    
    ```python
    from datetime import date
    print(date.today())  # Output: 2023-10-05 (contoh)
    
    ```
    

## **Tantangan Kecil [Mini Project]**

- Buat program kalkulator sederhana dengan fungsi:
    - `tambah`, `kurang`, `kali`, `bagi`.
    - Gunakan `import` untuk memisahkan fungsi kalkulator ke file terpisah.
    
    Contoh struktur:
    
    ```
    project/
    │── main.py
    │── kalkulator.py
    ```
    
- Isi `kalkulator.py`:
    
    ```python
    def tambah(a, b):
        return a + b
    # Definisikan fungsi lainnya...
    ```
    
    …
    
    Selengkapnya [On Going]
    

## 📘 Ringkasan

- Eksplor modul Python standar: [Python Standard Library](https://docs.python.org/3/library/).
- Gunakan **docstring** untuk mendokumentasikan fungsi:
- Praktik langsung menggunakan Google Colab.

## 🔧 Tools Digunakan

- Python
- Google Colab

## 📈 Progress

- Kode atau Proyek Mini:

## 📎 Resource

- [FreeCodeCamp Python](https://youtu.be/rfscVS0vtbw)

## 🗣️ Refleksi

- Memulai semuanya dari awal, karena itu menyebalkan … buat catatan agar tidak terdistraksi lagi.
- Mulai terasa paham logika pemrograman.