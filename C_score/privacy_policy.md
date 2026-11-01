# CardioScore Gizlilik Politikası

> **Yayın öncesi taslak — henüz mağazada veya uygulamada yayımlanmak için hazır değildir.**
> Köşeli parantez içindeki alanlar uygulama sahibince doldurulmalı; veri sorumlusu/veri işleyen rolleri, hukuki işleme şartları, saklama süreleri, altyapı sağlayıcıları ve uluslararası aktarım düzeni doğrulanmalıdır. Bu metin teknik incelemeye dayalı bir taslaktır; hukuki danışmanlık değildir.

**Sürüm:** 0.1 (taslak)  
**Son inceleme tarihi:** 1 Kasım 2026  
**Yürürlük tarihi:** [YAYIN TARİHİNİ EKLEYİN]  
**Uygulama:** CardioScore / Cardio Score  
**Paket adı:** `com.alihmida.cardio_score_app`

## 1. Bu politika neyi kapsar?

Bu politika, CardioScore mobil uygulaması ve uygulamanın kullandığı API hizmeti üzerinden işlenen kişisel verileri açıklar. CardioScore; sağlık profesyonellerinin hasta kayıtlarını yönetmesine, kalp cerrahisi öncesi klinik parametreleri değerlendirmesine ve risk değerlendirme geçmişini görüntülemesine yardımcı olan bir yazılımdır.

Uygulamadaki hasta kayıtları, uygulamaya giriş yapan sağlık profesyonelinden farklı kişilere ait olabilir. Bu nedenle sağlık profesyoneli, hastaya ait verileri uygulamaya girmeden önce gerekli yetkiyi ve bilgilendirmeyi sağlamalıdır. Veri sorumlusu ile CardioScore hizmet sağlayıcısının hangi işlemler için veri sorumlusu veya veri işleyen olduğu, hizmetin nasıl sunulduğuna ve taraflar arasındaki sözleşmelere göre belirlenmelidir: **[TARAFLARIN ROLLERİNİ VE İLGİLİ KURUMU AÇIKLAYIN]**.

## 2. Hangi verileri işleyebiliriz?

Uygulama ve backend kaynak kodunda görülen işlevlere göre aşağıdaki veri kategorileri işlenebilir:

| Veri kategorisi | Örnekler | Kullanım yeri |
| --- | --- | --- |
| Profesyonel hesap bilgileri | Ad soyad, e-posta, parola özeti, rol, uzmanlık, lisans numarası; backend şemasında isteğe bağlı hastane kimliği | Hesap oluşturma, oturum açma, kullanıcı rolü ve erişim kontrolü |
| Hasta kimlik ve iletişim bilgileri | Ad soyad, T.C. kimlik numarası, doğum tarihi, cinsiyet, telefon, adres, acil durumda aranacak kişinin adı ve telefonu | Yetkili sağlık profesyonelinin hasta kaydı oluşturması ve kaydı bulması |
| Sağlık ve klinik bilgiler | Boy, kilo, kan grubu; kronik akciğer hastalığı, damar hastalığı, önceki kalp ameliyatı, kreatinin, diyaliz, endokardit, diyabet, nörolojik durum, ejeksiyon fraksiyonu, pulmoner arter basıncı, anjina, yakın zamanda geçirilmiş miyokart enfarktüsü, tansiyon, nabız ve ameliyatın aciliyeti/türü gibi değerlendirme girdileri | Risk değerlendirmesini hesaplama ve değerlendirme geçmişini gösterme |
| Değerlendirme sonuçları | Toplam puan, risk bandı, tahmini mortalite değeri, puan dökümü, gerekçeler, açıklama, öneri metinleri, algoritma sürümü, tarih, durum, hekim notu ve hesaplama girdisinin anlık görüntüsü | Sonucu göstermek, geçmiş değerlendirmeleri sunmak ve denetim izini korumak |
| Teknik ve denetim bilgileri | İstek kimliği, HTTP yöntemi ve yolu, yanıt kodu; denetim kayıtlarında kullanıcı kimliği, işlem, kaynak türü/kimliği, IP adresi, User-Agent ve bazı işlem metaverileri | Güvenlik, hata araştırması, kötüye kullanımın önlenmesi ve işlemlerin denetlenmesi |
| Cihazda tutulan tercihler | Dil, tema, “beni hatırla” seçeneği kullanıldığında e-posta adresi ve oturum belirteçleri | Tercihleri hatırlama ve oturumun sürdürülmesi |

Şema, klinik rapor kimliklerini değerlendirme isteğinde kabul eder ve rapor kayıtları için hasta ilişkisi içerir. İncelenen mobil istemci ve API’de rapor dosyasını yükleyen bir uç nokta veya dosya içeriği depolama akışı tespit edilmemiştir. Bu nedenle bu taslak, klinik rapor dosyalarının yüklendiğini ya da saklandığını iddia etmez. Dosya yükleme özelliği eklenirse politika güncellenmelidir.

Uygulama Android’de oturum belirteçlerini `flutter_secure_storage` üzerinden, şifreli paylaşılan tercihler kullanarak saklar. Hatırlanan e-posta, tema ve dil tercihleri uygulama tercihleri alanında tutulur. Parolalar backend’de Argon2id ile özetlenir; düz metin parola olarak veritabanına yazılmaz.

Hasta T.C. kimlik numarası backend’de AES-256-GCM ile şifrelenmiş biçimde saklanacak şekilde uygulanmıştır. Veritabanında ayrıca şifreli metinden türetilen bir SHA-256 alanı vardır. Şifrelemede her işlemde rastgele IV kullanıldığından bu alanı anonimleştirme veya kişiyi belirleyememe garantisi olarak değerlendirmiyoruz.

## 3. Verileri hangi amaçlarla kullanırız?

Veriler, ürünün mevcut işlevlerine göre şu amaçlarla işlenebilir:

1. Profesyonel kullanıcı hesabı oluşturmak, kimlik doğrulamak ve hesabın rolüne uygun erişim sağlamak.
2. Sağlık profesyonelinin hasta kayıtlarını oluşturmasına, güncellemesine, aramasına ve görüntülemesine olanak sağlamak.
3. Klinik değerlendirme girdilerini işlemek; puan, risk bandı, tahmini değer, gerekçe ve açıklama üretmek.
4. Değerlendirme geçmişini ve denetim kayıtlarını sunmak.
5. Hizmeti güvenli ve çalışır tutmak; teknik sorunları, yetkisiz erişim girişimlerini ve kötüye kullanımı araştırmak.
6. Yasal yükümlülükleri ve yetkili makamların geçerli taleplerini karşılamak.

Her amaç için kullanılacak hukuki işleme şartı ve sağlık verilerine uygulanacak özel şart, hizmetin gerçek kullanım biçimine göre belirlenmelidir: **[HER VERİ KATEGORİSİ İÇİN HUKUKİ İŞLEME ŞARTINI VE SAĞLIK VERİLERİNE UYGULANAN ŞARTI EKLEYİN]**. Bu taslak açık rızanın her işlem için gerekli veya tek başına yeterli olduğunu varsaymaz.

## 4. Risk hesaplaması ve otomatik işleme

Teknik referansta anlatıldığı ve backend kaynak kodunda görüldüğü üzere hesaplama, sabit kuralları çalıştıran deterministik ve eklemeli bir puanlama motorudur. İncelenen hesaplama yolunda öğrenilmiş bir makine öğrenmesi modeli veya harici üretken yapay zekâ hizmeti kullanılmamaktadır. Girdilerden toplam puan ve risk seviyesi üretilir; tahmini değer sabit bir eşleştirme tablosundan gelir, açıklamalar ise şablonlarla oluşturulur. Değerlendirme girdisi ve sonucu veritabanına kaydedilebilir.

Teknik referans; puanlama kurallarının ve tahmini mortalite tablosunun hasta kohortunda kalibre veya klinik olarak valide edilmediğini, bazı eşik ve ağırlıkların gerekçelendirilmediğini belirtir. Bu nedenle sonuçlar tahmindir; tanı, tedavi önerisi veya klinik karar yerine geçmez. Sağlık profesyoneli girdileri doğrulamalı ve sonucu klinik bağlam içinde bağımsız olarak değerlendirmelidir. Ürün sahibi, Google Play’deki sağlık ve tıbbi işlev beyanlarında ürünün tıbbi cihaz statüsünü ayrıca değerlendirmelidir.

## 5. Veriler kimlerle paylaşılır?

Uygulama, klinik kayıt ve hesap verilerini uygulamanın backend API’sine gönderir. Kod tabanındaki API adresi Google Cloud Run altyapısında çalışan bir `run.app` hizmetini gösterir. Backend PostgreSQL kullanır; gerçek veritabanı sağlayıcısı ve konumu çalışma ortamındaki veritabanı bağlantı yapılandırmasına bağlıdır ve bu incelemede doğrulanamamıştır.

Hizmetin çalışması için veriler, uygulama sahibi adına çalışan barındırma, veritabanı, güvenlik, yedekleme ve teknik destek sağlayıcılarıyla işlenebilir. Yayından önce sağlayıcıların tam adları, işleme rolleri, konumları, alt işleyenleri ve ilgili sözleşmeler bu bölüme eklenmelidir: **[SAĞLAYICI LİSTESİNİ VE VERİ MERKEZİ ÜLKELERİNİ EKLEYİN]**.

Klinik değerlendirme girdilerinin üçüncü taraf bir yapay zekâ sağlayıcısına gönderildiği görülmemiştir. Uygulama, üçüncü taraflara pazarlama veya reklam amacıyla sağlık verisi satmak üzere tasarlanmamıştır. Bu beyan; ürüne analitik, reklam, hata izleme veya başka SDK’lar eklenirse yeniden incelenmelidir.

Veriler ayrıca, geçerli bir hukuki zorunluluk bulunduğunda veya kişilerin güvenliğini korumak gerektiğinde yetkili kamu kurumlarıyla paylaşılabilir. Sağlık profesyoneli ya da sağlık kuruluşu, kendi mesleki ve kurumsal yükümlülükleri kapsamında hasta kayıtlarını ilgili kişilerle veya yetkili sağlık hizmeti sağlayıcılarıyla paylaşabilir.

## 6. Veriler nerede işlenir ve yurt dışına aktarılır mı?

API hizmetinin Cloud Run üzerinde çalıştığı anlaşılmaktadır; ancak Cloud Run hizmetinin bölgesi ve PostgreSQL veritabanının sağlayıcısı/bölgesi bu kaynak kodundan doğrulanamamıştır. Bu nedenle verilerin Türkiye’de veya belirli bir ülkede kaldığına dair taahhütte bulunmuyoruz.

Yayın öncesinde API, veritabanı, yedekler, günlükler ve destek erişimleri için gerçek ülke/bölgeler belirlenmeli; Türkiye’den yurt dışına aktarım varsa yürürlükteki mevzuata uygun aktarım mekanizması ve gerekli bilgilendirmeler tamamlanmalıdır: **[ÜLKE/BÖLGE VE AKTARIM GÜVENCELERİNİ EKLEYİN]**.

## 7. Saklama süreleri ve silme

Kaynak kodunda hasta, risk değerlendirmesi ve denetim kayıtları için belirlenmiş bir saklama takvimi veya otomatik silme işi tespit edilmemiştir. Kayıtlar PostgreSQL’de, oturum belirteçleri ve bazı tercihler cihazda tutulabilir. Bu nedenle şu anda kesin bir saklama süresi beyan edemiyoruz.

Veri kategorisi bazında saklama süresi ve sürenin başlangıç noktası belirlenmelidir: **[HESAP, HASTA KAYDI, DEĞERLENDİRME, DENETİM KAYDI, YEDEK VE TEKNİK GÜNLÜK SÜRELERİNİ EKLEYİN]**. Veriler, ilgili amaç için gerekli süreyi aşmayacak şekilde saklanmalı; yedeklerden silinme ve yasal saklama istisnaları da açıklanmalıdır.

Uygulamada hesap oluşturma vardır; ancak incelenen uygulama ve backend kodunda hesap silme ekranı, harici hesap silme web sayfası veya hesap silme API’si bulunmamaktadır. Bu özellik eklenip çalışır hâle gelmeden, hesap ve ilişkili verilerin silinebileceğini vaat etmeyin. Hesap silme uygulandığında kullanıcıya hem uygulama içinden hem de web üzerinden başvuru olanağı verilmeli; kullanıcı kayıtları, ilişkili hasta ve değerlendirme verileri ile denetim kayıtlarının akıbeti belirlenmeli ve saklanması gereken istisnalar açıklanmalıdır.

Hesap silme ve veri talepleri için kullanılacak sayfa: **[HERKESE AÇIK HESAP SİLME URL’SİNİ EKLEYİN]**. Başvuru kanalı: **[GİZLİLİK İLETİŞİM E-POSTASI/ADRESİ]**.

## 8. Güvenlik

Uygulama ile API arasındaki yapılandırılmış temel adres HTTPS kullanır. Backend’de parola özetleme için Argon2id, hasta T.C. kimlik numarasını şifrelemek için AES-256-GCM, oturum için JWT ve rol kontrolleri kullanılır. Android istemcisi oturum belirteçlerini Android şifreli paylaşılan tercihlerle korunan güvenli depolamada tutar. API denetim kayıtları erişilen kaynaklar ve işlemler hakkında iz oluşturur.

Bu kontroller, mutlak güvenlik veya tüm veritabanı alanlarının uygulama katmanında şifrelenmiş olduğu anlamına gelmez. Veritabanı ve yedeklerin depolama katmanındaki şifrelemesi, anahtar yönetimi, erişim yetkileri, yedekleme ve olay müdahalesi uygulama sahibi tarafından doğrulanmalıdır: **[GÜVENLİK KONTROLLERİNİ VE SORUMLU EKİBİ DOĞRULAYIN]**.

İstemci tarafındaki hassas kayıt gövdesi, parola ve oturum belirteci değerlerini yazan debug günlükleri bu politika hazırlanırken kaldırılmıştır. Backend’de teknik istek günlükleri yöntem, URL/yol, istek kimliği ve yanıt kodu gibi metaverileri; denetim günlükleri kullanıcı kimliği, işlem, kaynak kimliği, IP adresi, User-Agent ve işlem metaverilerini içerebilir. Bu günlüklerin erişim yetkileri ve saklama süresi ayrıca sınırlandırılmalıdır.

Bir güvenlik veya veri ihlali şüphesi fark ederseniz **[GÜVENLİK İLETİŞİM KANALI]** üzerinden bize bildirin. Bildirim ve ilgili kişilere/kurumlara yapılacak duyurular yürürlükteki mevzuata göre ele alınır.

## 9. İlgili kişilerin başvuruları

Uygun olduğu ölçüde, ilgili kişiler kişisel verilerine erişme, yanlış verileri düzelttirme, silme veya yok etme talep etme, işleme faaliyetlerine itiraz etme ve yürürlükteki mevzuatta öngörülen diğer haklarını kullanabilir. Başvurular, **[VERİ SORUMLUSUNUN TAM UNVANI]** adresine **[BAŞVURU E-POSTASI/POSTA ADRESİ/WEB FORMU]** üzerinden iletilmelidir. Başvuru sahibinin kimliğini güvenli ve orantılı biçimde doğrulamak gerekebilir.

Hasta kaydı sağlık profesyoneli tarafından yönetiliyorsa, başvurunun önce ilgili sağlık kuruluşuna iletilmesi gerekebilir. CardioScore, kayıt üzerinde yetkili olmayan bir kullanıcıya hasta verisi açıklamaz. Uygulama sahibinin ve sağlık kuruluşunun başvurulardaki görev dağılımı **[TARAFLAR ARASINDAKİ BAŞVURU SÜRECİNİ AÇIKLAYIN]**.

## 10. Çocuklar ve başka kişiler hakkındaki veriler

CardioScore çocukların kendi hesaplarını oluşturması için tasarlanmamıştır. Bununla birlikte sağlık profesyonelleri, mesleki ve hukuki yetkileri kapsamında reşit olmayan hastalara ilişkin sağlık bilgilerini sisteme girebilir. Bu durumda gerekli veli/temsilci bilgilendirmesi ve diğer hukuki koşulları veriyi giren sağlık kuruluşu sağlamalıdır.

Kullanıcılar, acil durum kişisi gibi başka kişilere ait iletişim bilgilerini girerken bu kişileri uygun şekilde bilgilendirmeli ve yalnızca gerekli verileri paylaşmalıdır.

## 11. Politika değişiklikleri

Veri işleme biçimi, ürün işlevleri, altyapı sağlayıcıları veya mevzuat değişirse bu politika güncellenir. Önemli değişiklikler uygulama içinde veya uygun başka bir kanalla duyurulur. Güncel metin **[GİZLİLİK POLİTİKASININ KALICI, HERKESE AÇIK HTTPS URL’Sİ]** adresinde yayımlanır.

## 12. İletişim

**Hizmet/uygulama adı:** CardioScore  
**Veri sorumlusu veya hizmet sağlayıcının tam yasal unvanı:** [DOLDURULACAK]  
**Kayıtlı adres:** [DOLDURULACAK]  
**Gizlilik ve veri başvuruları:** [DOLDURULACAK]  
**Güvenlik bildirimleri:** [DOLDURULACAK]  
**Hesap silme sayfası:** [DOLDURULACAK]

---

## Yayın öncesi tamamlanacaklar

- [ ] Veri sorumlusu/hizmet sağlayıcının tam yasal unvanı, adresi ve gizlilik iletişim kanalı
- [ ] Her veri kategorisi için hukuki işleme şartı; sağlık verileri için uygulanacak özel şart
- [ ] Cloud Run bölgesi, PostgreSQL sağlayıcısı/bölgesi, yedek konumları ve alt işleyenler
- [ ] Yurt dışına aktarım olup olmadığı ve varsa uygun aktarım mekanizması
- [ ] Hesap, hasta, değerlendirme, denetim günlüğü ve yedekler için saklama/silme süreleri
- [ ] Hesap silme özelliği: uygulama içi yol, herkese açık web talep sayfası, ilişkili sağlık kayıtları ve yasal saklama istisnaları
- [ ] Tıbbi cihaz statüsü, sağlık işlevi beyanı ve Google Play açıklamasında gereken uyarılar
- [ ] İzinler, SDK’lar ve gerçek sürümde kullanılan tüm üçüncü tarafların veri akışları
- [ ] Bu politikanın HTTPS üzerinden erişilebilen, giriş gerektirmeyen kalıcı web sayfasında yayımlanması ve uygulama/Play Console’da bağlanması
- [ ] İngilizce mağaza veya kullanıcı kitlesi hedefleniyorsa, İngilizce metnin de hazırlanıp Türkçe metinle tutarlı tutulması

## Kaynaklar ve teknik dayanak

- Proje kökündeki `index.html` CardioScore’u 21 sabit kural kullanan deterministik ve eklemeli risk skorlama motoru olarak açıklar; klinik kalibrasyon/doğrulama eksiklerini ve tahmini sonucun klinik karar yerine geçmediğini belirtir.
- Backend veri kategorileri: `backend/prisma/schema.prisma`, `backend/src/api/validators/` ve `backend/src/api/middlewares/auditLogger.ts`.
- İstemci yerel depolaması: `app_core/cardio_score_app/lib/src/core/storage/`.
- Google Play sağlık uygulamaları: <https://support.google.com/googleplay/android-developer/answer/16679511>
- Google Play kullanıcı verileri, gizlilik politikası ve hesap silme: <https://support.google.com/googleplay/android-developer/answer/10144311>
- KVKK Aydınlatma Yükümlülüğü: <https://www.kvkk.gov.tr/Icerik/2033/Aydinlatma-Yukumlulugu->
- KVKK Yurt Dışına Aktarım: <https://www.kvkk.gov.tr/Icerik/2053/Yurtdisina-Aktarim>
