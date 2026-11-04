# VeriCheck Mobile

VeriCheck'in dokunmatik ekranlara uyarlanmış, kurulabilir PWA sürümüdür. Uygulama Türkçedir. Eğitim/test görüntülerini kamera veya galeriden alır, SHA-256 ve 64 bit DCT tabanlı pHash ile tarayıcıda karşılaştırır. Görüntüleri herhangi bir sunucuya göndermez.

## Başlatma

Klasörde `python -m http.server 8000` komutunu çalıştırın ve bilgisayarda `http://localhost:8000` adresini açın. Dosyayı doğrudan `file://` olarak açmak PWA kurulumu ve güvenli SHA-256 işlemi için uygun değildir.

## Telefona yükleme

Dosyaları HTTPS sunan statik bir web barındırma hizmetine yayınlayın (ör. GitHub Pages). Android Chrome'da site menüsünden **Uygulamayı yükle / Ana ekrana ekle**; iPhone Safari'de **Paylaş > Ana Ekrana Ekle** seçin. Kamera izni verin. PWA'nın yüklenebilirliği ve kamera davranışı tarayıcı/işletim sistemine bağlıdır. İlk ziyaretten sonra çevrimdışı açılabilir. Mobil cihazda `localhost` bilgisayarın localhost'u değildir.

## Bilimsel sınırlar

SHA-256 sadece birebir dosya aynılığını tespit eder. pHash genel görsel yapıyı karşılaştırır; eşikler pilot değerlerdir. Benzerlik uyarısı kesin veri sızıntısı veya aynı fiziksel yaprak kanıtı değildir. Gerçek durum kontrollü deneyle doğrulanmalıdır. Başarı oranları dış deneyden elle girilir. VeriCheck hastalık teşhisi veya görüntü sınıflandırması yapmaz.

## Kullanım

1. Eğitim ve test fotoğraflarını ayrı yükleyin veya kamera ile çekin.
2. Analiz ekranından pilot eşikleri seçin, analizi başlatın.
3. Şüpheli çiftleri inceleyin.
4. Yazılımı Test Et bölümünde gerçek durumları elle doğrulayın.
5. Rapor ekranından CSV indirin veya yazdırın.

## Notlar

Veriler sayfa belleğinde tutulur; sayfa yenilenince fotoğraflar ve analiz sonuçları silinir. Büyük veri setleri telefonda zaman ve bellek gerektirir. Kamera ile fotoğraf seçme tarayıcının yerel kamera/dosya arayüzünü açar. Bu sürüm native APK/IPA değildir; telefona kurulabilir web uygulamasıdır.


## Botanik tasarım (v2)
Açık yeşil, nane, lime ve şeftali tonlarında yeniden tasarlandı. Ana ekran az metinli, büyük dokunmatik işlem kartları ve anlık eğitim/test sayaçları içerir. Fotoğraf yükleme, analiz, doğrulama ve raporlama mantığı korunmuştur. Galeri seçimleri ve kameradan çekilen görüntüler aynı oturumda birlikte biriktirilir.

## Adım adım GitHub Pages kurulumu
1. GitHub hesabınıza giriş yapın ve `vericheck-mobile` adında **Public** bir repository oluşturun.
2. ZIP dosyasını açın. `VeriCheck_Mobile` klasörünün **içindeki** `index.html`, `manifest.webmanifest`, `sw.js` ve `icons` klasörünü repository köküne yükleyin.
3. Repository'de **Settings → Pages → Build and deployment → Deploy from a branch** seçin. Branch olarak `main`, klasör olarak `/(root)` seçip kaydedin.
4. GitHub Pages tarafından gösterilen HTTPS bağlantısını açın. İlk yayın birkaç dakika sürebilir.
5. **Android:** Chrome ile bağlantıyı açın → üç nokta menüsü → `Uygulamayı yükle` veya `Ana ekrana ekle` → onaylayın.
6. **iPhone:** Safari ile bağlantıyı açın → Paylaş → `Ana Ekrana Ekle` → Ekle.
7. Uygulamayı ana ekrandan açın; kamera iznini verip önce Eğitim, sonra Test fotoğraflarını ekleyin. Analiz bölümünde taramayı başlatın.

**Not:** Bu yöntem APK/IPA üretmez. Dosyalar HTTPS üzerinden açıldığında kurulabilir PWA'dır. Tarayıcıların kamera/kurulum davranışları farklı olabilir. Fotoğraflar cihazda işlenir; sayfa yenilenince oturum verileri kaybolur.
