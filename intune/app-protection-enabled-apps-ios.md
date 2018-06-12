---
title: App iOS con criteri di protezione delle app
titlesuffix: Microsoft Intune
description: Informazioni su cosa accade quando viene usata un'app iOS con criteri di protezione.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1b2789c8f3b57bbc97e06e8793a96656f74a54d
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703282"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo descrive l'esperienza utente relativa alle app iOS con criteri di protezione. I criteri di protezione delle app si applicano solo quando le app vengono usate in un contesto professionale, ad esempio quando si accede a un'app con un account aziendale o quando si accede a file archiviati nel percorso OneDrive dell'azienda.
##  <a name="accessing-apps"></a>Accesso alle app

Se il dispositivo **non è registrato in Intune**, all'utente verrà chiesto di riavviare l'app la prima volta che la usa.  Il riavvio è necessario per consentire l'applicazione dei criteri di protezione delle app all'app. Lo screenshot seguente illustra questo aspetto tramite l'app Skype:


![screenshot di un dispositivo iOS con la richiesta del PIN](./media/ios-pin-prompt.png)

Per i dispositivi **registrati per la gestione in Intune**, l'utente riceverà il messaggio che l'app è ora gestita dalla società:

![schermata del dispositivo iOS con il messaggio relativo alla gestione da parte della società e la richiesta del PIN](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Uso di app con supporto di più identità

I criteri di protezione delle app hanno effetto solo quando un utente tenta di accedere a dati relativi al lavoro. Se l'utente tenta di accedere all'app per uso personale, i comportamenti possono essere diversi. I criteri non si applicano anche al nuovo contenuto non ancora salvato. Il nuovo contenuto viene considerato informazioni aziendali solo dopo essere stato salvato in un percorso aziendale, ad esempio SharePoint o OneDrive for Business.

Per le app che supportano più identità, Intune applica criteri di protezione delle app solo se un utente accede ai dati di lavoro.  Un utente potrebbe, ad esempio, ricevere una richiesta del PIN.  Nell'**app Outlook** il messaggio di richiesta viene visualizzato quando un utente avvia l'app. Nell'**app OneDrive** il messaggio di richiesta viene visualizzato quando un utente digita l'account aziendale.  In Microsoft **Word**, **PowerPoint** ed **Excel** il messaggio di richiesta viene visualizzato quando un utente accede a documenti di OneDrive aziendale.
##  <a name="managing-user-accounts-on-the-device"></a>Gestione degli account utente nel dispositivo

Intune supporta solo la distribuzione di criteri di protezione delle app a un unico account utente per dispositivo.

* A seconda dell'applicazione che si usa, è possibile scegliere di bloccare o meno il secondo utente del dispositivo. In ogni caso, sarà tuttavia interessato dai criteri di protezione delle app solo il primo utente che ottiene i criteri.
  * **Microsoft Word**, **Excel** e **PowerPoint** non bloccheranno l'accesso a un account utente aggiuntivo. L'account utente non sarà tuttavia interessato dai criteri di protezione delle app.

  * Per le app **OneDrive e Outlook**, è possibile usare un solo account aziendale.  L'aggiunta di più account aziendali è bloccata in queste app.  È comunque possibile rimuovere un utente da un dispositivo e quindi aggiungere un altro utente al dispositivo.

* In un dispositivo potrebbero essere presenti più account utente esistenti prima della distribuzione dei criteri di protezione delle app. In questo caso, il primo account al quale vengono distribuiti i criteri di protezione delle app è gestito dai criteri di protezione delle app di Intune.


Per informazioni su come Intune gestisce più account utente, vedere l'esempio seguente.

L'utente A lavora per due aziende, l'**Azienda X** e l'**Azienda Y**. L'utente A ha un account aziendale per ognuna delle aziende per cui lavora e, in entrambi i casi, viene usato Intune per la distribuzione dei criteri di protezione delle app. L'**Azienda X** distribuisce i criteri di protezione delle app **prima dell'** **Azienda Y**. L'account associato all'**Azienda X** otterrà i criteri di protezione delle app, a differenza dell'account associato all'Azienda Y. Per fare in modo che l'account utente associato all'Azienda Y sia gestito con i criteri di protezione delle app, l'utente A deve rimuovere l'account associato all'Azienda X.
### <a name="adding-a-second-account"></a>Aggiunta di un secondo account

Se si usa un dispositivo iOS, quando si prova ad aggiungere un secondo account aziendale nello stesso dispositivo potrebbe essere visualizzato un messaggio di blocco.  Verranno visualizzati gli account e sarà possibile scegliere l'account da rimuovere.

![Schermata della finestra di dialogo con il messaggio di blocco e le opzioni Sì e No](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Passaggi successivi
[Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Vedere anche
[Creare e distribuire i criteri di protezione delle app con Microsoft Intune](app-protection-policies.md)
