---
title: Usare i certificati PKCS con Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare certificati PKCS (Public Key Cryptography Standards) con Microsoft Intune, inclusi i passaggi per esportare un certificato radice, configurare il modello di certificato, scaricare e installare il connettore di certificati di Microsoft Intune (NDES), creare un profilo di configurazione del dispositivo, creare un profilo certificato PKCS in Azure e nell'autorità di certificazione.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b3bfe76173eff76a3175952bef5c6e23ad5e429
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271542"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurare e usare i certificati PKCS con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I certificati vengono usati per autenticare e proteggere l'accesso alle risorse aziendali, ad esempio una rete VPN o Wi-Fi. In questo articolo viene illustrato come esportare un certificato PKCS e quindi aggiungerlo a un profilo di Intune. 

## <a name="requirements"></a>Requisiti

Per usare i certificati PKCS con Intune, verificare se è disponibile l'infrastruttura seguente:

- **Dominio di Active Directory**: tutti i server elencati in questa sezione devono essere aggiunti al dominio di Active Directory.

  Per altre informazioni sull'installazione e la configurazione di Active Directory Domain Services, vedere l'articolo relativo a [progettazione e pianificazione di AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autorità di certificazione** (CA): un'autorità di certificazione (CA) globale (enterprise)

  Per altre informazioni sull'installazione e la configurazione di Servizi certificati Active Directory (AD CS), vedere la [guida dettagliata di AD CS](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune richiede l'esecuzione di Servizi certificati Active Directory con un'autorità di certificazione globale (enterprise), non con un'autorità di certificazione autonoma (Standalone).

- **Un client**: per la connessione all'autorità di certificazione globale (enterprise)

- **Certificato radice**: una copia esportata del certificato radice dall'autorità di certificazione globale (enterprise)

- **Connettore di certificati di Microsoft Intune**: usare il portale di Azure per scaricare il programma di installazione del **Connettore di certificati** (**NDESConnectorSetup.exe**). 

  Il connettore di certificati del servizio Registrazione dispositivi di rete supporta anche la modalità FIPS (Federal Information Processing Standard). FIPS non è obbligatorio, ma è possibile emettere e revocare i certificati quando è abilitato.

- **Server Windows**: ospita il connettore di certificati di Microsoft Intune (NDESConnectorSetup.exe)

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

  - Impostare **Autorità di certificazione** su **Windows Server 2008 R2**
  - Impostare **Destinatario certificato** su **Windows 7 / Server 2008 R2**

5. Nella scheda **Generale** impostare **Nome visualizzato modello** su un valore significativo.

   > [!WARNING]
   > Per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*. Annotare il nome del modello, sarà necessario in un secondo momento.

6. In **Gestione richiesta** selezionare **Rendi la chiave privata esportabile**.
7. In **Crittografia** verificare che il campo **Dimensioni minime chiave** sia impostato su 2048.
8. In **Nome soggetto** scegliere **Inserisci nella richiesta**.
9. In **Estensioni** verificare che nell'area **Criteri di applicazione** siano presenti Crittografia file system, Posta elettronica sicura e Autenticazione client.

    > [!IMPORTANT]
    > Per i modelli di certificato iOS, accedere alla scheda **Estensioni**, aggiornare **Utilizzo chiavi** e verificare che l'opzione **Firma come prova dell'origine** non sia selezionata.

10. In **Sicurezza** aggiungere l'account computer relativo al server in cui si installa il connettore di certificati di Microsoft Intune. Assegnare all'account le autorizzazioni **Lettura** e **Registrazione**.
11. Selezionare **Applica** e quindi **OK** per salvare il modello di certificato.
12. Chiudere la **Console dei modelli di certificato**.
13. Nella console **Autorità di certificazione** fare clic con il pulsante destro del mouse su **Modelli di certificato**, **Nuovo** e **Modello di certificato da rilasciare**. Scegliere il modello creato nei passaggi precedenti e selezionare **OK**.
14. Per consentire al server di gestire i certificati per conto di utenti e dispositivi registrati in Intune, seguire questa procedura:

    1. Fare clic con il pulsante destro del mouse sull'autorità di certificazione e scegliere **Proprietà**.
    2. Nella scheda della sicurezza aggiungere l'account computer relativo al server in cui è in esecuzione il connettore di certificati di Microsoft Intune. Assegnare all'account le autorizzazioni **Rilascio e gestione certificati** e **Richiesta certificati**.

15. Disconnettersi dall'autorità di certificazione globale (enterprise).

## <a name="download-install-and-configure-the-certificate-connector"></a>Scaricare, installare e configurare il connettore di certificati

![ConnectorDownload][ConnectorDownload]

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione dispositivo** e quindi selezionare **Autorità di certificazione**.
4. Selezionare **Aggiungi** e quindi **Scaricare il file del connettore**. Salvare il file scaricato in un percorso a cui è possibile accedere dal server in cui verrà installato.
5. Al termine del download, accedere al server. Quindi:

    1. Assicurarsi che .NET Framework 4.5 sia installato, perché è richiesto per NDES Connector per i certificati. .NET Framework 4.5 è incluso automaticamente con Windows Server 2012 R2 e versioni più recenti.
    2. Eseguire il programma di installazione (NDESConnectorSetup.exe) e accettare il percorso predefinito. Il connettore viene installato in `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`. Selezionare **Distribuzione PFX** nelle opzioni di installazione. Continuare e completare l'installazione.

6. NDES Connector apre la scheda **Registrazione**. Per abilitare la connessione a Intune, selezionare **Accedi** e specificare un account con autorizzazioni amministrative globali.
7. Nella scheda **Avanzate** lasciare selezionata l'opzione **Usa l'account di sistema del computer (impostazione predefinita)**.
8. Fare clic su **Applica**, quindi su **Chiudi**.
9. Tornare al portale di Azure (**Intune** > **Configurazione dispositivo** > **Autorità di certificazione**). Dopo alcuni istanti, viene visualizzato un segno di spunta verde e lo **stato della connessione** è **attivo**. Il server del connettore ora può comunicare con Intune.

> [!NOTE]
> Il supporto di TLS 1.2 è incluso con NDES Connector per i certificati. Pertanto, se il server in cui è installato NDES Connector per i certificati supporta TLS 1.2, viene usato TLS 1.2. Se il server non supporta TLS 1.2, viene usato TLS 1.1. Attualmente, TLS 1.1 viene usato per l'autenticazione tra i dispositivi e il server.

## <a name="create-a-device-configuration-profile"></a>Creare un profilo di configurazione del dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.

   ![NavigateIntune][NavigateIntune]

3. Immettere le seguenti proprietà:

  - **Nome** del profilo
  - Inserire eventualmente una descrizione
  - **Piattaforma** in cui distribuire il profilo
  - Impostare **Tipo di profilo** su **Certificato attendibile**

4. Accedere a **Impostazioni** e specificare il file CER del certificato CA radice esportato in precedenza.

   > [!NOTE]
   > In base alla piattaforma selezionata nel **passaggio 3**, si può avere la possibilità di scegliere l'**archivio di destinazione** per il certificato.

   ![ProfileSettings][ProfileSettings]

5. Selezionare **OK** e quindi **Crea** per salvare il profilo.
6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le seguenti proprietà:

  - **Nome** del profilo
  - Inserire eventualmente una descrizione
  - **Piattaforma** in cui distribuire il profilo
  - Impostare **Tipo di profilo** su **Certificato PKCS**

4. Accedere a **Impostazioni** e immettere le proprietà seguenti:

  - **Soglia di rinnovo (%)**: il valore consigliato è 20%.
  - **Periodo di validità del certificato**: se il modello di certificato non è stato cambiato, questa opzione può essere impostata su un anno.
  - **Autorità di certificazione**: visualizza il nome di dominio completo interno dell'autorità di certificazione globale (enterprise).
  - **Nome dell'autorità di certificazione**: specifica il nome dell'autorità di certificazione globale (enterprise) e può essere diversa rispetto al valore precedente.
  - **Nome del modello di certificato**: nome del modello creato in precedenza. Ricordarsi che, per impostazione predefinita, il parametro **Nome modello** corrisponde al valore **Nome visualizzato modello** *senza spazi*.
  - **Formato nome soggetto**: impostare questa opzione su **Nome comune**, se non diversamente richiesto.
  - **Nome alternativo del soggetto**: impostare questa opzione su **Nome dell'entità utente (UPN)**, se non diversamente richiesto.
  - **Utilizzo chiavi avanzato**: se sono state usate le impostazioni predefinite nel passaggio 10 della sezione [Configurare i modelli di certificato nell'autorità di certificazione](#configure-certificate-templates-on-the-certification-authority) di questo articolo, aggiungere i seguenti **valori predefiniti** dalla selezione:
    - **Qualsiasi scopo**
    - **Autenticazione client**
    - **Posta elettronica sicura**
  - **Certificato radice** (per profili Android): specifica il file CER esportato nel passaggio 3 della sezione [Esportare il certificato radice dall'autorità di certificazione globale (enterprise)](#export-the-root-certificate-from-the-enterprise-ca) di questo articolo.

5. Selezionare **OK** e quindi **Crea** per salvare il profilo.
6. Per assegnare il nuovo profilo a uno o più dispositivi, vedere [Assegnare profili di dispositivo in Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Passaggi successivi
[Usare i certificati SCEP](certificates-scep-configure.md) o [Rilasciare certificati PKCS da un servizio Web di gestione PKI Symantec](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Passare a Intune nel portale di Azure e creare un nuovo profilo per un certificato attendibile"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Creare un profilo e caricare un certificato attendibile"
[ConnectorDownload]: ./media/certificates-download-connector.png "Scaricare il connettore di certificati dal portale di Azure"  
