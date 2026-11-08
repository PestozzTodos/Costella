# ✨ Costella

**Il social dove i pensieri sono stelle.**

Costella è un social network diverso dagli altri: niente feed, niente follower, niente like. Ogni post è una stella in un cielo condiviso che si esplora trascinandolo con il dito.

## Come funziona

- **Accendi una stella.** Scrivi un pensiero (massimo 140 caratteri) e scegli un umore: Calore, Calma, Amore, Mistero o Gioia. Il colore della stella dipende dall'umore.
- **Le stelle si spengono.** Ogni stella brilla circa 36 ore, poi svanisce. Nessuno accumula popolarità.
- **Rispondere significa collegare.** Quando rispondi a una stella ne accendi una nuova, unita alla prima da una linea. La stella a cui hai risposto si riaccende: i pensieri restano vivi finché qualcuno ci parla.
- **Nascono le costellazioni.** I gruppi di stelle collegate formano una costellazione. Nella scheda *Costellazioni* vedi chi parla con chi.
- **Nessun account.** Ogni persona riceve un nome casuale (tipo `@viandante-27`) e un codice segreto salvato nel proprio browser. Serve solo a riconoscere le proprie stelle ed eliminarle. Il sito ricorda le stelle, non le persone.

## Struttura del progetto

| File | A cosa serve |
| --- | --- |
| `index.html` | L'intero sito: grafica, cielo, interazioni. Un unico file, nessuna installazione. |
| `Code.gs` | Lo script di Google Apps Script che fa da archivio, collegato a un Google Sheet. |

Il sito è ospitato su **GitHub Pages**. Le stelle sono salvate in un **Google Sheet** a cui il sito accede tramite un'app web di **Google Apps Script**.

## Come metterlo online (da zero)

### 1. L'archivio su Google Sheet

1. Crea un nuovo foglio su Google Sheets, con un account Google dedicato a Costella.
2. Apri *Estensioni → Apps Script*, cancella il contenuto e incolla `Code.gs`. Salva.
3. Premi *Esegui il deployment → Nuovo deployment* e scegli il tipo **Applicazione web**.
4. Imposta *Esegui come: Io* e *Chi ha accesso: Chiunque*.
5. Autorizza i permessi richiesti e copia l'**URL dell'app web** (finisce con `/exec`).

### 2. Il sito su GitHub Pages

1. In `index.html`, cerca la riga `const API="..."` e sostituisci l'indirizzo con il tuo URL.
2. Crea un repository pubblico e carica `index.html` (il nome deve essere esattamente quello).
3. Vai in *Settings → Pages*, scegli il ramo `main` e la cartella `/ (root)`, poi salva.
4. Dopo un paio di minuti il sito è online all'indirizzo `https://tuonome.github.io/nome-repository`.

## Sicurezza e limiti

- Lo script accetta solo testi fino a 140 caratteri e al massimo **6 stelle ogni 10 minuti** per persona, per evitare che il foglio si riempia di spam.
- Le stelle più vecchie di 7 giorni vengono cancellate automaticamente.
- Il testo viene sempre mostrato come testo semplice, non come codice, quindi non può eseguire script.
- Il cielo si aggiorna **ogni 10 secondi circa**, non in tempo reale.
- Google Apps Script ha dei limiti giornalieri di richieste: va benissimo per un prototipo con poche persone, ma non regge un traffico molto alto.
- Senza account, chiunque può scrivere qualsiasi cosa. Non c'è ancora un sistema di segnalazione o moderazione.
- Chi cancella i dati del browser perde il codice segreto e non può più eliminare le proprie vecchie stelle, che restano nel cielo finché si spengono da sole.
- **Non condividere mai** il link di modifica del foglio o dello script: l'URL dell'app web, invece, è pubblico per natura e va bene così.

## Se modifichi `Code.gs`

Dopo ogni modifica devi creare una **nuova versione** del deployment (*Esegui il deployment → Gestisci deployment → modifica → Nuova versione*). Altrimenti il sito continua a usare il codice vecchio.

## Idee per il futuro

- Moderazione e segnalazioni.
- Aggiornamento in tempo reale con un database vero (per esempio Supabase).
- Una stella cadente quando una costellazione si spegne.
- Una schermata di benvenuto che spiega il concetto in tre secondi.

---

Fatto da Pestozz Todos con l'aiuto di Claude. ✨
