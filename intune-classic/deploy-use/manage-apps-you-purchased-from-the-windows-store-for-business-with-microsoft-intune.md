---
title: Gestire le app di Microsoft Store per le aziende
description: Connettere Microsoft Intune a Microsoft Store per le aziende se si vuole gestire e distribuire app acquistate con Volume Purchase Program dalla console di Intune
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e4bac9ba7497b579d05318bd2d11829a44dbc482
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Gestire le app acquistate in Microsoft Store per le aziende con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In [Microsoft Store per le aziende](https://www.microsoft.com/business-store) è possibile trovare e acquistare app per l'organizzazione, singolarmente o con Volume Purchase Program. Collegando lo Store a Microsoft Intune è possibile gestire dalla console di Intune le app acquistate con Volume Purchase Program. Ad esempio:
* È possibile sincronizzare l'elenco di app acquistate dallo Store con Intune.
* Le app sincronizzate vengono visualizzate nella console di amministrazione di Intune ed è possibile distribuirle come qualsiasi altra app.
* È possibile tenere traccia del numero di licenze disponibili e del numero di licenze in uso nella console di amministrazione di Intune.
* Intune blocca la distribuzione e l'installazione di app se non sono disponibili licenze sufficienti.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare la sincronizzazione e la distribuzione di app da Microsoft Store per le aziende, leggere attentamente le informazioni seguenti:
* È necessario configurare Intune come autorità di gestione dei dispositivi mobili dell'organizzazione. Per altre informazioni, vedere [Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md).
* È necessario ottenere un account registrandosi in Microsoft Store per le aziende.
* Dopo che un account di Windows Store per le aziende è stato associato a Intune, non è possibile passare a un altro account in futuro.
* Le app acquistate dallo Store non possono essere aggiunte o eliminate manualmente da Intune. Possono solo essere sincronizzate con Microsoft Store per le aziende.
* Intune sincronizza solo le app concesse in licenza online e acquistate da Microsoft Store per le aziende.
* Per usare questa funzionalità i dispositivi devono essere aggiunti a Servizi di dominio Active Directory o all'area di lavoro.
* I dispositivi registrati devono usare la versione 1511 di Windows 10.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Associare l'account Microsoft Store per le aziende a Intune
Prima di abilitare la sincronizzazione nella console di Intune, è necessario configurare l'account dello Store per usare Intune come strumento di gestione:
1. Assicurarsi di accedere a Windows Store per le aziende con lo stesso account tenant usato per accedere a Intune.
2. In Business Store scegliere **Impostazioni** > **Strumenti di gestione**
3. Nella pagina Strumenti di gestione scegliere **Aggiungi uno strumento di gestione** e scegliere **Microsoft Intune**.

> [!NOTE]
> Se si usa più di uno strumento di gestione per distribuire le app di Microsoft Store per le aziende, in precedenza era possibile associare soltanto un'app a Microsoft Store per le aziende. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager.

È ora possibile continuare con l'impostazione della sincronizzazione nella console di Intune.

## <a name="configure-synchronization"></a>Configurare la sincronizzazione

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione**.
2. Nell'area di lavoro **Amministrazione** espandere **Gestione dei dispositivi mobili** > **Windows** e quindi scegliere **Store for Business**.
3. Nella pagina **Microsoft Store per le aziende** eseguire le operazioni seguenti:
 * Se non è già stato fatto, fare clic sul collegamento per registrarsi a Microsoft Store per le aziende.
 * Dopo aver effettuato la registrazione, fare clic su **Configura sincronizzazione**.
4. Nella finestra di dialogo **Configura sincronizzazione app di Microsoft Store per le aziende** selezionare **Abilita sincronizzazione di Microsoft Store per le aziende**.
5. Nell'elenco a discesa **Lingua** selezionare la lingua in cui visualizzare le app scaricate da Microsoft Store per le aziende nella console di Intune. Indipendentemente dalla lingua in cui sono visualizzate, verranno installate nella lingua dell'utente finale, quando disponibile.
6. Fare clic su **OK**.

## <a name="synchronize-apps"></a>Sincronizzare le app

1. Nella pagina **Microsoft Store per le aziende** scegliere **Sincronizza** per sincronizzare le app acquistate dallo Store con Intune.
2. Nell'area di lavoro **App** scegliere **App** > **App acquistate con Volume Purchase Program** per visualizzare le app che è possibile distribuire, quindi verificare che le app acquistate siano state importate correttamente. Le app in questo nodo vengono visualizzate con il numero totale di licenze possedute e con il numero di licenze ancora disponibili.
Ad esempio, è possibile acquistare l'app Portale aziendale (licenza online) da Microsoft Store per le aziende, sincronizzarla con la console di Intune e quindi distribuirla come app obbligatoria nei dispositivi Windows 10 richiesti. 


## <a name="deploy-apps"></a>Distribuire le app

Le app scaricate dallo Store vengono distribuite allo stesso modo di qualsiasi altra app di Intune. Per altre informazioni vedere [Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Quando si distribuisce un'app di Microsoft Store per le aziende, viene usata una licenza per ogni utente che installa l'app. Se si usano tutte le licenze disponibili per un'app distribuita, non sarà possibile distribuire altre copie. Scegliere una delle azioni seguenti:
* Disinstallare l'app da alcuni dispositivi.
* Ridurre l'ambito della distribuzione corrente agli utenti per i quali si dispone di un numero sufficiente di licenze.
* Acquistare più copie dell'app da Microsoft Store per le aziende.

> [!Important]
> Le app distribuite sono disponibili solo per l'utente che ha originariamente registrato il dispositivo. Gli altri utenti non possono accedere all'app.


### <a name="see-also"></a>Vedere anche
[Aggiungere app per dispositivi mobili in Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)
