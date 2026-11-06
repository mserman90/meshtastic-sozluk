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
- **Heltec WiFi LoRa 32 (V2 / V3):** En yaygın ve ucuz ESP32-S3 tabanlı, dahili OLED ekranlı geliştirme kartı.
- **LilyGO TTGO T-Beam:** 18650 pil yuvası, GPS, dahili PMIC ve LoRa telsizi barındıran klasik saha ve araç takip düğümü.
- **LilyGO T-Echo:** nRF52840 işlemcili, E-ink ekranlı ve GPS'li taşınabilir el cihazı.
- **RAKwireless WisBlock (RAK4631 / RAK19007):** Modüler yapılı, güneş paneliyle aylarca çalışabilen profesyonel nRF52840 altyapı donanımı.
  - **RAK19007 / RAK19003 Taban Kartları:** USB-C, solar şarj ve lehim gerektirmeyen sensör yuvaları barındıran 2. nesil WisBlock taşıyıcı kartları.
  - **RAK4631 Çekirdek Modülü:** Nordic nRF52840 ve Semtech SX1262 içeren ultra düşük güçlü ($< 15\text{ }\mu\text{A}$) ana işlemci modülü.
  - **RAK12500 GNSS & RAK13800 Ethernet:** Tak-çalıştır u-blox ZOE-M8Q GPS ve kablolu 10/100 Ethernet MQTT ağ geçidi genişleme modülleri.
- **RAK WisMesh Serisi (Kullanıma Hazır Fabrika Cihazları):**
  - **WisMesh Board ONE:** nRF52840, SX1262, 1.3" OLED ekran ve GPS yuvasını birleştiren Meshtastic'e özel entegre anakart.
  - **WisMesh Pocket:** Özel koruyucu kasalı, 1.3" OLED ekranlı, butonlu ve bataryalı kullanıma hazır kompakt el telsizi.
  - **WisMesh Tap:** Dokunmatik ekranlı bağımsız Meshtastic mesajlaşma ve harita terminali.
  - **WisMesh Tag:** nRF52840 ve GNSS barındıran IP66 su ve toz geçirmez kompakt personel takip cihazı.
  - **WisMesh Repeater:** Entegre güneş paneli, IP67 kutu ve fiberglas koliner antenle donatılmış dış ortam dağ/çatı rölesi.
  - **WisMesh Gateway:** Ethernet PoE veya Wi-Fi üzerinden çalışan IP67 endüstriyel dış mekan LoRa-MQTT ağ geçidi.
- **LilyGO T-Deck:** Dahili klavyeye, trackball'a ve ekrana sahip, telefonsuz bağımsız kullanılan Meshtastic mesajlaşma cihazı.
- **SenseCAP MeshTracker X1 (Seeed Studio):** Kredi kartı boyutunda (IP66 su geçirmez), Semtech LR2021 LoRa çipi, çift bant L1+L5 GNSS, dahili barometre, buzzer ve 1100 mAh Li-ion pille donatılmış bağımsız takip cihazı.
- **SenseCAP Card Tracker T1000-E (Seeed Studio):** nRF52840 ve Semtech SX1262 LoRa telsizine sahip, manyetik pogo-pin şarjlı, ışık ve sıcaklık sensörlü ultra ince kart takip donanımı.

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
