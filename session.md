# session.md — Excel → CSV Bölücü (Jinja2) Oturum Günlüğü

Her çalışma oturumunda buraya kısa bir kayıt düşülür: ne yapıldı, hangi kararlar alındı, sıradaki adım ne. Amaç, bir sonraki oturuma (veya başka bir geliştiriciye/Claude örneğine) hızlıca bağlam aktarmak.

---

## Şablon

```markdown
## YYYY-AA-GG

**Yapılanlar:**
- ...

**Alınan kararlar / neden:**
- ...

**Açık sorunlar / bilinen eksikler:**
- ...

**Sıradaki adım:**
- ...
```

---

## 2026-10-05

**Yapılanlar:**
- Eksik proje çalışma dosyaları oluşturuldu: `architect.md`, `backlog.md`, `CLAUDE.md`, `session.md`, `task.md`.
- İçerik; README, dosya yapısı, bağımlılık dosyaları ve git geçmişinden çıkarıldı.

**Açık sorunlar / bilinen eksikler:**
- Repo kökünde `.gitignore` yok — `venv/`, `__pycache__/`, `.env`, build çıktıları için eklenmeli.
- Otomatik test bulunamadı — kritik akışlar için en azından duman (smoke) testleri eklenmeli.

**Sıradaki adım:**
- `CLAUDE.md` ve `architect.md` içeriğini gözden geçirip proje sahibinin bilgisiyle tamamla.

### Bu tarihten önceki son commit'ler (referans)

- 2026-05-03 — Add files via upload
- 2026-05-03 — Create ornek_veri_parca_001.csv
- 2026-05-03 — Add files via upload
- 2026-05-03 — Create csv_template.j2
- 2026-05-03 — Add files via upload
- 2026-05-03 — Add files via upload
