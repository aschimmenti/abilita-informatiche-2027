# Abilità Informatiche 2026/27

Sito del corso di idoneità *Abilità Informatiche (LM)* — Università di Bologna.

- `docs/` — le pagine del sito (MkDocs Material)
- `slides/` — le slide in Markdown (Marp), una per lezione: `slides/L01.md`, `slides/L02.md`…
- `slides/themes/abinf.css` — il tema grafico delle slide

Le slide vengono compilate in `docs/slides/` (HTML e PDF) e incorporate nelle pagine delle lezioni.
`docs/slides/` è generata automaticamente e non va modificata né committata.

## Anteprima in locale

Servono [uv](https://docs.astral.sh/uv/) (o Python) e Node.js.

```bash
# 1. compila le slide (HTML; aggiungi --pdf per il PDF, richiede Chrome)
npx @marp-team/marp-cli@4 --theme-set slides/themes --input-dir slides --output docs/slides --html --allow-local-files

# 2. avvia il sito
uv run --with-requirements requirements.txt mkdocs serve
```

Apri <http://127.0.0.1:8000>.

Per lavorare solo sulle slide, con anteprima che si aggiorna a ogni salvataggio:

```bash
npx @marp-team/marp-cli@4 --theme-set slides/themes --server slides
```

In alternativa, l'estensione *Marp for VS Code* mostra l'anteprima direttamente nell'editor
(per usare il tema, aggiungi `slides/themes/abinf.css` all'impostazione `markdown.marp.themes`).

## Aggiungere le slide di una lezione

1. Crea `slides/LNN.md` partendo da `slides/L01.md` (intestazione con `theme: abinf`).
2. Nella pagina `docs/lezioni/NN-….md`, subito dopo il riquadro *In sintesi*, copia il blocco
   `<div class="slides-embed">…</div>` della L01 cambiando `L01` in `LNN`.

## Pubblicazione

1. Crea su GitHub un repository vuoto `abilita-informatiche-2027`.
2. Sostituisci `USERNAME` in `mkdocs.yml` (`site_url`).
3. ```bash
   git init && git add . && git commit -m "Primo commit"
   git branch -M main
   git remote add origin git@github.com:aschimmenti/abilita-informatiche-2027.git
   git push -u origin main
   ```
4. Al primo push la Action compila slide e sito e crea il branch `gh-pages`. Poi *Settings → Pages →
   Deploy from a branch → `gh-pages` / root*.

Ogni push successivo su `main` aggiorna sito e slide.

## Licenza

Testi e slide: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.it).
