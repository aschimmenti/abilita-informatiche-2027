# L05 · Caso di studio: una bibliografia come base di dati (Zotero)

<p class="meta">Online · 2 ore · Blocco A — Fondamenti · Tutorial</p>

!!! abstract "In sintesi"
    Nelle lezioni precedenti abbiamo parlato di dati, di formati e di strutture in modo generale. Oggi
    li vediamo all'opera in uno strumento che userete per tutta la carriera universitaria: un **gestore
    bibliografico**. Una bibliografia, a guardarla bene, è una piccola base di dati: ogni riferimento è
    un record con dei campi, i tipi di documento sono classi con proprietà diverse, gli ISBN e i DOI sono
    identificativi univoci, e gli stili citazionali sono semplicemente modi diversi di presentare gli
    stessi dati. La lezione è un **tutorial**: costruiremo insieme, passo per passo, una piccola
    biblioteca in **Zotero**, e a ogni passo ci chiederemo quale concetto delle lezioni precedenti stiamo
    usando.

<div class="slides-embed">
  <iframe src="../../slides/L05.html" title="Slide della lezione 5" loading="lazy" allowfullscreen></iframe>
</div>
<p class="slides-links">
  <a class="md-button" href="../../slides/L05.html" target="_blank" rel="noopener">Slide a schermo intero</a>
  <a class="md-button" href="../../slides/L05.pdf" target="_blank" rel="noopener">Slide in PDF</a>
</p>

## Obiettivi

Alla fine della lezione saprete:

- riconoscere in un riferimento bibliografico un **record strutturato**, con campi e valori;
- spiegare perché tipi di documento diversi hanno **campi diversi** (classi e proprietà);
- usare gli **identificativi persistenti** (ISBN, DOI) per recuperare automaticamente i dati;
- capire da dove Zotero ricava i dati quando salvate una pagina web, e perché a volte sbaglia;
- organizzare una biblioteca con collezioni, tag e collegamenti tra elementi;
- esportare gli stessi dati in formati diversi (BibTeX, RIS, CSL JSON) e riconoscerne la struttura;
- inserire citazioni e bibliografia in un documento e cambiarne lo stile senza toccare i dati;
- verificare se un riferimento esiste davvero.

!!! info "Prima della lezione"
    Installate dal sito ufficiale, [zotero.org/download](https://www.zotero.org/download/),
    l'**applicazione** Zotero e il **Zotero Connector** per il vostro browser. Create anche un account
    gratuito su zotero.org: servirà per sincronizzare la biblioteca tra più dispositivi. Se non riuscite,
    seguite comunque la lezione: potete recuperare il tutorial in qualsiasi momento.

---

## 0. Perché un caso di studio

Nella L03 abbiamo visto che **strutturare** i dati significa decidere quali informazioni registrare, in
quali campi, con quali relazioni. Nella L04 abbiamo visto che, una volta strutturati, i dati si possono
**elaborare** con procedure automatiche. Una bibliografia è un ottimo banco di prova per entrambe le
idee, per tre ragioni:

- è un problema **concreto**: dovrete scrivere tesine, relazioni e una tesi, e dovrete citare le fonti;
- è un problema **di dati**: ogni riferimento è fatto di campi (autore, titolo, anno…) che devono essere
  completi, coerenti e corretti;
- è un problema **già risolto bene** da strumenti gratuiti, che mostrano in modo molto chiaro che cosa si
  guadagna quando le informazioni sono strutturate.

Lo strumento che useremo è **Zotero**, un gestore bibliografico **libero e gratuito**, nato nel 2006
alla George Mason University e oggi sviluppato da un'organizzazione senza fini di lucro. Esistono
alternative (Mendeley, EndNote), ma Zotero è il più diffuso nelle scienze umane ed è open source.

---

## Passo 1 · Il primo record: un libro da un ISBN

### Che cosa fare

1. Aprite Zotero.
2. Cliccate sull'icona della **bacchetta magica** (*Aggiungi elemento tramite identificativo*).
3. Incollate questo ISBN: `9788806253301` e premete Invio.

Dopo qualche secondo compare un nuovo elemento: *L'intelligenza artificiale. Una guida per esseri
umani pensanti* di Melanie Mitchell, Einaudi, 2022. Selezionatelo e guardate il riquadro a destra.

### Che cosa è successo

Avete inserito un solo dato, l'ISBN, e Zotero ha compilato tutti gli altri campi. Lo ha fatto
interrogando un catalogo bibliografico che conosce quell'identificativo, e da cui ha ricevuto un
**record strutturato**.

Il riquadro di destra mostra il record nella sua forma più semplice: una serie di coppie **campo →
valore**, cioè esattamente il **dizionario** della L03.

| Campo | Valore |
|---|---|
| Tipo di elemento | Libro |
| Titolo | L'intelligenza artificiale: una guida per esseri umani pensanti |
| Autore | Mitchell, Melanie |
| Luogo | Torino |
| Editore | Einaudi |
| Data | 2022 |
| ISBN | 9788806253301 |

!!! tip "Il concetto: identificativo univoco"
    L'ISBN identifica in modo univoco **una specifica edizione** di un libro. È la stessa idea degli
    identificativi di Wikidata (Q652 per la lingua italiana): un codice che non è ambiguo e che permette
    a sistemi diversi di riferirsi alla stessa cosa. Una curiosità che ci riporta alla L04: l'ultima
    cifra dell'ISBN è una **cifra di controllo**, calcolata dalle altre con un piccolo algoritmo, che
    permette di accorgersi degli errori di battitura.

??? example "Approfondimento: verificare la cifra di controllo"
    Si moltiplicano le prime dodici cifre alternativamente per 1 e per 3, si sommano i prodotti e si
    prende il numero che manca per arrivare al multiplo di 10 successivo.

    | Cifra | 9 | 7 | 8 | 8 | 8 | 0 | 6 | 2 | 5 | 3 | 3 | 0 |
    |---|---|---|---|---|---|---|---|---|---|---|---|---|
    | Peso | 1 | 3 | 1 | 3 | 1 | 3 | 1 | 3 | 1 | 3 | 1 | 3 |
    | Prodotto | 9 | 21 | 8 | 24 | 8 | 0 | 6 | 6 | 5 | 9 | 3 | 0 |

    La somma è 99, al 100 manca 1: l'ISBN termina infatti con **1**.

---

## Passo 2 · Un articolo da un DOI: classi diverse, campi diversi

### Che cosa fare

1. Bacchetta magica di nuovo, questa volta con il DOI `10.1162/tacl_a_00401`.
2. Selezionate il nuovo elemento e confrontate i suoi campi con quelli del libro.

### Che cosa è successo

Il nuovo elemento è un **articolo di rivista** (*Gender Bias in Machine Translation*, di Savoldi e
colleghi, 2021) e i suoi campi sono diversi da quelli del libro:

| Libro | Articolo di rivista |
|---|---|
| Titolo | Titolo |
| Autore | Autore (cinque) |
| Luogo, Editore | **Pubblicazione** (il nome della rivista) |
| — | **Volume**, **Fascicolo**, **Pagine** |
| ISBN | **DOI**, **ISSN** |

Zotero prevede decine di **tipi di elemento**: libro, sezione di un libro, articolo di rivista, articolo
di giornale, tesi, pagina web, manoscritto, lettera, intervista, film, registrazione audio, dataset,
software, e altri ancora. Ciascuno ha il proprio insieme di campi.

!!! tip "Il concetto: classi e proprietà"
    È esattamente il livello **terminologico** dei grafi di conoscenza visto nella L03. Ogni tipo di
    elemento è una **classe**, e ogni classe ha le sue **proprietà**: un *Articolo di rivista* ha un
    volume e un fascicolo, un *Libro* ha un editore e un luogo di edizione, un *Capitolo* ha un libro che
    lo contiene. Lo schema decide che cosa si può dire, e che cosa no: provate a cercare dove registrare,
    in un libro, il fatto che è la traduzione di un'opera scritta in un'altra lingua.

### Due pause di riflessione

- Cambiate il tipo dell'articolo in *Libro* (menu a tendina *Tipo di elemento*) e osservate che cosa
  succede ai campi. Zotero vi avvisa che alcuni dati andranno persi: non esiste un posto, in un libro,
  per il volume di una rivista. Riportatelo poi ad *Articolo di rivista*.
- Il DOI funziona come l'ISBN, ma per oggetti digitali: articoli, capitoli, dataset. Aprite nel browser
  `https://doi.org/10.1162/tacl_a_00401`: il DOI vi porta all'articolo dovunque si trovi oggi, anche se
  l'editore ha cambiato sito. È un **identificativo persistente**, al contrario di un normale indirizzo
  web, che può smettere di funzionare.

---

## Passo 3 · Dalla pagina web al record: da dove vengono i dati?

### Che cosa fare

1. Aprite nel browser la pagina dell'articolo di Bender e Koller sull'ACL Anthology:
   [aclanthology.org/2020.acl-main.463](https://aclanthology.org/2020.acl-main.463/).
2. Cliccate sull'icona del **Zotero Connector** nella barra del browser. L'articolo viene salvato in
   Zotero, spesso insieme al PDF.
3. Ora, sulla stessa pagina, aprite il **codice sorgente** (tasto destro → *Visualizza sorgente pagina*,
   oppure `Ctrl+U` / `Cmd+Opt+U`) e cercate (`Ctrl+F`) la parola `citation_title`.

### Che cosa è successo

Nel codice HTML della pagina troverete righe simili a queste (qui leggermente semplificate):

```html
<meta name="citation_title" content="Climbing towards NLU: On Meaning, Form, and Understanding in the Age of Data">
<meta name="citation_author" content="Bender, Emily M.">
<meta name="citation_author" content="Koller, Alexander">
<meta name="citation_conference_title" content="Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics">
<meta name="citation_publication_date" content="2020/7">
<meta name="citation_doi" content="10.18653/v1/2020.acl-main.463">
```

Sono **metadati** nascosti nella pagina, scritti con un **linguaggio di marcatura** (HTML) e pensati per
essere letti dalle macchine, non dalle persone: il browser non li mostra, ma Zotero, Google Scholar e
altri programmi sì. Il connettore di Zotero contiene centinaia di piccoli programmi, chiamati
*translator*, ciascuno specializzato nel leggere i dati di un certo sito (un catalogo di biblioteca, un
editore, un giornale, Wikipedia) e trasformarli in un record.

!!! tip "Il concetto: dati strutturati dentro un documento"
    Una pagina web contiene due livelli: il testo per gli esseri umani e, a volte, dei dati strutturati
    per le macchine. Quando i secondi mancano o sono sbagliati, Zotero deve indovinare, e spesso sbaglia.
    È la stessa differenza vista nella L01 tra Wikipedia, scritta per le persone, e Wikidata, scritta
    anche per le macchine.

### Provate con altre fonti

Salvate con il connettore anche:

- la scheda di un libro dall'[OPAC SBN](https://opac.sbn.it/), il catalogo delle biblioteche italiane;
- un articolo di un quotidiano online;
- una voce di Wikipedia.

Per ciascuno, controllate quale **tipo di elemento** ha scelto Zotero e quali campi ha compilato.

---

## Passo 4 · La qualità dei dati: trovare e correggere gli errori

### Che cosa fare

Guardate con attenzione gli elementi che avete salvato. Quasi certamente troverete qualcuno di questi
problemi:

- un titolo scritto **TUTTO IN MAIUSCOLO**, o con le maiuscole all'inglese (*Title Case*) in un titolo
  italiano;
- un autore con nome e cognome invertiti, o un ente (*Ministero della Cultura*) registrato come se fosse
  una persona con nome e cognome;
- un tipo di elemento sbagliato (una pagina web registrata come articolo, un capitolo come libro);
- un campo vuoto (le pagine, il luogo di edizione, l'editore);
- la data della ristampa al posto di quella della prima edizione.

Correggete almeno due errori. Per gli autori, cliccate sull'icona accanto al nome per passare dalla
modalità a due campi (cognome, nome) a quella a campo unico, adatta agli enti.

### Che cosa impariamo

I dati recuperati automaticamente sono **affidabili quanto la fonte** da cui provengono. Strutturare i
dati non basta: bisogna anche **controllarli**. È la stessa lezione dei *capta* della L01: ogni dato è
stato preso da qualcuno, in un certo modo, e porta con sé gli errori di quel passaggio.

!!! example "Elementi duplicati"
    Salvate di nuovo, con il connettore o con il DOI, l'articolo di Savoldi. Poi aprite la voce
    *Elementi duplicati* nel pannello di sinistra: Zotero ha riconosciuto che i due record descrivono lo
    stesso oggetto e vi propone di unirli. Capire quando due descrizioni diverse si riferiscono alla
    stessa cosa è un problema classico della gestione dei dati, e gli identificativi univoci (qui il
    DOI) lo rendono molto più semplice.

---

## Passo 5 · Organizzare: alberi, etichette e collegamenti

### Che cosa fare

1. Create una **collezione** chiamata *Abilità Informatiche* (tasto destro su *La mia biblioteca* →
   *Nuova collezione*), e al suo interno due **sottocollezioni**: *Traduzione automatica* e *Dati e AI*.
2. Trascinate gli elementi nelle collezioni giuste. Mettete l'articolo di Savoldi **in entrambe**.
3. Aggiungete dei **tag** (scheda *Tag* del riquadro di destra): ad esempio `bias`, `da leggere`,
   `inglese`.
4. Collegate due elementi tra loro con la scheda *Correlati*: ad esempio l'articolo di Bender e Koller e
   il libro di Mitchell.

### Che cosa è successo

Avete usato tre strutture diverse, che conoscete dalla L03:

| In Zotero | Struttura | Che cosa permette |
|---|---|---|
| Collezioni e sottocollezioni | **albero** | una gerarchia, come le cartelle |
| Tag | **etichette molti-a-molti** | ogni elemento può avere più tag, ogni tag più elementi |
| Elementi correlati | **grafo** | collegamenti liberi tra elementi |

C'è però una differenza importante rispetto alle cartelle del computer: uno stesso elemento può stare
in **più collezioni senza essere duplicato**. Le collezioni non contengono gli elementi, contengono dei
**riferimenti** agli elementi, che esistono una volta sola nella biblioteca.

??? info "Dove sta, fisicamente, la vostra biblioteca?"
    Zotero conserva tutti i dati in un file chiamato `zotero.sqlite`, nella cartella *Zotero* del vostro
    computer. È una **base di dati relazionale**: un insieme di tabelle collegate tra loro (una per gli
    elementi, una per i campi, una per gli autori, una per le collezioni, una per i tag…). Quello che
    vedete nell'interfaccia è una presentazione di queste tabelle. Non modificate mai quel file a mano.

---

## Passo 6 · Esportare: stessi dati, sintassi diverse

### Che cosa fare

1. Tasto destro sulla collezione *Abilità Informatiche* → *Esporta collezione…*.
2. Esportatela tre volte, nei formati **BibTeX**, **RIS** e **CSL JSON**.
3. Aprite i tre file con un editor di testo (Blocco note, TextEdit, VS Code).

### Che cosa troverete

Ecco l'articolo di Savoldi nei tre formati (i file reali possono contenere qualche campo in più):

=== "BibTeX"

    ```text
    @article{savoldi_gender_2021,
      title   = {Gender Bias in Machine Translation},
      author  = {Savoldi, Beatrice and Gaido, Marco and Bentivogli, Luisa
                 and Negri, Matteo and Turchi, Marco},
      journal = {Transactions of the Association for Computational Linguistics},
      volume  = {9},
      pages   = {845--874},
      year    = {2021},
      doi     = {10.1162/tacl_a_00401}
    }
    ```

=== "RIS"

    ```text
    TY  - JOUR
    TI  - Gender Bias in Machine Translation
    AU  - Savoldi, Beatrice
    AU  - Gaido, Marco
    AU  - Bentivogli, Luisa
    AU  - Negri, Matteo
    AU  - Turchi, Marco
    T2  - Transactions of the Association for Computational Linguistics
    VL  - 9
    SP  - 845
    EP  - 874
    PY  - 2021
    DO  - 10.1162/tacl_a_00401
    ER  -
    ```

=== "CSL JSON"

    ```json
    {
      "type": "article-journal",
      "title": "Gender Bias in Machine Translation",
      "author": [
        { "family": "Savoldi", "given": "Beatrice" },
        { "family": "Gaido", "given": "Marco" },
        { "family": "Bentivogli", "given": "Luisa" },
        { "family": "Negri", "given": "Matteo" },
        { "family": "Turchi", "given": "Marco" }
      ],
      "container-title": "Transactions of the Association for Computational Linguistics",
      "volume": "9",
      "page": "845-874",
      "issued": { "date-parts": [[2021]] },
      "DOI": "10.1162/tacl_a_00401"
    }
    ```

### Che cosa impariamo

I tre file contengono **gli stessi dati** scritti con **sintassi diverse**, esattamente come la tabella
della L03 scritta in CSV, JSON e XML. Notate le differenze:

- in **BibTeX** gli autori sono una sola stringa separata da `and`; in **CSL JSON** sono una **lista**
  di **dizionari**, ciascuno con cognome e nome separati;
- in **RIS** ogni riga comincia con un codice di due lettere (`TY` per il tipo, `AU` per l'autore,
  `ER` per la fine del record) e un autore ripetuto significa più autori;
- le pagine sono scritte `845--874` in BibTeX e `845-874` in CSL JSON, oppure divise in due campi
  (`SP` e `EP`) in RIS.

Nessuno di questi formati è "quello giusto": ciascuno è nato per un programma o una comunità diversa
(BibTeX per LaTeX, RIS per le banche dati bibliografiche, CSL JSON per i sistemi che usano gli stili
CSL). Saperli riconoscere vi permette di spostare la vostra bibliografia da un programma all'altro
senza ricopiarla.

---

## Passo 7 · Citare: i dati restano, la presentazione cambia

### Che cosa fare

1. Aprite un documento di Word, LibreOffice Writer o Google Documenti. Nella barra comparirà una scheda
   o un menu *Zotero* (per Google Documenti il comando si trova nel menu *Zotero* aggiunto dal
   connettore).
2. Scrivete una frase e cliccate su *Add/Edit Citation*. Digitate il cognome di un autore, selezionate
   il riferimento, premete Invio. Alla prima citazione Zotero vi chiede di scegliere uno stile:
   scegliete **APA**.
3. Inserite altre due citazioni, poi andate in fondo al documento e cliccate su *Add/Edit
   Bibliography*.
4. Cliccate su *Document Preferences* e cambiate stile: provate **Chicago (note)**, poi uno stile
   numerico come **IEEE**.

### Che cosa è successo

Citazioni e bibliografia si sono riscritte da sole, con un ordine, una punteggiatura e un uso del
corsivo completamente diversi. I dati non sono cambiati: è cambiata soltanto la loro **presentazione**.

Ecco lo stesso articolo in due stili:

APA
: Savoldi, B., Gaido, M., Bentivogli, L., Negri, M., & Turchi, M. (2021). Gender bias in machine
  translation. *Transactions of the Association for Computational Linguistics*, *9*, 845–874.
  https://doi.org/10.1162/tacl_a_00401

IEEE
: [1] B. Savoldi, M. Gaido, L. Bentivogli, M. Negri, and M. Turchi, "Gender bias in machine
  translation," *Trans. Assoc. Comput. Linguist.*, vol. 9, pp. 845–874, 2021.

!!! tip "Il concetto: separare i dati dalla presentazione"
    È lo stesso principio della **marcatura descrittiva** vista nella L03, e lo ritroveremo nel web
    con HTML e CSS (L08). Gli stili citazionali usati da Zotero sono a loro volta descritti in un
    linguaggio basato su XML, il **CSL** (*Citation Style Language*), e ne esistono oltre diecimila.
    Quale stile usare non è una questione tecnica: dipende da ciò che vi chiede il relatore, la rivista o
    il corso. Con i dati strutturati, cambiarlo costa un clic.

!!! warning "Non correggete a mano le citazioni nel documento"
    Le citazioni inserite da Zotero sono collegate alla biblioteca. Se trovate un errore, correggetelo in
    Zotero e cliccate su *Refresh*: la correzione si propagherà a tutto il documento.

---

## Passo 8 · Verificare: un riferimento esiste davvero?

I chatbot basati su modelli linguistici producono con grande facilità testi che **sembrano**
riferimenti bibliografici: autori plausibili, titoli coerenti, riviste esistenti, persino DOI
formalmente corretti. Ma un modello linguistico genera testo prevedendo le parole più probabili, senza
consultare un catalogo (lo vedremo nella L13), e il risultato può essere un riferimento inesistente.

In uno studio del 2023, Walters e Wilder hanno verificato una per una 636 citazioni prodotte da ChatGPT:
il 55% di quelle generate con GPT-3.5 e il 18% di quelle generate con GPT-4 si riferivano a
pubblicazioni **inesistenti**. I modelli più recenti sbagliano meno, soprattutto quando possono cercare
sul web, ma nessuno offre garanzie.

Qui torna utile tutto ciò che abbiamo fatto oggi: un riferimento con un DOI o un ISBN si può
**verificare** in pochi secondi, ad esempio provando ad aggiungerlo a Zotero con la bacchetta magica.

!!! example "Esercizio: trovate il riferimento inventato"
    Provate ad aggiungere a Zotero, tramite DOI, questi quattro riferimenti. Uno è stato inventato per
    questo esercizio. Quale?

    1. Joshi et al. (2020). The state and fate of linguistic diversity and inclusion in the NLP world.
       DOI `10.18653/v1/2020.acl-main.560`
    2. Bianchi & Moreau (2022). Neural approaches to Leopardi's prosody: A corpus study.
       *Journal of Digital Philology*, 14(2). DOI `10.5555/jdp.2022.0142`
    3. Rowley (2007). The wisdom hierarchy: Representations of the DIKW hierarchy.
       DOI `10.1177/0165551506070706`
    4. Vrandečić & Krötzsch (2014). Wikidata: A free collaborative knowledgebase.
       DOI `10.1145/2629489`

    ??? success "Soluzione"
        Il **2**. Zotero non trova nulla, il DOI non porta a nessun articolo e la rivista non esiste.
        A una prima lettura, però, il riferimento non ha nulla di diverso dagli altri.

---

## Riepilogo: che cosa abbiamo visto, e dove

| Passo | Che cosa abbiamo fatto | Concetto | Lezione |
|---|---|---|---|
| 1 | aggiunto un libro da un ISBN | record come dizionario campo → valore; identificativo univoco | L03 |
| 2 | aggiunto un articolo da un DOI | classi e proprietà; identificativo persistente | L03 |
| 3 | salvato una pagina web | metadati in HTML, dati per le persone e per le macchine | L01, L03 |
| 4 | corretto e unito i record | qualità dei dati, duplicati | L01 |
| 5 | collezioni, tag, correlati | albero, etichette, grafo | L03 |
| 6 | esportato in BibTeX, RIS, CSL JSON | stessi dati, sintassi diverse | L02, L03 |
| 7 | citato e cambiato stile | separazione tra dati e presentazione | L03 |
| 8 | verificato un riferimento | identificativi come strumento di controllo | L13 |

---

## Attività

**Durante la lezione (online)**

Seguite il tutorial passo per passo. Alla fine dovreste avere una collezione *Abilità Informatiche* con
almeno cinque elementi di tipi diversi, corretti, organizzati in sottocollezioni con dei tag, esportati
in tre formati e citati in un documento.

**A casa (facoltativo)**

- Create una collezione per la vostra prossima tesina o relazione e salvate con il connettore almeno
  dieci fonti. Controllate e correggete i dati di ciascuna.
- Chiedete a un chatbot di suggerirvi cinque articoli scientifici su un argomento del vostro piano di
  studi, con i relativi DOI, e verificateli con Zotero. Quanti esistono davvero? Quanti hanno dati
  corretti?

---

## Mettetevi alla prova

**1.** In Zotero, un riferimento bibliografico è rappresentato come:

- A. un'immagine della copertina
- B. un insieme di coppie campo → valore
- C. un file PDF
- D. una riga di testo libero

??? success "Soluzione"
    **B.** È un record strutturato, simile a un dizionario.

**2.** Perché un *Libro* e un *Articolo di rivista* hanno campi diversi in Zotero?

- A. Per un errore del programma
- B. Perché sono classi diverse, ciascuna con le proprie proprietà
- C. Perché gli articoli non hanno autori
- D. Perché i libri non hanno titolo

??? success "Soluzione"
    **B.** È il livello terminologico, o schema, visto nella L03.

**3.** A che cosa serve un DOI?

- A. A identificare in modo univoco e persistente un oggetto digitale, come un articolo
- B. A identificare un autore
- C. A comprimere un PDF
- D. A indicare lo stile citazionale

??? success "Soluzione"
    **A.** Per gli autori si usa l'ORCID.

**4.** Quando salvate una pagina web con il Zotero Connector, da dove provengono di solito i dati?

- A. Zotero legge e interpreta il testo come farebbe una persona
- B. Da metadati strutturati inseriti nel codice HTML della pagina, letti da appositi *translator*
- C. Da un database di Google
- D. L'utente li deve sempre inserire a mano

??? success "Soluzione"
    **B.** Quando questi metadati mancano o sono sbagliati, anche il record di Zotero lo sarà.

**5.** In Zotero lo stesso elemento può stare in due collezioni diverse. Che cosa significa?

- A. L'elemento viene copiato due volte
- B. Le collezioni contengono riferimenti all'elemento, che esiste una sola volta nella biblioteca
- C. È un errore da correggere con la funzione duplicati
- D. L'elemento viene spostato dalla prima alla seconda collezione

??? success "Soluzione"
    **B.**

**6.** BibTeX, RIS e CSL JSON sono:

- A. tre stili citazionali
- B. tre formati diversi per scrivere gli stessi dati bibliografici
- C. tre versioni di Zotero
- D. tre tipi di identificativo

??? success "Soluzione"
    **B.** Lo stile citazionale riguarda invece la presentazione dei dati in un documento.

**7.** Cambiando lo stile citazionale in un documento gestito con Zotero:

- A. bisogna reinserire tutte le citazioni
- B. si modificano i dati della biblioteca
- C. cambia soltanto la presentazione, mentre i dati restano gli stessi
- D. si perdono le citazioni già inserite

??? success "Soluzione"
    **C.**

**8.** Un chatbot vi suggerisce un articolo con un DOI. Qual è il modo più rapido per verificarlo?

- A. Chiedere allo stesso chatbot se esiste
- B. Provare ad aggiungerlo a Zotero tramite DOI, o aprire `https://doi.org/` seguito dal DOI
- C. Controllare che il titolo sia pertinente
- D. Fidarsi, perché il DOI ha un formato corretto

??? success "Soluzione"
    **B.** Un DOI formalmente corretto può essere inventato.

---

## Per approfondire

- La [documentazione ufficiale di Zotero](https://www.zotero.org/support/), con guide per ogni funzione.
- Il sito del [Citation Style Language](https://citationstyles.org/) e il
  [repertorio degli stili di Zotero](https://www.zotero.org/styles).
- Walters, W. H., & Wilder, E. I. (2023). Fabrication and errors in the bibliographic citations
  generated by ChatGPT. *Scientific Reports*, *13*, 14045.
  [doi:10.1038/s41598-023-41032-5](https://doi.org/10.1038/s41598-023-41032-5)

Elenco completo in [Letture e materiali](../letture.md#blocco-a-fondamenti).

## Parole chiave

[Gestore bibliografico](../glossario.md#gestore-bibliografico) ·
[Riferimento bibliografico](../glossario.md#riferimento-bibliografico) ·
[Metadati](../glossario.md#metadati) ·
[Identificativo persistente](../glossario.md#identificativo-persistente) ·
[ISBN](../glossario.md#isbn) ·
[DOI](../glossario.md#doi) ·
[Cifra di controllo](../glossario.md#cifra-di-controllo) ·
[BibTeX](../glossario.md#bibtex) ·
[Stile citazionale](../glossario.md#stile-citazionale) ·
[CSL](../glossario.md#csl-citation-style-language) ·
[Struttura dati](../glossario.md#struttura-dati) ·
[Albero](../glossario.md#albero) ·
[Grafo](../glossario.md#grafo)
