# JavaIII — Klubi i debatit

Ky folder përmban zgjidhjen e detyrës së javës së tretë, “Klinika e CSS:
shpëto afishen”. Projekti paraqet një afishe responsive për Klubin e debatit.

## Si të ekzekutohet

1. Hap folderin `JavaIII`.
2. Hap `index.html` në shfletues ose përdor Live Server.
3. Zvogëlo dritaren deri në 360 px për të kontrolluar paraqitjen responsive.
4. Përdor tastin `Tab` për të kontrolluar fokusin e dukshëm të lidhjeve.
5. Kliko “Kërko informacion” për të hapur Gmail-in me marrësin
   `gjergj.cuni@student.uni-pr.edu`.

## Skedarët

- `index.html` — struktura dhe përmbajtja semantike e afishes.
- `style.css` — dizajni responsive, variablat, box model-i dhe gjendjet
  `hover`/`focus-visible`.
- `gabime.css` — versioni i korrigjuar i konfliktit të specifikës dhe overflow-it.
- `README.md` — dokumentimi dhe udhëzimet për ekzekutim.

## Funksionalitetet

- Tri etiketa të dallueshme: falas, vende të kufizuara dhe online.
- Panel responsive që nuk del jashtë ekranit në gjerësi 360 px.
- Fokus i dukshëm gjatë navigimit me tastierë.
- Buton që hap Gmail-in në një tab të ri me marrësin dhe subjektin të plotësuar.

## Shpjegimi i box model-it

Me `box-sizing: border-box`, vlera e `width` përfshin përmbajtjen, `padding`-un
dhe `border`-in. Kështu paneli me `width: 100%` nuk e tejkalon ekranin.

## Reflektim

Në versionin me gabime, selektori `#poster` fitonte ndaj `.poster`, sepse një
selektor ID-je ka specifikë më të lartë se një selektor klase. Konflikti u
eliminua duke përdorur një rregull të vetëm `.poster`, pa `!important`.

Të dhënat e aktivitetit janë të sajuara dhe projekti përdor vetëm front end.
