---
title: Impostazioni dei criteri di Exchange ActiveSync
description: "Usare i criteri di Exchange ActiveSync di Intune per configurare le impostazioni che consentono di controllare una gamma di funzionalità sui dispositivi gestiti da Exchange ActiveSync."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 6bbb0cd7ca87a3c6cc352cbdd6dd2b61a9c5e36c
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017


---

# <a name="exchange-activesync-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di Exchange ActiveSync in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare i criteri di **Exchange ActiveSync** di Microsoft Intune per configurare le impostazioni che consentono di controllare diverse funzionalità nei dispositivi gestiti da Exchange ActiveSync.


## <a name="password-settings"></a>Impostazioni della password

|Nome impostazione|Dettagli
|----------------|---|
|**Richiedi una password per sbloccare i dispositivi mobili**|Specifica se i dispositivi devono essere bloccati usando una password.<br>Non applicabile ai dispositivi che eseguono Windows RT.|
|**Tipo di password richiesto**|Specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.|
|**Lunghezza minima password**|Specifica il numero minimo di caratteri richiesti per la password del dispositivo.|
|**Consenti password semplici**|Specifica se è possibile usare password semplici come '0000' e '1234'.|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Specifica il numero di tentativi di immissione della password non corretti prima che il dispositivo venga cancellato.|
|**Scadenza password (giorni)**|Specifica il numero di giorni dopo i quali è necessario modificare la password del dispositivo.
|**Ricorda cronologia password**|Specifica se consentire o meno l'uso di password usate in precedenza.|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che non possono più essere usate.|
|**Minuti di inattività prima che venga richiesta la password**|Specifica per quanto tempo il dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.

## <a name="encryption-settings"></a>Impostazioni di crittografia

|Nome impostazione|Dettagli|
|----------------|---|
|**Richiedi crittografia sul dispositivo mobile**<sup>1</sup>|Richiede la crittografia dei dati nel dispositivo, quando è supportata.<br><br>Per i dispositivi Windows Phone 8, è necessario impostare su **Sì**.<br /><br />Per abilitare la crittografia nei dispositivi iOS, abilitare l'impostazione **Richiedi una password per sbloccare i dispositivi mobili**.|
|**Richiedi crittografia sulle schede di memoria**|Richiede la crittografia dei dati presenti nella risorsa di archiviazione esterna, ad esempio una scheda SD (nei dispositivi supportati).
<sup>1</sup> Altre informazioni per i dispositivi che eseguono Windows 8.1

-   Per imporre la crittografia nei dispositivi che eseguono Windows 8.1, è necessario installare l'[Aggiornamento del client MDM di dicembre 2014 in Windows](https://support.microsoft.com/kb/3013816) in ogni dispositivo.

-   Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un account Microsoft.

-   Per il corretto funzionamento della crittografia nei dispositivi Windows 8.1, il dispositivo deve soddisfare i requisiti di certificazione hardware di Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/).

-   Quando si impone la crittografia in un dispositivo Windows 8.1, la chiave di ripristino è accessibile solo dall'account Microsoft dell'utente, disponibile dall'account OneDrive dell'utente. È possibile ripristinare la chiave per conto dell'utente.

## <a name="email-settings"></a>Impostazioni di posta elettronica

|Nome impostazione|Dettagli
|----------------|---|
|**Consenti agli utenti di eseguire il download degli allegati di posta elettronica**|Specifica se gli allegati di posta elettronica possono essere scaricati sul dispositivo.|
|**Periodo di sincronizzazione della posta elettronica**|Specifica il numero di giorni in cui i messaggi ricevuti verranno sincronizzati con il dispositivo.
|**Consenti ai dispositivi mobili che non supportano completamente le impostazioni di Exchange ActiveSync di eseguire la sincronizzazione con Exchange**|Specifica se consentire a Exchange di accedere ai dispositivi che non supportano una o più impostazioni di Exchange ActiveSync.

## <a name="browser-settings"></a>Impostazioni del browser

|Nome impostazione|Dettagli
|----------------|---|
|**Consenti Web browser**|Specifica se è consentito l'uso del Web browser nel dispositivo.<br>Opzione non disponibile per Windows RT o Windows Phone.

## <a name="hardware-settings"></a>Impostazioni hardware

|Nome impostazione|Dettagli
|----------------|---|
|**Consenti la fotocamera**|Specifica se è consentito l'uso della fotocamera del dispositivo.<br>Opzione non disponibile per Windows RT o Windows Phone.



### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

