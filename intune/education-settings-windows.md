---
title: Impostazioni Istruzione di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni Istruzione per i dispositivi Windows 10. Usare queste impostazioni in un profilo di configurazione del dispositivo con l'app Test ed esami, scegliere la modalità di accesso di utenti e studenti, monitorare lo schermo durante il test e altro ancora in Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07d3488d509339fc48eb8449b12725b757775eb5
ms.sourcegitcommit: 98f2597eec28c6096985d5a1acae72430c2afb1a
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877984"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configurare l'app Test ed esami nei dispositivi Windows 10 tramite Intune

L'app Take a test consente di amministrare in modo sicuro i test online sui dispositivi Windows 10 della tua classe. Per configurare l'app Take a test, è necessario creare un profilo di configurazione del dispositivo in Intune e configurare le impostazioni di valutazione sicura. Questo articolo descrive le impostazioni disponibili per l'app di test. 

Dopo aver configurato il profilo, assegnarlo e distribuirlo agli studenti. 

L'[app Test ed esami in Intune](education-settings-configure.md) offre altre informazioni su questa funzionalità.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Impostazioni di Test ed esami
Dopo aver creato un profilo di configurazione del dispositivo, passare a **profilo tipo** e selezionare **valutazione sicura (istruzione)** . Di seguito sono riportate le impostazioni dell'app di test. 


- **Tipo di account**: scegliere la modalità di accesso degli utenti al test. Le opzioni disponibili sono:
  - Account di Azure AD
  - Account di dominio
  - Account locale
  - Account Guest locale: disponibile solo nei dispositivi che eseguono Windows 10, versione 1903 e successive.    
- **Nome utente dell'account**: immettere il nome utente dell'account usato con l'app Test ed esami. È possibile immettere gli account nel formato seguente:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Nome account**: per configurare un tipo di account Guest locale, immettere il nome dell'account usato con l'app di test. Il nome dell'account verrà visualizzato come riquadro nella schermata di accesso. Gli studenti fanno clic sul riquadro per avviare il test.  
- **URL della valutazione**: immettere l'URL del test che dovrà essere eseguito dagli utenti. Per altre informazioni su come ottenere l'URL, vedere la [documentazione relativa a Test ed esami](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Connessione stampante**: scegliere **Richiedi** per consentire l'accesso solo a un'app di test da dispositivi connessi a una stampante. Questa impostazione rende anche disponibile il pulsante stampa dell'app per i test-acquirenti. **Non configurato** consente agli studenti di accedere all'app da dispositivi non connessi a una stampante.  
- **Monitoraggio dello schermo**: scegliere **Consenti** per monitorare l'attività dello schermo mentre gli utenti eseguono il test. L'opzione **Non configurato** impedisce il monitoraggio dello schermo durante il test.
- **Suggerimenti di testo**: scegliere **Consenti** per consentire a chi esegue il test di visualizzare i suggerimenti di testo. **Non configurato**: blocca i suggerimenti di testo mentre gli utenti eseguono il test.

## <a name="next-steps"></a>Passaggi successivi

Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
