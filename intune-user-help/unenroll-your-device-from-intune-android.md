---
title: Come rimuovere il dispositivo Android da Intune | Microsoft Docs
description: Descrive come annullare la registrazione di un dispositivo Android da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
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
ms.openlocfilehash: d932005c955afed7f16e9766b559b77b2cd43182
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959486"
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
Portale aziendale è un'app di gestione dei dispositivi, che pertanto non può essere disinstallata finché non si [annulla la registrazione del dispositivo dalla relativa gestione](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). Dopo aver eseguito questa operazione, toccare e tenere premuta l'icona dell'app Portale aziendale finché non viene visualizzato **Disinstalla**. Toccare **Disinstalla** per rimuovere l'app dal dispositivo.  

In alternativa, toccare **Impostazioni** > **App** > **Portale aziendale** > **Disinstalla**.  

Serve ancora assistenza? Contattare l'amministratore IT. Per le informazioni di contatto, visitare il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980)
