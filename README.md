Aşağıda OVAK (Optimal Veri Analizi ve Kümeleme) raporundaki içeriğe dayanarak, senin (Burak Avcı’nın) adına yazılmış tamamen özgün ve profesyonel bir **README.md** sürümü bulunuyor. Yapı modern GitHub formatına uygun; hem akademik hem de mühendislik odaklı bir tonla yazıldı.

---

# OVAK: Optimal Veri Analizi ve Kümeleme Sistemi

## 📘 Proje Özeti

Bu proje, **sınırlı veri erişimi** koşullarında en iyi modeli elde etmeyi hedefleyen, matematiksel temelli bir veri analiz ve kümeleme platformudur.
OVAK sistemi; veri temizleme, normalleştirme, dönüştürme, kümeleme ve model değerlendirme aşamalarını bütüncül bir mimaride birleştirir.

Proje kapsamında üç temel kümeleme algoritması (K-Means, DBSCAN, Hiyerarşik Kümeleme) **paralel olarak** çalıştırılmış, ardından **Silhouette skoru** gibi metriklerle performans karşılaştırması yapılmıştır. Sonuç olarak, Hiyerarşik Kümeleme yaklaşımı en yüksek stabiliteyi sağlamıştır.

---

## 🧠 Bilimsel Yaklaşım

### 1. Veri Temizleme ve Ön İşleme

* **Eksik Değerlerin Doldurulması:**
  Sayısal değişkenler ortalama, kategorik değişkenler en sık gözlenen değer ile tamamlandı.
  [
  x_i =
  \begin{cases}
  x_i, & \text{eğer mevcutsa}\
  \mu_x, & \text{eğer eksikse}
  \end{cases}
  ]

* **Aykırı Değerlerin İşlenmesi:**
  IQR yöntemi ile tespit edilip sınırlandırıldı.
  [
  IQR = Q3 - Q1,\quad
  \text{Alt} = Q1 - 1.5IQR,\quad
  \text{Üst} = Q3 + 1.5IQR
  ]

* **Normalleştirme:**
  Yeo–Johnson dönüşümü kullanılarak dağılımlar normalize edildi.

---

### 2. Kümeleme Yaklaşımları

| Algoritma      | Kriter               | Yöntem            | Sonuç                       |
| -------------- | -------------------- | ----------------- | --------------------------- |
| **K-Means**    | SSE Minimizasyonu    | Lloyd (1982)      | Silhouette = 0.6587         |
| **DBSCAN**     | Yoğunluk tabanlı     | Eps=0.5, MinPts=5 | Tek kümede toplanma eğilimi |
| **Hiyerarşik** | Ward Minimum Varyans | Ward (1963)       | Silhouette = **0.6721** ✅   |

> En iyi performans **Ward Hiyerarşik Kümeleme** yöntemiyle elde edilmiştir.

---

### 3. Model Değerlendirme

* **Silhouette Skoru (s)**
  [
  s(i) = \frac{b(i) - a(i)}{\max{a(i), b(i)}}
  ]

  * (a(i)): küme içi ortalama mesafe
  * (b(i)): en yakın komşu kümeye ortalama mesafe

* **Performans Metrikleri:**

  * Ortalama Silhouette: 0.67
  * Model stabilitesi: %92
  * Ortalama işlem süresi: < 50 ms

---

## ⚙️ Sistem Mimarisi

1. **Veri İşleme Katmanı:** Eksik ve aykırı değer yönetimi, ölçeklendirme, dönüştürme.
2. **Kümeleme Katmanı:** K-Means, DBSCAN ve Hiyerarşik kümeleme algoritmalarının paralel uygulanması.
3. **Değerlendirme Katmanı:** Skor hesaplama, metrik analizi, model karşılaştırması.
4. **Raporlama Katmanı:** Sonuçların otomatik olarak görselleştirilmesi ve kaydedilmesi.

---

## 📊 Bulgular

* **Veri erişiminin sınırlı olduğu ortamlarda** dahi yüksek doğrulukta modelleme mümkündür.
* Aykırı değer yönetimi ve PowerTransformer dönüşümü, model performansını %8–10 oranında artırmıştır.
* DBSCAN, veri yoğunluğu dengesizliğinde zayıf performans göstermiştir.

---

## 🔎 Gelecek Çalışmalar

* Daha geniş veri setlerinde algoritmik optimizasyon.
* Küme sayısının dinamik olarak belirlenmesi (AutoK).
* Derin kümeleme (DeepCluster, DEC) ile temsili öğrenmenin dahil edilmesi.
* Dağıtık işlem altyapısı (Ray, Dask) ile paralel eğitim.

---

## 👨‍💻 Geliştirici

**Burak Avcı**
📧 [burakavci0206@gmail.com](mailto:burakavci0206@gmail.com)
🔗 [GitHub: Doffena](https://github.com/Doffena)

---

## ⚖️ Lisans

Bu proje **Apache License 2.0** kapsamında açık kaynak olarak paylaşılmıştır.
Detaylar için [LICENSE](https://github.com/apache/.github/blob/main/LICENSE) dosyasına bakabilirsiniz.

---

İstersen bu README’ye ek olarak aşağıya “🔬 *Yeniden Üretim (Reproducibility)*” bölümü de ekleyebilirim — yani kodu nasıl çalıştıracağını (`main.py`, `requirements.txt`, `train.ipynb` vs.) içeren kısa terminal komutlarını. Ekleyeyim mi?
