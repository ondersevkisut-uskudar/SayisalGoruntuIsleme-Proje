# 🧬 Sayısal Görüntü İşleme: ISIC Deri Lezyonu Analizi ve İyileştirme

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/OpenCV-Image%20Processing-green)
![Data](https://img.shields.io/badge/Pandas-Data%20Analysis-orange)
![Visualization](https://img.shields.io/badge/Matplotlib-Visualization-red)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

Bu proje, **Üsküdar Üniversitesi Yapay Zeka Mühendisliği**, Sayısal Görüntü İşleme dersi vize ödevi kapsamında geliştirilmiştir. **ISIC 2018 (Skin Lesion Analysis Towards Melanoma Detection)** veri seti kullanılarak dermatoskopik görüntülerin işlenmesi, gürültüden arındırılması ve detaylarının belirginleştirilmesi hedeflenmiştir.

Proje, ham görüntü verisinden başlayarak Frekans Alanı (FFT) işlemlerine kadar uzanan kapsamlı bir **Görüntü İşleme Hattı (Pipeline)** sunmaktadır.

## 📋 İçindekiler
- [Proje Özeti](#-proje-özeti)
- [Dosya Yapısı](#-dosya-yapısı)
- [Kullanılan Teknolojiler](#-kullanılan-teknolojiler)
- [Akıllı Veri Yönetimi](#-akıllı-veri-yönetimi-smart-data-handling)
- [Kurulum ve Çalıştırma](#-kurulum-ve-çalıştırma)
- [Proje Adımları ve Teknikler](#-proje-adımları-ve-teknikler)
- [Sonuçlar](#-sonuçlar)

## 🔍 Proje Özeti
Dermatoskopik görüntüler genellikle kıl, düşük kontrast veya sensör gürültüsü gibi analiz yapmayı zorlaştıran unsurlar içerir. Bu çalışmanın amacı:
1.  Veri setini yapısal ve istatistiksel olarak analiz etmek.
2.  Görüntüleri farklı renk uzaylarında (RGB, Grayscale) incelemek.
3.  Lezyon (ben/tümör) detaylarını ortaya çıkarmak için iyileştirme teknikleri uygulamak.
4.  Veri setini yapay zeka eğitimine hazırlamak için zenginleştirmektir (Augmentation).

## 📂 Dosya Yapısı
Repo içerisindeki temel dosyalar şunlardır:

* **`Odev.ipynb`**: Tüm görüntü işleme adımlarını (7 aşama) içeren ana Jupyter Notebook dosyası].
* **`data/`**: Veri setinin bulunduğu klasör (Kod çalışınca otomatik oluşturulur).
* **`README.md`**: Proje dokümantasyonu.

## 🛠 Kullanılan Teknolojiler
Proje **Python** dili ile geliştirilmiş olup aşağıdaki kütüphaneler kullanılmıştır:

* **Veri İşleme:** `pandas`, `numpy`, `os`
* **Görselleştirme:** `matplotlib`, `seaborn`
* **Görüntü İşleme:** `opencv-python` (cv2)

## ⚙️ Akıllı Veri Yönetimi (Smart Data Handling)
Bu proje, büyük veri setlerinin yönetimini kolaylaştırmak için **otomatik bir kontrol mekanizması** içerir:

* **Otomatik Algılama:** Kod çalıştırıldığında `data` klasörünü kontrol eder.
* **Otomatik Kurulum:** Eğer klasör boşsa ancak proje dizininde `archive.zip` dosyası varsa, bu dosyayı otomatik olarak çıkarır.
* **Kullanıcı Dostu:** Veri seti hiç bulunamazsa, indirme linkini ve talimatları terminal ekranında gösterir.

## 🚀 Kurulum ve Çalıştırma

Repo, veri seti (780MB+) dahil olmak üzere "tak-çalıştır" (plug-and-play) mantığında hazırlanmıştır.

1.  **Repoyu klonlayın:**
    ```bash
    git clone https://github.com/ondersevkisut-uskudar/SayisalGoruntuIsleme-Proje.git
    cd SayisalGoruntuIsleme-Proje
    ```
    *(Not: Veri seti repoya dahil olduğu için indirme işlemi internet hızınıza bağlı olarak zaman alabilir.)*

2.  **Gerekli kütüphaneleri yükleyin:**
    ```bash
    pip install pandas numpy matplotlib seaborn opencv-python
    ```

3.  **Notebook'u çalıştırın:**
    VS Code veya Jupyter Lab kullanarak `254329023_onder_sevki_sut.ipynb` dosyasını açın ve **"Run All"** diyerek tüm hücreleri çalıştırın. Sistem veri setini otomatik olarak algılayacak ve işlemleri başlatacaktır.

## 📊 Proje Adımları ve Teknikler

Proje 7 ana teknik adımdan oluşmaktadır:

### 1. Veri Analizi (EDA)
* 2200+ görüntünün çözünürlük, boyut ve kanal analizi yapıldı.
* Sınıf dağılımı (Actinic keratosis, Melanoma vb.) görselleştirildi.

### 2. Görselleştirme
* Görüntülerin RGB ve Grayscale versiyonları karşılaştırıldı.
* Histogram analizleri ile renk kanallarının (R, G, B) yoğunluk dağılımları incelendi.

### 3. Görüntü İyileştirme
* **Kontrast Germe:** Piksel değerleri 0-255 aralığına yayıldı.
* **Histogram Eşitleme:** RGB görüntülerde renk bozulmasını önlemek için **YCrCb** renk uzayı kullanıldı (Sadece Y kanalı eşitlendi).
* **Gamma Düzeltme:** $\gamma=0.5$ değeri ile koyu renkli lezyon detayları ortaya çıkarıldı.

### 4. Gürültü Azaltma (Noise Reduction)
* **Median Blur** ve **Gaussian Blur** karşılaştırıldı.
* **Sonuç:** Median Blur, lezyon sınırlarını (kenarları) koruma konusunda Gaussian Blur'a göre daha başarılı bulundu.

### 5. Veri Çoğaltma (Augmentation)
* Rastgele Döndürme (Rotation) ve Aynalama (Horizontal Flip) işlemleri uygulandı.

### 6. Frekans Alanı İşlemleri (FFT)
* Görüntü Fourier Dönüşümü ile frekans spektrumuna alındı.
* **Alçak Geçiren Filtre (Low Pass Filter)** uygulanarak yüksek frekanslı gürültüler (kıl, ince detaylar) temizlendi.

### 7. Keskinleştirme ve Ölçekleme
* **Unsharp Masking** ile lezyon kenarları belirginleştirildi.
* **Bicubic Interpolation** ile görüntü kalitesi bozulmadan 2x büyütme (Zoom) yapıldı.

## 🏆 Sonuçlar

* **Kenar Koruma:** Deri lezyonu segmentasyonu için **Median Blur** tekniğinin en uygun ön işleme adımı olduğu gözlemlendi.
* **Dijital Kıl Temizleme:** FFT ve Alçak Geçiren Filtre uygulaması, görüntüdeki kılları yok etmede etkili oldu ancak görüntüde bulanıklığa yol açtı.
* **Detay Analizi:** Gamma düzeltmesi ($\gamma=0.5$) ve Histogram Eşitleme kombinasyonu, lezyonun iç yapısını en net gösteren yöntem oldu.

---
**Geliştirici:** Önder Şevki Süt  
**Ders:** Yapay Zeka Mühendisliği - Sayısal Görüntü İşleme
