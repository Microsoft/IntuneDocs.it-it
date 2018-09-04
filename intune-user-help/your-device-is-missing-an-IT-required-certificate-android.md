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
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 19128e9de06239fb82266654fe038b4be9ce7d41
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/29/2018
ms.locfileid: "43149782"
---
# <a name="your-android-device-is-missing-a-certificate-required-by-your-company-support"></a>Il dispositivo Android non ha un certificato richiesto dal supporto tecnico dell'azienda

Se il dispositivo non è registrato in Intune e non ha un determinato certificato richiesto dal supporto tecnico dell'azienda, non sarà possibile accedere all'app Portale aziendale dal dispositivo. Quando si tenta di accedere, verrà visualizzato il messaggio seguente:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Per risolvere questo problema e ottenere il certificato richiesto, è necessario eseguire due passaggi principali:

- Identificare il certificato mancante cercando in un PC della società o dell'istituto di istruzione.
- Usare il dispositivo per scaricare il certificato mancante da Internet.

## <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>Identificare il certificato mancante cercando in un PC della società o dell'istituto di istruzione

1. In un PC aprire Internet Explorer. Se non si ha un PC da usare per questo scopo, contattare il supporto tecnico dell'azienda. Per le informazioni di contatto del supporto tecnico dell'azienda, vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).

2. Passare al [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) ed eseguire l'accesso con le credenziali della società o dell'istituto di istruzione.

3. All'estrema destra della barra degli indirizzi del browser, fare clic sul simbolo simile a un lucchetto, come illustrato di seguito.

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    Se non viene visualizzato il simbolo di un lucchetto, interrompere la procedura e contattare il supporto tecnico dell'azienda. Il lucchetto indica che l'accesso viene eseguito in modalità sicura. Se quindi non si visualizza tale simbolo, è consigliabile non procedere.

4. Fare clic su **Visualizza certificati**.

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. Nella finestra di dialogo **Certificato** fare clic sulla scheda **Percorso certificazione** e identificare il certificato che è necessario ottenere da Internet. Il nome del certificato necessario si trova nello stesso percorso di quello evidenziato nella schermata di esempio precedente.

## <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>Scaricare e installare il certificato mancante nel dispositivo mobile Android

1. Con un motore di ricerca come Bing o Google, cercare il nome del certificato mancante identificato nella sezione precedente. Il certificato può avere varie "estensioni", ad esempio "crt" o "pem" e così via.

2. Scaricare il certificato radice dal sito Web.

3. Dopo aver scaricato il certificato, trascinare verso il basso dalla parte superiore del dispositivo per aprire le notifiche e quindi toccare il nome del certificato nell'elenco delle notifiche.

4. Nella finestra di dialogo **Name the Certificate** (Denominare il certificato) illustrata nella schermata seguente, accettare il nome predefinito.

5. Verificare che l'uso delle **credenziali** sia impostato su **VPN e app**, quindi fare clic su **OK**.

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. Chiudere l'app Portale aziendale.

7. Aprire nuovamente l'app Portale aziendale. Accedere all'app Portale aziendale. Per assistenza, contattare il supporto tecnico dell'azienda.

Se viene visualizzato di nuovo il messaggio "Certificato mancante" illustrato in precedenza ed è già stata eseguita la relativa procedura, è probabile che sia necessario installare un altro certificato con l'assistenza del supporto tecnico dell'azienda. Per indicazioni sull'uso delle informazioni di contatto disponibili nel [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980), contattare il supporto tecnico dell'azienda.
