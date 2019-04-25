---
title: Usare dispositivi Windows Holographic con Microsoft Intune - Azure | Microsoft Docs
description: Con Microsoft Intune è possibile gestire e completare diverse attività sui dispositivi che eseguono Windows Holographic for Business e HoloLens, ad esempio configurare il portale aziendale, creare criteri di conformità, personalizzare le impostazioni URI OMA, distribuire le app, classificare i dispositivi nei gruppi, creare profili, limitare i dispositivi, abilitare gli aggiornamenti software, impostare termini e condizioni, configurare le impostazioni VPN e Wi-Fi e usare Hello for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98d4608864512ae437441bf144e17fce4545a921
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509800"
---
# <a name="manage-and-use-different-device-management-features-on-windows-holographic-and-hololens-devices-with-intune"></a>Gestire e usare diverse funzionalità di gestione dei dispositivi nei dispositivi Windows Holographic e HoloLens con Intune

Microsoft Intune include molte funzionalità che consentono di gestire i dispositivi che eseguono Windows Holographic for Business, ad esempio [Microsoft HoloLens](https://docs.microsoft.com/hololens/). Con Intune è possibile verificare che i dispositivi siano conformi alle regole dell'organizzazione ed è possibile personalizzare il dispositivo tramite l'aggiunta di un profilo VPN o Wi-Fi. Un'altra funzionalità fondamentale consiste nell'usare il dispositivo come chiosco multimediale ed eseguire un'app specifica o un set specifico di app.

Le attività in questo articolo consentono di gestire, personalizzare e proteggere i dispositivi che eseguono Windows Holographic for Business, inclusi gli aggiornamenti software e con Windows Hello for Business.

Per usare i dispositivi Windows Holographic con Intune, creare un profilo di aggiornamento edizione. Tale profilo di aggiornamento consente di aggiornare i dispositivi da Windows Holographic a Windows Holographic for Business. Per Microsoft HoloLens è possibile acquistare Commercial Suite per ottenere la licenza necessaria per l'aggiornamento. Per altre informazioni, vedere [Aggiornare i dispositivi che eseguono Windows Holographic a Windows Holographic for Business](holographic-upgrade.md).

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) è una risorsa eccezionale per la gestione e il controllo dei dispositivi che eseguono Windows Holographic for Business. Con Intune e Azure AD è possibile: 

- **[Aggiungere dispositivi ad Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)**: in Azure Active Directory (AD) è possibile aggiungere i dispositivi Windows 10 di proprietà aziendale, inclusi quelli che eseguono Windows Holographic for Business. Questa funzionalità consente ad Azure AD di controllare il dispositivo, verificando che gli utenti accedano alle risorse aziendali da dispositivi che soddisfano gli standard di sicurezza e conformità in vigore.

  Per altri dettagli, vedere [Gestione dei dispositivi in Azure AD](https://docs.microsoft.com/azure/active-directory/devices/overview).

- **[Registrazione in blocco per dispositivi Windows](windows-bulk-enroll.md)**: è possibile aggiungere un numero elevato di nuovi dispositivi Windows ad Azure Active Directory (AD) e Intune. Questa funzionalità, detta registrazione in blocco, usa pacchetti di provisioning. Questi pacchetti aggiungono i dispositivi che eseguono Windows Holographic for Business al tenant Azure AD e li registrano in Intune.

## <a name="company-portal"></a>Portale aziendale
**[Configurare l'app Portale aziendale](company-portal-app.md)**

Intune include l'app Portale aziendale che consente agli utenti di accedere ai dati aziendali, registrare i dispositivi, installare le app, contattare il reparto IT e altro ancora. È possibile personalizzare l'app Portale aziendale per i dispositivi che eseguono Windows Holographic for Business.

Se si usa l'app Portale aziendale è possibile anche eseguire una delle operazioni seguenti:

- [Rimuovere un dispositivo da Intune](/intune-user-help/unenroll-your-device-from-intune-windows) usando l'app delle impostazioni o l'app Portale aziendale
- [Rinominare un dispositivo](/intune-user-help/rename-your-device-cpapp)
- [Installare app](/intune-user-help/install-apps-cpapp-windows) nei dispositivi
- [Sincronizzare i dispositivi manualmente](/intune-user-help/sync-your-device-manually-windows) dall'app delle impostazioni o dall'app Portale aziendale

## <a name="compliance-policy"></a>Criteri di conformità
**[Creare criteri di conformità dei dispositivi](compliance-policy-create-windows.md)**

I criteri di conformità sono regole e impostazioni che i dispositivi devono soddisfare per adeguarsi ai criteri di conformità. Usare questi criteri con accesso condizionale per bloccare l'accesso alle risorse aziendali per i dispositivi che risultino non conformi. In Intune creare criteri di conformità per consentire o bloccare l'accesso per i dispositivi che eseguono Windows Holographic for Business. È possibile ad esempio creare un criterio che richiede l'abilitazione di Bitlocker.

Vedere anche **[Introduzione ai criteri di conformità](device-compliance-get-started.md)**.

## <a name="deploy-and-manage-apps"></a>Distribuire e gestire le app
**[Aggiungere le app a Intune](apps-add.md)**

Con Intune è possibile aggiungere le app ai dispositivi che eseguono Windows Holographic for Business. Esistono molti modi per distribuire le app, ad esempio:

- [Aggiungere le app di Microsoft Store](store-apps-windows.md)
- [Aggiungere le app create dall'utente](lob-apps-windows.md)
- [Assegnare app ai gruppi](apps-deploy.md)

Microsoft Intune può distribuire app di Windows universale in dispositivi Microsoft HoloLens che eseguono Windows Holographic for Business. È possibile caricare i pacchetti dell'app direttamente nel portale di Intune di Azure o distribuirle da Microsoft Store per le aziende. Per altre informazioni sulle aree correlate, vedere gli articoli seguenti:
- Per distribuire app line-of-business usando il portale di Intune di Azure, vedere [Come aggiungere app line-of-business per Windows in Microsoft Intune](lob-apps-windows.md).

    > [!NOTE]
    > Intune supporta i pacchetti con una dimensione massima di 8 GB. Questa dimensione di pacchetto è disponibile solo per le app LOB caricate in Intune.

- Per distribuire app usando Microsoft Store per le aziende, vedere [Come gestire le app acquistate in Microsoft Store per le aziende con Microsoft Intune](windows-store-for-business.md). 
- Per informazioni sulla gestione delle app con Microsoft Intune, vedere [Informazioni sulla gestione delle app in Microsoft Intune](app-management.md).
- Per altre informazioni sullo sviluppo di app per Microsoft HoloLens, vedere [Mixed reality apps for Microsoft HoloLens](https://www.microsoft.com/hololens/apps) (App di realtà mista per Microsoft HoloLens). 

> [!NOTE]
> I dispositivi HoloLens che eseguono Windows 10 Holographic for Business 1607 non supportano le app con licenza online di Microsoft Store per le aziende. Per altre informazioni, vedere [Installare app in HoloLens](https://docs.microsoft.com/hololens/hololens-install-apps).

## <a name="device-actions"></a>Azioni del dispositivo
In Intune sono presenti alcune azioni predefinite che consentono agli amministratori IT di eseguire attività diverse, in locale nel dispositivo o in remoto tramite Intune nel portale di Azure. Gli utenti possono anche inviare un comando remoto dall'app Portale aziendale Intune ai dispositivi privati registrati in Intune.

Quando si usano dispositivi che eseguono Windows Holographic for Business, è possibile eseguire le azioni seguenti: 

- **[Cancellare](devices-wipe.md#wipe)**: l'azione **Cancella** rimuove il dispositivo da Intune e ne ripristina le impostazioni predefinite di fabbrica. Usare questa azione prima di consegnare il dispositivo a un nuovo utente o quando il dispositivo viene smarrito o rubato.

- **[Disattivare](devices-wipe.md#retire)**: l'azione **Disattiva** rimuove il dispositivo da Intune. Rimuove anche dati, impostazioni e profili di posta elettronica delle app assegnati da Intune. I dati personali dell'utente rimangono nel dispositivo.

- **[Sincronizzare i dispositivi per ottenere i criteri e le azioni più recenti](device-sync.md)**: l'azione **Sincronizza** forza il dispositivo a contattare immediatamente Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente eventuali azioni o criteri in sospeso assegnati. Questa funzionalità consente di convalidare e risolvere i problemi dei criteri assegnati, senza attendere la successiva archiviazione pianificata.

**[Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md)**  è un'ottima risorsa per ottenere informazioni sulla gestione dei dispositivi tramite il portale di Azure. 

## <a name="device-categories-and-groups"></a>Categorie e gruppi di dispositivi
**[Raggruppare i dispositivi in categorie](device-group-mapping.md)**

Con Intune è possibile creare categorie di dispositivi per aggiungere automaticamente i dispositivi ai gruppi in base alle categorie create, ad esempio Vendite, Contabilità, Risorse umane e così via. L'idea è semplificare la gestione dei dispositivi che eseguono Windows Holographic for Business.

## <a name="device-configuration-profiles"></a>Profili di configurazione dispositivo 
**[Introduzione ai profili di configurazione](device-profiles.md) e [Creare un profilo](device-profile-create.md)**

Intune include impostazioni e funzionalità che è possibile abilitare o disabilitare in dispositivi diversi all'interno dell'organizzazione. Queste impostazioni e funzionalità vengono gestite usando i profili. Ad esempio, è possibile creare un profilo che abilita Cortana o usa Windows Defender SmartScreen nei dispositivi che eseguono Windows Holographic for Business.

Nei profili è possibile usare URI OMA per personalizzare alcune impostazioni, creare restrizioni dei dispositivi e configurare una rete privata virtuale (VPN) e Wi-Fi.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Impostazioni dispositivo personalizzate](custom-settings-windows-holographic.md)

Per configurare le impostazioni OMA-URI (Open Mobile Alliance Uniform Resource Identifier), è possibile creare un profilo personalizzato in Intune. Usare le impostazioni URI OMA per controllare diverse funzionalità nei dispositivi Windows Holographic for Business, ad esempio abilitare la rete VPN o controllare gli aggiornamenti su Microsoft Update.

#### <a name="configure-kiosk-modekiosk-settings-holographicmd"></a>[Configurare la modalità tutto schermo](kiosk-settings-holographic.md)

Grazie alle funzionalità del PC in condivisione o guest disponibili in Intune, è possibile configurare i dispositivi Windows Holographic for Business per l'esecuzione in modalità tutto schermo. Questi dispositivi possono eseguire un'app (modalità tutto schermo per app singola), o più app (modalità tutto schermo per più app).

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Restrizioni dei dispositivi](device-restrictions-windows-holographic.md)

Le restrizioni dei dispositivi consentono di controllare diverse impostazioni e funzionalità nei dispositivi, inclusi la richiesta di password, l'installazione di app da [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), l'abilitazione Bluetooth e altro ancora. Queste restrizioni vengono create in un profilo di Intune. Questo profilo può essere applicato a più dispositivi che eseguono Windows Holographic for Business.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Configurare la rete VPN](vpn-settings-configure.md)

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. In Intune è possibile creare un profilo VPN che include impostazioni specifiche per i dispositivi che eseguono Windows Holographic for Business. È possibile ad esempio creare un profilo VPN in modo che tutti i dispositivi Windows Holographic for Business usino la VPN Citrix come tipo di connessione.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Configurare la rete Wi-Fi](wi-fi-settings-configure.md)

È anche possibile creare un profilo Wi-Fi in Intune per assegnare le impostazioni della rete wireless ai dispositivi Windows Holographic for Business. Quando si assegna un profilo Wi-Fi, gli utenti finali ottengono l'accesso alla rete aziendale, senza alcuna configurazione di rete. È ad esempio possibile creare una rete Wi-Fi dedicata esclusivamente ai dispositivi Windows Holographic for Business.

## <a name="shared-multi-user-devices"></a>Dispositivi multiutente condivisi
[Dispositivi condivisi](shared-user-device-settings-windows-holographic.md)

I dispositivi che eseguono Windows Holographic for Business, ad esempio Microsoft HoloLens, possono avere più utenti. In Intune sono disponibili impostazioni che consentono di controllare varie funzionalità su questi dispositivi, ad esempio il risparmio energia, mediante la gestione dell’archiviazione locale e degli account. I profili di configurazione possono anche essere applicati ai dispositivi con sistemi operativi diversi. Ad esempio, il gruppo di dispositivi può includere dispositivi che eseguono RS2 e RS3 nello stesso gruppo.

## <a name="software-updates"></a>Aggiornamenti software
**[Gestire gli aggiornamenti software](windows-update-for-business-configure.md)**

Intune include una funzionalità denominata anelli di aggiornamento per i dispositivi Windows 10. Questi anelli di aggiornamento includono un gruppo di impostazioni che determinano il modo in cui vengono installati gli aggiornamenti. È possibile ad esempio creare una finestra di manutenzione per installare gli aggiornamenti o scegliere di riavviare dopo l'installazione degli aggiornamenti. Un anello di aggiornamento può essere applicato a più dispositivi che eseguono Windows Holographic for Business.

## <a name="terms-and-conditions"></a>Termini e condizioni
**[Impostare termini e condizioni aziendali per l'accesso degli utenti](terms-and-conditions-create.md)**

Prima che gli utenti possano registrare i dispositivi e accedere alle app aziendali, inclusa la posta elettronica, è possibile richiedere che accettino i termini e le condizioni della società. In Intune è possibile definire come termini e condizioni vengono visualizzati in Portale aziendale e anche assegnare questi termini e condizioni ai dispositivi che eseguono Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello for Business
**[Usare Windows Hello for Business](windows-hello.md)**

Hello for Business è un metodo di accesso alternativo che usa un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale. Con Hello for Business, i dispositivi Windows Holographic for Business possono eseguire l'accesso tramite un PIN con una lunghezza minima impostata dall'utente.
