---
title: Importare le impostazioni Wi-Fi per i dispositivi Windows in Microsoft Intune - Azure | Microsoft Docs
description: Esportare le impostazioni Wi-Fi da un dispositivo Windows come file XML usando netsh wlan. Quindi importare questo file in Intune per creare un profilo Wi-Fi per i dispositivi che eseguono Windows 8.1, Windows 10 e Windows Holographic for Business.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207010"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importare le impostazioni Wi-Fi per i dispositivi Windows in Intune

Per i dispositivi che eseguono Windows, è possibile importare un profilo di configurazione Wi-Fi precedentemente esportato in un file. **Per i dispositivi Windows 10 e versioni successive è anche possibile [creare un profilo Wi-Fi](wi-fi-settings-windows.md) direttamente in Intune**.

Si applica a:  
- Windows 8.1 e versioni successive
- Windows 10 e versioni successive
- Windows 10 Desktop o Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Esportare le impostazioni Wi-Fi da un dispositivo Windows

In Windows usare `netsh wlan` per esportare un profilo Wi-Fi esistente in un file XML leggibile da Intune. Per usare correttamente il profilo è necessario esportare la chiave in testo normale.

In un computer Windows in cui il profilo Wi-Fi necessario è già installato, seguire questa procedura:

1. Creare una cartella locale per i profili Wi-Fi esportati, ad esempio **c:\WiFi**.
2. Aprire un prompt dei comandi come amministratore.
3. Eseguire il comando `netsh wlan show profiles`. Prendere nota del nome del profilo che si vuole esportare. In questo esempio, il nome del profilo è **WiFiName**.
4. Eseguire il comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Questo comando crea un file di profilo Wi-Fi denominato **Wi-Fi-WiFiName.xml** nella cartella di destinazione.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importare le impostazioni Wi-Fi in Intune

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Il nome **deve** corrispondere all'attributo name nel file XML del profilo Wi-Fi. In caso contrario, si verifica un errore.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
    - **Piattaforma**: Selezionare **Windows 8.1 e versioni successive**.
    - **Tipo di profilo**: selezionare **Wi-Fi per importazione**.

    > [!IMPORTANT]
    > - Se si sta esportando un profilo Wi-Fi che include una chiave precondivisa, **è necessario** aggiungere `key=clear` al comando. Immettere ad esempio: `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - L'uso di una chiave precondivisa con Windows 10 determina la visualizzazione di un errore di correzione in Intune. Quando ciò accade, il profilo Wi-Fi viene assegnato correttamente al dispositivo e il profilo funziona come previsto.
    > - Se si esporta un profilo Wi-Fi che include una chiave precondivisa, verificare che il file sia protetto. La chiave è in testo normale ed è quindi necessario proteggerla.

4. Immettere le impostazioni seguenti:

    - **Nome della connessione**: immettere un nome per la connessione Wi-Fi. Questo nome viene visualizzato agli utenti quando esplorano le reti Wi-Fi disponibili.
    - **Profilo XML**: selezionare il pulsante Sfoglia e selezionare il file XML che contiene le impostazioni del profilo Wi-Fi da importare.
    - **Contenuti del file**: visualizza il codice XML per il profilo di configurazione selezionato.

5. Selezionare **OK** per salvare le modifiche.
6. Al termine, selezionare **OK** > **Crea** per creare il profilo di Intune. Una volta completata l'operazione, il profilo viene visualizzato nell'elenco **Dispositivi - Profili di configurazione**.

## <a name="next-steps"></a>Passaggi successivi

Il profilo viene creato, ma non è ancora operativo. [Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Vedere [Panoramica delle impostazioni Wi-Fi](wi-fi-settings-configure.md), incluse altre piattaforme disponibili.
