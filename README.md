# PROJECT-SO-ANDRI3
1. Buat Struktur Direktori

Buat 3 folder departemen, masing-masing memiliki subfolder Documents dan Archives.

Perintah:
mkdir -p /server/Marketing/Documents /server/Marketing/Archives
mkdir -p /server/Engineering/Documents /server/Engineering/Archives
mkdir -p /server/HR/Documents /server/HR/Archives


-p memastikan folder dibuat lengkap dengan struktur yang diperlukan.

✅ 2. Pindahkan dan Salin File
Contoh Skenario:

Misalnya ada file salah tempat di /server/tmp/.

Pindahkan file ke direktori yang benar:
mv /server/tmp/proposal_marketing.pdf /server/Marketing/Documents/
mv /server/tmp/engineering_report.docx /server/Engineering/Documents/
mv /server/tmp/employee_list.xlsx /server/HR/Documents/

Buat backup di folder Archives:

Gunakan cp untuk menyalin file ke folder arsip.

cp /server/Marketing/Documents/proposal_marketing.pdf /server/Marketing/Archives/
cp /server/Engineering/Documents/engineering_report.docx /server/Engineering/Archives/
cp /server/HR/Documents/employee_list.xlsx /server/HR/Archives/

✅ 3. Atur Permission

Berikan akses hanya pada departemen terkait.

Langkah 1 — Buat grup departemen:
groupadd marketing
groupadd engineering
groupadd hr

Langkah 2 — Set grup owner direktori:
chgrp -R marketing /server/Marketing
chgrp -R engineering /server/Engineering
chgrp -R hr /server/HR

Langkah 3 — Atur permission agar hanya pemilik dan grup yang dapat mengakses:
chmod -R 770 /server/Marketing
chmod -R 770 /server/Engineering
chmod -R 770 /server/HR


770 artinya:

owner: full

group: full

others: no access

(Opsional) Tambahkan user ke dalam grup departemen:
usermod -aG marketing user1
usermod -aG engineering user2
usermod -aG hr user3

✅ 4. Cari & Filter File PDF Dari Minggu Lalu

Gunakan perintah find dengan filter waktu.

Perintah:
find /server -type f -name "*.pdf" -mtime -7 > /server/pdf_minggu_lalu.txt


Penjelasan:

-type f → hanya file

-name "*.pdf" → hanya PDF

-mtime -7 → dimodifikasi dalam 7 hari terakhir

> file.txt → simpan daftar ke file
