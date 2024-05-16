<div align="center">
  <h1 style="text-align: center;">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1>
  <h4 style="text-align: center;">Dosen Pengampu : Dr. Ferry Astika Saputra, S.T., M.Sc.</h4>
</div>

<p align="center"><img src="../Tugas-Pertama/img/logo.png" alt="logo"></p>

<div align="center">
  <h3>Disusun Oleh:</h3>
  <p align="center">Mayada Azizah 3122500015</p>
  <p align="center">Adinda Zahra Qariru 3122500020</p>
  <p align="center">Masyitha Fahra Nabila 3122500023</p>
</div>

<div align="center">
  <h3>PROGRAM STUDI TEKNIK INFORMATIKA <br>
      POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br>
      TAHUN 2023/2024 <br>
  </h3>
</div>

#

# A. Web Server and Web Browser Architecture

## Web Browser(Client)
<p align="center">
  <img src="../Tugas-Keenam/img/web_browser.png" width="80%" height="auto">
</p>

Gambar di atas menunjukkan arsitektur dari komponen utama sebuah web browser. Komponen-komponen ini bekerja bersama untuk memungkinkan pengguna mengakses dan berinteraksi dengan situs web.

- **User Interface** <br>
  User Interface (UI) adalah bagian dari browser yang langsung berinteraksi dengan pengguna. Ini mencakup elemen seperti bilah alamat, tombol, menu, dan tab. Antarmuka pengguna bertanggung jawab untuk mengambil masukan pengguna dan mengirimkannya ke mesin browser.
- **Browser Engine** <br>
  Browser Engine adalah "otak" dari browser. Ini bertanggung jawab untuk menginterpretasi masukan pengguna dan berkomunikasi dengan komponen browser lainnya. Mesin browser juga menangani tugas seperti mengelola riwayat dan bookmark, dan memproses cookie.
- **Rendering Engine** <br>
- Rendering Engine bertanggung jawab untuk mengambil kode HTML, CSS, dan JavaScript dari server web dan mengubahnya menjadi representasi visual yang dapat ditampilkan di layar pengguna. Mesin pemrosesan juga menangani tugas seperti tata letak dan lukisan.
- **Networking** <br>
  Komponen jaringan bertanggung jawab untuk mengirimkan dan menerima permintaan dari dan ke server web. Ini menggunakan protokol seperti HTTP dan HTTPS untuk mentransfer data
- **JavaScript Interpreter** <br>
  JavaScript Interpreter bertanggung jawab untuk mengeksekusi kode JavaScript yang tertanam dalam halaman web. JavaScript adalah bahasa skrip yang memungkinkan halaman web menjadi lebih interaktif dan dinamis.
- **UI Backend** <br>
  UI Backend bertanggung jawab untuk menggambar elemen antarmuka pengguna di layar. Ini menggunakan pustaka grafis sistem operasi untuk merender antarmuka pengguna.
- **Data Persistence** <br>
  Komponen Data Persistence bertanggung jawab untuk menyimpan data seperti cookie, riwayat, dan bookmark. Data ini disimpan di komputer pengguna sehingga dapat digunakan bahkan ketika browser tidak terbuka.

Selain komponen utama ini, web browser juga mencakup sejumlah komponen lain, seperti security module, plug-in manager, dan search engine. 

Berikut adalah gambaran singkat tentang bagaimana komponen-komponen browser bekerja bersama untuk menampilkan halaman web:
1. Pengguna memasukkan URL ke dalam bilah alamat.
2. Mesin browser mengirim permintaan ke server web untuk halaman web.
3. Server web mengirimkan kode HTML, CSS, dan JavaScript untuk halaman web ke browser.
4. Mesin browser meneruskan kode HTML, CSS, dan JavaScript ke mesin pemrosesan.
5. Mesin pemrosesan mengkonversi kode HTML, CSS, dan JavaScript menjadi representasi visual.
6. Backend antarmuka pengguna menggambar representasi visual di layar.

#

<h2 align="center">Web Server</h2>
<p align="center">
  <img src="../Tugas-Keenam/img/web_server.JPG" width="80%" height="auto">
</p>

Gambar di atas menunjukkan diagram siklus permintaan-respons web. Siklus ini adalah proses dasar di mana browser web dan server web berkomunikasi untuk mengirimkan halaman web kepada pengguna.

- **Client** <br>
  Klien adalah perangkat lunak yang memulai permintaan untuk halaman web. Ini biasanya merupakan browser web, tetapi juga bisa menjadi jenis perangkat lunak lain, seperti aplikasi seluler atau aplikasi desktop.
- **Request** <br>
  Permintaan adalah pesan yang dikirim oleh klien ke server. Ini berisi informasi tentang sumber daya yang diminta, seperti URL, metode HTTP (mis., GET, POST), dan header apa pun.
- **Server** <br>
  Server adalah perangkat lunak yang menerima dan merespons permintaan dari klien. Biasanya terletak di komputer jarak jauh yang terhubung ke internet.
- **Respons** <br>
  Respons adalah pesan yang dikirim kembali oleh server ke klien. Ini berisi sumber daya yang diminta, seperti halaman HTML, gambar, atau objek JSON. Ini juga berisi informasi tentang status permintaan, seperti kode sukses (200) atau kode kesalahan (404).

Langkah-langkah dalam Siklus Permintaan-Respons Web:
1. Pengguna memasukkan URL ke dalam bilah alamat browser web
2. Browser mengurai URL dan mengirim permintaan DNS ke server DNS untuk meresolusi URL ke alamat IP.
3. Server DNS merespons dengan alamat IP dari server web yang menyimpan sumber daya yang diminta.
4. Browser membuka koneksi TCP ke server web menggunakan alamat IP.
5. Browser mengirim permintaan HTTP ke server web melalui koneksi TCP.
6. Server web menerima permintaan HTTP dan memprosesnya.
7. Server web mengirim respons HTTP kembali ke browser melalui koneksi TCP.
8. Browser menerima respons HTTP dan menguraikannya.
9. Browser menampilkan sumber daya yang diminta kepada pengguna.

Tambahan:
- Siklus permintaan-respons web dapat diulang beberapa kali untuk memuat semua sumber daya yang membentuk halaman web.
- Siklus permintaan-respons web dapat digunakan untuk mengirimkan data ke server, seperti saat pengguna mengirimkan formulir.
- Siklus permintaan-respons web dapat digunakan untuk menerima data dari server, seperti saat pengguna memuat halaman web.

#

# B. Containerized Web Server Using Docker
### Apa itu Docker?
Docker adalah platform yang memungkinkan aplikasi berjalan dalam container. Meskipun secara fungsi mirip dengan VirtualBox (VMBox), mereka tidak sama. Docker menjalankan aplikasi, seperti microservices, yang dipecah menjadi bagian-bagian kecil dalam container.

### Perbedaan dengan VMBox
VirtualBox biasanya digunakan dalam lingkungan yang mengikuti prinsip SDLC Agile, di mana setiap VMBox menyimpan satu server. Misalnya, VMBox A bisa menjadi server Nginx, sedangkan VMBox B menjadi server database.

Sebaliknya, dalam SDLC DevOps, aplikasi sering kali dipecah menjadi microservices yang berjalan dalam container. Ini adalah tempat Docker bersinar.

### Contoh Container Engine
Beberapa contoh container engine termasuk Docker, Salad, Ambassador, dan Red Hat OpenShift. Docker adalah salah satu yang paling sering digunakan.

### Menggunakan VirtualBox dengan Containerisasi
Mari kita coba melakukan containerisasi pada VirtualBox.

### Install Docker dan Uninstall Conflicted di Debian vmBox
1. Hapus Docker.io dan dependency bawaan dari DEBIAN!, lakukan seperti command berikut!
   ```bash
   for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
   ```

   <img src="../Tugas-Keenam/img/1.1.png" width="100%" height="auto">

2. Lakukan Update/Upgrade Repository dan tambahkan Docker Official GPG Keys
   ```bash
    sudo apt-get update
    sudo apt-get install ca-certificates curl
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc
   ```

   <img src="../Tugas-Keenam/img/1.2.png" width="100%" height="auto">
   <img src="../Tugas-Keenam/img/1.3.png" width="100%" height="auto">
   <img src="../Tugas-Keenam/img/1.4.png" width="100%" height="auto">

3. Tambahkan Repository Apt Resources
   ```bash
   echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/etc apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
      $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
      sudo apt-get update
   ```
4. Install `DOCKER OFFICIAL PACKAGE`
   ```bash
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```
   <img src="../Tugas-Keenam/img/1.5.png" width="100%" height="auto">
5. Docker Sudah Terpasang :D !, Yuk coba jalankan Hello World
   ```
   sudo docker run hello-world
   ```
   atau
   ```
   sudo docker pull hello-world && docker run hello-world
   ```
   <img src="../Tugas-Keenam/img/1.6.png" width="100%" height="auto">

6. Coba Clone example hasil docker 
   ```
    git clone https://github.com/alfiyansys/docker-examples.git
    docker build -t example .
    docker run -p 3000:80 example
   ```
   <img src="../Tugas-Keenam/img/1.7.png" width="100%" height="auto">
   <img src="../Tugas-Keenam/img/1.8.png" width="100%" height="auto">
7. Open browser http://localhost:3000 dan lihat hasilnya
   
   <img src="../Tugas-Keenam/img/1.9.png" width="100%" height="auto">

# C. Apache2 + Dns Resolver + Docker Uptime Kuma Package
1. Git Clone Uptime Kuma
   ```
    git clone https://github.com/louislam/uptime-kuma.git
    cd uptime-kuma
   ```
   <img src="../Tugas-Keenam/img/2.1.png" width="100%" height="auto">
2. Coba jalankan
   ```
   sudo docker compose up
   sudo docker ps -a
   ```
   <img src="../Tugas-Keenam/img" width="100%" height="auto">
3. Cek pada port berjalan yaitu 3001
   ```
   localhost:3001
   ```
   <img src="../Tugas-Keenam/img" width="100%" height="auto">

### Bagaimana jika menggunakan url monitoring.kelompok10.local saat mengaksesnya?
1. Konfigurasi file `/var/lib/bind/db.kelompok10.local`.
   ```
   sudo sytemctl restart named
   ```
   <img src="../Tugas-Keenam/img" width="100%" height="auto">
2. Install beberapa Package berikut
   ```
   sudo a2enmod
   ```
   Masukkan Package berikut proxy proxy_ajp proxy_http rewrite deflate headers proxy_balancer proxy_connect proxy_html
   <img src="../Tugas-Keenam/img" width="100%" height="auto">
3. Lakukan Konfigurasi pada 
   ```
   Apache2sudo nano /etc/apache2/sites-enabled/000-default.conf
   ```
   <img src="../Tugas-Keenam/img" width="100%" height="auto">
4. Lakukan pengecekan pada web browser, dengan mengetikkan monitoring.`kelompok10.local`
   <img src="../Tugas-Keenam/img" width="100%" height="auto">
