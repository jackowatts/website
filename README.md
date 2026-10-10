# Marco Giacovazzo — sito personale

> Visual webiste design and README.md file template developed with AI assistance (ChatGPT 6-Luna).

Sito statico personale per presentare il percorso di studi in Fisica alla Sapienza Università di Roma e raccogliere appunti, materiali e progetti. È realizzato con HTML, CSS e JavaScript e pubblicato tramite GitHub Pages.

## Pagine e funzionalità

- `index.html`: profilo, formazione, materiali, progetti e contatti.
- `archivio.html`: archivio degli appunti della laurea triennale e magistrale.
- `404.html`: pagina mostrata per gli indirizzi non trovati.
- Tema scuro predefinito, con possibilità di passare al tema chiaro.
- Inglese predefinito; il selettore con la bandiera alterna inglese e italiano. Lingua e tema scelti vengono ricordati nel browser.
- Transizioni leggere fra pagine nei browser compatibili, disattivate per chi preferisce il movimento ridotto.
- Credito per la grafica sviluppata con l’assistenza di ChatGPT nel piè di pagina.

## Anteprima e sviluppo in IntelliJ IDEA

1. Apri il repository in IntelliJ IDEA e apri il terminale da **View → Tool Windows → Terminal**.
2. Se non hai già installato le dipendenze, esegui `npm.cmd install`.
3. Avvia il server di sviluppo con `npm.cmd start`. Se il browser non si apre automaticamente, visita **http://localhost:8080**.
4. Modifica `index.html`, `archivio.html`, `css/style.css` o `js/app.js`; il server aggiorna l’anteprima.
5. Premi **Ctrl+C** nel terminale per arrestare il server.

In PowerShell usa `npm.cmd` se il comando `npm` non viene riconosciuto o se l’esecuzione di script blocca `npm.ps1`. Dal Prompt dei comandi puoi usare `npm`.

Per generare e verificare il sito pronto per la pubblicazione:

```powershell
npm.cmd run build
```

Webpack crea i file finali nella cartella `dist`. Modifica i file sorgente, non quelli generati.

## Modificare i contenuti

### Pagine e testi semplici

La pagina iniziale è `index.html`; l’archivio degli appunti è `archivio.html`. Se una scritta è direttamente tra i tag HTML, puoi cambiarla nel relativo file. Per esempio:

```html
<h2>Titolo del progetto</h2>
```

può diventare:

```html
<h2>Simulazione del moto orbitale</h2>
```

In IntelliJ puoi cercare una scritta in tutto il progetto con **Ctrl+Shift+F**. Modifica i file sorgente, non `dist`: quella cartella viene rigenerata a ogni build.

La sezione **Projects** della homepage contiene testi di esempio: sostituisci titolo, anno, ambito e descrizione con i tuoi contenuti. In `archivio.html` puoi aggiornare le voci “Coming soon” quando aggiungi materiali.

### Traduzioni inglese e italiano

Le scritte precedute da un attributo `data-i18n`, ad esempio `data-i18n="projectsTitle"`, sono tradotte in `js/app.js`, nelle raccolte `en` e `it`. Per cambiare un testo, modifica la voce corrispondente **in entrambe** le raccolte:

```js
// Dentro en:
projectsTitle: 'Selected work',

// Dentro it:
projectsTitle: 'Lavori selezionati',
```

La stessa chiave viene usata nella pagina HTML:

```html
<h2 data-i18n="projectsTitle">Selected work</h2>
```

Quando aggiungi una nuova scritta traducibile, crea una chiave in entrambe le raccolte e usala nell’HTML con `data-i18n="nomeChiave"`. Se la chiave manca in una lingua, quel testo non avrà la traduzione corrispondente.

### Email e navigazione

Nella sezione contatti di `index.html`, aggiorna sia l’indirizzo visibile sia quello dentro `mailto:`:

```html
<a href="mailto:marco.giacovazzo@icloud.com">
  marco.giacovazzo@icloud.com
</a>
```

Per cambiare le voci del menu, modifica i link in `index.html` e `archivio.html`. Ogni collegamento a una sezione, come `href="#progetti"`, deve corrispondere all’`id` di quella sezione, ad esempio `id="progetti"`.

### Anteprima e pubblicazione

Nel terminale PowerShell di IntelliJ avvia l’anteprima con:

```powershell
npm.cmd start
```

Quando hai finito, verifica il sito con:

```powershell
npm.cmd run build
```

Se la build riesce, fai push delle modifiche su GitHub: il workflow del repository ricostruirà e pubblicherà il sito.

Colori e impaginazione si modificano in `css/style.css`. I file pubblicati con il sito sono pubblici: non inserirvi credenziali, documenti personali o materiali che devono restare privati.

## Pubblicazione con GitHub Pages

Il workflow `.github/workflows/pages.yml` esegue la build e pubblica il contenuto di `dist` dopo un push sul branch `main` o `master`. Puoi avviare la pubblicazione anche manualmente dalla scheda **Actions**.

1. Fai push del repository su GitHub.
2. Apri **Settings → Pages** e imposta **Build and deployment → Source** su **GitHub Actions**.
3. Controlla l’esito del workflow **Pubblica su GitHub Pages** nella scheda **Actions**.

L’indirizzo di un sito di progetto è in genere `https://<username>.github.io/<nome-repository>/`. Se il repository si chiama `<username>.github.io`, il sito è pubblicato all’indirizzo `https://<username>.github.io/`.

### Visibilità del repository

Con **GitHub Free**, il repository sorgente deve essere pubblico per usare GitHub Pages. Anche quando un piano consente di pubblicare da un repository privato, il sito Pages è normalmente accessibile pubblicamente: repository privato non significa sito privato. La pubblicazione privata del sito è una funzione per organizzazioni che usano **GitHub Enterprise Cloud**.

Per i dettagli aggiornati, consulta la documentazione ufficiale:

- [Creare un sito GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [Visibilità dei siti GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/changing-the-visibility-of-your-github-pages-site)
