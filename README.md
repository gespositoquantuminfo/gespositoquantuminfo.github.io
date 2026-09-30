# Gianluca Esposito — sito personale

Sito statico: `index.html` e le immagini vengono pubblicati direttamente su GitHub Pages.

## Miniature delle pubblicazioni

Carica le immagini nella cartella `images/publications/` usando i nomi esatti riportati qui sotto (minuscole ed estensione `.png`). Non occorre modificare l’HTML. Puoi aggiungerne anche solo alcune: se un’immagine manca o non è valida, la miniatura resta nascosta e il testo occupa lo spazio disponibile.

| File                                   | Pubblicazione / preprint                                                             |
| ----------------------------------------| --------------------------------------------------------------------------------------|
| `tensor-network-nonstabilizerness.png` | Nonstabilizerness of quantum tensor network states is intractable in two dimensions  |
| `mixed-state-stabilizer-entropy.png`   | Stabilizer entropy is trustworthy for mixed states                                   |
| `clifford-chaos.png`                   | Probes of chaos over the Clifford group and approach to Haar values                  |
| `non-local-magic.png`                  | Experimental demonstration of non-local magic in a superconducting quantum processor |
| `chsh-nonstabilizerness.png`           | Non-stabilizerness and violations of CHSH inequalities                               |
| `random-bipartite-entropies.png`       | Entanglement and Stabilizer entropies of random bipartite pure quantum states        |
| `lattice-gauge-magic.png`              | Magic of discrete Lattice Gauge theories                                             |
| `quantum-tetrahedra.png`               | Stabilizer entropy of quantum tetrahedra                                             |
| `purity-phase-transition.png`          | Phase transition in stabilizer entropy and efficient purity estimation               |

### Se le figure sono PDF

1. Carica i PDF in `sources/publications/`, usando i nomi della tabella con estensione `.pdf` al posto di `.png` (per esempio `quantum-tetrahedra.pdf`).
2. Dalla directory del progetto esegui:

   ```sh
   python3 scripts/convert-publication-pdfs.py
   ```

3. Includi i PNG generati in `images/publications/` nel commit e nel push.

Il comando converte la **prima pagina** di ciascun PDF, con il lato maggiore di 600 px, senza ritagli. Usa PDF della figura che vuoi mostrare: se carichi l’articolo completo verrà mostrata la sua prima pagina. Puoi rieseguire il comando dopo aver sostituito i PDF. Se un PDF non è valido, la miniatura precedente viene conservata. Eliminare un PDF non elimina il PNG già generato: per togliere una miniatura elimina anche il PNG.

La conversione richiede Python 3 e `pdftoppm` (Poppler), già disponibili in questo ambiente. Su Ubuntu, se necessario, installa Poppler con `sudo apt install poppler-utils`. GitHub Pages serve direttamente i PNG generati: **non converte i PDF al momento del deployment**.

### Aspetto delle miniature

Per immagini preparate manualmente, una larghezza di 400–600 px è sufficiente; preferisci file leggeri (indicativamente meno di 200 KB). Il riquadro ha proporzioni 4:3 e mostra la figura intera senza ritagliarla, su fondo bianco, anche se l’immagine ha proporzioni diverse. Le miniature sono decorative: titolo e link del lavoro restano nel testo accanto.

Per sostituire una miniatura, sovrascrivi il file corrispondente. Per rimuoverla, elimina quel file. Per un nuovo lavoro, copia una voce nell’HTML e assegna al suo elemento `img` un nuovo percorso.

## Deployment su GitHub Pages

Includi nel commit e nel push sia `index.html` sia i file in `images/publications/`. Se il deployment usa un workflow che carica un artefatto, includi anche la cartella `images/` nell’artefatto insieme all’HTML. I percorsi sono relativi, senza `/` iniziale: funzionano anche quando il sito è pubblicato sotto il nome della repository (`https://utente.github.io/repository/`). Non sono necessari build, dipendenze o servizi esterni. Un piccolo gestore JavaScript mostra le immagini dopo il caricamento; se JavaScript è disabilitato, rimangono visibili tutti i testi e i link.

Per un’anteprima locale dalla directory del progetto:

```sh
python3 -m http.server 8000
```

Apri `http://localhost:8000/`. Dopo aver sostituito un’immagine già pubblicata, se compare ancora quella vecchia, ricarica la pagina svuotando la cache.
