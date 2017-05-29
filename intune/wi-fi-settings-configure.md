---
title: Come configurare le impostazioni Wi-Fi di Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come usare Intune per configurare le connessioni Wi-Fi nei dispositivi gestiti.'
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1fadb488-9c6c-43c1-ba23-8c69db633b96
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3378df904936def8737ca3b5b791feebdb95823b
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Come configurare le impostazioni Wi-Fi in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Usare i profili Wi-Fi in di Microsoft Intune per assegnare le impostazioni di rete wireless agli utenti e ai dispositivi dell'organizzazione. Quando si assegna un profilo Wi-Fi, gli utenti hanno accesso alla rete Wi-Fi aziendale senza doverla configurare.

Si immagini, ad esempio, di installare una nuova rete Wi-Fi denominata Contoso Wi-Fi e di voler configurare tutti i dispositivi iOS in modo che si connettano alla rete. Questa è la procedura:

1. Creare un profilo Wi-Fi contenente le impostazioni necessarie per connettersi alla rete wireless Contoso Wi-Fi.
2. Assegnare il profilo a un gruppo contenente tutti gli utenti dei dispositivi iOS.
3. Gli utenti visualizzeranno la nuova rete Contoso Wi-Fi nell'elenco delle reti wireless sul proprio dispositivo e potranno facilmente connettersi a tale rete.

I profili Wi-Fi supportano le piattaforme per dispositivi seguenti:

- Android 4 e versioni successive
- iOS 8.0 e versioni successive
- macOS (Mac OS X 10.9 e versioni successive)

Per i dispositivi che eseguono Windows 8.1, Windows 10 e 10 Windows Mobile, è possibile importare una configurazione Wi-Fi precedentemente esportata da un altro dispositivo.

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione di un profilo Wi-Fi e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Creare un profilo dispositivo contenente le impostazioni Wi-Fi

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo Wi-Fi.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni Wi-Fi. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni Wi-Fi:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows 8.1 e versioni successive (importazione di un profilo)**
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Wi-Fi di base** o **Wi-Fi aziendale**.
    >[!TIP]
    >Usare **Wi-Fi di base** per fornire informazioni di base quali il nome della rete e l'SSID. **Wi-Fi aziendale** consente di fornire informazioni più avanzate come il protocollo EAP (Extensible Authentication Protocol), se la rete Wi-Fi lo usa. **Wi-Fi per importazione**  (per Windows 8.1 e Windows 10) consente di importare le impostazioni Wi-Fi come un file XML precedentemente esportato da un altro dispositivo.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android](wi-fi-settings-android.md)
    - [Impostazioni iOS](wi-fi-settings-ios.md)
    - [Impostazioni macOS](wi-fi-settings-macos.md)
    - [Impostazioni Windows Phone 8.1](wi-fi-settings-import-windows-8-1.md)
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).


