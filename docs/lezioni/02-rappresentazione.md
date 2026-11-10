# L02 · Come si rappresenta l'informazione

<p class="meta">In presenza · 2 ore · Blocco A — Fondamenti</p>

!!! abstract "In sintesi"
    All'interno di un computer esistono soltanto due stati, convenzionalmente indicati con 0 e 1.
    Eppure sullo schermo compaiono poesie in arabo, ideogrammi cinesi, emoji, fotografie e canzoni.
    In questa lezione ricostruiamo i passaggi che portano dai bit alle lettere, alle immagini e ai suoni;
    vediamo perché a volte, al posto di "è", compare "Ã¨"; scopriamo chi decide quali sistemi di
    scrittura esistano nel mondo digitale; e apriamo un file per capire che cosa contenga davvero.

<div class="slides-embed">
  <iframe src="../../slides/L02.html" title="Slide della lezione 2" loading="lazy" allowfullscreen></iframe>
</div>
<p class="slides-links">
  <a class="md-button" href="../../slides/L02.html" target="_blank" rel="noopener">Slide a schermo intero</a>
  <a class="md-button" href="../../slides/L02.pdf" target="_blank" rel="noopener">Slide in PDF</a>
</p>

## Obiettivi

Alla fine della lezione saprete:

- spiegare che cosa sono **bit** e **byte**, contare in binario e leggere un numero esadecimale;
- calcolare in modo approssimativo quanto spazio occupano un testo, un'immagine e un brano musicale;
- descrivere il funzionamento di una **codifica dei caratteri** e la differenza tra **ASCII**,
  **Unicode** e **UTF-8**;
- riconoscere e diagnosticare un problema di codifica (*mojibake*) e un problema di carattere tipografico (*tofu*);
- distinguere **carattere** e **glifo**, **file** e **formato**, formati **aperti** e **proprietari**.

---

## 1. Il bit: l'unità minima

### Due stati

Il **bit** (contrazione di *binary digit*, "cifra binaria") è la più piccola quantità di informazione
rappresentabile: un'alternativa tra due possibilità, che chiamiamo per convenzione 0 e 1. Fisicamente,
a seconda del supporto, può corrispondere alla presenza o all'assenza di una tensione elettrica in un
circuito, all'orientamento di una particella magnetica su un disco, a un minuscolo avvallamento sulla
superficie di un CD.

La scelta di due soli stati ha ragioni pratiche: distinguere tra "c'è corrente" e "non c'è corrente"
è molto più affidabile che distinguere tra dieci livelli diversi di tensione, e un sistema a due stati
resiste meglio ai disturbi.

### Combinare i bit

Un bit risponde a una domanda sì/no. Per rappresentare più alternative si usano più bit, e ogni bit
aggiunto **raddoppia** il numero delle combinazioni possibili:

| Bit | Combinazioni | Che cosa ci sta |
|---|---|---|
| 1 | 2 | vero / falso, acceso / spento |
| 2 | 4 | le quattro stagioni |
| 3 | 8 | i sette giorni della settimana, con un valore di avanzo |
| 5 | 32 | le 21 lettere dell'alfabeto italiano, maiuscole o minuscole |
| 7 | 128 | l'alfabeto inglese, maiuscolo e minuscolo, cifre e punteggiatura (ASCII) |
| 8 | 256 | un **byte** |
| 16 | 65.536 | una buona parte degli ideogrammi cinesi di uso comune |
| *n* | 2<sup>*n*</sup> | |

Il **byte** è un gruppo di otto bit, e costituisce l'unità di misura di base della memoria. I suoi
multipli si indicano con i prefissi del Sistema internazionale:

| Unità | Valore | Ordine di grandezza |
|---|---|---|
| kilobyte (kB) | mille byte | una pagina di testo semplice, una breve email |
| megabyte (MB) | un milione di byte | un romanzo in formato testo, una fotografia compressa |
| gigabyte (GB) | un miliardo di byte | un film in alta definizione, alcune centinaia di libri illustrati |
| terabyte (TB) | mille miliardi di byte | il disco di un computer recente |
| petabyte (PB) | un milione di miliardi di byte | l'archivio di una grande biblioteca digitale |

??? info "1000 o 1024?"
    Per ragioni storiche, in informatica si è usato a lungo il valore 1 kB = 1024 byte, perché 1024 è
    una potenza di due (2<sup>10</sup>). Le norme attuali distinguono il kilobyte (kB, 1000 byte) dal
    *kibibyte* (KiB, 1024 byte), e così via per MiB, GiB e TiB. È questa la ragione per cui un disco
    venduto come "1 TB" appare, una volta collegato al computer, come circa 931 GB: il produttore
    conta in potenze di dieci, il sistema operativo in potenze di due.

---

## 2. Contare in binario (e in esadecimale)

### Il sistema posizionale

Il sistema con cui contiamo abitualmente è **posizionale in base 10**: usa dieci cifre, e il valore di
una cifra dipende dalla posizione che occupa. Nel numero 1819 la cifra 8 vale ottocento, perché si
trova nella posizione delle centinaia:

1819 = 1 × 1000 + 8 × 100 + 1 × 10 + 9 × 1

Il sistema **binario** funziona allo stesso modo, ma con due sole cifre, e ogni posizione vale il
doppio della precedente:

| Posizione | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|---|
| `01000001` | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| `00010011` | 0 | 0 | 0 | 1 | 0 | 0 | 1 | 1 |

Il primo numero vale 64 + 1 = **65**, il secondo 16 + 2 + 1 = **19**. Il numero 65 avrà un ruolo
importante tra poco.

Per passare dal decimale al binario si può procedere al contrario: si cerca la potenza di due più
grande contenuta nel numero, la si sottrae e si ripete. Per 45: 32 ci sta (resta 13), 16 no, 8 sì
(resta 5), 4 sì (resta 1), 2 no, 1 sì. Quindi 45 = `00101101`.

### Perché esiste l'esadecimale

Le sequenze binarie diventano presto illeggibili. Per questo i programmatori usano spesso il sistema
**esadecimale** (base 16), che impiega le cifre da 0 a 9 e le lettere da A a F per i valori da 10 a 15.
Il vantaggio è che **una cifra esadecimale corrisponde esattamente a quattro bit**, quindi un byte si
scrive sempre con due cifre:

| Binario | `0100` `0001` | `1100` `0011` | `1111` `1111` |
|---|---|---|---|
| Esadecimale | `41` | `C3` | `FF` |
| Decimale | 65 | 195 | 255 |

Vedrete numeri esadecimali ovunque: nei codici dei colori sul web (`#980260` è il colore di questo
sito), negli indirizzi di rete, nei codici dei caratteri Unicode (`U+00E8`).

!!! example "Esercizio (5 minuti)"
    1. Quanto vale in decimale `00001010`? E `00011001`?
    2. Come si scrive 7 in binario? E 100?
    3. Il colore `#FF0000` è composto da tre byte (rosso, verde, blu). Che colore è?

    ??? success "Soluzioni"
        1. `00001010` = 8 + 2 = **10**; `00011001` = 16 + 8 + 1 = **25**.
        2. 7 = `00000111`; 100 = 64 + 32 + 4 = `01100100`.
        3. Rosso al massimo (`FF` = 255), verde e blu a zero: è **rosso puro**.

---

## 3. Dai numeri alle lettere

### Una tabella condivisa

Il computer non conosce le lettere, conosce soltanto numeri. Per scrivere un testo occorre quindi una
convenzione condivisa che associ a ogni carattere un numero: questa convenzione si chiama **codifica
dei caratteri** (*character encoding*). Chi scrive e chi legge un file devono usare la stessa tabella;
se le tabelle differiscono, i numeri vengono interpretati come caratteri sbagliati.

### ASCII, un alfabeto per una sola lingua

La codifica più antica ancora in uso è **ASCII** (*American Standard Code for Information
Interchange*), pubblicata negli Stati Uniti nel 1963. Usa 7 bit e definisce quindi 128 caratteri:

- 33 caratteri di controllo, eredità delle telescriventi (il ritorno a capo, la tabulazione, un
  segnale acustico);
- lo spazio, le cifre da 0 a 9, la punteggiatura e alcuni simboli;
- le 26 lettere dell'alfabeto inglese, maiuscole e minuscole.

In ASCII `A` corrisponde a 65, `B` a 66, `a` a 97, lo spazio a 32. Una parola come `Ciao` diventa la
sequenza di numeri 67 105 97 111.

L'elenco è notevole soprattutto per ciò che **manca**: lettere accentate, la `ñ` spagnola, la `ç`
francese, la `ß` tedesca, la `ø` danese, e naturalmente qualsiasi alfabeto non latino. ASCII è stato
progettato per l'inglese, e per molti anni il mondo digitale ha dato per scontato che l'inglese
bastasse.

### Il caos delle codifiche nazionali

Per rimediare, negli anni Ottanta e Novanta produttori e organismi di standardizzazione hanno usato
l'ottavo bit del byte per aggiungere altri 128 caratteri. Ma lo hanno fatto ciascuno a modo proprio:

- **ISO 8859-1** (detta *Latin-1*) per le lingue dell'Europa occidentale, e la sua variante
  Microsoft **Windows-1252**;
- **ISO 8859-2** per le lingue dell'Europa centrale (polacco, ceco, ungherese);
- **ISO 8859-5** e **KOI8-R** per il cirillico;
- **ISO 8859-6** per l'arabo, **ISO 8859-7** per il greco;
- **Shift-JIS** ed **EUC-JP** per il giapponese, **GB 2312** per il cinese semplificato, **Big5** per
  il cinese tradizionale.

Lo stesso numero indicava così lettere diverse a seconda della tabella: il valore 232 era `è` in
Latin-1, `č` in ISO 8859-2, `ш` in ISO 8859-5. Un file scritto in Polonia e aperto in Francia mostrava
caratteri sbagliati, e non era possibile scrivere nello stesso documento, ad esempio, un testo
francese con citazioni in russo.

### Il *mojibake*

Questo genere di errore è così comune che il giapponese ha una parola apposita, ***mojibake***
(文字化け, "caratteri trasformati"), entrata ormai nel lessico informatico internazionale.

!!! example "Anatomia di un errore"
    In UTF-8, la codifica che vedremo tra poco, la lettera `è` si scrive con due byte: `C3 A8`.
    Se un programma legge quei byte credendo che il testo sia in Latin-1, li interpreta come due
    caratteri distinti: `C3` diventa `Ã` e `A8` diventa `¨`. È per questo che *perché* si trasforma in
    **perchÃ©** e *città* in **cittÃ **.

    I byte del file sono corretti: è sbagliata la tabella usata per leggerli. Per questo il problema
    si risolve quasi sempre senza modificare il file, indicando al programma la codifica giusta.

Il caso opposto, un testo in Latin-1 letto come se fosse UTF-8, produce di solito un altro sintomo:
il carattere sostitutivo **�**, con cui il programma segnala di aver incontrato una sequenza di byte
che non sa decifrare.

### Unicode: un numero per ogni carattere

Per uscire dal caos, alla fine degli anni Ottanta un gruppo di aziende e di studiosi avviò il progetto
**Unicode**, la cui prima versione fu pubblicata nel 1991. L'idea è semplice e ambiziosa: assegnare a
**ogni carattere di ogni sistema di scrittura** un numero unico, valido ovunque, detto **punto di
codice** (*code point*). Per convenzione lo si scrive in esadecimale preceduto da `U+`:

| Carattere | Punto di codice | Nome ufficiale |
|---|---|---|
| `A` | U+0041 | LATIN CAPITAL LETTER A |
| `è` | U+00E8 | LATIN SMALL LETTER E WITH GRAVE |
| `ж` | U+0436 | CYRILLIC SMALL LETTER ZHE |
| `א` | U+05D0 | HEBREW LETTER ALEF |
| `ع` | U+0639 | ARABIC LETTER AIN |
| `अ` | U+0905 | DEVANAGARI LETTER A |
| `中` | U+4E2D | CJK UNIFIED IDEOGRAPH-4E2D |
| `😀` | U+1F600 | GRINNING FACE |

Unicode contiene oggi **oltre 150.000 caratteri** e più di 160 sistemi di scrittura: le lingue vive
più diffuse e molte lingue minoritarie, ma anche scritture storiche come il cuneiforme, i geroglifici
egizi, la lineare B, il gotico di Wulfila, le rune. Ogni nuova versione dello standard ne aggiunge altri.

I caratteri sono organizzati in **blocchi** (Latino di base, Cirillico, Arabo, Ideogrammi CJK
unificati…) e ciascuno è accompagnato da proprietà formali: la categoria (lettera, cifra,
punteggiatura), la direzione di scrittura, l'eventuale corrispondenza tra maiuscola e minuscola.

### UTF-8: come scrivere Unicode in byte

Unicode stabilisce *quale numero* corrisponde a ogni carattere, ma non dice ancora come scrivere quel
numero in una sequenza di byte. Esistono diverse **forme di codifica**; la più diffusa, di gran lunga,
è **UTF-8**, progettata nel 1992 da Ken Thompson e Rob Pike. UTF-8 usa un numero variabile di byte,
da uno a quattro, a seconda del carattere:

| Carattere | Punto di codice | Byte in UTF-8 | Quanti |
|---|---|---|---|
| `A` | U+0041 | `41` | 1 |
| `è` | U+00E8 | `C3 A8` | 2 |
| `ж` | U+0436 | `D0 B6` | 2 |
| `中` | U+4E2D | `E4 B8 AD` | 3 |
| `😀` | U+1F600 | `F0 9F 98 80` | 4 |

Due proprietà ne spiegano il successo. La prima è la **compatibilità con ASCII**: i 128 caratteri di
ASCII si codificano con un solo byte e con lo stesso valore, quindi qualsiasi testo ASCII è già, senza
modifiche, un testo UTF-8 valido. La seconda è l'**universalità**: con UTF-8 si possono scrivere nello
stesso file l'italiano, il russo, l'arabo e il giapponese. Oggi la quasi totalità delle pagine web
usa questa codifica.

Una conseguenza pratica è che in UTF-8 lettere e byte non coincidono. Il testo dell'*Infinito* che
abbiamo visto nella L01 conta 552 caratteri ma occupa 556 byte: le quattro lettere accentate
(*là*, *Così*, *immensità*, *m'è*) richiedono due byte ciascuna. Un testo in russo occupa circa il
doppio dei byte rispetto a un testo inglese di pari lunghezza, uno in cinese o in giapponese circa il
triplo per carattere.

### Una lettera, due codifiche: la normalizzazione

Unicode permette di scrivere alcuni caratteri in due modi diversi. La lettera `é` può essere un unico
carattere (U+00E9, *e con accento acuto*) oppure la sequenza di una `e` semplice (U+0065) seguita da un
**accento combinante** (U+0301), che il sistema sovrappone alla lettera precedente. A schermo le due
forme sono indistinguibili, ma per il computer sono sequenze diverse, di lunghezza diversa.

Il problema è tutt'altro che teorico. I file prodotti su macOS, ad esempio, usano spesso la forma
scomposta per i nomi dei file, mentre Windows e la maggior parte delle pagine web usano la forma
composta. Se costruite un corpus raccogliendo testi da fonti diverse e cercate la parola *café*,
potreste ottenere solo una parte delle occorrenze. Per evitarlo, i testi vanno **normalizzati**,
cioè convertiti tutti nella stessa forma: si parla di **NFC** (forma composta) e **NFD** (forma
scomposta). La normalizzazione è uno dei primissimi passaggi di qualunque analisi linguistica
automatica, e la ritroveremo nel Blocco C.

Lo stesso meccanismo degli accenti combinanti rende possibile scrivere lingue che impilano più
diacritici sulla stessa lettera, come il vietnamita (*ệ* ha sia un accento circonflesso sia un punto
sottoscritto), o alfabeti in cui le vocali si scrivono come segni attorno alle consonanti, come
l'hindi in devanagari.

### Le emoji sono caratteri

Le emoji fanno parte di Unicode a pieno titolo: sono caratteri con un punto di codice, un nome e delle
proprietà, esattamente come le lettere. Ciascun sistema operativo le disegna però a modo proprio, ed è
per questo che la stessa emoji può avere un aspetto, e talvolta una sfumatura di significato, diversi
su un iPhone e su un telefono Android. Alcune sono in realtà sequenze di più caratteri:

- 👍🏽 è il pollice alzato (U+1F44D) seguito da un **modificatore di carnagione** (U+1F3FD);
- 👩‍💻 è la donna (U+1F469) unita al computer (U+1F4BB) da un carattere invisibile chiamato
  *zero width joiner* (U+200D);
- 🇮🇹 è formata da due "lettere regionali", I e T, che il sistema riconosce come codice del paese.

---

## 4. Caratteri, glifi e caratteri tipografici

### Carattere e glifo

È utile distinguere il **carattere**, cioè l'unità astratta che Unicode codifica ("la lettera a
minuscola"), dal **glifo**, la forma concreta con cui quel carattere viene disegnato sullo schermo o
sulla carta. La stessa `a` ha glifi molto diversi in Times New Roman, in Helvetica o in un corsivo
calligrafico, ma resta lo stesso carattere U+0061. Il file contiene i caratteri, mentre il carattere
tipografico (*font*) installato sul computer fornisce i glifi.

In alcune scritture la distinzione è ancora più evidente. In arabo ogni lettera assume forme diverse a
seconda che si trovi isolata, all'inizio, in mezzo o alla fine di una parola: il file contiene un solo
carattere per ciascuna lettera, ed è il sistema di visualizzazione a scegliere la forma giusta.

### Il *tofu*

Se il computer riceve un carattere corretto ma non possiede un font in grado di disegnarlo, al posto
del glifo compare un rettangolo vuoto, talvolta con il codice esadecimale all'interno: □. Per la sua
forma lo si chiama scherzosamente ***tofu***. A differenza del *mojibake*, qui la codifica è giusta e
manca soltanto il disegno. Il progetto di caratteri tipografici liberi **Noto** di Google prende il
nome proprio da questo problema (*no more tofu*) e si propone di coprire tutte le scritture presenti
in Unicode.

!!! warning "Due problemi diversi, due soluzioni diverse"
    Se vedete **caratteri sbagliati** (Ã¨, Ð¶) il problema è la codifica: bisogna dire al programma
    con quale tabella leggere il file. Se vedete **rettangoli vuoti** il problema è il font: bisogna
    installarne uno che copra quella scrittura.

### La direzione della scrittura

L'arabo, l'ebraico, il persiano e l'urdu si scrivono da destra verso sinistra, ma i numeri al loro
interno si scrivono da sinistra verso destra, e un testo può contenere parole in alfabeto latino.
Unicode gestisce queste situazioni con l'**algoritmo bidirezionale**, che stabilisce l'ordine di
visualizzazione dei caratteri a partire dalle loro proprietà. Chi ha provato a inserire una citazione
in arabo dentro un documento italiano sa che il cursore, a volte, sembra impazzire: è l'algoritmo
bidirezionale al lavoro.

!!! question "Per discutere"
    Le decisioni su quali caratteri entrino in Unicode sono prese dal **Consorzio Unicode**,
    un'organizzazione senza fini di lucro i cui membri con pieno diritto di voto sono soprattutto
    grandi aziende tecnologiche. La codifica di una scrittura richiede ricerca, documentazione e
    proposte formali, e molte scritture usate da comunità minoritarie, in Africa e in Asia in
    particolare, sono state aggiunte solo di recente o attendono ancora di esserlo. Per chi le usa,
    scrivere un messaggio sul telefono nella propria lingua è difficile o impossibile.
    Un caso discusso a lungo è quello dell'**unificazione Han**: per ridurre il numero di caratteri,
    Unicode ha assegnato lo stesso punto di codice a ideogrammi cinesi, giapponesi e coreani
    considerati varianti dello stesso carattere, una scelta che alcuni utenti giapponesi hanno
    percepito come una forzatura.
    Chi dovrebbe decidere quali lingue esistano nel mondo digitale, e con quali criteri?

---

## 5. Immagini, suoni, video

### Le immagini

Un'immagine digitale *bitmap* (fotografie, scansioni) è una griglia di **pixel**. Due parametri ne
determinano la qualità:

- la **risoluzione**, cioè il numero di pixel: una foto da 12 megapixel ha, ad esempio,
  4000 × 3000 pixel;
- la **profondità di colore**, cioè quanti bit si usano per ciascun pixel. Nel modello più comune,
  **RGB**, ogni pixel è descritto da tre valori (rosso, verde, blu) di un byte ciascuno, per un totale
  di oltre sedici milioni di colori possibili.

Una foto da 12 megapixel non compressa occupa quindi circa 12 milioni × 3 byte = **36 MB**. Lo stesso
file salvato in JPEG pesa di solito tra 3 e 5 MB.

Accanto alle immagini *bitmap* esistono le immagini **vettoriali** (SVG, molti loghi, i caratteri
tipografici stessi), descritte come insiemi di forme geometriche: "un cerchio di raggio 10 con centro
in (50, 50)". Si possono ingrandire all'infinito senza perdere nitidezza, ma non si prestano a
rappresentare fotografie.

### I suoni

Il suono è un'onda di pressione. Per digitalizzarlo se ne misura l'ampiezza a intervalli regolari:
è il **campionamento**. Un CD audio registra 44.100 campioni al secondo per ciascuno dei due canali
stereo, con 16 bit (due byte) per campione. Un minuto di musica non compressa occupa quindi:

44.100 campioni × 2 byte × 2 canali × 60 secondi ≈ **10,6 MB**

Un file MP3 di qualità media riduce lo stesso minuto a circa 1 MB.

### Il video

Un video è una sequenza di immagini (di solito 24, 25 o 30 al secondo) accompagnata da una traccia
audio. Senza compressione, un minuto di video in alta definizione occuperebbe svariati gigabyte; è per
questo che la compressione video è uno dei campi più sofisticati dell'informatica applicata.

### La compressione

Comprimere significa ridurre lo spazio occupato da un file. Si distinguono due famiglie:

- la compressione **senza perdita** (*lossless*: ZIP, PNG, FLAC) individua regolarità e ripetizioni
  nei dati e le descrive in modo più compatto. Il file originale si può ricostruire esattamente,
  bit per bit;
- la compressione **con perdita** (*lossy*: JPEG, MP3, la maggior parte dei formati video) elimina i
  dettagli che occhio e orecchio umani percepiscono meno. Il risultato è molto più leggero, ma
  l'originale non è più recuperabile, e ogni nuovo salvataggio peggiora un poco la qualità.

Per conservare un documento nel lungo periodo (un archivio, un'edizione digitale, una registrazione
sul campo) si usano formati senza perdita; i formati con perdita vanno bene per la diffusione.

### I metadati nascosti nei file

Molti file contengono, oltre ai dati veri e propri, dei **metadati**, cioè dati che descrivono il
file stesso. Una fotografia scattata con lo smartphone registra di norma, nel formato **EXIF**, la
data e l'ora dello scatto, il modello del telefono e spesso anche le **coordinate GPS** del luogo.
Un documento di Word conserva il nome dell'autore e la cronologia di alcune modifiche.

!!! question "Per discutere"
    Pubblicare online una foto scattata a casa propria può rivelare, attraverso i metadati, l'indirizzo
    esatto in cui è stata scattata. Molti social network rimuovono questi dati al momento del
    caricamento, ma non tutti i servizi lo fanno. Sapevate che le vostre foto contengono queste
    informazioni? Ne riparleremo a proposito di privacy nella L07.

---

## 6. Dove stanno i dati: un ripasso

Nella L01 abbiamo distinto **hardware** e **software** e visto le componenti principali di un computer.
Alla luce di quanto visto oggi possiamo aggiungere un dettaglio: tutto ciò che abbiamo descritto finora
(testi, immagini, suoni) vive come sequenza di byte nella **memoria centrale** (RAM) mentre un programma
lo sta usando, e nella **memoria di massa** (disco, SSD) quando viene salvato. Quando "salviamo nel
*cloud*", quei byte finiscono sui dischi dei server di un'azienda, in un **data center** che ha una sede
fisica, un proprietario e una legislazione di riferimento: ne riparleremo nella L06.

---

## 7. File e formati

### Che cosa c'è in un file

Un **file** è una sequenza di byte a cui il sistema operativo associa un nome e alcune informazioni
(dimensione, data di modifica, permessi). Il **formato** è la convenzione che stabilisce come
interpretare quella sequenza: dove inizia il testo, come sono descritte le immagini, dove si trovano
i metadati.

L'**estensione** (`.txt`, `.docx`, `.pdf`, `.jpg`) è soltanto un'indicazione per il sistema operativo,
che la usa per scegliere con quale programma aprire il file. Rinominare `foto.jpg` in `foto.txt` non
trasforma l'immagine in testo: il contenuto resta lo stesso, e il Blocco note mostrerà soltanto una
serie di simboli incomprensibili.

### Tre grandi famiglie

| Tipo | Esempi | Che cosa contiene | Si apre con |
|---|---|---|---|
| **Testo semplice** | `.txt`, `.csv`, `.md`, `.html`, `.xml`, `.json` | solo caratteri, in una codifica come UTF-8 | qualsiasi editor di testo |
| **Documenti formattati** | `.docx`, `.odt`, `.pdf`, `.epub` | testo, impaginazione, stili, immagini, metadati | programmi specifici |
| **Multimediali** | `.png`, `.jpg`, `.mp3`, `.mp4` | immagini, suoni, video, spesso compressi | visualizzatori e lettori |

!!! example "Che cosa c'è dentro un .docx?"
    Fate una copia di un documento Word, cambiate l'estensione da `.docx` a `.zip` e aprite l'archivio.
    Troverete una serie di cartelle e di file: il testo del documento è in `word/document.xml`, scritto
    in un linguaggio di marcatura (lo vedremo nella L03), mentre le immagini sono nella cartella
    `word/media`. Un `.docx` è dunque un archivio compresso di file di testo strutturato.

### Il PDF

Il **PDF** (*Portable Document Format*) è stato progettato per far apparire un documento identico su
qualsiasi computer e su qualsiasi stampante. Per ottenere questo risultato descrive la **posizione**
di ogni carattere sulla pagina, più che la struttura del testo. Ne derivano problemi ben noti a chi
lavora sui testi: copiando da un PDF si ottengono parole spezzate dalla sillabazione, righe interrotte,
note a piè di pagina mescolate al testo principale, colonne lette nell'ordine sbagliato. Un PDF ottenuto
dalla scansione di un libro, poi, può contenere soltanto immagini, senza alcun testo.

### Formati aperti e proprietari

Un formato è **aperto** quando le sue specifiche sono pubbliche e chiunque può scrivere un programma
in grado di leggerlo e produrlo, senza chiedere permessi né pagare licenze. Sono aperti, ad esempio,
il testo semplice, HTML, XML, PNG, il formato **OpenDocument** (`.odt`) usato da LibreOffice e
normato dallo standard internazionale ISO/IEC 26300, e oggi anche il PDF. Un formato è
**proprietario** quando è controllato da un'azienda, che può modificarlo o smettere di supportarlo.

La scelta del formato ha conseguenze sulla **conservazione a lungo termine**. I file scritti con
programmi molto diffusi negli anni Ottanta e Novanta, come WordStar o le prime versioni di
WordPerfect, sono oggi difficili da aprire; i dischi floppy su cui erano salvati non si leggono più con
i computer attuali. Si parla, con qualche enfasi, del rischio di una *digital dark age*, un'età oscura
digitale in cui una parte della memoria del nostro tempo diventa illeggibile. Per un testo destinato a
durare decenni, un formato aperto e il più semplice possibile resta la scelta più prudente.

!!! tip "Perché vi riguarda"
    Quasi tutti gli strumenti di analisi linguistica (programmi di concordanze, corpora, strumenti di
    NLP) lavorano su **testo semplice in UTF-8**. Un `.docx` o un PDF vanno prima convertiti, e nella
    conversione si perdono o si alterano note, corsivi, caratteri speciali, a volte intere porzioni di
    testo. Conoscere questi passaggi vi risparmierà molte ore quando dovrete preparare un corpus per la
    tesi.

---

## Attività

**Durante la lezione (online)**

1. **Il vostro nome in binario.** Usando la tabella ASCII, scrivete in binario l'iniziale del vostro
   nome e incollatela nella chat. Gli altri devono decifrarla.
2. **Caccia al mojibake.** Ci sono due file con lo stesso testo in cinque lingue,
   [uno salvato in UTF-8](../assets/files/prova-codifica-utf8.txt) e
   [uno salvato in Latin-1](../assets/files/prova-codifica-latin1.txt).
   Apriteli nel browser: quale si legge male, e in che modo? Scaricate poi il file "rotto" e apritelo
   in un editor (Notepad++, VS Code, TextEdit) scegliendo la codifica *Western / ISO 8859-1*. Che cosa
   cambia?
3. **Esplorare Unicode.** Cercate su [Codepoints](https://codepoints.net/) o sulle
   [tabelle ufficiali](https://www.unicode.org/charts/) un carattere della lingua che studiate. Qual è
   il suo punto di codice? A quale blocco appartiene? Quanti byte occupa in UTF-8?
4. **Dentro un .docx.** Seguite le istruzioni del box qui sopra e aprite `word/document.xml`.
   Riuscite a trovare il vostro testo?

**A casa (facoltativo)**

- Prendete una foto scattata con il vostro telefono e controllatene i metadati (su Windows: tasto
  destro → *Proprietà* → *Dettagli*; su macOS: apri con *Anteprima* → *Strumenti* → *Mostra
  ispettore*). Contiene le coordinate GPS?
- Prendete un documento Word con accenti, corsivi e una nota a piè di pagina. Salvatelo come *Testo
  semplice (.txt)* scegliendo la codifica UTF-8 e riapritelo con il Blocco note o TextEdit. Che cosa è
  sopravvissuto alla conversione?

---

## Mettetevi alla prova

**1.** Quante combinazioni diverse si possono rappresentare con 8 bit?

- A. 8
- B. 16
- C. 128
- D. 256

??? success "Soluzione"
    **D.** 2<sup>8</sup> = 256. Le combinazioni di 7 bit, quelle di ASCII, sono 128.

**2.** Il numero binario `00000101` corrisponde in decimale a:

- A. 3
- B. 5
- C. 6
- D. 101

??? success "Soluzione"
    **B.** 4 + 1 = 5.

**3.** Perché i programmatori usano spesso il sistema esadecimale?

- A. Perché i computer funzionano in base 16
- B. Perché ogni cifra esadecimale corrisponde a quattro bit, e un byte si scrive con due cifre
- C. Perché è più preciso del sistema binario
- D. Perché è il sistema usato da ASCII

??? success "Soluzione"
    **B.** Il computer lavora in binario; l'esadecimale è solo un modo più compatto di scrivere i bit.

**4.** Qual è il limite principale della codifica ASCII?

- A. Occupa troppo spazio
- B. Rappresenta soltanto i caratteri dell'alfabeto inglese
- C. Non rappresenta i numeri
- D. Funziona soltanto su computer Apple

??? success "Soluzione"
    **B.** 128 caratteri, senza lettere accentate né alfabeti non latini.

**5.** Un testo mostra "cittÃ " al posto di "città". Qual è la causa più probabile?

- A. Il file è stato danneggiato da un virus
- B. Manca un font adatto a mostrare la lettera
- C. Il file è in UTF-8 ma viene letto con un'altra codifica
- D. Il file è troppo grande

??? success "Soluzione"
    **C.** È un caso di *mojibake*. Se mancasse il font si vedrebbe un rettangolo vuoto (*tofu*).

**6.** Quale affermazione su Unicode e UTF-8 è corretta?

- A. Unicode e UTF-8 sono due nomi dello stesso standard
- B. Unicode assegna un numero a ogni carattere, UTF-8 stabilisce come scrivere quel numero in byte
- C. UTF-8 può rappresentare solo le lingue europee
- D. Unicode è un formato di file per documenti di testo

??? success "Soluzione"
    **B.**

**7.** Due parole visivamente identiche, *café* e *café*, non vengono riconosciute come uguali da un
programma di ricerca. Qual è la spiegazione più probabile?

- A. Una delle due è scritta in un font diverso
- B. L'accento è codificato in un caso come carattere unico, nell'altro come carattere combinante
- C. Una delle due è in maiuscolo
- D. Il programma non supporta il francese

??? success "Soluzione"
    **B.** Per risolvere il problema si normalizza il testo (NFC o NFD).

**8.** La memoria RAM:

- A. conserva i dati anche quando il computer è spento
- B. è la memoria di lavoro del processore, veloce e volatile
- C. è un tipo di processore
- D. è il sistema operativo

??? success "Soluzione"
    **B.** I dati che devono essere conservati vanno salvati sulla memoria di massa.

**9.** Quale di questi formati usa una compressione **senza perdita**?

- A. JPEG
- B. MP3
- C. PNG
- D. MP4

??? success "Soluzione"
    **C.** PNG permette di ricostruire esattamente l'immagine originale.

---

## Per approfondire

- Petzold, C. (2022). *Code: The Hidden Language of Computer Hardware and Software* (2ª ed.). Microsoft Press.
- Spolsky, J. (2003). [*The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets*](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/).
- Il sito del [Consorzio Unicode](https://home.unicode.org/) e quello dello
  [Script Encoding Initiative](https://www.linguistics.berkeley.edu/sei/) (Università di Berkeley),
  che lavora per codificare le scritture ancora escluse.

Elenco completo in [Letture e materiali](../letture.md#blocco-a-fondamenti).

## Parole chiave

[Bit](../glossario.md#bit) ·
[Byte](../glossario.md#byte) ·
[Sistema binario](../glossario.md#sistema-binario) ·
[Esadecimale](../glossario.md#esadecimale) ·
[Codifica dei caratteri](../glossario.md#codifica-dei-caratteri) ·
[ASCII](../glossario.md#ascii) ·
[Unicode](../glossario.md#unicode) ·
[Punto di codice](../glossario.md#punto-di-codice) ·
[UTF-8](../glossario.md#utf-8) ·
[Mojibake](../glossario.md#mojibake) ·
[Normalizzazione](../glossario.md#normalizzazione) ·
[Glifo](../glossario.md#glifo) ·
[Tofu](../glossario.md#tofu) ·
[Pixel](../glossario.md#pixel) ·
[Compressione](../glossario.md#compressione) ·
[Metadati](../glossario.md#metadati) ·
[Hardware](../glossario.md#hardware) ·
[Software](../glossario.md#software) ·
[Sistema operativo](../glossario.md#sistema-operativo) ·
[Formato aperto](../glossario.md#formato-aperto)
