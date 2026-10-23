# 🎵 Festival di Sanremo (1951–2023) — Analisi e storytelling

Come è cambiato il Festival di Sanremo nei suoi primi 73 anni, raccontato in tre atti: **come cambia il Festival, chi vince, cosa resta oggi**. Report interattivo con dati preparati in Excel/Power Query e visualizzati in Looker Studio. Esercitazione finale del modulo Looker Studio del corso Data Analyst EPICODE.

**Autrice:** Carol Pagano · **Strumenti:** Excel + Power Query (data engineering) · Google Looker Studio (report)

🔗 **[Apri il report interattivo su Looker Studio](https://datastudio.google.com/reporting/61e722f7-479c-4fcc-8c40-302c3946e428)**

📄 **[Nota metodologica completa (PDF)](./Metodologico_Sanremo.pdf)**

---

## I dati

Tre tabelle fornite dal corso (edizioni, classifiche, canzoni con popolarità Spotify), unite in un modello unico: **1.663 righe a livello canzone** e **73 righe a livello edizione**.

## Il lavoro sui dati (Power Query)

Tutta la pulizia e la preparazione sono state svolte in Power Query, con i passaggi tracciati e riproducibili. Interventi principali:

- **Gestione delle omonimie Spotify**: il dataset conteneva brani internazionali con lo stesso titolo di canzoni sanremesi (es. *"Luna"* di Feid, non di Loredana Bertè). Il merge è stato fatto su **interprete + canzone** (doppia chiave) e non sul solo titolo, per agganciare la popolarità solo ai veri brani del Festival.
- **Estrazione del periodo** dal campo testuale (es. "29-31 gennaio") in data di inizio, fine e mese.
- **Normalizzazione dell'esito** (Finalista / Non Finalista) accanto alla posizione originale.
- **Classificazione del genere dei vincitori** (Uomo, Donna, Gruppo, Misto) tramite una tabella di mappatura dedicata.
- **Conversione della durata** da mm:ss a minuti decimali; campi calcolati per decennio.

## Scelte metodologiche (alcune)

- **Genere dei vincitori** attribuito a livello di edizione: sulle 73 edizioni, 43 Uomo, 19 Donna, 9 Gruppo, 2 Misto — **26% di vittorie femminili**. La stessa proporzione calcolata a livello canzone (25,9%) coincide con quella per edizione (26,0%): dato robusto.
- **Partecipanti medi** calcolati sulla tabella a livello edizione (30,5 ≈ 30) e non a livello canzone, che avrebbe pesato di più le edizioni con più brani in gara.
- **Sedi**: l'edizione 1990 (Palafiori, per i lavori all'Ariston) è stata tenuta come categoria a sé e non accorpata al Casinò.

## Alcuni risultati

- Crescita dei partecipanti: da 3 nel 1951 al record di 58 nel 1967.
- Divario di genere che non si chiude: anni '50 quasi paritari, nessuna vittoria femminile nel 2020–2023.
- I tre brani sanremesi più ascoltati oggi su Spotify: *L'italiano* (Toto Cutugno, 1983), *Cenere* (Lazza, 2023), *Tango* (Tananai, 2023).

## File

| File / cartella | Contenuto |
|---|---|
| `Origine Dati/` | I dataset grezzi di partenza (edizioni, classifiche, canzoni, Spotify) |
| `Dati puliti/` | Le tabelle pulite e unite in Power Query |
| `Metodologico_Sanremo.pdf` | Nota metodologica completa (dati, pulizia, scelte, limiti) |
| `Festival_di_Sanremo.pdf` | Esportazione visiva del report Looker Studio |

## Nota sui limiti

Le edizioni per decennio non sono equinumerose (gli anni 2020 includono solo 2020–2023); la copertina dell'album non è disponibile per tutti i brani (498 su 1.663). Questi limiti sono dichiarati apertamente nel report e nella nota metodologica.
