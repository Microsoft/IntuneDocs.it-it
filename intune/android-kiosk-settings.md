---
title: Impostazioni della modalità tutto schermo per Android in Microsoft Intune - Azure | Microsoft Docs
description: Configurare i dispositivi in modalità tutto schermo Android come singole app o più app in modalità tutto schermo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 9/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b2a31a90dc0d88386a829756116edebd28990f9
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602181"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Impostazioni della modalità tutto schermo per dispositivi Android in Intune

È possibile configurare un dispositivo come un'app singola o più app in modalità tutto schermo usando le impostazioni di configurazione del dispositivo. Quando un dispositivo è in modalità tutto schermo, l'uso del dispositivo è limitato alle app o ai collegamenti Web definiti dal profilo di restrizione. 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Limitare un dispositivo in modalità tutto schermo Android a un'app singola

Se il profilo di restrizione di un dispositivo in modalità tutto schermo è impostato su **Modalità tutto schermo** = **app singola in modalità tutto schermo**, gli utenti posso accedere solo a un'app singola. All'avvio di un dispositivo configurato in questa modalità, viene avviata l'app specifica. Gli utenti non possono aprire nuove app o modificare l'app in esecuzione.

1. Assicurarsi che l'app che si vuole aggiungere al dispositivo in modalità tutto schermo sia [distribuita nel dispositivo](apps-deploy.md) e assegnata al gruppo di dispositivi creato per i dispositivi in modalità tutto schermo.
2. Passare al [portale di Intune](https://portal.azure.com) e scegliere **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Nel pannello **Crea profilo** impostare i campi seguenti:
     - **Nome**
     - **Piattaforma**: Android Enterprise
     - **Tipo di profilo**: Proprietario dispositivo > Limitazioni del dispositivo
4. Scegliere **Impostazioni** > **Modalità tutto schermo**.
5. Per **Modalità tutto schermo**, scegliere **Single app kiosk** (App singola in modalità tutto schermo).
6. Scegliere **Selezionare un'app gestita** e quindi selezionare l'app Google Play gestita che si vuole impostare come unica app disponibile per i dispositivi che usano questo profilo.
7. Scegliere **OK** > **OK** > **OK** > **Crea**.
8. Scegliere il profilo appena creato > **Assegnazioni**.
9. In **Assegna a** scegliere **Gruppi selezionati**.
10. Scegliere **Selezionare i gruppi da includere** > scegliere il gruppo di dispositivi creato per i dispositivi in modalità tutto schermo > **Seleziona**.

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>Limitare un dispositivo in modalità tutto schermo a un set di app o collegamenti Web

Se il profilo di restrizione di un dispositivo in modalità tutto schermo è impostato su **Modalità tutto schermo** = **più app in modalità tutto schermo**, gli utenti possono accedere solo al numero limitato di app configurato. È anche possibile definire un set di collegamenti Web che gli utenti possono visitare. Quando viene applicato il criterio, gli utenti visualizzano le icone delle app consentite nella schermata iniziale.

Per impostare un dispositivo in modalità tutto schermo Android per più app, eseguire i passaggi principali seguenti:

1. [Importare e distribuire l'app di schermata iniziale gestita da Google Play gestito](#import-and -deploy-the-managed-home-screen-app)
2. [Aggiungere e assegnare le app che possono essere usate in modalità tutto schermo](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (Facoltativo) [Aggiungere collegamenti Web che possono essere usati in modalità tutto schermo](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deploy-the-managed-home-screen-app"></a>Importare e distribuire l'app di schermata iniziale gestita

1. Passare alla [pagina della schermata iniziale gestita in Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) e accedere con lo stesso account usato per le altre app Google Play gestite.
2. Scegliere **Approva**.
3. Passare al [portale di Intune](https://portal.azure.com) e scegliere **App client** > **Google Play gestito** > **Sincronizza**.
4. Scegliere **App** > **Schermata iniziale gestita** > **Assegnazioni** > **Aggiungi gruppo**.
5. In **Tipo di assegnazione** scegliere **Obbligatorio**.
6. Scegliere **Gruppi inclusi** > **Selezionare i gruppi da includere** > scegliere il gruppo di dispositivi creato per i dispositivi in modalità tutto schermo > **Seleziona** > **OK** > **OK** > **Salva**.

> [!NOTE]
> Quando si aggiunge l'app di schermata iniziale gestita al profilo più app in modalità tutto schermo, viene aggiunta un'icona. Tuttavia, quando si seleziona l'icona non accade nulla. Di conseguenza, non si deve aggiungere l'app di schermata iniziale gestita al profilo più app in modalità tutto schermo.

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>Aggiungere e assegnare le app che possono essere usate in modalità tutto schermo

Per ogni app che si vuole rendere disponibile nei dispositivi in modalità tutto schermo, seguire questa procedura:

1. [Aggiungere l'app in Intune](store-apps-android.md).
2. Scegliere **App client** > **App** > scegliere l'app > **Assegnazioni** > **Aggiungi gruppo**.
3. In **Tipo di assegnazione** scegliere **Obbligatorio**.
4. Scegliere **Gruppi inclusi** > **Selezionare i gruppi da includere** > scegliere il gruppo di dispositivi creato per i dispositivi in modalità tutto schermo > **Seleziona** > **OK** > **OK** > **Salva**.

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>Aggiungere collegamenti Web che possono essere usati in modalità tutto schermo

1. Passare al [portale di Intune](https://portal.azure.com) e scegliere **App client** > **App** > **Aggiungi**.
2. In **Tipo di app** scegliere **Collegamento Web**.
3. Scegliere **Configura** e specificare le informazioni richieste. Non è necessario aggiungere un'immagine del logo poiché verrà recuperata automaticamente dal file favicon.ico del sito Web.
4. Scegliere **OK** > **Aggiungi**.

Assicurarsi di avere distribuito un'app Web ai dispositivi in modalità tutto schermo. Per altre informazioni, vedere [Aggiungere app Web a Microsoft Intune](web-app.md).

### <a name="create-a-multi-app-kiosk-profile"></a>Creare un profilo di più app in modalità tutto schermo

1. Passare al [portale di Intune](https://portal.azure.com) e scegliere **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Nel pannello **Crea profilo** impostare i campi seguenti:
     - **Nome**: digitare un nome intuitivo
     - **Piattaforma**: Android Enterprise
     - **Tipo di profilo**: Proprietario dispositivo > Limitazioni del dispositivo
4. Scegliere **Impostazioni** > **Modalità tutto schermo**.
5. Per **Modalità tutto schermo**, scegliere **Più app in modalità tutto schermo**.
6. Scegliere **Aggiungi** e quindi selezionare le app o i collegamenti Web che si vuole rendere disponibili per i dispositivi che usano questo profilo.
7. Scegliere **OK** > **OK** > **OK** > **Crea**.
8. Scegliere il profilo appena creato > **Assegnazioni**.
9. In **Assegna a** scegliere **Gruppi selezionati**.
10. Scegliere **Selezionare i gruppi da includere** > scegliere il gruppo di dispositivi creato per i dispositivi in modalità tutto schermo > **Seleziona** > **Salva**.

## <a name="next-steps"></a>Passaggi successivi
[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
