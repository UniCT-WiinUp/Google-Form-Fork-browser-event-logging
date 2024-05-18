## Google-Form-Fork: Automatizza il Tuo Processo di Valutazione con Controllo Anti-Furbi

Google-Form-Fork è una piattaforma personalizzata basata su Google Forms, arricchita con l'integrazione degli eventi del browser per garantire un processo di valutazione affidabile e efficiente, con un occhio di riguardo per prevenire eventuali tentativi di frode da parte degli studenti.

### Caratteristiche Principali:

- **Controllo Anti-Furbi:** Grazie agli eventi del browser, Google-Form-Fork può rilevare e segnalare eventuali comportamenti sospetti degli studenti, garantendo un'esperienza di test equa e affidabile.

- **Automazione della Valutazione:** Non perdere più tempo a correggere manualmente i test. Google-Form-Fork ti permette di ottenere immediatamente i risultati dei tuoi candidati, indicando chi ha superato il test e chi no.

- **Esportazione dei Risultati:** Puoi esportare facilmente tutti gli esiti in formato PDF o creare un riepilogo delle domande da analizzare con il tuo software di calcolo preferito, rendendo la gestione dei risultati dei test ancora più efficiente.

### Gestione degli Eventi del Browser:

Il codice JavaScript integrato in Google-Form-Fork gestisce intelligentemente gli eventi del browser per garantire un ambiente di test sicuro. Quando uno studente tenta di uscire dalla modalità schermo intero durante il test, viene immediatamente segnalato, preservando l'integrità del processo di valutazione.


```javascript

<input type="hidden" id="fullscreenExit" name="fullscreen_exit" value="0">

$(document).ready(function() {
    var isQuizSubmitted = false; // Flag per controllare se il quiz è stato inviato

    // Funzione per attivare la modalità schermo intero
    function enterFullscreen() {
        var elem = document.documentElement;
        if (elem.requestFullscreen) {
            elem.requestFullscreen();
        } else if (elem.webkitRequestFullscreen) { /* Safari */
            elem.webkitRequestFullscreen();
        } else if (elem.msRequestFullscreen) { /* IE11 */
            elem.msRequestFullscreen();
        }
    }

    // Funzione per bloccare l'interazione con gli elementi della pagina
    function disablePageInteraction() {
        $('body').css('pointer-events', 'none');
    }

    // Funzione per riattivare l'interazione con gli elementi della pagina
    function enablePageInteraction() {
        $('body').css('pointer-events', '');
    }

    // Funzione per mostrare il messaggio di uscita da schermo intero
    function showFullscreenMessage() {
        $('#fullscreenMessage').fadeIn();
        setTimeout(function() {
            $('#fullscreenMessage').fadeOut();
        }, 9000);
    }

    // Gestore di eventi per il pulsante "Inizia Quiz"
    $('#startQuizBtn').click(function() {
        enterFullscreen(); // Attiva la modalità schermo intero
        $('#quizForm').show(); // Mostra il modulo del quiz dopo aver fatto clic sul pulsante
    });

    // Monitora il cambio di stato della modalità schermo intero
    document.addEventListener('fullscreenchange', function() {
        if (!document.fullscreenElement) { // Se l'utente esce dalla modalità schermo intero
            showFullscreenMessage(); // Mostra il messaggio di uscita da schermo intero
            $('#fullscreenExit').val("1"); // Imposta il valore del campo nascosto
        }
    });

    // Gestore di eventi per il submit del quiz
    $('#quizForm').submit(function() {
        isQuizSubmitted = true; // Imposta il flag per indicare che il quiz è stato inviato
        // Inserisci qui il codice per salvare il valore nel database
        // Rimuovi il commento e sostituisci 'URL_DEL_DATABASE' con l'URL del tuo script PHP per salvare nel database
        /*
        $.post('URL_DEL_DATABASE', { fullscreen_exit: $('#fullscreenExit').val() }, function(response) {
            console.log(response); // Puoi fare qualcosa con la risposta dal server
        });
        */
        return true; // Invia il modulo
    });
});
```
Questo codice assicura che quando uno studente tenta di uscire dalla modalità schermo intero durante il test, viene immediatamente segnalato, preservando l'integrità del processo di valutazione.

### Backend Python e Frontend HTML:
Google-Form-Fork è gestito da un backend Python per il processamento dei dati e un frontend HTML per l'interazione con gli utenti. Il backend si occupa di elaborare le risposte dei test e gestire il salvataggio dei dati nel database, mentre il frontend fornisce un'interfaccia intuitiva per la creazione e la gestione dei test.

## Demo:
# Puoi visualizzare una demo del sistema <a href="https://quiz.unict-forum.icu/" target="blank">Qui</a>

![Imgur](https://i.imgur.com/uLJJO2U.png)
# Editor
### Per entrare in editor clicca la matita in basso a destra e iniserisci come credenziali di accesso:
#### email: test@gmail.com
#### password: test

# Aggiornamento Google Forms Fork - Versione 1.0.1

Siamo entusiasti di annunciare il rilascio della versione 1.0.1 della nostra piattaforma Google Forms Fork! Questa versione include una serie di miglioramenti significativi per offrire una migliore esperienza utente e un'interfaccia più moderna.

## Miglioramenti in questa versione

### 1. Estetica e Template
- **Nuovo design moderno**: Abbiamo aggiornato il template per renderlo più accattivante e allineato con gli standard attuali di design.
- **Miglioramento della UI**: Sono stati fatti vari aggiustamenti per migliorare l'interfaccia utente e rendere la navigazione più intuitiva.

### 2. Linguaggio dell'algoritmo
- **Ottimizzazione del codice**: Il linguaggio dell'algoritmo è stato rivisitato e migliorato per garantire una maggiore efficienza e velocità di esecuzione.
- **Pulizia del codice**: Sono stati eliminati bug e ridondanze, rendendo il codice più pulito e facile da mantenere.

### 3. Posizionamento degli elementi
- **Riorganizzazione degli elementi**: Abbiamo cambiato alcune posizioni degli elementi sulla pagina per migliorare l'ergonomia e la facilità d'uso.
- **Nuova disposizione dei campi**: I campi del form sono stati riordinati per rendere la compilazione più semplice e logica.
