---
title: Come rimuovere il dispositivo Android da Intune | Microsoft Docs
description: Rimuovere il dispositivo Android dal portale aziendale Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: be980a8cd2eb7f0cbe40002f73f9bc36a36d1193
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859067"
---
# <a name="unenroll-your-android-device-from-management"></a>Annullare la registrazione del dispositivo Android dalla gestione  

Rimuovere un dispositivo Android registrato in modo che non sia più gestito dalla propria organizzazione. Questo articolo descrive come rimuovere il dispositivo dall'app Portale aziendale. Dopo aver rimosso il dispositivo:  

* Il dispositivo perde l'accesso alle risorse e ai dati protetti dell'organizzazione.
* Il dispositivo non viene più visualizzato nel Portale aziendale.
* Non è possibile installare app dal Portale aziendale.
* Non saranno più valide le impostazioni modificate nel dispositivo quando questo è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza.  

> [!NOTE]
> Non è possibile annullare la registrazione o rimuovere il dispositivo di proprietà dell'azienda dall'app Microsoft Intune. Il dispositivo è stato registrato durante la configurazione iniziale del dispositivo e deve essere registrato per accedere alle risorse dell'organizzazione.  

1. Nel Portale aziendale andare all'angolo superiore destro e toccare i tre punti verticali. Si apre il menu di azione.

   ![Screenshot dell'app Portale aziendale per Android, con il menu Azione aperto nell'angolo in alto a destra. La nuova opzione "Remove company portal" (Rimuovi portale aziendale) è disponibile come terza opzione dopo "Profilo personale" e "Impostazioni" e prima di "Termini e condizioni", "Guida e commenti e suggerimenti" e "Informazioni su".](./media/android_remove_cp_menu_action_after_1705.png)

2. Toccare **Rimuovi il portale aziendale**.  

3. Viene visualizzato un messaggio che spiega cosa accade dopo che viene annullata la registrazione del dispositivo. Toccare **OK** per confermare che si vuole rimuovere il dispositivo dal Portale aziendale.

   ![Screenshot della conferma visualizzata dopo aver selezionato la nuova funzione Rimuovi il portale aziendale dal menu Azione.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>Rimuovere i dati raccolti dall'app Portale aziendale  

Per rimuovere tutti i dati archiviati dall'app Portale aziendale per Android nel dispositivo:

- Cancellare i dati dell'app toccando **Applicazioni** > **[*nome dell'app*]**  > **Cancella dati**.
- Eliminare la cartella seguente: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>Disinstallare l'app Portale aziendale

Portale aziendale è un'app per la gestione dei dispositivi. Non può essere disinstallata finché non si annulla la registrazione del dispositivo dalla relativa gestione. Dopo aver eseguito questa operazione, toccare e tenere premuta l'icona dell'app Portale aziendale finché non viene visualizzato **Disinstalla**. Toccare **Disinstalla** per rimuovere l'app dal dispositivo.  

In alternativa, toccare **Impostazioni** > **App** > **Portale aziendale** > **Disinstalla**.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>Rimuovere l'app Portale aziendale come amministratore del dispositivo

Come ultima risorsa, è possibile disinstallare l'app dal dispositivo come amministratore del dispositivo.  

Se si usa un dispositivo aziendale, l'organizzazione potrebbe richiedere la disponibilità continua di Portale aziendale nel dispositivo. Se si disinstalla l'app, è possibile perdere l'accesso alle risorse aziendali protette, ad esempio la posta elettronica, le app, il Wi-Fi o la rete VPN, finché l'app non viene reinstallata. Per altre informazioni su installazione, aggiornamento o rimozione di app necessarie, vedere [Aggiungere app in Microsoft Intune](/intune/apps/apps-add#apps-that-are-added-automatically-by-intune).

Di seguito viene spiegato come disabilitare Portale aziendale come amministratore del dispositivo. I nomi reali delle impostazioni possono variare in base al dispositivo Android.  

**Opzione 1**:  

1. Selezionare **Impostazioni** > **Sicurezza** > **Impostazioni di protezione aggiuntive** > **Amministratori dei dispositivi** .  
2. Cancellare la selezione **Portale aziendale**.  

**Opzione 2**:

1. Selezionare **Impostazioni** > **Schermata di blocco e sicurezza** > **Altre impostazioni di sicurezza** > **Device admin apps** (App di amministrazione dispositivi).
2. Cancellare la selezione **Portale aziendale**.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
