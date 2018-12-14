---
title: Configurare la pagina dello stato della registrazione
titleSuffix: Microsoft Intune
description: Dare il benvenuto agli utenti che stanno effettuando la registrazione di dispositivi Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b953ea281ad785d8a0ce7bee4b0f6d420b785dd9
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52729042"
---
# <a name="set-up-an-enrollment-status-page"></a>Configurare la pagina dello stato della registrazione
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Durante la configurazione dei dispositivi, la pagina relativa allo stato della registrazione visualizza le informazioni sull'installazione nel dispositivo. Alcune applicazioni, profili e certificati potrebbero non essere installati fino a quando l'utente non completa la registrazione guidata del dispositivo. Una pagina relativa allo stato della registrazione consente agli utenti di conoscere lo stato del dispositivo durante l'installazione. È possibile creare più profili di pagina dello stato della registrazione e applicarli a gruppi diversi. I profili possono essere impostati su:
- Visualizzazione dello stato di installazione.
- Blocco dell'utilizzo fino al completamento dell'installazione.
- Specificare le azioni che possono essere eseguite dall'utente se l'installazione non viene eseguita.

È anche possibile impostare l'ordine di priorità di ogni profilo per tenere conto delle assegnazioni dei profili in conflitto per lo stesso utente o dispositivo.

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Attivare la pagina relativa allo stato della registrazione predefinita per tutti gli utenti

Per attivare la pagina dello stato della registrazione, eseguire i passaggi descritti di seguito.
 
1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Enrollment Status Page (Preview)** (Pagina stato registrazione (anteprima)).
2. Nel pannello **Enrollment Status Page** (Pagina stato registrazione) scegliere **Predefinito** > **Impostazioni**.
3. Per **Show app and profile installation progress** (Visualizza stato di avanzamento installazione app e profilo), scegliere **Sì**.
4. Scegliere le altre impostazioni che si vuole attivare e selezionare **Salva**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Creare il profilo della pagina dello stato della registrazione e assegnarlo a un gruppo

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Pagina relativa allo stato della registrazione (anteprima)** > **Crea profilo**.
2. Specificare un **nome** e una **descrizione**.
3. Scegliere **Crea**.
4. Scegliere il nuovo profilo nell'elenco **Pagina relativa allo stato della registrazione**.
5. Scegliere **Assegnazioni** > **Selezionare i gruppi** > scegliere i gruppi che devono adottare questo profilo > **Seleziona** > **Salva**.
6. Scegliere **Impostazioni** > scegliere le impostazioni che si vuole applicare a questo profilo > **Salva**.

## <a name="set-the-enrollment-status-page-priority"></a>Impostare la priorità della pagina dello stato della registrazione

Un dispositivo o un utente può essere incluso in più gruppi e avere più profili della pagina dello stato della registrazione. Per risolvere questi conflitti, è possibile impostare le priorità per ogni profilo. Se un utente ha più di un profilo della pagina dello stato della registrazione, verrà applicato solo il profilo con la priorità più alta.

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Enrollment Status Page (Preview)** (Pagina stato registrazione (anteprima)).
2. Passare il mouse sul profilo nell'elenco.
3. Usando i tre punti verticali, trascinare il profilo sulla posizione desiderata nell'elenco.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Impedire l'accesso a un dispositivo fino a quando non viene installata un'applicazione specifica

È possibile specificare le app da installare prima che l'utente possa accedere al desktop.

1. In Intune scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Pagina relativa allo stato della registrazione (anteprima)**.
2. Scegliere un profilo > **Impostazioni**.
3. Scegliere **Sì** per **Mostra lo stato dell'installazione di app e profili**.
4. Scegliere **Sì** per **Impedisci l'uso del dispositivo fino al completamento dell'installazione di tutte le app e di tutti i profili**.
5. Scegli **Selezionate** per **Blocca l'uso del dispositivo fino all'installazione delle app necessarie in caso di assegnazione a un utente/dispositivo**.
 6. Scegliere **Selezionare le app** > scegliere le app > **Seleziona** > **Salva**.

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
- Profili di connettività
    - I profili VPN o Wi-Fi sono assegnati a **tutti i dispositivi** o un gruppo di dispositivi di cui il dispositivo di registrazione è membro, ma solo per i dispositivi di Autopilot
- I profili di certificato sono assegnati a **tutti i dispositivi** o un gruppo di dispositivi di cui il dispositivo di registrazione è membro, ma solo per i dispositivi di Autopilot

### <a name="account-setup"></a>Configurazione dell'account
Per la configurazione dell'account, la pagina dello stato della registrazione tiene traccia degli elementi seguenti:
- Criteri di sicurezza
    - Un provider di servizi di configurazione per tutte le registrazioni.
    - I provider di servizi di configurazione configurati da Intune non vengono tracciati qui.
- Applicazioni
    - Le app line-of-business di identità del servizio gestita per utente assegnate a tutti i dispositivi, a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.
    - Le app line-of-business di identità del servizio gestita per computer assegnate a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.
    - App dello store line-of-business, le app dello store online e le app dello store offline che vengono assegnate a uno degli elementi seguenti:
        - Tutti i dispositivi
        - Tutti gli utenti
        - Un gruppo utenti in cui l'utente che registra il dispositivo è un membro con il contesto di installazione impostato su Utente.
- Profili di connettività
    - I profili VPN o Wi-Fi assegnati a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.
- Certificati
    - I profili di certificato assegnati a tutti gli utenti o a un gruppo di utenti di cui l'utente che registra il dispositivo è membro.

## <a name="next-steps"></a>Passaggi successivi
Dopo aver configurato le pagine di registrazione di Windows, è necessario imparare a gestire i dispositivi Windows. Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](https://docs.microsoft.com/intune/device-management).
