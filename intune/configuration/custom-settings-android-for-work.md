---
title: Aggiungere impostazioni personalizzate ai dispositivi Android Enterprise in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo personalizzato per i dispositivi aziendali Android in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bd6e2d5ceebd23e87f464d15376594d1764c5b8
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206806"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Usare le impostazioni personalizzate per i dispositivi Android Enterprise in Microsoft Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi con profilo di lavoro Android Enterprise usando un "profilo personalizzato". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

I profili personalizzati Android Enterprise usano impostazioni Open Mobile Alliance Uniform Resource Identifier (OMA-URI) per controllare le funzionalità nei dispositivi Android Enterprise. Queste impostazioni vengono in genere usate dai produttori di dispositivi mobili per controllare le funzionalità.

Intune supporta il seguente numero limitato di profili personalizzati Android Enterprise:

- ./Vendor/MSFT/WiFi/Profile/SSID/Settings: [per creare un profilo Wi-Fi con una chiave precondivisa](wi-fi-profile-shared-key.md) sono disponibili alcuni esempi.
- ./Vendor/MSFT/VPN/Profile/Name/PackageList: [per creare un profilo VPN per app](android-pulse-secure-per-app-vpn.md) sono disponibili alcuni esempi.
- ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste: vedere l' [esempio](#example) in questo articolo. Questa impostazione è disponibile anche nell'interfaccia utente. Per altre informazioni, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità](device-restrictions-android-for-work.md).

Se sono necessarie impostazioni aggiuntive, vedere [OEMConfig per Android Enterprise](android-oem-configuration-overview.md).

Questo articolo descrive come creare un profilo personalizzato per i dispositivi Android Enterprise. L'articolo offre anche un esempio di profilo personalizzato che blocca l'operazione di copia e incolla.

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di profilo valido è **il profilo personalizzato Android Enterprise**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Android Enterprise**.
    - **Tipo di profilo**: selezionare **personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome univoco per l'impostazione OMA-URI in modo da poterla individuare facilmente.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
    - **OMA-URI**: immettere l'OMA-URI da usare come impostazione.
    - **Tipo di dati**: selezionare il tipo di dati da usare per questa impostazione OMA-URI. Le opzioni disponibili sono:

      - Stringa
      - Stringa (file XML)
      - Data e ora
      - Intero
      - A virgola mobile
      - Boolean
      - Base64 (file)

    - **Valore**: immettere il valore dati da associare all'impostazione OMA-URI immessa. Il valore varia a seconda del tipo di dati selezionato. Ad esempio, se si seleziona **Data e ora**, selezionare il valore dalla selezione data.

    Dopo aver aggiunto alcune impostazioni, è possibile selezionare **Esporta**. **Esporta** crea un elenco di tutti i valori aggiunti in un file con valori delimitati da virgole (file con estensione csv).

5. Selezionare **OK** per salvare le modifiche. Continuare ad aggiungere altre impostazioni in base alle esigenze.
6. Al termine, selezionare **OK** > **Crea** per creare il profilo di Intune. Una volta completata l'operazione, il profilo viene visualizzato nell'elenco **Dispositivi - Profili di configurazione**.

## <a name="example"></a>Esempio

In questo esempio viene creato un profilo personalizzato che limita le operazioni di copia e incolla tra app aziendali e personali nei dispositivi Android Enterprise.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, immettere **Android ENT Block Copy Incolla profilo personalizzato**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Android Enterprise**.
    - **Tipo di profilo**: selezionare **personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome come `Block copy and paste`.
    - **Descrizione**: immettere un nome come `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: immettere `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Tipo di dati**: selezionare **Booleano** in modo che il valore per l'OMA-URI sia **True** o **False**.
    - **Valore**: selezionare **True**.

5. Dopo aver immesso le impostazioni, l'ambiente avrà un aspetto simile all'immagine seguente:

    ![Bloccare copia e incolla per il profilo di lavoro Android.](./media/custom-settings-android-for-work/custom-policy-afw-copy-paste.png)

Quando si assegna il profilo ai dispositivi Android Enterprise gestiti, le operazioni di copia e incolla verranno bloccate tra le app incluse nei profili aziendali e personali.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Creare un [profilo personalizzato nei dispositivi Android](../custom-settings-android.md).
