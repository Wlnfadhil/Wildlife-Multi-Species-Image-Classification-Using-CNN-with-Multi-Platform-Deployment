# Submission - Wildlife Multi-Species Image Classification

Proyek ini adalah submission klasifikasi gambar satwa liar berbasis CNN, dengan deployment model ke beberapa format (`SavedModel`, `TFLite`, dan `TFJS`).

## Sumber Dataset (Kaggle)

Dataset yang digunakan berasal dari Kaggle:

- **Nama dataset**: `wildlifedatasets/wildlifereid-10k`
- **Deskripsi**: *WildlifeReID-10k* adalah dataset re-identification satwa liar dengan lebih dari 140 ribu gambar dari 10 ribu individu hewan.
- Dataset ini merupakan gabungan dari 37 dataset wildlife re-identification yang sudah ada, dengan proses kurasi tambahan.
- Dua penggunaan utama:
	1. Klasifikasi **individu hewan** (fine-grained, ~10k kelas).
	2. Klasifikasi **spesies hewan** (coarse-grained, ~20 kelas), lebih ringan untuk eksperimen awal.

## Cara Download Dataset dari Kaggle

Gunakan kode berikut:

```python
import kagglehub

# Download latest version
path = kagglehub.dataset_download("wildlifedatasets/wildlifereid-10k")

print("Path to dataset files:", path)
```

## Catatan Lisensi & Atribusi Dataset

WildlifeReID-10k dibuat dengan menggabungkan banyak dataset pihak ketiga. Penggunaan dataset harus mengikuti file lisensi yang disediakan.

Poin penting:

- Tidak untuk penggunaan komersial (sesuai ketentuan lisensi masing-masing sumber).
- Tidak boleh diunggah ulang.
- Wajib mencantumkan atribusi untuk dataset penyusun.

Jenis lisensi yang disebutkan pada deskripsi dataset meliputi (ringkas):

- CC BY 4.0
- CC BY-NC-SA 4.0
- CC BY-SA 3.0 / 4.0
- CDLA-Permissive-1.0
- MIT
- NC-Government
- None / Other (mengikuti ketentuan masing-masing dataset sumber)

## Menjalankan Submission Dicoding

Dokumen utama submission berada di folder ini:

- Notebook: `klasifikasi-gambar.ipynb`
- Dependensi: `requirements.txt`
- Artefak model (hasil rapih): di folder `../model/`

Langkah umum menjalankan submission:

1. Install dependensi:
	 ```bash
	 pip install -r requirements.txt
	 ```
2. Buka dan jalankan notebook `klasifikasi-gambar.ipynb` dari awal sampai akhir.
3. Pastikan artefak model tersimpan untuk kebutuhan deployment / penilaian.

## Struktur Relevan

```text
submission/
├─ klasifikasi-gambar.ipynb
├─ requirements.txt
└─ README.md

model/
├─ saved_model/
├─ tflite/
└─ tfjs_lite/
```

## Referensi

- Kaggle Dataset: `wildlifedatasets/wildlifereid-10k`
