# Watermaker Android uygulamasi

Uygulama kartin Wi-Fi agina (WaterMaker) kendisi baglanir ve kartin sundugu paneli uygulama icinde acar.
Android 10+ icin sistem "WaterMaker agina baglanilsin mi?" diye bir kez onay sorar; "Baglan" demek yeterli.

> NOT: Bu proje yazildi ama bu ortamda derlenip denenmedi (Android araclarina erisim yok). Ilk derlemede hata cikarsa bana yazin.

## APK'yi derleme (iki yol)
**A) Bilgisayara bir sey kurmadan (GitHub Actions)**
1. github.com'da hesap ac, yeni bir repo olustur.
2. Bu klasorun icindekileri (`.github` klasoru dahil) repoya yukle.
3. Repoda **Actions** sekmesi -> **APK derle** -> **Run workflow**.
4. Bitince calisan isin sayfasinda **watermaker-apk** dosyasini indir (icinde `app-debug.apk`).

**B) Android Studio ile**
1. Klasoru Android Studio'da ac, Gradle senkronizasyonunu bekle.
2. Build > Build Bundle(s)/APK(s) > Build APK(s).

## Ayarlar
`app/src/main/java/com/watermakerhospital/control/Config.java` icindeki Wi-Fi adi ve sifresi, kartin `settings.toml` dosyasindakiyle ayni olmali
(`WM_AP_SSID`, `WM_AP_PASS`). Degistirirseniz uygulamayi yeniden derleyin.

## QR ile dagitim
1. `app-debug.apk` dosyasini indirilebilir bir yere koyun (kendi siteniz, Google Drive "herkes indirebilir" linki veya GitHub Releases).
2. O linkin QR kodunu uretin: `python make_qr.py <APK_LINKI>` (once `pip install qrcode pillow`) veya linki bana verin, ben uretirim.
3. QR'i kartin kutusuna / kapagina yapistirin.
4. Telefon QR'i okutunca APK iner. Android "bilinmeyen kaynaklardan yukleme" izni ve (varsa) "Play Protect" uyarisi cikar; "Yine de yukle" deyin.

APK'yi indirmek icin telefonun interneti olmali (mobil veri veya baska Wi-Fi). Uygulama kurulduktan sonra internet gerekmez, sadece kartin agi yeter.

## iPhone
APK iPhone'da calismaz. iPhone icin: Wi-Fi QR'ini okutup WaterMaker agina baglan, Safari'de kart adresini ac, Paylas > "Ana Ekrana Ekle".
Gercek bir iPhone uygulamasi icin Apple Developer hesabi (yillik ucretli) ve App Store/TestFlight gerekir.
