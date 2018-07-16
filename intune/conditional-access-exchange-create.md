---
title: Creare criteri di accesso condizionale per Exchange
titlesuffix: Microsoft Intune
description: Configurare l'accesso condizionale per Exchange locale ed Exchange Online dedicato legacy in Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fbe55be15df9755c109ec7e8e8e23db3c27931b0
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905530"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Creare criteri di accesso condizionale per Exchange locale ed Exchange Online dedicato legacy

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In questo articolo viene illustrato come configurare l'accesso condizionale per Exchange locale in base alla conformità del dispositivo.

Se si dispone di un ambiente Exchange Online dedicato ed è necessario definire se si trova nell'ambiente di configurazione nuovo o legacy, contattare l'account manager. Per controllare l'accesso alla posta elettronica per Exchange locale o per l'ambiente legacy Exchange Online dedicato, configurare l'accesso condizionale per Exchange locale in Intune.

## <a name="before-you-begin"></a>Prima di iniziare

Prima di configurare l'accesso condizionale, verificare quanto segue:

- La versione di Exchange deve essere **Exchange 2010 SP1 o successiva**. È supportato un array del server Accesso client di Exchange Server.

- È necessario usare [On-Premises Exchange Connector di Exchange Active](exchange-connector-install.md) che connette Intune a Exchange locale.

    >[!IMPORTANT]
    >On-premises Exchange Connector è specifico del tenant di Intune e non può essere usato con un altro tenant. Intune ora supporta più Exchange Connector locali per ogni sottoscrizione. Se sono presenti più organizzazioni di Exchange locali, è possibile configurare un connettore separato per ogni organizzazione di Exchange.

- Il connettore per un'organizzazione di Exchange locale può essere installato in qualsiasi computer, purché possa comunicare con il server di Exchange.

- Questo connettore supporta l'**ambiente CAS di Exchange**. Anche se è tecnicamente possibile, non è consigliabile installare il connettore direttamente nel server CAS di Exchange perché aumenta il carico sul server. Quando si configura il connettore, è necessario configurarlo in modo che comunichi con uno dei server CAS di Exchange.

- È necessario configurare **Exchange ActiveSync** per l'autenticazione basata su certificati o l'immissione di credenziali utente.

- Quando i criteri per l'accesso condizionale sono stati configurati e indirizzati a un utente, prima che un utente possa connettersi alla posta elettronica, il **dispositivo** in uso deve:
    - Essere **registrato** con Intune o essere un PC aggiunto a un dominio.
    - Essere **registrato in Azure Active Directory**. Inoltre, l'ID client Exchange ActiveSync deve essere registrato con Azure Active Directory.
<br></br>
- Il servizio Registrazione dispositivo Azure AD (DRS) viene attivato automaticamente per i clienti di Intune e Office 365. I clienti che hanno già distribuito il servizio Device Registration Service di AD FS non visualizzano i dispositivi registrati in Active Directory locale. **Ciò non si applica ai PC Windows e ai dispositivi Windows Phone**.

- Essere **conforme** ai criteri di conformità dei dispositivi distribuiti a quel dispositivo.

- Se il dispositivo non soddisfa le impostazioni dei criteri di accesso condizionale, all'accesso verrà visualizzato uno dei messaggi seguenti:
    - Se il dispositivo non è registrato con Intune oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente istruzioni su come installare l'app Portale aziendale, eseguire la registrazione e attivare la posta elettronica. Questo processo associa anche l'ID Exchange ActiveSync del dispositivo con il record del dispositivo in Azure Active Directory.
    - Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale di Intune o all'app Portale aziendale dove sono disponibili informazioni sul problema e su come risolverlo.

### <a name="support-for-mobile-devices"></a>Supporto per dispositivi mobili

- Windows Phone 8.1 e versioni successive
- App di posta elettronica nativa in iOS
- Client di posta EAS, ad esempio Gmail in Android 4 o versione successiva.
- Client di posta EAS - **Dispositivi del profilo di lavoro Android:** nei dispositivi del profilo di lavoro Android sono supportate solo le app **Gmail** e **Nine Work** nel **profilo di lavoro**. Perché l'accesso condizionale funzioni nei profili di lavoro Android, è necessario distribuire un profilo di posta elettronica per l'app Gmail o Nine Work. È anche necessario distribuire tali applicazioni come installazioni obbligatorie.

> [!NOTE]
> L'app Microsoft Outlook per Android e iOS non è supportata. 

### <a name="support-for-pcs"></a>Supporto per PC

L'applicazione **Mail** nativa in Windows 8.1 e versioni successive (se registrata con Intune)


## <a name="configure-exchange-on-premises-access"></a>Configurare l'accesso locale a Exchange

1. Passare al [portale di Azure](https://portal.azure.com/) e accedere con le credenziali di Intune.

1. Dopo aver completato l'accesso, viene visualizzato il **dashboard di Azure**.

1. Scegliere **Tutti i servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

1. Scegliere **Intune**. Verrà visualizzato il **dashboard di Intune**.

1. Scegliere **Accesso locale**. Il riquadro **Accesso locale** visualizza lo stato dei criteri di accesso condizionale e i dispositivi da esso interessati.

1. In **Gestisci** scegliere **Accesso locale a Exchange**.

1. Nel riquadro **Accesso locale a Exchange** scegliere **Sì** per consentire il controllo dell'accesso locale a Exchange.

    > [!NOTE]
    > Se Exchange Active Sync On-Premises Connector non è stato configurato, questa opzione è disabilitata.  Prima installare e configurare almeno un connettore, quindi abilitare l'accesso condizionale a Exchange locale. Per altri dettagli, vedere [Installare Intune On-premises Exchange Connector](exchange-connector-install.md)

1. In **Assegnazione** scegliere **Gruppi inclusi**.  Usare il gruppo di utenti di sicurezza a cui applicare l'accesso condizionale. Questa azione richiede agli utenti di registrare i propri dispositivi in Intune e renderli conformi ai profili di conformità.

1. Se si vogliono escludere determinati gruppi di utenti, è possibile farlo scegliendo **Gruppi esclusi** e selezionando un gruppo di utenti da escludere dalla richiesta di registrazione del dispositivo e di conformità.

1. In **impostazioni** scegliere **Notifiche utente** per modificare il messaggio di posta elettronica predefinito. Questo messaggio viene inviato agli utenti se il dispositivo non è conforme e desiderano accedere a Exchange locale. Il modello di messaggio usa il linguaggio di markup.  Mentre si digita è anche possibile visualizzare l'anteprima dell'aspetto del messaggio.
    > [!TIP]
    > Per altre informazioni sul linguaggio di markup, vedere questo [articolo](https://en.wikipedia.org/wiki/Markup_language) di Wikipedia.

1. Nel riquadro **Advanced Exchange Active Sync access settings** (Impostazioni di accesso a Exchange Active Sync avanzate) impostare la regola predefinita globale per l'accesso da dispositivi non gestiti da Intune e per le regole a livello di piattaforma come descritto nei prossimi due passaggi.

1. Per un dispositivo non soggetto ad accesso condizionale e a nessun'altra regola, è possibile scegliere di consentire l'accesso a Exchange o bloccarlo.

   - Quando si imposta questa opzione per consentire l'accesso, tutti i dispositivi sono in grado di accedere immediatamente a Exchange locale.  I dispositivi che appartengono agli utenti nei **Gruppi inclusi** vengono bloccati se in un secondo momento sono ritenuti non conformi ai criteri di conformità o non registrati in Intune.
   - Quando si imposta questa opzione per bloccare l'accesso, inizialmente viene bloccato l'accesso di tutti i dispositivi a Exchange locale.  I dispositivi che appartengono agli utenti in **Gruppi inclusi** hanno l'accesso dopo che il dispositivo viene registrato in Intune e ritenuto conforme. I dispositivi Android che non eseguono Samsung Knox Standard sono sempre bloccati perché non supportano questa impostazione.

1. In **Eccezioni della piattaforma del dispositivo** scegliere **Aggiungi** per specificare le piattaforme. Se l'opzione **Accesso al dispositivo non gestito** è impostata su **Bloccato**, i dispositivi conformi e registrati possono accedere anche se è presente un'eccezione che blocca la piattaforma. Scegliere **OK** per salvare le impostazioni.

1. Nel riquadro **Locale** fare clic su **Salva** per salvare il criterio di accesso condizionale.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Creare criteri di accesso condizionale di Azure AD in Intune

A partire dalla versione 1704 di Intune, gli amministratori possono creare criteri di accesso condizionale di Azure AD dal portale di Intune di Azure, una soluzione che non richiede di spostarsi tra i carichi di lavoro Azure e Intune.

> [!IMPORTANT]
> È necessario avere una licenza di Azure AD Premium per creare criteri di accesso condizionale di Azure AD dal portale di Intune di Azure.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Per creare criteri di accesso condizionale di Azure AD

1. Nel **dashboard di Intune** scegliere **Accesso condizionale**.

2. Nel riquadro **Criteri** scegliere **Nuovi criteri** per creare i nuovi criteri di accesso condizionale di Azure AD.

## <a name="see-also"></a>Vedere anche

[Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
