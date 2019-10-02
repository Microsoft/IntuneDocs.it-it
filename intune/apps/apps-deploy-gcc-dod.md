---
title: App per ambienti GCC High e DoD
titleSuffix: Microsoft Intune
description: Informazioni sulle app usate in ambienti GCC High e DoD con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 17d94252dd957c5699b34e0b8c2cbae2eee0b66f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725192"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Distribuzione di app con Intune in ambienti GCC High e DoD 

Gli amministratori tenant possono usare Microsoft Intune per distribuire le app al personale. Il personale è costituito dai dipendenti dell'azienda, ovvero gli utenti delle app. Ci sono molti tipi di app che è possibile distribuire da Intune in ambienti DoD o GCC High. Se un amministratore deve caricare e distribuire un'app di Windows per utenti di un ambiente GCC High o DoD personalizzata, creata da fornitori di terze parti o come app offline scaricata da [Microsoft Store per le aziende](https://businessstore.microsoft.com/store), l'amministratore può decidere di distribuirla come [app line-of-business](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> Per gli ambienti commerciali, un amministratore tenant può sincronizzare lo Store per le aziende con Intune, tuttavia per gli ambienti GCC High e DoD questo servizio non è disponibile. Gli amministratori in questa situazione devono distribuire un'app caricandola direttamente in Intune.  

## <a name="add-line-of-business-apps-using-intune"></a>Aggiungere app line-of-business usando Intune 

Per aggiungere un'app line-of-business destinata a un ambiente GCC High o DoD tramite Intune, è possibile seguire le istruzioni per le [app line-of-business Windows](lob-apps-windows.md). È possibile scegliere di distribuire prima di tutto il Portale aziendale da Microsoft Store per le aziende. Se si sceglie di usare il Portale aziendale, è possibile installarlo e distribuirlo manualmente. Per altre informazioni, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Distribuire app offline dallo Store per le aziende usando Intune  

Se è necessario [scaricare un'app con licenza offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) da Microsoft Store per le aziende, seguire questa procedura per scaricare l'applicazione: 

1. Accedere allo [Store per le aziende](https://businessstore.microsoft.com/).
2. Selezionare **Gestisci** > **Impostazioni**.
3. In **Shopping Experience** (Esperienza di acquisto) impostare **Show offline apps** (Mostra app offline) su **Sì**.

Quando si acquistano le app, se è disponibile una versione offline, sarà possibile scegliere di modificare il tipo di licenza in offline. Dopo aver ottenuto l'app, è possibile gestirla selezionando **Gestisci** > **Prodotti e servizi** nello [Store per le aziende](https://businessstore.microsoft.com/). È anche possibile scaricare l'app e le relative dipendenze. È quindi possibile distribuire l'app scaricata (e le relative dipendenze) agli utenti usando Intune.  

## <a name="syncing-intune-to-the-store-for-business"></a>Sincronizzazione di Intune con lo Store per le aziende 

In un ambiente commerciale (non di enti pubblici), un amministratore può sincronizzare Intune con Microsoft Store per le aziende. Questa funzionalità non è disponibile per gli ambienti di enti pubblici. Per informazioni dettagliate sulle differenze tra Intune negli ambienti commerciali e Intune per gli ambienti di enti pubblici, vedere [Descrizione del servizio Enterprise Mobility + Security per il governo degli Stati Uniti](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Per sincronizzare Intune con l'account dello Store per le aziende, vedere [Come gestire le app acquistate in Microsoft Store per le aziende con Microsoft Intune](windows-store-for-business.md).  

## <a name="compliance"></a>Conformità 

Esaminare le informative sulla privacy e sulla conformità delle app e confrontarle con i requisiti di conformità, sicurezza e privacy dell'organizzazione per stabilire se l'uso di questi servizi è appropriato.   

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sulla distribuzione e sull'assegnazione di app, vedere [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

 
