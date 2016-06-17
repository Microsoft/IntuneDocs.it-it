---
# required metadata

title: Manca un certificato necessario per il dispositivo | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Manca un certificato necessario per il dispositivo
Se il dispositivo Android non è registrato in Intune e manca un certificato solitamente installato nel telefono, non sarà possibile accedere all'app Portale aziendale Android. Quando si tenta di accedere, verrà visualizzato il messaggio seguente:

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

Per risolvere questo problema e ottenere il certificato richiesto:

1.  In un browser passare alla [pagina del certificato Digicert](https://www.digicert.com/digicert-root-certificates.htm).

2.  Individuare e scaricare il certificato radice Baltimore CyberTrust (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt).

3.  Trascinare verso il basso dalla parte superiore per aprire le notifiche e toccare **BaltimoreCyberTrustRoot.crt** nell'elenco delle notifiche.

4.  Nella finestra relativa all'**assegnazione di un nome al certificato**, accettare il nome del certificato predefinito.

5. Verificare che l'uso delle **credenziali** sia impostato su **VPN e app**, quindi fare clic su **OK**.

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. Chiudere il browser Web e l'app Portale aziendale.

7. Aprire nuovamente l'app Portale aziendale. Accedere all'app Portale aziendale. Per assistenza, contattare l'amministratore IT.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

<!--HONumber=Jun16_HO2-->


