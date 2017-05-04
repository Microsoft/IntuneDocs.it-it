---
title: Gestire le app iOS acquistate con Volume Purchase Program | Documentazione Microsoft
description: "Usare Intune per la gestione delle app acquistate con Volume Purchase Program da Apple importando le informazioni di licenza dall&quot;App Store, verificando il numero di licenze usate e impedendo l&quot;installazione di più copie dell&quot;app rispetto a quelle possedute."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: b81228ccd1c515bfd82486475996eecf20655993
ms.lasthandoff: 04/24/2017


---

# <a name="manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Gestire le app iOS acquistate tramite Volume Purchase Program con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

L'App Store iOS consente di acquistare più licenze per un'app da eseguire nell'azienda. In questo modo, è possibile ridurre il carico amministrativo associato al monitoraggio di più copie delle app acquistate.

Microsoft Intune semplifica la gestione delle app acquistate con questo programma importando le informazioni di licenza dall'App Store, verificando il numero di licenze usate e impedendo l'installazione di più copie dell'app rispetto a quelle possedute.

> [!Important]
> Attualmente Intune assegna licenze VPP (Volume Purchase Program per le aziende) per app iOS a utenti e non a dispositivi. Per questo motivo, per installare le app gli utenti finali devono immettere la password dell'ID Apple.
> Il programma Apple Volume Purchase Program (VPP) non è supportato in questa versione.

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gestione delle app acquistate tramite Volume Purchase Program per dispositivi iOS
Per acquistare più licenze per app iOS, è necessario usare [Volume Purchase Program di Apple per le aziende](http://www.apple.com/business/vpp/). A questo scopo, configurare un account VPP di Apple dal sito Web Apple e caricare il token VPP di Apple in Intune.  È quindi possibile sincronizzare le informazioni relative a Volume Purchase Program con Intune e tenere traccia dell'uso delle app acquistate con VPP.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare, è necessario ottenere un token VPP da Apple e caricarlo nell'account di Intune. Tenere anche presente quanto segue:

* Ogni organizzazione può avere solo un account e un token VPP.
* Dopo aver associato un account VPP di Apple a Intune, in seguito non sarà più possibile associare un account diverso. Per questo motivo, è molto importante comunicare a più persone i dettagli dell'account usato.
* Se in passato è stato usato un token VPP con un prodotto diverso, è necessario generare un nuovo token da usare con Intune.
* Ogni token è valido per un anno.
* Per impostazione predefinita, Intune esegue la sincronizzazione con il servizio VPP di Apple due volte al giorno. È possibile avviare una sincronizzazione manuale in qualsiasi momento.
* Dopo avere importato il token VPP in Intune, non importare lo stesso token in un'altra soluzione di gestione dei dispositivi. Questo potrebbe infatti causare la perdita di record relativi agli utenti e alle assegnazioni di licenze.
* Prima di iniziare a usare VPP iOS con Intune, rimuovere tutti gli account utente VPP esistenti creati con altri fornitori di soluzioni di gestione dei dispositivi mobili (MDM). Intune non sincronizzerà tali account utente in Intune come misura di protezione. Intune sincronizza solo i dati dal servizio VPP di Apple creati da Intune stesso.
* Se l'affinità utente per il dispositivo è configurata, è possibile distribuire app VPP per iOS solo nei dispositivi dell'utente registrati mediante il protocollo DEP (Device Enrollment Protocol).

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Per ottenere e caricare un token VPP di Apple

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione** &gt; **iOS e Mac OS X** &gt; **Volume Purchase Program**.

2.  Scegliere il collegamento **Account VPP di Apple**. Registrarsi a Volume Purchase Program per le aziende, se non è già stato fatto. Dopo aver completato l'iscrizione, scaricare il token VPP di Apple per l'account.

3.  Nella pagina **Gestisci Volume Purchase Program (VPP) di Apple** della console di Intune scegliere **Carica un token VPP**.

4.  Nella finestra di dialogo **Carica il token VPP** immettere o incollare il nome del token VPP e il proprio ID Apple, quindi scegliere **Carica**.

5.  Nella finestra di dialogo di avviso selezionare la casella di controllo per indicare di aver compreso che in seguito non sarà possibile passare a un account VPP diverso e quindi scegliere **Sì**.

Nella pagina **Volume Purchase Program** è ora possibile visualizzare le informazioni sul token VPP di Apple, incluse le date dell'ultimo aggiornamento, di scadenza e dell'ultima sincronizzazione con Intune.

È possibile sincronizzare i dati archiviati da Apple con Intune in qualsiasi momento scegliendo **Sincronizza**.

## <a name="to-deploy-a-volume-purchased-app"></a>Per distribuire un'app acquistata tramite Volume Purchase Program

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **App** &gt; **App** &gt; **App acquistate con Volume Purchase Program**. Questo elenco visualizza tutte le applicazioni che sono state sincronizzate dal servizio VPP di Apple.

2.  Scegliere l'app da distribuire, scegliere **Gestisci distribuzione**, quindi usare le istruzioni specificate nell'argomento [Deploy apps in Microsoft Intune](deploy-apps-in-microsoft-intune.md) (Distribuire app in Microsoft Intune) per completare il caricamento, la creazione e la distribuzione dell'app.

> [!TIP]
> È necessario scegliere un'azione di distribuzione **Obbligatoria**. Le installazioni disponibili non sono attualmente supportate. Inoltre, è possibile solo distribuire le app ai gruppi di utenti.

Quando si distribuisce l'app come **Installazione richiesta**, ogni utente che installa l'app usa una licenza.

Per revocare una licenza, è necessario modificare l'azione di distribuzione specificando **Disinstalla**. La licenza verrà revocata una volta disinstallata l'app.

La prima volta che un utente con un dispositivo idoneo tenta di installare un'app VPP gli viene richiesto di partecipare al programma Volume Purchase Program di Apple. È necessario completare questo passaggio per poter proseguire l'installazione dell'app.

Se non ci sono altre licenze disponibili, la distribuzione non riuscirà.

## <a name="to-monitor-apple-vpp-apps"></a>Per monitorare le app VPP di Apple
Per monitorare quali app VPP sono state distribuite e quante licenze sono in uso, è possibile usare l'area di lavoro **App** nel nodo **App acquistate con Volume Purchase Program**.

> [!TIP]
> È anche possibile usare **Filtri** per esaminare lo stato dell'installazione di ogni app.

### <a name="see-also"></a>Vedere anche
[Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md)

