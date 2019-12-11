---
ms.openlocfilehash: 6f5b0c8df86cf5bf1206c1cccb879e37c7944a21
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71912785"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Abilitare la registrazione automatica di Windows 10

La registrazione automatica consente agli utenti di registrare i propri dispositivi Windows 10 in Intune. Per eseguire la registrazione, gli utenti aggiungono l'account aziendale ai propri dispositivi personali oppure aggiungono i dispositivi di proprietà dell'azienda ad Azure Active Directory. Il dispositivo esegue la registrazione e accede ad Azure Active Directory in background. Dopo la registrazione, il dispositivo viene gestito con Intune.

**Prerequisiti**

- Sottoscrizione di Azure Active Directory Premium ([sottoscrizione di prova](http://go.microsoft.com/fwlink/?LinkID=816845))
- Sottoscrizione di Microsoft Intune

### <a name="configure-automatic-mdm-enrollment"></a>Configurare la registrazione MDM automatica

1. Accedere al [portale di Azure](https://portal.azure.com) e selezionare **Azure Active Directory**.

   ![Schermata del portale di Azure](../enrollment/media/windows-enroll/auto-enroll-azure-main.png)

2. Selezionare **Servizi Mobility (MDM e MAM)** .

   ![Schermata del portale di Azure](../enrollment/media/windows-enroll/auto-enroll-mdm.png)

3. Selezionare **Microsoft Intune**.

   ![Schermata del portale di Azure](../enrollment/media/windows-enroll/auto-enroll-intune.png)

4. Configurare **Ambito utente MDM**. Specificare i dispositivi degli utenti che devono essere gestiti da Microsoft Intune. I dispositivi Windows 10 possono essere registrati automaticamente per la gestione con Microsoft Intune.

   - **Nessuno**: registrazione automatica MDM disabilitata
   - **Alcuni**: selezionare i **gruppi** che possono registrare automaticamente i dispositivi Windows 10
   - **Tutti**: tutti gli utenti possono registrare automaticamente i dispositivi Windows 10

      > [!IMPORTANT]
      > Per i dispositivi BYOD, l'ambito utente MAM ha la precedenza se sia l'ambito utente MAM che l'ambito utente MDM (registrazione MDM automatica) sono abilitati per tutti gli utenti o gli stessi gruppi di utenti. Il dispositivo userà i criteri di Windows Information Protection (WIP), se configurati, anziché essere registrato in MDM.
      >
      > Per i dispositivi aziendali, l'ambito utente MDM ha la precedenza se entrambi gli ambiti sono abilitati. I dispositivi vengono registrati in MDM.

   > [!NOTE]
   > L'ambito utente MDM deve essere impostato su un gruppo di Azure AD contenente oggetti utente.

   ![Schermata del portale di Azure](../enrollment/media/windows-enroll/auto-enroll-scope.png)

5. Usare i valori predefiniti per gli URL seguenti:
    - **URL delle condizioni per l'uso di MDM**
    - **URL individuazione MDM**
    - **URL conformità MDM**

6. Selezionare **Salva**.

Per impostazione predefinita, l'autenticazione a due fattori non è abilitata per il servizio. Tuttavia l'autenticazione a due fattori è consigliabile quando si registra un dispositivo. Per attivare l'autenticazione a due fattori, configurare un provider di autenticazione a due fattori in Azure AD e configurare gli account utente per l'autenticazione a più fattori. Vedere [Introduzione al server Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
