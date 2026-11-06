# 📡 Meshtastic Sözlüğü (Meshtastic Glossary)
### Açık Kaynaklı, Şebekesiz (Off-Grid) LoRa Örgüsel İletişim Terimleri Ansiklopedisi
*Türkçe - İngilizce Detaylı Yazılım ve Donanım Terimleri Sözlüğü*

[![Canlı Sözlük (Wikipedia Formatında)](https://img.shields.io/badge/Canl%C4%B1%20Web%20S%C3%B6zl%C3%BCk-Wikipedia%20Aray%C3%BCz%C3%BC-blue?style=for-the-badge&logo=wikipedia)](https://mserman90.github.io/meshtastic-sozluk/)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Meshtastic%20Resmi-24292e?style=for-the-badge&logo=github)](https://github.com/meshtastic)
[![Lisans](https://img.shields.io/badge/Lisans-GPL--3.0-green?style=for-the-badge)](LICENSE)
[![Yasal Uyarılar](https://img.shields.io/badge/Yasal%20Uyar%C4%B1lar-Sorumsuzluk%20Beyan%C4%B1-orange?style=for-the-badge)](DISCLAIMER.md)
[![Teşekkürler](https://img.shields.io/badge/Te%C5%9Fekk%C3%BCrler-Katk%C4%B1da%20Bulunanlar-purple?style=for-the-badge)](CREDITS.md)

---

## 🌐 Çevrimiçi Ansiklopedi (Wikipedia Arayüzü)
Bu sözlüğün Wikipedia tarzı arama motoruna, A-Z fihristine, bilgi kutularına (infobox) ve çapraz bağlantılarına sahip interaktif web sürümüne aşağıdaki adresten erişebilirsiniz:

👉 **[https://mserman90.github.io/meshtastic-sozluk/](https://mserman90.github.io/meshtastic-sozluk/)**

---

## 📑 İçindekiler
1. [Ağ Mimarisi ve İletişim Protokolü](#1-ağ-mimarisi-ve-iletişim-protokolü-network--protocol)
2. [Donanım, Çipler ve Bileşenler](#2-donanım-çipler-ve-bileşenler-hardware--components)
3. [Cihaz Rolleri ve Çalışma Modları](#3-cihaz-rolleri-ve-çalışma-modları-device-roles)
4. [Güvenlik, Şifreleme ve Kimlik](#4-güvenlik-şifreleme-ve-kimlik-security--encryption)
5. [Yazılım Mimarisi, Firmware ve Protobufs](#5-yazılım-mimarisi-firmware-ve-protobufs-software--firmware)
6. [Radyo Frekansı (RF) ve Yayılım](#6-radyo-frekansı-rf-ve-yayılım-rf--propagation)
7. [Entegrasyonlar ve Harici Modüller](#7-entegrasyonlar-ve-harici-modüller-integrations--modules)
8. [Topluluklar ve Bölgesel Ağlar (Türkiye ve Dünya)](#8--meshtastic-toplulukları-ve-ağları-türkiye-ve-dünya)
9. [SEO ve Arama Motoru Optimizasyonu](#-seo-ve-arama-motoru-optimizasyonu-google-settings)
10. [Yasal Uyarılar ve Sorumsuzluk Beyanı](#️-yasal-uyarılar-ve-sorumsuzluk-beyanı-legal-disclaimers)
11. [Teşekkür ve Katkıda Bulunanlar](#-teşekkür-ve-katkıda-bulunanlar-acknowledgments--credits)

---

## 1. Ağ Mimarisi ve İletişim Protokolü (Network & Protocol)

### 🔹 Mesh Network (Örgüsel Ağ / Ağ Örgüsü)
Merkezi bir yönlendirici (router), baz istasyonu veya internet bağlantısına ihtiyaç duymaksızın, her cihazın hem alıcı hem verici hem de aktarıcı olarak çalıştığı merkeziyetsiz kablosuz topoloji. Meshtastic'te tüm düğümler kapsama alanını el birliğiyle genişletir.

### 🔹 Controlled Flood Routing (Kontrollü Taşkın Yönlendirme)
Meshtastic firmware'inin temel yönlendirme mekanizması. Bir düğüm paket aldığında:
1. Paketin kimliği (Packet ID) daha önce duyulmuş mu diye kontrol edilir.
2. Paket daha önce iletilmemişse ve `hop_limit` 0'dan büyükse, rastgele bir bekleme süresinin (backoff delay) ardından paket tekrar havaya fırlatılır.
3. Böylece rota tablosu oluşturma zahmeti olmadan paket ağda hızla dağıtılır.

### 🔹 Hop Limit (Atlama Sınırı)
Bir paketin kaynaktan çıktıktan sonra kaç kez tekrarlanabileceğini (röle edilebileceğini) belirleyen sayaç. Varsayılan genellikle 3, izin verilen maksimum değer 7'dir. Her tekrarda değer 1 azalır; 0'a ulaştığında paket artık yeniden yayınlanmaz. Bu mekanizma paketlerin sonsuz döngüye (packet storm) girmesini önler.

### 🔹 Hop Start (Başlangıç Atlama Değeri)
Paketi ilk üreten cihazın atadığı orijinal hop limitidir. Örneğin `hop_start: 3` olan bir paket `hop_limit: 1` ile alındıysa, paketin yolda 2 atlama yaptığı (2 düğüm üzerinden geçtiği) anlaşılır.

### 🔹 Node / Peer (Düğüm / Eş)
Meshtastic ağına katılan, LoRa alıcı-vericisine sahip her bir fiziksel cihaz.

### 🔹 Node ID (Düğüm Numarası / Kimliği)
Her cihazın Bluetooth/Wi-Fi MAC adresinin son baytlarından üretilen benzersiz 32-bit tamsayı (hexadecimal olarak `!2a3b4c5d` biçiminde gösterilir). Ağdaki yönlendirme ve doğrudan mesajlaşma bu kimlik üzerinden yapılır.

### 🔹 NodeDB (Düğüm Veritabanı)
Cihazın geçici belleğinde ve flash hafızasında tutulan komşu cihazlar listesi. Her kayıt; komşu düğümün adı, GPS konumu, sinyal gücü (SNR), donanım tipi ve son görülme zaman damgasını barındırır.

### 🔹 Primary Channel (Birincil Kanal)
Cihazın slot 0'ında tanımlanan temel mantıksal kanal. Frekans kanal numarasını, modem ön ayarlarını belirler ve düğümler arası durum eşitlemesi için zorunludur.

### 🔹 Secondary Channel (İkincil Kanal)
Kullanıcıların kendi aralarında özel veya şifreli gruplar oluşturmak amacıyla eklediği 7 adede kadar ek kanal slotu.

### 🔹 Airtime (Hava Süresi / İletim Süresi)
Bir paketin LoRa telsiz frekansı üzerinden havada iletilmesi esnasında geçen süre (milisaniye cinsinden). Paket boyutu, Spreading Factor ve Bant Genişliğine bağlı olarak artar.

### 🔹 Duty Cycle (Görev Döngüsü / Yasal Yayın Oranı)
Radyo frekans regülasyonlarınca (örneğin Avrupa ve Türkiye ETSI kurallarında 868 MHz için saatlik %1) telsiz cihazının toplam sürede havayı meşgul etmesine izin verilen azami yüzde.

### 🔹 Channel Utilization (ChUtil - Kanal Doluluk Oranı)
Düğümün bulunduğu LoRa frekansının çevredeki tüm yayınlar tarafından ne kadar meşgul edildiğini gösteren yüzde. %25'in üzerindeki doluluklar paket çarpışmalarına yol açabilir.

### 🔹 CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)
Cihazın havaya paket basmadan önce frekansı dinleyip, o anda başka bir yayının olup olmadığını kontrol ederek çarpışmaları engelleyen radyo erişim protokolü.

### 🔹 Direct Message (DM - Doğrudan Mesaj)
Yalnızca hedef düğümün çözebileceği biçimde Açık Anahtarlı Kriptografi (PKC) ile uçtan uca şifrelenmiş bire bir mesaj. Ağdaki diğer düğümler bu mesajı iletir fakat içeriğini göremez.

### 🔹 Traceroute (Yol İzleme / Rota Keşfi)
Belirli bir hedef düğüme giden paketin hangi ara röle düğümlerinden ve hangi SNR değerleriyle geçtiğini tespit etmek için kullanılan teşhis aracı.

### 🔹 Store and Forward (Depola ve İlet)
Pil tasarrufu amacıyla uykuya geçen veya kapsama alanından geçici olarak ayrılan istemciler için mesajları kendi belleğinde saklayan ve istemci uyandığında aktaran altyapı mekanizması.

---

## 2. Donanım, Çipler ve Bileşenler (Hardware & Components)

### 🔹 LoRa Transceiver (LoRa Alıcı-Verici Entegresi)
Chirp Spread Spectrum (CSS) teknolojisini kullanarak radyo dalgaları üreten ve çözen tümleşik devre.
- **SX1262:** Düşük güç tüketimi (-148 dBm alıcı duyarlılığı, +22 dBm çıkış gücü) ile günümüzün en popüler Meshtastic telsiz çipi.
- **SX1268:** SX1262'nin 433/470 MHz Asya/Avrupa bantlarına optimize edilmiş versiyonu.
- **SX1276 / SX1278:** Eski nesil, güç tüketimi daha yüksek fakat yaygın kullanılan klasik Semtech LoRa yongaları.
- **LR1121:** Çift bantlı (Sub-GHz ve 2.4 GHz) çalışan, uydu iletişimine de uygun yeni nesil Semtech telsiz yongası.

### 🔹 MCU (Microcontroller Unit - Mikrodenetleyici)
Meshtastic yazılımını (firmware) ve FreeRTOS işletim sistemini yürüten ana işlemci.
- **ESP32 / ESP32-S3:** Espressif üretimi, Wi-Fi ve Bluetooth destekli yüksek işlem kapasiteli çift çekirdekli MCU. Güç tüketimi fazladır ancak yerel WebUI sunucusu ve MQTT ağ geçidi kurabilir.
- **nRF52840:** Nordic Semiconductor üretimi Cortex-M4 tabanlı ultra düşük güçlü yonga. Bluetooth Low Energy (BLE) içerir; tek pille haftalarca çalışabilir.
- **RP2040:** Raspberry Pi Vakfı'nın geliştirdiği uygun maliyetli çift çekirdekli mikrodenetleyici.

### 🔹 PMIC (Power Management IC - Güç Yönetim Entegresi)
Lityum pillerin şarjını, deşarj korumasını, voltaj regülatörlerini ve enerji dağıtımını yöneten akıllı çip (ör. AXP192, AXP2101).

### 🔹 GNSS / GPS Modülü
Düğümün enlem, boylam, rakım ve hassas uydu zaman bilgisini sağlayan modül (ör. u-blox NEO-6M, NEO-8M, MAX-M10S veya ATGM336H).

### 🔹 Ekran Teknolojileri
- **OLED ($128 \times 64$):** SSD1306 veya SH1106 sürücülü, karanlıkta net görünen kompakt I2C ekranlar.
- **E-Paper / E-Ink:** Güneş ışığı altında mükemmel okunabilirlik sunan ve sadece ekran güncellenirken enerji tüketen ultra tasarruflu ekranlar (ör. LilyGO T-Echo).

### 🔹 Anten Konnektörleri
- **SMA / RP-SMA:** Dış kasada bulunan vidalı standart yüksek frekans koaksiyel soket.
- **U.FL / IPEX:** Devre kartı üzerindeki minik çıtçıtlı konektör. Anten takılmadan cihazın vericiye geçirilmesi (TX) çipi kalıcı olarak yakabilir!

### 🔹 Popüler Cihaz Modelleri
- **Heltec WiFi LoRa 32 (V2 / V3):** En yaygın ve ucuz ESP32-S3 tabanlı, dahili OLED ekranlı geliştirme kartı.
- **LilyGO TTGO T-Beam:** 18650 pil yuvası, GPS, dahili PMIC ve LoRa telsizi barındıran klasik saha ve araç takip düğümü.
- **LilyGO T-Echo:** nRF52840 işlemcili, E-ink ekranlı ve GPS'li taşınabilir el cihazı.
- **RAKwireless WisBlock (RAK4631 / RAK19007):** Modüler yapılı, güneş paneliyle aylarca çalışabilen profesyonel nRF52840 altyapı donanımı.
- **LilyGO T-Deck:** Dahili klavyeye, trackball'a ve ekrana sahip, telefonsuz bağımsız kullanılan Meshtastic mesajlaşma cihazı.

---

## 3. Cihaz Rolleri ve Çalışma Modları (Device Roles)

| Rol Adı | Türkçe Karşılığı | Davranış ve Ağ Fonksiyonu |
| :--- | :--- | :--- |
| **CLIENT** | İstemci (Varsayılan) | Standart kullanıcı düğümü. Telefona BLE ile bağlanır, mesajlaşır ve ağdaki paketleri eşit öncelikle tekrarlar. |
| **CLIENT_MUTE** | Sessiz İstemci | Mesaj gönderip alabilir fakat havadan duyduğu yabancı paketleri **asla tekrarlamaz**. Yoğun şehir içi kanallarda hava kirliliğini engeller. |
| **ROUTER** | Altyapı Yönlendiricisi | Yüksek tepe, çatı veya kulelere yerleştirilen cihaz. Gelen paketleri en kısa bekleme süresiyle (öncelikli) yineler; derin uykuya geçmez. |
| **ROUTER_CLIENT** | İstemci Destekli Yönlendirici | Hem yönlendirici gibi agresif paket aktarımı yapar hem de yerel kullanıcıların Bluetooth ile bağlanmasına olanak tanır. |
| **REPEATER** | Salt Röle / Tekrarlayıcı | Kullanıcı arayüzü, ekran ve Bluetooth kapalıdır. Yalnızca paketleri havada dinler ve menzili artırmak için yeniden fırlatır. |
| **TRACKER** | Takip Düğümü | Konumunu düzenli aralıklarla ağa raporlar. Ekran ve gereksiz telemetriler pil tasarrufu için devre dışıdır. |
| **SENSOR** | Sensör Düğümü | Sıcaklık, nem, gaz, basınç sensörlerini periyodik olarak okuyup telemetri portuna basan istasyon modu. |
| **TAK / TAK_TRACKER** | Taktik Harita Terminali | ATAK / CivTAK askeri harita uygulamaları ile entegre çalışan taktik durum farkındalık modu. |
| **LOST_AND_FOUND** | Kayıp Eşya Bulucu | Düşük enerjiyle periyodik kimlik sinyali yayan ve bulan kişinin konum bildirmesine yardımcı olan mod. |

---

## 4. Güvenlik, Şifreleme ve Kimlik (Security & Encryption)

### 🔹 PSK (Pre-Shared Key - Önceden Paylaşılan Anahtar)
Kanal düzeyinde simetrik şifreleme sağlayan anahtar. AES-128 veya AES-256 standardında çalışır. Aynı PSK'ya sahip olmayan cihazlar kanal mesajlarını çözemez.

### 🔹 Default Public Key (`AQ==`)
Meshtastic'in varsayılan açık kanallarında (`LongFast`) kullandığı, şifreleme gizliliği amacı gütmeyen, sadece ağın standart çalışmasını sağlayan genel anahtar (`0x01`).

### 🔹 PKC (Public Key Cryptography - Açık Anahtarlı Kriptografi)
Doğrudan mesajlarda (DM) kullanılan asimetrik şifreleme mimarisi (Curve25519 / Ed25519). Her cihaz kendi özel anahtarına (private key) ve paylaştığı açık anahtara (public key) sahiptir.

### 🔹 Long Name / Short Name
- **Long Name:** Düğümün insan tarafından okunabilen tam adı (ör. `Ankara-Cankaya-Relay`).
- **Short Name:** Cihaz ekranında veya listelerde görünen maksimum 4 karakterlik kısa çağrı kodu (ör. `ANK1`).

### 🔹 Admin Key & Remote Admin
Bir düğümün ayarlarını telsiz üzerinden uzaktan değiştirmek için gereken yetkilendirme anahtarı ve yönetim kanalı.

---

## 5. Yazılım Mimarisi, Firmware ve Protobufs (Software & Firmware)

### 🔹 Google Protocol Buffers (Protobufs)
Meshtastic ekosisteminin can damarı olan ikili (binary) serileştirme standardı (`meshtastic/protobufs`). JSON veya metin yerine veriyi bit düzeyinde sıkıştırarak çok dar LoRa bantlarında iletir.

### 🔹 Meshtastic Port Numaraları (`portnums.proto`)
Her LoRa paketinin başlığında paketin amacını bildiren port kimliği:
- `TEXT_MESSAGE_APP` (1): Standart kullanıcı sohbet mesajları.
- `ROUTING_APP` (2): Ağ içi rota keşfi, paket teslim alındı (ACK) ve hata iletileri.
- `POSITION_APP` (3): GPS enlem, boylam, irtifa ve hassasiyet paketleri.
- `NODEINFO_APP` (4): Cihaz adı, modeli ve MAC kimlik yayını.
- `ADMIN_APP` (32): Uzaktan yönetim ve konfigürasyon komutları.
- `TELEMETRY_APP` (67): Cihaz voltajı, pil yüzdesi ve çevre sensörü verileri.
- `TRACEROUTE_APP` (70): Rota izleme teşhis paketleri.
- `MAP_REPORT_APP` (73): Düğümün harita sunucularına durum bildirme paketi.
- `ATAK_FORWARDER` (256): ATAK Cursor on Target (CoT) veri köprüsü.

### 🔹 PlatformIO
Meshtastic firmware'inin C++ ile geliştirildiği, ESP-IDF, Arduino Core ve nRF SDK kütüphanelerini derleyen modern geliştirme platformu.

### 🔹 Web Flasher
Kullanıcıların herhangi bir program derlemeden Chrome veya Edge tarayıcısı üzerinden Web Serial API kullanarak kartlara doğrudan yazılım yüklemesini sağlayan resmi araç.

---

## 6. Radyo Frekansı (RF) ve Yayılım (RF & Propagation)

### 🔹 Chirp Spread Spectrum (CSS)
LoRa'nın temel modülasyon tekniği. Veri bitleri, frekansı zamanla yukarı ("up-chirp") veya aşağı ("down-chirp") kayan sürekli sinyaller halinde iletilir. Bu sayede sinyal termal gürültü tabanının altında olsa dahi çözülebilir.

### 🔹 Spreading Factor (SF - Yayılma Faktörü)
Bir veri sembolünü kodlamak için kullanılan cıvıltı sayısı ($2^{SF}$).
- **SF7:** Hızlı iletim, kısa hava süresi, daha kısa menzil.
- **SF12:** Çok yavaş iletim, uzun hava süresi, maksimum menzil ve parazit dayanımı.

### 🔹 Bandwidth (BW - Bant Genişliği)
Sinyalin havada kapladığı frekans aralığı (ör. 125 kHz, 250 kHz, 500 kHz). Bant genişliği daraldıkça alıcı duyarlılığı artar fakat iletim süresi uzar.

### 🔹 Coding Rate (CR - Kodlama Oranı)
İletim esnasında gürültüden bozulan bitleri onarmak için eklenen hata düzeltme (Forward Error Correction - FEC) bitlerinin oranı (ör. 4/5, 4/8).

### 🔹 RSSI & SNR
- **RSSI (Received Signal Strength Indicator):** Alınan radyo dalgasının mutlak gücü (dBm cinsinden, ör. -70 dBm güçlü, -125 dBm sınırda).
- **SNR (Signal-to-Noise Ratio):** Sinyalin ortamdaki arka plan gürültüsüne oranı. LoRa negatif SNR değerlerinde (ör. -15 dB) bile paket çözebilir.

### 🔹 VSWR (Voltage Standing Wave Ratio)
Antenin empedans uyumunu ve vericiden çıkan gücün ne kadarının geri yansıdığını gösteren katsayı. 1.0 idealdir, 1.5 altı mükemmeldir, 2.0 üzerindeki değerler cihazın çıkış katına zarar verebilir.

---

## 7. Entegrasyonlar ve Harici Modüller (Integrations & Modules)

### 🔹 MQTT Gateway (Ağ Geçidi)
Wi-Fi veya Ethernet'e bağlı bir Meshtastic cihazının, LoRa üzerinden duyduğu paketleri internetteki bir MQTT broker sunucusuna aktarması. Böylece dünya genelindeki farklı bölgeler internet üzerinden birbirine bağlanabilir.

### 🔹 ATAK / CivTAK Entegrasyonu
Android Taktik Saldırı Kiti (Android Tactical Assault Kit). Meshtastic ATAK eklentisi sayesinde internet ve hücresel şebekenin olmadığı afet veya tatbikat bölgelerinde telsiz üzerinden canlı harita, konum ve rota paylaşımı yapılır.

### 🔹 CoT (Cursor on Target)
Savunma sanayi ve acil durum müdahale ekiplerinin konum, dost/düşman unsurlar ve görev hedeflerini paylaştığı standart XML veri şeması.

### 🔹 Remote Hardware Module
Bir Meshtastic cihazının, kilometrelerce ötedeki diğer bir cihazın GPIO pinine bağlı bir röleyi açıp kapatmasını veya bir anahtarın durumunu telsiz üzerinden okumasını sağlayan firmware modülü.

---

## 8. 👥 Meshtastic Toplulukları ve Ağları (Türkiye ve Dünya)

### 🇹🇷 TA Mesh (tamesh.org / Purgatoria) & Türkiye Topluluğu
[Purgatoria](https://purgatoria.net) çatısı altında geliştirilen [TA Mesh (tamesh.org)](https://tamesh.org), Türkiye genelinde internetten bağımsız, afet ve acil durumlara dayanıklı merkeziyetsiz LoRa iletişim altyapısı kuran öncü topluluk platformudur ([GitHub: Purgatoria/tamesh.org](https://github.com/Purgatoria/tamesh.org)):
- **Özel Kanal:** `TA_Mesh` (Türkiye için ortak açık kanal)
- **Çift Bant Desteği (Cross-Linking):** Hem 433 MHz hem de 868 MHz frekanslarını kullanan cihazları sunucu köprüleri üzerinden çapraz bağlama kabiliyeti.
- **Yerel Altyapı:**
  - **MQTT Sunucusu (Broker):** `mqtt.tamesh.org` (Port: 1883 TCP, 8883 SSL/TLS)
  - **Canlı Harita:** [map.tamesh.org](https://map.tamesh.org)
  - **Topoloji İzleme:** [topo.tamesh.org](https://topo.tamesh.org)
  - **Rehberler:** Cihaz kurulum kılavuzları ve MQTT katılım formu.

### 🏙️ Türkiye Şehir Ağları ve Bölgesel Röleler
- **İstanbul Mesh Ağı:** Çamlıca, Aydos Ormanı, Beylikdüzü ve Boğaz sırtlarındaki güneş enerjili sabit yönlendiriciler (Router) ile kıtalararası köprüleme.
- **Ankara Mesh Ağı:** Çankaya, Dikmen, ODTÜ ve Keçiören sabit istasyonları ile başkent genelinde haberleşme omurgası.
- **İzmir & Ege Mesh Ağı:** Yamanlar ve Nif Dağı röleleri ile körfez hattında kesintisiz acil durum ağı.
- **Diğer Şehirler:** Bursa, Antalya, Kocaeli, Trabzon ve Eskişehir yerel çalışma grupları.
- **Türkiye Standart Ayarları:**
  - **Bölge (Region):** `EU_868` (868.0 - 868.6 MHz yasal ISM bandı)
  - **Modem Profili:** `LongFast` (varsayılan)
  - **Birincil Kanal Anahtarı:** Varsayılan açık anahtar (`AQ==`)

### 🌐 Dünyadaki Öncü Meshtastic Toplulukları
- **[Austin Mesh (austinmesh.org)](https://austinmesh.org) (Teksas, ABD):** Dünyanın en organize ve popüler referans şehir ağı ([GitHub: austin-mesh](https://github.com/austin-mesh)); su kuleleri ve tepelere monte edilen yüzlerce güneş enerjili RAK WisBlock yönlendiricisiyle tüm metropolitan alanı kapsar.
- **UK Mesh (Birleşik Krallık):** 868 MHz bandında Londra ve İngiltere genelini kapsayan geniş çatı röleleri ağı.
- **DL-Mesh / Freifunk (Almanya):** Almanya'nın köklü kablosuz özgür halk ağı Freifunk ile Meshtastic LoRa entegrasyonu.
- **Bay Mesh & NYC Mesh (ABD):** San Francisco Silikon Vadisi ve New York metropolünde teknoloji çalışanlarınca kurulan yüksek katlı gökdelen röleleri.
- **ANZ Mesh (Avustralya & Yeni Zelanda):** Kırsal arazi ve orman yangını erken tespiti için 915 MHz bandında kıta çapında geniş kapsama.
- **Resmi Topluluk Platformları:** [Meshtastic Discord](https://discord.gg/meshtastic) (50k+ üye), [Discourse Forum](https://meshtastic.discourse.group), Reddit (`r/meshtastic`).

### 🗺️ Canlı Ağ Haritaları ve İzleyiciler
- **[MeshMap (meshmap.net)](https://meshmap.net):** Dünya genelindeki ve Türkiye'deki aktif Meshtastic düğümlerinin, sinyal kalitelerinin (SNR) ve batarya seviyelerinin canlı görüntülendiği harita.
- **MeshObserver / LiMe:** Düğümlerin RF komşuluklarını (Neighbor Info) çizelgeleyen topoloji analiz aracı.

---

## 🔍 SEO ve Arama Motoru Optimizasyonu (Google Settings)
Bu sözlük Google, Yandex ve Bing gibi arama motorlarında indekslenecek şekilde tam uyumlu yapılandırılmıştır:
- **Site Haritası:** [sitemap.xml](https://mserman90.github.io/meshtastic-sozluk/sitemap.xml)
- **Tarama Kuralları:** [robots.txt](https://mserman90.github.io/meshtastic-sozluk/robots.txt)
- **Sosyal Medya & Önizleme:** Open Graph & Twitter Cards (`og-image.svg`)
- **Yapılandırılmış Veri:** Schema.org (`WebSite`, `SearchAction`, `DefinedTermSet`)
- **Google Search Console Doğrulaması:** `index.html` içerisindeki `<meta name="google-site-verification" ...>` etiketi ile tek adımda mülk doğrulaması yapılabilir.

---

## ⚖️ Yasal Uyarılar ve Sorumsuzluk Beyanı (Legal Disclaimers)
Bu proje, web sitesi ve sözlük içeriği yalnızca **eğitim, teknik araştırma ve bilgi edinme** amacıyla sunulmuştur:
1. **Acil Durum ve Yaşam Güvenliği:** Meshtastic sistemleri resmi acil durum haberleşme kanallarının (112 Acil Çağrı, AFAD vb.) yerini tutamaz; hayati güvenlik amaçlı birincil sistem olarak kullanılmamalıdır.
2. **Radyo Frekans Mevzuatı (BTK / ETSI):** LoRa cihazlarını kullanırken bulunduğunuz ülkenin Kısa Mesafe Telsiz Cihazları (SRD/KMT) yönetmeliklerine (Türkiye için 868.0 - 868.6 MHz bandı, azami çıkış gücü ve %1 Görev Döngüsü / Duty Cycle kısıtlamalarına) uyulması yasal zorunluluktur. Lisanssız frekanslarda izinsiz harici güçlendirici (PA) kullanılması cezai sorumluluk doğurur.
3. **Kriptografi ve Amatör Telsiz:** Amatör telsiz frekanslarında yapılan yayınlarda şifreleme kullanılması yasaktır; şifreleme yalnızca halka açık ISM bantlarında serbesttir.
4. **Donanım Emniyeti:** Anten takılmadan cihazların vericiye (TX) geçirilmesi telsiz çipinin yanmasına (VSWR hasarı) neden olabilir. Lityum pillerle çalışırken yangın riskine karşı dikkatli olunmalıdır.
5. **Marka:** Meshtastic®, Meshtastic LLC'nin tescilli markasıdır. Bu site bağımsız bir açık kaynak topluluk çalışmasıdır.

Detaylı yasal bildirimler için [DISCLAIMER.md](DISCLAIMER.md) dosyasını inceleyiniz.

---

## 🙏 Teşekkür ve Katkıda Bulunanlar (Acknowledgments & Credits)
Bu açık kaynak sözlüğün ortaya çıkmasında ve teknik içeriğinin zenginleştirilmesinde emeği geçen kişi, topluluk ve kurumlara teşekkür ederiz:
- **Kevin Hester (geeksville) & Meshtastic Çekirdek Ekibi:** Projenin kurucu vizyonu, protokol tasarımı ve [meshtastic](https://github.com/meshtastic) depolarındaki açık kaynak mimari için.
- **[Purgatoria](https://purgatoria.net) & [TA Mesh (tamesh.org)](https://tamesh.org) Ekibi:** Türkiye'de Meshtastic altyapısını kuran, yerli MQTT sunucusu (`mqtt.tamesh.org`), canlı haritalar ve 433/868 MHz çapraz köprülerini geliştiren öncü çalışmaları için ([GitHub: Purgatoria/tamesh.org](https://github.com/Purgatoria/tamesh.org)).
- **Türkiye Afet Haberleşmesi Gönüllüleri & TRAC:** 6 Şubat ve sonrasında sivil telsiz afet haberleşmesine emek veren tüm arama-kurtarma gönüllüleri, AKUT/AFAD paydaşları ve radyo amatörleri için.
- **[Austin Mesh (austinmesh.org)](https://austinmesh.org):** Açık kaynak şehir ağı ve güneş enerjili kule rölesi kılavuzlarıyla dünyaya referans oldukları için ([GitHub: austin-mesh](https://github.com/austin-mesh)).
- **Liam Cottle:** [MeshMap (meshmap.net)](https://meshmap.net) canlı küresel izleme haritasını geliştirdiği için.
- **Jan Gromes (RadioLib):** Semtech SX1262 ve LoRa telsiz entegrelerinin açık kaynak sürücü kütüphanesini geliştirdiği için.
- **Semtech, Espressif, Nordic, RAKwireless, Heltec & LilyGO:** LoRa yongaları, modülleri ve açık geliştirici donanımlarını erişilebilir kıldıkları için.
- **Wikimedia Vakfı & Wikipedia Topluluğu:** Bilgiyi özgürleştirme misyonu ve ilham verici MediaWiki tasarımı için.

Ayrıntılı teşekkür listesi ve referanslar için [CREDITS.md](CREDITS.md) belgesini inceleyebilirsiniz.

---

## 🤝 Katkıda Bulunma
Sözlüğe yeni terimler, çip modelleri veya Türkçe açıklamalar eklemek için bir Pull Request açabilir veya Issue oluşturabilirsiniz.

## 📄 Lisans
Bu dokümantasyon ve web sözlüğü [GPL-3.0](LICENSE) altında açık kaynak olarak sunulmuştur. Meshtastic projesinin resmi GitHub deposu [meshtastic/firmware](https://github.com/meshtastic/firmware) adresindedir.
