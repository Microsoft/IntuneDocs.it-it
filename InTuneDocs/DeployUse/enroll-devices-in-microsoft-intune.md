---
# required metadata

title: Registrare i dispositivi | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: damionw
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrare i dispositivi per la gestione in Intune
La Gestione dei dispositivi mobili di Microsoft Intune (MDM) usa la registrazione per gestire i dispositivi e consentire l'accesso alle risorse. Il modo di registrazione dei dispositivi varia a seconda del tipo di dispositivo in uso, della proprietà e del livello di gestione necessario. Per i dispositivi BYOD e di proprietà dell'azienda è necessario un processo di registrazione. Le aziende che usano Exchange ActiveSync, locale oppure ospitato nel cloud, possono abilitare una gestione semplificata senza necessità di registrazione. I PC Windows possono essere gestiti tramite il software client di Intune.

###  Piattaforme per dispositivi supportate

Intune può gestire le piattaforme dei dispositivi seguenti:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Abilitare la registrazione dei dispositivi  
 La registrazione consente agli utenti di accedere a risorse aziendali dai dispositivi personali e all'amministratore di verificare che tali dispositivi siano conformi ai criteri di protezione delle risorse aziendali. È il modo migliore per abilitare gli scenari BYOD con Intune. L'amministratore deve abilitare la registrazione nella console di Intune. È possibile che sia necessario creare una relazione di trust con il dispositivo e assegnare licenze agli utenti. Il dispositivo viene registrato quindi registrato, generalmente dopo che gli utenti immettono le proprie credenziali aziendali o dell'istituto di istruzione. A questo punto il dispositivo riceve i criteri di Intune e può accedere alle risorse.

[Prepararsi alla registrazione dei dispositivi in Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Registrare i dispositivi di proprietà dell'azienda
È possibile gestire i dispositivi di proprietà dell'azienda usando la console di Intune. I dispositivi iOS possono essere registrati direttamente mediante gli strumenti di Apple. Tutti i tipi di dispositivo possono essere registrati da un amministratore o da un responsabile usando il manager di registrazione dispositivi. È anche possibile identificare e contrassegnare come dispositivo di proprietà dell'azienda i dispositivi con numero IMEI e abilitare questo tipo di registrazione.

[Registrare i dispositivi di proprietà dell'azienda](manage-corporate-owned-devices.md)

## Gestione dei dispositivi mobili con Exchange ActiveSync e Intune
I dispositivi mobili che non sono registrati, ma che sono connessi a Exchange ActiveSync, possono essere gestiti da Intune mediante i criteri MDM di EAS. Intune usa Exchange Connector per comunicare con EAS, in locale oppure ospitato nel cloud.



[Gestione dei dispositivi mobili con Exchange ActiveSync e Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Gestire i PC Windows con Intune  
È anche possibile usare Microsoft Intune per gestire i PC Windows che implementano il software client di Intune per PC Windows. I PC gestiti con il client di Intune possono:

 - Compilare relazioni su inventari software e hardware
 - Installare applicazioni desktop, ad esempio file con estensione msi ed exe
 - Impostazioni del firewall

I computer gestiti con il software client di Intune non possono essere cancellati o ritirati in modo selettivo e non possono sfruttare le numerose funzionalità di gestione di Intune, ad esempio l'accesso condizionale, le impostazioni VPN e Wi-Fi o la distribuzione di certificati e le configurazioni di posta elettronica.

[Gestire i PC Windows con Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


