---
title: Aggiungere le impostazioni di file delle preferenze per dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere un file XML o plist che includa le informazioni chiave sull'app. Usare un profilo di configurazione del dispositivo file preferenziale per modificare le informazioni sulla chiave nel file di elenco delle proprietà e assegnarlo ai dispositivi macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acad2e8539da7210c349ffb254af62f370af5f6
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391498"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Aggiungere un file elenco di proprietà ai dispositivi macOS usando Microsoft Intune

Con Microsoft Intune è possibile aggiungere un file di elenco di proprietà (con estensione plist) per i dispositivi macOS o le app nei dispositivi macOS.

Questa funzionalità si applica a:

- dispositivi macOS che eseguono 10,7 e versioni successive

I file dell'elenco di proprietà includono in genere informazioni sulle applicazioni macOS. Per ulteriori informazioni, vedere [About Information Property List files](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (sito Web di Apple) e [impostazioni del payload personalizzate](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

Questo articolo elenca e descrive le diverse impostazioni del file dell'elenco di proprietà che è possibile aggiungere ai dispositivi macOS. Come parte della soluzione di gestione dei dispositivi mobili (MDM), usare queste impostazioni per aggiungere l'ID bundle dell'app (`com.company.application`) e aggiungere il file con estensione plist.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi macOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare il profilo](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Informazioni importanti

- Queste impostazioni non vengono convalidate. Assicurarsi di testare le modifiche prima di assegnare il profilo ai dispositivi.
- Se non si è certi di come immettere una chiave dell'app, modificare l'impostazione all'interno dell'app. Esaminare quindi il file delle preferenze dell'app usando [Xcode](https://developer.apple.com/xcode/) per vedere come è configurata l'impostazione. Apple consiglia di rimuovere le impostazioni non gestibili usando Xcode prima di importare il file.
- Solo alcune app funzionano con le preferenze gestite e potrebbero non consentire la gestione di tutte le impostazioni.
- Assicurarsi di caricare i file dell'elenco di proprietà che hanno come destinazione le impostazioni del canale del dispositivo, non le impostazioni del canale utente. I file dell'elenco delle proprietà sono destinati all'intero dispositivo.

## <a name="preference-file"></a>File delle preferenze

- **Nome di dominio preferenza**: i file di elenco delle proprietà vengono in genere usati per i Web browser (Microsoft Edge), [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)e le app personalizzate. Quando si crea un dominio di preferenza, viene creato anche un ID bundle. Immettere l'ID bundle, ad esempio `com.company.application`. Ad esempio, immettere `com.Contoso.applicationName`, `com.Microsoft.Edge` o `com.microsoft.wdav`.
- **File elenco proprietà**: selezionare il file dell'elenco di proprietà associato all'app. Assicurarsi che sia un file `.plist` o `.xml`. Ad esempio, caricare un file di `YourApp-Manifest.plist` o `YourApp-Manifest.xml`.
- **Contenuto del file**: vengono visualizzate le informazioni sulla chiave nel file dell'elenco delle proprietà. Se è necessario modificare le informazioni sulla chiave, aprire il file dell'elenco in un altro editor e quindi caricare nuovamente il file in Intune.

Selezionare **OK** > **Crea** per salvare le modifiche. Il profilo verrà creato e visualizzato nell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
