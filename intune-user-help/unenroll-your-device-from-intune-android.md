---
title: Come rimuovere il dispositivo Android da Intune | Microsoft Docs
description: Descrive come annullare la registrazione di un dispositivo Android da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
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
ms.openlocfilehash: ec3c0a1c8ce4e04f4d23fb01e7c2525d8f2eed5b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018363"
---
# <a name="how-to-remove-your-android-device-from-intune"></a>Come rimuovere il dispositivo Android da Intune

Quando il dispositivo Android viene rimosso da Intune, non può più accedere alle risorse aziendali.  Per altre informazioni su cosa accade quando il dispositivo viene rimosso dalla gestione, vedere [Che cosa accade se si annulla la registrazione del dispositivo da Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md)

## <a name="removing-the-device-from-the-company-portal-app"></a>Rimozione del dispositivo dall'app Portale aziendale

Per rimuovere il dispositivo da Intune e rimuovere l'app Portale aziendale, seguire questa procedura:

1. Aprire il **menu Azione** toccando i tre puntini verticali nell'angolo in alto a destra dell'app Portale aziendale.

   ![Immagine dell'app Portale aziendale per Android, con il menu Azione aperto nell'angolo in alto a destra. La nuova opzione "Remove company portal" (Rimuovi portale aziendale) è disponibile come terza opzione dopo "Profilo personale" e "Impostazioni" e prima di "Termini e condizioni", "Guida e commenti e suggerimenti" e "Informazioni su".](./media/android_remove_cp_menu_action_after_1705.png)

2. Toccare **Rimuovi il portale aziendale**.

3. Verrà visualizzato un messaggio di conferma, in cui viene richiesto di confermare la rimozione dell'app Portale aziendale. Il messaggio fornisce alcune informazioni su cosa accade quando si annulla la registrazione del dispositivo. Dopo aver letto il messaggio, toccare **OK** per rimuovere l'app.

   ![Immagine della finestra di dialogo di conferma visualizzata dopo aver selezionato la nuova opzione "Remove company portal" (Rimuovi portale aziendale) dal menu Azione. La finestra di dialogo informa l'utente che "se si rimuove il portale aziendale, il dispositivo non sarà più gestito dall'amministratore IT ed è possibile che l'accesso ai dati, alle app e ai messaggi di posta elettronica aziendali venga rimosso." Viene quindi richiesto all'utente di confermare la rimozione dell'app Portale aziendale selezionando "Sì".](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Rimozione dei dati raccolti dall'app Portale aziendale

Per rimuovere tutti i dati archiviati dall'app Portale aziendale per Android nel dispositivo:

-   Cancellare tutti i dati dell'app in Applicazioni > selezionare l'app > pulsante di cancellazione dati
-   Eliminare la cartella '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal'

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
