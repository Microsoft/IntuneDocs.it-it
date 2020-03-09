---
title: Creare criteri di accesso condizionale per Exchange
titleSuffix: Microsoft Intune
description: Configurare l'accesso condizionale per Exchange locale ed Exchange Online dedicato legacy in Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6650c091917ea265783044efd78b19a7e032e6a7
ms.sourcegitcommit: 5511b4f2b8a3383176a7afe2a22ad5a8d42caf7b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169298"
---
# <a name="configure-exchange-on-premises-access-for-intune"></a>Configurare l'accesso locale a Exchange per Intune

Questo articolo illustra come configurare l'accesso condizionale per Exchange locale in base alla conformità del dispositivo.

Se si dispone di un ambiente Exchange Online dedicato ed è necessario definire se si trova nell'ambiente di configurazione nuovo o legacy, contattare l'account manager. Per controllare l'accesso alla posta elettronica per Exchange locale o per l'ambiente legacy Exchange Online dedicato, configurare l'accesso condizionale per Exchange locale in Intune.

## <a name="before-you-begin"></a>Prima di iniziare

Prima di configurare l'accesso condizionale, verificare che siano presenti le configurazioni seguenti:

- La versione di Exchange è **Exchange 2010 SP1 o successiva**. È supportato un array del server Accesso client di Exchange Server.

- È stato installato ed è in uso [On-Premises Exchange Connector di Exchange Active Sync](exchange-connector-install.md), che connette Intune a Exchange locale.

    >[!IMPORTANT]  
    >Intune supporta più Exchange Connector locali per ogni sottoscrizione.  Tuttavia ogni istanza di Exchange Connector locale è specifica per un singolo tenant di Intune e non può essere usata con un altro tenant.  Se sono presenti più organizzazioni di Exchange locali, è possibile configurare un connettore separato per ogni organizzazione di Exchange.

- Il connettore per un'organizzazione di Exchange locale può essere installato in qualsiasi computer, a condizione che il computer sia in grado di comunicare con il server di Exchange.

- Questo connettore supporta l'**ambiente CAS di Exchange**. Intune supporta l'installazione diretta del connettore nel server CAS di Exchange. È consigliabile installarlo in un computer separato in considerazione del carico aggiuntivo del connettore nel server. Quando si configura il connettore, è necessario configurarlo in modo che comunichi con uno dei server CAS di Exchange.

- È necessario configurare **Exchange ActiveSync** per l'autenticazione basata su certificati o l'immissione di credenziali utente.

- Quando i criteri per l'accesso condizionale sono stati configurati e indirizzati a un utente, prima che un utente possa connettersi alla posta elettronica, il **dispositivo** in uso deve:
  - Essere **registrato** con Intune o essere un PC aggiunto a un dominio.
  - Essere **registrato in Azure Active Directory**. Inoltre, l'ID client Exchange ActiveSync deve essere registrato con Azure Active Directory.

- Il servizio Registrazione dispositivo Azure AD (DRS) viene attivato automaticamente per i clienti di Intune e Office 365. I clienti che hanno già distribuito il servizio Device Registration Service di ADFS non visualizzano i dispositivi registrati in Active Directory locale. **Ciò non si applica ai PC Windows e ai dispositivi Windows Phone**.

- Essere **conforme** ai criteri di conformità dei dispositivi distribuiti a quel dispositivo.

- Se il dispositivo non soddisfa le impostazioni dei criteri di accesso condizionale, all'accesso viene visualizzato uno dei messaggi seguenti:
  - Se il dispositivo non è registrato in Intune oppure non è registrato in Azure Active Directory, viene visualizzato un messaggio contenente istruzioni per installare l'app Portale aziendale, registrare il dispositivo e attivare la posta elettronica. Questo processo associa anche l'ID Exchange ActiveSync del dispositivo con il record del dispositivo in Azure Active Directory.
  - Se il dispositivo non è conforme, viene visualizzato un messaggio che indirizza l'utente al sito Web del portale aziendale di Intune o all'app Portale aziendale. Nel portale aziendale sono disponibili informazioni sul problema e su come risolverlo.

### <a name="support-for-mobile-devices"></a>Supporto per dispositivi mobili

- **Windows Phone 8.1 e versioni successive** - Per creare i criteri di accesso condizionale, vedere [Creare criteri di accesso condizionale](../protect/create-conditional-access-intune.md)
- **App di posta elettronica nativa in iOS/iPadOS** - Per creare i criteri di accesso condizionale, vedere [Creare criteri di accesso condizionale](../protect/create-conditional-access-intune.md)
- **Client di posta EAS, ad esempio Gmail in Android 4 o versione successiva** - Per creare i criteri di accesso condizionale, vedere [Creare criteri di accesso condizionale](../protect/create-conditional-access-intune.md)

- **Client di posta EAS in dispositivi con profilo di lavoro Android** - Per i dispositivi con profilo di lavoro Android sono supportati solo *Gmail* e *Nine Work for Android Enterprise*. Perché l'accesso condizionale funzioni nei profili di lavoro Android, è necessario distribuire un profilo di posta elettronica per l'app *Gmail* o *Nine Work for Android Enterprise*. È anche necessario distribuire tali app come installazioni obbligatorie. Dopo aver distribuito l'app, è possibile configurare l'accesso condizionale basato sul dispositivo.

#### <a name="to-set-up-conditional-access-for-android-work-profile-devices"></a>Per configurare l'accesso condizionale per i dispositivi con profilo di lavoro Android

  1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
  
  2. Distribuire l'app Gmail o Nine Work come **Obbligatoria**.

  3. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**, immettere **Nome** e **Descrizione** per il profilo.

  4. Selezionare **Android Enterprise** in **Piattaforma** e selezionare **Posta elettronica** in **Tipo di profilo**.

  5. Configurare le [impostazioni del profilo di posta elettronica](https://docs.microsoft.com/intune/configuration/email-settings-android-enterprise#android-enterprise).

  6. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

  7. Dopo aver creato il profilo di posta elettronica, [assegnarlo ai gruppi](https://docs.microsoft.com/intune/device-profile-assign).

  8. Configurare l'[accesso condizionale basato sul dispositivo](https://docs.microsoft.com/intune/protect/conditional-access-intune-common-ways-use#device-based-conditional-access).

> [!NOTE]
> Microsoft Outlook per Android e iOS/iPadOS non è supportato tramite il connettore Exchange locale. Se si vogliono usare i criteri di accesso condizionale di Azure Active Directory e i criteri di Protezione app di Intune con Outlook per iOS/iPadOS e Android per le cassette postali in locale, vedere [Uso dell'autenticazione moderna ibrida con Outlook per iOS/iPadOS e Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

### <a name="support-for-pcs"></a>Supporto per PC

L'applicazione **Mail** nativa in Windows 8.1 e versioni successive (se registrata in MDM con Intune)

## <a name="configure-exchange-on-premises-access"></a>Configurare l'accesso locale a Exchange

Prima di poter usare la procedura seguente per configurare il controllo di accesso locale per Exchange, è necessario installare e configurare almeno un [Intune On-Premises Exchange Connector](exchange-connector-install.md) per Exchange locale.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Passare ad **Amministrazione del tenant** > **Accesso ad Exchange**, quindi selezionare **Accesso locale a Exchange**.

3. Nel riquadro **Accesso locale a Exchange** scegliere **Sì** per attivare l'opzione *Abilita il controllo di accesso locale per Exchange*.

   > [!div class="mx-imgBorder"]
   > ![Schermata di esempio della pagina di accesso locale a Exchange](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. In **Assegnazione** scegliere **Selezionare i gruppi da includere** e selezionare uno o più gruppi per configurare l'accesso.

   Ai membri dei gruppi selezionati vengono applicati i criteri Accesso condizionale per l'accesso a Exchange locale. Per poter accedere a Exchange locale, gli utenti che ricevono questi criteri devono registrare i propri dispositivi in Intune e soddisfare i requisiti dei profili di conformità.

   > [!div class="mx-imgBorder"]
   > ![Selezionare i gruppi da includere](./media/conditional-access-exchange-create/select-groups.png)

5. Per escludere gruppi, scegliere **Selezionare i gruppi da escludere** e selezionare uno o più gruppi esenti dai requisiti per la registrazione dei dispositivi e dall'essere conforme con per i profili di conformità ai fini dell'accesso a Exchange locale.

   Selezionare **Salva** per salvare la configurazione e tornare al riquadro **Accesso ad Exchange**.

6. Quindi configurare le impostazioni di Intune On-Premises Exchange Connector. Nella console selezionare **Amministrazione del tenant** > **Accesso ad Exchange**> **Connettore locale per Exchange ActiveSync** e quindi selezionare il connettore per l'organizzazione di Exchange che si vuole configurare.

7. Per **Notifiche utente** selezionare **Modifica** per aprire il flusso di lavoro **Modifica organizzazione** in cui è possibile modificare il messaggio di *notifica per l'utente*.

   > [!div class="mx-imgBorder"]
   > ![Schermata di esempio del flusso di lavoro Modifica organizzazione per le notifiche](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   Modificare il messaggio di posta elettronica predefinito inviato agli utenti se il dispositivo non è conforme e gli utenti vogliono accedere a Exchange locale. Il modello di messaggio usa il linguaggio di markup. Mentre si digita è anche possibile visualizzare l'anteprima dell'aspetto del messaggio

   Selezionare **Verifica e salva** e quindi **Salva** per salvare le modifiche e completare la configurazione dell'accesso a Exchange locale.

   > [!TIP]
   > Per altre informazioni sul linguaggio di markup, vedere questo [articolo](https://en.wikipedia.org/wiki/Markup_language) di Wikipedia.

8. Selezionare **Impostazioni avanzate dell'accesso a Exchange ActiveSync** per aprire il flusso di lavoro *Impostazioni avanzate dell'accesso a Exchange ActiveSync* e configurare le regole di accesso al dispositivo.

   > [!div class="mx-imgBorder"]
   > ![Schermata di esempio del flusso di lavoro Modifica organizzazione per le impostazioni avanzate](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - In **Accesso al dispositivo non gestito** impostare la regola predefinita globale per l'accesso da dispositivi non interessati dall'accesso condizionale o da altre regole:

     - **Consenti l'accesso**: tutti i dispositivi sono in grado di accedere immediatamente a Exchange locale. I dispositivi che appartengono agli utenti nei gruppi configurati come inclusi nella procedura precedente vengono bloccati se in un secondo momento sono ritenuti non conformi in base ai criteri di conformità o non registrati in Intune.

     - **Blocca accesso** e **Quarantena**: inizialmente viene bloccato l'accesso di tutti i dispositivi a Exchange locale. I dispositivi che appartengono a utenti dei gruppi configurati come inclusi nella procedura precedente ottengono l'accesso dopo che il dispositivo viene registrato in Intune e valutato come conforme.

       I dispositivi Android che *non* eseguono Samsung Knox non supportano questa impostazione e vengono sempre bloccati.

   - In **Eccezioni della piattaforma del dispositivo** selezionare **Aggiungi** e quindi specificare i dettagli necessari per l'ambiente.

      Se l'opzione **Accesso al dispositivo non gestito** è impostata su **Bloccato**, i dispositivi conformi e registrati possono accedere anche se è presente un'eccezione della piattaforma che li blocca.  

9. Selezionare **OK** per salvare le modifiche.

10. Selezionare **Verifica e salva** e quindi **Salva** per salvare i criteri di accesso condizionale di Exchange.

## <a name="next-steps"></a>Passaggi successivi

Quindi creare un criterio di conformità e assegnarlo agli utenti, in modo che Intune valuti i dispositivi mobili. Vedere [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

[Risoluzione dei problemi di Intune On-Premises Exchange Connector in Microsoft Intune](https://support.microsoft.com/help/4471887)
