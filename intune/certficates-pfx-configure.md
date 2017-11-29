---
title: Configurare e gestire i certificati PKCS con Intune
titleSuffix: Intune on Azure
description: Configurare e assegnare certificati PKCS con Intune."
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: angrobe
ms.date: 11/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 105b5fc73bc537eaca67a0e6943701ba25a53972
ms.sourcegitcommit: 2b35c99ca7d3dbafe2dfe1e0b9de29573db403b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2017
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Configurare e gestire i certificati PKCS con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="requirements"></a>Requisiti

Per usare i certificati PKCS con Intune, è necessario avere l'infrastruttura seguente:

* Un dominio Active Directory Domain Services (AD DS) esistente configurato.
 
  Se sono necessarie altre informazioni su come installare e configurare AD DS, vedere l'articolo [Pianificazione e progettazione di Servizi di dominio Active Directory](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

* Un'autorità di certificazione (CA) globale (enterprise) esistente configurata.

  Se sono necessarie altre informazioni su come installare e configurare Servizi certificati Active Directory (AD CS), vedere l'articolo [Guida dettagliata di Servizi certificati Active Directory di Windows Server](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune richiede l'esecuzione di Servizi certificati Active Directory con un'autorità di certificazione globale (enterprise), non con un'autorità di certificazione autonoma (Standalone).

* Un client con connettività all'autorità di certificazione globale (enterprise).
* Una copia del certificato radice esportato dall'autorità di certificazione globale (enterprise).
* Il connettore di certificati di Microsoft Intune (NDESConnectorSetup.exe) scaricato dal portale di Intune.
* Un server Windows disponibile per ospitare il connettore di certificati di Microsoft Intune (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Esportare il certificato radice dall'autorità di certificazione globale (enterprise)

Per ogni dispositivo è necessario un certificato CA radice o intermedio per l'autenticazione con VPN, WiFi e altre risorse. La procedura seguente illustra come ottenere il certificato richiesto dall'autorità di certificazione globale (enterprise).

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire un prompt dei comandi come amministratore.
3. Esportare il certificato CA radice in un percorso a cui è possibile accedere in un secondo momento.

   Ad esempio:

   `certutil -ca.cert certnew.cer`

   Per altre informazioni, vedere [Operazioni certutil per la gestione dei certificati](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).


## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurare i modelli di certificato nell'autorità di certificazione

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire la console **Autorità di certificazione**.
3. Fare clic con il pulsante destro del mouse su **Modelli di certificato** e scegliere **Gestisci**.
4. Individuare il modello di certificato **User**, fare clic con il pulsante destro del mouse su di esso e scegliere **Duplica modello**. Viene visualizzata la finestra **Proprietà nuovo modello**.
5. Nella scheda **Compatibilità**
   * Impostare **Autorità di certificazione** su **Windows Server 2008 R2**
   * Impostare **Destinatario certificato** su **Windows 7 / Server 2008 R2**
6. Fare clic sulla scheda **Generale** :
   * Impostare **Nome visualizzato modello** su un valore significativo.

   > [!WARNING]
   > Per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*. Prendere nota del nome del modello per un uso successivo.

7. Nella scheda **Gestione richieste** selezionare la casella **Rendi la chiave privata esportabile**.
8. Nella scheda **Crittografia** verificare che il campo **Dimensioni minime chiave** sia impostato su 2048.
9. Nella scheda **Nome soggetto** scegliere il pulsante di opzione **Inserisci nella richiesta**.
10. Nella scheda **Estensioni** assicurarsi che nell'area **Criteri di applicazione** siano presenti Crittografia file system, Posta elettronica sicura e Autenticazione client.
    
      > [!IMPORTANT]
      > Per i modelli di certificato iOS e macOS, nella scheda **Estensioni** modificare **Utilizzo chiavi** e verificare che l'opzione **Firma come prova dell'origine** non sia selezionata.

11. Nella scheda **Sicurezza** aggiungere l'account computer relativo al server in cui si installa il connettore di certificati di Microsoft Intune.
    * Assegnare all'account le autorizzazioni **Lettura** e **Registrazione**.
12. Fare clic su **Applica** e quindi su **OK** per salvare il modello di certificato.
13. Chiudere la **Console dei modelli di certificato**.
14. Nella console **Autorità di certificazione** fare clic con il pulsante destro del mouse su **Modelli di certificato**, **Nuovo** e **Modello di certificato da rilasciare**.
    * Scegliere il modello creato nei passaggi precedenti e fare clic su **OK**.
15. Per consentire al server di gestire i certificati per conto di utenti e dispositivi registrati in Intune, seguire questa procedura:

    a. Fare clic con il pulsante destro del mouse sull'autorità di certificazione e scegliere **Proprietà**.

    b. Nella scheda della sicurezza aggiungere l'account computer relativo al server in cui è in esecuzione il connettore di certificati di Microsoft Intune.
      * Assegnare all'account le autorizzazioni **Rilascio e gestione certificati** e **Richiesta certificati**.
16. Disconnettersi dall'autorità di certificazione globale (enterprise).

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Scaricare, installare e configurare il connettore di certificati di Microsoft Intune

![ConnectorDownload][ConnectorDownload]

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Passare a **Intune**, **Configurazione del dispositivo**, **Autorità di certificazione** e fare clic su **Scarica il connettore del certificato**.
   * Salvare il file scaricato in un percorso a cui è possibile accedere dal server in cui verrà installato.
3. Accedere al server in cui verrà installato il connettore di certificati di Microsoft Intune.
4. Eseguire il programma di installazione e accettare il percorso predefinito. Il connettore viene installato in C:\Programmi\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.

      a. Nella pagina delle opzioni del programma di installazione scegliere **Distribuzione PFX** e fare clic su **Avanti**.

   b. Fare clic su **Installa** e attendere il completamento dell'installazione.

   c. Nella pagina di completamento selezionare la casella **Avvia Intune Connector** e fare clic su **Fine**.

5. La finestra di NDES Connector viene aperta sulla scheda **Registrazione**. Per abilitare la connessione a Intune, è necessario fare clic su **Accedi** e specificare un account con autorizzazioni amministrative.
6. Nella scheda **Avanzate** è possibile lasciare selezionato il pulsante di opzione **Usa l'account di sistema del computer (impostazione predefinita)**.
7. Fare clic su **Applica** e quindi su **Chiudi**.
8. Tornare al portale di Azure. Dopo alcuni minuti, in **Intune**, **Configurazione del dispositivo**, **Autorità di certificazione** verrà visualizzato un segno di spunta verde e apparirà il termine **Attivo** nell'area **Stato di connessione**. In questo modo si ha la conferma che il server connettore può comunicare con Intune.

## <a name="create-a-device-configuration-profile"></a>Creare un profilo di configurazione del dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Passare a **Intune**, **Configurazione del dispositivo**, **Profili** e fare clic su **Crea profilo**.

   ![NavigateIntune][NavigateIntune]

3. Specificare le informazioni seguenti:
   * **Nome** del profilo
   * Inserire eventualmente una descrizione
   * **Piattaforma** in cui distribuire il profilo
   * Impostare **Tipo di profilo** su **Certificato attendibile**
4. Passare a **Impostazioni** e fornire il file con estensione cer del certificato CA radice esportato in precedenza.

   > [!NOTE]
   > A seconda della piattaforma selezionata in **Passaggio 3**, può essere possibile scegliere l'**Archivio di destinazione** del certificato.

   ![ProfileSettings][ProfileSettings]

5. Fare clic su **OK** e quindi su **Crea** per salvare il profilo.
6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Passare a **Intune**, **Configurazione del dispositivo**, **Profili** e fare clic su **Crea profilo**.
3. Specificare le informazioni seguenti:
   * **Nome** del profilo
   * Inserire eventualmente una descrizione
   * **Piattaforma** in cui distribuire il profilo
   * Impostare **Tipo di profilo** su **Certificato PKCS**
4. Passare a **Impostazioni** e specificare le informazioni seguenti:
   * **Soglia di rinnovo (%)**: il valore consigliato è 20%.
   * **Periodo di validità del certificato**: se il modello di certificato non è stato cambiato, questa opzione deve essere impostata su un anno.
   * **Autorità di certificazione**: questa opzione corrisponde al nome di dominio completo interno dell'autorità di certificazione globale (enterprise).
   * **Nome dell'autorità di certificazione**: questa opzione corrisponde al nome dell'autorità di certificazione globale (enterprise) e può essere diversa rispetto al valore precedente.
   * **Nome del modello di certificato**: questa opzione corrisponde al nome del modello creato in precedenza. Ricordarsi che, per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*.
   * **Formato nome soggetto**: impostare questa opzione su **Nome comune**, se non diversamente richiesto.
   * **Nome alternativo del soggetto**: impostare questa opzione su **Nome dell'entità utente (UPN)**, se non diversamente richiesto.
   * **Utilizzo chiavi avanzato**: se sono state usate le impostazioni predefinite nel passaggio 10 della sezione precedente **Configurare i modelli di certificato nell'autorità di certificazione**, aggiungere i **Valori predefiniti** seguenti dalla casella di selezione:
      * **Qualsiasi scopo**
      * **Autenticazione client**
      * **Posta elettronica sicura**
   * **Certificato radice** (per profili Android): questa opzione corrisponde al file con estensione cer esportato nel passaggio 3 della sezione precedente [Esportare il certificato radice dall'autorità di certificazione globale (enterprise)](#export-the-root-certificate-from-the-enterprise-ca).

5. Fare clic su **OK** e quindi su **Crea** per salvare il profilo.
6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere l'articolo [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Passare a Intune nel portale di Azure e creare un nuovo profilo per un certificato attendibile"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Creare un profilo e caricare un certificato attendibile"
[ConnectorDownload]: ./media/certificates-pfx-configure-connector-download.png "Scaricare il connettore di certificati dal portale di Azure"
