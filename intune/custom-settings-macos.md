---
title: Aggiungere impostazioni personalizzate per dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Esportare le impostazioni macOS da Apple Configurator o Apple Profile Manager e quindi importarle in Microsoft Intune. Queste impostazioni possono creare, usare e controllare le impostazioni personalizzate e le funzionalità nei dispositivi macOS. Il profilo personalizzato può essere quindi assegnato o distribuito nei dispositivi macOS nell'organizzazione per creare una baseline o uno standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3bb4691ff46b4d28254d11fb94fa5b2fbcffaa6f
ms.sourcegitcommit: c969b596ec0fec227484c50f210ba4e159e2e533
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49983177"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Usare le impostazioni personalizzate per i dispositivi macOS in Microsoft Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi macOS usando un "profilo personalizzato". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

Quando si usano dispositivi macOS, è possibile ottenere le impostazioni personalizzate in Intune in due modi:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

È possibile usare questi strumenti per esportare le impostazioni in un profilo di configurazione. In Intune si importa il file e quindi si assegna il profilo agli utenti e ai dispositivi macOS. Dopo l'assegnazione, vengono distribuite le impostazioni e viene anche creata una baseline o uno standard per macOS nell'organizzazione.

Questo articolo descrive come creare un profilo personalizzato per i dispositivi macOS. L'articolo offre anche materiale sussidiario sull'uso di Apple Configurator e Apple Profile Manager.

## <a name="before-you-begin"></a>Prima di iniziare

- Quando si usa **Apple Configurator** per creare il profilo di configurazione, assicurarsi che le impostazioni esportate siano compatibili con la versione di macOS nei dispositivi in uso. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

- Quando si usa **Apple Profile Manager**, assicurarsi di:

  - Abilitare la [gestione di dispositivi mobili](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) in Profile Manager.
  - Aggiungere i [dispositivi macOS](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) in Profile Manager.
  - Dopo aver aggiunto un dispositivo in Profile Manager, passare a **Under the Library** (Nella libreria)  > **Devices** (Dispositivi) > selezionare il dispositivo > **Settings** (Impostazioni). Specificare le impostazioni generali, di sicurezza, privacy, directory, e certificato per il dispositivo.

    Scaricare e salvare il file. Il file verrà inserito nel profilo di Intune. 

  - Assicurarsi che le impostazioni esportate da Apple Profile Manager siano compatibili con la versione di macOS nei dispositivi in uso. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `macos custom profile`.
    - **Descrizione:** immettere una descrizione per il profilo.
    - **Piattaforma**: scegliere **macOS**.
    - **Tipo di profilo**: scegliere **Personalizzato**.

4. In **Configurazione personalizzata** immettere le impostazioni seguenti:

    - **Nome del profilo di configurazione personalizzato**: immettere un nome per i criteri. Questo nome viene visualizzato nel dispositivo e nello stato di Intune.
    - **File del profilo di configurazione**: passare al profilo di configurazione creato usando Apple Configurator o Apple Profile Manager. Il file importato è visualizzato nell'area **Contenuti del file**.

5. Selezionare **OK** > **Crea** per creare il profilo di Intune. Il profilo viene visualizzato nell'elenco **Configurazione del dispositivo - Profili**.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. È ora necessario [assegnare il profilo](device-profile-assign.md).

Vedere come [creare il profilo nei dispositivi iOS](custom-settings-ios.md).