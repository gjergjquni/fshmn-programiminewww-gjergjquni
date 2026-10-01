# Java II: Muzeu i sendeve

## Çfarë realizova

Faqe e vetme front-end për ekspozitën *Muzeu i sendeve*: tre sende (çelësi,
filxhani, bileta) me imazhe lokale dhe navigim me `id` (`#celesi`, `#filxhani`,
`#bileta`) që e ndryshon URL-në pa hapur faqe të reja. Të dhënat janë të
sajuara; vetëm HTML dhe CSS.

| Skedari | Përmbajtja |
|---|---|
| `index.html` | Muzeu, kartelat me `id`, lidhjet `#…` |
| `style.css` | Stili (header, kartela, galeria flex) |
| `images/` | `celesi.png`, `filxhani.png`, `bileta.png` |

## Hapat e hapjes

1. Klono repository-n dhe hyr në folderin `JavaII`:

   ```sh
   git clone https://github.com/gjergjquni/fshmn-programiminewww-gjergjquni.git
   cd fshmn-programiminewww-gjergjquni/JavaII
   ```

2. Nis një server lokal (kërkohet Python 3):

   ```sh
   python -m http.server 8000
   ```

3. Hap në shfletues: <http://localhost:8000/index.html>

Alternativë: hap `index.html` me zgjerimin *Live Server* në VS Code / Cursor.

## Para kodimit: hyrjet, daljet dhe rastet

- **Hyrja:** URL-ja ose lidhja me ankorë (`#filxhani`, etj.).
- **Dalja:** i njëjti `index.html`; në adresë shfaqet `#filxhani` (ose `#celesi` / `#bileta`).
- **Rast normal:** klik «Filxhani» → URL bëhet `…/index.html#filxhani`.
- **Rast kufitar 1:** kërkesë për skedar që s'ekziston → serveri kthen `404`.
- **Rast kufitar 2:** ankorë e gabuar `#nuk-ekziston` → faqja nuk thyhet; URL ndryshon, por nuk ka element me atë `id`.

## Testet: hyrje → rezultat i pritur → rezultat i marrë

Testuar me `python -m http.server 8000` në `127.0.0.1`.

| # | Hyrje | Rezultati i pritur | Rezultati i marrë |
|---|---|---|---|
| 1 | `GET /index.html` | `200 OK`, tre kartela | `200 OK` |
| 2 | `GET /images/celesi.png` (dhe dy ikonat e tjera) | `200 OK` | `200 OK` |
| 3 | Klik «Filxhani» në nav | URL: `…#filxhani`, pa faqe të re | OK |
| 4 | Klik «Historia e fshehur» te Çelësi / Bileta | URL: `#celesi` / `#bileta` | OK |
| 5 | `GET /nuk-ekziston.html` | `404 Not Found` | `404 File not found` |
| 6 | Hap `index.html#nuk-ekziston` | faqja ngarkohet; nuk ka target me atë id | OK |

## DevTools → Network

| Fusha | Vlera |
|---|---|
| **URL** | `http://127.0.0.1:8000/index.html` |
| **Metoda** | `GET` |
| **Statusi** | `200 OK` |

Pas dokumentit shfaqen `GET /style.css` dhe tre `GET /images/*.png` me status `200`.
Kliku me `#…` nuk hap kërkesë të re HTTP për faqe tjetër; ndryshon vetëm fragmenti i URL-së.


