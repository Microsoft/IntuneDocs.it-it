---
title: Creare un profilo Wi-Fi per i dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Vedere la procedura per creare un profilo di configurazione Wi-Fi per i dispositivi in Microsoft Intune. Creare profili per dispositivi Android, Android Enterprise, Android in modalità tutto schermo, iOS, macOS, Windows 10 e versioni successive e Windows Holographic for Business. Usare questi profili per creare una connessione Wi-Fi per usare i certificati, scegliere un tipo EAP, selezionare un metodo di autenticazione, abilitare un proxy e altro ancora.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75cdd958d9663d5b2d330a947a19963c219feaea
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545925"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Aggiungere e usare le impostazioni Wi-Fi nei dispositivi in Microsoft Intune

Il Wi-Fi è una rete wireless usata da molti dispositivi mobili per ottenere accesso alla rete. Microsoft Intune include delle impostazioni Wi-Fi predefinite che possono essere distribuite agli utenti e ai dispositivi dell'organizzazione. Questo gruppo di impostazioni è denominato "profilo" e può essere assegnato a diversi utenti e gruppi. Quando viene assegnato, gli utenti ottengono l'accesso alla rete Wi-Fi dell'organizzazione senza configurarla autonomamente.

Si supponga, ad esempio, di installare una nuova rete Wi-Fi denominata Contoso Wi-Fi. Si vogliono quindi configurare tutti i dispositivi iOS per la connessione a questa rete. Questa è la procedura:

1. Creare un profilo Wi-Fi contenente le impostazioni per connettersi alla rete wireless Contoso Wi-Fi.
2. Assegnare il profilo a un gruppo contenente tutti gli utenti dei dispositivi iOS.
3. Gli utenti visualizzeranno la nuova rete Contoso Wi-Fi nell'elenco delle reti wireless sul proprio dispositivo. Gli utenti potranno quindi connettersi alla rete usando il metodo di autenticazione scelto.

Questo articolo illustra la procedura per creare un profilo Wi-Fi e include i collegamenti che descrivono le diverse impostazioni per ogni piattaforma.

## <a name="supported-device-platforms"></a>Piattaforme per dispositivi supportate

I profili Wi-Fi supportano le piattaforme per dispositivi seguenti:

- Android 4 e versioni successive
- Android Enterprise e modalità tutto schermo
- iOS 8.0 e versioni successive
- macOS X 10.11 e versioni successive
- Windows 10 e versioni successive, Windows 10 Mobile e Windows Holographic for Business

> [!NOTE]
> Per i dispositivi che eseguono Windows 8.1, è possibile importare una configurazione Wi-Fi precedentemente esportata da un altro dispositivo.

## <a name="create-a-device-profile"></a>Creare un profilo del dispositivo

1. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
2. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un buon nome di profilo è **Profilo WiFi per l'intera azienda**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:

      - **Android**
      - **Android Enterprise**
      - **iOS**
      - **macOS**
      - **Windows 8.1 e versioni successive**
      - **Windows 10 e versioni successive**

    - **Tipo di profilo**: selezionare **Wi-Fi**.

      > [!TIP]
      >
      > - Per i dispositivi **Android Enterprise** eseguiti come dispositivi dedicati (modalità a tutto schermo) scegliere **Solo proprietario del dispositivo** > **Wi-Fi**.
      > - Per **Windows 8.1 e versioni successive** è possibile scegliere **Wi-Fi per importazione**. Questa opzione consente di importare le impostazioni Wi-Fi come un file XML precedentemente esportato da un altro dispositivo.

3. Alcune impostazioni Wi-Fi sono diverse per ogni piattaforma. Per visualizzare le impostazioni per una piattaforma specifica, scegliere la piattaforma:

    - [Android](wi-fi-settings-android.md)
    - [Android Enterprise](wi-fi-settings-android-enterprise.md), inclusi i dispositivi dedicati
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 e versioni successive](wi-fi-settings-windows.md)
    - [Windows 8.1 e versioni successive](wi-fi-settings-import-windows-8-1.md), incluso Windows Holographic for Business

4. Al termine, selezionare **Crea profilo** > **Crea**.

Il profilo viene creato e visualizzato nell'elenco dei profili (**Configurazione del dispositivo** > **Profili**).

## <a name="next-steps"></a>Passaggi successivi

Il profilo viene creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
