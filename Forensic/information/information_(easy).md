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
      <h3 align="left">Author: SUSIE</h3>
      <h3>Description</h3>
        <p align="justify">Files can always be changed in a secret way. Can you find the flag? <a href="https://mercury.picoctf.net/static/a614a27d4cb251d04c7d2f3f3f76a965/cat.jpg">cat.jpg</a>.</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: Look at the details of the file <br>
> Hint 2: Make sure to submit the flag as picoCTF{XXXXX} <br>

# Konteks dan Asumsi🤔
> - Konteks dari challenge ini adalah, kita diharuskan untuk menganalisis sebuah file dengan ekstensi .jpg <br>
> - Dari deskripsi yang diberikan author, kemungkinan ada sesuatu yang dirubah dari file ini <br>
> - Dari hint 1 yang diberikan oleh author kita diminta untuk melihat detail dari isi file, kita bisa asumsikan sesuatu yang dirubah itu ada pada detail file.

# Tujuan 🚩
> - Mengidentifikasi dan menganalisis detail file.jpg

# LOOK AT ME 😠
> [!WARNING]
> SEBELUM MENGERJAKAN PASTIKAN SUDAH MEMBACA FILE README_FIRST.md DI REPOSITORY INI <br>
> AKU ANGGAP KETIKA MEMBACA JAWABAN KALIAN SEMUA SUDAH TAU ISTILAH ATAU HAL-HAL YANG TERKAIT DENGAN SOLVING CHALLENGENYA

<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/alice2.gif" alt="alice2.gif">
  <hr>
</p> 
<!----- Start Answer ----->

### Step 1
Seperti biasa kita menggunakan terminal linux untuk challenge CTF ini<br>
Buka terminal dan download file  dari deskripsi challenge menggunakan <em>wget</em>
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
└─$ wget https://mercury.picoctf.net/static/a614a27d4cb251d04c7d2f3f3f76a965/cat.jpg <br>
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
└─$ ls <br>
cat.jpg <br>

File yang kita dapat memiliki ekstensi jpg.<br>

### Step 2
Karena kita diminta melihat detail dari file, mungkin kita bisa melihat metada dari file tersebut terlebih dahulu dengan <em>exiftool</em>
> [!TIP]
> ![Screenshot 2025-02-18 075324](https://github.com/user-attachments/assets/7a736a47-0c60-4aff-babf-56a730f5ce75)

Hmm🤔, Jika kamu menjawab:
> Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617

Kamu kurang tepat, karena bagian itu merupakan hash dari file. Nilai hash tergantung isi dari file.<br>
Tapi tidak apa, untuk saat ini kita simpan dulu. Hash dapat berubah jika ada sesuatu yang dirubah dari filenya <br>

Lalu jika kamu menemukan satu lagi:
> License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9

Benar, tapi masih perlu kita uji karena kemungkinan ini adalah enkripsi lagi <br>
Metadata licence dari suatu file seharusnya menampilkan lisensi dari pemilik hak cipta atau URL tertentu <br>
Tapi apakah itu sebuah URL🤔

### Step 3
Karena kita berasumsi itu adalah enkripsi, maka metode enkripsi yang paling mirip adalah <em>base64</em> <br>
Agar lebih yakin, mari kita coba menggunakan perintah berikut:
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
└─$ echo "cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" | base64 -d <br>
picoCTF{the_m3tadata_1s_modified} <br> 

### Dan YESS We got the flag🚩 <br>
Itu berarti sesuatu yang dirubah tadi adalah metadata dari file tersebut, lebih spesifiknya yakni Licence nya👀

<!----- End Answer ----->
<hr>
<p align="center">
   <img src="/assets/zerotwo.gif" alt="zerotwo.gif">
  <hr>
</p> 
