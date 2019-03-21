---
title: Gestione dei dispositivi in Microsoft 365
description: Microsoft 365 Enterprise include Microsoft Intune. Vedere come Intune gestisce la gestione dei dispositivi mobili e delle applicazioni mobili per l'organizzazione; conoscere gli scenari comuni e imparare a usare Intune per distribuire Microsoft 365 nell'ambiente in uso.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93e34c3de77dde59b87829617b8cbbd2614f7081
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57231248"
---
# <a name="what-is-device-management"></a>Che cos'è la gestione dei dispositivi? 

Un'attività chiave che spetta a qualsiasi amministratore è la protezione e messa in sicurezza delle risorse e dei dati di un'organizzazione. Questa attività è la gestione dei dispositivi. Spesso gli utenti dispongono di molti dispositivi che usano per aprire e condividere file personali, visitare siti Web e installare app e giochi. Questi utenti sono anche dipendenti e studenti pertanto desiderano poter usare i propri dispositivi per accedere alle risorse professionali o scolastiche, ad esempio la posta elettronica o OneNote. La *gestione dei dispositivi* consente alle organizzazioni di proteggere e mettere in sicurezza le risorse e i dati. 

Tramite un provider per la gestione dei dispositivi, le organizzazioni possono assicurarsi che solo gli utenti e i dispositivi autorizzati riescano ad accedere alle informazioni proprietarie. Analogamente, gli utenti dei dispositivi possono accedere ai dati di lavoro dal proprio telefono in tutta tranquillità, perché sanno che il dispositivo soddisfa i requisiti di sicurezza dell'organizzazione. Un'organizzazione potrebbe chiedersi **che strumenti usare per proteggere le proprie risorse**.

Ecco che entra in gioco [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune). Intune mette a disposizione servizi di gestione dei dispositivi mobili (MDM) e di gestione delle app mobili (MAM). Alcune attività chiave che deve poter svolgere qualsiasi soluzione MDM o MAM sono:

- Supportare un ambiente di dispositivi mobili eterogeneo&mdash;gestire i dispositivi iOS, Android, Windows e macOS in modo sicuro
- Assicurarsi che i dispositivi e le app siano conformi ai requisiti di sicurezza aziendali
- Creare criteri che consentano di proteggere i dati aziendali nei dispositivi personali e aziendali
- Usare una soluzione mobile singola e unificata per applicare questi criteri e facilitare la gestione di dispositivi, app, utenti e gruppi.

Intune è inclusa con Microsoft 365 e si integra con Azure Active Directory (Azure AD). Azure AD consente di controllare chi ha accesso e a cosa.

## <a name="hello-intune"></a>Panoramica di Intune
Molte organizzazioni, come Microsoft, usano Intune per proteggere i dati proprietari a cui gli utenti accedono dai dispositivi mobili personali e aziendali. Intune include funzionalità quali criteri di configurazione di dispositivi e app, criteri di aggiornamento software e stati dell'installazione, così come grafici, tabelle e report, che consentono di proteggere e monitorare l'accesso ai dati.

È consueto per le persone utilizzare più dispositivi che usano piattaforme diverse. Ad esempio, un dipendente potrebbe usare Surface Pro per il lavoro e un dispositivo mobile Android per la vita privata. Ed è consueto per una persona accedere alle risorse aziendali, ad esempio Microsoft Outlook e SharePoint, da questi vari dispositivi.

Intune consente di gestire più dispositivi per ogni persona e le piattaforme diverse in esecuzione su ogni dispositivo, tra cui iOS, macOS, Android e Windows. Intune separa i criteri e le impostazioni in funzione della piattaforma del dispositivo, pertanto risulta facile gestire e visualizzare i dispositivi di una piattaforma specifica.

**[Scenari comuni](https://docs.microsoft.com/intune/common-scenarios)** è un'ottima risorsa per capire come Intune gestisce situazioni comuni in cui sono coinvolti dispositivi mobili. Sono disponibili scenari su:  
- Protezione della posta elettronica con Exchange locale
- Accesso protetto e sicuro a Office 365
- Uso di dispositivi personali per accedere a risorse aziendali

## <a name="integration-with-secure-and-protect-services"></a>Integrazione con servizi di sicurezza e protezione
Fornire sicurezza e protezione è un compito fondamentale che deve svolgere qualsiasi soluzione di gestione dei dispositivi. Intune svolge questo compito in modo particolarmente efficace integrandosi con altri servizi. Ad esempio:

- **Microsoft 365** è un componente chiave per semplificare le attività IT più comuni. Usando l'interfaccia di amministrazione di Microsoft 365, è possibile creare utenti, gestire gruppi e ottenere accesso ad altri servizi, ad esempio Intune, Azure Active Directory e altro ancora. Ad esempio, è possibile creare un gruppo di dispositivi iOS in Microsoft 365. Quindi, con Intune si possono distribuire i criteri tramite push al gruppo di dispositivi iOS che usano le funzionalità iOS, ad esempio l'accesso all'app store, l'uso di AirDrop, l'esecuzione di backup in iCloud, l'uso del filtro Web di Apple e altro ancora.

- **Windows Defender** include molte funzionalità di sicurezza per proteggere i dispositivi Windows 10. Ad esempio, usando Intune e Windows Defender insieme, è possibile: 

    - Abilitare [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) per individuare attività sospette nei file e nelle app dei dispositivi mobili. 
    - Usare [Windows Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/intune/advanced-threat-protection) per prevenire le violazioni alla sicurezza nei dispositivi mobili e limitare l'impatto delle violazioni bloccando l'accesso di un utente alle risorse aziendali.

- **Accesso condizionale** è una funzionalità di Azure Active Directory che si integra perfettamente con Intune. Usando [accesso condizionale](https://docs.microsoft.com/intune/conditional-access) è possibile assicurarsi che accedano alla posta elettronica, a SharePoint e ad altre app solo i dispositivi conformi. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Scegliere la soluzione di gestione dei dispositivi adatta alle esigenze della propria azienda

Esistono un paio di metodi per affrontare la gestione dei dispositivi. In primo luogo, è possibile gestire tutti gli aspetti dei dispositivi facendo leva su tutte le funzionalità integrate in Intune. Questo metodo si chiama **Gestione di dispositivi mobili (MDM)**. In questo scenario gli utenti "registrano" i propri dispositivi e usano certificati per comunicare con Intune. Gli amministratori IT possono eseguire il push delle app nei dispositivi, limitare i dispositivi a un unico sistema operativo, bloccare i dispositivi personali e altro ancora. Se un dispositivo viene smarrito o rubato, sarà possibile anche rimuovere tutti i dati dal dispositivo. 

Il secondo metodo, invece, prevede la gestione delle app nei dispositivi. Questo metodo si chiama **Gestione di applicazioni mobili (MAM)**. In questo scenario gli utenti possono usare i propri dispositivi personali per accedere alle risorse aziendali. Quando gli utenti aprono un'app, ad esempio la posta elettronica o SharePoint, viene richiesta un'autenticazione aggiuntiva. Se un dispositivo viene smarrito o rubato, sarà possibile anche rimuovere tutti i dati dell'organizzazione dal dispositivo. 

È anche possibile combinare tra loro [MDM e MAM](https://docs.microsoft.com/intune/byod-technology-decisions).

Quando si configura Intune, è possibile scegliere di gestire i dispositivi esclusivamente nel portale di Azure oppure usando Intune e Microsoft 365 insieme. Per scoprire l'approccio moderno che Microsoft IT ha scelto per la gestione dei dispositivi e per vedere l'analisi di fine progetto, consultare il case study di Microsoft IT [Migrating mobile device management to Intune in the Azure portal](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal) (Migrazione della gestione dei dispositivi mobili su Intune nel portale di Azure). 

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>Semplificare le attività IT usando il dashboard Gestione dei dispositivi

Il [dashboard Gestione dei dispositivi](https://devicemanagement.portal.azure.com/) è una risorsa centralizzata per gestire e completare le attività relative ai dispositivi mobili. Questo dashboard include i servizi usati per la gestione dei dispositivi, tra cui Intune e Azure Active Directory, e per la gestione delle app client. 

Nel dashboard Gestione dei dispositivi è possibile:

- [Registrare i dispositivi](https://docs.microsoft.com/intune/device-enrollment)
- [Impostare la conformità dei dispositivi](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Gestire i dispositivi](https://docs.microsoft.com/intune/device-management)
- [Gestire le app](https://docs.microsoft.com/intune/app-management)  
- [eBook iOS](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Installare On-premises Exchange Connector](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Gestire i ruoli](https://docs.microsoft.com/intune/role-based-access-control)  
- Gestire gli aggiornamenti software
  - [Gestire gli aggiornamenti di Windows 10](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Gestire gli aggiornamenti di iOS](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Gestire gli utenti](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Gestire gruppi e membri](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Risolvere i problemi](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>Passaggio successivo
Quando si è pronti per iniziare a usare una soluzione MDM o MAM, eseguire i diversi passaggi per configurare Intune, registrare i dispositivi e iniziare a creare i criteri, vedere [Gestione dei dispositivi mobili per Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure). 
