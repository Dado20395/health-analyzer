# 🩸 Health Analyzer — App AI per la lettura delle analisi del sangue

> **Case study** di un progetto personale. Il codice è privato: questo repository ne descrive **idea, architettura e funzionalità**.

**Tipo:** Progetto personale · **Ruolo:** sviluppo end-to-end
**Stack:** JavaScript · PWA · Service Worker · HTML/CSS · Integrazione LLM (Claude) · Dati locali

> ⚠️ Non è un dispositivo medico: non fornisce diagnosi, indica solo se un valore è dentro o fuori dall'intervallo di riferimento. Per qualsiasi valutazione, rivolgersi al proprio medico.

---

## L'idea

Leggere i referti delle analisi del sangue (PDF o foto), capire quali valori sono **dentro o fuori dal range** di riferimento, archiviarli e **seguirne l'andamento nel tempo** — direttamente dal telefono, in modo privato.

## Architettura a "due cervelli"

Il cuore del progetto è la divisione dei compiti tra AI e codice:

- **L'AI (Claude)** fa la parte intelligente ma incerta: legge il documento ed estrae i valori, e scrive i commenti educativi. Un modello più capace legge i referti, uno più economico scrive i commenti — con un contatore del costo reale di ogni analisi.
- **Il codice** fa la parte semplice ma certa: confronto dentro/fuori range, classificazione, calcoli, salvataggio.

Questa separazione tiene il sistema affidabile (i numeri non li "inventa" l'AI) e trasparente sui costi.

## Cosa fa

- Legge referti in **PDF o foto** ed estrae nome, valore, unità e range
- Valuta i valori (nel range / sotto / sopra) e classifica anche i risultati **non numerici** (es. "nitriti presenti")
- **Stato attuale** a colpo d'occhio + **storia nel tempo** con variazioni e andamenti
- **Indici derivati** (NLR, eGFR, BUN/Creatinina…) con formule verificate, stato e fonti
- Commenti educativi automatici, glossario con fonti, profili multipli, temi chiaro/scuro
- **Costo trasparente**: ogni analisi mostra quanto è costata (token reali)

## Tecnologia

- **Progressive Web App** mobile-first: installabile e funzionante anche **offline** grazie al **service worker**
- **JavaScript · HTML/CSS** per l'interfaccia e la logica
- **Integrazione LLM (Claude)** per estrazione e commenti
- **Archiviazione locale** dei dati storici

## Privacy by design

I dati personali e la chiave API restano **solo sul dispositivo** e sono esclusi dal versionamento. I referti caricati non vengono conservati: si salvano solo i valori estratti. Nulla va online.

---

*Progetto personale. Codice privato; demo disponibile su richiesta.*
