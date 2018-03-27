---
title: Impostazioni personalizzate di Microsoft Intune per dispositivi Windows Holographic for Business
titlesuffix: ''
description: Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Windows Holographic for Business.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d5cdba24c10b90756d9a2b9f08fd7d4dcd727303
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-holographic-for-business"></a>Impostazioni per i dispositivi personalizzate di Microsoft Intune per i dispositivi che eseguono Windows Holographic for Business

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Usare il profilo **personalizzato** di Microsoft Intune per Windows Holographic for Business per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows Holographic for Business rende disponibili molte impostazioni dei provider di servizi di configurazione (CSP). Per una panoramica sui provider di servizi di configurazione, vedere [Introduzione ai provider di servizi di configurazione per i professionisti IT](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Per i provider di servizi di configurazione specifici supportati da Windows Holographic, vedere [Provider di servizi di configurazione supportati in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Se si sta cercando una determinata impostazione, tenere presente che il [profilo di restrizione del dispositivo Windows Holographic for Business](device-restrictions-windows-holographic.md) contiene molte impostazioni predefinite per cui non è necessario specificare valori personalizzati.

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
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


|Nome impostazione|URI OMA|Tipo di dati  |
|---------|---------|---------|
|[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)|./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Intero<br>0 - non consentito<br>1 - consentito (impostazione predefinita)|
|[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)|./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Intero<br>0 - non consentito<br>1 - consentito (impostazione predefinita)|
|[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)|./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Intero<br>0 - servizio di aggiornamento non consentito <br>1 - servizio di aggiornamento consentito (impostazione predefinita)|
|[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)|./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Stringa<br>URL - il dispositivo verifica la disponibilità di aggiornamenti dal server WSUS all'URL specificato.<br>Non configurato - il dispositivo verifica la disponibilità di aggiornamenti da Microsoft Update.|
|[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)|./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Intero<br>0 - non configurato. Il dispositivo installa tutti gli aggiornamenti applicabili.<br>1 - il dispositivo installa solo gli aggiornamenti sia applicabili sia inclusi nell'elenco degli aggiornamenti approvati. Impostare questo criterio su 1 se il personale IT vuole controllare la distribuzione degli aggiornamenti nei dispositivi, ad esempio quando sono necessari test prima della distribuzione.|
|[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)|./Vendor/MSFT/Update/ApprovedUpdates<br><br>**Importante**<br>È necessario leggere e accettare i contratti di licenza con l'utente finale per conto degli utenti finali. La mancata accettazione rappresenta una violazione degli obblighi legali e contrattuali.|Nodo per le approvazioni degli aggiornamenti e l'accettazione del contratto di licenza con l'utente finale per conto dell'utente finale.|
[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)|./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br><br>**Importante**<br>L'articolo dedicato al provider del servizio di crittografia AppLocker usa esempi XML con caratteri di escape. Per configurare le impostazioni con profili personalizzati di Intune, è necessario usare XML semplice.|Stringa<br>Per altre informazioni, vedere l'articolo [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp) (Provider del servizio di crittografia AppLocker).

## <a name="how-to-find-the-policies-you-can-configure"></a>Come trovare i criteri che è possibile configurare

È possibile trovare un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows Holographic in [Provider di servizi di configurazione supportati in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Non tutte le impostazioni sono compatibili con tutte le versioni di Windows Holographic. La tabella nell'articolo di Windows indica quali versioni sono supportate per ogni CSP.

Intune, inoltre, non supporta tutte le impostazioni elencate nell'articolo. Per verificare se Intune supporta l'impostazione desiderata, aprire l'articolo relativo all'impostazione. Ogni pagina relativa a un'impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare l'operazione **Add** o **Replace**.
