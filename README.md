# 🧩 Data Integration Pipeline (Node.js + pnpm + SQLite)

## 📌 Overview

Project ini merupakan implementasi pipeline data berdasarkan studi kasus di tugas Integrasi & Migrasi Sistem pertemuan-6:

* Input: `master_data.csv`
* Output: data terstruktur melalui beberapa tahap:

  * Part 1: SQLite
  * Part 2: JSON
  * Part 3: XML
  * Re-integrate
  * Data Cleaning

---

## 🏗️ Project Structure

```
data-integration/
│
├── apps/
│   ├── part1-sql/
│   ├── part2-json/
│   ├── part3-xml/
│   ├── re-integrate/
│   └── data-cleaning/
│
├── data/
│   ├── raw/
│   │   └── master_data.csv
│   └── output/ #output hasil data cleaning masuk sini
│
├── package.json
├── pnpm-workspace.yaml
└── README.md
```

---

## ⚙️ Tech Stack

* Node.js (v24)
* pnpm (workspace monorepo)
* Built-in SQLite (`node:sqlite`)
* csv-parser
* bisa aja nambah--

---

## 🚀 Installation

### 1. Clone Repository

```bash
git clone <repo-url>
cd data-integration
```

### 2. Install Dependencies

```bash
pnpm install
```

### 3. Run Part 1 for the first time

```bash
pnpm start1
```


## 📂 Data Mentah

Lokasi file:

```
data/raw/master_data.csv
```

Kolom:

* id
* product_name
* price
* stock
* vendor
* date_added

---

## 🧠 Part 1 – SQL (SQLite)

### 🎯 Objective

Menyimpan 3 kolom utama ke database:

* id
* product_name
* price

---

### ⚙️ Workflow

```
CSV → Read Stream → Transform → Insert → SQLite
```

---

### 📄 Penjelasan File

#### `apps/part1-sql/index.js`

| Section      | Fungsi                     |
| ------------ | -------------------------- |
| Path Setup   | Menentukan lokasi CSV & DB |
| Init DB      | Membuat database SQLite    |
| Create Table | Membuat tabel `products`   |
| Read CSV     | Streaming data             |
| Insert       | Simpan ke database         |

---

### 🗄️ Output

File database:

```
apps/part1-sql/db/products.db
```

---

## ⚠️ Catatan Penting

* Menggunakan `node:sqlite` untuk menghindari error native binding
* CSV tidak diubah (raw data tetap immutable)
* Insert menggunakan `INSERT OR REPLACE`

---

## 🔜 Next Steps (Not Implemented Yet)

### Part 2 – JSON

* Export 3 kolom operasional
* Ubah format tanggal (Unix / MM-DD-YYYY)

### Part 3 – XML

* Simpan sisa data
* Kosongkan 5 nilai vendor

### Re-integrate

* Gabungkan semua data menjadi satu tabel

### Data Cleaning

* Isi vendor kosong → `"Unknown Vendor"`
* Format tanggal → `YYYY-MM-DD`

---

## 🤝 Contribution (Fork & PR)

### Step:

1. Fork repository ini

2. Clone fork kamu

3. Buat branch baru:

   ```bash
   git checkout -b feature/part2-json
   ```

4. Implement feature

5. Commit:

   ```bash
   git commit -m "Add Part 2 JSON transformation"
   ```

6. Push:

   ```bash
   git push origin feature/part2-json
   ```

7. Buat Pull Request

---

## 🧠 Design Principles

* Modular architecture (per part)
* Separation of concern
* Reusable packages
* Data pipeline approach

---
