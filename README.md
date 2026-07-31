# Bakery Partner Club — Firebase

Versione statica pronta da pubblicare su GitHub Pages. La grafica è invariata; categorie, partner e contenuti sono salvati in Cloud Firestore e arrivano in tempo reale a tutti i visitatori.

## Funzionamento

- Pagina pubblica: legge Firestore in tempo reale.
- Dashboard: `/#admin`.
- Accesso admin: Firebase Authentication con email e password.
- Scrittura in Firestore: autorizzata esclusivamente alla tua email tramite le regole incluse.
- Nessun `localStorage`, server Python o database locale.

## Ultima configurazione Firebase (necessaria una sola volta)

Firebase è un tuo account cloud: non posso creare progetto, utente o regole al posto tuo senza accesso. Non devi modificare il codice dell'app; devi solo configurare il progetto nella console Firebase.

1. Crea un progetto Firebase e registra una **Web App**.
2. Crea un database **Cloud Firestore**.
3. In **Authentication > Sign-in method**, abilita **Email/Password** e crea il tuo utente admin.
4. Copia la configurazione della Web App in `firebase-config.js` e inserisci la stessa email usata per l'utente admin in `BPC_ADMIN_EMAIL`.
5. In **Firestore Database > Rules**, pubblica il contenuto di `firestore.rules`, sostituendo `INSERISCI_LA_TUA_EMAIL` con la stessa email.
6. In **Authentication > Settings > Authorized domains**, aggiungi il dominio GitHub Pages sul quale pubblicherai il sito, se non è già autorizzato.
7. Carica **tutti i file di questa cartella** in un repository GitHub e attiva GitHub Pages dalla cartella principale del branch scelto.

Il file `firebase-config.js` contiene dati pubblici di collegamento, non password. La protezione effettiva è data dall'utente Firebase Authentication e dalle regole Firestore.
