---
title: Risolvere i problemi di installazione delle app
titleSuffix: Microsoft Intune
description: Usare il riquadro Risoluzione dei problemi di Microsoft Intune per facilitare la risoluzione dei problemi di installazione delle app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 13aea23f58c69d5c7e38f77ae7dfa19bd12edd35
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511652"
---
# <a name="troubleshoot-app-installation-issues"></a>Risolvere i problemi di installazione delle app

Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. Microsoft Intune offre dettagli sugli errori di installazione delle app che consentono agli operatori di help desk e agli amministratori di Intune di visualizzare informazioni sulle app in per rispondere alle richieste degli utenti. Il riquadro di risoluzione dei problemi all'interno di Intune fornisce dettagli sull'errore, incluse informazioni dettagliate sulle app gestite nel dispositivo dell'utente. Per ogni singolo dispositivo sono disponibili informazioni dettagliate sul ciclo di vita completo di un'app nel riquadro **App gestite**. È possibile visualizzare i problemi di installazione, ad esempio quando l'app è stato creata, modificata, assegnata e recapitata a un dispositivo. 

> [!NOTE]
> Per informazioni specifiche sul codice di errore di installazione dell'app, vedere [Informazioni di riferimento sugli errori di installazione delle app di Intune](~/apps/app-install-error-codes.md).

## <a name="app-troubleshooting-details"></a>Informazioni dettagliate per la risoluzione dei problemi delle app

Intune offre informazioni dettagliate per la risoluzione dei problemi delle app in base alle app installate nel dispositivo di un utente specifico.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selezionare **Risoluzione dei problemi e supporto tecnico**.
4. Fare clic su **Seleziona utente** per selezionare un utente per risolvere i problemi. Verrà visualizzato il riquadro **Seleziona utenti**.
5. Selezionare un utente digitando il nome o l'indirizzo di posta elettronica. Fare clic su **Seleziona** nella parte inferiore del riquadro. Le informazioni di risoluzione dei problemi per l'utente vengono visualizzate nel riquadro **Risoluzione dei problemi**. 
6. Selezionare il dispositivo per cui si vuole eseguire la risoluzione dei problemi nell'elenco **Dispositivi**.
    ![Riquadro Risoluzione dei problemi di Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Selezionare **App gestite** nel riquadro del dispositivo selezionato. Verrà visualizzato un elenco delle app gestite.
    ![Dettagli di un dispositivo specifico gestito da Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Selezionare un'app nell'elenco per cui **Stato dell'installazione** indica un errore.
    ![App selezionata che mostra informazioni dettagliate sull'errore di installazione.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > La stessa app potrebbe essere assegnata a più gruppi, ma con diverse azioni previste (finalità) per l'app. Ad esempio, la finalità risolta per un'app indicherà **esclusa** se l'app viene esclusa per un utente durante l'assegnazione di app. Per altre informazioni, vedere [Modalità di risoluzione dei conflitti tra finalità di app](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Se si verifica un errore di installazione per un'app obbligatoria, l'utente o il supporto tecnico sarà in grado di sincronizzare il dispositivo e ritentare l'installazione dell'app.

I dettagli dell'errore di installazione dell'app indicheranno il problema. È possibile usare questi dettagli per determinare l'azione migliore da intraprendere per risolvere il problema. Per altre informazioni sulla risoluzione dei problemi di installazione delle app, vedere [Errori di installazione delle app Android](app-install-error-codes.md#android-app-installation-errors) ed [Errori di installazione delle app iOS](app-install-error-codes.md#ios-and-ipados-app-installation-errors).

> [!Note]  
> È anche possibile accedere al riquadro **Risoluzione dei problemi** digitando nel browser l'indirizzo seguente: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>L'installazione dell'app di destinazione del gruppo di utenti non raggiunge il dispositivo
In caso di problemi durante l'installazione delle app, è consigliabile prendere in considerazione le azioni seguenti:
- Se l'app non viene visualizzata nel Portale aziendale, assicurarsi che sia distribuita con finalità **Available** e che l'utente acceda al Portale aziendale con il tipo di dispositivo supportato dall'app.
- Per i dispositivi BYOD Windows, l'utente deve aggiungere un account aziendale al dispositivo.
- Verificare se l'utente ha superato il limite di dispositivi di AAD:
  1. Passare ad [Azure Active Directory - Impostazioni dispositivo](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Prendere nota del valore impostato per **Numero max dispositivi per utente**.
  3. Passare a [Utenti di Azure Active Directory](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Selezionare l'utente interessato e fare clic su **Dispositivi**.
  5. Se l'utente supera il limite impostato, eliminare tutti i record obsoleti che non sono più necessari.
- Per i dispositivi DEP iOS/iPadOS, assicurarsi che l'utente sia elencato come **Registrato dall'utente** nel riquadro Panoramica del dispositivo Intune. Se viene visualizzato NA, distribuire un criterio di configurazione per il Portale aziendale Intune. Per altre informazioni, vedere [Configurare l'app Portale aziendale](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-and-ipados-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Risoluzione dei problemi di installazione delle app Win32

Selezionare l'app Win32 distribuita usando l'estensione di gestione di Intune. È possibile selezionare l'opzione **Raccogli i log** se l'installazione dell'app Win32 ha esito negativo. 

> [!IMPORTANT]
> L'opzione **Raccogli i log** non viene infatti attivata se l'app Win32 è stata installata nel dispositivo.<p>Per poter raccogliere i log dell'app Win32, è necessario che l'estensione di gestione di Intune sia stata installata nel client Windows. L'estensione di gestione di Intune viene installata quando uno script di PowerShell o un'app Win32 viene distribuita in un gruppo di sicurezza dispositivi o utente. Per altre informazioni, vedere i [Prerequisiti dell'estensione di gestione di Intune](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Raccogliere i file di log

Per raccogliere i log di installazione dell'app Win32, prima di tutto seguire le istruzioni riportate nella sezione [Informazioni dettagliate per la risoluzione dei problemi delle app](troubleshoot-app-install.md#app-troubleshooting-details). Quindi, continuare con la seguente procedura:

1. Fare clic sull'opzione **Raccogli registri** nel riquadro **Dettagli installazione**.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Specificare i percorsi dei file e i nomi di file dei log per iniziare il processo di raccolta, quindi fare clic su **OK**.

    > [!NOTE]
    > La raccolta dei log richiederà meno di due ore. Sono supportati i tipi di file con estensione *log, txt, dmp, cab, zip, xml, evtx ed evtl*. Sono consentiti fino a 25 percorsi di file.

3. Dopo aver raccolto i file di log, selezionare il collegamento **log** per scaricarli.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Verrà visualizzata una notifica per indicare l'esito positivo della raccolta dei log dell'app.

#### <a name="win32-log-collection-requirements"></a>Requisiti per la raccolta di log di Win32

Esistono regole specifiche da seguire per raccogliere i file di log:

- È necessario specificare il percorso completo dei file di log. 
- È possibile specificare variabili di ambiente per la raccolta dei log, ad esempio:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Sono ammesse solo estensioni di file esatte, ad esempio:<br>
  *.log,.txt,.dmp,.cab,.zip,.xml*
- Il limite per il caricamento è 60 MB o 25 file, a seconda di quale condizione si verifica per prima. 
- La raccolta dei log di installazione dell'app Win32 è abilitata per le app che rispettano la finalità di assegnazione obbligatoria, disponibile e disinstallazione dell'app.
- I log archiviati sono crittografati per proteggere le informazioni personali che contengono.
- Quando si aprono dei ticket di supporto per gli errori che si verificano nelle app Win32, allegare i relativi log di errore usando la procedura riportata sopra.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Risoluzione dei problemi delle app da Microsoft Store

Le informazioni nell'argomento [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Risoluzione dei problemi relativi a pacchetti, distribuzioni e query delle app di Microsoft Store) consentono di risolvere i problemi comuni riscontrabili durante l'installazione di app da Microsoft Store, tramite Intune o altri mezzi.

## <a name="app-troubleshooting-resources"></a>Risorse per la risoluzione dei problemi delle app
- [Distribuzione di Visio e Project nell'ambito della distribuzione di Office Pro Plus](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Eseguire un'azione per assicurarsi che le app MSfB distribuite tramite Intune siano installate in Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Risoluzione dei problemi delle distribuzioni di app MSI in Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Procedure consigliate per la distribuzione del software all'agente PC Windows classico di Intune](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sulla risoluzione dei problemi di Intune, vedere [Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali](../fundamentals/help-desk-operators.md). 
- È possibile ottenere informazioni sui problemi noti in Microsoft Intune. Per altre informazioni, vedere il blog [Intune Customer Success](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- È possibile ottenere altre informazioni. Vedere [Come ottenere supporto per Microsoft Intune](../fundamentals/get-support.md).
