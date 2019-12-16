---
title: Reimpostare il passcode nei dispositivi Windows con Microsoft Intune - Azure | Microsoft Docs
description: Per reimpostare il passcode nei dispositivi Windows, installare il servizio di reimpostazione PIN Microsoft e il client di reimpostazione PIN Microsoft, creare i criteri dei dispositivi tramite l'ID directory di Azure Active Directory e reimpostare il passcode nel portale di Azure usando Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b643ed41d01b70376dac32c26a66dcf9f9735ceb
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907220"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Reimpostare il passcode nei dispositivi Windows con Intune

È possibile reimpostare il passcode per i dispositivi Windows. La funzionalità di reimpostazione del passcode usa il servizio di reimpostazione PIN Microsoft per generare un nuovo passcode per i dispositivi che eseguono Windows 10 Mobile. 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows 10 Mobile con Creators Update in esecuzione e versioni successive (aggiunto ad Azure AD).

**Non** sono supportate le piattaforme seguenti:
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>Autorizzare i servizi di reimpostazione PIN

Per reimpostare il passcode nei dispositivi Windows, caricare il servizio di reimpostazione PIN servizio nel tenant di Intune.

1. Passare a [Microsoft Pin Reset Service Production](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) e accedere usando l'account amministratore del tenant.
2. Fare clic su **Accetta** per consentire al servizio di reimpostazione PIN di accedere all'account: ![Accettare la richiesta di autorizzazioni del server di reimpostazione PIN](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. Passare a [Microsoft Pin Reset Client Production](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) e accedere usando l'account amministratore del tenant. **Accetta** consente al client di reimpostazione PIN di accedere all'account.
4. Nel [portale di Azure](https://portal.azure.com) verificare che i servizi di reimpostazione PIN siano elencati in Applicazioni aziendali (Tutte le applicazioni): ![Pagina autorizzazioni del servizio di reimpostazione PIN](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> Dopo aver accettato le richieste di reimpostazione PIN, può essere visualizzato un messaggio `Page not found` oppure può sembrare che nessuna operazione sia stata eseguita. Si tratta di un comportamento normale. Controllare che le due applicazioni di reimpostazione PIN siano elencate per il tenant.

## <a name="configure-windows-devices-to-use-pin-reset"></a>Configurare i dispositivi Windows per usare la reimpostazione PIN

Per configurare la reimpostazione PIN nei dispositivi Windows gestiti, usare i [criteri dei dispositivi personalizzati per Windows 10 in Intune](../configuration/custom-settings-windows-10.md). Configurare i criteri usando il provider del servizio di configurazione (CSP) dei criteri di Windows seguente:

**Usare i criteri dei dispositivi** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

Sostituire *ID tenant* con l'ID directory di Azure AD elencato in **Proprietà** di Azure Active Directory nel [portale di Azure](https://portal.azure.com).

Impostare il valore per questo CSP su **True**.

> [!TIP]
> Dopo aver creato i criteri, assegnare (o distribuire) i criteri a un gruppo. I criteri possono essere assegnati a gruppi di utenti o a gruppi di dispositivi. Se vengono assegnati a un gruppo di utenti, è possibile che nel gruppo siano inclusi utenti con altri dispositivi, ad esempio IOS. Tecnicamente, i criteri non vengono applicabili. Questi dispositivi sono comunque inclusi nei dettagli relativi allo stato.

## <a name="reset-the-passcode"></a>Reimpostare il passcode

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). 
2. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
3. Selezionare il dispositivo per il quale si vuole reimpostare il passcode. Nelle proprietà del dispositivo selezionare **Reimposta passcode**.
4. Selezionare **Sì** per confermare. Il passcode viene generato e visualizzato nel portale per sette giorni successivi.

## <a name="next-step"></a>Passaggio successivo

Se la reimpostazione del passcode ha esito negativo, viene visualizzato un collegamento nel portale per ottenere altre informazioni dettagliate.
