# Preprocessing LendingClub Loan Dataset

Tugas mata kuliah Rekayasa Data

Nama : Muhammad Zakiyyuddin Abdul Adhiim

NIM  : 24/545668/TK/60719

Prodi : Teknologi Informasi

## Dataset

Pakai data pinjaman LendingClub (accepted loans, periode 2007–2018Q4) dari Kaggle:
https://www.kaggle.com/datasets/wordsforthewise/lending-club

Data aslinya 2,26 juta baris x 151 kolom. Karena kegedean buat diproses bolak-balik, yang dipakai di sini cuma sampel acak ~60 ribu baris. Cara ngambil sampelnya (bukan cuma `head()`, karena datanya terurut per tanggal) ada di dalam notebook, bagian paling atas.

## Struktur Repo

- `notebooks/preprocessing.ipynb`: notebook utama, isinya seluruh tahap: audit data, cleaning (missing value, tipe data, outlier), integration (deteksi kolom redundan lewat korelasi), sampai reduction pakai PCA.
- `data/raw/`: data mentah hasil sampling (`lendingclub_sample_raw.csv`). File sumber penuhnya (.csv.gz, ~375MB) sengaja tidak ikut di-push, kegedean buat GitHub: kalau mau jalanin notebook dari nol, nanti otomatis ke-download sendiri asal kredensial Kaggle API-nya udah ada di `~/.kaggle/kaggle.json`.
- `data/processed/`: hasil setelah dibersihkan + diintegrasikan, dan hasil setelah PCA.
- `figures/`: semua grafik yang dihasilkan notebook (missing value, outlier, korelasi, scree plot PCA, dll).

Laporan (docx) dan file presentasi disimpen terpisah di lokal, tidak ikut masuk sini karena masih bolak-balik diedit manual.

## Cara Jalankan

Butuh environment Python sendiri (tidak ikut di-push karena isinya package doang, ~700MB):

```bash
python3 -m venv venv
source venv/bin/activate
pip install pandas numpy scikit-learn matplotlib seaborn jupyter kaggle
```

Setelah itu tinggal buka notebooknya:

```bash
jupyter notebook notebooks/preprocessing.ipynb
```

atau kalau mau langsung dieksekusi semua dari terminal tanpa buka browser:

```bash
jupyter nbconvert --to notebook --execute --inplace notebooks/preprocessing.ipynb
```
