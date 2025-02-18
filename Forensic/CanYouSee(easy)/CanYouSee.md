<!----- Start Main ----->
<body>
  <header>
    <h2>🧐 CanYouSee 🧐</h2>
    <table border= "1" cellspacing="5" align="left">    
      <tr>
        <td><strong>Easy</strong></td>
        <td><strong>Forensics</strong></td>
        <td><strong>picoCTF 2024</strong></td>
        <td><strong>browser_webshell_solveable</strong></td>
      </tr>
    </table>
  </header>
  <main>
      <br>
      <h2></h2>
      <h3 align="left">Author: Mubarak Mikail</h3>
      <h3>Description</h3>
        <p align="justify">How about some hide and seek?
Download this file <a href="https://artifacts.picoctf.net/c_titan/131/unknown.zip">here</a>.</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: How can you view the information about the picture? <br>
> Hint 2: If something isn't in the expected form, maybe it deserves attention? <br>

# Konteks dan Asumsi🤔
> - Konteks dari challenge ini dari hint 1 yang kita dapat, kita diminta untuk menganalisis informasi dari sebuah foto <br>
> - Dari deskripsi author disebutkan kalau kita diajak bermain "Hide and Seek", hmm <br>
> - Dari Hint kedua kita dapat informasi jika ada sesuatu yang diluar ekspektasi, mungkin itu harus diperhatikan <br>
> - Sesuatu yang dimaksud disini mungkin informasi terkait gambar tersebut

# Tujuan 🚩
> - Mengidentifikasi dan menganalisis data dari sebuah foto

# LOOK AT ME 😠
> [!WARNING]
> SEBELUM MENGERJAKAN PASTIKAN SUDAH MEMBACA FILE README_FIRST.md DI REPOSITORY INI <br>
> AKU ANGGAP KETIKA MEMBACA JAWABAN KALIAN SEMUA SUDAH TAU ISTILAH ATAU HAL-HAL YANG TERKAIT DENGAN SOLVING CHALLENGENYA

<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/eye.gif" alt="eye.gif">
  <hr>
</p> 
<!----- Start Answer ----->

### Step 1
Seperti biasa kita menggunakan terminal linux untuk challenge CTF ini<br>
Buka terminal dan download file  dari deskripsi challenge menggunakan <em>wget</em>
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
└─$ wget https://artifacts.picoctf.net/c_titan/131/unknown.zip

Hmm🤔, <em>unknown.zip</em> <br> 
bukannya di hint ini adalah gambar ya<br>
Sepertinya kita perlu meng-unzip file ini. Tapi sebelum itu, agar lebih aman kita bisa mengecek file tersebut seperti challenge sebelumnya<br>

### Step 2
Coba identifikasi dulu file apa ini sebenarnya
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[\~/PicoCTF] <br>
└─$ ls <br>
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br> 
└─$ file unknown.zip <br>
unknown.zip: Zip archive data, at least v2.0 to extract, compression method=deflate

Ini ada <em>Zip file</em> yang berisi data  yang dikompresi<br>

### Step 3
Kita Unzip file zip ini untuk mengekstrak isinya dengan perintah: <br>
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
  └─$ unzip unknown.zip <br>
> Archive:  unknown.zip 
  inflating: ukn_reality.jpg

Sepertinya kita berhasil mengekstrak file <em>ukn_reality.jpg</em><br>
Istilah "inflating" artinya ekstrasi file tersebut mengembangkan data yang awalnya terkompresi di zip menjadi ukuran aslinya <br>

### Step 4
Karena kita diminta untuk mengidentifikasi file gambar, kita coba fokus saja untuk identifikasi tanpa melihat gambar terlebih dahulu<br>
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
└─$ file ukn_reality.jpg <br>
ukn_reality.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 72x72, segment length 16, baseline, precision 8, 4308x2875, components 3 <br>
Hmm, sepertinya hanya beberapa informasi saja yang bisa kita dapat dan tidak ada yang aneh, coba kita gunakan <em>exiftool</em> untuk melihat metadata lebih lengkapnya.<br>

> [!TIP]
> ![Screenshot 2025-02-17 210103](https://github.com/user-attachments/assets/d2530ee7-0788-49a7-9ad7-a5679ae7d934)

Hmm🤔, Apakah ada sesuatu yang aneh atau diluar ekspektasi dari metadata? <br>
Jawabannya ya, jika kamu lihat di meta data <em>URL</em>, ada sesuatu yang aneh. Apakah URL normal berbentuk seperti itu? 🤔
> [!TIP]
> Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fZDhjMzgxZmR9Cg==

Kita asumsikan ini adalah hasil enkripsi dari suatu kata/kalimat.<br>
Tanda "==" di akhir biasanya umum digunakan untuk metode <em>enkripsi base64</em> . Kita bisa coba <em>decrypt</em> kalimat ini.

### Step 5
Gunakan dan gabungkan beberapa perintah linux di CLi seperti: <em>echo</em>, <em>| (Pipe)</em> dan <em>-d</em>:
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF] <br>
└─$ echo "cGljb0NURntNRTc0RDQ3QV9ISUREM05fZDhjMzgxZmR9Cg==" | base64 -d <br>
picoCTF{ME74D47A_HIDD3N_d8c381fd} <br>

Damn di luar nurul👀 <br> 
Dan yes we got the flag 🚩
> [!NOTE]
> picoCTF{ME74D47A_HIDD3N_d8c381fd}
> <br>
<!----- End Answer ----->
<hr>
<p align="center">
   <img src="/assets/tamako.gif" alt="tamako.gif">
  <hr>
</p> 
