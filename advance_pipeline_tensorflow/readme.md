# MNIST Veri Seti ile TensorFlow Modeli Eğitimi

Bu proje, MNIST veri seti üzerinde TensorFlow ve TensorFlow Datasets kullanarak çeşitli ileri düzey sinir ağı modelleri oluşturmayı ve farklı optimizasyon/regularizasyon tekniklerini karşılaştırmayı içermektedir.

## Proje Özeti

Bu çalışmada, klasik MNIST rakam tanıma problemi üzerinde farklı model mimarileri ve eğitim teknikleri denenerek performans karşılaştırması yapılmıştır. Çalışmanın temel amacı, TensorFlow pipeline yaklaşımını kullanarak çeşitli derin öğrenme tekniklerinin etkisini analiz etmektir.

## Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki kütüphanelere ihtiyacınız vardır:

```
tensorflow
tensorflow-datasets
matplotlib
```

Gerekli kütüphaneleri yüklemek için:
```
pip install tensorflow tensorflow-datasets matplotlib
```

## Projede Kullanılan Teknikler

### Veri İşleme Teknikleri
- TensorFlow veri pipeline'ı (`tf.data` API)
- Görüntü normalizasyonu
- Veri seti önbelleğe alma (caching)
- Veri karıştırma (shuffling)
- Batch işleme
- Prefetching

### Model Optimizasyon ve Düzenlileştirme (Regularization) Teknikleri
- Adam optimizer
- SGD (Stochastic Gradient Descent) optimizer
- Dropout
- Batch Normalization
- Farklı katman konfigürasyonları

## Denenmiş Modeller

Projede beş farklı model denenmiş ve karşılaştırılmıştır:

1. **Temel Adam Modeli**: Adam optimizer ile eğitilmiş basit sinir ağı
2. **SGD Modeli**: SGD optimizer ile eğitilmiş basit sinir ağı
3. **Dropout Modeli**: Dropout düzenlileştirme tekniği eklenmiş model
4. **Batch Normalization Modeli**: Batch normalization eklenmiş model
5. **Gelişmiş Model**: Batch normalization ve dropout birlikte kullanılarak oluşturulmuş daha derin bir model

## Performans Karşılaştırması

| Model | Optimizasyon | Regularization | Test Kaybı | Test Doğruluğu |
|-------|--------------|----------------|------------|----------------|
| Adam | Adam (lr=0.001) | Yok | 0.0785 | 0.9764 |
| SGD | SGD (lr=0.01) | Yok | 0.3222 | 0.9100 |
| Dropout | Adam (lr=0.001) | Dropout (0.5) | 0.0998 | 0.9701 |
| BatchNorm | Varsayılan | Batch Normalization | 0.0753 | 0.9770 |
| BatchNorm+Dropout | Varsayılan | Batch Norm + Dropout | 0.0772 | 0.9768 |

## Proje Yapısı

Kodlama dosyası aşağıdaki ana bölümlerden oluşmaktadır:

1. **Kütüphanelerin İçe Aktarılması**: Gerekli TensorFlow bileşenlerinin içe aktarılması
2. **Veri Setinin Yüklenmesi**: MNIST veri setinin TensorFlow Datasets aracılığıyla yüklenmesi
3. **Veri Önişleme**: Görüntülerin normalizasyonu ve veri pipeline'ının hazırlanması
4. **Model Tanımlamaları**: Farklı özelliklere sahip beş modelin oluşturulması
5. **Model Eğitimi**: Modellerin eğitilmesi ve eğitim tarihçesinin kaydedilmesi
6. **Sonuçların Değerlendirilmesi**: Model performanslarının karşılaştırılması ve görselleştirilmesi
7. **Analiz ve İyileştirme Önerileri**: Sonuçların yorumlanması ve gelecek çalışmalar için öneriler

## Örnek Kullanım

```python
# Modelleri eğitmek için
import tensorflow as tf
import tensorflow_datasets as tfds

# MNIST veri setini yükleme
(ds_train, ds_test), ds_info = tfds.load(
    'mnist',
    split=['train', 'test'],
    shuffle_files=True,
    as_supervised=True,
    with_info=True,
)

# Normalizasyon fonksiyonu
def normalize_img(image, label):
  return tf.cast(image, tf.float32) / 255., label

# Veri setlerini hazırlama
ds_train = ds_train.map(normalize_img).cache().shuffle(ds_info.splits['train'].num_examples).batch(128).prefetch(tf.data.AUTOTUNE)
ds_test = ds_test.map(normalize_img).batch(128).cache().prefetch(tf.data.AUTOTUNE)

# Model oluşturma ve eğitme
model = tf.keras.Sequential([
  tf.keras.layers.Flatten(input_shape=(28, 28)),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.BatchNormalization(),
  tf.keras.layers.Dropout(0.3),
  tf.keras.layers.Dense(10)
])

model.compile(
    optimizer=tf.keras.optimizers.Adam(0.001),
    loss=tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True),
    metrics=['accuracy']
)

history = model.fit(ds_train, epochs=6, validation_data=ds_test)
```

## İyileştirme Önerileri

1. **Mimari İyileştirmeler**:
   - Evrişimli Sinir Ağları (CNN) kullanmak
   - Residual bağlantılar eklemek
   - Daha derin model mimarileri denemek

2. **Hiperparametre Optimizasyonu**:
   - Grid Search/Random Search ile hiperparametre optimizasyonu
   - Learning Rate Scheduling
   - Early Stopping

3. **Veri Artırma (Data Augmentation)**:
   - Rotasyon, ölçekleme, kaydırma gibi dönüşümler eklemek
   
4. **Ensemble Yöntemleri**:
   - Farklı modellerin tahminlerini birleştirerek (voting) sonuçları iyileştirmek

## Sonuçlar ve Çıkarımlar

- Batch Normalization tekniği, model performansında belirgin iyileşme sağlamıştır
- Adam optimizasyon algoritması, SGD'ye göre daha hızlı yakınsama ve daha iyi sonuçlar üretmiştir
- Regularization teknikleri (Dropout ve BatchNorm), modellerin genelleme yeteneğini artırmıştır
- En düşük performans SGD ile elde edilirken, en yüksek doğruluk BatchNorm kullanan modellerde gözlemlenmiştir
