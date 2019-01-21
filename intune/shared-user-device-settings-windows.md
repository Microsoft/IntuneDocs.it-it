---
title: Impostazioni dei dispositivi condivisi Windows 10 - Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere e usare Windows 10 per configurare dispositivi condivisi o usati da più utenti in Microsoft Intune. Visualizzare un elenco di tutte le impostazioni e delle loro funzioni nei dispositivi, inclusi i dispositivi Microsoft Surface. Controllare gli account Guest, gestire gli account ed eliminare quelli inattivi, consentire o impedire il salvataggio nella risorsa di archiviazione locale, impostare le opzioni di alimentazione e sospensione, scegliere quando installare gli aggiornamenti e usare i dispositivi in ambienti di formazione in un profilo di configurazione del dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: fb51ba835491da284ddd304bc038d16862c6dfc1
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2019
ms.locfileid: "54205103"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Impostazioni di Windows 10 e versioni successive per la gestione dei dispositivi condivisi con Intune

I dispositivi Windows 10 e versioni successive, ad esempio Microsoft Surface, possono essere usati da molti utenti. I dispositivi con più utenti, detti dispositivi condivisi, fanno parte di soluzioni di gestione di dispositivi mobili (MDM, Mobile Device Management).

Con Microsoft Intune gli utenti finali possono accedere a tali dispositivi condivisi con un account Guest. Quando usano il dispositivo, possono accedere solo alle funzionalità loro consentite. Gli amministratori di Intune, tra l'altro, configurano l'accesso, scelgono quando eliminare gli account, controllano le impostazioni di risparmio energia per i dispositivi Windows 10 condivisi.

Questo articolo elenca e descrive le impostazioni usate in un profilo di configurazione di dispositivi Windows 10 e versioni successive. Quando il profilo viene creato in Intune, l'amministratore lo distribuisce o lo assegna ai gruppi di dispositivi nell'organizzazione. Il profilo può anche essere assegnato a gruppi di dispositivi contenenti tipi di dispositivo e versioni del sistema operativo diversi.

Per altre informazioni su questa funzionalità in Intune, vedere [Controllare l'accesso, gli account e le funzionalità di risparmio energia nei PC condivisi o nei dispositivi con più utenti](shared-user-device-settings.md). Per altre informazioni sul provider di servizi di configurazione di Windows, vedere [SharedPC CSP](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp) (Provider di servizi di configurazione SharedPC).

## <a name="before-your-begin"></a>Prima di iniziare

[Creare il profilo](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Impostazioni dei dispositivi multiutente condivisi

- **Modalità Computer condiviso**: Scegliere **Abilita** per attivare la modalità Computer condiviso. In questa modalità, può accedere al dispositivo un solo utente alla volta. Un altro utente può accedere solo quando il primo si disconnette. **Non configurata** (impostazione predefinita) lascia questa impostazione non gestita da Intune e non esegue il push di alcun criterio al dispositivo per controllare questa impostazione.
- **Account Guest**: consente di scegliere di creare un'opzione Guest nella schermata di accesso. Gli account Guest non richiedono credenziali o autenticazione utente. Questa impostazione crea un nuovo account locale ogni volta che viene usata. Le opzioni disponibili sono:
  - **Guest**: crea un account Guest locale nel dispositivo.
  - **Dominio**: crea un account Guest in Azure Active Directory (AD).
  - **Guest e dominio**: crea un account Guest locale nel dispositivo e in Azure Active Directory (AD).
- **Gestione account**: impostare su **Abilita** per eliminare automaticamente gli account locali creati dagli utenti Guest e gli account in AD e in Azure AD. Quando un utente si disconnette dal dispositivo o quando viene eseguita la manutenzione del sistema, questi account vengono eliminati. Quando l'opzione è abilitata, impostare anche:
  - **Eliminazione account**: scegliere quando eliminare gli account: **In corrispondenza della soglia di spazio di archiviazione**, **In corrispondenza della soglia di spazio di archiviazione e della soglia di inattività** o **Immediatamente dopo la disconnessione**. Specificare anche:
    - **Soglia di inizio dell'eliminazione (%)**: immettere una percentuale (0-100) di spazio su disco. Quando lo spazio totale di archiviazione o su disco scende sotto il valore specificato, vengono eliminati gli account memorizzati nella cache. Gli account vengono eliminati in modo continuo per recuperare spazio su disco. Gli account inattivi da più tempo vengono eliminati per primi.
    - **Soglia di interruzione dell'eliminazione (%)**: immettere una percentuale (0-100) di spazio su disco. Quando lo spazio totale di archiviazione o su disco corrisponde al valore specificato, l'eliminazione viene interrotta.

  Impostare su **Disabilita** per mantenere gli account locali, AD e Azure AD creati dagli utenti guest.

- **Archiviazione locale**: scegliere **Abilitata** per impedire agli utenti di salvare e visualizzare file nel disco rigido del dispositivo. Scegliere **Disabilitata** per consentire agli utenti di visualizzare e salvare file in locale tramite Esplora file. **Non configurata** (impostazione predefinita) lascia questa impostazione non gestita da Intune e non esegue il push di alcun criterio al dispositivo per controllare questa impostazione.
- **Criteri per l'alimentazione**: se questa opzione è impostata su **Abilitati**, gli utenti non possono disabilitare l'ibernazione, eseguire l'override delle azioni di sospensione (ad esempio la chiusura del coperchio) o cambiare le impostazioni di risparmio energia. Se questa opzione è impostata su **Disabilitati**, gli utenti possono attivare l'ibernazione del dispositivo, chiudere il coperchio per sospendere il dispositivo e cambiare le impostazioni di risparmio energia. **Non configurati** (impostazione predefinita) lascia questa impostazione non gestita da Intune e non esegue il push di alcun criterio al dispositivo per controllare questa impostazione.
- **Timeout della sospensione (in secondi)**: immettere il numero di secondi di inattività (0-100) che devono trascorrere prima che il dispositivo passi alla modalità sospensione. Se non si imposta alcun valore, il dispositivo passa in modalità sospensione dopo 60 minuti.
- **Accedi alla riattivazione del computer**: impostare su **Abilitato** per richiedere agli utenti di accedere con la password quando il dispositivo esce dalla modalità sospensione. Scegliere **Disabilitato** perché gli utenti non debbano immettere il nome utente e la password. **Non configurato** (impostazione predefinita) lascia questa impostazione non gestita da Intune e non esegue il push di alcun criterio al dispositivo per controllare questa impostazione.
- **Ora di inizio della manutenzione (in minuti da mezzanotte)**: immettere l'ora di avvio dell'esecuzione delle attività di manutenzione automatica, ad esempio Windows Update, in minuti (0-1440). L'ora di avvio predefinito è mezzanotte, ovvero zero (`0`) minuti. Per cambiare l'ora di inizio, immettere un'ora in minuti successivi alla mezzanotte. Se ad esempio si vuole che la manutenzione inizi alle 2.00, immettere `120`. Se si vuole che la manutenzione inizi alle 20.00, immettere `1200`.
- **Criteri per la formazione**: scegliere **Abilitati** per usare le impostazioni consigliate per i dispositivi usati negli istituti di istruzione, più restrittive. Scegliere **Disabilitati** perché i criteri per la formazione predefiniti e consigliati non vengano usati. **Non configurati** (impostazione predefinita) lascia questa impostazione non gestita da Intune e non esegue il push di alcun criterio al dispositivo per controllare questa impostazione.

  Per altre informazioni sulla funzione dei criteri per la formazione, vedere [Consigli sulla configurazione di Windows 10 per i clienti del settore istruzione](https://docs.microsoft.com/education/windows/configure-windows-for-education).

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
- Vedere le impostazioni per [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).