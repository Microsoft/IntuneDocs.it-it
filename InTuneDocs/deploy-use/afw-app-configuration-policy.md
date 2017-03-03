---
title: Criteri di configurazione delle app Android for Work | Microsoft Docs
description: Usare i criteri di configurazione delle app per dispositivi mobili in Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un&quot;app Android for Work.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 31e28514ab4bdb0f5af261a1f7c87633ca0bd4a6
ms.openlocfilehash: 58671d037c7f62e5fdaa56657737a4470c90bdb7


---

# <a name="configure-android-for-work-apps-with-mobile-app-configuration-policies-in-microsoft-intune"></a>Configurare le app Android for Work con i criteri di configurazione delle app per dispositivi mobili in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

Usare i criteri di configurazione delle app mobili in Microsoft Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un'app iOS. Ad esempio, un'app può richiedere agli utenti di specificare quanto segue:

-   Un numero di porta personalizzato
-   Impostazione della lingua
-   Impostazioni di personalizzazione, ad esempio il logo aziendale

Se gli utenti immettono impostazioni in modo non corretto, si può verificare un aumento del carico dell'help desk e un rallentamento nell'adozione di nuove app.

I criteri di configurazione delle app per dispositivi mobili consentono di distribuire le impostazioni ai dispositivi prima che gli utenti eseguano l'app. Le impostazioni vengono specificate automaticamente e gli utenti non devono eseguire alcuna azione.

Per usare i criteri di configurazione delle app, è necessario che lo sviluppatore dell'app abbia esposto le configurazioni delle app aziendali al momento della creazione. Ad esempio, Google Chrome espone le impostazioni che consentono di specificare i segnalibri predefiniti, i siti consentiti e negati e molto altro ancora. Contattare lo sviluppatore dell'app per verificare se queste impostazioni sono supportate e come specificarle nei criteri.

I criteri di configurazione delle app vengono distribuiti agli stessi utenti a cui è stata distribuita l'app da configurare. Le impostazioni delle app vengono applicate quando si esegue l'app.

## <a name="configure-a-mobile-app-configuration-policy"></a>Configurare un criterio di configurazione delle app mobili

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Panoramica** &gt; **Aggiungi criterio**.

2.  Nell'elenco dei criteri espandere **Android for Work**, scegliere **Criteri di configurazione dell'app per dispositivi mobili (Android for Work)** e quindi **Crea criterio**.

    > [!TIP]
    > Per questo tipo di criterio è possibile configurare solo le impostazioni personalizzate. Le impostazioni consigliate non sono disponibili.

3.  Nella sezione **Generale** della pagina **Crea criterio** specificare un nome e una descrizione facoltativa per il criterio di configurazione delle app mobili.

4. Nella sezione **Criterio di configurazione delle app per dispositivi mobili** della pagina specificare le informazioni seguenti:
    - **ID pacchetto per l'applicazione a cui si applica questa configurazione**: l'ID pacchetto è indicato nella sezione 'id=' dell'URL dell'app nella pagina Google Play. Ad esempio, l'ID pacchetto per l'app Microsoft Excel è **com.microsoft.office.excel**.
    - Nella casella di testo immettere i dati delle impostazioni dell'app da configurare. È possibile ottenere queste impostazioni dal fornitore dell'app. Non tutte le applicazioni supportano queste impostazioni.
5.  Fare clic su **Convalida** per verificare che per i dati immessi sia stato usato un formato di elenco delle proprietà valido.

    > [!IMPORTANT]
    > Quando si fa clic su **Convalida**, Intune verifica che i dati di configurazione immessi siano in un formato valido. Non verifica che i dati funzionino con l'app a cui sono associati.

6.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio verrà visualizzato nel nodo **Criteri di configurazione** .


## <a name="deploy-the-app-configuration-policy"></a>Distribuire i criteri di configurazione delle app
Dopo aver creato i criteri di configurazione delle app per dispositivi mobili, è necessario distribuirli agli stessi utenti a cui si distribuisce l'app a cui verranno applicate le impostazioni.

Per informazioni su come distribuire i criteri, vedere [Distribuire un criterio di configurazione](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)

Per informazioni su come distribuire le ap a dispositivi Android for Work, vedere [How to deploy Android for Work apps with Intune](android-for-work-apps.md) (Come distribuire app Android for Work con Intune).

Quando l'app distribuita viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione delle app mobili.

> [!TIP]
> Distribuire solo un criterio di configurazione dell'app per ogni app a un utente.



<!--HONumber=Feb17_HO1-->


