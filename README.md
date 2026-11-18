# linkaro-jakt

Källkoden till **[jakt.linkaro.se](https://jakt.linkaro.se)**, en enkel sida för Linkaro Jakt, ett verksamhetsområde inom Linkaro AB.

Det här är en **tillfällig platshållare** för en kommande fullständig webbplats. Sidan är medvetet lågmäld:

- Den länkas inte från linkaro.se.
- Alla sidor har `<meta name="robots" content="noindex">`. `robots.txt` tillåter ändå genomsökning, annars kan sökmotorerna inte se `noindex`. Det finns ingen sitemap ännu.
- Webbplatsen är ren statisk HTML och CSS, utan JavaScript, cookies, statistik eller spårning. Typsnitt och logotyper ligger lokalt, så sidan gör inga anrop till andra servrar.

> Innehåll, logotyp och design är skyddade av upphovsrätt (© Linkaro AB). Repot har därför ingen licensfil. Typsnitten har egna licenser (SIL Open Font License), se `assets/fonts/`.

## Förhandsgranska

Sökvägarna utgår från webbplatsens rot (`/assets/…`), så sidan behöver serveras från repots rot. Att öppna `index.html` direkt i webbläsaren fungerar inte.

```bash
python3 -m http.server 8000
```

Öppna sedan http://localhost:8000 och http://localhost:8000/404.html.

## Struktur

```
index.html            Startsidan
404.html              Felsida (GitHub Pages visar den för adresser som inte finns)
assets/css/site.css   Stilmall. Accentfärgen (#9DBA6A) är variabeln --accent
assets/fonts/         Outfit och Atkinson Hyperlegible Next (woff2) med licenser
assets/img/           Logotyper för mörk bakgrund och Open Graph-bild (og-image.png)
favicon.svg           Favicon: Linkaro-symbolen i accentfärgen
favicon.ico           Favicon för äldre webbläsare
apple-touch-icon.png  Ikon för hemskärmen på iOS
CNAME                 Egen domän för GitHub Pages (jakt.linkaro.se)
.nojekyll             Stänger av Jekyll på GitHub Pages
robots.txt            Tillåter genomsökning (noindex sköts i HTML)
```

## Publicering

GitHub Pages publicerar grenen `main` från rotmappen. Domänen anges i `CNAME`. DNS hanteras i Cloudflare och e-postadressen jakt@linkaro.se hanteras utanför det här repot.

## Mallen synkas inte automatiskt

Webbplatsen skapades från [linkaro-subsite-template](https://github.com/linkaro-ab/linkaro-subsite-template), tillsammans med linkaro-enduro, linkaro-tech och linkaro-jakt. **Mallen synkas inte automatiskt.** En gemensam ändring (stilmall, sidfot, typsnitt, logotyper, 404-sidan) måste därför göras i mallen och sedan föras över till vart och ett av de tre repona.

Det enklaste sättet är att ändra i mallen och köra dess skript, som skriver om mallens filer i det här repot:

```bash
cd ../linkaro-subsite-template/verktyg
npm install
node skapa.mjs jakt
```

Texter, accentfärg och e-post för varje webbplats finns i mallens `verktyg/webbplatser.json`. Det går också bra att redigera filerna här direkt, men då försvinner ändringen nästa gång skriptet körs, om den inte också görs i mallen.
