---
title: Gestire le app da Microsoft Store per le aziende
titlesuffix: Azure portal
description: Informazioni su come sincronizzare le app in Intune da Microsoft Store per le aziende, assegnarle e tenerne traccia."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 649766b26a1061c4bce11235c04dcbe8570fcdc4
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Come gestire le app acquistate in Microsoft Store per le aziende con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


In [Microsoft Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dal portale di Azure le app acquistate con Volume Purchase Program. Ad esempio:
* È possibile sincronizzare l'elenco di app acquistate dallo Store con Intune.
* Le app sincronizzate vengono visualizzate nella console di amministrazione di Intune ed è possibile assegnarle come qualsiasi altra app.
* È possibile tenere traccia del numero di licenze disponibili e del numero di licenze in uso nella console di amministrazione di Intune.
* Intune blocca l'assegnazione e l'installazione di app se non sono disponibili licenze sufficienti.

## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare la sincronizzazione e l'assegnazione di app da Microsoft Store per le aziende, leggere attentamente le informazioni seguenti:

- Configurare Intune come autorità di gestione dei dispositivi mobili dell'organizzazione.
- È necessario ottenere un account registrandosi in Microsoft Store per le aziende.
- Dopo che un account di Windows Store per le aziende è stato associato a Intune, non è possibile passare a un altro account in futuro.
- Le app acquistate dallo Store non possono essere aggiunte o eliminate manualmente da Intune. Possono solo essere sincronizzate con Microsoft Store per le aziende.
- Intune sincronizza le app concesse in licenza sia online che offline acquistate da Microsoft Store per le aziende.
- Solo le applicazioni offline gratuite possono essere sincronizzate con Intune.
- Per usare questa funzionalità i dispositivi devono essere aggiunti ad Active Directory Domain Services o all'area di lavoro.
- I dispositivi registrati devono usare la versione 1511 di Windows 10 o successive.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Associare l'account Microsoft Store per le aziende a Intune
Prima di abilitare la sincronizzazione nella console di Intune, è necessario configurare l'account dello Store per usare Intune come strumento di gestione:
1. Assicurarsi di accedere a Windows Store per le aziende con lo stesso account tenant usato per accedere a Intune.
2. In Business Store scegliere **Impostazioni** > **Strumenti di gestione**
3. Nella pagina Strumenti di gestione scegliere **Aggiungi uno strumento di gestione** e scegliere **Microsoft Intune**.

> [!NOTE]
> In precedenza era possibile associare a Microsoft Store per le aziende un solo strumento di gestione per l'assegnazione di app. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager.

È ora possibile continuare con l'impostazione della sincronizzazione nella console di Intune.

## <a name="configure-synchronization"></a>Configurare la sincronizzazione

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
1. Nel pannello **App per dispositivi mobili** scegliere **Installazione** > **Microsoft Store per le aziende**.
2. Fare clic su **Abilita**.
3. Se non è ancora stato fatto, fare clic sul collegamento per registrarsi a Microsoft Store per le aziende e associare il proprio account come descritto in precedenza.
5. Nell'elenco a discesa **Lingua** scegliere la lingua in cui visualizzare le app scaricate da Microsoft Store per le aziende nel portale di Azure. Indipendentemente dalla lingua in cui sono visualizzate, vengono installate nella lingua dell'utente finale, se disponibile.
6. Fare clic su **Sincronizza** per trasferire le app acquistate da Microsoft Store in Intune.

## <a name="synchronize-apps"></a>Sincronizzare le app

1. Nel carico di lavoro **App per dispositivi mobili** scegliere **Installazione** > **Microsoft Store per le aziende**.
2. Fare clic su **Sincronizza** per trasferire le app acquistate da Microsoft Store in Intune.

## <a name="assign-apps"></a>Assegnare le app

Le app assegnate dallo Store vengono assegnate allo stesso modo di qualsiasi altra app di Intune. Per altre informazioni, vedere [How to assign apps to groups with Microsoft Intune](apps-deploy.md) (Come assegnare app ai gruppi con Microsoft Intune). Tuttavia, invece di assegnare le app dalla pagina **Tutte le app**, è necessario assegnarle dalla pagina **App con licenza**.

Le app offline possono essere assegnate a gruppi di utenti, gruppi di dispositivi o gruppi composti da utenti e dispositivi.
Le app offline possono essere installate in un dispositivo per un utente specifico o per tutti gli utenti. 


Quando si assegna un'app di Microsoft Store per le aziende, viene usata una licenza per ogni utente che installa l'app. Se si usano tutte le licenze disponibili per un'app assegnata, non è possibile assegnare altre copie. Eseguire una delle azioni seguenti:
* Disinstallare l'app da alcuni dispositivi.
* Ridurre l'ambito dell'assegnazione corrente agli utenti per i quali si dispone di un numero sufficiente di licenze.
* Acquistare più copie dell'app da Microsoft Store per le aziende.


