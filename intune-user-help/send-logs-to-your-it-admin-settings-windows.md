---
title: Inviare i log all'amministratore IT per i dispositivi Windows 10 | Microsoft Docs
description: Registrare un dispositivo Windows 10 1511 in Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: be9976f03bf749222ca372040d4d936e6a8fd26b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="send-logs-to-your-it-admin-from-the-settings-app-for-windows-10"></a>Inviare i log all'amministratore IT dall'app Impostazioni per Windows 10

Se si verifica un errore durante l'uso di un dispositivo Windows 10 gestito dall'azienda, è possibile inviare informazioni sull'errore tramite posta elettronica per consentire all'amministratore IT di risolvere il problema. Queste informazioni vengono memorizzate nel dispositivo in uno specifico documento definito _log di diagnostica_.

1.  Aprire l'app **Impostazioni** di Windows. Passare al **menu Start** e selezionare il pulsante **Impostazioni**. È anche possibile cercare "impostazioni" nella barra di ricerca.
2.  Passare ad **Account** > **Accedi all'azienda o all'istituto di istruzione**.
3.  Selezionare "Esporta i file di log di gestione".

  ![Schermata "Accedi all'azienda o all'istituto di istruzione" con l'opzione Esporta sotto l'intestazione "Impostazioni correlate".](./media/w10-export-logs.png)

4. I log verranno salvati in **C:\Users\Public\Public Documents\MDMDiagnostics**. Verranno creati due file: uno è il log stesso e l'altro è un documento speciale che consente all'amministratore di esaminare i log in programmi diversi, ad esempio Microsoft Excel. Allegare entrambi i file a un messaggio di posta elettronica e inviarlo all'amministratore IT. Se si esegue questa operazione più volte, scegliere semplicemente i file del giorno in cui sono stati creati i log. 

Potrebbe anche essere necessario inviare i [log dall'app Portale aziendale](send-logs-to-your-it-admin-cp-windows.md) per offrire all'amministratore IT ulteriore supporto per la risoluzione degli eventuali problemi rilevati. 

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).