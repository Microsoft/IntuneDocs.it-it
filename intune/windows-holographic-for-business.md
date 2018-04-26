---
title: Gestire dispositivi Windows Holographic con Microsoft Intune - Azure | Microsoft Docs
description: Con Microsoft Intune è possibile completare diverse attività sui dispositivi che eseguono Windows Holographic for Business, ad esempio configurare il Portale aziendale, creare criteri di conformità, personalizzare le impostazioni URI OMA, distribuire le app, classificare i dispositivi nei gruppi, creare profili, limitare i dispositivi, abilitare gli aggiornamenti software, impostare termini e condizioni, configurare le impostazioni VPN e Wi-Fi e usare Hello for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41c1ea3bf12b83a0f09c8535275ffb58e5f46931
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>Personalizzare i dispositivi che eseguono Windows Holographic con Intune

Microsoft Intune supporta i dispositivi che eseguono Windows Holographic for Business, ad esempio [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/).

Per gestire i dispositivi che eseguono Windows Holographic con Microsoft Intune, è necessario creare un profilo di aggiornamento dell'edizione. Tale profilo di aggiornamento consente di aggiornare i dispositivi da Windows Holographic a Windows Holographic for Business. Per Microsoft HoloLens è possibile acquistare Commercial Suite per ottenere la licenza necessaria per l'aggiornamento. Per altre informazioni, vedere [Aggiornare i dispositivi che eseguono Windows Holographic a Windows Holographic for Business](holographic-upgrade.md).

Per gestire e personalizzare i dispositivi che eseguono Windows Holographic for Business, è possibile usare le attività descritte in questo articolo. È possibile ad esempio gestire gli aggiornamenti software, configurare le impostazioni VPN e altro ancora.

## <a name="company-portal"></a>Portale aziendale
**[Configurare l'app Portale aziendale](company-portal-app.md)**

Intune include il Portale aziendale, in cui gli utenti possono accedere ai dati aziendali, registrare i dispositivi, installare le app, contattare il reparto IT e altro ancora. È possibile personalizzare l'app Portale aziendale per i dispositivi che eseguono Windows Holographic for Business.

## <a name="compliance-policy"></a>Criteri di conformità
**[Creare criteri di conformità dei dispositivi](compliance-policy-create-windows.md)**

I criteri di conformità sono regole e impostazioni che i dispositivi devono soddisfare per adeguarsi ai criteri di conformità. Questi criteri con accesso condizionale possono essere usati per bloccare l'accesso alle risorse aziendali per i dispositivi che risultano non conformi. In Intune è possibile creare criteri di conformità per consentire o bloccare l'accesso per i dispositivi che eseguono Windows Holographic for Business. È possibile ad esempio creare un criterio che richiede l'abilitazione di Bitlocker.

Vedere anche **[Introduzione ai criteri di conformità](device-compliance-get-started.md)**.

## <a name="deploy-apps"></a>Distribuire le app
**[Aggiungere le app a Intune](apps-add.md)**

Con Intune è possibile aggiungere le app ai dispositivi che eseguono Windows Holographic for Business. Esistono molti modi per distribuire le app, ad esempio:

- [Aggiungere le app di Microsoft Store](store-apps-windows.md)
- [Aggiungere le app create dall'utente](lob-apps-windows.md)
- [Assegnare app ai gruppi](apps-deploy.md)

## <a name="device-categories-and-groups"></a>Categorie e gruppi di dispositivi
**[Raggruppare i dispositivi in categorie](device-group-mapping.md)**

Con Intune è possibile creare categorie di dispositivi per aggiungere automaticamente i dispositivi ai gruppi in base alle categorie create, ad esempio Vendite, Contabilità, Risorse umane e così via. L'idea è semplificare la gestione dei dispositivi che eseguono Windows Holographic for Business.

## <a name="device-configuration-profiles"></a>Profili di configurazione dispositivo 
**[Introduzione ai profili di configurazione](device-profiles.md) e [Creare un profilo](device-profile-create.md)**

Intune include impostazioni e funzionalità che è possibile abilitare o disabilitare in dispositivi diversi all'interno dell'organizzazione. Queste impostazioni e funzionalità vengono gestite usando i profili. Ad esempio, è possibile creare un profilo che abilita Cortana o usa Windows Defender SmartScreen nei dispositivi che eseguono Windows Holographic for Business.

Nei profili è possibile usare URI OMA per personalizzare alcune impostazioni, creare restrizioni dei dispositivi e configurare una rete privata virtuale (VPN) e Wi-Fi.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Impostazioni dispositivo personalizzate](custom-settings-windows-holographic.md)

Per configurare le impostazioni OMA-URI (Open Mobile Alliance Uniform Resource Identifier), è possibile creare un profilo personalizzato in Intune. Usare le impostazioni URI OMA per controllare diverse funzionalità nei dispositivi Windows Holographic for Business, ad esempio abilitare la rete VPN o controllare gli aggiornamenti su Microsoft Update.

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Restrizioni dei dispositivi](device-restrictions-windows-holographic.md)

Le restrizioni dei dispositivi consentono di controllare diverse impostazioni e funzionalità nei dispositivi, inclusi la richiesta di password, l'installazione di app da [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), l'abilitazione Bluetooth e altro ancora. Queste restrizioni vengono create in un profilo di Intune. Questo profilo può essere applicato a più dispositivi che eseguono Windows Holographic for Business.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Configurare la rete VPN](vpn-settings-configure.md)

Le reti private virtuali (VPN) offrono agli utenti accesso remoto sicuro alla rete aziendale. In Intune è possibile creare un profilo VPN che include impostazioni specifiche per i dispositivi che eseguono Windows Holographic for Business. È possibile ad esempio creare un profilo VPN in modo che tutti i dispositivi Windows Holographic for Business usino la VPN Citrix come tipo di connessione.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Configurare la rete Wi-Fi](wi-fi-settings-configure.md)

È anche possibile creare un profilo Wi-Fi in Intune per assegnare le impostazioni della rete wireless ai dispositivi Windows Holographic for Business. Quando si assegna un profilo Wi-Fi, gli utenti finali ottengono l'accesso alla rete aziendale, senza alcuna configurazione di rete. È ad esempio possibile creare una rete Wi-Fi dedicata esclusivamente ai dispositivi Windows Holographic for Business.

## <a name="software-updates"></a>Aggiornamenti software
**[Gestire gli aggiornamenti software](windows-update-for-business-configure.md)**

Intune include una funzionalità denominata anelli di aggiornamento per i dispositivi Windows 10. Questi anelli di aggiornamento includono un gruppo di impostazioni che determinano il modo in cui vengono installati gli aggiornamenti. È possibile ad esempio creare una finestra di manutenzione per installare gli aggiornamenti o scegliere di riavviare dopo l'installazione degli aggiornamenti. Un anello di aggiornamento può essere applicato a più dispositivi che eseguono Windows Holographic for Business.

## <a name="terms-and-conditions"></a>Termini e condizioni
**[Impostare termini e condizioni aziendali per l'accesso degli utenti](terms-and-conditions-create.md)**

Prima che gli utenti possano registrare i dispositivi e accedere alle app aziendali, inclusa la posta elettronica, è possibile richiedere che accettino i termini e condizioni della società. In Intune è possibile definire come termini e condizioni vengono visualizzati nel Portale aziendale e anche assegnare questi termini e condizioni ai dispositivi che eseguono Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello for Business
**[Usare Windows Hello for Business](windows-hello.md)**

Hello for Business è un metodo di accesso alternativo che usa un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale. Con Hello for Business, i dispositivi Windows Holographic for Business possono eseguire l'accesso tramite un PIN con una lunghezza minima impostata dall'utente.
