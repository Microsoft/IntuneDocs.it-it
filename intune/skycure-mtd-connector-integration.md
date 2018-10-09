---
title: Configurare l'integrazione di Symantec con Microsoft Intune
titlesuffix: ''
description: Come configurare la soluzione Symantec Endpoint Protection Mobile con Microsoft Intune per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 00ae29b831bebb770b70c38b5e76d7f19bab10ee
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231398"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>Configurare l'integrazione di Symantec Endpoint Protection Mobile con Intune

Completare i passaggi seguenti per integrare la soluzione Symantec Endpoint Protection Mobile (SEP Mobile) con Intune. È necessario aggiungere app SEP Mobile in Azure AD per usufruire di funzionalità di accesso Single Sign-On.

## <a name="before-you-begin"></a>Prima di iniziare

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Account di Azure AD usato per l'integrazione di Intune e SEP Mobile

-   Prima di avviare la procedura di configurazione di base di SEP Mobile, verificare che l'account Azure AD sia configurato correttamente nella [console di gestione di Symantec Endpoint Protection Mobile](https://aad.skycure.com).
- L'account Azure AD deve essere un account amministratore globale per eseguire l'integrazione.
### <a name="network-setup"></a>Configurazione della rete

Per verificare che la rete sia configurata correttamente per l'integrazione con l'installazione di SEP Mobile, vedere l'articolo di Symantec [Setting up your network configuration](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016) (Impostazione della configurazione di rete).

### <a name="full-integration-vs-read-only"></a>Confronto tra integrazione completa e integrazione di sola lettura

SEP Mobile supporta due modalità di integrazione con Intune:

-   **Integrazione di sola lettura (configurazione di base)**: esegue solo l'inventario dei dispositivi da Azure Active Directory e li inserisce nella console di gestione di Symantec Endpoint Protection Mobile.
<br>
    -   Se le caselle **Report the health and risk of devices to Intune** (Segnala l'integrità e i rischi dei dispositivi a Intune) e **Also report security incidents to Intune** (Segnala anche gli eventi imprevisti per la sicurezza a Intune) non sono selezionate nella console di gestione di Symantec Endpoint Protection Mobile, l'integrazione è di sola lettura e quindi lo stato di un dispositivo (conforme o non conforme) rimarrà sempre invariato in Intune.
<br></br>
-   **Integrazione completa**: consente a SEP Mobile di segnalare a Intune i dettagli relativi ai rischi e agli eventi imprevisti per la sicurezza, creando così una comunicazione bidirezionale tra i due servizi cloud.

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>Uso delle app SEP Mobile con Azure AD e Intune

-   **App iOS**: consente agli utenti finali di accedere ad Azure AD usando un'app iOS.

-   **App Android**: consente agli utenti finali di accedere ad Azure AD usando un'app Android.

-   **App di gestione**: questa è l'app multi-tenant Azure AD SEP Mobile che consente le comunicazioni da servizio a servizio con Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>Per configurare l'integrazione di sola lettura tra Intune e SEP Mobile

> [!IMPORTANT]
> Le credenziali di amministratore di SEP Mobile devono essere costituite da un account di posta elettronica appartenente a un utente valido in Azure Active Directory, altrimenti il tentativo di accesso non riesce. SEP Mobile usa Azure Active Directory per autenticare l'amministratore con Single Sign-On (SSO).

1.  Andare alla [console di gestione di Symantec Endpoint Protection Mobile](https://aad.skycure.com).

2.  Immettere le **credenziali amministratore SEP Mobile** e quindi scegliere **Continue** (Continua).

3.  Scegliere **Settings** (Impostazioni) e in **Intune Integration** (Integrazione di Intune) scegliere **Basic Setup** (Configurazione di base).

4.  Accanto a **iOS App** (App iOS) scegliere **Add to Active Directory** (Aggiungi ad Active Directory).

    ![Immagine dell'app iOS nella [console di gestione di Symantec Endpoint Protection Mobile]](./media/symantec-portal-basic-add.png)

5.  Quando viene visualizzata la pagina di accesso, immettere le credenziali di Intune e quindi scegliere **Accept** (Accetto).

    ![Immagine del prompt di accesso a Intune dell'app iOS](./media/symantec-portal-basic-accept.png)

6.  Dopo avere aggiunto l'app in Azure AD, si noterà l'indicazione che l'app è stata aggiunta correttamente.

    ![Immagine della schermata di completamento dell'app iOS](./media/symantec-portal-basic-added.png)

7. Ripetere questi passaggi per le app **SEP Mobile Android** e **Management** (Gestione).

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>Aggiungere un gruppo di sicurezza di Azure AD in SEP Mobile

È necessario aggiungere un gruppo di sicurezza di Azure AD contenente tutti i dispositivi che eseguono SEP Mobile.

-  Immettere e selezionare tutti i gruppi di sicurezza dei dispositivi che eseguono SEP Mobile e quindi salvare le modifiche.

    ![Immagine che mostra i gruppi utenti per le app SEP Mobile](./media/symantec-portal-basic-groups.png)   

SEP Mobile sincronizza i dispositivi che eseguono il servizio Mobile Threat Defense con i gruppi di sicurezza di Azure AD.

![Immagine che illustra la configurazione dei gruppi di sicurezza completata nella console di gestione di SEP Mobile](./media/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>Per configurare l'integrazione completa tra Intune e SEP Mobile

### <a name="retrieve-the-directory-id-in-azure-ad"></a>Recuperare l'ID directory in Azure AD

1. Accedere al [portale di Azure](https://portal.azure.com).

2. Digitare "Active Directory" nella casella di ricerca e quindi selezionare **Azure Active Directory**.

3. Scegliere **Proprietà**.

4. Accanto all'**ID directory** scegliere l'icona Copia e quindi incollarlo in una posizione sicura. Questo identificatore sarà necessario in un passaggio successivo.

    ![Immagine che mostra l'ID directory nel portale di Azure](./media/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(Facoltativo) Creare un gruppo di sicurezza dedicato per i dispositivi che devono eseguire le app SEP Mobile
1. Nel [portale di Azure](https://portal.azure.com), in **Gestione** scegliere **Utenti e gruppi** e quindi scegliere **Tutti i gruppi**.

2. Fare clic sul pulsante **Aggiungi**. Digitare un **nome** di gruppo. Sotto **Tipo di appartenenza** scegliere **Assegnata**.

3. Nel pannello **Membri** selezionare i membri del gruppo e quindi scegliere il pulsante **Seleziona**.

4. Nel pannello **Gruppo** scegliere **Crea**.

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>Configurare l'integrazione tra Symantec Endpoint Protection Mobile e Intune

1.  Andare alla [console di gestione di Symantec Endpoint Protection Mobile](https://aad.skycure.com).

2.  Immettere le **credenziali amministratore SEP Mobile**, quindi scegliere **Continue** (Continua).

3.  Andare a **Settings** (Impostazioni) > **Integrations** (Integrazioni) > **Intune** > sezione **EMM Integration Selection** (Selezione integrazione EMM).

4. Nella casella **ID directory** incollare l'ID directory copiato da Azure Active Directory nella sezione precedente e salvare le impostazioni.

    ![Immagine che mostra l'ID directory nel portale di SEP Mobile](./media/symantec-portal-directory-ID.png)     

5. Andare a **Settings** (Impostazioni) > **Integrations** (Integrazioni) > **Intune** > sezione **Basic Setup** (Configurazione di base).

6. Accanto a **iOS App** (App iOS) scegliere il pulsante **Add to Active Directory** (Aggiungi ad Active Directory).

    ![Immagine che illustra l'aggiunta all'app iOS ad Active Directory](./media/symantec-portal-basic-add.png)   

7.  Accedere con le credenziali di Azure Active Directory per l'account Office 365 che gestisce la directory.

8.  Scegliere il pulsante **Accept** (Accetto) per aggiungere l'app SEP Mobile iOS ad Azure Active Directory.

    ![Immagine che mostra il pulsante Accept (Accetto)](./media/symantec-portal-basic-accept.png)     

9.  Ripetere lo stesso processo per l'**app Android** e l'**app di gestione**.

10. Selezionare tutti i gruppi utenti che devono eseguire le app SEP Mobile, ad esempio il gruppo di sicurezza creato in precedenza.

    ![Immagine che mostra i gruppi utenti per le app SEP Mobile](./media/symantec-portal-basic-groups.png)   

11.  SEP Mobile sincronizza i dispositivi nei gruppi selezionati e avvia la segnalazione delle informazioni a Intune. È possibile visualizzare questi dati nella sezione Full Integration (Integrazione completa). Andare a **Settings** (Impostazioni) > **Integrations** (Integrazioni) > **Intune** > sezione **Full Integration** (Integrazione completa).

     ![Immagine che illustra l'integrazione completa di SEP Mobile completata](media/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>Passaggi successivi

[Configurare le app SEP Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)
