# architect.md — Excel → CSV Bölücü (Jinja2) Mimari Referansı

Bu dosya projenin yapısının hızlı-referans özetidir. Kod değiştikçe güncel tutun.

## Genel Bakış

Excel dosyasındaki **2 sütunlu** veriyi okur; her biri en fazla **99 satır** içeren ayrı CSV dosyalarına dışa aktarır. CSV çıktısı [Jinja2](https://jinja.palletsprojects.com/) şablonuyla üretilir.

## Teknoloji Yığını

- pandas
- openpyxl
- Python

## Dizin Yapısı

```
README.md
excel_to_csv.zip
main.py
ornek_veri.xlsx
output/
  ornek_veri_parca_001.csv
requirements.txt
templates/
  csv_template.j2
```

## Modüller / Kaynak Dosyalar

- `main.py` — Excel → CSV Bölücü (Jinja2 Tabanlı) — Büyük Dosya Sürümü

## Giriş Noktaları ve Yapılandırma

- `main.py`
- `requirements.txt`

## Dağıtım / Çalışma Ortamı

- GitHub: https://github.com/SHapeloglu/excel_to_csv

## Diğer Dokümanlar

- `README.md`

## Mimari Kararlar

_Önemli tasarım kararlarını ve gerekçelerini buraya ekleyin (ör. "X yerine Y seçildi çünkü ...")._
