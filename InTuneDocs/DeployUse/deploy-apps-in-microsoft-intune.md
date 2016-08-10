---
title: Come distribuire le app | Microsoft Intune
description: Usare le informazioni in questo argomento per distribuire le app con Microsoft Intune.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0c6f795031ec23ffe6f332b3510eea43d5fbdbcd
ms.openlocfilehash: 4c9f5b111fbd95f9e1c928cfaaa0c7ebf61dad2a

---
# Distribuire app in Microsoft Intune

Usare le informazioni in questo argomento per distribuire le app con Microsoft Intune.


## Distribuzione di un'app
In questa procedura l'app verrà distribuita a gruppi selezionati di dispositivi o utenti.

### Per distribuire un'app

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **App** &gt; **App** per visualizzare l'elenco delle app gestite.

2.  Selezionare l'app da distribuire, quindi fare clic su **Gestisci distribuzione**.

3.  Nella pagina **Seleziona gruppi** della finestra di dialogo *&lt;nome app&gt;* scegliere i gruppi di utenti o dispositivi in cui si vuole distribuire l'app.

4.  Nella pagina **Azione di distribuzione** configurare gli elementi seguenti:

    - **Approvazione**: indicare se la distribuzione è:
        - **Obbligatorio** (installazione obbligatoria)
        - **Disponibile** (installazione dal portale aziendale su richiesta)
        - **Non applicabile** (l'app non è installata o visualizzata nel portale aziendale)
        - **Disinstalla** (l'app viene disinstallata dai dispositivi specificati)
    - **Scadenza**: per le installazioni obbligatorie indicare dopo quanto tempo distribuire l'app. È possibile scegliere uno dei valori predefiniti o selezionare **Personalizzato** per configurare una scadenza personalizzata.

5. Se è possibile configurare l'app da distribuire con i criteri di gestione per applicazioni mobili, verrà visualizzata la pagina **Gestione delle app mobili**. In questa pagina scegliere i criteri di gestione di applicazioni mobili da associare a questa app.

    [Vedere quali app Microsoft sono compatibili con i criteri di gestione delle applicazioni mobili.](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

6. Se l'app da distribuire è compatibile con i profili VPN di Intune, verrà visualizzata la pagina **Profilo VPN**. In questa pagina è possibile scegliere di associare le app iOS a un profilo VPN già distribuito. La connessione VPN verrà aperta automaticamente all'avvio dell'app. Per rendere disponibile un profilo VPN, l'impostazione del profilo **VPN per app** deve essere abilitata.
 Per informazioni su come configurare i profili VPN, incluse le informazioni su come associare i profili con le app, vedere [Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md).

## Esempio

In questo esempio l'app è stata distribuita come **Disponibile** a un dispositivo iOS.
L'app viene visualizzata nei dispositivi degli utenti nel portale aziendale e gli utenti possono installarla da quella posizione.

In questo screenshot, ad esempio, l'app Bing per iOS è stata distribuita con il tipo di installazione **Collegamento esterno** con un'icona personalizzata. È stata selezionata l'opzione **Visualizzare questo elemento come app in evidenza ed evidenziarlo nel Portale aziendale**.  
![App disponibile iOS](./media/available-install-on-iOS.png)

Se l'app è stata distribuita come **Richiesta**, l'utente viene avvisato quando è possibile iniziare l'installazione di un'app. In questo screenshot, ad esempio, l'app Cartelle di lavoro per iOS è stata distribuita con il tipo di installazione **App iOS gestita dall'App Store**.
![App obbligatoria iOS](./media/iOS-Required-install.PNG)

## Passaggi successivi

Dopo aver distribuito un'app, è possibile monitorarne l'avanzamento. Per altre informazioni, vedere [Monitor app deployments in Microsoft Intune](monitor-apps-in-microsoft-intune.md) (Monitoraggio delle distribuzioni di app in Microsoft Intune).



<!--HONumber=Jul16_HO5-->


