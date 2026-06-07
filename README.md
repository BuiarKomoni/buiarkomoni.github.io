# buiarkomoni.github.io — CV Buiar Komoni

CV statico pubblicato su GitHub Pages.
URL: https://buiarkomoni.github.io

## Struttura

```
docs/
├── index.html          # tutto il CV (HTML + CSS + JS inline)
├── .nojekyll           # disabilita Jekyll su GitHub Pages
└── img/
    ├── profilo.jpg         # foto profilo
    ├── home.jpeg           # sfondo mobile
    └── home-landscape.jpeg # sfondo desktop
```

Tutto in un unico file `index.html` — nessun framework, zero dipendenze.

---

## Come modificare il contenuto

### Testo profilo
Apri `docs/index.html` e cerca `id="tab-profilo"`. Lì trovi:
```html
<div id="tab-profilo" class="animate-fade-in space-y-8">
    <h2>Profilo Personale</h2>
    <p>...</p>
    <p>...</p>
</div>
```
Modifica i paragrafi.

### Esperienze e studi
Cerca `id="tab-esperienza"`. Ogni esperienza è un blocco:
```html
<div class="accent-card relative pl-8 p-4 rounded-3xl border border-white/10 bg-white/10">
    <div class="absolute w-4 h-4 bg-white/30 rounded-full ..."></div>
    <h3 class="text-white font-bold">Titolo ruolo</h3>
    <p class="text-xs text-gray-400">Azienda · Data</p>
    <p class="text-sm text-gray-300 mt-1">Descrizione</p>
</div>
```
Per aggiungerne una: copia l'intero blocco `accent-card` e incollalo dentro `#tab-esperienza`.

### Competenze / Digital Skills
Cerca `id="tab-competenze"`. Ogni skill è una card:
```html
<div class="skill-card accent-card group bg-white/10 p-4 rounded-3xl border border-white/10">
    <h4 class="text-white font-bold">ACRONIMO</h4>
    <p class="text-xs text-gray-300">Nome corso</p>
    <!-- tooltip hover -->
    <p class="text-xs text-gray-400 opacity-0 group-hover:opacity-100 transition-opacity">
        Dettagli corso
    </p>
</div>
```
#### Per cambiare il tooltip hover:
Modifica il `<p>` con `group-hover:opacity-100`. Puoi accorciarlo o allungarlo.

#### Per aggiungere una nuova skill:
1. Scegli un acronimo (es. `MYSQ`)
2. Copia un blocco `skill-card` esistente
3. Incollalo dentro la griglia (dopo un altro `skill-card`)
4. Cambia acronimo, nome corso e tooltip

#### Per togliere una skill:
Cancella l'intero blocco `<div class="skill-card ...">...</div>`.

### Contatti
Cerca `href="mailto:b.komoni@gmail.com"` o `href="tel:+41763846969"`.
Cambia indirizzi e numeri.

### Foto
Sostituisci i file in `docs/img/` con le tue immagini stesse dimensioni:
- `profilo.jpg`: 500×500 px (quadrata)
- `home.jpeg`: 1080×1920 px (ritratto)
- `home-landscape.jpeg`: 1920×1080 px (paesaggio)

---

## Come modificare lo stile

- **Colori accent (rosa)**: cerca `#f472b6` nel file e sostituisci
- **Sfondo card destra**: cambia `bg-black/30` su `<div class="flex-1 flex-col ... bg-black/30">`
- **Colore testo**: cerca `text-gray-200`, `text-gray-300`, `text-gray-400`
- **Font**: cerca `font-` (già Tailwind, cambia con `font-light`, `font-bold`, ecc.)
- **Hover rosa**: tutti i box hanno classe `accent-card` — lo stile hover è nelle righe CSS iniziali (cerca `.accent-card:hover`)

---

## Come pubblicare su GitHub Pages

### Primo deploy
```bash
# crea repo su GitHub (se non esiste)
gh repo create buiarkomoni.github.io --public --source . --remote origin --push

# attiva Pages su docs/
gh api --method POST repos/BuiarKomoni/buiarkomoni.github.io/pages -f 'source[branch]=main' -f 'source[path]=/docs'
```

### Aggiornare
```bash
git add -A
git commit -m "descrizione delle modifiche"
git push origin main
```
GitHub Pages aggiorna automaticamente in 1-2 minuti.

### URL
`https://buiarkomoni.github.io/`

---

## Consigli

- **Tooltip lunghi?** Accorcia il testo dentro `group-hover:opacity-100`
- **Vuoi aggiungere una sezione?** Copia lo schema tab: crea un nuovo `<input type="radio">`, una label e un `<div id="tab-nuova">`
- **Icone social**: SVG inline dentro `#mob-socials`, cambia solo i link `href`
- **Stampa/PDF**: il browser può salvare come PDF (Cmd+P / Ctrl+P)
