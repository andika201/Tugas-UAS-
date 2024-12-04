# Tugas-UAS-
---

# Face Detection dengan OpenCV

Program berikut digunakan untuk mendeteksi wajah pada gambar menggunakan library OpenCV dan model Haar Cascade Classifier.

## Penjelasan Program

1. **Import Library**
    ```python
    import cv2
    import numpy as np
    ```
    - `cv2`: Library dari OpenCV untuk pengolahan gambar dan video.
    - `numpy`: Library untuk manipulasi array, meskipun dalam program ini tidak digunakan secara eksplisit.

2. **Load Model Haar Cascade**
    ```python
    face_cascade = cv2.CascadeClassifier('D:/File Dika/file kuliah/pak arsan/uas/haarcascade_frontalface_default (1).xml')
    ```
    - Memuat file Haar Cascade XML, yang berisi data untuk mendeteksi wajah.

3. **Membaca dan Mengonversi Gambar**
    ```python
    image = cv2.imread("D:/File Dika/file kuliah/pak arsan/Capture.PNG")
    img = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
    ```
    - `cv2.imread`: Membaca file gambar.
    - `cv2.cvtColor`: Mengonversi gambar menjadi skala abu-abu (`GRAY`), karena Haar Cascade bekerja lebih baik dengan gambar grayscale.

4. **Deteksi Wajah**
    ```python
    faces = face_cascade.detectMultiScale(img, scaleFactor=1.1)
    ```
    - `detectMultiScale`: Fungsi untuk mendeteksi objek (wajah dalam kasus ini).
      - `scaleFactor=1.1`: Memperbesar ukuran pencarian di setiap iterasi. Nilai ini membantu mendeteksi wajah dari berbagai ukuran.

5. **Menandai Wajah dengan Kotak**
    ```python
    for (x, y, w, h) in faces:
        cv2.rectangle(image, (x, y), (x+w, y+h), (0, 0, 155), 3)
    ```
    - `cv2.rectangle`: Menggambar kotak pada gambar.
        - `(x, y)`: Titik awal kotak (koordinat kiri atas).
        - `(x+w, y+h)`: Titik akhir kotak (koordinat kanan bawah).
        - `(0, 0, 155)`: Warna kotak dalam format RGB (merah dalam contoh ini).
        - `3`: Ketebalan garis kotak.

6. **Menampilkan Gambar Hasil**
    ```python
    cv2.imshow("display", image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
    ```
    - `cv2.imshow`: Menampilkan gambar dengan nama jendela `"display"`.
    - `cv2.waitKey(0)`: Menunggu hingga ada input tombol dari keyboard.
    - `cv2.destroyAllWindows`: Menutup semua jendela tampilan gambar.

## Output
Program akan menampilkan gambar dengan kotak merah pada area wajah yang terdeteksi.

## File Dependensi
- File Haar Cascade: `haarcascade_frontalface_default.xml`
- Gambar untuk deteksi: `Capture.PNG`

## Catatan
Jika ingin menyimpan hasil gambar dengan wajah yang diberi kotak, gunakan kode berikut:
```python
cv2.imwrite("hasil_deteksi.png", image)
```

![Deteksi Wajah](https://github.com/andika201/Tugas-UAS-/blob/main/Capture.PNG)
