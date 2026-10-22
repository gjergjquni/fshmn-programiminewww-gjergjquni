# Java V: Festivali që përshtatet në çdo ekran

## Çfarë realizova

Faqe e vetme për programin e një festivali shkencor: menu fleksibile (Flexbox),
gjashtë karta në Grid (1 kolonë nën 600 px, 2 nga 600 deri 899 px, 3 nga 900 px),
imazh lokal fleksibël dhe pa lartësi fikse për tekst. Çdo kartë ka titull,
kategori, orar dhe lidhjen «Detaje» drejt informacionit në fund të faqes.
Të dhënat janë të sajuara; vetëm HTML dhe CSS.

| Skedari | Përmbajtja |
|---|---|
| `index.html` | Menu, imazh, 6 karta, detajet në fund |
| `style.css` | Flexbox (menu), Grid + media queries, imazh fleksibël |
| `images/festival.svg` | Aseti lokal i imazhit |

## Hapat e hapjes

1. Klono repository-n dhe hyr në folderin `JavaV`:

   ```sh
   git clone https://github.com/gjergjquni/fshmn-programiminewww-gjergjquni.git
   cd fshmn-programiminewww-gjergjquni/JavaV
   ```

2. Nis një server lokal (kërkohet Python 3):

   ```sh
   python -m http.server 8000
   ```

3. Hap në shfletues: <http://localhost:8000/index.html>

Alternativë: hap `index.html` me zgjerimin *Live Server* në VS Code / Cursor.

## Para kodimit: hyrjet, daljet dhe rastet

- **Hyrja:** gjerësia e viewport-it (360 / 768 / 1280 px) dhe lidhjet e menusë ose «Detaje».
- **Dalja:** 1, 2 ose 3 kolona kartash; lundrimi te karta ose te detajet në fund.
- **Rast normal:** në 900+ px shfaqen 3 kolona; klik «Detaje» te Robotikë → `#detaje-robotike`.
- **Rast kufitar 1:** titull 100+ karaktere — mbështillet brenda kartës, pa overflow.
- **Rast kufitar 2:** Tab përmes menusë — çdo lidhje merr fokus të dukshëm.

## Testet: hyrje → rezultat i pritur → rezultat i marrë

Testuar me DevTools → Responsive dhe `python -m http.server 8000`.

| # | Hyrje | Rezultati i pritur | Rezultati i marrë |
|---|---|---|---|
| 1 | Viewport **360 px** | 1 kolonë; pa scroll horizontal | 1 kolonë; pa scroll horizontal |
| 2 | Viewport **768 px** | 2 kolona (600–899 px) | 2 kolona |
| 3 | Viewport **1280 px** | 3 kolona (≥ 900 px) | 3 kolona |
| 4 | Tab në menu, pastaj Enter | Fokusi i dukshëm; lëviz te karta | OK |
| 5 | Klik «Detaje» te Robotikë | URL `#detaje-robotike`, teksti i detajeve në fund | OK |
| 6 | Titull 100+ karaktere te Robotikë | Teksti brenda kartës, pa overflow | OK |

### Rastet e pranimit

- [x] Në 360/768/1280 px shfaqen përkatësisht 1/2/3 kolona.
- [x] Nuk ka scroll horizontal në faqen e plotë.
- [x] Menuja mbetet e përdorshme me tastierë.

## DevTools → Network

| Fusha | Vlera |
|---|---|
| **URL** | `http://127.0.0.1:8000/index.html` |
| **Metoda** | `GET` |
| **Statusi** | `200 OK` |

Pas dokumentit shfaqen `GET /style.css` dhe `GET /images/festival.svg` me status `200`.

## Reflektim individual

**Kur do të zgjidhja Flexbox dhe kur Grid?**

Flexbox për menunë: një rresht lidhjesh në një aks, që mbështillet me
`flex-wrap` kur nuk ka vend. Grid për kartat: layout me numër të caktuar
kolonash sipas gjerësisë (1 → 2 → 3), që shprehet drejtpërdrejt me
`grid-template-columns`.

## Deklarim AI / burime

- Ndihmë nga Cursor për HTML/CSS dhe këtë README, sipas kërkesave të
  fletës së ushtrimit.
- Referencë tematike: kap. 6–7 (Flexbox, Grid, media queries).
