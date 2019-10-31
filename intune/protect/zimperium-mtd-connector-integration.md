---
title: Integrare Zimperium MTD con Microsoft Intune
titleSuffix: Microsoft Intune
description: Come configurare la soluzione Zimperium Mobile Threat Defense (MTD) con Microsoft Intune per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d843cf707cf182655d0044dde289caca730ccd6b
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810309"
---
# <a name="integrate-zimperium-with-intune"></a>Integrare Zimperium con Intune

Seguire questa procedura per integrare la soluzione Zimperium Mobile Threat Defense (MTD) con Intune.

## <a name="before-you-begin"></a>Prima di iniziare

I passaggi seguenti vengono eseguiti nella [console di Zimperium MTD](https://www.zimperium.com/platform) e consentiranno una connessione al servizio Lookout per i dispositivi registrati di Intune (usando la conformità del dispositivo) e i dispositivi non registrati (usando i criteri di protezione delle app).

Prima di avviare il processo di integrazione di Zimperium con Intune, verificare che siano disponibili la sottoscrizione e le credenziali seguenti:

- Sottoscrizione di Microsoft Intune

- Credenziali di amministratore globale di Azure Active Directory per concedere le autorizzazioni seguenti:

  - Accesso e lettura del profilo utente

  - Accesso alla directory come utente connesso

  - Lettura dati directory

  - Invio di informazioni sul dispositivo a Intune

- Credenziali di amministratore per accedere alla console di Zimperium MTD.

### <a name="zimperium-app-authorization"></a>Autorizzazione dell'app Zimperium

Il processo di autorizzazione dell'app Zimperium è il seguente:

- Concedere al servizio Zimperium le autorizzazioni per comunicare a Intune informazioni relative allo stato di integrità dei dispositivi. Per concedere queste autorizzazioni è necessario usare le credenziali di amministratore globale. La concessione di autorizzazioni è un'operazione da eseguire una volta sola. Una volta concesse le autorizzazioni, le credenziali di amministratore globale non sono necessarie per le operazioni quotidiane.

- Zimperium esegue la sincronizzazione con l'appartenenza al gruppo di registrazione di Azure Active Directory (AD) per popolare il relativo database del dispositivo.

- Consentire alla console di amministrazione di Zimperium di usare la funzionalità Single Sign-On (SSO) di Azure AD.

- Consentire all'app Zimperium di accedere usando la funzionalità SSO di Azure AD.

Per altre informazioni sul consenso e sulle applicazioni di Azure Active Directory, vedere [Richiedere le autorizzazioni da un amministratore di directory](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) nell'articolo di Azure Active Directory *Autorizzazioni e consenso nell'endpoint v2.0 di Azure Active Directory*.


## <a name="to-set-up-zimperium-integration"></a>Per configurare l'integrazione con Zimperium

1. Passare alla [console di Zimperium MTD](https://www.zimperium.com/platform) e accedere con le proprie credenziali. Per eseguire il processo di configurazione dell'integrazione con Zimperium, è necessario accedere con un account utente di Azure Active Directory dotato del ruolo di amministratore globale. Questa operazione di configurazione, da eseguire una volta sola, usa i diritti di amministratore globale per concedere all'interno dell'organizzazione l'autorizzazione necessaria per consentire alle app di Zimperium di comunicare con Intune. 

2. Scegliere **Management** (Gestione) nel menu a sinistra.

3. Scegliere la scheda **MDM Settings** (Impostazioni MDM).

4. Scegliere **Add MDM** (Aggiungi MDM), quindi selezionare **Microsoft Intune** dall'elenco **dei provider MDM**.

5. Dopo aver configurato Microsoft Intune come servizio di gestione dei dati master (MDM), viene visualizzata la finestra **Microsoft Intune Configuration**(Configurazione di Microsoft Intune). Scegliere **Aggiungi Azure Active Directory** per ogni opzione: **Zimperium zConsole**, **app zIPS per iOS e Android** per autorizzare Zimperium a comunicare con Intune e Azure AD tramite Single Sign-On di Azure AD.

    > [!IMPORTANT]  
    > È necessario aggiungere Zimperium zConsole e le app zIPS per iOS e Android per completare il processo di integrazione con Intune.

6. Scegliere **Accept** (Accetta) per autorizzare l'app Zimperium a comunicare con Intune e Azure Active Directory.

7. Dopo aver aggiunto **Zimperium zConsole** e le app **zIPS per iOS e Android** ad Azure AD, aggiungere i gruppi di sicurezza di Azure AD. In questo modo si consente a Zimperium di sincronizzare il gruppo di sicurezza di Azure AD con il proprio servizio.

8. Scegliere **Finish** (Fine) per salvare la configurazione e avviare la sincronizzazione del primo gruppo di sicurezza di Azure AD.

9. Disconnettersi dalla console di Zimperium MTD.

## <a name="next-steps"></a>Passaggi successivi

- [Configurare app Zimperium per i dispositivi registrati](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Configurare app Zimperium per i dispositivi non registrati](~/protect/mtd-add-apps-unenrolled-devices.md)
