# architect.md — Excel → CSV Bölücü Mimarisi

```
main.py excel [-o OUT] [-n ROWS=99] [-w WORKERS=min(8, 2×CPU)]
  │
  ├─ count_nonempty_rows()      1. geçiş: boş olmayan satır sayısı → parça sayısı
  ├─ iter_excel_rows()          2. geçiş: read_only generator, başlık = 2 sütun kontrolü, boş satırları atla
  ├─ ROWS satırlık gruplar → task {template, columns, rows, path}
  ├─ flush_tasks()              ThreadPoolExecutor ile render_and_write (Jinja2 → write_text utf-8)
  └─ ProgressBar                dosya bazında ilerleme + ETA
```

## Dosyalar

| Dosya | Rol |
|---|---|
| `main.py` | Tüm mantık (`ProgressBar`, `iter_excel_rows`, `count_nonempty_rows`, `render_and_write`, `flush_tasks`, `export`, argparse) |
| `templates/csv_template.j2` | Başlık + satırlar, `,` ile birleştirme |
| `ornek_veri.xlsx`, `output/ornek_veri_parca_001.csv` | Örnek girdi/çıktı |
| `excel_to_csv.zip` | 2026-04-18 tarihli eski paket (kaynakların kopyası) |

## Mimari Kararlar

- **İki geçişli okuma**: toplam satırı bilip ilerleme çubuğu ve parça sayısı göstermek için; bedeli dosyayı iki kez okumak.
- **Jinja2 ile CSV**: çıktı formatını kod değiştirmeden şablonla özelleştirebilmek için (ör. farklı ayraç/başlık).
- **99 satır varsayılanı**: hedef doğrulama servisinin yükleme limitine göre.
