---
title: Accesso delle app per Exchange Online
description: Questo argomento descrive come configurare criteri di accesso condizionale per app MAM.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a64a5ac7f10bb7988c75dd473e1e87dae03959d4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>Creare un accesso condizionale a Exchange Online per consentire solo le app supportate dalla gestione di applicazioni mobili

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Questo argomento contiene istruzioni dettagliate su come configurare un accesso condizionale a Exchange Online in modo da consentire solo le app mobili che supportano i criteri di protezione delle app di Intune.


## <a name="create-an-exchange-online-policy"></a>Creare criteri di Exchange Online
1.  Accedere al [Portale di Azure](https://portal.azure.com) in cui è disponibile la funzionalità di accesso delle app. Se non si ha familiarità con il Portale di Azure, leggere l'argomento [Portale di Azure per i criteri di protezione delle app](azure-portal-for-microsoft-intune-mam-policies.md).

2.  Scegliere **Altri servizi** e digitare "Intune".

3.  Scegliere **Protezione app di Intune**.

4.  Nel pannello **Gestione di applicazioni mobili di Intune** scegliere **Tutte le impostazioni**.

5.  Nella sezione **Accesso condizionale** scegliere **Exchange Online**.

    ![Screenshot del pannello delle impostazioni e sezione dell'accesso condizionale con l'opzione Exchange Online selezionata](../media/MAM-conditional-access-1.png)

6. Nel pannello **App consentite** scegliere l'opzione **Allow apps that support Intune app policies** (Consenti app che supportano i criteri per app Intune) per consentire solo alle app supportate dai criteri di protezione delle app di Intune di accedere a Exchange Online. Quando si seleziona questa opzione, viene visualizzato l'elenco delle app supportate.

    >[!NOTE]
    >Tutti i client di posta elettronica di Exchange Active Sync, tra cui i client di posta elettronica predefiniti in iOS e Android che si connettono a Exchange Online, non potranno inviare né ricevere messaggi di posta elettronica. Gli utenti riceveranno invece un solo messaggio di posta elettronica che li avvisa di usare Outlook come app di posta elettronica.

7. Per applicare questi criteri agli utenti, aprire il pannello **Gruppi di utenti limitati** e scegliere **Aggiungi un gruppo di utenti**. Selezionare uno o più gruppi di utenti a cui applicare questi criteri.

    ![Screenshot del pannello Gruppi di utenti limitati e opzione Aggiungi un gruppo di utenti selezionata](../media/mam-ca-add-user-group.png)

8. È possibile che alcuni utenti appartenenti al gruppo selezionato nel passaggio precedente non debbano essere interessati da questi criteri. In questi casi aggiungere il gruppo di utenti all'elenco dei gruppi esentati. Scegliere **Exempted user groups** (Gruppi di utenti esentati) dal pannello **Exchange Online**. Scegliere **Aggiungi un gruppo di utenti** per aprire l'elenco dei gruppi di utenti. Selezionare i gruppi che si vuole esentare da questi criteri.  

## <a name="modify-an-existing-policy"></a>Modificare criteri esistenti
### <a name="add-or-delete-user-groups"></a>Aggiungere o eliminare gruppi di utenti

Per **eliminare un gruppo di utenti** dall'elenco dei **gruppi di utenti limitati**, aprire il pannello **Gruppi di utenti limitati**, evidenziare il gruppo da eliminare e fare clic sui **puntini di sospensione (...)** per visualizzare l'opzione **Elimina**. Scegliere **Elimina** per rimuovere il gruppo di utenti dall'elenco. È possibile seguire la stessa procedura per rimuovere un gruppo di utenti dall'elenco dei **gruppi di utenti esentati**.


## <a name="next-steps"></a>Passaggi successivi
[Bloccare le app che non usano l'autenticazione moderna](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>Vedere anche
[Proteggere i dati delle app con i criteri di protezione delle app](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
