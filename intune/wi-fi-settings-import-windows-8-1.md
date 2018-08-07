---
title: Importare le impostazioni Wi-Fi per i dispositivi Windows in Microsoft Intune - Azure | Microsoft Docs
description: Esportare le impostazioni Wi-Fi da un dispositivo Windows come file XML usando netsh wlan. Quindi importare questo file in Intune per creare un profilo Wi-Fi per i dispositivi che eseguono Windows 8.1, Windows 10 e Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ce5cdd9509ed3407491714ccfa853613eb43973
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321136"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importare le impostazioni Wi-Fi per i dispositivi Windows in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Per i dispositivi che eseguono Windows, è possibile importare un profilo di configurazione Wi-Fi precedentemente esportato in un file. **Per i dispositivi Windows 10 e versioni successive è possibile [creare un profilo Wi-Fi](wi-fi-settings-windows.md) direttamente in Intune**.

Si applica a:  
- Windows 8.1 e versioni successive
- Windows 10 e versioni successive
- Windows 10 Desktop o Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Esportare le impostazioni Wi-Fi da un dispositivo Windows

In Windows usare **netsh wlan** per esportare un profilo Wi-Fi esistente in un file XML leggibile da Intune. Per usare correttamente il profilo è necessario esportare la chiave in testo normale.

In un computer Windows in cui il profilo Wi-Fi necessario è già installato, seguire questa procedura:

1. Creare una cartella locale per i profili Wi-Fi esportati, ad esempio **c:\WiFi**.
2. Aprire un prompt dei comandi come amministratore.
3. Eseguire il comando `netsh wlan show profiles` e prendere nota del nome del profilo da esportare. In questo esempio, il nome del profilo è **WiFiName**.
4. Eseguire il comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Verrà creato un file di profilo Wi-Fi denominato **Wi-Fi-WiFiName.xml** nella cartella di destinazione.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importare le impostazioni Wi-Fi in Intune

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
4. Immettere un **Nome** e una **Descrizione** per il profilo di restrizione del dispositivo.

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
