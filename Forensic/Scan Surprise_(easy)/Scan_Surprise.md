<!----- Start Main ----->
<body>
  <header>
    <h2>🎊 Scan_Surprise 🎊</h2>
    <table border= "1" cellspacing="5" align="left">    
      <tr>
        <td><strong>Easy</strong></td>
        <td><strong>Forensics</strong></td>
        <td><strong>picoCTF 2024</strong></td>
        <td><strong>shell</strong></td>
        <td><strong>browser_webshell_solveable</strong></td>
        <td><strong>qr_code</strong></td>
      </tr>
    </table>
  </header>
  <main>
      <br>
      <h2></h2>
      <h3 align="left">Author: Jeffery John</h3>
      <h3>Description</h3>
        <p align="justify">I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?
You can download the challenge files here:
<a href="https://artifacts.picoctf.net/c_atlas/3/challenge.zip">challenge.zip</a>
Additional details will be available after launching your challenge instance..</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too. <br>
> Hint 2: Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11 <br>
> Hint 3: If you don't have access to a phone, you can also use zbar-tools to convert an image to text
<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/kana_arima.gif" alt="kana_arima.gif">
  <hr>
</p> 

<!----- Start Answer ----->
### Cara 1 (Akses Soal)
Sama seperti sebelumnya, kalian harus launch dulu challenge nya agar bisa diakses
> [!TIP]
> The same files are accessible via SSH here:
ssh -p 54481 ctf-player@atlas.picoctf.net
Using the password 6dd28e9b. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden!

Kita diminta untuk remote server picoctf untuk mengakses file yang berisi soalnya 

### Cara 2 (Akses Soal)
> [!IMPORTANT]
> KALIAN TIDAK HARUS LAUNCH CHALLENGE NYA <br>
> KALIAN BISA MENDOWNLOAD SOALNYA DI "DESCRIPTION" SEBELUMNYA <br>
> <a href="https://artifacts.picoctf.net/c_atlas/3/challenge.zip">challenge.zip</a>

> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF] <br>
  └─$ wget https://artifacts.picoctf.net/c_atlas/3/challenge.zip <br>
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF] <br>
  └─$ unzip challenge.zip

Kalian akan menemukan flag.png dan dari sini caranya akan sama <br>
Keduanya sama-sama berisi file dengan nama flag.png baik <b>Cara 1 maupun Cara 2 untuk akses soal</b> <br>
Aku disini menggunakan remote server untuk mengerjakan
# Pembahasan Soal
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF] <br>
  └─$ ssh -p 54481 ctf-player@atlas.picoctf.net

Akan muncul tampilan seperti ini<br>
> ![Screenshot 2025-02-15 204629](https://github.com/user-attachments/assets/4e211eab-0221-462b-adcf-2bd0cde67f5c)

dan yah disini kita akan menggunakan hint yang diberikan author:
# 1. Menggunakan scanner bawaan dari android
> [!TIP]
> Untuk cara ini sangat mudah, kalian hanya perlu menggunakan google lens dan kalian akan mendapatkan tampilan seperti ini:


> ![Screenshot 2025-02-15 205230](https://github.com/user-attachments/assets/6c4fc29e-676b-4b7e-81d2-b0181570a3d3)

# 2. Menggunakan zbar tools
Dari hint author, kita juga bisa menggunakan tools linux, Zbar tools. <br>
Fitur Utama ZBar-tools adalah:
- membaca Kode dari Gambar <br>
ZBar dapat mendeteksi dan membaca kode QR atau barcode yang ada di file gambar. <br>

- Membaca Kode dari Kamera <br>
Anda dapat menggunakan ZBar untuk membaca kode QR langsung dari kamera atau webcam.

Mendukung Berbagai Format <br>
ZBar mendukung berbagai format kode, termasuk:<br>
- QR Code
- EAN-13/8
- UPC-A/E
- Code 128
- Code 39
> [!TIP]
> ctf-player@challenge:~/drop-in$ zbarimg flag.png

Dan yah flag nya langsung muncul yeyy!👀<br>
> ![Screenshot 2025-02-15 210338](https://github.com/user-attachments/assets/fefcead8-b2ab-4537-8ce4-e6bf13e06e77)
<br>
<!----- End Answer ----->
<hr>
<p align="center">
   <img src="/assets/anime.gif" alt="anime.gif">
  <hr>
</p> 
