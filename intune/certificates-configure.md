---
title: Creare profili certificato in Microsoft Intune - Azure | Microsoft Docs
description: Per i dispositivi, aggiungere o creare un profilo certificato configurando l'ambiente di certificato SCEP o PKCS, esportare il certificato pubblico, creare il profilo nel portale di Azure e quindi assegnare SCEP o PKCS ai profili certificato in Microsoft Intune nel portale di Azure
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76e6ba8cb1ed6804bfb50f69a00817a50fe1912e
ms.sourcegitcommit: 3db8af810b95c3a6ed3f8cc00f6ce79076ebb9db
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2019
ms.locfileid: "71012447"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Usare i certificati per l'autenticazione in Microsoft Intune  

Usare i certificati con Intune per autenticare gli utenti in applicazioni e risorse aziendali tramite profili VPN, Wi-Fi o di posta elettronica. Quando si usano i certificati per autenticare queste connessioni, gli utenti finali non dovranno immettere nomi utente e password e l'accesso risulterà così semplificato. I certificati vengono usati anche per la firma e la crittografia della posta elettronica tramite S/MIME.

Intune supporta i tipi di certificato seguenti:  

- Simple Certificate Enrollment Protocol (SCEP)  
- PKCS#12 (o PFX)  
- Certificati importati PKCS

Per distribuire questi certificati, verranno creati e assegnati profili di certificato ai dispositivi.  

Ogni singolo profilo di certificato creato supporta un'unica piattaforma. Ad esempio, se si usano i certificati PKCS, verrà creato un profilo di certificato PKCS per Android e un profilo di certificato PKCS separato per iOS. Se si usano anche i certificati SCEP per queste due piattaforme, verrà creato un profilo di certificato SCEP per Android e un altro per iOS.  

**Considerazioni generali**:  
- Se non è disponibile un'autorità di certificazione (CA) globale (enterprise), è necessario crearne una o usarne una da [uno dei partner supportati](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- Se si usano i profili di certificato SCEP usando Servizi certificati Microsoft Active Directory, verrà configurato un server del servizio Registrazione dispositivi di rete (NDES).
- Se si usa SCEP con uno dei partner Microsoft di autorità di certificazione, sarà necessario [integrarlo con Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Per i profili di certificato SCEP e PKCS è necessario scaricare, installare e configurare Connettore di certificati di Microsoft Intune. 
- Per i certificati PCKS importati è necessario scaricare, installare e configurare Connettore di certificati PFX per Microsoft Intune.
- Per i certificati PKCS importati è necessario esportare i certificati dall'autorità di certificazione e importarli in Microsoft Intune. Vedere [il progetto PowerShell PFXImport](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- Affinché possa usare i profili di certificato SCEP, PCKS o PKCS importato, un dispositivo deve considerare attendibile l'autorità di certificazione radice. Usare un *profilo di certificato attendibile* per distribuire il certificato CA radice attendibile nei dispositivi.  

## <a name="supported-platforms-and-certificate-profiles"></a>Piattaforme e profili di certificato supportati  
| Piattaforma              | Profilo di certificato attendibile | Profilo di certificato PKCS | Profilo di certificato SCEP | Profilo di certificato PKCS importato  |
|--|--|--|--|---|
| Amministratore dispositivo Android | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png)|  ![Supportato](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> - Proprietario del dispositivo   | ![Supportato](./media/certificates-configure/green-check.png) |   |  |   |
| Android Enterprise <br> - Profilo di lavoro    | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) |
| iOS                   | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) |
| macOS                 | ![Supportato](./media/certificates-configure/green-check.png) |   |![Supportato](./media/certificates-configure/green-check.png)|![Supportato](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Supportato](./media/certificates-configure/green-check.png)  |  | ![Supportato](./media/certificates-configure/green-check.png)| ![Supportato](./media/certificates-configure/green-check.png) |
| Windows 8.1 e versioni successive |![Supportato](./media/certificates-configure/green-check.png)  |  |![Supportato](./media/certificates-configure/green-check.png) |   |
| Windows 10 e versioni successive  | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) | ![Supportato](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Esportare il certificato CA radice attendibile  
Per usare i certificati PKCS, SCEP e PKCS importato, i dispositivi devono considerare attendibile l'autorità di certificazione radice. Per stabilire questa relazione di trust, esportare il certificato dell'autorità di certificazione (CA) radice attendibile, nonché eventuali certificati di autorità di certificazione intermedia o emittente, come certificato pubblico (con estensione cer). È possibile ottenere questi certificati dalla CA emittente o da qualsiasi dispositivo che considera attendibile la CA emittente.  

Per esportare il certificato, fare riferimento alla documentazione relativa all'autorità di certificazione. Sarà necessario esportare il certificato pubblico come file con estensione cer.  Non esportare la chiave privata (file con estensione pfx).  

Il file con estensione cer verrà usato quando si [creano profili di certificato attendibili](#create-trusted-certificate-profiles) per distribuire il certificato nei dispositivi.  

## <a name="create-trusted-certificate-profiles"></a>Creare profili di certificati attendibili  
Creare un profilo di certificato attendibile prima di creare un profilo di certificato SCEP o PKCS oppure un profilo di certificato PKCS importato. La distribuzione di un profilo di certificato attendibile garantisce che ogni dispositivo riconosca la legittimità dell'autorità di certificazione. I profili di certificato SCEP fanno riferimento direttamente a un profilo di certificato attendibile. I profili di certificato PKCS non fanno riferimento direttamente al profilo di certificato attendibile, ma fanno riferimento direttamente al server che ospita la CA. I profili di certificato PKCS importato non fanno riferimento direttamente al profilo di certificato attendibile, ma potrebbero usarlo nel dispositivo. La distribuzione di un profilo di certificato attendibile nei dispositivi garantisce che venga stabilita questa relazione di trust. Quando un dispositivo non considera attendibile la CA radice, i criteri del profilo di certificato SCEP o PKCS avranno esito negativo.  

Creare un profilo di certificato attendibile separato per ogni piattaforma del dispositivo che si vuole supportare, così come si farà per i profili di certificato SCEP, PCKS e PKCS importato.  


### <a name="to-create-a-trusted-certificate-profile"></a>Per creare un profilo certificato attendibile  

1. Accedere al [portale di Intune](https://aka.ms/intuneportal).  
2. Selezionare **Configurazione del dispositivo** > **Gestisci** > **Profili** > **Crea profilo**.  
3. Immettere **Nome e Descrizione** per il profilo di certificato attendibile.  
4. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato attendibile.  
5. Dall'elenco a discesa **Tipo di profilo** scegliere **Certificato attendibile**.  
6. Individuare il file con estensione cer del certificato CA radice attendibile esportato per l'uso con questo profilo di certificato e quindi selezionare **OK**.  
7. Solo per i dispositivi Windows 8.1 e Windows 10, selezionare l'**Archivio di destinazione** per il certificato attendibile da:  
   - **Archivio certificati computer - Radice**
   - **Archivio certificati computer - Intermedio**
   - **Archivio certificati utente - Intermedio**
8. Al termine scegliere **OK**, tornare alla pagina **Crea profilo** e selezionare **Crea**.
Il profilo viene visualizzato nell'elenco dei profili nel riquadro di visualizzazione *Configurazione del dispositivo - Profili* con il tipo di profilo **Certificato attendibile**.  Assicurarsi di assegnare questo profilo ai dispositivi che useranno certificati SCEP o PCKS. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

> [!NOTE]  
> È possibile che nei dispositivi Android venga visualizzato un messaggio che indica che un certificato attendibile è stato installato da terze parti.  

## <a name="additional-resources"></a>Risorse aggiuntive  
- [Assegnare i profili di dispositivo](device-profile-assign.md)  
- [Usare S/MIME per firmare e crittografare la posta elettronica](certificates-s-mime-encryption-sign.md)  
- [Usare l'autorità di certificazione di terze parti](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Passaggi successivi  
Dopo aver creato e assegnato profili di certificato attendibili, creare i profili di certificato SCEP, PKCS o PKCS importato per ogni piattaforma che si vuole usare. Per continuare, vedere gli articoli seguenti:  
- [Configurare l'infrastruttura per supportare i certificati SCEP con Intune](certificates-scep-configure.md)  
- [Configurare e gestire i certificati PKCS con Intune](certficates-pfx-configure.md)  
- [Creare un profilo di certificato PKCS importato](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

