---
title: Controllare, esportare o eliminare i dati personali
description: Informazioni su come controllare, esportare o eliminare i dati personali.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6bb00dc966503439b1553b4167e05b2a630b02a
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2019
ms.locfileid: "71080166"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Controllare, esportare o eliminare i dati personali in Intune

Gli amministratori di Intune possono usare i log di controllo per tenere traccia delle attività riguardanti i dati personali. Gli amministratori possono anche esportare ed eliminare dati personali.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Controllare i dati personali

I log di controllo offrono agli amministratori del tenant una registrazione delle attività che generano una modifica in Microsoft Intune. I log di controllo sono disponibili per molte attività di gestione e in genere per le azioni di creazione, aggiornamento (modifica), eliminazione e assegnazione. È anche possibile verificare le attività remote che generano eventi di controllo. Questi log di controllo possono contenere dati personali da utenti con dispositivi registrati in Intune.  

Per motivi di sicurezza Intune può gestire i log di controllo per le azioni degli utenti e dei dispositivi per un periodo di un anno. Questi log vengono eliminati automaticamente dopo il periodo di conservazione di un anno.

Per esaminare i log di controllo, vedere [Log di controllo per le attività di Intune](monitor-audit-logs.md). 

Gli amministratori non possono eliminare i log di controllo.

Questi eventi di controllo vengono conservati per un anno. Gli amministratori del tenant possono richiedere i log di controllo usando [questo modulo di richiesta di supporto](https://privacy.microsoft.com/en-US/privacy-questions?).

## <a name="export-personal-data"></a>Esportare i dati personali

Gli amministratori possono esportare dati personali degli utenti finali, inclusi gli account, i dati del servizio e i log associati ai fini della conformità con le Richieste del soggetto interessato. Dipende dall'amministratore e dall'organizzazione decidere se fornire o meno al soggetto interessato una copia dei dati personali o se esistono motivi aziendali legittimi per trattenerli. Se si decide di procedere, è possibile fornire una copia del documento effettivo, una versione appositamente redatta o uno screenshot delle parti che si ritiene appropriato condividere.

Per esportare i dati personali di un utente, è possibile usare: 
- Il pannello dei dispositivi MDM di Intune per esportare un elenco di dispositivi. È anche possibile copiare direttamente i dati del dispositivo.
- Lo [script Export-IntuneData.ps1](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>Eliminare i dati personali degli utenti finali

Esistono tre modi per rimuovere i dati personali dalla gestione di Intune:
- Eliminare l'utente da Azure Active Directory
- Ripristinare le impostazioni predefinite del dispositivo
- Rimozione in autonomia dell'utente

### <a name="delete-a-user-from-intune"></a>Eliminare un utente da Intune

Per eliminare i dati personali di un utente finale da Intune, un amministratore deve [eliminare l'utente da Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user). Quando l'utente viene eliminato da AAD (eliminazione definitiva), Intune riceve il segnale di eliminazione da AAD e quindi avvia automaticamente l'eliminazione di tutti i dati personali dell'utente dal servizio Intune. Le informazioni dell'utente verranno eliminate dal servizio Intune entro 30 giorni dall'azione di rimozione.

### <a name="reset-device-to-factory-settings"></a>Ripristino delle impostazioni predefinite del dispositivo
Il ripristino delle impostazioni predefinite consente di ripristinare tutti i dati e le impostazioni personali e dell'azienda sulle impostazioni di fabbrica originali. È utile per fornire un dispositivo al dipendente successivo. I file dell'utente, le applicazioni installate dall'utente e le impostazioni non predefinite vengono rimosse e questi dati vengono eliminati dal servizio di Intune entro 30 giorni dall'azione di rimozione.

### <a name="user-self-removal-from-intune-management"></a>Rimozione in autonomia dell'utente dalla gestione di Intune
Gli utenti possono rimuovere i dispositivi personali [Windows, Android o Apple](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) dalla gestione di Intune senza intervento dell'amministratore.   

### <a name="retire"></a>Ritiro
L'azione **Ritira** consente di rimuovere i dati di cui è stato eseguito il provisioning da Intune, ad esempio le applicazioni aziendali, i dati sulle app gestite in Intune, le impostazioni dei criteri e i profili di posta elettronica sottoposti a provisioning con Intune. Questa azione lascia i dati personali dell'utente nel dispositivo.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Eliminare un tenant da Microsoft Intune

Se un cliente di tenant di Intune annulla il proprio account di Intune, tutti i dati del tenant vengono eliminati entro 180 giorni dopo la chiusura dell'account Intune da parte del cliente. Se il tenant AAD è associato ad altre sottoscrizioni aziendali Microsoft (Azure, Office 365), vengono eliminati solo i dati del cliente per Intune. La risorsa del tenant di AAD viene mantenuta per l'uso con altre sottoscrizioni. Se l'account di Intune è l'unica sottoscrizione associata al tenant di AAD, allora il tenant verrà eliminato insieme a tutte le risorse e ai dati del cliente.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Eliminare un utente in un ambiente di gestione dei dispositivi mobili (MDM) ibrido
In presenza di un ambiente MDM ibrido (Intune integrato con Configuration Manager) è necessario completare le azioni seguenti (nell'ordine indicato) per eliminare un utente completamente e rimuoverlo del tutto da Active Directory locale, Configuration Manager e Intune.

1. Eliminare l'utente dal servizio Active Directory (AD) locale. In questo modo l'utente non verrà più sincronizzato in Azure AD e non verrà più incluso nell'individuazione di Configuration Manager. 
2. Eliminare l'utente dalla console di Configuration Manager per rimuovere l'utente e i dati associati da Configuration Manager. Nella console passare ad **Asset e conformità** > **Utenti**, fare clic con il pulsante destro del mouse sull'utente da eliminare e quindi scegliere **Elimina**.
3. [Eliminare l'utente da AAD](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user), operazione che rimuove contemporaneamente l'utente e i dati associati sia da Azure Active Directory che da Intune. Quando l'utente viene eliminato da AAD (eliminazione definitiva), Intune riceve il segnale di eliminazione da AAD e quindi avvia automaticamente l'eliminazione di tutti i dati personali dell'utente dal servizio Intune. Le informazioni dell'utente verranno eliminate dal servizio Intune entro 30 giorni dall'azione di rimozione.

> [!Important]
>l'onboarding di nuovi clienti di MDM con configurazione ibrida è deprecato. Per altre informazioni, vedere il post di blog [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) (Passare dalla gestione di dispositivi mobili ibrida a Intune in Azure).

## <a name="next-steps"></a>Passaggi successivi

Scoprire come [controllare, esportare o eliminare](privacy-data-audit-export-delete.md) i dati personali in Intune.
