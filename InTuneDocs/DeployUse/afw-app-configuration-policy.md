---
title: Usare i criteri di configurazione delle app per dispositivi mobili Android for Work | Microsoft Intune
description: Usare i criteri di configurazione delle app per dispositivi mobili in Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un&quot;app Android for Work.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fc6b645a-e837-4b2a-a10f-144065cbd8dd
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 32bded5047b1a08738418e3e36382eeae1a5f3b4
ms.openlocfilehash: a986e859e38e0936f53c57a75872dc86de3ee181


---

# Configurare le app Android for Work con i criteri di configurazione delle app per dispositivi mobili in Microsoft Intune
Usare i criteri di configurazione delle app mobili in Microsoft Intune per specificare le impostazioni che possono essere richieste quando gli utenti eseguono un'app iOS. Ad esempio, un'app può richiedere agli utenti di specificare quanto segue:

-   Un numero di porta personalizzato.

-   Impostazioni della lingua.

-   Impostazioni di personalizzazione, ad esempio il logo aziendale.

Se gli utenti immettono queste impostazioni in modo non corretto, si può verificare un aumento del carico dell'help desk e un rallentamento nell'adozione di nuove app.

I criteri di configurazione delle app per dispositivi mobili permettono di evitare questi problemi consentendo di distribuire tali impostazioni agli utenti prima dell'esecuzione dell'app. Le impostazioni vengono quindi specificate automaticamente e gli utenti non devono eseguire alcuna azione.

Per usare i criteri di configurazione delle app, è necessario che lo sviluppatore dell'app abbia esposto le configurazioni delle app aziendali al momento della creazione. Ad esempio, Google Chrome espone le impostazioni che consentono di specificare i segnalibri predefiniti, i siti consentiti e negati e molto altro ancora. Contattare lo sviluppatore dell'app per verificare se queste impostazioni sono supportate e come specificarle nei criteri.

I criteri di configurazione delle app vengono distribuiti agli stessi utenti a cui è stata distribuita l'app da configurare. Le impostazioni dei criteri verranno usate ogni volta che viene eseguita l'app.

## Configurare un criterio di configurazione delle app mobili

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


## Distribuire i criteri di configurazione delle app
Dopo aver creato i criteri di configurazione delle app per dispositivi mobili, è necessario distribuirli agli stessi utenti a cui si distribuisce l'app a cui verranno applicate le impostazioni.

Per informazioni su come distribuire i criteri, vedere [Distribuire un criterio di configurazione](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)

Per informazioni su come distribuire le ap a dispositivi Android for Work, vedere [How to deploy Android for Work apps with Intune](android-for-work-apps.md) (Come distribuire app Android for Work con Intune).

Quando l'app distribuita viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione delle app mobili.

> [!TIP]
> Distribuire solo un criterio di configurazione dell'app per ogni app a un utente.







<!--HONumber=Oct16_HO2-->


