# Programma del corso

Il corso è diviso in **quattro blocchi** e **16 lezioni**, di cui tre in presenza (:material-account-group:)
e tredici online (:material-laptop:). Ogni lezione dura circa due ore.

Tre temi attraversano tutti i blocchi:

- **il linguaggio come dato**: come un testo diventa qualcosa che una macchina può contare, cercare,
  tradurre e generare;
- **gli aspetti sociali**: chi è rappresentato nei dati e chi ne resta escluso, chi prende le decisioni,
  chi ne sostiene i costi;
- **l'uso consapevole degli strumenti**: sapere abbastanza di come funzionano per servirsene con giudizio.

---

## Blocco A · Fondamenti

*Che cosa fa davvero un computer con le informazioni, e come si organizzano i dati di una ricerca.*

### L01 · Dati e macchine :material-account-group:
Quiz di benchmark su Kahoot e domande per alzata di mano. Che cosa sono i dati, e perché nessun dato è
del tutto neutrale; dataset e corpora. Perché i dati servono: la mappa del colera di John Snow (Londra,
1854). Che cosa ce ne facciamo dei dati quando studiamo le lingue: organizzare, cercare pattern,
analizzare su larga scala; linguistica dei corpora, annotazione, modelli linguistici. Rendere computabile
ciò che non lo è. Una breve storia: Ada Lovelace, le schede perforate di Hollerith, Turing e Bletchley
Park, Warren Weaver e l'idea della traduzione come decifrazione. Dare istruzioni a una macchina:
interfacce, hardware e software; strutture dati, linguaggi di programmazione, linguaggi di marcatura.
Esempi dal vivo: Wikidata e il corpus DiaCORIS.
→ [Vai alla lezione](lezioni/01-dati-e-macchine.md)

### L02 · Come si rappresenta l'informazione :material-account-group:
Bit e byte, sistema binario ed esadecimale, unità di misura. La codifica dei testi: ASCII, le codifiche
nazionali, il *mojibake*, Unicode e UTF-8, la normalizzazione, le emoji. Carattere e glifo, il *tofu*, la
scrittura bidirezionale; chi decide quali scritture esistono nel digitale. Immagini, suoni, video e
compressione; i metadati nascosti nei file. Hardware, software, sistema operativo, *cloud*. File e
formati, formati aperti e conservazione a lungo termine.
→ [Vai alla lezione](lezioni/02-rappresentazione.md)

### L03 · Strutturare i dati :material-account-group:
Strutturare ed elaborare. Le strutture dati fondamentali: lista, dizionario, tabella, albero, grafo.
I formati CSV, JSON e XML. I linguaggi di marcatura: storia, sintassi, HTML, XML e TEI. I grafi di
conoscenza: triple, classi, proprietà, identificativi, Linked Open Data. Un accenno all'estrazione
automatica di entità e relazioni. Le scelte (e le esclusioni) implicite in ogni struttura.
→ [Vai alla lezione](lezioni/03-strutturare-i-dati.md)

### L04 · Algoritmi e pensiero computazionale :material-laptop:
I quattro principi del pensiero computazionale. Che cos'è un algoritmo; la ricetta riscritta per una
macchina. Linguaggio naturale, pseudocodice, diagrammi di flusso e un primo programma in Python.
Sequenza, selezione, iterazione. Un algoritmo per il plurale e le sue eccezioni. Ordinare e cercare
nelle diverse lingue; ricerca lineare e binaria. "L'algoritmo" nel discorso pubblico.
→ [Vai alla lezione](lezioni/04-algoritmi.md)

### L05 · Gestire la bibliografia: standard, identificativi, Zotero :material-laptop:
Anatomia di un riferimento bibliografico e metadati. Gli stili citazionali (autore-data, note, numerici)
e il Citation Style Language. Identificativi persistenti: ISBN, ISSN, DOI, ORCID, Handle. Dove trovare i
riferimenti. Zotero: installazione, importazione, organizzazione, citazione in Word, LibreOffice e
Google Documenti. I riferimenti inventati dai chatbot e come riconoscerli.
→ [Vai alla lezione](lezioni/05-bibliografia-e-zotero.md)

---

## Blocco B · Internet e Web

*Come funziona la rete che usiamo ogni giorno, e come ci si pubblica qualcosa di proprio.*

### L06 · Internet: la rete delle reti :material-laptop:
Breve storia: ARPANET, TCP/IP, la nascita di Internet in Italia. Come viaggiano i dati: pacchetti,
indirizzi IP, router, DNS, il modello client/server. L'infrastruttura fisica: cavi sottomarini, data
center, consumi. Il *digital divide* e le lingue di Internet: il peso dell'inglese, i domini con
caratteri non latini, le lingue minoritarie in rete.

### L07 · Il Web e la società :material-laptop:
Tim Berners-Lee e il CERN, l'ipertesto, URL, HTTP, browser e server. Come funziona un motore di ricerca
e come cercare meglio. Algoritmi di raccomandazione, bolle informative, disinformazione. Tracce
digitali, cookie, GDPR e diritti dell'interessato. Licenze e diritto d'autore in rete.

### L08 · Laboratorio: costruire e pubblicare una pagina web :material-laptop:
HTML in pratica, a partire da quanto visto sui linguaggi di marcatura nella L03: struttura del
documento, titoli, paragrafi, elenchi, link, immagini, tabelle. L'attributo `lang` e la codifica: una
pagina bilingue. Accessibilità di base. Le basi di CSS. Pubblicare la pagina con GitHub Pages partendo
da un modello, senza riga di comando. Risultato: ognuno ha un indirizzo web pubblico.

---

## Blocco C · Natural Language Processing

*Che cosa succede quando una macchina tratta una lingua, e come può aiutare la vostra ricerca.*

### L09 · Il linguaggio come dato :material-laptop:
Che cos'è un corpus. Dal testo ai *token*: tokenizzazione, lemmatizzazione, frequenze, la legge di Zipf.
Concordanze e collocazioni. I livelli dell'analisi linguistica visti da una macchina: *part-of-speech
tagging*, analisi a dipendenze, Universal Dependencies. L'ambiguità come problema centrale.
Esercitazione con Voyant Tools e con strumenti di analisi online.

### L10 · Dalle regole alla statistica: la traduzione automatica :material-laptop:
L'esperimento Georgetown-IBM (1954) e il rapporto ALPAC (1966). Traduzione basata su regole, statistica,
neurale. Il significato come vicinanza: i *word embeddings*. Il bias nella traduzione automatica, in
particolare quello di genere. Che cosa cambia per chi traduce di mestiere.

### L11 · NLP al servizio della ricerca :material-laptop:
Corpora di riferimento e Sketch Engine. Riconoscimento di entità, analisi del *sentiment*, *topic
modelling*. Lingue con poche risorse e disuguaglianze tra lingue nel NLP. Mini-esercizio su una vostra
domanda di ricerca.

---

## Blocco D · Intelligenza artificiale e LLM

*Che cos'è l'AI, come funzionano i modelli linguistici, come usarli bene e che cosa comportano.*

### L12 · Che cos'è l'intelligenza artificiale :material-laptop:
Ragionamento, apprendimento, azione autonoma. Una storia per tappe: il test di Turing, Dartmouth, ELIZA
e l'effetto ELIZA, i sistemi esperti, il *machine learning*. Apprendimento supervisionato, non
supervisionato, per rinforzo. Reti neurali e *deep learning*, spiegati in modo intuitivo.

### L13 · Come funziona un Large Language Model :material-laptop:
La previsione del token successivo. L'architettura Transformer e il meccanismo di attenzione, senza
matematica. Pre-addestramento, *fine-tuning*, feedback umano. Perché i modelli producono "allucinazioni".
Tokenizzazione e lingue: perché non tutte le lingue costano allo stesso modo. Modelli multimodali.

### L14 · Usare l'AI senza esserne sopraffatti :material-laptop:
Che cosa delegare e che cosa no. Il *prompting*: contesto, obiettivo, vincoli, esempi, iterazione.
Verificare fonti e citazioni. Usi concreti per lo studio, la traduzione, la scrittura e la ricerca.
Integrità accademica e linee guida d'Ateneo. Esercitazione su un vostro compito reale.

### L15 · Etica, diritto e società :material-laptop:
Bias nei dati e nei modelli. L'AI Act europeo e i livelli di rischio. Dati di addestramento e diritto
d'autore. L'impatto sul lavoro di traduttori, interpreti, redattori. Costo ambientale. Deepfake e
disinformazione. Discussione strutturata.

---

## Chiusura

### L16 · Com'è andata? Ripasso e simulazione :material-laptop:
Rifacciamo il gioco della prima lezione e confrontiamo i risultati. Ripasso dei concetti chiave dei
quattro blocchi. Simulazione d'esame e domande aperte.
