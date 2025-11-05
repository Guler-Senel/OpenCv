# C# ve OpenCV ile Basit Yüz Tanıma

Bu proje, C# (.NET Framework) ve OpenCvSharp kütüphanesi kullanılarak bir fotoğraftaki insan yüzlerini bulan temel bir Windows Forms uygulamasıdır.

Görüntü işleme dersi veya kişisel denemeler için basit bir başlangıç noktası olarak hazırlanmıştır.

## Kullanılan Teknolojiler
* C# (.NET Framework)
* Windows Forms
* OpenCvSharp4 (ve OpenCvSharp4.Extensions)
* Haar Cascade (OpenCV'nin `haarcascade_frontalface_default.xml` modeli)

## Hızlı Başlangıç

Projeyi çalıştırmak için Visual Studio'da açın ve aşağıdaki NuGet paketlerini yükleyin:
* `OpenCvSharp4.Windows`
* `OpenCvSharp4.Extensions`

Program, yüzleri bulmak için `haarcascade_frontalface_default.xml` model dosyasına ve üzerinde arama yapmak için `test.jpg` adlı bir test resmine ihtiyaç duyar.

**En Önemli Adım:**
Projenin hata vermeden (`!_src.empty()` hatası almamak için) çalışması için, projeye eklediğiniz `test.jpg` ve `haarcascade_frontalface_default.xml` dosyalarına tıklayın. Visual Studio "Properties" (Özellikler) penceresinden **"Copy to Output Directory"** ayarını **"Copy if newer"** olarak değiştirin.

## Çalışma Mantığı

Butona tıklandığında:
1.  `CascadeClassifier`, `.xml` modelini hafızaya yükler.
2.  `test.jpg` dosyası `Mat` nesnesi olarak okunur.
3.  Resim, hız ve doğruluk için `Cv2.CvtColor` ile gri tona çevrilir.
4.  `DetectMultiScale` fonksiyonu, gri resimdeki yüzlerin koordinatlarını (`Rect[]`) bulur.
5.  `foreach` döngüsüyle her yüzün etrafına `Cv2.Rectangle` ile yeşil bir kare çizilir.
6.  Sonuç, `BitmapConverter` ile `PictureBox`'ta gösterilir.
