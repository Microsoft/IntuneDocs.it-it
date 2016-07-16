---
title: Integrazione di Intune con prodotti e servizi cloud Microsoft | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 49675811-08a3-408f-810b-89552ff404bd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: e58b295bf89e200c7c986902c9b4408d23e67c64


---

# Integrazione di Intune con prodotti e servizi cloud Microsoft

Prima di configurare [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] leggere questo argomento e gli altri requisiti elencati in [Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).
##Integrazione con altri servizi cloud Microsoft


[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] condivide una base comune con altri servizi cloud Microsoft. Quando si usa lo stesso account per sottoscrivere più servizi cloud, tali servizi usano la stessa infrastruttura di Microsoft Azure Active Directory e sono tenant di Azure Active Directory. Azure Active Directory fornisce le principali funzionalità di gestione identità e directory per i servizi cloud Microsoft.

Altre informazioni sull'[amministrazione di Azure Active Directory](http://technet.microsoft.com/library/hh967611.aspx) nella libreria TechNet.

## Integrazione con altri prodotti Microsoft
È possibile usare [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] come servizio autonomo sul cloud oppure come servizio cloud che si integra con altri prodotti. Attualmente, solo [!INCLUDE[cmshort](../includes/cmshort_md.md)] può integrarsi direttamente con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

La decisione di eseguire l'integrazione di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] con [!INCLUDE[cmshort](../includes/cmshort_md.md)] è una scelta permanente che richiede l'impostazione dell'autorità di gestione dei dispositivi mobili dalla console di [!INCLUDE[cmshort](../includes/cmshort_md.md)] e non dal [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]. Dopo aver impostato l'autorità di gestione dei dispositivi mobili, non è possibile modificare o annullare questa configurazione.

Quando si usa [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] con [!INCLUDE[cmshort](../includes/cmshort_md.md)], non viene usata la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] per gestire [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], ma la console di [!INCLUDE[cmshort](../includes/cmshort_md.md)]. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] usa ancora la memorizzazione cloud in Azure per ospitare il software distribuito ai dispositivi gestiti con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Per altre informazioni, vedere [Gestire i dispositivi mobili con Configuration Manager e Microsoft Intune](http://msdn.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10) nella documentazione di [!INCLUDE[cm5short](../includes/cm5short_md.md)] SP1.

### Vedere anche
[Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=Jun16_HO4-->


