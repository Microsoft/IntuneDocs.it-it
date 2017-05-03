---
title: Configurare l&quot;accesso alle app per SharePoint Online
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 992273f88e4bbe234f11f936d6416dbaf0d394e9
ms.lasthandoff: 04/19/2017


---

# <a name="create-a-sharepoint-online-conditional-access-policy-to-only-allow-apps-supported-by-mam"></a>Creare criteri di accesso condizionale a SharePoint Online per consentire solo le app supportate dal software MAM
Questo argomento contiene istruzioni dettagliate su come configurare un accesso condizionale a Exchange Online in modo da consentire solo le app mobili che sopportano i criteri di gestione delle app mobili Intune.

## <a name="configure-a-sharepoint-online-policy"></a>Configurare criteri di SharePoint Online
**Passaggio 1:** accedere al [portale di Azure](https://portal.azure.com) in cui è disponibile la funzionalità di accesso delle app. Se non si ha familiarità con il Portale di Azure, leggere l'argomento [Portale di Azure per i criteri MAM](azure-portal-for-microsoft-intune-mam-policies.md).

**Passaggio 2:** scegliere **Sfoglia > Intune > Gestione di applicazioni mobili di Intune > Impostazioni** e nella sezione **Accesso condizionale** scegliere **SharePoint Online**.

![Schermata del pannello delle impostazioni con la sezione Accesso condizionale e il pannello SharePoint Online aperto](../media/mam-ca-settings-spo.png)

**Passaggio 3:** nel pannello **App consentite** scegliere **Consenti app che supportano i criteri di Intune** per consentire l'accesso a SharePoint Online solo alle app supportate dai criteri MAM di Intune. Quando si seleziona l'opzione che consente solo le app supportate dai criteri MAM di Intune, viene visualizzato l'elenco delle app supportate.

![Schermata del pannello delle app consentite con l'elenco delle app](../media/mam-ca-spo-allowed-apps.png)

**Passaggio 4:** per applicare questi criteri agli utenti, aprire il pannello **Gruppi di utenti limitati** e scegliere **Aggiungi un gruppo di utenti**. Selezionare uno o più gruppi di utenti a cui applicare questi criteri.

![Screenshot del pannello Gruppi di utenti limitati e opzione Aggiungi un gruppo di utenti selezionata](../media/mam-ca-spo-restricted-groups.png)


**Passaggio 5:** è possibile che si decida di non applicare questi criteri ad alcuni utenti del gruppo selezionato nel passaggio precedente. In questi casi aggiungere il gruppo di utenti all'elenco dei gruppi esentati. Nel pannello **SharePoint Online** scegliere **Gruppi di utenti esentati**. Scegliere **Aggiungi un gruppo di utenti** per aprire l'elenco dei gruppi di utenti. Selezionare i gruppi che si vuole esentare da questi criteri.  

## <a name="modifying-an-existing-policy"></a>Modificare criteri esistenti
### <a name="adding-or-deleting-user-groups"></a>Aggiungere o eliminare gruppi di utenti
Per **eliminare un gruppo di utenti** dall'elenco dei **gruppi di utenti con restrizioni**, aprire il pannello Gruppi di utenti limitati, evidenziare il gruppo da eliminare e fare clic sui puntini di sospensione (...) per visualizzare l'opzione di eliminazione. Scegliere **Elimina** per rimuovere il gruppo di utenti dall'elenco. È possibile seguire la stessa procedura per rimuovere un gruppo di utenti dall'elenco dei **gruppi di utenti esentati**.


## <a name="next-steps"></a>Passaggi successivi
[Configurare l'accesso delle app a Exchange Online](mam-ca-for-exchange-online.md)

[Bloccare le app che non usano l'autenticazione moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Vedere anche

[Proteggere i dati delle app usando i criteri di gestione delle app mobili con Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

