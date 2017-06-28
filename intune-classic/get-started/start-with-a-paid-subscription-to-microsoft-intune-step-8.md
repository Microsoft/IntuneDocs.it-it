---
title: Abilitare la registrazione dei dispositivi
description: "Impostare l&quot;autorità MDM e abilitare la registrazione per i dispositivi iOS, Windows, Android e Mac."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 64c6eb58246ac3ad232c1b8ee89d12a83e7e1784
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017


---

# <a name="enable-enrollment-for-mobile-devices"></a>Abilitare la registrazione per i dispositivi mobili

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento descrive come un amministratore di Intune può abilitare la registrazione dei dispositivi mobili. Per informazioni sull'uso di Intune nel telefono, vedere [Uso di dispositivi gestiti per lo svolgimento del lavoro](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions).

Per configurare la gestione dei dispositivi mobili con Intune, è prima necessario impostare l'*autorità di gestione dei dispositivi mobili*, che identifica il servizio utilizzabile per gestire i dispositivi associati all'account. In questo argomento si presuppone l'uso del servizio Intune invece di System Center Configuration Manager. Dopo aver configurato l'autorità MDM, è possibile abilitare la gestione per le piattaforme dei dispositivi e registrare i dispositivi con l'app Portale aziendale.

## <a name="enable-device-enrollment"></a>Abilitare la registrazione dei dispositivi

1. **Rendere Intune l'autorità di gestione dei dispositivi mobili**
    Nella [console di amministrazione di Intune](https://manage.microsoft.com/) fare clic su **Amministrazione** > **Gestione dei dispositivi mobili** e fare clic su **Imposta autorità MDM** in **Attività**.  

2. Scegliere **Sì** nella finestra di dialogo dell'autorità MDM.

    ![Console di amministrazione. Impostare MDM su Intune](../media/intune-mdm-authority.png)

## <a name="choose-how-to-enroll-devices"></a>Scegliere come registrare i dispositivi

Intune consente di gestire i dispositivi in diversi modi in base ai requisiti dell'azienda. Dispositivi personali (BYOD, Bring Your Own Device), dispositivi di proprietà dell'azienda, CYOD (Choose Your Own Device) e dispositivi in modalità tutto schermo sono solo alcuni degli scenari di registrazione disponibili.

Attenersi a questa procedura per [Scegliere come registrare i dispositivi](choose-how-to-enroll-devices1.md).

## <a name="enable-mdm-for-your-device-platform"></a>Abilitare la gestione dei dispositivi mobili per la piattaforma del dispositivo
La registrazione deve essere abilitata per i dispositivi iOS, Mac e Android for Work, in modo da stabilire una relazione tra il provider di piattaforma e il tenant di Intune. I dispositivi Windows e Android non richiedono passaggi aggiuntivi, ma per i dispositivi Windows è possibile semplificare la registrazione per gli utenti creando una voce del Registro di sistema DNS speciale.

Abilitare la registrazione dei dispositivi per la piattaforma del dispositivo da gestire. I requisiti variano a seconda della piattaforma:

- [iOS e macOS](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Windows 10 e Windows Phone](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
- [PC Windows](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) (client software di Intune)
- [Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

Dopo aver abilitato la registrazione, gli utenti possono scaricare l'app Portale aziendale nel dispositivo e completare il processo di registrazione del dispositivo.

### <a name="enable-company-owned-device-enrollment"></a>Abilitare la registrazione dei dispositivi di proprietà dell'azienda
È anche possibile abilitare un'ampia gamma di scenari di [registrazione dei dispositivi di proprietà dell'azienda](/intune-classic/deploy-use/manage-corporate-owned-devices) tra i quali:
- [Programma di registrazione dispositivi di Apple (DEP, Device Enrollment Program).](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Registrazione con Assistente configurazione e Apple Configurator](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Registrazione diretta con Apple Configurator](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [Manager di registrazione dispositivi](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>Passaggi successivi
A questo punto, Ultimo passaggio della *Guida introduttiva di Intune* completato Ora che la configurazione iniziale è stata completata, è possibile attivare altre funzionalità di MDM.

>[!div class="step-by-step"]
>[&larr; **Registrare i dispositivi**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md)     [**Attività successive alla configurazione** &rarr;](.\post-configuration-tasks.md)  

