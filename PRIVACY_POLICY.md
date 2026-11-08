# Gizlilik Politikası — Radar Haritası TR

**Son güncelleme:** 8 Kasım 2026

Bu politika, **Radar Haritası TR** iOS uygulamasının (paket adı:
`com.aob.radarharitasitr`) kişisel verilerinizi nasıl işlediğini açıklar.

**Uygulama:** Radar Haritası TR
**Geliştirici iletişim:** [info@arsesoft.com](mailto:info@arsesoft.com) ·
[github.com/TA4AB/radar-haritasi-tr](https://github.com/TA4AB/radar-haritasi-tr)
**Politika adresi:** `https://github.com/TA4AB/radar-haritasi-tr/blob/main/PRIVACY_POLICY.md`

---

## Kısa Özet

- Hesap, e-posta, telefon veya kullanıcı adı **istemez ve saklamaz**.
- **Reklam, analitik, izleyici (tracker) veya çökme raporu kitaplığı kullanılmaz.**
- Konum bilgisi **yalnızca cihazınızda** işlenir; tarafımıza ait hiçbir sunucuya
  gönderilmez.
- Uygulama içindeki tüm tercihler ve geçmiş verisi **yalnızca cihazınızda**
  (UserDefaults) tutulur.
- Satın alımlar Apple üzerinden yapılır; kart veya ödeme bilgilerine
  **erişimimiz yoktur**.

---

## 1. Topladığımız / İşlediğimiz Veriler

### 1.1 Konum bilgisi

Uygulama, radar ve kontrol noktası uyarılarını verebilmek için cihazınızın
konumunu kullanır (`NSLocationAlwaysAndWhenInUseUsageDescription`,
`NSLocationWhenInUseUsageDescription`).

| | |
|---|---|
| **Amaç** | Yaklaşan radar/hız koridoru uyarıları, mesafe hesabı, sesli uyarı |
| **Nerede işlenir** | **Yalnızca cihazınızda** (CoreLocation) |
| **Sunucuya gönderilir mi?** | **Hayır.** Konumunuz tarafımıza ait hiçbir sunucuya gönderilmez, kaydedilmez |

**İstisna — "Konumumu kullan" düğmesi:** Başlangıç noktası olarak mevcut
konumunuzu seçtiğinizde, cihaz konumunuz **Apple'ın ters coğrafi kodlama
servisine** (`CLGeocoder`) gönderilir ve bir **il/ilçe** olarak eşleştirilir.
Bu aşamadan sonra yalnızca seçilen **ilçenin genel koordinatları** (kişisel
konumunuz değil) güzergah sorgusu için kullanılır.

### 1.2 Bildirimler

Uygulama **yerel bildirimler** (radar uyarıları, 30 dakikalık veri yenileme
hatırlatıcısı) kullanır. Uzaktan bildirim (push) gönderimi, cihaz token'ı
toplama veya sunucu üzerinden bildirim gönderme **yoktur**.

### 1.3 Cihazınızda saklanan veriler

Aşağıdaki veriler yalnızca uygulamanın kendi alanında (`UserDefaults`)
saklanır ve cihazınızdan çıkmaz:

| Veri | İçerik | Amaç |
|---|---|---|
| `alertRadius` | Uyarı mesafesi | Tercih |
| `themeMode` | Açık/koyu tema | Tercih |
| `vehicleType` | Araç tipi | Tercih |
| `saved_favorite_routes` | Kayıtlı güzergahlar (il/ilçe adı ve koordinatları) | Favoriler |
| `saved_trip_history` | Geçmiş yolculuklar | Geçmiş ekranı |
| `trialStartDate`, `trialFurthestDate`, `trialLengthDays` | 5 günlük deneme süresi başlangıcı | Deneme süresi |
| `hasActiveSubscription` | Abonelik durumu (önbellek) | Erişim kontrolü |

### 1.4 Satın alımlar ve abonelikler

Uygulama içi satın alımlar **Apple App Store (StoreKit 2)** üzerinden yapılır.

- Apple ödeme bilgilerinizi işler; **kart numarası, banka bilgisi veya ödeme
  verisine erişimimiz yoktur.**
- Apple yalnızca satın alma işlemini doğrulamak için gereken bilgiyi
  (satın alma makbuzu / transaction) uygulamaya iletir.
- Abonelik durumu, cihazınızda önbelleklenir ve Apple'ın
  `Transaction.currentEntitlements` sorgusuyla doğrulanır.

## 2. Toplamadığımız Veriler

Aşağıdakiler **hiçbir şekilde toplanmaz**:

- Ad, soyad, e-posta adresi, telefon numarası, adres
- Kullanıcı hesabı veya kimlik doğrulama bilgisi
- Reklam kimliği (IDFA) veya cihaz izleme verisi
- Analitik / kullanım istatistikleri
- Çökme raporları veya telemetri
- Sosyal medya veya üçüncü taraf izleyici verisi

## 3. Ağ İletişimi (Hangi Sunucuya Ne Gidiyor)

Uygulama yalnızca aşağıdaki uç noktalarla iletişim kurar:

| Sunucu | İstek | Gönderilen bilgi |
|---|---|---|
| `https://www.icisleri.gov.tr` | `GetCities` | Yok (yalnızca istek) |
| `https://www.icisleri.gov.tr` | `GetDistricts?cityId=…` | Seçilen ilin kimliği |
| `https://www.icisleri.gov.tr` | `CreateRoute` | **Seçilen başlangıç ve varış ilçesinin koordinatları ve kimlikleri** |
| Apple Maps (`MKDirections`) | Güzergah geometrisi | Seçilen başlangıç/varış noktası |
| Apple `CLGeocoder` | Ters coğrafi kodlama | "Konumumu kullan" seçildiğinde cihaz konumu |

> **Not:** Canlı GPS konumunuz `icisleri.gov.tr` adresine **gönderilmez**.
> Yalnızca seçtiğiniz il/ilçenin genel koordinatları iletilir.

## 4. Üçüncü Taraflar

| Sağlayıcı | Amaç | Politika |
|---|---|---|
| **T.C. İçişleri Bakanlığı** (`icisleri.gov.tr`) | Kamuya açık radar/kontrol noktası verileri | [icisleri.gov.tr](https://www.icisleri.gov.tr) |
| **Apple Inc.** | Harita, ters coğrafi kodlama, App Store satın alımları, bildirimler | [Apple Gizlilik Politikası](https://www.apple.com/legal/privacy/) |

Verileriniz **satılmaz**, reklam amacıyla **paylaşılmaz** ve üçüncü taraflara
**devredilmez**.

## 5. Saklama Süresi ve Silme

- Cihazda saklanan veriler, uygulamayı **cihazınızdan sildiğinizde** silinir.
- Favori güzergahları ve yolculuk geçmişini uygulama içinden silebilirsiniz.
- Veriler hiçbir sunucuda tutulmadığı için sunucu üzerinde silme işlemi
  gerekmez.

## 6. Çocukların Gizliliği

Uygulama **13 yaş altı çocuklara yönelik değildir** ve bilerek çocuklardan
veri toplamaz. Ebeveynlerin çocuklarının cihazındaki uygulama kullanımını
yönetmesi önerilir.

## 7. Güvenlik

- Konum verisi cihaz dışına çıkmadığı için aktarım riski oluşmaz.
- Ağ istekleri yalnızca **HTTPS** üzerinden yapılır.
- Satın alma doğrulaması Apple'ın güvenli altyapısı üzerinden gerçekleşir.

## 8. KVKK (6698 sayılı Kanun) Uyarısı

6698 sayılı Kişisel Verilerin Korunması Kanunu kapsamında **veri sorumlusu**
konumundayız. İşlenen kişisel verileriniz yalnızca yukarıda belirtilen amaçlar
kullanılır ve yasal dayanağı, uygulamanın sunduğu hizmetin sunulması ile
kullanıcının açık rızasıdır.

Kanunun 11. maddesi kapsamında:

- Kişisel verilerinizin işlenip işlenmediğini öğrenme,
- İşlenmişse buna ilişkin bilgi talep etme,
- Düzeltilmesini veya silinmesini isteme,
- İşlemenin münhasıran otomatik sistemlerle analiz edilmesine itiraz etme
  haklarına sahipsiniz.

Taleplerinizi [info@arsesoft.com](mailto:info@arsesoft.com) adresine veya
[GitHub depomuz](https://github.com/TA4AB/radar-haritasi-tr) üzerinden
iletebilirsiniz.

## 9. Değişiklikler

Bu politika zaman zaman güncellenebilir. Güncel sürüm her zaman bu sayfada
yayınlanır; önemli değişikliklerde uygulama içinden bilgilendirme yapılabilir.

## 10. İletişim

Gizlilikle ilgili tüm sorularınız için:

- **GitHub:** [github.com/TA4AB/radar-haritasi-tr](https://github.com/TA4AB/radar-haritasi-tr)
- **E-posta:** [info@arsesoft.com](mailto:info@arsesoft.com)

---

> ⚠️ Bu uygulama resmi bir kamu uygulaması değildir. T.C. İçişleri Bakanlığı
> veya herhangi bir devlet kurumu tarafından geliştirilmemiş, onaylanmamış veya
> desteklenmemiştir.
