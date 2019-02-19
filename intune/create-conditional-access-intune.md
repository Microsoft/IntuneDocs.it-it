---
title: Configurare l'accesso condizionale basato su dispositivo con Intune
titlesuffix: Microsoft Intune
description: Informazioni su come creare criteri di accesso condizionale basato su dispositivo usando i criteri di gestione delle app mobili e di conformità dei dispositivi di Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 03ca9a65d5a62c75c45541b42c9b2aa5c4871a18
ms.sourcegitcommit: e0374b3ced83c8876a4f78b326869c10588a55e5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56307788"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Creare criteri di accesso condizionale basato su dispositivo

Con Intune, è possibile migliorare l'accesso condizionale in Azure Active Directory aggiungendo i criteri di conformità dei dispositivi mobili ai controlli di accesso. Dopo aver creato in Intune i criteri che definiscono i requisiti di conformità dei dispositivi, è possibile usare lo stato di conformità di un dispositivo per consentire o bloccare l'accesso ad app e servizi. A tale scopo è possibile creare criteri di accesso condizionale con l'impostazione **Richiedi che i dispositivi siano contrassegnati come conformi**. 

I criteri di accesso condizionale specificano le app o i servizi da proteggere, le condizioni di accessibilità alle app o ai servizi e gli utenti a cui si applicano i criteri. L'accesso condizionale è una funzionalità di Azure AD Premium che è possibile configurare in Azure Active Directory, ma questi stessi criteri possono essere configurati dal portale di Intune. 

> [!IMPORTANT]
> Prima dell'accesso condizionale, è necessario configurare i criteri di conformità dei dispositivi di Intune per valutare i dispositivi in base alla capacità di soddisfare requisiti specifici. Vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Creare criteri di accesso condizionale

1.  Nel portale di Intune selezionare **Accesso condizionale** > **Criteri** > **Nuovi criteri**.
   
    ![Creare nuovi criteri di accesso condizionale](media/create-conditional-access-intune/create-ca.png)
 
2.  In **Assegnazioni** selezionare **Utenti e gruppi**. 
3.  Nella scheda **Includi** identificare gli utenti o i gruppi a cui dovranno essere applicati i criteri di accesso condizionale. Dopo aver scelto chi si vuole includere, è possibile usare la scheda **Escludi** per specificare eventuali utenti, ruoli o gruppi da escludere da questi criteri.  
    - **Tutti gli utenti**: selezionare questa opzione per applicare i criteri a tutti gli utenti e gruppi, inclusi gli utenti interni e guest.
  
    - **Seleziona utenti e gruppi**: selezionare questa opzione e specificare una o più delle opzioni seguenti:
  
      a. **Tutti gli utenti guest**: selezionare questa opzione per includere o escludere gli utenti guest esterni (ad esempio, i partner o i collaboratori esterni).
       
      b. **Ruoli della directory**: selezionare uno o più ruoli di Azure AD per includere o escludere gli utenti cui sono assegnati questi ruoli.
      
      c. **Utenti e gruppi**: selezionare questa opzione per cercare e selezionare singoli utenti o gruppi da includere o escludere.
     
       > [!TIP]  
       > Testare i criteri su un gruppo di utenti più limitato per assicurarsi che funzionino come previsto.
4.  Seleziona **Chiudi**.
5.  In **Assegnazioni** selezionare **App cloud**. 
6.  Nella scheda **Includi** identificare le app e i servizi da proteggere con questi criteri di accesso condizionale. È quindi possibile usare la scheda **Escludi** per escludere eventuali app o servizi da questi criteri.
    - **Tutte le app cloud**: selezionare questa opzione per applicare i criteri a tutte le app.
      > [!IMPORTANT]  
      > In questo elenco è inclusa l'app di gestione di Microsoft Azure per l'accesso al portale di Azure. Usare la scheda **Escludi** in questo riquadro o nelle opzioni del riquadro **Utenti e gruppi** per assicurarsi di poter accedere al portale di Azure (o consentire agli utenti o gruppi designati di accedervi). 

    - **Selezionare le app**: selezionare questa opzione, scegliere **Seleziona** e quindi usare l'elenco di applicazioni per cercare e selezionare le app o i servizi da proteggere.
    
      ![Creare nuovi criteri di accesso condizionale](media/create-conditional-access-intune/create-ca-select-apps.png)

7.  Seleziona **Chiudi**.
8.  In **Assegnazioni** selezionare **Condizioni**.
    - **Rischio di accesso**: scegliere Sì per usare il rilevamento del rischio di accesso di Azure AD Identity Protection con questi criteri e quindi scegliere i livelli di rischio di accesso a cui devono essere applicati i criteri.
    - **Piattaforme del dispositivo**: nella scheda **Includi** identificare le piattaforme per dispositivi a cui devono essere applicati i criteri di accesso condizionale. Usare la scheda **Escludi** per escludere eventuali piattaforme da questi criteri.
    - **Percorsi**: nella scheda **Includi** specificare se i criteri si applicano a qualsiasi percorso, a percorsi di rete attendibili che sono sotto il controllo del reparto IT o a percorsi di rete specifici. Usare la scheda **Escludi** per escludere percorsi di rete da questi criteri. 
    - **App client**: scegliere **Sì** per specificare se i criteri devono essere applicati ad app basate su browser, app per dispositivi mobili e client desktop. È anche possibile selezionare **Client con autenticazione moderna** (ad esempio, Outlook per iOS o Outlook per Android) e **Client Exchange ActiveSync**.
    - **Stato dispositivo**: i criteri di accesso condizionale verranno applicati a tutti gli stati dei dispositivi, a meno che non si scelga Sì specificando di escludere lo stato Dispositivo aggiunto ad Azure AD ibrido o Dispositivo contrassegnato come conforme (oppure entrambi).
    
      ![Creare nuovi criteri di accesso condizionale](media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Se si vogliono proteggere sia i **client con autenticazione moderna** sia i **client Exchange ActiveSync**, creare due criteri di accesso condizionale separati, uno per ogni tipo di client. Anche se Exchange ActiveSync supporta l'autenticazione moderna, l'unica condizione supportata da Exchange ActiveSync è quella relativa alla piattaforma. Non sono supportate altre condizioni, inclusa l'autenticazione a più fattori. Per proteggere in modo efficace l'accesso a Exchange Online da Exchange ActiveSync, creare criteri di accesso condizionale che specificano l'app cloud Office 365 Exchange Online e l'app client Exchange ActiveSync con l'opzione Applica i criteri solo alle piattaforme supportate selezionata.

9.  Seleziona **Chiudi**.
10. In **Controlli di accesso** selezionare **Concedi**. Specificare cosa accade in base alle condizioni configurate.  È possibile selezionare una delle opzioni seguenti:
    - **Blocca accesso**: agli utenti specificati in questi criteri verrà negato l'accesso alle app in base alle condizioni specificate.
    - **Concedi accesso**: agli utenti specificati in questi criteri verrà concesso l'accesso, ma è possibile richiedere una delle azioni seguenti:
      - **Richiedi autenticazione a più fattori** : l'utente dovrà soddisfare requisiti di sicurezza aggiuntivi, ad esempio una telefonata o un SMS.
      - **Richiedi che i dispositivi siano contrassegnati come conformi**: il dispositivo deve essere conforme a Intune. Se il dispositivo non è conforme, l'utente avrà la possibilità di registrare il dispositivo in Intune. 
      - **Richiedi dispositivo aggiunto ad Azure AD ibrido**: i dispositivi devono essere aggiunti ad Azure AD ibrido.
      - **Richiedi app client approvata**: il dispositivo deve usare app client approvate. 
      - **Per più controlli**: selezionare **Richiedi tutti i controlli selezionati** in modo che vengano applicati tutti i requisiti sopra elencati quando un dispositivo prova ad accedere all'app.
    
      ![Impostazioni dei controlli per concedere l'accesso](media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. In **Abilita criterio** selezionare **Sì**.
     
     ![Abilitare i criteri](media/create-conditional-access-intune/enable-policy.png)

12. Selezionare **Crea**.

## <a name="see-also"></a>Vedere anche
[Accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md)
