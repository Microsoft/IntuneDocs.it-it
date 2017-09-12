---
title: Reimpostare il passcode nei dispositivi Windows con Intune
titlesuffix: Azure portal
description: Informazioni su come usare Intune per reimpostare il passcode nei dispositivi Windows integrati con il servizio di reimpostazione PIN.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0c00d52f3ed06e1810d8b537c2232221ac8f53bd
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="reset-the-passcode-on-windows-devices-integrated-with-the-microsoft-pin-reset-service-using-intune"></a>Reimpostare il passcode nei dispositivi Windows integrati con il servizio di reimpostazione PIN tramite Intune

La funzionalità di reimpostazione del passcode per i dispositivi Windows si integra con il servizio di reimpostazione PIN per consentire di generare un nuovo passcode per i dispositivi che eseguono Windows 10 Mobile. I dispositivi devono eseguire Windows 10 Creators Update o versioni successive.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità supportata in Windows 10 Creators Update e versioni successive (aggiunto ad Azure AD)
- Windows Phone: funzionalità non supportata
- iOS: funzionalità non supportata
- macOS: funzionalità non supportata
- Android: funzionalità non supportata


## <a name="before-you-start"></a>Prima di iniziare

Prima che si possa reimpostare in modalità remota il passcode nei dispositivi Windows che è possibile gestire, è necessario caricare il servizio di reimpostazione PIN del tenant di Intune e configurare i dispositivi gestiti. Seguire queste istruzioni per ottenere tale configurazione:

### <a name="connect-intune-with-the-pin-reset-service"></a>Connettere Intune con il servizio di reimpostazione PIN

1. Visitare [il sito Web sull'integrazione del servizio di reimpostazione PIN](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) e accedere usando l'account di amministratore tenant usato per gestire il tenant di Intune.
2. Dopo l'accesso, fare clic su **Accetta** per consentire al servizio di reimpostazione PIN di accedere all'account.<br>
![Pagina autorizzazioni del servizio di reimpostazione PIN](./media/pin-reset-service-application.png)
3. Nel portale di Azure, è possibile verificare che Intune e il servizio di reimpostazione PIN sono stati integrati dal pannello Enterprise applications - All applications (Applicazioni Enterprise - Tutte le applicazioni) come illustrato di seguito:<br>
![Applicazione del servizio di reimpostazione PIN in Azure](./media/pin-reset-service-home-screen.png)
4. Accedere a [questo sito Web](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) usando le credenziali amministratore tenant di Intune e scegliere nuovamente **Accetta** per consentire al servizio di accedere all'account.

### <a name="configure-windows-devices-to-use-pin-reset"></a>Configurare i dispositivi Windows per usare la reimpostazione PIN

Per configurare la reimpostazione PIN nei dispositivi Windows gestiti, usare i [criteri di dispositivo personalizzato per Windows 10 in Intune](custom-settings-windows-10.md) per abilitare la funzionalità. Configurare i criteri usando il provider del servizio di configurazione (CSP) dei criteri di Windows seguente:


- **Per i dispositivi** - **./Device/Vendor/MSFT/PassportForWork/*ID tenant*/Policies/EnablePinRecovery**

*ID tenant* fa riferimento all'ID di directory di Azure Active Directory che è possibile ottenere dalla pagina **Proprietà** di Azure Active Directory.

Impostare il valore per questo CSP su **True**.

## <a name="steps-to-reset-the-passcode"></a>Passaggi per reimpostare il passcode

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi** scegliere **Gestisci** > **Tutti i dispositivi**.
5. Selezionare il dispositivo per il quale si vuole reimpostare il passcode e quindi nel pannello delle proprietà del dispositivo, scegliere **Nuovo passcode**.
6. Nel messaggio di conferma visualizzato scegliere **Sì**. Il passcode viene generato e visualizzato nel portale per sette giorni successivi.

## <a name="next-steps"></a>Passaggi successivi

Se la reimpostazione del passcode ha esito negativo, viene visualizzato un collegamento nel portale per ottenere altre informazioni.


