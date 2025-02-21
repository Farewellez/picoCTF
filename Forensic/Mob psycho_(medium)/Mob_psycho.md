<!----- Start Main ----->
<body>
  <header>
    <h2>💢 Mob Psycho 💢</h2>
    <table border= "1" cellspacing="5" align="left">    
      <tr>
        <td><strong>Medium</strong></td>
        <td><strong>Forensics</strong></td>
        <td><strong>picoCTF 2024</strong></td>
        <td><strong>browser_webshell_solveable</strong></td>
        <td><strong>apk</strong></td>
      </tr>
    </table>
  </header>
  <main>
      <br>
      <h2></h2>
      <h3 align="left">Author: NGIRIMANA SCHADRACK</h3>
      <h3>Description</h3>
        <p align="justify">Can you handle APKs?
Download the android apk <a href="https://artifacts.picoctf.net/c_titan/142/mobpsycho.apk">here</a>.</p>
      <h2></h2>
  </main>
</body>
<!----- End Main ----->
<!----- Start Hint ----->

## 👀 Hint 👀
> [!NOTE]
> Hint 1: Did you know you can unzip APK files? <br>
> Hint 2: Now you have the whole host of shell tools for searching these files.

# Konteks dan Asumsi🤔
> - Jadi kita diminta untuk mengulik sebuah APK files dari author <br>
> - Sudah jelas sepertinya flag nya ada di dalam file-file di dalam file APK yang di arsip

# Tujuan 🚩
> - Mengulik file-file di dalam APK untuk mencari flag nya

# LOOK AT ME 😠
> [!WARNING]
> SEBELUM MENGERJAKAN PASTIKAN SUDAH MEMBACA FILE README_FIRST.md DI REPOSITORY INI <br>
> AKU ANGGAP KETIKA MEMBACA JAWABAN KALIAN SEMUA SUDAH TAU ISTILAH ATAU HAL-HAL YANG TERKAIT DENGAN SOLVING CHALLENGENYA

<!----- End Hint ----->
<h3 align="center">😉ANSWER😉</h3>
<hr>
<p align="center">
  <img src="/assets/rikka_cdkgs.gif" alt="rikka.gif">
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
Kita coba cek dulu menggunakan perintah <em>file</em> untuk mencari tahu jenis file apa ini <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ file mobpsycho.apk
mobpsycho.apk: Zip archive data, at least v1.0 to extract, compression method=store
```
### Step 3
Karena file nya berupa <em>Zip archive data</em> sesuai dengan hint 1. Maka bisa langsung kita unzip <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ unzip mobpsycho.apk
```
Coba kita cek isi directory kita sekarang
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ ls
AndroidManifest.xml  classes2.dex  classes3.dex  classes.dex  META-INF  mobpsycho.apk  res  resources.arsc
```
Ada lumayan banyak file yang ter ekstrak. Kita bisa melihat spesifik semua file dengan:
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ file *

AndroidManifest.xml: Android binary XML
classes2.dex:        Dalvik dex file version 037
classes3.dex:        Dalvik dex file version 037
classes.dex:         Dalvik dex file version 037
META-INF:            directory
mobpsycho.apk:       Zip archive data, at least v1.0 to extract, compression method=store
res:                 directory
resources.arsc:      Android package resource table (ARSC), 5899 string(s), utf8
```
Coba kita kesampingkan dulu file yang ada dan coba fokus pada pemeriksaan menyeluruh. Coba gunakan _tree_ untuk saat ini <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ tree
```
Akan muncul banyak cabang dari directory dan semua file juga. Di akhir kita bisa melihat total 47 directories, 727 files. <br>
### Step 4
Kita coba persempit lagi pencarian kita. Asumsikan nama file yang kita cari adalah flag.txt <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ find . -iname '*flag*'
./res/color/flag.txt
```
Kita menemukan hasil di path ./res/color, coba kita cek dengan _tree_ path apa sebenarnya ini. <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ tree ./res/color
./res/color
├── abc_background_cache_hint_selector_material_dark.xml
├── abc_background_cache_hint_selector_material_light.xml
├── abc_hint_foreground_material_dark.xml
├── abc_hint_foreground_material_light.xml
├── abc_primary_text_disable_only_material_dark.xml
├── abc_primary_text_disable_only_material_light.xml
├── abc_primary_text_material_dark.xml
├── abc_primary_text_material_light.xml
├── abc_search_url_text.xml
├── abc_secondary_text_material_dark.xml
├── abc_secondary_text_material_light.xml
├── checkbox_themeable_attribute_color.xml
├── design_box_stroke_color.xml
├── design_error.xml
├── design_icon_tint.xml
├── flag.txt
├── m3_appbar_overlay_color.xml
├── m3_assist_chip_icon_tint_color.xml
├── m3_assist_chip_stroke_color.xml
├── m3_button_background_color_selector.xml
├── m3_button_foreground_color_selector.xml
├── m3_button_outline_color_selector.xml
├── m3_button_ripple_color_selector.xml
├── m3_button_ripple_color.xml
├── m3_calendar_item_disabled_text.xml
├── m3_calendar_item_stroke_color.xml
├── m3_card_foreground_color.xml
├── m3_card_ripple_color.xml
├── m3_card_stroke_color.xml
├── m3_chip_assist_text_color.xml
├── m3_chip_background_color.xml
├── m3_chip_ripple_color.xml
├── m3_chip_stroke_color.xml
├── m3_chip_text_color.xml
├── m3_dark_default_color_primary_text.xml
├── m3_dark_default_color_secondary_text.xml
├── m3_dark_highlighted_text.xml
├── m3_dark_hint_foreground.xml
├── m3_dark_primary_text_disable_only.xml
├── m3_default_color_primary_text.xml
├── m3_default_color_secondary_text.xml
├── m3_elevated_chip_background_color.xml
├── m3_highlighted_text.xml
├── m3_hint_foreground.xml
├── m3_navigation_bar_item_with_indicator_icon_tint.xml
├── m3_navigation_bar_item_with_indicator_label_tint.xml
├── m3_navigation_bar_ripple_color_selector.xml
├── m3_navigation_item_background_color.xml
├── m3_navigation_item_icon_tint.xml
├── m3_navigation_item_text_color.xml
├── m3_popupmenu_overlay_color.xml
├── m3_primary_text_disable_only.xml
├── m3_radiobutton_ripple_tint.xml
├── m3_selection_control_button_tint.xml
├── m3_selection_control_ripple_color_selector.xml
├── m3_slider_active_track_color.xml
├── m3_slider_halo_color.xml
├── m3_slider_inactive_track_color.xml
├── m3_slider_thumb_color.xml
├── m3_switch_thumb_tint.xml
├── m3_switch_track_tint.xml
├── m3_tabs_icon_color.xml
├── m3_tabs_ripple_color.xml
├── m3_text_button_background_color_selector.xml
├── m3_text_button_foreground_color_selector.xml
├── m3_text_button_ripple_color_selector.xml
├── m3_textfield_filled_background_color.xml
├── m3_textfield_indicator_text_color.xml
├── m3_textfield_input_text_color.xml
├── m3_textfield_label_color.xml
├── m3_textfield_stroke_color.xml
├── m3_timepicker_button_background_color.xml
├── m3_timepicker_button_ripple_color.xml
├── m3_timepicker_button_text_color.xml
├── m3_timepicker_clock_text_color.xml
├── m3_timepicker_display_background_color.xml
├── m3_timepicker_display_ripple_color.xml
├── m3_timepicker_display_stroke_color.xml
├── m3_timepicker_display_text_color.xml
├── m3_timepicker_secondary_text_button_ripple_color.xml
├── m3_timepicker_secondary_text_button_text_color.xml
├── m3_tonal_button_ripple_color_selector.xml
├── material_cursor_color.xml
├── material_divider_color.xml
├── material_on_background_disabled.xml
├── material_on_background_emphasis_high_type.xml
├── material_on_background_emphasis_medium.xml
├── material_on_primary_disabled.xml
├── material_on_primary_emphasis_high_type.xml
├── material_on_primary_emphasis_medium.xml
├── material_on_surface_disabled.xml
├── material_on_surface_emphasis_high_type.xml
├── material_on_surface_emphasis_medium.xml
├── material_on_surface_stroke.xml
├── material_slider_active_tick_marks_color.xml
├── material_slider_active_track_color.xml
├── material_slider_halo_color.xml
├── material_slider_inactive_tick_marks_color.xml
├── material_slider_inactive_track_color.xml
├── material_slider_thumb_color.xml
├── material_timepicker_button_background.xml
├── material_timepicker_button_stroke.xml
├── material_timepicker_clockface.xml
├── material_timepicker_clock_text_color.xml
├── material_timepicker_modebutton_tint.xml
├── mtrl_btn_bg_color_selector.xml
├── mtrl_btn_ripple_color.xml
├── mtrl_btn_stroke_color_selector.xml
├── mtrl_btn_text_btn_bg_color_selector.xml
├── mtrl_btn_text_btn_ripple_color.xml
├── mtrl_btn_text_color_selector.xml
├── mtrl_calendar_item_stroke_color.xml
├── mtrl_calendar_selected_range.xml
├── mtrl_card_view_foreground.xml
├── mtrl_card_view_ripple.xml
├── mtrl_chip_background_color.xml
├── mtrl_chip_close_icon_tint.xml
├── mtrl_chip_surface_color.xml
├── mtrl_chip_text_color.xml
├── mtrl_choice_chip_background_color.xml
├── mtrl_choice_chip_ripple_color.xml
├── mtrl_choice_chip_text_color.xml
├── mtrl_error.xml
├── mtrl_fab_bg_color_selector.xml
├── mtrl_fab_icon_text_color_selector.xml
├── mtrl_fab_ripple_color.xml
├── mtrl_filled_background_color.xml
├── mtrl_filled_icon_tint.xml
├── mtrl_filled_stroke_color.xml
├── mtrl_indicator_text_color.xml
├── mtrl_navigation_bar_colored_item_tint.xml
├── mtrl_navigation_bar_colored_ripple_color.xml
├── mtrl_navigation_bar_item_tint.xml
├── mtrl_navigation_bar_ripple_color.xml
├── mtrl_navigation_item_background_color.xml
├── mtrl_navigation_item_icon_tint.xml
├── mtrl_navigation_item_text_color.xml
├── mtrl_on_primary_text_btn_text_color_selector.xml
├── mtrl_on_surface_ripple_color.xml
├── mtrl_outlined_icon_tint.xml
├── mtrl_outlined_stroke_color.xml
├── mtrl_popupmenu_overlay_color.xml
├── mtrl_tabs_colored_ripple_color.xml
├── mtrl_tabs_icon_color_selector_colored.xml
├── mtrl_tabs_icon_color_selector.xml
├── mtrl_tabs_legacy_text_color_selector.xml
├── mtrl_tabs_ripple_color.xml
├── mtrl_text_btn_text_color_selector.xml
├── radiobutton_themeable_attribute_color.xml
├── switch_thumb_material_dark.xml
├── switch_thumb_material_light.xml
├── test_mtrl_calendar_day_selected.xml
└── test_mtrl_calendar_day.xml
```
Dan yah benar saja, hampir semua isinya memiliki ekstensi xml dan hanya satu dengan ektensi _.txt_ yaitu _flag.txt_. Coba kita cek isi dari flag.txt <br>
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ cat ./res/color/flag.txt
7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f37343664666133397d
```
Hmm jika kamu perhatikan, isi nya adalah sebuah hexadecimal. Kita coba decode isi nya menggunakan beberapa cara alternatif. <br>
### Step 5
> [!NOTE]
> Aku berikan beberapa cara yang aku tahu agar kalian bisa memilih sendiri cara yang paling kalian suka untuk mendecode hexadecimal

## Menggunakan python3
Disini aku menggunakan script python3 via terminal untuk langsung mendecode hexadecimal tadi
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ python3
>>> flag = "7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f37343664666133397d"
>>> result = bytes.fromhex(flag).decode("utf-8")
>>> print(result)
picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_746dfa39}
```
setiap selesai menulis syntax di promt ">>>" bisa kalian enter

## Menggunakan xxd
Karena flag saat ini di encode ke format hexadecimal, maka kita bisa juga menggunakan hexdump untuk mendecode nya
```
┌──(wallnut_㉿LAPTOP-B49Q3K5D)-[~/PicoCTF]
└─$ cat ./res/color/flag.txt | xxd -r -p
picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_746dfa39}
```
Kita membaca terlebih dahulu flag.txt menggunakan _cat_ dan melakukan pipe ke xxd -r -p untuk mendecode nya

## Menggunakan tools online | cyberchef
Untuk tools online kalian bisa menggunakan cyberchef dan input string hexadecimal yang kita dapat tadi. Pilih yang from hex dan lakukan decode dengan pilih Bake <br>
![Screenshot 2025-02-21 094610](https://github.com/user-attachments/assets/b1297160-ff91-46b8-9ff4-6086b64178c6) <br>
Outputnya akan terlihat seperti itu

### Hurray 🚩
## picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_746dfa39}
<!----- End Answer ----->
<hr>
<p align="center">
   <img src="/assets/uhul.gif" alt="uhul.gif">
  <hr>
</p> 
