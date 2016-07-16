---
title: Configurare la gestione dei dispositivi Windows con Microsoft Intune | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: c18445385e8361cf01948b583f08e992658a8762


---

# Configurare la gestione dei dispositivi Windows
Con Intune è possibile abilitare la registrazione di dispositivi PC Windows BYOD (Bring Your Own Device) per concedere l'accesso alla posta elettronica e alle app aziendali. Usato con Azure Active Directory, offre anche un modo veloce e no-touch per gestire i nuovi dispositivi Windows 10 e ottenere l'accesso alle risorse aziendali senza dover ricreare l'immagine del computer. Dopo la registrazione, gli utenti possono accedere mentre ai dispositivi possono essere assegnati criteri, app e impostazioni mediante la console di amministrazione di Intune. È anche possibile [configurare la gestione di Windows Phone con Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) o [gestire i computer con software client di Intune](manage-windows-pcs-with-microsoft-intune.md) tramite il client Intune.

La creazione di DNS CNAME consente agli utenti di connettersi e registrarsi in Intune senza immettere un nome server.

### Configurare la gestione dei dispositivi Windows

  1.  Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. I record di risorse CNAME devono contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

    La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

    **EnterpriseEnrollment-s.manage.microsoft.com**: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

    **EnterpriseRegistration.windows.net**: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati con Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  2.  Nella [console di amministrazione di Intune](http://manage.microsoft.com) fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows**.
  ![Finestra di dialogo della gestione dei dispositivi Windows](../media/enroll-intune-winenr.png)
  3.  Digitare l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e fare clic su **Verifica il rilevamento automatico**.

### Vedere anche
[Prepararsi alla registrazione dei dispositivi in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


