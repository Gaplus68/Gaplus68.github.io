---
layout: post
title: "HBF: prime impressioni sulla specifica OCP"
date: 2026-08-07
categories: ai memory hbf
tags: [HBF, AI, UCIe, OCP, NAND, LLM]
---
HBF: è uscita la prima specifica OCP. Prime impressioni da sviluppatore
Mentre gli articoli su High Bandwidth Flash (HBF) si concentrano sui numeri — banda fino a diversi TB/s, stack NAND, interfaccia UCIe — è uscita la prima bozza della specifica OCP, versione 0.7.0. Oltre cento pagine di draft. Prime impressioni.
Non è uno SSD più veloce. HBF è integrata strettamente con l'xPU via UCIe, con un proprio Base Die Controller e canali paralleli interni: architettura da memoria, non da storage.
AXI sopra UCIe rafforza questa lettura: modello più simile a memoria integrata che a un dispositivo NVMe. Da capire l'impatto su software di sistema e runtime.
Grande spazio al modello di programmazione: la specifica indica come organizzare e distribuire i dati sui canali per sfruttare il parallelismo.
La sorpresa: gli esempi sono carichi di lavoro LLM reali — Parameter Store, KV Cache, Single/Multiple LLM Serving, Mixture of Experts. HBF nasce per colmare il divario tra velocità di memoria e capacità richiesta dai modelli AI.
Domande aperte: esposizione ai sistemi operativi, ruolo dei driver, nuove API, integrazione con HBM/CXL, impatto su framework e runtime.
Nei prossimi articoli andrò nel dettaglio, separando ciò che è definito da ciò che è ancora direzione progettuale.
