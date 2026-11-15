Do této složky vkládejte obrázky pro protokol.

V main.tex je pak použijte bez cesty, například:

    \obrazek[0.7\textwidth]{obrazek-1.png}{Popisek.}{obr:stitek}

Makro hledá soubor nejdřív zde, potom v kořeni projektu.
Dokud soubor neexistuje, v PDF se zobrazí šedý rámeček.
