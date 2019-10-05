---
title: Aggiungere impostazioni personalizzate ai dispositivi Android in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo personalizzato per dispositivi Android per creare un profilo Wi-Fi con una chiave precondivisa, creare un profilo VPN per app o consentire e bloccare app per dispositivi Samsung Knox Standard in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6150359843e5e089226717dd07f3d932ab21f6d6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735103"
---
# <a name="use-custom-settings-for-android-devices-in-microsoft-intune"></a>Usare le impostazioni personalizzate per i dispositivi Android in Microsoft Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi Android usando un "profilo personalizzato". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

I profili personalizzati Android usano impostazioni Open Mobile Alliance Uniform Resource Identifier (URI-OMA) per configurare funzionalità diverse nei dispositivi Android. Queste impostazioni vengono in genere usate dai produttori di dispositivi mobili per controllare le funzionalità.

L'uso di un profilo personalizzato consente di configurare e assegnare le impostazioni Android seguenti. Le impostazioni seguenti non sono predefinite in Intune:

- [Creare un profilo Wi-Fi con una chiave precondivisa](/intune/wi-fi-profile-shared-key)
- [Creare un profilo VPN per ogni app](/intune/android-pulse-secure-per-app-vpn)
- [Consentire e bloccare app per dispositivi Samsung Know Standard](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
> Solo le impostazioni elencate possono essere configurate in un profilo personalizzato. I dispositivi Android non espongono un elenco completo di impostazioni URI OMA configurabili. Se si vogliono visualizzare altre impostazioni, chiedere più impostazioni nel [sito Uservoice di Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

Questo articolo descrive come creare un profilo personalizzato per i dispositivi Android.

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `android custom profile`.
    - **Descrizione:** immettere una descrizione per il profilo.
    - **Piattaforma**: scegliere **Android**.
    - **Tipo di profilo**: scegliere **Personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome univoco per l'impostazione OMA-URI in modo da poterla individuare facilmente.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
    - **OMA-URI**: immettere l'OMA-URI da usare come impostazione.
    - **Tipo di dati**: immettere il tipo di dati da usare per l'impostazione OMA-URI. Le opzioni disponibili sono:

      - Stringa
      - Stringa (file XML)
      - Data e ora
      - Integer
      - A virgola mobile
      - Boolean
      - Base64 (file)

    - **Valore**: immettere il valore dati da associare all'impostazione OMA-URI immessa. Il valore varia a seconda del tipo di dati selezionato. Ad esempio, se si sceglie **Data e ora**, selezionare il valore dalla selezione data.

    Dopo aver aggiunto alcune impostazioni, è possibile selezionare **Esporta**. **Esporta** crea un elenco di tutti i valori aggiunti in un file con valori delimitati da virgole (file con estensione csv).

5. Selezionare **OK** per salvare le modifiche. Continuare ad aggiungere altre impostazioni in base alle esigenze. 
6. Al termine, scegliere **OK** > **Crea** per creare il profilo di Intune. Il profilo viene visualizzato nell'elenco **Configurazione del dispositivo - Profili**.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. È ora necessario [assegnare il profilo](device-profile-assign.md).

Vedere come [creare il profilo nei dispositivi Android Enterprise](custom-settings-android-for-work.md).
