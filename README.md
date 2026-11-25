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

Seluruh angka cakupan pada UI (jumlah provinsi, entri, SK UMP, provinsi ber-UMSP/UMK, dan entri sektor) dihitung saat runtime dari `const PROVINCES` melalui `computeDataStats()`. Tidak ada angka cakupan yang ditulis manual di markup, kecuali `<title>` dan meta description yang harus tetap statis untuk crawler.

## Struktur

```
index.html          # dasbor lengkap: data inline (const PROVINCES), UI, grafik Chart.js
jabar_umk_2027.json # snapshot data mentah UMK Jawa Barat 2027
robots.txt          # aturan crawler + rujukan sitemap
sitemap.xml         # sitemap satu URL
og-image.png        # gambar pratinjau 1200x630 untuk Open Graph / Twitter Card
```

Data provinsi berada di dalam `index.html` pada `const PROVINCES` — tidak ada proses build dan tidak ada berkas data eksternal yang dimuat saat runtime.

## SEO

`index.html` memuat metadata berikut:

- `<title>`, `meta description`, `meta keywords`, `meta robots` (`index, follow, max-image-preview:large`), `author`, `theme-color`
- `link rel="canonical"` dan favicon SVG inline
- Open Graph (`og:*`) dan Twitter Card (`summary_large_image`) dengan `og-image.png`
- JSON-LD `WebPage`, `WebSite`, dan `Dataset` (cakupan spasial Indonesia, temporal 2027, kredit sumber data)

URL kanonis dan sitemap memakai `https://muhfaris.github.io/ump-indonesia/` (GitHub Pages). Jika dasbor dipasang di domain lain, ubah `canonical`, `og:url`, `og:image`, `twitter:image`, `sitemap.xml`, dan `robots.txt` secara bersamaan.

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
