---
title: Impostazioni di conformità per Android for Work
description: Questo argomento descrive le impostazioni dei criteri di conformità per i dispositivi Android compatibili con Android for Work.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 02/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 085cca57365da0df9dd739c3a1b2b0c6dd6fded6
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="compliance-policy-settings-for-android-for-work-devices-in-microsoft-intune"></a>Impostazioni dei criteri di conformità per i dispositivi Android for Work in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Le impostazioni dei criteri descritte in questo argomento si applicano ai dispositivi Android for Work.

Per informazioni su altre piattaforme, selezionare una delle voci seguenti:
> [!div class="op_single_selector"]
> - [Impostazione dei criteri di conformità per Android](android-compliance-policy-settings-in-microsoft-intune.md)
> - [Impostazioni dei criteri di conformità per i dispositivi iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
> - [Impostazioni dei criteri di conformità per i dispositivi Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema
### <a name="password"></a>Password
- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password per poter accedere al dispositivo.

-  **Lunghezza minima password**: specificare il numero minimo di cifre o caratteri che la password dell'utente deve contenere.

- **Qualità password:** questa impostazione rileva se i requisiti di password specificati sono configurati nel dispositivo. Abilitare questa impostazione per richiedere agli utenti la configurazione di determinati requisiti di password per i dispositivi Android. Scegliere tra:
  -   **Protezione biometrica bassa**
  - **Richiesto**
  -   **Almeno numerico**
  -   **Almeno alfabetico**
  -   **Almeno alfanumerico**
  -   **Alfanumerico con simboli**

- **Minuti di inattività prima che venga richiesta la password:** specifica il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni):** selezionare il numero di giorni che mancano alla scadenza della password attuale, quando l'utente deve creare una nuova password.

- **Ricorda cronologia password:** usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.

- **Impedisci riutilizzo delle password precedenti:** se l'opzione **Ricorda cronologia password** è selezionata, specificare il numero di password usate in precedenza che non è possibile riutilizzare.

- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività:** questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti finali viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

### <a name="encryption"></a>Crittografia
- **Richiedi crittografia sul dispositivo mobile:** non è necessario configurare questa impostazione poiché i dispositivi Android for Work applicano la crittografia.

## <a name="device-health-and-security-settings"></a>Impostazioni di integrità e sicurezza dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted:** se si abilita questa impostazione, i dispositivi jailbroken verranno valutati come non conformi.
- **Richiedi che i dispositivi impediscano l'installazione di app da origini sconosciute:** non è necessario configurare questa impostazione poiché i dispositivi Android for Work impediscono sempre l'installazione da origini sconosciute. .  

- **Richiedi la disabilitazione del debug USB**: non è necessario configurare queste impostazioni poiché il debug USB è già disabilitato nei dispositivi Android for Work.

- **Livello minimo di patch di protezione per Android**: usare questa impostazione per specificare il livello minimo di patch per Android.  I dispositivi che non presentano almeno questo livello di patch vengono considerati non conformi. La data deve essere specificata nel formato: AAAA-MM-GG.
- **Richiedi l'abilitazione della protezione dalle minacce per il dispositivo**: usare questa impostazione per considerare la valutazione dei rischi della soluzione di protezione dalle minacce per il dispositivo come condizione di conformità. Selezionare il livello di minaccia massimo consentito tra uno dei seguenti:

  - **Nessuno (protetto)**: questo è il livello più sicuro e indica che il dispositivo non può avere minacce. Se viene rilevata la presenza di minacce di qualsiasi livello per il dispositivo, questo sarà considerato come non conforme.
  - **Bassa**: il dispositivo viene valutato come conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello più alto, il dispositivo verrà messo in stato di non conformità.
  - **Media**: il dispositivo viene valutato come conforme se le minacce presenti nel dispositivo sonio di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.
  - **Alta**: questo è il livello meno sicuro. Fondamentalmente consente tutti i livelli di minaccia ed è utile solo se si usa questa soluzione esclusivamente per la creazione di report.

  Per altre informazioni, vedere [Creare criteri di conformità dei dispositivi](create-lookout-device-compliance-policy.md).

## <a name="device-property-settings"></a>Impostazioni delle proprietà dei dispositivi
- **Versione minima del sistema operativo**: se un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme.
  Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.

- **Versione massima del sistema operativo**: se un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali è bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.
