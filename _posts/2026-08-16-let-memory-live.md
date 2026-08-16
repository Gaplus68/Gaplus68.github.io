---
title: "Let the memory live again"
date: 2026-08-16 18:00:00 +0200
categories: [AI, Architetture]
tags: [Neuroscienze, Memoria, Epigenetica, Reti Neurali, Biologia]
description: "Viaggio verso nuovi modelli di memoria"
image:
  path: /assets/img/prvw/Cromatina_1200x630.png
  
---
> *Contenuto parzialmente modificato con IA* 
> Il testo di questo post è stato sottoposto a un trattamento parziale mediante IA, limitato alla correzione linguistica e ortografica. 
> Il contenuto, la struttura e la responsabilità editoriale del post restano dell'autore. _Art. 50 del Regolamento (UE) 2024/1689 (AI Act)_
{: .prompt-info }

Per più di settanta anni, grazie a D.O. Hebb, abbiamo rappresentato la memoria come una rete di cavi e nodi: un ricordo si forma quando i neuroni si attivano insieme e rafforzano le loro sinapsi. Se le connessioni sono forti il ricordo c'è, se si indeboliscono il ricordo svanisce. Questa semplificazione, tra l'altro, è stata adottata come modello per le reti neurali, base delle recenti ricerche sull'intelligenza Artificiale.

Tuttavia, la complessità dei meccanismi cellulari ha indotto a formulare modelli meno banali. In questa direzione un recente [studio di Stanford](https://www.biorxiv.org/content/10.64898/2026.07.29.741555v1) (guidato dalla ricercatrice Yuxi Ke nei laboratori Greenleaf e Schnitzer) ha evidenziato il ruolo della Cromatina all'interno del nucleo neuronale. Trattandosi di un preprint (attualmente su bioRxiv e in attesa di peer review), i risultati sono da prendere con le dovute cautele, ma le premesse sono interessanti. Lo studio è stato [condiviso su X]  (https://x.com/Yuxi_Ke/status/2087215792047915362?s=20) in questi giorni.

## Metodologia e prime evidenze

Lo studio è stato condotto su modelli murini (roditori), concentrandosi sulla corteccia prefrontale mediale (mPFC), un'area fondamentale per il consolidamento della memoria a lungo termine. Attraverso tecniche di biologia molecolare avanzata, come il *single-nucleus multiome sequencing* (che unisce l'ATAC-seq per l'accessibilità della cromatina e il trascrittoma) e il *genetic trapping* per isolare e marcare i neuroni che formano la traccia mnestica (archiviazione di un evento vissuto all'interno della memoria) i ricercatori hanno osservato i neuroni coinvolti in un ricordo di paura per settimane dopo la sua codifica. 

La prima evidenza è stata che la differenza tra neuroni "della memoria" e gli altri emerge prepotentemente solo al momento del richiamo (*recall*). È in quel momento che si evidenzia, solo per alcune tipologie di neuroni, l'avvio di un processo di "riconfigurazione" della Cromatina che impiega settimane per maturare (circa 28 giorni).

## Il tempo futuro della memoria

> *"Memory may preserve not only information about the past, but rules for how to change next"*

Il meccanismo osservato non sarebbe la semplice variazione di un "peso" neuronale (come nel modello hebbiano) ma una sorta di "programma" che determinerebbe il comportamento del neurone agli stimoli futuri. In altre parole la memorizzazione non serve solo a conservare informazioni sul passato, ma codifica le regole su come il neurone dovrà (o non dovrà) cambiare in futuro.

Questo meccanismo definito "metaplasticità" potrebbe servire a "proteggere" i ricordi consolidati, smorzando la reattività dei neuroni a nuovi stimoli e riducendo il rischio che nuove memorizzazioni sovrascrivano quelle vecchie. La metaplasticità, secondo i ricercatori, aiuta anche a risolvere l'intrinseca tensione nella necessità funzionale di avere circuiti che siano sia stabili che plastici, limitando selettivamente la plasticità piuttosto che sopprimerla globalmente. Nell'ippocampo, le esperienze temporalmente prossimali sarebbero codificate da insiemi "ravvicinati" di neuroni, mentre le esperienze che si verificano più distanti nel tempo corrisponderebbero a insiemi neurali più distanti, consentendo la riduzione dell'interferenza della memoria. 

L'ipotesi sviluppata è che memorizzare le informazioni sotto forma di "regole epigenetiche" (da attivare solo al bisogno) sia molto meno dispendioso a livello energetico rispetto a mantenere costantemente attive proteine ed espressione genica.
Un'ulteriore, affascinante considerazione dello studio riguarda l'evoluzione: i percorsi biologici che traducono gli stimoli ambientali in cambiamenti della cromatina non sono un'esclusiva dei neuroni. Sono meccanismi cellulari arcaici e conservati, condivisi da organismi lontanissimi: dai protozoi alle spugne (organismi privi di sistema nervoso), fino alle dinamiche di adattamento delle cellule tumorali.

## Il parallelo con la Computer Science

Nella *computer science*, il modello classico di Hebb è analogo a una rete neurale dove i pesi sinaptici si aggiornano con l'apprendimento. La metaplasticità introduce qualcosa di diverso. Sarebbe come conservare all'interno del neurone non solo "dati" ma anche "programmi", una sorta di *firmware* che cambia le regole di funzionamento di quel neurone: unisce stabilità con modificabilità.

Io ci vedo un parallelo con il tema del cosiddetto *stability-plasticity dilemma* delle reti neurali profonde (DNN), una sorta di funzione computazionale che, a livello di singolo neurone, potrebbe garantire l'equilibrio omeostatico tra persistenza dei ricordi e apprendimento continuo. Sicuramente potrebbe essere un interessante filone di ricerca.

## Conclusioni

La memoria, almeno secondo questa prospettiva, è più sofisticata di come è spesso descritta. E se riscrive le regole con cui il neurone reagirà agli stimoli futuri, possiede un meccanismo che protegge "i ricordi" senza rinunciare alla flessibilità, che la natura ha affinato per centinaia di milioni di anni.

Per chi lavora con le reti neurali artificiali, questo studio suggerisce una domanda provocatoria: dovremmo insegnare alle macchine come memorizzare i dati, o a imparare le regole per imparare?

Non ho approfondito qui temi complessi come l'epigenetica o i dettagli molecolari della regolazione genica, per non appesantire la lettura e per mantenere il focus sulla prospettiva generale. Ma sono certo che nei prossimi mesi sentiremo parlare molto di metaplasticità, cromatina e delle loro implicazioni per l'intelligenza artificiale.

## Riferimenti

- [Thread originale di Yuxi Ke su X](c)
- [Preprint su bioRxiv](https://www.biorxiv.org/content/10.64898/2026.07.29.741555v1)

