---
title: Impostare l'autorità di gestione dei dispositivi mobili
titlesuffix: Microsoft Intune
description: Impostare l'autorità di gestione dei dispositivi mobili in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce6464cc6aa67636743479e69ad2b55c9b102ed9
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2018
---
# <a name="set-the-mobile-device-management-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.

Le configurazioni possibili sono:

- **Intune autonomo**: gestione solo cloud, che viene configurata tramite il portale di Azure. Include il set completo di funzionalità offerte da Intune. [Impostare l'autorità MDM nella console di Intune](#set-mdm-authority-to-intune).

- **Intune ibrido**: integrazione della soluzione cloud di Intune con System Center Configuration Manager. Intune viene configurato tramite la console di Configuration Manager. [Impostare l'autorità MDM in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestione dei dispositivi mobili per Office 365**: integrazione di Office 365 con la soluzione cloud di Intune. Intune viene configurato dall'interfaccia di amministrazione di Office 365. Include un sottoinsieme delle funzionalità disponibili con Intune autonomo. Impostare l'autorità MDM nell'interfaccia di amministrazione di Office 365.

>[!IMPORTANT]    
In Configuration Manager versione 1610 o successiva e Microsoft Intune versione 1705 è possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Per informazioni dettagliate, vedere [Cosa fare se si sceglie l'impostazione dell'autorità MDM sbagliata](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Impostare l'autorità MDM su Intune

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
2. Selezionare l'intestazione arancione per aprire l’impostazione **Autorità di gestione dei dispositivi mobili**.
3. In **Autorità di gestione dei dispositivi mobili** scegliere una delle opzioni seguenti per l'autorità MDM:
  - **Autorità MDM Intune**
  - **Autorità MDM Configuration Manager**
  - **Nessuno**

  ![Immagine della schermata di impostazione dell’autorità di gestione dei dispositivi mobili di Intune](media/set-mdm-auth.png)

  Un messaggio indica che l'autorità MDM è stata impostata su Intune.

## <a name="enable-device-enrollment"></a>Abilitare la registrazione dei dispositivi

Con Intune impostato come autorità MDM, gli utenti possono registrare dispositivi di proprietà personale e ottenere l'accesso alle risorse aziendali, ad esempio la posta elettronica, nei modi seguenti: installando il Portale aziendale (iOS e Android), aggiungendo le credenziali di lavoro (Windows) oppure accedendo al sito Web Portale aziendale (iOS, Android, macOS).

Per abilitare o semplificare la gestione per le diverse piattaforme, sono previsti i requisiti seguenti:
- **iOS** (obbligatorio): [ottenere un certificato push MDM di Apple](apple-mdm-push-certificate-get.md) e quindi [abilitare la registrazione per i dispositivi iOS di proprietà dell'azienda](ios-enroll.md) (facoltativo).
- **Android** (facoltativo): [abilitare i profili di lavoro Android](android-enroll.md)
- **Windows** (facoltativo: abilitare la [registrazione automatica](windows-enroll.md) o la [registrazione in blocco](windows-bulk-enroll.md)
- **macOS** - (obbligatorio) [Ottenere un certificato push MDM Apple](apple-mdm-push-certificate-get.md).


## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Pulizia dei dispositivi mobili dopo la scadenza del certificato MDM

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. In caso di cancellazione dei dispositivi mobili o se questi non riescono a comunicare con il servizio Intune per un determinato periodo di tempo, il certificato MDM non verrà rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.
