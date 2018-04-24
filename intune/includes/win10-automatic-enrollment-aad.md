## <a name="enable-windows-10-automatic-enrollment"></a>Abilitare la registrazione automatica di Windows 10

La registrazione automatica consente agli utenti di registrare i propri dispositivi Windows 10 in Intune. Per eseguire la registrazione, gli utenti aggiungono l'account aziendale ai propri dispositivi personali oppure aggiungono i dispositivi di proprietà dell'azienda ad Azure Active Directory. Il dispositivo esegue la registrazione e accede ad Azure Active Directory in background. Dopo la registrazione, il dispositivo viene gestito con Intune.

**Prerequisiti**
- Sottoscrizione di Azure Active Directory Premium ([sottoscrizione di prova](http://go.microsoft.com/fwlink/?LinkID=816845))
- Sottoscrizione di Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurare la registrazione MDM automatica

1. Accedere al [portale di Azure](https://portal.azure.com) e selezionare **Azure Active Directory**.

   ![Schermata del portale di Azure](../media/auto-enroll-azure-main.png)

2. Selezionare **Servizi Mobility (MDM e MAM)**.

   ![Schermata del portale di Azure](../media/auto-enroll-mdm.png)

3. Selezionare **Microsoft Intune**.

   ![Schermata del portale di Azure](../media/auto-enroll-intune.png)

4. Configurare **Ambito utente MDM**. Specificare i dispositivi degli utenti che devono essere gestiti da Microsoft Intune. I dispositivi Windows 10 possono essere registrati automaticamente per la gestione con Microsoft Intune.

   - **Nessuno**: registrazione automatica MDM disabilitata
   - **Alcuni**: selezionare i **gruppi** che possono registrare automaticamente i dispositivi Windows 10
   - **Tutti**: tutti gli utenti possono registrare automaticamente i dispositivi Windows 10

      > [!IMPORTANT]
      > Se per un gruppo sono attivati sia l'**ambito utente MAM** sia la registrazione automatica a MDM (**ambito utente MDM**), è attivato solo MAM. Per gli utenti di tale gruppo, quando il dispositivo personale viene registrato nell'area di lavoro viene aggiunto solo MAM. I dispositivi non vengono registrati automaticamente con MDM.

   ![Schermata del portale di Azure](../media/auto-enroll-scope.png)

5. Usare i valori predefiniti per gli URL seguenti:
    - **URL delle condizioni per l'uso di MDM**
    - **URL individuazione MDM**
    - **URL conformità MDM**

6. Selezionare **Salva**.

Per impostazione predefinita, l'autenticazione a due fattori non è abilitata per il servizio. Tuttavia l'autenticazione a due fattori è consigliabile quando si registra un dispositivo. Per attivare l'autenticazione a due fattori, configurare un provider di autenticazione a due fattori in Azure AD e configurare gli account utente per l'autenticazione a più fattori. Vedere [Introduzione al server Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
