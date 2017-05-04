---
title: Creare e assegnare criteri di accesso condizionale per Exchange locale
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: come configurare l&quot;accesso condizionale per Exchange locale ed Exchange Online dedicato legacy su Intune.'
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 2a011bf390bb55d685f580cfc782b21ff0c2ebd5
ms.lasthandoff: 04/26/2017


---

# <a name="how-to-create-and-assign-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated-in-microsoft-intune-azure-preview"></a>Come creare e assegnare un criterio di accesso condizionale per Exchange locale ed Exchange Online dedicato legacy nell'anteprima di Microsoft Intune in Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Questo argomento descrive il processo di configurazione dell'accesso condizionale per Exchange locale a seconda della conformità del dispositivo.

Se si dispone di un ambiente Exchange Online dedicato ed è necessario definire se si trova nell'ambiente di configurazione nuovo o legacy, contattare l'account manager. Per controllare l'accesso alla posta elettronica per Exchange locale o per l'ambiente legacy Exchange Online dedicato, configurare l'accesso condizionale per Exchange locale in Intune.

## <a name="before-you-begin"></a>Prima di iniziare

Prima di configurare l'accesso condizionale, verificare quanto segue:

- La versione di Exchange deve essere **Exchange 2010 SP1 o successiva**. È supportato un array del server Accesso client di Exchange Server.

- È necessario usare [On-Premises Exchange Connector di Exchange Active](https://docs.microsoft.com/intune-azure/conditional-access/install-intune-on-premises-exchange-connector) che connette Intune a Exchange locale.

    >[!IMPORTANT]
    >On-premises Exchange Connector è specifico del tenant di Intune e non può essere usato con un altro tenant. È necessario anche assicurarsi che Exchange Connector per il tenant sia installato **in un solo computer**.

- Il connettore può essere installato in qualsiasi computer, purché sia in grado di comunicare con il server di Exchange.

- Questo connettore supporta l'**ambiente CAS di Exchange**. Anche se è tecnicamente possibile, non è consigliabile installare il connettore direttamente nel server CAS di Exchange perché aumenta il carico sul server. Quando si configura il connettore, è necessario configurarlo in modo che comunichi con uno dei server CAS di Exchange.

- È necessario configurare **Exchange ActiveSync** per l'autenticazione basata su certificati o l'immissione di credenziali utente.

- Quando i criteri per l'accesso condizionale sono stati configurati e indirizzati a un utente, prima che un utente possa connettersi alla posta elettronica, il **dispositivo** in uso deve:
    - Essere **registrato** con Intune o essere un PC aggiunto a un dominio.
    - Essere **registrato in Azure Active Directory**. Inoltre, l'ID client Exchange ActiveSync deve essere registrato con Azure Active Directory.
<br></br>
- Il servizio AAD DRS verrà attivato automaticamente per i clienti di Intune e Office 365. I clienti che hanno già distribuito il servizio di registrazione dei dispositivi di ADFS non visualizzeranno i dispositivi registrati in Active Directory locale. **Ciò non si applica ai PC Windows e ai dispositivi Windows Phone**.

- Essere **conforme** ai criteri di conformità dei dispositivi distribuiti a quel dispositivo.

- Se il dispositivo non soddisfa le impostazioni dei criteri di accesso condizionale, all'accesso l'utente visualizzerà uno dei messaggi seguenti:
    - Se il dispositivo non è registrato con Intune oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente istruzioni su come installare l'app Portale aziendale, eseguire la registrazione e attivare la posta elettronica. Questo processo associa anche l'ID Exchange ActiveSync del dispositivo con il record del dispositivo in Azure Active Directory.
    - Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale di Intune o all'app Portale aziendale dove sono disponibili informazioni sul problema e su come risolverlo.

### <a name="support-for-mobile-devices"></a>Supporto per dispositivi mobili

- Windows Phone 8.1 e versioni successive
- App di posta elettronica nativa in iOS
- Client di posta EAS, ad esempio Gmail in Android 4 o versione successiva.
- Client di posta EAS **Dispositivi Android for Work:** nei dispositivi Android for Work sono supportate solo le app **Gmail** e **Nine Work** nel **profilo di lavoro**. Perché l'accesso condizionale funzioni in Android for Work, è necessario distribuire un profilo di posta elettronica per l'app Gmail o Nine Work. È anche necessario distribuire tali applicazioni come installazioni obbligatorie.

> [!NOTE]
> L'app Microsoft Outlook per Android e iOS non è supportata. L'implementazione di Android for Work nei tenant Intune verrà completata nei prossimi mesi.

### <a name="support-for-pcs"></a>Supporto per PC

L'applicazione **Mail** nativa in Windows 8.1 e versioni successive (se registrata con Intune)


## <a name="configure-exchange-on-premises-access"></a>Configurare l'accesso locale a Exchange

1. Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le credenziali di Intune.

2. Dopo l'accesso viene visualizzato il **dashboard di Azure**.

3. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

4. Scegliere **Intune**. Verrà visualizzato il **dashboard di Intune**.

5.  Scegliere **Accesso condizionale** e quindi scegliere

6. Il pannello **Locale** visualizza lo stato dei criteri di accesso condizionale e i dispositivi da esso interessati.

7. In **Gestisci** scegliere **Accesso locale a Exchange**.

8. Nel pannello **Accesso locale a Exchange** scegliere **Sì** per consentire il controllo dell'accesso locale a Exchange.

      > [!NOTE]
      > Se Exchange Active Sync on-premises connector non è stato configurato, questa opzione sarà disabilitata.  È innanzitutto necessario installare e configurare il connettore prima di abilitare l'accesso condizionale a Exchange locale. Per altri dettagli, vedere [Installare Intune On-premises Exchange Connector](install-intune-on-premises-exchange-connector.md)

9. In **Assegnazione** scegliere **Gruppi inclusi**.  Usare il gruppo di utenti di sicurezza a cui applicare l'accesso condizionale. Ciò richiede agli utenti di registrare i propri dispositivi in Intune e renderli conformi ai profili di conformità.

10. Se si desidera escludere un determinato gruppo di utenti, è possibile farlo scegliendo **Gruppi esclusi** e selezionando un gruppo di utenti da escludere dalla richiesta di registrazione del dispositivo e conformità.

11. In **impostazioni** scegliere **Notifiche utente** per modificare il messaggio di posta elettronica predefinito. Questo messaggio viene inviato agli utenti se il dispositivo non è conforme e desiderano accedere a Exchange locale. Il modello di messaggio usa il linguaggio di markup.  Durante la digitazione, viene anche visualizzata l'anteprima dell'aspetto del messaggio.
    > [!TIP]
    > Per altre informazioni sul linguaggio di markup, vedere questo [articolo](https://en.wikipedia.org/wiki/Markup_language) di Wikipedia.

12. Nel pannello **Advanced Exchange Active Sync access settings** (Impostazioni di accesso a Exchange Active Sync avanzate) impostare la regola predefinita globale per l'accesso da dispositivi non gestiti da Intune e per le regole a livello di piattaforma come descritto nei prossimi due passaggi.

13. Per un dispositivo non soggetto ad accesso condizionale e a nessun'altra regola, è possibile scegliere di consentire l'accesso a Exchange o bloccarlo.
  - Quando si imposta questa opzione per consentire l'accesso, tutti i dispositivi saranno in grado di accedere immediatamente a Exchange locale.  I dispositivi che appartengono agli utenti nei **Gruppi inclusi** vengono bloccati se in un secondo momento sono ritenuti non conformi ai criteri di conformità o non registrati in Intune.
  - Quando si imposta questa opzione per bloccare l'accesso, inizialmente viene bloccato l'accesso di tutti i dispositivi a Exchange locale.  I dispositivi che appartengono agli utenti in **Gruppi inclusi** avranno l'accesso una volta che il dispositivo viene registrato in Intune e ritenuto conforme. I dispositivi Android che non eseguono Samsung KNOX standard saranno sempre bloccati poiché non supportano questa impostazione.
<br></br>
14. In **Eccezioni della piattaforma del dispositivo** scegliere **Aggiungi** per specificare le piattaforme. Se l'opzione **Accesso al dispositivo non gestito** è impostata su **Bloccato**, i dispositivi conformi e registrati potranno accedere anche se è presente un'eccezione che blocca la piattaforma. Scegliere **OK** per salvare le impostazioni.

15. Nel pannello **Locale** fare clic su **Salva** per salvare il criterio di accesso condizionale.

## <a name="create-azure-ad-conditional-access-policies-in-intune-azure-preview"></a>Creare criteri di accesso condizionale di Azure AD nell'anteprima di Intune in Azure

A partire dalla versione 1704 di Intune, gli amministratori possono creare criteri di accesso condizionale Azure AD dall'anteprima di Intune in Azure: una soluzione comoda che non richiede di spostarsi tra i carichi di lavoro Azure e Intune.

> [!IMPORTANT]
> È necessario avere una licenza di Azure AD Premium per creare criteri di accesso condizionale di Azure AD dal portale di anteprima di Intune in Azure.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Per creare criteri di accesso condizionale di Azure AD

1. Nel **dashboard di Intune** scegliere **Accesso condizionale**.

2. Nel dashboard **Accesso condizionale** scegliere **Accesso condizionale in Azure Active Directory**.

3. Scegliere **Nuovo criterio** per creare il nuovo criterio di accesso condizionale di Azure AD.

    ![Criteri di accesso condizionale di Azure AD](../media/Azure-AD-CA-Intune.png)

## <a name="see-also"></a>Vedere anche

[Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
