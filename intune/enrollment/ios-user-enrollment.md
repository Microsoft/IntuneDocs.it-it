---
title: Registrare dispositivi iOS - Registrazione utente
titleSuffix: Microsoft Intune
description: Informazioni su come configurare la registrazione utente iOS e iPadOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57162664d6ca3a35696e56088c4e86acadf45371
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955327"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>Configurare la registrazione utente iOS e iPadOS (anteprima)

È possibile configurare Intune per registrare i dispositivi iOS e iPadOS con il processo di registrazione utente di Apple. La registrazione utente offre agli amministratori un subset di opzioni di gestione semplificato rispetto ad altri metodi di registrazione.

Per altre informazioni sulle opzioni disponibili con la registrazione utente, vedere [Azioni e opzioni supportate per la registrazione utente](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> Il supporto per la registrazione utente di Apple in Intune è attualmente in versione di anteprima.

## <a name="prerequisites"></a>Prerequisiti
- [Autorità di gestione dei dispositivi mobili (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- [ID Apple gestiti](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Creare un profilo di registrazione utente in Intune

Un profilo di registrazione definisce le impostazioni applicate a un gruppo di dispositivi durante la registrazione. 

1. Nel portale di Intune scegliere **Registrazione dispositivi** > **Registrazione Apple** > **Tipi di registrazione (anteprima)**  > **Crea profilo** > **iOS**. Questo profilo è la posizione in cui verrà indicata l'esperienza di registrazione degli utenti finali di iOS e iPadOS nei dispositivi non registrati tramite un metodo Apple aziendale. Se si vogliono apportare modifiche, è possibile modificare questo profilo dopo averlo creato.

    ![Creare un profilo di registrazione Apple](./media/ios-user-enrollment/create-profile.png)

2. Nella pagina **Informazioni di base** immettere un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti. È possibile usare questo campo **Nome** per creare un gruppo dinamico in Azure Active Directory. Usare il nome del profilo per definire il parametro enrollmentProfileName per assegnare i dispositivi con questo profilo di registrazione. Altre informazioni sui [gruppi dinamici di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Pagina Informazioni di base](./media/ios-user-enrollment/basics-page.png)


3. Selezionare **Avanti**.

4. Nella pagina **Impostazioni** è possibile scegliere di offrire agli utenti la possibilità di selezionare il tipo di registrazione da usare. In alternativa, è possibile specificare un'impostazione predefinita.

    ![Pagina Impostazioni](./media/ios-user-enrollment/settings-page.png)

    - Se si vuole che tutti gli utenti di questo profilo usino la registrazione utente, seguire questa procedura:
        1. Per **Richiedi all'utente di selezionare il tipo di dispositivo** selezionare **Non configurato**.
        2. Per **Tipo di registrazione predefinito** selezionare **Registrazione utente**.
    - Se si vuole che tutti gli utenti di questo profilo usino la registrazione dispositivi, seguire questa procedura:
        1. Per **Richiedi all'utente di selezionare il tipo di dispositivo** selezionare **Non configurato**.
        2. Per **Tipo di registrazione predefinito** selezionare **Registrazione dispositivi**.
    - Se si vuole consentire a tutti gli utenti del gruppo di scegliere il tipo di registrazione da usare, selezionare **Obbligatorio** per **Richiedi all'utente di selezionare il tipo di dispositivo**. Quando gli utenti registrano i propri dispositivi, avranno la possibilità di scegliere tra **Sono il proprietario del dispositivo** e **(Società) possiede il dispositivo**. Se scelgono la prima opzione, il dispositivo verrà registrato usando la registrazione utente. Se scelgono la seconda opzione, il dispositivo verrà registrato usando la registrazione dispositivi. Se l'utente sceglie **Sono il proprietario del dispositivo**, otterrà un'altra opzione per proteggere l'intero dispositivo o solo le app e i dati correlati al lavoro. La scelta dell'utente finale sulla proprietà del dispositivo determina solo il tipo di registrazione implementato nel dispositivo. Questa scelta dell'utente non viene riflessa nell'attributo Proprietà del dispositivo in Intune. Per altre informazioni sull'esperienza utente, vedere [Configurare l'accesso del dispositivo iOS alle risorse aziendali](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
    > [!NOTE]
    > L'avviso seguente non è accurato e verrà rimosso dall'interfaccia utente.
    > "Per consentire il funzionamento dell'Accesso condizionale nei dispositivi con Registrazione utente, sarà necessario eseguire il push dell'app Azure Authenticator come app obbligatoria per questo gruppo di utenti per abilitare l'accesso Single Sign-On e Workplace Join".
    > In qualità di amministratore, non è necessario eseguire alcuna azione per eseguire il push dell'app Authenticator per gli utenti. All'interno del Portale aziendale verrà richiesto agli utenti di installare l'app Authenticator per completare il processo di registrazione utente per assicurare il corretto funzionamento di questi scenari.

5. Selezionare **Avanti**.

6. Nella pagina **Assegnazioni** scegliere i gruppi di utenti contenenti gli utenti a cui si vuole assegnare il profilo. È possibile scegliere di assegnare il profilo a tutti gli utenti o a gruppi specifici. Tutti gli utenti dei gruppi selezionati useranno il tipo di registrazione selezionato in precedenza. I gruppi di dispositivi non sono supportati per gli scenari di registrazione utente poiché la funzionalità è basata sulle identità utente anziché sui dispositivi. È possibile scegliere di assegnare il profilo a tutti gli utenti o a gruppi specifici.

    ![Pagina Assegnazioni](./media/ios-user-enrollment/assignments-page.png)

7. Selezionare **Avanti**.

8. Nella pagina **Rivedi e crea** esaminare le scelte effettuate e quindi selezionare **Crea** per assegnare il profilo agli utenti.

    ![Pagina Assegnazioni](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Priorità del profilo

Dopo aver creato più profili del tipo di registrazione, è possibile modificare l'ordine di priorità in cui vengono applicati.

1. In Intune nel portale di Azure scegliere **Registrazione dispositivi** > **Registrazione Apple** > **Tipi di registrazione (anteprima)** .
2. Trascinare e rilasciare i profili nell'elenco nell'ordine in cui si vuole applicarli.

In caso di conflitti tra i profili di un utente, viene applicato all'utente il profilo con priorità più elevata.


