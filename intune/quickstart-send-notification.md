---
title: Guida introduttiva - Inviare notifiche a dispositivi non conformi
titlesuffix: Microsoft Intune
description: In questa guida introduttiva si userà Microsoft Intune per inviare notifiche tramite posta elettronica ai dispositivi non conformi.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/09/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1b89f2d-7937-46bb-926b-b05f6fa9c749
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e76e173bef7a370f89f60f6c9eb4588bb63aefdc
ms.sourcegitcommit: 4c4e87cb0d8906085fcb7cdd170bd6b0cfeb23ff
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2018
ms.locfileid: "51510908"
---
# <a name="quickstart-send-notifications-to-noncompliant-devices"></a>Guida introduttiva: Inviare notifiche a dispositivi non conformi

In questa guida introduttiva si userà Microsoft Intune per l'invio di notifiche di posta elettronica ai membri della forza lavoro che hanno dispositivi non conformi.

Per impostazione predefinita, quando Intune rileva un dispositivo che non è conforme, lo contrassegna immediatamente come non conforme. Quindi l'[accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) di Azure Active Directory (AAD) blocca il dispositivo. Quando un dispositivo non è conforme, Intune consente di aggiungere azioni per la non conformità offrendo la flessibilità necessaria per decidere cosa fare. Ad esempio, è possibile concedere agli utenti un periodo di tolleranza per diventare conformi prima di bloccare i dispositivi non conformi.

Una delle azioni che è possibile eseguire in caso di dispositivi non conformi consiste nell'inviare un messaggio di posta elettronica agli utenti finali. È anche possibile personalizzare la notifica di posta elettronica prima di inviarla all'utente finale. In particolare, è possibile personalizzare i destinatari, l'oggetto e il corpo del messaggio, inclusi il logo aziendale e le informazioni di contatto. Intune inserisce nella notifica di posta elettronica anche i dettagli sul dispositivo non conforme.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
- Quando si usano i criteri di conformità dei dispositivi per bloccare i dispositivi delle risorse aziendali è necessario impostare l'accesso condizionale di Azure AD. Se sono state eseguite le procedure descritte nella guida introduttiva [Creare criteri di conformità dei dispositivi](quickstart-set-password-length-android.md) si sta usando Azure Active Directory. Per altre informazioni su Azure AD, vedere [Che cos'è l'accesso condizionale in Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) e [Quali sono i modi comuni per usare l'accesso condizionale con Intune?](conditional-access-intune-common-ways-use.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere al portale di [Intune](https://aka.ms/intuneportal) come [Amministratore globale](users-add.md#types-of-administrators) o come [Amministratore servizio](users-add.md#types-of-administrators) di Intune. 

## <a name="create-a-notification-message-template"></a>Creare un modello di messaggio di notifica

Per inviare il messaggio di posta elettronica agli utenti, creare un modello di messaggio di notifica. Quando un dispositivo risulta non conforme, i dettagli immessi nel modello vengono visualizzati nel messaggio di posta elettronica inviato agli utenti.

1. In Intune selezionare **Conformità del dispositivo** > **Notifiche** > **Crea la notifica**. 
2. Immettere le informazioni seguenti:

   - **Nome**: *Amministratore Contoso*
   - **Oggetto**: *Conformità del dispositivo*
   - **Messaggio**: *Il dispositivo attualmente non rispetta i requisiti di conformità delle organizzazioni.*
   - **Piè di pagina del messaggio di posta elettronica - Includere il logo dell'azienda**: impostare su **Abilitato** per visualizzare il logo dell'organizzazione.
   - **Piè di pagina del messaggio di posta elettronica - Includere il nome dell'azienda**: impostare su **Abilitato** per visualizzare il nome dell'organizzazione.
   - **Piè di pagina del messaggio di posta elettronica - Includere le informazioni sul contatto**: impostare su **Abilitato** per visualizzare le informazioni di contatto dell'organizzazione.

   ![Esempio di messaggio di notifica di Intune relativo alla conformità](./media/quickstart-send-notification-01.png)

3. Dopo aver aggiunto le informazioni, scegliere **Crea**. Il modello di messaggio di notifica è pronto per l'uso.

    > [!NOTE]
    > È anche possibile modificare un modello di notifica creato in precedenza.

Per informazioni dettagliate sull'impostazione del nome della società, delle informazioni di contatto e del logo aziendale, vedere [Informazioni e informativa sulla privacy della società](company-portal-app.md#company-information-and-privacy-statement), [Informazioni di supporto](company-portal-app.md#support-information) e [Personalizzazione del branding dell'identità aziendale](company-portal-app.md#company-identity-branding-customization). 

## <a name="add-a-noncompliance-policy"></a>Aggiungere un criterio di non conformità

Quando si crea un criterio di conformità del dispositivo, Intune crea automaticamente un'azione per la non conformità. Quando un dispositivo non soddisfa i criteri di conformità, Intune contrassegna automaticamente il dispositivo come non conforme. È possibile personalizzare il periodo di tempo in cui il dispositivo rimane contrassegnato come non conforme. È anche possibile aggiungere un'altra azione quando si crea un criterio di conformità o si aggiorna un criterio di conformità esistente. 

La procedura seguente consente di creare un criterio di conformità per i dispositivi Windows 10.

1. In Intune selezionare **Conformità del dispositivo**.
2. Selezionare **Criteri** > **Crea criterio**.
3. Immettere le informazioni seguenti:

   - **Nome**: *Conformità di Windows 10*
   - **Descrizione**: *Criteri di conformità di Windows 10*
   - **Piattaforma**: Windows 10 e versioni successive

4. Selezionare **Impostazioni** > **Sicurezza del sistema** per visualizzare le impostazioni correlate alla sicurezza dei dispositivi.
5. Impostare **Richiedi una password per sbloccare i dispositivi mobili** su **Rendi obbligatorio**. Questa impostazione specifica se richiedere agli utenti di immettere una password per poter accedere alle informazioni sui dispositivi mobili. 
6. Impostare **Lunghezza minima password** su **6**. Questa impostazione specifica il numero minimo di cifre e caratteri nella password.

    ![Impostazioni di sicurezza del sistema per un nuovo criterio di conformità](./media/quickstart-send-notification-02.png) 

7. Fare clic su **OK**, **OK** e **Crea** per creare il criterio di conformità.
8. Selezionare il nome del nuovo criterio: **Conformità di Windows 10**.
9. Selezionare **Proprietà** > **Azioni per la non conformità** > **Aggiungi**.
10. Nella casella a discesa **Azione** verificare che sia selezionata l'opzione **Invia un messaggio di posta elettronica all'utente finale**.
11. Selezionare **Modello di messaggio** > **Amministratore Contoso** > **Seleziona** per selezionare il modello di messaggio creato in precedenza in questo argomento.
12. Selezionare **OK** > **OK** > **Salva** per salvare le modifiche.

## <a name="assign-the-policy"></a>Assegnare i criteri

È possibile assegnare i criteri di conformità a un gruppo specifico di utenti o a tutti gli utenti. Quando Intune rileva che un dispositivo non è conforme, all'utente viene inviata una notifica che richiede l'aggiornamento del dispositivo per soddisfare i criteri di conformità. La procedura seguente consente di assegnare i criteri.

1. Selezionare il criterio **Conformità di Windows 10** creato in precedenza.
2. Selezionare **Assegnazioni**.
3. Nella casella a discesa **Assegna a** selezionare **Tutti gli utenti**. Verranno selezionati tutti gli utenti. La notifica verrà inviata a tutti gli utenti con un dispositivo **Windows 10 e versioni successive** che non soddisfa il criterio di conformità.

    > [!NOTE]
    > Durante l'assegnazione dei criteri di conformità è possibile includere ed escludere gruppi.

4. Fare clic su **Salva**.

Dopo averlo creato e salvato, il criterio apparirà nell'elenco **Conformità del dispositivo - Criteri**. Si noti che nell'elenco l'opzione **Assegnato** è impostata su **Sì**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato usato Intune per creare e assegnare un criterio di conformità per i dispositivi Windows 10 della forza lavoro per richiedere una password di almeno sei caratteri. Per altre informazioni sulla creazione dei criteri di conformità per i dispositivi Windows, vedere [Aggiungere i criteri di conformità per i dispositivi Windows in Intune](compliance-policy-create-windows.md).

Per seguire questa serie di guide introduttive di Intune, continuare con la guida introduttiva che segue.

> [!div class="nextstepaction"]
> [Guida introduttiva: Aggiungere e assegnare un'app client](quickstart-add-assign-app.md)
