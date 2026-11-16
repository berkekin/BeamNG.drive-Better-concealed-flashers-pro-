# Better Concealed Flashers PRO 3

**BeamNG.drive'da her araca gizli polis çakarı: aracı yapanın koyacağı yerlere kendiliğinden yerleşir.**

[English](README.md) · BeamNG.drive 0.40+ · Türkçe ve İngilizce arayüz

![Yerleşim sekmesi](docs/img/ui_tr_zone.png)

LED başlıkları ön camın arkasına, panjurun içine ya da tampon boyunca gizlemek normalde her araç için bir saat
konum oynamak demek. Bu mod o işi senin yerine yapıyor. Uygulamayı aç, araç haritasında bir bölgeye tıkla; çakarlar
olması gereken yere oturur: camın üst kenarının hemen altına, panjurla aynı hizaya, lamba gövdelerinin içine, plakanın
yanına. Oyunun kendi araçlarında da modlu araçlarda da çalışır, Automation'dan aktarılan araçlar dahil.

## Öne çıkanlar

- **Bölge başına tek tık.** 16 bölge ve serbest konum: ön cam, torpido, panjur, ön ve arka tampon, kaput, far ve stop
  içi (hideaway), aynalar, ön çamurluklar, marşpiyeller, arka yan camlar, arka cam, arka raf, bagaj ve tavan.
- **Önce fabrika konumları.** Araçta ya da araca uyan bir parçada zaten gizli çakar varsa mod onların konumunu ve
  aralığını aynen kullanır. Aracı yapanın seçtiği yerleşimin aynısı olur.
- **Diğer her yerde gerçek yüzey.** Aracın 3B modeli taranır, her başlık gerçek yüzeye oturtulur: cama, panjura,
  tampona ya da lambaya.
- **Fabrika parçası gibi montaj.** Başlıklar oturdukları gövde parçalarına bağlanır, önündeki cam kırılınca söner.
  Titremez, araca fazladan fizik düğümü eklemez.
- **Hızlı başlangıç için kitler:** Sivil ekip, Tam donanım, Sadece ön, Sadece arka, İç lightbar (slicktop), Hideaway
  ve Trafik oku; 10 renk şeması. İstersen seçtiğin kit bindiğin her araca kendiliğinden uygulanır.
- **Gerçekçi ışık.** Gerçek ölçülü altı başlık tipi. Parlaklık hazır seviyelerden ya da doğrudan kandela, lümen veya
  belirli mesafede lüks olarak ayarlanır; ölçek oyunun kendi ışık parçalarıyla aynı. Her birinin üç tonu olan altı
  LED rengi (ör. kırmızı 625 nm, polis mavisi 470 nm, beyaz 6000 K) ve bölge başına isteğe bağlı ikinci renk:
  takedown, sahne, dönüşümlü, trafik oku ya da seyir.
- **Desenler.** 31 mod, bölge başına 21 desen, A/B faz grupları, faz kayması, bölge başına seviye ve sıralı trafik oku.
- **Hızlı düzenleme.** Renk, ton, parlaklık ve desen değişiklikleri araç yeniden yüklenmeden anında uygulanır.
  Konum ve adet değişikliklerinde önce araç üzerinde tel kutu önizlemesi görünür, sonra araç bir kez yüklenir.
- **Ayrıca:** multicolor hoparlörlü LED bar (116 / 139 / 161 cm), araçtaki ya da başka modlardaki tepe lambalarından
  kopya, araçtaki tüm uyarı ışıkları için Işık Stüdyosu, araca özel ve genel profiller, çakışan fabrika çakarlarını
  gizleme seçeneği, radyal menü girişi ve tuş atamaları.

![Işık ve Profil sekmeleri](docs/img/ui_en_light_profiles.png)

Automation'dan aktarılmış bir mod araçta otomatik yerleşim:

![Mod araçta yerleşim](docs/img/placement_mod_vehicle.jpg)

## Kurulum

1. **Releases** bölümünden `better_concealed_flashers_pro.zip` dosyasını indir.
2. Zip'i **açmadan** `%LOCALAPPDATA%\BeamNG\BeamNG.drive\current\mods\` klasörüne koy.
3. Oyunu başlat ve **Concealed Flashers PRO · Gizli Çakar PRO** arayüz uygulamasını ekle (UI Apps → Add app).

## Hızlı kullanım

1. Herhangi bir otomobile ya da kamyona bin.
2. Yerleşim sekmesinde bir **kit** ve **renk şeması** seç ya da haritada tek bir bölgeye tıkla.
3. İnce ayar için yanan bir bölgeye tıkla: adet, aralık, başlık tipi, renkler, parlaklık, desen ve konum.
4. Işıkları uygulamanın üst şeridindeki **ÇAKAR** / **SİREN** düğmeleriyle ya da oyunun lightbar tuşuyla yak.
   Modlar arasında ◀ ▶ ile geçiş yap.
5. Ayarları korumak için Araç Ayarları'ndan konfigürasyonu kaydet; çakarlar konfigürasyonun içinde saklanır.

Dil için uygulamanın üst şeridindeki **TR / EN** düğmesini kullan. Varsayılan dil oyunun diliyle aynıdır.

Örnek konfigürasyonlar: *Lansdale* ve *Fullsize* → "Undercover — Concealed Flashers PRO", *Fullsize* → "LED bar —
Concealed Flashers PRO".

Sürüm 2'den geçiş: eski ayarlar kendiliğinden dönüştürülür. Başlıklar artık gerçek yüzeye yerleştiği için ince ayar
kaydırmaları sıfırlanır.

## Uyumluluk

- BeamNG.drive 0.40 ya da daha yeni.
- Oyunun 39 aracının tamamında (584 bölge yerleşti, hata yok) ve Automation aktarımları dahil birkaç mod araçta denendi.
- Bir araçta bulunmayan bölge (ör. ATV'de arka cam) yanlış bir yere konmaz, haritada soluk görünür.

## Geliştiriciler için

```
python3 tools/build.py          # dist/better_concealed_flashers_pro.zip dosyasını üretir
python3 tools/gen_assets.py     # vehicles/common/bcfp_pro içindeki başlık modellerini ve materyalleri yeniden üretir

pip install lupa
export BEAMNG_GAME="/oyunun/kurulu/oldugu/klasor"
python3 tools/bench/eng.py tests/t_full.lua lansdale:25_base_A
python3 tools/bench/eng.py tests/t_ui.lua lansdale
python3 tools/bench/eng.py tests/t_batch.lua $(cat tools/bench/cars.txt)
```

Test tezgahı oyunun kendi jbeam yükleyicisini oyun dışında, mod eklenmiş halde çalıştırır; tüm akış oyunu açmadan
denenebilir. Klasör yapısı ve modüllerin açıklaması [İngilizce README](README.md#for-developers) dosyasında.
