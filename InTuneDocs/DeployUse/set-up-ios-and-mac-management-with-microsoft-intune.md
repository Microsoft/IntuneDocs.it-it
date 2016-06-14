---
# required metadata

title: Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurare la gestione dei dispositivi iOS e Mac
Con Microsoft Intune è possibile abilitare la registrazione di dispositivi iOS e Mac OS X BYOD (Bring Your Own Device) per concedere l'accesso alla posta elettronica e alle app aziendali agli utenti di iPhone, iPad e Mac. Una volta registrati, gli utenti possono installare l'app Portale aziendale di Intune e assegnare i criteri ai dispositivi mediante la console di amministrazione di Intune.

Prima di poter gestire dispositivi iOS con Intune, questi devono essere in grado di comunicare con Intune. Apple richiede una relazione di trust con Intune stabilita tramite l'importazione di un certificato Apple Push Notification Service (APNs).

1.  **Configurare Intune**<br>
    Se non è stato già fatto, preparare la gestione di dispositivi mobili (MDM) [impostando l'autorità di gestione di dispositivi mobili](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2.  **Ottenere una richiesta di firma del certificato**<br>
    Gli utenti amministratori possono aprire la [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), fare clic su **Amministrazione** &gt; ** Gestione dei dispositivi mobili** &gt; **iOS e Mac OS X** &gt; **Carica un certificato APNs**, quindi selezionare **Scarica richiesta di certificato APN**. Salvare il file della richiesta di firma del certificato (estensione csr) in locale. Questo file viene usato per richiedere un certificato di relazione di trust al portale Apple Push Certificates.

    ![Caricare la finestra di dialogo del certificato APN](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Ottenere un certificato per Apple Push Notification Service**<br>
    Visitare il [portale Apple Push Certificates](http://go.microsoft.com/fwlink/?LinkId=269844) e accedere con il proprio ID Apple per creare il certificato APN usando il file CSR. Dopo aver fatto clic su **Upload** (Carica) nel portale Apple Push Certificates si riceverà un file con estensione json che non può essere usato per il servizio APN. Completare il download e ritornare al portale Apple Push Certificates per **Certificates for Third-Party Servers** (Certificati per server di terze parti) e fare clic su **Download** (Scarica).

    Scaricare il certificato APN (con estensione PEM) e salvare il file in locale. Questo ID Apple deve essere usato in futuro per rinnovare il certificato APN.

4.  **Aggiungere il certificato APNs a Intune**<br>
    Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **iOS e Mac OS X** &gt; **Carica un certificato APNs**, quindi selezionare **Carica il certificato APNs**. **Individuare** il file di certificato (con estensione PEM) e fare clic su **Apri** , quindi immettere l' **ID Apple**. Con il certificato APN Intune può registrare e gestire i dispositivi iOS effettuando il push dei criteri nei dispositivi mobili registrati.

5.  **Comunicare agli utenti come ottenere l'accesso alle risorse aziendali con il portale aziendale**<br>
    Gli utenti dovranno sapere come registrare i propri dispositivi e cosa aspettarsi una volta che vengono introdotti nella gestione. [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)

Se l'azienda o l'organizzazione acquista dispositivi iOS per gli utenti, i dispositivi possono anche essere registrati per la gestione come [dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### Vedere anche
[Prepararsi alla registrazione dei dispositivi in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO4-->


