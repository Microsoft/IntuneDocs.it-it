---
title: Ritirare un PC Windows
description: Come ritirare un PC Windows gestito da Intune.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99dc86bf20a50710cf1661702d46a3124861a619
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31015711"
---
# <a name="retire-a-windows-pc"></a>Ritirare un PC Windows

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Usare la procedura descritta di seguito per ritirare i desktop gestiti come PC eseguendo il client software di Intune. Quando si ritira un PC, lo si rimuove dalla gestione Intune. Non è possibile ripristinare le impostazioni predefinite di un PC da Intune per riportarlo alle impostazioni originali.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il PC da ritirare.

2.  Selezionare i dispositivi da ritirare, quindi scegliere **Disattiva/Cancella**.

Per registrare nuovamente un PC in Intune, reinstallare il client software nel PC seguendo la procedura descritta in [Installare il client PC Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Se un PC non è in grado di connettersi a Intune, viene visualizzato un messaggio nell'area di lavoro **Dashboard**.

Quando si ritira un PC:

-   Il PC viene rimosso dall'inventario e dalla gestione di Intune e la licenza associata al PC viene resa disponibile per essere riusata. Ritira/cancella dati rimuove il client software Intune ma non rimuove le app o i dati dal PC. Il ritiro non esegue una cancellazione completa nel PC.

-   Lo stato del computer non viene più visualizzato nella console di Intune.

-   Intune rimuove il client software dal PC. Se il PC non è connesso al servizio Intune, il client software verrà rimosso alla successiva connessione.

-   Microsoft Intune Endpoint Protection viene rimosso dal PC. Se nel PC è installata un'altra applicazione endpoint ed è disabilitata, sarà possibile abilitarla di nuovo dopo aver rimosso Microsoft Intune Endpoint Protection per garantire che i PC siano protetti.

-   Tutti i criteri vengono rimossi dal PC e i valori impostati dal criterio verranno modificati.

-   Il PC non riceve più aggiornamenti software o aggiornamenti delle definizioni malware dal servizio Intune.

-   A seconda del modo in cui sono configurati, i PC ritirati possono continuare a ricevere gli aggiornamenti tramite Windows Server Update Services, Windows Update o Microsoft Update.

    > [!IMPORTANT]
    > Se il software client è stato installato tramite un oggetto Criteri di gruppo, è necessario rimuovere l'oggetto Criteri di gruppo prima di rimuovere il software client per evitare che il software venga reinstallato.

    Qualora non fosse possibile disinstallare il client Endpoint Protection, vedere [Risolvere i problemi di Endpoint Protection](/intune-classic/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) per altre informazioni.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)