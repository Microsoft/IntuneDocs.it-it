---
title: Importare le impostazioni Wi-Fi per dispositivi Windows 8.1 e versioni successive
titleSuffix: Azure portal
description: Come importare le impostazioni Wi-Fi da Windows a un profilo Wi-Fi di Intune."
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
ms.openlocfilehash: 5b4b77f9c9c1c957e3332c20e010a5e8e8ec2b56
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Come importare le impostazioni Wi-Fi per i dispositivi Windows 8.1 e versioni successive in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Per i dispositivi che eseguono Windows 8.1, Windows 10 Desktop o Mobile o Windows Holographic for Business, è possibile importare un profilo di configurazione Wi-Fi precedentemente esportato in un file.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Esportare le impostazioni Wi-Fi da un dispositivo Windows

In Windows usare l'utilità **netsh wlan** per esportare un profilo Wi-Fi esistente in un file XML leggibile da Intune. In un computer Windows in cui è già installato il profilo Wi-Fi necessario, attenersi alla procedura seguente.
1. Creare una cartella locale per i profili Wi-Fi esportati, ad esempio **c:\WiFi**.
1. Aprire un prompt dei comandi come amministratore.
1. Eseguire il comando **netsh wlan show profiles**e prendere nota del nome del profilo da esportare. In questo esempio, il nome del profilo è **WiFiName**.
1. Eseguire questo comando: **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Verrà creato un file di profilo Wi-Fi denominato **Wi-Fi-WiFiName.xml** nella cartella di destinazione.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importare le impostazioni Wi-Fi in Intune

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili fare clic su **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di restrizione del dispositivo.

   > [!WARNING]
   > Il nome **deve** corrispondere all'attributo name nel file XML del profilo Wi-Fi, in caso contrario si verifica un errore.

5. Dall'elenco a discesa **Piattaforma** scegliere **Windows 8.1 e versioni successive**.
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Importazione Wi-Fi**.
7. Nel pannello **Wi-Fi di base** configurare le impostazioni seguenti:
    - **Nome della connessione** Immettere il nome della connessione Wi-Fi. Gli utenti finali visualizzano questo nome quando esplorano le reti Wi-Fi disponibili.
    - **Profilo XML** Fare clic sul pulsante Sfoglia per selezionare il file XML contenente le impostazioni del profilo Wi-Fi da importare in Intune.
    - **Contenuti del file** Visualizza il codice XML per il profilo di configurazione selezionato.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.
