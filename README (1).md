# 🌍 Akıllı Enerji Asistanı (Smart Energy Assistant)

Bu depo (repository), "AI for the SDGs" Capstone Projesi kapsamındaki **Assignment 1 (Proje Teklifi ve İlk Deneyler)** teslimi için oluşturulmuştur.

## 🎯 Proje Amacı ve SDG Bağlantısı

Projemiz, Birleşmiş Milletler'in **SDG 7 (Erişilebilir ve Temiz Enerji)** hedefine katkıda bulunmayı amaçlamaktadır.
Geliştireceğimiz yapay zeka destekli araç, ev kullanıcılarının saatlik ve cihaz bazlı (mutfak, çamaşır odası, iklimlendirme) elektrik tüketim verilerini analiz ederek, onlara enerji israfını önlemeye yönelik kişiselleştirilmiş ve eyleme geçirilebilir tasarruf planları sunacaktır.

## 📂 Depo İçeriği (Assignment 1 Teslimatları)

Bu repoda bulunan dosyalar ve amaçları aşağıda listelenmiştir:

* **`Proje_Teklifi.pdf`**: Projemizin hedeflerini, kullanılacak modeli (LLM Entegrasyonu) ve iş akışını anlatan 1-2 sayfalık ana proje teklifi dokümanımız.

* **`household_power_consumption_sample.xlsx`**: Projemizde kullanacağımız, saatlik toplam tüketim ve alt sayaç (Sub_metering) verilerini içeren örnek veri setimiz.

* **`SDG7_Power_Consumption_EDA_Results.pdf`**: Veri setimiz üzerinde yaptığımız Keşifçi Veri Analizi sonuçlarını, özet istatistikleri ve dağılım/korelasyon grafiklerini içeren raporumuz.

* **`ilk_model_denemesi.py`**: Projenin temelini oluşturacak Büyük Dil Modeli (LLM) entegrasyonu için yaptığımız "ilk deney" kodumuz. Bu kod, ham veriyi okuyarak yapay zekaya gönderilmek üzere anlamlı bir Türkçe isteme (Prompt) dönüştürmektedir.

## 🚀 Çalıştırma Adımları

Model test script'ini kendi bilgisayarınızda çalıştırmak için aşağıdaki kütüphanenin yüklü olması gerekmektedir:

```
pip install pandas openpyxl
```

1. Veri setini ve `.py` dosyasını aynı dizine indirin.

2. LLM'e gönderilecek veri tabanlı test prompt'unu ekranda görmek için `ilk_model_denemesi.py` dosyasını çalıştırın.

## 👥 Grup Üyeleri

- Buğra Karatepe 22061032
- Burak Arslan 22061025
- Erva Akdoğan 22061049
- Zeynep Şura Çetin 22069030