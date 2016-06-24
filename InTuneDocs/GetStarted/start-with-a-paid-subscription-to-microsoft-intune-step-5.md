---
# required metadata

title: Creare gruppi per organizzare utenti e dispositivi | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Creazione di gruppi per organizzare utenti e dispositivi
I gruppi di Intune offrono una grande flessibilità per la gestione di dispositivi e utenti. È possibile configurare gruppi in base alle esigenze dell'organizzazione, ad esempio per località geografica, reparto o caratteristiche dell'hardware, e usarli per eseguire una vasta gamma di attività amministrative, dalla distribuzione di criteri per un set di utenti alla distribuzione di applicazioni a un set di dispositivi.

Sia i gruppi di utenti e che i gruppi di dispositivi vengono creati nell'area di lavoro Gruppi della console di amministrazione di Intune.

![Area di lavoro Gruppi della console di amministrazione](./media/groups.png)


> [!TIP]
> Per altre informazioni sull'uso dei gruppi, vedere [Usare i gruppi per gestire utenti e dispositivi con Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)..


## Creare un gruppo di dispositivi
I gruppi di dispositivi consentono di distribuire app e aggiornamenti, nonché di configurare altre funzionalità. È ad esempio possibile eseguire le operazioni seguenti per configurare un gruppo denominato "Dispositivi personali":

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** > **Panoramica** > **Crea gruppo**.

2.  In **Nome gruppo** digitare "Dispositivi personali" e, dall'elenco di gruppi padre, selezionare **Tutti i dispositivi**, quindi scegliere **Avanti**.

3.  Nella pagina **Definisci criteri appartenenza** selezionare **Tutti i dispositivi** per indicare che il gruppo include sia dispositivi mobili sia computer.

4.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Se in precedenza è stato creato un gruppo che non include tutti i dispositivi e si vogliono aggiungere dispositivi specifici al nuovo gruppo, è possibile farlo qui.

5.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi selezionare **Fine**..

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti i dispositivi**. Da qui è possibile inoltre modificare o eliminare il gruppo.

## Creare un gruppo di utenti
I gruppi di utenti consentono di distribuire criteri software e per dispositivi. È ad esempio possibile eseguire le operazioni seguenti per configurare un gruppo denominato "Utenti di Intune":

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** > **Panoramica** > **Crea gruppo**.

2.  In **Nome gruppo** digitare "Utenti di Intune", quindi selezionare **Tutti gli utenti** nell'elenco di gruppi padre e infine scegliere **Avanti**.

3.  Nella pagina **Definisci criteri appartenenza** impostare **Iniziare l'appartenenza al gruppo con** su **Tutti gli utenti del gruppo padre**..

4.  Accanto a **Escludi i membri di questi gruppi di sicurezza** scegliere **Sfoglia** e quindi selezionare **Amministratore società**. Questa esclusione consente di gestire il gruppo Utenti di Intune senza modificare l'account dell'amministratore della società (noto anche come amministratore tenant).

5.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Non è necessario effettuare alcuna operazione perché si vuole che il gruppo di utenti di Intune includa tutti gli utenti, eccetto l'amministratore della società.

6.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi selezionare **Fine**..

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti gli utenti**. Da qui è possibile inoltre modificare o eliminare il gruppo.



### Passaggi successivi
A questo punto, Passaggio 5 della *Guida introduttiva di Intune* completato.

>[!div class="step-by-step"]

>[&larr; **Gestire le licenze di Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**Creare criteri e applicazioni** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  


<!--HONumber=May16_HO1-->


