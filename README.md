# 📊 Public Procurement Risk Analysis and Risk Level Prediction

# 📊 Kamu İhale Risk Analizi ve Risk Seviyesi Tahmini


## 📌 Proje Hakkında / Project Overview

This project presents an end-to-end machine learning pipeline for analyzing public procurement data and predicting procurement risk levels.

Bu proje, kamu ihale verilerinin analiz edilmesi, risk faktörlerinin belirlenmesi ve makine öğrenmesi yöntemleri kullanılarak ihale risk seviyelerinin tahmin edilmesi amacıyla hazırlanmıştır.

Projede **Global Public Procurement Dataset (GPPD)** kullanılmıştır. Veri seti içerisinden Almanya'ya ait kamu ihale kayıtları analiz edilerek ihaleler:

- Düşük Risk
- Orta Risk
- Yüksek Risk

olmak üzere üç farklı sınıfa ayrılmıştır.

Çalışma kapsamında veri ön işleme, keşifsel veri analizi, özellik mühendisliği, risk skoru oluşturma ve makine öğrenmesi için veri hazırlama adımları uygulanmıştır.


---

# 🎯 Proje Amacı / Project Objective

Bu projenin temel amacı:

- Kamu ihalelerindeki risk faktörlerini analiz etmek,
- Rekabet, süre ve fiyat değişkenlerinin etkisini incelemek,
- İhale bazında risk göstergeleri oluşturmak,
- Makine öğrenmesi modelleri ile ihale risk seviyelerini tahmin etmektir.


Model, ihale süreçlerindeki:

- Rekabet seviyesi,
- Teklif bilgileri,
- İhale süreleri,
- Fiyat değişimleri,
- Risk göstergeleri

üzerinden risk tahmini gerçekleştirmek üzere hazırlanmıştır.


---

# 📂 Kullanılan Veri Seti / Dataset

Projede:

**Global Public Procurement Dataset (GPPD)**

kullanılmıştır.

Veri seti aşağıdaki ihale bilgilerini içermektedir:

- İhale prosedür bilgileri,
- Tedarik türleri,
- Alıcı bilgileri,
- Teklif sayıları,
- İhale süreç tarihleri,
- Tahmini ve gerçekleşen fiyat bilgileri,
- Risk göstergeleri.


Çalışmada veri boyutunun büyük olması nedeniyle veri setinin **Almanya (Germany)** kayıtları kullanılmıştır.

Ham veri dosyaları boyut nedeniyle GitHub repository içerisinde paylaşılmamıştır.


---

# ⚙️ 1. Environment Setup / Ortam Hazırlığı

Bu aşamada çalışma ortamı hazırlanmış ve gerekli Python kütüphaneleri yüklenmiştir.

Google Drive bağlantısı kurularak büyük boyutlu veri dosyalarına erişim sağlanmıştır.

Kullanılan temel kütüphaneler:

- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly


Amaç:

- Veri analiz ortamını hazırlamak,
- Büyük veri dosyalarını işleyebilmek,
- Sonraki analiz ve modelleme aşamalarına uygun çalışma ortamı oluşturmaktır.


---

# 💾 2. Dataset Loading / Veri Setinin Yüklenmesi

Bu aşamada ihale veri seti çalışma ortamına yüklenmiş ve ilk kontroller gerçekleştirilmiştir.

Gerçekleştirilen işlemler:

- Veri setinin okunması,
- Veri boyutunun kontrol edilmesi,
- Kolon isimlerinin incelenmesi,
- Veri tiplerinin kontrol edilmesi,
- İlk gözlemlerin analiz edilmesi.


Bu aşama ile veri yapısı anlaşılmış ve analiz süreci için gerekli değişkenler belirlenmiştir.


---

# 🔍 3. Exploratory Data Analysis (EDA) / Keşifsel Veri Analizi

Veri setinin genel yapısını anlamak amacıyla istatistiksel ve görsel analizler gerçekleştirilmiştir.

Yapılan analizler:

- Sayısal değişkenlerin istatistiksel analizi,
- Kategorik değişkenlerin incelenmesi,
- Eksik değer analizi,
- Değişken dağılımlarının incelenmesi,
- Korelasyon analizi.


Kullanılan yöntemler:

- Descriptive statistics
- Missing value analysis
- Pearson correlation matrix
- Veri dağılım grafikleri


Bu aşamada veri içerisindeki önemli değişkenler ve veri kalitesi problemleri belirlenmiştir.


---

# 🧹 4. Data Preprocessing / Veri Ön İşleme

Ham veri, analiz ve modelleme için uygun hale getirilmiştir.

Gerçekleştirilen işlemler:

- Gereksiz kolonların kaldırılması,
- Yüksek eksiklik oranına sahip kolonların çıkarılması,
- Veri tiplerinin düzenlenmesi,
- Tarih değişkenlerinin datetime formatına çevrilmesi.


Ayrıca tarih değişkenlerinden yeni süre özellikleri oluşturulmuştur:

- Submission period
- Decision period
- Decision duration days
- Total process duration


Amaç:

Veriyi temizlemek ve özellik mühendisliği aşamasına uygun hale getirmektir.


---

# ⚙️ 5. Missing Value Handling / Eksik Değer Yönetimi

Bu aşamada veri setindeki eksik değerler analiz edilmiş ve uygun yöntemlerle ele alınmıştır.

Uygulanan işlemler:

- Eksik değer oranlarının hesaplanması,
- %90'dan fazla eksik değer içeren kolonların değerlendirilmesi,
- Gereksiz eksik kolonların kaldırılması,
- Modelleme aşaması için uygun doldurma yöntemlerinin belirlenmesi.


Modelleme sırasında:

Sayısal değişkenler:
- Median değer ile doldurulmuştur.

Kategorik değişkenler:
- En sık görülen değer ile doldurulmuştur.


---

# 📦 6. Outlier Analysis / Aykırı Değer Analizi

Sayısal değişkenlerdeki sıra dışı değerler incelenmiştir.

Özellikle:

- İhale fiyatları,
- Teklif sayıları,
- Süre değişkenleri

analiz edilmiştir.


Aşırı sağa çarpık dağılıma sahip değişkenlerde:

**Log1p dönüşümü**

uygulanmıştır.


Log dönüşümü uygulanan bazı değişkenler:

- tender_estimatedprice
- tender_finalprice
- decision_duration_days
- submission_period
- tender_recordedbidscount


Amaç:

Aykırı değerlerin model performansına olan olumsuz etkisini azaltmaktır.


---

# ⚙️ 7. Feature Engineering / Özellik Mühendisliği

Ham veri içerisinden model performansını artırabilecek yeni özellikler oluşturulmuştur.


## Rekabet Özellikleri

### low_competition

Az teklif verilen ihaleleri belirlemek amacıyla oluşturulmuştur.

### has_bids

İhalede teklif bulunup bulunmadığını gösterir.


## Süre Özellikleri

Oluşturulan değişkenler:

- submission_period
- decision_period
- decision_duration_days
- total_process_duration


## Risk Özellikleri

Risk göstergeleri kullanılarak:

```
risk_indicator_count
```

isimli toplam risk skoru oluşturulmuştur.


---

# 🚩 Risk Seviyesi Oluşturma / Risk Level Creation

Modelin hedef değişkeni olan:

```
risk_level
```

risk göstergeleri kullanılarak oluşturulmuştur.


Kullanılan risk göstergeleri:

- corr_nocft
- corr_proc
- corr_decp
- corr_singleb
- corr_subm
- corr_buyer_concentration
- corr_tax_haven


Bu değişkenlerin toplamı alınarak:

```
risk_indicator_count
```

oluşturulmuştur.


Risk skoruna göre sınıflandırma:

| Risk Skoru | Risk Seviyesi |
|---|---|
| 0-1 | Düşük Risk |
| 2 | Orta Risk |
| 3+ | Yüksek Risk |


Modelleme aşamasında veri sızıntısını önlemek amacıyla risk seviyesini oluşturan risk kolonları model girişlerinden çıkarılmıştır.


---

# 🎯 8. Feature Selection / Özellik Seçimi

Bu aşamada makine öğrenmesi modellerinde kullanılacak özellikler belirlenmiştir.


Amaç:

- Gereksiz değişkenleri kaldırmak,
- Tekrarlayan bilgileri azaltmak,
- Model karmaşıklığını azaltmak,
- Daha anlamlı özelliklerle tahmin performansını artırmaktır.


Yapılan işlemler:

- Korelasyon analizi,
- Özellik değerlendirmesi,
- Risk kolonlarının model girdilerinden çıkarılması.


---

# 🤖 9. Data Preparation for Machine Learning / Makine Öğrenmesi İçin Veri Hazırlama

Seçilen özellikler makine öğrenmesi algoritmalarına uygun hale getirilmiştir.


## Sayısal Değişkenler

Uygulanan işlemler:

- Eksik değer doldurma,
- Ölçeklendirme.


## Kategorik Değişkenler

Uygulanan işlemler:

- Eksik değer doldurma,
- One-Hot Encoding.


## Target Encoding

Risk seviyeleri:

- Düşük Risk
- Orta Risk
- Yüksek Risk

LabelEncoder kullanılarak sayısal değerlere dönüştürülmüştür.


## Train-Test Split

Veri seti:

- %80 eğitim,
- %20 test

olarak ayrılmıştır.


`stratify` kullanılarak risk sınıflarının eğitim ve test veri setlerinde dengeli kalması sağlanmıştır.


---

# 🛠️ Kullanılan Teknolojiler

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Plotly
- Google Colab


---

# 📁 Proje Yapısı

```
Ihale-Risk-Tahmini/

│
├── ihale_risk_prediction.ipynb
├── README.md
└── requirements.txt
```


---

# 📌 Sonuç / Conclusion

Bu proje kapsamında kamu ihale verileri analiz edilmiş, risk göstergeleri kullanılarak yeni özellikler oluşturulmuş ve makine öğrenmesi modelleri için gerekli veri hazırlama süreci tamamlanmıştır.

Oluşturulan pipeline ile ihale süreçlerindeki risk seviyelerinin tahmin edilmesi hedeflenmektedir.
