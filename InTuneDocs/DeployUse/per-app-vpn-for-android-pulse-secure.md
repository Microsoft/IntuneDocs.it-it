---
# required metadata

title: [Profilo VPN app per Android con Pulse Secure | Microsoft Intune]
description:
keywords:
author: [nbigman]
manager: [jeffgilb]
ms.date: 05/08/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: [ALIAS]
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Usare criteri personalizzati per creare un profilo VPN per app per dispositivi Android

È possibile creare un profilo VPN per app specifiche per i dispositivi Android gestiti da Intune. Prima si crea un profilo VPN che usa il tipo di connessione Pulse Secure, quindi si definiscono criteri di configurazione personalizzati per associare il profilo ad app specifiche. Dopo aver distribuito i criteri ai gruppi di utenti o dispositivi Android, quando si apre una delle app specificate su quei dispositivi viene attivata una connessione VPN per l'app. 

### Passaggio 1: Creare un profilo VPN

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** > **Aggiungi criterio**.
2. Selezionare un modello per il nuovo criterio espandendo **Android**, quindi scegliere **Profilo VPN (Android 4 e versioni successive)**.

3. Nel modello, in **Tipo di connessione** scegliere **Pulse Secure**.
4. Completare e salvare il profilo VPN. Per altri dettagli sui profili VPN vedere [Profili VPN](Help%20users%20connect%20to%20their%20work%20using%20VPN%20profiles%20with%20Microsoft%20Intune.md).

> [!NOTE]
Prendere nota del nome del profilo VPN per usarlo nel passaggio successivo. Ad esempio **MyAppVpnProfile**.
   
### Passaggio 2: Creare criteri di configurazione personalizzati
    
   1. Nella console di amministrazione di Intune scegliere **Criteri** -> **Aggiungi criterio** -> **Android** -> **Configurazione personalizzata** -> **Crea criterio**.
   2. Specificare un nome per il criterio.
   3. In **Impostazioni URI OMA** fare clic su **Aggiungi**.
   4. Specificare un nome per l'impostazione.
   5. In **Tipo di dati** specificare **Stringa**.
   6. In **URI OMA** specificare la seguente stringa: **./Vendor/MSFT/VPN/Profile/*nome*/PackageList** dove *nome* è il nome del profilo VPN annotato nel Passaggio 1. Con il nome di esempio, citato in precedenza la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   In **Valore** aggiungere un elenco separato da punti e virgola dei pacchetti che devono essere associati al profilo.  Ad esempio, se si vuole che Excel e il browser Google Chrome usino la connessione VPN digitare: **com.microsoft.office.excel;com.android.chrome**.
  

   ![Esempio di criteri personalizzati VPN per app Android](..\media\android_per_app_vpn_oma_uri.png) 
#### Impostare l'elenco di app come Blacklist o Whitelist (facoltativo)
È possibile specificare un elenco di app che *non* saranno autorizzate a usare la connessione VPN usando il valore **BLACKLIST**.  Tutte le app non incluse nell'elenco si connetteranno tramite VPN.

In alternativa è possibile specificare che *solo* determinate app potranno usare la connessione VPN usando il valore **WHITELIST**.
 

1.  In Impostazioni URI OMA fare clic su **Aggiungi**.
2.  Specificare un nome per l'impostazione.
3.  In **Tipo di dati** specificare **Stringa**.
4.  In **URI OMA** specificare la seguente stringa: **./Vendor/MSFT/VPN/Profile/*nome*/Mode** dove *nome* è il nome del profilo VPN annotato nel Passaggio 1. Con il nome di esempio citato in precedenza la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
5.  In **Valore** immettere **BLACKLIST** o **WHITELIST**. 


   
### Passaggio 3: Distribuire entrambi i criteri

È necessario distribuire *entrambi* i criteri agli *stessi* gruppi di Intune.

   1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**: selezionare uno o più gruppi in cui si vuole distribuire il criterio, quindi fare clic su **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuire il criterio**, fare clic su **Annulla**.

Un riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** consentono di identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene visualizzato anche nell'area di lavoro Dashboard.



<!--HONumber=May16_HO4-->


