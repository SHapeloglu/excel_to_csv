# Excel → CSV Bölücü (Jinja2)

Excel dosyasındaki **2 sütunlu** veriyi okur; her biri en fazla **99 satır** içeren ayrı CSV dosyalarına dışa aktarır. CSV çıktısı [Jinja2](https://jinja.palletsprojects.com/) şablonuyla üretilir.

## Proje Yapısı

```
excel_to_csv/
├── main.py                  # Ana betik
├── requirements.txt         # Bağımlılıklar
├── templates/
│   └── csv_template.j2      # Jinja2 CSV şablonu
└── output/                  # Üretilen CSV'ler buraya düşer
```

## Kurulum

```bash
pip install -r requirements.txt
```

## Kullanım

```bash
# Temel kullanım (varsayılan: 99 satır/dosya, output/ klasörüne yazar)
python main.py ornek_veri.xlsx

# Özel çıktı klasörü
python main.py ornek_veri.xlsx -o /tmp/cikti

# Satır sayısını değiştir
python main.py ornek_veri.xlsx -n 50
```

## Şablonu Özelleştirmek

`templates/csv_template.j2` dosyasını düzenleyerek çıktıyı şekillendirebilirsiniz.

```
{{ columns | join(',') }}
{% for row in rows -%}
{{ row | join(',') }}
{% endfor %}
```

Örnek: Tırnak içine almak istiyorsanız `join('","')` kullanın ve satır başına/sonuna `"` ekleyin.

## Notlar

- Excel dosyasında **tam olarak 2 sütun** olmalıdır; aksi hâlde hata verir.
- Çıktı dosyaları `<excel_adı>_parca_001.csv`, `_002.csv` ... şeklinde adlandırılır.
- Encoding: **UTF-8**
