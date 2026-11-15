# Šablona semestrálního projektu – FEL ZČU

Jednoduchá šablona pro psaní semestrálních protokolů na Fakultě
elektrotechnické ZČU. Všechno, co budete při psaní potřebovat, je
připravené: titulní strana, nadpisy, obrázky s automatickým číslováním,
tabulky, rovnice, seznamy, výpisy kódu, citace i poznámky pod čarou.

Hlavní myšlenka je **main.tex = jen vaše údaje a váš text**. Zbytek
(načtení balíčků, písmo, makra, titulní strana) je schovaný v podsložce
`tex/`, takže se při psaní nemusíte brodit boilerplate kódem. Ukázky
syntaxe jsou v samostatném souboru `example.tex`; `main.tex` je záměrně
čistý a připravený k psaní.

## Struktura složky

```text
sablona/
├── main.tex                  ← tady pište: údaje o projektu + obsah
├── example.tex               ← ukázky syntaxe (samostatný dokument)
├── example.pdf               ← náhled ukázek (volitelné)
├── tex/
│   ├── preambule.tex         ← balíčky, písmo, okraje, globální sazba
│   ├── makra.tex             ← \vstup, \obrazek a další pomocné příkazy
│   └── titulni-strana.tex    ← vzhled titulní strany
├── obrazky/                  ← sem vkládejte obrázky
├── .vscode/
│   ├── settings.json         ← LaTeX Workshop, XeLaTeX 2x, auto build
│   ├── tasks.json            ← build, otevření PDF, čištění
│   └── extensions.json       ← doporučená rozšíření
├── README.md                 ← tento návod
├── .gitattributes            ← Git LFS pro PDF, obrázky a archivy
├── .gitignore                ← ignorované pomocné soubory
└── latexmkrc                 ← volba XeLaTeXu pro latexmk
```

`main.tex` se dá otevřít v TeXstudiu a rovnou kompilovat. `example.tex`
je samostatný dokument – otevřete ho, když si potřebujete zkopírovat
syntaxi, a kompilujte ho zvlášť. V podsložkách `tex/*.tex` je na začátku
řádek `% !TEX root = ../main.tex`, takže při úpravách těchto souborů
TeXstudio ví, že má překládat `main.tex`.

### Git LFS

Soubor `.gitattributes` nastavuje Git LFS pro PDF, obrázky, archivy a
dokumenty z Office/LibreOffice. Po naklonování repozitáře spusťte:

```bat
git lfs install
```

Nově přidané soubory těchto typů se pak automaticky ukládají do LFS.
Už dříve commitnuté binární soubory je potřeba do LFS převést zvlášť
(např. přes `git lfs migrate import`).

## Rychlý start

1. Otevřete složku `sablona` ve VS Code, nebo v TeXstudiu otevřete
   `main.tex`.
2. Na začátku vyplňte údaje o projektu (viz níže).
3. Do kapitol pište svůj text. Šedé `\vstup{...}` nahraďte normálním
   textem. Kapitoly `Zadání`, `Řešení`, `Zhodnocení` a `Závěr` jsou jen
   kostra – přejmenujte je nebo smažte.
4. Syntaxi obrázků, tabulek, rovnic, kódu a citací najdete v
   `example.tex`. Otevřete ho, zkopírujte si potřebný blok a vložte do
   `main.tex`. `example.tex` se do hlavního dokumentu nepřidává.
5. Obrázky nakopírujte do složky `obrazky/`.
6. Stiskněte **F5** v TeXstudiu. Pro správné odkazy a citace je potřeba
   překlad spustit dvakrát (druhý běh doladí čísla a `??`).
7. Před odevzdáním zkontrolujte seznam na konci tohoto návodu.

## Údaje o projektu

Všechny údaje se nastavují na jednom místě v `main.tex`:

```latex
\newcommand{\nazevPredmetu}{\vstup{Název předmětu}}
\newcommand{\zkratkaPredmetu}{\vstup{ZKRATKA}}
\newcommand{\katedra}{\vstup{Katedra – doplňte název}}
\newcommand{\nazevProjektu}{\vstup{Název semestrálního projektu}}
\newcommand{\typPrace}{Semestrální projekt}
\newcommand{\autor}{\vstup{Jméno Příjmení}}
\newcommand{\osobniCislo}{\vstup{A00B0000P}}
\newcommand{\datumOdevzdani}{\today}
\newcommand{\nazevArchivu}{\vstup{prijmeni\_projekt.zip}}
```

| Příkaz | Význam |
|---|---|
| `\nazevPredmetu` | celý název předmětu |
| `\zkratkaPredmetu` | zkratka předmětu, např. `VP` |
| `\katedra` | celý název katedry |
| `\nazevProjektu` | název semestrálního projektu |
| `\typPrace` | typ práce, výchozí „Semestrální projekt“ |
| `\autor` | jméno a příjmení |
| `\osobniCislo` | osobní číslo |
| `\datumOdevzdani` | datum; `\today` vypíše dnešní datum |
| `\nazevArchivu` | název odevzdávaného ZIPu |

**Důležité:** výchozí hodnoty jsou obalené v `\vstup{...}`, takže jsou
v PDF šedé a kurzívou. Nahrazujte **celou hodnotu** i s `\vstup`, např.:

```latex
\newcommand{\autor}{Jan Novák}
```

Když chcete pevné datum místo dnešního, napište například:

```latex
\newcommand{\datumOdevzdani}{15.~11.~2026}
```

Podtržítko v názvu archivu se v LaTeXu píše jako `\_`:

```latex
\newcommand{\nazevArchivu}{novak\_projekt.zip}
```

## Ukázky syntaxe

V `main.tex` nejsou žádné ukázkové bloky, aby se dalo rovnou psát.
Kompletní přehled syntaxe je v `example.tex`:

- otevřete `example.tex` a přeložte ho stejně jako `main.tex`
  (**Ctrl+Alt+B** ve VS Code, **F5** v TeXstudiu, nebo task
  `LaTeX: Build example (XeLaTeX 2x)`),
- v `example.pdf` uvidíte výsledek,
- potřebný blok z `example.tex` zkopírujte do `main.tex`.

`example.tex` je samostatný dokument. Nikdy ho nepřidávejte do
`main.tex` přes `\input{example}` – do protokolu by se vložily všechny
ukázky.

## Jak psát obsah

### Nadpisy

```latex
\section{Zadání}
\subsection{Postup řešení}
```

Sekce se číslují automaticky. Podkapitoly jsou záměrně bez čísel, aby
text působil lehčeji. Pokud chcete nečíslovaný nadpis, použijte hvězdičku:

```latex
\section*{Přílohy}
```

### Odstavce a formátování

Odstavce se oddělují prázdným řádkem. Uvnitř textu můžete použít:

```latex
\textbf{tučné písmo}
\textit{kurzíva}
\texttt{monospace nebo název souboru}
```

Pro českou sazbu je dobré psát pevnou mezeru `~` tam, kde nemá dojít
k zalomení, například `v~textu`, `obr.~\ref{obr:stitek}` nebo
`15.~11.~2026`.

### Seznamy

Odrážky:

```latex
\begin{itemize}
  \item První položka.
  \item Druhá položka.
\end{itemize}
```

Číslovaný seznam:

```latex
\begin{enumerate}
  \item První krok.
  \item Druhý krok.
\end{enumerate}
```

Seznamy lze vnořovat.

### Obrázky

Obrázky se vkládají pomocí připraveného příkazu `\obrazek`:

```latex
\obrazek[0.7\textwidth]{obrazek-1.png}{Popisek obrázku.}{obr:stitek}
```

Argumenty:

| Argument | Význam |
|---|---|
| `[0.7\textwidth]` | nepovinná šířka; výchozí je `0.85\textwidth` |
| `obrazek-1.png` | název souboru; hledá se v `obrazky/` i v kořeni |
| `Popisek obrázku.` | text pod obrázkem |
| `obr:stitek` | štítek pro odkazy přes `\ref{obr:stitek}` |

Příklad odkazu v textu:

```latex
Na obrázku~\ref{obr:stitek} je vidět...
```

Dokud soubor neexistuje, zobrazí se šedý rámeček se jménem souboru.
Dokument se tedy vždy zkompiluje, i když obrázek ještě nemáte.

Podporované formáty jsou PNG, JPG a PDF. Obrázek se automaticky zmenší
tak, aby nepřesáhl `0.45\textheight`; pokud se nevejde na stránku,
zmenšete šířku, např. na `0.6\textwidth`.

Pro dva obrázky vedle sebe použijte ručně prostředí `figure` a dvě
`minipage`:

```latex
\begin{figure}[H]
  \centering
  \begin{minipage}{0.48\textwidth}
    \centering
    \includegraphics[width=\linewidth]{obrazky/a.png}
  \end{minipage}\hfill
  \begin{minipage}{0.48\textwidth}
    \centering
    \includegraphics[width=\linewidth]{obrazky/b.png}
  \end{minipage}
  \caption{Dva obrázky vedle sebe.}
  \label{obr:dva}
\end{figure}
```

### Tabulky

```latex
\begin{table}[H]
  \centering
  \caption{Popisek tabulky.}
  \label{tab:stitek}
  \begin{tabular}{|l|c|r|}
    \hline
    \textbf{Parametr} & \textbf{Hodnota} & \textbf{Jednotka} \\ \hline
    Napětí & 5,00 & V \\ \hline
    Proud & 0,25 & A \\ \hline
  \end{tabular}
\end{table}
```

Odkaz v textu: `tab.~\ref{tab:stitek}`. K dispozici jsou i balíčky
`array` a `multirow` pro složitější tabulky.

### Rovnice

Jedna číslovaná rovnice:

```latex
\begin{equation}
  y = a x + b
  \label{eq:stitek}
\end{equation}
```

Odkaz: `\eqref{eq:stitek}`.

Více zarovnaných rovnic:

```latex
\begin{align}
  y &= a x + b \label{eq:prvni}\\
  z &= y^2     \label{eq:druha}
\end{align}
```

### Výpisy kódu

```latex
\begin{lstlisting}[language=Python,
                   caption={Popisek výpisu.},
                   label={lst:stitek}]
def soucet(a, b):
    return a + b
\end{lstlisting}
```

Odkaz: `\ref{lst:stitek}`. Jazyk se volí parametrem `language`, například
`Python`, `C`, `C++`, `Java`, `SQL` nebo `bash`. Pro číslování řádků
přidejte `numbers=left`.

Krátké názvy a příkazy pište přímo do textu:

```latex
Soubor \texttt{main.py} spustíte příkazem \texttt{python main.py}.
```

### Citace a literatura

V textu:

```latex
Toto tvrzení vychází z~literatury~\cite{ref:zdroj}.
```

Na konci dokumentu:

```latex
\begin{thebibliography}{9}
  \bibitem{ref:zdroj}
  Autor. \textit{Název publikace}. Město: Vydavatel, 2024.
\end{thebibliography}
```

Po přidání citace je potřeba zkompilovat dokument dvakrát, aby se
odkazy a čísla srovnaly.

### Poznámky, odkazy a URL

```latex
Poznámka pod čarou.\footnote{Text poznámky.}
Webová adresa: \url{https://www.zcu.cz}
```

Odkazy na obrázky, tabulky a rovnice fungují přes štítky:

```latex
\label{obr:stitek}
\ref{obr:stitek}
\pageref{obr:stitek}
```

### Zlomy stránek

Ruční zlom:

```latex
\newpage
```

Když nechcete, aby nadpis zůstal sám na konci stránky:

```latex
\needspace{8cm}
\section{Zhodnocení}
```

### Volitelný obsah a přílohy

Obsah dokumentu:

```latex
\tableofcontents
\newpage
```

Seznam obrázků a tabulek:

```latex
\listoffigures
\listoftables
```

Přílohy:

```latex
\appendix
\section{Přílohy}
```

## Užitečné příkazy

| Příkaz | Co dělá |
|---|---|
| `\vstup{text}` | šedý text – místo k doplnění |
| `\obrazek[šířka]{soubor}{popisek}{štítek}` | obrázek s automatickým číslem |
| `\section{...}` | číslovaná kapitola |
| `\subsection{...}` | podkapitola |
| `\section*{...}` | nečíslovaná kapitola |
| `\label{...}` | štítek pro odkaz |
| `\ref{...}` | číslo obrázku, tabulky, výpisu… |
| `\eqref{...}` | číslo rovnice v závorkách |
| `\pageref{...}` | číslo stránky se štítkem |
| `\cite{...}` | citace |
| `\footnote{...}` | poznámka pod čarou |
| `\url{...}` | webová adresa |
| `\needspace{...}` | ochrana proti osamocenému nadpisu |
| `\newpage` | nová stránka |
| `\textbf{...}`, `\textit{...}`, `\texttt{...}` | tučné, kurzíva, monospace |

## Kompilace

Šablona používá **XeLaTeX** kvůli písmu Times New Roman a české sazbě.

### TeXstudio

Otevřete `main.tex` a stiskněte **F5**. Díky prvnímu řádku
`% !TEX program = xelatex` se použije správný překladač. Pro správné
odkazy a citace stiskněte **F5** ještě jednou.

### Příkazová řádka

```bat
xelatex main.tex
xelatex main.tex
```

Dvakrát proto, aby se správně vyřešily odkazy, citace a čísla obrázků.

### Overleaf

V nabídce **Menu → Compiler** zvolte **XeLaTeX**.

### latexmk

Pokud máte nainstalovaný Perl, můžete použít:

```bat
latexmk main.tex
```

### VS Code

Ve složce je připravená konfigurace `.vscode/`, takže VS Code můžeš
používat jako hlavní LaTeX editor.

1. Otevři ve VS Code **celou složku** `sablona`:

   `File → Open Folder… → C:\Users\David\Desktop\sablona`

   Neotvírej jen samotný `main.tex`, jinak se nenajdou `.vscode`
   nastavení ani složka `tex/`.

2. Nainstaluj rozšíření **LaTeX Workshop**:

   VS Code ho nabídne sám díky `.vscode/extensions.json`, případně ho
   najdeš jako `james-yu.latex-workshop`.

3. Ověř, že máš v PATH `xelatex`:

   ```bat
   xelatex --version
   ```

4. Překlad:

   - **Ctrl+S** – automatický build při uložení (LaTeX Workshop),
   - **Ctrl+Alt+B** – build přes LaTeX Workshop,
   - **Ctrl+Shift+B** – výchozí VS Code task
     `LaTeX: Build main (XeLaTeX 2x)`.

   LaTeX Workshop pozná správný hlavní soubor podle prvního řádku
   `% !TEX root = ...`. Když máš otevřený `main.tex`, překládá se
   `main.tex`; když máš otevřený `example.tex`, překládá se
   `example.tex`.

5. PDF:

   - **Ctrl+Alt+V** – otevře PDF v záložce VS Code,
   - nebo task `LaTeX: Otevřít PDF` (main) / `LaTeX: Otevřít example PDF`.

Připravené tasky najdeš v `Terminal → Run Task…` (nebo
`Ctrl+Shift+P → Tasks: Run Task`):

| Task | Co dělá |
|---|---|
| `LaTeX: Build main (XeLaTeX 2x)` | dva průchody pro `main.tex`, výchozí build |
| `LaTeX: Rychlý překlad main (XeLaTeX 1x)` | jeden rychlý průchod pro `main.tex` |
| `LaTeX: Build example (XeLaTeX 2x)` | dva průchody pro `example.tex` |
| `LaTeX: Otevřít PDF` | otevře `main.pdf` v systémovém prohlížeči |
| `LaTeX: Otevřít example PDF` | otevře `example.pdf` v systémovém prohlížeči |
| `LaTeX: Build main + otevřít PDF` | přeloží `main.tex` a hned otevře PDF |
| `LaTeX: Vyčistit pomocné soubory` | smaže aux, log, out, synctex… u obou dokumentů |

Nastavení v `.vscode/settings.json` už řeší:

- XeLaTeX jako výchozí překladač,
- recept `XeLaTeX 2x`,
- automatický build při uložení,
- zobrazení hlavního souboru ve stavovém řádku,
- PDF v záložce a SyncTeX,
- české UTF-8 a zalamování řádků.

Když `xelatex` ve VS Code nefunguje, zkontroluj instalaci MiKTeXu nebo
TeX Live a restartuj VS Code. Tasky fungují i bez rozšíření LaTeX
Workshop, jen pak nebude automatický build a vestavěný PDF prohlížeč.

## Před odevzdáním – kontrolní seznam

- [ ] Vyplněné všechny údaje na začátku `main.tex` (už žádný `\vstup`).
- [ ] Zkontrolovaná titulní strana (katedra, předmět, autor, datum, archiv).
- [ ] Vlastní text v kapitolách Zadání, Řešení, Zhodnocení a Závěr.
- [ ] Přejmenované nebo smazané kapitoly, které do projektu nepatří.
- [ ] Vložené všechny obrázky a zkontrolované popisky.
- [ ] Zkontrolované odkazy – v PDF nesmí být `??`.
- [ ] Zkontrolované citace a seznam literatury.
- [ ] Dokument zkompilovaný dvakrát.
- [ ] Zkontrolovaný výsledný `main.pdf`.
- [ ] Případně smazané volitelné části (obsah, seznamy, přílohy).
- [ ] `example.tex` není součástí odevzdávaného dokumentu.
- [ ] Archiv s `main.tex`, složkou `tex/`, obrázky a `main.pdf`.

## Časté problémy

**V PDF je šedý rámeček místo obrázku.**
Soubor se nenašel. Zkontrolujte přesný název včetně přípony a to, že
je ve složce `obrazky/` nebo v kořeni projektu.

**Místo čísel odkazů je `??`.**
Zkompilujte dokument ještě jednou. Odkazy se dopočítají ve druhém průchodu.

**Chyba `Undefined control sequence`.**
Pravděpodobně je v textu překlep v názvu příkazu, nebo chybí zpětné
lomítko. Zkontrolujte poslední změnu v `main.tex`.

**Chyba kvůli podtržítku.**
Podtržítko v textu se píše `\_`, například `main\_file.py`.

**Chybí Times New Roman.**
Šablona se pokusí použít náhradní písmo TeX Gyre Termes. Pokud chcete
přesně Times New Roman, nainstalujte ho do systému.

**Obrázek nebo tabulka přetéká.**
Zmenšete šířku obrázku (`0.6\textwidth`), zkraťte popisek nebo před
objekt vložte `\newpage`.

**Nadpis zůstal sám na konci stránky.**
Před něj vložte `\needspace{8cm}`.

**Přeložil se špatný soubor.**
Zkontrolujte první řádek otevřeného souboru: `main.tex` má
`% !TEX root = main.tex`, `example.tex` má `% !TEX root = example.tex`.
Ve VS Code lze také použít task `LaTeX: Build main (XeLaTeX 2x)` nebo
`LaTeX: Build example (XeLaTeX 2x)`.

**Titulní strana přetéká.**
Zkraťte název projektu nebo upravte `\vspace{150pt}` v
`tex/titulni-strana.tex`.

## Kde co upravit

| Co chcete změnit | Kde |
|---|---|
| údaje o projektu | `main.tex` – hned na začátku |
| text protokolu | `main.tex` – kapitoly |
| ukázky syntaxe | `example.tex` (samostatný dokument) |
| okraje, písmo, řádkování | `tex/preambule.tex` |
| vzhled nadpisů a seznamů | `tex/preambule.tex` |
| makro `\obrazek` nebo `\vstup` | `tex/makra.tex` |
| titulní stranu | `tex/titulni-strana.tex` |
| obrázky | složka `obrazky/` |

Do `tex/preambule.tex` a `tex/makra.tex` se běžně nemusí zasahovat.
Když si je rozbijete, stačí se vrátit k této šabloně.
