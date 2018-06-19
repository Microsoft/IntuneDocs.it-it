---
title: Gestire le app da Microsoft Store per le aziende
titlesuffix: Microsoft Intune
description: Informazioni su come sincronizzare le app in Intune da Microsoft Store per le aziende, assegnarle e tenerne traccia.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0fb7d432edf62de48e81f65b1ac2f67c6dbad70a
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224954"
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Come gestire le app acquistate in Microsoft Store per le aziende con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In [Microsoft Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dal portale di Azure le app acquistate con Volume Purchase Program. Ad esempio:
* È possibile sincronizzare l'elenco di app acquistate dallo Store con Intune.
* Le app sincronizzate vengono visualizzate nella console di amministrazione di Intune ed è possibile assegnarle come qualsiasi altra app.
* È possibile tenere traccia del numero di licenze disponibili e del numero di licenze in uso nella console di amministrazione di Intune.
* Intune blocca l'assegnazione e l'installazione di app se non sono disponibili licenze sufficienti.
* Le app gestite da Microsoft Store per le aziende revocano automaticamente le licenze quando un utente lascia l'azienda o l'amministratore rimuove l'utente e i dispositivi dell'utente.

## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare la sincronizzazione e l'assegnazione di app da Microsoft Store per le aziende, leggere attentamente le informazioni seguenti:

- Configurare Intune come autorità di gestione dei dispositivi mobili dell'organizzazione.
- È necessario ottenere un account registrandosi in Microsoft Store per le aziende.
- Dopo che un account di Microsoft Store per le aziende è stato associato a Intune, non è possibile passare a un altro account in futuro.
- Le app acquistate dallo Store non possono essere aggiunte o eliminate manualmente da Intune. Possono solo essere sincronizzate con Microsoft Store per le aziende.
- Le app concesse in licenza sia online che offline acquistate da Microsoft Store per le aziende vengono sincronizzate nel portale di Intune. Sarà quindi possibile quindi distribuire le app ai gruppi di dispositivi o ai gruppi di utenti. 
- Le installazioni di app online vengono gestite dallo Store.
- Anche le app offline gratuite possono essere sincronizzate con Intune. Queste app vengono installate da Intune, non dallo Store.
- Per usare questa funzionalità i dispositivi devono essere aggiunti ad Active Directory Domain Services o all'area di lavoro.
- I dispositivi registrati devono usare la versione 1511 di Windows 10 o successive.

Inoltre, i set correlati e le app con licenza offline sincronizzate da Microsoft Store per le aziende ora verranno consolidati in un'unica voce di app nell'interfaccia utente. I dettagli relativi alla distribuzione dei singoli pacchetti verranno migrati in quell'unica voce. Per visualizzare gli insiemi correlati nel portale di Azure, selezionare **Licenze dell'app** dal pannello **App per dispositivi mobili**.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Associare l'account Microsoft Store per le aziende a Intune
Prima di abilitare la sincronizzazione nella console di Intune, è necessario configurare l'account dello Store per usare Intune come strumento di gestione:
1. Assicurarsi di accedere a Windows Store per le aziende con lo stesso account tenant usato per accedere a Intune.
2. In Business Store scegliere **Impostazioni** > **Strumenti di gestione**.
3. Nella pagina Strumenti di gestione scegliere **Aggiungi uno strumento di gestione** e scegliere **Microsoft Intune**.

> [!NOTE]
> In precedenza era possibile associare a Microsoft Store per le aziende un solo strumento di gestione per l'assegnazione di app. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager.

È ora possibile continuare con l'impostazione della sincronizzazione nella console di Intune.

## <a name="configure-synchronization"></a>Configurare la sincronizzazione

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
1. Nel riquadro **App per dispositivi mobili** scegliere **Installazione** > **Microsoft Store per le aziende**.
2. Fare clic su **Abilita**.
3. Se non è ancora stato fatto, fare clic sul collegamento per registrarsi a Microsoft Store per le aziende e associare il proprio account come descritto in precedenza.
5. Nell'elenco a discesa **Lingua** scegliere la lingua in cui visualizzare le app scaricate da Microsoft Store per le aziende nel portale di Azure. Indipendentemente dalla lingua in cui sono visualizzate, vengono installate nella lingua dell'utente finale, se disponibile.
6. Fare clic su **Sincronizza** per trasferire le app acquistate da Microsoft Store in Intune.

## <a name="synchronize-apps"></a>Sincronizzare le app

1. Nel carico di lavoro **App per dispositivi mobili** scegliere **Installazione** > **Microsoft Store per le aziende**.
2. Fare clic su **Sincronizza** per trasferire le app acquistate da Microsoft Store in Intune.

## <a name="assign-apps"></a>Assegnare le app

Le app assegnate dallo Store vengono assegnate allo stesso modo di qualsiasi altra app di Intune. Per altre informazioni, vedere [Come assegnare app ai gruppi con Microsoft Intune](apps-deploy.md). Tuttavia, invece di assegnare le app dalla pagina **Tutte le app**, è necessario assegnarle dalla pagina **App con licenza**.

Le app offline possono essere assegnate a gruppi di utenti, gruppi di dispositivi o gruppi composti da utenti e dispositivi.
Le app offline possono essere installate in un dispositivo per un utente specifico o per tutti gli utenti. 


Quando si assegna un'app di Microsoft Store per le aziende, viene usata una licenza per ogni utente che installa l'app. Se si usano tutte le licenze disponibili per un'app assegnata, non è possibile assegnare altre copie. Eseguire una delle azioni seguenti:
* Disinstallare l'app da alcuni dispositivi.
* Ridurre l'ambito dell'assegnazione corrente agli utenti per i quali si dispone di un numero sufficiente di licenze.
* Acquistare più copie dell'app da Microsoft Store per le aziende.


