---
title: Guida introduttiva - Inviare notifiche a dispositivi non conformi
titleSuffix: Microsoft Intune
description: In questa guida introduttiva si userà Microsoft Intune per inviare notifiche via posta elettronica ai dispositivi non conformi.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6d89cfcafd5452b990509e0fa6fd431a614ee5c1
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410226"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Guida introduttiva: Inviare notifiche a dispositivi non conformi

In questa guida introduttiva si userà Microsoft Intune per l'invio di notifiche di posta elettronica ai membri della forza lavoro che hanno dispositivi non conformi.

Per impostazione predefinita, quando Intune rileva un dispositivo che non è conforme, lo contrassegna immediatamente come non conforme. Quindi l'[accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) di Azure Active Directory (Azure AD) blocca il dispositivo. Quando un dispositivo non è conforme, Intune consente di aggiungere azioni per la non conformità offrendo la flessibilità necessaria per decidere cosa fare. Ad esempio, è possibile concedere agli utenti un periodo di tolleranza per diventare conformi prima di bloccare i dispositivi non conformi.

Un'azione da intraprendere quando un dispositivo non soddisfa la conformità è inviare un messaggio di posta elettronica all'utente dei dispositivi. È anche possibile personalizzare la notifica di posta elettronica prima di inviarla. In particolare, è possibile personalizzare i destinatari, l'oggetto e il corpo del messaggio, inclusi il logo aziendale e le informazioni di contatto. Intune inserisce nella notifica di posta elettronica anche i dettagli sul dispositivo non conforme.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti

Per usare i criteri di conformità per impedire ai dispositivi di usare le risorse aziendali, è necessario aver configurato l'accesso condizionale di Azure AD. Se sono state eseguite le procedure descritte nella guida introduttiva [Creare criteri di conformità dei dispositivi](quickstart-set-password-length-android.md), si sta usando Azure Active Directory. Per altre informazioni su Azure AD, vedere [Che cos'è l'accesso condizionale in Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) e [Quali sono i modi comuni per usare l'accesso condizionale con Intune?](../protect/conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) come [Amministratore globale](../fundamentals/users-add.md#types-of-administrators) o come [Amministratore del servizio](../fundamentals/users-add.md#types-of-administrators) Intune. Se è stata creata una sottoscrizione di valutazione di Intune, l'account con cui è stata creata la sottoscrizione sarà l'amministratore globale.

## <a name="create-a-notification-message-template"></a>Creare un modello di messaggio di notifica

Per inviare il messaggio di posta elettronica agli utenti, creare un modello di messaggio di notifica. Quando un dispositivo risulta non conforme, i dettagli immessi nel modello vengono visualizzati nel messaggio di posta elettronica inviato agli utenti.

1. In Intune selezionare **Dispositivi** > **Criteri di conformità** > **Notifiche** > **Crea notifica**.
2. Immettere le informazioni seguenti:

   - **Nome**: *Amministratore Contoso*
   - **Oggetto**: *Conformità dei dispositivi*
   - **Messaggio**: *Il dispositivo attualmente non rispetta i requisiti di conformità dell'organizzazione.*
   - **Intestazione del messaggio di posta elettronica: includere il logo dell'azienda**: impostare su **Abilitato** per visualizzare il logo dell'organizzazione.
   - **Piè di pagina del messaggio di posta elettronica: includere il nome dell'azienda**: impostare su **Abilitato** per visualizzare il nome dell'organizzazione.
   - **Piè di pagina del messaggio di posta elettronica: includere le informazioni sul contatto**: impostare su **Abilitato** per visualizzare le informazioni sul contatto dell'organizzazione.

   ![Esempio di messaggio di notifica di Intune relativo alla conformità](./media/quickstart-send-notification/quickstart-send-notification-01.png)

3. Selezionare **Avanti** ed esaminare la notifica. Selezionare **Crea** e il modello di messaggio di notifica è pronto per l'uso.

   > [!NOTE]
   > È anche possibile modificare un modello di notifica creato in precedenza.

Per informazioni dettagliate sull'impostazione di nome della società, informazioni di contatto della società e logo della società, vedere gli articoli seguenti:

- [Informazioni e informativa sulla privacy della società](../apps/company-portal-app.md#company-information-and-privacy-statement)
- [Informazioni di supporto](../apps/company-portal-app.md#support-information)
- [Personalizzazione del branding dell'identità aziendale](../apps/company-portal-app.md#company-identity-branding-customization).

## <a name="add-a-noncompliance-policy"></a>Aggiungere un criterio di non conformità

Quando si crea un criterio di conformità del dispositivo, Intune crea automaticamente un'azione per la non conformità. Intune contrassegna quindi i dispositivi come non conformi quando non soddisfano i criteri di conformità. È possibile personalizzare il periodo di tempo in cui il dispositivo rimane contrassegnato come non conforme. È anche possibile aggiungere un'altra azione quando si crea un criterio di conformità o si aggiorna un criterio di conformità esistente.

La procedura seguente consente di creare un criterio di conformità per i dispositivi Windows 10.

1. In Intune, selezionare **Dispositivi** > **Criteri di conformità** > **Crea criterio**.

2. Immettere le informazioni seguenti:

   - **Nome**: *Conformità di Windows 10*
   - **Description**: *Criteri di conformità di Windows 10*
   - **Piattaforma**: Windows 10 e versioni successive

3. Selezionare **Impostazioni** > **Sicurezza del sistema** per visualizzare le impostazioni correlate alla sicurezza dei dispositivi.

4. Configurare le opzioni seguenti:

   - Impostare **Richiedi una password per sbloccare i dispositivi mobili** su **Rendi obbligatorio**. Questa impostazione specifica se richiedere agli utenti di immettere una password per poter accedere alle informazioni sui dispositivi mobili.

   - Impostare **Lunghezza minima password** su **6**. Questa impostazione specifica il numero minimo di cifre e caratteri nella password.

   ![Impostazioni di sicurezza del sistema per un nuovo criterio di conformità](./media/quickstart-send-notification/system-security-settings-01.png)

5. Selezionare **OK** > **OK** > **Crea** per creare i criteri di conformità.

6. Selezionare **Proprietà** > **Azioni per la non conformità** > **Aggiungi**.

7. Nella casella a discesa **Azione** verificare che sia selezionata l'opzione **Invia un messaggio di posta elettronica all'utente finale**.

8. Selezionare **Modello di messaggio**, il modello creato in precedenza in questo articolo e quindi **Seleziona** per selezionare il modello di messaggio.

9. Selezionare **Aggiungi** > **OK** > **Salva** per salvare le modifiche.

## <a name="assign-the-policy"></a>Assegnare i criteri

È possibile assegnare i criteri di conformità a un gruppo specifico di utenti o a tutti gli utenti. Quando Intune rileva che un dispositivo non è conforme, all'utente viene inviata una notifica che richiede l'aggiornamento del dispositivo per soddisfare i criteri di conformità. Usare la procedura seguente per assegnare i criteri.

1. In Intune passare a **Dispositivi** > **Criteri di conformità** e selezionare i criteri di **conformità di Windows 10** creati in precedenza.

2. Selezionare **Assegnazioni**.

3. Nella casella a discesa **Assegna a** selezionare **Tutti gli utenti**. Verranno selezionati tutti gli utenti. La notifica verrà inviata a tutti gli utenti con un dispositivo **Windows 10 e versioni successive** che non soddisfa il criterio di conformità.

    > [!NOTE]
    > Durante l'assegnazione dei criteri di conformità è possibile includere ed escludere gruppi.

4. Fare clic su **Save**.

Dopo la creazione e il salvataggio, i criteri vengono visualizzati nell'elenco **Criteri di conformità - Criteri**. Si noti che nell'elenco l'opzione **Assegnato** è impostata su **Sì**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato usato Intune per creare e assegnare un criterio di conformità per i dispositivi Windows 10 della forza lavoro per richiedere una password di almeno sei caratteri. Per altre informazioni sulla creazione dei criteri di conformità per i dispositivi Windows, vedere [Aggiungere i criteri di conformità per i dispositivi Windows in Intune](compliance-policy-create-windows.md).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Avvio rapido: Aggiungere e assegnare un'app client](../apps/quickstart-add-assign-app.md)
