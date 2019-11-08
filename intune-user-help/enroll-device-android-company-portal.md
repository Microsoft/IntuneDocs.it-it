---
title: Registrare un dispositivo Android in Portale aziendale Intune | Microsoft Docs
description: Descrive come registrare un dispositivo Android in Portale aziendale Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5baf0e9079cc148101a68e5cd2d3a4ed500f567f
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414819"
---
# <a name="enroll-your-device-with-company-portal"></a>Registrare il dispositivo in Portale aziendale  
Registrare il dispositivo Android personale o aziendale per ottenere accesso sicuro alla posta elettronica, alle app e ai dati aziendali. Il portale aziendale supporta i dispositivi Android, incluso Samsung Knox, che eseguono Android 4.4 e versioni successive.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox è un tipo di sicurezza che alcuni dispositivi Samsung usano per fornire protezione aggiuntiva oltre all'offerta prevista per i dispositivi Android nativi. Per determinare se il dispositivo è di tipo Samsung Knox, passare a **Impostazioni** > **Informazioni sul dispositivo**. Se non viene visualizzata l'indicazione **Versione Knox**, significa che il dispositivo è un dispositivo Android nativo.

## <a name="enroll-device"></a>Registrare il dispositivo  
Assicurarsi di [installare l'app Portale aziendale Intune gratuita da Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Durante la registrazione potrebbe essere richiesto di scegliere la categoria che descrive meglio come viene usato il dispositivo. Il team di supporto tecnico aziendale usa questa risposta per controllare le app a cui è possibile accedere.  

1. Aprire l'app Portale aziendale e accedere con l'account aziendale o dell'istituto di istruzione.  

2. Se viene richiesto di accettare i termini e le condizioni dell'organizzazione, toccare **ACCETTA TUTTO**.  

   ![Immagine di esempio della schermata Portale aziendale, termini, evidenziando il pulsante "accetta tutto".](./media/accept-terms-1911.png)  


3. Esaminare le informazioni che l'organizzazione può e non può visualizzare. Quindi toccare **CONTINUA**.


    ![Immagine di esempio di Portale aziendale, ci occupiamo della schermata sulla privacy, evidenziando il pulsante continue (continua).](./media/android-privacy-screen-1911.png)  
4. Vedere cosa aspettarsi nei prossimi passaggi. Quindi toccare **Avanti**.  

    ![Immagine di esempio di Portale aziendale, schermata successiva, che evidenzia il pulsante Avanti.](./media/android-whats-next-1911.png)  


5. A seconda della versione di Android, potrebbe essere richiesto di consentire l'accesso a determinate parti del dispositivo. Questi prompt sono necessari per Google e non sono controllati da Microsoft.  

    Toccare **Consenti** per le autorizzazioni seguenti:  
    * **Consenti a portale aziendale di effettuare e gestire chiamate telefoniche**: questa autorizzazione consente al dispositivo di condividere il numero IMEI (International Mobile Station Equipment Identity) con Intune, il provider di gestione dei dispositivi dell'organizzazione. È sicuro consentire questa autorizzazione. Microsoft non effettuerà né gestirà mai le chiamate telefoniche.  
    * **Consenti a portale aziendale di accedere ai tuoi contatti**: questa autorizzazione consente all'app portale aziendale di creare, usare e gestire l'account aziendale.  È sicuro consentire questa autorizzazione. Microsoft non accederà mai ai contatti. 

    Se si nega l'autorizzazione, al successivo accesso a Portale aziendale verrà richiesto di nuovo. Per disattivare i messaggi, selezionare **Non visualizzare più questo messaggio**. Per gestire le autorizzazioni dell'app, passare a impostazioni app **> app** > **Portale aziendale** > **autorizzazioni** > **telefono**.  

6. Attivare l'app amministratore del dispositivo. 

    Portale aziendale richiede le autorizzazioni di amministratore del dispositivo per gestire in modo sicuro il dispositivo. L'attivazione dell'app consente all'organizzazione di identificare i possibili problemi di sicurezza, ad esempio tentativi ripetuti non riusciti di sbloccare il dispositivo e rispondere in modo appropriato.  

    ![Immagine di esempio della schermata attiva amministratore del dispositivo, evidenziando il pulsante attiva.](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> Microsoft non controlla la messaggistica in questa schermata. È chiaro che la formulazione può sembrare un po' drastica. Portale aziendale non è in grado di specificare quali restrizioni e accesso sono rilevanti per l'organizzazione. In caso di domande sul modo in cui l'organizzazione usa l'app, contattare il personale di supporto IT. Visitare il [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per trovare le informazioni di contatto dell'organizzazione.  


7. Il dispositivo inizia la registrazione. Se si usa un dispositivo Samsung Knox, verrà richiesto di esaminare prima di tutto l'informativa sulla privacy dell'agente ELM.   

    ![Immagine di esempio della schermata di informativa sulla privacy di Samsung Knox visualizzata durante la registrazione.](./media/and-enroll-7-knox-privacy-policy.png)  

8. Nella schermata **configurazione dell'accesso aziendale** verificare che il dispositivo sia registrato. Quindi toccare **CONTINUA**.  

    ![Immagine di esempio di Portale aziendale, schermata di configurazione dell'accesso aziendale, che Mostra come ottenere la gestione del dispositivo è stata completata.](./media/update-settings-1911.png)  

9. Per l'organizzazione potrebbe essere necessario aggiornare le impostazioni del dispositivo. Toccare **Risolvi** per modificare un'impostazione. Al termine dell'aggiornamento delle impostazioni, toccare **continua**.  

   ![Immagine di esempio di Portale aziendale, aggiornare le impostazioni del dispositivo, evidenziare i pulsanti Risolvi e continua.](./media/resolve-settings-1911.png)  

10. Al termine dell'installazione, toccare **fine**.    

    ![Immagine di esempio di Portale aziendale, schermata di configurazione dell'accesso aziendale, che mostra il pulsante completato per l'installazione e l'evidenziazione.](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>Passaggi successivi  

Prima di provare a installare un'app School o di lavoro, passare a **impostazioni** > **sicurezza**e attivare **origini sconosciute**. Se non si attiva questa opzione, quando si tenta di installare un'app viene visualizzato il messaggio che indica che l'installazione è bloccata per motivi di sicurezza che impediscono di installare nel dispositivo app ottenute da origini sconosciute. È possibile toccare **Impostazioni** nel messaggio per passare direttamente a **origini sconosciute**.  

> [!Note]
> Se la propria organizzazione usa software per la gestione delle spese per telecomunicazioni, sarà necessario eseguire alcuni passaggi aggiuntivi prima che la registrazione del dispositivo sia completata. Per altre informazioni, vedere [qui](enroll-your-device-with-telecom-expense-management-android.md).

Se si verifica un errore durante la registrazione del dispositivo in Intune, è possibile [inviare un messaggio di posta elettronica al supporto tecnico aziendale](send-logs-to-your-it-admin-by-email-android.md).  

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  