## <a name="enable-windows-10-automatic-enrollment"></a>Abilitare la registrazione automatica di Windows 10

La registrazione automatica consente agli utenti di registrare dispositivi e PC di proprietà dell'azienda o personali Windows 10 e 10 Windows Mobile in Intune aggiungendo un account aziendale o dell'istituto di istruzione e accettandone la gestione. La procedura è molto semplice: in background, il dispositivo dell'utente si registra e unisce ad Azure Active Directory. Dopo la registrazione, il dispositivo viene gestito con Intune.

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

4. Configurare gli utenti che saranno registrati automaticamente.

  ![Schermata del portale di Azure](../media/auto-enroll-scope.png)

  Usare i valori predefiniti per gli URL seguenti:
  - **Registrazione MDM**
  - **Condizioni per l'utilizzo di MDM**
  - **Conformità MDM**

5. Specificare i dispositivi degli utenti che devono essere gestiti da Microsoft Intune. I dispositivi utente Windows 10 vengono registrati automaticamente per essere gestiti con Microsoft Intune.

  - **Tutti**
  - **Gruppi**
  - **Nessuno**

6. Selezionare **Salva**.
