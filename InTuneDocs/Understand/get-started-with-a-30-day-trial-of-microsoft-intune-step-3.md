---
# required metadata

title: Creare gruppi per organizzare utenti e dispositivi della sottoscrizione di valutazione | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7162cad3-5c14-43f3-a760-833ffd7786b1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Creare gruppi per organizzare utenti e dispositivi della sottoscrizione di valutazione
I gruppi in Intune offrono una grande flessibilità per la gestione di dispositivi e utenti. È possibile configurare i gruppi in base alle esigenze dell'organizzazione, ad esempio per località geografica, reparto o caratteristiche dell'hardware, e usarli per eseguire una vasta gamma di attività amministrative, dall'impostazione dei criteri per un set di utenti alla distribuzione di applicazioni a un set di dispositivi.

## Creare un gruppo di dispositivi
Usare i gruppi di dispositivi per distribuire software e aggiornamenti e per configurare i criteri di Impostazioni agente di Microsoft Intune e Impostazioni di Windows Firewall. Ad esempio, configurare un gruppo "Dispositivi di valutazione personali" usando la procedura seguente:

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Panoramica** &gt; **Crea gruppo**.

2.  Per **Nome gruppo** digitare "Dispositivi di valutazione personali", dall'elenco di gruppi padre selezionare **Tutti i dispositivi**, quindi fare clic su **Avanti**.

3.  Nella pagina **Definisci criteri appartenenza** selezionare **Tutti i dispositivi** per indicare che il gruppo include sia dispositivi mobili sia computer.

4.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Se in precedenza è stato creato un gruppo che non include tutti i dispositivi e si vogliono aggiungere dispositivi specifici al nuovo gruppo, è possibile farlo qui.

5.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi selezionare **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti i dispositivi**. Da qui è possibile inoltre modificare o eliminare il gruppo.

## Creare un gruppo di utenti
I gruppi di utenti consentono di distribuire criteri software e per dispositivi. Ad esempio, configurare un gruppo "Utenti di valutazione personali" usando la procedura seguente:

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Panoramica** &gt; **Crea gruppo**.

2.  Per **Nome gruppo**, digitare "Utenti di valutazione personali", dall'elenco di gruppi padre selezionare **Tutti gli utenti**, quindi fare clic su **Avanti**.

3.  In **Definisci criteri appartenenza** impostare **Iniziare l'appartenenza al gruppo con** su **Tutti gli utenti del gruppo padre**.

4.  Accanto a **Escludi i membri da questi gruppi di sicurezza** scegliere **Sfoglia** e quindi selezionare **Amministratore società**. Questa esclusione consentirà di gestire il gruppo Utenti di valutazione personali senza influire sull'account dell'amministratore dell'azienda (denominato anche amministratore tenant).

5.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Non è necessario effettuare alcuna operazione qui perché si vuole che il gruppo di utenti di valutazione personali includa tutti gli utenti tranne l'amministratore della società.

6.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi selezionare **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti gli utenti**. Da qui è possibile inoltre modificare o eliminare il gruppo.

Per altre informazioni sull’uso dei gruppi, vedere [Use groups to manage users and devices with Microsoft Intune](/Intune/Deploy-Use/use-groups-to-manage-users-and-devices-with-microsoft-intune) (Usare i gruppi per gestire utenti e dispositivi con Microsoft Intune).

### Passaggi successivi
A questo punto, il passaggio 3 della procedura di *valutazione di Microsoft Intune* è stato completato.

>[!div class="step-by-step"]

>[&larr; **Aggiungere utenti**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md)     [**Creare criteri** &larr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)  


<!--HONumber=May16_HO1-->


