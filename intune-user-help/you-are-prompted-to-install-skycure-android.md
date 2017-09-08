---
title: "È necessario installare Symantec Endpoint Protection Mobile sul dispositivo Android | Microsoft Docs"
description: Informazioni su come installare SEP Mobile sul dispositivo Android in uso.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 627cd171-6e1b-439e-809a-2e6f007c4b3d
searchScope: User help
ROBOTS: 
ms.custom: intune-enduser
ms.openlocfilehash: f94a7cdb4feeea19527efec6486d09efcaca9b67
ms.sourcegitcommit: 1135765fd3ac2149663341d8107f656aba236493
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2017
---
# <a name="you-need-to-install-symantec-endpoint-protection-mobile-on-your-android-device"></a>È necessario installare Symantec Endpoint Protection Mobile sul dispositivo Android

Per l'accesso ai dati aziendali l'amministratore IT richiede di installare l'app Symantec Endpoint Protection (SEP), che consente di proteggere il dispositivo rilevando potenziali minacce per la sicurezza.

Se si verificano problemi con l'installazione, seguire la procedura di risoluzione dei problemi alla fine di questo argomento.

**Eseguire le operazioni seguenti:**

1. Trascinare verso il basso dalla parte superiore della schermata per aprire la barra Notifiche e quindi toccare **Applicazione richiesta - Installa Skycure da Play Store**. È anche possibile accedere a questa app dall'interno dell'app Portale aziendale in __Dettagli conformità__.

  <!--![The compliance details page on an Android device. The device is not in compliance, with a message at the bottom of the Company Portal page that says the device doesn't meet the mobile risk policy, and that Skycure must be opened to resolve the issue.](./media/skycure-resolves-compliance-android.png)-->

2. Verrà visualizzata la pagina di installazione di SEP Mobile in Play Store. Installare SEP Mobile e quindi toccare **ACCEPT** (ACCETTA) per consentire a SEP Mobile di accedere al dispositivo.

3. Aprire SEP Mobile e quindi toccare **VERIFY** (VERIFICA).

4. Toccare **Sign in with Azure Active Directory** (Accedi con Azure Active Directory) e immettere l'account usato per accedere alla posta elettronica e ai file aziendali o dell'istituto di istruzione.

5. Selezionare l'account usato per accedere all'e-mail e ai file di lavoro o scuola e quindi toccare **ADD ACCOUNT**.

6. Toccare **Accept** (Accetta) per autorizzare SEP Mobile a eseguire l'accesso e a leggere il profilo personale.

7. Rivedere le informazioni sulla protezione del dispositivo di SEP Mobile e quindi toccare **OK**. La configurazione di SEP Mobile richiede alcuni minuti, dopodiché viene avviato il controllo delle minacce per la sicurezza nel dispositivo.

8. SEP Mobile avvia immediatamente una ricerca delle minacce per la sicurezza nel dispositivo.

  <!--![Skycure is analyzing your device for security threats.](./media/skycure-scan-in-progress-android.png)-->

  Se SEP Mobile rileva una minaccia per la sicurezza nel dispositivo vengono visualizzate le istruzioni per la risoluzione del problema.

  <!--![Skycure found a security threat.](./media/skycure-found-a-threat-android.png)-->

  Se non viene trovata alcuna minaccia, tutti e tre i tipi di minacce saranno visualizzati in verde.

    La schermata **Dettagli dispositivo** nell'app Portale aziendale indicherà ora la conformità ai requisiti di sicurezza della società.

    ![Il dispositivo è ora conforme ai criteri](./media/mtd-device-now-compliant-android.png)

**Se l'installazione non riesce**

Talvolta le installazioni possono avere esito negativo a causa di problemi tecnici non prevedibili. In questo caso provare a installare SEP Mobile [manualmente da Play Store](https://play.google.com/store/apps/details?id=com.skycure.skycure).

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).
