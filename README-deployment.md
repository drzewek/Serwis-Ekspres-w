# Wdrożenie — wszystko przez folder img/

## Co się zmieniło
Wszystkie ścieżki `images/` zostały zamienione na `img/` we wszystkich plikach.
Używamy istniejącego folderu `img/` w repo — nie trzeba tworzyć nowego.

## Pliki do wgrania

```
/                                                ← root repo
├── index.html                                  ← ZAKTUALIZOWANY
├── sitemap.xml                                 ← ZAKTUALIZOWANY
├── ekspres-nie-robi-kawy.html                  ← NOWY
├── odkamienianie-ekspresu-poradnik.html        ← NOWY
├── ile-kosztuje-naprawa-ekspresu.html          ← NOWY
└── img/                                         ← ISTNIEJĄCY folder
    ├── (Twoje stare pliki — bez zmian)
    │   ├── warsztat-delonghi.jpg
    │   ├── ekspres-nivona-serwis.jpg
    │   ├── diagnostyka-ekspresu-philips.jpg
    │   ├── wnetrze-ekspresu-zabrudzone.jpg
    │   └── plytka-elektroniczna-ekspresu.jpg
    │
    └── (DODAJ tych 6 nowych)
        ├── ekspres-nie-parzy-rutkowski-szczecin.jpg
        ├── zaparzacz-ekspresu-naprawa-warsztat.jpg
        ├── pompa-wibracyjna-ekspresu-zawor.jpg
        ├── bojler-ekspresu-cisnieniowego-kamien.jpg
        ├── serwis-ekspresu-konserwacja-warsztat.jpg
        └── naprawa-ekspresu-philips-saeco-rozkrecony.jpg
```

## Brak konfliktu nazw
Nazwy 6 nowych plików są unikalne — nie nadpiszą Twoich starych.

## Kolejność wdrożenia

1. **Najpierw** wgraj 6 nowych plików .jpg do folderu `img/` w repo
2. **Potem** wgraj 5 plików HTML/XML
3. Odczekaj 30 sekund (Cloudflare Workers przebuduje deployment)
4. Odśwież ekspresy.org.pl — sekcja "Poradniki" pokaże miniaturki

## Po wdrożeniu — checklist

- [ ] Otwórz https://ekspresy.org.pl/ — sekcja Poradniki pokazuje 4 obrazki
- [ ] Otwórz każdy z 3 nowych poradników — sprawdź czy obrazy w treści ładują się
- [ ] Search Console → wgraj zaktualizowany sitemap.xml
- [ ] Search Console → "Inspect URL" + "Request indexing" dla 3 nowych URL-i
