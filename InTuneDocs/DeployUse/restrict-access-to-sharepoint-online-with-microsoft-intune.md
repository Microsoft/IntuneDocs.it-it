---
# required metadata

title: Limitare l'accesso a SharePoint Online | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Limitare l'accesso a SharePoint Online con Microsoft Intune
Usare l'accesso condizionale di [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] per controllare l'accesso ai file in SharePoint Online.
L'accesso condizionale è costituito da due componenti:
- Criteri di conformità che il dispositivo deve soddisfare per essere considerato conforme.
- Criteri di accesso condizionale in cui si specificano le condizioni che il dispositivo deve soddisfare per poter accedere al servizio.
Per altre informazioni sul funzionamento dell'accesso condizionale, leggere l'argomento [Limitare l'accesso alla posta elettronica e ai servizi di Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Quando un utente prova a connettersi a un file usando un'app supportata, come OneDrive installata nel dispositivo, vengono effettuate le valutazioni seguenti.

![Immagine che illustra gli aspetti che determinano se a un dispositivo è consentito o meno l'accesso a SharePoint ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>L'accesso condizionale per i PC e i dispositivi Windows 10 Mobile con app che usano l'autenticazione moderna non è attualmente disponibile per tutti i clienti di Intune. Se si usano già queste funzionalità, non è necessario intraprendere alcuna azione ed è possibile continuare a usarle.

>Se non sono stati creati criteri di accesso condizionale per PC o dispositivi Windows 10 Mobile con app che usano l'autenticazione moderna e si desidera eseguire questa operazione, è necessario inviare una richiesta.  Per altre informazioni sui problemi noti e su come ottenere l'accesso a questa funzionalità, consultare il [sito di Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=761472).

**Prima** di configurare i criteri di accesso condizionale per SharePoint Online è necessario:
- Avere una **sottoscrizione a SharePoint Online** e gli utenti devono avere una licenza per SharePoint Online.
- Avere una sottoscrizione di **Enterprise Mobility Suite** o **Azure Active Directory Premium**.

  Per connettersi ai file richiesti, il dispositivo deve:
-   Essere **registrato** con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] o un PC aggiunto a un dominio.

-   **Essere registrato** in Azure Active Directory. Questo avviene automaticamente quando il dispositivo viene registrato con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].


-   Essere compatibile con i criteri di conformità di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] distribuiti

Lo stato del dispositivo viene archiviato in Azure Active Directory che consente o blocca l'accesso ai file, in base alle condizioni specificate.

Se non viene soddisfatta una condizione, viene visualizzato uno dei due messaggi seguenti quando l'utente esegue l'accesso:

-   Se il dispositivo non è registrato con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente istruzioni su come installare l'app Portale aziendale ed eseguire la registrazione.

-   Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] dove sono disponibili informazioni sul problema e su come risolverlo.

## Supporto per dispositivi mobili
- iOS 7.1 e versioni successive
- Android 4.0 e versioni successive, Samsung Knox Standard 4.0 o versioni successive
- Windows Phone 8.1 e versioni successive

## Supporto per PC
- Windows 8.1 e versioni successive (se registrato con Intune)
- Windows 7.0 o Windows 8.1 (se aggiunto a un dominio)

  - I PC aggiunti a un dominio devono essere configurati in modo che vengano [registrati automaticamente](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) con Azure Active Directory.
Il servizio AAD DRS verrà attivato automaticamente per i clienti di Intune e Office 365. I clienti che hanno già distribuito il servizio di registrazione dei dispositivi di ADFS non visualizzeranno i dispositivi registrati in Active Directory locale.

  - Se i criteri sono impostati in modo da richiedere l'aggiunta a un dominio e il PC non è aggiunto a un dominio, viene visualizzato un messaggio che indica di contattare l'amministratore IT.

  - Se i criteri sono impostati in modo da richiedere l'aggiunta a un dominio o la conformità e il PC non soddisfa questi requisiti, viene visualizzato un messaggio contenente istruzioni su come installare l'app Portale aziendale ed eseguire la registrazione.
-    [L'autenticazione moderna di Office 365 deve essere abilitata](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) ed è necessario disporre di tutti gli aggiornamenti di Office più recenti.

    L'autenticazione moderna consente l'accesso basato su Active Directory Authentication Library (ADAL) ai client Windows con Office 2013 e offre migliori opzioni di sicurezza, come l'**autenticazione a più fattori** e l'**autenticazione basata sui certificati**.


## Configurare l'accesso condizionale per SharePoint Online

### Passaggio 1: Configurare i gruppi di sicurezza di Active Directory
Prima di iniziare configurare i gruppi di sicurezza di Azure Active Directory per i criteri di accesso condizionale. È possibile configurare questi gruppi nel **centro di amministrazione di Office 365**o nel **portale per gli account di Intune**. Questi gruppi verranno usati per destinare o escludere gli utenti dai criteri. Per poter accedere alle risorse, un utente di destinazione in un criterio deve usare solo dispositivi conformi.

In un criterio di SharePoint Online è possibile specificare due tipi di gruppi:

-   **Gruppi di destinazione**: contiene i gruppi di utenti ai quali si applicano i criteri.

-   **Gruppi di esenzione**: contiene i gruppi di utenti esclusi dai criteri.

Se un utente si trova in entrambi i gruppi, sarà esentato dai criteri.

### Passaggio 2: Configurare e distribuire i criteri di conformità
Se questa operazione non è ancora stata eseguita, creare e distribuire i criteri di conformità agli utenti a cui saranno destinati i criteri di SharePoint Online.

> [!NOTE] Mentre i criteri di conformità vengono distribuiti nei gruppi di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], i criteri di accesso condizionale sono destinati ai gruppi di sicurezza di Azure Active Directory.

Per informazioni dettagliate su come configurare i criteri di conformità, vedere [Creare i criteri di conformità](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT] Se i criteri di conformità non sono stati distribuiti, i dispositivi verranno considerati conformi.

Quando si è pronti, continuare con il **Passaggio 3**.

### Passaggio 3: Configurare i criteri di SharePoint Online
A questo punto, configurare i criteri in modo che solo i dispositivi gestiti e conformi possano accedere a SharePoint Online. Questi criteri verranno archiviati in Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** > **Accesso condizionale** > **Criteri di SharePoint Online**.
![Schermata della pagina dei criteri di SharePoint Online](../media/IntuneSASharePointOnlineCAPolicy.png)

2.  Selezionare **Abilita criteri di accesso condizionale per SharePoint Online**.

3.  In **Accesso all'applicazione** è possibile scegliere di applicare i criteri di accesso condizionale a:

    -   **Tutte le piattaforme**

        Tutti i dispositivi usati per accedere a **SharePoint Online** devono essere registrati in Intune e devono essere conformi ai criteri.  Qualsiasi applicazione client che usa l'**autenticazione moderna** è soggetta ai criteri di accesso condizionale. Se la piattaforma non è attualmente supportata da Intune, l'accesso a **SharePoint Online** è bloccato.
        >[!TIP]
        >Se l'accesso condizionale per PC non è già in uso, è possibile che questa opzione non venga visualizzata.  Usare le **piattaforme specifiche**. L'accesso condizionale per i PC non è attualmente disponibile per tutti i clienti di Intune.   Per altre informazioni sui problemi noti e su come ottenere l'accesso a questa funzionalità, consultare il [sito di Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=761472).

    -   **Piattaforme specifiche**

         I criteri di accesso condizionale si applicano a tutte le app client che usano l'autenticazione moderna nelle piattaforme specificate.

     Per i PC Windows, i PC devono essere aggiunti a un dominio oppure registrati e conformi a [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. È possibile impostare i requisiti seguenti:

     -   **I dispositivi devono essere aggiunti a un dominio o conformi.** Se si vuole che i PC siano aggiunti a un dominio o conformi ai criteri impostati in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], scegliere questa opzione. Se il PC non soddisfa alcun requisito, all'utente verrà richiesto di registrare il dispositivo con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **I dispositivi devono essere aggiunti a un dominio.** Affinché i PC vengano aggiunti a un dominio per l'accesso a Exchange Online, scegliere questa opzione. Se il PC non è aggiunto a un dominio, l'accesso alla posta elettronica è bloccato e all'utente viene richiesto di contattare l'amministratore IT.

     -   **I dispositivi devono essere conformi.** Affinché i PC siano registrati in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e conformi, scegliere questa opzione. Se il PC non è registrato, viene visualizzato un messaggio con le istruzioni su come eseguire la registrazione.

4.  In **Gruppi di destinazione**fare clic su **Modifica** per selezionare i gruppi di sicurezza di Azure Active Directory ai quali verranno applicati i criteri. È possibile scegliere applicare questa opzione a tutti gli utenti o solo a un gruppo selezionato di utenti.

5.  Facoltativamente, in **Gruppi esentati**fare clic su **Modifica** per selezionare i gruppi di sicurezza di Azure Active Directory esentati da questi criteri.

6.  Al termine, fare clic su **Salva**.

Non è necessario distribuire i criteri di accesso condizionale perché diventano immediatamente effettivi.

### Passaggio 4: Monitorare i criteri di conformità e di accesso condizionale
Nell'area di lavoro **Gruppi** è possibile visualizzare lo stato dei dispositivi.

Selezionare un gruppo qualsiasi di dispositivi mobili e quindi nella scheda **Dispositivi** selezionare uno dei **filtri**seguenti:

-   **Dispositivi non registrati con AAD** : si tratta dei dispositivi che non possono accedere a SharePoint Online.

-   **Dispositivi non conformi** : si tratta dei dispositivi che non possono accedere a SharePoint Online.

-   **Dispositivi conformi e registrati con AAD** : si tratta dei dispositivi che possono accedere a SharePoint Online.

### Vedere anche
[Limitare l'accesso alla posta elettronica e ai servizi di Office 365 con Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


