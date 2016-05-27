---
# required metadata

title: Informazioni di riferimento sui criteri di Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Informazioni di riferimento sui criteri di Microsoft Intune

Usare le informazioni in questo argomento per decidere più facilmente quali criteri di Microsoft Intune è necessario usare per gestire i dispositivi.

> [!TIP]
> Per informazioni più dettagliate su come usare i criteri, vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)..


## Criteri di configurazione di Android

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Configurazione personalizzata (Android 4 e versioni successive, Samsung KNOX Standard 4.0 e versioni successive)**|Distribuire impostazioni URI OMA, come le impostazioni Wi-Fi che possono essere usate per controllare le funzionalità del dispositivo. Questo criterio è utile quando l'impostazione necessaria non è disponibile nei criteri di configurazione.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di Android in Microsoft Intune](android-policy-settings-in-microsoft-intune.md).|
|**Profilo di posta elettronica (Samsung KNOX Standard 4.0 e versioni successive)**|Creare, distribuire e monitorare le impostazioni di posta elettronica di Exchange ActiveSync in dispositivi gestiti. In questo modo, gli utenti possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione.<br /><br />Per informazioni dettagliate, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)..|
|**Configurazione generale (Android 4 e versioni successive, Samsung KNOX Standard 4.0 e versioni successive)**|Configurare le impostazioni funzionali e di sicurezza del dispositivo mobile.<br />Specificare le app conformi o non conformi e segnalare quando vengono usate.<br />Configurare la modalità a tutto schermo che blocca i dispositivi per permettere il funzionamento solo di determinate funzionalità. Ad esempio, consentire al dispositivo di eseguire una sola app o disabilitare i pulsanti del volume.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di Android in Microsoft Intune](android-policy-settings-in-microsoft-intune.md).|
|**Profilo certificato PKCS #12 (PFX) (Android 4 e versioni successive)**|Usare questo profilo per creare e distribuire le impostazioni PFX per le richieste di certificato del dispositivo.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo certificato SCEP (Android 4 e versioni successive)**|Consente di configurare un certificato Simple Certificate Enrollment Protocol (SCEP) che può essere usato con un certificato attendibile di dispositivo mobile per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili Wi-Fi e VPN.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo certificato attendibile (Android 4 e versioni successive)**|Consente di configurare un certificato attendibile di dispositivo mobile che può essere usato per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili VPN e Wi-Fi.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo VPN (Android 4 e versioni successive)**|Consente di configurare e distribuire le impostazioni che permettono agli utenti di accedere in modo sicuro alla rete aziendale dal proprio dispositivo mobile. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi al proprio lavoro.<br /><br />Per informazioni dettagliate, vedere [Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Profilo Wi-Fi (Android 4 e versioni successive)**|Consente di configurare e distribuire le impostazioni di rete wireless agli utenti dell'organizzazione. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alla rete wireless.<br /><br />Per informazioni dettagliate, vedere [Connessioni Wi-Fi in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|

## Criteri di configurazione di iOS

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Configurazione personalizzata (iOS 7.1 e versioni successive)**|Distribuire i profili di configurazione ai dispositivi iOS creati usando lo strumento Apple Configurator. Questo criterio è utile quando l'impostazione necessaria non è disponibile nei criteri di configurazione.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di iOS in Microsoft Intune](ios-policy-settings-in-microsoft-intune.md)..|
|**Profilo di posta elettronica (iOS 7.1 e versioni successive)**|Creare, distribuire e monitorare le impostazioni di posta elettronica di Exchange ActiveSync in dispositivi gestiti. In questo modo, gli utenti possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione.<br /><br />Per informazioni dettagliate, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)..|
|**Configurazione generale (iOS 7.1 e versioni successive)**|Configurare le impostazioni funzionali e di sicurezza del dispositivo mobile.<br />-   Specificare le app conformi o non conformi e segnalare quando vengono usate.<br />Configurare la modalità a tutto schermo che blocca i dispositivi per permettere il funzionamento solo di determinate funzionalità. Ad esempio, consentire al dispositivo di eseguire una sola app o disabilitare i pulsanti del volume.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di iOS in Microsoft Intune](ios-policy-settings-in-microsoft-intune.md)..|
|**Profilo certificato SCEP (iOS 7.1 e versioni successive)**|Consente di configurare un certificato Simple Certificate Enrollment Protocol (SCEP) che può essere usato con un certificato attendibile di dispositivo mobile per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili Wi-Fi e VPN.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo certificato attendibile (iOS 7.1 e versioni successive)**|Consente di configurare un certificato attendibile di dispositivo mobile che può essere usato per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili VPN e Wi-Fi.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo VPN (iOS 7.1 e versioni successive)**|Consente di configurare e distribuire le impostazioni che permettono agli utenti di accedere in modo sicuro alla rete aziendale dal proprio dispositivo mobile. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi al proprio lavoro.<br /><br />Per informazioni dettagliate, vedere [Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Profilo Wi-Fi (iOS 7.1 e versioni successive)**|Consente di configurare e distribuire le impostazioni di rete wireless agli utenti dell'organizzazione. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alla rete wireless.<br /><br />Per informazioni dettagliate, vedere [Connessioni Wi-Fi in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|
|**Criteri di configurazione delle app per dispositivi mobili (iOS 7.1 e versioni successive)**|Usare i criteri di configurazione delle app mobili per specificare automaticamente le impostazioni che potrebbero essere necessarie quando l'utente esegue un'app iOS.<br /><br />Per informazioni dettagliate, vedere [Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)..|

## Criteri di configurazione di Mac OS X

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Configurazione personalizzata (Mac OS X 10.9 e versioni successive)**|Distribuire ai computer Mac i profili di configurazione creati con lo strumento Apple Configurator. Questo criterio è utile quando l'impostazione necessaria non è disponibile nei criteri di configurazione.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di Mac OS X in Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md).|
|**Configurazione generale (Mac OS X 10.9 e versioni successive)**|Configurare le impostazioni funzionali e di sicurezza del dispositivo mobile.<br />Specificare le app conformi o non conformi e segnalare quando vengono usate.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di Mac OS X in Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md).|
|**Profilo certificato SCEP (Mac OS X 10.9 e versioni successive)**|Consente di configurare un certificato Simple Certificate Enrollment Protocol (SCEP) che può essere usato con un certificato attendibile di dispositivo mobile per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili Wi-Fi e VPN.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo certificato attendibile (Mac OS X 10.9 e versioni successive)**|Consente di configurare un certificato attendibile di dispositivo mobile che può essere usato per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili VPN e Wi-Fi.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo VPN (Mac OS X 10.9 e versioni successive)**|Consente di configurare e distribuire le impostazioni che permettono agli utenti di accedere in modo sicuro alla rete aziendale dal proprio dispositivo mobile. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi al proprio lavoro.<br /><br />Per informazioni dettagliate, vedere [Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Profilo Wi-Fi (Mac OS X 10.9 e versioni successive)**|Consente di configurare e distribuire le impostazioni di rete wireless agli utenti dell'organizzazione. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alla rete wireless.<br /><br />Per informazioni dettagliate, vedere [Connessioni Wi-Fi in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|

## Criteri di configurazione di Windows
Si applica solo a Windows Phone e ai dispositivi Windows registrati.

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Configurazione personalizzata (Windows 10 Desktop e Mobile e versioni successive)**|Distribuire impostazioni URI OMA che possono essere usate per controllare le funzionalità del dispositivo. Questo criterio è utile quando l'impostazione necessaria non è disponibile nei criteri di configurazione.<br />    Per informazioni dettagliate, vedere [Impostazioni dei criteri di Windows 10 in Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md).|
|**Configurazione personalizzata (Windows Phone 8.1 e versioni successive)**|Distribuire impostazioni URI OMA che possono essere usate per controllare le funzionalità del dispositivo. Questo criterio è utile quando l'impostazione necessaria non è disponibile nei criteri di configurazione.<br /><br />Per informazioni dettagliate, vedere [Windows Phone 8.1 policy settings in Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md) (Impostazioni dei criteri di Windows Phone 8.1 in Microsoft Intune).|
|**Criteri di aggiornamento edizione (Windows 10 Desktop e versioni successive)**<br><br>**Criteri di aggiornamento edizione (Windows 10 Holographic e versioni successive)**|Configurare e distribuire criteri contenenti informazioni sul codice di licenza o sul codice Product Key usato per aggiornare i dispositivi Windows 10 a una versione più recente<br><br>Per informazioni dettagliate, vedere [Impostazioni dei criteri di aggiornamento dell'edizione Windows in Microsoft Intune](edition-upgrade-policy-settings-in-microsoft-intune.md).|  
|**Profilo di posta elettronica (Windows Phone 8 e versioni successive)**<br /><br />**Profilo di posta elettronica (Windows 10 Desktop e Mobile e versioni successive)**|Creare, distribuire e monitorare le impostazioni di posta elettronica di Exchange ActiveSync in dispositivi gestiti. In questo modo, gli utenti possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione.<br /><br />Per informazioni dettagliate, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)..|
|**Configurazione generale (Windows 10 Desktop e Mobile e versioni successive)**|Configurare le impostazioni funzionali e di sicurezza del dispositivo mobile per i dispositivi Windows 10 Desktop e Mobile registrati.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di Windows 10 in Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md).|
|**Configurazione generale (Windows 10 Team e versioni successive)**|Configurare la sicurezza dei dispositivi e le impostazioni funzionali per i dispositivi Windows 10 Team registrati (ad esempio, un dispositivo Surface Hub).<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di configurazione di Windows Team in Microsoft Intune](windows-team-configuration-policy-settings-in-microsoft-intune.md)..|
|**Configurazione generale (Windows 8.1 e versioni successive)**|Configurare le impostazioni funzionali e di sicurezza del dispositivo mobile per i dispositivi Windows registrati.<br /><br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di Windows in Microsoft Intune](windows-configuration-policy-settings-in-microsoft-intune.md).|
|**Configurazione generale (Windows Phone 8.1 e versioni successive)**|Configurare le impostazioni funzionali e di sicurezza del dispositivo mobile.<br />Consente di specificare le app che gli utenti possono o non possono usare e di bloccare l'installazione o l'uso di app non conformi.<br /><br />Per informazioni dettagliate, vedere [Windows Phone 8.1 policy settings in Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md) (Impostazioni dei criteri di Windows Phone 8.1 in Microsoft Intune).|
|**Profilo certificato PKCS #12 (PFX) (Windows 10 Desktop e Mobile e versioni successive)**|Usare questo profilo per creare e distribuire le impostazioni PFX per le richieste di certificato del dispositivo.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo certificato SCEP (Windows 8.1 e versioni successive)**<br /><br />**Profilo certificato SCEP (Windows Phone 8.1 e versioni successive)**|Consente di configurare un certificato Simple Certificate Enrollment Protocol (SCEP) che può essere usato con un certificato attendibile di dispositivo mobile per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili Wi-Fi e VPN.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md).|
|**Profilo certificato attendibile (Windows 8.1 e versioni successive)**<br /><br />**Profilo certificato attendibile (Windows Phone 8.1 e versioni successive)**|Consente di configurare un certificato attendibile di dispositivo mobile che può essere usato per autenticare i dispositivi mobili e consentire loro l'accesso a risorse di rete, quali quelle configurate da profili VPN e Wi-Fi.<br /><br />Per informazioni dettagliate, vedere [Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](secure-resource-access-with-certificate-profiles.md)).|
|**Profilo VPN (Windows 10 Desktop e Mobile e versioni successive)**<br /><br />**Profilo VPN (Windows 8.1 e versioni successive)**<br /><br />**Profilo VPN (Windows Phone 8.1 e versioni successive)**|Consente di configurare e distribuire le impostazioni che permettono agli utenti di accedere in modo sicuro alla rete aziendale dal proprio dispositivo mobile. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi al proprio lavoro.<br /><br />Per informazioni dettagliate, vedere [Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md).|
|**Importazione Wi-Fi**|Importare e distribuire le configurazioni Wi-Fi di Windows precedentemente esportate in un file.<br /><br />Per informazioni dettagliate, vedere [Connessioni Wi-Fi in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md).|

## Criteri software

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Criteri di Managed Browser (Android 4 e versioni successive)**<br /><br />**Criteri di Managed Browser (iOS 7.1 e versioni successive)**|Consente di specificare i siti Web a cui gli utenti possono o non possono accedere quando usano l'app Managed Browser.<br /><br />Per informazioni dettagliate, vedere [Gestire l'accesso a Internet usando criteri di Managed Browser con Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).|
|**Criteri di gestione per applicazioni mobili (Android 4 e versioni successive)**<br /><br />**Criteri di gestione di applicazioni mobili (iOS 7.1 e versioni successive)**|Consente di modificare la funzionalità delle app distribuite per adeguarle ai criteri aziendali di conformità e di sicurezza. Ad esempio, è possibile limitare le operazioni taglia, copia e incolla in un'app con restrizioni oppure configurare un'app per aprire tutti i collegamenti Web in Managed Browser.<br /><br />Per informazioni dettagliate, vedere l[Configurare e distribuire i criteri di gestione delle applicazioni mobili nella console di Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)|

## Impostazioni del dispositivo mobile comuni

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Criteri di Exchange ActiveSync**|Configurare le impostazioni funzionali e di sicurezza del dispositivo mobile per i dispositivi gestiti da Exchange ActiveSync.<br /><br />Per informazioni dettagliate, vedere [Impostazione dei criteri di Exchange ActiveSync in Microsoft Intune](exchange-activesync-policy-settings-in-microsoft-intune.md)..|
|**Criterio di protezione del dispositivo mobile**|<ul><li>Configura le impostazioni per i dispositivi mobili (tutte le piattaforme), ad esempio:<br /><br /><ul><li>Sicurezza</li><li>Crittografia</li><li>Sistema</li><li>Posta elettronica</li><li>Applicazioni</li></ul></li></ul> **Importante:** Microsoft Intune include ora **criteri di configurazione** distinti per ogni piattaforma del dispositivo e tali criteri includono le impostazioni più aggiornate che è possibile usare. È possibile continuare a usare i criteri di sicurezza del dispositivo mobile. Tutte le distribuzioni esistenti continueranno a funzionare, ma è consigliabile pianificare la migrazione ai nuovi criteri di configurazione non appena possibile.<br />Per informazioni dettagliate, vedere [Impostazioni dei criteri di sicurezza dei dispositivi mobili in Microsoft Intune](mobile-device-security-policy-settings-in-microsoft-intune.md)..|

## Accesso condizionale e criteri di conformità

### Accesso condizionale

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Criteri di Exchange Online**<br /><br />**Criteri di Exchange locale**|Gestire l'accesso alla posta elettronica di Microsoft Exchange dai dispositivi non gestiti da Intune o non conformi ai criteri di conformità creati.<br /><br />Per informazioni dettagliate, vedere [Restrict email access to Exchange Online and new Exchange Online Dedicated environment with Intune](restrict-access-to-exchange-online-with-microsoft-intune.md) (Limitare l'accesso per la posta elettronica a Exchange Online e al nuovo ambiente Exchange online dedicato).|
|**Criteri di SharePoint Online**|Gestire l'accesso a SharePoint Online dai dispositivi non gestiti da Intune o non conformi ai criteri di conformità creati.<br /><br />Per informazioni dettagliate, vedere [Restrict access to SharePoint Online with Microsoft Intune](restrict-access-to-sharepoint-online-with-microsoft-intune.md) (Limitare l'accesso a SharePoint Online con Microsoft Intune).|
|**Skype for Business**|Gestire l'accesso a Skype for Business dai dispositivi non gestiti da Intune o non conformi ai criteri di conformità creati.<br /><br />Per informazioni dettagliate, vedere [Restrict access to Skype for Business with Microsoft Intune](restrict-access-to-skype-for-business-online-with-microsoft-intune.md) (Limitare l'accesso a Skype for Business con Microsoft Intune).|
> [!NOTE]
> Non distribuire i criteri di accesso condizionale a utenti e dispositivi. Configurare invece i criteri necessari, che verranno applicati a tutti i gruppi di destinazione indicati nei criteri.

### Criteri di conformità

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Criteri di conformità**|Definire il livello di conformità per i dispositivi e quindi segnalare quelli non conformi. Questi criteri vengono usati con l'accesso condizionale per facilitare la valutazione dei dispositivi che dovranno essere bloccati dai servizi.<br /><br />Per informazioni dettagliate, vedere [Criteri di conformità dei dispositivi in Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)..|

## Gestione dei PC Windows

|Nome criteri|Quando usarli|
|---------------|------------------------|
|**Impostazioni agente di Microsoft Intune**|Configurare il client di Intune nei PC, incluse le impostazioni per:<br /><br />-   Endpoint Protection<br />-   Aggiornamenti software<br />-   Pianificazione del controllo dei criteri<br /><br />Questo tipo di criteri può essere distribuito solo a gruppi di dispositivi.<br /><br />I client Intune scaricano i criteri nuovi e aggiornati in base all'impostazione della **frequenza di rilevamento di applicazioni e aggiornamenti**, il cui valore predefinito è 8 ore. Tuttavia, è possibile forzare un aggiornamento dei criteri nei computer in qualsiasi momento.<br /><br />Per informazioni dettagliate, vedere [Keep Windows PCs up to date with software updates in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) (Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune).|
|**Impostazioni di Microsoft Intune Center**|Configurano i dettagli visualizzati in Microsoft Intune Center per i computer gestiti.<br /><br />Questo tipo di criteri può essere distribuito solo a gruppi di dispositivi.<br /><br />Per informazioni dettagliate, vedere [Attività comuni di gestione di PC Windows con client di Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)..|
|**Impostazioni di Windows Firewall**|Consente di configurare le impostazioni di Windows Firewall e le eccezioni per le comunicazioni di rete comuni nei computer, inclusi:<br /><br />-   BranchCache<br />-   Assistenza remota<br />-   Condivisione file multimediali<br /><br />Questo tipo di criteri può essere distribuito solo a gruppi di dispositivi.<br /><br />Per informazioni dettagliate, vedere [Help secure Windows PCs with Endpoint Protection for Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) (Proteggere i PC Windows con Endpoint Protection per Microsoft Intune).|

### Vedere anche

[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


