---
title: Ripristinare dispositivi iOS gestiti da Intune da backup
description: Offrire indicazioni agli utenti finali su come registrare nuovamente i propri dispositivi dopo il ripristino da backup.
keywords: ripristino, gestito, iOS
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 7fc99a944000a8d5ecfc09ebc2e956e7c0f201c9
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017


---

# <a name="restore-intune-managed-ios-devices-from-backup"></a>Ripristinare dispositivi iOS gestiti da Intune da backup

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In alcuni casi è necessario ripristinare un dispositivo iOS da backup, ad esempio quando si prende possesso di un nuovo dispositivo. In questo argomento vengono illustrati i passaggi aggiuntivi che potrebbe essere necessario eseguire per impostare la gestione di Intune dopo il ripristino del dispositivo.

## <a name="restoring-backups-onto-the-same-device"></a>Ripristino di backup nello stesso dispositivo

Se il backup viene ripristinato nello stesso dispositivo, verrà ripristinato anche lo stato di registrazione del dispositivo. Non sono necessarie altre azioni.

## <a name="restoring-backups-onto-different-devices"></a>Ripristino di backup in dispositivi diversi

Se il backup viene ripristinato in un dispositivo diverso, lo stato della registrazione non viene automaticamente ripristinato nel nuovo dispositivo. Gli utenti devono attenersi alla procedura di registrazione standard nell'app Portale aziendale versione 2.1.22 o successive per [registrare il dispositivo iOS in Intune](/intune-user-help/enroll-your-device-in-intune-ios).

> [!NOTE]
> Se agli utenti finali sono destinati criteri di accesso condizionale, gli utenti potranno accedere alla posta elettronica aziendale solo dopo la nuova registrazione.

> [!TIP]
> Un esempio di comunicazione per gli utenti potrebbe essere il seguente: Per registrarsi nel nuovo dispositivo, verificare che la versione dell'app Portale aziendale corrisponda alla versione 2.1.22 o successiva. Per controllare la versione, aprire l'app Portale aziendale, toccare il pulsante Menu in alto a destra e quindi toccare Info. Se è installata una versione precedente, chiudere l'app Portale aziendale e aprire App Store. Toccare il pulsante Aggiornamenti nell'angolo inferiore destro, quindi toccare il pulsante Aggiorna accanto alla voce Portale aziendale nell'elenco. Al termine dell'aggiornamento, avviare l'app Portale aziendale e [registrare il dispositivo iOS in Intune](/intune-user-help/enroll-your-device-in-intune-ios).

## <a name="resolving-known-issues-with-restores"></a>Risoluzione dei problemi noti di ripristino

Gli utenti potrebbero riscontrare alcune difficoltà in caso di ripristino del dispositivo e di avvio dell'app Portale aziendale se usano ancora la versione 2.1.21 o precedente di quest'ultima. È possibile risolvere queste difficoltà attenendosi alla procedura appropriata per la situazione dell'utente.

### <a name="for-users-who-will-only-use-their-new-device"></a>Per gli utenti che usano solo il nuovo dispositivo
Avviare l'app Portale aziendale e annullare la registrazione selezionando il riquadro del dispositivo corrente e toccando il pulsante __Rimuovi__. Dopo la rimozione attenersi alla procedura di registrazione standard per [registrare un dispositivo iOS in Intune](/intune-user-help/enroll-your-device-in-intune-ios).

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>Per gli utenti che usano sia il dispositivo precedente che quello nuovo
Cancellare i cookie da Safari toccando __Impostazioni__ > __Safari__ > __Cancella dati siti web e cronologia__. Dopo la cancellazione, disinstallare e reinstallare l'app Portale aziendale e quindi seguire la procedura di registrazione standard per [registrare un dispositivo iOS in Intune](/intune-user-help/enroll-your-device-in-intune-ios).

