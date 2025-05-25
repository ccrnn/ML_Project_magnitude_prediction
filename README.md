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

*Bu adımda, projede kullanılacak kütüphaneler yüklendi ve veri seti içe aktarıldı. Ardından temel istatistiksel incelemeler (`head`, `info`, `describe`) yapılarak veri setinin yapısı, sütun türleri, eksik değer durumu ve özet istatistikleri analiz edildi.*

* **2.ADIM: Eksik Değerlerin İncelenmesi ve Temizliği**
* 2.1.Eksik Değerlerin Tespiti
* 2.2.Eksik Değerler İçin Strateji Belirlenmesi ve Uygulama

*Bu adımda, veri setindeki eksik değerler detaylı şekilde incelendi. Eksik verilerin yoğun olduğu sütunlar belirlendi ve sıralandı. Bu sütunlar için uygun stratejiler geliştirildi. Eksik değerler için tercih edilen yöntem doldurma oldu. Sayısal sütunlardaki eksik veriler medyan, kategorik sütunlardaki eksik veriler mod ile dolduruldu.Bir sütun haricinde (nst sütunu) diğer sütunlarda eksik değer yüzdesi çok yüksek olmadığı için doldurma yöntemi tercih edildi. En çok eksik değer sahip sütunun silinmeme nedeni ise özelliği nedeniyle hedef değişkenin tahminini etkileyebilecek olmasıydı.*

* **3.ADIM: Veri Tiplerinin Dönüştürülmesi**
* 3.1.time ve uptated Sütunlarını datetime Formatına Çevrilmesi
* 3.2.time sütunundan yeni zamansal özellikler türetme

*Bu adımda, zamanla ilgili `time` ve `updated` sütunları uygun analizler yapılabilmesi için `datetime` formatına dönüştürüldü. Ardından `time` sütunundan yıl, ay, gün, saat gibi yeni zamansal değişkenler türetilerek veri setine anlamlı özellikler eklendi.*

* **4. ADIM: Detaylı Keşifsel Veri Analizi (EDA) ve Görselleştirmeler**
* 4.1.Hedef Değişken (mag) Dağılımı
* 4.2.Coğrafi Dağılım Analizi
* 4.3.Zaman Bazlı Özelliklerin mag ile İlişkisi
* 4.4.Sayısal Özellikler Arası Korelasyon Analizi
* 4.5.Kategorik Özelliklerin Analizi

*Bu adımda, hedef değişken olan `mag` (deprem büyüklüğü) dağılımı incelendi ve coğrafi konumlara göre dünya haritası üzerinde görselleştirildi. Zaman bazlı özellikler (yıl, ay, saat) ile büyüklük arasındaki ilişkiler analiz edildi. Sayısal değişkenler arası korelasyon matrisiyle ilişkiler belirlendi. Son olarak kategorik değişkenlerin `mag` üzerindeki etkileri incelenerek veri yapısı daha iyi anlaşıldı.*

* **5. ADIM: Özellik Mühendisliği ve Seçimi**
* 5.1. Kategorik Özelliklerin İşlenmesi (One-Hot Encoding)
* 5.2. Yüksek Kardinaliteli Kategorik Özelliklerin İşlenmesi
* 5.3. Eksik Değerlerin ve Gereksiz Sütunların Son Kez İşlenmesi

*Bu adımda, modellemeye uygun hale getirmek için kategorik değişkenler one-hot encoding yöntemiyle sayısal forma dönüştürüldü. Yüksek benzersiz değer içeren değişkenlerde anlamlı gruplamalar yapılarak veri boyutu kontrol altında tutuldu. Ayrıca, eksik değerler son kez gözden geçirilip uygun şekilde temizlendi ve modellemeye katkı sağlamayan sütunlar veri setinden çıkarıldı.*

* **6. ADIM: Model Eğitimi ve Değerlendirilmesi**
* 6.1.Veri Setinin Test-Train Bölünmesi 
* 6.2.Random Forest Regressor Modeli ile Eğitilmesi ve Temel Değerlendirmesi
* 6.3.Hiperparametre Optimizasyonu 
* 6.4. Model değerlendirme 

*Bu adımda, veri seti eğitim ve test olarak 80/20 oranında bölündü. Random Forest Regressor modeli ile temel bir eğitim gerçekleştirildi ve performans metrikleri hesaplandı. Ardından RandomizedSearchCV yöntemiyle hiperparametre optimizasyonu yapılarak modelin başarısı artırıldı. Son olarak optimize edilen model MAE, MSE, RMSE ve R² skorları ile değerlendirildi.*

**Model Seçim Aşaması**

4 farklı model proje için test edilmiştir. Bunlar; `Linear Regression, Decision Tree, LightGBM ve Random Forest.` Daha sonra modellerin performans metrikleri değerlendirilmişitr. Ayrıca çapraz doğrulama (5Fold CV) da uygulanmıştır. 


| Modeller | RMSE | MAE | R2 Score | Çapraz Doğrulama (5Fold CV) Sonucu RMSE |
| --|:-------:| -----:|-----:|-----:|
| Linear Regression | 0.2716 | 0.2029 | 0.8216 | 0.2929 |
| Decision Tree | 0.2829 | 0.1847 | 0.8064 | 0.3203 |
| LightGBM | 0.2106 | 0.1521 | 0.8928 | 0.2360 |
| Random Forest | 0.1973 | 0.1344 | 0.9058 | 0.2292 |

-Random Forest, en düşük RMSE ve MAE değerlerine ve en yüksek R2 skoruna (%90.58) sahiptir Bu, modelin veri setindeki karmaşık ilişkileri yakalamada çok başarılı olduğunu göstermektedir.

-Çapraz doğrulama (5Fold CV) sonucu RMSE değerlerinde ise en düşük RMSE değeri Random Forest Regressor’a aittir. 

**Sonuç olarak performans açısından en başırılı model Random Forest olmuştur ve projeye onunla devam edilmiştir.**

# Metrikler

Random Forest modelinin optimize önesi ve sonrası metriklerinin karşılaştırılması:
| Metrik   | Optimize Edilmeden | Optimize Edildikten Sonra | Değişim  | Yorumu                      |
| -------- | ------------------ | ------------------------- | -------- | --------------------------- |
| *RMSE* | 0.1973             | 0.1963                    | ↓ 0.0010 | Hata biraz azaldı           |
| *MAE*  | 0.1344             | 0.1336                    | ↓ 0.0008 | Ortalama mutlak hata  azaldı |
| *MSE*  | 0.0389             | 0.0385                    | ↓ 0.0004 | Kareli hata da azaldı       |
| *R²*   | 0.9058             | 0.9068                    | ↑ 0.0010 | Modelin açıklama gücü arttı |

* Optimize sonrasında modelin hataları hafifçe azaldı ve R2 skoru yani modelin doğru tahmin edebilme oranı yükseldi.
* Model optimize öncesinde de iyi bir performans gösteriyordu. Ancak optimize sonrası artık deprem büyüklüğü değerlerindeki değişimin %90.68 ni açıklayabiliyor. Yani gerçek deprem büyüklüklerine çok yakın sonuçlar üretiyor ve daha büyük ölçüde doğru tahmin ediyor. Optimize soncunda küçük ama pozitif bir iyileşme olmuştur. Modelin açıklayıcığı arttı ve daha dengeli hale geldi.



