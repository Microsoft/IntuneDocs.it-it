---
title: Importare le impostazioni Wi-Fi per dispositivi Windows 8.1 e versioni successive
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: come importare le impostazioni Wi-Fi da Windows a un profilo Wi-Fi di Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c4e9b19-b268-4f6d-9663-7cdbe4e4a8dd
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 9f98a786e97afbb93628609808637def0a7e8fe8
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Come importare le impostazioni Wi-Fi per i dispositivi Windows 8.1 e versioni successive in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Per i dispositivi che eseguono Windows 8.1 o Windows 10 Desktop o Mobile, è possibile importare un profilo di configurazione Wi-Fi precedentemente esportato in un file.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Esportare le impostazioni Wi-Fi da un dispositivo Windows

In Windows usare l'utilità **netsh wlan** per esportare un profilo Wi-Fi esistente in un file XML leggibile da Intune. In un computer Windows in cui è già installato il profilo Wi-Fi necessario, attenersi alla procedura seguente.
1. Creare una cartella locale per i profili Wi-Fi esportati, ad esempio **c:\WiFi**.
1. Aprire un prompt dei comandi come amministratore.
1. Eseguire il comando **netsh wlan show profiles**e prendere nota del nome del profilo da esportare. In questo esempio, il nome del profilo è **WiFiName**.
1. Eseguire questo comando: **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Verrà creato un file di profilo Wi-Fi denominato **Wi-Fi-WiFiName.xml** nella cartella di destinazione.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importare le impostazioni Wi-Fi in Intune

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili fare clic su **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di restrizione del dispositivo.
5. Dall'elenco a discesa **Piattaforma** scegliere **Windows 8.1 e versioni successive**.
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Importazione Wi-Fi**.
7. Nel pannello **Wi-Fi di base** configurare quanto segue:
    - **Nome della connessione** Immettere il nome della connessione Wi-Fi. Gli utenti finali visualizzano questo nome quando esplorano le reti Wi-Fi disponibili.
    - **Profilo XML** Fare clic sul pulsante Sfoglia per selezionare il file XML contenente le impostazioni del profilo Wi-Fi da importare in Intune.
    - **Contenuti del file** Visualizza il codice XML per il profilo di configurazione selezionato.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.

