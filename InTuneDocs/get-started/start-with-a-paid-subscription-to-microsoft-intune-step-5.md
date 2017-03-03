---
title: Creare gruppi per organizzare utenti e dispositivi | Documentazione Microsoft
description: Creare utenti e gruppi per la sottoscrizione di Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5fdf98c8-fe67-4d7a-9837-ed1234348014
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ad13897fe7bbe4fe13167bb4ce7f558b436a7a90
ms.openlocfilehash: 1b14ec6330c512981025a2910dbd222fa4d7cf7f
ms.lasthandoff: 02/15/2017


---


# <a name="create-groups-to-organize-users-and-devices"></a>Creazione di gruppi per organizzare utenti e dispositivi

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento descrive come gli amministratori possono creare gruppi di utenti in Intune.

I gruppi in Intune offrono una grande flessibilità per la gestione di dispositivi e utenti. È possibile configurare gruppi in base alle esigenze dell'organizzazione, ad esempio per località geografica, reparto o caratteristiche dell'hardware, e usarli per eseguire una vasta gamma di attività amministrative, dalla distribuzione di criteri per un set di utenti alla distribuzione di applicazioni a un set di dispositivi.

## <a name="group-management-moving-to-azure-ad"></a>Migrazione della gestione dei gruppi ad Azure AD

**A partire da novembre 2016** i nuovi account gestiranno i gruppi di utenti e dispositivi nel portale di Azure Active Directory (AD). A dicembre 2016 il team di prodotto Intune inizierà la migrazione dei clienti esistenti alla nuova esperienza di gestione dei gruppi basata su Azure AD. Tutti i gruppi di utenti e dispositivi verranno migrati a gruppi di sicurezza di Azure AD. Microsoft non inizierà la migrazione senza prima aver ridotto al minimo l'impatto sulle attività quotidiane degli utenti e fino a quando non sarà previsto alcun impatto sugli utenti finali. Verrà inoltre inviata notifica prima della migrazione degli account.


>[!IMPORTANT]
>
>Se si apre l'area di lavoro Gruppi nel portale di Intune e viene visualizzata l'indicazione **I gruppi utenti di Intune vengono ora gestiti come gruppi in Azure Active Directory** con un collegamento al portale di Azure Active Directory, questo indica che è già in uso il *nuovo* approccio alla gestione dei gruppi in Intune basato sui gruppi di sicurezza di Azure AD. Per informazioni su come creare i gruppi, vedere [Gestione dei gruppi in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal).
>
>Se non viene visualizzato il collegamento al portale di Azure AD, questa è un'indicazione che è ancora in uso il portale di Intune per la gestione dei gruppi.

## <a name="group-management-in-the-intune-portal"></a>Gestione dei gruppi nel portale di Intune

Sia i gruppi di utenti e che i gruppi di dispositivi vengono creati nell'area di lavoro Gruppi della console di amministrazione di Intune.

![Area di lavoro Gruppi della console di amministrazione](./media/groups.png)


> [!TIP]
> Per altre informazioni sull'uso dei gruppi, vedere [Creare gruppi per gestire utenti e dispositivi con Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).


## <a name="create-a-device-group"></a>Creare un gruppo di dispositivi
I gruppi di dispositivi consentono di distribuire app e aggiornamenti, nonché di configurare altre funzionalità. È ad esempio possibile eseguire le operazioni seguenti per configurare un gruppo denominato "Dispositivi personali":

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** > **Panoramica** > **Crea gruppo**.

2.  In **Nome gruppo** digitare "Dispositivi personali", dall'elenco di gruppi padre selezionare **Tutti i dispositivi** e quindi scegliere **Avanti**.

3.  Nella pagina **Definisci criteri appartenenza** selezionare **Tutti i dispositivi** per indicare che il gruppo include sia dispositivi mobili sia computer.

4.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Se in precedenza è stato creato un gruppo che non include tutti i dispositivi e si vogliono aggiungere dispositivi specifici al nuovo gruppo, è possibile farlo qui.

5.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi scegliere **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti i dispositivi**. Da qui è possibile inoltre modificare o eliminare il gruppo.

## <a name="create-a-user-group"></a>Creare un gruppo di utenti
I gruppi di utenti consentono di distribuire criteri software e per dispositivi. È ad esempio possibile eseguire le operazioni seguenti per configurare un gruppo denominato "Utenti di Intune":

1.  Nella [console di amministrazione di Intune](https://manage.microsoft.com/) scegliere **Gruppi** > **Panoramica** > **Crea gruppo**.

2.  In **Nome gruppo** digitare "Utenti di Intune", quindi selezionare **Tutti gli utenti** nell'elenco di gruppi padre e infine scegliere **Avanti**.

3.  In **Definisci criteri appartenenza** impostare **Iniziare l'appartenenza al gruppo con** su **Tutti gli utenti del gruppo padre**.

4.  Accanto a **Escludi i membri di questi gruppi di sicurezza** scegliere **Sfoglia** e quindi selezionare **Amministratore società**. Questa esclusione consente di gestire il gruppo Utenti di Intune senza modificare l'account dell'amministratore della società (noto anche come amministratore tenant).

5.  Nella pagina **Definisci appartenenza diretta** scegliere **Avanti**. Non è necessario effettuare alcuna operazione perché si vuole che il gruppo di utenti di Intune includa tutti gli utenti, eccetto l'amministratore della società.

6.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite e quindi scegliere **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** in **Tutti gli utenti**. Da qui è possibile inoltre modificare o eliminare il gruppo.

>[!div class="step-by-step"]

>[&larr; **Gestire le licenze di Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)       [**Creare criteri e app** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-6.md)  

