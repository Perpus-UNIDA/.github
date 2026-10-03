# Perpustakaan UNIDA Gontor

Sistem perpustakaan Universitas Darussalam Monadun Indonesia, Gontor.
Portal: <https://library.unida.gontor.ac.id>

## Repo aktif

| Repo | Isi | Dipakai untuk apa |
|---|---|---|
| [`Unida-Library`](Unida-Library) | Laravel 12, Filament v3, Livewire 3 | Otak sistem: admin `/control`, portal staff `/staff`, member `/member`, OPAC `/`, mobile API `/api/v1` |
| [`repo-unida`](repo-unida) | EPrints 3.3 fork | Institutional Repository (skripsi, jurnal,RIER) |
| [`unida-library-mobile`](unida-library-mobile) | Flutter | Aplikasi untuk mahasiswa |

## Repo ter-archive

Repo di bawah ini **read-only**. Jangan mulai projek baru di sana.

| Repo | Digantikan oleh |
|---|---|
| [`ILMS`](ILMS) | `Unida-Library` |
| [`digilib`](digilib) | `Unida-Library` (fitur `Ebook`, `Ethesis`) |
| [`UCS-Library`](UCS-Library) | Tidak ada. Katalog union antar kampus, read-only. |
| [`e-libsensi`](e-libsensi) | Tidak perlu. Absensi sudah ada di `Unida-Library`. |

## Cara kerja antar sistem

```
                 unida-library-mobile (Flutter)
                              |
                              v  HTTPS + Sanctum
   ┌──────────────────────────────────────────────────────┐
   │  Unida-Library  (laravel, DB utama)                 │
   │  /staff  /member  /control  /  (OPAC)  /api/v1      │
   └───────┬───────────────────────────┬──────────────────┘
           | EPrints REST + OAI-PMH     | Export/import berkala
           v                           v
   repo-unida (EPrints)          UCS / katalog antar kampus
```

Dokumentasi lengkap (peta spokes, pemilik secret, Failure mode):
[`Unida-Library/docs/ARSITEKTUR-LINTAS-SISTEM.md`](Unida-Library/blob/develop/docs/ARSITEKTUR-LINTAS-SISTEM.md)

## Kontribusi

- Kontribusi hanya lewat branch + PR, jangan pernah langsung ke `staging`/`production`.
- `Unida-Library` punya `AGENTS.md` dan `CONTRIBUTING.md` - baca dulu.
- Jalankan `./vendor/bin/pint` dan `php artisan test` sebelum push.

## Kontak

Pertanyaan operasional: tim perpustakaan UNIDA Gontor, lewat issue tracker `Unida-Library`.