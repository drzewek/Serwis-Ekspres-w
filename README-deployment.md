# Wdrożenie — komplet zmian

## Struktura w repozytorium

```
/                         ← root repo
├── index.html            ← ZAKTUALIZOWANY
├── sitemap.xml           ← ZAKTUALIZOWANY (12 URL-i + image refs)
├── ekspres-nie-robi-kawy.html              ← NOWY
├── odkamienianie-ekspresu-poradnik.html    ← NOWY
├── ile-kosztuje-naprawa-ekspresu.html      ← NOWY
└── images/                                  ← NOWY FOLDER
    ├── ekspres-nie-parzy-rutkowski-szczecin.jpg
    ├── zaparzacz-ekspresu-naprawa-warsztat.jpg
    ├── pompa-wibracyjna-ekspresu-zawor.jpg
    ├── bojler-ekspresu-cisnieniowego-kamien.jpg
    ├── serwis-ekspresu-konserwacja-warsztat.jpg
    └── naprawa-ekspresu-philips-saeco-rozkrecony.jpg
```

## Co zostało zmienione w index.html

### 1. Galeria — naprawiona
**Problem:** Ścieżki `img/warsztat-delonghi.jpg` itd. — folder `img/` nie istnieje
w repo, miniatury były martwe.

**Rozwiązanie:** Wszystkie ścieżki przeniesione na `images/*.jpg` z prawdziwymi
zdjęciami z warsztatu. Galeria pokazuje teraz: DeLonghi La Specialista (big),
zaparzacz, Philips Saeco rozkręcony, bojler z kamieniem, pompa wibracyjna.

### 2. Nowa sekcja "Poradniki"
Pod galerią — siatka 4 kart z miniaturami i opisami:
- Ekspres nie robi kawy (diagnostyka)
- Odkamienianie ekspresu (konserwacja)
- Ile kosztuje naprawa ekspresu (cennik)
- Pompa Ulka (technika)

ID sekcji: `#poradniki` — z anchora w nawigacji.

### 3. Menu nawigacji
- Singular "Poradnik" → "Poradniki" wskazujące na `#poradniki`
- Sekcja "O nas" zachowana

### 4. Karty usług — kontekstowe linki
W kartach usług dodane linki do odpowiednich poradników:
- "Diagnostyka i wycena" → cennik napraw
- "Naprawa pompy" → poradnik o pompie Ulka
- "Wymiana bojlera" → diagnostyka „nie parzy"
- "Czyszczenie i odkamienianie" → poradnik odkamieniania

### 5. FAQ — link kontekstowy
W odpowiedzi „Ile kosztuje naprawa" dodany link do pełnego cennika.

### 6. Stopka — rozszerzona
Dodane linki do wszystkich 4 poradników.

### 7. Schema.org — nowy ItemList
Dodany blok `ItemList` z wszystkimi 4 poradnikami w polu `@graph`.
Google rozpozna to jako kategorię artykułów.

### 8. Open Graph image
Dodana referencja do hero image dla głównej strony.

## Co zostało zmienione w sitemap.xml

- **Z 9 → 14 URL-i** (3 nowe poradniki + naprawiony układ)
- **Image references** dodane przy każdym URL z istotnymi zdjęciami
- **Lastmod** zaktualizowane na 2026-04-29
- **Priority** ustawiona racjonalnie: główna 1.0, marki 0.9, poradniki 0.85–0.9

## Kolejność wgrywania (WAŻNE)

```
1. NAJPIERW utwórz /images/ i wrzuć 6 plików .jpg
2. POTEM index.html, sitemap.xml i 3 nowe artykuły HTML
3. Cloudflare Workers podchwyci zmiany automatycznie
```

Jeśli HTML pójdzie pierwszy → Google przy pierwszym crawlu zobaczy 404 na obrazach.

## Po wdrożeniu — checklist

- [ ] Otwórz https://ekspresy.org.pl/ — sprawdź czy galeria pokazuje zdjęcia
- [ ] Scrolluj do sekcji "Poradniki" — sprawdź czy 4 karty się wyświetlają
- [ ] Kliknij każdą kartę poradnika — sprawdź czy artykuły otwierają się
- [ ] Otwórz poszczególne poradniki — sprawdź czy obrazy w treści ładują się
- [ ] Google Search Console → wgraj zaktualizowany sitemap.xml
- [ ] Search Console → "Inspect URL" + "Request indexing" dla 3 nowych URL-i:
  - ekspres-nie-robi-kawy.html
  - odkamienianie-ekspresu-poradnik.html
  - ile-kosztuje-naprawa-ekspresu.html (priorytet — fraza komercyjna)
- [ ] Sprawdź w PageSpeed Insights czy LCP/CLS są w zielonym
- [ ] Test Rich Results Test dla `index.html` — czy ItemList jest rozpoznany

## llms.txt — sugestia uzupełnienia

W llms.txt warto dodać 3 nowe URL-e w sekcji "Poradniki":

```
## Poradniki
- [Ekspres nie robi kawy — diagnostyka](https://ekspresy.org.pl/ekspres-nie-robi-kawy.html)
- [Odkamienianie ekspresu — poradnik](https://ekspresy.org.pl/odkamienianie-ekspresu-poradnik.html)
- [Ile kosztuje naprawa ekspresu — cennik 2026](https://ekspresy.org.pl/ile-kosztuje-naprawa-ekspresu.html)
- [Pompa Ulka w ekspresach do kawy](https://ekspresy.org.pl/pompa-ulka-ekspres-do-kawy.html)
```

To pomoże AI search (ChatGPT, Perplexity) cytować nowe artykuły.
