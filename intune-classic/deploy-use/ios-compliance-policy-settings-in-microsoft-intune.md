---
title: Impostazione dei criteri di conformità per i dispositivi iOS
description: In questo argomento vengono descritte le regole e le impostazioni che è possibile usare nei criteri di conformità per i dispositivi iOS.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 58af24f4c3ed7a650323dab0072d4e5a85f5554c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="compliance-policy-settings-for-ios-devices-in-microsoft-intune"></a>Impostazioni dei criteri di conformità per i dispositivi iOS in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Le impostazioni dei criteri descritte in questo argomento si applicano ai dispositivi che eseguono iOS 8.0 e versioni successive.

Per informazioni su altre piattaforme, selezionare una delle voci seguenti:
> [!div class="op_single_selector"]
> - [Impostazioni dei criteri di conformità per i dispositivi Android](android-compliance-policy-settings-in-microsoft-intune.md)
> - [Impostazioni dei criteri di conformità per i dispositivi Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)
> - [Impostazioni dei criteri di conformità per i dispositivi Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema
### <a name="password"></a>Password
- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per consentire a un utente di immettere una password per poter accedere al dispositivo. I dispositivi iOS che usano una password vengono crittografati.

- **Consenti password semplici**: impostare questa opzione su **Sì** per consentire all'utente di creare una password semplice come **1234** o **1111**.

-  **Lunghezza minima password**: specifica il numero minimo di cifre o caratteri per la password dell'utente.

- **Tipo di password richiesto:** specificare se l'utente deve creare una password di tipo **Alfanumerico** o **Numerico**.

- **Numero minimo di set di caratteri:** se **Tipo di password richiesto** è impostato su **Alfanumerico**, usare questa impostazione per specificare il numero minimo di set di caratteri che la password deve avere. I quattro set di caratteri sono:
  -   Lettere minuscole
  -   Lettere maiuscole
  -   Simboli
  -   Numeri

  Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

  Per i dispositivi iOS, questa impostazione si riferisce al numero di caratteri speciali (ad esempio **!**, **#**, **&amp;**) che è necessario includere nella password.

- **Minuti di inattività prima che venga richiesta la password**: specifica il tempo di inattività prima che l'utente debba immettere di nuovo la password.

- **Scadenza password (giorni):** selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.

- **Ricorda cronologia password**: usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.

- **Impedisci riutilizzo delle password precedenti:** se l'opzione **Ricorda cronologia password** è selezionata, specifica il numero di password usate in precedenza che non è possibile usare di nuovo.

- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività**: questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

### <a name="email-profile"></a>Profilo di posta elettronica
- **L'account di posta elettronica deve essere gestito da Intune**: se questa opzione è impostata su **Sì**, il dispositivo deve usare il profilo di posta elettronica distribuito al dispositivo stesso. Il dispositivo è considerato non conforme nelle seguenti situazioni:
  - Il profilo di posta elettronica viene distribuito a un gruppo di utenti diverso dal gruppo di utenti a cui sono destinati i criteri di conformità.
  - L'utente ha già configurato un account di posta elettronica nel dispositivo che corrisponde al profilo di posta elettronica di Intune distribuito nel dispositivo. Intune non può sovrascrivere il profilo con provisioning dell'utente, quindi non può gestirlo. Per garantire la conformità, l'utente deve rimuovere le impostazioni di posta elettronica esistenti. Intune potrà quindi installare il profilo di posta elettronica.

- **Selezionare il profilo di posta elettronica che deve essere gestito da Intune**: se è stata selezionata l'impostazione **L'account di posta elettronica deve essere gestito da Intune**, scegliere **Seleziona** per specificare il profilo di posta elettronica di Intune. Il profilo di posta elettronica deve essere presente nel dispositivo.

     Per dettagli sui profili di posta elettronica, vedere [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="device-health-settings"></a>Impostazioni dello stato dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted**: se si abilita questa impostazione, i dispositivi jailbroken non risultano conformi.

##  <a name="device-properties"></a>Proprietà dispositivo
- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme.
Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse aziendali.

- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali è bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.
