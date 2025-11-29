# 🔬 Sayısal Görüntü İşleme: ISIC Deri Lezyonu Analizi ve İyileştirme

Bu proje, **Üsküdar Üniversitesi Yapay Zeka Mühendisliği**, Sayısal Görüntü İşleme dersi vize ödevi kapsamında geliştirilmiştir. Projenin temel amacı, **ISIC 2018 (Skin Lesion Analysis Towards Melanoma Detection)** veri seti kullanılarak dermatoskopik görüntülerin işlenmesi, iyileştirilmesi ve analize hazır hale getirilmesidir.

## 📂 Proje İçeriği ve İşlem Hattı (Pipeline)

Proje, ham görüntü verisinden başlayarak ileri seviye frekans alanı filtrelemeye kadar uzanan **7 aşamalı** bir görüntü işleme hattını kapsar:

1.  **Veri Analizi (EDA):** Çözünürlük, kanal ve sınıf dağılımı analizleri.
2.  **Görselleştirme:** RGB ve Grayscale karşılaştırmaları, kanal bazlı histogram analizleri.
3.  **Görüntü İyileştirme:** Kontrast germe, Histogram eşitleme (YCrCb) ve Gamma düzeltme.
4.  **Gürültü Azaltma:** Median ve Gaussian Blur tekniklerinin kenar koruma (edge preserving) performanslarının kıyaslanması.
5.  **Veri Çoğaltma (Augmentation):** Rastgele döndürme ve aynalama işlemleri.
6.  **Frekans Alanı İşlemleri (FFT):** Fourier Dönüşümü ve Alçak Geçiren Filtre (Low Pass Filter) ile gürültü temizleme.
7.  **Keskinleştirme ve Ölçekleme:** Unsharp Masking ve Bicubic Interpolation (2x Zoom) teknikleri.

## ⚙️ Akıllı Veri Yönetimi (Smart Data Handling)

Proje, veri setinin kurulumunu kolaylaştırmak için **otomatik kontrol mekanizması** içerir:

* **Otomatik Kontrol:** Kod çalıştırıldığında `data` klasörünün dolu olup olmadığını kontrol eder.
* **Otomatik Zip Çıkarma:** Eğer veri klasörü boşsa ancak proje dizininde `archive.zip` dosyası varsa, bu dosyayı otomatik olarak tespit eder ve çıkarır.
* **Kullanıcı Yönergesi:** Veri seti hiç bulunamazsa, kullanıcıya indirme linkini ve yapması gerekenleri adım adım terminal ekranında gösterir.

## 🛠️ Kurulum ve Çalıştırma

Repo, veri seti (780MB+) dahil olmak üzere "tak-çalıştır" (plug-and-play) mantığında hazırlanmıştır.

### 1. Depoyu Klonlayın

git clone https://github.com/ondersevkisut-uskudar/SayisalGoruntuIsleme-Proje.git  
cd SayisalGoruntuIsleme-Proje

*(Not: Veri seti repoya dahil olduğu için indirme işlemi internet hızınıza bağlı olarak zaman alabilir.)*

### 2. Gerekli Kütüphaneleri Yükleyin
pip install pandas numpy matplotlib seaborn opencv-python

### 3. Projeyi Çalıştırın
* VS Code veya Jupyter Lab kullanarak `254329023_onder_sevki_sut.ipynb` dosyasını açın.
* "Run All" diyerek tüm hücreleri çalıştırın.
* *Sistem veri setini otomatik olarak algılayacak ve işlemleri başlatacaktır.*

## 📊 Veri Seti Hakkında
* **Kaynak:** [ISIC 2018 Challenge](https://challenge.isic-archive.com/data/#2018) / Kaggle
* **İçerik:** Actinic keratosis, Melanoma, Nevus gibi farklı deri hastalığı sınıflarına ait dermatoskopik görüntüler.
* **Yapı:** JPG Formatı, RGB, 2200+ Görüntü.

## 👨‍💻 Geliştirici
* **Ad Soyad:** Önder Şevki Süt
* **Bölüm:** Yapay Zeka Mühendisliği
* **Ders:** Sayısal Görüntü İşleme

---
*Bu proje eğitim amaçlı hazırlanmıştır.*
