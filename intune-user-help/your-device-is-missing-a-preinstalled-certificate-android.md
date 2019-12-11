---
title: Manca un certificato necessario per il dispositivo | Documentazione Microsoft
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- User help
ROBOTS: NOINDEX, NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 753fce1e37014e0ad4dac44f1eeb9284482e8f83
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72500180"
---
# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>Manca un certificato necessario per il dispositivo Android generalmente installato nel telefono

Se il dispositivo non è registrato in Intune e manca un certificato solitamente installato nel telefono, non sarà possibile accedere all'app Portale aziendale. Quando si tenta di accedere, verrà visualizzato il messaggio seguente:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

È possibile risolvere il problema ottenendo il certificato richiesto dalla [pagina dei certificati di Digicert](https://www.digicert.com/digicert-root-certificates.htm).

1. Trovare e scaricare il certificato __Baltimore CyberTrust Root__. È possibile scaricare il certificato anche da [qui](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

2. Trascinare verso il basso dalla parte superiore dello schermo per visualizzare l'elenco delle notifiche recenti e toccare **BaltimoreCyberTrustRoot.crt**.

3. Il dispositivo richiederà di **assegnare un nome al certificato**. Non modificare il nome predefinito del certificato che viene visualizzato.

4. Verificare che l'uso delle **credenziali** sia impostato su **VPN e app**, quindi fare clic su **OK**.

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. Chiudere il browser e l'app Portale aziendale.

6. Aprire nuovamente l'app Portale aziendale. Accedere all'app Portale aziendale. Se non è ancora possibile usare l'app Portale aziendale, richiedere assistenza al supporto tecnico dell'azienda usando le informazioni riportate nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).

>[!NOTE]
> Se l'installazione di questo certificato non risolve il problema e viene visualizzato un altro messaggio "certificato mancante", è necessario eseguire passaggi aggiuntivi per [installare il certificato mancante](your-device-is-missing-an-IT-required-certificate-android.md).

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
