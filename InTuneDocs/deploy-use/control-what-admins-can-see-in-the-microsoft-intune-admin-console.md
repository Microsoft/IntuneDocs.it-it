---
title: Personalizzare le visualizzazioni della console per i ruoli di amministratore | Microsoft Intune
description: Usare questo argomento per filtrare la visualizzazione della console di amministrazione di Intune per consentire agli amministratori di visualizzare solo gli elementi necessari per il proprio ruolo.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 02448f2f960d98b28780798b469aea23cdab0e2d


---

# Personalizzare le visualizzazioni della console di Intune in base ai ruoli di amministratore
È possibile filtrare la visualizzazione della console di amministrazione di Microsoft Intune per consentire gli amministratori di visualizzare solo gli elementi necessari per il proprio ruolo. Ad esempio, è possibile consentire solo agli operatori della console di amministrazione di aggiornare le definizioni malware o reimpostare il passcode su dispositivi. Questa operazione viene eseguita usando il set di impostazioni **designazioni** che è possibile assegnare a utenti specifici. Quando gli utenti accedono alla console di amministrazione, possono vedere solo gli elementi specifici di loro designazione.

## Per creare una visualizzazione personalizzata

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Amministrazione**&gt;**Amministratori dei servizi**.

2.  Nell'elenco degli amministratori dei servizi scegliere l'utente di cui si vuole modificare la designazione e fare clic su **Gestisci accesso**.

3.  Nella finestra di dialogo **Gestisci accesso** , scegliere il livello di accesso che si desidera assegnare l'utente selezionato. È possibile scegliere tra:

    -   **Accesso completo**
    -   **Accesso in sola lettura**
    -   **Supporto tecnico - Nodo Gruppi**

    Accesso completo e accesso in sola lettura sono di chiara interpretazione. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    **Supporto tecnico - Nodo Gruppi** limita le attività che l'amministratore può eseguire a quanto segue:

    -   Visualizzare elenchi di utenti e dispositivi. L'amministratore non può usare filtri per modificare la visualizzazione. È possibile tuttavia usare filtri di gruppo per modificare quello che l'amministratore può visualizzare. Per altre informazioni, vedere [Creare gruppi per gestire utenti e dispositivi con Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Stampare l'elenco di utenti e dispositivi.

    -   Esportare l'elenco di utenti e dispositivi.

    -   Visualizzare le proprietà di un utente o dispositivo.

    -   È possibile eseguire le seguenti attività:

        -   Esegui un'analisi completa di malware

        -   Esegui un'analisi rapida di malware

        -   Riavvia il computer

        -   Aggiorna definizioni malware

        -   Aggiornare i criteri

        -   Aggiornare l'inventario

        -   Bloccare un dispositivo in modalità remota

        -   Reimpostare un passcode

Il livello di accesso designato viene assegnato all'amministratore configurato quando apre la console di amministrazione di Intune.



<!--HONumber=Oct16_HO4-->


