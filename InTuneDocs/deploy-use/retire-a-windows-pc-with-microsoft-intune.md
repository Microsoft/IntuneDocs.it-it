---
title: Ritirare un PC Windows | Microsoft Intune
description: Come ritirare un PC Windows gestito da Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 19e8e2b6a7eaa3cf02e4296a6fd147baa1472b61


---

# <a name="retire-a-windows-pc"></a>Ritirare un PC Windows
Seguire questa procedura per ritirare PC gestiti da Intune.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il computer da ritirare.

2.  Selezionare i dispositivi da ritirare, quindi scegliere **Disattiva/Cancella**.

Per registrare nuovamente un computer in Intune, reinstallare il client software nel PC seguendo la procedura descritta in [Installare il client PC Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Se un computer non è in grado di connettersi a Intune, viene visualizzato un messaggio nell'area di lavoro **Dashboard** .

Quando si ritira un computer:

-   Il computer viene rimosso dall'inventario e dalla gestione di Intune e la licenza associata al computer viene resa disponibile per essere riusata. Ritira/cancella dati rimuove il client del software Intune ma non rimuove le app o i dati dal computer. Il ritiro non esegue una cancellazione completa nel computer.

-   Lo stato del computer non viene più visualizzato nella console di Intune.

-   Intune rimuove il client software dal computer. Se il computer non è connesso al servizio Intune, il client software verrà rimosso alla successiva connessione.

-   Microsoft Intune Endpoint Protection viene rimosso dal computer. Se nel computer è installata un'altra applicazione Endpoint che è disabilitata, sarà possibile abilitarla di nuovo dopo aver rimosso Microsoft Intune Endpoint Protection per garantire che i computer siano protetti.

-   Tutti i criteri vengono rimossi dal computer e i valori impostati dal criterio vengono modificati.

-   Il computer non riceve più aggiornamenti software o aggiornamenti delle definizioni malware dal servizio Intune.

-   A seconda del modo in cui sono configurati, i computer ritirati possono continuare a ricevere gli aggiornamenti tramite Windows Server Update Services, Windows Update o Microsoft Update.

    > [!IMPORTANT]
    > Se il software client è stato installato tramite un oggetto Criteri di gruppo, è necessario rimuovere l'oggetto Criteri di gruppo prima di rimuovere il software client per evitare che il software venga reinstallato.

    Qualora non fosse possibile disinstallare il client, vedere [Risolvere i problemi di Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) per altre informazioni.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


