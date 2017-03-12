---
title: Criteri di accesso condizionale per Exchange locale
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: come configurare l&quot;accesso condizionale per Exchange locale ed Exchange Online dedicato legacy su Intune.'
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: a9edd882e2cf0fb7abf50002e9f1e8dfd5634fe1
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated-in-microsoft-intune-azure-preview"></a>Come creare un criterio di accesso condizionale per Exchange locale ed Exchange Online dedicato legacy nell'anteprima di Microsoft Intune in Azure


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Questo argomento descrive il processo di configurazione dell'accesso condizionale per Exchange locale a seconda della conformità del dispositivo.

Se si dispone di un ambiente Exchange Online dedicato ed è necessario definire se si trova nell'ambiente di configurazione nuovo o legacy, contattare l'account manager. Per controllare l'accesso alla posta elettronica per Exchange locale o per l'ambiente legacy Exchange Online dedicato, configurare l'accesso condizionale per Exchange locale in Intune.

## <a name="prerequisites"></a>Prerequisiti

**Prima** di configurare l'accesso condizionale, verificare quanto segue:

- La versione di Exchange deve essere **Exchange 2010 o successiva**. È supportato un array del server Accesso client di Exchange Server.
- È necessario usare **On-Premises Exchange Connector di Exchange Active** che connette Intune a Microsoft Exchange locale. Per informazioni dettagliate sul connettore, vedere <link>.

  - On-premises Exchange Connector, disponibile nella console di Intune, è specifico del tenant di Intune e non può essere usato con un altro tenant. È necessario anche assicurarsi che Exchange Connector per il tenant sia installato **in un solo computer**.

Questo connettore deve essere scaricato dalla console di amministrazione di Intune. Per una guida dettagliata sulla configurazione di On-Premises Exchange Connector, vedere <link to new topic>.

Il connettore può essere installato in qualsiasi computer, purché sia in grado di comunicare con il server di Exchange.

- Questo connettore supporta l'**ambiente CAS di Exchange**. Anche se è tecnicamente possibile, non è consigliabile installare il connettore direttamente nel server CAS di Exchange perché aumenta il carico sul server. Quando si configura il connettore, è necessario configurarlo in modo che comunichi con uno dei server CAS di Exchange.
- È necessario configurare **Exchange ActiveSync** per l'autenticazione basata su certificati o l'immissione di credenziali utente.

Quando i criteri per l'accesso condizionale sono stati configurati e indirizzati a un utente, prima che un utente possa connettersi alla posta elettronica, il **dispositivo** in uso deve:

- Essere **registrato** con Intune o essere un PC aggiunto a un dominio.
- Essere **registrato in Azure Active Directory**. Inoltre, l'ID client Exchange ActiveSync deve essere registrato con Azure Active Directory.

Il servizio AAD DRS verrà attivato automaticamente per i clienti di Intune e Office 365. I clienti che hanno già distribuito il servizio di registrazione dei dispositivi di ADFS non visualizzeranno i dispositivi registrati in Active Directory locale. **Ciò non si applica ai PC Windows e ai dispositivi Windows Phone**.

- Deve essere **compatibile** con i criteri di compatibilità di Intune distribuiti per quel dispositivo

Se il dispositivo non soddisfa le impostazioni dei criteri di accesso condizionale, all'accesso l'utente visualizzerà uno dei messaggi seguenti:

- Se il dispositivo non è registrato con Intune oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente istruzioni su come installare l'app Portale aziendale, eseguire la registrazione e attivare la posta elettronica. Questo processo associa anche l'ID Exchange ActiveSync del dispositivo con il record del dispositivo in Azure Active Directory.
- Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale di Intune o all'app Portale aziendale dove sono disponibili informazioni sul problema e su come risolverlo.

## <a name="support-for-mobile-devices"></a>Supporto per dispositivi mobili

- Windows Phone 8.1 e versioni successive
- App di posta elettronica nativa in iOS
- Client di posta EAS, ad esempio Gmail in Android 4 o versione successiva.
- Client di posta EAS **Dispositivi Android for Work:** nei dispositivi Android for Work sono supportate solo le app **Gmail** e **Nine Work** nel **profilo di lavoro**. Perché l'accesso condizionale funzioni in Android for Work, è necessario distribuire un profilo di posta elettronica per l'app Gmail o Nine Work. È anche necessario distribuire tali applicazioni come installazioni obbligatorie.

>[!NOTE]
>L'app Microsoft Outlook per Android e iOS non è supportata.

> L'implementazione di Android for Work nei tenant Intune verrà completata nei prossimi mesi.

Per altre informazioni sullo stato di supporto di Android for Work, leggere l'annuncio relativo ad Android for Work nell'edizione di ottobre 2016 di [Novità di Microsoft Intune](https://docs.microsoft.com/en-us/intune/whats-new/whats-new-archive#october-2016).

## <a name="support-for-pcs"></a>Supporto per PC

L'applicazione **Mail** in Windows 8.1 e versioni successive (se registrata con Intune)


## <a name="configure-exchange-on-premises-access"></a>Configurare l'accesso locale a Exchange

1. Scegliere il carico di lavoro **Accesso condizionale** nel portale di Azure per aprire il pannello Locale.
2. Il pannello **Locale** visualizza lo stato dei criteri di accesso condizionale e i dispositivi da esso interessati.
3. In **Gestisci** scegliere **Accesso locale a Exchange**.
4. Nel pannello **Accesso locale a Exchange** scegliere **Sì** per consentire il controllo dell'accesso locale a Exchange.

  >[!NOTE]
  >Se Exchange Active Sync on-premises connector non è stato configurato, questa opzione sarà disabilitata.  È innanzitutto necessario installare e configurare il connettore prima di abilitare l'accesso condizionale a Exchange locale. Per altri dettagli, vedere [Installare Intune On-premises Exchange Connector](install-intune-on-premises-exchange-connector.md)

5. In **Assegnazione** scegliere **Gruppi inclusi**.  Usare il gruppo di utenti di sicurezza a cui applicare l'accesso condizionale.  Ciò richiede agli utenti di registrare i propri dispositivi in Intune e renderli conformi ai profili di conformità.
6. Se si desidera escludere un determinato gruppo di utenti, è possibile farlo scegliendo **Gruppi esclusi** e selezionando un gruppo di utenti da escludere dalla richiesta di registrazione del dispositivo e conformità.
7. In **impostazioni** scegliere **Notifiche utente** per modificare il messaggio di posta elettronica predefinito. Questo messaggio viene inviato agli utenti se il dispositivo non è conforme e desiderano accedere a Exchange locale. Il modello di messaggio usa il linguaggio di markup.  Durante la digitazione, viene anche visualizzata l'anteprima dell'aspetto del messaggio. Per altre informazioni sul linguaggio di markup, vedere questo [articolo](https://en.wikipedia.org/wiki/Markup_language) di Wikipedia.
8. Nel pannello **Advanced Exchange Active Sync access settings** (Impostazioni di accesso a Exchange Active Sync avanzate) impostare la regola predefinita globale per l'accesso da dispositivi non gestiti da Intune e per le regole a livello di piattaforma come descritto nei prossimi due passaggi.
9. Per un dispositivo non soggetto ad accesso condizionale e a nessun'altra regola, è possibile scegliere di consentire l'accesso a Exchange o bloccarlo.
  - Quando si imposta questa opzione per consentire l'accesso, tutti i dispositivi saranno in grado di accedere immediatamente a Exchange locale.  I dispositivi che appartengono agli utenti nei **Gruppi inclusi** vengono bloccati se in un secondo momento sono ritenuti non conformi ai criteri di conformità o non registrati in Intune.
  - Quando si imposta questa opzione per bloccare l'accesso, inizialmente viene bloccato l'accesso di tutti i dispositivi a Exchange locale.  I dispositivi che appartengono agli utenti in **Gruppi inclusi** avranno l'accesso una volta che il dispositivo viene registrato in Intune e ritenuto conforme. I dispositivi Android che non eseguono Samsung KNOX standard saranno sempre bloccati poiché non supportano questa impostazione.
10. In **Eccezioni della piattaforma del dispositivo** scegliere **Aggiungi** per specificare le piattaforme. Se l'opzione **Accesso al dispositivo non gestito** è impostata su **Bloccato**, i dispositivi conformi e registrati potranno accedere anche se è presente un'eccezione che blocca la piattaforma. Scegliere **OK** per salvare le impostazioni.
11. Nel pannello **Locale** fare clic su **Salva** per salvare il criterio di accesso condizionale.
