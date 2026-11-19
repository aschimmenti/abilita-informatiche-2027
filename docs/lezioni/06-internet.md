# L06 · Internet: la rete delle reti

<p class="meta">Online · 2 ore · Blocco B — Internet e Web</p>

!!! abstract "In sintesi"
    Usiamo Internet ogni giorno senza chiederci come funziona, un po' come la rete idrica: apriamo il
    rubinetto e l'acqua arriva. In questa lezione apriamo il rubinetto e guardiamo i tubi. Partiamo da
    una breve storia, da ARPANET alla prima connessione italiana del 1986. Poi seguiamo il viaggio di
    una richiesta qualsiasi, dal vostro computer al server di unibo.it e ritorno: pacchetti, indirizzi
    IP, router, DNS, protocolli. Infine scopriamo che la "nuvola" è fatta di cavi sul fondo del mare e
    di edifici pieni di server, e che non tutti, e non tutte le lingue, sono in rete allo stesso modo.

<div class="slides-embed">
  <iframe src="../../slides/L06.html" title="Slide della lezione 6" loading="lazy" allowfullscreen></iframe>
</div>
<p class="slides-links">
  <a class="md-button" href="../../slides/L06.html" target="_blank" rel="noopener">Slide a schermo intero</a>
  <a class="md-button" href="../../slides/L06.pdf" target="_blank" rel="noopener">Slide in PDF</a>
</p>

## Obiettivi

Alla fine della lezione saprete:

- raccontare a grandi linee come è nata Internet, e quando e come è arrivata in Italia;
- distinguere il modello **client/server** da quello **peer-to-peer**;
- spiegare perché Internet usa la **commutazione di pacchetto** e non quella di circuito;
- descrivere i quattro livelli della pila **TCP/IP** e dire che cosa fa ciascuno;
- leggere un **indirizzo IP** e spiegare a che cosa serve il **DNS**;
- ricostruire passo per passo che cosa succede quando digitate un indirizzo nel browser;
- descrivere l'**infrastruttura fisica** della rete e il suo costo energetico;
- discutere il **divario digitale** e il peso delle diverse lingue in rete.

!!! info "Prima della lezione"
    Non c'è niente da installare. Tenete aperto un browser: durante la lezione useremo alcuni strumenti
    online gratuiti, che trovate collegati nella sezione [Attività](#attivita).

---

## 0. Una domanda per cominciare

Scrivete nel browser `unibo.it` e premete Invio. In meno di un secondo compare la pagina dell'Ateneo.
**Che cosa è successo in quel secondo?** Prima di proseguire, provate a rispondere in chat con le
parole che conoscete: anche "non ne ho idea" è una risposta utile. Alla fine della lezione
riprenderemo le risposte e le confronteremo con quello che avremo visto.

---

## 1. Breve storia

### Da ARPA ad ARPANET

Nel 1957 l'Unione Sovietica lancia lo **Sputnik**, il primo satellite artificiale. Gli Stati Uniti
rispondono l'anno successivo creando l'**ARPA** (*Advanced Research Projects Agency*), un'agenzia del
Dipartimento della Difesa che finanzia la ricerca di base nelle università. Tra i progetti finanziati
c'è una rete per collegare i grandi calcolatori dei centri di ricerca, che all'epoca erano costosi,
rari e incompatibili tra loro: si chiama **ARPANET**.

Alla fine del 1969 ARPANET collega quattro nodi: la University of California a Los Angeles (UCLA), lo
Stanford Research Institute (SRI), la University of California a Santa Barbara e la University of
Utah. Il primo messaggio parte da UCLA verso SRI il 29 ottobre 1969: doveva essere la parola `LOGIN`,
ma il sistema si blocca dopo le prime due lettere. Il primo messaggio della storia della rete è
quindi `LO`.

<figure markdown>
![Mappa logica di ARPANET nel marzo 1977](https://commons.wikimedia.org/wiki/Special:FilePath/Arpanet_logical_map,_march_1977.png?width=1000){ width="640" loading=lazy }
<figcaption>Mappa logica di ARPANET nel marzo 1977: ogni rettangolo è un nodo della rete, ogni ovale
un calcolatore collegato. Pubblico dominio, via Wikimedia Commons.</figcaption>
</figure>

### Da una rete a una rete di reti

Negli anni Settanta nascono altre reti a commutazione di pacchetto: reti via radio, reti via satellite,
reti nazionali in Europa. Ciascuna funziona a modo suo, e nessuna sa parlare con le altre. Nel 1974
**Vinton Cerf** e **Robert Kahn** pubblicano un articolo in cui propongono un protocollo comune per far
comunicare reti diverse: è l'origine di **TCP/IP**. Il 1° gennaio 1983 ARPANET abbandona il vecchio
protocollo e passa definitivamente a TCP/IP.

Da qui viene anche il nome: *internet* è l'abbreviazione di *internetworking*, il collegamento tra
reti. Internet non è una rete unica, ma decine di migliaia di reti indipendenti (quelle delle
università, delle aziende, dei fornitori di connessione) che hanno accettato di usare le stesse
regole per scambiarsi dati.

### L'Italia in rete

L'Italia si collega per la prima volta a Internet il **30 aprile 1986**, poco dopo le sei di sera.
Un gruppo di ricercatori del **CNUCE** di Pisa, il centro di calcolo del CNR, invia un `ping` verso
gli Stati Uniti. Il segnale viaggia su linea telefonica fino alla stazione di Telespazio nella piana
del Fucino, in Abruzzo, sale su un satellite Intelsat e arriva alla stazione di Roaring Creek, in
Pennsylvania. Dall'altra parte qualcuno risponde. L'Italia è tra i primi paesi europei a collegarsi.

L'anno successivo, sempre a Pisa, viene registrato il primo nome di dominio italiano, `cnuce.cnr.it`.
Il **Registro .it**, che ancora oggi gestisce tutti i domini che finiscono in `.it`, ha sede presso
l'Istituto di Informatica e Telematica del CNR, a Pisa. Le università e i centri di ricerca italiani,
compresa la nostra, sono collegati tra loro e al resto del mondo dalla rete **GARR**.

### Perché ha funzionato

Le slide dell'anno scorso individuano quattro fattori del successo di Internet, che vale la pena
ricordare perché torneranno quando parleremo del Web:

- **investimenti pubblici**: per i primi vent'anni Internet è stata finanziata quasi solo da governi e
  università;
- **collaborazione** tra ricerca pubblica e industria;
- **standard aperti**: le regole di Internet sono pubblicate in documenti chiamati **RFC** (*Request
  for Comments*), che chiunque può leggere e usare gratuitamente;
- **estensibilità**: l'architettura è fatta a strati, e si può cambiare uno strato senza toccare gli
  altri.

---

## 2. Reti e architetture

### Nodi, host, collegamenti

Una **rete** è un insieme di **nodi** collegati da canali di comunicazione. Ogni dispositivo collegato
a Internet si chiama **host**: il vostro portatile, il telefono, il server che ospita un sito, ma anche
la smart TV o il termostato. Tra un host e l'altro ci sono i **router**, dispositivi specializzati che
smistano il traffico tra reti diverse.

Perché servono i router? Immaginate di voler collegare direttamente ogni computer a tutti gli altri.
Con 10 computer servono 45 cavi, con 100 computer 4.950, con un milione circa 500 miliardi. In
generale, con *n* nodi servono *n*(*n*−1)/2 collegamenti: il numero cresce molto più in fretta dei
nodi. La soluzione è organizzare la rete in modo **gerarchico**: i computer di una stanza formano una
piccola rete locale (in inglese *LAN*, *Local Area Network*), le reti locali di un edificio si
collegano tra loro, gli edifici si collegano alla rete dell'Ateneo, e la rete dell'Ateneo si collega a
Internet. In ogni punto di raccordo c'è un router.

Una rete come quella dell'Università di Bologna, che usa le tecnologie di Internet ma è riservata a una
sola organizzazione e protetta da un *firewall*, si chiama **intranet**.

### Client e server, o tutti alla pari

Gli host possono avere ruoli diversi:

- nel modello **client/server** c'è chi chiede (il **client**, ad esempio il vostro browser) e chi
  risponde (il **server**, un computer sempre acceso che ospita un servizio). È il modello di gran
  lunga più diffuso: il Web, la posta elettronica, Netflix, Virtuale funzionano così;
- nel modello **peer-to-peer** (P2P, "da pari a pari") ogni nodo è insieme client e server, e i dati
  passano direttamente da un utente all'altro senza un server centrale. Lo usano alcuni sistemi di
  condivisione di file come BitTorrent, alcune criptovalute e, in parte, alcune applicazioni di
  videochiamata.

<div class="grid" markdown>
<figure markdown>
![Modello client/server](https://commons.wikimedia.org/wiki/Special:FilePath/Client-server-model.svg?width=800){ width="380" loading=lazy }
<figcaption>Client/server: un server risponde a molti client. Calimo, CC BY-SA, via Wikimedia Commons.</figcaption>
</figure>
<figure markdown>
![Rete peer-to-peer](https://commons.wikimedia.org/wiki/Special:FilePath/P2P_network.svg?width=800){ width="300" loading=lazy }
<figcaption>Peer-to-peer: ogni nodo parla direttamente con gli altri. The 360 Degree, via Wikimedia Commons.</figcaption>
</figure>
</div>

---

## 3. Come viaggiano i dati

### Commutazione di circuito e commutazione di pacchetto

La rete telefonica tradizionale funzionava a **commutazione di circuito**: quando chiamavate qualcuno,
le centrali stabilivano un collegamento fisico dedicato tra i due telefoni, che restava occupato per
tutta la durata della chiamata, anche durante i silenzi. È un sistema semplice e prevedibile, ma spreca
risorse e si interrompe del tutto se un tratto del circuito si guasta.

Internet usa invece la **commutazione di pacchetto**. Il messaggio viene diviso in piccoli pezzi, i
**pacchetti**, e ciascuno viene spedito per conto suo, con un'etichetta che indica il mittente, il
destinatario e il numero d'ordine. I pacchetti possono seguire strade diverse: ogni router decide, in
quel momento, a quale vicino passarli. Il destinatario li riceve, magari in disordine, e li rimette in
sequenza.

Un'analogia: dovete spedire un'enciclopedia in venti volumi. Invece di noleggiare un camion che vada
direttamente a destinazione (il circuito), spedite venti pacchi separati, numerati, ciascuno con il suo
indirizzo. Alcuni passeranno per Milano, altri per Firenze, ma arriveranno tutti, e chi li riceve li
metterà in ordine sullo scaffale.

<figure markdown>
![Animazione della commutazione di pacchetto](https://commons.wikimedia.org/wiki/Special:FilePath/Packet_Switching.gif){ width="640" loading=lazy }
<figcaption>Un messaggio diviso in pacchetti che seguono percorsi diversi e vengono ricomposti
all'arrivo. Oddbodz, via Wikimedia Commons.</figcaption>
</figure>

I vantaggi sono tre: la rete è usata solo quando c'è davvero qualcosa da trasmettere, molte
comunicazioni condividono gli stessi cavi, e se un collegamento si interrompe i pacchetti trovano
un'altra strada.

### Che cos'è un protocollo

Perché tutto questo funzioni, ogni dispositivo deve seguire le stesse regole. Un **protocollo** è un
insieme di regole che stabilisce quali messaggi si possono scambiare, in che formato, in che ordine, e
che cosa fare quando qualcosa va storto. Nella L02 abbiamo visto che un linguaggio formale ha una
sintassi e una semantica senza ambiguità: un protocollo è un linguaggio formale pensato per far
dialogare due macchine.

Ci sono protocolli anche nella vita quotidiana. Al telefono si risponde "pronto?", si aspetta che
l'altro si presenti, si parla a turno, si chiude salutando. Se la linea è disturbata si chiede "mi
senti?". Un protocollo di rete fa la stessa cosa, ma in modo molto più rigido.

### La pila TCP/IP

Far comunicare due computer è un problema troppo complesso per un solo protocollo. Per questo i
protocolli di Internet sono organizzati in **livelli** (*layer*), ciascuno dei quali risolve una parte
del problema e si appoggia a quello sottostante. L'insieme si chiama **pila TCP/IP** (*TCP/IP stack*).

| Livello | Domanda a cui risponde | Esempi di protocolli |
|---|---|---|
| **Applicazione** | Che cosa vogliono dirsi i due programmi? | HTTP (Web), SMTP e IMAP (posta), DNS |
| **Trasporto** | Come arriva il messaggio completo e in ordine al programma giusto? | TCP, UDP |
| **Rete** (o Internet) | Come raggiunge un pacchetto l'host di destinazione, attraversando più reti? | IP |
| **Collegamento** | Come passa un pacchetto da un dispositivo al successivo? | Ethernet, Wi-Fi, 5G |

<figure markdown>
![La pila TCP/IP tra due host collegati da due router](https://commons.wikimedia.org/wiki/Special:FilePath/IP_stack_connections.svg?width=1000){ width="440" loading=lazy }
<figcaption>Due host comunicano attraverso due router. In alto il percorso fisico, in basso i livelli
usati a ogni passaggio: i router arrivano solo fino al livello di rete, mentre i livelli di trasporto
e di applicazione riguardano solo i due estremi. Kbrose, via Wikimedia Commons.</figcaption>
</figure>

Quando inviate qualcosa, il dato scende la pila: ogni livello aggiunge un'**intestazione** (*header*)
con le informazioni che gli servono, come una busta dentro un'altra busta. Questo meccanismo si chiama
**incapsulamento**. All'arrivo il dato risale la pila, e ogni livello toglie la sua busta e passa il
contenuto a quello superiore.

<figure markdown>
![Incapsulamento dei dati nei livelli della pila TCP/IP](https://commons.wikimedia.org/wiki/Special:FilePath/UDP_encapsulation.svg?width=1000){ width="560" loading=lazy }
<figcaption>Incapsulamento: i dati dell'applicazione ricevono un'intestazione dal livello di trasporto
(qui UDP; con TCP funziona allo stesso modo), una da IP e una dal livello di collegamento. Cburnett e
Kbrose, GFDL, via Wikimedia Commons.</figcaption>
</figure>

La divisione in livelli è il motivo per cui potete passare dal Wi-Fi di casa al 5G del telefono senza
che il browser se ne accorga: cambia il livello di collegamento, gli altri restano uguali.

### IP: gli indirizzi

Ogni host collegato a Internet ha un **indirizzo IP**. Nella versione più diffusa, **IPv4**, un
indirizzo è un numero di 32 bit, scritto per comodità come quattro numeri da 0 a 255 separati da punti:
ad esempio `192.168.1.10`. Ricordate la L02? Ciascuno dei quattro numeri è un byte, e un byte va da 0
a 255.

Con 32 bit si possono scrivere 2<sup>32</sup> indirizzi diversi, circa 4,3 miliardi. Negli anni
Settanta sembravano infiniti; oggi gli host collegati sono molti di più. La IANA, l'ente che coordina
gli indirizzi a livello mondiale, ha distribuito gli ultimi blocchi liberi nel 2011, e il RIPE NCC, che
li assegna in Europa, ha esaurito i suoi nel 2019. Le soluzioni sono due:

- **IPv6**, la nuova versione del protocollo, usa indirizzi di 128 bit (2<sup>128</sup> combinazioni,
  un numero di 39 cifre). Un indirizzo IPv6 si scrive in esadecimale, ad esempio
  `2001:db8::8a2e:370:7334`;
- il **NAT** (*Network Address Translation*): il router di casa ha un solo indirizzo pubblico e assegna
  ai dispositivi della casa indirizzi privati (quelli che cominciano con `192.168.` o `10.`), facendo
  da intermediario.

Gli indirizzi sono assegnati in modo **gerarchico**: la IANA delega blocchi di indirizzi a cinque
registri regionali (per l'Europa il RIPE NCC, che ha sede ad Amsterdam), che li assegnano ai fornitori
di connessione e alle grandi organizzazioni, che a loro volta li assegnano ai singoli dispositivi.

!!! warning "Un indirizzo IP non è un indirizzo di casa"
    Il vostro indirizzo IP di solito cambia: il fornitore di connessione ve ne assegna uno temporaneo,
    spesso condiviso con altri utenti. Un indirizzo IP indica più o meno da quale rete vi collegate e
    da quale città, ma da solo non identifica una persona. Insieme ai registri del fornitore, però,
    può farlo: per questo è considerato un **dato personale** (ne parleremo nella L07).

### TCP: arrivare tutto, e in ordine

IP si preoccupa di far arrivare ogni pacchetto a destinazione, ma non garantisce nulla: un pacchetto
può perdersi, arrivare due volte o arrivare in ritardo. Il livello di trasporto rimedia.

**TCP** (*Transmission Control Protocol*) divide i dati in segmenti numerati, chiede al destinatario di
confermare la ricezione di ciascuno, rispedisce quelli persi e rimette tutto in ordine. È il protocollo
usato quando ogni bit conta: pagine web, posta, file.

**UDP** (*User Datagram Protocol*) è più semplice e più veloce: spedisce e basta, senza conferme. Si
usa quando un pacchetto perso è meno grave di un ritardo, come nelle videochiamate o nei giochi online:
meglio un'immagine sgranata per un istante che una conversazione che si blocca.

Il livello di trasporto usa anche le **porte**, numeri che identificano il programma a cui è destinato
un messaggio sullo stesso computer. Un server web risponde sulla porta 443 (HTTPS) o sulla 80 (HTTP), un
server di posta sulla 25. Se l'indirizzo IP è il numero civico di un condominio, la porta è il numero
dell'interno.

### DNS: l'elenco telefonico di Internet

Nessuno ricorda un numero come `203.0.113.42`: ricordiamo `unibo.it`. Il **DNS** (*Domain Name System*) è il sistema
che traduce i **nomi di dominio**, comodi per le persone, negli indirizzi IP, necessari alle macchine.

I nomi di dominio sono organizzati ad **albero**, la struttura dati che abbiamo visto nella L03, e si
leggono da destra verso sinistra:

- in cima c'è la **radice**, gestita in ultima istanza dall'ICANN;
- sotto la radice ci sono i **domini di primo livello** (*TLD*, *Top-Level Domain*): quelli nazionali
  come `.it`, `.fr`, `.jp` e quelli generici come `.com`, `.org`, `.edu`;
- sotto ciascun TLD ci sono i **domini di secondo livello**, registrati da organizzazioni e persone:
  `unibo.it`, `wikipedia.org`. In Italia li gestisce il Registro .it;
- chi possiede un dominio di secondo livello può creare tutti i **sottodomini** che vuole: `www.unibo.it`,
  `virtuale.unibo.it`, `it.wikipedia.org`.

<figure markdown>
![Lo spazio dei nomi di dominio come albero](https://commons.wikimedia.org/wiki/Special:FilePath/Domain_name_space.svg?width=1000){ width="520" loading=lazy }
<figcaption>Lo spazio dei nomi del DNS è un albero: ogni nodo è un dominio, e ogni dominio può delegare
la gestione dei propri sottodomini. LionKimbro, pubblico dominio, via Wikimedia Commons.</figcaption>
</figure>

Quando digitate `it.wikipedia.org`, il vostro computer chiede l'indirizzo a un **resolver**, di solito
quello del vostro fornitore di connessione. Se il resolver non conosce già la risposta, la cerca
scendendo l'albero: chiede a un server della radice chi gestisce `.org`, chiede al server di `.org` chi
gestisce `wikipedia.org`, chiede a quest'ultimo l'indirizzo di `it.wikipedia.org`. La risposta viene
poi conservata per un po' in memoria (*cache*), così la volta successiva arriva subito.

<figure markdown>
![Esempio di risoluzione iterativa di un nome di dominio](https://commons.wikimedia.org/wiki/Special:FilePath/Example_of_an_iterative_DNS_resolver-it.svg?width=1000){ width="560" loading=lazy }
<figcaption>Il resolver interroga in successione la radice, il server di <code>.org</code> e il
server di <code>wikipedia.org</code>. Versione italiana dell'originale di Mfwitten, via Wikimedia Commons.</figcaption>
</figure>

### Mettiamo insieme i pezzi

Torniamo alla domanda iniziale. Ecco, semplificando, che cosa succede quando scrivete `unibo.it` e
premete Invio:

| # | Che cosa succede | Chi lo fa |
|---|---|---|
| 1 | Il browser chiede al DNS l'indirizzo IP di `unibo.it` | DNS (livello applicazione) |
| 2 | Il browser apre una connessione con quell'indirizzo, sulla porta 443 | TCP (trasporto) |
| 3 | Il browser invia una richiesta: "dammi la pagina principale" | HTTP (applicazione) |
| 4 | La richiesta viene divisa in pacchetti, ciascuno con l'indirizzo di destinazione | IP (rete) |
| 5 | I pacchetti passano dal Wi-Fi al router di casa, poi di router in router fino al server | collegamento e rete |
| 6 | Il server risponde con la pagina, divisa a sua volta in pacchetti | tutti i livelli, in senso inverso |
| 7 | Il browser riceve i pacchetti, li rimette in ordine e mostra la pagina | TCP, poi il browser |

Tutto questo accade, di solito, in qualche decina di millisecondi. Il passo 3, la conversazione tra il
browser e il server web, è il tema della prossima lezione.

---

## 4. L'infrastruttura fisica

### La "nuvola" è sott'acqua

Parliamo di *cloud*, di "nuvola", come se i dati fluttuassero nell'aria. In realtà quasi tutto il
traffico tra continenti viaggia in **cavi in fibra ottica posati sul fondo del mare**. Secondo
TeleGeography, la società che ne cura la mappa più completa, all'inizio del 2025 i cavi sottomarini in
servizio erano circa 570, per una lunghezza complessiva di circa 1,4 milioni di chilometri. I satelliti
servono soprattutto per raggiungere luoghi isolati, ma trasportano una quota piccola del traffico.

<figure markdown>
![Sezione di un cavo sottomarino per telecomunicazioni](https://commons.wikimedia.org/wiki/Special:FilePath/Submarine_cable_cross-section.svg?width=800){ width="380" loading=lazy }
<figcaption>Sezione di un cavo sottomarino: al centro le fibre ottiche, intorno strati di protezione,
un conduttore di rame che alimenta i ripetitori e un'armatura d'acciaio. Mysid, via Wikimedia Commons.</figcaption>
</figure>

Al centro del cavo ci sono poche coppie di fibre ottiche, sottili come capelli; tutto il resto è
protezione. Il cavo arriva a terra in punti precisi della costa, detti **punti di approdo**. Il
Mediterraneo è uno snodo importante tra Europa, Africa e Asia, e diversi cavi approdano in Sicilia.

I cavi si rompono più spesso di quanto si pensi, soprattutto per colpa di ancore e reti da pesca, e
vengono riparati da navi specializzate. Negli ultimi anni sono diventati anche una questione
geopolitica: chi li possiede, chi li può danneggiare, quali paesi restano isolati se si rompono. Un
tempo erano posati da consorzi di compagnie telefoniche; oggi molti dei nuovi cavi sono di proprietà
delle grandi aziende tecnologiche.

### I data center

All'altro capo dei cavi ci sono i **data center**: edifici pieni di server, collegati alla rete con
connessioni velocissime, alimentati giorno e notte e raffreddati continuamente. Quando salvate un file
"nel cloud", lo state salvando sul disco di un computer in uno di questi edifici.

<figure markdown>
![Il data center del CERN](https://commons.wikimedia.org/wiki/Special:FilePath/CERN_Server_03.jpg?width=1200){ width="560" loading=lazy }
<figcaption>Una sala server del CERN di Ginevra. Florian Hirzinger, via Wikimedia Commons.</figcaption>
</figure>

I data center consumano molta energia. Secondo l'Agenzia Internazionale dell'Energia, nel 2024 hanno
consumato circa 415 terawattora di elettricità, l'1,5% del consumo mondiale; la stessa agenzia prevede
che entro il 2030 il consumo più che raddoppi, fino a circa 945 TWh, soprattutto per la crescita
dell'intelligenza artificiale. Il consumo è anche molto concentrato: nel 2024 gli Stati Uniti ne
rappresentavano il 45%, la Cina il 25% e l'Europa il 15%. A questo si aggiunge l'acqua usata per il
raffreddamento, che pesa soprattutto nelle zone già povere d'acqua. Torneremo su questi numeri nella L15,
quando parleremo del costo ambientale dei modelli linguistici.

---

## 5. Chi c'è in rete, e in quale lingua

### Il divario digitale

Secondo l'Unione Internazionale delle Telecomunicazioni (ITU), l'agenzia dell'ONU che si occupa di
telecomunicazioni, nel 2026 usano Internet circa **6,3 miliardi** di persone, il 76% della popolazione
mondiale. Restano fuori circa **2 miliardi** di persone, e la distribuzione è tutt'altro che uniforme:

- usa Internet il **93%** delle persone nei paesi ad alto reddito, il **32%** in quelli a basso reddito;
- nelle città è online l'82% delle persone, nelle aree rurali il 63%;
- è online il 79% degli uomini e il 74% delle donne;
- tra i giovani dai 15 ai 24 anni la quota sale all'86%.

Si parla di **divario digitale** (*digital divide*) per indicare queste disuguaglianze. Il termine è
nato per indicare chi ha accesso alla rete e chi no, ma oggi gli studiosi ne distinguono almeno tre
livelli: l'**accesso** (avere una connessione e un dispositivo), le **competenze** (saperli usare) e i
**benefici** (riuscire a ricavarne qualcosa di utile, come un lavoro, un servizio, un'informazione
affidabile). Anche in un paese dove quasi tutti sono connessi, il secondo e il terzo livello possono
fare molta differenza. Lo vedrete anche in questo corso: avere un computer non basta per saper
pubblicare una pagina web o valutare una fonte.

### Le lingue del Web

In quale lingua è scritto il Web? Il servizio W3Techs analizza ogni giorno i dieci milioni di siti più
visitati e ne rileva la lingua. Ecco i dati del 18 novembre 2026:

| Lingua | Quota dei siti |
|---|---|
| Inglese | 49,5% |
| Spagnolo | 6,0% |
| Tedesco | 5,9% |
| Giapponese | 4,9% |
| Francese | 4,6% |
| Portoghese | 4,2% |
| Russo | 3,4% |
| **Italiano** | **2,7%** |
| Cinese | 1,2% |
| Arabo | 0,6% |

Quasi un sito su due è in inglese, una lingua parlata come prima lingua da una piccola parte
dell'umanità. Il cinese, che ha più parlanti nativi di qualsiasi altra lingua, si ferma all'1,2%; lingue
con centinaia di milioni di parlanti, come l'hindi o il bengalese, non arrivano allo 0,1%.

!!! question "Leggere un dato con spirito critico"
    Prima di trarre conclusioni, chiediamoci come è stato prodotto questo dato (ricordate i *capta*
    della L01). W3Techs guarda solo i siti **più visitati**, solo la **pagina principale**, e conta i
    **siti**, non le pagine né le persone che li leggono. Molti contenuti in cinese stanno su piattaforme
    chiuse, che non compaiono come siti separati; molti contenuti in lingue africane o indiane circolano
    sui social e nei messaggi, non sul Web. Il dato misura bene una cosa precisa, e male tutto il resto.

Questa disuguaglianza ha conseguenze che vanno oltre la navigazione. I modelli linguistici e gli strumenti
di traduzione automatica imparano dai testi che trovano in rete: se una lingua è poco presente sul Web,
gli strumenti funzioneranno peggio per chi la parla. Joshi e colleghi (2020) hanno mostrato che la
grande maggioranza delle oltre 7.000 lingue del mondo è quasi del tutto ignorata dalle tecnologie
linguistiche. Ne parleremo nel blocco sul NLP (L11).

### Nomi di dominio in tutte le scritture

Per decenni i nomi di dominio potevano contenere solo lettere latine senza accenti, cifre e trattini:
in pratica, i caratteri ASCII della L02. Un sito in arabo, in russo o in cinese doveva comunque avere un
indirizzo in caratteri latini.

Dal 2003 esiste uno standard, chiamato **IDNA**, che permette di usare nei nomi di dominio qualsiasi
carattere Unicode. Il trucco è una codifica, chiamata **Punycode**, che trasforma il nome in una
stringa ASCII che comincia con `xn--`. Il DNS continua a vedere solo ASCII, mentre il browser mostra
all'utente il nome originale.

| Nome che vedete | Nome che vede il DNS |
|---|---|
| `città.it` | `xn--citt-3na.it` |
| `università.it` | `xn--universit-y1a.it` |
| `пример.рф` | `xn--e1afmkfd.xn--p1ai` |

Nel maggio 2010 sono entrati nella radice del DNS i primi domini di primo livello interamente in
caratteri non latini: `مصر` (Egitto), `السعودية` (Arabia Saudita) e `امارات` (Emirati Arabi Uniti),
seguiti a breve da `.рф` per la Russia e da quelli in caratteri cinesi.

!!! warning "Lettere che si somigliano"
    La `а` cirillica e la `a` latina sono caratteri diversi, con punti di codice diversi, ma hanno lo
    stesso aspetto. Un truffatore può registrare un dominio che *sembra* identico a quello di una banca,
    usando qualche lettera cirillica. Si chiama **attacco omografico**, e per difendersi i browser in
    alcuni casi mostrano l'indirizzo in Punycode invece che nella forma originale.

### Le lingue minoritarie in rete

Per le lingue con pochi parlanti, o senza un riconoscimento ufficiale, la rete è insieme un rischio e
un'opportunità. Il rischio è che l'uso quotidiano della rete in una lingua dominante acceleri
l'abbandono della lingua di casa. L'opportunità è che pubblicare costa pochissimo: esistono edizioni di
Wikipedia in siciliano, napoletano, friulano, ladino e in oltre trecento lingue, scritte da volontari.
Una lingua presente in rete può essere usata dai giovani, raccolta in corpora, e dare dati agli
strumenti di cui parleremo nel blocco C.

---

## Riepilogo

| Concetto | In una frase |
|---|---|
| Internet | Una rete di reti indipendenti che usano gli stessi protocolli |
| Commutazione di pacchetto | I dati viaggiano in pezzi separati, ciascuno per la sua strada |
| Protocollo | Un insieme di regole condivise per comunicare |
| Pila TCP/IP | Quattro livelli: collegamento, rete (IP), trasporto (TCP/UDP), applicazione |
| Indirizzo IP | Il numero che identifica un host in rete (IPv4: 32 bit; IPv6: 128 bit) |
| DNS | Il sistema, organizzato ad albero, che traduce i nomi in indirizzi IP |
| Infrastruttura | Cavi sottomarini, router, data center: oggetti fisici, con costi energetici |
| Divario digitale | Disuguaglianze di accesso, competenze e benefici |
| IDN | Nomi di dominio in scritture non latine, codificati in Punycode |

---

## Attività

**Durante la lezione (online)**

1. **Qual è il vostro indirizzo IP?** Cercate "what is my IP" su un motore di ricerca. Confrontate in
   chat la città indicata: corrisponde a dove siete davvero?
2. **Interrogate il DNS.** Con lo strumento [Dig di Google Admin Toolbox](https://toolbox.googleapps.com/apps/dig/)
   cercate l'indirizzo IP di `unibo.it`, di `wikipedia.org` e di un sito del vostro paese o della
   vostra lingua. Provate anche a cercare `città.it`: che cosa vedete?
3. **Seguite un pacchetto.** Con un servizio di *visual traceroute* (cercate "visual traceroute
   online") tracciate il percorso verso un sito giapponese, ad esempio `nhk.or.jp`. Quanti router
   attraversa? Passa da qualche cavo sottomarino?
4. **Esplorate i cavi.** Aprite la [Submarine Cable Map](https://www.submarinecablemap.com/) e cercate i
   cavi che approdano in Italia. Da dove partono? Dove arrivano?

??? tip "Per chi vuole usare il terminale"
    Gli stessi esperimenti si possono fare dal terminale del vostro computer (su Windows il *Prompt dei
    comandi*, su macOS e Linux il *Terminale*):

    ```text
    ping unibo.it
    nslookup unibo.it
    tracert nhk.or.jp       (Windows)
    traceroute nhk.or.jp    (macOS e Linux)
    ```

**A casa (facoltativo)**

- Scegliete una lingua che conoscete o che studiate, diversa dall'inglese e dall'italiano. Cercate su
  W3Techs la sua quota di siti e su Wikipedia (pagina *Lista di Wikipedia*) il numero di voci della sua
  edizione. Confrontateli con il numero approssimativo di parlanti. Scrivete tre righe di commento.

---

## Mettetevi alla prova

**1.** Che cosa significa che Internet è una "rete di reti"?

- A. Che è una sola grande rete gestita da un'unica organizzazione
- B. Che è formata da molte reti indipendenti che usano gli stessi protocolli per comunicare
- C. Che ogni computer è collegato direttamente a tutti gli altri
- D. Che esistono tante Internet diverse, una per paese

??? success "Soluzione"
    **B.** Il nome stesso viene da *internetworking*, il collegamento tra reti diverse.

**2.** Qual è il principale vantaggio della commutazione di pacchetto rispetto a quella di circuito?

- A. Garantisce che i pacchetti arrivino sempre nell'ordine in cui sono partiti
- B. Riserva un canale dedicato a ogni comunicazione
- C. Usa le risorse della rete solo quando serve e permette di aggirare i guasti
- D. Non ha bisogno di indirizzi

??? success "Soluzione"
    **C.** I pacchetti possono anzi arrivare in disordine: a rimetterli in sequenza ci pensa TCP.

**3.** A quale livello della pila TCP/IP appartiene il protocollo IP?

- A. Applicazione
- B. Trasporto
- C. Rete
- D. Collegamento

??? success "Soluzione"
    **C.** IP si occupa di far arrivare i pacchetti all'host di destinazione attraverso reti diverse.

**4.** Perché per le videochiamate si usa spesso UDP invece di TCP?

- A. Perché UDP è più sicuro
- B. Perché un pacchetto perso è meno grave di un ritardo, e UDP non aspetta le conferme
- C. Perché TCP non può trasportare audio e video
- D. Perché UDP usa indirizzi IPv6

??? success "Soluzione"
    **B.**

**5.** Quanti indirizzi diversi si possono scrivere con IPv4?

- A. 256
- B. 65.536
- C. Circa 4,3 miliardi (2<sup>32</sup>)
- D. Infiniti

??? success "Soluzione"
    **C.** Un indirizzo IPv4 è lungo 32 bit. Gli indirizzi liberi sono finiti: per questo si è passati
    a IPv6, che ne usa 128.

**6.** Che cosa fa il DNS?

- A. Cifra le comunicazioni tra browser e server
- B. Traduce i nomi di dominio in indirizzi IP
- C. Assegna un indirizzo IP al vostro computer
- D. Divide i messaggi in pacchetti

??? success "Soluzione"
    **B.** I nomi di dominio sono organizzati ad albero, dalla radice ai domini di primo livello
    (`.it`, `.org`) e via via ai sottodomini.

**7.** Quale di queste affermazioni sull'infrastruttura di Internet è corretta?

- A. La maggior parte del traffico tra continenti viaggia via satellite
- B. Il "cloud" non occupa spazio fisico
- C. La maggior parte del traffico tra continenti viaggia in cavi in fibra ottica sottomarini
- D. I data center consumano una quantità trascurabile di elettricità

??? success "Soluzione"
    **C.** E secondo l'IEA i data center consumano circa l'1,5% dell'elettricità mondiale, una quota
    destinata a crescere.

**8.** Che cos'è il Punycode?

- A. Una lingua artificiale usata dai programmatori
- B. Un modo di scrivere nomi di dominio non ASCII usando solo caratteri ASCII, con il prefisso `xn--`
- C. Un protocollo per la posta elettronica
- D. Un tipo di attacco informatico

??? success "Soluzione"
    **B.** Permette di avere domini come `città.it` o `.рф` senza cambiare il funzionamento del DNS.

---

## Per approfondire

- Leiner, B. M., Cerf, V. G., Clark, D. D., Kahn, R. E., Kleinrock, L., Lynch, D. C., Postel, J.,
  Roberts, L. G., & Wolff, S. (2009). A brief history of the Internet. *ACM SIGCOMM Computer
  Communication Review*, *39*(5), 22–31. [doi:10.1145/1629607.1629613](https://doi.org/10.1145/1629607.1629613)
  La storia raccontata da chi l'ha fatta.
- Cerf, V. G., & Kahn, R. E. (1974). A protocol for packet network intercommunication. *IEEE
  Transactions on Communications*, *22*(5), 637–648. [doi:10.1109/TCOM.1974.1092259](https://doi.org/10.1109/TCOM.1974.1092259)
  L'articolo da cui nasce TCP/IP (per curiosi: è tecnico).
- MDN Web Docs, [How does the Internet work?](https://developer.mozilla.org/en-US/docs/Learn_web_development/Howto/Web_mechanics/How_does_the_Internet_work)
  Una spiegazione breve e chiara, in inglese.
- TeleGeography, [Submarine Cable Map](https://www.submarinecablemap.com/).
- International Telecommunication Union (2026). [*Measuring digital development: Facts and Figures 2026*](https://www.itu.int/itu-d/reports/statistics/facts-figures-2026/).
- International Energy Agency (2025). [*Energy and AI*](https://www.iea.org/reports/energy-and-ai).
- W3Techs, [Usage statistics of content languages for websites](https://w3techs.com/technologies/overview/content_language).
- Joshi, P., Santy, S., Budhiraja, A., Bali, K., & Choudhury, M. (2020). The state and fate of
  linguistic diversity and inclusion in the NLP world. In *Proceedings of ACL 2020*, 6282–6293.
  [doi:10.18653/v1/2020.acl-main.560](https://doi.org/10.18653/v1/2020.acl-main.560)

Elenco completo in [Letture e materiali](../letture.md#blocco-b-internet-e-web).

## Parole chiave

[Internet](../glossario.md#internet) ·
[Host](../glossario.md#host) ·
[Router](../glossario.md#router) ·
[Client/server](../glossario.md#clientserver) ·
[Peer-to-peer](../glossario.md#peer-to-peer) ·
[Commutazione di pacchetto](../glossario.md#commutazione-di-pacchetto) ·
[Protocollo](../glossario.md#protocollo) ·
[TCP/IP](../glossario.md#tcpip) ·
[Indirizzo IP](../glossario.md#indirizzo-ip) ·
[DNS](../glossario.md#dns-domain-name-system) ·
[Nome di dominio](../glossario.md#nome-di-dominio) ·
[Data center](../glossario.md#data-center) ·
[Divario digitale](../glossario.md#divario-digitale) ·
[IDN e Punycode](../glossario.md#idn-e-punycode)
