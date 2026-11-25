# Dasbor UMP, UMSP & UMK Indonesia 2027

Dasbor statis satu halaman untuk membandingkan Upah Minimum Provinsi (UMP), Upah Minimum Sektoral Provinsi (UMSP), dan Upah Minimum Kabupaten/Kota (UMK) tahun 2027.

## Sumber Data

Seluruh dokumen sumber (berkas salinan SK Gubernur) dihimpun dari unggahan akun Threads **[@hrdbacot](https://www.threads.com/@hrdbacot)**. Repositori ini hanya merapikan dan menyajikan ulang isi dokumen tersebut; bukan penetapan resmi dan bukan milik pemilik akun.

Data pada dasbor diambil dari 18 berkas SK Gubernur. Untuk data resmi, selalu rujuk salinan SK dari pemerintah provinsi terkait.

## Cakupan Data

| Item | Jumlah |
| --- | --- |
| Baris data (provinsi / provinsi + UMK) | 25 |
| Provinsi | 22 |
| Provinsi dengan entri UMSP/UMK | 14 |
| Entri sektor / KBLI | 213 |

Tiga provinsi memiliki dua baris terpisah (UMP dan rincian UMK): Jawa Barat, Jawa Tengah, dan Jawa Timur.

## Struktur

```
index.html          # dasbor lengkap: data inline (const PROVINCES), UI, grafik Chart.js
jabar_umk_2027.json # snapshot data mentah UMK Jawa Barat 2027
```

Data provinsi berada di dalam `index.html` pada `const PROVINCES` — tidak ada proses build dan tidak ada berkas data eksternal yang dimuat saat runtime.

## Menjalankan

Buka langsung `index.html` di peramban, atau sajikan lewat server lokal:

```bash
python3 -m http.server 8000
# lalu buka http://localhost:8000/index.html
```

Grafik memakai Chart.js dari CDN, sehingga koneksi internet diperlukan untuk menampilkan grafik.

## Fitur

- Tabel interaktif dengan rincian SK dan sektor per provinsi
- Grafik perbandingan UMP vs UMSP tertinggi, serta mode premi UMSP (%)
- Filter wilayah, status UMSP, pencarian, dan pengurutan
- Indeks lintas provinsi untuk kode KBLI dan kelompok sektor

## Catatan

Angka dibulatkan sesuai salinan SK. Beberapa SK mencantumkan nilai UMK yang sama dengan UMP bagi kabupaten/kota yang tidak menetapkan UMK sendiri.
