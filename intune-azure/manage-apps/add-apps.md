---
title: Come aggiungere app in Microsoft Intune | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: queste procedure consentono di ottenere in Intune app pronte per l&quot;assegnazione a utenti e dispositivi. '
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 969ce8deae9142944f3481172277dc252baa5779
ms.openlocfilehash: a7838f57b2eb8bd36a875f7b5b001b12eafcbf8d

---

# <a name="how-to-add-an-app"></a>Come aggiungere un'app 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Prima di poter gestire e assegnare le app per gli utenti, è necessario aggiungerle in Intune. Intune supporta un'ampia gamma di tipi diversi di app e le opzioni possono essere diverse per ogni tipo.

Intune supporta l'aggiunta e l'assegnazione di questi tipi di app:

![Tipi di app supportati da Intune](./media/app-types.png)

Sono supportate le piattaforme seguenti. Fare clic su uno degli argomenti per altre informazioni sulle modalità di aggiunta di tutti i tipi di app.

- [App line-of-business Android](/intune-azure/manage-apps/android-lob-app)
- [App di Android Store](/intune-azure/manage-apps/android-store-app)
- [App line-of-business iOS](/intune-azure/manage-apps/ios-lob-app)
- [App di iOS Store](/intune-azure/manage-apps/ios-store-app)
- [App Web (per tutte le piattaforme)](/intune-azure/manage-apps/web-app)
- [App di Windows Phone 8.1 Store](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [App di Windows Store](/intune-azure/manage-apps/windows-store-app)

> [!NOTE]
> Quando si aggiunge e si distribuisce un'app da un archivio, gli utenti finali devono avere un account dell'archivio per poter installare l'app.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Come creare e modificare le categorie di app 

Le categorie di app possono essere usate per ordinare le app in modo da consentire agli utenti finali di trovarle più facilmente nel portale aziendale. È possibile assegnare una o più categorie a un'app, ad esempio **App per sviluppatori** o **App di comunicazione**. Quando si aggiunge un'app in Intune, è possibile selezionare la categoria desiderata. Usare gli argomenti specifici della piattaforma per aggiungere un'app e assegnare le categorie. Per creare e modificare le categorie, usare la procedura seguente: 

1. Accedere al portale Azure. 
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. 
3. Nel pannello **Intune** scegliere **Gestisci le app**. 
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Installazione** > **Categorie di app**. 
5. Nel pannello **Categorie di app** viene visualizzato un elenco delle categorie correnti. Scegliere una delle azioni seguenti: 
    - **Creare una categoria**: nel pannello **Create category**(Crea categoria) immettere un nome per la nuova categoria. I nomi possono essere immessi in una sola lingua e non vengono tradotti da Intune. Al termine, fare clic su **Crea**.
    - **Modificare una categoria**: per qualsiasi categoria nell'elenco, scegliere "**...**". Nel pannello **Proprietà** è possibile immettere un nuovo nome per la categoria o eliminare la categoria. --->






<!--HONumber=Feb17_HO1-->


