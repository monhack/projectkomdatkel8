# Aplikasi Web "Sourcegraph"

## Sekilas Tentang Sourcegraph

**Sourcegraph** adalah alat pencarian kode yang memungkinkan para pengembang mencari dan menjelajahi semua kode organisasi di web dengan integrasi ke dalam perangkat para pengembangnya.

Apa yang dilakukan Sourcegraph?
Fitur utama **Sourcegraph** adalah:
- Pencarian kode: cepat, terkini, dan terukur, dengan dukungan regexp pada cabang apa pun atau melakukan tanpa penundaan pengindeksan (dan pencarian berbeda)
- Intelijen kode: lompat-ke-definisi, temukan referensi, dan fitur penjelajahan kode IDE-like yang cerdas lainnya di cabang, komit, atau PR / review kode
- Instalasi mandiri yang mudah dan aman (kode Anda tidak pernah menyentuh server sourcegraph)
- Integrasi dengan host kode, alat peninjau kode, editor, browser web, dll.


## Instalasi

Prasyarat, apa saja yang harus diinstal sebelumnya.
  - Virtual Box
  - Ubuntu Server

Langkah instalasi dalam CLI.
1. Setup The Repository
  - Install packages to allow apt to use a repository over HTTPS:
      ```
      $ sudo apt-get install \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg-agent \
      software-properties-common
      ```
  - Add Docker’s official GPG key:
      ```
      $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
      ```
  - Set up the stable repository
      ```
      $ sudo add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) \
      stable"
      ```
2. Install Docker
  - Install the latest version of Docker CE and containerd
  ```
  $ sudo apt-get install docker-ce docker-ce-cli containerd.io
  ```
  - Verify that Docker CE is installed correctly by running the hello-world image
  ```
  $ sudo docker run hello-world
  ```
3. Install Source Graph
  a. docker run 
  ```
  --publish 7080:7080 --publish 2633:2633 --rm
  --volume ~/.sourcegraph/config:/etc/sourcegraph 
  --volume ~/.sourcegraph/data:/var/opt/sourcegraph 
  sourcegraph/server:3.1.1
  ```

## Konfigurasi (opsional)

Menambahkan External Service

Memilih External Service yang ingin ditambahkan
misal.Github
Display Name : Github
Kind : GitHub

Kunjungi Menu Setting pada Akun Github yang ingin dihubungkan
-Pilih Developer Settings
-Pilih Personal Access Token
-Generate New Token
-Isi Token Desciption, misal : Sourcegraph
-Klik Generate Token
-Copy dan paste token yang sudah digenerate ke sourcegraph
-Klik Setting pada Salah satu External Service
-Pilih Projek apa saja yang boleh di-search oleh Sourcegraph

<!---
Setting server tambahan yang diperlukan untuk meningkatkan fungsi dan kinerja aplikasi, misalnya:
- batas upload file
- batas memori
- dll

Plugin untuk fungsi tambahan
- login dengan Google/Facebook
- editor Markdown
- dll


##  Maintenance (opsional)

Setting tambahan untuk maintenance secara periodik, misalnya:
- buat backup database tiap pekan
- hapus direktori sampah tiap hari
- dll


## Otomatisasi (opsional)

Skrip shell untuk otomatisasi instalasi, konfigurasi, dan maintenance.
-->



## Cara Pemakaian

### Fitur pencarian kode
Contoh pemakaian:

Buka sourcegraph.com dan sign in terlebih dahulu. Akan langsung dialihkan ke sourcegraph.com/search.
![Fitur search pada Sourcegraph](etc/image2.png)

Misal akan mencari **repogroup:sample "not found"** maka akan keluar hasil pencarian berikut. 
![Hasil search](etc/image3.png)

Untuk menggunakan repository milik tim sendiri saat menggunakan fitur pencarian, harap menginstal terlebih dahulu seperti diatas.
Baca [dokumentasi pencarian kode](https://docs.sourcegraph.com/user/search) untuk informasi lebih lanjut.

### Fitur intelijen kode
Sourcegraph menyediakan intelijen kode pada:
1. File kode pada UI web Sourcegraph
![Intelijen kode](etc/image4.png)

2. Diffs pada alat peninjau kode, menggunakan [integrasi](https://docs.sourcegraph.com/integration)
![Intelijen kode](etc/image5.png)

3. File kode pada host kode milik sendiri, menggunakan [integrasi](https://docs.sourcegraph.com/integration)
![Intelijen kode](etc/image6.png)

Baca [dokumentasi intelijen kode](https://docs.sourcegraph.com/user/code_intelligence) untuk informasi lebih lanjut.



## Pembahasan

Aplikasi seperti Github tidak memiliki fitur search untuk mencari kode tertentu, hanya fitur search file, sehingga developer mungkin akan membutuhkan banyak waktu hanya untuk mencari kode tersebut. Sesuai dengan tujuan utama dibuatnya aplikasi sourcegraph &mdash; alat pencarian kode yang memungkinkan para pengembang mencari dan menjelajahi semua kode organisasi di web &mdash; sourcegraph juga dapat menghindari pencarian manual tersebut yang membutuhkan banyak waktu.



## Referensi

1. [About Source Graph](https://docs.sourcegraph.com/user) - Source Graph
2. [How to Install Source Graph](https://docs.sourcegraph.com/admin/install/docker) - Source Graph
3. [About Docker](https://docs.docker.com/install/) - Docker
4. [How to Install Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/) - Docker
