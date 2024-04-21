<h1 align="center">LAPORAN WORKSHOP ADMINISTRASI JARINGAN</h1>

<h3 align="center">Dosen Pembimbing: Dr. Ferry Astika Saputra ST, M.Sc</h3>

<p align="center"><img src="../Tugas-Pertama/img/logo.png" alt="logo"></p>

<div align="center">
  <h3>Disusun Oleh:</h3>
  <p align="center">Adinda Zahra Qariru 3122500020</p>
</div>

<div align="center">
  <h3>PROGRAM STUDI TEKNIK INFORMATIKA <br>
      POLITEKNIK ELEKTRONIKA NEGERI SURABAYA <br>
      TAHUN 2023/2024 <br>
  </h3>
</div>

##

### Note
Pastikan BIND9 pada praktikum sebelumnya sudah terinstall dan terkonfigurasi sesuai dengan custom domain kelompok.

**Kembalikan debian dalam keadaan Network NAT dan IP DNS Automatic agar terkoneksi dengan internet.** <br>
// <img src="../Tugas-UTS" width="70%" height="auto"><br>

- Atur server email pada konfigurasi zona agar dapat diakses melalui ```mail.kelompok10.local.``` <br>
    <img src="../Tugas-UTS/img/1.1.png" width="70%" height="auto"><br>
    <img src="../Tugas-UTS/img/1.2.png" width="70%" height="auto"><br>
    <img src="../Tugas-UTS/img/1.3.png" width="70%" height="auto"><br>
    <img src="../Tugas-UTS/img/1.4.png" width="70%" height="auto"><br>
- Selanjutnya, gunakan perintah ```nslookup``` untuk melakukan pengecekan.
  <img src="../Tugas-UTS/img/1.5.png" width="70%" height="auto"><br>

#

### A. Setup NTP ( Network Time Protocol )

1. Mulailah dengan menginstal paket systemd-timesyncd 
   ```
   sudo apt install systemd-timesyncd
   sudo timedatectl set-timezone Asia/Jakarta
   ```
   <img src="../Tugas-UTS/img/2.1.png" width="70%" height="auto"><br>
2. Ubahlah zona waktu menjadi Asia/Jakarta dan sesuaikan RTC dengan UTC dan aktifkan NTP untuk sinkronisasi waktu.
   ```
   sudo timedatectl set-local-rtc false
   sudo timedatectl set-ntp true
   ```
   <img src="../Tugas-UTS/img/2.2.png" width="70%" height="auto"><br>
3. Konfigurasikan file ```timesync.d``` untuk menggunakan pool NTP terdekat guna meminimalkan delay.
   ```
   sudo nano /etc/systemd/timesyncd.conf
   ```
   <img src="../Tugas-UTS/img/2.3.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/2.4.png" width="70%" height="auto"><br>
4. Lakukan restart layanan dan periksa statusnya. 
   ```
   sudo systemctl restart systemd-timesyncd
   sudo systemctl status systemd-timesyncd
   ```
   <img src="../Tugas-UTS/img/2.5.png" width="70%" height="auto"><br>
   Pastikan tanggal sudah terupdate!
   ```
   sudo timedatectl
   ```
   <img src="../Tugas-UTS/img/2.6.png" width="70%" height="auto"><br>

#

### B. Instalasi dan Konfirgurasi Apache2

1. Instal Apache2
   ```
   sudo apt -y install apache2
   ```
   <img src="../Tugas-UTS/img/3.1.png" width="70%" height="auto"><br>
2. Konfigurasi Apache2 dengan mengubah pengaturan ServerToken menjadi "Prod".
   ```
   sudo nano /etc/apache2/conf-enabled/security.conf
   ```
   <img src="../Tugas-UTS/img/3.2.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/3.3.png" width="70%" height="auto"><br>
3. Tambahkan direktori yang dapat diakses.
   ```
   sudo nano /etc/apache2/mods-enabled/dir.conf
   ```
   <img src="../Tugas-UTS/img/3.4.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/3.5.png" width="70%" height="auto"><br>
4. Atur Servernamenya.
   ```
   sudo nano /etc/apache2/apache2.conf
   ```
   <img src="../Tugas-UTS/img/3.6.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/3.7.png" width="70%" height="auto"><br>
5. Pastikan email webmaster telah ditetapkan.
   ```
   /etc/apache2/sites-enabled/000-default.conf
   ```
   <img src="../Tugas-UTS/img/3.8.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/3.9.png" width="70%" height="auto"><br>
6. Lakukan reload layanan Apache2.
   ```
   sudo systemctl reload apache2
   ```
   <img src="../Tugas-UTS/img/3.10.png" width="70%" height="auto"><br>
7. Periksa apakah webserver berjalan dengan membuka browser. Tapi sebelumnya ubah dulu IP dan DNS sesuai dengan yang sudah diset sebelumnya!
   <img src="../Tugas-UTS/img/3.11.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/3.12.png" width="70%" height="auto"><br>
   **Apache berhasil diakses!**

#

### C. Instalasi PHP 8.2

1. Instal PHP 8.2
   ```
   sudo apt -y install php8.2 php8.2-mbstring php-pear
   ```
   <img src="../Tugas-UTS/img/4.1.png" width="70%" height="auto"><br>
2. periksa apakah instalasi berhasil.
   ```
   php -v
   ```
   <img src="../Tugas-UTS/img/4.2.png" width="70%" height="auto"><br>
3. Buat file PHP untuk menguji apakah PHP berjalan dengan baik seperti di bawah ini
   <img src="../Tugas-UTS/img/4.3.png" width="70%" height="auto"><br>
4. Jalankan dengan command berikut
   ```
   php test.php | head
   ```
   <img src="../Tugas-UTS/img/4.4.png" width="70%" height="auto"><br>

#

### D. Instalasi dan Konfigurasi PHP-FM

1. Instal PHP FM 
   ```
   sudo apt -y install php-fpm
   ```
   <img src="../Tugas-UTS/img/5.1.png" width="70%" height="auto"><br>
2. Konfigurasikan file Apache untuk PHP-FM.
   ```
   sudo nano /etc/apache2/sites-available/default-ssl.conf
   ```
   <img src="../Tugas-UTS/img/5.2.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/5.3.png" width="70%" height="auto"><br>
3. Jalankan ulang layanan.<br>
   <img src="../Tugas-UTS/img/5.4.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/5.5.png" width="70%" height="auto"><br>
4. Uji coba webserver dengan membuat ```file info.php```.
   <img src="../Tugas-UTS/img/5.6.png" width="70%" height="auto"><br>
5. Cek pada web, jangan lupa kembalikan ke IP dan DNS manual untuk mengakses internet.<br>
   <img src="../Tugas-UTS/img/5.7.png" width="70%" height="auto"><br>
   Berhasil!

#

### E. Instalasi Database server ( Mariadb-Server )

1. Instal paket Mariadb-Server 
   <img src="../Tugas-UTS/img/6.1.png" width="70%" height="auto"><br>
2. Pastikan pengaturan charset sesuai.
   ```
   nano /etc/mysql/mariadb.conf.d/50-server.cnf
   ```
   <img src="../Tugas-UTS/img/6.2.png" width="70%" height="auto"><br>
3. Lakukan restart ariadb lalu konfigurasi mariadb
   ```
   sudo mysql_secure_installation
   ```
   <img src="../Tugas-UTS/img/6.3.png" width="70%" height="auto"><br>
   Instalasi patter: pastikan sama sehingga langkah tetap sama.
   ```
   Enter current password for root (enter for none): Tekan Enter
   Switch to unix_socket authentication [Y/n] n
   Change the root password? [Y/n] n
   Remove anonymous users? [Y/n] y
   Disallow root login remotely? [Y/n] y
   Remove test database and access to it? [Y/n] y
   Reload privilege tables now? [Y/n] y
   ```
4. Tes konek ke mariadb dengan masuk ke dalam MySQL dan cek akses pengguna.
   <img src="../Tugas-UTS/img/6.4.png" width="70%" height="auto"><br>
   <img src="../Tugas-UTS/img/6.5.png" width="70%" height="auto"><br>
5. Pastikan instalasi MySQL berhasil dengan membuat database dan tabel dummy.
   <img src="../Tugas-UTS/img/6.6.png" width="70%" height="auto"><br>
6. Lihat semua database<br>
   <img src="../Tugas-UTS/img/6.7.png" width="70%" height="auto"><br>
7. Berhasil dan Database mariadb sudah terinstall.<br>
   <img src="../Tugas-UTS/img/6.8.png" width="70%" height="auto"><br>

#

### F. Instalasi dan Konfigurasi Email System POSTFIX (SMTP Server)

1. Instal Postfix. 
   ```
   sudo nano apt -y install postfix sasl2-bin
   ```
2. Konfigurasikan manual.<br>
   <img src="../Tugas-UTS/img/7.1.png" width="90%" height="auto"><br>
3. Salin file konfigurasi<br>
   <img src="../Tugas-UTS/img/7.2.png" width="70%" height="auto"><br>
4. Ubah beberapa pengaturan sebagai berikut.<br>
   <img src="../Tugas-UTS/img/7.3.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.4.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.5.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.6.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.7.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.8.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.9.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.10.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.11.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.12.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/7.13.png" width="90%" height="auto"><br>
5. Tambahkan konfigurasi anti-spam.
   <img src="../Tugas-UTS/img/7.14.png" width="70%" height="auto"><br>

#

### G. Instalasi DOVECOT (IMAP POP3)

1. Instal paket Dovecot.
   ```
   sudo  apt -y install dovecot-core dovecot-pop3d dovecot-imapd
   ```
2. Ubah listen IP yang digunakan.<br>
   <img src="../Tugas-UTS/img/8.2.png" width="90%" height="auto"><br>
3. Lakukan konfigurasi file auth dan mail.
   <img src="../Tugas-UTS/img/8.3.png" width="90%" height="auto"><br>
   <img src="../Tugas-UTS/img/8.4.png" width="90%" height="auto"><br>
4. Tambahkan mode 0666 dan user serta group pada file master.
   <img src="../Tugas-UTS/img/8.5.png" width="90%" height="auto"><br>
5. Restart layanan dan periksa statusnya di netstat
   <img src="../Tugas-UTS/img/8.6.png" width="90%" height="auto"><br>
6. Setelah beberapa paket terinstall seperti imap, pop3 kita akan coba melakukan test connection ke postfix
   ```
   telnet mail.kelompok10.local
   ```
   <img src="../Tugas-UTS/img/8.7.png" width="70%" height="auto"><br>

#

### H. DEBIAN EVOLUTION

1. Buat user dan lakukan konfigurasi identitas, penerimaan, dan pengiriman email (di saya yaitu ```user```)<br>
   - Identity<br>
   <img src="../Tugas-UTS/img/9.1.png" width="70%" height="auto"><br>
   - Receive<br>
   <img src="../Tugas-UTS/img/9.2.png" width="70%" height="auto"><br>
   - Sending<br>
   <img src="../Tugas-UTS/img/9.3.png" width="70%" height="auto"><br>
2. ```user``` telah dibuat sekarang buat user lagi (dummy) untuk saya, dind dengan langkah yang sama. adduser terlebih dahulu.
   <img src="../Tugas-UTS/img/9.4.png" width="90%" height="auto"><br>
3. Kirim email dan periksa kotak masuk.
   <img src="../Tugas-UTS/img/9.5.png" width="90%" height="auto"><br>

#

### I. ROUNDCUBE

1. Lakukan konfigurasi untuk pengguna Roundcube, tambahkan pada tabel db user<br>
   <img src="../Tugas-UTS/img/10.1.png" width="70%" height="auto"><br>
2. Berikan akses penuh.<br>
   <img src="../Tugas-UTS/img/10.2.png" width="70%" height="auto"><br>
   
   Loading<br>
   <img src="../Tugas-UTS/img/10.3.png" width="70%" height="auto"><br>
3. Instal Roundcube.
   ```
   sudo apt-get install roundcube -y
   ```
   <img src="../Tugas-UTS/img/10.4.png" width="70%" height="auto"><br>
   
   klik YES<br>
   <img src="../Tugas-UTS/img/10.5.png" width="70%" height="auto"><br>
   
   Masukkan password tadi (123)
   <img src="../Tugas-UTS/img/10.6.png" width="70%" height="auto"><br>
4. Lakukan config pada file ```/etc/roundcube/config.inc.php```. lakukan seperti di bawah ini!<br>
   <img src="../Tugas-UTS/img/10.7.png" width="70%" height="auto"><br>
5. Kemudian konfigurasi file apache pada roundcube, uncomment line 3 dan hapus public_html path<br>
   <img src="../Tugas-UTS/img/10.8.png" width="70%" height="auto"><br>
6. Pada ```apache2 default conf``` tambahkan Servername untuk mail dan document root menjadi roundcube ```sudo nano /etc/apache2/sites-available/000-default.conf```, Servername ```mail.kelompok10.local``` DocumentRoot /var/lib/roundcube/<br>
   <img src="../Tugas-UTS/img/10.9.png" width="70%" height="auto"><br>
7. Jalankan seperti berikut ini!
   <img src="../Tugas-UTS/img/10.10.png" width="70%" height="auto"><br>

   OK<br>
   <img src="../Tugas-UTS/img/10.11.png" width="70%" height="auto"><br>

   en_Us<br>
   <img src="../Tugas-UTS/img/10.12.png" width="30%" height="auto"><br>

   Install ulang => YES<br>
   <img src="../Tugas-UTS/img/10.13.png" width="70%" height="auto"><br>

   Pilih TCP/IP<br>
   <img src="../Tugas-UTS/img/10.14.png" width="70%" height="auto"><br>

   Pilih localhost<br>
   <img src="../Tugas-UTS/img/10.15.png" width="70%" height="auto"><br>

   Pilih PORT: 3306<br>
   <img src="../Tugas-UTS/img/10.16.png" width="70%" height="auto"><br>

   Pilih native password<br>
   <img src="../Tugas-UTS/img/10.17.png" width="70%" height="auto"><br>

   Database name default<br>
   <img src="../Tugas-UTS/img/10.18.png" width="70%" height="auto"><br>

   Username default<br>
   <img src="../Tugas-UTS/img/10.19.png" width="70%" height="auto"><br>

   Password 123<br>
   <img src="../Tugas-UTS/img/10.20.png" width="70%" height="auto"><br>

   Admin root<br>
   <img src="../Tugas-UTS/img/10.21.png" width="70%" height="auto"><br>

   Pilih Webserver apache2<br>
   <img src="../Tugas-UTS/img/10.22.png" width="70%" height="auto"><br>

   **Restrart and keep currently installed!**
8.  Roundcude berhasil terinstall
   <img src="../Tugas-UTS/img/11.1.png" width="90%" height="auto"><br>
9.  Login sebagai user debian kita ```user > user`` dan coba kirim email.
   <img src="../Tugas-UTS/img/11.2.png" width="90%" height="auto"><br>
   Coba kirim email
   <img src="../Tugas-UTS/img/11.3.png" width="90%" height="auto"><br>
