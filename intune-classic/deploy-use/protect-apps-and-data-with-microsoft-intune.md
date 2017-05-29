---
title: Proteggere app e dati | Documentazione Microsoft
description: "Questo argomento illustra le varie funzionalità e caratteristiche disponibili in Intune per proteggere le app e i dati aziendali."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: fdd85177f21a430eb940d1f88b3bb016c56cee55
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="protect-apps-and-data-with-microsoft-intune"></a>Proteggere app e dati con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune protegge i dati aziendali tra più livelli di tecnologia. A livello di identità, l'accesso condizionale protegge l'accesso ai servizi consentendo solo l'accesso da dispositivi conformi e gestiti. A livello di applicazione client, la gestione di applicazioni per dispositivi mobili (MAM) consente di evitare la perdita dei dati impedendo lo spostamento dei dati in app o percorsi di archiviazione di dati non protetti e cancellando i dati quando un dispositivo viene smarrito o rubato. È consigliabile usare questi due livelli di protezione insieme, in modo da proteggere i dati assicurando al tempo stesso la produttività dei dipendenti mobili.

Un importante passaggio iniziale per la protezione dei dati aziendali consiste nell'implementazione dell'accesso condizionale. A questo scopo, verificare che i dispositivi usati per accedere ai dati usino soluzioni di protezione della sicurezza quali password complessa e crittografia e che non siano jailbroken. Intune consente di impostare le condizioni che i dispositivi devono rispettare per avere accesso alla posta elettronica e ai dati aziendali.

L'[accesso condizionale](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) è determinato da due tipi di criteri che è possibile impostare in Intune:
- I [criteri di conformità](introduction-to-device-compliance-policies-in-microsoft-intune.md), usati per determinare la conformità di un dispositivo. Esaminano impostazioni e condizioni quali:
  - PIN e password: è possibile creare regole che impongono la specifica di password per sbloccare un dispositivo, nonché regole per i requisiti di complessità della password e per altre impostazioni relative alle password.
  - Crittografia: è possibile limitare l'accesso ai dispositivi che vengono crittografati.
  - Dispositivo non jailbroken o rooted: Intune può rilevare se un dispositivo registrato è jailbroken. È possibile impostare i criteri per bloccare l'accesso a tale dispositivo.
- I [criteri di accesso condizionale](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) vengono configurati per un determinato servizio, ad esempio Exchange Online o SharePoint Online. Per ogni servizio, è possibile definire i gruppi di utenti a cui devono essere applicati questi criteri. È possibile ad esempio assicurarsi che tutti i dipendenti del reparto contabilità possano accedere alla posta elettronica aziendale solo da dispositivi registrati e conformi.

La protezione dell'accesso alle risorse aziendali è solo il primo passaggio per la protezione dei dati aziendali. Dopo che è stato eseguito l'accesso ai dati sul dispositivo, è necessario continuare a proteggerli. I dati possono ora essere copiati, spostati e salvati in un percorso diverso oppure condivisi. Intune risolve questo problema, offrendo la possibilità di limitare lo spostamento dei dati mediante la creazione di un set di regole con le finalità seguenti:
- Bloccare le operazioni di copia e incolla o impedire il trasferimento dei dati all'esterno del contesto aziendale.
- Impedire il backup nello spazio di archiviazione cloud personale, bloccando funzionalità come "Salva con nome".
- Proteggere l'accesso alle app richiedendo PIN/passcode o credenziali aziendali.
- Aprire tutti i collegamenti Web all'interno di Intune Managed Browser.

Questi set di regole sono denominati [criteri di gestione delle applicazioni per dispositivi mobili (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md). È possibile applicare criteri MAM ad app in esecuzione su dispositivi gestiti o non gestiti dall'utente.  

È possibile proteggere i dati aziendali tramite criteri MAM applicati a dispositivi **registrati in Intune**, dispositivi **registrati e gestiti da una soluzione di gestione di dispositivi mobili (MDM) di terze parti** o dispositivi che **non sono registrati in alcuna soluzione MDM**, ad esempio i dispositivi di proprietà dei dipendenti.

Per associare un'app a un criterio MAM, l'app deve incorporare Microsoft Intune App SDK. In alternativa, è possibile usare lo strumento di wrapping delle app.

In app come quelle di Microsoft Office, Intune App SDK è integrato. È possibile visualizzare l'elenco completo delle applicazioni supportate nella [raccolta di applicazioni per dispositivi mobili di Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) disponibile nella pagina dei partner di Microsoft Intune. Scegliere l'app per visualizzare le piattaforme e gli scenari supportati e per verificare se l'app supporta identità multiple.

È anche possibile [abilitare le app line-of-business personalizzate](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) da usare con i criteri MAM.

Oltre a limitare lo spostamento dei dati, se un dispositivo viene smarrito o rubato o se l'utente non lavora più nell'azienda, è possibile [cancellare selettivamente i dati aziendali](wipe-managed-company-app-data-with-microsoft-intune.md) lasciando solo quelli personali.

