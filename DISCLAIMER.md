# ⚖️ Sorumsuzluk Beyanı ve Yasal Uyarılar (Legal Disclaimers)

Bu belge, **Meshtastic Türkçe-İngilizce Terimler Sözlüğü** web sitesi, dokümantasyonu, kaynak kodları ve ilgili tüm içerikler için geçerli yasal çerçeveyi, sorumluluk sınırlarını ve uyarıları düzenler.

---

## 1. 🚨 Acil Durum ve Yaşam Güvenliği Uyarısı (Life-Safety Disclaimer)
* **Birincil Güvenlik Sistemi Değildir:** Meshtastic donanım ve yazılımları, afet veya acil durumlarda resmi acil durum haberleşme sistemlerinin (112 Acil Çağrı, AFAD, Kızılay, GSM şebekeleri vb.) yerine geçecek birincil (primer) bir yaşam destek veya güvenlik altyapısı **değildir ve bu amaçla tasarlanmamıştır**.
* **Hayati Riskler:** Arama-kurtarma, yangın, dağcılık, afet veya tıbbi kriz durumlarında yalnızca LoRa/Meshtastic telsiz ağına güvenerek planlama yapılamaz. Telsiz paketlerinin havada çarpışması, menzil dışı kalması, pil tükenmesi veya yazılım kilitlenmeleri nedeniyle mesajların iletilememesinden doğabilecek can ve mal kayıplarından bu projenin yazarları ve katkıcıları hiçbir surette sorumlu tutulamaz.

---

## 2. 📡 Telsiz ve Radyo Frekansı Mevzuatı (RF & Telecommunications Compliance)
* **Bölgesel ve Ulusal Mevzuat (BTK / ETSI):** LoRa cihazları çalıştırılırken kullanıcının bulunduğu ülkenin yetkili frekans ve haberleşme otoritelerinin (Türkiye Cumhuriyeti için **BTK - Bilgi Teknolojileri ve İletişim Kurumu**, Avrupa için **ETSI**) yayımladığı Kısa Mesafe Telsiz Cihazları (KMT / SRD) yönetmeliklerine uyulması yasal bir zorunluluktur.
* **Frekans Uyumluluğu:** Türkiye ve Avrupa Birliği sınırları içinde lisanssız halka açık kullanım için **868.0 - 868.6 MHz** bandı tahsis edilmiştir. Yanlış bölge (ör. ABD için 915 MHz veya Çin için 470 MHz) seçilerek Türkiye'de yayın yapılması, lisanslı GSM ve kamu güvenliği frekanslarına parazit yapacağından ağır adli ve idari yaptırımlara tabidir.
* **Yayın Gücü ve Görev Döngüsü (Duty Cycle):**
  * Yasal azami çıkış gücü (genellikle 25 mW / +14 dBm ERP) aşılmamalıdır.
  * İlgili frekans aralığında saatlik azami **%1 Görev Döngüsü (Duty Cycle)** kuralına uyulmalıdır.
  * Telsiz cihazına yasa dışı harici güçlendirici (Power Amplifier / PA) eklenmesi ve lisanssız frekanslarda izinsiz yüksek güçlü yayın yapılması tamamen kullanıcının şahsi sorumluluğundadır.

---

## 3. 🔒 Kriptografi ve Şifreleme Uyarısı (Encryption & Amateur Radio)
* **Amatör Telsizcilik vs. ISM Bandı:** Meshtastic cihazları halka açık ISM bandında (868 MHz) kullanıldığında AES şifreleme serbesttir. Ancak Meshtastic yazılımı bir amatör telsiz frekansında (ör. 430-440 MHz 70cm amatör bandı) ve amatör çağrı işaretiyle çalıştırılıyorsa, uluslararası ve ulusal amatör telsizcilik mevzuatına göre **şifreli (kriptolu) yayın yapılması kesinlikle yasaktır**. Tüm yayınların açık ve çözülebilir olması gerekir.
* İletişim kanallarında gizli anahtar (PSK) veya Açık Anahtarlı Kriptografi (PKC) kullanılırken mevzuat uyumluluğunu gözetmek tamamen kullanıcının sorumluluğundadır.

---

## 4. ⚡ Donanım Güvenliği ve Yangın Riski (Hardware & Battery Safety)
* **Antensiz Çalıştırma (VSWR Hasarı):** Bir LoRa kartının (SX1262, SX1276 vb.) anteni takılı olmadan USB'ye bağlanması veya vericiye (TX) geçirilmesi, RF çıkış katının aşırı ısınmasına ve entegrenin saniyeler içinde kalıcı olarak yanmasına yol açabilir.
* **Lityum İyon / LiPo Pil Riskleri:** 18650 veya LiPo pillerin ters kutuplanması, kısa devre edilmesi, aşırı şarj edilmesi veya ezilmesi ciddi yangın ve patlama riski taşır. Lityum pillerle çalışırken daima koruma devreli (BMS / PCM) ve kaliteli piller kullanılmalıdır.

---

## 5. 🏷️ Ticari Marka ve Bağımsızlık Beyanı (Trademark Notice)
* **Meshtastic®**, Meshtastic LLC ve ilgili hak sahiplerinin tescilli ticari markasıdır.
* Bu web sitesi, sözlük ve ilgili belgeler **bağımsız bir açık kaynak topluluk çalışmasıdır**.
* Bu projenin resmi Meshtastic projesi, Meshtastic LLC veya Semtech Corporation ile doğrudan, kurumsal veya ticari bir bağı, sponsorluğu veya resmi ortaklığı bulunmamaktadır.

---

## 6. 📄 Genel Sorumsuzluk / "Olduğu Gibi" (Warranty Disclaimer - "AS IS")
Bu sitede ve depoda yer alan tüm teknik tanımlar, şemalar, kod parçacıkları ve yönergeler **"OLDUĞU GİBİ" (AS IS)** esasıyla, yalnızca eğitim, araştırma ve bilgi edinme amacıyla sunulmuştur. 

Sitede yer alan bilgilerin doğruluğu, güncelliği, eksiksizliği veya belirli bir amaca uygunluğu konusunda açık veya zımni hiçbir garanti verilmez. Bu bilgilerin veya yazılımların kullanımından doğrudan, dolaylı, arızi veya cezai olarak doğabilecek maddi hasar, donanım arızası, idari para cezası veya diğer hukuki ihtilaflardan site sahipleri, yazarları ve katkıda bulunanlar hiçbir şekilde mesul tutulamaz.
