---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows Phone 8.1 in Microsoft Intune
titleSuffix: 
description: "Informazioni relative alle opzioni di Intune per il controllo delle impostazioni e funzionalità nei dispositivi che eseguono Windows Phone 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 808c8e9ac1ef944b69ae8e548c62d4c6366820d0
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-windows-phone-81-device-restriction-settings"></a>Impostazioni relative alle restrizioni dei dispositivi Windows Phone 8.1 in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni relative alle restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi che eseguono Windows Phone 8.1.


## <a name="general"></a>Generale

-   **Fotocamera** - Abilita o blocca la fotocamera del dispositivo.
-   **Copia e incolla** - Abilita o blocca la funzionalità copia e incolla nel dispositivo.
-   **Archivi rimovibili** - Consente al dispositivo di usare unità di archiviazione rimovibili, ad esempio schede SD.
-   **Georilevazione** - Consente al dispositivo di usare le informazioni sulla posizione geografica.
-   **Account Microsoft** - Consente o impedisce all'utente di collegare un account Microsoft al dispositivo.
-   **Acquisizione schermo** - Consente all'utente di acquisire il contenuto della schermata come file di immagine.
-   **Invio dati di diagnostica** - Consente al dispositivo di inviare informazioni di diagnostica a Microsoft.
-   **Sincronizzazione degli account di posta elettronica personalizzati** - Consente al dispositivo di connettersi ad account di posta elettronica non Microsoft.

## <a name="password"></a>Password

-   **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
    -   **Tipo di password richiesto** - Specifica il tipo di password che viene richiesto, ad esempio alfanumerico o solo numerico.
    -   **Lunghezza minima password** - Specifica il numero minimo di caratteri complessi richiesti per la password.
    -   **Password semplici** - Specifica la possibilità di usare password semplici, ad esempio "0000" e "1234".
    -   **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Specifica il numero di tentativi di immissione di una password errata ripetuti prima che il dispositivo venga cancellato.
    -   **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il periodo di tempo per cui un dispositivo deve rimanere inattivo prima che lo schermo venga bloccato automaticamente.
    -   **Scadenza password (giorni)** - Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.
    -   **Impedisci riutilizzo delle password precedenti** - Specifica quante password utilizzate in precedenza devono essere ricordate.
-   **Crittografia** - Richiede che i dati presenti nei dispositivi mobili supportati siano crittografati.

## <a name="app-store"></a>App Store

-   **App Store** - Consente all'utente di connettersi all'App Store dal dispositivo.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

Un elenco di **App bloccate** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire.
Un elenco di **App consentite** - Elenca le app che gli utenti sono autorizzati a installare. Le app gestite da Intune sono automaticamente consentite.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL app nell'elenco di app consentite e bloccate, usare il formato seguente:

Nella pagina [Windows Phone Store](https://www.microsoft.com/store/apps/windows-phone) cercare l'applicazione che si vuole usare.

Aprire la pagina dell'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app consentite o bloccate.

Esempio: cercare per l'app Skype in Store. L'URL usato è **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.



### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*app url*>, <*app name*>, <app publisher> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app con restrizioni nello stesso formato.


## <a name="browser"></a>Browser

-   **Browser Web** - Abilita o blocca il Web browser integrato nei dispositivi.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività

-   **Wi-Fi** - Abilita o disabilita le funzionalità Wi-Fi del dispositivo.
-   **Tethering Wi-Fi** - Abilita l'uso del tethering Wi-Fi nel dispositivo.
-   **Connetti automaticamente a hotspot Wi-Fi** - Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente le condizioni d'uso.
-   **Reporting hotspot Wi-Fi** - Invia informazioni sulle connessioni Wi-Fi per individuare connessioni nelle vicinanze.
-   **NFC** - Abilita o disabilita le operazioni che usano Near Field Communication sui dispositivi che la supportano.
-   **Bluetooth** - Abilita o disabilita la funzione Bluetooth del dispositivo.
