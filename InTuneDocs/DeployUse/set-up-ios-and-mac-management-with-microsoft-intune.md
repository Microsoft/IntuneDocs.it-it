---
title: Configurare la gestione dei dispositivi iOS e Mac con Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per dispositivi iOS, inclusi iPad e iPhone, e dispositivi Mac OS X con Microsoft Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: 8a41c4c4f0ab4b4864fe366a2852046693b6baee


---

# Configurare la gestione dei dispositivi iOS e Mac
Gestione Intune dei dispositivi iPad, iPhone e Mac OS X e accesso alla posta elettronica aziendale e alle app. Affinché Intune gestisca i dispositivi iOS e Mac, è necessario un dispositivo Apple Push Notification Service. Dopo aver aggiunto il certificato a Intune, gli utenti possono installare l'app Portale aziendale per registrare i propri dispositivi. In alternativa, l'amministratore può configurare la [gestione dei dispositivi iOS di proprietà dell'azienda](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

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



<!--HONumber=Jul16_HO4-->


