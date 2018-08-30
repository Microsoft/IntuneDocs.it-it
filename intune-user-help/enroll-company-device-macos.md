---
title: Registrare un dispositivo macOS di proprietà dell'azienda o fornito dall'azienda nella gestione | Microsoft Docs
description: Informazioni su come registrare in Intune un dispositivo macOS acquistato e fornito dall'organizzazione.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 272a82f7d3d62d117fa5506ccf446b3169ff514f
ms.sourcegitcommit: bb56ada81e6d4950f130415918c4acc455bb52dd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43016228"
---
# <a name="get-your-company-owned-macos-device-managed"></a>Registrare per la gestione un dispositivo macOS di proprietà dell'azienda

Informazioni su come gestire automaticamente in Intune un nuovo dispositivo macOS.

I dispositivi di proprietà dell'azienda o dell'istituto di istruzione spesso vengono forniti preconfigurati. L'organizzazione invia impostazioni preconfigurate al dispositivo alla prima accensione e al primo accesso. Al termine della configurazione del dispositivo, si otterrà l'accesso alle risorse aziendali o dell'istituto di istruzione. 

Per avviare la configurazione per la gestione, accendere il dispositivo e accedere con le credenziali aziendali o dell'istituto di istruzione. Il resto di questo articolo descrive i passaggi e le schermate visualizzati durante l'utilizzo dell'Assistente configurazione.   

## <a name="what-is-apple-dep"></a>Che cos'è il programma DEP di Apple?
Un dispositivo di proprietà dell'azienda potrebbe essere stato acquistato con il programma DEP (Device Enrollment Program) Apple. Alcune organizzazioni acquistano grandi quantità di dispositivi iOS o macOS tramite il programma DEP di Apple. Le organizzazioni possono quindi configurare e gestire i dispositivi all'interno del provider di gestione dei dispositivi mobili preferito, ad esempio Intune. Gli amministratori che vogliono consultare altre informazioni sul programma DEP di Apple possono vedere [Registrare automaticamente i dispositivi macOS nel programma Device Enrollment Program di Apple](https://docs.microsoft.com/intune/device-enrollment-program-enroll-macos).  

## <a name="set-up-your-macos-device"></a>Configurare il dispositivo macOS  
Seguire questa procedura per registrare il dispositivo macOS nella gestione. Se si usa il dispositivo personale, invece di un dispositivo aziendale, seguire questa procedura per i [dispositivi personali e BYOD](enroll-your-device-in-intune-macos-cp.md).  

1. Accendere il dispositivo macOS. 
2. Scegliere la **lingua** e fare clic su **Continua**.  

   ![Screenshot della schermata iniziale dell'Assistente configurazione per il dispositivo macOS, che mostra un elenco di lingue per la selezione.](./media/macos-dep-welcome-1808.png)   
3. Scegliere un layout di tastiera. L'elenco mostra una o più opzioni in base alla lingua selezionata. Per visualizzare tutte le opzioni di layout, indipendentemente dalla lingua selezionata, fare clic su **Mostra tutto**. Al termine dell'operazione fare clic su **Continua**.  

   ![Screenshot della schermata Layout di tastiera dell'Assistente configurazione per il dispositivo macOS, che mostra un elenco delle lingue della tastiera per la selezione, l'opzione Mostra tutto non selezionata e i pulsanti Indietro e Continua.](./media/macos-dep-keyboard-1808.png)  
4. Selezionare la rete Wi-Fi. È necessario disporre di una connessione Internet per continuare con la configurazione. Se la rete non è visibile o se è necessario connettersi tramite una rete cablata, fare clic su **Other Network Options** (Altre opzioni di rete). Al termine dell'operazione fare clic su **Continua**.  

   ![Screenshot della schermata Select Your Wi-Fi Network (Seleziona rete Wi-Fi) dell'Assistente configurazione per il dispositivo macOS che mostra un elenco delle reti disponibili tra cui scegliere. Sono visibili anche i pulsanti Other Network Options (Altre opzioni di rete), Indietro e Continua.](./media/macos-dep-wifi-1808.png)  
5. Dopo la connessione alla rete Wi-Fi, viene visualizzata la schermata **Gestione remota**. La gestione remota consente all'amministratore dell'organizzazione di configurare in remoto il dispositivo con gli account, le impostazioni, le app e le reti richiesti dall'organizzazione. Prima di procedere, leggere la documentazione per comprendere come vengono gestiti i dispositivi. Fare clic su **Continua**.  

   ![Screenshot della schermata Gestione remota dell'Assistente configurazione per un dispositivo macOS, con il testo che descrive la gestione remota e un collegamento alla documentazione per altre informazioni. Sono visualizzati anche i pulsanti Indietro e Continua.](./media/macos-dep-remote-management-1-1808.png)  
6. Quando richiesto, accedere con l'account aziendale o dell'istituto di istruzione. Dopo l'autenticazione, il dispositivo installerà un profilo di gestione. Il profilo configura e abilita l'accesso alle risorse dell'organizzazione.  
7. Leggere le informazioni sulla privacy e sulla gestione dei dati Apple, in modo da poter identificare in seguito le situazioni in cui vengono raccolte informazioni personali. Fare clic su **Continua**.  

   ![Screenshot della schermata Data & Privacy (Dati e privacy) dell'Assistente configurazione per un dispositivo macOS, che mostra un'illustrazione di due persone che si stringono la mano e descrivono l'uso delle informazioni personali da parte di Apple. Sono visualizzati anche i pulsanti Indietro e Continua.](./media/macos-dep-apple-data-privacy-1808.png)  
8. Dopo aver registrato il dispositivo, potrebbe essere necessario eseguire altri passaggi. I passaggi illustrati variano a seconda di come l'organizzazione ha personalizzato l'esperienza di installazione. Potrebbe essere richiesto di:
    * Accedere a un account Apple
    * Accettare i termini e le condizioni
    * Creare un account computer
    * Eseguire una configurazione rapida
    * Configurare il Mac  
## <a name="get-the-company-portal-app"></a>Scaricare l'app Portale aziendale      
Passare ad App Store per scaricare l'app Portale aziendale di Intune nel dispositivo. L'app consente di monitorare, sincronizzare, aggiungere e rimuovere il dispositivo dalla gestione e di installare app.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
