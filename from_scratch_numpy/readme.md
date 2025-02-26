# MNIST Rakam Tanıma: Yapay Sinir Ağı Implementasyonu ve Analizi

Bu proje, MNIST veri seti üzerinde sıfırdan bir yapay sinir ağı (Neural Network) uygulamasını içerir. Projenin amacı, el yazısı rakamları tanıyan bir model oluşturmak ve bu modelin performansını detaylı olarak analiz etmektir.

## Proje Özeti

MNIST veri seti, 0'dan 9'a kadar el yazısı rakamların 28x28 piksellik gri tonlamalı görüntülerinden oluşan standart bir veri setidir. Bu projede:

- NumPy kullanarak temel matematik işlemlerini gerçekleştiren
- Gizli katmanda ReLU aktivasyon fonksiyonu kullanan
- Çıkış katmanında Softmax aktivasyon fonksiyonu kullanan
- Geri yayılım (backpropagation) algoritması ile eğitilen

bir yapay sinir ağı modeli geliştirilmiştir.

## Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki kütüphanelere ihtiyacınız vardır:

```
numpy
tensorflow
scikit-learn
matplotlib
seaborn
```

Gerekli kütüphaneleri şu komutla kurabilirsiniz:
```
pip install numpy tensorflow scikit-learn matplotlib seaborn
```

## Proje Yapısı

Proje aşağıdaki ana bölümlerden oluşmaktadır:

1. **Kütüphanelerin İçe Aktarılması**: Gerekli Python kütüphanelerinin yüklenmesi
2. **Aktivasyon Fonksiyonlarının Tanımlanması**: ReLU, ReLU türevi ve Softmax fonksiyonlarının implementasyonu
3. **Performans Metriklerini Hesaplama**: Precision, recall ve F1 skorlarını hesaplayan fonksiyonlar
4. **Veri Setinin Yüklenmesi ve Ön İşleme**: MNIST veri setinin yüklenmesi, normalize edilmesi ve hazırlanması
5. **Model Parametrelerinin Başlatılması**: Sinir ağı ağırlıklarının ve bias değerlerinin başlatılması
6. **Model Eğitimi**: Mini-batch gradyan inişi ile modelin eğitilmesi ve metrik takibi
7. **Test Seti Değerlendirmesi**: Eğitilmiş modelin test verileri üzerinde değerlendirilmesi

## Model Mimarisi

Bu projede kullanılan yapay sinir ağı şu özelliklere sahiptir:

- Giriş Katmanı: 784 nöron (28x28 görüntü düzleştirilmiş)
- Gizli Katman: 128 nöron (ReLU aktivasyon fonksiyonu)
- Çıkış Katmanı: 10 nöron (Softmax aktivasyon fonksiyonu)

## Eğitim Detayları

Model şu hiperparametrelerle eğitilmiştir:
- Öğrenme oranı (Learning rate): 0.01
- Epoch sayısı: 10
- Batch boyutu: 32
- Kayıp fonksiyonu: Categorical Cross-Entropy

## Performans Değerlendirmesi

Model performansı şu metriklerle değerlendirilmiştir:
- Doğruluk (Accuracy)
- Kesinlik (Precision)
- Duyarlılık (Recall)
- F1 skoru (F1 score)

Ayrıca, her rakam sınıfı (0-9) için ayrı ayrı kesinlik ve duyarlılık değerleri hesaplanmıştır.

## Kullanım

Kodu çalıştırmak için:
1. Gerekli kütüphaneleri yükleyin
2. Jupyter notebook'u çalıştırın veya Python dosyasını doğrudan çalıştırın
3. Eğitim süreci otomatik olarak başlayacak ve sonuçlar görüntülenecektir