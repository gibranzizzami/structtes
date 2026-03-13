---
title: "result 2"
level: 2
---

# 2 Testing sistem pada archlinux
Berikut merupakan beberapa kernel, desktop, dan game yang akan diuji pada archlinux.

| kernel | Cara instalasi                              | link |
|--------|---------------------------------------------|------|
|  Tkg   | compaile menggunakan makepkg                | https://github.com/Frogging-Family/linux-tkg      |
| xanmod | compaile menggunakan makepkg                | https://aur.archlinux.org/linux-xanmod.git    |
| liquorix | instalasi dari dokumentasi liquorix       | https://liquorix.net/     |
| zen    | menggunakan package manager pacman          | https://archlinux.org/packages/?name=linux-zen  |

Pengujian sistem pada Arch Linux dilakukan dengan menggunakan beberapa varian kernel untuk melihat perbedaan performa dan stabilitas saat menjalankan desktop environment maupun game. Kernel Tkg dan Xanmod dipasang melalui proses kompilasi menggunakan makepkg, masing-masing dari repositori github setiap kernel, sedangkan kernel Liquorix diinstal langsung mengikuti dokumentasi resmi Liquorix. Sementara itu, kernel Zen dipasang paling sederhana melalui package manager pacman dari repositori resmi Arch. Kombinasi berbagai kernel ini memungkinkan pengujian yang lebih menyeluruh untuk melihat bagaimana tiap kernel memengaruhi kinerja sistem pada skenario penggunaan yang berbeda.

| Desktop| Cara instalasi                              | link |
|--------|---------------------------------------------|------|
|  gnome | menggunakan package manager pacman          | https://wiki.archlinux.org/title/GNOME     |
| plasma | menggunakan package manager pacman          | https://wiki.archlinux.org/title/KDE#Plasma   |
| hyprland | menggunakan package manager pacman        | https://wiki.archlinux.org/title/Hyprland |

Pengujian juga mencakup berbagai desktop environment yang dipasang langsung melalui pacman untuk memastikan konsistensi instalasi dan konfigurasi. GNOME digunakan sebagai desktop environment modern berbasis GTK dengan fokus pada kesederhanaan dan workflow terstruktur, Plasma menawarkan lingkungan KDE yang kaya fitur dan sangat dapat dikustomisasi, sementara Hyprland mewakili window manager Wayland yang ringan dan fleksibel, terkenal berkat efek animasi serta pendekatan konfigurasi yang dinamis. Variasi ini membantu melihat bagaimana setiap lingkungan memengaruhi performa dan stabilitas pada sistem operasi archlinux.

| No       | Aplikasi |   
|----------|----------|
| 1.       | Steam          |
| 2.       | Rise of the Tomb Raider |

Pengujian aplikasi difokuskan pada Steam sebagai platform distribusi game utama di archlinux. Di dalam Steam, Rise of the Tomb Raider dipilih sebagai game benchmark karena memiliki opsi grafik yang luas, beban GPU/CPU yang berat, serta tiga skenario pengujian bawaan—Mountain Peak, Syria, dan Geothermal Valley—yang memungkinkan evaluasi performa secara konsisten pada berbagai konfigurasi kernel dan desktop environment di sistem operasi archlinux.

## 2.1 Riset Performa
### 2.1.1 Uji Coba Tahap 1
**plasma**

|kernel|low fps|high fps|ram   |cpu|gpu  |
|------|-------|--------|------|---|-----|
|tkg   |18     | 103    | 6.5gb| 16%|100%|
|lqx   |16     | 51     | 6.1gb| 14%|100%|
|zen   |21     | 75     | 6.2gb| 20%|100%|
|xanmod|18     | 76     | 7.6gb|27% |100%|

Hasil benchmarking pada Plasma menunjukkan bahwa seluruh kernel berada dalam kondisi GPU-bound karena penggunaan GPU selalu 100% sementara CPU relatif rendah. Kernel tkg mencatat FPS tertinggi (hingga 103) sehingga unggul dalam performa puncak, Liquorix paling hemat CPU dan RAM namun memiliki performa FPS terendah, sedangkan XanMod menawarkan performa cukup tinggi tetapi dengan konsumsi CPU dan RAM paling besar, sehingga secara umum Zen paling seimbang, TKG paling kencang, dan Liquorix paling efisien.

**gnome**

|kernel|low fps|high fps|ram  |cpu|gpu |
|------|-------|--------|-----|---|----|
|tkg   |19     |100     |7.3gb|22%|100%|
|lqx   |24     |73      |7.3gb|23%|100%|
|zen   |22     |87      |7.4gb|16%|100%|
|xanmod|20     |90      |7.6gb|23%|100%|

Pada hasil benchmarking ini, semua kernel kembali menunjukkan kondisi GPU-bound karena penggunaan GPU konsisten di 100%, sementara CPU berada di kisaran rendah hingga menengah. Liquorix memiliki FPS relatif lebih rendah, TKG tetap memimpin pada FPS maksimum (100) namun dengan low FPS yang lebih rendah, Zen tampil paling efisien dari sisi CPU dengan performa yang seimbang antara low dan high FPS, sedangkan XanMod memberikan high FPS cukup tinggi tetapi disertai konsumsi CPU dan RAM paling besar, sehingga secara keseluruhan Liquorix terasa paling smooth, TKG paling kencang di puncak performa, dan Zen paling efisien.

**hyprland**

|kernel|low fps|high fps|ram  |cpu|gpu |
|------|-------|--------|-----|---|----|
|tkg   |26     |62      |7.5gb|21%|100%|
|lqx   |21     |52      |7.5gb|20%|100%|
|zen   |22     |79      |7.1gb|26%|100%|
|xanmod|19     |82      |7.4gb|20%|100%|

Seluruh kernel kembali berada pada kondisi GPU-bound karena GPU selalu 100% sementara penggunaan CPU relatif rendah. TKG mencatat low FPS tertinggi (26), Liquorix memiliki performa paling rendah baik di low maupun high FPS, Zen menawarkan kombinasi yang cukup seimbang dengan high FPS tinggi (79) dan penggunaan RAM paling efisien, sedangkan XanMod unggul pada FPS maksimum tertinggi (82) namun dengan low FPS terendah, sehingga TKG terasa paling stabil, XanMod paling kencang di puncak, dan Zen tetap menjadi opsi seimbang.

### 2.1.2 Uji Coba Tahap 2
**plasma**

|kernel|low fps|high fps|ram   |cpu|gpu  |
|------|-------|--------|------|---|-----|
|tkg   |   100    |   180     |   7.7gb   |  45% |   100%  |
|lqx   |    85   |    130    |    8.2gb  | 45%  |  100%   |
|zen   |    50   |    110    |  8.4gb  | 50%  |  100%   |
|xanmod|     90  |    160    |  7.9gb    | 45%  |  100%   |

Hasil ini menunjukkan beban GPU-bound yang kuat (GPU 100% di semua kernel) dengan CPU cukup tinggi di kisaran 45–50%. TKG unggul dalam  performa puncak dengan low FPS tertinggi (100) dan high FPS 180, diikuti XanMod yang juga kuat di high FPS (160) dengan stabilitas cukup baik. Liquorix berada di tengah dengan performa menengah namun penggunaan RAM lebih tinggi, sementara Zen tertinggal cukup jauh pada low FPS (50) meski high FPS masih kompetitif.

**gnome**

|kernel|low fps|high fps|ram   |cpu|gpu  |
|------|-------|--------|------|---|-----|
|tkg   |    90   |      125  |  7.6gb    | 30%  |   100%  |
|lqx   |    100   |    148    |   7.2gb   | 30%  |  100%   |
|zen   |    84   |    138    |   7.6gb   | 39%  |   100%  |
|xanmod|    50   |    120    |  8.1gb    |  40% |  100%   |

Pada pengujian ini, penggunaan CPU lebih rendah (30–40%) namun tetap GPU-bound. Liquorix tampil paling seimbang dengan low FPS tertinggi (100) dan high FPS 148 sekaligus RAM paling efisien, membuatnya terasa paling smooth. TKG dan Zen berada di kelas menengah dengan performa cukup stabil, sedangkan XanMod menunjukkan penurunan signifikan pada low FPS (50) meski high FPS masih relatif baik, sehingga pengalaman cenderung kurang konsisten.

**hyprland**

|kernel|low fps|high fps|ram   |cpu|gpu  |
|------|-------|--------|------|---|-----|
|tkg   |    90   |    120    |   6.2 gb  | 30%  |   100%  |
|lqx   |  90     |   120     |   6.0gb   | 30% |   100%  |
|zen   |    90   |    115    |   6.0gb   | 40%  |   100%  |
|xanmod|    90   |   117     |   6.0gb   | 30%  |   100%  |

Hasil benchmarking ini memperlihatkan performa yang sangat merata antar kernel, dengan semua mencatat low FPS sekitar 90 dan high FPS di kisaran 115–120. Perbedaannya hanya terlihat pada efisiensi resource, di mana Liquorix dan Zen paling hemat RAM, Zen sedikit lebih boros CPU, dan TKG serta XanMod berada di tengah. Secara keseluruhan, tidak ada kernel yang benar-benar dominan karena performanya nyaris identik dan kemungkinan dibatasi penuh oleh GPU.

### 2.2 Riset stabilitas
**plasma**

| kernel | indikasi  | scene |waktu |
|--------|-----------------|----------|------|
| tkg    | Lagging | efek banjir dan runtuhan goa dalam satu adegan |0.34.31 |
| tkg    | Lagging | upgrade senjata karakter | 1.16.50 |

Benchmarking pada kernel tkg menunjukkan bahwa performanya masih mengalami lagging pada dua skenario berbeda: pertama saat adegan kompleks yang memadukan efek banjir dan runtuhan goa dan kedua ketika proses upgrade senjata karakter. Kedua titik uji ini memperlihatkan bahwa kernel belum menangani beban grafis secara optimal, baik pada adegan berat maupun momen dengan efek visual menengah.

| kernel | indikasi  | scene | waktu |
|--------|-----------------|----------|------|
| lqx    | lagging | spam gerakan | 0.21.27 |
| lqx    | lagging | efek ledakan berulang kali dalam satu adegan | 0.36.01 |
| lqx    | lagging | turun dari ketinggian dalam keadaan hujan lebat | 2.12.53 |

Benchmarking pada kernel lqx memperlihatkan bahwa indikasi lagging muncul konsisten di tiga titik uji: saat karakter melakukan spam gerakan, ketika terjadi efek ledakan berulang dalam satu adegan, serta pada momen turun dari ketinggian di tengah hujan lebat. Ketiga skenario ini menggambarkan bahwa kernel LQX belum mampu menangani beban efek visual intens maupun aktivitas karakter yang cepat secara optimal.



| kernel | indikasi  | kode | 
|--------|-----------------|----------|
| lqx    | Crashed with signal | SIGSEGV(11) | 

<img src="/image/Lqx-crash.jpg" width="300" height="200" alt="very high">
Gambar 4.2.2.1 : crash lqx 1
<img src="/image/Lqx-cras-2.jpg" width="300" height="200" alt="very high">
Gambar 4.2.2.2 : crash lqx2

Kernel lqx menunjukkan kegagalan serius berupa crash dengan sinyal SIGSEGV(11), yang terlihat jelas pada kedua tangkapan layar saat game menampilkan pesan kesalahan terkait segmentation fault dan dialog laporan crash. Pada gambar pertama terlihat bahwa aplikasi berhenti secara tiba-tiba sebelum masuk gameplay, sementara gambar kedua memperlihatkan jendela pelaporan resmi dari game yang mengonfirmasi bahwa proses eksekusi dihentikan akibat error internal. Kedua bukti visual ini menegaskan bahwa kernel LQX tidak stabil dalam menjalankan game tersebut dan mengalami kegagalan memori yang menyebabkan crash konsisten.

| kernel | aplikasi             | erorr    |
|--------|----------------------|----------|
| xanmod | steam                | rusak dalam tataran grafis dengan menampilkan garis garis pada aplikasi         |      


<img src="/image/Xanmod-trouble.jpg" width="300" height="200" alt="very high">
Gambar 4.2.2.2 : crash xanmod      

Kernel Xanmod menunjukkan masalah pada aplikasi Steam berupa kerusakan visual yang tampak jelas melalui munculnya pola garis-garis pada elemen antarmuka aplikasi. Gangguan grafis ini terlihat langsung pada tangkapan layar, di mana tampilan Steam menjadi terdistorsi dan tidak stabil, menandakan bahwa kernel tersebut mengalami kendala dalam menangani render grafis pada tingkat aplikasi. Hal ini mengindikasikan adanya ketidakcocokan atau kegagalan pemrosesan visual yang mempengaruhi kejelasan dan fungsionalitas antarmuka Steam.


**gnome**

| kernel | indikasi        | scene |waktu |
|--------|-----------------|----------|------|
| tkg   |  lagging |  cut scene        | 01:22:21  |
| tkg    | lagging | edit baju karakter         | 02:15:10     |
| tkg    | lagging | cut scene         |  02:15:36     |
| tkg    | lagging | combat scene         | 02:23:07     |
| tkg    | lagging | combat scene         |02:30:06.      |

Benchmarking pada kernel tkg menunjukkan masalah berupa lagging di berbagai momen gameplay, mulai dari cut-scene, proses pengeditan baju karakter, hingga cut-scene lainnya pada. Penurunan performa juga muncul pada dua titik combat scene yang umumnya membutuhkan respons grafis dan sistem yang lebih cepat. Pola ini menegaskan bahwa kernel tkg belum mampu mempertahankan stabilitas frame dalam situasi sinematik maupun pertempuran intens.

| kernel | indikasi        | scene |waktu |
|--------|-----------------|----------|------|
| lqx    | lagging | edit baju karakter   |     00:40:43 |
| lqx    | lagging | saat gerakan double jump   | 00:59:13     |
| lqx    | lagging | lompat di obstacle |  01:09:34    |
| lqx    | lagging | perang dengan banyak musuh        | 01:20:09     |

Benchmarking pada kernel lqx memperlihatkan munculnya lagging di berbagai aktivitas gameplay, mulai dari proses mengedit baju karakter, gerakan double jump, hingga lompatan di area obstacle. Penurunan performa juga terlihat saat memasuki adegan perang dengan banyak musuh yang umumnya membutuhkan pemrosesan grafis dan respons sistem yang lebih intens. Pola ini menunjukkan bahwa kernel lqx belum optimal dalam menangani aksi cepat maupun adegan dengan beban visual tinggi.

| kernel | indikasi        | scene |waktu |
|--------|-----------------|----------|------|
| zen | lagging | cut scene         | 00:22:09     |
| zen | lagging | render pemandangan         | 00:30:06     |

Benchmarking pada kernel zen menunjukkan adanya lagging pada dua momen penting: saat pemutaran cut-scene dalam waktu 22 menit bermain dan ketika sistem melakukan render pemandangan. Kejadian lagging pertama dan kedua memiliki rentang waktu 7 menit 57 detik , penurunan performa menandakan bahwa kernel zen belum sepenuhnya optimal dalam menangani adegan sinematik maupun proses rendering lingkungan.

