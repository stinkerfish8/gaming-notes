## Comandi Console e Papyrus principali (Skyrim)

### 1. Ricerca ID e ispezione oggetti
* `help "<nome>" 4` — Cerca il **Base ID** di un oggetto, NPC, incantesimo o oggetto statico (es. `help "map" 4`).
* *(Click sull'oggetto in console)* — Seleziona il **Reference ID** dell'istanza nel mondo di gioco.
* `getpos x` / `getpos y` / `getpos z` — Restituisce le coordinate esatte dell'oggetto selezionato.
* `getangle x` / `getangle y` / `getangle z` — Restituisce l'inclinazione sugli assi dell'oggetto selezionato.

---

### 2. Posizionamento, scala e gestione oggetti
* `player.placeatme <BaseID> <quantità>` — Genera un'istanza dell'oggetto alle coordinate del giocatore.
* `setpos x <valore>` / `setpos y <valore>` / `setpos z <valore>` — Sposta l'oggetto selezionato alle coordinate indicate.
* `setangle x <valore>` / `setangle y <valore>` / `setangle z <valore>` — Ruota l'oggetto selezionato (utile impostare `x 0` e `y 0` per metterlo in bolla).
* `setscale <valore>` — Ridimensiona l'oggetto selezionato (`1.0` è la scala predefinita).
* `disable` — Nasconde e disattiva l'oggetto selezionato.
* `enable` — Riattiva un oggetto disabilitato.
* `markfordelete` — Segna un oggetto generato con `placeatme` per la rimozione definitiva al successivo caricamento (usare insieme a `disable`).

---

### 3. Funzioni Papyrus invocabili da console (su oggetto selezionato)
* `callfunction "SetOpen" 1` / `0` — Apre o chiude porte, cancelli o contenitori animati.
* `callfunction "Lock" <livello>` — Blocca una serratura (`25` Principiante, `50` Apprendista, `75` Specialista, `100` Arduo, `255` Richiede chiave).
* `unlock` — Sblocca istantaneamente la serratura o il terminale selezionato.
* `callfunction "Reset"` — Esegue il reset dello stato Papyrus della cella o dell'oggetto selezionato.
* `recycleactor` — Ripristina un NPC o una creatura al suo stato e inventario iniziali.
* `resurrect` — Riporta in vita l'NPC selezionato (`resurrect 1` conserva l'inventario corrente).

---

### 4. Giocatore, inventario e teletrasporto
* `player.additem <BaseID> <quantità>` — Aggiunge un oggetto nell'inventario del giocatore.
* `player.removeitem <BaseID> <quantità>` — Rimuove un oggetto dall'inventario.
* `moveto player` — Teletrasporta l'NPC o l'oggetto selezionato accanto al giocatore.
* `player.moveto <RefID>` — Teletrasporta il giocatore accanto all'NPC o all'oggetto indicato.
* `coc <EditorID_Cella>` — Teletrasporta il giocatore nella cella indicata (es. `coc WhiterunOrigin`).
* `tcl` — Attiva/disattiva le collisioni (noclip) per posizionare oggetti in punti difficili.
* `tfc` — Attiva/disattiva la telecamera libera (`tfc 1` mette anche in pausa il mondo).

---

### 5. Missioni (Quest)
* `sqt` — Elenca le missioni attive e i relativi ID interni.
* `getstage <QuestID>` — Mostra lo stadio attuale di una missione.
* `setstage <QuestID> <stadio>` — Avanza una missione allo stadio specificato.
