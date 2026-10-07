# test-senarlari
imys
PBI VE TASK KABUL TESTİ PROMPTU

TEST EDİLECEK KAYITLAR

PBI No: 26929
Task No (bu sırayla test edilecek):
26930
26931


Her task ayrı ayrı test edilir. PBI yalnızca task bağlamını anlamak için okunur.


ÇALIŞMA AKIŞI

1. Teste başlamadan önce tek bir soru sor: hazır test verisi var mı, yoksa veri üretilmesi mi gerekiyor? Cevap geldikten sonra tüm tasklar bitene kadar kullanıcıya soru sorma.
2. TFS'te PBI'yi ve sıradaki taskı aç. Başlık, Description, bağlı iş kuralı, kabul kriterleri ve Tartışma alanını oku.
3. Test edilebilir açık beklentileri belirle.
4. Bu beklentileri doğrulayan en kısa ve en kapsamlı akışı uygula.
5. Sonucu kesinleştir, raporu yaz.
6. Rapor sonrası onay bekleme. Sonuç Geçti, Kaldı veya Koşulamadı olsun, doğrudan listedeki sonraki taska geç.
7. Tüm tasklar bittiğinde en sonda tek bir özet tablo ver (Task No | Durum | Bug var mı).


TARTIŞMA ALANI (ÇOK ÖNEMLİ)

Her task için Tartışma alanını baştan sona, eskiden yeniye doğru oku. Şunlara dikkat et:
- Önceki test sonuçları ve "Kaldı" bırakılma gerekçeleri
- Geliştiricinin "düzeltildi", "çalışma yapıldı", "ortamda güncellendi" gibi notları
- Analist veya test uzmanı yorumları, kural değişiklikleri, kapsam netleştirmeleri
- Henüz çözülmemiş veya tekrar eden itirazlar

Kullanım kuralları:
- Daha önce Kaldı gerekçesi olan nokta task kapsamındaysa, bu noktayı mutlaka canlıda yeniden doğrula.
- Geliştirici düzeltme bildirdiyse, düzeltmenin gerçekten çalıştığını canlıda kontrol et. Bildirimi tek başına kanıt sayma.
- Tartışma yeni bir kabul kriteri üretmez. Yalnızca mevcut kriterin yorumunu netleştirir ve test odağını belirler.
- Tartışmada çelişki varsa en güncel ve yetkili yorumu esas al, raporun Notlar bölümüne yaz.


KAPSAM KURALI

- Kapsamı task başlığı, Description, bağlı iş kuralı, açık kabul kriterleri ve Tartışma alanındaki netleştirmeler belirler.
- PBI içindeki diğer gereksinimleri, child taskları veya genel fonksiyonları kapsama dahil etme.
- Taskta istenmeyen ekran, alan, iş akışı, rol ve yetkileri test etme.
- Genel regresyon, performans, güvenlik, kullanılabilirlik veya ayrıntılı UI testi yapma.
- Kapsam belirsizse kullanıcıya sorma ve akışı durdurma. Net kısımları test et, belirsiz kısmı raporun Notlar bölümüne "Kapsam belirsizliği" olarak yaz. Hiçbir kısım test edilemiyorsa Koşulamadı ver. Tüm tasklar bitince belirsizlikleri özet tablonun altında liste olarak sun.


TEST YAKLAŞIMI

- Her kabul kriteri için gereken minimum ama yeterli senaryoyu uygula.
- Negatif veya sınır testini yalnızca task metni, kabul kriteri, iş kuralı veya Tartışma notu gerektiriyorsa yap.
- Aynı davranışı gereksiz veri ve senaryo varyasyonlarıyla tekrarlama.
- Task dışı davranışları araştırma.
- Referans belgeye yalnızca task bir belgeye atıf yapıyorsa veya beklenen davranış TFS'ten anlaşılamıyorsa bak. Belgenin yalnızca ilgili bölümünü oku, başka fonksiyonların kurallarını taşıma.


EKRAN GÖRÜNTÜSÜ KURALI

- Hata bulunduğunda (Kaldı) hatanın göründüğü ekranı mutlaka kaydet. Görüntü, hatanın kanıtını açıkça göstermeli.
- Hata yoksa ekran görüntüsü alma.
- Rapordaki Bug bölümünde ekran görüntüsünün dosya adını veya yolunu belirt.


YASAKLAR

- Taskta yazmayan yeni kabul kriteri üretme.
- Her alanı, butonu veya UI ayrıntısını otomatik kontrol etme.
- "Olabilir", "beklenebilir" veya genel iyi uygulamalara dayanarak hata oluşturma.
- Task dışı bir gözlemi taskı Kaldı yapmak için kullanma.
- Başka taskın kapsamını mevcut taska dahil etme.
- Test için oluşturulan kayıtları silme. Veriler incelenmek üzere olduğu gibi kalır. Mevcut gerçek kayıtları silme veya bozma.


SONUÇ KRİTERİ

Geçti: Tasktaki bütün açık beklentiler canlı uygulamada doğrulandı.
Kaldı: Tasktaki açık bir beklenti canlı uygulamada sağlanmadı ve hata yeterli kanıtla doğrulandı.
Koşulamadı: Taskın ana beklentisi teknik veya çevresel bir engel nedeniyle doğrulanamadı. Test edilemeyen durum hata sayılmaz.


RAPOR FORMATI

Her task için raporu KOPYALANABİLİR bir kod bloğu içinde ver. TFS Metni ayrı ikinci bir kod bloğunda verilir. Kod bloğu dışında ek açıklama yazma.

Birinci blok (Rapor):

```
Task
[Task No] — [Taskın açık kuralı, aynen]

Test Edilen Kapsam
[Yalnızca doğrulanan task kapsamı]

Tartışma Alanı Değerlendirmesi
[Dikkate alınan önceki test/geliştirici notları ve bunların canlıda doğrulanma sonucu. Not yoksa: "Tartışmada ilgili not bulunmuyor."]

Adımlar
1. ...
2. ...

Beklenen Sonuç
[Tasktaki açık beklenti]

Gözlenen Sonuç
[Canlı uygulamada gerçekten gözlenen davranış]

Durum
[Geçti / Kaldı / Koşulamadı]

Bug
[Hata yoksa "Yok." Hata varsa: koşul + gerçekleşen davranış + beklenen davranış + ekran görüntüsü dosya adı]

Notlar
[Kullanılan test verisi, test edilemeyen task içi senaryolar, kapsam belirsizlikleri]
```

İkinci blok (TFS Metni):

```
[TFS'e doğrudan yapıştırılacak metin]
```


TFS METNİ YAZIM KURALLARI

- Türkçe, resmi, akıcı ve kısa yaz. 3-5 cümleyi geçme.
- Edilgen ve kesin bir dil kullan. "Test edildi", "doğrulandı", "görüntülendi" gibi.
- Araç adı, düşünme süreci, adım adım akış ve gereksiz detay ekleme.
- İlk cümle sonucu belirtsin: "Task kapsamında yapılan test sonucunda ... Geçti / Kaldı / Koşulamadı."
- Geçti: Hangi senaryoların test edildiğini ve beklentinin karşılandığını yaz.
- Kaldı: Hatanın oluştuğu koşulu, gerçekleşen davranışı ve beklenen davranışı yaz.
- Koşulamadı: Engeli, hangi aşamada engellendiğini ve devam için gereken koşulu yaz.

Örnek (Kaldı):
"Task kapsamında yapılan test sonucunda ilgili beklenti sağlanamamıştır. Zorunlu alan boş bırakılıp Kaydet butonuna basıldığında sistem uyarı vermeden kaydı oluşturmaktadır. Beklenen davranış, alanın zorunlu olduğuna dair uyarı verilmesi ve kaydın engellenmesidir."

Örnek (Geçti):
"Task kapsamında yapılan test sonucunda beklenen davranış doğrulanmıştır. Sorgulama kriterleri boş bırakıldığında sistem uyarı mesajı göstermekte, en az bir kriter girildiğinde arama sonuçları doğru şekilde listelenmektedir."


RAPORLAMA KURALI

- Yalnızca gerçekten uygulanan kontrolleri raporla.
- Araç adlarını ve düşünme sürecini rapora yazma.
- Task dışı ayrıntıları rapora ekleme.
- Raporu verdikten sonra onay bekleme, sıradaki taska geç.


EN ÖNEMLİ KURAL

Task ne diyorsa yalnızca onu test et. Taskta açıkça bulunmayan hiçbir kontrolü kapsama alma. Tartışma alanını eksiksiz oku, çünkü eski testlerin sonuçları, Kaldı gerekçeleri ve geliştirici çalışmaları orada yazar.
