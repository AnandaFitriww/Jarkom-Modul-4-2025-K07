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
| B1 (Link WAN) | 2 Host   |   /30   | 10.67.18.184 |  10.67.18.184	10.67.18.185 - 10.67.18.186 |
