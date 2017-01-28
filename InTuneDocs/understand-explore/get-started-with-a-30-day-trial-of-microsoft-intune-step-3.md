---
title: Creare gruppi per organizzare utenti e dispositivi in una versione di valutazione gratuita| Microsoft Docs
description: Come creare gruppi di dispositivi e gruppi di utenti quando si esegue l&quot;iscrizione per una valutazione gratuita di 30 giorni di Microsoft Intune.
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89e190e6a3e514c0f38b33409cde2abea0776885
ms.openlocfilehash: 0cdf5bf8f9fad1f44dbb0ef11de71aea55949d89


---

# <a name="create-groups-to-organize-evaluation-subscription-users-and-devices"></a>Creare gruppi per organizzare utenti e dispositivi della sottoscrizione di valutazione

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I gruppi in Intune offrono una grande flessibilità per la gestione di dispositivi e utenti. È possibile configurare i gruppi in base alle esigenze dell'organizzazione, ad esempio per località geografica, reparto o caratteristiche dell'hardware, e usarli per eseguire una vasta gamma di attività amministrative, dall'impostazione dei criteri per un set di utenti alla distribuzione di applicazioni a un set di dispositivi.

## <a name="create-a-device-group"></a>Creare un gruppo di dispositivi
Usare i gruppi di dispositivi per distribuire software e aggiornamenti e per configurare i criteri di Impostazioni agente di Microsoft Intune e Impostazioni di Windows Firewall. Ad esempio, configurare un gruppo "Dispositivi di valutazione personali" usando la procedura seguente:

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Panoramica** &gt; **Crea gruppo**.

2.  Per **Nome gruppo** digitare "Dispositivi di valutazione personali", selezionare **Tutti i dispositivi** dall'elenco di gruppi padre e quindi scegliere **Avanti**.

3.  Nella pagina **Definisci criteri appartenenza** selezionare **Tutti i dispositivi** per indicare che il gruppo include sia dispositivi mobili sia computer.

4.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Se in precedenza è stato creato un gruppo che non include tutti i dispositivi e si vogliono aggiungere dispositivi specifici al nuovo gruppo, è possibile farlo qui.

5.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi scegliere **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti i dispositivi**. Da qui è possibile inoltre modificare o eliminare il gruppo.

## <a name="create-a-user-group"></a>Creare un gruppo di utenti
I gruppi di utenti consentono di distribuire criteri software e per dispositivi. Ad esempio, configurare un gruppo "Utenti di valutazione personali" usando la procedura seguente:

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Panoramica** &gt; **Crea gruppo**.

2.  Per **Nome gruppo**, digitare "Utenti di valutazione personali", selezionare **Tutti gli utenti** dall'elenco di gruppi padre e quindi fare clic su **Avanti**.

3.  In **Definisci criteri appartenenza** impostare **Iniziare l'appartenenza al gruppo con** su **Tutti gli utenti del gruppo padre**.

4.  Accanto a **Escludi i membri di questi gruppi di sicurezza** scegliere **Sfoglia** e quindi selezionare **Amministratore società**. Questa esclusione consentirà di gestire il gruppo Utenti di valutazione personali senza influire sull'account dell'amministratore dell'azienda (denominato anche amministratore tenant).

5.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Non è necessario effettuare alcuna operazione qui perché si vuole che il gruppo di utenti di valutazione personali includa tutti gli utenti tranne l'amministratore della società.

6.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi scegliere **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti gli utenti**. Da qui è possibile inoltre modificare o eliminare il gruppo.

Per altre informazioni sull'uso dei gruppi, vedere [Creare gruppi per gestire utenti e dispositivi con Microsoft Intune](/Intune/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="next-steps"></a>Passaggi successivi
[Creare i criteri](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  



<!--HONumber=Jan17_HO1-->


