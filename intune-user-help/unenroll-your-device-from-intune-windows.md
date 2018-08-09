---
title: Rimuovere il dispositivo Windows da Intune
description: Descrive come rimuovere un dispositivo Windows da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/01/2018
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
ms.openlocfilehash: 980b7d9f221fd1a1ae12f27743757d5b3bd53492
ms.sourcegitcommit: 5f6117b83f96f7d93dde3685c2ff2b67ae53740b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39481190"
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

-   **Log di diagnostica**: dati di attività standard delle app raccolti da Microsoft. Tali dati vengono cancellati automaticamente quando si disinstalla l'app Portale aziendale. I dati dell'attività dell'app indicano ad esempio per quanto tempo è stata aperta l'app o se ha registrato un arresto anomalo.
-   **Cache dell'applicazione**: file di supporto necessari per il funzionamento dell'app, come icone e impostazioni.

Per eliminare i log e la cache memorizzati, completare una delle operazioni seguenti:

* [Disinstallare l'app Portale aziendale](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* Ripristinare l'app Portale aziendale. Aprire l'app **Impostazioni** e selezionare > **App** > **Portale aziendale** > **Opzioni avanzate** > **Ripristina**. 

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
