---
title: Come rimuovere il dispositivo Android da Intune | Microsoft Docs
description: Rimuovere il dispositivo Android dal portale aziendale Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 75b26e178badbaa7905199eb91490134d2b72ba9
ms.sourcegitcommit: 61ed365f7f8826451c41bcab5e19bef97b5a3c72
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2019
ms.locfileid: "54057339"
---
# <a name="unenroll-your-android-device-from-management"></a>Annullare la registrazione del dispositivo Android dalla gestione  

Rimuovere un dispositivo Android registrato in modo che non sia più gestito dalla propria organizzazione. Questo articolo descrive come rimuovere il dispositivo dall'app Portale aziendale. Dopo aver rimosso il dispositivo:  

* Il dispositivo perde l'accesso alle risorse e ai dati protetti dell'organizzazione.
* Il dispositivo non viene più visualizzato nel Portale aziendale.
* Non è possibile installare app dal Portale aziendale.
* Non saranno più valide le impostazioni modificate nel dispositivo quando questo è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.  

1. Nel Portale aziendale andare all'angolo superiore destro e toccare i tre punti verticali. Si apre il menu di azione.

   ![Immagine dell'app Portale aziendale per Android, con il menu Azione aperto nell'angolo in alto a destra. La nuova opzione "Remove company portal" (Rimuovi portale aziendale) è disponibile come terza opzione dopo "Profilo personale" e "Impostazioni" e prima di "Termini e condizioni", "Guida e commenti e suggerimenti" e "Informazioni su".](./media/android_remove_cp_menu_action_after_1705.png)

2. Toccare **Rimuovi il portale aziendale**.  

3. Viene visualizzato un messaggio che spiega cosa accade dopo che viene annullata la registrazione del dispositivo. Toccare **OK** per confermare che si vuole rimuovere il dispositivo dal Portale aziendale.

   ![Immagine della finestra di dialogo di conferma visualizzata dopo aver selezionato la nuova opzione "Remove company portal" (Rimuovi portale aziendale) dal menu Azione. La finestra di dialogo informa l'utente che "se si rimuove il portale aziendale, il dispositivo non sarà più gestito dall'amministratore IT ed è possibile che l'accesso ai dati, alle app e ai messaggi di posta elettronica aziendali venga rimosso." Viene quindi richiesto all'utente di confermare la rimozione dell'app Portale aziendale selezionando "Sì".](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Rimozione dei dati raccolti dall'app Portale aziendale  

Per rimuovere tutti i dati archiviati dall'app Portale aziendale per Android nel dispositivo:

-   Cancellare tutti i dati dell'app in Applicazioni > selezionare l'app > pulsante di cancellazione dati
-   Eliminare la cartella '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal'

## <a name="uninstall-the-company-portal-app"></a>Disinstallare l'app Portale aziendale  
Portale aziendale è un'app per la gestione dei dispositivi. Non può essere disinstallata finché non si [annulla la registrazione del dispositivo dalla relativa gestione](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). Dopo aver eseguito questa operazione, toccare e tenere premuta l'icona dell'app Portale aziendale finché non viene visualizzato **Disinstalla**. Toccare **Disinstalla** per rimuovere l'app dal dispositivo.  

In alternativa, toccare **Impostazioni** > **App** > **Portale aziendale** > **Disinstalla**.  

### <a name="remove-company-portal-app-as-device-administrator"></a>Rimuovere l'app Portale aziendale come amministratore del dispositivo  
Come ultima risorsa, è possibile disinstallare l'app dal dispositivo rimuovendola come amministratore del dispositivo.  

Se si usa un dispositivo aziendale, l'organizzazione potrebbe richiedere la disponibilità continua di Portale aziendale nel dispositivo. Se si disinstalla l'app, si potrebbe perdere l'accesso alle risorse aziendali protette, ad esempio la posta elettronica, le app, il Wi-Fi o la rete VPN, finché l'app non viene reinstallata. Per altre informazioni su installazione, aggiornamento o rimozione di app necessarie, vedere [Aggiungere app in Microsoft Intune](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Completare la procedura seguente per disabilitare Portale aziendale come amministratore del dispositivo. I nomi reali delle impostazioni possono variare in base al dispositivo Android.  

**Procedura per Android, opzione 1**:  
1. Selezionare **Impostazioni** > **Sicurezza** > **Impostazioni di protezione aggiuntive** > **Amministratori dei dispositivi** .  
2. Cancellare la selezione **Portale aziendale**.  

**Procedura per Android, opzione 2**:  
1. Selezionare **Impostazioni** > **Schermata di blocco e sicurezza** > **Altre impostazioni di sicurezza** > **Device admin apps** (App di amministrazione dispositivi).  
2. Cancellare la selezione **Portale aziendale**.    

Serve ancora assistenza? Contattare l'amministratore IT. Per le informazioni di contatto, visitare il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980)
