---
title: Risolvere i problemi di registrazione dei dispositivi Windows 10 | Documentazione Microsoft
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4ab630b6-47ff-443b-a2a5-be23388bcea7
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fe8a765bdb11d0b94dbbb7519360c6e7a01e8ce
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61501239"
---
# <a name="troubleshoot-your-windows-10-device-enrollment"></a>Risolvere i problemi di registrazione dei dispositivi Windows 10
Se il dispositivo è stato registrato, ma non è ancora possibile accedere alla posta elettronica e ai file di lavoro o dell'istituto di istruzione, provare questi passaggi di risoluzione dei problemi.  

1.  Esaminare le due schermate seguenti e trovare quella simile a quanto viene visualizzato sul dispositivo. Seguire i passaggi corrispondenti alla schermata visualizzata sul dispositivo.

    Se si visualizza questa schermata, seguire i passaggi in [Passaggi di risoluzione dei problemi da seguire se si visualizza Access work or school (Accesso azienda o istituto di istruzione)](#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

    ![settings-accounts-access-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Se si visualizza questa schermata, seguire i passaggi in [Passaggi di risoluzione dei problemi da seguire se si visualizza Il tuo account](#troubleshooting-steps-to-follow-if-you-see-your-account).

    ![settings-accounts-your-account](./media/W10-enroll-2-accounts-your-account.png)

## <a name="troubleshooting-steps-to-follow-if-you-see-access-work-or-school"></a>Passaggi di risoluzione dei problemi da seguire se si visualizza "Accedi all'azienda o all'istituto di istruzione"

1. Se è stata eseguita la procedura sopra descritta, ma non è tuttavia possibile accedere alla posta elettronica e ai file dell'azienda o dell'istituto di istruzione, tornare alla schermata **Access work or school** (Accesso azienda o istituto di istruzione).

2. Eseguire una delle operazioni seguenti:

   - Se si visualizza una connessione simile all'immagine seguente, toccarla e quindi verificare se le opzioni Gestisci, Informazioni e Disconnetti sono presenti. Se si visualizzano queste opzioni, l'utente è registrato e connesso.

     ![validate-successful-enrollment](./media/w10-enroll-rs1-validate-successful-enrollment.png)

   - Se non si visualizzano le informazioni di connessione illustrate in precedenza o si visualizzano, ma mancano alcune opzioni, toccare **Connetti**. Accedere quindi con le credenziali aziendali o dell'istituto di istruzione per connettersi.  

## <a name="troubleshooting-steps-to-follow-if-you-see-your-account"></a>Passaggi di risoluzione dei problemi da seguire se si visualizza "Il tuo account"

Se è stata eseguita la procedura sopra descritta, ma non è tuttavia possibile accedere alla posta elettronica, ai file e ad altri dati dell'azienda o dell'istituto di istruzione, tornare alla schermata **Account** e toccare **Accesso società**.

- Se viene visualizzato l'account aziendale o dell'istituto di istruzione, si è connessi.  

- In caso contrario, toccare **Connetti** e quindi accedere con le credenziali aziendali o dell'istituto di istruzione.

## <a name="troubleshooting-steps-to-follow-if-you-see-set-up-a-work-or-school-account"></a>Passaggi di risoluzione dei problemi da seguire se si visualizza "Imposta un account aziendale o dell'istituto di istruzione"

Se viene visualizzato il messaggio <strong>Non è possibile individuare automaticamente un endpoint di gestione che corrisponde al nome utente immesso. Controlla il nome utente e riprova. Se conosci l'URL dell'endpoint di gestione, immettilo qui.</strong>, è consigliabile provare a immettere nuovamente nome utente e password. Se il problema persiste, richiedere al supporto tecnico dell'azienda quale sito Web è necessario specificare nella casella di testo <strong>Endpoint di gestione</strong>. Si tratta di un sito Web in un formato probabilmente simile a <strong>www.società.onmicrosoft.com</strong>.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
