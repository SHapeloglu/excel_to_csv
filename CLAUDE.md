# CLAUDE.md

Bu dosya, bu proje üzerinde çalışırken Claude'un (Claude Code dahil) izlemesi gereken bağlamı ve kuralları içerir.

## Proje

**Excel → CSV Bölücü (Jinja2)** — Excel dosyasındaki **2 sütunlu** veriyi okur; her biri en fazla **99 satır** içeren ayrı CSV dosyalarına dışa aktarır. CSV çıktısı [Jinja2](https://jinja.palletsprojects.com/) şablonuyla üretilir.

- GitHub: https://github.com/SHapeloglu/excel_to_csv

## Teknoloji Yığını

- pandas
- openpyxl
- Python

## Önemli Dosyalar

- `main.py`
- `requirements.txt`

Mimari ayrıntılar için bkz. `architect.md`.

## Sık Kullanılan Komutlar

```bash
python3 -m venv venv && . venv/bin/activate && pip install -r requirements.txt
python main.py
```

## Kurallar

- `.env`, parola, token ve API anahtarlarını asla commit etme.
- Her çalışma oturumunun sonunda `session.md`ye kısa kayıt düş; görev durumunu `task.md`de güncelle.
- Önceliklendirilmemiş fikirleri `backlog.md`ye yaz; somutlaşınca `task.md`ye taşı.

## Çalışma Dosyaları

| Dosya | Amaç |
|---|---|
| `architect.md` | Mimari ve dizin yapısı referansı |
| `task.md` | Aktif / devam eden / tamamlanan görevler |
| `backlog.md` | Önceliklendirilmemiş fikir ve teknik borç havuzu |
| `session.md` | Oturum günlüğü — her oturum sonunda güncellenir |
