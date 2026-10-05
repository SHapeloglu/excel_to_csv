# CLAUDE.md — Excel → CSV Bölücü

İki sütunlu (`email | customData`) büyük Excel dosyalarını, her biri en fazla 99 satırlık CSV parçalarına bölen CLI aracı. Amaç: satır limiti olan e-posta doğrulama servislerine yüklenebilir parçalar üretmek (sonuçlar sonra **CSVMerger** ile birleştirilir). openpyxl read-only akış okuma, Jinja2 şablonla CSV üretimi, thread havuzuyla paralel yazma, ETA'lı ilerleme çubuğu.

- GitHub: https://github.com/SHapeloglu/excel_to_csv (2026-05-03)
- Mimari: `architect.md` · Görevler: `task.md` · Fikirler: `backlog.md` · Günlük: `session.md`

## Komutlar

```bash
python3 -m venv venv && . venv/bin/activate && pip install -r requirements.txt
python main.py ornek_veri.xlsx                 # → output/ornek_veri_parca_001.csv …
python main.py veri.xlsx -o /tmp/cikti -n 500 -w 4
```

## Kurallar ve Tuzaklar

- Excel **tam olarak 2 sütun** olmalı (başlık satırına bakılır); değilse `ValueError`.
- **CSV kaçışı yok:** `templates/csv_template.j2` alanları düz `join(',')` ile birleştiriyor; `customData` içinde virgül, tırnak veya satır sonu varsa CSV bozulur. Şablonu değiştirirken bunu düzelt ya da `csv` modülüne geç.
- Dosyalar UTF-8 **BOM'suz** yazılıyor (Excel'de Türkçe karakterler bozuk görünebilir; hedef servis için sorun değil).
- Dosya adı biçimi `<excel_adı>_parca_NNN.csv`; CSVMerger doğal sıralamayla bu sırayı korur — formatı değiştirme.
- `excel_to_csv.zip` ve `output/` içindeki örnek çıktı repoda; gerçek müşteri listesi commit etme.
- Test yok; değişiklikten sonra `python main.py ornek_veri.xlsx -o <geçici klasör>` ile dene.
- Oturum sonunda `session.md`'ye kayıt düş, `task.md`'yi güncelle.
