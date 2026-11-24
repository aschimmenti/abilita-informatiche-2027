# L08 · Laboratorio: costruire e pubblicare una pagina web

<p class="meta">Online · 2 ore · Blocco B — Internet e Web</p>

!!! abstract "In sintesi"
    Un laboratorio molto semplice. Nella L03 abbiamo visto che l'HTML è un linguaggio di marcatura, e
    nella L07 che il browser lo legge per mostrare una pagina. Oggi lo scriviamo noi: una pagina con
    titoli, paragrafi, elenchi, link e immagini, in due lingue; poi la rendiamo più bella con un po' di
    **CSS**; infine la pubblichiamo con **GitHub Pages**. Alla fine ognuno ha un indirizzo web pubblico.

<div class="slides-embed">
  <iframe src="../../slides/L08.html" title="Slide della lezione 8" loading="lazy" allowfullscreen></iframe>
</div>
<p class="slides-links">
  <a class="md-button" href="../../slides/L08.html" target="_blank" rel="noopener">Slide a schermo intero</a>
  <a class="md-button" href="../../slides/L08.pdf" target="_blank" rel="noopener">Slide in PDF</a>
</p>

## Obiettivi

Alla fine della lezione saprete:

- scrivere un documento **HTML** con la struttura di base, titoli, paragrafi, elenchi, link, immagini e tabelle;
- indicare la lingua con l'attributo `lang` e la codifica con `charset`;
- applicare **regole CSS** semplici (colori, caratteri, margini);
- pubblicare la pagina con **GitHub Pages**.

!!! info "Prima della lezione: installate due cose (10 minuti)"
    1. **Un editor di testo.** Useremo [Visual Studio Code](https://code.visualstudio.com/download),
       gratuito, per Windows, macOS e Linux. Va bene anche il Blocco note, ma VS Code colora il codice
       e segnala gli errori.
    2. **Un account GitHub.** Iscrivetevi gratuitamente su [github.com/signup](https://github.com/signup)
       e confermate l'indirizzo e-mail. Il nome utente farà parte dell'indirizzo della vostra pagina:
       sceglietene uno che non vi imbarazzi tra dieci anni.

---

## 1. HTML in dieci minuti

### Elementi e attributi

Un documento HTML è fatto di **elementi**: un tag di apertura, un contenuto e un tag di chiusura
(→ [Tag](../glossario.md#tag)). Gli **attributi** aggiungono informazioni al tag di apertura.

```html
<p>Questo è un <strong>paragrafo</strong> con un
   <a href="https://www.unibo.it">link</a>.</p>
```

Qui `p`, `strong` e `a` sono elementi; `href` è un attributo di `a`. Gli elementi si annidano come
nell'albero visto nella L03: `strong` e `a` sono *figli* di `p`.

### Lo scheletro di ogni pagina

```html
<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="utf-8">
  <title>La mia pagina</title>
</head>
<body>
  <h1>Il mio titolo</h1>
  <p>Il mio primo paragrafo.</p>
</body>
</html>
```

- `<!DOCTYPE html>` dice al browser che è HTML moderno.
- `lang="it"` dichiara la lingua del documento: serve ai lettori di schermo per scegliere la pronuncia,
  ai motori di ricerca e ai correttori ortografici.
- `<meta charset="utf-8">` dichiara la codifica (L02): senza, le lettere accentate rischiano di
  diventare *mojibake*.
- `<head>` contiene informazioni *sulla* pagina (come il `<title>`, che compare nella scheda del
  browser); `<body>` contiene ciò che si vede.

### Gli elementi che servono quasi sempre

| Che cosa | Elemento | Esempio |
|---|---|---|
| Titoli (da 1 a 6) | `h1` … `h6` | `<h2>Biografia</h2>` |
| Paragrafo | `p` | `<p>Testo.</p>` |
| Enfasi / importanza | `em`, `strong` | `<em>corsivo</em>` |
| Elenco puntato / numerato | `ul` / `ol` con `li` | `<ul><li>uno</li></ul>` |
| Link | `a` con `href` | `<a href="pagina2.html">avanti</a>` |
| Immagine | `img` con `src` e `alt` | `<img src="foto.jpg" alt="Descrizione">` |
| Citazione | `blockquote` | `<blockquote>…</blockquote>` |
| Tabella | `table`, `tr`, `th`, `td` | vedi sotto |

```html
<table>
  <tr><th>Lingua</th><th>Saluto</th></tr>
  <tr><td>Italiano</td><td>Ciao</td></tr>
  <tr><td>Spagnolo</td><td>Hola</td></tr>
</table>
```

!!! tip "Accessibilità di base"
    - Usate i titoli **in ordine** (un solo `h1`, poi `h2`, poi `h3`): chi usa un lettore di schermo
      naviga la pagina per titoli.
    - Ogni immagine ha un testo alternativo (`alt`) che la descrive; se è solo decorativa, `alt=""`.
    - Un link deve dire dove porta: meglio "[leggi il programma](../programma.md)" di "clicca qui".

### Una pagina bilingue

L'attributo `lang` si può mettere anche su un singolo elemento, per segnalare un passo in un'altra lingua:

```html
<html lang="it">
  ...
  <p>Il motto del corso è <span lang="en">"keep it simple"</span>.</p>
```

---

## 2. CSS in dieci minuti

L'HTML descrive *che cosa* è un pezzo di testo (un titolo, un elenco); il **CSS** (*Cascading Style
Sheets*) descrive *come appare*: colori, caratteri, spazi. Tenere separate le due cose è lo stesso
principio della L03: la struttura da una parte, la presentazione dall'altra.

Una regola CSS ha un **selettore** (a chi si applica) e delle **dichiarazioni** (che cosa cambia):

```css
h1 {
  color: darkred;
  font-family: Georgia, serif;
}

p {
  line-height: 1.5;
}
```

Si può scrivere in un file `stile.css` e collegarlo nell'`<head>`:

```html
<link rel="stylesheet" href="stile.css">
```

### Proprietà utili per cominciare

| Proprietà | Che cosa fa | Esempio |
|---|---|---|
| `color` | colore del testo | `color: #333;` |
| `background-color` | colore di sfondo | `background-color: #f5f5f5;` |
| `font-family` | carattere | `font-family: Arial, sans-serif;` |
| `font-size` | dimensione del testo | `font-size: 1.1rem;` |
| `margin` / `padding` | spazio fuori / dentro un elemento | `margin: 1rem;` |
| `max-width` | larghezza massima | `max-width: 40rem;` |

### Selettori: elementi, classi

Per colpire solo alcuni elementi si dà loro una **classe** e la si richiama con un punto:

```html
<p class="nota">Attenzione!</p>
```

```css
.nota {
  background-color: #fff3cd;
  padding: 0.5rem;
}
```

!!! tip "Una pagina leggibile con tre righe"
    ```css
    body { max-width: 40rem; margin: 2rem auto; font-family: Georgia, serif; line-height: 1.6; }
    ```
    Righe non troppo lunghe, centrate e con un'interlinea ampia rendono leggibile qualsiasi testo.

---

## 3. Pubblicare con GitHub Pages

**GitHub** è un servizio che conserva file in "repository" (cartelle online). **GitHub Pages** può
mostrare come sito web i file HTML di un repository, gratuitamente. Non serve la riga di comando:
basta il browser.

1. Accedete a GitHub e cliccate **New** (nuovo repository).
2. Chiamatelo **`nomeutente.github.io`**, sostituendo `nomeutente` con il vostro nome utente GitHub.
   Impostatelo come **Public** e cliccate **Create repository**.
3. Cliccate **uploading an existing file**, trascinate `index.html` (e `stile.css`, e le immagini) e
   cliccate **Commit changes**.
4. Attendete uno o due minuti e aprite **`https://nomeutente.github.io`**: la vostra pagina è online.

!!! warning "Attenzione"
    - Il file della pagina principale si deve chiamare esattamente **`index.html`**, in minuscolo.
    - Il repository è pubblico: non caricate nulla che non vogliate far vedere al mondo.
    - Se dopo qualche minuto vedete un errore 404, controllate nome del repository e nome del file
      (l'errore 404 lo abbiamo incontrato nella L07).

---

## Riepilogo

| Concetto | In una frase |
|---|---|
| Elemento | Tag di apertura, contenuto, tag di chiusura; si annidano ad albero |
| Attributo | Informazione aggiuntiva nel tag di apertura (`href`, `src`, `alt`, `lang`) |
| `lang`, `charset` | Dichiarano la lingua e la codifica del documento |
| CSS | Regole selettore + dichiarazioni che definiscono l'aspetto |
| GitHub Pages | Pubblica gratuitamente come sito i file di un repository |

---

## Attività

**Durante la lezione (online)**

1. **Il vostro `index.html`.** Create con VS Code un file `index.html` con lo scheletro visto sopra e
   apritelo nel browser (doppio clic sul file). Scrivete un `h1` con il vostro nome e un paragrafo di
   presentazione.
2. **Arricchitela.** Aggiungete: un elenco dei vostri interessi di studio, un link al sito del vostro
   corso di laurea, un'immagine con testo alternativo, una frase in un'altra lingua con `lang`.
3. **Aggiungete lo stile.** Create `stile.css`, collegatelo e cambiate almeno il colore dei titoli, il
   carattere e la larghezza del testo.
4. **Pubblicate.** Seguite i quattro passi della sezione 3 e inviate al docente l'indirizzo della
   vostra pagina.

**A casa (facoltativo)**

- Aggiungete una seconda pagina (`about.html`) e collegate le due pagine tra loro.
- Aprite la vostra pagina e premete `F12`: trovate l'elemento `h1`? Che cosa cambia se modificate il
  testo nello strumento (senza salvare)?

---

## Mettetevi alla prova

**1.** Quale elemento contiene le informazioni *sulla* pagina, che non si vedono nel corpo?

- A. `<body>`
- B. `<head>`
- C. `<title>`
- D. `<meta>`

??? success "Soluzione"
    **B.** `<head>` contiene il titolo, la codifica e il collegamento ai fogli di stile; `<body>` ciò
    che appare nella pagina.

**2.** A che cosa serve `<meta charset="utf-8">`?

- A. A dichiarare la lingua della pagina
- B. A dichiarare la codifica dei caratteri
- C. A collegare il file CSS
- D. A rendere la pagina più veloce

??? success "Soluzione"
    **B.** Senza la dichiarazione, le lettere accentate possono comparire come simboli strani
    (*mojibake*, L02). La lingua si dichiara con `lang`.

**3.** Che cosa fa la regola `h1 { color: red; }`?

- A. Rende rosso il testo di tutti i titoli di primo livello
- B. Rende rosso lo sfondo della pagina
- C. Rende rossi tutti i link
- D. Crea un nuovo titolo rosso

??? success "Soluzione"
    **A.** `h1` è il selettore, `color: red` la dichiarazione.

**4.** Perché è importante l'attributo `alt` di un'immagine?

- A. Per ingrandirla
- B. Per renderla un link
- C. Per descriverla a chi non può vederla e quando non si carica
- D. È obbligatorio solo per le foto

??? success "Soluzione"
    **C.** Lo leggono i lettori di schermo e compare se l'immagine non si carica.

---

## Per approfondire

- [MDN Web Docs in italiano: Introduzione al Web](https://developer.mozilla.org/it/docs/Learn_web_development/Getting_started/Your_first_website)
  — il tutorial di riferimento, gratuito.
- [Documentazione di GitHub Pages](https://docs.github.com/it/pages)
- [Visual Studio Code: scaricare](https://code.visualstudio.com/download) ·
  [GitHub: iscriversi](https://github.com/signup)

## Parole chiave

[HTML](../glossario.md#html) ·
[CSS](../glossario.md#css) ·
[Tag](../glossario.md#tag) ·
[GitHub Pages](../glossario.md#github-pages)
