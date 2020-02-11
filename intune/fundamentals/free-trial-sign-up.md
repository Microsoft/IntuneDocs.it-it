---
title: Guida introduttiva - Provare Microsoft Intune gratuitamente
titleSuffix: ''
description: In questa guida introduttiva si creerà una sottoscrizione di valutazione gratuita, verranno spiegate le configurazioni supportate e i requisiti di rete e, in via facoltativa, si procederà alla configurazione del nome del dominio.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/16/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1baf0b4273a9074ac7172c08240a8e3c3a9d7fa
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541116"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Guida introduttiva: Provare Microsoft Intune gratuitamente

Microsoft Intune aiuta a proteggere i dati aziendali del personale tramite la gestione dei dispositivi e delle app. In questa guida introduttiva si creerà una sottoscrizione gratuita per provare Intune in un ambiente di test.

Intune offre la gestione dei dispositivi mobili (MDM) e delle app per dispositivi mobili (MAM) con un servizio sicuro e basato sul cloud gestito usando l'interfaccia di amministrazione di Microsoft Endpoint Manager. Tramite Intune ci si assicura che la configurazione, l'aggiornamento e l'accesso alle risorse aziendali del personale, cioè i dati, i dispositivi e le app, siano gestiti correttamente e che soddisfino i criteri di conformità e i requisiti aziendali.

## <a name="prerequisites"></a>Prerequisiti
Prima di configurare Microsoft Intune, esaminare i requisiti seguenti:

- [Sistemi operativi e browser supportati](supported-devices-browsers.md)
- [Requisiti di configurazione di rete e larghezza di banda](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Iscriversi per una versione di valutazione gratuita di Microsoft Intune

È possibile provare Intune gratuitamente per 30 giorni. Se si ha già un account aziendale o dell'istituto di istruzione, **eseguire l'accesso** con tale account e aggiungere Intune alla sottoscrizione. In alternativa, è possibile **iscriversi** per ottenere un nuovo account e usare Intune per l'organizzazione.

> [!IMPORTANT]
> Non è possibile combinare un account aziendale o dell'istituto di istruzione dopo essersi iscritti per ottenere un nuovo account.

1. Andare alla pagina della [versione di valutazione di Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2019088) e compilare il modulo.

    ![Screenshot della pagina Web di iscrizione per l'account di prova Microsoft Intune](./media/free-trial-sign-up/account-sign-up-site-full-browser.png)

    Se per la maggior parte delle operazioni IT e degli utenti viene usata un'area geografica diversa dalla propria, è consigliato selezionarla in **Paese o area geografica**. Azure usa le informazioni a livello di area per offrire i servizi corretti. Questa impostazione non può essere modificata in un secondo tempo.

2. Creare un account con il nome della propria società seguito da **.onmicrosoft.com**. 

    ![Screenshot del processo di definizione delle nuove credenziali per l'account di prova Intune](./media/free-trial-sign-up/account-sign-up-site-user-id.png)

    Se si vuole usare il dominio personalizzato dell'organizzazione anziché **.onmicrosoft.com**, è possibile cambiare questa opzione nell'interfaccia di amministrazione di Microsoft 365 descritta più avanti in questo articolo.

3. Al termine del processo di iscrizione, l'utente può visualizzare le informazioni del nuovo account.

    ![Immagine delle informazioni sull'account](./media/free-trial-sign-up/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Accedere a Intune in Microsoft Endpoint Manager

Se non è già stato effettuato l'accesso al portale, completare i passaggi seguenti:

1. Aprire una nuova finestra del browser e immettere **https://devicemanagement.microsoft.com** nella barra degli indirizzi. 
2. Usare l'ID utente assegnato nei passaggi precedenti per eseguire l'accesso ( *yourID@yourdomain* . onmicrosoft.com).

    ![Immagine della pagina di accesso al portale](./media/free-trial-sign-up/azure-portal-signin.png)

Quando si esegue l'iscrizione per una versione di valutazione, all'indirizzo di posta elettronica specificato in fase di iscrizione verrà anche inviato un messaggio contenente le informazioni sul proprio account. Questo messaggio conferma che la versione di valutazione è attiva.

> [!TIP]
> Quando si usa Microsoft Endpoint Manager è possibile ottenere risultati migliori usando un browser in modalità normale anziché in modalità privata.

## <a name="confirm-the-mdm-authority-in-intune"></a>Confermare l'autorità MDM in Intune

Per impostazione predefinita, l'autorità MDM è impostata quando si crea la versione di prova gratuita. Per verificare che l'autorità MDM sia impostata, seguire questa procedura:

1. Se non è già stato effettuato l'accesso, accedere a Microsoft Endpoint Manager.
2. Fare clic su **Amministrazione del tenant**.
3. Visualizzare i dettagli del tenant. L'**autorità MDM** dovrebbe essere impostata su **Microsoft Intune**.

Se dopo l'accesso a Microsoft Endpoint Manager viene visualizzato un banner arancione che indica che non è stata ancora impostata l'autorità MDM, è possibile attivarla in questa fase. L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'autorità MDM deve essere impostata per consentire agli utenti di registrare i dispositivi per la gestione.

### <a name="to-set-the-mdm-authority-to-intune-follow-these-steps"></a>Per impostare l'autorità MDM su Intune, seguire questa procedura:

1. Aprire una nuova finestra del browser e immettere **https://portal.azure.com** nella barra degli indirizzi. 
2. Scegliere **Tutti i servizi** > **Microsoft Intune**.
3. Selezionare il banner che indica che non è stata abilitata la gestione dei dispositivi oppure, se il banner non viene visualizzato immediatamente, selezionare **Registrazione del dispositivo**. Se non è stata ancora abilitata la gestione dei dispositivi viene visualizzato il pannello **Scegliere l'autorità MDM**.

    > [!NOTE]
    > Se l'autorità MDM è stata impostata, il valore dell'autorità MDM sarà visualizzato nel pannello **Registrazione del dispositivo**. L'intestazione arancione viene visualizzata solo se l'autorità MDM non è stata ancora impostata. 

    ![Immagine del pannello Scegliere l'autorità MDM](./media/free-trial-sign-up/choose-mdm-authority.png) 

4. Se l'autorità MDM non è impostata, in **Scegliere l'autorità MDM** impostare l'autorità MDM su **Autorità MDM Intune**.

Per altre informazioni sull'autorità MDM, vedere [Impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md).

## <a name="configure-your-custom-domain-name-optional"></a>Configurare il nome di dominio personalizzato (facoltativo)

Come accennato in precedenza, se l'organizzazione ha il proprio dominio personalizzato che si vuole usare senza **.onmicrosoft.com**, cambiare questa opzione nell'interfaccia di amministrazione di Microsoft 365. È possibile aggiungere, verificare e configurare il nome di dominio personalizzato usando la procedura seguente.  

> [!IMPORTANT]
> Non è possibile rinominare o rimuovere la parte **onmicrosoft.com** *iniziale* del nome di dominio. È tuttavia possibile aggiungere, verificare o rimuovere i nomi di dominio *personalizzati* usati con Intune in modo che l'identità aziendale risulti chiara. Per altre informazioni, vedere [Configurare un nome di dominio personalizzato](custom-domain-name-configure.md).

1. Passare all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) e accedere con l'account amministratore.

2. Nel riquadro di spostamento scegliere **Impostazioni** > **Domini** > **Aggiungi dominio**.

3. Immettere il nome di dominio personalizzato. Selezionare **Avanti**.

   ![Screenshot dell'interfaccia di amministrazione di Microsoft 365 - Aggiunta del dominio](./media/free-trial-sign-up/domain-custom-add.png)

4. Verificare di essere il proprietario del dominio immesso nel passaggio precedente. 
    
    Selezionando **Invia codice per posta elettronica**, il contatto registrato del dominio riceverà un messaggio di posta elettronica. Copiare il codice contenuto nel messaggio di posta elettronica e immetterlo nel campo **Digita qui il codice di verifica**. Se il codice di verifica corrisponde, il dominio verrà aggiunto al tenant. Il messaggio di posta elettronica visualizzato potrebbe non avere un aspetto familiare. Alcuni registrar nascondono l'indirizzo di posta elettronica reale. L'indirizzo di posta elettronica può anche essere diverso da quello specificato in fase di registrazione del dominio.

   ![Screenshot dell'interfaccia di amministrazione di Microsoft 365 - Verifica del dominio](./media/free-trial-sign-up/domain-custom-verify.png)

   > [!NOTE]
   > Per informazioni dettagliate sulla verifica dei record TXT, vedere [Creare record DNS presso un provider di hosting DNS per Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Esperienze di amministrazione

Sono due i portali che verranno usati più spesso:
- L'interfaccia di amministrazione di Microsoft Endpoint Manager ([https://devicemanagement.microsoft.com/](https://devicemanagement.microsoft.com/)) consente di esplorare le [funzionalità di Intune](what-is-intune.md). Si tratta della posizione in cui l'amministratore lavora con Intune.
- L'interfaccia di amministrazione di Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) è la posizione in cui è possibile aggiungere e gestire gli utenti se non si usa Azure Active Directory a tale scopo. È anche possibile gestire altri aspetti del proprio account, incluse la fatturazione e il supporto tecnico.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stata creata una sottoscrizione gratuita per provare Intune in un ambiente di test. Per altre informazioni sulla configurazione di Intune, vedere [Configurare Intune](setup-steps.md).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Creare un utente e assegnargli una licenza](quickstart-create-user.md)
