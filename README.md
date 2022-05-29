# P1_Probstat_F_5025201134
## Laporan Praktikum Modul 2 
**Nama  : Rivaldo Panangian Tambunan**

**NRP   : 5025201134**

**Kelas : F**

***
## **Soal 1**
Seorang peneliti melakukan penelitian mengenai pengaruh aktivitas 𝐴 terhadap
kadar saturasi oksigen pada manusia. Peneliti tersebut mengambil sampel
sebanyak 9 responden. Pertama, sebelum melakukan aktivitas 𝐴, peneliti mencatat
kadar saturasi oksigen dari 9 responden tersebut. Kemudian, 9 responden tersebut
diminta melakukan aktivitas 𝐴. Setelah 15 menit, peneliti tersebut mencatat kembali
kadar saturasi oksigen dari 9 responden tersebut. Berikut data dari 9 responden
mengenai kadar saturasi oksigen sebelum dan sesudah melakukan aktivitas 𝐴

![Picture1](https://user-images.githubusercontent.com/71111983/170866877-8caab896-8ffb-4d62-880a-f4c0ef7ffc24.png)

Berdasarkan data pada tabel diatas, diketahui kadar saturasi oksigen dari
responden ke-3 ketika belum melakukan aktivitas 𝐴 sebanyak 67, dan setelah
melakukan aktivitas 𝐴 sebanyak 70.
a. Carilah Standar Deviasi dari data selisih pasangan pengamatan tabel
diatas
b. carilah nilai t (p-value)
c. tentukanlah apakah terdapat pengaruh yang signifikan secara statistika
dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan
aktivitas 𝐴 jika diketahui tingkat signifikansi 𝛼 = 5% serta H0 : “tidak ada
pengaruh yang signifikan secara statistika dalam hal kadar saturasi
oksigen , sebelum dan sesudah melakukan aktivitas 𝐴”

### A.
Carilah Standar Deviasi dari data selisih pasangan pengamatan tabel diatas
``` 
# A

Responden = c (1,2,3,4,5,6,7,8,9)

x = c (78, 75, 67, 77, 70, 72, 78, 74, 77)

y = c (100, 85, 70, 90, 90, 90, 89, 90, 100)

Tabel_Saturasi = data.frame(Responden, x, y)

Tabel_Saturasi

Standar_Deviasi = sd(Tabel_Saturasi$x - Tabel_Saturasi$y)

Standar_Deviasi
```
Untuk mendapatkan standar deviasi dari data selisih pasangan tabel diatas yaitu x 
( kadar saturasi oksigen sebelum melakukan aktivitas A) dan y ( kadar oksigen sesudah melakukan aktivitas A).
Pertama kita akan mengurangkan data x dan data y dari setiap responden lalu mencari standar deviasinya. 
Dalam pengerjaannya dalam bahasa R, kita akan menggunakan data.frame untuk membuat 
sebuah tabel 2 dimensi dari data-data responden tersebut. Lalu untuk mendapatkan 
standar deviasi dari data selisih pasangan tabel, kita akan mengurangkan data dari x dan y. 
Kemudian menggunakan fungsi sd yang ada dalam R

![Picture2](https://user-images.githubusercontent.com/71111983/170867051-0350aefe-4541-4188-849c-2e430cc99114.png)

### B.
carilah nilai t (p-value)
``` 
# B
data_saturasi <- data.frame(
  group = rep(c("x", "y"), each = 9),
  saturation = c(x, y)
)

data_saturasi

t.test(x, y, alternative = "greater", var.equal = FALSE)
```
Untuk mendapatkan t(p-value) kita bisa menggunakan fungsi t-test yang ada di bahasa r

![Picture3](https://user-images.githubusercontent.com/71111983/170867134-ae1acd16-704b-4406-80cf-b86b332b790a.png)

### C.
tentukanlah apakah terdapat pengaruh yang signifikan secara statistika
dalam hal kadar saturasi oksigen , sebelum dan sesudah melakukan
aktivitas 𝐴 jika diketahui tingkat signifikansi 𝛼 = 5% serta H0 : “tidak ada
pengaruh yang signifikan secara statistika dalam hal kadar saturasi
oksigen , sebelum dan sesudah melakukan aktivitas 𝐴”
``` 
# B
var.test(x,y)

t.test(x,y,var.equal = TRUE)
```
Untuk menentukan pengaruh yang signifikan secara statistika dalam hal kadar saturai 
oksigen, sebelum (x) dan sesudah (y) melakukan aktivitas A. dimana tingkan signifikasinya ada 5 persen. 
Kita perlu melakukan komparasi pada 2 variabel sebelum (x) dan sesudah (y).  

![Picture4](https://user-images.githubusercontent.com/71111983/170867193-4eccf5b0-c281-4ddb-a00c-07864f8320e4.png)

Kemudian kita menggunakan fungsi t.test yang ada pada bahasa r. untuk melihat pengaruh jika tingkat signifikasi sebesar 5 persen. Dan dari hasil yang didapat bis akita simpulakan bahwa mean dan convidence yang di dapat dari fungsi t.test ini sama dengan mean dan convidence yang di dapat pada 1b. dan juga bis akita lihat juga yang berbeda hanya pada p-value yang didapat yaitu 0.0002366 (1c) dan 0.9997 (1b). oleh karena itu bisa disimpulakan bahwa tidak memiliki pengaruh yang signifikan dalam statistika

![Picture5](https://user-images.githubusercontent.com/71111983/170867194-221265df-4d2b-4616-a37c-2d5dbfc71306.png)


***
## **Soal 2**
Diketahui bahwa mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun.
Untuk menguji klaim ini, 100 pemilik mobil yang dipilih secara acak diminta untuk
mencatat jarak yang mereka tempuh. Jika sampel acak menunjukkan rata-rata
23.500 kilometer dan standar deviasi 3900 kilometer. (Kerjakan menggunakan
library seperti referensi pada modul).
a. Apakah Anda setuju dengan klaim tersebut?
b. Jelaskan maksud dari output yang dihasilkan!
c. Buatlah kesimpulan berdasarkan P-Value yang dihasilkan!

### A.
Apakah Anda setuju dengan klaim tersebut?
``` 
Setuju
```

### B.
Jelaskan maksud dari output yang dihasilkan!
``` 
tsum.test(mean.x = 23500, sd(3900), n.x = 100)
```
Untuk mendapatkan output yang dihasilkan, kita akan menggunakan tsum.test dimana kita melakukan satu sampel atau dua sampel, berdasarkan informasi ringkasan yang diberikan pengguna.  Kemungkinan outputnya identik dengan yang dihasilkan dengan t.test. Dari pernyataan soal diatas mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun, 100 pemilik mobil yang dipilih secara acak diminta untuk mencatat jarak yang mereka tempuh, sampel acak menunjukkan rata-rata 23.500 kilometer dan standar deviasi 3900 kilometer. Maka H0 = μ = 20.000, sedangkan alternatif hipotesisinya (H1) adalah lebih besar dari H0 (μ).

![Picture6](https://user-images.githubusercontent.com/71111983/170867337-4047cd85-8a87-42ef-9c92-70c0133e0aba.png)

### C.
Buatlah kesimpulan berdasarkan P-Value yang dihasilkan!

![Picture7](https://user-images.githubusercontent.com/71111983/170867416-53e1d49c-851c-4522-aabe-b357ea79c11d.png)

Untuk mendapatkan kesimpulan berdasarkan nilai p-value dari rata-rata jarak mobil dikendarai, kita akan mencari nilai z untuk mencari nilai p nya. Dari nilai z yang didapat menggunakan rumus tersebut yaitu sebesar 8.97. dengan cara mengurangi sampel acak menunjukkan rata-rata (X ̅) dengan rata-rata mobil dikemudikan (μ) kemudian dibagikan dengan pembagian standar deviasi (σ) dengan akar dari jumlah sampel mobil secara acak (n). kemungkinan p-value yang didapat itu lebih kecil dari 0 .00001 maka dapat disamakan dengan 0. Sehingga kesimpulan yang didapat adalah bahwa mobil dikemudikan rata-rata lebih dari 20.000 kilometer per tahun

## **Soal 3**
Diketahui perusahaan memiliki seorang data analyst ingin memecahkan
permasalahan pengambilan keputusan dalam perusahaan tersebut. Selanjutnya
didapatkanlah data berikut dari perusahaan saham tersebut.

![Picture8](https://user-images.githubusercontent.com/71111983/170867501-4a6679c9-d895-44e7-8dcf-8548a6c2ad25.png)

Dari data diatas berilah keputusan serta kesimpulan yang didapatkan dari hasil
diatas. Asumsikan nilai variancenya sama, apakah ada perbedaan pada
rata-ratanya (α= 0.05)? Buatlah :
A. H0 dan H1
B. Hitung Sampel Statistik
C. Lakukan Uji Statistik (df =2)
D. Nilai Kritikal
E. Keputusan
F. Kesimpulan

### A.
H0 dan H1

Untuk H0
![Picture9](https://user-images.githubusercontent.com/71111983/170867557-f1d114b8-4d25-4f96-a311-5dc9f7f261ca.png)

Untuk H1

![Picture10](https://user-images.githubusercontent.com/71111983/170867614-f99a801b-a039-4bc2-a6f5-e6e7b4effc86.png)

Didalam soal terdapat data analis dari sebuah perusahaan untuk memecahkan permasalahan. Dimana data tersebut terdapat 2 kota yaitu Bandung dan Bali. Dimana jumlah saham bandung 19 dan untuk bali 27. Kemudian untuk mean  di Bandung 3.64 dan Bali 2.79 dan yang terakhir standar deviasinya Bandung adalah 1.67 dan Bali 1.32. Dari data diatas berilah keputusan serta kesimpulan yang didapatkan dari hasil diatas. Asumsikan nilai variancenya sama dan α= 0.05. 

### B.
Hitung Sampel Statistik
``` 
tsum.test(mean.x=3.64, s.x = 1.67, n.x = 19, mean.y =2.79 , s.y = 1.32, n.y = 27, alternative = "greater", var.equal = TRUE)

```
. Selanjutnya untuk menghitung sampel statistik menggunakan tsum.test dimana kita melakukan satu sampel atau dua sampel, berdasarkan informasi ringkasan yang diberikan pengguna.  Kemungkinan outputnya identik dengan yang dihasilkan dengan t.test. menggunakan data . Dimana jumlah saham bandung 19 dan untuk bali 27. Kemudian untuk mean  di Bandung 3.64 dan Bali 2.79 dan yang terakhir standar deviasinya Bandung adalah 1.67 dan Bali 1.32. 

![Picture11](https://user-images.githubusercontent.com/71111983/170867678-3c9b6eb5-51c6-4547-a09b-face5eed10ff.png)

### C.
Lakukan Uji Statistik (df =2)
``` 
install.packages("mosaic")

library(mosaic)

plotDist(dist='t', df=2, col="red")

```
kemudian untuk melakukan uji statisik pad df = 2 pertama kita akan menggunakan library mosaic untuk membuat kurva yang dapat menjelaskan data pada df =2. Kita menggunakan distribusi student t dikarenakan inferensia ketika nilai varians dari suatu populasi tidak diketahui. 

![Picture12](https://user-images.githubusercontent.com/71111983/170867794-a099dc41-6561-4f5b-aa8c-d721bc622705.png)

### D.
Nilai Kritikal
``` 
qchisq(p = 0.05, df = 2, lower.tail = FALSE)
```
selnjutnya untuk mendapatkan nilai kritikal kita akan menggunakan qchisq dengan df = 2 sesuai dengan soal df = 2.

![Picture13](https://user-images.githubusercontent.com/71111983/170867879-699a6964-a566-416a-841d-48b82ae82789.png)

### E.
Keputusan

Selanjutnya untuk mencari keputusan, Teori Keputusan adalah berasal dari teori kemungkinan yang merupakan konsekuensi dari beberapa keputusan yang telah dievaluasi dan juga teori formal pengambilan keputusan di bawah ketidakpastian. Aksinya adalah : ({a}_{a∈A}) Kemungkinan konsekuensi : ({c}_{c∈C}) (tergantung pada keadaan dan tindakan) Maka keputusan dapat dibuat dengan t.test. 

### F.
Kesimpulan

kesimpulan yang didapat dari jawaban dari data-data diatas. Dikarenakan diatas kita menggunakan 2 jenis uji yaitu uji statistic dan juga menggunaan nilai kritikal. Uji statistik adalah perhitungan untuk menentukan apakah ada cukup bukti menolak atau menerima hipotesis dan nilai kritis adalah batasan nilai hasil pemeriksaan laboratorium, yang menunjukkan keadaan patologis di luar normal dan berpotensi membahayakan keselamatan jiwa bila tidak ditindaklanjuti dengan cepat..Yang didapatkan adalah perbedaan rata-rata yang terjadi tidak ada jika dilihat dari uji statistik dan akan ada tetapi tidak signifikan jika dipengaruhi nilai kritikal.

***
## **Soal 4**
Seorang Peneliti sedang meneliti spesies dari kucing di ITS . Dalam penelitiannya
ia mengumpulkan data tiga spesies kucing yaitu kucing oren, kucing hitam dan
kucing putih dengan panjangnya masing-masing.
Jika :
diketahui dataset https://intip.in/datasetprobstat1
H0 : Tidak ada perbedaan panjang antara ketiga spesies atau rata-rata panjangnya
sama
Maka Kerjakan atau Carilah:
A. Buatlah masing masing jenis spesies menjadi 3 subjek "Grup" (grup 1,grup
2,grup 3). Lalu Gambarkan plot kuantil normal untuk setiap kelompok dan
lihat apakah ada outlier utama dalam homogenitas varians.
B. carilah atau periksalah Homogeneity of variances nya , Berapa nilai p yang
didapatkan? , Apa hipotesis dan kesimpulan yang dapat diambil ?
C. Untuk uji ANOVA (satu arah), buatlah model linier dengan Panjang versus
Grup dan beri nama model tersebut model 1.
D. Dari Hasil Poin C, Berapakah nilai-p ? , Apa yang dapat Anda simpulkan
dari H0?
E. Verifikasilah jawaban model 1 dengan Post-hoc test Tukey HSD, dari nilai p
yang didapatkan apakah satu jenis kucing lebih panjang dari yang lain?
Jelaskan.
F. Visualisasikan data dengan ggplot2

### A.
Buatlah masing masing jenis spesies menjadi 3 subjek "Grup" (grup 1,grup
2,grup 3). Lalu Gambarkan plot kuantil normal untuk setiap kelompok dan
lihat apakah ada outlier utama dalam homogenitas varians.
``` 
Setuju
```
### A.
Buatlah masing masing jenis spesies menjadi 3 subjek "Grup" (grup 1,grup
2,grup 3). Lalu Gambarkan plot kuantil normal untuk setiap kelompok dan
lihat apakah ada outlier utama dalam homogenitas varians.
``` 
myFile  <- read.table(url("https://rstatisticsandresearch.weebly.com/uploads/1/0/2/6/1026585/onewayanova.txt")) 
dim(myFile)
head(myFile)
```
Peniliti sedang menilite sepesies dari kucing yang ada di ITS, kucing-kucing terebut memiliki 3 spesies yaitu : kucing oren, kucing hitam, dan kucing putih. Dataset kucing itu didapat dari  https://intip.in/datasetprobstat1. Buatlah masing masing jenis spesies menjadi 3 subjek "Grup" (grup 1,grup 2,grup 3). Lalu Gambarkan plot kuantil normal untuk setiap kelompok dan lihat apakah ada outlier utama dalam homogenitas varians. Langkah pertama mengambil data dari link yang telah disediadakan kemudian data-data file tersebut dibuat menjadi sebuah group

![Picture24](https://user-images.githubusercontent.com/71111983/170877925-29da8a3c-a46c-47b0-8950-0e6597090208.png)

Kemudian untuk melanjutnya kita akan membuat myFile atau data tersebut kedalam sbuah group
``` 
myFile$Group <- as.factor(myFile$Group)
myFile$Group = factor(myFile$Group,labels = c("Kucing Oren","Kucing Hitam","Kucing Putih"))
```

Setelah itu, dicek apakah dia menyimpan nilai di groupnya
``` 
class(myFile$Group)
```

Kemudian bagi kedalam tiap group, yang terdiri dari 3 bagian. yang memiliki nama Kucing Oren, Kucing Hitam, Kucing Putih
```
group1 <- subset(myFile, Group=="Kucing Oren")
group2 <- subset(myFile, Group=="Kucing Hitam")
group3 <- subset(myFile, Group=="Kucing Putih")
```

### B.
carilah atau periksalah Homogeneity of variances nya , Berapa nilai p yang
didapatkan? , Apa hipotesis dan kesimpulan yang dapat diambil ?
``` 
bartlett.test(Length~Group, data=dataoneway)
```
untuk mendapatkan Homogeneity of variancenya , p, dan kseimpulannya kita akan menggunakan fungsi bartlett.test. Dimana  menguji in- terdependensi antara variabel-variabel yang menjadi indi- kator suatu faktor oleh karena itu kita akan mendapatkan nilai p-value sebesar 0.8054 dan Kesimpulan yang didapatkan yaitu Bartlett's K-squared memiliki nilai sebesar 0.43292 dan df bernilai 2

### C.
Untuk uji ANOVA (satu arah), buatlah model linier dengan Panjang versus
Grup dan beri nama model tersebut model 1.
``` 
qqnorm(group1$Length)
qqline(group1$Length)
```
![Picture25](https://user-images.githubusercontent.com/71111983/170878301-175a3b1f-1288-431c-8430-da8d6c50eb8b.png)

### D.
Dari Hasil Poin C, Berapakah nilai-p ? , Apa yang dapat Anda simpulkan
dari H0?
``` 
p-value = 0.8054
```
maka Probabilitas (p-value) > 0,05 maka h0 diterima

### E.
Verifikasilah jawaban model 1 dengan Post-hoc test Tukey HSD, dari nilai p
yang didapatkan apakah satu jenis kucing lebih panjang dari yang lain?
Jelaskan.
``` 
model <- lm(Length~Group, data = oneWayData)
anova(model)
TukeyHSD(aov(model))
```

### F.
Visualisasikan data dengan ggplot2
``` 
library(ggplot2)
ggplot(dataoneway, aes(x = Group, y = Length)) + geom_boxplot(fill = "grey80", colour = "black") + scale_x_discrete() + xlab("Treatment Group") +  ylab("Length (cm)")
```

***
## **Soal 5**
Data yang digunakan merupakan hasil eksperimen yang dilakukan untuk
mengetahui pengaruh suhu operasi (100˚C, 125˚C dan 150˚C) dan tiga jenis kaca
pelat muka (A, B dan C) pada keluaran cahaya tabung osiloskop. Percobaan
dilakukan sebanyak 27 kali dan didapat data sebagai berikut: Data Hasil
Eksperimen. Dengan data tersebut:
a. Buatlah plot sederhana untuk visualisasi data
b. Lakukan uji ANOVA dua arah
c. Tampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk
setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi)
d. Lakukan uji Tukey
e. Gunakan compact letter display untuk menunjukkan perbedaan signifikan
antara uji Anova dan uji Tukey
Berikut adalah contoh daftar package dan fungsi yang dapat digunakan (dapat pula
menggunakan contoh lainnya)
● Packages: readr, ggplot2, multcompView, dplyr
● Function: aov, TukeyHSD, qplot, group_by, summarise, multcompLetters4

### A.
Buatlah plot sederhana untuk visualisasi data
``` 
GTL <- read_csv("GTL.csv")
head(GTL)

str(GTL)

qplot(x = Temp, y = Light, geom = "point", data = GTL) +facet_grid(.~Glass, labeller = label_both)
```
Membuat plot sederhana menggunakan visualisasi data yang berasal dari hasil eksperimen yang dilakukan untuk mengetahui pengaruh suhu operasi (100˚C, 125˚C dan 150˚C) dan tiga jenis kaca pelat muka (A, B dan C) pada keluaran cahaya tabung osiloskop. Percobaan dilakukan sebanyak 27 kali dan didapat data sebagai berikut: Data Hasil Eksperimen. Pertama kita akan menggunakan library seperti readr, ggplot2, multcompview, dplyr. Selanjutnya kita akan membaca file yang berasal dari soal yaitu file GTL.csv yang telah di berikan pada link yang ada di soal

![Picture15](https://user-images.githubusercontent.com/71111983/170868158-211cb60e-b040-4e86-b245-b9fca1619608.png)

Kemudian untuk membuat plot tersebut kita juga memerlukan obserasi menggunakan str pada glass,temp, dan light terseut. Untuk mengetahui struktur dari sebuah dataframe Anda dapat gunakan fungsi str() (str-ucture). Dengan fungsi ini Anda dapat memperoleh informasi lebih lengkap dari sebuah dataframe seperti banyaknya observation dan variable, nama-nama variable, tipe variable, dan beberapa nilai baris pertama untuk masing-masing variable.

![Picture16](https://user-images.githubusercontent.com/71111983/170868160-e408be42-c667-4f85-9bdc-8b49f138d736.png)

Dan yang terakhir untukk membuat plot tersebut kita akan menggunakan syntax qplot 

![Picture17](https://user-images.githubusercontent.com/71111983/170868167-f0005c89-09db-4002-aafa-0cc24632863c.png)


### B.
Lakukan uji ANOVA dua arah
``` 
GTL$Glass <- as.factor(GTL$Glass)

GTL$Temp_Factor <- as.factor(GTL$Temp)

str(GTL)

ujianova <- aov(Light ~ Glass*Temp_Factor, data = GTL)

summary(ujianova)
```
Kemudian kita disuruh untuk melakukan uji ANOVA 2 arah dimana membandingkan perbedaan rata-rata antara kelompok yang telah dibagi pada dua variabel independen (disebut faktor). Anda perlu memiliki dua variabel independen berskala data kategorik dan satu variabel terikat berskala data kuantitatif/numerik (interval atau rasio). Oleh karena itu membuat variabel as factor sebagai ANOVA

![Picture18](https://user-images.githubusercontent.com/71111983/170868230-cc154d34-ab0c-4615-b6df-759b3ffdc809.png)

Kemudian lakukan analisis of variance (aov)

![Picture19](https://user-images.githubusercontent.com/71111983/170868236-8418ca89-3154-4cd5-8710-060f9334d9ef.png)

### C.
Tampilkan tabel dengan mean dan standar deviasi keluaran cahaya untuk
setiap perlakuan (kombinasi kaca pelat muka dan suhu operasi)
``` 
tabel_summary <- group_by(GTL, Glass, Temp) %>%
  summarise(mean=mean(Light), sd=sd(Light)) %>%
  arrange(desc(mean))

print(tabel_summary)
```
Selanjutnya untuk menampilkan tabel dengan adanya mean dan standar deviasi keluaran cahaya untuk setiap perlakukan yang ada kita akan menggunakan syntax group_by dan juga summarise dikarenakan digunakan untuk meringkas beberapa nilai data menjadi satu nilai. Fungsi ini akan menjadi sangat berguna apabila digabungkan fungsi lain dalam dplyr. na.rm = TRUE memberikan hasil fungsi dengan meniadakan nilai missing.

![Picture20](https://user-images.githubusercontent.com/71111983/170868297-c98e42d0-2103-4708-b9fe-7738c6c15888.png)

### D.
Apakah Anda setuju dengan klaim tersebut?
``` 
ujitukey <- TukeyHSD(anova)

print(ujitukey)
```
kemudian uji tukey dengan cara menggunakan fungsi TukeyHSD yang sudah ada pada bahasa r 

![Picture21](https://user-images.githubusercontent.com/71111983/170868358-556e7ebd-d6a2-4fff-b804-4c951c680927.png)

### E.
Gunakan compact letter display untuk menunjukkan perbedaan signifikan
antara uji Anova dan uji Tukey
``` 
tukey <- multcompLetters4(anova, ujitukey)

print(tukey)

cld <- as.data.frame.list(tukey$`Glass:Temp_Factor`)

tabel_summary$Tukey <- cld$Letters

print(tabel_summary)
```
Yang terakhir kita akan menggunakan compact letter display untuk menunjukkan perbedaan yang signifikan antara kedua uji diatas yaitu uji Anova dan Tukey dengan cara membuat compact letter display menggunakan multcompletters4 

![Picture22](https://user-images.githubusercontent.com/71111983/170868406-811c0c53-4b60-4f5c-a696-cfb0618c3ed6.png)

Dan yang terakhir Tambahkan compact letter display tersebut ke tabel dengan means(rata-rata) dan sd.

![Picture23](https://user-images.githubusercontent.com/71111983/170868408-0b427fa6-2a4f-4aec-a0f3-8c50d6558dde.png)




