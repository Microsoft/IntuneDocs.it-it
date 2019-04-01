---
title: Registrazione del dispositivo Windows nel portale aziendale di Intune | Microsoft Docs
description: Introduzione alla registrazione di un dispositivo Windows nel portale aziendale
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: a637b6eed162243d2be81ac08fbcc055e1fd5816
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069179"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Registrazione del dispositivo Windows nel portale aziendale di Intune  

Registrare il dispositivo Windows in all'app portale aziendale di Intune di ottenere accesso sicuro al lavoro e App dell'istituto di istruzione, messaggi di posta elettronica e i file. Se l'organizzazione richiede o si consiglia di alcune App, ad esempio Office o OneDrive, è possibile ricevere li durante la registrazione o sarà disponibile nel portale aziendale dopo la registrazione.  

È possibile registrare i dispositivi Windows 10 tramite il sito Web portale aziendale *o* app. Se si vuole registrare un dispositivo con una versione precedente di Windows, è necessario registrare il dispositivo tramite il sito Web portale aziendale.  

## <a name="install-company-portal-app"></a>App portale aziendale di installazione  
Se si dispone già l'app portale aziendale installata nel dispositivo. Cercare l'app nel __tutte le app__ elenco.  Se l'app Portale aziendale non è visualizzata nell'elenco di app, seguire questa procedura per installarla.  

1. Aprire **Microsoft Store** nel dispositivo.

2. Nel **ricerca** , digitare **portale aziendale**.

3. Nell'elenco dei risultati selezionare **Portale aziendale** > **Installa**.

4. Selezionare **Installa** o **Gratuito**. Non c'è alcuna differenza tra queste due opzioni; le parole vengono visualizzati in base sul modo in cui l'organizzazione configura l'app.  

## <a name="find-windows-10-version-number"></a>Trovare il numero di versione di Windows 10  
Procedura di registrazione sono diverse per versioni diverse dei dispositivi Windows 10. I passaggi seguenti descrivono come trovare il numero di versione in Windows 10 desktop e dispositivi mobili. Dopo avere stabilito la versione in uso, continuare con i passaggi di registrazione consigliati.  

### <a name="windows-10-desktop-devices"></a>Dispositivi Windows 10 Desktop  

1. Fare clic su **Start**.

2. Nella barra di ricerca, digitare la frase "informazioni sul"PC. Selezionare __informazioni sul PC__ dai risultati.  


   ![impostazioni di ricerca per Informazioni sul PC](media/searching_for_about_your_pc.png)  

3. Scorrere verso il basso **specifiche di Windows** per trovare il **versione** di Windows 10 che è installato nel PC.  


   ![Windows 10 Desktop - Informazioni sul PC](media/settings_about_pc.png)  

4. Se la versione è  

    *  __1607 o successiva__: registrare il dispositivo tramite il [ **impostazioni** > **Account** > **accesso azienda o dell'istituto di istruzione**route](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 o versioni precedenti__: registrare il dispositivo tramite il [ **impostazioni** > **Account** > **gli account** route](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Dispositivi Windows 10 Mobile       

1.  Passare a __tutte le app__ e selezionare il __impostazioni__ app.  
2.  Selezionare __Sistema__ > __Informazioni__.      
3.  Sotto __le informazioni sul dispositivo__, trovare il __versione__.  
4. Se la versione è  

    *  __1607 o successiva__: registrare il dispositivo usando il [ **impostazioni** > **accesso azienda o dell'istituto di istruzione** route](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 o versioni precedenti__: registrare il dispositivo usando il [ **impostazioni** > **account** route](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Registrare i dispositivi non Windows 10  
Usare gli articoli seguenti per registrare altri dispositivi di Windows supportati tramite il sito Web portale aziendale:   
* [Dispositivo Windows 8.1. o Windows RT 8.1](enroll-your-W81-or-rt81-windows.md)  
* [Dispositivo Windows Phone 8.1](enroll-your-wp81-windows.md)    

## <a name="next-steps"></a>Passaggi successivi  
Ora che sai che i dispositivi supportati e il numero di versione di Windows 10, passare all'articolo di registrazione consigliati.  
 
Per altre informazioni sulla gestione dei dispositivi, portale aziendale, e come vengono utilizzati nelle scuole e in ufficio, vedere gli articoli seguenti:  
* [Usare dispositivi gestiti per accedere alle risorse aziendali o dell'istituto di istruzione](use-managed-devices-to-get-work-done.md)  
* [Cosa accade quando si registra il dispositivo in Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [Quali sono le informazioni visibili per l'organizzazione quando si registra il dispositivo?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

Serve assistenza? Contattare l'amministratore IT. [Visitare il sito Web portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per trovare l'organizzazione IT le informazioni di contatto.  
