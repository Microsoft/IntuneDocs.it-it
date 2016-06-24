---
# required metadata

title: Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune? | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d22f5aea-7be4-419b-b51b-a522ca037b69

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune?

Quando si installa l'app Portale aziendale e si registra il dispositivo Android in Intune, è possibile usare tale app per:

-   Accedere alla rete aziendale e ai file della posta elettronica e di lavoro

-   Ottenere app aziendali dal Portale aziendale

-   Configurare automaticamente l'account di posta elettronica aziendale

-   Ripristinare le impostazioni di fabbrica del telefono se questo viene smarrito o rubato

Quando si registra il dispositivo Android, vengono concesse all'amministratore IT le autorizzazioni per accedere al dispositivo. Tali autorizzazioni consentono di:

-   Ripristinare le impostazioni predefinite del dispositivo. Questa operazione è utile se il dispositivo viene smarrito o rubato.

-   Rimuovere tutti i dati correlati alla società. Impostazioni e dati personali non vengono rimossi.

-   Potrebbe essere necessario impostare una password o un PIN, che bloccherà il dispositivo, ripristinerà le impostazioni predefinite o eliminerà i dati dopo troppi tentativi di accesso con password errata.

-   Richiedere di accettare i termini e le condizioni.

-   Attivare o disattivare la fotocamera del dispositivo.

-   Forzare la crittografia di tutti i dati sul dispositivo, inclusi i dati aziendali e personali. Questa operazione consente di proteggere i dati se il dispositivo viene smarrito o rubato.

-   Dopo aver aggiunto il dispositivo al portale aziendale, ogni 8 ore circa verranno eseguite le operazioni seguenti:

    -   Download degli aggiornamenti di criteri o app resi disponibili dall'amministratore IT.

    -   Inviare gli aggiornamenti dell'inventario hardware (questi aggiornamenti non contengono informazioni personali).

    -   Invio degli aggiornamenti dell'inventario delle app aziendali (questi aggiornamenti non contengono informazioni personali).

Per informazioni, contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

### Vedere anche
[Uso del dispositivo Android con Intune](using-your-android-device-with-intune.md)

<!--HONumber=Jun16_HO2-->


