---
title: Scenari di accesso condizionale | Microsoft Intune
description: Informazioni su come l'accesso condizionale di Intune viene usato comunemente per l'accesso condizionale basato su dispositivo e basato su app.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.openlocfilehash: 753ad125e541936586f2939985a23ed3b06ea7ea
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817161"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Quali sono i modi comuni per usare l'accesso condizionale con Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Esistono due tipi di accesso condizionale con Intune: l'accesso condizionale basato su dispositivo e l'accesso condizionale basato su app. È necessario configurare i criteri di conformità correlati per promuovere la conformità dell'accesso condizionale nell'organizzazione. L'accesso condizionale viene in genere usato per operazioni come consentire o bloccare l'accesso a Exchange in locale e controllare l'accesso alla rete o come integrazione per una soluzione Mobile Threat Defense.

Le informazioni seguenti consentono di comprendere come usare le funzionalità per la conformità dei *dispositivi* mobili di Intune e le funzionalità di gestione delle *applicazioni* per dispositivi mobili (MAM) di Intune. 

> [!NOTE]
> L'accesso condizionale è una funzionalità di Azure Active Directory inclusa con una licenza di Azure Active Directory Premium. Intune contribuisce a migliorare questa funzionalità aggiungendo la conformità dei dispositivi mobili e la gestione delle app per dispositivi mobili alla soluzione.

## <a name="device-based-conditional-access"></a>Accesso condizionale basato su dispositivo

Intune e Azure Active Directory collaborano per assicurarsi che solo i dispositivi gestiti e conformi abbiano accesso alla posta elettronica, ai servizi di Office 365, alle app SaaS (Software as a Service) e alle [app locali](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). È inoltre possibile impostare un criterio in Azure Active Directory per consentire l'accesso ai servizi di Office 365 solo ai computer che appartengono a un dominio o ai dispositivi mobili registrati in Intune.

Intune offre funzionalità per i criteri di conformità dei dispositivi che consentono di valutare lo stato di conformità dei dispositivi. Lo stato di conformità viene segnalato ad Azure Active Directory, che lo usa per l'applicazione dei criteri di accesso condizionale creati in Azure Active Directory quando l'utente tenta di accedere alle risorse aziendali.

I criteri di accesso condizionale basato su dispositivo per Exchange Online e gli altri prodotti di Office 365 sono configurati nel [portale di Azure](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

-   Altre informazioni sull'[accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Altre informazioni sulla [conformità dei dispositivi di Intune](device-compliance.md).

-   Altre informazioni sulla [protezione di posta elettronica, Office 365 e altri servizi che usano l'accesso condizionale con Intune](app-based-conditional-access-intune.md).

> [!NOTE]
> Quando si abilita l'accesso in base al dispositivo per Sharepoint Online sui dispositivi Android, gli utenti devono abilitare l'opzione **Abilita l'accesso al browser nel dispositivo registrato** seguendo questa procedura:
> 1. Avviare **l'app Portale aziendale**.
> 2. Passare alla pagina **Impostazioni** facendo clic sui punti di sospensione (...) o sul tasto di menu.
> 3. Scegliere il pulsante **Abilita l'accesso al browser** . 
> 4. Nel browser Chrome disconnettersi da Office 365 e riavviare Chrome.

### <a name="conditional-access-for-exchange-on-premises"></a>Accesso condizionale per Exchange locale

L'accesso condizionale può essere usato per consentire o bloccare l'accesso a **Exchange locale** in base ai criteri di conformità e allo stato di registrazione dei dispositivi. Quando l'accesso condizionale viene usato in combinazione con i criteri di conformità dei dispositivi, possono accedere a Exchange locale solo i dispositivi conformi.

È possibile configurare le impostazioni avanzate dell'accesso condizionale per un controllo più granulare, ad esempio:

-   Consentire o bloccare determinate piattaforme.

-   Bloccare immediatamente i dispositivi non gestiti da Intune.

Quando si applicano i criteri di accesso condizionale e di conformità dei dispositivi, viene verificata la conformità di qualsiasi dispositivo usato per accedere a Exchange locale.

Se i dispositivi non soddisfano le condizioni previste, l'utente viene guidato nel processo di registrazione del dispositivo per la risoluzione del problema che rende il dispositivo non conforme.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Funzionamento dell'accesso condizionale per Exchange locale

Intune Exchange Connector effettua il pull di tutti i record di Exchange Active Sync (EAS) presenti nel server Exchange, per consentire a Intune di acquisire questi record EAS e associarli ai record dei dispositivi di Intune. Tali record sono i dispositivi registrati e riconosciuti da Intune. Questo processo consente o blocca l'accesso alla posta elettronica.

Se il record EAS è nuovo e Intune non lo riconosce, Intune invia un cmdlet che blocca l'accesso alla posta elettronica. Ecco altri dettagli sul funzionamento di questo processo:

![Diagramma di flusso di Exchange locale con autorità di certificazione](./media/ca-intune-common-ways-1.png)

1.  L'utente tenta di accedere alla posta elettronica aziendale, ospitata in Exchange locale 2010 SP1 o versione successiva.

2.  Se il dispositivo non è gestito da Intune, l'accesso alla posta elettronica sarà bloccato. Intune invia una notifica di blocco al client EAS.

3.  EAS riceve la notifica di blocco, mette il dispositivo in quarantena e invia il messaggio di posta elettronica di quarantena con i passaggi correttivi che contengono collegamenti per consentire agli utenti di registrare i dispositivi.

4.  Viene eseguito il processo di aggiunta alla rete aziendale, ovvero il primo passaggio per la gestione del dispositivo tramite Intune.

5.  Il dispositivo viene registrato in Intune.

6.  Intune associa il record EAS a un record di dispositivo e salva lo stato di conformità del dispositivo.

7.  L'ID del client EAS viene registrato tramite il processo di registrazione del dispositivo di Azure AD, che crea una relazione tra il record del dispositivo di Intune e l'ID del client EAS.

8.  La registrazione del dispositivo di Azure AD consente di salvare le informazioni sullo stato del dispositivo.

9.  Se l'utente soddisfa i criteri di accesso condizionale, Intune invia un cmdlet tramite Intune Exchange Connector che consente la sincronizzazione della cassetta postale.

10. Il server Exchange invia la notifica al client EAS, in modo che l'utente possa accedere alla posta elettronica.

#### <a name="whats-the-intune-role"></a>Qual è il ruolo di Intune?

Intune valuta e gestisce lo stato del dispositivo.

#### <a name="whats-the-exchange-server-role"></a>Qual è il ruolo del server Exchange?

Il server Exchange fornisce l'API e l'infrastruttura per mettere i dispositivi in quarantena.

> [!IMPORTANT]
> Tenere presente che l'utente che usa il dispositivo deve disporre di un profilo di conformità assegnato, in modo che venga valutata la conformità del dispositivo. Se all'utente non viene distribuito alcun criterio di conformità, il dispositivo viene considerato conforme e non vengono applicate restrizioni di accesso.

### <a name="conditional-access-based-on-network-access-control"></a>Accesso condizionale basato sul controllo di accesso alla rete

Intune è integrato con partner come Cisco ISE, Aruba Clear Pass e Citrix NetScaler per fornire controlli di accesso basati sulla registrazione di Intune e sullo stato di conformità del dispositivo.

Quando gli utenti tentano di accedere alle risorse Wi-Fi o VPN aziendali, l'accesso può essere consentito o negato a seconda del fatto che il dispositivo sia gestito e conforme ai criteri di conformità dei dispositivi di Intune.

-   Altre informazioni sull'[integrazione del controllo di accesso alla rete con Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Accesso condizionale basato sul rischio di dispositivo

Intune collabora con i fornitori di Mobile Threat Defense, che forniscono una soluzione di sicurezza per il rilevamento di malware, trojan horse e altre minacce nei dispositivi mobili.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Funzionamento dell'integrazione tra Intune e Mobile Threat Defense

Quando nei dispositivi mobili è installato l'agente di Mobile Threat Defense, questo può inviare messaggi sullo stato di conformità al reporting di Intune se viene rilevata una minaccia nel dispositivo mobile.

L'integrazione tra Intune e Mobile Threat Defense rappresenta un fattore per le decisioni di accesso condizionale in base al rischio del dispositivo.

-   Altre informazioni su [Mobile Threat Defense di Intune](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Accesso condizionale per i PC Windows

L'accesso condizionale per i PC offre funzionalità simili a quelle disponibili per i dispositivi mobili. Di seguito sono descritti i modi in cui è possibile usare l'accesso condizionale durante la gestione dei PC con Intune.

#### <a name="corporate-owned"></a>Dispositivi di proprietà dell'azienda

-   **Aggiunta a un dominio AD locale:** questa opzione viene usata generalmente dalle organizzazioni che hanno già familiarità con la gestione dei PC tramite i criteri di gruppo di Active Directory e/o con System Center Configuration Manager.

-   **Aggiunta a un dominio AD e gestione tramite Intune:** questo scenario è generalmente associato agli scenari CYOD (Choose Your Own Device) e con portatili roaming in cui i dispositivi si connettono raramente alla rete aziendale. Il dispositivo viene aggiunto ad Azure AD ed è registrato in Intune, che rimuove qualsiasi dipendenza da Active Directory locale e controller di dominio. Può essere usato come criterio di accesso condizionale durante l'accesso alle risorse aziendali.

-   **Aggiunta a un dominio AD e System Center Configuration Manager:** a partire dalla versione Current Branch, System Center Configuration Manager fornisce funzionalità di accesso condizionale che consentono di valutare specifici criteri di conformità, oltre all'aggiunta di un PC a un dominio:

    -   Il PC è crittografato?

    -   È installato malware? È aggiornato?

    -   Il dispositivo è jailbroken o rooted?

#### <a name="bring-your-own-device-byod"></a>Bring Your Own Device (BYOD)

-   **Aggiunta alla rete aziendale e gestione di Intune:** qui l'utente può aggiungere i propri dispositivi personali per accedere ai servizi e alle risorse aziendali. È possibile usare l'aggiunta alla rete aziendale e registrare i dispositivi in Intune per ricevere criteri a livello di dispositivo. Questa rappresenta un'altra opzione per la valutazione dei criteri di accesso condizionale.

## <a name="app-based-conditional-access"></a>Accesso condizionale basato su app

Intune e Azure Active Directory interagiscono per verificare che solo le app gestite possano accedere alla posta elettronica aziendale o ad altri servizi di Office 365.

-   Altre informazioni sull'[accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Passaggi successivi

[How to configure conditional access in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) (Come configurare l'accesso condizionale in Azure Active Directory)

[How to install on-premises Exchange connector with Intune](https://docs.microsoft.com/intune/exchange-connector-install) (Come installare On-premises Exchange Connector con Intune).

[How to create a conditional access policy for Exchange on-premises](conditional-access-exchange-create.md) (Come creare criteri di accesso condizionale per Exchange locale)
