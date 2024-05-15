---
layout: ../../layouts/MarkdownPostLayout.astro
title: 'Scoperta una delle backdoor più pericolose nel mondo del software open source'
pubDate: 2022-07-01
description: 'This is the first post of my new Astro blog.'
author: Federico Bottarelli
image:
    url: 'https://docs.astro.build/assets/full-logo-light.png'
    alt: 'The full Astro logo.'
tags: ["astro", "blogging", "learning in public"]
---

## Cosa è successo?
Il 30 marzo è stata scoperta una delle backdoor potenzialmente più pericolose mai viste nel mondo dei software open source, che fa riflettere sulla possibilità che ne esistano altre simili ancora non scoperte.

XZ Utils è una raccolta di strumenti open source e librerie per la compressione XZ, simile a zip o rar, che vengono utilizzati ampiamente nel mondo Linux. Venerdì 29 marzo, Andres Freund (un ingegnere del software di Microsoft) ha inviato una email a oss-security informando la comunità sulla scoperta di una backdoor nelle versioni 5.6.0 e 5.6.1 di xz/liblzma.

## Come funzionava la backdoor e cosa permetteva di fare?
La backdoor entra in gioco con uno dei modi principali in cui xz viene utilizzato - SSH. SSH è un protocollo crittografato tra due macchine in cui possono essere scambiati comandi di testo, consentendo a un utente di interagire con un server. La backdoor significa che la connessione non è più privata e potrebbe consentire a un attaccante di lanciare comandi, permettendo quindi il pieno controllo del server.

## Perché è importante?
XZ Utils è una libreria usata ovunque nei server Linux, che hanno una quota di mercato del 70% dei server nel mondo. Parliamo di una backdoor che permette quindi di rubare informazioni e controllare un numero immenso di server nel mondo, e avrebbe potuto causare disastri difficili da immaginare se fosse arrivata alle release stabili usate comunemente dai server.

## Devo preoccuparmi?
Riguardo a questa specifica backdoor no, perché grazie alla sua recente scoperta è già stata corretta prima di arrivare a qualsiasi release Linux stabile. Ha colpito solo le rolling release linux. Tuttavia, rimane un motivo di preoccupazione il fatto che potrebbero esserci altre simili backdoor ancora non scoperte.

## Come è stata scoperta?
Andres Freund è un ingegnere di Microsoft che, dopo l'aggiornamento di OpenSSH, ha notato un uso anomalo di CPU, anche con un login errato. Ha iniziato a fare reverse engineering per cercare la causa di questa anomalia e, dopo un'approfondita analisi, ha trovato la backdoor, offuscata con tecniche avanzate.

## Chi ha messo la backdoor?
Per poter fare modifiche su un progetto open source di questa importanza bisogna essere contributori affidabili. Infatti, l'account colpevole ha contribuito molte volte nell'arco di mesi, conquistando la fiducia degli altri contributori. Non sembra un'azione compiuta da un singolo soggetto; la complessità dell'operazione non lascia dubbi. Non è improbabile, visti i precedenti e la scala dell'attacco, che ci sia un eventuale governo dietro, Cina e Russia in primis.