# MNIST Rakam Tanıma Projesi

Bu repo, MNIST veri seti üzerinde rakam tanıma için iki farklı yaklaşım içermektedir:

## İçerik

1. **basic_algorithm_numpy.ipynb**
   <a target="_blank" href="https://colab.research.google.com/drive/1_LjMSeXhapvW815osna3_GZgbBN9St67#scrollTo=kk7O74MoQbxD">
  <img src="https://www.tensorflow.org/images/colab_logo_32px.png" />Run in Google Colab
</a>

<a target="_blank" href="https://github.com/OguzBerkAydin/mnist_derin_ogrenme/tree/main/from_scratch_numpy">
  <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />View source on GitHub
</a>
   - Sıfırdan NumPy ile yapay sinir ağı implementasyonu
   - İleri ve geri yayılım algoritmaları manuel olarak kodlanmıştır
   - ReLU ve Softmax aktivasyon fonksiyonları
   - Precision, recall ve F1 skoru analizleri

2. **advanced_algorithm_keras_pipeline.ipynb**
   <a target="_blank" href="https://colab.research.google.com/drive/1PtY4KN5QQnk9oUPgxpxO_8Y8fG6-cRFy#scrollTo=YGaqMvDgRUUv">
  <img src="https://www.tensorflow.org/images/colab_logo_32px.png" />Run in Google Colab
</a>

<a target="_blank" href="https://github.com/OguzBerkAydin/mnist_derin_ogrenme/tree/main/advance_pipeline_tensorflow">
  <img src="https://www.tensorflow.org/images/GitHub-Mark-32px.png" />View source on GitHub
</a>
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
