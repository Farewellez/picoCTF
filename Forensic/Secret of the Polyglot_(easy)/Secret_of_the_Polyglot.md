<!----- Start Main ----->
<body>
  <header>
    <h2>🗣️ Secret of the Polyglot 🗣️</h2>
    <table border= "1" cellspacing="5" align="left">    
      <tr>
        <td><strong>Easy</strong></td>
        <td><strong>Forensics</strong></td>
        <td><strong>picoCTF 2024</strong></td>
        <td><strong>file_format</strong></td>
        <td><strong>polyglot</strong></td>
      </tr>
    </table>
  </header>
  <main>
      <br>
      <h2></h2>
      <h3 align="left">Author: syreal</h3>
      <h3>Description</h3>
        <p align="justify">The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?
Download the suspicious file <a href="https://artifacts.picoctf.net/c_titan/98/flag2of2-final.pdf">here</a>.</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: This problem can be solved by just opening the file in different ways <br>

# Konteks 🤔
> Yah konteks dari challenge ini adalah, kita diminta untuk menginvestigasi sebuah file yang tidak diketahui ekstensi nya. <br>
> File itu sendiri didapat dari NOC (Network Operation Center) <br>
> Selama ekstensi file tersebut tidak sesuai, maka akan sulit bagi kita mengekstrak isi dari filenya <br>

# Tujuan 🚩
> Menemukan cara untuk mengekstrak semua informasi dari file aneh tersebut

<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/Cook.gif" alt="Cook.gif">
  <hr>
</p> 

<!----- Start Answer ----->
### Step 1
> [!TIP]
> - Jelas, pertama kita harus membuka the shell kita atau biasa kita sebut CLI <br>
> - Aku menggunakan WSL disini, untuk kalian bebas menggunakan apa <br>
> - Aku anggap kalian sudah paham cara menggunakan CLI Linux. Jika belum, kalian bisa melihat file README_FIRST.md di repository yang sama dengan file ini <br>
### Step 2
Kalian bisa mulai dengan mendownload file yang ada di deskripsi challenge nya dengan perintah <em>wget</em>
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF] <br>
  └─$ wget https://artifacts.picoctf.net/c_titan/98/flag2of2-final.pdf

Ketika kalian ls maka akan muncul sebuah file
> [!TIP]
>┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF] <br>
└─$ ls <br>
flag2of2-final.pdf <br>
### Step 3
Karena file tersebut memiliki ekstensi .pdf maka kita bisa coba melihat terlebih dahulu isinya
> ![Screenshot 2025-02-16 100906](https://github.com/user-attachments/assets/f8b9ba59-3e68-498a-8b1d-fdfeefbfadb8) <br>

Setelah di scroll ke bawah, ternyata file tersebut memiliki teks di dalamnya. Bisa kita simpan dulu teks tersebut <br>
> 1n_pn9_&_pdf_1f991f77}
### Step 4
Kita bisa menggunakan promt selanjutnya di CLI untuk memeriksa file tersebut lebih lanjut
> [!TIP]
> ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF] <br>
└─$ file flag2of2-final.pdf <br>
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced

Ha?? PNG?? 🤔 <br>
Ternyata ekstensi dari file ini sebenarnya adalah .png, namun author mengubah ekstensi menjadi .pdf dengan isi yang masih bisa dibuka. <br>
Keren banget ya 🤩
Ini berarti kita bisa mengubah ekstensi file yang sebelumnya .pdf menjadi .png untuk melihat gambar dari file .png ini <br>
### Step 5
> [!TIP]
> - Kalian bisa mengubah ektensi nya langsung di file dengan rename menjadi flag2of2-final.pdf ----> flag2of2-final.png<br>
> - Atau kalian bisa mengubah ekstensi nya di CLI dengan promt berikut: <br>
>   ┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF] <br>
└─$ mv flag2of2-final.pdf flag2of2-final.png <br>
> Coba buka file tersebut dan lihat apa isi dari gambarnya
<br>
> ![flag2of2-final](https://github.com/user-attachments/assets/9157b377-9e05-40d7-96ad-7c1a1ad04045) <br>

Hmm Potongan Flag lainnya? 🤔
Mungkin bisa kita gabungkan
picoCTF{f1u3n7_1n_pn9_&_pdf_1f991f77}

Dan..bingo kita dapat Flagnya 👀
<br>
<!----- End Answer ----->
<hr>
<p align="center">
   <img src="/assets/chisato.gif" alt="chisato.gif">
  <hr>
</p> 





