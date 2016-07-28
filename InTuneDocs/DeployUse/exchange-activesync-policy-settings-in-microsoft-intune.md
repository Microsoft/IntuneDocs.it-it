---
title: Impostazioni dei criteri di Exchange ActiveSync | Microsoft Intune
description: "Usare i criteri di Exchange ActiveSync di Intune per configurare le impostazioni che consentono di controllare una gamma di funzionalità sui dispositivi gestiti da Exchange ActiveSync."
keywords: 
author: robstackmsft
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e9cbb826-b155-4df6-abf3-60c6f05b2783
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a409d36c1c5fcfd3d81ce0cbdf1f69af4747157a
ms.openlocfilehash: 7cdb34c469d2932deb10deec592a899b9848226a


---

# Impostazioni dei criteri di Exchange ActiveSync in Microsoft Intune
Usare i criteri di **Exchange ActiveSync** di Microsoft Intune per configurare le impostazioni che consentono di controllare una gamma di funzionalità sui dispositivi gestiti da Exchange ActiveSync.


## Impostazioni della password

|Nome impostazione|Dettagli
|----------------|
|**Richiedi una password per sbloccare i dispositivi mobili**|Specifica se i dispositivi devono essere bloccati usando una password.<br>Non applicabile ai dispositivi che eseguono Windows RT|
|**Tipo di password richiesto**|Specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.|
|**Lunghezza minima password**|Specifica il numero minimo di caratteri richiesti per la password del dispositivo.|
|**Consenti password semplici**|Le password semplici includono "0000" e "1234".|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Consente il numero indicato di tentativi di immissione di una password corretta prima della cancellazione del dispositivo.|
|**Scadenza password (giorni)**|Specifica il numero di giorni dopo i quali è necessario modificare la password del dispositivo.
|**Ricorda cronologia password**|Specifica se consentire o meno l'uso di password usate in precedenza.|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che non possono più essere usate.|
|**Minuti di inattività prima che venga richiesta la password**|Specifica per quanto tempo il dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.

## Impostazioni di crittografia

|Nome impostazione|Dettagli|
|----------------|
|**Richiedi crittografia sul dispositivo mobile**<sup>1</sup>|Richiede la crittografia dei dati nel dispositivo, quando è supportata.<br>Per i dispositivi Windows Phone 8, è necessario impostare su **Sì**.<br /><br />Per abilitare la crittografia su dispositivi iOS, abilitare l'impostazione **richiedono una password per sbloccare i dispositivi mobili**.|
|**Richiedi crittografia sulle schede di memoria**|Richiede la crittografia dei dati presenti nella risorsa di archiviazione esterna, ad esempio una scheda SD (su dispositivi supportati).
<sup>1</sup> Altre informazioni per i dispositivi che eseguono Windows 8.1

-   Per applicare la crittografia su dispositivi che eseguono Windows 8.1, è necessario installare il [dicembre 2014 MDM aggiornamento del client per Windows](http://support.microsoft.com/kb/3013816) su ogni dispositivo.

-   Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un Account Microsoft.

-   Per la crittografia funzioni, il dispositivo deve soddisfare Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) requisiti di certificazione hardware.

-   Quando si applica la crittografia in un dispositivo, la chiave di ripristino è accessibile solo da utenti Account Microsoft, accessibili dal proprio account OneDrive. È possibile ripristinare la chiave per conto dell'utente.

## Impostazioni di posta elettronica

|Nome impostazione|Dettagli
|----------------|
|**Consentire agli utenti di scaricare gli allegati di posta elettronica.**|Specifica se gli allegati di posta elettronica possono essere scaricati sul dispositivo.|
|**Periodo di sincronizzazione della posta elettronica.**|Selezionare il numero di giorni in cui i messaggi ricevuti verranno sincronizzati con il dispositivo.
|**Consentire ai dispositivi mobili che non supportano completamente le impostazioni di Exchange ActiveSync per la sincronizzazione con Exchange**|Specifica se consentire a Exchange di accedere ai dispositivi che non supportano una o più impostazioni di Exchange ActiveSync.

## Impostazioni del browser

|Nome impostazione|Dettagli
|----------------|-
|**Consenti browser Web**|Specifica se è consentito l'uso del Web browser nel dispositivo.<br>Opzione non disponibile per Windows RT o Windows Phone.

## Impostazioni hardware

|Nome impostazione|Dettagli
|----------------|
|**Consenti dispositivo foto/video**|Specifica se è consentito l'uso della fotocamera del dispositivo.<br>Opzione non disponibile per Windows RT o Windows Phone.



### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jul16_HO3-->


