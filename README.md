# 📊 Power BI Satış Analizi Projesi – Ülker Markası

Bu projede, Power BI kullanılarak **Ülker markasına özel** satış analizi gerçekleştirilmiştir. Proje, kullanıcı, sipariş, ürün ve bölge verilerini kapsamaktadır. Amaç; satışların, müşteri demografisinin ve ürün kategorilerinin detaylı analizidir.

---

## 📁 Kullanılan Veri Setleri

- **users.csv** – Kullanıcı bilgileri  
- **adres.csv** – Şehir ve kullanıcı eşleşmeleri  
- **items.csv** – Ürün bilgileri  
- **orderdetail.csv** – Sipariş detayları  
- **orders.csv** – Sipariş zaman bilgileri  
- **SehirlerBolgeler.csv** – Şehir-bölge eşleştirmesi  

Tüm analizler yalnızca `items.csv` içindeki **brand = 'Ülker'** olacak şekilde filtrelenmiştir.

---

## 🔧 Yapılan İşlemler

### 1. **Veri Hazırlama ve Modelleme**
- Tüm CSV dosyaları Power BI’a aktarıldı.
- Veri türleri düzenlendi.
- Gereksiz sütunlar gizlendi/kaldırıldı.
- Tablolar arası ilişkiler kuruldu:
  - `Kullanıcılar.ID` → `siparis.USERID`  
  - `siparis.ID` → `siparisdetay.ORDERID`  
  - `siparis.ADRESSID` → `adres.ID`  
  - `siparisdetay.ITEMID` → `urunler.ID`  
  - `adres.CITY` ↔ `bölgeler.IL`

---

### 2. **DAX Formülleri ve Ölçümler**

#### 📌 Temel Ölçümler
- `Toplam Ciro`  
- `Toplam Satış Adeti`  
- `Toplam Müşteri Sayısı`  
- `Toplam Sipariş Sayısı`  
- `Müşteri Başına Ciro`  
- `Müşteri Başına Adet`  
- `Ortalama Sipariş Tutarı`  

#### 📌 Zaman Bazlı
- `GunTipi` (Hafta içi / Hafta sonu)  
- `Saat` (Saatlik analiz için)

#### 📌 Demografik
- `Yaş` = `DATEDIFF(BIRTHDATE, TODAY(), YEAR)`  
- `Yaş Grubu` (0–20: Genç, 20–35: Yetişkin, 35–55: Orta Yaş, 55+: Yaşlı)  
- `Cinsiyet` koşullu sütunu: E → Erkek, K → Kadın  

---

## 📈 Rapor Sayfaları

### 🟩 **Giriş Sayfası**
- Navigasyon için 3 buton:
  - Özet
  - Müşteri Perspektifi
  - Kategori Perspektifi

### 🟨 **Özet Sayfa**
- Haftaiçi/Haftasonu Satış Grafiği  
- Saatlik Satış Grafiği  
- Bölgelere Göre Satış  
- Kartlar: Ciro, Satış Adedi, Sipariş, Müşteri Sayısı  

### 🟦 **Müşteri Perspektifi**
- Kadın/Erkek Müşteri Sayısı  
- Yaş Grubuna Göre Satış Grafiği  
- İstanbul’daki Top 10 Müşteri  
- Bölgelere Göre Müşteri Dağılımı  

### 🟪 **Kategori Perspektifi**
- İstanbul’da yaşayan, Genç yaş grubundaki müşterilerin toplam cirosunun **Ürün Kategorilerine göre Ağaç Haritası**

---

## 🧠 Proje Notları

- Tüm analizler **sadece Ülker markası** için yapılmıştır.
- Modelleme mantığı, veri temizliği ve kullanıcıya yönelik sade arayüz hedeflenmiştir.
- Tasarımda sezgisel butonlar ve temiz filtreleme mantığı uygulanmıştır.

---

## 🛠 Gereksinimler

- Microsoft Power BI Desktop
- Veri setleri (.csv formatında)
