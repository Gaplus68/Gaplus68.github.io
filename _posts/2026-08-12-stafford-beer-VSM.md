---
title: "Le briglie di Stafford Beer"
date: 2026-08-12 10:00:00 +0200
categories: [AI, Sistemi]
tags: [Stafford Beer, cibernetica, VSM, agentic AI, multi-agent]
description: "Dalla cibernetica una 'vecchia' risposta ad una domanda attuale: cosa serve davvero perché un sistema di agenti resti vitale?"
image:
  path: /assets/img/prvw/VSM_1200x630.png
---

Un gruppo di agenti AI può avere accesso ai modelli migliori, a una quantità spropositata di tool e a tutta la memoria che siamo disposti a pagare. Può pianificare, scrivere codice, interrogare database e discutere con sé stesso per centinaia di cicli.

E può comunque fallire per una ragione molto banale: è organizzato male.

Non manca intelligenza ai singoli componenti. Manca qualcosa che impedisca loro di contraddirsi, che assegni le risorse, che controlli se il lavoro dichiarato sia stato realmente eseguito, che osservi ciò che cambia all'esterno e che ricordi a tutti quale fosse lo scopo iniziale. In breve, non manca un altro agente. Manca un sistema.

Nel 1972 il ricercatore britannico Stafford Beer pubblicò *Brain of the Firm*. Il suo Viable System Model (VSM, Modello del Sistema Vitale) cerca di descrivere le funzioni e i canali di comunicazione necessari perché un'organizzazione possa conservare la propria identità e adattarsi a un ambiente mutevole.

Cinquant'anni dopo sembra quasi una scorciatoia per progettare sistemi multi-agente migliori.

In questo articolo presenterò la metodologia di Beer e approfondirò la sua applicazione ai sistemi multi-agente, gettando le basi per un percorso di ricerca che includerà esperimenti concreti, con l'obiettivo di costruire le briglie ("harness") con il modello VSM ad una piccola implementazione multi-agente.

## Prima puntualizzazione: non è un teorema magico

La tentazione è raccontarla così: ogni sistema capace di sopravvivere possiede esattamente cinque funzioni; ne togli una e la patologia è inevitabile. È una formulazione efficace. Forse troppo.

Beer e molti autori successivi presentano il VSM come un insieme di condizioni necessarie per la sopravvivenza organizzativa, anche se alcuni interpreti ne hanno talvolta enfatizzato la sufficienza in modo eccessivo. Non significa però che ci troviamo davanti a un teorema dimostrato nel senso matematico del termine, né che mezzo secolo di applicazioni abbia trasformato il modello in una legge naturale. Il VSM è stato usato nell'industria, nelle cooperative, nelle amministrazioni pubbliche e, nel caso più famoso, nel progetto Cybersyn in Cile sotto Salvador Allende. La letteratura riporta molte esperienze pratiche; riporta anche la necessità di raccogliere più evidenze sulle condizioni di successo e di fallimento.

Non è una debolezza da nascondere. È il modo corretto di usare il modello.

Il VSM non certifica che un'organizzazione sopravvivrà. Offre una mappa con cui diagnosticare perché rischia di non farlo. E le mappe più utili non sono quelle che riproducono ogni sasso: sono quelle che mostrano i confini che altrimenti non vedremmo.

## Il punto non sono cinque scatole

Di solito il VSM viene riassunto disegnando cinque blocchi numerati. Il rischio è leggerlo come un organigramma: cinque uffici, cinque microservizi o, nella traduzione più immediata (e attuale), cinque agenti AI con prompt diversi.

Ma il punto non sono le scatole. Sono i canali.

Un sistema piatto composto da cinque unità può richiedere fino a venti relazioni dirette se ciascuna deve comunicare con tutte le altre. Il problema, però, non è soltanto il numero dei collegamenti. È che sullo stesso filo finiscono messaggi di natura diversa: una contesa su una risorsa, un controllo di qualità, una variazione del mercato e un'emergenza esistenziale diventano quattro notifiche nella stessa coda.

Quando tutto ha la stessa priorità, niente ha davvero priorità.

Beer parte da un'altra domanda: quali differenze deve saper riconoscere un'organizzazione per governare la propria complessità? Qui entra in gioco la legge della varietà necessaria di Ross Ashby, una delle fondamenta teoriche del VSM. La legge afferma che la varietà del controllore deve essere almeno pari alla varietà del sistema da controllare. In altre parole, un regolatore può gestire solo ciò per cui possiede un repertorio di risposte adeguato.

Non serve quindi far parlare tutti con tutti. Serve attenuare il rumore, amplificare i segnali importanti e portare ciascun problema nel canale che può trattarlo.

## Sistema 1 — Dove si realizza il lavoro

Il Sistema 1 comprende le unità operative che realizzano lo scopo primario dell'organizzazione. Una fabbrica produce, un ospedale cura, un team software consegna una applicazione. In un sistema agentico sono gli agenti — o i gruppi di agenti — che svolgono il lavoro per cui il sistema esiste: analizzano documenti, generano codice, eseguono test, rispondono agli utenti.

È la parte più visibile e quindi quella su cui concentriamo quasi tutta l'attenzione. Confrontiamo modelli, aumentiamo il contesto, aggiungiamo tool e miglioriamo i prompt. Stiamo rendendo più capace il Sistema 1.

Ma un insieme di ottimi esecutori non costituisce ancora un'organizzazione. Costituisce un insieme di ottimi esecutori.

Le unità operative devono conservare una certa autonomia: se ogni decisione risale al centro, la varietà dell'ambiente travolge il collo di bottiglia manageriale (ed esaurisce la capacità di contesto). Allo stesso tempo, l'autonomia non può diventare indipendenza assoluta. Il problema del VSM è precisamente questo equilibrio: lasciare libertà locale senza perdere coerenza globale.

## Sistema 2 — Impedire le oscillazioni

Il Sistema 2 viene tradotto abitualmente con “coordinamento”, ma la parola può trarre in inganno. Non è necessariamente un coordinatore e non coincide con un capo intermedio.

È più simile a un semaforo.

Standard condivisi, calendari, protocolli, schemi dei messaggi, lock sulle risorse, regole per il passaggio di consegne: sono tutti meccanismi che impediscono alle unità operative di oscillare e pestarsi i piedi. Se due agenti modificano lo stesso file, il Sistema 2 non decide quale progetto sia strategicamente più importante. Stabilisce chi può scrivere, quando e con quale procedura di riconciliazione.

Il coordinamento non deve essere intelligente a ogni costo. Spesso deve essere prevedibile.

Senza Sistema 2, due unità possono essere localmente corrette e globalmente incompatibili. Entrambe fanno bene il proprio lavoro. Insieme producono un incidente.

## Sistema 3 — Il dentro e l'adesso

Il Sistema 3 osserva l'insieme delle operazioni nel presente. Controlla risorse, capacità, vincoli e prestazioni; cerca duplicazioni e squilibri; decide se un'unità debba ricevere più budget, più tempo o meno lavoro.

In un'architettura multi-agente è il livello che vede i costi complessivi, distribuisce token e capacità di calcolo, limita la concorrenza, interrompe un ramo improduttivo e sposta il compito verso un modello più adatto. Il suo canale non produce soltanto raccomandazioni: deve poter allocare.

Qui emerge una prima tensione. Se il Sistema 3 è troppo debole, le risorse vengono ottimizzate localmente e sprecate globalmente. Se è troppo forte, ogni scelta diventa centralizzata e le unità operative perdono la varietà necessaria per rispondere in tempo.

L'ottimizzazione non consiste nel controllare tutto. Consiste nel controllare ciò che deve essere comune.

## Sistema 3* — Non fidarsi del riassunto

Il Sistema 3 riceve rapporti dalle unità operative. E i rapporti hanno un difetto: sono rappresentazioni prodotte dallo stesso sistema che dovrebbe essere valutato.

Gli esseri umani abbelliscono, omettono e razionalizzano. I modelli linguistici fanno qualcosa di ancora più insidioso: possono produrre una descrizione perfettamente plausibile di un lavoro mai eseguito. Il test è “passato”, il file è stato “aggiornato”, la fonte è stata “verificata”. La frase suona bene. L'artefatto non esiste.

Il canale 3* — si legge “tre stella” — serve a saltare occasionalmente la normale catena di reporting e osservare direttamente le operazioni. Non è un sesto sistema: è il canale di audit del Sistema 3.

Per un agente di coding significa aprire davvero il diff, eseguire i test e verificare l'output. Per un sistema RAG significa controllare che la risposta sia sostenuta dai documenti recuperati, non dal riassunto che il modello ne ha prodotto. Per un servizio significa interrogare il database, non chiedere al processo responsabile se il backup sia aggiornato.

La regola è semplice: non verificare la dichiarazione. Verificare l'artefatto.

E c'è un dettaglio importante. Se auditore e operatore usano lo stesso modello, lo stesso contesto e gli stessi criteri, possono condividere anche lo stesso errore. L'indipendenza del controllo non è una decorazione organizzativa. È parte del suo contenuto informativo.

## Sistema 4 — Il fuori e il domani

Mentre il Sistema 3 guarda dentro e adesso, il Sistema 4 guarda fuori e avanti.

Una dipendenza verrà dismessa? È cambiata una norma? Un concorrente ha già rilasciato la funzione che stiamo costruendo? È comparsa una nuova architettura capace di rendere obsoleto il nostro investimento? Il Sistema 4 raccoglie i segnali dell'ambiente, costruisce scenari e li porta dentro l'organizzazione.

In un sistema agentico potrebbe monitorare documentazione, vulnerabilità, prezzi, benchmark, requisiti normativi e mutamenti nelle fonti di dati. Non dovrebbe però sommergere le operazioni con ogni novità incontrata. Anche l'intelligence deve filtrare varietà: riconoscere ciò che cambia davvero il piano e lasciare scorrere il resto.

Senza Sistema 4, il sistema può diventare molto efficiente. Nel mondo di ieri.

Il passaggio più delicato è il confronto tra Sistema 3 e Sistema 4: capacità presente contro possibilità futura. Una strategia non nasce osservando soltanto l'ambiente, né spremendo ancora un po' le risorse esistenti. Nasce dal conflitto regolato tra le due prospettive.

## Sistema 5 — Decidere che cosa conta

Il Sistema 5 custodisce identità, politica e scopo del sistema. Stabilisce il quadro entro cui gli altri livelli possono decidere.

Quando occorre scegliere tra velocità e accuratezza, tra risparmio e ridondanza, tra autonomia dell'agente e controllo umano, non esiste una risposta tecnicamente neutra. La scelta dipende da ciò che il sistema dichiara di essere e, soprattutto, da ciò che non è disposto a sacrificare.

Per questo il Sistema 5 non può ridursi a una frase motivazionale inserita nel prompt di sistema. Deve tradursi in vincoli, priorità e criteri di escalation. In un servizio sanitario l'affidabilità può prevalere sulla velocità; in un prototipo esplorativo può valere il contrario. Entrambe le scelte sono legittime. Farle senza dichiararle produce invece ordine locale e disordine globale.

Il Sistema 5 bilancia anche il rapporto tra 3 e 4. Troppo Sistema 3 e l'organizzazione perfeziona ciò che già sa fare fino a renderlo irrilevante. Troppo Sistema 4 e accumula scenari, esperimenti e roadmap senza consegnare nulla.

L'identità non serve a descrivere il sistema. Serve a chiudere decisioni che i soli dati non possono chiudere.

## Il canale algedonico — quando la gerarchia è troppo lenta

*Algedonico* deriva dalle parole greche per dolore e piacere. Nel VSM indica un segnale eccezionale capace di attraversare i livelli ricorsivi quando una soglia critica viene superata. Più precisamente, è un canale dedicato che trasporta informazioni continue sullo stato di salute delle unità operative — non solo segnali di emergenza, ma anche dati che indicano quando le condizioni si stanno deteriorando, prima che si verifichi un fallimento.

È l'allarme antincendio, non la chat aziendale.

Una violazione grave della sicurezza, la perdita di integrità dei dati o un comportamento incompatibile con lo scopo del sistema non devono aspettare il normale ciclo di coordinamento, ottimizzazione e analisi strategica. Devono raggiungere il livello in grado di proteggere l'identità e la sopravvivenza dell'insieme.

Ma se tutto viene dichiarato algedonico, il canale collassa. Un allarme che suona ogni cinque minuti smette di segnalare un'emergenza e diventa rumore ambientale. Anche qui il problema non è aggiungere una notifica: è definire soglie credibili, destinatari responsabili e conseguenze verificabili.

## La parte che si dimentica: il VSM è ricorsivo

Fin qui potremmo ancora commettere l'errore di disegnare cinque grandi agenti in cima al sistema: uno operativo, uno coordinatore, uno manager, uno stratega e uno custode dei valori.

Beer dice qualcosa di più scomodo. Un sistema vitale è ricorsivo: se guardiamo all'interno di una sua unità operativa, possiamo trovare una struttura analoga, purché quell'unità abbia un sufficiente grado di autonomia da essere considerata un sistema vitale a sé stante. Non tutte le unità operative sono sistemi vitali; alcune sono semplici componenti che non necessitano della piena struttura VSM. Un team può essere un Sistema 1 dell'azienda e, guardato più da vicino, contenere le proprie operazioni, il proprio coordinamento, il proprio controllo e la propria capacità di adattamento.

La prima decisione progettuale non è quindi “quale agente interpreta il Sistema 4?”. È “qual è il sistema che stiamo osservando?”. Beer lo chiama *system in focus*.

Se sbagliamo il livello di osservazione, replichiamo burocrazia a ogni task oppure lasciamo interi livelli senza governo. Non ogni chiamata a un tool ha bisogno di cinque sottosistemi. Un gruppo di agenti dotato di autonomia, memoria, risorse e responsabilità persistenti probabilmente sì.

La ricorsività è ciò che permette al modello di scalare. È anche ciò che impedisce di trasformarlo in un diagramma statico.

## Dall'organigramma alla topologia

La traduzione del VSM in architettura agentica può essere riassunta così:

| Funzione | In un sistema multi-agente | Patologia quando manca |
|---|---|---|
| Sistema 1 | Agenti che eseguono il lavoro primario | Molta governance, nessun risultato |
| Sistema 2 | Protocolli, lock, schemi e regole di coordinamento | Conflitti, oscillazioni, lavoro duplicato |
| Sistema 3 | Budget, capacità, priorità e controllo operativo | Ottimi locali, spreco globale |
| Sistema 3* | Audit diretto di output, log e artefatti | Autovalutazioni plausibili ma false |
| Sistema 4 | Osservazione dell'ambiente e scenari futuri | Ottimizzazione per condizioni superate |
| Sistema 5 | Scopo, identità, vincoli e criteri finali | Decisioni coerenti localmente, incompatibili insieme |
| Canale algedonico | Escalation per soglie critiche | Emergenze intrappolate nella normale gerarchia |

La tabella è utile, purché non venga scambiata per un file di configurazione. Il VSM non specifica modelli, code, database o protocolli. Non dice se una funzione debba essere centralizzata, distribuita o affidata a un essere umano. Non risolve automaticamente sicurezza, incentivi, latenza e qualità delle informazioni.

Soprattutto, un sistema di agenti non è un organismo soltanto perché lo rappresentiamo con una metafora biologica. La vitalità è una lente progettuale, non la prova che il software possieda bisogni, intenzioni o un'identità propria.

## Qualche commento

La maggior parte dei framework multi-agente parte dal Sistema 1. Aggiunge ruoli, tool, memoria e un router; poi chiama “orchestrazione” tutto ciò che rimane. Il VSM suggerisce che stiamo comprimendo funzioni diverse dentro una sola parola.

Coordinare non è allocare. Allocare non è verificare. Verificare non è osservare il futuro. E nessuna di queste attività decide, da sola, che cosa debba contare.

La distinzione è importante perché i modelli linguistici tendono a rendere simili superfici che sotto sono diverse. Un report, un piano, una verifica e una policy possono essere tutti blocchi di testo ben formati. Ma producono effetti organizzativi differenti e richiedono autorità, fonti e canali differenti.

Il secondo punto riguarda l'audit. Nei sistemi agentici il Sistema 3* potrebbe diventare più importante del Sistema 3: generare un risultato costa sempre meno, stabilire se corrisponde al mondo continua a costare. Più aumentiamo l'autonomia, più dobbiamo spostare il controllo dalle intenzioni dichiarate agli artefatti osservabili.

Il terzo punto è politico, nel senso più concreto del termine. Il Sistema 5 decide i limiti entro cui il sistema può ottimizzare. Se lo deleghiamo interamente alla macchina, non eliminiamo il giudizio umano: lo nascondiamo nei dati, nei prompt, nelle metriche e nei permessi scelti da qualcuno. L'identità resta. Diventa soltanto meno visibile.

## Cosa non è ancora chiaro

Il VSM offre un vocabolario potente per leggere un sistema multi-agente, ma siamo ancora lontani da una teoria operativa completa.

Non sappiamo quale livello di autonomia renda un gruppo di agenti un vero sistema in focus anziché una semplice pipeline. Non sappiamo quanta indipendenza serva a un audit basato su modelli simili. Non abbiamo metriche consolidate per misurare la varietà che ciascun canale attenua o amplifica. E non è affatto scontato che una struttura progettata per organizzazioni umane possa essere trasferita senza residui a processi software che possono essere clonati, sospesi e cancellati.

A ciò si aggiungono alcune critiche di fondo al VSM che diventano ancora più rilevanti in questo contesto: il modello è essenzialmente statico e strutturale, e dice poco sui processi di cambiamento o apprendimento che sono invece centrali nei sistemi AI. Inoltre, il VSM presuppone che le funzioni possano essere progettate e allocate dall'alto, mentre in sistemi complessi e adattivi queste funzioni potrebbero emergere in modo non deterministico. Infine, la dimensione umana — motivazione, identità culturale, bisogni psicologici — per cui Beer progettava le organizzazioni non ha un equivalente diretto negli agenti artificiali, e questo rende alcune analogie più suggestive che operative.

Sono obiezioni sufficienti per evitare la parola “teorema”. Non per smettere di usare la mappa.

## La domanda che resta

Per qualche anno la domanda sui sistemi agentici è stata: quanti agenti servono e quale modello assegniamo a ciascuno?

Forse la domanda sta cambiando.

Come fa il sistema a sapere che le sue unità non si stanno ostacolando? Chi può riallocare le risorse? Chi controlla gli artefatti invece di credere ai report? Chi osserva il mondo esterno? Chi stabilisce che cosa non deve essere sacrificato? E quale segnale può attraversare tutto il sistema quando la normale gerarchia è troppo lenta?

Il VSM di Stafford Beer è un metodo: può aiutarci a comprendere perché un sistema multi-agente non performa meglio pur avendo componenti sempre più intelligenti. Può aiutarci ad imbrigliare il sistema.

Il problema non è più costruire l'agente più capace. È progettare i canali che permettano all'insieme di restare coerente mentre cambia.


## Riferimenti

- Stafford Beer, [*Brain of the Firm*](https://books.google.com/books/about/Brain_of_the_Firm.html?id=gm55QAAACAAJ), Allen Lane, 1972.
- Stafford Beer, [*Diagnosing the System for Organizations*](https://archive.org/details/diagnosingsystem00beer), Wiley, 1985.
- Metaphorum, [*The VSM in 1000 words*](https://metaphorum.org/staffords-work/viable-system-model).
- Angela Espinosa, Jon Walker e Andrea Martinez-Lozada, [*The Viable System Model: An Introduction to Theory and Practice*](https://doi.org/10.54120/jost.000004), *Journal of Systems Thinking*, 2023.
- Martin Pfiffner, [*Five experiences with the viable system model*](https://doi.org/10.1108/03684921011081196), *Kybernetes*, 2010.
- Philipp Enderle (2026a), [*Your AI Agents Need an Org Chart — But Not the Kind You Think*](https://dev.to/philippenderle/your-ai-agents-need-an-org-chart-but-not-the-kind-you-think-2fg7), DEV Community [Part I].
- Philipp Enderle (2026b), [*Your Multi-Agent Framework Handles Operations. What About the Other Five?*](https://dev.to/philippenderle/your-multi-agent-framework-handles-operations-what-about-the-other-five-3hlj), DEV Community [Part II].
