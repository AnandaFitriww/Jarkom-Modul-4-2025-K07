# Jarkom-Modul-4-2025-K07

## ANGGOTA 
<table>
  <thead>
    <tr>
      <th>No</th>
      <th>Nama</th>
      <th>NRP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Zein Muhammad Hasan</td>
      <td>5027241035</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Ananda Fitri Wibowo</td>
      <td>5027241057</td>
    </tr>
  </tbody>
</table>

## I. Pendahuluan
Laporan ini mendokumentasikan proses perancangan pengalamatan IP (IP Addressing) untuk topologi jaringan skala besar yang terdiri dari 27 jaringan LAN dan 13 koneksi WAN point-to-point. Metode yang digunakan adalah VLSM untuk efisiensi alokasi host dan CIDR untuk efisiensi tabel routing.

## II. Perhitungan VLSM (Variable Length Subnet Masking)
Data Perhitungan Lengkap: https://docs.google.com/spreadsheets/d/19BcGHHzaCNgCsvFIZGAw7s7gztEtc9sSoSEpSUK6tpo/edit?usp=sharing

### 1. Metodologi Alokasi
Agar alokasi IP efisien dan mencegah tumpang tindih (overlapping), diterapkan pengurutan kebutuhan host dari yang terbesar hingga terkecil.
- Total Subnet: 40 Subnet (A1 s/d A27 untuk LAN, B1 s/d B13 untuk Link WAN).
- Rentang Alokasi: Dimulai dari 10.67.0.0 hingga 10.67.18.235.

### 2. Hasil ALokasi IP (Ringkasan)
Berikut adalah sampel alokasi IP dari subnet terbesar hingga terkecil yang telah dihitung:
| Nama Subnet  | Kebutuhan |    Prefix   | Network ID   | Range IP   |
|--------------|-----------|-------------|--------------|------------|
| A1 (Mirdain)  | 628 Host |   /22   | 10.67.0.0    |  10.67.0.1 - 10.67.3.254 |
| A2 (Silmaris) | 381 Host |   /23   | 10.67.4.0    |  10.67.4.1 - 10.67.5.254 |
| A5 (Khazad)   | 252 Host |   /24   | 10.67.10.0   |  10.67.10.1 - 10.67.10.254 |
| A21 (Arnor)   | 10 Host  |   /28   | 10.67.18.128 |  10.67.18.129 - 10.67.18.142 |
| B1 (Link WAN) | 2 Host   |   /30   | 10.67.18.184 |  10.67.18.185 - 10.67.18.186 |
Data lengkap tersedia pada file Spreadsheet terlampir.

## III. Perhitungan CIDR (Classless Inter-Domain Routing)
Data Perhitungan Lengkap: https://docs.google.com/spreadsheets/d/1Eoyg_HkfIUjbm6FVtaNv0XtGPRjNFO6o/edit?usp=drive_link&ouid=100777610193669444745&rtpof=true&sd=true

Untuk menyederhanakan tabel routing pada router utama, kami melakukan penggabungan rute (route summarization) secara bertingkat (Hierarki A > B > C > D > E).

### 1. Hierarki Penggabungan
- Level 1 (Subnet A > B): Subnet-subnet kecil digabung menjadi blok yang lebih besar.
  Contoh: A1 (/23) + A2 (/26) digabung menjadi B1 (/22).
- Level 2 (Subnet B > C): Blok B digabung menjadi blok C.
  Contoh: Blok-blok B digabung menjadi C1 (/21) dan C3 (/20).
- Level 3 (Subnet C > D): Blok C digabung menjadi blok D.
  Contoh: D1 (/20) mencakup range 10.67.0.0 s/d 10.67.15.255.
