---
title: Rimuovere il dispositivo Windows da Intune | Microsoft Docs
description: Descrive come rimuovere un dispositivo Windows da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/28/2018
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
ms.openlocfilehash: 9f9051fb393c82031d581f7fec731a3b148cbf2e
ms.sourcegitcommit: 7f46e9990797bdfa669ccba2077721f1bc70c07e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="remove-your-windows-device-from-intune"></a>Rimuovere il dispositivo Windows da Intune

Se il dispositivo è registrato in Intune, ma non si vuole più usare il dispositivo Windows per accedere alla posta elettronica, alle app o ad altre risorse aziendali o dell'istituto di istruzione, è necessario rimuovere il dispositivo dalla gestione. Dopo aver rimosso il dispositivo da Intune, non sarà più possibile accedere a tali risorse. Per altre informazioni su cosa accade quando il dispositivo viene rimosso dalla gestione, vedere [Che cosa accade se si annulla la registrazione del dispositivo da Intune?](what-happens-if-you-unenroll-your-device-from-intune-windows.md).

## <a name="remove-your-windows-10-device"></a>Rimuovere il dispositivo Windows 10

1.  Dall'elenco delle app, toccare l'app **Portale aziendale** .

2.  Accedere con le credenziali aziendali o dell'istituto di istruzione.

3.  Selezionare il dispositivo di cui annullare la registrazione in **Dispositivi personali**.

4.  Toccare **Rimuovi** &gt; **Rimuovi**.

## <a name="remove-your-windows-81-computer"></a>Rimuovere il computer Windows 8.1

1.  Passare a **Impostazioni PC** &gt; **Rete** &gt; **Area di lavoro**.

2.  In **Aggiunta all'area di lavoro** selezionare **Esci**.

3.  In **Turn on device management** (Attiva gestione dei dispositivi) selezionare **Disattiva**.

4.  Nella finestra popup visualizzata selezionare **Disattiva**.

## <a name="remove-your-windows-phone-81-mobile-device"></a>Rimuovere il dispositivo mobile Windows Phone 8.1

1.  Passare a **Impostazioni** &gt; **Area di lavoro**.

2.  Toccare l'account aziendale di cui si vuole annullare la registrazione.

3.  Nella parte inferiore della schermata toccare **Elimina**.

4.  Nella finestra di dialogo **Elimina account** toccare **Elimina**.

## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Rimozione delle informazioni personali dopo avere rimosso il Portale aziendale

Esistono due tipi di dati archiviati dal Portale aziendale nel dispositivo Windows:

-   **Log di diagnostica**: i dati sulle attività dell'app standard raccolti da Microsoft, ad esempio per quanto tempo l'app restava aperta o se si arresta in modo anomalo , vengono automaticamente cancellati quando si rimuove il dispositivo dal Portale aziendale.
-   **Cache dell'applicazione**: archiviazione di determinati file di supporto necessari all'app per funzionare, come icone e impostazioni.

Per eliminare completamente queste informazioni, è necessario seguire alcuni passaggi.

### <a name="uninstall-the-company-portal"></a>Disinstallare il Portale aziendale  

La [disinstallazione dell'app Portale aziendale](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) rimuoverà alcuni dei dati dell'app archiviati nel dispositivo.  

### <a name="reset-the-company-portal"></a>Ripristinare il Portale aziendale

È possibile ripristinare i dati dell'app Portale aziendale rimanenti ripristinando l'app in Impostazioni. Aprire **Impostazioni** > **App e Funzionalità** > **Portale aziendale** > **Advanced options (Opzioni avanzate** > **Ripristina**.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).