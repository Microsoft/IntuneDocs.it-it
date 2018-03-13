---
title: Come configurare le impostazioni Wi-Fi di Intune
titleSuffix: Microsoft Intune
description: Informazioni su come usare Microsoft Intune per configurare le connessioni Wi-Fi nei dispositivi gestiti.
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 21bc79d3440e57ec91f7e4482112d77cf233575f
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-configure-wi-fi-settings-in-microsoft-intune"></a>Come configurare le impostazioni Wi-Fi in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare i profili Wi-Fi in di Microsoft Intune per assegnare le impostazioni di rete wireless agli utenti e ai dispositivi dell'organizzazione. Quando si assegna un profilo Wi-Fi, gli utenti hanno accesso alla rete Wi-Fi aziendale senza doverla configurare.

Si immagini, ad esempio, di installare una nuova rete Wi-Fi denominata Contoso Wi-Fi e di voler configurare tutti i dispositivi iOS in modo che si connettano alla rete. Questa è la procedura:

1. Creare un profilo Wi-Fi contenente le impostazioni necessarie per connettersi alla rete wireless Contoso Wi-Fi.
2. Assegnare il profilo a un gruppo contenente tutti gli utenti dei dispositivi iOS.
3. Gli utenti visualizzeranno la nuova rete Contoso Wi-Fi nell'elenco delle reti wireless sul proprio dispositivo e potranno facilmente connettersi a tale rete.

## <a name="supported-device-platforms"></a>Piattaforme per dispositivi supportate

I profili Wi-Fi supportano le piattaforme per dispositivi seguenti:

- Android 4 e versioni successive
- Android for Work
- iOS 8.0 e versioni successive
- macOS (Mac OS X 10.9 e versioni successive)

Per i dispositivi che eseguono Windows 8.1, Windows 10, 10 Windows Mobile e Windows Holographic for Business, è possibile importare una configurazione Wi-Fi precedentemente esportata da un altro dispositivo.

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione di un profilo Wi-Fi e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-wi-fi-settings"></a>Creare un profilo dispositivo contenente le impostazioni Wi-Fi

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo Wi-Fi.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni Wi-Fi. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni Wi-Fi:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows 8.1 e versioni successive (importazione di un profilo)**

   > [!IMPORTANT]
   > Se si sta creando un profilo per dispositivi che eseguono Windows 10, tra cui Windows Holographic for Business, è necessario scegliere la piattaforma **Windows 8.1 e versioni successive**. La piattaforma **Windows 10 e versioni successive** non include un tipo di profilo Wi-Fi. 

6. Per i dispositivi Apple o Android nell'elenco a discesa **Tipo di Wi-Fi** scegliere **Basic** o **Enterprise**. È possibile usare **Basic** per fornire informazioni di base, come il nome della rete e l'identificatore SSID. **Enterprise** consente di fornire informazioni più avanzate come il protocollo EAP (Extensible Authentication Protocol), se la rete Wi-Fi usa questo protocollo. 

   Il profilo **Wi-Fi per importazione**  (per Windows 8.1 e versioni successive) consente di importare le impostazioni Wi-Fi come un file XML precedentemente esportato da un altro dispositivo.
1. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android e Android for Work](wi-fi-settings-android.md)
    - [Impostazioni iOS](wi-fi-settings-ios.md)
    - [Impostazioni macOS](wi-fi-settings-macos.md)
    - [Impostazioni di Windows 8.1 e versioni successive](wi-fi-settings-import-windows-8-1.md) (incluso Windows Holographic for Business)
1. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
