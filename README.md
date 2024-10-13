Bagian kode ini berfungsi untuk menghitung dan mengisi konfigurasi elektron ke dalam subkulit suatu atom berdasarkan nomor atom yang diberikan. Berikut penjelasan tiap barisnya:

<br>

```python
    sub_kulit = [
        ('1s', 2), ('2s', 2), ('2p', 6), 
        ('3s', 2), ('3p', 6), ('4s', 2), 
        ('3d', 10), ('4p', 6), ('5s', 2), 
        ('4d', 10), ('5p', 6), ('6s', 2), 
        ('4f', 14), ('5d', 10), ('6p', 6), 
        ('7s', 2), ('5f', 14), ('6d', 10), 
        ('7p', 6)
    ]
    konfigurasi = []
    sisa_elektron = nomor_atom
    subkulit_terakhir = None
    elektron_terakhir = 0
    for sub, kapasitas in sub_kulit:
        if sisa_elektron > 0:
            elektron_diisi = min(sisa_elektron, kapasitas)
            konfigurasi.append(f'{sub}{elektron_diisi}')
            sisa_elektron -= elektron_diisi 
            if sisa_elektron == 0:
                subkulit_terakhir = sub 
                elektron_terakhir = elektron_diisi  
                break  
        else:
            break
```

<br>

### 1. **Daftar Subkulit Elektron**
```python
sub_kulit = [
    ('1s', 2), ('2s', 2), ('2p', 6), 
    ('3s', 2), ('3p', 6), ('4s', 2), 
    ('3d', 10), ('4p', 6), ('5s', 2), 
    ('4d', 10), ('5p', 6), ('6s', 2), 
    ('4f', 14), ('5d', 10), ('6p', 6), 
    ('7s', 2), ('5f', 14), ('6d', 10), 
    ('7p', 6)
]
```
- **`sub_kulit`** adalah daftar yang berisi pasangan subkulit elektron beserta kapasitas maksimum elektron yang bisa diisi pada setiap subkulit.
- Misalnya, `'1s'` memiliki kapasitas 2 elektron, `'2p'` memiliki kapasitas 6 elektron, `'3d'` memiliki kapasitas 10 elektron, dan seterusnya.
- Urutan subkulit ini mengikuti aturan Aufbau, yang digunakan untuk mengisi elektron ke dalam subkulit dengan energi terendah terlebih dahulu.

### 2. **Inisialisasi Variabel**
```python
konfigurasi = []
sisa_elektron = nomor_atom
subkulit_terakhir = None
elektron_terakhir = 0
```
- **`konfigurasi`**: List kosong yang akan menyimpan konfigurasi elektron atom. Nantinya, konfigurasi ini akan berisi subkulit dan jumlah elektron yang diisi, misalnya: `['1s2', '2s2', '2p6']`.
- **`sisa_elektron`**: Diinisialisasi dengan nilai dari `nomor_atom` (jumlah elektron yang dimiliki atom). Variabel ini akan menyimpan jumlah elektron yang tersisa untuk diisi ke dalam subkulit.
- **`subkulit_terakhir`**: Variabel untuk menyimpan subkulit terakhir yang diisi elektron.
- **`elektron_terakhir`**: Menyimpan jumlah elektron yang diisi di subkulit terakhir.

### 3. **Proses Pengisian Elektron ke Subkulit**
```python
for sub, kapasitas in sub_kulit:
    if sisa_elektron > 0:
        elektron_diisi = min(sisa_elektron, kapasitas)
        konfigurasi.append(f'{sub}{elektron_diisi}')
        sisa_elektron -= elektron_diisi 
        if sisa_elektron == 0:
            subkulit_terakhir = sub 
            elektron_terakhir = elektron_diisi  
            break  
    else:
        break  
```
- **Looping `for sub, kapasitas in sub_kulit`**:
  - Loop ini akan menelusuri setiap subkulit (`sub`) dan kapasitas maksimalnya (`kapasitas`) yang sudah didefinisikan di dalam `sub_kulit`.
  
- **`if sisa_elektron > 0`**:
  - Mengecek apakah masih ada elektron yang perlu diisi (`sisa_elektron` lebih dari 0). Jika tidak ada lagi elektron, maka pengisian akan berhenti.

- **`elektron_diisi = min(sisa_elektron, kapasitas)`**:
  - Menentukan jumlah elektron yang akan diisi ke subkulit saat ini. Elektron yang diisi adalah nilai minimum antara jumlah elektron yang tersisa (`sisa_elektron`) dan kapasitas subkulit yang sedang diproses (`kapasitas`).
  - Contoh: Jika sisa elektron adalah 5 dan kapasitas subkulit adalah 2, maka hanya 2 elektron yang bisa diisi.

- **`konfigurasi.append(f'{sub}{elektron_diisi}')`**:
  - Menambahkan subkulit dan jumlah elektron yang terisi ke dalam list `konfigurasi`. Formatnya adalah nama subkulit (`sub`) diikuti dengan jumlah elektron yang diisi (`elektron_diisi`).
  - Contoh: Jika subkulit adalah `'2p'` dan jumlah elektron yang diisi adalah 6, maka akan ditambahkan sebagai `'2p6'`.

- **`sisa_elektron -= elektron_diisi`**:
  - Mengurangi jumlah elektron yang tersisa (`sisa_elektron`) dengan jumlah elektron yang sudah diisi ke dalam subkulit (`elektron_diisi`).
  
- **`if sisa_elektron == 0:`**:
  - Jika semua elektron sudah terdistribusi (jumlah `sisa_elektron` menjadi 0), maka program akan:
    - Menyimpan nama subkulit terakhir yang diisi dalam variabel `subkulit_terakhir`.
    - Menyimpan jumlah elektron yang terisi pada subkulit terakhir ke dalam variabel `elektron_terakhir`.
    - **`break`**: Menghentikan loop karena tidak ada lagi elektron yang perlu diisi.

- **`else: break`**:
  - Jika tidak ada lagi elektron (`sisa_elektron <= 0`), loop akan berhenti lebih awal.

### Kesimpulan:
- Bagian kode ini menghitung bagaimana elektron terdistribusi ke dalam berbagai subkulit berdasarkan aturan kapasitas maksimum setiap subkulit.
- Setelah semua elektron terdistribusi, kode akan menyimpan subkulit terakhir yang diisi dan jumlah elektron terakhir yang diisi.
- Konfigurasi akhir dari distribusi elektron disimpan di list `konfigurasi`.
  
<br>
<br>
<br>

Bagian kode ini bertujuan untuk menentukan karakteristik subkulit terakhir yang diisi elektron dalam atom, lalu menghitung **bilangan kuantum magnetik** untuk elektron terakhir berdasarkan subkulit tersebut. Berikut penjelasan rinci dari setiap bagian:

<br>

```python
  if subkulit_terakhir:
        subkulit_terakhir =  subkulit_terakhir[1:]    
        if subkulit_terakhir == 's':
            l = 0  
            jumlah_orbital = 1
        elif subkulit_terakhir == 'p':
            l = 1  
            jumlah_orbital = 3
        elif subkulit_terakhir == 'd':
            l = 2 
            jumlah_orbital = 5
        elif subkulit_terakhir == 'f':
            l = 3  
            jumlah_orbital = 7
        orbital = [[0, 0] for _ in range(jumlah_orbital)]  
        bilangan_kuantum_magnetik = list(range(-l, l + 1))
        posisi_terakhir = None
```

<br>

### 1. **Memeriksa Apakah Ada Subkulit Terakhir yang Diisi**
```python
if subkulit_terakhir:
```
- Bagian ini memeriksa apakah variabel `subkulit_terakhir` berisi nama subkulit yang terakhir kali diisi elektron. Kondisi ini hanya terjadi jika masih ada elektron yang diisi ke subkulit sebelumnya.
- Jika ada subkulit terakhir yang diisi, blok kode berikut akan dijalankan.

### 2. **Memotong Nama Subkulit Terakhir**
```python
subkulit_terakhir = subkulit_terakhir[1:]
```
- Variabel `subkulit_terakhir` berisi nama subkulit terakhir (misalnya "2p", "3d", dsb.).
- Bagian kode ini memotong karakter pertama dari nama subkulit, yang biasanya merupakan angka, sehingga hanya tersisa huruf subkulitnya, misalnya: `'s'`, `'p'`, `'d'`, atau `'f'`.
- Contoh: Jika `subkulit_terakhir` adalah `'2p'`, maka setelah pemotongan, variabel ini hanya akan menjadi `'p'`.

### 3. **Menentukan Nilai Bilangan Kuantum Azimuthal (l) dan Jumlah Orbital**
```python
if subkulit_terakhir == 's':
    l = 0  
    jumlah_orbital = 1
elif subkulit_terakhir == 'p':
    l = 1  
    jumlah_orbital = 3
elif subkulit_terakhir == 'd':
    l = 2 
    jumlah_orbital = 5
elif subkulit_terakhir == 'f':
    l = 3  
    jumlah_orbital = 7
```
- Kode ini menentukan **bilangan kuantum azimuthal** `l` (atau disebut juga **bilangan kuantum orbital**) berdasarkan jenis subkulit (s, p, d, f):
  - Subkulit `'s'`: l = 0, jumlah orbital = 1.
  - Subkulit `'p'`: l = 1, jumlah orbital = 3.
  - Subkulit `'d'`: l = 2, jumlah orbital = 5.
  - Subkulit `'f'`: l = 3, jumlah orbital = 7.
  
  Bilangan kuantum azimuthal `l` menggambarkan bentuk orbital, sedangkan **jumlah orbital** menentukan berapa banyak orbital dalam subkulit tersebut:
  - **Subkulit s** memiliki 1 orbital,
  - **Subkulit p** memiliki 3 orbital,
  - **Subkulit d** memiliki 5 orbital,
  - **Subkulit f** memiliki 7 orbital.

### 4. **Menyiapkan List Orbital**
```python
orbital = [[0, 0] for _ in range(jumlah_orbital)]  
```
- Membuat list dua dimensi bernama `orbital`, yang merepresentasikan status pengisian elektron pada setiap orbital dalam subkulit terakhir.
- **Setiap orbital** direpresentasikan oleh sebuah list `[0, 0]`, yang menyatakan dua kemungkinan spin elektron:
  - `[0, 0]` artinya orbital belum diisi elektron (baik spin-up maupun spin-down).
  - Nilai `[1, 0]` menandakan elektron pertama (spin-up) telah diisi.
  - Nilai `[1, 1]` menandakan orbital penuh (terisi elektron dengan spin-up dan spin-down).
  
  Jumlah list `[0, 0]` dalam `orbital` ditentukan oleh `jumlah_orbital` (bergantung pada subkulit yang sedang diproses, misalnya 1 untuk subkulit s, 3 untuk subkulit p, dan seterusnya).

### 5. **Menentukan Bilangan Kuantum Magnetik**
```python
bilangan_kuantum_magnetik = list(range(-l, l + 1))
```
- **`bilangan_kuantum_magnetik`** adalah list yang berisi nilai-nilai **bilangan kuantum magnetik** (m) untuk setiap orbital dalam subkulit.
- Rentang bilangan kuantum magnetik ini adalah dari `-l` hingga `+l`.
  - Untuk subkulit **s** (l = 0), maka bilangan kuantum magnetiknya adalah [0].
  - Untuk subkulit **p** (l = 1), bilangan kuantum magnetiknya adalah [-1, 0, 1].
  - Untuk subkulit **d** (l = 2), bilangan kuantum magnetiknya adalah [-2, -1, 0, 1, 2].
  - Untuk subkulit **f** (l = 3), bilangan kuantum magnetiknya adalah [-3, -2, -1, 0, 1, 2, 3].

### 6. **Inisialisasi Posisi Terakhir**
```python
posisi_terakhir = None
```
- Variabel `posisi_terakhir` diinisialisasi dengan `None` dan akan digunakan untuk menyimpan indeks posisi orbital terakhir tempat elektron diisi.
- Nantinya, nilai `posisi_terakhir` ini akan digunakan untuk mengambil bilangan kuantum magnetik dari list `bilangan_kuantum_magnetik`.

### Kesimpulan:
Bagian kode ini melakukan beberapa langkah untuk menentukan sifat subkulit terakhir yang diisi elektron:
1. Menentukan **jenis subkulit** terakhir (s, p, d, atau f).
2. Menghitung **bilangan kuantum azimuthal** `l` dan jumlah orbital.
3. Membuat representasi orbital untuk subkulit tersebut.
4. Menyusun bilangan kuantum magnetik yang sesuai dengan orbital dalam subkulit terakhir.
5. Mempersiapkan variabel `posisi_terakhir` yang akan digunakan untuk melacak orbital terakhir yang terisi.

Langkah-langkah ini membantu menghitung bilangan kuantum magnetik elektron terakhir berdasarkan subkulit yang ditempati.

<br>
<br>
<br>

Bagian kode ini bertujuan untuk **mengisi elektron** ke dalam orbital subkulit terakhir dan melacak **posisi orbital terakhir** yang ditempati oleh elektron tersebut. Berikut adalah penjelasan detail dari setiap baris:

<br>

```python
for i in range(elektron_terakhir):  
            for pengisian in range(jumlah_orbital):
                if orbital[pengisian][0] == 0: 
                    orbital[pengisian][0] = 1  
                    posisi_terakhir = pengisian  
                    break
            else:
                for pengisian in range(jumlah_orbital):
                    if orbital[pengisian][1] == 0:  
                        orbital[pengisian][1] = 1   
                        posisi_terakhir = pengisian  
                        break
```

<br>

### 1. **Loop untuk Mengisi Elektron ke dalam Orbital**
```python
for i in range(elektron_terakhir):
```
- **Loop pertama (`for i in range(elektron_terakhir)`)** akan dijalankan sebanyak jumlah elektron yang diisi di subkulit terakhir (`elektron_terakhir`).
- Setiap iterasi `i` mewakili pengisian satu elektron ke salah satu orbital dalam subkulit.

### 2. **Mengisi Elektron ke Spin-Up dalam Orbital**
```python
for pengisian in range(jumlah_orbital):
    if orbital[pengisian][0] == 0: 
        orbital[pengisian][0] = 1  
        posisi_terakhir = pengisian  
        break
```
- **Loop kedua (`for pengisian in range(jumlah_orbital)`)** digunakan untuk mencari orbital yang belum terisi elektron.
- **`if orbital[pengisian][0] == 0`**:
  - Mengecek apakah orbital saat ini (indeks `pengisian`) belum diisi dengan elektron ber-spin-up (ditandai dengan nilai 0 di posisi pertama list `[0, 0]`).
- **`orbital[pengisian][0] = 1`**:
  - Jika orbital belum terisi, maka elektron ber-spin-up akan diisi ke orbital tersebut, dengan cara mengubah nilai pertama list menjadi 1 (`[1, 0]`).
- **`posisi_terakhir = pengisian`**:
  - Menyimpan indeks orbital yang diisi terakhir kali (yaitu indeks `pengisian`), untuk melacak posisi orbital terakhir yang ditempati elektron.
- **`break`**:
  - Menghentikan loop setelah menemukan orbital kosong yang telah diisi dengan elektron ber-spin-up. Loop tidak perlu mengecek orbital lainnya karena hanya satu elektron diisi per iterasi.

### 3. **Jika Semua Orbital Sudah Terisi Elektron Spin-Up, Isi Elektron Spin-Down**
```python
else:
    for pengisian in range(jumlah_orbital):
        if orbital[pengisian][1] == 0:  
            orbital[pengisian][1] = 1   
            posisi_terakhir = pengisian  
            break
```
- **Else di sini** berarti bahwa jika pada loop pertama tidak ada orbital kosong untuk diisi elektron ber-spin-up (semua posisi `[0]` di setiap orbital sudah diisi), maka program akan masuk ke blok kode ini.
- **Loop kedua (`for pengisian in range(jumlah_orbital)`)** digunakan untuk mencari orbital yang belum terisi elektron ber-spin-down.
- **`if orbital[pengisian][1] == 0`**:
  - Mengecek apakah orbital saat ini belum diisi dengan elektron ber-spin-down (posisi kedua list `[1]` masih 0).
- **`orbital[pengisian][1] = 1`**:
  - Jika orbital belum diisi dengan elektron ber-spin-down, elektron akan diisi ke orbital tersebut, mengubah nilai kedua menjadi 1 (`[1, 1]`).
- **`posisi_terakhir = pengisian`**:
  - Sama seperti pada proses pengisian spin-up, indeks orbital yang diisi terakhir kali akan disimpan dalam `posisi_terakhir`.
- **`break`**:
  - Menghentikan loop setelah menemukan orbital yang belum terisi elektron ber-spin-down dan mengisinya.

### **Proses Pengisian Elektron:**
1. Kode pertama kali akan mencoba mengisi elektron ke orbital kosong yang belum memiliki elektron dengan spin-up.
2. Jika semua orbital sudah terisi elektron spin-up, maka kode akan mengisi elektron ke orbital yang belum memiliki elektron ber-spin-down.
3. **Variabel `posisi_terakhir`** selalu diperbarui setiap kali orbital diisi dengan elektron, menyimpan indeks orbital terakhir yang ditempati oleh elektron.

### **Contoh Kasus:**
Misalkan jumlah elektron terakhir yang diisi (`elektron_terakhir`) adalah 5, dan subkulit terakhir adalah subkulit **p**, yang memiliki 3 orbital. Kode ini akan:
1. Mengisi elektron pertama ke orbital pertama dengan spin-up (`[1, 0]`).
2. Mengisi elektron kedua ke orbital kedua dengan spin-up (`[1, 0]`).
3. Mengisi elektron ketiga ke orbital ketiga dengan spin-up (`[1, 0]`).
4. Mengisi elektron keempat ke orbital pertama dengan spin-down (`[1, 1]`).
5. Mengisi elektron kelima ke orbital kedua dengan spin-down (`[1, 1]`).
6. Posisi terakhir elektron kelima adalah di orbital kedua.

### Kesimpulan:
- Kode ini memastikan pengisian elektron mengikuti aturan **Hund** (mengisi spin-up terlebih dahulu) dan **Prinsip Larangan Pauli** (maksimal dua elektron dengan spin berbeda dalam satu orbital).
- Variabel `posisi_terakhir` digunakan untuk melacak orbital terakhir yang diisi, yang akan digunakan untuk menentukan **bilangan kuantum magnetik** dari elektron terakhir.

<br>
<br>
<br>

Baris kode ini menampilkan **Nilai Kuantum Magnetik** dari elektron terakhir yang diisi ke dalam orbital. Mari kita uraikan secara rinci:

<br>

```python
  print(f"Nilai Kuantum Magnetik = {bilangan_kuantum_magnetik[posisi_terakhir]}")
```

<br>

### 1. **Fungsi `print()`**
```python
print(f"Nilai Kuantum Magnetik = {bilangan_kuantum_magnetik[posisi_terakhir]}")
```
- Fungsi `print()` digunakan untuk menampilkan teks atau informasi pada layar.

### 2. **F-String**
```python
f"Nilai Kuantum Magnetik = {bilangan_kuantum_magnetik[posisi_terakhir]}"
```
- **F-string** (`f"..."`) digunakan untuk memformat string dengan cara memasukkan variabel atau ekspresi Python langsung ke dalam string.
- Dalam kasus ini, ekspresi `{bilangan_kuantum_magnetik[posisi_terakhir]}` akan dievaluasi dan hasilnya dimasukkan ke dalam string di tempat tanda `{}`.

### 3. **`bilangan_kuantum_magnetik[posisi_terakhir]`**
- **`bilangan_kuantum_magnetik`** adalah list yang berisi nilai-nilai bilangan kuantum magnetik (m) untuk subkulit terakhir yang diisi. Nilai-nilai ini tergantung pada jenis subkulit:
  - Untuk subkulit **s** (l = 0), list ini hanya berisi [0].
  - Untuk subkulit **p** (l = 1), list ini berisi [-1, 0, 1].
  - Untuk subkulit **d** (l = 2), list ini berisi [-2, -1, 0, 1, 2].
  - Untuk subkulit **f** (l = 3), list ini berisi [-3, -2, -1, 0, 1, 2, 3].
  
- **`posisi_terakhir`** menyimpan indeks dari orbital terakhir yang ditempati oleh elektron terakhir. Indeks ini digunakan untuk mengambil nilai bilangan kuantum magnetik dari list `bilangan_kuantum_magnetik`.
  
- Misalnya, jika `posisi_terakhir` bernilai 2 dan subkulit yang sedang diisi adalah **subkulit p**, maka nilai `bilangan_kuantum_magnetik[posisi_terakhir]` adalah 1 (karena list bilangan kuantum magnetik untuk subkulit p adalah `[-1, 0, 1]`).

### 4. **Output dari Baris Ini**
- Baris ini akan mencetak teks **"Nilai Kuantum Magnetik ="** diikuti oleh nilai bilangan kuantum magnetik untuk elektron terakhir, yang diambil dari list `bilangan_kuantum_magnetik` pada posisi `posisi_terakhir`.
  
### **Contoh Kasus:**
- Misalkan elektron terakhir diisi ke subkulit **p** (bilangan kuantum magnetik = [-1, 0, 1]) dan `posisi_terakhir` bernilai 2. Maka, nilai yang diambil dari list `bilangan_kuantum_magnetik` adalah 1, sehingga output dari baris ini adalah:
  ```
  Nilai Kuantum Magnetik = 1
  ```

### Kesimpulan:
Baris ini menampilkan nilai **bilangan kuantum magnetik** (m) untuk elektron terakhir yang diisi, berdasarkan subkulit yang ditempati elektron tersebut dan posisi orbital terakhir yang terisi.
