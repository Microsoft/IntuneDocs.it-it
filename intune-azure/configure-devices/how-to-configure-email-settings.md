---
title: Come configurare le impostazioni di posta elettronica di Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come configurare Intune per creare connessioni alla posta elettronica aziendale nei dispositivi gestiti.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 484bd9b0-fbf1-4f4f-940c-6b12fa07e228
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: f316b332c3f1b80b9d6af488943298fcfea13741
ms.openlocfilehash: 70d013768c07f1782255a309b5941f05c2222912
ms.lasthandoff: 03/30/2017


---

# <a name="how-to-configure-email-settings-in-microsoft-intune"></a>Come configurare le impostazioni di posta elettronica in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

È possibile usare i profili di posta elettronica per configurare i dispositivi gestiti con le impostazioni necessarie per connettersi e sincronizzarsi con la posta elettronica aziendale. Ciò consente di garantire che le impostazioni siano standard in tutti i dispositivi e anche di ridurre le chiamate al servizio di supporto da parte di utenti finali che non conoscono le impostazioni di posta elettronica corrette.

Il client di posta elettronica predefinito è supportato per la maggior parte delle piattaforme. Molte applicazioni di posta elettronica di terze parti non sono attualmente supportate.

È possibile usare i profili di posta elettronica per configurare il client di posta elettronica nativo nei tipi di dispositivi seguenti:

- Android Samsung KNOX Standard 4.0 e versioni successive
- Android for Work
- iOS 8.0 e versioni successive
- Windows Phone 8.1 e versioni successive
- Windows 10 (Desktop) e Windows 10 Mobile

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione di un profilo di posta elettronica e quindi leggere argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-email-settings"></a>Creare un profilo dispositivo contenente le impostazioni di posta elettronica

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di posta elettronica.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni di posta elettronica. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni del dispositivo di posta elettronica:
    - **Android**
    - **iOS**
    - **Windows Phone 8.1**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Posta elettronica**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android](email-profile-settings-for-android.md)
    - [Impostazioni iOS](email-profile-settings-for-ios.md)
    - [Impostazioni Windows Phone 8.1](email-profile-settings-for-windows-phone-8-1.md)
    - [Impostazioni Windows 10](email-profile-settings-for-windows-10.md)
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md).

## <a name="further-information"></a>Altre informazioni

### <a name="remove-an-email-profile"></a>Rimuovere un profilo di posta elettronica

Per rimuovere un profilo di posta elettronica da un dispositivo, modificare l'assegnazione e rimuovere tutti i gruppi di cui il dispositivo è membro. Si noti che non è possibile rimuovere un profilo di posta elettronica in questo modo se questo è l'unico profilo presente su un dispositivo.

### <a name="securing-email-access"></a>Proteggere l'accesso alla posta elettronica

È possibile proteggere i profili di posta elettronica usando uno dei due metodi seguenti:

1. **Certificati**: quando si crea il profilo di posta elettronica, si sceglie un profilo di certificato creato in precedenza in Intune. Questo profilo, noto come certificato di identità, viene usato per eseguire l'autenticazione in base a un profilo di certificato attendibile (o certificato radice) per stabilire se il dispositivo dell'utente è autorizzato alla connessione. Il certificato attendibile viene distribuito al computer che autentica la connessione alla posta elettronica che è in genere il server di posta elettronica nativo.
Per altre informazioni su come creare e usare i profili di certificato in Intune, vedere [Come configurare i certificati con Intune](/intune-azure/configure-devices/how-to-configure-certificates).
2. **Nome utente e password**: l'utente esegue l'autenticazione al server di posta elettronica nativo specificando nome utente e password.
Poiché la password non è contenuta nel profilo di posta elettronica, l'utente deve specificarla quando si connette alla posta elettronica.


### <a name="how-intune-handles-existing-email-accounts"></a>In che modo Intune gestisce gli account di posta elettronica esistenti

Se l'utente ha già configurato un account di posta elettronica, il risultato dell'assegnazione del profilo di posta elettronica di Intune varierà a seconda della piattaforma del dispositivo:

- **iOS:** un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Il profilo di posta elettronica duplicato blocca l'assegnazione di un profilo di Intune. In questo caso il portale aziendale comunica all'utente che esiste un problema di conformità e richiede quindi di rimuovere il profilo. Per evitare il problema, indicare agli utenti di eseguire la registrazione prima di installare un profilo di posta elettronica e di consentire a Intune di impostarlo.
- **Windows:** un profilo di posta elettronica esistente duplicato viene individuato in base al nome host e all'indirizzo di posta elettronica. Intune sovrascrive il profilo di posta elettronica esistente creato dall'utente.
- **Android** un profilo di posta elettronica esistente duplicato viene individuato sulla base dell'indirizzo di posta elettronica e viene sovrascritto con il profilo di Intune.
Poiché Android non usa il nome host per identificare il profilo, si consiglia di non creare diversi profili di posta elettronica da usare con lo stesso indirizzo di posta elettronica su host diversi perché tali profili si sovrascrivono a vicenda.

