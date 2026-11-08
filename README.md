<div align="center">

# 🚦 Radar Haritası TR

**Türkiye genelinde güzergah üzerindeki radar kameraları, trafik kontrol
noktaları ve hız koridorlarını gösteren iOS uygulaması.**

![Platform](https://img.shields.io/badge/platform-iOS_16.0%2B-blue)
![Swift](https://img.shields.io/badge/Swift-5.9-orange)
![UI](https://img.shields.io/badge/UI-SwiftUI-5856D6)
![StoreKit](https://img.shields.io/badge/StoreKit-2-34C759)
![Device](https://img.shields.io/badge/device-iPhone-lightgrey)

</div>

---

> ⚠️ **Bu uygulama resmi bir kamu uygulaması değildir.** T.C. İçişleri Bakanlığı
> veya herhangi bir devlet kurumu tarafından geliştirilmemiş, onaylanmamış veya
> desteklenmemiştir.

## ✨ Özellikler

- **Güzergah Sorgulama** — Başlangıç ve varış il/ilçe seçilerek güzergah oluşturulur
- **Apple Maps Görselleştirme** — Güzergah ve radar noktaları MapKit üzerinde gösterilir
- **GPS Takibi** — Canlı konum takibi ile radar noktalarına yaklaşma uyarısı
- **Türkçe Sesli Uyarı** — `AVSpeechSynthesizer` ile Türkçe TTS
- **Hız Koridorları** — Güzergah üzerindeki hız koridorları turuncu çizgi ile işaretlenir
- **İl Bazlı Özet** — Her il için radarlı ve radarsız trafik uygulama sayıları listelenir
- **Karanlık Tema** — Sistem temasına uyumlu açık/koyu tema desteği
- **Arama ile Seçim** — İl ve ilçe seçiminde canlı arama desteği
- **Favoriler & Geçmiş** — Kayıtlı güzergahlar ve yolculuk geçmişi
- **iPhone'a Özel** — Uygulama yalnızca iPhone için derlenir, iPad'de çalışmaz

## 📱 Ekranlar

<!-- Ekran görüntülerinizi `Screenshots/` klasörüne ekleyip aşağıdaki satırları açın:

| Ana Ekran | Güzergah Sonucu | Ayarlar |
|:-:|:-:|:-:|
| ![Ana](Screenshots/home.png) | ![Sonuç](Screenshots/route.png) | ![Ayarlar](Screenshots/settings.png) |
-->

## 🛠 Teknik Yapı

| Katman | Teknoloji |
|--------|-----------|
| Dil | Swift 5.9+ |
| UI | SwiftUI |
| Cihaz | iPhone (`TARGETED_DEVICE_FAMILY = 1`, iPad desteklenmiyor) |
| Min iOS | iOS 16.0 |
| Harita | MapKit (Apple Maps) |
| Ağ | URLSession + async/await |
| Konum | CoreLocation (Background) |
| Ses | AVSpeechSynthesizer (TTS) |
| Mimari | MVVM + Combine |
| Satın Alma | StoreKit 2 |
| Ayarlar | UserDefaults |

## 🚀 Kurulum

1. `Radar_iOS.xcodeproj` dosyasını **Xcode 15+** ile açın
2. **Signing & Capabilities** → kendi **Team**'inizi seçin
3. Bir iPhone simülatörü veya cihazı seçip **⌘R** ile çalıştırın

> **Not:** Uygulama iPhone'a özeldir; iPad hedefi seçerseniz derleme alınmaz.

## ⏱ Deneme Süresi ve Abonelik (StoreKit 2)

Uygulama **5 günlük ücretsiz deneme** ile açılır. Süre dolunca ana ekran yerine
**kapatılamaz satın alma ekranı** (`PaywallView`) gösterilir; abonelik satın
alındığında uygulama kullanımına kaldığı yerden devam eder.

| Ürün | Product ID | Fiyat (yerel test) |
|------|-----------|--------------------|
| Aylık abonelik | `com.radarios.monthly` | ₺49,99 / ay |
| Yıllık abonelik | `com.radarios.yearly` | ₺399,99 / yıl |

**Akış**

- `SubscriptionManager` (StoreKit 2) deneme başlangıcını ve abonelik haklarını yönetir.
- `Radar_iOSApp` içinde `hasAccess` kontrolü yapılır: abonelik **veya** deneme süresi
  devam ediyorsa `ContentView`, değilse kilitli `PaywallView` gösterilir.
- Ana ekranda deneme süresi bandı, Ayarlar'da Abonelik bölümü bulunur
  (plan seçimi, satın alımları geri yükleme, aboneliği yönetme).
- Deneme süresi cihazda saklanır; saat geri alınarak uzatılamaz.

### App Store Connect Kurulumu

1. App Store Connect → Uygulamalar → Radar Haritası TR → **Abonelikler**
2. Aynı grup altında **aylık** ve **yıllık** abonelik oluşturun
3. Product ID'leri tablodakilerle **birebir** aynı girin
4. Gizlilik politikası ve kullanım koşulları URL'lerini tanımlayın
   (`PaywallView.swift` içindeki `LegalLink` sabitlerini kendi URL'lerinizle güncelleyin)

### Yerel Test (App Store Connect gerekmez)

- `Radar_iOS.storekit` dosyası proje kökündedir ve scheme'e bağlıdır
  (Product → Scheme → Edit Scheme → Run → StoreKit Configuration).
- Xcode ile ▶ ile çalıştırın; satın alma ekranında aylık/yıllık planlar görünür.
- **5 gün beklemeden test etmek için:** Ayarlar → *Test (Debug)* → *Deneme süresini bitir*.
- Alternatif: Scheme'e `-trialLengthDays 0` launch argument'i ekleyin
  (`0` = anında biter, `1` = 1 gün).
- Xcode'da abonelik durumunu simüle etmek için:
  **Xcode → Debug → StoreKit → Manage Transactions** (aboneliği sonlandırıp
  satın alma ekranının geri geldiğini doğrulayın).

> ⚠️ `Radar_iOS.storekit` hedefe (target membership) eklenmez; yalnızca scheme
> üzerinden çalışırken kullanılır. StoreKit yapılandırması yalnızca **Xcode'dan
> (⌘R)** başlatıldığında geçerlidir — `simctl` veya simülatör ikonuyla
> başlatıldığında "Planlar yüklenemedi" hatası alınır.

## 📂 Proje Yapısı

```
Radar_iOS/
├── Radar_iOSApp.swift          — Uygulama giriş noktası (deneme/abonelik kapısı)
├── Info.plist                  — Uygulama izinleri ve yapılandırma
├── Assets.xcassets/            — Uygulama simgesi ve renk varlıkları
├── Views/
│   ├── ContentView.swift       — Ana ekran
│   ├── MapView.swift           — MapKit harita görünümü
│   ├── RouteFormView.swift     — Güzergah seçim formu
│   ├── RouteResultView.swift   — Güzergah sonuçları
│   ├── PaywallView.swift       — Satın alma ekranı (abonelik)
│   ├── SettingsView.swift      — Ayarlar (tema, uyarı mesafesi, abonelik)
│   ├── FavoritesView.swift     — Favori güzergahlar
│   ├── TripHistoryView.swift   — Yolculuk geçmişi
│   └── AboutView.swift         — Hakkında sayfası
├── Models/
│   └── Models.swift            — Veri modelleri
├── Networking/
│   └── APIClient.swift         — API istekleri (async/await)
├── ViewModels/
│   └── MainViewModel.swift     — İş mantığı katmanı
├── Services/
│   ├── LocationAlertManager.swift — GPS takip ve sesli uyarı
│   ├── NotificationManager.swift  — Yerel bildirimler
│   └── SubscriptionManager.swift  — Deneme süresi + StoreKit 2 abonelik
├── Utilities/
│   └── UserPreferences.swift   — UserDefaults wrapper
└── Radar_iOS.storekit          — Yerel StoreKit test konfigürasyonu (hedefe eklenmez)
```

## 🔒 Gizlilik

Konum bilginiz **yalnızca cihazınızda** işlenir, sunuculara gönderilmez.
Reklam, analiz veya izleyici kullanılmaz. Ayrıntılar için:

📄 **[Gizlilik Politikası](https://github.com/TA4AB/radar-haritasi-tr/blob/main/PRIVACY_POLICY.md)**

## 📡 Veri Kaynağı

T.C. İçişleri Bakanlığı kamuya açık API:

- `https://www.icisleri.gov.tr/ISAYWebPart/PolGenControlPointV2/`
- Kaynak sayfa: `https://www.icisleri.gov.tr/iller-arasi-radar-ve-kontrol-noktasi-uygulama-sayilari`

Veriler yaklaşık **30 dakikada bir** güncellenmektedir.

## 📬 İletişim

Soru, öneri ve bildirimleriniz için:

- **E-posta:** [info@arsesoft.com](mailto:info@arsesoft.com)
- **Hata bildirimi:** [GitHub Issues](https://github.com/TA4AB/radar-haritasi-tr/issues)

## 📄 Lisans

Bu depo için şu anda bir lisans tanımlanmamıştır. Ticari kullanım öncesi
sahibiyle iletişime geçin.

---

<div align="center">
Made with ❤️ for Turkish drivers
</div>
