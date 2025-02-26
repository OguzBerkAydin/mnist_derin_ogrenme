# MNIST Rakam Tanıma Projesi

Bu repo, MNIST veri seti üzerinde rakam tanıma için iki farklı yaklaşım içermektedir:

## İçerik

1. **basic_algorithm_numpy.ipynb**
   - Sıfırdan NumPy ile yapay sinir ağı implementasyonu
   - İleri ve geri yayılım algoritmaları manuel olarak kodlanmıştır
   - ReLU ve Softmax aktivasyon fonksiyonları
   - Precision, recall ve F1 skoru analizleri

2. **advanced_algorithm_keras_pipeline.ipynb**
   - TensorFlow/Keras ile gelişmiş model pipeline'ı
   - Farklı optimizasyon yöntemlerinin karşılaştırılması (Adam vs SGD)
   - Regularizasyon teknikleri (Dropout, Batch Normalization)
   - Performans analizi ve görselleştirmeler

## Kullanım

Her iki notebook da Google Colab'da çalıştırılmak üzere tasarlanmıştır. Doğrudan Colab'da açabilir veya yerel ortamınızda çalıştırabilirsiniz.

## Gereksinimler

* numpy
* tensorflow
* tensorflow\_datasets
* sklearn
* matplotlib
* seaborn

## Yerel Ortamda Nasıl Çalıştırılır?

1.  Gerekli kütüphaneleri yükleyin.
   ```sh
pip install -r requirements.txt
```
2.  Not defterlerini (ipynb) Google Colab veya Jupyter Notebook gibi bir ortamda açın.
3.  Kod hücrelerini sırasıyla çalıştırın.

## Sonuçlar

* Numpy implementasyonu, temel sinir ağı kavramlarını anlamak için iyi bir başlangıç noktası sunmaktadır.
* TensorFlow/Keras pipeline'ı, daha yüksek doğruluk oranları ve gelişmiş özellikler sağlamaktadır.
* Batch Normalization tekniğinin kullanımı, model performansında belirgin iyileşme sağlamıştır.
* Adam optimizasyon algoritması, SGD'ye göre daha hızlı yakınsama ve daha iyi sonuçlar üretmiştir.
* Regularization teknikleri (Dropout ve BatchNorm), modellerin genelleme yeteneğini artırmıştır.
* En düşük performans SGD ile elde edilirken, en yüksek doğruluk BatchNorm kullanan modellerde gözlemlenmiştir.

## İyileştirme Önerileri

* Evrişimli Sinir Ağları (CNN) kullanılarak model performansı artırılabilir.
* Hiperparametre optimizasyonu (grid search, random search) yapılabilir.
* Veri artırma (data augmentation) teknikleri uygulanabilir.
* Learning Rate Scheduling ve Early Stopping yöntemleri uygulanabilir.
* Farklı modellerin sonuçları toplanarak (Voting) nihai sonuç üretilebilir.  
