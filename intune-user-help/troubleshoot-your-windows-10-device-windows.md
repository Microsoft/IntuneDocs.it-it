---
title: Risolvere i problemi di registrazione dei dispositivi Windows 10 | Documentazione Microsoft
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4ab630b6-47ff-443b-a2a5-be23388bcea7
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 701ee2081d8f696a1c37eaa2857ab92942d79f48
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="troubleshoot-your-windows-10-device-enrollment"></a>Risolvere i problemi di registrazione dei dispositivi Windows 10
Se è stata seguita la procedura descritta in [Registrare il dispositivo Windows 10 Mobile o Windows 10 Desktop in Intune](enroll-your-w10-phone-or-w10-pc-windows.md), ma non è ancora possibile accedere alla posta elettronica e ai file dell'azienda o dell'istituto di istruzione, provare a eseguire i passaggi di risoluzione dei problemi seguenti.

1.  Esaminare le due schermate seguenti e trovare quella simile a quanto viene visualizzato sul dispositivo. Seguire i passaggi corrispondenti alla schermata visualizzata sul dispositivo.

    Se si visualizza questa schermata, seguire i passaggi in [Passaggi di risoluzione dei problemi da seguire se si visualizza Access work or school (Accesso azienda o istituto di istruzione)](#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).

    ![settings-accounts-access-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Se si visualizza questa schermata, seguire i passaggi in [Passaggi di risoluzione dei problemi da seguire se si visualizza Il tuo account](#troubleshooting-steps-to-follow-if-you-see-your-account).

    ![settings-accounts-your-account](./media/W10-enroll-2-accounts-your-account.png)

## <a name="troubleshooting-steps-to-follow-if-you-see-access-work-or-school"></a>Passaggi di risoluzione dei problemi da seguire se si visualizza "Accedi all'azienda o all'istituto di istruzione"

1.  Se è stata eseguita la procedura sopra descritta, ma non è tuttavia possibile accedere alla posta elettronica e ai file dell'azienda o dell'istituto di istruzione, tornare alla schermata **Access work or school** (Accesso azienda o istituto di istruzione).

2. Eseguire una delle operazioni seguenti:

    - Se si visualizza una connessione simile all'immagine seguente, toccarla e quindi verificare se le opzioni Gestisci, Informazioni e Disconnetti sono presenti. Se si visualizzano queste opzioni, l'utente è registrato e connesso.

    ![validate-successful-enrollment](./media/w10-enroll-rs1-validate-successful-enrollment.png)

    - Se non si visualizzano le informazioni di connessione illustrate in precedenza o si visualizzano, ma mancano alcune opzioni, toccare **Connetti** e quindi accedere con le credenziali aziendali o dell'istituto di istruzione. A questo punto l'utente è connesso.

## <a name="troubleshooting-steps-to-follow-if-you-see-your-account"></a>Passaggi di risoluzione dei problemi da seguire se si visualizza "Il tuo account"

Se è stata eseguita la procedura sopra descritta, ma non è tuttavia possibile accedere alla posta elettronica, ai file e ad altri dati dell'azienda o dell'istituto di istruzione, tornare alla schermata **Account** e toccare **Accesso società**.

- Se viene visualizzato l'account aziendale o dell'istituto di istruzione, la connessione è attiva.

- In caso contrario, toccare **Connetti** e quindi accedere con le credenziali aziendali o dell'istituto di istruzione.

## <a name="troubleshooting-steps-to-follow-if-you-see-set-up-a-work-or-school-account"></a>Passaggi di risoluzione dei problemi da seguire se si visualizza "Imposta un account aziendale o dell'istituto di istruzione"

Se viene visualizzato il messaggio __Non è possibile individuare automaticamente un endpoint di gestione che corrisponde al nome utente immesso. Controlla il nome utente e riprova. Se conosci l'URL dell'endpoint di gestione, immettilo qui.__, è consigliabile provare a immettere nuovamente nome utente e password. Se il problema persiste, richiedere all'amministratore IT quale sito Web è necessario specificare nella casella di testo **Endpoint di gestione**. Si tratta di un sito Web in un formato probabilmente simile a **www.società.onmicrosoft.com**. 

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).
