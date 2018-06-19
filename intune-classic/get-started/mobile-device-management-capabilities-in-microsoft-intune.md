---
title: Funzionalità di gestione dei dispositivi registrati
description: Leggere questo argomento per scoprire in che modo Intune consente di gestire i dispositivi registrati.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/12/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 48b9650a8f0d6a79b3abab542148acf0a57c0e41
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024295"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Funzionalità di gestione dei dispositivi registrati di Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune consente di gestire una gamma di dispositivi *registrandoli* nel servizio. È possibile registrare autonomamente alcuni tipi di dispositivi. In alternativa, gli utenti possono usare l'app *portale aziendale*. Questo consente loro di eseguire una serie di operazioni, ad esempio cercare e installare app, verificare la conformità del dispositivo ai criteri aziendali e contattare il supporto IT.

Questo argomento include un elenco completo delle funzionalità offerte dalla registrazione dei dispositivi.

Tutte le attività di gestione, inventario, distribuzione di app, provisioning e ritiro vengono gestite tramite la console di amministrazione di Intune. Gli utenti ottengono l'accesso al portale aziendale da cui possono installare le app, registrare e rimuovere i dispositivi e ottenere assistenza quando devono contattare il reparto IT o il supporto tecnico.



## <a name="device-security-and-configuration"></a>Configurazione e sicurezza dei dispositivi

|Funzionalità|Dettagli|Altre informazioni|
|--------------|-----------|--------------------|
|Criteri di configurazione<br><br>Criteri personalizzati| Consentono di gestire molte impostazioni e funzionalità dei dispositivi mobili dell'organizzazione. Ad esempio è possibile impostare una password obbligatoria, limitare il numero di tentativi non riusciti, limitare l'intervallo di tempo prima del blocco dello schermo, impostare la scadenza della password e impedire che vengano usate password già usate in precedenza. È anche possibile controllare l'uso delle funzionalità hardware e software, ad esempio la fotocamera del dispositivo o il Web browser.<br><br>Usare i criteri personalizzati quando i criteri di configurazione non includono l'impostazione necessaria. Per i dispositivi iOS è possibile importare le impostazioni esportate dallo strumento Apple Configurator. Per altri dispositivi è possibile usare le impostazioni OMA-URI (Open Mobile Alliance Uniform Resource Identifier) per configurare le impostazioni e le funzionalità nel dispositivo.|[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)|
|Cancellazione remota, blocco remoto e reimpostazione passcode|Cancella i dati riservati quando un dispositivo viene smarrito o rubato. Ad esempio, è possibile bloccare in remoto il dispositivo, ripristinarne le impostazioni predefinite o cancellare solo i dati aziendali.<br><br>È possibile reimpostare i passcode se gli utenti perdono l'accesso al dispositivo, bloccare i dispositivi persi o rubati o persino cancellarne i dati.|[Protezione dei dispositivi con blocco remoto e reimpostazione passcode](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)|
|Modalità tutto schermo|Consente di bloccare alcune funzionalità dei dispositivi mobili, ad esempio l'acquisizione schermo e l'alimentazione. Consente anche di limitare i dispositivi per eseguire una sola app specificata dall'utente.|[Impostazioni dei criteri di configurazione di iOS in Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|

## <a name="app-management"></a>Gestione delle app

|Funzionalità|Dettagli|Altre informazioni|
|--------------|-----------|--------------------|
|Gestione e distribuzione delle app|Offre una serie di strumenti che consentono di gestire le app mobili in tutte le fasi del ciclo di vita, inclusa la distribuzione di app da file di installazione e App Store, il monitoraggio dettagliato dello stato delle app e la rimozione delle app.|[Distribuire app in Microsoft Intune](/intune-classic/deploy-use/deploy-apps)|
|Applicazioni conformi e non conformi|Consente di specificare elenchi di app conformi (che gli utenti sono autorizzati a installare) e di app non conformi (che gli utenti non sono autorizzati a installare).|[Impostazioni dei criteri di iOS in Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Gestione per applicazioni mobili|Configura limitazioni per le applicazioni mediante la gestione di applicazioni mobili sia per i dispositivi gestiti con Intune sia per quelli non gestiti con Intune. Questo consente di aumentare la sicurezza dei dati aziendali grazie alla limitazione delle operazioni di copia/incolla, backup esterno dei dati e trasferimento dei dati tra le app.|[Configurare e distribuire criteri di gestione delle applicazioni mobili nella console di Microsoft Intune](/intune/app-wrapper-prepare-android)|
|Configurazione delle app mobili iOS|Usa i criteri di configurazione delle app per dispositivi mobili per specificare impostazioni per app iOS che pssono essere necessarie quando l'utente esegue l'app. Ad esempio, un'app può richiedere all'utente di specificare un numero di porta o informazioni di accesso. Questo può semplificare la configurazione dell'app e ridurre il numero di chiamate all'help desk.|[Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Profili di provisioning delle app mobili iOS|Consente di distribuire in modo proattivo i profili di provisioning alle app iOS prossime alla scadenza. |[Usare i criteri del profilo di provisioning per dispositivi mobili iOS per impedire la scadenza delle app](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles)|
|Managed Browser|Configura i criteri di Managed Browser per controllare i siti Web che gli utenti possono visitare. Inoltre, è possibile applicare i criteri di gestione delle applicazioni mobili a Managed Browser.|[Gestire l'accesso a Internet usando criteri di Managed Browser con Microsoft Intune](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello for Business|Consente di eseguire l'integrazione con Windows Hello for Business, un metodo di accesso alternativo per Windows 10 che usa un'istanza locale di Active Directory o Azure Active Directory per sostituire password, smart card o smart card virtuali.|[Controllare le impostazioni di Windows Hello for Business nei dispositivi con Microsoft Intune](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|App acquistate con Volume Purchase Program|Semplifica la gestione delle app acquistate con Volume Purchase Program importando le informazioni di licenza dall'App Store, verificando il numero di licenze usate e impedendo l'installazione di più copie dell'app rispetto a quelle possedute.|[Gestire le app acquistate con Volume Purchase Program con Microsoft Intune](/intune-classic/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## <a name="company-resource-access"></a>Accesso alle risorse aziendali

|Funzionalità|Dettagli|Altre informazioni|
|--------------|-----------|--------------------|
|Profili certificato|Crea e distribuisce profili certificato attendibili e certificati SCEP (Simple Certificate Enrollment Protocol) che possono essere usati per proteggere e autenticare profili Wi-Fi, VPN e di posta elettronica.|[Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)|
|Profili Wi-Fi|Distribuisce le impostazioni di rete wireless agli utenti. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente deve eseguire per connettersi alla rete aziendale.|[Connessioni Wi-Fi in Microsoft Intune](/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)|
|Profili di posta elettronica|Crea e distribuisce le impostazioni di posta elettronica ai dispositivi. In questo modo, gli utenti possono accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione.|[Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|Profili VPN|Distribuisce impostazioni VPN agli utenti e ai dispositivi dell'organizzazione. La distribuzione di queste impostazioni consente di ridurre al minimo le operazioni che l'utente deve eseguire per connettersi alle risorse nella rete aziendale.|[Connessioni VPN in Microsoft Intune](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune)|
|Criteri di accesso condizionale|Gestisce l'accesso a SharePoint Online e alla posta elettronica di Microsoft Exchange da dispositivi non gestiti da Intune.|[Limitare l'accesso alla posta elettronica e a SharePoint con Microsoft Intune](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## <a name="inventory-and-reporting"></a>Inventario e creazione di report

|       Funzionalità        |                                             Dettagli                                              |                                                                  Altre informazioni                                                                   |
|-------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Inventario e creazione di report | Trova informazioni sui dispositivi gestiti e sul software che usano. | [Informazioni sui dispositivi con inventario in Microsoft Intune](/intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune) |

