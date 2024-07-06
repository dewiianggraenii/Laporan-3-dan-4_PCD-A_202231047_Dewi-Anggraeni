
# Deteksi Garis Tepi

Deteksi garis tepi dalam pengolahan citra adalah teknik ntuk mengidentifikasi lokasi di mana terjadi perubahan yang tajam dalam intensitas piksel citra. Tujuannya adalah untuk menyoroti tepi atau batas antara objek yang berbeda atau antara objek dan latar belakang dalam citra.

## Tujuan Utama Deteksi Garis Tepi dalam Pengolahan Citra:
- Pertama, tujuan utamanya adalah untuk mengidentifikasi lokasi di mana terjadi perubahan yang tajam dalam intensitas piksel citra. Perubahan ini sering kali menandakan batas atau tepi antara objek yang berbeda atau antara objek dan latar belakang. Dengan mengidentifikasi tepi ini secara akurat menggunakan metode seperti Sobel, Prewitt, Canny, atau Laplacian of Gaussian (LoG), kita dapat dengan tepat menandai dan memahami struktur visual yang ada dalam citra.

- Kedua, tujuan deteksi garis tepi adalah untuk melakukan segmentasi objek dalam citra. Segmentasi ini penting karena memungkinkan pemisahan objek dari latar belakang atau identifikasi batas antara objek untuk analisis lebih lanjut. Dengan menggunakan informasi tepi yang telah ditemukan, kita dapat memisahkan dan mengisolasi objek-objek dalam citra untuk aplikasi seperti pengenalan pola, pengukuran geometris, atau pengolahan citra medis.

## Metode Deteksi Garis Tepi Umum:
1. Metode Sobel dan Prewitt
Metode Sobel dan Prewitt adalah dua metode yang serupa dalam prinsip dasar, yaitu menggunakan kernel untuk menghitung gradien dalam arah horizontal dan vertikal. Kernel ini adalah matriks kecil yang diterapkan pada citra untuk menghitung perubahan gradien intensitas piksel di sekitarnya. Perbedaan utama antara keduanya terletak pada bentuk kernel yang digunakan:

- Sobel: Menggunakan kernel 3x3 dengan bobot yang lebih besar di tengah untuk menekankan gradien di tengah kernel.

- Prewitt: Juga menggunakan kernel 3x3 tetapi dengan bobot yang merata di semua arah.

Langkah-langkah operasinya:

- Pertama, citra dilakukan konvolusi dengan kernel Sobel atau Prewitt dalam arah horizontal dan vertikal secara terpisah.
- Setelah itu, gradien absolut untuk kedua arah (Gx dan Gy) dihitung dan digabungkan untuk mendapatkan magnitude gradien total.
- Arah gradien juga bisa dihitung menggunakan arctan dari Gx dan Gy untuk menentukan orientasi tepi.

2. Metode Canny
Metode Canny adalah pendekatan yang lebih kompleks dan sering dianggap sebagai standar emas dalam deteksi garis tepi karena menggabungkan beberapa langkah untuk menghasilkan deteksi tepi yang akurat:

- Filtrasi Gaussian: Langkah pertama adalah menerapkan filtrasi Gaussian untuk mengurangi noise dalam citra.

- Deteksi Gradien: Setelah itu, digunakan untuk mengidentifikasi gradien citra dan arah perubahan yang tajam.

- Non-Maximum Suppression: Dilakukan untuk mempertahankan hanya piksel yang merupakan lokal maksimum (yaitu, tepi yang tepat) di sepanjang arah gradien.

- Hysteresis Thresholding: Langkah terakhir adalah menggunakan dua ambang nilai (batas bawah dan atas) untuk menentukan piksel tepi yang terhubung (strong edge) dari piksel-piksel yang lemah yang mungkin terkait (weak edge).

3. Metode Laplacian of Gaussian (LoG)
Metode LoG menggabungkan dua operasi, yaitu filtrasi Gaussian dan operasi Laplacian, untuk mendeteksi tepi dalam satu langkah:

- Filtrasi Gaussian: Pertama-tama, citra diterapkan dengan filtrasi Gaussian untuk menghaluskan dan mengurangi noise.

- Operasi Laplacian: Selanjutnya, dilakukan untuk menemukan perubahan gradien yang tajam dalam citra, yang terkonsentrasi di sekitar tepi.

# Ekstraksi Fitur Menggunakan Skimage 
Ekstraksi fitur menggunakan skimage (scikit-image) adalah proses yang esensial dalam analisis citra yang bertujuan untuk mengambil informasi yang relevan dan deskriptif dari gambar. Scikit-image adalah pustaka Python yang menyediakan berbagai algoritma dan fungsi untuk manipulasi, analisis, dan pemrosesan gambar yang beragam. Berikut ini adalah beberapa teknik ekstraksi fitur yang umum digunakan dengan skimage:

1. Histogram of Oriented Gradients (HOG)
- Deskripsi: HOG adalah metode untuk mengukur distribusi lokal dari gradien intensitas dalam citra. Ini berguna untuk mengidentifikasi dan mendeskripsikan objek dalam gambar berdasarkan distribusi gradien mereka.
- Implementasi: Anda dapat menggunakan skimage.feature.hog() untuk menghasilkan deskripsi HOG dari gambar. Ini dapat digunakan untuk klasifikasi objek dalam sistem pengenalan gambar.

2. Local Binary Pattern (LBP)
- Deskripsi: LBP adalah metode untuk menggambarkan tekstur lokal dalam citra dengan membandingkan nilai piksel dengan tetangganya. Ini efektif untuk analisis dan pengenalan tekstur dalam citra.
- Implementasi: skimage.feature.local_binary_pattern() menghitung pola biner lokal dari citra, yang memberikan deskripsi detail tentang tekstur dalam citra.

3. Corner Detection (Deteksi Sudut)
- Deskripsi: Teknik deteksi sudut digunakan untuk menemukan titik-titik sudut dalam citra, yang sering kali menunjukkan perubahan signifikan dalam struktur objek.
- Implementasi: skimage.feature.corner_harris() dan skimage.feature.corner_shi_tomasi() adalah dua metode yang tersedia untuk deteksi sudut dalam skimage.

4. Texture Descriptors (Deskripsi Tekstur)
- Deskripsi: Ini termasuk berbagai metode untuk menggambarkan sifat-sifat tekstur dalam citra, seperti energi, kontras, dan homogenitas.
- Implementasi: skimage.feature.greycomatrix() digunakan untuk menghitung matriks ko-occurance abu-abu, yang memungkinkan ekstraksi deskripsi tekstur dalam citra.

5. Edge Detection (Deteksi Tepi)
- Deskripsi: Deteksi tepi adalah teknik untuk mengidentifikasi garis tepi atau perubahan tajam dalam intensitas citra, yang sering kali menjadi langkah awal dalam analisis citra.
- Implementasi: skimage.feature.canny() atau skimage.filters.sobel() dapat digunakan untuk melakukan deteksi tepi dalam skimage.

## Konversi Warna: RGB ke HSV
- RGB (Red-Green-Blue): Sistem warna yang umum digunakan di mana setiap warna direpresentasikan sebagai kombinasi dari tiga warna dasar: merah, hijau, dan biru.

- HSV (Hue-Saturation-Value): Sistem warna yang memisahkan informasi warna (Hue), kejenuhan (Saturation), dan nilai kecerahan (Value) dari gambar.

## Langkah-langkah Ekstraksi Fitur dengan skimage
- Memuat Gambar: Menggunakan io.imread() untuk memuat gambar dari file.

- Konversi Warna: Menggunakan color.rgb2hsv() untuk mengubah gambar dari RGB ke HSV.


- Ekstraksi Fitur: Setelah konversi, Anda dapat mengekstraksi fitur yang diinginkan dari gambar, seperti nilai Hue, Saturation, atau Value, untuk keperluan analisis lebih lanjut.

- Visualisasi (Opsional): Anda bisa menggunakan io.imshow() untuk memvisualisasikan hasil konversi dan ekstraksi fitur.

## Keuntungan skimage untuk Ekstraksi Fitur:
- Komprehensif: Menyediakan berbagai metode ekstraksi fitur yang dapat digunakan untuk berbagai aplikasi analisis citra.
- Penggunaan yang Mudah: API yang sederhana dan dokumentasi yang baik memudahkan implementasi dan eksperimen dengan berbagai teknik.
- Integrasi dengan scipy: Scikit-image terintegrasi dengan baik dengan pustaka ilmiah Python lainnya seperti numpy dan scipy, memungkinkan analisis yang lebih lanjut dan pengolahan data.