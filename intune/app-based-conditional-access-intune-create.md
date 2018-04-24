---
title: Configurare criteri di accesso condizionale basato su app con Intune
description: Informazioni su come configurare criteri di accesso condizionale basato su app con Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b7e3654021935495189b62da5257793383586137
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Configurare criteri di accesso condizionale basato su app con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo descrive come configurare criteri di accesso condizionale basato su app per le app che fanno parte dell'elenco di app approvate. L'elenco di app approvate include le applicazioni testate da Microsoft.

> [!IMPORTANT]
> Questo articolo descrive la procedura per l'aggiunta di criteri per l'accesso condizionale basato su app con Exchange Online, ma è possibile usare la stessa procedura per aggiungere altre app dall'elenco delle app approvate, come ad esempio SharePoint Online, Microsoft Teams e così via.

## <a name="to-create-an-app-based-conditional-access-policy"></a>Per creare criteri di accesso condizionale basato su app
1.  Passare al [portale di Azure](https://portal.azure.com) e accedere con le proprie credenziali.

2.  Scegliere **Tutti i servizi** e digitare "Intune".

3.  Scegliere **Protezione app di Intune**.

4.  In **Protezione app di Intune** nella sezione **Accesso condizionale** scegliere **Exchange Online**.

    ![Screenshot del riquadro delle impostazioni che include la sezione dell'accesso condizionale con l'opzione Exchange Online selezionata](./media/MAM-conditional-access-1.png)

6. Nel riquadro **App consentite** scegliere l'opzione **Consenti app che supportano i criteri app di Intune** per consentire solo alle app supportate dai criteri di protezione delle app di Intune di accedere a Exchange Online. Quando si seleziona questa opzione, viene visualizzato l'elenco delle app supportate.

    > [!NOTE]
    > Tutti i client di posta elettronica di Exchange Active Sync, tra cui i client di posta elettronica predefiniti in iOS e Android che si connettono a Exchange Online, non possono inviare né ricevere messaggi di posta elettronica. Gli utenti riceveranno invece un solo messaggio di posta elettronica che li avvisa di usare Outlook come app di posta elettronica.

7. Per applicare questi criteri agli utenti, aprire il riquadro **Gruppi di utenti limitati** e scegliere **Aggiungi un gruppo di utenti**. Selezionare uno o più gruppi di utenti a cui applicare questi criteri.

    ![Screenshot del riquadro Gruppi di utenti limitati e opzione Aggiungi un gruppo di utenti selezionata](./media/mam-ca-add-user-group.png)

8. È possibile che alcuni utenti appartenenti al gruppo selezionato nel passaggio precedente non debbano essere interessati da questi criteri. In questi casi aggiungere il gruppo di utenti all'elenco dei gruppi esentati. Dal riquadro **Exchange Online** scegliere **Exempted user groups** (Gruppi di utenti esentati). Scegliere **Aggiungi un gruppo di utenti** per aprire l'elenco dei gruppi di utenti. Selezionare i gruppi che si vuole esentare da questi criteri.

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Per modificare o eliminare gruppi di utenti da un criterio di accesso condizionale basato su app esistente

1. Aprire il pannello **Gruppi di utenti limitati** ed evidenziare il gruppo di utenti che si vuole eliminare.
2. Fare clic sui puntini di sospensione per visualizzare le opzioni di eliminazione.
3. Scegliere **Elimina** per rimuovere il gruppo di utenti dall'elenco.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Creare criteri di accesso condizionale basato su app in un carico di lavoro di Azure AD

A partire dalla versione 1708 di Intune, gli amministratori IT possono creare criteri di accesso condizionale basato su app dal carico di lavoro di Azure AD. Questo approccio è molto comodo, perché evita di doversi spostare tra i carichi di lavoro di Azure e Intune.

> [!IMPORTANT]
> È necessario avere una licenza di Azure AD Premium per creare criteri di accesso condizionale di Azure AD dal portale di Intune di Azure.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Per creare criteri di accesso condizionale basato su app

> [!IMPORTANT]
> Per potere usare i criteri di accesso condizionale basato su app, è prima di tutto necessario che i [criteri di protezione delle app di Intune](app-protection-policies.md) siano applicati alle app.

1. Nel **dashboard di Intune** scegliere **Accesso condizionale**.

2. Nel pannello **Criteri** scegliere **Nuovi criteri** per creare i nuovi criteri di accesso condizionale basato su app.

4. Dopo avere immesso un nome di criterio e dopo avere configurato le impostazioni disponibili nella sezione **Assegnazioni**, scegliere **Concedi** nella sezione **Controlli di accesso**.

5. Scegliere **Richiedi app client approvata**, quindi **Seleziona** e infine **OK** per salvare il nuovo criterio.

## <a name="next-steps"></a>Passaggi successivi
[Bloccare le app che non usano l'autenticazione moderna](app-modern-authentication-block.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app con i criteri di protezione delle app](app-protection-policies.md)
[Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
