# Dream Job Resume Tailor

**Author:** Kursat GURCAY  
**Category:** Career / Job Search  
**Tool:** Claude.ai veya Claude Code  
**Prerequisites:**
- `dream-job-criteria.md` — Cowork klasöründe mevcut olmalı
- Kullanıcının temel CV'si (plain text veya markdown formatında)

## Purpose

Her iş ilanı için CV'yi akıllıca kişiselleştir. Pozisyonun anahtar kelimelerini, gereksinimlerini ve şirket dilini analiz ederek mevcut CV'yi optimize et — hiçbir şey uydurmadan, yalnızca mevcut deneyimi öne çıkararak.

## Instructions for Claude

Kullanıcı sana şunları verecek:
1. Temel CV (plain text veya markdown)
2. İş ilanı (URL veya yapıştırılmış metin)
3. Şirket adı ve rol başlığı

### Step 1 — İlanı Analiz Et

İş ilanından şunları çıkar:
- **Zorunlu beceriler** (must-have)
- **Tercih edilen beceriler** (nice-to-have)
- **Anahtar kelimeler** (ATS sistemleri için kritik)
- **Şirketin dili ve tonu** (startup mı, kurumsal mu?)
- **Vurgulanan değerler** (hız, ölçek, inovasyon, vb.)
- **Rol için en kritik 3 sorumluluk**

### Step 2 — CV Boşluk Analizi

Mevcut CV ile ilanı karşılaştır:

| Kriter | CV'de Var mı? | Öne Çıkarma Fırsatı |
|---|---|---|
| [Beceri/deneyim] | Evet / Kısmi / Hayır | [Nasıl güçlendirilebilir] |

### Step 3 — CV'yi Uyarla

Aşağıdaki kuralları uygula:

**Özet / Profil Bölümü:**
- İlk 2 satırı bu role özel yeniden yaz
- Şirketin dilinden 2–3 anahtar kelimeyi doğal şekilde dahil et
- Ölçülebilir bir başarı ile aç

**Deneyim Bölümü:**
- En alakalı 3 pozisyonu öne çıkar
- Her maddede şu yapıyı kullan: **[Eylem fiili] + [Ne yaptın] + [Ölçülebilir sonuç]**
- İlanın anahtar kelimelerini maddelerde doğal şekilde geç
- İlgisiz veya zayıf maddeleri kaldır ya da küçült

**Beceriler Bölümü:**
- İlanın zorunlu becerilerini listeye ekle (eğer CV'de karşılığı varsa)
- Şirkete özgü araçları veya platformları öne çıkar

**Genel Kurallar:**
- Hiçbir şey uydurma — yalnızca mevcut deneyimi farklı vurgula
- ATS sistemlerini geçmek için anahtar kelimeleri başlıklarda ve maddelerde kullan
- Uzunluğu 1 sayfa (deneyimli ise 2 sayfa) ile sınırla

### Step 4 — Output

Şunları üret:

1. **Uyarlanmış CV** — markdown formatında, kopyalanmaya hazır
2. **Değişiklik Özeti** — ne değiştirildi ve neden (şeffaflık için)
3. **ATS Anahtar Kelime Raporu** — ilandan alınan kritik kelimeler ve CV'de nerede geçtiği
4. **Kapak Mektubu İçin Notlar** — bir sonraki skill için bu role özel 3–5 vurgu noktası

### Dosya Adlandırma Kuralı

Uyarlanmış CV'yi şu isimle kaydet:
`cv-[şirket-adı]-[rol-başlığı].md`

Örnek: `cv-abridge-senior-marketing-manager.md`
