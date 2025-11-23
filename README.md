# PROJECT_SO_ANDRI_ENO3
---

# 🖥️ **SIMULASI TERMINAL — Membuat Struktur Direktori**

### 📌 **1. Cek apakah folder `/server` sudah ada**

```
$ ls /
bin  boot  dev  etc  home  lib  media  mnt  opt  root  run  sbin  srv  tmp  usr  var
```

Misalnya *folder server belum ada*, maka kita buat dulu.

```
$ mkdir /server
```

---
https://drive.google.com/file/d/1y8KIsPcNCybfAbykOHgC4IfckhenTbC9/view?usp=drivesdk

### 📌 **2. Membuat folder departemen + subfoldernya**

## 👉 Buat Marketing dengan Documents & Archives

```
$ mkdir -p /server/Marketing/Documents /server/Marketing/Archives
```

**Tidak ada output**, artinya sukses (normal di Linux).

Cek isinya:

```
$ tree /server/Marketing
/server/Marketing
├── Archives
└── Documents
```

---

## 👉 Buat Engineering

```
$ mkdir -p /server/Engineering/Documents /server/Engineering/Archives
```

Cek:

```
$ tree /server/Engineering
/server/Engineering
├── Archives
└── Documents
```

---

## 👉 Buat HR

```
$ mkdir -p /server/HR/Documents /server/HR/Archives
```

Cek:

```
$ tree /server/HR
/server/HR
├── Archives
└── Documents
```

---

# 📂 **3. Lihat seluruh struktur server**

```
$ tree /server
/server
├── Engineering
│   ├── Archives
│   └── Documents
├── HR
│   ├── Archives
│   └── Documents
└── Marketing
    ├── Archives
    └── Documents
```
https://drive.google.com/file/d/1yOieFCzwTPP1bRzy22YyJGfC3MJhsVSx/view?usp=drivesdk
---

# 🟢 **Selesai!**


---

# 🖥️ **SIMULASI TERMINAL — Nomor 2: Pindahkan & Backup File**

## 🎯 **Skenario:**

Ada file yang salah tempat di folder:

```
/server/tmp/
```

File-file itu seharusnya masuk ke departemen masing-masing:

* Marketing → proposal_marketing.pdf
* Engineering → engineering_report.docx
* HR → employee_list.xlsx

Setelah dipindahkan, kamu harus **membuat backup-nya** ke folder **Archives**.

---

# 📌 **1. Cek isi folder tmp**

```
$ ls /server/tmp
proposal_marketing.pdf  engineering_report.docx  employee_list.xlsx
```
https://drive.google.com/file/d/1yRJxPjHleYl51bMg0kHs2y2LC0arfFF_/view?usp=drivesdk
---

# 📌 **2. Pindahkan file ke direktori yang benar (mv)**

## 👉 Pindahkan file Marketing

```
$ mv /server/tmp/proposal_marketing.pdf /server/Marketing/Documents/
```

## 👉 Pindahkan file Engineering

```
$ mv /server/tmp/engineering_report.docx /server/Engineering/Documents/
```

## 👉 Pindahkan file HR

```
$ mv /server/tmp/employee_list.xlsx /server/HR/Documents/
```
https://drive.google.com/file/d/1yTsmA_EhsKADmk8c-MLo7l-ZVKH283sT/view?usp=drivesdk
---

# 📌 **3. Cek apakah file sudah dipindahkan**

### Marketing:

```
$ ls /server/Marketing/Documents
proposal_marketing.pdf
```

### Engineering:

```
$ ls /server/Engineering/Documents
engineering_report.docx
```

### HR:

```
$ ls /server/HR/Documents
employee_list.xlsx
```
https://drive.google.com/file/d/1yUi4c2doYWGoQX2xIhhZeaIZDO_cQSCd/view?usp=drivesdk
---

# 📌 **4. Buat backup file di folder Archives (cp)**

## 👉 Backup file Marketing

```
$ cp /server/Marketing/Documents/proposal_marketing.pdf /server/Marketing/Archives/
```

## 👉 Backup file Engineering

```
$ cp /server/Engineering/Documents/engineering_report.docx /server/Engineering/Archives/
```

## 👉 Backup file HR

```
$ cp /server/HR/Documents/employee_list.xlsx /server/HR/Archives/
```
https://drive.google.com/file/d/1yWJPxcrInW8o4ZIPNRgOVe9H_d_WKjKi/view?usp=drivesdk
---

# 📌 **5. Cek isi folder Archives**

### Marketing:

```
$ ls /server/Marketing/Archives
proposal_marketing.pdf
```

### Engineering:

```
$ ls /server/Engineering/Archives
engineering_report.docx
```

### HR:

```
$ ls /server/HR/Archives
employee_list.xlsx
```
https://drive.google.com/file/d/1yhAUuqACpgvynmr0dUZe_WRaKr8VPLEi/view?usp=drivesdk
---

# 🎉 **6. Kesimpulan**

Perintah yang digunakan:

### **Untuk memindahkan file:**

```
mv asal tujuan
```

### **Untuk membuat backup (menyalin file):**

```
cp asal tujuan
```
# Dan ini hasilnya 
---

https://drive.google.com/file/d/1yme8ipMxAa0NM7Lh8dAQmcV6c8bsbOLI/view?usp=drivesdk
---

# 🖥️ **SIMULASI TERMINAL — Nomor 3: Permission Folder Departemen**

## 🎯 **Tujuan:**

* Setiap departemen hanya boleh mengakses folder mereka sendiri.
* Kita akan:

  1. Membuat grup untuk tiap departemen
  2. Mengubah kepemilikan grup folder
  3. Memberi permission 770 (hanya owner & group yang bisa akses)

---

# 📌 **1. Cek struktur folder (opsional)**

```
$ tree /server
/server
├── Engineering
│   ├── Archives
│   └── Documents
├── HR
│   ├── Archives
│   └── Documents
└── Marketing
    ├── Archives
    └── Documents
```
https://drive.google.com/file/d/1ynq5MY51QWgd3A90OIEgk8zKcv1v0T8B/view?usp=drivesdk
---

# 📌 **2. Buat grup untuk masing-masing departemen**

```
$ groupadd marketing
$ groupadd engineering
$ groupadd hr
```

Tidak ada output → berarti berhasil.

---
https://drive.google.com/file/d/1ys2uIBeV1bRc3m_w9cMqKPs0XPI_mflu/view?usp=drivesdk

# 📌 **3. Ubah grup pemilik (group owner) folder**

### Marketing:

```
$ chgrp -R marketing /server/Marketing
```

### Engineering:

```
$ chgrp -R engineering /server/Engineering
```

### HR:

```
$ chgrp -R hr /server/HR
```

`-R` = recursive → seluruh folder & subfolder ikut berubah grupnya.

---

# 📌 **4. Set permission folder dengan chmod**

Permission yang digunakan:

```
770
```

Artinya:

* owner = full access (rwx)
* group = full access (rwx)
* others = no access (---)

### Terapkan ke semua folder Marketing:

```
$ chmod -R 770 /server/Marketing
```

### Engineering:

```
$ chmod -R 770 /server/Engineering
```

### HR:

```
$ chmod -R 770 /server/HR
```

---

# 📌 **5. Cek permission setelah diatur**

Contoh untuk Marketing:

```
$ ls -ld /server/Marketing
drwxrwx--- 3 root marketing 4096 Nov 20 10:22 /server/Marketing
```

Artinya:

* `drwxrwx---` = permission 770
* owner = root
* group = marketing

Cek salah satu subfolder:

```
$ ls -ld /server/Marketing/Documents
drwxrwx--- 2 root marketing 4096 Nov 20 10:22 /server/Marketing/Documents
```

Semuanya sudah memakai grup **marketing** dan permission **770**.

---

# 📌 **6. (Opsional) Tambahkan user ke grup masing-masing**

Contoh:

```
$ usermod -aG marketing user1
$ usermod -aG engineering user2
$ usermod -aG hr user3
```

Agar setiap user hanya bisa membuka folder departemen mereka.

---

# 🎉 **Permission Berhasil Diatur**

Sekarang:

* Marketing hanya bisa mengakses folder Marketing
* Engineering hanya bisa mengakses folder Engineering
* HR hanya bisa mengakses folder HR

---

Baik! Berikut **SIMULASI TERMINAL LINUX** untuk **Nomor 4: Mencari file PDF yang dibuat/mampir minggu lalu**.

Simulasi ini dibuat seakan-akan kamu mengetik langsung di terminal.

---

# 🖥️ **SIMULASI TERMINAL — Nomor 4: Cari File PDF Minggu Lalu**

## 🎯 **Tujuan:**

* Menemukan **semua file PDF** yang **dimodifikasi dalam 7 hari terakhir**
* Dari seluruh folder `/server`
* Lalu menyimpannya ke dalam file daftar bernama:

  ```
  pdf_minggu_lalu.txt
  ```

---

# 📌 **1. Cek dulu isi server (opsional)**

```
$ tree /server
/server
├── Engineering
│   ├── Documents
│   │   └── draft_engineering.pdf
│   └── Archives
├── HR
│   ├── Documents
│   │   └── data_karyawan.pdf
│   └── Archives
└── Marketing
    ├── Documents
    │   └── proposal_marketing.pdf
    └── Archives
```

Misalnya beberapa file PDF ini baru diedit minggu lalu.

---

# 📌 **2. Gunakan perintah find**

Perintahnya:

```
find /server -type f -name "*.pdf" -mtime -7 > /server/pdf_minggu_lalu.txt
```

Mari lihat simulasi terminalnya 👇

---

# 🖥️ **Terminal: Jalankan perintah find**

```
$ find /server -type f -name "*.pdf" -mtime -7 > /server/pdf_minggu_lalu.txt
```

Perintah ini **tidak menampilkan output** (normal), karena hasilnya dikirim ke file.

---

# 📌 **3. Cek isi file daftar PDF minggu lalu**

```
$ cat /server/pdf_minggu_lalu.txt
/server/Marketing/Documents/proposal_marketing.pdf
/server/Engineering/Documents/draft_engineering.pdf
/server/HR/Documents/data_karyawan.pdf
```

Ini berarti ketiga PDF tersebut dimodifikasi dalam 7 hari terakhir.

---

# 📘 **Penjelasan Perintah**

| Bagian                        | Arti                                                   |
| ----------------------------- | ------------------------------------------------------ |
| `find /server`                | Cari file di dalam folder /server                      |
| `-type f`                     | Hanya file, bukan folder                               |
| `-name "*.pdf"`               | Cari file yang berakhiran .pdf                         |
| `-mtime -7`                   | File yang diubah (modified time) dalam 7 hari terakhir |
| `>`                           | Mengalihkan output ke file                             |
| `/server/pdf_minggu_lalu.txt` | Nama file daftar hasil pencarian                       |

---

# 🎉 **Hasil Akhir:**

berhasil membuat daftar file PDF yang ditemukan minggu lalu.

---

