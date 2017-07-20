---
title: Criteri di accesso condizionale basato su app con Intune
description: Questo argomento descrive come configurare criteri di accesso condizionale basato su app con Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a7f054868d0bae061f348239614f3a40b96a15b1
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2017
---
# <a name="set-up-app-based-conditional-access-policies"></a>Configurare criteri di accesso condizionale basato su app

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento descrive come configurare criteri di accesso condizionale basato su app per le app che fanno parte dell'elenco di app approvate. L'elenco di app approvate include le applicazioni testate da Microsoft.

> [!IMPORTANT]
> Questo argomento descrive come configurare la procedura per l'aggiunta di criteri per l'accesso condizionale basato su app con Exchange Online, ma è possibile usare la stessa procedura per aggiungere altre app dall'elenco delle app approvate, ad esempio SharePoint Online, Microsoft Teams e così via.

## <a name="to-create-an-app-based-conditional-access-policy"></a>Per creare criteri di accesso condizionale basato su app
1.  Passare al [portale di Azure](https://portal.azure.com) e accedere con le proprie credenziali.

2.  Scegliere **Altri servizi** e digitare "Intune".

3.  Scegliere **Protezione app di Intune**.

4.  Nel pannello **Gestione di applicazioni mobili di Intune** scegliere **Tutte le impostazioni**.

5.  Nella sezione **Accesso condizionale** scegliere **Exchange Online**.

    ![Screenshot del pannello delle impostazioni e sezione dell'accesso condizionale con l'opzione Exchange Online selezionata](./media/MAM-conditional-access-1.png)

6. Nel pannello **App consentite** scegliere l'opzione **Allow apps that support Intune app policies** (Consenti app che supportano i criteri per app Intune) per consentire solo alle app supportate dai criteri di protezione delle app di Intune di accedere a Exchange Online. Quando si seleziona questa opzione, viene visualizzato l'elenco delle app supportate.

    > [!NOTE]
    > Tutti i client di posta elettronica di Exchange Active Sync, tra cui i client di posta elettronica predefiniti in iOS e Android che si connettono a Exchange Online, non potranno inviare né ricevere messaggi di posta elettronica. Gli utenti riceveranno invece un solo messaggio di posta elettronica che li avvisa di usare Outlook come app di posta elettronica.

7. Per applicare questi criteri agli utenti, aprire il pannello **Gruppi di utenti limitati** e scegliere **Aggiungi un gruppo di utenti**. Selezionare uno o più gruppi di utenti a cui applicare questi criteri.

    ![Screenshot del pannello Gruppi di utenti limitati e opzione Aggiungi un gruppo di utenti selezionata](./media/mam-ca-add-user-group.png)

8. È possibile che alcuni utenti appartenenti al gruppo selezionato nel passaggio precedente non debbano essere interessati da questi criteri. In questi casi aggiungere il gruppo di utenti all'elenco dei gruppi esentati. Scegliere **Exempted user groups** (Gruppi di utenti esentati) dal pannello **Exchange Online**. Scegliere **Aggiungi un gruppo di utenti** per aprire l'elenco dei gruppi di utenti. Selezionare i gruppi che si vuole esentare da questi criteri.

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Per modificare o eliminare gruppi di utenti da un criterio di accesso condizionale basato su app esistente

1. Aprire il pannello **Gruppi di utenti limitati** e quindi evidenziare il gruppo di utenti che si vuole eliminare.
2. Fare clic sui puntini di sospensione per visualizzare le opzioni di eliminazione.
3. Scegliere **Elimina** per rimuovere il gruppo di utenti dall'elenco.

## <a name="next-steps"></a>Passaggi successivi
[Bloccare le app che non usano l'autenticazione moderna](app-modern-authentication-block.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](app-protection-policies.md)
