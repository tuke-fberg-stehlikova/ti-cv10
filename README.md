# cv10: JavaScript

Stránka týždňa: https://beata.stehlikova.website.tuke.sk/ti/11.html
Prijať zadanie: https://classroom50.org/tuke-fberg-stehlikova/technologie-internetu-5k/assignments/cv10/accept?k=tcc8jmx0

Výsledkom je aplikácia z cv08 s file `js/app.js`. Vysvetlenie so živými náhľadmi je na stránke týždňa, čísla ukážok v úlohách sú z nej. `ENTITY` je názov table svojej main entity.

**Odovzdávaš** (v repository a vo svojom webovom priestore na sigma.tuke.sk v `ti/cv10/`, obsah `web/` aj v `ti/projekt/`):

- `web/js/app.js` s komentárom o role, pripojený v `web/template.php` tagom `<script src="js/app.js"></script>` pred `</body>`
- počítadlo znakov pri jednom `input` alebo `textarea` vo formulári `add-ENTITY.php`
- filter pri písaní v `ENTITY.php`
- otázku pred zmazaním pri každom buttone Zmazať v `data.php` a `detail.php`
- `README.md` s mapou aplikácie doplnenou o `web/js/app.js`

**Hodnotenie:** 1 bod. Aplikácia s `js/app.js` (počítadlo znakov, filter pri písaní, otázka pred zmazaním) funguje vo svojom webovom priestore na sigma.tuke.sk a funguje aj s vypnutým JavaScriptom, kód je v repository. Po push sa spustia testy (10 kontrol); zelený výsledok znamená, že files a požadované časti kódu sú na mieste, body udeľuje učiteľka.

Ak v Kubeflow chýbajú rozšírenia, príkaz na obnovu je v návode 04 Odovzdávanie.

## Kde sa čo umiestni

| Čo | V ktorom file | Ako to vyzerá |
|---|---|---|
| kód JavaScriptu | `web/js/app.js` | riadky ako `const info = ...;` |
| pripojenie `app.js` k stránke | `web/template.php`, posledný riadok pred `</body>` | `<script src="js/app.js"></script>` |
| elementy, s ktorými JavaScript pracuje | content file stránky, napr. `web/content/contact.php` | HTML tag s `id`, `class` alebo `data-...`, napr. `<p id="info">` |
| čo sa má stať po kliknutí alebo pri písaní | `web/js/app.js` | `addEventListener` z ukážky 3. Do HTML tagu sa `onclick="..."` nepíše. |

## Prompty

Prompt A, počítadlo znakov. Prikladá sa `web/js/app.js` a `web/content/add-ENTITY.php`.

```text
Prikladám js/app.js a content file s formulárom. Doplň počítadlo znakov pre textarea alebo input, ktorý označím komentárom <!-- POČÍTADLO -->. Do HTML pridaj maxlength a pod element <div class="form-text"> s id končiacim na -count. Do js/app.js pridaj na koniec: querySelector pre oba elementy, podmienku if (element), addEventListener('input', function () { ... }) s textContent a value.length. Bez knižníc, bez šípkových funkcií, bez onclick v HTML. Komentár pri každom riadku po slovensky. Limit znakov nechaj ako // DOPLŇ. Vráť celé oba files.
```

Prompt B, filter pri písaní. Prikladá sa `web/js/app.js` a `web/content/ENTITY.php`.

```text
Prikladám js/app.js a content file so zoznamom z databázy. Doplň filter pri písaní. Do HTML pridaj nad zoznam input type text s id search a každej položke zoznamu class, podľa ktorej ju JavaScript nájde; existujúci filter cez GET nechaj. Do js/app.js pridaj na koniec: querySelector pre input, querySelectorAll pre položky, podmienku if (search), addEventListener('input', ...), v ňom for (const ... of ...) s textContent.toLowerCase().includes(...) a classList.add / remove 'd-none'. Bez knižníc, bez šípkových funkcií. Komentár pri každom riadku po slovensky. Názov class položky nechaj ako // DOPLŇ. Vráť celé oba files.
```

Prompt C, otázka pred zmazaním. Prikladá sa `web/js/app.js`, `web/content/data.php` a `web/content/detail.php`.

```text
Prikladám js/app.js a content files s formulármi na zmazanie. Každému buttonu Zmazať pridaj attribute data-confirm s textom otázky; formuláre a ich action nemeň. Do js/app.js pridaj na koniec: querySelectorAll('button[data-confirm]'), for (const button of ...), addEventListener('click', function (event) { ... }); pri prvom kliknutí event.preventDefault(), button.dataset.asked = 'yes' a text buttonu z button.dataset.confirm; druhé kliknutie formulár odošle. Bez alert a confirm, bez šípkových funkcií. Komentár pri každom riadku po slovensky. Text otázky nechaj ako // DOPLŇ. Vráť celé files.
```

Prečo sú prompty napísané práve takto:

- priložený `app.js`: AI dopĺňa na koniec jedného file a nevytvára ďalší,
- „bez šípkových funkcií": kód je v tom istom zápise ako na tejto stránke a dá sa obhájiť,
- „bez onclick v HTML": JavaScript zostane v `app.js`,
- „bez alert a confirm": na stránke nič nevyskakuje,
- „existujúci filter cez GET nechaj" a „formuláre nemeň": to, čo fungovalo v cv07 a cv08, zostane funkčné aj bez JavaScriptu,
- `// DOPLŇ` necháva limit, názov class a text otázky na autorovi aplikácie.

## Úlohy

**11.1** Kubeflow: skontroluj rozšírenia (SFTP, Five Server, Intelephense). Ak chýbajú, spusti v termináli príkaz na obnovu z návodu [04 Odovzdávanie](https://beata.stehlikova.website.tuke.sk/navody/04-odovzdavanie.html).

**11.2** `git clone` repository cv10 a prekopíruj aplikáciu z cv08:

```bash
rsync -a --exclude .git --exclude README.md cv08/ cv10/
```

Commit.

**11.3** `web/js/app.js` s komentárom o role a `console.log`, pripojený v `template.php` pred `</body>` (ukážka 1). Over v Console, že na každej stránke z menu je riadok `app.js je pripojený`. Commit.

**11.4** Počítadlo znakov pri jednom `input` alebo `textarea` vo formulári `add-ENTITY.php` (ukážka 5, prompt A). Ak je ten istý element aj v `edit-ENTITY.php`, počítadlo funguje aj tam.

**11.5** Filter pri písaní v `ENTITY.php` (ukážka 7, prompt B). Filter cez GET z cv07 zostáva. Commit.

**11.6** Otázka pred zmazaním pri každom buttone Zmazať v `data.php` a `detail.php` (ukážka 8, prompt C). Over: prvé kliknutie nič nezmaže, druhé zmaže.

**11.7** Podmienky `if` pre elementy, ktoré nie sú na každej stránke (ukážka 9). Otvor každú položku menu a over, že Console je bez červených hlášok. Commit.

**11.8** V nástrojoch pre vývojárov vypni JavaScript (F12, Ctrl+Shift+P, napíš „Disable JavaScript") a over, že pridanie, úprava aj zmazanie fungujú. Potom JavaScript znova zapni.

**11.9** Poriadok v projekte: spusti `python3 unify.py --check`. Do mapy aplikácie v `README.md` doplň riadok pre `web/js/app.js`. V repository nie sú files, ktoré aplikácia nepoužíva.

**11.10** Commit a push, aspoň 4 commity v rôznych krokoch. Upload Folder: `cv10` do `ti/cv10/` a obsah `web/` do `ti/projekt/`. Over vo svojom webovom priestore na sigma.tuke.sk.

Voliteľné úlohy:

**11.11** Časť formulára, ktorá sa zobrazí po zaškrtnutí checkboxu (ukážka 6).

**11.12** Počet zobrazených položiek nad zoznamom, ktorý sa mení pri filtrovaní (vo vzore `<span id="shown">`).

**11.13** Počítadlo, ktoré zmení farbu textu, keď zostáva menej ako 10 znakov (`classList` a Bootstrap class `text-danger`).

---

# cv10: JavaScript

Week page: https://beata.stehlikova.website.tuke.sk/ti/11.html
Accept the assignment: https://classroom50.org/tuke-fberg-stehlikova/technologie-internetu-5k/assignments/cv10/accept?k=tcc8jmx0

The result is the application from cv08 with the file `js/app.js`. The explanation with live previews is on the week page; the example numbers in the tasks refer to it. `ENTITY` is the name of the table of your main entity.

**You submit** (in the repository and in your web space on sigma.tuke.sk in `ti/cv10/`, the content of `web/` also in `ti/projekt/`):

- `web/js/app.js` with the comment about its role, included in `web/template.php` with the tag `<script src="js/app.js"></script>` before `</body>`
- a character counter for one `input` or `textarea` in the form of `add-ENTITY.php`
- a filter while typing in `ENTITY.php`
- a question before deleting for every Zmazať button in `data.php` and `detail.php`
- `README.md` with the map of the application extended with `web/js/app.js`

**Grading:** 1 point. The application with `js/app.js` (character counter, filter while typing, question before deleting) works in your web space on sigma.tuke.sk and also works with JavaScript switched off, and the code is in the repository. Tests run after the push (10 checks); a green result means the files and the required parts of the code are in place, points are awarded by the teacher.

If extensions are missing in Kubeflow, the restore command is in the guide 04 Submitting.

## What is placed where

| What | In which file | What it looks like |
|---|---|---|
| JavaScript code | `web/js/app.js` | lines like `const info = ...;` |
| including `app.js` in the page | `web/template.php`, the last line before `</body>` | `<script src="js/app.js"></script>` |
| the elements JavaScript works with | the content file of the page, e.g. `web/content/contact.php` | an HTML tag with `id`, `class` or `data-...`, e.g. `<p id="info">` |
| what should happen after a click or while typing | `web/js/app.js` | `addEventListener` from example 3. `onclick="..."` is not written into the HTML tag. |

## Prompts

Prompt A, the character counter. Attach `web/js/app.js` and `web/content/add-ENTITY.php`.

```text
I attach js/app.js and a content file with a form. Add a character counter for the textarea or input that I mark with the comment <!-- POČÍTADLO -->. In the HTML add maxlength and below the element a <div class="form-text"> with an id ending in -count. In js/app.js add at the end: querySelector for both elements, the condition if (element), addEventListener('input', function () { ... }) with textContent and value.length. No libraries, no arrow functions, no onclick in HTML. A comment on every line in Slovak. Leave the character limit as // DOPLŇ. Return both files whole.
```

Prompt B, the filter while typing. Attach `web/js/app.js` and `web/content/ENTITY.php`.

```text
I attach js/app.js and a content file with a list from the database. Add a filter while typing. In the HTML add an input type text with the id search above the list and give every item of the list a class by which JavaScript finds it; keep the existing GET filter. In js/app.js add at the end: querySelector for the input, querySelectorAll for the items, the condition if (search), addEventListener('input', ...), inside it for (const ... of ...) with textContent.toLowerCase().includes(...) and classList.add / remove 'd-none'. No libraries, no arrow functions. A comment on every line in Slovak. Leave the name of the item class as // DOPLŇ. Return both files whole.
```

Prompt C, the question before deleting. Attach `web/js/app.js`, `web/content/data.php` and `web/content/detail.php`.

```text
I attach js/app.js and content files with delete forms. Give every Zmazať button the attribute data-confirm with the text of the question; do not change the forms or their action. In js/app.js add at the end: querySelectorAll('button[data-confirm]'), for (const button of ...), addEventListener('click', function (event) { ... }); on the first click event.preventDefault(), button.dataset.asked = 'yes' and the text of the button from button.dataset.confirm; the second click submits the form. No alert or confirm, no arrow functions. A comment on every line in Slovak. Leave the text of the question as // DOPLŇ. Return the files whole.
```

Why the prompts are written this way:

- the attached `app.js`: the AI adds to the end of one file and does not create another,
- "no arrow functions": the code uses the same notation as this page and can be defended,
- "no onclick in HTML": JavaScript stays in `app.js`,
- "no alert or confirm": nothing pops up on the page,
- "keep the existing GET filter" and "do not change the forms": what worked in cv07 and cv08 keeps working without JavaScript,
- `// DOPLŇ` leaves the limit, the class name and the text of the question to the author of the application.

## Tasks

**11.1** Kubeflow: check the extensions (SFTP, Five Server, Intelephense). If they are missing, run the restore command from the guide [04 Submitting](https://beata.stehlikova.website.tuke.sk/navody/04-odovzdavanie.html) in the terminal.

**11.2** `git clone` the repository cv10 and copy the application from cv08:

```bash
rsync -a --exclude .git --exclude README.md cv08/ cv10/
```

Commit.

**11.3** `web/js/app.js` with the comment about its role and `console.log`, included in `template.php` before `</body>` (example 1). Verify in the Console that every page from the menu shows the line `app.js je pripojený`. Commit.

**11.4** A character counter for one `input` or `textarea` in the form of `add-ENTITY.php` (example 5, prompt A). If the same element is also in `edit-ENTITY.php`, the counter works there too.

**11.5** A filter while typing in `ENTITY.php` (example 7, prompt B). The GET filter from cv07 stays. Commit.

**11.6** A question before deleting for every Zmazať button in `data.php` and `detail.php` (example 8, prompt C). Verify: the first click deletes nothing, the second one deletes.

**11.7** The `if` conditions for elements that are not on every page (example 9). Open every menu item and verify that the Console has no red messages. Commit.

**11.8** In the developer tools switch JavaScript off (F12, Ctrl+Shift+P, type "Disable JavaScript") and verify that adding, editing and deleting work. Then switch JavaScript back on.

**11.9** Tidying the project: run `python3 unify.py --check`. Add a line for `web/js/app.js` to the map of the application in `README.md`. The repository holds no files the application does not use.

**11.10** Commit and push, at least 4 commits at different steps. Upload Folder: `cv10` to `ti/cv10/` and the content of `web/` to `ti/projekt/`. Verify in your web space on sigma.tuke.sk.

Optional tasks:

**11.11** A part of the form that appears after checking a checkbox (example 6).

**11.12** The number of shown items above the list, changing while filtering (in the sample `<span id="shown">`).

**11.13** A counter that changes the colour of its text when fewer than 10 characters remain (`classList` and the Bootstrap class `text-danger`).
