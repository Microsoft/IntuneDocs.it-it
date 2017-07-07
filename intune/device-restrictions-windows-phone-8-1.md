---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows Phone 8.1
titleSuffix: Intune on Azure
description: "Informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo in dispositivi Windows Phone 8.1.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d42714-49ca-43b3-b080-2e67a4268198
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e425b8a3c93c2f5dc73fbe9c75aa9adf49c5cdc8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="windows-phone-81-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows Phone 8.1 in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="general"></a>Generale
-   **Apply all settings to Windows Phone 8.1 only**(Applica tutte le impostazioni solo a Windows Phone 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10 Mobile.
-   **Fotocamera** - Abilita o blocca la fotocamera del dispositivo.
-   **Copia e incolla** - Abilita o blocca la funzionalità copia e incolla nel dispositivo.
-   **Archivi rimovibili** - Consente al dispositivo di usare unità di archiviazione rimovibili, ad esempio schede SD.
-   **Georilevazione** - Consente al dispositivo di usare le informazioni sulla posizione geografica.
-   **Account Microsoft** - Consente o impedisce all'utente di collegare un account Microsoft al dispositivo.
-   **Acquisizione schermo** - Consente all'utente di acquisire il contenuto della schermata come file di immagine.
-   **Invio dati di diagnostica** - Consente al dispositivo di inviare informazioni di diagnostica a Microsoft.
-   **Sincronizzazione degli account di posta elettronica personalizzati** - Consente al dispositivo di connettersi ad account di posta elettronica non Microsoft.

## <a name="password"></a>Password
-   **Apply all settings to Windows Phone 8.1 only**(Applica tutte le impostazioni solo a Windows Phone 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10 Mobile.
-   **Password necessaria** - Richiede all'utente finale di immettere una password per accedere al dispositivo.
    -   **Tipo di password richiesto** - Specifica il tipo di password che verrà richiesto, ad esempio alfanumerico o solo numerico.
    -   **Lunghezza minima password** - Specifica il numero minimo di caratteri complessi richiesti per la password.
    -   **Password semplici** - Specifica la possibilità di usare password semplici, ad esempio "0000" e "1234".
    -   **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Specifica il numero di tentativi di immissione di una password errata ripetuti prima che il dispositivo venga cancellato.
    -   **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il periodo di tempo per cui un dispositivo deve rimanere inattivo prima che lo schermo venga bloccato automaticamente.
    -   **Scadenza password (giorni)** - Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.
    -   **Impedisci riutilizzo delle password precedenti** - Specifica quante password utilizzate in precedenza devono essere ricordate.
-   **Crittografia** - Richiede che i dati presenti nei dispositivi mobili supportati siano crittografati.

## <a name="app-store"></a>App Store
-   **Apply all settings to Windows Phone 8.1 only**(Applica tutte le impostazioni solo a Windows Phone 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10 Mobile.
-   **App Store** - Consente all'utente di connettersi all'App Store dal dispositivo.

## <a name="restricted-apps"></a>App con restrizioni

-   **Apply all settings to Windows Phone 8.1 only**(Applica tutte le impostazioni solo a Windows Phone 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10 Mobile.

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

Un elenco di **App bloccate** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire.
Un elenco di **App consentite** - Elenca le app che gli utenti sono autorizzati a installare. Le app gestite da Intune sono automaticamente consentite.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL app nell'elenco di app consentite e bloccate, usare il formato seguente:

Nella pagina [Windows Phone Store](https://www.microsoft.com/store/apps/windows-phone) cercare l'applicazione che si vuole usare.

Aprire la pagina dell'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app consentite o bloccate.

Esempio: cercare per l'app Skype in Store. L'URL usato sarà **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app con restrizioni nello stesso formato.


## <a name="browser"></a>Browser
-   **Apply all settings to Windows Phone 8.1 only**(Applica tutte le impostazioni solo a Windows Phone 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10 Mobile.
-   **Browser Web** - Abilita o blocca il Web browser integrato nei dispositivi.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività
-   **Apply all settings to Windows Phone 8.1 only**(Applica tutte le impostazioni solo a Windows Phone 8.1): si tratta di un'impostazione che è possibile configurare nel portale classico di Intune. Nel portale di Azure questa impostazione non può essere modificata. Se è impostata su **Configurato**, tutte le impostazioni verranno applicate solo ai dispositivi Windows Phone 8.1. Se impostata su **Non configurato**, queste impostazioni verranno applicate anche ai dispositivi Windows 10 Mobile.
-   **Wi-Fi** - Abilita o disabilita le funzionalità Wi-Fi del dispositivo.
-   **Tethering Wi-Fi** - Abilita l'uso del tethering Wi-Fi nel dispositivo.
-   **Connetti automaticamente a hotspot Wi-Fi** - Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente le condizioni d'uso.
-   **Reporting hotspot Wi-Fi** - Invia informazioni sulle connessioni Wi-Fi per individuare connessioni nelle vicinanze.
-   **NFC** - Abilita o disabilita le operazioni che usano Near Field Communication sui dispositivi che la supportano.
-   **Bluetooth** - Abilita o disabilita la funzione Bluetooth del dispositivo.