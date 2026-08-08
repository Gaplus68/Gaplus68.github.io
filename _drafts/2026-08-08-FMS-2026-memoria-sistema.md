---
layout: post
title: "FMS 2026: la memoria non è più un livello, è un sistema"
date: 2026-08-08
categories: [Hardware, Memory]
tags: [FMS 2026, AI, CXL, KV cache, HBM, HBF, NAND, NVMe, PIM]
description: "Dalla crisi della KV cache al CXL memory pooling: cronaca dalla fine dello storage passivo, e perché il nostro codice deve iniziare a pensare in termini di continuum."
# image:
#   path: /assets/img/prvw/FMS2026_xxx.png
---

Santa Clara, 6 agosto. Da qualche parte, nel Convention Center, un acceleratore da decine di migliaia di dollari sta aspettando i dati. Non è un'immagine retorica: è il problema attorno a cui l'intera industria della memoria e dello storage ha scoperto di aver lavorato per anni nel modo sbagliato. L'agenda del Future of Memory and Storage 2026 — tre giorni, oltre duecentocinquanta interventi tecnici — non parla di IOPS, non parla di layer di NAND, non parla di fattori di forma. Parla di un unico, ingombrante protagonista: l'inferenza AI. E del suo unico nemico: il movimento dei dati.

Non faremo la lista dei trend. Le liste non spiegano nulla. Quello che proveremo a fare è ricostruire il **sistema** che emerge quando si leggono gli abstract uno dopo l'altro: perché a FMS 2026 la memoria ha smesso di essere un livello della piramide, ed è diventata il tessuto connettivo di tutto il resto.

## La cronaca: tre giorni che azzerano il confine

### Il leitmotiv: la KV cache come workload di riferimento

Se fino a ieri la key-value cache era un dettaglio interno di vLLM — quel buffer dove un modello linguistico parcheggia le chiavi e i valori dell'attenzione per non ricalcolarli a ogni token — a Santa Clara è diventata il **working set ufficiale dell'infrastruttura**. La meccanica è spietata, e la descrive bene l'abstract di Netflix: ogni token in ingresso genera voci di cache nella memoria ad alta banda (HBM, High Bandwidth Memory) della GPU; gli agenti AI di oggi spingono regolarmente i contesti oltre i 100.000 token, consumando gigabyte di cache *per singola richiesta*. La cache cresce con la lunghezza del contesto e con il numero di sessioni concorrenti, la HBM satura in millisecondi, e il time to first token — il tempo che l'utente aspetta prima di vedere la prima parola della risposta — esplode. Non è un problema di qualità del modello. È un problema di dove mettere le cose.

### Le voci dal palco

Le risposte, ascoltate in tre giorni, arrivano da direzioni opposte — ed è questa la notizia.

Netflix, che hardware non vende, ha presentato **Headroom**: un framework di compressione del contesto che riduce dell'80% la memoria occupata dalla KV cache prima che questa tocchi il silicio. La frase chiave del loro abstract vale un panel intero: le soluzioni hardware — più HBM, offload su flash, memoria attaccata via Compute Express Link (CXL) — *affrontano il sintomo; la compressione affronta la causa*. Quando un'azienda di streaming deve inventarsi ingegneria della memoria per far funzionare i propri servizi, il confine tra chi produce infrastruttura e chi la usa si è già spostato.

Dalla parte opposta spingono i costruttori: Supermicro e Graid Technology con il tiering hardware della KV cache dalla HBM fino ai drive Non-Volatile Memory Express (NVMe); Micron con l'offload ottimizzato per l'inferenza; Samsung, SK hynix e Micron nelle keynote a ripetere la stessa formula — *memory-centric* — come se la si fosse passata di mano in mano. IBM, dal palco del computational storage, ha portato il **Cognitive File System**: un file system che prova a "capire" i dati senza aspettare che un umano scriva i metadati. Ne riparliamo tra poco, perché è la sessione che fa più male, nel senso buono.

E poi c'è la tensione che nessuno ha voluto risolvere. Il secondo giorno IBM ha messo in titolo un panel *"Near-line drives vs QLC… what about Near-line killer?"* — il flash a celle quad-level che punta dritto alla gola del disco meccanico. Il terzo giorno la provocazione si è ribaltata: la startup XCENA ha mostrato un modulo di memoria convergente DRAM-NAND attaccato via CXL per condividere la KV cache tra server. La domanda che girava nei corridoi non era più *"il CXL ucciderà l'SSD?"*, ma qualcosa di più scomodo: l'SSD resterà una scatola, o si scioglierà direttamente nel bus di memoria?

### Il dato che fotografa il cambiamento

*Conteggio nostro sugli abstract pubblicati in agenda (una sessione può coprire più temi):*

| Tema | Interventi |
|---|---|
| Inferenza LLM | 61 |
| CXL | 35 |
| KV cache | 28 |
| Pooling / disaggregazione | 25 |

Su circa 260 sessioni di contenuto, un quarto ruota attorno a una sola frase: *il contesto non ci sta più dove stava*.

## I cinque fronti: un framework, non una lista

Provate a immaginare il data center come un palazzo. A FMS 2026 non si è discusso di ristrutturare una stanza: si è discusso di rifare le fondamenta mentre il palazzo è abitato.

All'**attico** si sta larghi e si vede lontano: HBM e DRAM, la memoria più veloce e più vicina al calcolo. È anche il metro quadrato più costoso del mondo digitale, e la domanda che tutti i keynote hanno posto è brutale nella sua semplicità: quanto ci costa tenere il contesto *qui*? La risposta implicita dell'intera conferenza — troppo — è il motore di tutto ciò che segue.

Gli **ascensori** sono il CXL e i link tra acceleratori: non producono nulla, ma decidono chi sale, chi scende e a che velocità. Che Meta stia testando il memory pooling CXL in ambiente hyperscale, e che 35 interventi in agenda ruotino attorno a questo standard, dice che gli ascensori sono diventati l'infrastruttura critica del palazzo: se il trasporto è efficiente, non serve più che ogni stanza sia grande.

Il **magazzino** è dove il palazzo tiene la roba: gli SSD NVMe, le nuove unità flash pensate per l'inferenza, e soprattutto la High Bandwidth Flash (HBF) — flash impilato con un'interfaccia che assomiglia a quella della memoria, proposta come riempitivo del canyon tra HBM e NAND. La domanda aperta: è ancora un magazzino, o sta diventando un piano abitabile con indirizzo proprio? Quando un drive smette di essere "archivio" e diventa "memoria indirizzabile", la pianta del palazzo cambia.

La **fabbrica in-house** è il processing in-memory e near-memory (PIM e PNM): invece di spostare il prodotto grezzo al reparto lavorazione, lavorare sul posto. SK hynix ha mostrato un sistema PIM/PNM che disaggrega il calcolo dell'attenzione portandolo dentro la memoria; startup come SEMRON propongono celle CapRAM che si candidano a superare sia HBM che HBF. Perché muovere il dato, se il calcolo può trasferirsi?

E poi c'è **il direttore**, il livello che decide tutto senza possedere nulla: l'orchestrazione software. LMCache per il riuso della cache tra richieste, lo Storage Performance Development Kit (SPDK) per parlare ai drive senza passare dal kernel, Headroom per comprimere prima di allocare, il Cognitive File System per decidere cosa è rilevante prima ancora che qualcuno lo chieda. La domanda del direttore è quella che conta di più: chi stabilisce dove va ogni dato, e quando?

Il momento chiave, mettendo insieme i cinque livelli, è questo: **non c'è una tecnologia vincitrice**. C'è una competizione su chi sposta il confine tra calcolo e dato — verso la memoria, verso lo storage, o dentro il software che li coordina. Il palazzo non avrà un nuovo proprietario. Avrà nuovi confini interni.

## Il punto di vista dello sviluppatore

Qui smettiamo i panni del cronista. Perché tutto questo, fra diciotto mesi, arriva nel codice che scriviamo noi.

**Il nostro codice non sa più dove vivono i dati.** POSIX ci ha cresciuti dentro un'assunzione comoda: un disco lento, una RAM veloce, e la cache come affare dell'hardware. Quando tra il processore e il bit ci sono quattro o cinque livelli di velocità e persistenza — HBM, DRAM, memoria pooled via CXL, flash NVMe, magari HBF — quell'assunzione crolla. La località spaziale e temporale, quella che abbiamo studiato per la cache L1 e poi felicemente dimenticato, torna centrale: ma a livello di sistema intero, non di linea da 64 byte.

**Il software sta diventando il collo di bottiglia.** SPDK, LMCache, i runtime di tiering: fino a ieri erano ottimizzazioni per specialisti, roba da mettere in produzione quando il resto andava male. A Santa Clara li presentavano come layer dello stack applicativo, al pari del framework web. E Netflix con Headroom ha mandato il segnale più chiaro: la compressione del contesto è diventata responsabilità del servizio, non del sistema operativo. Se il tuo servizio non sa come viene spesa la memoria che occupa, qualcun altro deciderà per te — e ti manderà il conto.

**Il Cognitive File System pone una domanda scomoda.** Se i nuovi consumatori di dati sono agenti AI, il file system deve ancora essere organizzato per umani? Non è filosofia: è design di API. Quando un agente chiede *"tutti i documenti correlati a X"*, ha ancora senso obbligarlo a passare per path e directory — una mappa disegnata per la memoria umana, non per la sua? Chi scrive backend dovrebbe iniziare a farsela, questa domanda, prima che il filesystem la risponda al posto nostro.

**E il rischio è concreto.** L'astrazione ci ha salvato per trent'anni: read(), write(), e il sistema operativo a farsi carico del resto. Il tiering esplicito ci restituisce potenza — decidere quale dato merita l'attico e quale il magazzino — al prezzo di gestire politiche di migrazione nel codice applicativo. È potente. È anche pericoloso. Ogni astrazione che crolla porta con sé una generazione di bug che non abbiamo ancora imparato a riconoscere.

## Cosa non è ancora chiaro

Onestà prima di tutto: HBF, per ora, è una proposta architetturale più che un prodotto — il panel con Sandisk, SK hynix e Google DeepMind ne parlava come prospettiva, non come roadmap di consegna. Il CXL in produzione resta un cantiere: Meta lo sta testando in scala, ma il terzo giorno si discuteva apertamente di come validare i dispositivi "out of the box", sintomo che latenza variabile e affidabilità del firmware sono problemi ancora sul tavolo. E il super-ciclo della memoria 2026–2028 annunciato da TrendForce — conversione reale delle fab, o speculazione sui prezzi della prossima HBM? Nessuno, a Santa Clara, aveva la risposta.

FMS 2026 non ha annunciato vincitori. Ha annunciato che il gioco si sposta su un campo più grande.

## La domanda che resta

Per vent'anni la domanda dell'industria è stata "quanto è veloce questo drive?". A Santa Clara è diventata un'altra: con quale efficacia l'intero sistema — attico, ascensori, magazzino, fabbrica e direttore — mantiene gli acceleratori alimentati, riducendo costo, energia e movimento dei dati? È una domanda che non si esaurisce in un articolo, e nemmeno in una conferenza. Ma è la domanda giusta da porsi adesso, mentre il continuum tra memoria e storage smette di essere uno slogan e diventa il campo su cui si progetteranno i prossimi anni. Il resto, come sempre, si vedrà scrivendo codice.

---

*Nota metodologica: questa analisi si basa sull'agenda ufficiale FMS 2026 (Santa Clara, 4–6 agosto 2026) e sugli abstract pubblicati dagli organizzatori. I conteggi per tema derivano da classificazione multi-label su titoli e abstract; ogni affermazione su vendor e tecnologie è ancorata a sessioni specifiche dell'agenda. Gli organizzatori non pubblicheranno centralmente slide né registrazioni: i materiali dei singoli relatori, dove resi disponibili, verranno collegati in aggiornamento.*

## Riferimenti

- [Agenda ufficiale FMS 2026 (Terrapinn)](https://www.terrapinn.com/conference/future-memory-storage/agenda.stm)
- [OCP HBF Architecture Specification v0.7.0](https://www.opencompute.org/documents/ocp-hbf-architecture-specification-v0-7-0-final-pdf)

<!-- Suggerimento: cross-link interno al post HBF con la sintassi Chirpy:
{% raw %}{% post_url 2026-08-07-HBF-prime-impressioni %}{% endraw %}
da inserire dove si parla di HBF, dopo aver verificato il nome file reale in _posts/ -->
