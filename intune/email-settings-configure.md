---
title: Come configurare le impostazioni di posta elettronica di Microsoft Intune
titleSuffix: ''
description: Informazioni su come configurare Microsoft Intune per creare connessioni alla posta elettronica aziendale nei dispositivi gestiti.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f51854bfb198ca65cc5fc82bad0e3b3befbb173a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Come configurare le impostazioni di posta elettronica in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile usare i profili di posta elettronica per configurare i dispositivi gestiti con le impostazioni necessarie per connettersi e sincronizzarsi con la posta elettronica aziendale. Ciò consente di garantire che le impostazioni siano standard in tutti i dispositivi e anche di ridurre le chiamate al servizio di supporto da parte di utenti finali che non conoscono le impostazioni di posta elettronica corrette.

Il client di posta elettronica predefinito è supportato per la maggior parte delle piattaforme. Molte applicazioni di posta elettronica di terze parti non sono attualmente supportate.

È possibile usare i profili di posta elettronica per configurare il client di posta elettronica nativo nei tipi di dispositivi seguenti:

- Android Samsung Knox Standard 4.0 e versioni successive
- Android for Work
- iOS 8.0 e versioni successive
- Windows Phone 8.1 e versioni successive
- Windows 10 (Desktop) e Windows 10 Mobile

Usare le informazioni in questo articolo per apprendere le nozioni di base sulla configurazione di un profilo di posta elettronica e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-email-settings"></a>Creare un profilo dispositivo contenente le impostazioni di posta elettronica

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
3. Nel riquadro dei profili scegliere **Crea profilo**.
4. Nel riquadro **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di posta elettronica.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni di posta elettronica. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni del dispositivo di posta elettronica:
    - **Android** (solo Samsung Android Knox Standard)
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Posta elettronica**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android for Work e Samsung Knox Standard](email-settings-android.md)
    - [Impostazioni iOS](email-settings-ios.md)
    - [Impostazioni Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Impostazioni Windows 10](email-settings-windows-10.md)
8. Al termine tornare al riquadro **Crea profilo** e scegliere **Crea**.

Il profilo verrà creato e visualizzato nel riquadro dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).

## <a name="further-information"></a>Altre informazioni

### <a name="remove-an-email-profile"></a>Rimuovere un profilo di posta elettronica

Per rimuovere un profilo di posta elettronica da un dispositivo, modificare l'assegnazione e rimuovere tutti i gruppi di cui il dispositivo è membro. Non è possibile rimuovere un profilo di posta elettronica in questo modo se questo è l'unico profilo presente su un dispositivo.

### <a name="securing-email-access"></a>Proteggere l'accesso alla posta elettronica

È possibile proteggere i profili di posta elettronica usando uno dei due metodi seguenti:

1. **Certificati**: quando si crea il profilo di posta elettronica, si sceglie un profilo di certificato creato in precedenza in Intune. Questo profilo, noto come certificato di identità, viene usato per eseguire l'autenticazione in base a un profilo di certificato attendibile (o certificato radice) per stabilire se il dispositivo dell'utente è autorizzato alla connessione. Il certificato attendibile viene assegnato al computer che autentica la connessione alla posta elettronica che è in genere il server di posta elettronica nativo.
Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Intune](certificates-configure.md).
2. **Nome utente e password**: l'utente esegue l'autenticazione al server di posta elettronica nativo specificando nome utente e password.
Poiché la password non è contenuta nel profilo di posta elettronica, l'utente deve specificarla quando si connette alla posta elettronica.


### <a name="how-intune-handles-existing-email-accounts"></a>In che modo Intune gestisce gli account di posta elettronica esistenti

Se l'utente ha già configurato un account di posta elettronica, il risultato dell'assegnazione del profilo di posta elettronica di Intune varierà a seconda della piattaforma del dispositivo:

- **iOS:** un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Il profilo di posta elettronica duplicato blocca l'assegnazione di un profilo di Intune. In questo caso il portale aziendale comunica all'utente che esiste un problema di conformità e richiede quindi di rimuovere il profilo. Per evitare il problema, indicare agli utenti di eseguire la registrazione prima di installare un profilo di posta elettronica e di consentire a Intune di impostarlo.
- **Windows:** un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente.
- **Android Samsung Knox Standard**: un profilo di posta elettronica esistente duplicato viene individuato sulla base dell'indirizzo di posta elettronica e viene sovrascritto con il profilo di Intune.
Poiché Android non usa il nome host per identificare il profilo, si consiglia di non creare diversi profili di posta elettronica da usare con lo stesso indirizzo di posta elettronica su host diversi perché tali profili si sovrascrivono a vicenda.
- **Android for Work** Intune offre due profili di posta elettronica Android for Work, uno per Gmail e uno per Nine Work. Queste app sono disponibili in Google Play Store e vengono installate nel profilo di lavoro del dispositivo, quindi possono subentrare profili duplicati. Entrambe le app supportano le connessioni a Exchange. Per abilitare la connettività della posta elettronica, distribuire una di queste app nei dispositivi dell'utente. In seguito creare e distribuire il profilo di posta elettronica corrispondente. Le app di posta elettronica, ad esempio Nine Work, potrebbero non essere gratuite. Rivedere i dettagli relativi alla licenza dell'app o contattare l'azienda produttrice per richiedere informazioni.

### <a name="update-an-email-profile"></a>Aggiornare un profilo di posta elettronica

Se si apportano modifiche a un profilo di posta elettronica assegnato in precedenza, è possibile che un messaggio richieda agli utenti finali di approvare la riconfigurazione delle impostazioni di posta elettronica.
