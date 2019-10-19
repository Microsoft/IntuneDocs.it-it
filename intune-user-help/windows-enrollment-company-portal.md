---
title: Registrazione di un dispositivo Windows in Portale aziendale Intune | Microsoft Docs
description: Introduzione alla registrazione di un dispositivo Windows nel portale aziendale
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86aeb2b54d45f111864d71e65b8c90fce7205868
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508031"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Registrazione di un dispositivo Windows in Portale aziendale Intune  

Registrare il dispositivo Windows nell'app Portale aziendale di Intune per ottenere accesso sicuro alle app, ai messaggi di posta elettronica e ai file per il lavoro e la scuola. Se l'organizzazione richiede o consiglia app specifiche, come Office o OneDrive, queste verranno ricevute durante la registrazione o saranno disponibili nel portale aziendale dopo la registrazione.  

È possibile registrare i dispositivi Windows 10 tramite il sito Web *o* l'app Portale aziendale. Per registrare un dispositivo con una versione precedente di Windows, è necessario registrare il dispositivo tramite il sito Web Portale aziendale.  

## <a name="install-company-portal-app"></a>Installare l'app Portale aziendale  
È possibile che l'app Portale aziendale sia già installata nel dispositivo. Cercare l'app nell'elenco __Tutte le app__.  Se l'app Portale aziendale non è visualizzata nell'elenco di app, seguire questa procedura per installarla.  

1. Aprire **Microsoft Store** nel dispositivo.

2. Nel campo **Cerca** digitare **Portale aziendale**.

3. Nell'elenco dei risultati selezionare **Portale aziendale** > **Installa**.

4. Selezionare **Installa** o **Gratuito**. Non c'è alcuna differenza tra queste due opzioni, che vengono visualizzate in base al modo in cui l'organizzazione configura l'app.  

## <a name="find-windows-10-version-number"></a>Trovare il numero di versione di Windows 10  
La procedura di registrazione è diversa per versioni differenti dei dispositivi Windows 10. La procedura seguente descrive come trovare il numero di versione nei desktop e nei dispositivi mobili con Windows 10. Dopo avere stabilito la versione in uso, continuare con la procedura consigliata per la registrazione.  

### <a name="windows-10-desktop-devices"></a>Dispositivi Windows 10 Desktop  

1. Fare clic su **Start**.

2. Nella barra di ricerca digitare la frase "informazioni sul PC". Selezionare __Informazioni sul PC__ nei risultati.  


   ![impostazioni di ricerca per Informazioni sul PC](media/searching_for_about_your_pc.png)  

3. Scorrere verso il basso fino a **Specifiche Windows** per trovare la **Versione** di Windows 10 installata nel PC.  


   ![Windows 10 Desktop - Informazioni sul PC](media/settings_about_pc.png)  

4. Se la versione è  

    * __1607 o successive__: registrare il dispositivo tramite il [percorso **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 o precedenti__: registrare il dispositivo tramite il [percorso **Impostazioni** > **Account** > **Il tuo account**](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Dispositivi Windows 10 Mobile

1. Passare a __Tutte le app__ e selezionare l'app __Impostazioni__.
2. Selezionare __Sistema__ > __Informazioni__.
3. In __Informazioni sul dispositivo__ trovare __Versione__.  
4. Se la versione è  

    * __1607 o successive__: registrare il dispositivo tramite il [percorso **Impostazioni** > **Accedi all'azienda o all'istituto di istruzione**](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 o precedenti__: registrare il dispositivo tramite il [percorso **Impostazioni** > **Account**](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Registrare dispositivi non Windows 10  
Usare gli articoli seguenti per registrare altri dispositivi Windows supportati tramite il sito Web Portale aziendale:   
* [Dispositivo Windows 8.1. o Windows RT 8.1](enroll-your-W81-or-rt81-windows.md)  
* [Dispositivo Windows Phone 8.1](enroll-your-wp81-windows.md)    

## <a name="it-administrator-support"></a>Supporto per amministratori IT  
Gli amministratori IT che riscontrano problemi durante la registrazione dei dispositivi possono vedere [Risoluzione dei problemi di registrazione dei dispositivi Windows in Microsoft Intune](https://support.microsoft.com/help/4469913). Questo articolo elenca gli errori comuni, le cause e le procedure per risolverli.  

## <a name="next-steps"></a>Passaggi successivi  
Ora che sono noti i dispositivi supportati e il numero di versione di Windows 10, passare all'articolo consigliato per la registrazione.  
 
Per altre informazioni sulla gestione dei dispositivi, il portale aziendale e come vengono usate entrambe queste funzionalità in ambito aziendale e scolastico, vedere gli articoli seguenti:  
* [Usare dispositivi gestiti per accedere alle risorse aziendali o dell'istituto di istruzione](use-managed-devices-to-get-work-done.md)  
* [Cosa accade quando si registra il dispositivo in Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [Quali sono le informazioni visibili per l'organizzazione quando si registra il dispositivo?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

Serve assistenza? Contattare l'amministratore IT. [Visitare il sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per trovare le informazioni di contatto IT per l'organizzazione.  
