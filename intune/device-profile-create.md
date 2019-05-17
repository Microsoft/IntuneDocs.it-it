---
title: Creare profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o configurare un profilo di configurazione del dispositivo in Microsoft Intune. Selezionare il tipo di piattaforma, configurare le impostazioni e aggiungere un tag di ambito.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570403"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Creare un profilo di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I profili di dispositivo consentono di aggiungere e configurare impostazioni e quindi di eseguire il push di queste impostazioni nei dispositivi dell'organizzazione. Per informazioni più dettagliate e procedure, vedere [Applicare le impostazioni delle funzionalità nei dispositivi usando i profili dei dispositivi in Microsoft Intune](device-profiles.md).

Questo articolo:

- Elenca i passaggi da eseguire per creare un profilo.
- Illustra come aggiungere un tag di ambito per "filtrare" il profilo.
- Elenca la frequenza dei cicli di aggiornamento quando i dispositivi ricevono i profili e i relativi aggiornamenti.

## <a name="create-the-profile"></a>Creare il profilo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.

2. Selezionare **Configurazione del dispositivo**. Sono disponibili le seguenti opzioni:

    - **Panoramica**: elenca lo stato dei profili e offre dettagli aggiuntivi sui profili assegnati a utenti e dispositivi.
    - **Gestione**: consente di creare profili di dispositivo, caricare [script di PowerShell](intune-management-extension.md) personalizzati da eseguire all'interno del profilo e di aggiungere piani dati ai dispositivi che usano [eSIM](esim-device-configuration.md).
    - **Monitoraggio**: consente di verificare lo stato di un profilo e le operazioni riuscite e non riuscite, nonché di visualizzare i log per i profili.
    - **Configurazione**: aggiungere un'autorità di certificazione SCEP o PFX o abilitare [Gestione delle spese per telecomunicazioni](telecom-expenses-monitor.md) nel profilo.

3. Selezionare **Profili** > **Crea profilo**. Immettere le proprietà seguenti:

   - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un buon nome di profilo è **Profilo di posta elettronica WP per l'intera azienda**.
   - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
   - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:  

       - **Android**
       - **Android Enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 e versioni successive**
       - **Windows 10 e versioni successive**

   - **Tipo di profilo**: selezionare il tipo di impostazioni da creare. L'elenco visualizzato dipende dalla **piattaforma** scelta.
   - **Impostazioni**: Gli articoli seguenti descrivono le impostazioni per ogni tipo di profilo:

       - [Modelli amministrativi](administrative-templates-windows.md)
       - [Personalizzato](custom-settings-configure.md)
       - [Ottimizzazione recapito](delivery-optimization-windows.md)
       - [Funzionalità dei dispositivi](device-features-configure.md)
       - [Restrizioni dei dispositivi](device-restrictions-configure.md)
       - [Aggiornamento dell'edizione e cambio di modalità](edition-upgrade-configure-windows-10.md)
       - [Istruzione](education-settings-configure.md)
       - [Posta elettronica](email-settings-configure.md)
       - [Endpoint Protection](endpoint-protection-configure.md)
       - [Protezione dell'identità](identity-protection-configure.md)  
       - [Modalità tutto schermo](kiosk-settings.md)
       - [Certificato PKCS](certficates-pfx-configure.md)
       - [Certificato SCEP](certificates-scep-configure.md)
       - [Certificato attendibile](certificates-configure.md)
       - [Criteri di aggiornamento](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     Se ad esempio si seleziona **iOS** come piattaforma, le opzioni del tipo di profilo sono simili a quelle del profilo seguente:

     ![Creare un profilo iOS in Intune](./media/create-device-profile.png)

4. Al termine, selezionare **OK** > **Crea** per salvare le modifiche. Il profilo viene creato e visualizzato nell'elenco.

## <a name="scope-tags"></a>Tag di ambito

Dopo aver aggiunto le impostazioni, si può anche aggiungere un tag di ambito al profilo. I tag di ambito assegnano e filtrano criteri a gruppi specifici, ad esempio il reparto Risorse umane o i dipendenti di una filiale.

Per altre informazioni sui tag di ambito e le relative procedure, vedere [Use RBAC and scope tags for distributed IT](scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

### <a name="add-a-scope-tag"></a>Aggiungere un tag di ambito

1. Selezionare **Ambito (tag)**.
2. Selezionare **Aggiungi** per creare un nuovo tag di ambito. Oppure selezionare un tag di ambito esistente dall'elenco.
3. Selezionare **OK** per salvare le modifiche.

## <a name="refresh-cycle-times"></a>Frequenza dei cicli di aggiornamento

Intune usa i cicli di aggiornamento seguenti per verificare la disponibilità di aggiornamenti per i profili di configurazione:

| Piattaforma | Ciclo di aggiornamento|
| --- | --- |
| iOS | Ogni 6 ore |
| macOS | Ogni 6 ore |
| Android | Ogni 8 ore |
| PC Windows 10 registrati come dispositivi | Ogni 8 ore |
| Windows Phone | Ogni 8 ore |
| Windows 8.1 | Ogni 8 ore |

Se il dispositivo è stato registrato di recente, il controllo viene eseguito con maggiore frequenza:

| Piattaforma | Frequenza |
| --- | --- |
| iOS | Ogni 15 minuti per 6 ore e quindi ogni 6 ore |  
| macOS | Ogni 15 minuti per 6 ore e quindi ogni 6 ore | 
| Android | Ogni 3 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 
| PC Windows 10 registrati come dispositivi | Ogni 3 minuti per 30 minuti e quindi ogni 8 ore | 
| Windows Phone | Ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 
| Windows 8.1 | Ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 

Gli utenti possono aprire in qualsiasi momento l'app Portale aziendale e sincronizzare il dispositivo per controllare immediatamente la disponibilità di aggiornamenti del profilo.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
