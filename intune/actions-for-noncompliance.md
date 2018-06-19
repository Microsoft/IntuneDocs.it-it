---
title: Messaggio e azioni per i dispositivi non conformi con Microsoft Intune - Azure | Microsoft Docs
description: Creare un messaggio di posta elettronica di notifica da inviare ai dispositivi non conformi. Se un dispositivo viene contrassegnato come non conforme, è possibile aggiungere azioni, ad esempio un periodo di tolleranza al termine del quale il dispositivo deve essere conforme, o creare una pianificazione per bloccare l'accesso finché il dispositivo non è conforme. Queste operazioni possono essere eseguite con Microsoft Intune in Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8e8603ca59b46937b1529e710a8bc83aec5dd4d6
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2018
ms.locfileid: "32017958"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi - Intune

La funzionalità **Azioni per la mancata conformità** consente di configurare una sequenza di azioni in ordine temporale. Queste azioni riguardano i dispositivi che non soddisfano i criteri di conformità. 

## <a name="overview"></a>Panoramica
Per impostazione predefinita, quando Intune rileva un dispositivo che non è conforme, lo contrassegna immediatamente come non conforme. Quindi l'[accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) di Azure Active Directory (AD) blocca il dispositivo. Quando un dispositivo non è conforme, le **azioni per la non conformità** offrono anche la flessibilità necessaria per decidere cosa fare. Ad esempio, si può decidere di non bloccare immediatamente il dispositivo e di concedere all'utente un periodo di tolleranza per adeguarsi ai criteri di conformità.

Esistono due tipi di azioni:

- **Notifica via posta elettronica agli utenti finali**: personalizzare il messaggio di posta elettronica di notifica prima di inviarlo all'utente finale. È possibile personalizzare i destinatari, l'oggetto e il corpo del messaggio, inclusi il logo aziendale e le informazioni di contatto.

    Intune include inoltre le informazioni sul dispositivo non conforme nella notifica di posta elettronica.

- **Contrassegnare il dispositivo come non conforme**: pianificare un numero di giorni trascorsi i quali il dispositivo viene contrassegnato come non conforme. È possibile configurare l'azione in modo che venga applicata immediatamente oppure concedere all'utente un periodo di tolleranza entro il quale dovrà adeguarsi ai criteri di conformità.

## <a name="before-you-begin"></a>Prima di iniziare

- Per configurare le azioni per la mancata conformità è necessario aver creato almeno un criterio di conformità dei dispositivi. Per creare criteri di conformità dei dispositivi, vedere le piattaforme seguenti:

  - [Android](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Per usare i criteri di conformità per impedire ai dispositivi di usare le risorse aziendali, è necessario aver configurato l'accesso condizionale di Azure AD. Per le indicazioni, vedere [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

- Deve essere creato un modello di messaggio di notifica. Per inviare messaggi di posta elettronica agli utenti, usare questo modello per creare azioni per la non conformità.

## <a name="create-a-notification-message-template"></a>Creare un modello di messaggio di notifica

1. Accedere al [portale di Azure](https://portal.azure.com) con le credenziali di Intune. 
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Conformità del dispositivo**, quindi **Notifiche**. 
4. Selezionare **Crea la notifica** e quindi immettere le informazioni seguenti:

   - Name
   - Subject
   - Messaggio
   - Intestazione del messaggio di posta elettronica: includere il logo dell'azienda
   - Piè di pagina del messaggio di posta elettronica: includere il nome dell'azienda
   - Piè di pagina del messaggio di posta elettronica: includere le informazioni sul contatto

   ![Esempio di messaggio di notifica di Intune relativo alla conformità](./media/actionsfornoncompliance-1.PNG)

Dopo aver aggiunto le informazioni, scegliere **Crea**. Il modello di messaggio di notifica è pronto per l'uso.

> [!NOTE]
> È anche possibile modificare un modello di notifica creato in precedenza.

## <a name="add-actions-for-noncompliance"></a>Aggiungere azioni per la mancata conformità

Per impostazione predefinita, Intune crea automaticamente un'azione in caso di mancata conformità. Quando un dispositivo non soddisfa i criteri di conformità, questa azione contrassegna il dispositivo come non conforme. È possibile personalizzare il periodo di tempo in cui il dispositivo rimane contrassegnato come non conforme. Questa azione non può essere rimossa.

È possibile aggiungere un'azione quando si crea un nuovo criterio di conformità o si aggiorna un criterio esistente. 

1. Nel [portale di Azure](https://portal.azure.com) aprire **Microsoft Intune** e selezionare **Conformità del dispositivo**.
2. Selezionare **Criteri**, scegliere uno dei criteri e quindi selezionare **Proprietà**. 

  Non esiste ancora un criterio? Creare un criterio per [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) o un'altra piattaforma.
  
  > [!NOTE]
  > Attualmente i dispositivi JAMF e i dispositivi selezionati con i gruppi di dispositivi non possono ricevere le azioni di conformità.

3. Selezionare **Azioni per la mancata conformità**, quindi selezionare **Aggiungi** per immettere i parametri dell'azione. È possibile scegliere il modello di messaggio creato in precedenza, aggiungere altri destinatari e aggiornare la pianificazione del periodo di tolleranza. È possibile indicare il numero di giorni (da 0 a 365) nella pianificazione, quindi applicare i criteri di accesso condizionale. Se si immette **0** come numero di giorni, l'accesso condizionale blocca **immediatamente** l'accesso alle risorse aziendali.

4. Al termine, selezionare **Aggiungi** > **OK** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi
Monitorare l'attività di conformità del dispositivo eseguendo i report. Alcune indicazioni sono contenute in [Come monitorare la conformità dei dispositivi in Intune](device-compliance-monitor.md).
