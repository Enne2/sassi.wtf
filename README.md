# Progetto sassi.wtf

1 Obbiettivo
============

Realizzare una piattaforma radiofonica web-based e delocalizzata per consentire a chiunque nel territorio Materano abbia un contenuto da esprimere, comunicare e condividere tramite il mezzo radiofonico di poterlo fare in modo intuitivo, semplice, autogestito e rapido in qualsiasi luogo si trovi e qualsiasi mezzo informatico abbia a disposizione, il tutto in maniera del completamente gratuita, sia in live che pubblicando on demand in podcasting

2 Alternative già esistenti
===========================

Il principio alla base della piattaforma è simile ai sistemi di streaming già esistenti (spreaker, facebook, youtube, twitch ad esempio), la differenza sta nell'offrire una piattaforma e un brand riconoscibile e di aggregazione in cui gli autori possono riconoscersi e sentirsi parte di un lavoro cooperativo, evitando di frammentare il pubblico e la visibilità creando canali e pagine tra loro scollegate. Inoltre avere una piattaforma hardware e software propria può garantire continuità di funzionalità negli anni e spazio per sperimentazione tecnologica e adattamento alle necessità che emergeranno con l'uso effettivo. Ancora, la volontà di implementare webrtc come tecnologia di streaming (abbondando protocolli come icecast, rtmp, websocket) garantirebbero caratteristiche non presenti sulle altre piattaforme come soprattutto la bassissima latenza nell'ascolto, risultato molto prossimo alle radio in FM analogico.

3 Use cases
===========

Il sistema prevede tre tipologie di utenti per le quai devono essere sviluppate tipologie diverse di interfaccia e un adatto sistema di gestione utenti.

3.1 Listener
------------

Utente generico che abbia la possibilità di usufruire dei contenuti live e on demand. La sua interfaccia è il sito pubblico con dominio sassi.wtf, su di esso deve essere possibile ricevere e ascoltare lo stream live via webrtc, le puntate e il feed xml del podcast via https.A questo può aggiugersi la possibilità di interagire con commenti e altro

3.2 Broadcaster
---------------

Utente che ha la possibilità di generare contenuti radiofonici. Ha a disposizione un programma di regia con interfaccia browser ed è in grado di streammare e/o registrare i contenuti prodotti. Ha anche la possibilità di uploadare puntate del podcast relative al suo format. La rceazione di broadcaster e relativi formati ne, database utenti è compito dell'Admin

3.3 Admin
---------

Upervisiona l'utilizzo della piattaforma e i contenuti pubblicati. Ha una sua dashboard di controllo.

4 Architettura software
=======================

Nell'ottica di garantire affidabilità, sicurezza e scalabilità il server http, il sistema di signnaling, di trasmissione broadcasting webrtc e quello di ricezione del broadcaster saranno fra di loro indipendenti e scalarmente ridondabili.

4.1 Server http
---------------

Server utile a pubblicare i contenuti web, i podcast e servire le interfacce di podcasting e le interfacce di amministrazione e broadcasting.

4.2 Server di signaling
-----------------------

Server che implementa il protocollo websocket che consenta di instaurare le sessioni webrtc tra listener e i bradcaster webrtc

4.3 Broadcaster webrtc
----------------------

Processi software avviati on demand per goni Listener in grado di raccogliere la fonte audio da streamare e trasmeterla via webrtc

4.4 Ricevitore Broadcaster
--------------------------

Middleware in grado di ricevere lo stream trasmesso dall'utente Broadcaster applicare logche per garantire i fallback e inoltrare lo stream ai broascaster webrtc

5 Hardware
==========

È sufficiente una piccola macchina Debian Linux anche virualizzata con ragionevole banda in upload

6 Costi
=======

I costi iniziali riguardano la sola attrezzatura hardware e possono essere da nulli a pochi euro mensili

7 Proposta di tabella di marcia
===============================

7.1 Proof of concept sistema webrtc
-----------------------------------

7.2 Versione essenziale del sito
--------------------------------

Implementare bnnell'attuale sito l'ascolto tramite webrtc di uno stream di prova

### 7.2.1 Realizzazione del server di signaling (python, backend)

### 7.2.2 Realizzazione broadcaster webrtc (python, backend)

### 7.2.3 Implementazione nel sito del receiver webrtc javascript (JS, Frontend)

### 7.2.4 Implementazione del middleware usando liquidsoa con input icecast

7.3 Interfaccia broadcaster web-based
-------------------------------------

### 7.3.1 Adattare...
