---
title: Registrare un dispositivo Windows 10 in Portale aziendale Intune | Microsoft Docs
description: Procedura per registrare dispositivi Windows 10 in Portale aziendale Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/21/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca8b24a1e8d0da4386ab185533fec38d9b34eb21
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506264"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Registrare dispositivi Windows 10 in Portale aziendale Intune

Usare Portale aziendale Intune per registrare il dispositivo Windows 10 nella gestione dell'organizzazione. Questo articolo descrive come registrare i dispositivi con Windows 10 versione 1607 e versioni successive e Windows 10 versione 1511 e versioni precedenti. Prima di iniziare, assicurarsi di [verificare la versione sul dispositivo](windows-enrollment-company-portal.md#find-windows-10-version-number) in modo da poter seguire la procedura corretta.  

Windows 10 è supportato in vari tipi di dispositivo, inclusi desktop, telefoni e tablet. La procedura di registrazione è uguale indipendentemente dal dispositivo in uso. Tuttavia, la schermata potrebbe essere leggermente diversa dalle immagini riportate in questo articolo.  
</br>
> [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Registrare un dispositivo con Windows 10 versione 1607 e successive 
Questa procedura descrive come registrare un dispositivo che esegue Windows 10, versione 1607 e successive.  

1. Fare clic su **Start**. Se si usa un dispositivo Windows 10 Mobile, passare all'elenco **Tutte le app**.

2. Aprire l'app **Impostazioni**. Se l'app non è subito disponibile nell'elenco delle app, passare alla barra di ricerca e digitare "impostazioni".

3. Selezionare **Account** > **Accedi all'azienda o all'istituto di istruzione** > **Connetti**.  


    ![Selezionare Accedi all'azienda o all'istituto di istruzione](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. Per accedere alla pagina di accesso di Intune dell'organizzazione, immettere l'indirizzo di posta elettronica aziendale o dell'Istituto di istruzione. Selezionare quindi **Avanti**.  


   ![Immissione dell'account aziendale o dell'istituto di istruzione](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. Accedere a Intune con l'account aziendale o dell'istituto di istruzione.  


    ![Aggiungi un account aziendale o dell'istituto di istruzione](./media/w10-enroll-rs1-enter-your-credentials.png)  

    Verrà infine visualizzato un messaggio che la società o l'istituto di istruzione sta registrando il dispositivo.

6. Se l'organizzazione richiede di configurare un PIN per Windows Hello, verrà richiesto di immettere un codice di verifica. Immettere il codice e continuare con le istruzioni visualizzate per creare un PIN.  

7. Nella schermata **La configurazione è completata** selezionare **Fine**. Il dispositivo è ora registrato.  

8. Per verificare la connessione, tornare a **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**.  L'account dovrebbe ora essere elencato.  


    ![Convalida della corretta configurazione della connessione](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

Non è ancora possibile accedere agli indirizzi di posta elettronica, ai file o ad altri dati aziendali o dell'istituto di istruzione? Informazioni su come [risolvere i problemi relativi agli account](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Registrare un dispositivo con Windows 10 versione 1511 e precedenti  
Questa procedura descrive come registrare un dispositivo che esegue Windows 10, versione 1511 e precedenti.  

1. Fare clic su **Start**. Se si usa un dispositivo Windows 10 Mobile, passare all'elenco **Tutte le app**.

2. Aprire l'app **Impostazioni**. Se l'app non è subito disponibile nell'elenco delle app, passare alla barra di ricerca e digitare "impostazioni".

3. Selezionare **Account** > **Il tuo account**.  


    ![Selezionare l'account personale](./media/W10-enroll-2-accounts-your-account.png)  

5. Selezionare **Aggiungi un account aziendale o dell'istituto di istruzione**.  


    ![Selezionare Aggiungi un account aziendale o dell'istituto di istruzione](./media/w10-enroll-3-add-work-school-acct.png)  

6. Accedere con le credenziali aziendali o dell'istituto di istruzione.  


    ![Accesso](./media/W10-enroll-4-sign-in.png)  

Non è ancora possibile accedere agli indirizzi di posta elettronica, ai file o ad altri dati aziendali o dell'istituto di istruzione? Informazioni su come [risolvere i problemi relativi agli account](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account) durante la registrazione.  

## <a name="it-administrator-support"></a>Supporto per amministratori IT   

Gli amministratori IT che riscontrano problemi durante la registrazione dei dispositivi possono vedere [Risoluzione dei problemi di registrazione dei dispositivi Windows in Microsoft Intune](https://support.microsoft.com/help/4469913). Questo articolo elenca gli errori comuni, le cause e le procedure per risolverli. 

## <a name="next-steps"></a>Passaggi successivi  
Se occorre assistenza con il portale aziendale o la registrazione, contattare il team di supporto IT della propria organizzazione. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980). Accedere al sito con l'account aziendale o dell'istituto di istruzione.  

 

