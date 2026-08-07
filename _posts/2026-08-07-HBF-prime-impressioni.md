---
layout: post
title: "HBF: prime impressioni sulla specifica OCP"
image: assets/img/_tmb/HBF_512x512.png
date: 2026-08-07
categories: ai memory storage hbf
tags: [HBF, AI, UCIe, OCP, NAND, LLM]
---
# HBF: è uscita la prima specifica OCP.

Le news uscite in questi giorni su High Bandwidth Flash (HBF) si concentrano sui dettagli da marketing.
Io sono andato a recuperare la prima bozza della specifica OCP (versione 0.7.0), più di cento pagine

[OCP HBF spec v 0.7.0](https://www.opencompute.org/documents/ocp-hbf-architecture-specification-v0-7-0-final-pdf)

## Prime impressioni

Non è uno "storage più veloce".
HBF è integrata strettamente con l'xPU via UCIe, con un proprio Base Die Controller e canali paralleli interni: architettura da memoria, non da storage.
AXI sopra UCIe rafforza questa lettura: modello più simile a memoria integrata che a un dispositivo NVMe. Da capire l'impatto su software di sistema e runtime.
Grande spazio al modello di programmazione: la specifica dovrebbe indicare come organizzare e distribuire i dati sui canali per sfruttare il parallelismo.

## Gli spunti di interesse

Il documento porta esempi di carichi di lavoro LLM reali:
- Parameter Store
- KV Cache
- Single/Multiple LLM Serving
- Mixture of Experts

HBF è pensato per colmare il divario tra velocità di memoria e capacità richiesta dai modelli AI.

## Domande aperte

- Esposizione ai sistemi operativi
- Ruolo dei driver
- Nuove API
- Integrazione con HBM/CXL, NVMe-oC ecc. 
- Impatto su framework e runtime

## Nei prossimi post

Nei prossimi post spero di scendere nei dettagli ed anticipare qualche tema utile per i futuri sviluppi.

## Riferimenti

- [Hardware Upgrade 04/08](https://www.hwupgrade.it/news/memorie/hbf-la-nuova-memoria-tra-rime-specifiche-tecniche-aperte_157285.html)
- [Tom's Hardware ITA 31/07](https://www.tomshw.it/hardware/le-gpu-potrebbero-avere-terabyte-di-memoria-grazie-alla-flash-hbf)