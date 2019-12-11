---
title: Aggiungere impostazioni personalizzate per dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Esportare le impostazioni macOS da Apple Configurator o Apple Profile Manager e quindi importarle in Microsoft Intune. Queste impostazioni possono creare, usare e controllare le funzionalità e le impostazioni personalizzate nei dispositivi macOS. Il profilo personalizzato può essere quindi assegnato o distribuito nei dispositivi macOS nell'organizzazione per creare una baseline o uno standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c24c120b033a4db0162e985ef185932dd931eda
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506915"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Usare le impostazioni personalizzate per i dispositivi macOS in Microsoft Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi macOS usando un "profilo personalizzato". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

Quando si usano dispositivi macOS, è possibile ottenere le impostazioni personalizzate in Intune in due modi:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

È possibile usare questi strumenti per esportare le impostazioni in un profilo di configurazione. In Intune si importa il file e quindi si assegna il profilo agli utenti e ai dispositivi macOS. Una volta assegnate, le impostazioni vengono distribuite. Creano anche una linea di base o standard per macOS nell'organizzazione.

Questo articolo fornisce indicazioni sull'uso di Apple Configurator e Apple Profile Manager e descrive le proprietà che è possibile configurare.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare il profilo](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Informazioni importanti

- Quando si usa **Apple Configurator** per creare il profilo di configurazione, assicurarsi che le impostazioni esportate siano compatibili con la versione di macOS nei dispositivi. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

- Quando si usa **Apple Profile Manager**, assicurarsi di:

  - Abilitare la [gestione di dispositivi mobili](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) in Profile Manager.
  - Aggiungere i [dispositivi macOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) in Profile Manager.
  - Dopo aver aggiunto un dispositivo in Profile Manager, passare a **Under the Library** (Nella libreria)  > **Devices** (Dispositivi) > selezionare il dispositivo > **Settings** (Impostazioni). Specificare le impostazioni generali, di sicurezza, privacy, directory, e certificato per il dispositivo.

    Scaricare e salvare il file. Il file verrà inserito nel profilo di Intune. 

  - Assicurarsi che le impostazioni esportate da Apple Profile Manager siano compatibili con la versione di macOS nei dispositivi. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

## <a name="custom-configuration-profile-settings"></a>Impostazioni del profilo di configurazione personalizzato

- **Nome del profilo di configurazione personalizzato**: immettere un nome per i criteri. Questo nome viene visualizzato nel dispositivo e nello stato di Intune.
- **File del profilo di configurazione**: passare al profilo di configurazione creato usando Apple Configurator o Apple Profile Manager. Il file importato è visualizzato nell'area **Contenuti del file**.

  È anche possibile aggiungere token di dispositivo ai file di `.mobileconfig`. I token del dispositivo vengono usati per aggiungere informazioni specifiche del dispositivo. Per visualizzare, ad esempio, il numero di serie, immettere `{{serialnumber}}`. Nel dispositivo il testo è simile a `123456789ABC`, che è univoco per ogni dispositivo. Quando si immettono le variabili, assicurarsi di usare le parentesi graffe `{{ }}`. I [token di configurazione delle app](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) includono un elenco delle variabili che è possibile usare. È anche possibile usare `deviceid` o qualsiasi altro valore specifico del dispositivo.

  > [!NOTE]
  > Le variabili non vengono convalidate nell'interfaccia utente e fanno distinzione tra maiuscole e minuscole. Di conseguenza possono essere visualizzati dei profili salvati con input non corretto. Ad esempio, se si immette `{{DeviceID}}` invece di `{{deviceid}}`, viene visualizzata la stringa letterale anziché l'ID univoco del dispositivo. Assicurarsi di immettere le informazioni corrette.

Selezionare **OK** > **Crea** per salvare le modifiche. Il profilo verrà creato e visualizzato nell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. È ora necessario [assegnare il profilo](device-profile-assign.md).

Vedere come [creare il profilo nei dispositivi iOS](../custom-settings-ios.md).
