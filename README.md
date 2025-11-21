# Fundamental Web Crawling & Web Scraping  
### Pendekatan Praktis untuk Pengumpulan Data Digital  

_Disusun untuk mahasiswa Statistika & Sains Data / pemula yang ingin masuk dunia data digital._

---

## 1. Dari Survei ke Data Web: Evolusi Metode Pengumpulan Data di Era Digital

Di mata kuliah **Metode Pengumpulan Data**, kita biasanya belajar:

- Survei (kuesioner)
- Sensus
- Rancangan percobaan / eksperimen

### 1.1 Lalu Jejak Digital / Web Data Itu Masuk Kategori Apa?

<img width="800" height="500" alt="image" src="https://github.com/user-attachments/assets/2b5cfffd-3cbd-4c85-8d3e-72ecf396b81c" />


> Nah, begitu masuk era digital, muncul satu kategori baru yang sering disebut:
> “Found Data” / “Data Web / Jejak Digital”
(data yang sudah ada, bukan kita yang minta orang isi atau kita yang ngatur eksperimen)

**Contohnya:**

- Orang buka lowongan di JobStreet → nulis posisi yang dibutuhkan, deskripsi pekerjaan, dan kualifikasinya.

- Orang belanja di e-commerce → meninggalkan harga, rating, ulasan.

- Pengguna medsos nge-post, like, komen, share.

**Ciri-cirinya:**

- Data tidak muncul karena kita melakukan survei atau eksperimen,
tapi sebagai “produk samping” aktivitas digital sehari-hari.

- Kita sebagai peneliti datang belakangan:
tugas kita bukan “membuat data”, tapi “memanen data yang sudah terbentuk”.

**Dari sisi metode:**

- Secara spirit, ini mirip observational study: kita mengamati perilaku yang sudah terjadi, tidak memanipulasi.

- Tapi proses pengumpulannya berbeda: bukan wawancara/kuesioner, melainkan:

   - Web Crawling → menyusuri halaman & mengumpulkan URL

   - Web Scraping → mengekstrak isi halaman (judul, harga, teks, dll.)

**Maka, di era digital, perubahan besar yang terjadi:**

> **Banyak data sudah tersedia di internet.**  
> Bukan lagi “bagaimana cara kita mengumpulkan data dari responden?”,  
> tapi “bagaimana cara kita mengambil data yang sudah ada di web dengan rapi dan etis?”

**Contoh sumber data web:**

- Lowongan kerja (JobStreet, LinkedIn, Kalibrr)
- Harga & review produk (Tokopedia, Shopee, Bukalapak)
- Berita (Kompas, Detik, Tempo)
- Media sosial (X/Twitter, Instagram, TikTok)
- Data properti, hotel, penerbangan, dll.

Di sinilah **Web Crawling** dan **Web Scraping** jadi “senjata baru” untuk pengumpulan data digital.

---

## 2. Crawling & Scraping: Ibarat Mencari dan Mengintip Isi Rumah

<img width="500" height="700" alt="image" src="https://github.com/user-attachments/assets/01dd329b-378a-4e12-bc9e-c3b5a10ab068" />
<img width="500" height="700" alt="image" src="https://github.com/user-attachments/assets/9f360e3b-6cad-48d6-9674-060df8afcf3f" />

Bayangkan internet seperti **satu kota besar** penuh rumah.

- **Rumah** = halaman web (web page)  
- **Alamat rumah** = URL (link)

### 2.1 Crawling = Mencari Alamat Rumah

Kamu keliling komplek:

- Jalan dari gang ke gang  
- Mencatat alamat rumah yang menarik  

Dalam konteks web:

- Crawler mulai dari satu halaman (seed URL)  
- Mencari link di halaman tersebut  
- Lanjut ke halaman berikutnya  
- Mengumpulkan **daftar URL** yang relevan  

> **Crawling fokus pada: menemukan & mengumpulkan URL.**

---

### 2.2 Scraping = Masuk ke Rumah & Cek Isinya

Setelah kamu punya daftar alamat rumah:

- Kamu datang ke rumah tertentu  
- Masuk dan lihat: jumlah kamar, luas, cat, isi rumah, dll.  

Dalam konteks web:

- Buka URL tertentu  
- Baca struktur HTML-nya  
- Ambil informasi spesifik:
  - judul (title)  
  - harga  
  - nama perusahaan  
  - deskripsi  
  - tanggal, dll.

> **Scraping fokus pada: mengekstrak isi halaman (data).**

---

## 3. Web Crawling & Scraping

### 3.1 Web Crawling

**Definisi singkat:**  
Proses mengunjungi banyak halaman web secara otomatis untuk mengumpulkan daftar URL.

Konsep dasar:

- **Seed URL** → titik mulai (misal halaman 1 JobStreet)  
- **Link extraction** → mendeteksi `<a href="...">` di halaman  
- **Frontier** → antrian URL yang akan dikunjungi  
- **Depth / breadth** → seberapa dalam/luas kita menjelajah  

Contoh:  
Crawl halaman 1, klik “Selanjutnya”, pindah ke halaman 2, dan seterusnya.

---

### 3.2 Web Scraping

**Definisi singkat:**  
Proses mengekstrak data terstruktur dari halaman web.

Biasanya melibatkan:

1. Mengirim request (HTTP) atau membuka browser otomatis  
2. Mengambil HTML (source code halaman)  
3. Mem–parsing HTML menjadi struktur yang bisa dibaca  
4. Menemukan elemen tertentu (pakai CSS Selector / XPath)  
5. Mengambil teks/atribut yang dibutuhkan  

Contoh:  
Dari satu halaman detail lowongan:

- Posisi: “Data Scientist”  
- Perusahaan: “PT Data Jaya”  
- Lokasi: “Jakarta”  
- Jenis Pekerjaan: “Full-Time”  
- Deskripsi: paragraf panjang  

---

## 4. Anatomi Halaman Web: HTML, DOM, dan CSS

Sebelum bisa scraping, kita harus paham “bentuk fisik” halaman web.

### 4.1 HTML (HyperText Markup Language)

HTML adalah **struktur dasar** halaman web.

Contoh sederhana:

```html
<html>
  <body>
    <h1>Judul Halaman</h1>
    <p>Ini paragraf pertama.</p>

    <div class="job-card">
      <h2>Data Scientist</h2>
      <span class="company">PT Data Jaya</span>
      <span class="location">Jakarta</span>
      <a href="/detail-job-123">Lihat detail</a>
    </div>
  </body>
</html>
````

Elemen penting:

* `<h1>, <h2>` : heading / judul
* `<p>` : paragraf
* `<div>` : container / blok
* `<span>` : teks kecil (inline)
* `<a href="...">` : link (selalu punya atribut `href`)

---

### 4.2 DOM (Document Object Model)

Browser membaca HTML lalu membentuk **pohon (tree)** yang disebut DOM.

Sketsa sederhana:

```text
HTML
 └── BODY
      ├── H1 ("Judul Halaman")
      └── DIV class="job-card"
            ├── H2 ("Data Scientist")
            ├── SPAN class="company" ("PT Data Jaya")
            ├── SPAN class="location" ("Jakarta")
            └── A href="/detail-job-123"
```

Scraper bekerja dengan **menjelajah pohon DOM** ini:
“Cari DIV dengan class `job-card`, lalu ambil H2 di dalamnya, dll.”

---

### 4.3 CSS Selector: Cara Menunjuk Elemen Tertentu

CSS Selector adalah **“alamat”** untuk menunjuk elemen HTML tertentu.

Contoh umum:

* `h1` → semua elemen `<h1>`
* `.job-card` → semua elemen dengan `class="job-card"`
* `span.company` → `<span>` dengan class `"company"`
* `div.job-card a` → `<a>` di dalam `<div class="job-card">`

**Di JobStreet**, hasil inspeksi (Inspect Element) sering terlihat seperti:

```css
a[data-automation="job-list-item-link-overlay"]     /* link overlay per job card */
h1[data-automation="job-detail-title"]              /* judul lowongan */
span[data-automation="advertiser-name"]             /* nama perusahaan */
span[data-automation="job-detail-location"]         /* lokasi */
div[data-automation="jobAdDetails"]                 /* deskripsi lengkap */
```

Itulah selector yang nanti dipakai di kode Python/R.

---

## 5. Workflow End-to-End Web Scraping

Secara praktis, alurnya biasanya seperti ini:

1. **Tentukan tujuan data**
   Misal: peta skill & lowongan data science dari JobStreet.

2. **Pilih website target**
   Contoh: `https://id.jobstreet.com/id/data-science-jobs` dengan keyword “data science”.

3. **Inspect Element**
   Gunakan fitur Inspect di browser untuk:

   * melihat struktur HTML
   * menemukan elemen dan CSS selector yang konsisten

4. **Crawling (opsional)**
   Kalau datanya tersebar di banyak halaman:

   * klik “Selanjutnya” / pagination
   * kumpulkan semua URL detail job.

5. **Scraping**
   Untuk tiap URL, ambil:

   * posisi
   * perusahaan
   * lokasi
   * jenis pekerjaan
   * deskripsi

6. **Simpan data**
   CSV / Excel / database.

7. **Analisis**
   Pakai R, Python, Power BI, dll.

8. **Automasi (lanjutan)**
   Cron job, scheduler, Airflow, atau AI agent.

---

## 6. Studi Kasus: JobStreet – Lowongan Data Science

Target URL contoh:

```text
https://id.jobstreet.com/id/data-science-jobs
```

Informasi yang ingin diambil (per lowongan):

* `Posisi`
* `Perusahaan`
* `Lokasi`
* `Bidang` / kategori
* `Jenis Pekerjaan` (Full-time, Contract, dll.)
* `Deskripsi` (narasi panjang)

Selector utama (hasil inspect):

```css
a[data-automation="job-list-item-link-overlay"]   /* link ke halaman detail */
h1[data-automation="job-detail-title"]            /* judul posisi */
span[data-automation="advertiser-name"]           /* nama perusahaan */
span[data-automation="job-detail-location"]       /* lokasi */
div[data-automation="jobAdDetails"]               /* deskripsi pekerjaan */
```

---

## 7. Implementasi dengan Python (Selenium + webdriver_manager)

Untuk halaman yang **pakai JavaScript untuk render konten**, gunakan Selenium.

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
import pandas as pd
import time
import os

# === SETUP DRIVER ===
save_path = "jobstreet_data_science_with_deskripsi.csv"

options = webdriver.ChromeOptions()
options.add_argument("--start-maximized")

#driver = webdriver.Chrome(service=Service(driver_path), options=options)
driver= webdriver.Chrome(
    service=Service(ChromeDriverManager().install()),
    options=options
)

# === MULAI SCRAPING MULTI PAGE ===
url = "https://id.jobstreet.com/id/data-science-jobs"
driver.get(url)
time.sleep(10)

all_data = []
visited_links = set()
page = 1
max_pages = 10  # batas halaman maksimum

while True:
    print(f"\n📄 Scraping halaman {page}...")

    # Scroll agar konten muncul semua
    for _ in range(3):
        driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        time.sleep(1.5)

    job_cards = driver.find_elements(By.CSS_SELECTOR, 'a[data-automation="job-list-item-link-overlay"]')
    job_links = [card.get_attribute('href') for card in job_cards if card.get_attribute('href') not in visited_links]

    if not job_links:
        print("🚫 Tidak ada link job baru.")
        break

    for i, link in enumerate(job_links):
        visited_links.add(link)
        print(f"   🔗 Job {i+1}: {link}")
        try:
            driver.execute_script("window.open('');")
            driver.switch_to.window(driver.window_handles[1])
            driver.get(link)
            time.sleep(4)

            def get(selector):
                try:
                    return driver.find_element(By.CSS_SELECTOR, selector).text
                except:
                    return "(Tidak Ada)"

            posisi = get('h1[data-automation="job-detail-title"]')
            perusahaan = get('span[data-automation="advertiser-name"]')
            lokasi = get('span[data-automation="job-detail-location"]')
            bidang = get('span[data-automation="job-detail-classifications"]')
            tipe = get('span[data-automation="job-detail-work-type"]')

            try:
                raw = driver.find_element(By.CSS_SELECTOR, 'div[data-automation="jobAdDetails"]').text
                deskripsi = " ".join(raw.strip().splitlines())
            except:
                deskripsi = "(Tidak Ada Deskripsi)"

            all_data.append({
                "Posisi": posisi,
                "Perusahaan": perusahaan,
                "Lokasi": lokasi,
                "Bidang": bidang,
                "Jenis Pekerjaan": tipe,
                "Deskripsi": deskripsi
            })

            print(f"      ✅ {posisi} | {perusahaan}")

        except Exception as e:
            print(f"      ⚠️ Error saat buka detail: {e}")

        finally:
            driver.close()
            driver.switch_to.window(driver.window_handles[0])
            time.sleep(1)

    # PAGINATION: klik tombol "Selanjutnya"
    try:
        next_btn = driver.find_element(By.XPATH, '//a[contains(., "Selanjutnya")]')
        next_btn.click()
        page += 1
        time.sleep(6)
        if page > max_pages:
            print("✅ Mencapai batas maksimum halaman.")
            break
    except:
        print("🚫 Tidak menemukan tombol Selanjutnya.")
        break

driver.quit()

# SIMPAN KE EXCEL
df = pd.DataFrame(all_data)
df.to_excel(save_path, index=False)

print(f"\n📁 {len(df)} job disimpan ke:\n{os.path.abspath(save_path)}")
```

## 8. Instant / No-Code Scraper

Jika tidak ingin menulis kode, ada **instant scraper / no-code tools** seperti:

* Data Miner (Chrome extension)
* Web Scraper (Chrome extension)
* Apify
* Bardeen

**Workflow umum:**

1. Buka halaman yang ingin di-scrape (misal daftar lowongan JobStreet)
2. Klik extension / tool
3. Pilih elemen (judul job, perusahaan, lokasi)
4. Preview hasil
5. Export ke CSV / Excel
6. Analisis di R / Python

Tools seperti ini bagus untuk:

* Eksplorasi cepat
* Non-programmer
* Proof of concept

---

## 9. AI-Assisted Scraping (Bonus Konsep)

AI bisa membantu:

* Menulis kode scraping dari deskripsi natural language
* Memahami HTML & mengubahnya jadi JSON terstruktur
* Mengontrol browser (agent) untuk jelajah & mengambil data

Contoh prompt (konseptual):

> “Dari HTML halaman ini, ambil semua judul lowongan, nama perusahaan, dan lokasi, lalu buat dalam format tabel (CSV).”

AI tidak menggantikan kebutuhan paham konsep, tapi **mempercepat pekerjaan teknis**.

---

## 10. Etika & Legalitas Web Scraping

Sebelum scraping, pertimbangkan:

* **robots.txt**: apakah situs mengizinkan scraping?
* **Terms of Service**: apa batasannya?
* Jangan mengambil data pribadi atau sensitif
* Jangan membebani server (batasi request / pakai jeda)
* Gunakan data untuk tujuan riset / edukasi dengan tanggung jawab

---


---

## 11. Penutup

Web Crawling dan Web Scraping adalah **metode pengumpulan data digital** yang melengkapi survei, sensus, dan eksperimen.

Untuk mahasiswa Statistika & Sains Data:

* Ini adalah cara untuk **membangun dataset sendiri** dari dunia nyata.
* Dengan kombinasi **konsep yang kuat + kemampuan teknis (R/Python/No-Code/AI)**, kamu bisa mengubah website apa pun menjadi sumber data riset yang kaya.

Selamat bereksperimen dan eksplorasi. 🚀

```
