<!----- Start Main ----->
<body>
  <header>
    <h2>⁉️ information ⁉️</h2>
    <table border= "1" cellspacing="5" align="left">    
      <tr>
        <td><strong>Easy</strong></td>
        <td><strong>Forensics</strong></td>
        <td><strong>picoCTF 2021</strong></td>
      </tr>
    </table>
  </header>
  <main>
      <br>
      <h2></h2>
      <h3 align="left">Author: JEDAVIS/DANNY</h3>
      <h3>Description</h3>
        <p align="justify">This <a href="https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg">garden</a> contains more than it seems.</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: What is a hex editor?

# Konteks dan Asumsi🤔
> - Untuk melihat konteks dari challenge ini sangat minim informasi jika hanya dilihat dari deskripsi dan hint <br>
> - Author memberikan sebuah file yang bisa kita download dan satu hint yakni tentang "Apa itu Hex Editor" <br>
> - Dalam deskripsi, author menyebutkan bahwa file <em>garden</em> tersebut mengandung lebih dari apa yang terlihat

# Tujuan 🚩
> - Mencoba mengulik lebih dalam tentang file <em>garden</em> 

# LOOK AT ME 😠
> [!WARNING]
> SEBELUM MENGERJAKAN PASTIKAN SUDAH MEMBACA FILE README_FIRST.md DI REPOSITORY INI <br>
> AKU ANGGAP KETIKA MEMBACA JAWABAN KALIAN SEMUA SUDAH TAU ISTILAH ATAU HAL-HAL YANG TERKAIT DENGAN SOLVING CHALLENGENYA

<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/bocchi.gif" alt="bocchi.gif">
  <hr>
</p> 
<!----- Start Answer ----->

### Step 1
Seperti biasa kita menggunakan terminal linux untuk challenge CTF ini<br>
Buka terminal dan download file  dari deskripsi challenge menggunakan <em>wget</em>
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
└─$ wget https://jupiter.challenges.picoctf.org/static/d0e1ffb10fc0017c6a82c57900f3ffe3/garden.jpg <br>
> garden.jpg                    100%[=================================================>]   2.19M   537KB/s    in 4.2s <br>
2025-02-18 10:14:36 (537 KB/s) - ‘garden.jpg’ saved [2295192/2295192] <br>

Hmm🤔, sepertinya file yang kita download adalah sebuah file gambar dengan ekstensi jpg berukuran 2.19M (MegaByte/MB) <br>
> [!NOTE]
> Dalam Konversi Decimal <br>
> - 1 megabyte (MB) = 1.000.000 byte <br>
> 
> Dalam Konversi Biner 
> - 1 megabyte (MB) = 1.048.576 byte
>
> Artinya file ini mengandung kurang lebih:
> - 2.190.000 byte (dengan konversi decimal)
> - 2.251.392 byte (dengan konversi biner)
> Waw banyak banget ya 😵‍💫

### Step 2
Dari deskripsi soal, author memberi informasi kepada kita bahwa "contains more than it seems" terhadap file ini <br>
Artinya file ini mengandung lebih dari sekedar yang <em>terlihat</em>, mungkin kita bisa membuka file ini dulu
> ![garden](https://github.com/user-attachments/assets/a9a21e5f-cf6e-49d5-afad-d2e37e6f42ae)

Hmm🤔, sepertinya tidak ada yang aneh

### Step 3
Setelah melihat gambar dan ternyata tidak ada yang aneh, kita bisa menggunakan hint yang diberikan author <br>
"What is a hex editor?" <br>
Kita coba menggunakan HxD untuk membuka file nya dan melihat <em>raw content</em> dari file ini
## Tapi sebelum itu, tidak mungkin kita mengecek 2.190.000 byte satu persatu dengan HxD
> [!NOTE]
> - Kita tadi sudah mengecek gambar nya dan ternyata gambar tidak rusak atau corrupt <br>
> - Warna dari gambar juga normal, tapi ini bertentangan dengan deskripsi dari author <br>
> - Itu artinya hanya ada dua kemungkinan: <br>
>   1. Ada data yang disembunyikan <em>setelah footer file</em> <br>
>   2. Ada data yang disembunyikan <em>di bite terakhir</em> dari bagian hexdump file ini <br>
Karena itu kita coba langsung menuju ke byte terakhir dari file <br>

> [!TIP]
> ![Screenshot 2025-02-18 111857](https://github.com/user-attachments/assets/bf4cde48-f839-40cf-861b-32519a9dd59e) <br>
> Struktur khas dari file jpg bisa dilihat dari hexdump nya yang diawali dengan <em>FF D8</em> dan di akhiri dengan <em>FF D9</em> <br>
> Headernya sepertinya normal dan representasi ASCHII nya juga. Kalau begitu kita coba ke bagian footer <br>
> 
>![Screenshot 2025-02-18 111757](https://github.com/user-attachments/assets/418343b8-a18a-4097-b463-25eaa3583344) <br>

hmm👀, bukannya akhir footer harusnya <em>FF D9</em>? <br>
Tapi disini ada beberapa byte hexadesimal lagi setelah EOF (End of File) <br>
Coba kita copy karakter ASCHII dari tiap kode hexadecimal yang di dapat <br>
> [!TIP]
> 48 65 72 65 20 69 73 20 61 20 66 6C 61 67 20 22 70 69 63 6F 43 54 46 7B 6D 6F 72 65 5F 74 68 61 6E 5F 6D 33 33 74 73 5F 74 68 65 5F 33 79 33 65 42 64 42 64 32 63 63 7D 22 0A <br>
> Here is a flag "picoCTF{more_than_m33ts_the_3y3eBdBd2cc}"

### Dan YESS We got the flag🚩 <br>
Haha itu berarti data aneh yang ada dan disembunyikan setelah footer file adalah flagnya👀 <br>
Karena byte ditambahkan setelah footer, maka itu tidak akan mengganggu tampilan dari gambarnya🤩<br>
<!----- End Answer ----->
<hr>
<p align="center">
   <img src="/assets/asuka.gif" alt="asuka.gif">
  <hr>
</p> 
