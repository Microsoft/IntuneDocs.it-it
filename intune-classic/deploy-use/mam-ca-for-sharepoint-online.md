---
title: Creare criteri di accesso condizionale basato su app per SharePoint Online
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2d9065281436d4c44e6af7d7a4401786a2a01965
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-app-based-conditional-access-ca-policies-for-sharepoint-online"></a>Configurare criteri di accesso condizionale basato su app per SharePoint Online

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Questo argomento contiene le linee guida per la configurazione di criteri di accesso condizionale basato su app per SharePoint Online. L'accesso condizionale basato su app permette agli amministratori di consentire solo le app per dispositivi mobili cui sono applicati criteri di protezione delle app di Intune.

## <a name="to-create-the-app-based-ca-policy-for-sharepoint-online"></a>Per creare i criteri di accesso condizionale basato su app per SharePoint Online

1. Passare al [portale di Azure](https://portal.azure.com) e accedere con le proprie credenziali.

    > [!NOTE]
    > Se non si ha familiarità con il portale di Azure, leggere l'argomento [Portale di Azure per i criteri di protezione delle app](azure-portal-for-microsoft-intune-mam-policies.md).

2. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Protezione app di Intune** > **Gestione di applicazioni mobili di Intune** > **Tutte le impostazioni**.

4. Nel pannello di gestione di applicazioni mobili di Intune scegliere il riquadro SharePoint Online.

5. Nel pannello **App consentite** scegliere l'opzione **Consenti app che supportano i criteri app di Intune** per consentire solo le app supportate da criteri di protezione delle app di Intune.

    > [!NOTE] 
    > Quando si seleziona l'opzione per consentire solo le app supportate dai criteri di protezione delle app di Intune, viene visualizzato un elenco che contiene **solo** le app supportate.

    ![Schermata del pannello delle app consentite con l'elenco delle app](../media/mam-ca-spo-allowed-apps.png)

## <a name="to-assign-app-based-ca-policies-to-your-users"></a>Per assegnare criteri di accesso condizionale basato su app agli utenti

1. Aprire il pannello **Gruppi di utenti limitati** e quindi scegliere **Aggiungi un gruppo di utenti**.

2. Selezionare uno o più gruppi di utenti a cui applicare questi criteri.

    ![Screenshot del pannello Gruppi di utenti limitati e opzione Aggiungi un gruppo di utenti selezionata](../media/mam-ca-spo-restricted-groups.png)

    > [!IMPORTANT] 
    > È possibile che alcuni utenti appartenenti al gruppo selezionato nel passaggio precedente non debbano essere interessati da questi criteri. In questi casi aggiungere il gruppo di utenti all'elenco dei gruppi esentati. 

3. Nel pannello **SharePoint Online** scegliere **Gruppi di utenti esentati**, quindi scegliere **Aggiungi un gruppo di utenti** per aprire l'elenco dei gruppi di utenti.

4. Selezionare i gruppi che si vuole esentare da questi criteri.  

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Per modificare o eliminare gruppi di utenti da un criterio di accesso condizionale basato su app esistente

1. Aprire il pannello **Gruppi di utenti limitati** e quindi evidenziare il gruppo di utenti che si vuole eliminare.
2. Fare clic sui puntini di sospensione per visualizzare le opzioni di eliminazione.
3. Scegliere **Elimina** per rimuovere il gruppo di utenti dall'elenco.

> [!NOTE] 
> È possibile seguire la stessa procedura per rimuovere un gruppo di utenti dall'elenco **Gruppi di utenti esentati**.

## <a name="next-steps"></a>Passaggi successivi

[Bloccare le app che non usano l'autenticazione moderna (ADAL)](block-apps-with-no-modern-authentication.md)

## <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Configurare l'accesso condizionale basato su app per Exchange Online](mam-ca-for-exchange-online.md)

