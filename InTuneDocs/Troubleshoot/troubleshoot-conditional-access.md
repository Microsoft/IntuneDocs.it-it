---
title: Risoluzione dei problemi di accesso condizionale | Microsoft Intune
description: Operazioni da eseguire quando gli utenti non riescono ad accedere alle risorse usando l'accesso condizionale di Intune.
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c1e215320168c659d5f838355f6350111d6979b0
ms.openlocfilehash: 21ae91f0d2866b621d9353929bab6d41d95dc8cc


---

# Risolvere i problemi di accesso condizionale

Questo argomento descrive le operazioni da eseguire quando gli utenti non riescono ad accedere alle risorse usando l'accesso condizionale di Intune. 

### Nozioni di base per il corretto funzionamento dell'accesso condizionale

Per garantire il funzionamento dell'accesso condizionale, devono essere soddisfatte le condizioni seguenti:

-   Il dispositivo deve essere gestito da Intune.
-   L'utente deve essere registrato con Azure Active Directory (AAD).
-   Il dispositivo deve essere conforme in base ai criteri di conformità configurati in Intune. 
-   EAS deve essere attivato nel dispositivo se l'utente sta recuperando la posta usando il client di posta elettronica nativo del dispositivo anziché Outlook.

Queste condizioni possono essere visualizzate per ogni dispositivo nel portale di gestione di Azure e nel report inventario dispositivi.





In genere, un utente che tenta di accedere alla posta elettronica o a SharePoint riceve una richiesta di registrazione. La richiesta indirizza l'utente al portale aziendale. Di seguito sono riportate le possibili spiegazioni di tale comportamento e le soluzioni consigliate:

## Scenari di autenticazione moderna

### Problemi di registrazione

 -  Il dispositivo non è registrato, quindi la registrazione risolverà il problema.
 -  L'utente ha registrato il dispositivo, ma l'aggiunta all'area di lavoro non è riuscita. L'utente deve aggiornare la registrazione dal portale aziendale. 
 
### Problemi di conformità

 -  Il dispositivo non è conforme ai criteri di Intune. Problemi comuni sono i requisiti di crittografia e password. L'utente verrà reindirizzato al portale aziendale, in cui può configurare il dispositivo in modo che sia conforme.
 -  Per i dispositivi iOS un profilo di posta elettronica esistente creato dall'utente bloccherà la distribuzione di un profilo di conformità (creato dall'amministratore di Intune) da Intune. Si tratta di un problema comune poiché gli utenti di iOS in genere creano un profilo di posta elettronica e poi eseguono la registrazione. Il portale aziendale informerà l'utente che non è conforme perché il profilo di posta elettronica è stato configurato manualmente e richiederà la rimozione del profilo. L'utente deve rimuovere il proprio profilo di posta elettronica per consentire la distribuzione del profilo di Intune. Per evitare il problema, indicare agli utenti di eseguire la registrazione senza installare un profilo di posta elettronica e di consentire a Intune di distribuire il profilo.  
 -  La registrazione delle informazioni di conformità per un dispositivo può richiedere tempo. Attendere qualche minuto e riprovare.

### Problemi relativi ai criteri

Quando si crea un criterio di conformità e lo si collega a un criterio di posta elettronica, entrambi i criteri devono essere distribuiti allo stesso utente, occorre quindi prestare attenzione quando si stabilisce quali criteri verranno distribuiti e a quali gruppi. Agli utenti per i quali viene applicato un solo criterio probabilmente risulterà che i dispositivi in uso non sono conformi.


## Scenari Exchange ActiveSync


- Un dispositivo Android registrato e conforme può comunque ricevere un avviso di quarantena quando tenta di accedere alle risorse aziendali. Prima di scegliere il collegamento **Inizio**, l'utente deve verificare che il portale aziendale non fosse aperto quando ha tentato di accedere alle risorse. Gli utenti devono chiudere il portale aziendale, tentare nuovamente di accedere alle risorse e quindi scegliere il collegamento **Inizio**.

- Un dispositivo ritirato può continuare ad accedere per diverse ore dopo il ritiro. Questo avviene perché Exchange memorizza nella cache i diritti di accesso per 6 ore. Prendere in considerazione altri metodi di protezione dei dati nei dispositivi ritirati in questo scenario.
- Possibile problema: Impossibile applicare patch EASID ad AAD. Una causa comune di questo problema è la limitazione, quindi attendere qualche minuto e riprovare. 

## Raccolta dei log delle cassette postali OWA

Se i problemi di connettività di Exchange persistono dopo la risoluzione dei problemi di distribuzione, raccogliere i log delle cassette postali OWA prima di contattare il supporto Microsoft, come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

1. Accedere a OWA e scegliere il simbolo delle impostazioni (ingranaggio) accanto al nome nell'angolo superiore destro. 
2. Scegliere **Opzioni**.
3. Scegliere **Telefono** (può essere **Dispositivi mobili**) nella colonna a sinistra.
4. Scegliere **Dispositivi mobili** dal menu in alto. 
5. Scegliere il dispositivo dall'elenco, quindi **Avvia registrazione**. 
6. Quando richiesto, scegliere **Sì** nella finestra di dialogo popup. 
7. Eseguire l'azione che ha causato il problema, in modo da riprodurlo. 
8. Attendere uno o due minuti, quindi tornare all'elenco dei telefoni in OWA, verificare che il proprio telefono sia selezionato nell'elenco e scegliere **Recupera il log** dal menu principale. 
9. Si dovrebbe ricevere un messaggio di posta elettronica dal proprio indirizzo con un allegato. Quando si apre un ticket di supporto, indicare il contenuto del messaggio al supporto Microsoft.


### Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Jul16_HO3-->


