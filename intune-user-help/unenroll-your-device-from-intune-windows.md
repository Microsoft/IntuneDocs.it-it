---
title: Rimuovere il dispositivo Windows dalla gestione di Intune
description: Descrive come rimuovere un dispositivo Windows dalla gestione di Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 46f2193a3a13183d41b10f03b6efe7100f0d9f9d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "55840366"
---
# <a name="remove-your-windows-device-from-management"></a>Rimuovere il dispositivo Windows dalla gestione

Un dispositivo Windows registrato può essere rimosso dalla gestione quando non si vuole (o non è più necessario):  
* Usare il dispositivo per gestire risorse aziendali o dell'istituto di istruzione. 
* Accedere a posta, app o altre risorse aziendali o dell'istituto di istruzione.

Dopo aver annullato la registrazione del dispositivo, il dispositivo non potrà più accedere alle risorse aziendali o dell'istituto di istruzione. È possibile rimuovere dalla gestione i dispositivi Windows seguenti.  
* Dispositivi Windows 10 
* Computer Windows 8.1
* Telefono Windows 8.1
 
Per altre informazioni su cosa accade quando il dispositivo viene rimosso dalla gestione, vedere [Che cosa avviene se si rimuove il dispositivo da Intune](what-happens-if-you-unenroll-your-device-from-intune-windows.md).  

## <a name="remove-your-windows-10-device"></a>Rimuovere il dispositivo Windows 10
Per rimuovere dalla gestione un dispositivo Windows 10 seguire questa procedura.

### <a name="remove-in-company-portal-app-home-page"></a>Rimozione nell'app Portale aziendale, pagina **Home**  

1. Aprire l'app Portale aziendale.
2. Nella **home page** scorrere verso il basso fino alla sezione **Dispositivi personali**.
3. Selezionare il dispositivo da rimuovere.
3. Nell'angolo in alto a destra dell'app selezionare l'icona **Altre informazioni**.
4. Selezionare **Rimuovi**. 
5. Selezionare **Rimuovi** per confermare la rimozione del dispositivo.  

### <a name="remove-in-company-portal-app-device-context-menu"></a>Rimozione nell'app Portale aziendale, menu di scelta rapida del dispositivo  

1. Aprire l'app Portale aziendale e passare a **Dispositivi personali**.

    ![Screenshot di esempio dell'app Portale aziendale per Windows, home page, con la sezione Dispositivi personali evidenziata.](./media/1809_CheckAccess_Context_Select_Device.png)

2. Fare clic con il pulsante destro del mouse o tenere premuto il tasto sinistro su un dispositivo per aprire il relativo [menu di scelta rapida](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

3. Selezionare **Rimuovi**.  

    ![Screenshot di esempio dell'app Portale aziendale per Windows con home page. Il menu di scelta rapida è visibile nella sezione **Dispositivi personali** della pagina e contiene le azioni "Rinomina", "Rimuovi" e "Verifica l'accesso".](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. Nella finestra di conferma fare clic su **Altre informazioni** per sapere come potrebbe cambiare l'accesso alle risorse aziendali o dell'istituto di istruzione. Selezionare **Rimuovi** per confermare la rimozione del dispositivo.   

     ![Screenshot di esempio dell'app Portale aziendale per Windows con home page. Nel dispositivo viene visualizzato il campo Rinomina in cui l'utente può digitare il nuovo nome e fare clic su Rinomina o Annulla.](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>Rimozione nell'app Impostazioni del dispositivo
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

## <a name="remove-your-windows-81-phone"></a>Rimuovere il telefono Windows 8.1
Per rimuovere da Intune un telefono Windows 8.1 seguire questa procedura.

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

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
