# L07 · Il Web e la società

<p class="meta">Online · 2 ore · Blocco B — Internet e Web</p>

!!! abstract "In sintesi"
    Nella lezione precedente abbiamo visto Internet, l'infrastruttura. Oggi parliamo del servizio che
    usiamo di più tra quelli costruiti sopra di essa: il **World Wide Web**. Partiamo dall'idea di
    ipertesto, che è molto più antica dei computer, e arriviamo al CERN, dove Tim Berners-Lee inventa
    URL, HTTP e HTML. Poi guardiamo come si trovano le informazioni in un Web di miliardi di pagine
    (motori di ricerca, ranking, raccomandazioni) e che cosa comporta per il modo in cui ci informiamo.
    Chiudiamo con le tracce che lasciamo navigando, con i diritti che il GDPR ci riconosce e con le
    licenze che regolano il riuso di testi e immagini in rete.

<div class="slides-embed">
  <iframe src="../../slides/L07.html" title="Slide della lezione 7" loading="lazy" allowfullscreen></iframe>
</div>
<p class="slides-links">
  <a class="md-button" href="../../slides/L07.html" target="_blank" rel="noopener">Slide a schermo intero</a>
  <a class="md-button" href="../../slides/L07.pdf" target="_blank" rel="noopener">Slide in PDF</a>
</p>

## Obiettivi

Alla fine della lezione saprete:

- definire un **ipertesto** e riconoscerne gli elementi (nodi, ancore, link);
- raccontare come e perché è nato il **World Wide Web**, e in che cosa si distingue da Internet;
- scomporre un **URL** nelle sue parti e leggere una richiesta e una risposta **HTTP**;
- spiegare come funziona un **motore di ricerca** e usare gli operatori di ricerca avanzata;
- descrivere i **sistemi di raccomandazione** e discutere con dati alla mano bolle informative e
  disinformazione;
- distinguere i tipi di **cookie** e conoscere i vostri **diritti** secondo il GDPR;
- riconoscere le principali **licenze Creative Commons** e scegliere materiali riusabili.

!!! info "Prima della lezione"
    Usate un browser per computer (Firefox, Chrome, Edge o Safari): in un paio di esercizi apriremo gli
    **strumenti per sviluppatori**, che sui telefoni non sono disponibili. Su Safari vanno prima attivati
    da *Impostazioni → Avanzate → Mostra funzionalità per sviluppatori web*.

---

## 1. Dall'ipertesto al Web

### Che cos'è un ipertesto

Un testo normale si legge in un ordine stabilito dall'autore, dalla prima pagina all'ultima. Un
**ipertesto** è invece un insieme di testi collegati, che il lettore può percorrere in ordini diversi
seguendo dei collegamenti. Gli elementi sono tre:

- i **nodi**, cioè le unità di informazione (una pagina, un paragrafo, un'immagine);
- le **ancore**, i punti di un nodo da cui parte o in cui arriva un collegamento;
- i **link**, i collegamenti tra un'ancora e l'altra.

Nella L03 abbiamo incontrato i **grafi**: un ipertesto è un grafo **orientato**, perché un link va da A
a B ma non necessariamente da B ad A.

L'idea è molto più antica dei computer. Le glosse nei margini dei manoscritti medievali, le note a piè
di pagina, i rimandi di un dizionario ("→ vedi anche") sono già collegamenti tra testi. Alcuni
scrittori ne hanno fatto un principio di costruzione dell'opera: *Rayuela* (in italiano *Il gioco del
mondo*, 1963) di Julio Cortázar si può leggere in ordine oppure seguendo un percorso alternativo indicato
dall'autore alla fine di ogni capitolo, e i "librigame" degli anni Ottanta chiedevano al lettore di
scegliere a quale paragrafo saltare.

### Tre precursori

Nel 1945 l'ingegnere statunitense **Vannevar Bush** pubblica un articolo intitolato *As We May Think*,
in cui immagina il **Memex**: una scrivania con schermi e microfilm in cui uno studioso può conservare
tutti i suoi libri e documenti e, soprattutto, creare **percorsi associativi** tra di essi, da
ripercorrere e condividere. La macchina non verrà mai costruita, ma l'idea di collegare documenti per
associazione, come fa la mente, è quella dell'ipertesto.

<figure markdown>
![L'illustrazione del Memex su Life, 1945](https://commons.wikimedia.org/wiki/Special:FilePath/The_Memex_(3002477109).jpg?width=1000){ width="520" loading=lazy }
<figcaption>Il Memex nell'illustrazione che accompagnava la versione dell'articolo di Bush pubblicata
dalla rivista <em>Life</em> il 10 settembre 1945. Via Wikimedia Commons.</figcaption>
</figure>

Nel 1965 **Ted Nelson** conia la parola *hypertext* e avvia **Xanadu**, un progetto di "universo di
documenti" in cui ogni testo sarebbe stato collegato a tutti gli altri, con i link in entrambe le
direzioni e un sistema di citazione che teneva traccia degli autori. Xanadu non è mai stato completato.

Nel 1968 **Douglas Engelbart** presenta a San Francisco un sistema chiamato NLS, in una dimostrazione
passata alla storia come *The Mother of All Demos*: in novanta minuti mostra il mouse, le finestre, la
modifica collaborativa di documenti a distanza e, appunto, i collegamenti ipertestuali.

### Il Web nasce al CERN

Alla fine degli anni Ottanta **Tim Berners-Lee**, un informatico britannico che lavora al **CERN** di
Ginevra, si scontra con un problema pratico: migliaia di ricercatori di paesi diversi producono
documenti su computer diversi e incompatibili, e nessuno riesce a trovare niente. Nel marzo 1989
scrive una proposta intitolata *Information Management: A Proposal*: un sistema ipertestuale
**distribuito**, in cui i documenti restano sui computer di chi li produce ma sono collegati tra loro
da link.

Tra il 1990 e il 1991, su un computer NeXT, Berners-Lee sviluppa i tre ingredienti che usiamo ancora
oggi:

- **URL**, un modo uniforme di dare un indirizzo a ogni documento;
- **HTTP**, il protocollo con cui un client chiede un documento e un server lo invia;
- **HTML**, il linguaggio di marcatura con cui si scrivono i documenti e i link (lo abbiamo visto
  nella L03 e lo useremo nella L08).

Scrive anche il primo **browser** e il primo **server** web. Il primo sito, `info.cern.ch`, spiega che
cos'è il Web e come usarlo; è ancora online.

<figure markdown>
![Il computer NeXT usato come primo server web al CERN](https://commons.wikimedia.org/wiki/Special:FilePath/First_Web_Server.jpg?width=1200){ width="520" loading=lazy }
<figcaption>Il NeXTcube usato come primo server web, esposto al CERN. Sulla tastiera c'è una copia
della proposta del 1989; l'etichetta sul computer avverte di non spegnerlo. Coolcaesar, CC BY-SA 3.0,
via Wikimedia Commons.</figcaption>
</figure>

Il 30 aprile 1993 il CERN rende il software del Web di **pubblico dominio**: chiunque può usarlo e
modificarlo senza pagare nulla. È una scelta decisiva. Nello stesso periodo esistevano altri sistemi
per pubblicare documenti in rete, alcuni a pagamento, e nel giro di pochi anni il Web li sostituisce
tutti. Nel 1994 Berners-Lee fonda il **W3C** (*World Wide Web Consortium*), l'organizzazione che
ancora oggi definisce gli standard del Web.

### Internet e Web non sono la stessa cosa

Nel linguaggio comune "Internet" e "Web" si usano come sinonimi, ma indicano due cose diverse:

| | Internet | World Wide Web |
|---|---|---|
| Che cos'è | Un'infrastruttura di reti collegate | Un sistema di documenti ipertestuali |
| Quando nasce | Dal 1969 (ARPANET), TCP/IP dal 1983 | Dal 1989–1991 |
| Tecnologie | TCP, IP, DNS | URL, HTTP, HTML |
| Analogia | La rete stradale | Uno dei servizi che la usano, come le consegne a domicilio |

Il Web è **uno dei servizi** di Internet. Altri sono la posta elettronica, il trasferimento di file, le
videochiamate, i giochi online, e molte app che usano Internet senza passare dal browser.

---

## 2. Come funziona il Web

### Anatomia di un URL

Un **URL** (*Uniform Resource Locator*) è l'indirizzo di una risorsa sul Web. Prendiamo questo:

```text
https://it.wikipedia.org/wiki/Lingua_siciliana?action=history#top
```

| Parte | Nell'esempio | Che cosa indica |
|---|---|---|
| **Schema** | `https` | Il protocollo da usare |
| **Nome di dominio** | `it.wikipedia.org` | Il server a cui chiedere (lo traduce il DNS, L06) |
| **Percorso** | `/wiki/Lingua_siciliana` | La risorsa all'interno del server |
| **Parametri** (*query*) | `?action=history` | Informazioni aggiuntive per il server, in coppie `chiave=valore` |
| **Frammento** (*ancora*) | `#top` | Un punto preciso all'interno della pagina |

<figure markdown>
![Le parti di un URL](https://commons.wikimedia.org/wiki/Special:FilePath/URI_Components_Full_Example_HTTPS.svg?width=1400){ width="760" loading=lazy }
<figcaption>Un URL completo scomposto nelle sue parti, compresi i componenti meno comuni come le
credenziali dell'utente e la porta. Via Wikimedia Commons.</figcaption>
</figure>

I parametri sono la parte più interessante da osservare. Fate una ricerca su un motore di ricerca o su
un sito di vendita e guardate la barra degli indirizzi: troverete la vostra ricerca, i filtri, la
pagina dei risultati, e spesso codici che servono a tracciare da dove siete arrivati (quelli che
cominciano con `utm_`, ad esempio).

### HTTP: una conversazione tra client e server

**HTTP** (*HyperText Transfer Protocol*) è un protocollo a livello di applicazione (L06) basato su un
meccanismo di **richiesta e risposta**: il client chiede, il server risponde. Ogni messaggio è testo,
leggibile anche da una persona. Una richiesta semplificata:

```text
GET /wiki/Lingua_siciliana HTTP/1.1
Host: it.wikipedia.org
User-Agent: Mozilla/5.0 (Windows NT 10.0) Firefox/140.0
Accept-Language: it-IT,it;q=0.9,en;q=0.5
```

La prima riga contiene il **metodo** (`GET`, "dammi"), il percorso e la versione del protocollo. Le
righe successive sono le **intestazioni**: tra queste, il browser comunica quale programma state usando
e **quali lingue preferite**. È così che un sito multilingue sceglie in quale lingua mostrarvi la
pagina.

La risposta del server comincia con un **codice di stato**:

```text
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Language: it

<!DOCTYPE html>
<html lang="it">
...
```

Notate `charset=UTF-8`: il server dichiara la codifica dei caratteri del documento, il tema della L02.
Se la dichiarazione è sbagliata, compare il *mojibake*.

I codici di stato sono raggruppati in famiglie, e alcuni li avete sicuramente incontrati:

| Codice | Famiglia | Esempio |
|---|---|---|
| `2xx` | Successo | `200 OK`: ecco la risorsa |
| `3xx` | Reindirizzamento | `301 Moved Permanently`: la risorsa si è spostata a un altro URL |
| `4xx` | Errore del client | `403 Forbidden`: non avete il permesso. `404 Not Found`: la risorsa non esiste |
| `5xx` | Errore del server | `500 Internal Server Error`, `503 Service Unavailable` |

Oltre a `GET`, il metodo più comune è `POST`, con cui il client **invia** dati al server: un modulo di
iscrizione, un commento, un messaggio.

### HTTPS e il lucchetto

HTTP viaggia **in chiaro**: chiunque si trovi lungo il percorso dei pacchetti, ad esempio sulla stessa
rete Wi-Fi pubblica, può leggere che cosa vi scambiate con il server. **HTTPS** aggiunge uno strato di
**cifratura** (TLS): il contenuto della comunicazione diventa illeggibile per chi lo intercetta, e il
server dimostra con un **certificato** di essere davvero il titolare di quel dominio. Oggi la grande
maggioranza dei siti usa HTTPS, e i browser segnalano come "non sicuri" quelli che non lo fanno.

!!! warning "Il lucchetto non dice che il sito è affidabile"
    Il lucchetto accanto all'indirizzo garantisce che la comunicazione è cifrata e che state parlando
    con il server di quel dominio. Non dice nulla sulle intenzioni di chi lo gestisce. Anche i siti di
    *phishing* hanno il lucchetto: `unibo-verifica-account.com` può avere un certificato perfettamente
    valido. Guardate sempre il **nome di dominio**.

### Dal Web 1.0 al Web 2.0

Negli anni Novanta pubblicare sul Web richiedeva competenze tecniche: pochi scrivevano, molti
leggevano. Dai primi anni Duemila si diffondono piattaforme che permettono a chiunque di pubblicare
senza sapere nulla di HTML: blog, wiki, social network, siti di condivisione di foto e video. Si parla
allora di **Web 2.0**, il Web dei **contenuti generati dagli utenti**. L'architettura sottostante non
cambia, è sempre client/server: cambia chi scrive. Wikipedia, nata nel 2001, ne è l'esempio più
importante per chi lavora con le lingue.

C'è un rovescio: quando tutti pubblicano sulle stesse poche piattaforme, i contenuti, i dati sugli
utenti e le regole su che cosa si può dire finiscono nelle mani di poche aziende. Nella L08 vedremo
un'alternativa: pubblicare una pagina vostra, con un indirizzo vostro.

---

## 3. Cercare informazioni

### Come funziona un motore di ricerca

Per trovare una pagina dovete conoscere il suo URL, ma nella maggior parte dei casi non lo conoscete.
Un **motore di ricerca** risolve il problema in tre fasi.

1. **Scansione** (*crawling*). Un programma chiamato **crawler** o *spider* parte da un elenco di pagine
   note, le scarica, ne estrae i link e scarica le pagine collegate, e così via, all'infinito. È una
   visita del grafo del Web.
2. **Indicizzazione**. Il testo delle pagine viene analizzato e registrato in un **indice inverso**: per
   ogni parola, l'elenco delle pagine che la contengono. È lo stesso principio dell'indice analitico in
   fondo a un libro, ed è un **dizionario** nel senso della L03: la chiave è la parola, il valore è la
   lista delle pagine.
3. **Interrogazione e ordinamento** (*ranking*). Quando scrivete una ricerca, il motore trova nell'indice
   le pagine che contengono le parole e le **ordina** secondo la loro presunta rilevanza.

<figure markdown>
![Architettura di un web crawler](https://commons.wikimedia.org/wiki/Special:FilePath/WebCrawlerArchitecture.svg?width=900){ width="460" loading=lazy }
<figcaption>Architettura di un crawler: uno scheduler sceglie quali URL visitare, un componente
multithread scarica le pagine, e i testi e i nuovi URL trovati vengono salvati. Dnet, sulla base di
un'immagine di Carlos Castillo, pubblico dominio, via Wikimedia Commons.</figcaption>
</figure>

### PageRank: i link come voti

La parte difficile è l'ordinamento. Alla fine degli anni Novanta i motori di ricerca ordinavano le
pagine soprattutto in base a quante volte contenevano le parole cercate, ed era facile ingannarli.
Nel 1998 Sergey Brin e Larry Page, due dottorandi di Stanford, pubblicano l'algoritmo **PageRank**, da
cui nasce Google. L'idea è trattare ogni link come un **voto**: una pagina è importante se riceve link
da molte pagine, e ancora di più se quelle pagine sono a loro volta importanti.

<figure markdown>
![Esempio di valori di PageRank in un piccolo grafo](https://commons.wikimedia.org/wiki/Special:FilePath/PageRanks-Example.svg?width=900){ width="440" loading=lazy }
<figcaption>Valori di PageRank in un piccolo grafo. La pagina C ha un punteggio alto pur ricevendo un
solo link, perché quel link viene da B, la pagina più importante. Via Wikimedia Commons.</figcaption>
</figure>

Oggi i motori di ricerca usano centinaia di segnali oltre ai link: la vostra posizione, la lingua del
browser, le ricerche precedenti, la velocità del sito, il comportamento degli altri utenti. Due persone
che fanno la stessa ricerca possono vedere risultati diversi. Intorno al ranking è nata un'intera
industria, la **SEO** (*Search Engine Optimization*), che ottimizza le pagine per salire nei risultati,
e i primi risultati sono spesso **annunci a pagamento**, segnalati con la parola "Sponsorizzato".

### Cercare meglio: gli operatori di ricerca

La maggior parte delle persone scrive due o tre parole e guarda la prima pagina di risultati. Gli
**operatori di ricerca** permettono di essere molto più precisi. Questi funzionano su Google e, con
qualche differenza, sugli altri motori:

| Operatore | Esempio | Che cosa fa |
|---|---|---|
| `" "` | `"lingua siciliana"` | Cerca la frase esatta |
| `-` | `giaguaro -auto` | Esclude una parola |
| `OR` | `traduzione OR traduttologia` | Almeno una delle parole |
| `site:` | `site:unibo.it tirocinio` | Solo in un sito o in un dominio (anche `site:.edu`) |
| `filetype:` | `filetype:pdf "corpus parallelo"` | Solo un certo formato di file |
| `intitle:` | `intitle:glossario terminologia` | La parola deve stare nel titolo |
| `before:` / `after:` | `traduzione automatica after:2024-01-01` | Pagine prima o dopo una data |

Le stesse funzioni sono disponibili nella pagina di **ricerca avanzata**, con l'aggiunta di filtri per
lingua, paese e licenza d'uso delle immagini.

### Le risposte generate

Oggi molti motori di ricerca mostrano in cima ai risultati un **riassunto generato da un modello
linguistico**, e alcuni offrono una modalità di ricerca conversazionale. È comodo, ma cambia il
rapporto con le fonti: invece di una lista di pagine da valutare riceviamo una risposta già formulata,
che può contenere errori e che spesso non invoglia ad aprire le pagine da cui è tratta. Vedremo come
funzionano questi modelli nella L13 e come verificare le loro risposte nella L14.

### Il Web che i motori non vedono

Una parte enorme del Web non compare nei motori di ricerca. Si chiama **deep web** (web profondo) e non
ha nulla di misterioso: sono le pagine che stanno dietro un login (la vostra posta, Virtuale), quelle
generate al momento in risposta a una ricerca (i risultati di un catalogo di biblioteca come l'OPAC
SBN, i dati di un corpus interrogato online), quelle che i proprietari hanno chiesto di non indicizzare.
Per una persona che fa ricerca è il Web più prezioso: cataloghi, archivi, banche dati, corpora.

Il **dark web** è un'altra cosa: un insieme di siti raggiungibili solo con software apposito, come Tor,
che nasconde chi li gestisce e chi li visita. È usato sia da attività illegali sia da giornalisti e
attivisti in paesi dove la rete è censurata.

---

## 4. Raccomandazioni, bolle, disinformazione

### I sistemi di raccomandazione

Sui social network, sulle piattaforme video e musicali, nei negozi online non cercate quasi mai voi:
è la piattaforma che vi propone che cosa guardare. Lo fa un **sistema di raccomandazione**, un
algoritmo (L04) che prevede che cosa vi interesserà. I due approcci di base sono:

- il **filtraggio basato sul contenuto**: vi propongo cose simili a quelle che vi sono piaciute (un altro
  romanzo dello stesso autore, un altro video sullo stesso tema);
- il **filtraggio collaborativo**: vi propongo cose piaciute a persone che hanno gusti simili ai vostri
  ("chi ha acquistato questo articolo ha acquistato anche…").

I sistemi reali combinano i due approcci con migliaia di altri segnali. Ma la domanda più importante è
un'altra: **che cosa cerca di ottenere** il sistema? Spesso l'obiettivo è il **coinvolgimento**
(*engagement*): il tempo che passate sulla piattaforma, i clic, i commenti, le condivisioni, perché è da
questo che dipendono i ricavi pubblicitari. Un sistema ottimizzato per il coinvolgimento non è
ottimizzato per informarvi bene.

Dal 2024 il **Digital Services Act**, il regolamento europeo sulle piattaforme digitali, obbliga le
piattaforme molto grandi a spiegare come funzionano i loro sistemi di raccomandazione e a offrire
almeno un'opzione **non basata sulla profilazione**, ad esempio un feed in ordine cronologico.

### Bolle informative e camere dell'eco

Nel 2011 l'attivista Eli Pariser ha proposto l'espressione **filter bubble** (bolla di filtraggio):
se gli algoritmi ci mostrano solo ciò che è simile a ciò che già ci piace, finiremo chiusi in una bolla
in cui non incontriamo mai opinioni diverse. Un'idea vicina è quella di **camera dell'eco** (*echo
chamber*): un gruppo in cui le stesse opinioni rimbalzano e si rafforzano.

L'idea è intuitiva, ma le ricerche empiriche danno un quadro più sfumato:

- uno studio su oltre 10 milioni di utenti statunitensi di Facebook (Bakshy, Messing e Adamic, 2015) ha
  trovato che l'algoritmo riduce un po' l'esposizione a notizie di orientamento politico diverso, ma che
  pesano di più le **scelte degli utenti**: con chi si è amici e su che cosa si clicca;
- uno studio sulla navigazione di 50.000 utenti (Flaxman, Goel e Rao, 2016) ha trovato che social
  network e motori di ricerca aumentano la distanza ideologica tra gli utenti, ma anche, nello stesso
  tempo, la loro esposizione a fonti dell'orientamento opposto.

In sintesi: gli algoritmi contano, ma non agiscono da soli. Le nostre scelte, le persone che seguiamo e
il modo in cui il sistema premia il coinvolgimento contribuiscono tutti al risultato.

### Disinformazione

Il Consiglio d'Europa distingue tre fenomeni (Wardle e Derakhshan, 2017):

- **misinformazione**: un'informazione falsa diffusa in buona fede, da chi la crede vera;
- **disinformazione**: un'informazione falsa creata e diffusa **intenzionalmente** per ingannare;
- **malinformazione**: un'informazione vera usata per nuocere, ad esempio pubblicando dati privati.

In uno studio molto citato, Vosoughi, Roy e Aral (2018) hanno analizzato circa 126.000 notizie diffuse
su Twitter tra il 2006 e il 2017, verificate da sei organizzazioni di *fact-checking*. Le notizie false
si diffondevano **più lontano, più in fretta e a più persone** di quelle vere, e la causa principale non
erano i *bot*: erano gli esseri umani, più inclini a condividere ciò che appare nuovo e sorprendente.

### Come verificare: la lettura laterale

Come si valuta una fonte in rete? Wineburg e McGrew (2019) hanno messo a confronto tre gruppi: storici
con un dottorato, studenti di Stanford e *fact-checker* professionisti, chiedendo a tutti di valutare
l'affidabilità di alcuni siti. I *fact-checker* hanno ottenuto i risultati migliori in molto meno tempo,
e lo hanno fatto in un modo controintuitivo: invece di leggere a fondo il sito (lettura "verticale"),
lo lasciavano quasi subito e aprivano **altre schede** per cercare che cosa dicessero **altri** di quel
sito e di chi lo pubblica. Questa strategia si chiama **lettura laterale**.

!!! tip "Quattro mosse per verificare"
    1. **Fermatevi** prima di condividere o di credere: chiedetevi se conoscete la fonte.
    2. **Indagate la fonte**: cercate il nome del sito o dell'autore in un'altra scheda (Wikipedia è un
       ottimo punto di partenza per questo).
    3. **Cercate copertura migliore**: la stessa notizia è riportata da fonti che conoscete?
    4. **Risalite all'originale**: per le immagini usate la **ricerca inversa** (Google Lens, TinEye)
       per scoprire dove e quando sono apparse per la prima volta.

---

## 5. Tracce digitali e diritti

### Che cosa racconta di voi il browser

Ogni volta che visitate una pagina, il browser comunica al server, senza che ve ne accorgiate:

- il vostro **indirizzo IP** (e quindi, approssimativamente, la città e il fornitore di connessione);
- il **browser** e il **sistema operativo** che usate;
- le **lingue** che preferite;
- la pagina da cui arrivate (*referer*);
- la data e l'ora.

Combinando queste informazioni con altre (la risoluzione dello schermo, i caratteri installati, il
fuso orario) un sito può riconoscere lo stesso browser anche senza cookie, con una tecnica chiamata
***fingerprinting*** ("impronta digitale").

### I cookie

Un **cookie** è un piccolo file di testo che un sito chiede al browser di conservare. Alla visita
successiva il browser lo rimanda al sito, che così vi riconosce. HTTP di per sé non ha memoria: ogni
richiesta è indipendente dalle precedenti, e i cookie servono proprio a ricordare chi siete tra una
richiesta e l'altra.

<figure markdown>
![Scambio di cookie tra browser e server](https://commons.wikimedia.org/wiki/Special:FilePath/HTTP_cookie_exchange.svg?width=1000){ width="560" loading=lazy }
<figcaption>Il server invia il cookie insieme alla prima risposta (<code>Set-Cookie</code>); il browser
lo rimanda a ogni richiesta successiva verso lo stesso sito. Tizio, GFDL, via Wikimedia Commons.</figcaption>
</figure>

Conviene distinguere i cookie in due modi.

**Per finalità**:

- i cookie **tecnici** servono al funzionamento del sito: ricordare che avete fatto il login, che cosa
  c'è nel carrello, la lingua scelta;
- i cookie di **profilazione** servono a costruire un profilo dei vostri interessi, di solito a fini
  pubblicitari.

**Per provenienza**:

- i cookie **di prima parte** sono impostati dal sito che state visitando;
- i cookie **di terze parti** sono impostati da un altro dominio i cui contenuti (un banner pubblicitario,
  un pulsante "mi piace", uno strumento di statistica) sono incorporati nella pagina. Se lo stesso
  inserzionista è presente su mille siti, può seguirvi da un sito all'altro.

In Europa i cookie tecnici si possono usare senza chiedere nulla; per tutti gli altri serve il vostro
**consenso**, ed è per questo che vedete i banner. Secondo le linee guida del Garante italiano (2021), il
banner deve permettere di rifiutare con la stessa facilità con cui si accetta, ad esempio con un
pulsante o una "X" di chiusura, e continuare a navigare non equivale a dare il consenso.

### Il GDPR

Il **Regolamento generale sulla protezione dei dati** (*General Data Protection Regulation*, GDPR,
Regolamento UE 2016/679) si applica in tutta l'Unione Europea dal 25 maggio 2018. Alcuni concetti
fondamentali:

- un **dato personale** è qualsiasi informazione riguardante una **persona fisica** identificata o
  identificabile, anche indirettamente: un nome, un numero di identificazione, dati sull'ubicazione, un
  **identificativo online** (come un indirizzo IP o l'identificativo contenuto in un cookie);
- alcune **categorie particolari** di dati (origine etnica, opinioni politiche, convinzioni religiose,
  appartenenza sindacale, dati genetici e biometrici, salute, vita e orientamento sessuale) godono di una
  protezione più forte;
- il trattamento deve rispettare alcuni **principi**: liceità, correttezza e trasparenza; limitazione
  della finalità (i dati raccolti per uno scopo non si usano per un altro); minimizzazione (solo i dati
  necessari); esattezza; limitazione della conservazione; integrità e riservatezza.

!!! warning "Una correzione rispetto ai materiali degli anni passati"
    In alcune slide circolate negli anni scorsi la definizione di dato personale includeva "persona
    giuridica, ente o associazione". Era la definizione della vecchia normativa italiana, superata da
    tempo: il GDPR protegge soltanto le **persone fisiche**.

Il GDPR vi riconosce una serie di **diritti** nei confronti di chiunque tratti i vostri dati
(articoli 15–22):

| Diritto | In pratica |
|---|---|
| **Accesso** | Sapere se un'organizzazione ha dati su di voi, quali, perché e per quanto tempo, e riceverne una copia |
| **Rettifica** | Far correggere dati sbagliati |
| **Cancellazione** ("diritto all'oblio") | Far cancellare i dati, in certe condizioni |
| **Limitazione** | Bloccare temporaneamente l'uso dei dati, ad esempio mentre se ne contesta l'esattezza |
| **Portabilità** | Ricevere i dati in un formato strutturato e leggibile da una macchina, per portarli altrove |
| **Opposizione** | Opporsi a certi trattamenti, sempre a quelli per marketing diretto |
| **Decisioni automatizzate** | Non essere sottoposti a decisioni importanti prese solo da un algoritmo, con alcune eccezioni |

Il diritto alla portabilità ci riporta alla L03: i dati devono essere consegnati in un formato
**strutturato** e **leggibile da una macchina**, e spesso si tratta proprio di JSON o CSV. In Italia
l'autorità che vigila sul rispetto del GDPR è il **Garante per la protezione dei dati personali**.

---

## 6. Licenze e diritto d'autore in rete

### Tutto è protetto, salvo diverso avviso

Testi, fotografie, illustrazioni, musica, video e software sono **opere dell'ingegno**, e in Italia sono
protetti dalla legge sul diritto d'autore (legge 633/1941). La protezione è **automatica**: non serve
registrare l'opera né scrivere "tutti i diritti riservati". In generale dura fino a **settant'anni dopo
la morte dell'autore**; dopo, l'opera entra nel **pubblico dominio** e chiunque può usarla liberamente.

Il fatto che un'immagine sia visibile su un sito non significa che possiate riusarla. Senza
un'autorizzazione esplicita, la regola è che **non si può**, salvo alcune eccezioni previste dalla legge,
come la citazione di brevi brani per critica, discussione o insegnamento, purché accompagnata dalla
fonte.

### Le licenze Creative Commons

Per gli autori che vogliono permettere il riuso delle proprie opere esistono licenze già pronte. Le più
diffuse sono le **Creative Commons** (CC), nate nel 2001. Si costruiscono combinando quattro clausole:

| Sigla | Nome | Che cosa chiede |
|---|---|---|
| **BY** | Attribuzione | Citare l'autore e la licenza (presente in tutte le licenze) |
| **SA** | Condividi allo stesso modo | Le opere derivate devono avere la stessa licenza |
| **NC** | Non commerciale | Niente usi commerciali |
| **ND** | Non opere derivate | L'opera si può diffondere solo così com'è, senza modifiche |

Ne risultano sei licenze, dalla più aperta alla più restrittiva: CC BY, CC BY-SA, CC BY-NC, CC BY-NC-SA,
CC BY-ND, CC BY-NC-ND. A queste si aggiunge **CC0**, con cui l'autore rinuncia a tutti i diritti e
mette l'opera di fatto in pubblico dominio.

Qualche esempio che conoscete: Wikipedia è in **CC BY-SA**, quindi potete riusarne i testi citando la
fonte e mantenendo la stessa licenza; il sito di questo corso è in **CC BY**; le immagini che vedete in
queste pagine vengono da **Wikimedia Commons**, e sotto ciascuna è indicato l'autore, come chiede la
licenza.

!!! tip "Dove trovare immagini riusabili"
    - [Wikimedia Commons](https://commons.wikimedia.org/): oltre cento milioni di file, ciascuno con la
      sua licenza indicata nella pagina del file.
    - [Openverse](https://openverse.org/): un motore di ricerca per immagini e audio con licenze aperte.
    - Nella ricerca immagini di Google: *Strumenti → Diritti di utilizzo → Licenze Creative Commons*.

Ci servirà subito: nella L08 sceglierete una licenza per la vostra pagina web e userete solo immagini che
potete davvero pubblicare. Nella L15, invece, ci chiederemo che cosa succede quando milioni di opere
protette vengono usate per addestrare un modello linguistico.

---

## Riepilogo

| Concetto | In una frase |
|---|---|
| Ipertesto | Testi collegati da link, percorribili in ordini diversi: un grafo orientato |
| World Wide Web | Il sistema ipertestuale distribuito inventato al CERN (1989–1991), basato su URL, HTTP, HTML |
| URL | Schema, dominio, percorso, parametri, frammento |
| HTTP/HTTPS | Richiesta e risposta tra client e server; HTTPS aggiunge la cifratura |
| Motore di ricerca | Scansione, indice inverso, ranking (PageRank e molti altri segnali) |
| Raccomandazione | Algoritmi che scelgono che cosa mostrarvi, spesso per massimizzare il coinvolgimento |
| Disinformazione | Falsità diffuse intenzionalmente; si contrasta con la lettura laterale |
| Cookie | File che permettono a un sito di riconoscervi; per i non tecnici serve il consenso |
| GDPR | Protegge i dati delle persone fisiche e vi dà diritti di accesso, rettifica, cancellazione, portabilità… |
| Creative Commons | Licenze pronte per permettere il riuso delle opere a certe condizioni |

---

## Attività

**Durante la lezione (online)**

1. **Guardate dentro una pagina.** Aprite `it.wikipedia.org`, premete `F12` (o `Cmd+Opt+I` su Mac) e
   scegliete la scheda **Rete** (*Network*). Ricaricate la pagina. Quante richieste fa il browser per
   mostrare una sola pagina? Cliccate sulla prima: trovate il metodo, il codice di stato e
   l'intestazione `Accept-Language`?
2. **Provocate un errore.** Scrivete nella barra degli indirizzi un URL inventato su un sito che
   conoscete, ad esempio `https://www.unibo.it/pagina-che-non-esiste`. Che codice di stato riceve il
   browser?
3. **Cercate come un professionista.** Trovate con un solo comando di ricerca: (a) un PDF del sito
   dell'Unione Europea che contenga l'espressione "multilinguismo"; (b) pagine sulla traduzione
   automatica pubblicate dopo il 1° gennaio 2025, escludendo un sito a vostra scelta.
4. **Contate i cookie.** Aprite un sito di notizie e, prima di rispondere al banner, aprite gli strumenti
   per sviluppatori: scheda **Archiviazione** (Firefox) o **Applicazione** (Chrome). Quanti cookie ci
   sono? Da quali domini? Rifiutate il consenso e ricaricate: che cosa cambia?

**A casa (facoltativo)**

- Esercitate il **diritto di accesso** su un servizio che usate (Google, Instagram, Spotify, TikTok):
  quasi tutti hanno una pagina "Scarica i tuoi dati". Aprite il file che ricevete: in che formato è?
  Che cosa c'è che non vi aspettavate?
- Scegliete una notizia sorprendente che avete visto circolare di recente e applicate le quattro mosse
  della lettura laterale. Scrivete in cinque righe che cosa avete scoperto.

---

## Mettetevi alla prova

**1.** Qual è la differenza tra Internet e il World Wide Web?

- A. Sono due nomi per la stessa cosa
- B. Internet è l'infrastruttura di reti; il Web è uno dei servizi che la usano
- C. Il Web è più antico di Internet
- D. Internet funziona solo con i browser

??? success "Soluzione"
    **B.** Internet nasce da ARPANET (1969) e usa TCP/IP; il Web nasce al CERN tra il 1989 e il 1991 e
    usa URL, HTTP e HTML.

**2.** Nell'URL `https://www.example.org/catalogo/libri?genere=poesia#risultati`, che cosa è `genere=poesia`?

- A. Il nome di dominio
- B. Il percorso
- C. Un parametro
- D. Il frammento

??? success "Soluzione"
    **C.** Segue il punto interrogativo ed è una coppia `chiave=valore`. Il frammento è `#risultati`.

**3.** Un server risponde a una richiesta con il codice `404`. Che cosa significa?

- A. La richiesta ha avuto successo
- B. La risorsa si è spostata a un altro indirizzo
- C. La risorsa richiesta non è stata trovata
- D. Il server ha avuto un errore interno

??? success "Soluzione"
    **C.** I codici `4xx` indicano un errore dalla parte del client, in questo caso un indirizzo che non
    corrisponde a nessuna risorsa.

**4.** Un sito ha il lucchetto accanto all'indirizzo (HTTPS). Che cosa possiamo concludere?

- A. Che il sito è affidabile e i suoi contenuti sono veri
- B. Che la comunicazione tra browser e server è cifrata
- C. Che il sito non usa cookie
- D. Che il sito è stato verificato dal Garante

??? success "Soluzione"
    **B.** Anche un sito di *phishing* può avere il lucchetto.

**5.** Secondo l'idea alla base di PageRank, una pagina è importante se:

- A. contiene molte volte la parola cercata
- B. riceve link da molte pagine, soprattutto se a loro volta importanti
- C. è stata pubblicata di recente
- D. paga per comparire nei risultati

??? success "Soluzione"
    **B.** I link sono trattati come voti, e il voto di una pagina importante pesa di più.

**6.** Uno studente legge a lungo e con attenzione un sito per capire se è affidabile. Che cosa farebbe
invece un *fact-checker* professionista, secondo Wineburg e McGrew?

- A. Leggerebbe il sito ancora più a fondo
- B. Controllerebbe se il sito ha un design professionale
- C. Uscirebbe presto dal sito per cercare in altre schede che cosa dicono altri di quella fonte
- D. Guarderebbe solo la sezione "Chi siamo"

??? success "Soluzione"
    **C.** È la **lettura laterale**.

**7.** Secondo il GDPR, quale di queste informazioni **non** è un dato personale?

- A. L'indirizzo IP di uno studente
- B. Il nome e cognome di una docente
- C. Il fatturato di una società per azioni
- D. L'identificativo contenuto in un cookie di profilazione

??? success "Soluzione"
    **C.** Il GDPR protegge le persone fisiche, non le società.

**8.** Trovate su Wikimedia Commons una fotografia con licenza **CC BY-SA 4.0**. Potete usarla nella
vostra pagina web?

- A. No, le immagini trovate in rete non si possono mai usare
- B. Sì, senza nessuna condizione
- C. Sì, citando l'autore e la licenza, e pubblicando con la stessa licenza un'eventuale versione modificata
- D. Sì, ma solo se la pagina non ha scopi commerciali

??? success "Soluzione"
    **C.** BY chiede l'attribuzione, SA chiede di condividere le opere derivate con la stessa licenza.
    La clausola che vieta gli usi commerciali è NC, che qui non c'è.

---

## Per approfondire

- Berners-Lee, T. (1989). [*Information Management: A Proposal*](https://www.w3.org/History/1989/proposal.html).
  CERN. La proposta originale del Web.
- Bush, V. (1945). As we may think. *The Atlantic Monthly*, *176*(1), 101–108.
  [Testo online](https://www.theatlantic.com/magazine/archive/1945/07/as-we-may-think/303881/).
- Brin, S., & Page, L. (1998). The anatomy of a large-scale hypertextual Web search engine. *Computer
  Networks and ISDN Systems*, *30*(1–7), 107–117. [doi:10.1016/S0169-7552(98)00110-X](https://doi.org/10.1016/S0169-7552(98)00110-X)
- Bakshy, E., Messing, S., & Adamic, L. A. (2015). Exposure to ideologically diverse news and opinion
  on Facebook. *Science*, *348*(6239), 1130–1132. [doi:10.1126/science.aaa1160](https://doi.org/10.1126/science.aaa1160)
- Flaxman, S., Goel, S., & Rao, J. M. (2016). Filter bubbles, echo chambers, and online news
  consumption. *Public Opinion Quarterly*, *80*(S1), 298–320. [doi:10.1093/poq/nfw006](https://doi.org/10.1093/poq/nfw006)
- Vosoughi, S., Roy, D., & Aral, S. (2018). The spread of true and false news online. *Science*,
  *359*(6380), 1146–1151. [doi:10.1126/science.aap9559](https://doi.org/10.1126/science.aap9559)
- Wardle, C., & Derakhshan, H. (2017). [*Information Disorder: Toward an interdisciplinary framework for
  research and policy making*](https://rm.coe.int/information-disorder-toward-an-interdisciplinary-framework-for-researc/168076277c).
  Consiglio d'Europa.
- Wineburg, S., & McGrew, S. (2019). Lateral reading and the nature of expertise: Reading less and
  learning more when evaluating digital information. *Teachers College Record*, *121*(11), 1–40.
  [doi:10.1177/016146811912101102](https://doi.org/10.1177/016146811912101102)
- Garante per la protezione dei dati personali, [Linee guida cookie e altri strumenti di
  tracciamento](https://www.garanteprivacy.it/home/docweb/-/docweb-display/docweb/9677876) (10 giugno 2021).
- [Creative Commons: scegliere una licenza](https://creativecommons.org/chooser/).

Elenco completo in [Letture e materiali](../letture.md#blocco-b-internet-e-web).

## Parole chiave

[Ipertesto](../glossario.md#ipertesto) ·
[World Wide Web](../glossario.md#world-wide-web) ·
[URL](../glossario.md#url) ·
[HTTP e HTTPS](../glossario.md#http-e-https) ·
[Browser](../glossario.md#browser) ·
[Motore di ricerca](../glossario.md#motore-di-ricerca) ·
[Indice inverso](../glossario.md#indice-inverso) ·
[PageRank](../glossario.md#pagerank) ·
[Sistema di raccomandazione](../glossario.md#sistema-di-raccomandazione) ·
[Bolla di filtraggio](../glossario.md#bolla-di-filtraggio) ·
[Disinformazione](../glossario.md#disinformazione) ·
[Lettura laterale](../glossario.md#lettura-laterale) ·
[Cookie](../glossario.md#cookie) ·
[GDPR](../glossario.md#gdpr) ·
[Dato personale](../glossario.md#dato-personale) ·
[Creative Commons](../glossario.md#creative-commons) ·
[Pubblico dominio](../glossario.md#pubblico-dominio)
