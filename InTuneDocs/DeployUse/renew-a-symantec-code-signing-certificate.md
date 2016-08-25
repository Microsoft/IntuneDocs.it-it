---
title: Rinnovare un certificato di firma codice aziendale Symantec da usare con Microsoft Intune | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 566a226c19825990c6a34bffbbd9d1cd6a242ddb


---

# Rinnovare un certificato di firma codice aziendale Symantec per i dispositivi Windows

Il certificato Symantec usato per gestire alcuni dispositivi mobili Windows e Windows Phone deve essere rinnovato periodicamente. Per la registrazione dei dispositivi Windows Phone 8.0 sono necessari un'app Portale aziendale firmata e il certificato di firma codice. I dispositivi Windows Phone successivi possono usare l'app del portale aziendale scaricata dallo Store. Un certificato di firma codice può essere richiesto anche per distribuire app line-of-business.

## Come rinnovare il certificato di firma codice aziendale Symantec

1.  Attendere il messaggio di posta elettronica di rinnovo inviato da Symantec circa 14 giorni prima della scadenza del certificato. Questo messaggio di posta elettronica contiene le indicazioni di Symantec per il rinnovo del certificato aziendale.

    Per altre informazioni sui certificati Symantec, visitare [www.symantec.com](http://www.symantec.com) o chiamare il numero 1-877-438-8776 o 1-650-426-3400.

2.  Visitare il sito Web (ad esempio: [hhttps://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) e accedere con l’ID dell’editore Symantec e l’indirizzo di posta elettronica associato al certificato. Ricordare di usare lo stesso computer in cui sarà scaricato il certificato per avviare il rinnovo.

3.  Una volta approvato e pagato il rinnovo, scaricare il certificato.

## Come installare il certificato aggiornato per Windows Phone 8.0

1.  Scaricare e firmare il Portale aziendale di Windows Phone più recente: [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Aprire la console di amministrazione di Intune ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)), passare ad **Amministrazione**, **Gestione dei dispositivi mobili** &gt; **Windows Phone** e fare clic su **Carica app firmata**.

3.  Caricare il portale aziendale appena firmato. Saranno necessari il file SSP.xap appena firmato e il nuovo file PFX ricevuto da Symantec oppure il token di registrazione dell'applicazione creato con questo nuovo file PFX.

4.  Quando il caricamento è completo, rimuovere la vecchia versione del Portale aziendale nell'area di lavoro **Software** della console di gestione di Intune.

5.  Firmare di nuovo tutte le app aziendali line-of-business usando lo stesso certificato e caricare e sostituire le applicazioni esistenti.

La specifica di un file SSP.xap firmato attualmente è l'unico modo per fornire il certificato di firma codice aggiornato. Per supportare app line-of-business firmate, è necessario firmare e caricare un'app Portale aziendale, anche se gli utenti installeranno l'app Portale aziendale dall'archivio.

## Come installare il certificato aggiornato per i dispositivi Windows Phone 8.1 e versioni successive

1.  Scaricare e firmare il Portale aziendale di Windows Phone più recente dall’Area download alla pagina seguente: [http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Aprire la [console di amministrazione di Intune](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com), passare ad **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone** e fare clic su **Carica app firmata**.

3.  Caricare il portale aziendale appena firmato. Saranno necessari il file SSP.xap appena firmato e il nuovo file PFX ricevuto da Symantec oppure il token di registrazione dell'applicazione creato con questo nuovo file PFX.

4.  Una volta completato il caricamento, rimuovere la versione precedente di Portale aziendale attraverso l’area di lavoro **Software**  .

5.  Firmare tutte le app line-of-business aziendali nuove e aggiornate usando il nuovo certificato. Le applicazioni esistenti non devono essere firmate e distribuite di nuovo.


### Vedere anche
[Configurare la gestione del dispositivo per Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[Configurare la gestione di Windows Phone e Windows 10 Mobile con Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


