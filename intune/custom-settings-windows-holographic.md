---
title: Impostazioni personalizzate per dispositivi Windows Holographic for Business in Microsoft Intune - Azure | Microsoft Docs
description: Creare un profilo personalizzato per l'uso di impostazioni URI OMA con i dispositivi che eseguono Windows Holographic for Business. È possibile configurare le impostazioni del provider del servizio di configurazione (CSP) dei criteri AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates e ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1825d99243654c9fecac7729153a95234d435ff
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Impostazioni personalizzate per i dispositivi che eseguono Windows Holographic for Business in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Usare il profilo **personalizzato** di Microsoft Intune per Windows Holographic for Business per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows Holographic for Business rende disponibili molte impostazioni dei provider di servizi di configurazione (CSP). Per una panoramica sui provider di servizi di configurazione, vedere [Introduzione ai provider di servizi di configurazione per i professionisti IT](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Per i provider di servizi di configurazione specifici supportati da Windows Holographic, vedere [Provider di servizi di configurazione supportati in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Se si sta cercando una determinata impostazione, tenere presente che il [profilo di restrizione del dispositivo Windows Holographic for Business](device-restrictions-windows-holographic.md) contiene molte impostazioni predefinite per cui non è necessario specificare valori personalizzati.

## <a name="create-the-custom-oma-uri-profile"></a>Creare il profilo personalizzato URI OMA
1. Per iniziare, usare le istruzioni riportate in [Creare impostazioni personalizzate per i profili in Microsoft Intune](custom-settings-configure.md).
2. In **Crea profilo** scegliere **Impostazioni** per aggiungere una o più impostazioni URI OMA.
3. In **Impostazioni OMA-URI personalizzate** fare clic su **Aggiungi** per aggiungere un nuovo valore. È anche possibile fare clic su **Esporta** per creare un elenco di tutti i valori configurati in un file con valori delimitati da virgole (estensione CSV).
4. Per ogni impostazione URI OMA che si vuole aggiungere, immettere le informazioni seguenti:
    - **Nome impostazione**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione impostazione**: immettere facoltativamente una descrizione per l'impostazione.
    - **Tipo di dati**: scegliere tra:
        - **Stringa**
        - **Stringa (XML)**
        - **Data e ora**
        - **Intero**
        - **A virgola mobile**
        - **Booleano**
    - **URI OMA (maiuscole/minuscole)**: specificare l'impostazione URI OMA per cui si vuole fornire un'impostazione.
    - **Valore**: specificare il valore da associare all'impostazione URI OMA specificata.
1. Al termine tornare a **Crea profilo** e fare clic su **Crea**.
Il profilo viene creato e visualizzato nell'elenco dei profili.

## <a name="recommended-custom-settings"></a>Impostazioni personalizzate consigliate

Le impostazioni seguenti sono utili per i dispositivi che eseguono Windows Holographic for Business:

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

---
|URI OMA|Tipo di dati  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Intero<br>0 - non consentito<br>1 - consentito (impostazione predefinita)|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

---
|URI OMA|Tipo di dati  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Intero<br>0 - non consentito<br>1 - consentito (impostazione predefinita)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

---
|URI OMA|Tipo di dati  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Intero<br>0 - servizio di aggiornamento non consentito <br>1 - servizio di aggiornamento consentito (impostazione predefinita)|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

---
|URI OMA|Tipo di dati  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Stringa<br>URL - il dispositivo verifica la disponibilità di aggiornamenti dal server WSUS all'URL specificato.<br>Non configurato - il dispositivo verifica la disponibilità di aggiornamenti da Microsoft Update.|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

---
|URI OMA|Tipo di dati  |
|---------|---------|
|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Intero<br>0 - non configurato. Il dispositivo installa tutti gli aggiornamenti applicabili.<br>1 - il dispositivo installa solo gli aggiornamenti sia applicabili sia inclusi nell'elenco degli aggiornamenti approvati. Impostare questo criterio su 1 se il personale IT vuole controllare la distribuzione degli aggiornamenti nei dispositivi, ad esempio quando sono necessari test prima della distribuzione.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

---
|URI OMA|Tipo di dati  |
|---------|---------|
|./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br><br>**Importante**<br>È necessario leggere e accettare i contratti di licenza con l'utente finale per conto degli utenti finali. La mancata accettazione rappresenta una violazione degli obblighi legali e contrattuali.|Nodo per le approvazioni degli aggiornamenti e l'accettazione del contratto di licenza con l'utente finale per conto dell'utente finale.<br/><br/>Per altre informazioni, vedere [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (Provider del servizio di configurazione Update).|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

---
|URI OMA|Tipo di dati  |
|---------|---------|
|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**Importante**<br>L'articolo dedicato al provider del servizio di crittografia AppLocker usa esempi XML con caratteri di escape. Per configurare le impostazioni con profili personalizzati di Intune, è necessario usare XML semplice.|Stringa<br>Per altre informazioni, vedere [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp) (Provider del servizio di configurazione AppLocker).|

## <a name="find-the-policies-you-can-configure"></a>Individuare i criteri che è possibile configurare

È possibile trovare un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows Holographic in [Provider di servizi di configurazione supportati in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Non tutte le impostazioni sono compatibili con tutte le versioni di Windows Holographic. La tabella nell'articolo di Windows indica quali versioni sono supportate per ogni CSP.

Intune, inoltre, non supporta tutte le impostazioni elencate nell'articolo. Per verificare se Intune supporta l'impostazione desiderata, aprire l'articolo relativo all'impostazione. Ogni pagina relativa a un'impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare l'operazione **Add** o **Replace**.
