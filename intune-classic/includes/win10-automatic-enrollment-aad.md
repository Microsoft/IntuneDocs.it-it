## <a name="enable-windows-10-automatic-enrollment"></a>Abilitare la registrazione automatica di Windows 10

La registrazione automatica consente agli utenti di registrare i propri dispositivi Windows 10 in Intune quando l'account aziendale viene aggiunto ai dispositivi di proprietà personale o quando i dispositivi di proprietà dell'azienda vengono aggiunti ad Azure Active Directory. in background, il dispositivo dell'utente si registra e unisce ad Azure Active Directory. Dopo la registrazione, il dispositivo viene gestito con Intune.

**Prerequisiti**
- Sottoscrizione di Azure Active Directory Premium ([sottoscrizione di prova](http://go.microsoft.com/fwlink/?LinkID=816845))
- Sottoscrizione di Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurare la registrazione MDM automatica

1. Accedere al [portale di gestione di Azure](https://portal.azure.com) (https://manage.windowsazure.com) e selezionare **Azure Active Directory**.

  ![Schermata del portale di Azure](../media/auto-enroll-azure-main.png)

2. Selezionare **Servizi Mobility (MDM e MAM)**.

  ![Schermata del portale di Azure](../media/auto-enroll-mdm.png)

3. Selezionare **Microsoft Intune**.

  ![Schermata del portale di Azure](../media/auto-enroll-intune.png)

4. Configurare **Ambito utente MDM**. Specificare i dispositivi degli utenti che devono essere gestiti da Microsoft Intune. I dispositivi utente Windows 10 vengono registrati automaticamente per essere gestiti con Microsoft Intune.

  - **Nessuno**
  - **Alcuni**
  - **Tutti**

 ![Schermata del portale di Azure](../media/auto-enroll-scope.png)

5. Usare i valori predefiniti per gli URL seguenti:
  - **URL delle condizioni per l'uso di MDM**
  - **URL individuazione MDM**
  - **URL conformità MDM**

6. Selezionare **Salva**.

Per impostazione predefinita, l'autenticazione a due fattori non è abilitata per il servizio. Tuttavia l'autenticazione a due fattori è consigliabile quando si registra un dispositivo. Prima di richiedere l'autenticazione a due fattori per questo servizio, è necessario configurare un provider di autenticazione a due fattori in Azure Active Directory e configurare gli account utente per l'autenticazione a più fattori. Vedere [Introduzione al server Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
