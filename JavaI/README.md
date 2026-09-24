# Java I: Pasaporta digjitale dhe GitHub

## Çfarë realizova

Pasaporta digjitale e Gjergj Çunit, student i Shkencave Kompjuterike në UP, si kandidat për
udhërrëfyes të kampusit. Të dhënat janë marrë nga CV-ja ime; nga kontakti janë vendosur vetëm
email-i studentor dhe GitHub-i, sepse repository-a është publik.

| Skedari | Përmbajtja |
|---|---|
| `index.html` | `lang="sq"`, `charset`, `viewport`, titull, një `h1`, prezantim, listë me 3 aftësi dhe lidhje relative te `rreth.html` |
| `rreth.html` | Historia ime e shkurtër (studimet, RuajMençur, Erasmus, kërkimi në EEML) dhe lidhja e kthimit te `index.html` |
| `kontakt.html` | Sfida e transferimit: email, GitHub dhe lidhjet e projekteve, e lidhur nga të dyja faqet ekzistuese |
| `style.css` | Stili i përbashkët për të tria faqet |

## Hapat e hapjes

1. Klono repository-n dhe hyr në folderin `JavaI`:

   ```sh
   git clone https://github.com/gjergjquni/fshmn-programiminewww-gjergjquni.git
   cd fshmn-programiminewww-gjergjquni/JavaI
   ```

2. Nis një server lokal (kërkohet Python 3):

   ```sh
   python -m http.server 8000
   ```

3. Hap në shfletues: <http://localhost:8000/index.html>

Alternativë: hap `index.html` me zgjerimin *Live Server* në VS Code / Cursor.

## Para kodimit: hyrjet, daljet dhe rastet

- **Hyrja:** URL-ja që shtyp përdoruesi ose lidhja që klikon.
- **Dalja:** dokumenti HTML që kthen serveri, me status HTTP.
- **Rast normal:** hapet `index.html`, klikohet "Rreth Gjergjit", hapet `rreth.html`.
- **Rast kufitar 1:** kthimi nga `rreth.html` te `index.html`. Lidhja relative duhet të funksionojë nga çdo faqe.
- **Rast kufitar 2:** kërkesë për një skedar që s'ekziston. Serveri duhet të kthejë `404`, jo një faqe boshe.

## Testet: hyrje → rezultat i pritur → rezultat i marrë

Testuar me `python -m http.server 8000` në `127.0.0.1`.

| # | Hyrje | Rezultati i pritur | Rezultati i marrë |
|---|---|---|---|
| 1 | `GET /index.html` | `200 OK`, faqja shfaq h1, prezantimin dhe 3 aftësi | `200 OK` |
| 2 | Klik "Rreth Gjergjit" në `index.html` → `GET /rreth.html` | `200 OK`, shfaqet historia | `200 OK` |
| 3 | Klik "Kthehu te pasaporta" në `rreth.html` → `GET /index.html` | `200 OK`, kthehet te pasaporta | `200 OK` |
| 4 | Klik "Kontakt" nga `index.html` dhe nga `rreth.html` → `GET /kontakt.html` | `200 OK` nga të dyja faqet | `200 OK` |
| 5 | `GET /style.css` | `200 OK`, stili ngarkohet | `200 OK` |
| 6 | `GET /nuk-ekziston.html` (rast kufitar) | `404 Not Found` | `404 File not found` |

Të gjitha lidhjet vajtje/kthim funksionojnë; asnjë lidhje nuk jep 404.

## DevTools → Network

Dokumenti i hapur përmes serverit lokal (rreshti i parë në panelin *Network*):

| Fusha | Vlera |
|---|---|
| **URL** | `http://127.0.0.1:8000/index.html` |
| **Metoda** | `GET` |
| **Statusi** | `200 OK` |

Pas dokumentit shfaqet edhe një kërkesë `GET http://127.0.0.1:8000/style.css` me status `200`, sepse
shfletuesi e lexon `<link rel="stylesheet">` dhe kërkon stilin veçmas.

## Reflektim individual

**Cili ndryshim është ruajtur lokalisht por ende nuk shihet në GitHub?**

Çdo ndryshim që është bërë `git commit` por jo ende `git push`. Në këtë detyrë, pas komandës
`git commit -m "JavaI: realizimi dhe testet"`, skedarët `index.html`, `rreth.html`, `kontakt.html`,
`style.css` dhe ky `README.md` ekzistonin në historinë lokale të repository-t (`.git`), por GitHub-i
ende tregonte vetëm commit-in e strukturës me folderët nga `JavaI` deri `JavaXIV`. Vetëm pas `git push` ata
u shfaqën në GitHub.

Dallimi mes tri gjendjeve:

- **Skedar lokal:** ekziston vetëm në diskun tim dhe Git-i e sheh si *untracked* ose *modified*. Nëse
  prishet disku, humbet.
- **Commit:** një fotografi e ruajtur në historinë lokale të repository-t. Mund të kthehem te ai
  version, por askush tjetër nuk e sheh ende dhe GitHub-i nuk e ka.
- **Push:** commit-et lokale dërgohen te remote-i (`origin`). Vetëm tani ndryshimi shihet në GitHub
  dhe mund të dorëzohet në Classroom.

## Deklarimi i AI-së dhe burimeve

- Struktura e skedarëve u nis nga skeleti `Fillimi/` që dha profesori.
- Për ndërtimin e faqeve, README-n dhe komandat e Git-it u përdor asistenti AI (Cursor). Testet me
  serverin lokal u ekzekutuan realisht dhe rezultatet e shënuara më sipër janë ato të marra.
- Burime: kapitujt 1 deri 3 të librit të lëndës dhe dokumentacioni i `python -m http.server`.
