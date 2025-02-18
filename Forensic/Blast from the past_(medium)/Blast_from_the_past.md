<!----- Start Main ----->
<body>
  <header>
    <h2>⌛ Blast from the past ⌛</h2>
    <table border= "1" cellspacing="5" align="left">    
      <tr>
        <td><strong>Medium</strong></td>
        <td><strong>Forensics</strong></td>
        <td><strong>picoCTF 2024</strong></td>
        <td><strong>browser_webshell_solveable</strong></td>
        <td><strong>metadata</strong></td>
      </tr>
    </table>
  </header>
  <main>
      <br>
      <h2></h2>
      <h3 align="left">Author: SYREAL</h3>
      <h2>As of March 13th, the last check now accepts more formats</h2>
      <h3>Description</h3>
        <p align="justify">The judge for these pictures is a real fan of antiques. Can you age this photo to the specifications?
Set the timestamps on this picture to 1970:01:01 00:00:00.001+00:00 with as much precision as possible for each timestamp. In this example, +00:00 is a timezone adjustment. Any timezone is acceptable as long as the time is equivalent. As an example, this timestamp is acceptable as well: 1969:12:31 19:00:00.001-05:00. For timestamps without a timezone adjustment, put them in GMT time (+00:00). The checker program provides the timestamp needed for each.
Use this <a href="https://artifacts.picoctf.net/c_mimas/91/original.jpg">picture</a>.<br>
Additional details will be available after launching your challenge instance.</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: Exiftool is really good at reading metadata, but you might want to use something else to modify it.

# Konteks dan Asumsi🤔
> - Jadi kita diminta untuk mengubah timestamp dari gambar ini menjadi 1970:01:01 00:00:00.001 <br>
> - Sesuai nama dan deskripsi challenge, sepertinya gambar ini merupakan gambar yang ingin diubah timestamp dari setiap date data nya ke tahun 1970 <br>

# Tujuan 🚩
> - Mengubah TimeStamp dari file gambar ini menjadi waktu yang di spesifikkan 

# LOOK AT ME 😠
> [!WARNING]
> SEBELUM MENGERJAKAN PASTIKAN SUDAH MEMBACA FILE README_FIRST.md DI REPOSITORY INI <br>
> AKU ANGGAP KETIKA MEMBACA JAWABAN KALIAN SEMUA SUDAH TAU ISTILAH ATAU HAL-HAL YANG TERKAIT DENGAN SOLVING CHALLENGENYA

<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/ketik.gif" alt="ketik.gif">
  <hr>
</p> 
<!----- Start Answer ----->

### Step 1
Seperti biasa kita menggunakan terminal linux untuk challenge CTF ini<br>
Buka terminal dan download file  dari deskripsi challenge menggunakan <em>wget</em>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] 
└─$ wget https://artifacts.picoctf.net/c_mimas/91/original.jpg 
```

### Step 2
Dari permintaan author, kita diharuskan untuk mengubah TimeStamp dari gambar menjadi '1970:01:01 00:00:00.001' <br>
Tapi sebelum itu kita cek ada berapa banyak tag data yang harus diubah <br>
> ![Screenshot 2025-02-18 204054](https://github.com/user-attachments/assets/e1f28e8d-0873-4654-b54f-5f04d5144f69)

Sepertinya banyak tag yang harus diubah <br>

### Step 3
Kita bisa gunakan exiftool untuk merubah bersamaan <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ exiftool -AllDates="1970:01:01 00:00:00" original.jpg
    1 image files updated
```
Coba kita cek lagi <br>
> ![Screenshot 2025-02-18 204252](https://github.com/user-attachments/assets/34d65ac4-1bda-45f3-a3ea-19dbb9faa83a)

### Step 4
Masih ada beberapa <em>SubSec</em> yang belum berubah <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ exiftool -SubSecCreateDate="1970:01:01 00:00:00.001" -SubSecDateTimeOriginal="1970:01:01 00:00:00.001" -SubSecModifyDate="1970:01:01 00:00:00.001" original.jpg
    1 image files updated
```
Coba kita cek lagi <br>
![Screenshot 2025-02-18 204525](https://github.com/user-attachments/assets/132b6b04-98b9-4424-a98d-13ad6f42a478)

Oke sudah tidak ada tahun 2023 yang terlihat, seharusnya bisa kita kumpulkan <br>
> [!NOTE]
> Jangan lupa kalian launch challenge nya agar mendapat akses ke server pengumpulan soalnya
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ nc -w 2 mimas.picoctf.net 61135 < original.jpg

┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ nc mimas.picoctf.net 57448
MD5 of your picture:
eb5ae92ce9f801b9d1aa8e4c800e9705  test.out

Checking tag 1/7
Looking at IFD0: ModifyDate
Looking for '1970:01:01 00:00:00'
Found: 1970:01:01 00:00:00
Great job, you got that one!

Checking tag 2/7
Looking at ExifIFD: DateTimeOriginal
Looking for '1970:01:01 00:00:00'
Found: 1970:01:01 00:00:00
Great job, you got that one!

Checking tag 3/7
Looking at ExifIFD: CreateDate
Looking for '1970:01:01 00:00:00'
Found: 1970:01:01 00:00:00
Great job, you got that one!

Checking tag 4/7
Looking at Composite: SubSecCreateDate
Looking for '1970:01:01 00:00:00.001'
Found: 1970:01:01 00:00:00.001
Great job, you got that one!

Checking tag 5/7
Looking at Composite: SubSecDateTimeOriginal
Looking for '1970:01:01 00:00:00.001'
Found: 1970:01:01 00:00:00.001
Great job, you got that one!

Checking tag 6/7
Looking at Composite: SubSecModifyDate
Looking for '1970:01:01 00:00:00.001'
Found: 1970:01:01 00:00:00.001
Great job, you got that one!

Checking tag 7/7
Timezones do not have to match, as long as it's the equivalent time.
Looking at Samsung: TimeStamp
Looking for '1970:01:01 00:00:00.001+00:00'
Found: 2023:11:20 20:46:21.420+00:00
Oops! That tag isn't right. Please try again.
```
Hmm🤔, apakah ada yang terlewat <br>
Coba kita gunakan perintah berikut: <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ exiftool -v original.jpg
```
> [!TIP]
> Kalian cari bagian yang berisi tentang Samsung: TimeStamp
```
Samsung trailer (143 bytes at offset 0x2b82ae):
  SamsungTrailer_0x0a01Name = Image_UTC_Data
  TimeStamp = 1700513181420
  SamsungTrailer_0x0aa1Name = MCC_Data
  MCCData = 310
  SamsungTrailer_0x0c61Name = Camera_Capture_Mode_Info
  SamsungTrailer_0x0c61 = 1
```
Bagian samsung TimeStamp ini ada di offset 0x2b82ae <br>
>  TimeStamp = 1700513181420

Jika diperhatikan, TimeStamp nya aneh. Harusnya memiliki format "YYYY:MM:DD" <br>
Angka nya banyak dan berhubungan dengan waktu. Bisa disimpulkan bahwa TimeStamp ini berlalu dalam format <em>Epoch TIme</em><br>
> [!NOTE]
> Epoch time adalah salah satu format waktu yang menggunakan 13 digit angka untuk merepresentasikan jumlah milidetik yang telah berlalu sejak tanggal 1 Januari 1970, 00:00:00 UTC.<br>
> Itu berarti sudah 1700513181420 milidetik berlalu sejak 1 Januari 1970 00:00:00 <br>

Karena author meminta kita untuk merubah TimeStamp menjadi "1970:01:01 00:00:00.001" <br>
Maka kita hanya perlu merubah nya kembali ke tahun 1970:01:01 00:00:00.001 = 0000000000001 milidetik <br>

### Step 5
Kita tahu samsung TimeStamp ini ada di sekitar offset 0x2b82ae <br>
Kita bisa langsung buka HxD kita untuk melihat data biner dari file ini dan merubahnya <br>
> ![Screenshot 2025-02-18 203528](https://github.com/user-attachments/assets/51d8f328-6679-4efd-89fa-48cb75b10d07)

Dan aku menemukannya di sekitar 2B83xx, Kita bisa ubah angka setelah <b>UTCIMAGEDATA</b> menjadi 0000000000001
> [!TIP]
> - Jika kamu merubah byte nya kamu bisa mengganti dari hexadecimal 31 yang ku block menjadi 30 hingga 12 kali, dan tambahkan 31 di akhir <br>
> - Jika kamu merubah ASCHII nya, kamu hanya perlu langsung merubah angkanya menjadi 0000000000001

### Step 6
Sekarang bisa kamu submit
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ nc -w 2 mimas.picoctf.net 61135 < original.jpg

┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ nc mimas.picoctf.net 57448
MD5 of your picture:
412331ca77b633d2529dc0e0ab5ad6eb  test.out

Checking tag 1/7
Looking at IFD0: ModifyDate
Looking for '1970:01:01 00:00:00'
Found: 1970:01:01 00:00:00
Great job, you got that one!

Checking tag 2/7
Looking at ExifIFD: DateTimeOriginal
Looking for '1970:01:01 00:00:00'
Found: 1970:01:01 00:00:00
Great job, you got that one!

Checking tag 3/7
Looking at ExifIFD: CreateDate
Looking for '1970:01:01 00:00:00'
Found: 1970:01:01 00:00:00
Great job, you got that one!

Checking tag 4/7
Looking at Composite: SubSecCreateDate
Looking for '1970:01:01 00:00:00.001'
Found: 1970:01:01 00:00:00.001
Great job, you got that one!

Checking tag 5/7
Looking at Composite: SubSecDateTimeOriginal
Looking for '1970:01:01 00:00:00.001'
Found: 1970:01:01 00:00:00.001
Great job, you got that one!

Checking tag 6/7
Looking at Composite: SubSecModifyDate
Looking for '1970:01:01 00:00:00.001'
Found: 1970:01:01 00:00:00.001
Great job, you got that one!

Checking tag 7/7
Timezones do not have to match, as long as it's the equivalent time.
Looking at Samsung: TimeStamp
Looking for '1970:01:01 00:00:00.001+00:00'
Found: 1970:01:01 00:00:00.001+00:00
Great job, you got that one!

You did it!
picoCTF{71m3_7r4v311ng_p1c7ur3_12e0c36b}
```
## DANN BINGO KITA DAPAT FLAG NYA 🚩
picoCTF{71m3_7r4v311ng_p1c7ur3_12e0c36b}

> [!WARNING]
> Jika kalian terus stuck di tag 7/7:
> - Pastikan jaringan kalian lancar tanpa lag, karena upload file ke server butuh internet yang kuat <br>
> - Pastikan tidak ada metadata lain atau byte lain yang kalian ubah atau hapus

<!----- End Answer ----->
<hr>
<p align="center">
   <img src="/assets/gore.gif" alt="gore.gif">
  <hr>
</p> 
