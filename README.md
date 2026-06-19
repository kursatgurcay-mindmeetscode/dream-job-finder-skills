# Dream Job Finder — Claude Skills

**Author:** Kursat GURCAY  

CV uyarlama ve otomatik başvuru dahil, iş arama sürecini uçtan uca otomatize eden 5 Claude skill.

---

## Tam İş Akışı

```
Skill 1: Kariyer Kriter Anketi
        ↓  dream-job-criteria.md
Skill 2: Puanlama Metodolojisi
        ↓  company-scoring-methodology.md
Skill 3: Şirket Araştırması & Sıralama
        ↓  Puanı 70+ olan şirketler + açık roller
Skill 4: CV Uyarlama (her rol için)
        ↓  cv-[şirket]-[rol].md
Skill 5: Otomatik Başvuru
        ↓  application-log.md
```

---

## Skills

### Skill 1 — `dream-job-criteria`
Claude kariyer koçu rolüne girerek 10–15 derin soru sorar. Muğlak cevapları reddeder ("destekleyici bir yönetici istiyorum" gibi), gerçek örnekler üzerinden detaylandırmanızı ister.

**Çıktı:** `dream-job-criteria.md` — 15–20 adet önceliklendirilmiş, detaylı kriter

---

### Skill 2 — `dream-job-scoring`
Kriterlerinizi ağırlıklı bir 0–100 puanlama rubriğine dönüştürür. Her kategori için kanıt kaynakları ve eşik değerleri tanımlar.

**Çıktı:** `company-scoring-methodology.md`

---

### Skill 3 — `dream-job-finder`
Web araması yaparak Greenhouse, Lever, Ashby, LinkedIn, Built In ve Wellfound'da açık pozisyonları tarar. Her şirketi puanlar, 70+ olanları getirir. Feedback'inizi `decision-log.md`'ye kaydederek gelecek aramalarda daha iyi sonuçlar üretir.

**Çıktı:** Şirket adı, puan, karşılanan/karşılanmayan kriterler, iş linkleri

---

### Skill 4 — `dream-job-resume-tailor`
Her iş ilanı için CV'nizi kişiselleştirir. İlanın anahtar kelimelerini, ATS gereksinimlerini ve şirketin tonunu analiz ederek mevcut deneyiminizi öne çıkarır — hiçbir şey uydurmadan.

**Çıktı:** `cv-[şirket]-[rol].md` + ATS anahtar kelime raporu + kapak mektubu notları

---

### Skill 5 — `dream-job-apply`
Claude in Chrome ile Greenhouse, Lever ve Ashby formlarını otomatik olarak doldurur ve gönderir. Her başvuruyu `application-log.md`'ye kaydeder, follow-up tarihini hatırlatır. Göndermeden önce her zaman onayınızı alır.

**Çıktı:** `application-log.md` — tüm başvuruların kaydı

---

## Kurulum

### Claude Code (Önerilen)

```bash
# Skill dosyalarını kopyala
cp skills/*.md ~/.claude/skills/

# Boş log dosyalarını oluştur (Skill 3 ve 5 için)
touch ~/your-cowork-folder/decision-log.md
touch ~/your-cowork-folder/application-log.md
```

Sırayla çalıştır:
```
/dream-job-criteria
/dream-job-scoring
/dream-job-finder
/dream-job-resume-tailor
/dream-job-apply
```

### Claude Cowork (Manuel)

1. `skills/` klasöründeki `.md` dosyalarını Cowork klasörünüze kopyalayın
2. Her skill'in içeriğini Claude.ai sohbetine yapıştırın
3. Skill 5 için Claude in Chrome eklentisinin kurulu olduğundan emin olun

---

## Gereksinimler

| Gereksinim | Skill |
|---|---|
| Claude.ai hesabı | 1, 2 |
| Claude Cowork + web araması | 3 |
| Claude Code | 4 |
| Claude Code + Claude in Chrome MCP | 5 |

---

## Dosya Yapısı

```
dream-job-finder-skills/
├── README.md
└── skills/
    ├── dream-job-criteria.md        ← Skill 1
    ├── dream-job-scoring.md         ← Skill 2
    ├── dream-job-finder.md          ← Skill 3
    ├── dream-job-resume-tailor.md   ← Skill 4
    └── dream-job-apply.md           ← Skill 5
```

**Çalışma zamanında oluşan dosyalar (Cowork klasörünüzde):**
```
dream-job-criteria.md
company-scoring-methodology.md
decision-log.md
cv-[şirket]-[rol].md   (her başvuru için ayrı)
application-log.md
```

---

## Lisans

MIT — özgürce kullanın, uyarlayın, paylaşın.
