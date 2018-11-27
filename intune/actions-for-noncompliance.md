---
title: Messaggio e azioni per i dispositivi non conformi con Microsoft Intune - Azure | Microsoft Docs
description: Creare un messaggio di posta elettronica di notifica da inviare ai dispositivi non conformi. Se un dispositivo viene contrassegnato come non conforme, è possibile aggiungere azioni, ad esempio un periodo di tolleranza al termine del quale il dispositivo deve essere conforme, o creare una pianificazione per bloccare l'accesso finché il dispositivo non è conforme. Queste operazioni possono essere eseguite con Microsoft Intune in Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5bd8bfe0230e4d49ce5ae4372e0f373a014c00ce
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187770"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi - Intune

La funzionalità **Azioni per la mancata conformità** consente di configurare una sequenza di azioni in ordine temporale. Queste azioni riguardano i dispositivi che non soddisfano i criteri di conformità. 

## <a name="overview"></a>Panoramica
Per impostazione predefinita, quando Intune rileva un dispositivo che non è conforme, lo contrassegna immediatamente come non conforme. Quindi l'[accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) di Azure Active Directory (AD) blocca il dispositivo. Quando un dispositivo non è conforme, le **azioni per la non conformità** offrono anche la flessibilità necessaria per decidere cosa fare. Ad esempio, si può decidere di non bloccare immediatamente il dispositivo e di concedere all'utente un periodo di tolleranza per adeguarsi ai criteri di conformità.

Sono disponibili diversi tipi di azioni:

- **Invia un messaggio di posta elettronica all'utente finale**: personalizzare il messaggio di posta elettronica di notifica prima di inviarlo all'utente finale. È possibile personalizzare i destinatari, l'oggetto e il corpo del messaggio, inclusi il logo aziendale e le informazioni di contatto.

    Intune include inoltre le informazioni sul dispositivo non conforme nella notifica di posta elettronica.

- **Blocca in remoto il dispositivo non conforme**: per i dispositivi non conformi, è possibile impostare un blocco remoto. All'utente viene quindi richiesto un PIN o una password per sbloccare il dispositivo. Sono disponibili altre informazioni sulla funzionalità [Blocco remoto](device-remote-lock.md). 

- **Contrassegnare il dispositivo come non conforme**: pianificare un numero di giorni trascorsi i quali il dispositivo viene contrassegnato come non conforme. È possibile configurare l'azione in modo che venga applicata immediatamente oppure concedere all'utente un periodo di tolleranza entro il quale dovrà adeguarsi ai criteri di conformità.

Questo articolo illustra come:

- Creare un modello di notifica tramite messaggio
- Creare un'azione per la non conformità, ad esempio l'invio di un messaggio di posta elettronica o il blocco remoto di un dispositivo


## <a name="before-you-begin"></a>Prima di iniziare

- Per configurare le azioni per la mancata conformità è necessario aver creato almeno un criterio di conformità dei dispositivi. Per creare criteri di conformità dei dispositivi, vedere le piattaforme seguenti:

  - [Android](compliance-policy-create-android.md)
  - [Profili di lavoro Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Per usare i criteri di conformità per impedire ai dispositivi di usare le risorse aziendali, è necessario aver configurato l'accesso condizionale di Azure AD. Vedere [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) o [Modi comuni per usare l'accesso condizionale con Intune](conditional-access-intune-common-ways-use.md) per informazioni aggiuntive.

## <a name="create-a-notification-message-template"></a>Creare un modello di messaggio di notifica

Per inviare il messaggio di posta elettronica agli utenti, creare un modello di messaggio di notifica. Quando un dispositivo risulta non conforme, i dettagli immessi nel modello vengono visualizzati nel messaggio di posta elettronica inviato agli utenti.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
2. Selezionare **Conformità del dispositivo** > **Notifiche**.
3. Selezionare **Crea la notifica**. Immettere le informazioni seguenti:

   - **Nome**
   - **Oggetto**
   - **Message**
   - **Intestazione del messaggio di posta elettronica: includere il logo dell'azienda**
   - **Piè di pagina del messaggio di posta elettronica: includere il nome dell'azienda**
   - **Piè di pagina del messaggio di posta elettronica: includere le informazioni sul contatto**

   ![Esempio di messaggio di notifica di Intune relativo alla conformità](./media/actionsfornoncompliance-1.PNG)

4. Dopo aver aggiunto le informazioni, scegliere **Crea**. Il modello di messaggio di notifica è pronto per l'uso. Si noti che il logo che si carica nell'ambito della personalizzazione del Portale aziendale verrà usato per i modelli di posta elettronica. Per altre informazioni sulla personalizzazione del Portale aziendale, vedere [Personalizzazione dell'identità aziendale](company-portal-app.md#company-identity-branding-customization).  

> [!NOTE]
> È anche possibile modificare un modello di notifica creato in precedenza.

## <a name="add-actions-for-noncompliance"></a>Aggiungere azioni per la mancata conformità

Quando si crea un criterio di conformità del dispositivo, Intune crea automaticamente un'azione per la non conformità. Quando un dispositivo non soddisfa i criteri di conformità, questa azione contrassegna il dispositivo come non conforme. È possibile personalizzare il periodo di tempo in cui il dispositivo rimane contrassegnato come non conforme. Questa azione non può essere rimossa.

È anche possibile aggiungere un'altra azione quando si crea un criterio di conformità o si aggiorna un criterio esistente. 

1. Nel [portale di Azure](https://portal.azure.com) aprire **Microsoft Intune** > **Conformità del dispositivo**.
2. Selezionare **Criteri**, scegliere uno dei criteri e quindi selezionare **Proprietà**. 

    Non esiste ancora un criterio? Creare un criterio per [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) o un'altra piattaforma.
  
    > [!NOTE]
    > Attualmente i dispositivi JAMF e i dispositivi selezionati con i gruppi di dispositivi non possono ricevere le azioni di conformità.

3. Selezionare **Azioni per la mancata conformità** > **Aggiungi**.
4. Selezionare l'**azione**: 

    - **Invia un messaggio di posta elettronica all'utente finale**: quando il dispositivo risulta non conforme, scegliere di inviare un messaggio di posta elettronica all'utente. Inoltre: 
    
         - Scegliere il **modello di messaggio** creato in precedenza
         - Immettere eventuali **destinatari aggiuntivi** selezionando i gruppi
    
    - **Blocca in remoto il dispositivo non conforme**: quando il dispositivo risulta non conforme, bloccarlo. In tal modo l'utente dovrà immettere un PIN o un passcode per sbloccare il dispositivo. 
    
    - **Pianifica**: immettere il numero di giorni (da 0 a 365) dal rilevamento della non conformità, dopo cui attivare l'azione nei dispositivi degli utenti. Dopo questo periodo di tolleranza, è possibile applicare un criterio di accesso condizionale. Se si immette **0** come numero di giorni, l'accesso condizionale viene applicato **immediatamente**. È ad esempio possibile bloccare immediatamente l'accesso alle risorse aziendali se un dispositivo risulta non conforme.

5. Al termine, selezionare **Aggiungi** > **OK** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi
[Monitorare l'attività di conformità del dispositivo](device-compliance-monitor.md).
