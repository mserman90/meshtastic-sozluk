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

### 🔹 Off-Grid İletişim (Off-Grid Communication)
Hücresel baz istasyonları (GSM/LTE/5G), internet servis sağlayıcıları (ISP), uydu abonelikleri veya elektrik şebekesinden bağımsız otonom telsiz haberleşme mimarisi. Afetlerde, arama-kurtarmada ve vahşi doğada harici hiçbir altyapıya ihtiyaç duymadan cihazdan cihaza kesintisiz haberleşme olanağı tanır.

### 🔹 Merkeziyetsiz Ağ Mimarisi (Decentralized Network Architecture)
Merkezi bir sunucu, baz istasyonu denetleyicisi veya ana omurga gerektirmeyen, tüm düğümlerin eşit yetkiyle veri aktarımına katıldığı kendi kendini organize eden örgü (mesh) topolojisi. Tek bir hata noktası (Single Point of Failure - SPOF) barındırmaz; düğümler kapansa dahi ağ otomatik olarak alternatif rotalar bularak çalışmaya devam eder (Self-Healing).

### 🔹 Eşler Arası İletişim (Peer-to-Peer / P2P)
İstemci-sunucu hiyerarşisi olmaksızın, iki veya daha fazla LoRa telsiz düğümünün doğrudan birbirleriyle veya aracı komşu eşler üzerinden veri alıp vermesini sağlayan haberleşme modeli.

### 🔹 Hava Süresi Adaleti ve Spektrum Yönetimi (Airtime Fairness & Fair Access)
Paylaşımlı lisanssız RF frekans bandının tek bir düğüm veya aşırı konuşkan cihaz tarafından tıkanmasını önleyen algoritma bütünü. Token-bucket mekanizması ve kanal doluluğuna göre dinamik gecikmeler (backoff) uygulayarak acil durum ve metin mesajlarına spektrumda her zaman öncelikli ve adil yer açar.

### 🔹 Genel Yayın İletişimi (Broadcast Messaging)
Ağdaki tüm düğümlerin veya belirli bir kanala abone olmuş tüm telsizlerin alması amacıyla `0xFFFFFFFF` (`NODENUM_BROADCAST`) genel yayın adresine gönderilen şifreli veya açık paketler. Afet duyuruları, durum ikazları ve grup mesajlaşmaları bu yöntemle tüm ağa taşkın yönlendirme (flood routing) ile yayılır.

### 🔹 Mesh Network (Örgüsel Ağ / Ağ Örgüsü)
Merkezi bir yönlendirici (router), baz istasyonu veya internet bağlantısına ihtiyaç duymaksızın, her cihazın hem alıcı hem verici hem de aktarıcı olarak çalıştığı merkeziyetsiz kablosuz topoloji. Meshtastic'te tüm düğümler kapsama alanını el birliğiyle genişletir.

### 🔹 Controlled Flood Routing (Kontrollü Taşkın Yönlendirme)
Meshtastic firmware'inin temel yönlendirme mekanizması. Bir düğüm paket aldığında:
1. Paketin kimliği (Packet ID) daha önce duyulmuş mu diye kontrol edilir.
2. Paket daha önce iletilmemişse ve `hop_limit` 0'dan büyükse, rastgele bir bekleme süresinin (backoff delay) ardından paket tekrar havaya fırlatılır.
3. Böylece rota tablosu oluşturma zahmeti olmadan paket ağda hızla dağıtılır.

### 🔹 Yönetilen Taşkın Yönlendirme (Managed Flooding)
Meshtastic'in kör taşkın (naive flooding) yerine; atlama sınırları (hop limits), paket tekilleştirme, SNR tabanlı çekişme pencereleri ve havada tekrar bastırmasını harmanlayarak geliştirdiği akıllı örgüsel yönlendirme algoritması (`Mesh Broadcast Algorithm`). Ağdaki yayın fırtınalarını (broadcast storm) önler.

### 🔹 SNR Ağırlıklı Çekişme Penceresi ve Mesafe Önceliği (SNR-Weighted Contention)
"Uzak Düğümler Önce İletir" (*Farther nodes flood first*) prensibiyle çalışan radyo gecikme algoritması. Zayıf sinyal (düşük SNR) alan en uzaktaki rölelere daha kısa bekleme süresi verilir; böylece paket tek sıçramada en uzağa ulaştırılırken, yakındaki cihazlar gereksiz tekrarları bastırır.

### 🔹 Tekrar Yayınını Bastırma (Rebroadcast Suppression)
Bir düğümün havadaki bir paketi tekrarlamak üzere geri sayım sayacındayken (backoff delay), komşu bir rölenin aynı paketi başarıyla havaya bastığını duyması durumunda kendi iletimini iptal etmesi. Hava süresinden büyük tasarruf sağlar.

### 🔹 Sonraki Atlama Yönlendirmesi (Next-Hop Routing)
Doğrudan mesajlarda (DM) tüm ağı taşkınla meşgul etmek yerine, NodeDB önbelleğinde saklanan en iyi ara komşu rotası üzerinden hedefe yönelik iletim (directed unicast) yapan verimli yönlendirme tekniği.

### 🔹 Uyarlamalı Yayın Ölçekleme ve Dinamik Kısma (Adaptive Broadcast Scaling)
Ağdaki aktif düğüm sayısı arttıkça veya frekans doluluğu yükseldikçe, NodeInfo, Position ve Telemetry durum paketlerinin gönderim periyotlarını otomatik çarpanlarla uzatarak 100+ düğümlü büyük ağlarda kilitlenmeyi önleyen dengeleme mekanizması.

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

### 🔹 Implicit ACK (Örtük Teyit / Havada Tekrar Tespiti)
Bir düğümün paketi havaya fırlattıktan sonra dinlemeye geçip, komşu bir rölenin aynı paketi tekrarladığını (rebroadcast ettiğini) telsizden duymasıyla paketin başarıyla iletildiğini anladığı mekanizma. Ekstra onay paketi basılmasını önleyerek kıymetli hava süresinden (airtime) tasarruf sağlar.

### 🔹 Want ACK (Açık Teyit Talebi Bayrağı)
Paket başlığında bulunan ve hedef düğümden kesin bir açık alındı onayı (Explicit ACK) dönmesini zorunlu kılan kontrol biti (`MeshPacket.want_ack`). Doğrudan mesajlarda (DM) ve uzaktan yönetim komutlarında mesajın karşı tarafa ulaştığından emin olmak için kullanılır.

### 🔹 Channel Hash (Kanal Sağlama Özeti)
Paket başlığında yer alan 1 baytlık hafif hash değeri. Düğümler havadan yakaladıkları bir paketi işlemciyi yorup şifresini çözmeye çalışmadan önce bu özete bakarak abonesi olmadıkları kanalların paketlerini anında işlemden düşürür.

### 🔹 Bölge Frekans Ayarı ve UNSET Güvenlik Durumu (Region UNSET)
Yeni kurulan veya fabrika ayarlarına sıfırlanan cihazların, yasal olmayan bir telsiz frekansında yayın yapmasını engellemek için kullanıcı açıkça bir ülke/bölge seçene kadar vericisini (TX) kapalı tuttuğu güvenlik durumu. Türkiye için yasal mod `EU_868` seçilmelidir.

### 🔹 Kanal QR Kodu ve URL ile Hızlı Paylaşım (Channel Sharing)
Kanal adını, AES şifreleme anahtarını ve modem profilini tek bir optik QR koduna veya web bağlantısına (`meshtastic.org/e/#...`) paketleyerek diğer kullanıcıların kamera taramasıyla saniyeler içinde kanala katılmasını sağlayan pratik paylaşım yöntemi.

---

## 2. Donanım, Çipler ve Bileşenler (Hardware & Components)

### 🔹 LoRa Transceiver (LoRa Alıcı-Verici Entegresi)
Chirp Spread Spectrum (CSS) teknolojisini kullanarak radyo dalgaları üreten ve çözen tümleşik devre.
- **SX1262:** Düşük güç tüketimi (-148 dBm alıcı duyarlılığı, +22 dBm çıkış gücü) ile günümüzün en popüler Meshtastic telsiz çipi.
- **SX1268:** SX1262'nin 433/470 MHz Asya/Avrupa bantlarına optimize edilmiş versiyonu.
- **SX1276 / SX1278:** Eski nesil, güç tüketimi daha yüksek fakat yaygın kullanılan klasik Semtech LoRa yongaları.
- **LR1121:** Çift bantlı (Sub-GHz ve 2.4 GHz) çalışan, uydu iletişimine de uygun yeni nesil Semtech telsiz yongası.
- **LR2021:** Semtech'in ultra düşük güçlü, Sub-GHz (863-928 MHz) ve 2.4 GHz LoRa/FLRC modülasyonlu, -141 dBm alıcı duyarlılığına sahip yeni nesil telsiz çipi (Seeed Studio MeshTracker X1'de kullanılır).

### 🔹 MCU (Microcontroller Unit - Mikrodenetleyici)
Meshtastic yazılımını (firmware) ve FreeRTOS işletim sistemini yürüten ana işlemci.
- **ESP32 / ESP32-S3:** Espressif üretimi, Wi-Fi ve Bluetooth destekli yüksek işlem kapasiteli çift çekirdekli MCU. Güç tüketimi fazladır ancak yerel WebUI sunucusu ve MQTT ağ geçidi kurabilir.
- **nRF52840:** Nordic Semiconductor üretimi Cortex-M4 tabanlı ultra düşük güçlü yonga. Bluetooth Low Energy (BLE) içerir; tek pille haftalarca çalışabilir.
- **RP2040:** Raspberry Pi Vakfı'nın geliştirdiği uygun maliyetli çift çekirdekli mikrodenetleyici.

### 🔹 PMIC (Power Management IC - Güç Yönetim Entegresi)
Lityum pillerin şarjını, deşarj korumasını, voltaj regülatörlerini ve enerji dağıtımını yöneten akıllı çip (ör. AXP192, AXP2101).

### 🔹 GNSS / GPS Modülü
Düğümün enlem, boylam, rakım ve hassas uydu zaman bilgisini sağlayan modül (ör. u-blox NEO-6M, NEO-8M, MAX-M10S veya ATGM336H).

### 🔹 Çift Bant GNSS Konumlandırma (Dual-Band L1 + L5 GNSS)
Standart L1 frekansının yanı sıra modern sivil L5 frekansını eşzamanlı işleyen yeni nesil uydu konumlandırma mimarisi. Kentsel kanyonlarda (bina yansımaları), derin vadilerde ve yoğun ağaç örtüsü altında çok yollu (multipath) sinyal yansımalarını ve iyonosferik sapmaları filtreleyerek metre-altı hassasiyet ve hızlı ilk kilitlenme (TTFF) sağlar.

### 🔹 Ekran Teknolojileri
- **OLED ($128 \times 64$):** SSD1306 veya SH1106 sürücülü, karanlıkta net görünen kompakt I2C ekranlar.
- **E-Paper / E-Ink:** Güneş ışığı altında mükemmel okunabilirlik sunan ve sadece ekran güncellenirken enerji tüketen ultra tasarruflu ekranlar (ör. LilyGO T-Echo).

### 🔹 Anten Konnektörleri
- **SMA / RP-SMA:** Dış kasada bulunan vidalı standart yüksek frekans koaksiyel soket.
- **U.FL / IPEX:** Devre kartı üzerindeki minik çıtçıtlı konektör. Anten takılmadan cihazın vericiye geçirilmesi (TX) çipi kalıcı olarak yakabilir!

### 🔹 TCXO (Sıcaklık Kompanzasyonlu Kristal Osilatör)
Aşırı sıcak veya dondurucu soğuk hava koşullarında telsiz frekansının kaymasını önleyen yüksek kararlılıklı osilatör bileşeni. SX1262 LoRa yongalarında dar bant genişliklerinde (125 kHz) frekans kayması yaşanmadan paketlerin çözülebilmesini sağlar; zorlu kış şartlarındaki dağ rölelerinde hayati öneme sahiptir.

### 🔹 Popüler Cihaz Modelleri
- **Heltec Automation Ekosistemi:**
  - **WiFi LoRa 32 (V2 / V3 / V4):** En yaygın ESP32-S3 tabanlı, dahili 0.96" OLED ekranlı, Type-C portlu ve bütçe dostu klasik geliştirme kartı.
  - **Vision Master Serisi (E213 / E290 / T190):** ESP32-S3R8 MCU, HT-RA62 (SX1262) telsizi; 2.13" / 2.90" E-Ink veya 1.9" TFT ekranlı, InkHUD uyumlu çok yönlü terminaller.
  - **Mesh Node T114:** Ultra düşük güç tüketimli Nordic nRF52840 MCU, SX1262 LoRa, çift pil/solar girişi ve GNSS portuna sahip yeni nesil Heltec kartı.
  - **MeshPocket:** Qi2 manyetik kablosuz şarjlı (5000 / 10000 mAh) powerbank kasasına entegre nRF52840, SX1262 ve 2.13 inç E-Ink ekranlı hibrit acil durum telsizi.
  - **Capsule Sensor V3:** ESP32-S3FN8, SX1262, 250 mAh pil, manyetik şarj portu ve değiştirilebilir modüler sensör soketli IP65 su geçirmez minyatür telemetri kapsülü.
  - **HT-CT62 & HT-RA62:** ESP32-C3 RISC-V veya SX1262 tabanlı, özel DIY kartlar ve gömülü projeler için yüzey montajlı (SMD) minyatür LoRa modülleri.
  - **Heltec Buton Mantığı:** PRG/PROG tuşuna kısa basış ekran döngüsü, ~0.5 sn menü açma/onaylama, ~4 sn kapatma ve açılışta seri bootloader geçişi.
  - **MOSFET Periferik Güç Anahtarlaması:** Harici GT-U7 GPS modüllerinin bataryayı hızla bitirmesini önlemek için GPIO üzerinden firmware kontrollü transistörle güç kesme mimarisi.
- **LilyGO Telsiz ve Terminal Ekosistemi:**
  - **LilyGO TTGO T-Beam (v1.1 / v1.2):** 18650 pil yuvası, u-blox GPS, dahili AXP192/AXP2101 PMIC ve LoRa telsizi barındıran klasik saha ve araç takip düğümü.
  - **T-Beam Supreme (ESP32-S3 Core):** ESP32-S3FN8 çift çekirdekli işlemci, Semtech SX1262, u-blox NEO-M10S GNSS, BME280 çevre sensörü (sıcaklık/nem/basınç), QMI8658 IMU, manyetometre ve AXP2101 PMIC'li amiral gemisi.
  - **T-Beam 1W (High-Power):** 32 dBm (~1.5 Watt) tepe çıkış gücü sağlayan RF amplifikatörlü ve minyatür aktif soğutma fanlı yüksek güçlü omurga düğümü.
  - **T-Echo & T-Echo Plus:** Nordic nRF52840, SX1262, 1.54" E-Paper ekran, Quectel L76K GPS, NFC ve kapasitif dokunmatik navigasyonlu ultra düşük güçlü el cihazı.
  - **T-Deck & T-Deck Plus:** ESP32-S3 ana MCU + ikincil ESP32-C3 klavye denetleyicisi, 2.8" IPS dokunmatik ekran, mekanik trackball, QWERTY klavye, dahili GPS ve 2000 mAh bataryalı bağımsız el terminali.
  - **T-Lora Pager (T-Pager):** Semtech LR1121 (Sub-GHz & 2.4 GHz) telsiz, ESP32-S3, u-blox MIA-M10Q GPS, BHI260AP AI-IMU, ES8311 ses çipi ve katlanabilir antenli retro taktik el terminali.
  - **T-LoRa C6:** 32-bit RISC-V mimarili ESP32-C6 yongası, Wi-Fi 6, BLE 5, SX1262 telsizi ve dahili PCB antenli bütçe dostu kompakt kart.
  - **T-Watch S3 / S3 Plus:** Giyilebilir akıllı saat form faktöründe, ESP32-S3, SX1262, dokunmatik ekran, haptik titreşim motoru ve mikrofon/hoparlörlü bilek Meshtastic düğümü.
  - **T5 E-Paper S3 Pro:** 4.7 inç 960x540 16-kademe gri tonlamalı dev dokunmatik e-mürekkep ekran, GT911 panel, ESP32-S3 ve SX1262'li masaüstü/saha bilgi terminali.
  - **Mini ePaper S3:** 1.02 inç minyatür e-mürekkep ekranı ve 18350 lityum pil yuvasıyla ultra hafif sıfır-bekleme-tüketimli cep cihazı.
  - **InkHUD Arayüz Yazılımı:** T-Echo ve e-paper cihazlar için hayalet görüntüyü (ghosting) önleyen ve kapasitif arka ışık mandallaması sunan özel Meshtastic arayüzü.
  - **X-Powers AXP2101 PMIC:** Çok kanallı voltaj regülasyonu, Li-ion şarj yönetimi, NTC pil sıcaklık takibi ve I2C telemetrisi sağlayan gelişmiş güç yönetim entegresi.
- **RAKwireless WisBlock (RAK4631 / RAK19007):** Modüler yapılı, güneş paneliyle aylarca çalışabilen profesyonel nRF52840 altyapı donanımı.
  - **RAK19007 / RAK19003 Taban Kartları:** USB-C, solar şarj ve lehim gerektirmeyen sensör yuvaları barındıran 2. nesil WisBlock taşıyıcı kartları.
  - **RAK4631 Çekirdek Modülü:** Nordic nRF52840 ve Semtech SX1262 içeren ultra düşük güçlü ($< 15\text{ }\mu\text{A}$) ana işlemci modülü.
  - **RAK12500 GNSS & RAK13800 Ethernet:** Tak-çalıştır u-blox ZOE-M8Q GPS ve kablolu 10/100 Ethernet MQTT ağ geçidi genişleme modülleri.
- **RAK WisMesh Serisi (Kullanıma Hazır Fabrika Cihazları ve Modülleri):**
  - **WisMesh Board ONE:** nRF52840, SX1262, 1.3" OLED ekran ve GPS yuvasını birleştiren Meshtastic'e özel entegre anakart.
  - **WisMesh Pocket:** Özel koruyucu kasalı, 1.3" OLED ekranlı, butonlu ve bataryalı kullanıma hazır kompakt el telsizi.
  - **WisMesh Tap:** Dokunmatik ekranlı bağımsız Meshtastic mesajlaşma ve harita terminali.
  - **WisMesh Tag:** nRF52840, SX1262, AT6558R GNSS ve ST LIS2DH ivmeölçer barındıran IP66 su ve toz geçirmez kompakt personel/varlık takip cihazı.
  - **WisMesh Pod (RAK10708):** Kutudan çıktığı anda kullanıma hazır; çoklu-takımyıldız GNSS, hareket algılayıcı LIS2DH, buzzer ve 1000 mAh bataryalı entegre cep düğümü.
  - **WisMesh 1W Booster Starter Kit:** 1 Watt (+30 dBm) çıkış gücüne sahip RAK13302 LoRa amplifikatörü ve RAK3401 nRF52840 işlemcisiyle uzun menzil ve derin kanyonlar için geliştirilmiş güçlendirilmiş platform.
    - **RAK13302 1W LoRa Modülü:** Semtech SX1262 ve Skyworks SKY66122 PA/LNA içeren, 1000 mW TX gücü için harici 5V besleme gerektiren WisBlock telsiz modülü.
    - **RAK3401 Çekirdek Modülü:** 1W RF modülünü sürmek için optimize edilmiş Nordic nRF52840 çekirdek kartı.
  - **WisMesh Repeater & Repeater Mini:** Entegre güneş paneli, IP67 Unify kutu, 3200 mAh batarya ve fiberglas koliner antenle donatılmış bağımsız dış ortam dağ/çatı aktarıcı istasyonları.
  - **WisMesh Gateway (Ethernet & Wi-Fi):** RAK13800 Ethernet + RAK19018 PoE veya RAK11200 ESP32 Wi-Fi üzerinden çalışan IP67 endüstriyel dış mekan LoRa-MQTT ağ geçidi istasyonu.
  - **ST LIS2DH 3-Eksenli İvmeölçer:** WisMesh Tag ve Pod'da harekete duyarlı akıllı uyku (smart sleep) ve otomatik konum tetikleme sağlayan MEMS hareket sensörü.
- **Seeed Studio Donanım Ekosistemi:**
  - **SenseCAP Indicator:** 3.95" / 4.0" 480x480 RGB kapasitif dokunmatik ekran, ESP32-S3 + RP2040 çift MCU mimarisi, Semtech SX1262 telsizi ve Grove portlarıyla donatılmış masaüstü/araç içi kontrol paneli.
  - **SenseCAP Solar Node (P1 / P1 Pro):** Entegre 5W güneş paneli, 4 adet 18650 pil yuvası, nRF52840 MCU, SX1262 telsiz, CN3165 solar şarj ve XIAO L76K GPS barındıran ağır hizmet dış ortam rölesi.
  - **SenseCAP MeshTracker X1:** Kredi kartı boyutunda (IP66 su geçirmez), Semtech LR2021 LoRa çipi, çift bant L1+L5 GNSS, dahili barometre, buzzer ve 1100 mAh Li-ion pille donatılmış bağımsız takip cihazı.
  - **SenseCAP Card Tracker T1000-E:** nRF52840 ve Semtech SX1262 LoRa telsizine sahip, manyetik pogo-pin şarjlı, MediaTek AG3335 GNSS'li, ışık ve sıcaklık sensörlü ultra ince kart takip donanımı.
    - **Manyetik Pogo-Pin Arayüzü:** Su geçirmez gövde contasını bozmadan pil şarjı, USB seri port ve DFU firmware yükleme sağlayan yaylı kontak sistemi.
    - **T1000-E Tek Tuş Mantığı:** Tek buton üzerinden çift tıkla konum pingi, 3 tıkla GPS aç/kapat, 4 tıkla sessize alma ve kablo takılırken basılı tutarak DFU moduna alma.
  - **Wio Tracker L1 & L1 Lite:** USB Type-C, harici güneş paneli ve 3.7V Li-ion batarya üçlü güç girişli; çoklu-GNSS, 1.3" OLED veya 2.13" E-Ink ekranlı esnek takip ve telemetri düğümü.
  - **Wio Tracker L2 Pro:** 3.2 inç renkli dokunmatik TFT ekranlı, ESP32-S3 (Wio-S3 SoM, 16MB Flash, 8MB PSRAM), SX1262 telsiz, L76K GNSS, 3000 mAh batarya ve MicroSD çevrimdışı harita destekli bağımsız el terminali.
    - **Seeed Wio-S3 Çekirdek Modülü:** Çift çekirdekli Xtensa LX7 işlemci, 8MB Octal PSRAM ve 16MB Flash içeren yüksek grafik performanslı sistem modülü.
    - **Çevrimdışı Harita (Offline Map Tiles):** İnternetsiz afet ortamlarında OpenStreetMap karolarını MicroSD karttan okuyarak mesh düğümlerini harita üzerinde görselleştiren mimari.
  - **Seeed XIAO & Wio-SX1262 Kiti:** Başparmak tırnağı boyutundaki (XIAO ESP32-S3 / XIAO nRF52840) mikro kontrolcüleri Wio-SX1262 LoRa eklentisiyle birleştiren modüler DIY geliştirme kiti.
    - **Wio-SX1262 / Wio-SX1262S Modülleri:** nRF52 ve ESP32-S3 kitleri için özel optimize edilmiş dahili pin dizilimine sahip minyatür LoRa alıcı-vericisi.
  - **Wio-WM1110 Modülü:** Nordic nRF52840 MCU ile Semtech LR1110 (LoRa + GNSS + Wi-Fi Sniffer) hibrit konumlandırma ve IoT geliştirme kartı.
  - **Wio-E5 (STM32WLE5JC):** ARM Cortex-M4 işlemci ile SX126x telsizini tek silikon çipte birleştiren monolitik LoRaWAN ve Meshtastic SoC modülü.
  - **Grove Modüler Bağlantı Sistemi:** 4-pinli standart polarize konnektörle çevre sensörlerinin (BME680, SHT40 vb.) lehimleme gerektirmeden tak-çalıştır bağlanmasını sağlayan ekosistem.
- **B&Q Consulting Donanımları (Neil Hao Tasarımları):**
  - **Nano G2 Ultra & Nano Serisi:** Doğa sporları için özel tasarlanmış; nRF52840, entegre geniş bantlı iç anten (815-940 MHz), GPS ve hafif dayanıklı kasalı kompakt el cihazı.
  - **Station G1 / G2 Serisi:** Yüksek güçlü RF güç amplifikatörlü (PA), düşük gürültülü ön yükselticili (LNA), pirinç SMA soketli sabit baz istasyonu ve omurga rölesi.
- **Elecrow Donanım ve HMI Ekosistemi:**
  - **ThinkNode M1:** nRF52840, SX1262 LoRa, dahili GNSS GPS ve güneş ışığında okunabilir E-Ink ekranlı taşınabilir saha düğümü.
  - **CrowPanel Advance HMI Serisi:** 2.4" ile 7.0" arası canlı IPS dokunmatik ekranlı, ESP32-S3 tabanlı, masaüstü Meshtastic UI (MUI) ekran terminali.
  - **Elecrow MeshStick:** CH341 USB-SPI köprülü; Raspberry Pi, ev sunucusu veya Linux bilgisayarlarda `meshtasticd` çalıştırmak için tak-çalıştır USB LoRa telsiz çubuğu.
- **muzi ᴡᴏʀᴋꜱ Taktik ve Modüler Sistemleri:**
  - **R1 Neo:** Uçak sınıfı CNC alüminyum ve karbon fiber PETG kasalı, tam donanımsal GPS güç kesme anahtarlı, NTC batarya korumalı ve kırbaç antenli taktik arazi terminali.
  - **BASE Modüler Sistem (Base Uno & Duo):** Base Uno (nRF52840 + SX1262) ve Base Duo (Semtech LR1121 Sub-GHz & 2.4 GHz) çekirdeklerini barındıran modüler taşıyıcı mimari.
  - **Super I/O Eklenti Kartı:** Base Uno/Duo üzerine dikey istiflenen (stackable); sisteme bağımsız GPS, ekran soketi ve sensör arayüzü kazandıran genişleme modülü.
- **M5Stack ve Raspberry Pi Ekosistemi:**
  - **M5Stack Cardputer:** 56 tuşlu tam QWERTY klavyeli, 1.14 inç renkli ekranlı, ESP32-S3, 1750 mAh dahili pil ve tak-çıkar LoRa/GPS modüllü bağımsız mesajlaşma terminali.
  - **M5Stack Unit C6L:** 32-bit RISC-V mimarili ESP32-C6 çipi, SX1262 telsiz, 0.66" OLED ekran, RGB durum LED'i ve sesli buzzer içeren cep düğümü.
  - **M5Burner:** M5Stack Cardputer ve LoRa cihazlarına resmi Meshtastic bellenimini tek tıkla yükleyen resmi GUI aracı.
  - **Raspberry Pi Pico & Pico 2 (RP2040 / RP2350):** Waveshare LoRa modülü eklenerek tam teşekküllü Meshtastic düğümüne dönüştürülen düşük maliyetli açık donanım platformu.
  - **Waveshare Pico LoRa Modülü:** Pico'nun 40 pinli başlığına doğrudan oturan, Semtech SX1262 telsizli ve SMA soketli tak-çalıştır genişleme kartı.
  - **CardKB I2C Donanım Klavyesi:** Pico ve ESP32 kartlarının GPIO 4/5 (I2C) pinlerine bağlanarak telefonsuz metin ve Canned Message girişi sağlayan 50 tuşlu mini klavye.
- **Donanım Destek Seviyeleri ve Ekosistem Yönetişimi:**
  - **Resmi Destekli Donanımlar (Officially Supported Tier):** Partner ve Backer programına dahil üreticilerin ürettiği (RAK4631, SenseCAP T1000-E, Heltec V3, T-Beam vb.); çekirdek geliştirici ekibi tarafından doğrudan test edilen, Web Flasher ve istemci uygulamalarında tam desteklenen birinci sınıf donanım sınıfı.
  - **Topluluk Destekli Donanımlar (Community Supported Tier):** Üretici sponsorluğu bulunmayan, üretimi sonlanmış (legacy) veya bağımsız açık kaynak DIY projeleri; GitHub derlemeleri süren fakat teknik desteği Discord ve forum topluluğuna dayanan kartlar.
  - **Meshtastic Partner & Backer Programı:** Donanım üreticilerinin Meshtastic açık kaynak projesine altyapı ve finansman sağlayarak cihazlarının resmi sertifikasyon ve öncelikli yazılım desteği almasını güvenceye alan iş birliği çerçevesi.
  - **Topluluk CI/CD Derleme Matrisi:** Her kod değişikliğinde onlarca farklı resmi ve topluluk kart hedefini GitHub Actions ve PlatformIO ile eşzamanlı derleyerek geriye dönük uyumluluğu koruyan otomatik test hattı.

### 🔹 USB-Seri Dönüştürücüler ve Sürücüler (Serial Drivers)
Bilgisayar ile cihaz arasında seri haberleşme (UART) ve firmware yükleme sağlayan köprü entegreleri:
- **Silicon Labs CP210x (CP2102 / CP2104):** Heltec, TTGO T-Beam ve klasik ESP32 kartlarında en yaygın kullanılan köprü entegresi.
- **WCH CH340 & CH9102:** LilyGO T-Beam v1.2 ve birçok modern kartta kullanılan yüksek hızlı (4 Mbps) USB-UART dönüştürücüler.
- **Dahili USB CDC ACM:** nRF52840, ESP32-S3 ve RP2040 işlemcilerinde harici köprü çipi olmadan doğrudan SoC üzerinden tak-çalıştır sanal seri port sağlayan yerel USB sınıfı.

### 🔹 SWD / SWDIO ve Donanım Programlama
Önyükleyicisi silinmiş veya çökmüş (bricked) nRF52840 ve STM32 cihazlarını J-Link, ST-Link veya Picoprobe ile 2 pin üzerinden (SWDIO/SWCLK) bare-metal programlayıp hayata döndüren donanım arayüzü.

### 🔹 STM32 Dahili ROM Bootloader
STM32 mikrodenetleyicili LoRa kartlarında (ST B-L072Z-LRWAN1 vb.) `BOOT0` pini HIGH durumdayken dahili ROM bootloader üzerinden doğrudan UART portuyla (`stm32flash`) firmware yükleme yöntemi.

### 🔹 STM32 Bellek Okuma Koruması (RDP Kaldırma)
STM32 mikrodenetleyicilerinde (RAK811 vb.) flash belleğin harici programlayıcılar tarafından okunmasını/yazılmasını engelleyen güvenlik kilidi. Meshtastic yüklemeden önce STM32CubeProgrammer ile Option Bytes üzerinden RDP Level 0'a çekilerek kaldırılır (tüm belleği otomatik siler).

### 🔹 LoRa Anten Temelleri ve Seçim Kriterleri (LoRa Antenna Fundamentals)
LoRa düğümlerinin menzilini, sinyal verimliliğini ve telsiz ömrünü belirleyen ilkeler: 50 Ohm empedans uyumu, düşük VSWR (< 2.0), çalışma frekansına (868/915 MHz) tam rezonans ve kaliteli mekanik yapı. Kutudan çıkan ucuz stok antenlerin frekans sapmalarına karşı dikkatli olunmalıdır.

### 🔹 Anten Işıma Deseni ve Kazanç (Radiation Pattern & dBi)
Çok yönlü antenlerin enerjiyi küre yerine ufka doğru yassı bir çörek (donut) deseni şeklinde odaklaması. El cihazlarında geniş küresel 0-2 dBi kazanç avantaj sağlarken; baz istasyonlarında dengeli 5.8 dBi kullanılır. Aşırı yüksek kazanç (>8 dBi) tepe istasyonlarında alt vadideki düğümleri ıskalayarak kör nokta yaratabilir.

### 🔹 RF Konnektör Standartları (SMA, RP-SMA, U.FL / IPEX)
Standart SMA (erkekte pim, dişide delik) ile Wi-Fi'dan kalma RP-SMA (ters polarite) arasındaki fark. Standart gövdeye RP-SMA takıldığında merkez iletkenler temas etmez; bu da açık devreye ve telsizin anında yanmasına yol açar. Kart üstü narin IPEX/U.FL soketlerinin ömrü 30-50 takma-çıkarma döngüsüdür.

### 🔹 Anten Testi ve NanoVNA Vektör Ağ Analizörü (Antenna Testing)
Antenlerin rezonans frekansını ve VSWR değerini doğrulamak için kullanılan taşınabilir cihaz. SOLT kalibrasyonu yapılarak S11 geri dönüş kaybı dip noktasının hedeflenen frekansta (868/915 MHz) -15 dB altında ve VSWR'nin < 1.5 olması hedeflenir.

### 🔹 Meshtastic Topluluk Anten Test Raporları (Antenna Reports)
Meshtastic topluluğunun piyasadaki hazır antenleri NanoVNA ile tarayarak SWR sweep grafiklerini ve model karşılaştırmalarını paylaştığı açık kaynak test arşivi (`github.com/meshtastic/antenna-reports`).

### 🔹 Koaksiyel Kablo Zayıflaması ve Hat Seçimi (RG58 vs LMR-400)
868/915 MHz UHF frekanslarında koaksiyel iletim hattı kayıpları. Ucuz RG-58 kablo 10 metrede 4.5-5.0 dB kayıp oluşturarak gücün %70'ini kabloda eritir; uzun hatlarda düşük kayıplı LMR-240 veya LMR-400 kullanılmalıdır. En iyi çözüm, düğümü antenin hemen yanına direğe monte etmektir.

### 🔹 Antensiz Gönderme Hasarı ve Yayını Kapatma Güvenliği (`lora.tx_enabled false`)
Anten takılı olmadan telsizin yayına (TX) geçmesi durumunda sonsuz VSWR nedeniyle RF enerjisinin geri yansıyarak SX1262 dahili güç yükselticisini (PA) kalıcı olarak yakması riski. Test ve anten değişimlerinde CLI'dan `meshtastic --set lora.tx_enabled false` ile yayın durdurulmalıdır.

### 🔹 RF Yayılım ve Kapsama Tahmin Yazılımları (Propagation Tools)
Dağ zirveleri ve çatılara kurulacak rölelerin kapsama haritalarını, Fresnel bölgesi engellerini ve radyo ufkunu simüle eden Longley-Rice ve DEM tabanlı araçlar: TowerCoverage, Radio Mobile Online ve HeyWhat'sThat.

### 🔹 Kendin-Yap (DIY) Çeyrek Dalga Zemin Düzlemi Anteni (1/4 Wave Ground Plane)
Pirinç/bakır kaynak telleriyle SMA konnektörüne yapılan ev yapımı monopol anten. Dikey çeyrek dalga eleman (868 MHz için ~8.2 cm, 915 MHz için ~7.8 cm) ve 45° aşağı eğimli 4 radyal tel ile tam 50 Ohm empedans ve 1.1-1.2 VSWR sağlar.

### 🔹 Koaksiyel Yıldırım ve Statik Aşırı Gerilim Koruyucusu (Lightning Arrestor)
Dış mekan anten direklerinden gelen statik yükleri ve yıldırım endüksiyon darbelerini dahili Gaz Deşarj Tüpü (GDT) ile kalın bakır topraklama hattına deşarj eden 50 Ohm RF koruma bloğu.

### 🔹 Koliner Eşeksenli Anten (Collinear High-Gain Omni)
Çatı yönlendiricileri ve dağ tepesi rölelerinde 360 derece eşyönlü yatay kapsama sağlamak üzere fazlı elemanların üst üste dizilmesiyle üretilen yüksek kazançlı (5.8 - 8.5 dBi) fiberglas baz istasyonu anteni.

### 🔹 Yagi-Uda Yönlü Anten (Noktadan Noktaya Omurga)
Radyo dalgalarını dar bir açıya odaklayarak iki uzak dağ zirvesi veya şehirler arası sabit omurga (backbone) linki kurmak için kullanılan yüksek kazançlı (10–16 dBi) yönlü anten.

### 🔹 Yansıtıcı Zemin Düzlemi (Ground Plane ve Radyal Teller)
Monopol (çeyrek dalga) antenlerin 50 ohm karakteristik empedans uyumuna ulaşması ve VSWR değerini 1.1-1.2 seviyesine düşürmesi için anten tabanının altına yerleştirilen metal plaka veya 45° eğimli 3-4 adet radyal tel.

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
| **ROUTER_LATE** | Gecikmeli Altyapı Rölesi | Çekişme penceresinin sonuna kadar bekler; paket yerel istemcilerce tekrarlanmazsa devreye girip güçlü çıkışıyla uzak mesafelere aktarır. |
| **CLIENT_BASE** | Sabit Üs / Ev İstasyonu | Ev veya karargah cihazı; favorilere eklenmiş el telsizlerinin paketlerini bastırma (suppression) kurallarını esneterek sadakatle yineler. |

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

### 🔹 AES-CTR Şifreleme Modu ve Nonce Mimarisi
Meshtastic'in telsiz paketlerinin yükünü (payload) şifrelemek için kullandığı simetrik mod (AES-128/256-CTR). Dolgu baytı (padding) gerektirmez; açık metinle aynı uzunlukta şifreli metin üreterek hava süresinden tasarruf sağlar. 128-bit Nonce değeri, Packet ID ve Gönderen Düğüm Kimliği birleştirilerek tekil hale getirilir.

### 🔹 Paket Başlığı Görünürlüğü ve Kriptografik Kısıtlar (Traffic Analysis)
Yönlendirici rölelerin şifreyi çözmeden paket aktarabilmesi için `From`, `To`, `Packet ID`, `Channel Hash` ve `Hop Limit` meta verileri havada şifresiz dolaşır. Mesaj içeriği çözülemez ancak dinleyiciler kimin konuştuğuna dair trafik analizi yapabilir.

### 🔹 Sıfır Bilgili Düğüm İletimi (Zero-Knowledge Relaying)
Ara rölelerin ilettikleri paketlerin şifre anahtarına sahip olmadan ve içeriğini bilmeden paketi güvenle sonraki hedefe aktarması prensibi. Yabancı düğümler bile özel mesajların içeriğini görmeden menzili genişletir.

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

### 🔹 Position Precision (Konum Hassasiyeti ve Maskeleme)
Ev ve kişisel güvenlik için GPS koordinatlarının son basamaklarını kırparak haritada kesin ev adresi yerine yaklaşık bir mahalle bölgesi yayınlayan gizlilik özelliği (`position_precision`).

### 🔹 Fixed Position (Sabit Konum Modu)
Üzerinde GPS alıcısı bulunmayan sabit tepe yönlendiricilerine ve ev istasyonlarına manuel koordinat tanımlanmasını sağlayan mod (`fixed_position`). Uyduları aramayarak enerji tasarrufu sağlar ve haritada doğru noktada görünür.

### 🔹 Eşlikçi Uygulamalar ve İstemci Ekosistemi (Companion Apps & Clients)
Meshtastic donanımını kontrol etmek, mesajlaşıp harita görüntülemek ve ayarları yönetmek için Bluetooth, Wi-Fi veya USB üzerinden bağlanan resmi istemciler (Android, iOS/iPadOS, Meshtastic Web, Python CLI ve meshtasticd Linux servisi). Telsiz cihazıyla Google Protobuf formatında konuşur.

### 📱 Meshtastic Android İstemci Mimarisi (github.com/meshtastic/Meshtastic-Android)
- **Meshtastic Android Resmi İstemcisi (`meshtastic-android-app`):** Kotlin Multiplatform (KMP) ve Jetpack Compose ile inşa edilmiş; BLE, USB-OTG ve TCP/Wi-Fi üzerinden telsize bağlanarak mesajlaşma, düğüm listesi, SNR/RSSI geçmiş grafikleri ve kanal yönetimi sağlayan açık kaynaklı mobil uygulama.
- **`MeshService` Ön Plan Servis Orkestrasyonu (`meshservice-foreground`):** Ekran kapalıyken veya telefon derin Doze uykusundayken telsizle veri akışını kesintisiz canlı tutan, kalıcı durum çubuğu bildirimli (`sticky notification`) Android Foreground Service.
- **Google Play vs F-Droid FOSS Varyantları (`android-build-flavors-google-fdroid`):** Google Maps ve Play servislerini kullanan `google` yapısı ile MapLibre motorlu, tamamen izleyicisiz ve sıfır kapalı kaynak kodlu `fdroid` sürümünün modüler Gradle ayrımı.
- **Android USB OTG Doğrudan Seri Bağlantı (`android-usb-serial-otg`):** `usb-serial-for-android` altyapısıyla CP210x, CH340 ve CDC-ACM yongalarına USB kablosuyla doğrudan bağlanarak Bluetooth parazitsiz ve sıfır gecikmeli taktik tablet/araç istasyonu kurma imkanı.
- **MapLibre Çevrimdışı Vektör Harita Motoru (`android-maplibre-offline-maps`):** İnternet ve hücresel kapsama bulunmayan arazide `.mbtiles` vektör kiremitleriyle tam çevrimdışı topografya, yön pusulası ve anlık GPS konum takibi.
- **Dahili ATAK / CivTAK CoT Sunucusu (`android-atak-cot-integration`):** Yerel `127.0.0.1:8089` portunda çalışan mTLS TAK sunucusu sayesinde harici bir forwarder eklentisine gerek kalmadan ATAK/CivTAK uygulamalarıyla doğrudan Cursor-on-Target (CoT) veri köprüsü.
- **Jetpack Glance Canlı Ağ Widget'ları (`android-jetpack-glance-widgets`):** Uygulamayı açmadan telefonun ana ekranından canlı aktif düğüm sayısını, kanal doluluğunu ve hedeflenen dost düğümün batarya/mesafesini gösteren `LocalStatsWidget` ve `NodeTrackerWidget`.
- **Otomatik Ağ Keşif Modülü (`android-local-mesh-discovery`):** Bölgedeki aktif mesh ağlarını ve komşuluk ilişkilerini tespit etmek için telsizi LoRa modem preset'leri ve beacon yuvaları arasında sırayla taratan `:feature:discovery` bileşeni.
- **Kritik Bildirimler ve DND Baypas (`android-critical-alerts-dnd`):** Android Bildirim Kanalları üzerinden acil SOS ve afet çağrılarının sistemin "Rahatsız Etmeyin" (Do Not Disturb) modunu delerek sesli/titreşimli uyarı vermesini sağlayan yüksek öncelikli uyarı mekanizması.
- **Kable BLE Taşıma Katmanı (`android-ble-transport-kable`):** Kotlin Multiplatform reaktif coroutine altyapısıyla çalışan, ToRadio/FromRadio karakteristiklerini dinleyen ve dinamik MTU müzakeresiyle Bluetooth bağlantı kopmalarını önleyen modern BLE sürücüsü.

### 🍏 Meshtastic Apple Çoklu Platform Mimarisi (meshtastic.org/docs/software/apple)
- **Meshtastic Apple Çoklu Platform İstemcisi (`meshtastic-apple-app`):** iPhone, iPad, Mac, Apple Watch ve Apple Vision Pro için yerel Swift ve SwiftUI ile geliştirilmiş; BLE, TCP/Wi-Fi ve Seri port destekli resmi Apple ekosistemi istemcisi.
- **Live Activities ve Dynamic Island Entegrasyonu (`apple-live-activities-dynamic-island`):** ActivityKit ile iPhone kilit ekranında ve Dynamic Island üzerinde canlı telsiz bataryası, aktif düğüm sayısı veya seçilen bir cihazın mesafesi/SNR değerini anlık izleme.
- **watchOS Eşlikçi Uygulaması ve "Foxhunt" Pusulası (`apple-watchos-foxhunt`):** Apple Watch üzerinden iPhone ile senkronize çalışan ve ~800 metre içindeki kayıp veya dost düğümlere doğru yön oku ve mesafe çizen "Foxhunt" radyo yön bulma pusulası.
- **Apple CarPlay ve Siri ile Sürüş Odaklı Mesajlaşma (`apple-carplay-integration`):** Otomobil konsolunda CPTemplate arayüzü ve Siri Intent'leri (`INSendMessageIntent`) ile sürüş güvenliğini bozmadan eller serbest sesli telsiz mesajlaşması.
- **visionOS Uzamsal Deneyim ve 3D Donanım Vitrini (`apple-visionos-spatial`):** Apple Vision Pro'da RealityKit ile telsiz kartlarının 1:1 ölçekli 3D modellerini fiziksel odada masalara koyma, sanal duvar sunucu rafı ve 3D topografya haritası.
- **Bluetooth Üzerinden Havadan Firmware Güncelleme (`apple-ble-ota-firmware-update`):** Bilgisayara veya kabloya ihtiyaç duymadan GitHub releases üzerinden doğrudan iPhone/iPad BLE bağlantısıyla telsiz bellenimini kablosuz güncelleme (OTA DFU).
- **Paket Kimlik Doğrulama Seviyeleri (`packet-authentication-protection-levels`):** XEdDSA dijital imzalarıyla gelen paketleri doğrularken `Compatible` (eski uyumlu), `Balanced` (önerilen dengeli) ve `Strict` (sadece imzalı/şifreli paketleri kabul eden katı mod) güvenlik politikaları.
- **Meshtastic Kilitlenme Modu (`meshtastic-lockdown-mode`):** Cihazın fiziken ele geçirilmesi riskine karşı dahili NVS depolamayı şifreli kilitleyen ve yalnızca yetkili kullanıcının Bluetooth parolasını girmesiyle açılan `MESHTASTIC_LOCKDOWN` güvenlik seviyesi.
- **CoreBluetooth Arka Plan Durum Restorasyonu (`apple-corebluetooth-background`):** iOS uygulamayı bellekten temizlese dahi gelen telsiz paketinde sistemi arka planda uyandırıp paketi işleyen `bluetooth-central` ve `State Restoration` mimarisi.
- **Apple MapKit Çevrimdışı Rota ve İşaretçi Yönetimi (`apple-mapkit-offline-waypoints`):** iOS 17 yerel çevrimdışı harita indirme desteği ile internet olmadan dost düğüm GPS pinleri, irtifa, rota çizgileri ve telsizden gönderilen acil Waypoint işaretçilerini haritalandırma.

### 🌐 Meshtastic Web İstemcisi ve Tarayıcı Mimarisi (meshtastic.org/docs/software/web-client)
- **Meshtastic Resmi Web İstemcisi (`meshtastic-web-client`):** `client.meshtastic.org` üzerinden veya yerel ağda çalışan; TypeScript, React ve Preact Signals ile inşa edilmiş, masaüstü ve mobilde sürücüsüz tarayıcı tabanlı yönetim arayüzü.
- **Web Serial API Doğrudan USB İletişimi (`web-serial-transport`):** Chromium tarayıcılarının (Chrome, Edge, Brave) harici yazılıma ihtiyaç duymadan USB kablosuyla bağlı telsizle 115200 baud hızında çift yönlü Protobuf haberleşmesi.
- **Web Bluetooth API Kablosuz BLE Bağlantısı (`web-bluetooth-transport`):** Masaüstü veya Android cihazlarda tarayıcı içinden kablosuz Bluetooth GATT servislerini tarayarak ToRadio/FromRadio üzerinden telsize bağlanma.
- **HTTP ve WebSocket Yerel Ağ Erişimi (`web-client-http-transport`):** Wi-Fi destekli ESP32 düğümlerinin IP adresine yerel ağdan REST API ve WebSocket (`/ws`) protokolleriyle bağlanarak telsizi uzaktan yönetme.
- **HTTPS Karışık İçerik ve Self-Signed Sertifika Onayı (`https-self-signed-bypass`):** `client.meshtastic.org` HTTPS bağlantısının yerel ESP32'nin kendinden imzalı SSL sertifikasını tarayıcı güvenlik uyarısını onaylayarak aşması prosedürü.
- **Modüler TypeScript Kütüphanesi (`meshtastic-typescript-sdk`):** `@meshtastic/sdk` monorepo paketi; `@preact/signals-core` reaktif durum yönetimi, Buf Protobuf stubs ve modüler etki alanı dilimleri (`device`, `chat`, `nodes`, `channels`).
- **Cihaz Üstü Bağımsız Web Sunucusu (`on-device-standalone-web`):** ESP32'nin dahili LittleFS/SPIFFS flaş belleğinde saklanan, internete veya harici sunucuya çıkmadan telsizin kendi IP'sinden açılan acil durum web arayüzü.
- **İlerici Web Uygulaması (PWA) Kurulumu (`web-client-pwa`):** Service Worker önbelleklemesiyle masaüstüne veya ana ekrana yüklenebilen, internet kesilse dahi USB/BLE ile kesintisiz çalışan çevrimdışı web uygulaması.
- **İnteraktif Traceroute Görselleştiricisi (`web-traceroute-visualizer`):** Rota keşif paketlerinin sekmelerini (hops), ara rölelerin SNR değerlerini ve rota gecikmelerini şema üzerinde görselleştiren ağ analiz aracı.
- **Telemetri ve Çevre Grafikleri Paneli (`web-telemetry-dashboard`):** Batarya voltajı, sıcaklık, nem, barometrik basınç ve kanal doluluk oranını gerçek zamanlı zaman serisi grafiklerine döken gösterge tablosu.

### 📦 Meshtastic Web Monorepo ve TypeScript SDK Mimarisi (github.com/meshtastic/web)
- **Meshtastic Web PNPM Monorepo Mimarisi (`meshtastic-web-monorepo`):** `pnpm workspaces`, Oxlint ve Turborepo ile yönetilen; `apps/web` arayüzü, çoklu taşıma paketleri ve TypeScript SDK'sını tek çatı altında toplayan monorepo mimarisi.
- **`@meshtastic/sdk-react` ve MeshProvider (`sdk-react-meshprovider`):** React bileşen hiyerarşisine telsiz durumunu enjekte eden `<MeshProvider>` ve `useMeshClient()`, `useNodes()`, `useChannels()` özel kancaları (hooks).
- **Buf ile TypeScript Protobuf Kod Üretimi (`buf-protobuf-ts-generator`):** `buf generate` CLI aracıyla `meshtastic/protobufs` şemalarından esm/cjs uyumlu, tip güvenli ikili kodlayıcı/çözücü kütüphanesi derleme.
- **`@meshtastic/ui` Tasarım Sistemi (`packages-ui-radix-tailwind`):** Radix UI WAI-ARIA erişilebilir ilkel bileşenleri ve Tailwind CSS ile geliştirilmiş ortak tema ve görsel bileşen kütüphanesi.
- **Node.js TCP Taşıma Katmanı (`transport-node-tcp`):** Sunucu tarafı Node.js, Raspberry Pi ve Docker botlarının telsize ağ üzerinden TCP soketiyle (Port 4403) bağlanmasını sağlayan sürücü.
- **Node.js Donanımsal Seri Port Sürücüsü (`transport-node-serial`):** `node-serialport` yerel C++ eklentisiyle Linux/macOS/Windows sunucularda USB-UART portundan (`/dev/ttyUSB0`) doğrudan paket alışverişi.
- **Deno Çalışma Zamanı Sürücüsü (`transport-deno-runtime`):** Modern Deno çalışma zamanında `Deno.connect()` yerel TCP soket API'siyle sıfır harici paket bağımlılığıyla çalışan hafif taşıma katmanı.
- **Bellek İçi Sahte Telsiz ve CI Test Sürücüsü (`transport-mock-testing`):** Fiziksel donanım olmadan Vitest/Playwright birim testleri ve CI/CD hatlarında sahte telsiz simüle eden mock sürücüsü.
- **MeshClient Orkestratörü ve Preact Signals (`meshclient-orchestrator`):** Taşıma katmanlarını soyutlayan, Protobuf paketlerini çözen ve `@preact/signals-core` ile ince taneli reaktif durum bildirimleri yayan ana orkestratör.
- **SDK Alan Odaklı Tasarım Dilimleri (`ddd-feature-slices`):** SDK'nın `device`, `chat`, `nodes`, `channels`, `config`, `telemetry`, `traceroute` ve `files` olmak üzere bağımsız DDD mantıksal dilimlerine ayrılması.

### 🐍 Meshtastic Python Komut Satırı Arayüzü (CLI) (meshtastic.org/docs/software/python/cli)
- **Meshtastic Python CLI (`meshtastic-python-cli`):** Telsizleri terminal üzerinden yönetmek, paket akışını dinlemek ve ayarları otomatize etmek için kullanılan resmi `meshtastic` Python komut satırı aracı.
- **YAML Yapılandırma Dışa/İçe Aktarımı (`python-cli-export-config`):** `--export-config > backup.yaml` ile tam cihaz yedeği alma ve `--configure backup.yaml` ile onlarca karta saniyeler içinde toplu provizyon uygulama.
- **CLI ile Kanal Yönetimi (`python-cli-channel-management`):** `--ch-add`, `--ch-del`, `--ch-set` ve `--ch-index` parametreleriyle 8 kanala kadar bağımsız kanal adı, yetkileri ve 256-bit AES anahtarlarını yapılandırma.
- **Düğüm Ayarları ve Parametre Yapılandırması (`python-cli-device-settings`):** `--set-owner` ile telsiz çağrı adı verme ve `--set <modül>.<özellik> <değer>` hiyerarşik sözdizimi ile doğrudan Protobuf NVS parametrelerini değiştirme.
- **Terminal ASCII QR Kodu (`python-cli-terminal-qr`):** `--qr` ve `--qr-all` komutlarıyla terminal ekranında taranabilir siyah-beyaz ASCII QR blokları ve kanal bağlantıları oluşturma.
- **Linux IP Ağ Tünelleme Protokolü (`python-cli-ip-tunnel`):** Linux çekirdeğinin TUN sanal ağ sürücüsüyle (`--tunnel --subnet 10.10.0.0/24`) LoRa telsiz ağı üzerinden iki bilgisayar arasında standart IP/SSH/Ping haberleşmesi kurma.
- **Uzaktan Donanım GPIO Kontrolü (`python-cli-gpio-control`):** `--gpio-wrb` ve `--gpio-rd` komutlarıyla kilometrelerce uzaktaki dağ rölesinin GPIO pinlerini tetikleme ve sensör durumlarını telsiz üzerinden okuma.
- **CLI Taşıma Bağlantı Yolları (`python-cli-connection-routes`):** Seri port (`--port`), yerel ağ TCP soketi (`--host`) ve kablosuz Bluetooth BLE (`--ble` / `--ble-scan`) ile telsize bağlanma esnekliği.
- **İzole Python Ortam Kurulumu (`python-cli-pipx-installation`):** Modern Linux sistemlerinde PEP 668 paket yöneticisi kısıtlamalarını aşmak için `pipx install "meshtastic[cli]"` ile izole ve kararlı sanal çevre kurulumu.
- **Cihaz Bakım ve Sıfırlama Komutları (`python-cli-maintenance-reset`):** `--reboot` ile yeniden başlatma, `--reset-nodedb` ile şişen düğüm hafızasını temizleme ve `--factory-reset` ile tam NVS fabrika sıfırlaması yapma.

### 🛠️ Meshtastic Python CLI Kurulumu ve Sistem Yapılandırması (meshtastic.org/docs/software/python/cli/installation)
- **Meshtastic CLI Ekstra Bağımlılıkları (`meshtastic-cli-extra-dependencies`):** Yalın kütüphaneye ek olarak terminal tabloları (`tabulate`), QR kod (`pyqrcode`) ve YAML desteği için paketin `meshtastic[cli]` extras bayrağıyla kurulması şartı.
- **ZSH Köşeli Parantez Kaçırma Kuralı (`zsh-bracket-globbing-escape`):** macOS ve Linux ZSH kabuğunda `zsh: no matches found: meshtastic[cli]` hatasını önlemek için paket adının tırnak içine (`"meshtastic[cli]"`) alınması gerekliliği.
- **Linux `dialout` Seri Port İzinleri (`linux-dialout-group-permissions`):** `/dev/ttyUSB0` portlarına sudo olmadan doğrudan erişebilmek için kullanıcının `sudo usermod -a -G dialout $USER` ile yetkilendirilmesi.
- **ModemManager Seri Port Çakışması ve udev Çözümü (`linux-modemmanager-serial-conflict`):** ModemManager servisinin Meshtastic telsizine AT komutları basıp portu kilitlemesini `/etc/udev/rules.d/` içine `ENV{ID_MM_DEVICE_IGNORE}="1"` yazarak engelleme.
- **Windows Python PATH Ortam Değişkeni (`windows-python-path-configuration`):** Windows kurulumunda 'Add Python to PATH' unutulduğunda terminalin `meshtastic` komutunu tanımaması ve `%APPDATA%\Python\Scripts` yolunun eklenmesi.
- **`pipx ensurepath` Otomatik Profil Entegrasyonu (`pipx-ensurepath`):** `pipx` ile kurulan ikili dosyaların `~/.local/bin` yolunu kabuk profillerine (`~/.bashrc`, `~/.zshrc`) otomatik ekleyerek komutu sistem genelinde erişilebilir kılma.
- **Python Sanal Ortam İzolasyonu (`python-venv-isolation`):** Sistem Python paketlerini bozmadan `python3 -m venv meshtastic-env` ile izole bir klasörde bağımsız CLI çalıştırma standardı.
- **USB-UART Seri Köprü Sürücüleri (`serial-bridge-chip-drivers`):** ESP32 tabanlı kartların bilgisayar tarafından COM portu olarak tanınabilmesi için gerekli Silicon Labs CP210x ve WCH CH340/CH9102 VCP sürücüleri.
- **Docker Konteyner ile Meshtastic CLI (`docker-meshtastic-cli`):** Ana makineye hiçbir bağımlılık kurmadan `--device=/dev/ttyUSB0` ile seri portu bağlayıp `meshtastic/meshtastic` resmi Docker imajından komut koşturma.
- **CLI Kurulum Doğrulama ve Teşhis (`cli-installation-troubleshooting`):** Kurulum sağlığını `meshtastic --version`, yürütülebilir yolunu `which meshtastic` / `where meshtastic` ve aktif portları `meshtastic --port-list` ile test etme adımları.

### 💻 Meshtastic Python CLI İleri Komutları ve Kullanım Pratikleri (meshtastic.org/docs/software/python/cli/usage)
- **Canlı Paket Dinleme ve Sniffer Modu (`python-cli-listen-mode`):** `meshtastic --listen` ile terminali sürekli açık tutarak havadaki telsiz paketlerini, SNR/RSSI değerlerini ve ham Protobuf yüklerini anlık dökme.
- **Ham Seri Log Terminali Modu (`python-cli-noproto-serial`):** `meshtastic --noproto` ile Protobuf katmanını kapatıp cihazı saf seri konsola çevirerek mikrodenetleyicinin bootloader ve FreeRTOS panik loglarını izleme.
- **Hedef Düğüm Yönlendirmesi ve Uzak Yönetim (`python-cli-dest-targeting`):** `--dest '!node_id'` ile yayın yerine belirli bir hedefe doğrudan mesaj atma, telemetri isteme ve uzak rölenin ayarlarını uzaktan değiştirme.
- **Sabit GPS Koordinatları Atama (`python-cli-fixed-position`):** `--setlat`, `--setlon`, `--setalt` ve `fixed_position true` ile GPS donanımı olmayan baz istasyonlarına milimetrik statik konum tanımlama.
- **Hazır Mesaj Modülü Yapılandırması (`python-cli-canned-messages`):** `--set-canned-message` ile T-Deck veya Cardputer ekranlarında klavyesiz seçilip fırlatılacak hızlı yanıt dizgilerini (`"Yardım|Yoldayım|Tamam"`) yükleme.
- **RTTTL Zil Sesi ve Buzzer Melodisi Yükleme (`python-cli-rtttl-ringtone`):** `--set-ringtone` ile piezo buzzer donanımlı cihazlara gelen acil bildirimler için Nokia RTTTL formatında melodiler kodlama.
- **CLI ile Rota Keşfi ve Sekme Analizi (`python-cli-cli-traceroute`):** `meshtastic --traceroute '!node_id'` ile ara röleleri ve her bir sekmenin SNR sinyal kalitesini terminalde çift yönlü listeleme.
- **Tekil Yapılandırma Sorgulama (`python-cli-get-preferences`):** `--get owner` veya `--get lora.region` ile ekranı kirletmeden tek parametre okuma ve `--get all` ile tüm ayar ağacını listeleme.
- **Gerçek Zaman Saati (RTC) Zaman Eşitleme (`python-cli-rtc-time-sync`):** `meshtastic --set-time` ile GPS görmeyen ve Bluetooth bağlı olmayan kule istasyonlarının donanımsal RTC saatini bilgisayar saatiyle senkronize etme.
- **Teslimat Onayı ve ACK Yanıtı Bekleme (`python-cli-expect-ack`):** `--ack` / `--expect-ack` bayrağı ile hedef cihazdan teslimat onay paketi gelene kadar komut satırını bekleterek otomasyon güvenliğini sağlama.

### 🐧 mPWRD-OS & Meshtastic Linux Dağıtımı (meshtastic.org/docs/software/mpwrd-os)
- **mPWRD-OS İşletim Sistemi (`mpwrd-os`):** Tek kartlı bilgisayarlar (SBC) üzerinde Meshtastic düğümü çalıştırmak için Armbian ve Debian 13 (Trixie) üzerine inşa edilmiş, `meshtasticd`, Python CLI, contact TUI ve mpwrd-menu araçlarını önceden kurulu barındıran açık kaynaklı Linux dağıtımı.
- **meshtasticd Linux Arka Plan Servisi (`meshtasticd-linux-daemon`):** C++ çekirdeğini Portduino katmanıyla Linux donanım çağrılarına (spidev, libgpiod) çeviren, Raspberry Pi ve Luckfox üzerindeki SPI/GPIO LoRa şapkalarını doğrudan süren ve TCP soketi açan yerel systemd arka plan servisi.
- **mpwrd-menu Yönetim Konsolu (`mpwrd-menu-utility`):** SSH veya yerel konsoldan `mpwrd-menu` komutuyla açılan; donanım katmanı şablonu seçimi, servis durumları, ağ yapılandırması ve sistem güncellemelerini yöneten interaktif TUI aracı.
- **contact TUI Mesajlaşma İstemcisi (`contact-tui-client`):** Başsız Linux sunucularda veya düşük bant genişlikli SSH oturumlarında harici bir telefon veya web tarayıcısı olmadan doğrudan uçbirimden mesajlaşmayı ve düğüm yönetimini sağlayan hafif ncurses tabanlı arayüz.
- **Nymea BLE Ağ Hazırlama (`nymea-ble-provisioning`):** Ekranı ve Ethernet kablosu olmayan Raspberry Pi cihazlarının `nymea-networkmanager` üzerinden Bluetooth Low Energy ile Meshtastic Flasher veya mobil uygulamalarla kablosuz Wi-Fi ağına bağlanmasını sağlayan hazırlama servisi.
- **Armbian Web Kurulum Bağlantı Noktası (`armbian-web-setup-hotspot`):** Bluetooth bulunmayan Luckfox ve Rockchip kartlarının ilk açılışta `armbiansetup` adında geçici Wi-Fi bağlantı noktası oluşturarak `http://10.42.0.1:8080` adresinden ev Wi-Fi ağına bağlanmasını sağlayan web kurulum sihirbazı.
- **SBC LoRa HAT Yapılandırması (`sbc-lora-hat-configuration`):** `/etc/meshtasticd/config.yaml` dosyasında SPI veri yolu (`spidev0.0`), CS, IRQ, Busy, Reset GPIO pinleri, TCXO voltajı ve RF anahtarının (`DIO2_AS_RF_SWITCH`) tanımlandığı donanım eşleme protokolü.
- **meshtasticd Donanım Şablonları ve Katman Sistemi (`meshtasticd-config-overlays`):** `/etc/meshtasticd/available.d/` altındaki hazır HAT profillerinin (Waveshare, EByte, LilyGO vb.) `config.d/` dizinine sembolik bağ (symlink) ile eklenmesini sağlayan modüler yapılandırma mimarisi.
- **mPWRD-OS Desteklenen SBC Donanım Matrisi (`mpwrd-supported-sbc-platforms`):** Raspberry Pi (Pi 4, 5, Zero 2 W, CM4/CM5), Rockchip & Luckfox serisi (RV1106, RV1103, Lyra Plus, Lyra Ultra W, Pico), EByte ECB41-PGE, ForLinx OK3506 ve x86_64 UEFI sistemleri içeren resmi donanım listesi.
- **Rockchip Maskrom Modu ve rkdevtool Yazma Prosedürü (`rockchip-maskrom-rkdevtool`):** Luckfox Lyra ve Pico kartlarında Boot pinini GND'ye çekerek girilen Maskrom modunda, Windows 'rkdevtool' veya Linux 'upgrade_tool' ile dahili SPI NAND/NOR flaşı temizleyip mPWRD-OS imajı yükleme protokolü.

### 🛠️ mPWRD-OS Desteklenen Tek Kartlı Bilgisayarlar (meshtastic.org/docs/software/mpwrd-os/board-support)
- **Rockchip RK3506 İşlemci Mimarisi (`rockchip-rk3506-soc`):** 3x ARM Cortex-A7 (1.2 GHz) ve Cortex-M0 MCU barındıran; üçlü Ethernet, CAN-FD ve 1W altı rölanti tüketimiyle sabit baz istasyonları ve çatı röleleri için optimize edilmiş düşük güçlü endüstriyel uygulama işlemcisi.
- **Luckfox Lyra SBC Ailesi (`luckfox-lyra-series`):** RK3506G/RK3506B işlemcili Lyra Plus (Pico pin uyumlu & Ethernet), Lyra Ultra W (çift Ethernet, Wi-Fi & dahili eMMC) ve Lyra Zero W (ultra kompakt Pi Zero boyutlu) açık kaynaklı donanım serisi.
- **EByte ECB41-PGE Taşıyıcı Kartı (`ebyte-ecb41-pge`):** RK3506G yongalı, PoE ve endüstriyel klemens bağlantılı LoRa ağ geçidi anakartı; dahili NAND flaş silinerek SD karttan başlatılır.
- **ForLinx OK3506-S12 Endüstriyel SBC (`forlinx-ok3506-s12`):** -40°C ile +85°C sıcaklık dayanımlı Rockchip RK3506J işlemcisiyle aşırı iklim koşullarındaki dağ zirvesi telsiz kuleleri için tasarlanmış yüksek güvenilirlikli kart.
- **Luckfox Pico Modülleri (`luckfox-pico-rv1106-rv1103`):** RV1106G (Pico Max) ve RV1103G (Pico Mini) mikro yongalarıyla çalışan, Cortex-A7 + RISC-V + NPU mimarili, madeni para büyüklüğünde hızlı önyüklemeli gömülü Linux modülleri.
- **OnionIOT Omega4 SBC Desteği (`onioniot-omega4`):** Rockchip RV1103B mikro işlemcisiyle mPWRD-OS yol haritasında planlanan ultra kompakt ve modüler tak-çalıştır Linux IoT kartı.
- **Dahili Flaş Temizleme Prosedürü (`onboard-flash-erase-procedure`):** Fabrika çıkışlı Buildroot yazılımının mPWRD-OS önyüklemesini engellemesini önlemek için Maskrom modunda rkdevtool veya Web Flasher ile dahili SPI NAND/NOR flaşın sıfırlanması ('Erase flash').
- **Dahili eMMC Belleğe Yazma (`emmc-direct-flashing-mpwrd`):** Luckfox Lyra Ultra W kartında SD kart yerine titreşim ve aşınmaya dayanıklı dahili eMMC çipine Maskrom modu üzerinden doğrudan mPWRD-OS parçalarının yazılması.
- **Waveshare Pico-LoRa-SX1262 Şapkası (`waveshare-pico-lora-hat`):** Luckfox Lyra Plus kartının Pico pin rozetine doğrudan takılan ve mPWRD-OS içinde hazır pin konfigürasyonuyla gelen tak-çalıştır SX1262 LoRa eklenti kartı.
- **BCM2711 ARM64 mPWRD-OS Desteği (`bcm2711-armbian-mpwrd`):** Raspberry Pi 4, 5, Zero 2 W ve CM4/CM5 modellerinde flaş silme gerektirmeden doğrudan SD karta yazılarak Bluetooth BLE (nymea) ile kurulan resmi 64-bit Armbian destek katmanı.

### 🌐 mPWRD-OS İlk Ağ Kurulumu ve Provizyon Yöntemleri (meshtastic.org/docs/software/mpwrd-os/provisioning)
- **Meshtastic Flasher mPWRD-OS Araçları (`flasher-mpwrd-tools`):** Web Bluetooth ve Web Serial ile çalışan; yakındaki Raspberry Pi SBC kartlarını keşfedip kablosuz ağ taraması ve tek tıkla Wi-Fi şifresi enjeksiyonu sağlayan resmi Flasher sekmesi.
- **Armbian Web Yapılandırma Sihirbazı (`armbian-web-config-wizard`):** Luckfox Lyra Ultra/Zero W kartlarında `http://10.42.0.1:8080` adresinde çalışan; Root parolası, Kullanıcı hesabı, Bölgesel dil/zaman, Wi-Fi ağı ve gelişmiş optimizasyonları içeren 5 adımlı kurulum arayüzü.
- **Web Bluetooth ile Kablosuz Kurulum (`web-bluetooth-provisioning-flow`):** `nymea-networkmanager` GATT servisleri üzerinden telefon veya bilgisayar tarayıcısından Wi-Fi SSID ve WPA2/WPA3 parolasını kablosuz iletip anlık IP teyidi alma iş akışı.
- **Geçici Kurulum Erişim Noktası (`temporary-setup-hotspot`):** Wi-Fi bağlantısı olmayan kartların ilk açılışta yaydığı, `armbian1234` şifreli ve `10.42.0.1` yerel yapılandırma ağı sunan, ağa bağlanınca otomatik kapanan `armbiansetup` acil durum AP'si.
- **İlk Açılış Kimlik Doğrulama Politikası (`mpwrd-first-boot-credentials`):** Fabrika çıkışı gelen `root / 1234` varsayılan parolasının ilk konsol/SSH oturumunda Linux PAM katmanı veya web sihirbazı aracılığıyla zorunlu olarak değiştirilmesi kuralı.
- **Standart Kullanıcı ve Sudo Güvenlik Katmanı (`mpwrd-user-account-security`):** Root ile doğrudan çalışmayı önlemek amacıyla `sudo`, `dialout`, `spi` ve `gpio` gruplarına dahil edilen standart sistem kullanıcısı ve SSH güvenlik mimarisi.
- **Bölgesel Dil, Zaman Dilimi & NTP Eşitlemesi (`mpwrd-locale-timezone-sync`):** GPS modülü bulunmayan kule ve çatı düğümlerinde sistem loglarının ve Meshtastic iletim zaman damgalarının doğruluğu için internet üzerinden `systemd-timesyncd` ile atomik saat eşitlemesi.
- **Başsız Düğüm Güvenli Kabuk Erişimi (`sbc-headless-ssh-management`):** Monitörsüz çalışan kule düğümlerine uzaktan güvenli erişim için Ed25519 açık/özel anahtarlı SSH kimlik doğrulaması ve parola deneme ataklarına karşı sistem sertleştirme.
- **Ağ Bağlantısı Kurtarma ve Geri Çekilme Modu (`mpwrd-network-fallback-recovery`):** Wi-Fi şifresi değiştiğinde veya bağlantı koptuğunda kartın kilitlenmesini önleyerek otomatik olarak `armbiansetup` AP veya BLE provizyon moduna dönmesini sağlayan acil kurtarma mekanizması.
- **SBC Sabit IP & DHCP Rezervasyonu (`sbc-static-ip-dhcp-assignment`):** `meshtasticd` TCP servisinin (port 4403) ve SSH konsolunun (port 22) yerel ağda daima öngörülebilir bir adreste kalmasını sağlayan router MAC rezervasyonu veya `nmcli` statik IP yapılandırması.

### ⚡ Rockchip Düşük Seviyeli Flaşlama ve Kurtarma (meshtastic.org/docs/software/mpwrd-os/rockchip-flashing)
- **Meshtastic Flasher Rockchip Aracı (`flasher-rockchip-flash-tool`):** WebUSB ile çalışan; Maskrom modundaki Rockchip kartları otomatik tanıyan, USB kimliği ve flaş kapasitesini gösteren, tek tıkla 'Erase Flash' ve doğrudan imaj yazma imkanı sunan tarayıcı aracı.
- **rkdeveloptool Komut Satırı Aracı (`rkdeveloptool-cli`):** Linux/macOS ortamlarında libusb ile çalışan; Maskrom modundaki kartın DDR belleğini başlatma (`db`), dahili flaşı silme (`ef`) ve doğrudan LBA sektörlerine imaj yazma (`wl`) işlemlerini yöneten resmi açık kaynaklı komut satırı programı.
- **Maskrom Modu Donanımsal Tetikleme (`maskrom-mode-hardware-trigger`):** Dahili flaştan hatalı önyüklemeyi engellemek için karttaki BOOT/Maskrom butonuna 5 saniye basılı tutarak USB gücü verme ve işlemciyi donanımsal indirme moduna geçirme prosedürü.
- **Flaş Temizleme Öncesi MicroSD Çıkarma Kuralı (`microsd-removal-precaution`):** Kartın dahili flaşı silinirken yanlış depolama bloğunun sıfırlanmasını veya MBR/GPT tablosu bozulmasını önlemek için microSD kart yuvasının mutlaka boş tutulması zorunluluğu.
- **Sıkıştırılmış İmaj Akış Yazma Desteği (`compressed-image-flashing`):** Web Streams ve DecompressionStream API ile `.img.gz` ve `.img.xz` formatındaki sıkıştırılmış mPWRD-OS imajlarını diske açmadan bellekte anlık çözerek doğrudan karta yazma teknolojisi.
- **Rockchip Depolama Mimarisi (`rockchip-storage-nand-emmc`):** EByte ve Lyra Plus'taki blok silme gerektiren ham SPI NAND yongaları ile Lyra Ultra W'deki dahili aşınma dengelemeli (wear leveling) yönetilen eMMC 5.1 bellekler arasındaki mimari farklar.
- **balenaEtcher MicroSD Yazma Standardı (`balenaetcher-sd-preparation`):** Sıkıştırılmış `.img.xz` imajlarını doğrudan microSD karta sektör düzeyinde yazıp SHA sağlama toplamıyla doğrulayan ve ana sabit diski koruyan güvenli yazma protokolü.
- **Rockchip USB Tanımlama ve Numaralandırma (`rockchip-usb-vid-detection`):** Maskrom modundaki kartların `0x2207` USB Satıcı Kimliği (VID) ve `0x350a` (RK3506) / `0x110a` (RV1106) Ürün Kimlikleri (PID) ile WebUSB veya `lsusb` üzerinden doğrulanması.
- **MiniLoader Başlatma Mimarisi (`rockchip-miniloader-execution`):** İşlemcinin dahili SRAM'ine gönderilerek harici DDR RAM kontrolcüsünü ve yüksek hızlı USB 2.0 arayüzünü devreye sokan ilk aşama önyükleyici ikilisi (`MiniLoaderAll.bin`).
- **Rockchip Sürücü Asistanı ve Bağlantı Teşhisi (`rockchip-driverassistant-troubleshooting`):** Windows'ta Maskrom modunu tanımak için `rockusb.sys` sürücüsü kurulumu; veri hattı olmayan 2 telli şarj kabloları ve USB 3.0 port kararsızlıklarına karşı sorun giderme adımları.

### 🗺️ Meshtastic Saha Planlayıcısı & RF Kapsama Simülasyonu (site.meshtastic.org)
- **Meshtastic Saha Planlayıcısı (`meshtastic-site-planner`):** Gerçek coğrafi yükselti verileriyle LoRa düğümlerinin kapsama alanını, sinyal yayılımını ve bağlantı kalitesini sunucuya ihtiyaç duymadan tarayıcıda simüle eden resmi açık kaynaklı RF planlama platformu (`site.meshtastic.org`).
- **SPLAT! & ITWOM WebAssembly Motoru (`splat-itwom-wasm-engine`):** Tarihi C tabanlı SPLAT! ve Longley-Rice düzensiz arazi yayılım algoritmasını Web Workers ve Wasm ile doğrudan istemci bilgisayarında çalıştıran paralel hesaplama motoru.
- **NASA SRTM Dinamik Yükselti Akışı (`srtm-elevation-tiles-streaming`):** AWS Open Data üzerinden 30 metrelik küresel SRTM topoğrafya kiremitlerini anlık indirip tarayıcı önbelleğinde saklayan dinamik yükselti katmanı.
- **Fresnel Bölgesi Açıklığı & Kırınım (`fresnel-zone-clearance`):** İki düğüm arasındaki 1. Fresnel elipsoidinin en az %60'ının karasal engellerden arındırılmış olmasını doğrulayan ve faz iptali sönümlenmesini önleyen geometrik analiz.
- **Alıcı Duyarlılık Eşiği Modellemesi (`receiver-sensitivity-threshold`):** LongFast (-130 dBm) ve LongSlow (-137 dBm) modem profillerine göre hesaplanan RSSI değerinin kapsama sınırını belirleyen dinamik hassasiyet eşiği.
- **Anten Yerden Yüksekliği Modellemesi (`antenna-height-above-ground`):** Anten direk yüksekliğinin (AGL - Above Ground Level) yerel binaları aşma, Fresnel açıklığını temizleme ve radyo ufkunu geometrik olarak genişletme etkisinin modellenmesi.
- **Renk Kodlu RSSI Isı Haritası (`rssi-heatmap-visualization`):** Simüle edilen sinyal güçlerini güçlü bağlantı (>-110 dBm), orta kalite (-110 ila -125 dBm) ve sınır kapsama (-125 ila -130 dBm) bölgelerine göre renklendiren harita katmanı.
- **Çoklu Düğüm Kapsama Katmanlama (`multi-node-mesh-coverage-stacking`):** Birden fazla röle ve verici sahasını birleştirerek şehir genelindeki kolektif örgü ağ kapsamasını, yedekliliği ve kör noktaları (dead zones) analiz etme yöntemi.
- **Noktadan Noktaya Yükselti Kesit Grafiği (`link-profile-elevation-graph`):** Verici ve alıcı arasındaki karasal yükseltiyi, Dünya küreselliğini ve optik görüş hattını (LOS) 2 boyutlu kesit olarak çizerek engel sırtlarını gösteren grafik.
- **EIRP & Yasal Güç Sınırı Modellemesi (`eirp-effective-radiated-power`):** Simülasyonda TX gücü, anten dBi kazancı ve kablo kaybını birleştirerek Türkiye/AB (868 MHz / 25 mW) veya ABD (915 MHz / 1W) yasal sınırlarına uygun gerçekçi menzil hesaplama.

### 🧪 Meshtasticator Ağ Simülasyonu & Firmware Öykünümü (meshtastic.org/docs/software/meshtasticator)
- **Meshtasticator Ağ Simülatörü Paketi (`meshtasticator`):** Fiziksel donanıma ihtiyaç duymadan onlarca düğümün LoRa telsiz haberleşmesini, paket yönlendirmesini ve protokol ölçeklenebilirliğini test eden resmi açık kaynaklı simülatör suite'i (`github.com/meshtastic/Meshtasticator`).
- **interactiveSim.py Canlı Firmware Öykünücüsü (`interactivesim-py`):** Gerçek Meshtastic C++ Linux yerel firmware ikililerini veya Docker konteynerlerini eşzamanlı çalıştırarak artan yerel TCP soketleri (4403, 4404...) üzerinden sanal telsiz ağı kuran etkileşimli araç.
- **SimPy Ayrık Olay Simülasyon Çekirdeği (`simpy-discrete-event-engine`):** Süreç tabanlı Python SimPy motoru ve `BroadcastPipe` ile firmware çalıştırmadan yüzlerce düğümlük büyük afet ağlarını mikrosaniyeler mertebesinde matematiksel olarak simüle eden `loraMesh.py` çekirdeği.
- **Meshtasticator Ampirik Yol Kaybı Modelleri (`lora-pathloss-models-meshtasticator`):** Simülatörde mesafeye ve çevre tipine göre RF zayıflamasını hesaplayan 7 ampirik model: Log-Distance (0), Okumura-Hata (1-4: küçük şehir, metropol, banliyö, kırsal) ve 3GPP Makro Hücre (5-6).
- **LoRa Paket Çarpışması ve Yakalama Etkisi (`lora-collision-capture-effect`):** Aynı anda iletilen paketlerin havada çakışması ve sinyal gücü farkı >= 6 dB olduğunda güçlü olanın sağlam demodüle edilmesi (Capture Effect) dinamiği.
- **Docker Tabanlı Örgü Ağ Simülasyonu (`dockerized-mesh-simulation`):** Yerel derleme ortamına gerek kalmadan `python3 interactiveSim.py -d` komutuyla resmi `meshtastic/firmware` Docker imajından izole sanal düğüm konteynerleri ayağa kaldırma.
- **TCP Port Telsiz Köprüsü & Sanal Radyo (`tcp-port-proxy-virtual-radio`):** Donanımsal telsiz çipi yerine her sanal düğümün bağımsız bir TCP soketine bağlanıp merkezi Python aracısının coğrafi mesafeye göre paketleri yönlendirdiği sanal telsiz mimarisi.
- **Sanal Radyo Çarpışma Öykünümü Bayrağı (`userprefs-simradio-emulate-collisions`):** `userPrefs.jsonc` içinde `USERPREFS_SIMRADIO_EMULATE_COLLISIONS: true` yapılarak hava süresi örtüşmelerinde kasıtlı CRC/bozuk paket hataları üretilmesini sağlayan firmware bayrağı.
- **Paket Teslim Oranı Analizi (`packet-delivery-ratio-pdr`):** Simülasyon sonucunda kaynaktan çıkan paketlerin hedefe ulaşma yüzdesini ölçen (`PDR = Alınan/Gönderilen * 100`), aşırı sekme ve kanal doluluğu kaynaklı kayıpları tespit eden ana metrik.
- **Meshtasticator Kâhin Topoloji Görünümü (`meshtasticator-oracle-topology-view`):** Tüm ağın üstten tam haritasını, anlık aktif RF bağlantılarını, paket sekme rotalarını ve kuyruklarını tek ekranda izleyip yönlendirme döngülerini yakalayan küresel izleme arayüzü.

### ⏱️ Meshtasticator Ayrık Olay Simülatörü ve loraMesh (meshtastic.org/docs/software/meshtasticator/discrete-event-sim)
- **loraMesh.py Ayrık Olay Betiği (`loramesh-py-script`):** Simülasyonu başlatan, rastgele yerleşim (`python3 loraMesh.py 20`) veya etkileşimli GUI üzerinden düğüm konumları ve hop limitlerini alan ana Python betiği.
- **batchSim.py Otomatik Parametre Taraması (`batchsim-py-sweeps`):** Düğüm sayısını, sekme limitini veya paket periyotlarını otomatik artırarak yüzlerce ardışık Monte Carlo simülasyonu koşturan ve CSV raporları üreten test orkestratörü.
- **nodeConfig.yaml Kalıcı Topoloji (`nodeconfig-yaml-persisted-topology`):** Simülatörde üretilen veya elle yerleştirilen düğüm koordinatları, anten boyları, rolleri ve kazançlarını saklayarak `--from-file` ile deneylerin birebir tekrarlanmasını sağlayan YAML dosyası.
- **plotExample.py Analiz ve Grafikleştirici (`plotexample-py-visualization`):** `/out/report/` dizinindeki simülasyon loglarını okuyarak Matplotlib ile paket teslim oranları (PDR), gecikme ve çarpışmaları gösteren yüksek çözünürlüklü grafikler üreten araç.
- **Simülasyonda Router Rolü Modellemesi (`simulated-router-role`):** Ağdaki düğümlere `isRouter: true` atanarak agresif tekrarlama önceliği verilmesi ve optimum Router/Client oranının belirlenmesi.
- **Sekme Limiti (Hop Limit) Ölçekleme Analizi (`hop-limit-scaling-analysis`):** Hop limitin 1'den 7'ye çıkarılmasının ağda yarattığı paket fırtınasını ve kanal doygunluğunu tespit eden ölçeklenebilirlik analizi.
- **Algoritmik Rastgele Topoloji Üretimi (`random-topology-generation`):** `MINDIST` asgari mesafe kısıtlamasıyla düğümlerin üst üste binmesini engelleyen ve her düğümün bağlı kalmasını garanti eden örgü ağ grafı üretimi.
- **Başsız CI/CD Simülasyon Modu (`headless-ci-simulation-mode`):** `--no-gui`, `--simtime-seconds` ve `--period-seconds` bayraklarıyla GitHub Actions ve sunucularda ekran kartı olmadan otomatik regresyon testi koşturma yeteneği.
- **Milisaniye Hassasiyetli Paket Zaman Çizelgesi (`packet-timeline-scheduling`):** SimPy üzerinde her paketin ön ek, başlık ve veri iletim sürelerini (ToA) hesaplayarak zaman ekseninde çakışan pencereleri ve çarpışmaları gösteren Gantt çizelgesi.
- **Yapılandırılmış Rapor Kayıt Sistemi (`out-report-metric-logging`):** Gönderilen, alınan, çarpışan paketleri, sekme sayılarını ve gecikmeleri `/out/report/*.csv` dosyalarına işleyen veri kaydı altyapısı.

### 🖥️ interactiveSim.py Canlı Firmware Öykünümü (meshtastic.org/docs/software/meshtasticator/interactive-sim)
- **PlatformIO Yerel Firmware Hedefi (`interactivesim-native-firmware`):** Mikrodenetleyici olmadan `pio run -e native` ile x86/ARM Linux üzerinde doğrudan çalışan Portduino tabanlı yerel Meshtastic ikilisi derleme yöntemi.
- **interactiveSim.py Komut Satırı Bayrakları (`interactivesim-command-flags`):** `-p` (ikili yolu), `-d` (Docker kipi), `-c` (çarpışma öykünümü) ve `-m` (yol kaybı modeli) parametreleriyle simülatörü yapılandırma standardı.
- **Düğüm Başına TCP Port Tahsisi (`per-node-tcp-port-allocation`):** 4403 portundan başlayarak her sanal düğüme bağımsız birer TCP soketi (`4403`, `4404`...) atayan ve harici istemcilerin düğümleri yönetmesini sağlayan mimari.
- **Ayrık Terminal Pencereleri ve Canlı Loglar (`multi-window-terminal-emulation`):** Her düğüm için bağımsız bir terminal penceresi fırlatarak (xterm/tmux) cihazların bootloader, FreeRTOS görev ve yönlendirme loglarını canlı izleme tekniği.
- **Sanal SPIFFS & NVS Bellek İzolasyonu (`simulated-spiffs-storage-isolation`):** Eşzamanlı çalışan düğümlerin kimliklerinin, NodeDB verilerinin ve kanal PSK anahtarlarının birbirine karışmasını önleyen izole dizin mimarisi (`prefs/node_x`).
- **Resmi İstemcilerin Sanal Düğümlere Bağlanması (`client-app-tcp-interfacing`):** Meshtastic Web, Python CLI ve Android uygulamalarının yerel TCP soketleri üzerinden sanal düğümlere bağlanıp gerçek telsiz gibi mesajlaşma ve telemetri testi yapabilmesi.
- **Dinamik Yol Kaybı Modeli Seçimi (`interactivesim-pathloss-selection`):** `-m` parametresiyle metropol, banliyö veya kırsal yayılım modelleri seçilerek sinyalin mesafeye göre zayıflamasının ve paket düşürmelerin canlı öykünmesi.
- **Uçtan Uca Çok Sekmeli Yönlendirme Öykünümü (`end-to-end-multihop-emulation`):** Doğrudan menzil dışı sanal düğümlerin aradaki Router düğümü üzerinden sekerek uçtan uca mesajlaşması, hop limit düşümü ve ACK tesliminin doğrulanması.
- **Betik Tabanlı Ağ Trafiği Enjeksiyonu (`scripted-mesh-traffic-injection`):** Harici Python veya bash betikleriyle eşzamanlı olarak düğüm portlarına yoğun mesaj basarak CSMA/CA bekleme sürelerini ve kuyruk taşmalarını stres testine tabi tutma.
- **Simülasyon Sonlandırma ve Süreç Temizliği (`interactivesim-process-cleanup`):** `Ctrl+C` veya SIGINT sinyaliyle açılan tüm alt süreçleri, Docker konteynerlerini ve TCP soketlerini temizleyerek port kilitlenmelerini önleyen kapanış mekanizması.

### 🔹 Açık Standart ve Tedarikçi Bağımsızlığı (Open Architecture & Vendor Neutrality)
Meshtastic'in hiçbir tescilli ticari protokole veya tek bir donanım üreticisine bağımlı kalmamasını sağlayan açık kaynak ekosistem felsefesi (GPL-3.0 lisansı ve açık Protobuf şemaları). Semtech SX1262/SX1276/LR1121 telsizleri ile ESP32, nRF52840 ve RP2040 işlemcili onlarca farklı üreticinin (Heltec, LilyGO, RAKwireless) donanımları tam uyumla birlikte çalışabilir.

### 🔹 UF2 Bootloader ve DFU Modu (Device Firmware Upgrade)
nRF52840 tabanlı cihazlarda (SenseCAP X1, WisBlock RAK4631, T-Echo vb.) cihazı USB üzerinden bilgisayara harici bir flash sürücüsü gibi bağlayarak `.uf2` firmware dosyalarını sürükle-bırak yöntemiyle veya Web Flasher üzerinden yüklemeyi sağlayan önyükleyici modu. Bluetooth üzerinden (OTA) hatalı güncelleme sonucu cihazın kilitlenmesini (bricking) önler.

### 🔹 esptool.py (Espressif ROM Önyükleyici Aracı)
ESP32 ve ESP8266 yongalarının kalıcı ROM önyükleyicisiyle haberleşerek komut satırından flash bellek silen (`erase_flash`), firmware yükleyen (`write_flash`) ve donanım kimliği sorgulayan resmi Python aracı.

### 🔹 RAK4631-R RUI3'ten Meshtastic Önyükleyicisine Dönüştürme
Fabrikadan LoRaWAN RUI3 yazılımıyla gelen RAK4631-R modüllerinin, açık kaynaklı Adafruit nRF52 önyükleyicisine dönüştürülerek Meshtastic uyumlu hale getirilmesi işlemi.

### 🔹 Flash Bellek Silme ve Fabrika NVS Sıfırlaması (Flash Erase)
Bozulan NVS kayıtları veya yeniden başlama döngüsüne (bootloop) giren cihazları kurtarmak için ESP32'de `esptool.py erase_flash`, nRF52'de ise `nrf52-erase.uf2` ile yapılan tam bellek temizliği.

---

## 6. Radyo Frekansı (RF) ve Yayılım (RF & Propagation)

### 🔹 LPWAN (Düşük Güçlü Geniş Alan Ağı - Low-Power Wide-Area Network)
Düşük veri hızları karşılığında kilometrelerce fiziksel kapsama alanı ve yıllara varan batarya ömrü sunmak üzere optimize edilmiş kablosuz telekomünikasyon ağı kategorisi. LoRa modülasyonu sayesinde yüksek alıcı hassasiyeti (-140 dBm) ve 100 mW altı çıkış güçleriyle onlarca kilometrelik menzil sağlar.

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

### 🔹 LoRa Sembol Süresi ve Yuva Zamanlaması ($T_{sym}$ Slot Time)
Bir LoRa cıvıltı (chirp) sembolünün havada iletilmesi için geçen süre ($T_{sym} = 2^{SF} / BW$). Meshtastic'in tüm CSMA/CA çekişme yuvaları (contention slot times) ve dinamik geri sayım süreleri bu sembol süresi baz alınarak hesaplanır. Paket çarpışmaları matematiksel olarak en aza indirgenir.

### 🔹 Modem Ön Ayarları (Modem Presets)
- **LongFast (Varsayılan):** $SF=11, BW=250\text{ kHz}, CR=4/5$ (~1.07 kbps). Küresel açık kanalların standart dengeli profili.
- **LongSlow / LongModerate:** $SF=12, BW=125\text{ kHz}, CR=4/8$ (~0.18 kbps). Aşırı uzak mesafe ve derin vadi haberleşmesinde maksimum duyarlılık (-148 dBm).
- **ShortFast:** $SF=7, BW=250\text{ kHz}, CR=4/5$ (~10.9 kbps). Festival, kamp ve etkinlik gibi dar alanlarda hava süresini minimuma indiren yüksek hızlı profil.

### 🔹 Fresnel Bölgesi ve Radyo Görüş Hattı (Fresnel Zone & LoS)
İki telsiz düğümü arasındaki doğrusal görüş hattını çevreleyen eliptik elektromanyetik hacim. Optik görüş yetmez; radyo dalgalarının faz iptaline uğramaması için 1. Fresnel bölgesinin en az %60'ının binalardan, tepelerden ve yoğun ağaç örtüsünden arındırılmış olması gerekir.

### 🔹 Meshtastic Dünya Menzil Rekorları ve HAB Uçuşları
Standart yasal lisanssız ISM güç sınırlarında (+14 dBm / +22 dBm) elde edilmiş resmi rekorlar: Yer-yer (Ground-to-Ground) optik görüş rekoru 254+ km; stratosferik hava balonlarına (HAB) bağlanan düğümler ile yer istasyonları arasında 1000+ km doğrulanmış paket teslimatı.

### 🔹 TX Çıkış Gücü ve Efektif Işıma Gücü (TX Power & EIRP)
Telsiz alıcı-verici yongasının antene sağladığı RF gücü (dBm veya mW). Türkiye ve Avrupa BTK/ETSI mevzuatına göre lisanssız 868 MHz bandında azami yasal güç 25 mW (+14 dBm EIRP) ile sınırlandırılmıştır.

### 🔹 Atmosferik Kırılma ve 4/3 Efektif Dünya Yarıçapı (4/3 Earth Radius)
Atmosferdeki sıcaklık ve basınç değişimlerinin radyo dalgalarını yeryüzüne doğru bükmesi sonucu efektif radyo ufkunun geometrik optik ufuktan yaklaşık %15 daha uzun olmasını açıklayan standart RF modeli ($k = 1.33$).

### 🔹 HeyWhatsThat ve Sayısal Yükseklik Profili (DEM Arazi Analizi)
Sayısal Yükseklik Modelleri (DEM) ve atmosferik kırılma algoritmaları kullanarak, dağ tepelerine kurulacak Meshtastic rölelerinin gerçek radyo kapsama haritalarını ve iki nokta arasındaki Fresnel açıklığını simüle eden web aracı.

### 🔹 Anten Polarizasyonu ve Dikey Eksen Uyumu (Polarization)
Radyo dalgasının elektrik alan yönü. Meshtastic ağında tüm antenler dikey (vertical) konumlandırılmalıdır; biri dikey diğeri yatay olduğunda 20 ila 30 dB (100 ila 1000 kat) sinyal kaybı (çapraz polarizasyon kaybı) yaşanır.

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

### 🔹 MQTT Client Proxy (İstemci Vekili Protokolü)
Dahili Wi-Fi desteği olmayan (veya pil tasarrufu için Wi-Fi'ı kapalı olan nRF52840, RP2040 vb.) düğümlerin, USB Seri port veya TCP arayüzü üzerinden bağlı oldukları bilgisayar/sunucunun internetini kullanarak MQTT ağına erişmesini sağlayan Meshtastic protokolü (`mqttClientProxyMessage`). `meshtastic-mqtt-proxy` (ve LN4CY/mqtt-proxy) gibi açık kaynaklı bağımsız vekil yazılımları, telsizi kesintisiz bir MQTT gateway'e dönüştürür.

### 🔹 Drop-Oldest Queue (Hız Sınırlama ve Bayat Paket Eleme)
Yüksek hızlı internetten gelen yoğun MQTT paket trafiğinin, dar bantlı ve düşük hızlı LoRa telsiz bağlantısını tıkamasını ve cihazın kilitlenmesini önleyen akıllı kuyruk mekanizması. Tampon bellek dolduğunda en eski ve bayatlamış mesajlar çöpe atılarak telsize daima en güncel telemetri ve GPS paketlerinin ulaşması garanti edilir.

### 🔹 Implicit ACK Restoration (Örtük ACK Kurtarma)
MQTT köprülerinde paket döngüsü (loop) engellemesi nedeniyle iletim onaylarının (ACK) yutulması sonucunda oluşan "Kırmızı X / Red X" (Mesaj Teslim Edilemedi) hatasını çözen teyit simülasyonu. Broker'dan dönen eko paketini tespit ederek yerel istemciye örtük onay gönderir.

### 🔹 Virtual Channels & Cross-Region Monitoring (Sanal Kanallar)
Başka ülkelerin veya farklı frekans bölgelerinin (`EXTRA_MQTT_ROOTS`) MQTT trafiğini yerel telsiz bandına basmadan (RF crosstalk ve hava kirliliği yaratmadan), sadece sunucu ve harita düzeyinde pasif olarak dinlemeyi sağlayan vekil yapılandırması.

### 🔹 MeshMonitor (Açık Kaynak Ağ İzleme Paneli)
Meshtastic düğümlerini, MQTT paket trafiğini, SNR sinyal geçmişini ve harita topolojisini 7/24 izlemek için Docker üzerinde çalışan web tabanlı yönetim paneli (`meshmonitor.org`). `mqtt-proxy` ile tam entegre çalışır.

### 🔹 Home Assistant Entegrasyonu (`meshtastic-ui-ha`)
Meshtastic telsiz kartlarını Home Assistant akıllı ev sunucusuna (USB/Seri veya TCP üzerinden) bağlayarak, tüm örgüsel ağı akıllı evin kontrol paneline taşıyan açık kaynaklı entegrasyon ([Daring-Designs/meshtastic-ui-ha](https://github.com/Daring-Designs/meshtastic-ui-ha)). Canlı sohbet, düğüm tablosu, interaktif Leaflet haritası ve radyo donanım durumunu tek merkezden yönetir.

### 🔹 Waypoints (Yol Noktaları / Coğrafi İşaretçiler)
Harita üzerinde acil toplanma alanını, sahra çadırını, su kuyusunu veya sabit tepe rölesini tanımlayan ve telsiz üzerinden ağa yayınlanan adlandırılmış coğrafi işaret noktaları (`mesh.proto: Waypoint`). Tüm el cihazları ve akıllı ev haritalarında ortak nokta olarak canlı görüntülenir.

### 🔹 Mesh Olay Otomasyonları ve Tetikleyicileri (Smart Home Automations)
Telsizden belirli bir anahtar kelime, acil durum çağrısı (SOS) veya doğrudan mesaj (DM) alındığında evdeki sirenleri çalabilen, akıllı ışıkları açabilen veya yerel bildirim gönderebilen kural motoru. İnternet ve GSM şebekelerinin çöktüğü afet senaryolarında bağımsız sivil alarm sistemi sağlar.

### 🔹 Düğüm Varlık Sensörleri ve Teşhis Değerleri (Entity Sensors)
Bir Meshtastic cihazının batarya yüzdesi, voltajı, hava süresi kullanımı (`air_util_tx`), kanal doluluk oranı (`channel_utilization`) ve sinyal kalitesinin (SNR/RSSI) Home Assistant sensör varlıklarına dönüştürülmesi. Geçmişe dönük telemetri grafikleriyle sabit rölelerin sağlık durumu izlenir.

### 🔹 Canned Messages Module (Hazır Mesaj Şablonları)
Telefona bağlanmadan, cihaz üzerindeki döner enkoder (rotary encoder) veya fiziksel butonlarla hafızadaki hazır şablon mesajların (ör. "Kamptayım", "İyiyim", "SOS") ekrandan seçilip doğrudan gönderilmesini sağlayan yerleşik firmware modülü.

### 🔹 External Notification Module (Harici Bildirim ve Siren)
Mesaj veya acil durum çağrısı geldiğinde karta bağlı harici bir buzzer'ı, melodik piezo hoparlörü (PWM RTTL formatında), titreşim motorunu veya flaşör LED'i tetikleyen donanım bildirim modülü.

### 🔹 Paxcounter Module (Kalabalık ve İnsan Yoğunluğu Sayacı)
ESP32'nin Wi-Fi ve Bluetooth radyolarını dinleme (promiscuous) moduna alarak çevredeki akıllı telefonların sinyallerini tarayan ve kişisel veri toplamadan ortamdaki kalabalık/insan sayısını telsizle raporlayan modül.

### 🔹 Range Test Module (Menzil Testi ve Sinyal Haritalama)
İki düğüm arasındaki azami telsiz mesafesini, sinyal kalitesini (SNR/RSSI) ve paket kaybını GPS koordinatlarıyla haritalandırmak için kullanılan otomatik teşhis aracı (`RANGE_TEST_APP`). Verileri `.csv` olarak kaydeder.

### 🔹 Detection Sensor Module (Güvenlik ve Hareket Alarmı)
Karta bağlanan PIR hareket sensörü, manyetik kapı/pencere kontağı veya sarsıntı sensörü tetiklendiğinde otomatik olarak tanımlanan kanala telsiz alarmı basan güvenlik modülü.

### 🔹 Çoklu Buton Eylemleri ve Donanım Durum LED'leri (Multi-Click Controls)
Ekransız ve klavyesiz Meshtastic takip cihazlarında (SenseCAP MeshTracker X1 vb.) tek bir fiziksel butonla acil durum beacon'ı fırlatma (çift tık), GPS modülünü uykuya alma (üç tık), sesli ikazı kapatma (dört tık) ve güç yönetimi (uzun basış) sağlayan saha kontrol arayüzü.

### 🔹 Barometrik İrtifa ve Basınç Telemetrisi (Barometric Telemetry)
Dahili hava basıncı sensörü (300–1100 hPa) ile dikey eksendeki yükseklik değişimlerinin santimetre hassasiyetinde ölçülerek `TELEMETRY_APP` (Port 67) üzerinden ağa aktarılması. GPS'in dikey irtifa hata payını kompanse ederek dağcılık ve arama-kurtarma operasyonlarında hassas yükseklik tespiti sağlar.

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
