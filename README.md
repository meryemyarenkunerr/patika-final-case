# Kredi Kartı Harcama Analizi

Bu proje, kredi kartı işlem verilerini analiz ederek kullanıcı harcama davranışlarını anlamaya yönelik kapsamlı bir veri analizi çalışmasıdır.

## 📊 Proje Hakkında

Bu analiz, iki ayrı veri setini (kullanıcı bilgileri ve işlem verileri) birleştirerek kredi kartı harcamalarındaki örüntüleri keşfetmeyi amaçlar. Proje, veri temizleme, görselleştirme ve istatistiksel analiz adımlarını içerir.

## 📁 Veri Setleri

### 1. users.csv
- **User**: Kullanıcı ID'si
- **Card**: Kart numarası
- **Year**: Kartın çıkarıldığı yıl
- **Month**: Kartın çıkarıldığı ay
- **Day**: Kartın çıkarıldığı gün
- **Gender**: Cinsiyet
- **Per Capita Income - Zipcode**: Posta kodu bazında kişi başı gelir
- **Yearly Income - Person**: Kişinin yıllık geliri
- **Total Debt**: Toplam borç
- **FICO Score**: Kredi skoru
- **Num Credit Cards**: Sahip olunan kredi kartı sayısı
- **Address**: Adres bilgileri (City, State, Zipcode, Apartment)
- **Current Age**: Mevcut yaş
- **Retirement Age**: Emeklilik yaşı

![](images/screenshots/users_head.png)
![](images/screenshots/users_info.png)

### 2. transactions.csv
- **User**: Kullanıcı ID'si
- **Card**: Kart numarası
- **Year/Month/Day/Time**: İşlem zamanı
- **Amount**: İşlem tutarı
- **Use Chip**: Chip kullanımı
- **Merchant Name**: Satıcı adı
- **Merchant City/State**: Satıcı konumu
- **Zip**: Posta kodu
- **MCC**: Merchant Category Code
- **Errors?**: Hata bilgisi
- **Is Fraud?**: Dolandırıcılık durumu

![](images/screenshots/transactions_head.png)
![](images/screenshots/transactions_info.png)

## 🛠️ Kullanılan Teknolojiler

- **Python 3.x**
- **pandas**: Veri manipülasyonu ve analizi
- **numpy**: Sayısal hesaplamalar
- **matplotlib**: Temel görselleştirme
- **seaborn**: Gelişmiş görselleştirme
- **jupyter**: Etkileşimli analiz ortamı

## 📋 Kurulum

1. Gerekli kütüphaneleri yükleyin:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

2. Proje dosyalarını klonlayın veya indirin

3. Veri dosyalarını (`users.csv` ve `transactions.csv`) proje dizinine yerleştirin

4. Jupyter Notebook'u başlatın:

```bash
jupyter notebook proje.ipynb
```

## 🔄 Veri Ön İşleme Adımları

### Users Veri Seti
- ✅ Para birimi işaretlerinin ($) kaldırılması

![](images/screenshots/dollar_sign_remove.png)

- ✅ Numerik sütunların uygun veri tipine dönüştürülmesi

![](images/screenshots/numeric_to_string_users.png)

- ✅ Boş değerlerin uygun şekilde doldurulması

![](images/screenshots/fill_nan_users.png)

- ✅ Tekrarlayan kayıtların temizlenmesi

![](images/screenshots/duplicates_users.png)

### Transactions Veri Seti
- ✅ Online işlemlerin uygun şekilde etiketlenmesi

![](images/screenshots/online2.png)
![](images/screenshots/online1.png)

- ✅ Tarih sütunlarının datetime formatına birleştirilmesi

![](images/screenshots/datetime_transactions.png)

- ✅ Binary sütunların (Yes/No) numerik formata (0/1) dönüştürülmesi

![](images/screenshots/binary_transactions.png)

- ✅ Hata durumlarının kategorize edilmesi

![](images/screenshots/errors_transactions.png)

- ✅ Tekrarlayan kayıtların temizlenmesi

![](images/screenshots/duplicates_transactions.png)

### Veri Setlerinin Birleştirilmesi
İki veri seti "User" sütunu üzerinden inner join ile birleştirildi.

![](images/screenshots/data_merging.png)

## 📈 Analiz Sonuçları

### 1. En Fazla Harcama Yapılan Şehirler

![](images/graphs/homework_1.png)
![](images/graphs/en_fazla_harcama_10.png)

**Bulgular:**
- En çok harcama yapılan şehir: **La Verne**
- Online işlemler 4. sırada yer alıyor
- Fiziksel mağaza vs. online alışveriş dengesi gözlemleniyor

### 2. Saatlik Harcama Dağılımı

![](images/graphs/homework_2.png)
![](images/graphs/saatlik_harcama.png)

**Bulgular:**
- **Sabah 06:00**: En yüksek harcama yoğunluğu
- **Öğle 13:00**: Öğle molası harcama artışı
- **Akşam 20:00**: İkinci büyük harcama dalgası
- **Gece 00:00-04:00**: En düşük harcama dönemı

### 3. Cinsiyete Göre Harcama

![](images/graphs/homework_3.png)
![](images/graphs/cinsiyete_gore_harcama.png)

**Bulgular:**
- Kadın ve erkek kullanıcılar arasında dengeli harcama dağılımı
- Kadın kullanıcılar hafif üstünlük gösteriyor
- Cinsiyet bazında büyük fark gözlenmiyor

### 4. Gelir vs. Harcama İlişkisi

![](images/graphs/homework_4.png)
![](images/graphs/yillik_gelir_vs_harcama.png)

**Bulgular:**
- Genel olarak gelir arttıkça harcama artış eğilimi
- Orta gelir grubunda yoğun veri dağılımı
- Düşük ve yüksek gelir gruplarında uç noktalar mevcut

### 5. Yaş Gruplarına Göre Ortalama Harcama

![](images/graphs/homework_5.png)
![](images/graphs/chatgpt_ornegi.png)

**Bulgular:**
- Farklı yaş gruplarının harcama davranışları analiz edildi
- Yaş ile harcama miktarı arasındaki ilişki görselleştirildi

## 🎯 Temel İçgörüler

1. **Zaman Bazlı Trendler**: Harcamalar belirli saatlerde yoğunlaşıyor
2. **Coğrafi Dağılım**: Bazı şehirler harcama merkezleri olarak öne çıkıyor
3. **Online vs. Offline**: Digital dönüşümün harcama davranışlarına etkisi
4. **Demografik Etkiler**: Yaş ve cinsiyet faktörlerinin rolü
5. **Gelir-Harcama Korelasyonu**: Ekonomik durumun harcama üzerindeki etkisi