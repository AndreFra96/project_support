# Progetto RCA Support

RCA Support è un progetto nato per strutturare il servizio di assistenza cliente della società RCA SRL, il progetto prevede lo sviluppo di diverse componenti integrate fra loro, in particolare:

 - Applicazione cliente
 - Applicazione backend
 - Applicazione per la gestione delle notifiche push
 
## Applicazione cliente

L'applicazione cliente è un software multipiattaforma (iOS, Android, Web) dedicato alle aziende che acquistano prodotti di qualsiasi genere forniti da RCA.

**Accesso all'app**

L'accesso all'app prevede l'utilizzo di credenziali univoche per società, le credenziali  di accesso si compongono dalla partita iva della società e da una password che inizialmente è il codice cliente interno ed è possibile modificare in seguito.

L'accesso all'app viene mantenuto anche in seguito alla chiusura completa dell'applicazione tramite un sistema di gestione delle sessioni esterno al dispositivo.

Ogni accesso come nuova società viene salvato in una cache per proporre al cliente l'accesso diretto tramite bottone per tutte le società con le quali ha effettuato l'accesso.

**Gestione utenti**

All'interno dell'app nella sezione amministrazione esiste la possibilità per il cliente di creare diversi utenti, gli utenti sono di due tipi: utenti generici e utenti legati ad un locale.

Se non è stato configurato alcun utente l'accesso alle funzionalità dell'app è diretto dopo l'accesso all'app, se invece è presente almeno un utente in seguito all'accesso all'app è necessario effettuare l'accesso come utente per accedere alle funzionalità protette.

*utenti generici:*
Gli utenti generici possono effettuare l'accesso in tutte le istanze dell'app connesse con la società relativa all'utente, indipendentemente dal locale selezionato. 

*utenti legati ad un locale:*
Gli utenti generici possono effettuare l'accesso solo nelle istanze dell'app connesse con la società relativa all'utente, nella quale il locale selezionato corrisponde con il locale di competenza dell'utente.

**Amministrazione**

L'utente unico iniziale o gli utenti indicati come amministratori hanno accesso alla sezione amministrazione dell'app, la sezione amministrazione permette di:
- modificare le credenziali di accesso all'app
- gestire gli utenti

**Chat**

La chat è parte essenziale dell'applicazione cliente e canale principale di comunicazione fra cliente e RCA SRL, semplicemente scrivendo un messaggio in chat viene avviata una sessione di conversazione fra dispositivo e applicazione backend, l'inizio di una conversazione e unidirezionale da parte del cliente.

Funzionalità della chat:
- Invio di messaggi di testo
- Invio di immagini

**Contratto**

La sezione contratto contiene tutte le informazioni riguardo ai servizi attivi, suddivisi per tipologia di servizio (annuale, mensile, biennale, 31/12, prestiti)

**News**

La sezione news contiene informazioni e notizie riguardo i prodotti venduti da RCA, questa sezione non prevede l'accesso dell'utente ed è quindi di libera visualizzazione dopo aver effettuato l'accesso all'app.

Le news fornite in questa sezione sono di due tipi: 

*news generiche:*
Notizie dirette a tutte le istanze dell'app, qualunque sia il cliente e il locale selezionato. 

*news personalizzate:*
Notizie selezionate in base al profilo del locale connesso, permette di fornire informazioni comuni a tutti i locali classificati nello stesso profilo. 


## Applicazione backend

l'applicazione backend è un software multipiattaforma (iOS, Android, Web) dedicato al team di assistenza di RCA.

**Accesso all'app**

L'accesso all'applicazione backend prevede l'utilizzo di email e password come credenziali di accesso (generate manualmente su richiesta).

L'email di accesso deve corrispondere alla email utilizzata per accedere a t-order poichè grazie ad essa vengono estratte le informazioni sull'utente attualmente connesso.

**Chat personali**

Questa sezione contiene la lista di tutte le chat attualmente attive dell'utente connesso, selezionando una chat è possibile aprire la chatroom e comunicare con l'applicazione cliente selezionata.

**Chat generale**

Questa sezione contiene la lista di tutte le chat non assegnate o assegnate ad altri utenti rispetto a quello attualmento connesso, selezionando una chat è possibile aprire la chatroom e comunicare con l'applicazione cliente selezionata.

**Chatroom**

La chatroom è accessibile selezionando una conversazione.

Funzionalita:
- Invio di messaggi di testo
- Invio di immagini
- Informazioni sul cliente: all'interno della chatroom è disponibile una sezione con le informazioni sul cliente che ha avviato la chat e informazioni sul locale attualmente attivo nell'applicazione cliente

**News**

La sezione news permette di gestire la parte di notizie dell'applicazione cliente, all'interno di questa sezione è possibile:
- creare una nuova notizia
- modificare una notizia esistente
- cancellare una notizia
- assegnare un profilo ad una notizia
- modificare l'ordine delle notizie


## Applicazione per la gestione delle notifiche push

L'applicazione per la gestione delle notifiche push è una Web App che permette di visualizzare i dispositivi connessi all'applicazione cliente e inviare notifiche mirate ad un dispositivo o gruppo di dispositivi.

Come funzionano le notifiche push?
Ogni dispositivo connesso all'applicazione cliente possiede un token (codice identificativo) univoco, il servizio Firebase Cloud Messaging permette di inviare una notifica push ad un dispositivo indirizzando direttamente la notifica grazie al token del dispositivo. 

Ogni dispositivo, nel momento in cui effettua la connessione all'applicazione invia il token del dispositivo ad un server che salva il token del dispositivo e per ogni token viene salvato anche il cliente e il locale attualmente connesso, le modifiche al cliente o al locale comportano una nuova richiesta al server e un update dei dati connessi al token. 

Grazie a questo sistema possiamo collegare ogni token al cliente e locale attualmente attivo, e quindi a tutte le informazioni relative al cliente e al locale.

**Lista dispositivi**

In questa sezione è disponibile la lista di tutti i token salvati nel server con informazioni relative al locale e cliente connesso, le operazioni disponibili in questa sezione sono:
- ricerca avanzata fra tutti i dispositivi
- invio di un messaggio ad un singolo token
- invio di messaggi a molteplici token

**Analisi**

In questa sezione è possibile eseguire delle query di ricerca dei dispositivi connessi, una query di ricerca ha l'obiettivo di classificare una parte di dispositivi con alcune caratteristiche in comune. 

Le query di ricerca possono essere salvate dando vita a dei gruppi di dispositivi.

**Gruppi**

In questa sezione sono disponibili tutti i gruppi creati, ogni gruppo è caratterizzato da un titolo, una descrizione e una query.

Selezionando un gruppo è possibile inviare una notifica push a tutti i dispositivi che rientrano nella query di ricerca del gruppo.

Ogni gruppo ha un insieme di keywords che corrispondono ai campi estratti dalla query, nella creazione della notifica è possibile utilizzare queste keywords che verranno sostituite in fase di invio con l'informazione specifica del token, l'unica keyword sempre necessaria è token. 

E' possibile combinare più gruppi se hanno tutte le keywords in comune.





