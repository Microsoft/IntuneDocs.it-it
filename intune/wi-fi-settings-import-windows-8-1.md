---
title: Importare le impostazioni Wi-Fi per dispositivi Windows 8.1 e versioni successive
titleSuffix: Microsoft Intune
description: Come importare le impostazioni Wi-Fi da Windows a un profilo Wi-Fi di Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 033b60fded23f5a1dac5c8ff93716dac77c56fe2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="import-wi-fi-settings-for-windows-81-and-later-devices-in-microsoft-intune"></a>Importare le impostazioni Wi-Fi per i dispositivi Windows 8.1 e versioni successive in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Per i dispositivi che eseguono Windows 8.1, Windows 10 Desktop o Mobile o Windows Holographic for Business, è possibile importare un profilo di configurazione Wi-Fi precedentemente esportato in un file.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Esportare le impostazioni Wi-Fi da un dispositivo Windows

In Windows usare l'utilità **netsh wlan** per esportare un profilo Wi-Fi esistente in un file XML leggibile da Intune. Per usare correttamente il profilo è necessario esportare la chiave in testo normale.

In un computer Windows in cui il profilo Wi-Fi necessario è già installato, seguire questa procedura:

1. Creare una cartella locale per i profili Wi-Fi esportati, ad esempio **c:\WiFi**.
2. Aprire un prompt dei comandi come amministratore.
3. Eseguire il comando `netsh wlan show profiles` e prendere nota del nome del profilo da esportare. In questo esempio, il nome del profilo è **WiFiName**.
4. Eseguire il comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Verrà creato un file di profilo Wi-Fi denominato **Wi-Fi-WiFiName.xml** nella cartella di destinazione.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importare le impostazioni Wi-Fi in Intune

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
4. Immettere un **Nome** e una **Descrizione** per il profilo di restrizione dei dispositivi.

    > [!IMPORTANT]
    > - Il nome **deve** corrispondere all'attributo name nel file XML del profilo Wi-Fi. In caso contrario, si verifica un errore.
    > - Se si sta esportando un profilo Wi-Fi che include una chiave precondivisa, **è necessario** aggiungere `key=clear` al comando. Immettere ad esempio: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - L'uso di una chiave precondivisa con Windows 10 determina la visualizzazione di un errore di correzione in Intune. Quando ciò accade, il profilo Wi-Fi viene assegnato correttamente al dispositivo e il profilo funziona come previsto.
    > - Se si esporta un profilo Wi-Fi che include una chiave precondivisa, verificare che il file sia protetto. La chiave è in testo normale ed è quindi necessario proteggerla.

5. In **Piattaforma** selezionare **Windows 8.1 e versioni successive**.
6. In **Tipo di profilo** selezionare **Importazione Wi-Fi**.
7. Configurare le seguenti impostazioni:
  - **Nome della connessione**: immettere un nome per la connessione Wi-Fi. Gli utenti finali visualizzano questo nome quando esplorano le reti Wi-Fi disponibili.
  - **Profilo XML**: selezionare il pulsante Sfoglia per selezionare il file XML contenente le impostazioni del profilo Wi-Fi da importare in Intune.
  - **Contenuti del file**: visualizza il codice XML per il profilo di configurazione selezionato.
8. Al termine, scegliere **OK** e quindi **Crea** per creare il profilo.

Il profilo verrà creato e incluso nell'elenco dei profili.
