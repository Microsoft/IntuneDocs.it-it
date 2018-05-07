---
title: Usare i certificati PKCS con Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare certificati PKCS (Public Key Cryptography Standards) con Microsoft Intune, inclusi i passaggi per esportare un certificato radice, configurare il modello di certificato, scaricare e installare il connettore di certificati di Microsoft Intune, creare un profilo di configurazione del dispositivo, creare un profilo certificato PKCS in Azure e nell'autorità di certificazione
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61a190be2b4685030438988dab0d0134a8fa9f9b
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurare e usare i certificati PKCS con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I certificati vengono usati per autenticare e proteggere l'accesso alle risorse aziendali, ad esempio una rete VPN o Wi-Fi. In questo articolo viene illustrato come esportare un certificato PKCS e quindi aggiungerlo a un profilo di Intune. 

## <a name="requirements"></a>Requisiti

Per usare i certificati PKCS con Intune, verificare se è disponibile l'infrastruttura seguente:

* Un dominio Active Directory Domain Services (AD DS) esistente configurato.
 
  Per altre informazioni sull'installazione e la configurazione di Active Directory Domain Services, vedere l'articolo relativo a [progettazione e pianificazione di AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

* Un'autorità di certificazione (CA) globale (enterprise) esistente configurata.

  Per altre informazioni sull'installazione e la configurazione di Servizi certificati Active Directory (AD CS), vedere la [guida dettagliata di AD CS](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune richiede l'esecuzione di Servizi certificati Active Directory con un'autorità di certificazione globale (enterprise), non con un'autorità di certificazione autonoma (Standalone).

* Un client con connettività all'autorità di certificazione globale (enterprise).
* Una copia del certificato radice esportato dall'autorità di certificazione globale (enterprise).
* Il connettore di certificati di Microsoft Intune (NDESConnectorSetup.exe) scaricato dal portale di Intune.
* Un server Windows per ospitare il connettore di certificati di Microsoft Intune (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Esportare il certificato radice dall'autorità di certificazione globale (enterprise)

Per l'autenticazione con VPN, Wi-Fi e altre risorse, è necessario un certificato radice o intermedio della CA per ogni dispositivo. La procedura seguente illustra come ottenere il certificato richiesto dall'autorità di certificazione globale (enterprise).

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire un prompt dei comandi come amministratore.
3. Esportare il certificato CA radice (estensione CER) in un percorso a cui è possibile accedere in un secondo momento.

   Ad esempio:

4. Al termine della procedura guidata, prima di chiuderla, fare clic su **Avvia l'interfaccia utente di Connettore di certificati**.

   `certutil -ca.cert certnew.cer`

   Per altre informazioni, vedere [Operazioni certutil per la gestione dei certificati](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurare i modelli di certificato nell'autorità di certificazione

1. Accedere all'autorità di certificazione globale (enterprise) con un account che abbia privilegi amministrativi.
2. Aprire la console **Autorità di certificazione**, fare clic con il pulsante destro del mouse su **Modelli di certificato** e selezionare **Gestisci**.
3. Individuare il modello di certificato **User**, fare clic con il pulsante destro del mouse su di esso e scegliere **Duplica modello**. Vengono visualizzate le **proprietà di Nuovo modello**.
4. Nella scheda **Compatibilità**: 
   * Impostare **Autorità di certificazione** su **Windows Server 2008 R2**
   * Impostare **Destinatario certificato** su **Windows 7 / Server 2008 R2**
5. Fare clic sulla scheda **Generale** :
   * Impostare **Nome visualizzato modello** su un valore significativo.

   > [!WARNING]
   > Per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*. Annotare il nome del modello, sarà necessario in un secondo momento.

6. In **Gestione richiesta** selezionare **Rendi la chiave privata esportabile**.
7. In **Crittografia** verificare che il campo **Dimensioni minime chiave** sia impostato su 2048.
8. In **Nome soggetto** scegliere **Inserisci nella richiesta**.
9. In **Estensioni** verificare che nell'area **Criteri di applicazione** siano presenti Crittografia file system, Posta elettronica sicura e Autenticazione client.
    
      > [!IMPORTANT]
      > Per i modelli di certificato iOS, accedere alla scheda **Estensioni**, aggiornare **Utilizzo chiavi** e verificare che l'opzione **Firma come prova dell'origine** non sia selezionata.

10. In **Sicurezza** aggiungere l'account computer relativo al server in cui si installa il connettore di certificati di Microsoft Intune.
    * Assegnare all'account le autorizzazioni **Lettura** e **Registrazione**.
11. Selezionare **Applica** e quindi **OK** per salvare il modello di certificato.
12. Chiudere la **Console dei modelli di certificato**.
13. Nella console **Autorità di certificazione** fare clic con il pulsante destro del mouse su **Modelli di certificato**, **Nuovo** e **Modello di certificato da rilasciare**.
    * Scegliere il modello creato nei passaggi precedenti e selezionare **OK**.
14. Per consentire al server di gestire i certificati per conto di utenti e dispositivi registrati in Intune, seguire questa procedura:

    a. Fare clic con il pulsante destro del mouse sull'autorità di certificazione e scegliere **Proprietà**.

    b. Nella scheda della sicurezza aggiungere l'account computer relativo al server in cui è in esecuzione il connettore di certificati di Microsoft Intune.
      * Assegnare all'account le autorizzazioni **Rilascio e gestione certificati** e **Richiesta certificati**.
15. Disconnettersi dall'autorità di certificazione globale (enterprise).

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Scaricare, installare e configurare il connettore di certificati di Microsoft Intune

![ConnectorDownload][ConnectorDownload]

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi** e filtrare per **Intune**. Selezionare **Microsoft Intune** e quindi **Configurazione del dispositivo**. 
2. Selezionare **Autorità di certificazione**, **Aggiungi** e quindi **Scaricare il file del connettore**. Salvare il file scaricato in un percorso a cui è possibile accedere dal server in cui verrà installato. 
3. Accedere a questo server ed eseguire il programma di installazione: 

    1. Accettare il percorso predefinito. Il connettore viene installato in `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`.
    2. Selezionare **Distribuzione PFX** nelle opzioni di installazione e selezionare **Avanti**.
    3. Fare clic su **Installa** e attendere il completamento dell'installazione.
    4. Al termine, selezionare **Avvia Intune Connector** e quindi **Fine**.

4. La finestra del connettore NDES si apre sulla scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni amministrative globali.
5. Nella scheda **Avanzate** lasciare selezionata l'opzione **Usa l'account di sistema del computer (impostazione predefinita)**.
6. Fare clic su **Applica**, quindi su **Chiudi**.
7. Tornare al portale di Azure (**Intune** > **Configurazione dispositivo** > **Autorità di certificazione**). Dopo alcuni minuti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.

## <a name="create-a-device-configuration-profile"></a>Creare un profilo di configurazione del dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Accedere a **Intune**, **Configurazione dispositivo**, **Profili** e selezionare **Crea profilo**.

   ![NavigateIntune][NavigateIntune]

3. Immettere le seguenti proprietà:
   * **Nome** del profilo
   * Inserire eventualmente una descrizione
   * **Piattaforma** in cui distribuire il profilo
   * Impostare **Tipo di profilo** su **Certificato attendibile**

4. Accedere a **Impostazioni** e specificare il file CER del certificato CA radice esportato in precedenza.

   > [!NOTE]
   > In base alla piattaforma selezionata nel **passaggio 3**, si può avere la possibilità di scegliere l'**archivio di destinazione** per il certificato.

   ![ProfileSettings][ProfileSettings]

5. Selezionare **OK** e quindi **Crea** per salvare il profilo.
6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Accedere a **Intune**, **Configurazione dispositivo**, **Profili** e selezionare **Crea profilo**.
3. Immettere le seguenti proprietà:
   * **Nome** del profilo
   * Inserire eventualmente una descrizione
   * **Piattaforma** in cui distribuire il profilo
   * Impostare **Tipo di profilo** su **Certificato PKCS**
4. Accedere a **Impostazioni** e immettere le proprietà seguenti:
   * **Soglia di rinnovo (%)**: il valore consigliato è 20%.
   * **Periodo di validità del certificato**: se il modello di certificato non è stato cambiato, questa opzione può essere impostata su un anno.
   * **Autorità di certificazione**: visualizza il nome di dominio completo interno dell'autorità di certificazione globale (enterprise).
   * **Nome dell'autorità di certificazione**: specifica il nome dell'autorità di certificazione globale (enterprise) e può essere diversa rispetto al valore precedente.
   * **Nome del modello di certificato**: nome del modello creato in precedenza. Ricordarsi che, per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*.
   * **Formato nome soggetto**: impostare questa opzione su **Nome comune**, se non diversamente richiesto.
   * **Nome alternativo del soggetto**: impostare questa opzione su **Nome dell'entità utente (UPN)**, se non diversamente richiesto.
   * **Utilizzo chiavi avanzato**: se sono state usate le impostazioni predefinite nel passaggio 10 della sezione [Configurare i modelli di certificato nell'autorità di certificazione](#configure-certificate-templates-on-the-certification-authority) di questo articolo, aggiungere i seguenti **valori predefiniti** dalla selezione:
      * **Qualsiasi scopo**
      * **Autenticazione client**
      * **Posta elettronica sicura**
   * **Certificato radice** (per profili Android): specifica il file CER esportato nel passaggio 3 della sezione [Esportare il certificato radice dall'autorità di certificazione globale (enterprise)](#export-the-root-certificate-from-the-enterprise-ca) di questo articolo.

5. Selezionare **OK** e quindi **Crea** per salvare il profilo.
6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere l'articolo [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Passare a Intune nel portale di Azure e creare un nuovo profilo per un certificato attendibile"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Creare un profilo e caricare un certificato attendibile"
[ConnectorDownload]: ./media/certificates-download-connector.png "Scaricare il connettore di certificati dal portale di Azure"  
