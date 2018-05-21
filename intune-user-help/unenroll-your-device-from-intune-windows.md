---
title: Rimuovere il dispositivo Windows da Intune
description: Descrive come rimuovere un dispositivo Windows da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 1dd64250c1996c6b13c62f80572282d639112ba6
ms.sourcegitcommit: 8ee543c864097dc195b6f440471dca713fc21ed2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2018
---
# <a name="remove-your-windows-device-from-intune-management"></a>Rimuovere il dispositivo Windows dalla gestione di Intune

Un dispositivo Windows registrato può essere rimosso da Intune quando non si vuole (o non è più necessario):  
* Usare il dispositivo per gestire risorse aziendali o dell'istituto di istruzione. 
* Accedere a posta, app o altre risorse aziendali o dell'istituto di istruzione.

Dopo la rimozione non sarà possibile accedere alle risorse aziendali o dell'istituto di istruzione dal dispositivo. I dispositivi Windows che possono essere rimossi da Intune includono:  
* Dispositivi Windows 10 
* Computer Windows 8.1
* Dispositivi mobili Windows 8.1
 
Per altre informazioni su cosa accade quando il dispositivo viene rimosso dalla gestione di Intune, vedere [What happens if you remove your device from Intune](what-happens-if-you-unenroll-your-device-from-intune-windows.md) (Che cosa accade se si rimuove il dispositivo da Intune).

## <a name="remove-your-windows-10-device"></a>Rimuovere il dispositivo Windows 10
Per rimuovere da Intune un dispositivo Windows 10 seguire questa procedura.

### <a name="via-the-company-portal-app"></a>Tramite l'app Portale aziendale

1. Aprire l'app Portale aziendale.
2. Accedere con le credenziali aziendali o dell'istituto di istruzione.
3. Selezionare il dispositivo da rimuovere in **Dispositivi personali**.
4. Nell'angolo in alto a destra dell'app selezionare l'icona **Altre informazioni**.
5. Selezionare **Rimuovi**. 
6. Selezionare **Rimuovi dispositivo** per confermare la rimozione del dispositivo.

### <a name="via-device-settings-app"></a>Tramite l'app Impostazioni del dispositivo
1. Aprire l'app Impostazioni. 
2. Passare ad **Account** > **Accedi all'azienda o all'istituto di istruzione**.
3. Selezionare l'account connesso che si vuole rimuovere > **Disconnetti**.
4. Per confermare la rimozione del dispositivo selezionare **Sì**.

## <a name="remove-your-windows-81-computer"></a>Rimuovere il computer Windows 8.1
Per rimuovere da Intune un computer Windows 8.1 seguire questa procedura.

1.  Selezionare **Impostazioni PC** > **Rete** > **Area di lavoro**.
2.  In **Aggiunta all'area di lavoro** selezionare **Esci**.
3.  In **Turn on device management** (Attiva gestione dei dispositivi) selezionare **Disattiva**.
4.  Nella finestra popup visualizzata selezionare **Disattiva**.

## <a name="remove-your-windows-81-mobile-device"></a>Rimuovere il dispositivo mobile Windows 8.1
Per rimuovere da Intune un dispositivo mobile Windows 8.1 seguire questa procedura.

1.  Accedere a **Impostazioni** > **Area di lavoro**.
2.  Toccare l'account aziendale di cui si vuole annullare la registrazione.
3.  Nella parte inferiore della schermata toccare **Elimina**.
4.  Nella finestra di dialogo **Elimina account** toccare **Elimina**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Rimozione delle informazioni personali dopo avere rimosso il Portale aziendale
Esistono due tipi di dati archiviati dal Portale aziendale nel dispositivo Windows:

-   **Log di diagnostica**: i dati sulle attività dell'app standard raccolti da Microsoft vengono automaticamente cancellati quando si rimuove il dispositivo dal Portale aziendale. I dati dell'attività dell'app indicano ad esempio per quanto tempo è stata aperta l'app o se ha registrato un arresto anomalo.
-   **Cache dell'applicazione**: file di supporto necessari per il funzionamento dell'app, come icone e impostazioni.

Per eliminare completamente queste informazioni, è necessario seguire alcuni passaggi.

1. Disinstallare il Portale aziendale. La [disinstallazione dell'app Portale aziendale](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) rimuoverà alcuni dei dati dell'app archiviati nel dispositivo.  

2. Reimpostare il Portale aziendale per reimpostare i dati dell'app archiviati. Aprire l'app **Impostazioni** e selezionare **App** > **Portale aziendale** > **Opzioni avanzate** > **Reimposta**. 

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).