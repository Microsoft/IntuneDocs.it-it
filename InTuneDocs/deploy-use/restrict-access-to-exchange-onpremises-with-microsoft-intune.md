---
title: Proteggere l&quot;accesso alla posta elettronica in Exchange locale | Microsoft Docs
description: Proteggere e controllare l&quot;accesso alla posta elettronica aziendale in Exchange On-premises con accesso condizionale.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a55071f5-101e-4829-908d-07d3414011fc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: 24d000f650cafffc0c998ef80ba52bd06b56afe2


---

# <a name="protect-email-access-to-exchange-on-premises-and-legacy-exchange-online-dedicated-with-intune"></a>Proteggere l'accesso alla posta elettronica per Exchange locale e l'ambiente legacy Exchange Online dedicato con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> Se è disponibile un ambiente Exchange Online dedicato e si deve stabilire se si trova nell'ambiente di configurazione nuovo o legacy, contattare l'account manager.


Per controllare l'accesso alla posta elettronica per Exchange locale o per l'ambiente legacy Exchange Online dedicato, configurare l'accesso condizionale per Exchange locale tramite Microsoft Intune.
Per altre informazioni sul funzionamento dell'accesso condizionale, leggere l'articolo [Proteggere l'accesso alla posta elettronica e ai servizi O365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

**Prima** di configurare l'accesso condizionale, verificare quanto segue:

-   La versione di Exchange deve essere **Exchange 2010 o successiva**. Sono supportati array di server Accesso client di Exchange Server.

-   È necessario usare **On-premises Exchange Connector** che connette [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] a Exchange locale. Questo connettore consente di gestire i dispositivi attraverso la console di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Per informazioni dettagliate sul connettore, vedere [Install the Intune on-premises Exchange Connector](intune-on-premises-exchange-connector.md) (Installare On-premises Exchange Connector).

    -   On-premises Exchange Connector, disponibile nella console di Intune, è specifico del tenant di Intune e non può essere usato con un altro tenant. È consigliabile anche assicurarsi che Exchange Connector per il tenant sia installato **in un solo computer**.

        È possibile scaricare il connettore dalla console di amministrazione di Intune. Per una procedura dettagliata sulla configurazione di On-premises Exchange Connector, vedere [Install the Intune on-premises Exchange Connector](intune-on-premises-exchange-connector.md) (Installare Intune On-premises Exchange Connector).

    -   Il connettore può essere installato in qualsiasi computer, purché sia in grado di comunicare con il server di Exchange.

    -   Questo connettore supporta l'**ambiente CAS di Exchange**. Anche se è tecnicamente possibile, non è consigliabile installare il connettore direttamente nel server CAS di Exchange perché comporta un aumento del carico nel server. Quando si configura il connettore, è necessario configurarlo in modo che comunichi con uno dei server CAS di Exchange.

-   È necessario configurare **Exchange ActiveSync** per l'autenticazione basata su certificati o l'immissione di credenziali utente.

Quando si configurano i criteri per l'accesso condizionale e li si assegna a un utente, prima che un utente possa connettersi alla posta elettronica, il **dispositivo** in uso deve:

-  Essere un PC aggiunto a un dominio o **registrato** in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-  Essere **registrato in Azure Active Directory**. Inoltre, l'ID client Exchange ActiveSync deve essere registrato con Azure Active Directory.

  Il servizio Registrazione dispositivo di Azure Active Directory viene attivato automaticamente per i clienti di Intune e Office 365. I clienti che hanno già distribuito il servizio di registrazione dei dispositivi di ADFS non visualizzeranno i dispositivi registrati in Active Directory locale. **Ciò non si applica ai PC Windows e ai dispositivi Windows Phone**.

-   Essere **compatibile** con i criteri di conformità di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] distribuiti per il dispositivo.

Il diagramma seguente illustra il flusso usato dai criteri di accesso condizionale per Exchange locale per valutare se consentire o bloccare i dispositivi.

![Diagramma che illustra gli aspetti tenuti in considerazione per determinare se a un dispositivo è consentito o meno l'accesso a Exchange locale](../media/ConditionalAccess8-2.png)

Se non viene soddisfatto un criterio di accesso condizionale, quando esegue l'accesso l'utente vede uno dei messaggi seguenti:

- Se il dispositivo non è registrato in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente istruzioni su come installare l'app Portale aziendale, registrare il dispositivo e attivare la posta elettronica. Questo processo associa anche l'ID Exchange ActiveSync del dispositivo con il record del dispositivo in Azure Active Directory.

-   Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale o all'app Portale aziendale di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] dove sono disponibili informazioni sul problema e su come risolverlo.

## <a name="support-for-mobile-devices"></a>Supporto per dispositivi mobili
Sono supportati:
-   Windows Phone 8.1 e versioni successive.

-   App di posta elettronica nativa in iOS.

-   Client di posta Exchange ActiveSync, ad esempio Gmail in Android 4 o versione successiva.
- Client di posta Exchange ActiveSync in **dispositivi Android for Work**: nei dispositivi Android for Work sono supportate solo le app **Gmail** e **Nine Work** nel **profilo di lavoro**. Perché l'accesso condizionale funzioni in Android for Work, è necessario distribuire un profilo di posta elettronica per l'app Gmail o Nine Work. È anche necessario distribuire tali app come installazioni obbligatorie. 

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

> [!NOTE]
> L'app Microsoft Outlook per Android e iOS non è supportata.

## <a name="support-for-pcs"></a>Supporto per PC
È supportata:
-   L'applicazione **Mail** in Windows 8.1 e versioni successive (se il PC è registrato in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).

##  <a name="configure-a-conditional-access-policy"></a>Configurare i criteri di accesso condizionale

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** > **Accesso condizionale** > **Criteri di Exchange locale**.
![IntuneSA5aSelectExchOnPremPolicy](../media/IntuneSA5aSelectExchOnPremPolicy.png)

2.  Configurare i criteri con le impostazioni richieste: ![Screenshot della pagina dei criteri di Exchange locale](../media/IntuneSA5bExchangeOnPremPolicy.png)

  - **Bloccare l'accesso delle app di posta elettronica a Exchange locale se il dispositivo non è conforme o non è registrato in Microsoft Intune**: quando si seleziona questa opzione, ai dispositivi non gestiti da [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o non compatibili con i criteri di conformità non è consentito l'accesso ai servizi di Exchange.

  - **Sostituzione della regola predefinita: consenti sempre l'accesso a Exchange ai dispositivi conformi e registrati in Intune**: quando si seleziona questa opzione, i dispositivi registrati in Intune e conformi ai criteri di conformità possono accedere a Exchange.
  Questa regola sostituisce la **regola predefinita**, ossia anche se si definisce per la **regola predefinita** l'impostazione per la quarantena o il blocco dell'accesso, i dispositivi registrati e conformi possono comunque accedere a Exchange.

  - **Gruppi di destinazione**: selezionare i gruppi di utenti di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] che devono registrare il proprio dispositivo in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per poter accedere a Exchange.

  - **Gruppi di esenzione**: selezionare i gruppi di utenti di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] esenti dai criteri di accesso condizionale. Gli utenti in questo elenco sono esenti anche se sono inclusi nell'elenco **Gruppi di destinazione**.

  - **Eccezioni della piattaforma**: scegliere **Aggiungi regola** per configurare una regola che definisce i livelli di accesso per gruppi e modelli specificati di dispositivi mobili. Poiché questi dispositivi possono essere di qualsiasi tipo, possono essere configurati anche i tipi di dispositivo non supportati da [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

  - **Regola predefinita**: per un dispositivo non soggetto a nessun'altra regola, è possibile scegliere di consentire l'accesso a Exchange, bloccarlo o metterlo in quarantena. Quando si imposta la regola per consentire l'accesso, per i dispositivi registrati e conformi, l'accesso alla posta elettronica viene concesso automaticamente per i dispositivi iOS, Windows e Samsung KNOX. L'utente non deve eseguire alcuna procedura per ottenere l'accesso alla posta elettronica.

        Nei dispositivi Android che non eseguono Samsung KNOX, gli utenti visualizzano un messaggio di posta elettronica di quarantena che include una procedura guidata per verificare la conformità e la registrazione prima di poter accedere alla posta elettronica. Se si imposta la regola per bloccare l'accesso o mettere in quarantena i dispositivi, viene bloccato l'accesso a Exchange per tutti i dispositivi, indipendentemente dalla registrazione in Intune. Per impedire che i dispositivi registrati e conformi siano interessati da questa regola, selezionare **Override regola predefinita**.
>[!TIP]
>Se si intende bloccare tutti i dispositivi prima di concedere l'accesso alla posta elettronica, scegliere la regola per il blocco dell'accesso o la quarantena. La regola predefinita viene applicata a tutti i tipi di dispositivo, quindi ha effetto anche sui tipi configurati come eccezioni di piattaforma e che non sono supportati da [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

  - **Notifica utente**: oltre al messaggio di posta elettronica di notifica inviato da Exchange, Intune invia un messaggio di posta elettronica che contiene le istruzioni per sbloccare il dispositivo. È possibile modificare il messaggio predefinito per personalizzarlo in base alle proprie esigenze. Nel caso in cui il dispositivo dell'utente venga bloccato prima della ricezione del messaggio di posta elettronica di notifica di Intune contenente le istruzioni per la correzione (questo messaggio viene recapitato alla cassetta postale di Exchange dell'utente), è possibile usare un dispositivo non bloccato o un altro metodo per accedere a Exchange e visualizzare il messaggio.

        This is especially true when the **Default Rule** is set to block or quarantine. In this case, the user has to go to their app store, download the Microsoft Company Portal app, and enroll their device. This is applicable to iOS, Windows, and Samsung KNOX devices. For devices that don't run Samsung KNOX, you need to send the quarantine email to an alternate email account. The user has to copy the email to their blocked device to complete the enrollment and compliance process.
  > [!NOTE]
  > Affinché Exchange sia in grado di inviare il messaggio di posta elettronica di notifica, è necessario specificare l'account usato per inviare tale messaggio.
  >
  > Per informazioni dettagliate, vedere [Installare Intune On-premises Exchange Connector](intune-on-premises-exchange-connector.md).

3.  Al termine dell'operazione scegliere **Salva**.

-   Non è necessario distribuire i criteri di accesso condizionale perché diventano immediatamente effettivi.

-   Dopo la configurazione di un profilo di Exchange ActiveSync, il blocco del dispositivo potrebbe richiedere da 1 a 3 ore, a meno che non sia gestito da [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   Se un utente bloccato registra il dispositivo in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e risolve il problema di conformità, l'accesso alla posta elettronica verrà sbloccato entro 2 minuti.

-   Se l'utente annulla la registrazione da [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], il blocco del dispositivo potrebbe richiedere da 1 a 3 ore.

**Per vedere alcuni scenari di esempio sulla configurazione dei criteri di accesso condizionale per proteggere l'accesso dei dispositivi, vedere [Proteggere l'accesso alla posta elettronica: scenari di esempio](restrict-email-access-example-scenarios.md).**

## <a name="next-steps"></a>Passaggi successivi
-   [Proteggere l'accesso a SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

-   [Proteggere l'accesso a Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->


