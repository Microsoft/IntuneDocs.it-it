---
title: Configurare la pagina dello stato della registrazione
titleSuffix: Microsoft Intune
description: Dare il benvenuto agli utenti che stanno effettuando la registrazione di dispositivi Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-an-enrollment-status-page"></a>Configurare la pagina dello stato della registrazione
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Durante la configurazione dei dispositivi, la pagina dello stato della registrazione consente di visualizzare le informazioni sul dispositivo dell'utente finale. Alcune applicazioni, profili e certificati potrebbero non essere ancora stati installati completamente nel momento in cui l'utente viene registrato. La pagina dello stato consente agli utenti di conoscere lo stato del dispositivo durante e dopo la registrazione. È possibile attivare la pagina dello stato per tutti gli utenti, nonché impedire agli utenti di usare il dispositivo finché tutte le applicazioni e i profili assegnati non sono stati installati.
 
Per attivare la pagina dello stato della registrazione per tutti gli utenti finali, seguire la procedura qui riportata.
 
1.  In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Enrollment Status Page (Preview)** (Pagina stato registrazione (anteprima)).
2.  Nel pannello **Enrollment Status Page** (Pagina stato registrazione) scegliere **Predefinito** > **Impostazioni**.
3.  Per **Show app and profile installation progress** (Visualizza stato di avanzamento installazione app e profilo), scegliere **Sì**.
4.  Scegliere le altre impostazioni che si vuole attivare e selezionare **Salva**.
 
## <a name="enrollment-status-page-tracking-information"></a>Informazioni incluse nella pagina dello stato della registrazione

La pagina dello stato della registrazione consente di tenere traccia delle informazioni relative alla preparazione e configurazione del dispositivo e dell'account.

### <a name="device-preparation"></a>Preparazione del dispositivo

Per la preparazione del dispositivo, la pagina dello stato della registrazione tiene traccia delle attestazioni delle chiavi TPM (Trusted Platform Module), laddove applicabile, dello stato di avanzamento dell'associazione a Azure Active Directory e della registrazione in Intune.

### <a name="device-setup"></a>Configurazione del dispositivo

Per la configurazione del dispositivo, la pagina dello stato della registrazione tiene traccia degli elementi seguenti se vengono assegnati a tutti i dispositivi:
- Criteri di sicurezza
    - Un provider di servizi di configurazione per tutte le registrazioni.
    - I provider di servizi di configurazione configurati da Intune non vengono tracciati qui.
- Applicazioni
    - App line-of-business di identità del servizio gestita per computer.
    - App dello Store line-of-business con contesto di installazione = dispositivo.
    - App dello Store offline e line-of-business con contesto di installazione = dispositivo.
- I profili di connettività (VPN e Wi-Fi) non vengono ancora tracciati, pertanto indicheranno sempre "0 di 0".
- I certificati non vengono ancora tracciati, pertanto indicheranno sempre "0 di 0".

### <a name="account-setup"></a>Configurazione dell'account
Per la configurazione dell'account, la pagina dello stato della registrazione tiene traccia degli elementi seguenti:
- Criteri di sicurezza
    - Un provider di servizi di configurazione per tutte le registrazioni.
    - I provider di servizi di configurazione configurati da Intune non vengono tracciati qui.
- Applicazioni
    - Le app line-of-business di identità del servizio gestita per utente assegnate a tutti i dispositivi, a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.
    - Le app line-of-business di identità del servizio gestita per computer assegnate a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.
    - Le app line-of-business dello Store assegnate a tutti i dispositivi, a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro con contesto di installazione = utente.
    - Le app dello Store online assegnate a tutti i dispositivi, a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro con contesto di installazione = utente.
    - Le app dello Store offline assegnate a tutti i dispositivi, a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro con contesto di installazione = utente.
- Profili di connettività
    - I profili VPN o Wi-Fi assegnati a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.
- Certificati
    - I profili di certificato assegnati a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.

## <a name="next-steps"></a>Passaggi successivi
Dopo aver configurato le pagine di registrazione di Windows, è necessario imparare a gestire i dispositivi Windows. Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](https://docs.microsoft.com/intune/device-management).