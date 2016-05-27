---
# required metadata

title: Funzionalità di gestione dei PC Windows in Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Funzionalità di gestione dei dispositivi mobili di Microsoft Intune

Microsoft Intune consente di gestire una gamma di dispositivi *registrandoli* nel servizio. Gli utenti possono quindi usare un *portale aziendale* per eseguire una serie di operazioni, ad esempio registrare il dispositivo, cercare e installare app, verificare la conformità del dispositivo ai criteri aziendali e contattare il supporto.
Questo argomento include un elenco completo delle funzionalità offerte dalla registrazione dei dispositivi.

Tutte le attività di gestione, inventario, distribuzione di app, provisioning e ritiro vengono gestite tramite la console di amministrazione di Intune. Gli utenti ottengono l'accesso al portale aziendale da cui possono installare le app, registrare e rimuovere i dispositivi e ottenere assistenza quando devono contattare il reparto IT o il supporto tecnico.



## Configurazione e sicurezza dei dispositivi

|Funzionalità|Dettagli|Altre informazioni|
|--------------|-----------|--------------------|
|Criteri di configurazione<br><br>Criteri personalizzati|I criteri di configurazione dei dispositivi mobili consentono di gestire molte impostazioni e funzionalità dei dispositivi mobili dell'organizzazione. Ad esempio è possibile impostare una password obbligatoria, limitare il numero di tentativi non riusciti, limitare i minuti di attesa prima del blocco dello schermo, impostare la scadenza della password e impedire che vengano usate password già usate in precedenza. È anche possibile controllare l'uso delle funzionalità hardware e software, ad esempio la fotocamera del dispositivo o il Web browser.<br><br>Usare i criteri personalizzati quando i criteri di configurazione non includono l'impostazione necessaria. Per i dispositivi iOS è possibile importare le impostazioni esportate dallo strumento Apple Configurator. Per altri dispositivi è possibile usare le impostazioni URI OMA per configurare le impostazioni e le funzionalità nel dispositivo.|[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|Cancellazione remota, blocco remoto e reimpostazione passcode|Cancellare i dati riservati quando un dispositivo viene smarrito o rubato. Ad esempio, è possibile bloccare in remoto il dispositivo, ripristinarne le impostazioni predefinite o cancellare solo i dati aziendali.<br>È possibile reimpostare i passcode se gli utenti perdono l'accesso al dispositivo, bloccare i dispositivi persi o rubati o persino cancellarne i dati.|[Help protect your devices with remote lock and passcode reset (Proteggere i dispositivi con il blocco remoto e la reimpostazione del passcode)](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) e [Retire devices from Intune management (Ritirare i dispositivi dalla gestione Intune)](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|Modalità tutto schermo|Consente di bloccare alcune funzionalità dei dispositivi mobili, ad esempio l'acquisizione schermo e l'alimentazione. Consente anche di limitare i dispositivi per eseguire una sola app specificata dall'utente.|[Impostazioni dei criteri di configurazione di iOS in Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## Gestione delle app

|Funzionalità|Dettagli|Altre informazioni|
|--------------|-----------|--------------------|
|Gestione e distribuzione delle app|Offre una serie di strumenti che consentono di gestire le app mobili in tutte le fasi del ciclo di vita, inclusa la distribuzione di app da file di installazione e App Store, il monitoraggio dettagliato dello stato delle app e la rimozione delle app.|[Distribuire app in Microsoft Intune](/intune/deploy-use/deploy-apps)|
|Applicazioni conformi e non conformi|Consente di specificare elenchi di app conformi (che gli utenti sono autorizzati a installare) e di app non conformi (che non possono essere installate dagli utenti).|[Impostazioni dei criteri di iOS in Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Gestione per applicazioni mobili|Configurare limitazioni per le applicazioni mediante la gestione di applicazioni mobili sia per i dispositivi gestiti con Intune sia per quelli non gestiti con Intune. Limitando operazioni quali copia/incolla, backup esterno dei dati e trasferimento dei dati tra le app si aumenta la sicurezza dei dati aziendali.|[Configure and deploy mobile application management policies in the Microsoft Intune console](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[Preparare le app per iOS per la gestione delle applicazioni mobili con lo strumento di wrapping delle app di Microsoft Intune](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Preparare l'App per Android per la gestione di applicazioni per dispositivi mobili con lo strumento Microsoft Intune App esegue il Wrapping](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|Configurazione delle app per dispositivi mobili|Usare i criteri di configurazione delle app per dispositivi mobili per specificare impostazioni per app iOS che potrebbero essere necessarie quando l'utente esegue l'app. Ad esempio, un'app potrebbe richiedere all'utente di specificare un numero di porta o informazioni di accesso. Ciò può semplificare la configurazione dell'app e ridurre il numero di chiamate all'help desk.|[Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Managed Browser|Dopo aver distribuito Managed Browser agli utenti, è possibile configurare i criteri di Managed Browser per controllare i siti Web che gli utenti possono visitare. Inoltre, è possibile applicare i criteri di gestione delle applicazioni mobili a Managed Browser.|[Gestire l'accesso a Internet utilizzando criteri di browser gestiti con Microsoft Intune.](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Microsoft Passport|Con Intune è possibile eseguire l'integrazione con Microsoft Passport for Work, un metodo di accesso alternativo per Windows 10 che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale.|[Controllare le impostazioni di Microsoft Passport nei dispositivi con Microsoft Intune](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|

## Accesso alle risorse aziendali

|Funzionalità|Dettagli|Altre informazioni|
|--------------|-----------|--------------------|
|Profili certificato|Creare e distribuire profili certificato attendibile e certificati SCEP (Simple Certificate Enrollment Protocol) che possono essere usati per proteggere e autenticare profili Wi-Fi, VPN e di posta elettronica.|[Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Profili Wi-Fi|Distribuire le impostazioni di rete wireless agli utenti. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alla rete aziendale.|[Connessioni Wi-Fi in Microsoft Intune](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|Profili di posta elettronica|Creare e distribuire le impostazioni di posta elettronica ai dispositivi. In questo modo, gli utenti possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione.|[Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|Profili VPN|Distribuire impostazioni VPN agli utenti e ai dispositivi nella propria organizzazione. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente finale deve eseguire per connettersi alle risorse nella rete aziendale.|[Connessioni VPN in Microsoft Intune](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|Criteri di accesso condizionale|Gestire l'accesso a SharePoint Online e alla posta elettronica di Microsoft Exchange da dispositivi non gestiti da Intune.|[Limitare l'accesso alla posta elettronica e a SharePoint con Microsoft Intune](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## Inventario e creazione di report

|Funzionalità|Dettagli|Altre informazioni|
|--------------|-----------|--------------------|
|Inventario e creazione di report|Trovare informazioni sui dispositivi gestiti e il software che usano.<br /><br />È possibile filtrare questi report in diversi modi, ad esempio in base alla piattaforma del dispositivo e alla conformità del dispositivo agli standard aziendali.|[Comprendere le operazioni di Microsoft Intune con l'uso dei report](/intune/understand-explore/understand-microsoft-intune-operations-by-using-reports)|

### Vedere anche
[Funzionalità di gestione dei PC Windows in Microsoft Intune](/intune/understand-explore/windows-pc-management-capabilities-in-microsoft-intune)


<!--HONumber=May16_HO1-->


