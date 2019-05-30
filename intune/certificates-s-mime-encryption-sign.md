---
title: Firmare e crittografare la posta elettronica usando S/MIME - Microsoft Intune - Azure | Microsoft Docs
description: Informazioni su come usare i certificati digitali di posta elettronica in Microsoft Intune per firmare e crittografare i messaggi di posta elettronica nei dispositivi. Questi certificati vengono chiamati S/MIME e vengono configurati usando profili di configurazione. I certificati di firma e crittografia usano PKCS o i certificati privati e un connettore per importare i certificati.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5dba3866df9ce5c779deb18cf13852b3d8af1b8d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048888"
---
# <a name="smime-overview-to-sign-and-encrypt-email-in-intune"></a>Panoramica di S/MIME per firmare e crittografare la posta elettronica in Intune

I certificati di posta elettronica, noti anche come certificati S/MIME, forniscono sicurezza aggiuntiva per le comunicazioni di posta elettronica tramite la crittografia e la decrittografia. Microsoft Intune può usare i certificati S/MIME per firmare e crittografare i messaggi di posta elettronica destinati a dispositivi mobili che eseguono le piattaforme seguenti:

- Android
- iOS
- macOS
- Windows 10 e versioni successive
- Windows Phone

Nei dispositivi iOS è possibile creare un profilo di posta elettronica gestito da Intune che usa S/MIME e certificati per firmare e crittografare i messaggi di posta elettronica in ingresso e in uscita. Per altre piattaforme, S/MIME può essere supportato o meno. Se è supportato, installare certificati che usano la firma e la crittografia S/MIME. L'utente finale può quindi abilitare S/MIME nella propria applicazione di posta elettronica.

Per ulteriori informazioni sulla firma e la crittografia dei messaggi di posta elettronica tramite S/MIME con Exchange, vedere [S/MIME per la crittografia e firma dei messaggi](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

Questo articolo offre una panoramica dell'uso dei certificati S/MIME per firmare e crittografare i messaggi di posta elettronica nei dispositivi.

## <a name="signing-certificates"></a>Certificati di firma

I certificati usati per la firma consentono all'app client di posta elettronica di comunicare in modo protetto con il server di posta elettronica.

Per usare certificati di firma, creare nell'autorità di certificazione (CA) un modello basato sulla firma. Nell'autorità di certificazione di Microsoft Active Directory, [Configurare il modello di certificato del server](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) elenca i passaggi necessari per creare modelli di certificato.

I certificati di firma in Intune usano certificati PKCS. [Configurare e usare i certificati PKCS](certficates-pfx-configure.md) descrive come distribuire e usare i certificati PKCS nell'ambiente Intune in uso. Questi passaggi includono:

- Download e installazione del connettore di certificati di Microsoft Intune per il supporto delle richieste di certificato PKCS.
- Creazione di un profilo certificato radice trusted peri dispositivi. Questo passaggio include l'uso di certificati radice trusted e intermedi per l'autorità di certificazione e quindi la distribuzione del profilo ai dispositivi.
- Creazione di un profilo certificato PKCS tramite il modello di certificato creato. Questo profilo rilascia i certificati di firma ai dispositivi e distribuisce il profilo certificato PKCS a questi ultimi.

È anche possibile importare un certificato di firma per un utente specifico. Il certificato di firma viene distribuito in tutti i dispositivi registrati da tale utente. Per importare certificati in Intune, usare i [cmdlet di PowerShell disponibili in GitHub](https://github.com/Microsoft/Intune-Resource-Access). Per distribuire un certificato PKCS importato in Intune da usare per la firma di messaggi di posta elettronica, seguire la procedura descritta in [Configurare e usare i certificati PKCS con Intune](certficates-pfx-configure.md). Questi passaggi includono:

- Download e installazione del connettore di certificati PFX per Microsoft Intune. Questo connettore recapita i certificati PKCS importati ai dispositivi.
- Importazione di certificati di firma S/MIME per la posta elettronica in Intune.
- Creazione di un profilo certificato PKCS importato. Questo profilo recapita i certificati PKCS importati ai dispositivi dell'utente appropriato.

## <a name="encryption-certificates"></a>Certificati di crittografia

I certificati usati per la crittografia assicurano che un messaggio di posta elettronica crittografato possa essere decrittografato solo dal destinatario previsto. La crittografia S/MIME è un livello di sicurezza aggiuntivo che è possibile usare nelle comunicazioni di posta elettronica.

Quando si invia un messaggio di posta elettronica crittografato a un altro utente, si ottiene la chiave pubblica del certificato di crittografia dell'utente, che viene usata per crittografare il messaggio di posta elettronica da inviare. Il destinatario decrittografa il messaggio di posta elettronica usando la chiave privata nel proprio dispositivo. Gli utenti possono avere una cronologia dei certificati usati per crittografare i messaggi di posta elettronica. Perché la posta elettronica possa essere decrittografata, ognuno di questi certificati deve essere distribuito a tutti i dispositivi di un utente specifico.

È consigliabile non creare i certificati di crittografia della posta elettronica in Intune. Intune è in grado di rilasciare certificati PKCS che supportano la crittografia, ma crea un certificato univoco per ogni dispositivo. Un certificato univoco per ogni dispositivo non è ottimale per uno scenario di crittografia S/MIME, in cui il certificato di crittografia deve essere condiviso tra tutti i dispositivi dell'utente.

Per distribuire certificati S/MIME con Intune, è necessario importare in Intune tutti i certificati di crittografia di un utente. Intune distribuisce quindi tutti i certificati a ogni dispositivo registrato dall'utente in questione. Per importare certificati in Intune, usare i [cmdlet di PowerShell disponibili in GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Per distribuire un certificato PKCS importato in Intune da usare per la crittografia di messaggi di posta elettronica, seguire la procedura descritta in [Configurare e usare i certificati PKCS con Intune](certficates-pfx-configure.md). Questi passaggi includono:

- Download e installazione del connettore di certificati PFX per Microsoft Intune. Questo connettore recapita i certificati PKCS importati ai dispositivi.
- Importazione di certificati di crittografia S/MIME per la posta elettronica in Intune.
- Creazione di un profilo certificato PKCS importato. Questo profilo recapita i certificati PKCS importati ai dispositivi dell'utente appropriato.

 > [!NOTE]
 > I certificati di crittografia S/MIME importati vengono rimossi da Intune quando vengono rimossi i dati aziendali o quando la registrazione degli utenti alla gestione viene annullata. I certificati, tuttavia, non vengono revocati presso l'autorità di certificazione.

## <a name="smime-email-profiles"></a>Profili di posta elettronica S/MIME

Dopo aver creato profili certificato di firma e crittografia S/MIME, è possibile [abilitare S/MIME per la posta elettronica nativa di iOS](email-settings-ios.md).

## <a name="next-steps"></a>Passaggi successivi

- [Usare i certificati SCEP](certificates-scep-configure.md)
- [Usare i certificati PKCS](certficates-pfx-configure.md)
- [Usare un’autorità di certificazione partner](certificate-authority-add-scep-overview.md)
- [Rilasciare certificati PKCS da un servizio Web di gestione PKI Symantec](certificates-symantec-configure.md)
