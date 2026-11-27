# Creation Engine & Console Notes (IT)
Technical notes exploring how *The Elder Scrolls V: Skyrim Special Edition* works under the hood: console commands, Papyrus functions, object IDs, world placement mechanics, and engine quirks observed during an unmodded playthrough. Written in Italian, as I'm currently playing the Italian localization before switching to the original English version.

- [1. Comandi](#commands)
- [2. Motore Grafico](#engine)
- [Credits & License](#credits)
- [Connect](#connect)

## 1. Comandi Console e Papyrus principali <a id="commands"></a>

### Ricerca ID e ispezione oggetti
* `help "<nome>" 4` — Cerca il **Base ID** di un oggetto, NPC, incantesimo o oggetto statico (es. `help "map" 4`).
* *(Click sull'oggetto in console)* — Seleziona il **Reference ID** dell'istanza nel mondo di gioco.
* `getpos x` / `getpos y` / `getpos z` — Restituisce le coordinate esatte dell'oggetto selezionato.
* `getangle x` / `getangle y` / `getangle z` — Restituisce l'inclinazione sugli assi dell'oggetto selezionato.

### Posizionamento, scala e gestione oggetti
* `player.placeatme <BaseID> <quantità>` — Genera un'istanza dell'oggetto alle coordinate del giocatore.
* `setpos x <valore>` / `setpos y <valore>` / `setpos z <valore>` — Sposta l'oggetto selezionato alle coordinate indicate.
* `setangle x <valore>` / `setangle y <valore>` / `setangle z <valore>` — Ruota l'oggetto selezionato (utile impostare `x 0` e `y 0` per metterlo in bolla).
* `setscale <valore>` — Ridimensiona l'oggetto selezionato (`1.0` è la scala predefinita).
* `disable` — Nasconde e disattiva l'oggetto selezionato.
* `enable` — Riattiva un oggetto disabilitato.
* `markfordelete` — Segna un oggetto generato con `placeatme` per la rimozione definitiva al successivo caricamento (usare insieme a `disable`).

### Funzioni Papyrus invocabili da console (su oggetto selezionato)
* `callfunction "SetOpen" 1` / `0` — Apre o chiude porte, cancelli o contenitori animati.
* `callfunction "Lock" <livello>` — Blocca una serratura (`25` Principiante, `50` Apprendista, `75` Specialista, `100` Arduo, `255` Richiede chiave).
* `unlock` — Sblocca istantaneamente la serratura o il terminale selezionato.
* `callfunction "Reset"` — Esegue il reset dello stato Papyrus della cella o dell'oggetto selezionato.
* `recycleactor` — Ripristina un NPC o una creatura al suo stato e inventario iniziali.
* `resurrect` — Riporta in vita l'NPC selezionato (`resurrect 1` conserva l'inventario corrente).

### Giocatore, inventario e teletrasporto
* `player.additem <BaseID> <quantità>` — Aggiunge un oggetto nell'inventario del giocatore.
* `player.removeitem <BaseID> <quantità>` — Rimuove un oggetto dall'inventario.
* `moveto player` — Teletrasporta l'NPC o l'oggetto selezionato accanto al giocatore.
* `player.moveto <RefID>` — Teletrasporta il giocatore accanto all'NPC o all'oggetto indicato.
* `coc <EditorID_Cella>` — Teletrasporta il giocatore nella cella indicata (es. `coc WhiterunOrigin`).
* `tcl` — Attiva/disattiva le collisioni (noclip) per posizionare oggetti in punti difficili.
* `tfc` — Attiva/disattiva la telecamera libera (`tfc 1` mette anche in pausa il mondo).

### Missioni (Quest)
* `sqt` — Elenca le missioni attive e i relativi ID interni.
* `getstage <QuestID>` — Mostra lo stadio attuale di una missione.
* `setstage <QuestID> <stadio>` — Avanza una missione allo stadio specificato.

## 2. Struttura del Creation Engine <a id="engine"></a>

### Celle e caricamento

Il mondo di Skyrim è diviso in unità di spazio chiamate Cells, caricate attorno al giocatore mentre gioca. Possono essere esterne o interne, per limitare la quantità di dati caricati sulla macchina. La suddivisione in celle (e l'isolamento degli interni) serve a ridurre il carico su RAM e CPU/GPU, evitando di simulare contemporaneamente spazi troppo grandi.

Le celle esterne di Skyrim formano una griglia come i chunk di Minecraft. Di default il gioco carica una griglia 5×5 di celle attorno a te, chiamata uGridsToLoad=5 (render/simulation distance). Ogni cella interna è un worldspace isolato, come entrare in una nuova dimensione tramite portale (qui porta di caricamento).

### Reference ID e Base ID

Ad ogni oggetto nel gioco è associato un BaseID e un RefID. Il primo costituisce l'oggetto base su cui si costruisce l'oggetto nel gioco. Il BaseID è il modello generico di quell'oggetto o entità. Il RefID invece identifica la singola copia (istanza) di quel modello piazzata concretamente nel mondo.

### AI Packages

Ogni NPC o entità del gioco ha una lista di istruzioni. Il motore controlla continuamente quale pacchetto ha priorità in base a certe Conditions, come per esempio il valore di una variabile di missione.

### Havok (fisica legata al frame rate)

Per gestire la gravità degli oggetti il Creation Engine usa un sottosistema chiamato Havok. In Skyrim la fisica è strettamente legata agli fps (per questo di default il gioco è bloccato a 60, quelli per cui è stato progettato). In Skyrim 1 fotogramma = 1 unità di tempo fisico: se cambi la velocità dei fotogrammi, alteri il tempo della fisica di gioco.

## Credits & License <a id="credits"></a>

- **Repository License:** Unless otherwise specified, all other original content in this repository is governed by the terms in the main [README](../README.md).
- **Disclaimer:** This is an unofficial personal reference and is not affiliated with, endorsed, or sponsored by Bethesda Softworks or ZeniMax Media. *The Elder Scrolls V: Skyrim*, the Creation Engine, and related game content are trademarks and property of their respective owners.

## Connect
[![Linktree](https://img.shields.io/badge/Linktree-139651?style=for-the-badge&logo=linktree&logoColor=white)](https://linktr.ee/Stinker_Fish)
[![Discord Online](https://img.shields.io/discord/1356681047374299317?style=for-the-badge&logo=discord&logoColor=white&label=Discord&labelColor=555555&color=5865F2)](https://discord.gg/kTRQ7uXwpk)
