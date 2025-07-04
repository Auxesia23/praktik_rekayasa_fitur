# Dokumentasi Singkat Ekstraksi Fitur Uang Kertas

## Deskripsi Data
Dataset terdiri dari gambar uang kertas Indonesia dengan pecahan 5, 10, 20, 50, 100, dan 200 ribu. Setiap pecahan tersimpan dalam subfolder berbeda di direktori `gambar_lira/`. Gambar diambil dari berbagai kondisi pencahayaan dan posisi.

## Langkah Feature Engineering (FE)
1. **Ekstraksi Histogram RGB**  
   - Setiap gambar dikonversi ke RGB.
   - Histogram tiap channel (R, G, B) dihitung (32 bin per channel).
   - Histogram digabung dan dinormalisasi.
   - Hasil akhir: vektor fitur histogram RGB per gambar.

2. **Ekstraksi HOG (Histogram of Oriented Gradients)**  
   - Gambar dikonversi ke grayscale.
   - Fitur HOG diekstrak dengan parameter: 9 orientasi, 8x8 pixels per cell, 2x2 cells per block.
   - Hasil akhir: vektor fitur HOG per gambar.

3. **Penyimpanan Fitur**  
   - Fitur histogram dan HOG disimpan ke file CSV (`fitur_histogram.csv`, `fitur_hog.csv`).

## Insight
1. **Distribusi Data**  
   - Setiap pecahan uang memiliki jumlah gambar yang seimbang, memudahkan analisis dan pelatihan model klasifikasi.

2. **Karakteristik Histogram RGB**  
   - Histogram RGB tiap pecahan menunjukkan pola warna dominan berbeda, misal pecahan 100 ribu cenderung memiliki puncak pada channel merah.

3. **Ciri Tekstur dari HOG**  
   - Fitur HOG mampu menangkap pola garis dan tekstur khas pada masing-masing pecahan, membantu membedakan antar nominal.

4. **Potensi Klasifikasi**  
   - Kombinasi fitur warna (histogram) dan tekstur (HOG) dapat digunakan untuk membangun model klasifikasi pecahan uang secara otomatis.

5. **Visualisasi**  
   - Visualisasi histogram dan HOG memperlihatkan perbedaan signifikan antar pecahan, baik dari sisi warna maupun tekstur.

# Ekstraksi Fitur Uang Kertas

## Cara Menjalankan Notebook

1. **Pastikan sudah menginstall [uv](https://github.com/astral-sh/uv):**
   ```sh
   pip install uv
   ```

2. **Buat virtual environment dan Install dependensi dari pyproject.toml:**
   ```sh
   uv sync
   ```

3. **Buka dan jalankan `main.ipynb` di Jupyter Notebook.**

---

**Catatan:**  
Pastikan folder `gambar_lira/` sudah berisi gambar sesuai struktur subfolder pecahan uang.

