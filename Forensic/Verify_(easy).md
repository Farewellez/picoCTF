<!----- Start Main ----->
<body>
  <header>
    <h2>🔎 Verify 🔎</h2>
    <table border= "1" cellspacing="5" align="left">    
      <tr>
        <td><strong>Easy</strong></td>
        <td><strong>Forensics</strong></td>
        <td><strong>picoCTF 2024</strong></td>
        <td><strong>grep</strong></td>
        <td><strong>browser_webshell_solveable</strong></td>
        <td><strong>checksum</strong></td>
      </tr>
    </table>
  </header>
  <main>
      <br>
      <h2></h2>
      <h3 align="left">Author: Jeffery John</h3>
      <h3>Description</h3>
        <p align="justify">People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.Additional details will be available after launching your challenge instance.</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: Checksum let you tell if a file is complete and from the original distributor. If the hash doesn't match, it's a different file. <br>
> Hint 2: You can create a SHA checksum of a file with sha256sum \<file> or all files in a directory with sha256sum \<directory>/*. <br>
> Hint 3: Remember you can pipe the output of one command to another with |. Try practicing with the 'First Grep' challenge if you're stuck!
<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/alice.gif" alt="alice.gif">
  <hr>
</p> 

<!----- Start Answer ----->
Jadi pertama kalian perlu launch instance nya agar mendapat server soalnya. Tiap port pemain, mungkin akan berbeda
> [!TIP]
> <b>ssh -p 57291 ctf-player@rhea.picoctf.net <br>
  Using the password 6abf4a82. Accept the fingerprint with yes, and ls once connected to begin. Remember, in a shell, passwords are hidden! <br>
> - Checksum: b09c99c555e2b39a7e97849181e8996bc6a62501f0149c32447d8e65e205d6d2 <br>
> - To decrypt the file once you've verified the hash, run ./decrypt.sh files/<file>.</b>

Launch ssh server yang sudah diberikan oleh soal. Kalian bebas, menggunakan apa untuk mengakses nya. Disini aku menggunakan wsl
> [!TIP]
> <b>┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[/mnt/c/Users/ZAFARELL/CTF/picoCTF/Forensic/easy/Verify]
└─$ ssh -p 57291 ctf-player@rhea.picoctf.net</b>


> [!IMPORTANT]
> ![Screenshot 2025-02-12 232437](https://github.com/user-attachments/assets/de690fde-4097-47fc-8d31-25c1d6f3f813)



Jika sudah kalian akan diminta konfirmasi apakah ingin lanjut dengan kondisi 
> [!TIP]
> <b>"Are you sure you want to continue connecting (yes/no/[fingerprint])?"</b> <br>

Disini kalian bisa lanjut dengan <b>"yes"</b> lalu masukkan password yang kalian dapat sebelumnya. <br>
<b>Disini password yang aku dapat adalah 6abf4a82</b> <br>

Setelah berhasil login ke server kalian bisa type ls, untuk cek isi dari direktori saat ini
> [!TIP]
> <b>ctf-player@pico-chall$ ls<br>
checksum.txt  decrypt.sh  files </b>

> [!IMPORTANT]
> ![Screenshot 2025-02-12 232537](https://github.com/user-attachments/assets/efb3931c-a3b4-492f-853c-17050515d2f0)


Disini ada beberapa file dan folder yang bisa kita akses<br>
> [!NOTE]
> - checksum.txt: Merupakan file dengan ekstensi .txt yang bisa kita baca
> - decrypt.sh: Merupakan shell script atau sederhananya sebuah program yang di tulis dengan tujuan dijalankan di terminal
> - files: files disini merupakan sebuah direktori yang kemungkinan berisi <strong>Flag</strong> yang ingin kita cari

Kita bisa memulai dengan cek isi dari checksum.txt
> [!TIP]
> <b>ctf-player@pico-chall$ cat checksum.txt <br>
b09c99c555e2b39a7e97849181e8996bc6a62501f0149c32447d8e65e205d6d2</b>

> [!IMPORTANT]
> ![Screenshot 2025-02-12 232808](https://github.com/user-attachments/assets/7016dbe8-cb9b-481c-b7a7-9e2797bbe6bc)

Disini terihat bahwa isi dari file .txt ini berisi hash dari suatu file tertentu <br>
Dari <strong>Deskripsi</strong> kita tau bahwa author menyebutkan "I'm going to provide the SHA-256 hash and a decrypt" <br>
Disini dapat disimpulkan kalau hash dari checksum.txt berasal dari fungsi SHA-256 dan decrypt.sh merupakan script executable untuk mendekripsi file yang cocok dengan hash tersebut

> [!TIP]
> ctf-player@pico-chall$ sha256sum files/*
> 914eb674c3c0625ac3d0d229d3df05e3a1e74815dbc5ec1ed72ff7f07569a6b9  files/0QFPjDGl
c4cacb221571c4f813be56056fc0f00a244a9664ed3a7223b6bc543433984c44  files/0wKPM7Vk
b52f46a38b72d550c15366ba1345d304449a4f46b2011c57b0858e959d9ea46b  files/10tptfxh
2a077817bad18787db2847c600e722b90b50ad529e3eb6734065d94f9be4c9c3  files/119zBIIk
d8a154873237bf0fccdffb14702a5692d94da03fd99a503203f1a1c1f24cfb50  files/19TB8pZ3
c2f20f736137221306d268b72c9127822b7e9c1051bbced2a3497dd44655aa43  files/1OUKnRjk
fca036d2d86d3989ce5015b6b11647befb394ec1eb8072ecf4c9ce5972921bb0  files/1P1L0ygq
> ......

Ternyata Banyak sekali isi folder files dengan hash yang beragam <br>
Olehkarena itu kita coba cari hash yang cocok
> [!TIP]
> ctf-player@pico-chall$ sha256sum files/* | grep -i "b09c99c555e2b39a7e97849181e8996bc6a62501f0149c32447d8e65e205d6d2" <br>
b09c99c555e2b39a7e97849181e8996bc6a62501f0149c32447d8e65e205d6d2  files/451fd69b

Gunakan "|" untuk menyalurkan output dari "sha256sum files/*" lalu kita proses dengan "grep -i" <br>
> [!NOTE]
> grep -i: Digunakan untuk mengambil suatu string dan "-i" digunakan untuk ignore/mengabaikan kapital atau detail dari string yang kita cari

Output yang dihasilkan ternyata ada file dengan hash yang sesuai dengan isi hash checksum.txt
> [!IMPORTANT]
> ![Screenshot 2025-02-12 234825](https://github.com/user-attachments/assets/12a68e8c-158b-457b-9633-ad411b548fc6)

Dari hasil file yang cocok dengan hash sebelumnya, kita lanjut untuk mendekripsi file tersebut dengan script "decrypt.sh" <br>
dan Boom! Flagnya keluar!👀
<!----- End Answer ----->
<hr>
<p align="center">
  <img src="/assets/akane.gif" alt="akane.gif">
  <hr>
</p> 
