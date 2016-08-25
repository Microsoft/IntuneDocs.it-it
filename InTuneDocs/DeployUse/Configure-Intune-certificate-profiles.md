---
title: Configurare i profili certificato | Microsoft Intune
description: Informazioni su come creare un profilo certificato di Intune.
keywords: 
author: nbigman
manager: Arob98
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 72288296d966b9b9fae4fd721b4460528213f626
ms.openlocfilehash: 40ae2ce3ea4393d24770c010bf5292ca1829a7f1


---

# Configurare i profili certificato di Intune
Dopo aver configurato l'infrastruttura e i certificati come descritto in [Configurare l'infrastruttura di certificazione per SCEP](configure-certificate-infrastructure-for-scep.md) o [Configurare l'infrastruttura di certificazione](configure-certificate-infrastructure-for-pfx.md), è possibile configurare i profili certificato:

**Attività 1**: esportare il certificato CA radice attendibile **Attività 2**: creare profili certificato CA attendibili **Attività 3**: scegliere una delle alternative seguenti:

Creare profili certificato SCEP

Creare profili certificato PFX

### Attività 1: esportare il certificato radice attendibile
Esportare il certificato CA radice attendibile come file **.cer** dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente. Non esportare la chiave privata.

Questo certificato viene importato quando si configura un profilo di certificato attendibile.

### Attività 2: creare profili di certificato attendibile
È necessario creare un **profilo di certificato attendibile** prima di creare un profilo di certificato SCEP o PFX. È necessario un profilo di certificato attendibile e un profilo SCEP o PFS per ogni piattaforma del dispositivo mobile.

##### Per creare un profilo certificato attendibile

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com) e fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare uno dei tipi di criteri seguenti:

    **Android &gt; Profilo di certificato attendibile (Android 4 e versioni successive)**

    **iOS &gt; Profilo di certificato attendibile (iOS 7.1 e versioni successive)**

    **Mac OS X &gt; Profilo di certificato attendibile (Mac OS X 10.9 e versioni successive)**

    **Windows &gt; Profilo di certificato attendibile (Windows 8.1 e versioni successive)**

    **Windows &gt; Profilo di certificato attendibile (Windows Phone 8.1 e versioni successive)**

    Altre informazioni: [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Fornire le informazioni richieste per configurare le impostazioni del profilo di certificato attendibile per Android, iOS, Mac OS X, Windows 8.1 o Windows Phone 8.1. Nell'impostazione **File di certificato** importare il certificato CA radice attendibile (**.cer**) esportato dal CA emittente. L'impostazione **Archivio di destinazione** si applica esclusivamente ai dispositivi che eseguono Windows 8.1 e versioni successive e solo se il dispositivo ha più di un archivio di certificati.


4.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio viene visualizzato nell'area di lavoro **Criteri** e può essere distribuito.

### Attività 3: creare profili certificato SCEP o PFX
Dopo aver creato un profilo certificato CA attendibile, creare i profili certificato SCEP o PFX per ogni piattaforma da usare. Quando si crea un profilo di certificato SCEP, è necessario specificarne uno attendibile per la stessa piattaforma. Questo collega i due profili di certificato, anche se è ancora necessario distribuire i profili separatamente.

##### Per creare un profilo certificato SCEP

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com), fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare uno dei tipi di criteri seguenti:

    **Android &gt; Profilo di certificato SCEP (Android 4 e versioni successive)**

    **iOS &gt; Profilo di certificato SCEP (iOS 7.1 e versioni successive)**

    **Mac OS X &gt; Profilo di certificato SCEP (Mac OS X 10.9 e versioni successive)**

    **Windows &gt; Profilo di certificato SCEP (Windows 8.1 e versioni successive)**

    **Windows &gt; Profilo di certificato SCEP (Windows Phone 8.1 e versioni successive)**

    Altre informazioni: [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Seguire le istruzioni nella pagina di configurazione del profilo per configurare le impostazioni del profilo di certificato SCEP.

4.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio viene visualizzato nell'area di lavoro **Criteri** e può essere distribuito.

##### Per creare un profilo certificato PFX

1.  Aprire la [console di amministrazione di Intune](https://manage.microsoft.com), fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare uno dei tipi di criteri seguenti:



-   **Android &gt; Profilo di certificato PFX (Android 4 e versioni successive)**

    -   **Windows &gt; Profilo di certificato PKCS #12 (PFX)  (Windows 10 e versioni successive)**

    -   **Windows &gt; Profilo di certificato PKCS #12 (PFX) (Windows Phone 10 e versioni successive)**

    -    **iOS > Profilo di certificato PKCS #12 (PFX) (iOS 7.1 e versioni successive)**    

    Altre informazioni: [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Specificare le informazioni richieste nel modulo Criteri.

4.  Al termine, fare clic su **Salva criterio**.

Il nuovo criterio viene visualizzato nell'area di lavoro **Criteri** e può essere distribuito.

## Distribuire i profili di certificato
Quando si distribuiscono i profili certificato, il file del certificato dal profilo del certificato CA attendibile viene installato nei dispositivi e il profilo certificato SCEP o PFX viene usato dal dispositivo per creare una richiesta di certificato.

I profili di certificato vengono installati solo nei dispositivi applicabili in base alla piattaforma usata durante la creazione del profilo.

-   È possibile distribuire i profili di certificato alle raccolte di utenti o di dispositivi.

    > [!TIP]
    > Per consentire la pubblicazione rapida dei certificati nei dispositivi dopo la registrazione del dispositivo, distribuire questo profilo certificato a un gruppo di utenti (non di dispositivi). Se si distribuire a un gruppo di dispositivi, è necessario eseguire una registrazione completa del dispositivo prima che questo riceva i criteri.

-   Anche se ogni profilo viene distribuito separatamente, è necessario distribuire sia il profilo di radice attendibile che il profilo SCEP/PFX; in caso contrario, i criteri dei certificati SCEP/PFX non verranno eseguiti correttamente.

I profili di certificato si distribuiscono allo stesso modo degli altri criteri per Intune:

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire, quindi fare clic su **Gestisci distribuzione**.

2.  Nella finestra di dialogo **Gestisci distribuzione** :

    -   **Per distribuire il criterio**: selezionare uno o più gruppi in cui si vuole distribuire il criterio, quindi fare clic su **Aggiungi** &gt; **OK**.

    -   **Per chiudere la finestra di dialogo senza distribuire il criterio**, fare clic su **Annulla**.

Quando si seleziona un criterio distribuito, è possibile visualizzare altre informazioni sulla distribuzione nella parte inferiore dell'elenco di criteri.
###  Passaggi successivi

È ora possibile usare i certificati per proteggere posta elettronica, Wi-Fi e profili VPN:

-  [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Connessioni Wi-Fi in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


