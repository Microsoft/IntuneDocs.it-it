---
title: Proteggere app e dati | Microsoft Intune
description: 
keywords: "Questo argomento illustra le varie funzionalità e caratteristiche disponibili in Intune per proteggere le app e i dati aziendali."
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: be1ebcdf2514e45d383dd49890e0e21acf6ede44
ms.openlocfilehash: cf2ef1510aa9dafeddf54855123c826c9ccc2fd0


---

# Proteggere app e dati con Microsoft Intune


Intune protegge i dati aziendali tra più livelli di tecnologia.  A livello di identità, l'accesso condizionale protegge l'accesso ai servizi consentendo solo l'accesso da dispositivi conformi e gestiti.  A livello di applicazione client, la gestione di app per dispositivi mobili (MAM) consente di proteggere la perdita dei dati impedendo lo spostamento dei dati in app non protette o percorsi di archiviazione di dati e cancellando i dati quando un dispositivo viene smarrito o rubato.  Questi due livelli di protezione devono essere usati insieme in modo da proteggere i dati mantenendo i dipendenti mobili produttivi.

Un importante passaggio iniziale per la protezione dei dati aziendali consiste nell'implementazione dell'accesso condizionale, verificando che i dispositivi usati per accedere ai dati usino soluzioni di protezione della sicurezza come password complessa e crittografia e che non siano jailbroken. Microsoft Intune offre la possibilità di impostare le condizioni che i dispositivi devono rispettare prima di consentire l'accesso alla posta elettronica e ai dati aziendali.

L'[accesso condizionale](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) è determinato da due tipi di criteri che è possibile impostare in Intune:
- I [criteri di conformità](introduction-to-device-compliance-policies-in-microsoft-intune.md) stabiliscono la conformità di un dispositivo. Esaminano impostazioni e condizioni quali:
  - PIN e password: è possibile creare regole per richiedere le password prima di sbloccare un dispositivo, per i requisiti di complessità della password nonché per altre impostazioni relative alle password.
  - Crittografia: è possibile limitare l'accesso ai dispositivi che vengono crittografati.
  - Dispositivo non jailbroken o rooted: Intune può rilevare se un dispositivo registrato è jailbroken ed è quindi possibile impostare i criteri per bloccare l'accesso a tale dispositivo.
- I [criteri di accesso condizionale](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) sono configurati per un determinato servizio, ad esempio Exchange Online o SharePoint Online. Per ogni servizio, è possibile definire i gruppi di utenti a cui devono essere applicati questi criteri. È possibile ad esempio assicurarsi che tutti i dipendenti del reparto contabilità possano accedere alla posta elettronica aziendale solo da dispositivi registrati e conformi.

La protezione dell'accesso alle risorse aziendali è solo il primo passaggio per la protezione dei dati aziendali. È comunque necessario proteggere i dati dopo aver eseguito l'accesso al dispositivo. I dati possono ora essere copiati, spostati e salvati in un percorso diverso oppure condivisi. Intune risolve questo problema, offrendo la possibilità di limitare lo spostamento dei dati mediante la creazione di un set di regole, ad esempio:
- Bloccare le operazioni di copia e incolla o impedire il trasferimento dei dati all'esterno del contesto aziendale.
- Impedire il backup nello spazio di archiviazione cloud personale, impedire il salvataggio con nome.
- Proteggere l'accesso alle app richiedendo PIN/passcode o credenziali aziendali.
- Aprire tutti i collegamenti Web all'interno di Intune Managed Browser.

Questi set di regole sono denominati [criteri di gestione delle app per dispositivi mobili (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).  I criteri MAM possono essere adottati in app eseguite su dispositivi gestiti o non gestiti dall'utente.  

È possibile proteggere i dati aziendali tramite criteri MAM applicati a dispositivi **registrati in Intune**, dispositivi **registrati e gestiti da una soluzione MDM di terze parti** o dispositivi che **non sono registrati in alcuna soluzione MDM**, ad esempio i dispositivi di proprietà del dipendente.

Per associare un'app a un criterio MAM, l'app deve incorporare Microsoft Intune App SDK o usare lo strumento per la disposizione testo per app.

In app come quelle di Microsoft Office App SDK è integrato. Per l'elenco completo delle app supportate, consultare la [raccolta di applicazioni per dispositivi mobili di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) nella pagina dei partner dell'applicazione Microsoft Intune. Scegliere l'app per visualizzare gli scenari e le piattaforme supportate e per verificare se l'app supporta identità multiple.

È anche possibile [abilitare le app line-of-business personalizzate](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) da usare con i criteri MAM.

Oltre a limitare lo spostamento dei dati, se un dispositivo viene smarrito o rubato o se l'utente non lavora più nell'azienda, è possibile [cancellare selettivamente i dati aziendali](wipe-managed-company-app-data-with-microsoft-intune.md), lasciando solo quelli personali.



<!--HONumber=Jul16_HO5-->


