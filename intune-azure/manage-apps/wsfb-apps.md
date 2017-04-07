---
title: Gestire le app da Windows Store per le aziende
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come sincronizzare le app in Intune da Windows Store per le aziende, assegnarle e tenerne traccia.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: d02d7c3367e18c96cc1d72de3a3a0ef581ef63ff
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Come gestire le app acquistate in Windows Store per le aziende con Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


In [Windows Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dal portale di Intune le app acquistate con Volume Purchase Program. Ad esempio:
* È possibile sincronizzare l'elenco di app acquistate dallo Store con Intune.
* Le app sincronizzate vengono visualizzate nella console di amministrazione di Intune ed è possibile assegnarle come qualsiasi altra app.
* È possibile tenere traccia del numero di licenze disponibili e del numero di licenze in uso nella console di amministrazione di Intune.
* Intune blocca la distribuzione e l'installazione di app se non sono disponibili licenze sufficienti.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare la sincronizzazione e la distribuzione di app da Windows Store per le aziende, leggere attentamente le informazioni seguenti:
* È necessario configurare Intune come autorità di gestione dei dispositivi mobili dell'organizzazione.
* È necessario ottenere un account registrandosi in Windows Store per le aziende.
* Dopo che un account di Windows Store per le aziende è stato associato a Intune, non è possibile passare a un altro account in futuro.
* Le app acquistate dallo Store non possono essere aggiunte o eliminate manualmente da Intune. ma possono solo essere sincronizzate con Windows Store per le aziende.
* Intune sincronizza solo le app concesse in licenza online e acquistate da Windows Store per le aziende.
* Per usare questa funzionalità i dispositivi devono essere aggiunti a Servizi di dominio Active Directory o all'area di lavoro.
* I dispositivi registrati devono usare la versione 1511 di Windows 10 o successive.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Associare l'account Windows Store per le aziende a Intune
Prima di abilitare la sincronizzazione nella console di Intune, è necessario configurare l'account dello Store per usare Intune come strumento di gestione:
1. Assicurarsi di accedere a Windows Store per le aziende con lo stesso account tenant usato per accedere a Intune.
2. In Business Store scegliere **Impostazioni** > **Strumenti di gestione**
3. Nella pagina Strumenti di gestione scegliere **Aggiungi uno strumento di gestione** e scegliere **Microsoft Intune**.

> [!NOTE]
> Se si usa più di uno strumento di gestione per distribuire le app di Windows Store per le aziende, in precedenza era possibile associare soltanto un'app a Windows Store per le aziende. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager.

È ora possibile continuare con l'impostazione della sincronizzazione nella console di Intune.

## <a name="configure-synchronization"></a>Configurare la sincronizzazione

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
1. Nel pannello **App per dispositivi mobili** scegliere **Installazione** > **Windows Store per le aziende**.
2. Fare clic su **Abilita**.
3. Se non è già stato fatto, fare clic sul collegamento per registrarsi a Windows Store per le aziende e associare il proprio account come descritto in precedenza.
5. Nell'elenco a discesa **Lingua** selezionare la lingua in cui visualizzare le app scaricate da Windows Store per le aziende nel portale di Intune. Indipendentemente dalla lingua in cui sono visualizzate, verranno installate nella lingua dell'utente finale, quando disponibile.
6. Fare clic su **Sincronizza** per trasferire le app acquistate da Windows Store in Intune.

## <a name="synchronize-apps"></a>Sincronizzare le app

1. Nel carico di lavoro **Gestisci le app** scegliere **Installazione** > **Windows Store per le aziende**.
2. Fare clic su **Sincronizza** per trasferire le app acquistate da Windows Store in Intune.

## <a name="assign-apps"></a>Assegnare le app

Le app scaricate dallo store vengono assegnate allo stesso modo di qualsiasi altra app di Intune. Per altre informazioni, vedere [How to assign apps to groups with Microsoft Intune](deploy-apps.md) (Come assegnare app ai gruppi con Microsoft Intune). Tuttavia, invece di assegnare le app dalla pagina **Tutte le app**, è necessario assegnarle dalla pagina **App con licenza**.

Quando si assegna un'app di Windows Store per le aziende, viene usata una licenza per ogni utente che installa l'app. Se si usano tutte le licenze disponibili per un'app distribuita, non sarà possibile distribuire altre copie. Scegliere una delle azioni seguenti:
* Disinstallare l'app da alcuni dispositivi.
* Ridurre l'ambito della distribuzione corrente agli utenti per i quali si dispone di un numero sufficiente di licenze.
* Acquistare più copie dell'app da Windows Store per le aziende.

> [!Important]
> Le app distribuite sono disponibili solo per l'utente che ha originariamente registrato il dispositivo. Gli altri utenti non possono accedere all'app.

