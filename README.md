# CVL Tugas 2 : Sliding Window + HOG

Implementasi tugas Computer Vision MKA untuk **Opsi B — Sliding Window + HOG** dengan **Linear SVM** untuk pedestrian detection.

Eksperimen mengacu pada:

> N. Dalal and B. Triggs, “Histograms of Oriented Gradients for Human Detection,” in Proc. IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2005, pp. 886–893.

## Tujuan

Eksperimen ini melakukan partial replication studi parameter HOG untuk mengetahui pengaruh:

- ukuran cell
- jumlah orientation bins
- block normalization

terhadap performa pedestrian detector.

Evaluasi dilakukan menggunakan:

- **AP@0.5**
- **Miss Rate vs FPPW**
- **Failure Case Analysis**

## Dataset

Dataset yang digunakan:

**Maxim37/hazy-pedestrian-detection**

Dataset diakses secara otomatis melalui Hugging Face sehingga tidak membutuhkan upload dataset secara manual.

Pembagian data pada eksperimen:

| Split | Jumlah |
|---|---:|
| Training | 1,052 citra |
| Test | 143 citra |
| Ground-truth test | 245 pedestrian |

Dataset ini digunakan sebagai alternatif karena INRIA Person tidak dapat diakses selama pelaksanaan eksperimen. Karena domain dataset berbeda, terutama adanya kondisi hazy/kabut, hasil tidak dianggap sebagai reproduksi langsung angka pada paper Dalal and Triggs.

## Metode

Pipeline utama:

```text
Dataset
   ↓
Positive Patches
   +
Random Negative Patches
   ↓
HOG Feature Extraction
   ↓
Initial Linear SVM
   ↓
Hard-Negative Mining
   ↓
Final Linear SVM
   ↓
Multi-scale Sliding Window
   ↓
SVM Decision Score
   ↓
Greedy NMS
   ↓
AP@0.5
+
Miss Rate vs FPPW
