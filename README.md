# 🎯 Test d'aula — quiz interattivo con feedback immediato

> **Quiz individuale a risposta multipla** per verificare l'apprendimento in aula (o in autonomia), con stile ispirato a Kahoot: bottoni colorati ▲◆●, spiegazione immediata dopo ogni risposta ed esito finale con progressione per argomento.
> Un unico file HTML, **zero installazioni, zero account, zero dati inviati in rete**.

🔗 **Demo online:** [*(Test d'aula IA generale)*](https://gigicogo.github.io/Test-aula-IA-nella-PA/)

---

## 📋 Cos'è

Un singolo file HTML che accompagna i partecipanti in un test di verifica **individuale e autosufficiente**: ogni risposta — giusta o sbagliata — è seguita da una breve spiegazione, così **il test è anche un ripasso**, e il docente non sente mai dire «questo non lo avevi spiegato».

La versione in dotazione contiene **12 domande sull'Intelligenza Artificiale in generale** (che cos'è l'IA, IA debole e forte, gerarchia IA → Machine Learning → Deep Learning, i tre tipi di apprendimento, Deep Learning e reti neurali, IA generativa e LLM): un set pronto all'uso, pensato per essere **sostituito facilmente** con qualunque altro programma di domande (vedi *Personalizzazione*).

**Perché è pensato per l'aula:**

- le domande coprono gli **argomenti di una lezione tipo**: concetti di base, metodo, applicazioni;
- i distrattori sono **plausibili e della stessa lunghezza della risposta corretta**: niente opzioni "riconoscibili a colpo d'occhio";
- la spiegazione dopo ogni risposta riprende **i concetti chiave**, non solo il verdetto;
- l'esito finale mostra **le barre per argomento** (verde / ambra / rosso), per capire *cosa* ripassare, non solo *quanto* si è preso.

## ✨ Come funziona

| Funzione | Dettaglio |
| --- | --- |
| **Avanzamento visibile** | Barra di progresso + pallini verde/rosso per ogni risposta data |
| **Feedback immediato** | L'opzione giusta diventa verde ✓, quella scelta male resta rossa ✕, con la spiegazione |
| **Esito finale** | Punteggio, messaggio di valutazione e **barre colorate per argomento** (verde ≥70%, ambra ≥40%, rosso <40%) |
| **Riepilogo completo** | Elenco domanda per domanda con la propria risposta e la spiegazione da usare come ripasso |
| **Ripresa** | Il test lasciato a metà si **riprende dove lo si era lasciato** (salvataggio locale) |
| **Stampa / PDF** | L'esito si stampa o si salva in PDF in versione pulita (fondo bianco) |
| **Accessibilità** | Nessun dato obbligatorio, rispetto dell'impostazione *riduci animazioni*, funzionamento offline |

## 🚀 Come si usa

1. Scarica il file del test (es. `index.html`) dal repo — o copialo da una chiavetta.
2. Aprilo con un doppio clic in qualunque browser moderno: **funziona anche offline**.
3. Invia il link (o il file) ai partecipanti: ognuno lo svolge **sul proprio dispositivo**.

Il **nome è facoltativo** e serve solo alla traccia personale stampabile; il test si svolge senza login, senza raccolta dati e senza classifiche. Alla fine, chi vuole stampa o salva il proprio esito.

## 🔒 Privacy e protezione dei dati

L'app è progettata per essere usata anche in contesti sensibili (formazione in enti pubblici, dati interni, aule con personale):

- **Nessun dato lascia il dispositivo.** Nessuna richiesta di rete, nessun server, nessun cookie, nessun tracciamento.
- **Nessun account richiesta.** Il quiz funziona anche offline, da file locale.
- **Salvataggio solo locale** (localStorage del browser) per riprendere il test; si azzera con «Ricomincia».
- **Nessun dato personale obbligatorio**: il nome è facoltativo, resta sul dispositivo e compare solo sull'esito stampato.

## 🛠️ Struttura del repository

```text
├── index.html    # il test completo (HTML + CSS + JS inline, zero dipendenze)
├── README.md     # questo file
└── LICENSE       # licenza (da scegliere)
```

Non serve build, npm, né alcuno strumento: solo un browser. Funziona su desktop, tablet e smartphone.

## 🌐 Pubblicazione gratuita (GitHub Pages)

1. Crea il repository e carica il file del test.
2. Vai su **Settings → Pages**.
3. Sotto *Build and deployment*, seleziona il branch (`main`) e la cartella (`/root`), poi **Save**.
4. Dopo qualche minuto il test sarà online su `https://<tuo-username>.github.io/<repo>/`.

**Regge il carico d'aula?** Sì: è un file statico servito via CDN, con un limite gratuito di ~100 GB/mese di banda — per una classe che carica pochi KB di HTML è praticamente illimitato. Netlify o Vercel (free) sono alternative valide: trascini il file e ottieni un link immediato.

## ✏️ Personalizzazione

Tutto il contenuto è in chiaro nel file HTML, nell'array **`QS`**: ogni domanda è un oggetto con

```js
{ t:"base",                 // argomento: chiave presente in TOPICS
  q:"Testo della domanda?", // la domanda
  o:["opzione 1",            // l'opzione con indice 0
     "opzione 2",            // indice 1
     "opzione 3"],          // indice 2
  c:1,                       // indice della risposta CORRETTA (parte da 0)
  w:"Spiegazione mostrata dopo la risposta, corretta o sbagliata che sia." }
```

Per adattare il test a un altro programma di formazione basta:

1. **Sostituire le domande in `QS`** mantenendo la struttura sopra;
2. **aggiornare `TOPICS`** con i propri raggruppamenti (etichetta + chiave `k` corrispondente ai campi `t`): ogni argomento produce una barra nell'esito finale;
3. cambiare il testo della **schermata iniziale** (titolo, sottotitolo, descrizione) nell'HTML;
4. volendo, aggiornare la chiave di salvataggio `var LS = "..."` quando si cambia radicalmente il set di domande, così i vecchi salvataggi non interferiscono.

**Consigli per domande che funzionano davvero:**

- **distrattori credibili e lunghi come la risposta giusta**: se le opzioni sbagliate sono più corte o "brutte", il quiz si risolve a colpo d'occhio;
- **variare la posizione della risposta corretta** tra le opzioni, senza schemi riconoscibili;
- **scrivere la spiegazione (`w`) pensando al ripasso**: è il testo che il partecipante rilegge nell'esito finale.

Il layout è pronto per **3 opzioni**; per una quarta, aggiungere in CSS la regola `.opts .opt:nth-of-type(4){background:...}` e l'eventuale nuova forma.

## 📐 Come è costruito

- HTML + CSS + JavaScript **inline in un solo file**, nessuna dipendenza esterna (nessun CDN, nessun font remoto);
- stato del test in `localStorage`, con ripresa automatica e azzeramento;
- resa visiva ispirata a Kahoot (palette viola, quattro colori istituzionali del quiz) ma **senza account, timer competitivi né classifiche**: pensata per la verifica individuale, non per il gioco a squadre;
- supporto a stampa, `prefers-reduced-motion` e schermi piccoli.

## 📜 Licenza e crediti

*(Da definire: scegli una licenza open — es. MIT o CC BY 4.0 — e aggiungi qui il credito che preferisci.)*

Creato come artefatto didattico riutilizzabile: siete liberi di adattarlo al vostro corso, sostituire le domande e ripubblicarlo.
