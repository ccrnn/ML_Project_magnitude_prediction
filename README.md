# ML_Project_magnitude_prediction

# Giriş 
  Projemde gözetimli öğrenme tekniklerinden girdi özelliklerine göre sürekli değer tahmin etme yani bir regresyon problemi çalışmak istiyordum. Bu nedenle amacıma ve veri seti seçim kurallarına uygun olacak şekilde makine öğrenmesini daha temelden ve sindirerek öğrenmek için bu projeyi geliştirmeye karar verdim. 

## Proje Hakkında Bilgiler

Bu projenin temel amacı, 2010-2023 yılları arasında meydana gelen küresel deprem verilerini kullanarak, depremin büyüklüğünü (magnitude) çeşitli özelliklere (derinlik, konum, sismik istasyon sayısı vb.) göre tahmin edebilen bir model geliştirmektir. 


**_Veri Seti ve Seçim Sebepleri_**

Kaggle platformundan seçilen 2010-2023 yıllarında kaydedilen depremleri içeren (Earthquake Data 2010-2023 Latest) veri seti, yaklaşık 243.000 satır ve 22 sütundan oluşmaktadır. Bu veri setinde her bir satır meydana gelen bir depremi temsil etmektedir. Sütunlar ise depreme ait çeşitli özellikleri bize vermektedir.

Veri setinin gerçek dünya verisi olması, bilimsel olarak anlamlı ve güncel olması, proje kurallarına göre yeterli büyüklükte olması ve regresyon problemine uygun olması bu veri setini seçme sebeplerimdir.

**_Proje Adımları ve Kullanılan Teknikler_**

* **1.ADIM: Veri Setini Hazırlama ve Genel Bakış**
* 1.1.Gerekli Kütüphanelerin ve Veri Setinin Yüklenmesi
* 1.2.Veri Setine Genel Bakış(Temel EDA/Nümerik EDA)
* **2.ADIM: Eksik Değerlerin İncelenmesi ve Temizliği**
* 2.1.Eksik Değerlerin Tespiti
* 2.2.Eksik Değerler İçin Strateji Belirlenmesi ve Uygulama
* **3.ADIM: Veri Tiplerinin Dönüştürülmesi**
* 3.1.time ve uptated Sütunlarını datetime Formatına Çevrilmesi
* 3.2.time sütunundan yeni zamansal özellikler türetme
* **4. ADIM: Detaylı Keşifsel Veri Analizi (EDA) ve Görselleştirmeler**
* 4.1.Hedef Değişken (mag) Dağılımı
* 4.2.Coğrafi Dağılım Analizi
* 4.3.Zaman Bazlı Özelliklerin mag ile İlişkisi
* 4.4.Sayısal Özellikler Arası Korelasyon Analizi
* 4.5.Kategorik Özelliklerin Analizi
* **5. ADIM: Özellik Mühendisliği ve Seçimi**
* 5.1. Kategorik Özelliklerin İşlenmesi (One-Hot Encoding)
* 5.2. Yüksek Kardinaliteli Kategorik Özelliklerin İşlenmesi
* 5.3. Eksik Değerlerin ve Gereksiz Sütunların Son Kez İşlenmesi
* **6. ADIM: Model Eğitimi ve Değerlendirilmesi**
* 6.1.Veri Setinin Test-Train Bölünmesi 
* 6.2.Random Forest Regressor Modeli ile Eğitilmesi ve Temel Değerlendirmesi
* 6.3.Hiperparametre Optimizasyonu 
* 6.4. Model değerlendirme 

