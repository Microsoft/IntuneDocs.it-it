---
title: Configurare i profili certificato | Documentazione Microsoft
description: Informazioni su come creare un profilo certificato di Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 905be6a926dc5bab8e9b1016ba82751ee47313e5
ms.openlocfilehash: 70fba8f983efb245afc3fb19fa38287d1a84b1f4
ms.lasthandoff: 02/18/2017


---

# <a name="configure-intune-certificate-profiles"></a>Configurare i profili certificato di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Dopo aver configurato l'infrastruttura e i certificati come descritto in [Configurare l'infrastruttura di certificazione per SCEP](configure-certificate-infrastructure-for-scep.md) o [Configurare l'infrastruttura di certificazione per PFX](configure-certificate-infrastructure-for-pfx.md), è possibile creare i profili certificato. Questa è la procedura:

- **Attività 1**: esportare il certificato CA radice attendibile
- **Attività 2**: creare profili certificato attendibile
- **Attività 3**: creare uno dei due tipi di profilo certificato:
  - Profili certificato SCEP
  - Profilo certificato PFX

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>**Attività 1**: esportare il certificato CA radice attendibile
Esportare il certificato dell'Autorità di certificazione radice disponibile nell'elenco locale come file con estensione **cer** dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente. Non esportare la chiave privata.

Il certificato viene importato quando si configura un profilo certificato attendibile.

## <a name="task-2-create-trusted-certificate-profiles"></a>**Attività 2**: creare profili certificato attendibile
È necessario creare un profilo certificato attendibile prima di creare un profilo certificato Simple Certificate Enrollment Protocol (SCEP) o PKCS #12 (PFX). È necessario un profilo certificato attendibile e un profilo SCEP o PFX per ogni piattaforma del dispositivo mobile.

### <a name="to-create-a-trusted-certificate-profile"></a>Per creare un profilo certificato attendibile

1.  Nella [Console di amministrazione di Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Aggiungi criterio** e scegliere una piattaforma del dispositivo. È possibile creare un profilo certificato attendibile per i dispositivi seguenti:

-  Android 4 e versioni successive

-  Android for Work

-  iOS 7.1 e versioni successive

-  Mac OS X 10.9 e versioni successive

-  Windows 8.1 e versioni successive

-  Windows Phone 8.1 e versioni successive

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

2.  Aggiungere un criterio **Profilo certificato attendibile**.

    Altre informazioni: [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Specificare le informazioni richieste per configurare le impostazioni del profilo certificato attendibile per Android, iOS, Mac OS X, Windows 8.1 o Windows Phone 8.1.
4.  Nell'impostazione **File di certificato** importare il certificato CA radice attendibile (file con estensione cer) esportato dalla CA emittente. L'impostazione **Archivio di destinazione** si applica esclusivamente ai dispositivi che eseguono Windows 8.1 e versioni successive e solo se il dispositivo ha più di un archivio di certificati.

4.  Scegliere **Salva criterio**.

Il nuovo criterio verrà visualizzato nell'area di lavoro **Criteri**. È ora possibile distribuirlo.

> [!NOTE]
>
> I dispositivi Android e Android for Work visualizzano un avviso che indica che altri produttori hanno installato un certificato attendibile.


## <a name="task-3-create-scep-or-pfx-certificate-profiles"></a>**Attività 3**: creare profili certificato SCEP o PFX
Dopo aver creato un profilo certificato CA attendibile, creare i profili certificato SCEP o PFX per ogni piattaforma che si vuole usare. Quando si crea un profilo certificato SCEP, è necessario specificare un profilo certificato attendibile per la stessa piattaforma. In questo modo, i due profili certificato risultano collegati, anche se è ancora necessario distribuirli separatamente.

### <a name="to-create-an-scep-certificate-profile"></a>Per creare un profilo certificato SCEP

1.  Nella [Console di amministrazione di Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Aggiungi criterio** e scegliere una piattaforma del dispositivo.  È possibile creare un profilo certificato SCEP per i dispositivi seguenti:

-  Android 4 e versioni successive

-  Android for Work

-  iOS 7.1 e versioni successive

-  Mac OS X 10.9 e versioni successive

-  Windows 8.1 e versioni successive

-  Windows Phone 8.1 e versioni successive

2.  Aggiungere un criterio **Profilo certificato SCEP**

    Altre informazioni: [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Seguire le istruzioni nella pagina di configurazione del profilo per configurare le impostazioni del profilo di certificato SCEP.
    > [!NOTE]
    >
    > In **Formato del nome soggetto** selezionare **Personalizzato** per immettere un formato personalizzato del nome soggetto (solo nei profili iOS).
    >
    > Le due variabili attualmente supportate per il nome personalizzato sono `Common Name (CN)` ed `Email (E)`. Usando una combinazione di queste variabili e stringhe statiche, è possibile creare un formato di nome soggetto personalizzato simile al seguente:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > In questo esempio l'amministratore ha creato un formato di nome soggetto che, oltre alle variabili `CN` ed `E`, usa stringhe per i valori Unità organizzativa, Organizzazione, Località, Stato e Paese. La [funzione CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) elenca le stringhe supportate.

4.  Scegliere **Salva criterio**.

Il nuovo criterio verrà visualizzato nell'area di lavoro **Criteri**. È ora possibile distribuirlo.

### <a name="to-create-a-pfx-certificate-profile"></a>Per creare un profilo certificato PFX

1.  Nella [Console di amministrazione di Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Aggiungi criterio** e scegliere una piattaforma del dispositivo. I certificati PFX sono supportati per i dispositivi seguenti:
  - Android 4 e versioni successive
  - Android for Work
  - Windows 10 e versioni successive
  - Windows Phone 10 e versioni successive
  - iOS 8.0 e versioni successive    


2.  Aggiungere un criterio **Profilo certificato PFX**.
      Altre informazioni: [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Immettere le informazioni richieste nel modulo Criteri.
4.  Scegliere **Salva criterio**.

Il nuovo criterio verrà visualizzato nell'area di lavoro **Criteri**. È ora possibile distribuirlo.

## <a name="deploy-certificate-profiles"></a>Distribuire i profili di certificato
Quando si distribuiscono i profili certificato, il file del certificato dal profilo certificato CA attendibile viene installato nel dispositivo. Il dispositivo usa il protocollo certificato SCEP o PFX per creare una richiesta di certificato dal dispositivo.

I profili certificato vengono installati solo nei dispositivi che eseguono la piattaforma usata durante la creazione del profilo.

-   È possibile distribuire i profili certificato alle raccolte di utenti o di dispositivi.

    > [!TIP]
    > Per pubblicare rapidamente un certificato in un dispositivo dopo la registrazione del dispositivo, distribuire il profilo certificato a un gruppo di utenti piuttosto che di dispositivi. Se si distribuisce a un gruppo di dispositivi, è necessario eseguire una registrazione completa del dispositivo prima che questo riceva i criteri.

-   Anche se si distribuisce ogni profilo separatamente, è necessario distribuire anche la CA radice attendibile e il profilo SCEP o PFX. In caso contrario, i criteri di certificato SCEP o PFX avranno esito negativo.

Distribuire i profili certificato allo stesso modo degli altri criteri per Intune:

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire e quindi scegliere **Gestisci distribuzione**.
2.  Nella finestra di dialogo **Gestisci distribuzione** :
    -   **Per distribuire il criterio**, selezionare uno o più gruppi a cui distribuirlo e quindi scegliere **Aggiungi** &gt; **OK**.
    -   **Per chiudere la finestra di dialogo senza distribuirlo**, scegliere **Annulla**.

Quando si seleziona un criterio distribuito, è possibile visualizzare altre informazioni sulla distribuzione nella parte inferiore dell'elenco di criteri.

### <a name="next-steps"></a>Passaggi successivi

Comprendere, successivamente, come usare i certificati per proteggere i profili di posta elettronica, Wi-Fi e VPN.

-  [Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Connessioni Wi-Fi in Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [Connessioni VPN in Microsoft Intune](vpn-connections-in-microsoft-intune.md)

