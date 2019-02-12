---
title: Rimuovere il dispositivo dalla gestione se sono state rifiutate le Condizioni per l'utilizzo | Microsoft Intune
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbf35b77c843b4dc084916b2c283b6c66d5f066d
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849234"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>Rimuovere il dispositivo dalla gestione se sono state rifiutate le Condizioni per l'utilizzo

Se le Condizioni per l'utilizzo sono state rifiutate durante il tentativo di accesso all'app Portale aziendale, non saranno consentiti altri tentativi di accesso all'app Portale aziendale e, pertanto, sarà necessario usare queste istruzioni "alternative" per rimuovere il dispositivo da Intune.

Quando si disinstalla l'app Portale aziendale, viene anche rimosso il dispositivo da Intune. Il dispositivo non sarà più in grado di accedere alle risorse aziendali. Per altre informazioni su cosa accade quando il dispositivo viene rimosso dalla gestione, vedere [Che cosa accade se si annulla la registrazione del dispositivo da Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Prima di disinstallare l'app Portale aziendale, è necessario passare all'impostazione **Device Administrators** e disattivare **Portale aziendale**. La procedura può variare leggermente a seconda del dispositivo Android in uso.

## <a name="removing-the-device-from-the-company-portal-app"></a>Rimozione del dispositivo dall'app Portale aziendale

Per rimuovere il dispositivo da Intune e disinstallare l'app Portale aziendale:

1.  Passare a **Impostazioni** &gt; **Sicurezza &amp; Blocco schermo** &gt; **Amministratori dispositivo**.

    Al termine di questo passaggio la registrazione del dispositivo verrà immediatamente annullata.

2.  Deselezionare la casella accanto a **Portale aziendale** o disattivare il portale.

    Ora è possibile disinstallare l'app Portale aziendale.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Rimozione dei dati raccolti dall'app Portale aziendale

Per rimuovere tutti i dati archiviati dall'app Portale aziendale per Android nel dispositivo:

  - Cancellare tutti i dati dell'app in Applicazioni > selezionare l'app > pulsante di cancellazione dati
  - Eliminare la cartella '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal'


Serve ancora assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.
