# Dream Job Auto Apply

**Author:** Kursat GURCAY  
**Category:** Career / Job Search  
**Tool:** Claude Code (Claude in Chrome MCP gerekli)  
**Prerequisites:**
- `dream-job-resume-tailor` skill çalıştırılmış ve uyarlanmış CV hazır
- CV dosyası PDF olarak export edilmiş (tarayıcıya yüklenecek)
- `application-log.md` — Cowork klasöründe mevcut olmalı (boş başlayabilir)

## Purpose

Greenhouse, Lever veya Ashby üzerindeki iş başvuru formlarını otomatik olarak doldurup gönder. Her başvuruyu `application-log.md` dosyasına kaydet.

## ⚠️ Önemli Uyarılar

- Başvuru göndermeden önce formu kullanıcıya onaylat
- Kişisel bilgileri (telefon, adres, maaş beklentisi) kullanıcıdan al — asla tahmin etme
- "Easy Apply" veya tek tıklık başvurularda bile formu göster, onay al
- LinkedIn profilini veya portfolyo URL'sini kullanıcıdan iste

## Instructions for Claude

### Step 0 — Kullanıcıdan Bilgi Al (Her Oturumda Bir Kez)

İlk çalıştırmada şunları sor:

```
Başvurular için aşağıdaki bilgilere ihtiyacım var:
1. Ad Soyad:
2. E-posta:
3. Telefon:
4. LinkedIn URL:
5. Portfolyo / GitHub / kişisel site (varsa):
6. Şehir / Konum:
7. Maaş beklentisi (sorulursa kullanılacak):
8. PDF CV dosya yolu (bilgisayarda nerede):
9. İş yetkisi durumu (ör. Vatandaş, Vize sahibi, Sponsorluk gerekli):
```

Bu bilgileri oturum boyunca sakla, her başvuruda yeniden sorma.

### Step 1 — Başvuru URL'sini Al

Kullanıcı `dream-job-finder` çıktısından bir rol linki verecek.

Linkin hangi platforma ait olduğunu belirle:
- `boards.greenhouse.io` → Greenhouse akışı
- `jobs.lever.co` → Lever akışı
- `jobs.ashbyhq.com` → Ashby akışı
- Diğer → genel form akışı

### Step 2 — Sayfayı Aç ve Analiz Et

```
1. Chrome'da başvuru URL'sini aç
2. Sayfanın ekran görüntüsünü al
3. Formdaki tüm alanları listele:
   - Zorunlu alanlar (*)
   - Opsiyonel alanlar
   - Dosya yükleme alanları
   - Dropdown / çoktan seçmeli alanlar
4. Kullanıcıya form özetini göster
```

### Step 3 — Formu Doldur

Her alan için şu mantığı uygula:

| Alan Türü | Kaynak |
|---|---|
| Ad, E-posta, Telefon, Konum | Step 0'dan alınan bilgiler |
| CV yükleme | Kullanıcının belirttiği PDF dosyası |
| Cover letter (varsa) | `dream-job-resume-tailor` çıktısındaki notlardan üret |
| "Neden bu şirket?" sorusu | `dream-job-criteria.md` ve şirket araştırmasından üret |
| Maaş beklentisi | Kullanıcının verdiği rakam |
| İş yetkisi | Kullanıcının verdiği bilgi |
| LinkedIn, portfolyo | Kullanıcının verdiği URL'ler |
| Teknik sorular | Kullanıcıya sor, tahmin etme |

### Step 4 — Onay Al

Formu doldurmadan önce kullanıcıya şunu göster:

```
📋 BAŞVURU ÖNİZLEME
Şirket: [Şirket Adı]
Rol: [Rol Başlığı]
Platform: [Greenhouse / Lever / Ashby]

Doldurulan alanlar:
- Ad Soyad: [değer]
- E-posta: [değer]
- CV: [dosya adı]
- Cover Letter: [İlk 100 karakter...]
- [diğer alanlar]

Göndermemi onaylıyor musunuz? (Evet / Hayır / Düzenle)
```

Onay gelmeden formu gönderme.

### Step 5 — Gönder ve Kaydet

Onay sonrası:
1. "Submit" / "Apply" butonuna tıkla
2. Onay sayfasının ekran görüntüsünü al
3. `application-log.md` dosyasını güncelle

### Application Log Formatı

`application-log.md` dosyasına her başvurudan sonra ekle:

```markdown
## [Tarih] — [Şirket Adı]

- **Rol:** [Rol Başlığı]
- **Platform:** Greenhouse / Lever / Ashby
- **Başvuru Linki:** [URL]
- **Match Score:** [dream-job-finder'dan gelen puan]
- **CV Versiyonu:** [cv-şirket-rol.md]
- **Durum:** Gönderildi ✅
- **Follow-up Tarihi:** [Başvurudan 7 gün sonra]
- **Notlar:** [Varsa]
```

### Step 6 — Sonraki Adım

Her başvurudan sonra:
1. Kullanıcıya başvurunun tamamlandığını bildir
2. "Sıradaki şirketin başvurusuna geçeyim mi?" diye sor
3. Devam edilirse aynı adımları tekrar uygula

## Desteklenen Platformlar

| Platform | Destek Düzeyi |
|---|---|
| Greenhouse | Tam otomatik |
| Lever | Tam otomatik |
| Ashby | Tam otomatik |
| LinkedIn Easy Apply | Tam otomatik |
| Workday | Kısmi (bazı adımlar manuel) |
| Diğer | En iyi çaba, onay gerekli |

## Hata Durumları

- **CAPTCHA:** Kullanıcıya devret, manuel tamamlamasını iste
- **Zorunlu alan eksik:** Kullanıcıdan bilgiyi iste, tahmin etme
- **Dosya yükleme hatası:** Alternatif format (PDF → DOCX) öner
- **Sayfa yüklenmiyor:** 30 saniye bekle, yenile, hala olmuyorsa kullanıcıya bildir
