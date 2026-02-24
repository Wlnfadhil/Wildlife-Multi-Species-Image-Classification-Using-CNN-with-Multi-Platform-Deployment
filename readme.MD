# Sentimen Analisis Gambar Satwa Liar

Repositori ini berisi proyek klasifikasi gambar satwa liar berbasis CNN dengan fokus pipeline end-to-end untuk kebutuhan submission: persiapan data, pelatihan model, evaluasi, dan ekspor model ke beberapa format deployment.

Proyek ini mengacu pada dataset Kaggle **WildlifeReID-10k** dan implementasi notebook di folder `submission`.

## Ringkasan Proyek

- **Task utama**: klasifikasi gambar satwa (multi-species image classification).
- **Dataset**: `wildlifedatasets/wildlifereid-10k` dari Kaggle.
- **Output model**: `SavedModel`, `TFLite`, dan `TFJS`.
- **Target performa**: akurasi validasi **> 92%** (dengan eksperimen dan tuning yang konsisten).

## Dataset (Acuan dari Submission)

`WildlifeReID-10k` adalah kumpulan besar data satwa liar (lebih dari 140k gambar) dari banyak dataset re-identification. Untuk eksperimen yang lebih ringan, proyek ini menekankan pendekatan klasifikasi spesies (coarse-grained) sebelum masuk ke level individu (fine-grained).

Contoh unduh dataset:

```python
import kagglehub

path = kagglehub.dataset_download("wildlifedatasets/wildlifereid-10k")
print("Path to dataset files:", path)
```

## Struktur Direktori

```text
sentimen analisis gambar/
├── model/
│   ├── saved_model/
│   ├── tfjs_lite/
│   └── tflite/
├── submission/
│   ├── klasifikasi-gambar.ipynb
│   ├── requirements.txt
│   └── README.md
└── README.md
```

## Step-by-Step Menjalankan Proyek

### 1) Persiapan environment

Di root project:

- **PowerShell**
  ```powershell
  .\.venv\Scripts\Activate.ps1
  ```
- **Git Bash**
  ```bash
  source .venv/Scripts/activate
  ```

### 2) Install dependensi

```bash
pip install -r submission/requirements.txt
```

### 3) Siapkan dataset

Jalankan snippet `kagglehub` di notebook atau script Python untuk mengambil dataset ke local path.

### 4) Jalankan notebook utama

```bash
jupyter notebook
```

Buka `submission/klasifikasi-gambar.ipynb`, lalu jalankan dari cell awal sampai akhir agar seluruh output tersimpan.

### 5) Training dan evaluasi

Pastikan pipeline mencakup:

- preprocessing gambar,
- split train/valid yang konsisten,
- training model CNN,
- evaluasi akurasi dan metrik klasifikasi.

### 6) Ekspor model deployment

Simpan model ke format berikut:

- `SavedModel` → folder `model/saved_model/`
- `TFLite` → `model/tflite/model.tflite`
- `TFJS` → folder `model/tfjs_lite/`

### 7) Finalisasi submission

- Pastikan notebook sudah dijalankan (output terlihat).
- Pastikan berkas wajib tersedia (`.ipynb`, model, `requirements.txt`, `README.md`).
- Zip 1 folder submission untuk pengumpulan.

## Insight yang Paling Relevan untuk Meningkatkan Akurasi

1. **Pastikan split data tidak leakage**  
	Hindari gambar yang sangat mirip muncul di train dan validasi karena bisa memberi akurasi semu.

2. **Tangani ketidakseimbangan kelas**  
	Gunakan `class_weight`, oversampling terbatas, atau augmentasi terarah pada kelas minoritas.

3. **Augmentasi secukupnya**  
	Rotasi, flip, zoom, brightness efektif, tetapi augmentasi berlebihan dapat menurunkan generalisasi.

4. **Gunakan transfer learning**  
	Mulai dari backbone ringan (mis. MobileNet/DenseNet), freeze layer awal, lalu fine-tune bertahap.

5. **Pantau metrik selain accuracy**  
	Tambahkan confusion matrix, precision, recall, F1-score agar performa tiap kelas lebih terukur.

6. **Gunakan callback training**  
	`EarlyStopping`, `ReduceLROnPlateau`, dan `ModelCheckpoint` membantu stabilitas training.

## Checklist Submission

- Notebook `.ipynb` sudah complete output.
- Model tersedia di 3 format: SavedModel, TFLite, TFJS.
- `requirements.txt` tersedia.
- `README.md` menjelaskan dataset, alur, dan cara run.
- Seluruh berkas submission dikemas dalam 1 file `.zip`.

## Lisensi

Proyek ini mengikuti lisensi pada file `LICENSE`. Untuk dataset `WildlifeReID-10k`, tetap ikuti ketentuan lisensi dan atribusi tiap dataset penyusunnya.
