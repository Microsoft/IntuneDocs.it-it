---
title: Suggerimenti generali per la risoluzione dei problemi | Microsoft Docs
description: Risorse generali per risolvere problemi con Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c86a4e4a-6b9f-4835-a3d3-61a3f5f4c1ec
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: ef6c482a45a7c759cec1062b129d2644562d0da2
ms.lasthandoff: 01/10/2017


---

# <a name="general-troubleshooting-tips-for-microsoft-intune"></a>Suggerimenti generali per la risoluzione dei problemi di Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Dopo aver distribuito Microsoft Intune, potrebbero verificarsi problemi relativi alla configurazione o ai dispositivi client. Usare le seguenti risorse per scoprire la causa del problema per poterlo risolvere.

> [!NOTE]
> Per creare una richiesta di supporto o visualizzare una richiesta esistente, [visitare l'interfaccia di amministrazione di Office 365](https://portal.office.com/admin/default.aspx). Per altre informazioni sulle opzioni di supporto, vedere [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="define-the-problem"></a>Definire il problema

-   Qual è il comportamento?

-   Chi nota questo comportamento e su quali piattaforme e dispositivi?

-   Il dispositivo funzionava correttamente prima?

-   Quali modifiche sono state apportate alla configurazione di Intune o del dispositivo?

-   Sono state apportate altre modifiche all'ambiente in cui si opera, oltre alle modifiche di configurazione?

-   Con quale frequenza si verifica questo problema e si tratta di un problema sporadico o coerente?

-   È possibile che si verifichi un problema di autenticazione per l'utente? Se è possibile, vedere se l'utente può accedere ad altri servizi che usano Azure Active Directory. Vedere anche se l'utente può accedere da un altro dispositivo.

-   È stato controllato lo stato del servizio? È possibile monitorare l'integrità dei servizi Intune nel [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx). Scegliere **Integrità dei servizi** nel riquadro a sinistra.

## <a name="collect-available-data"></a>Raccogliere i dati disponibili

-   Le risorse seguenti consentono di imparare a raccogliere i registri del dispositivo:
  - [Send Android diagnostic data logs to your IT administrator using a USB cable (Inviare i log dei dati Android di diagnostica all'amministratore IT tramite un cavo USB)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Send Android diagnostic data logs to your IT administrator using email (Inviare i log dei dati Android di diagnostica all'amministratore IT tramite posta elettronica)](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)
  - [Send Android enrollment errors to your IT administrator (Inviare gli errori di registrazione Android all'amministratore IT)](/intune/enduser/send-enrollment-errors-to-your-it-administrator-android)
  - [Send iOS enrollment errors to your IT administrator (Inviare gli errori di registrazione iOS all'amministratore IT)](/intune/enduser/send-errors-to-your-it-admin-ios)

-   Con i dati della console di amministrazione (ad esempio, per i problemi di implementazione dei criteri) è consigliabile esaminare i criteri previsti e il relativo stato, come descritto in [Usare i gruppi per gestire utenti e dispositivi con Microsoft Intune](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

## <a name="research-the-solution"></a>Cercare la soluzione

-   Cercare una soluzione sul Web. Ad esempio, se si riceve l'errore 0x80073CF0, cercare **technet intune 0x80073cf0** sul Web per trovare l'articolo [Risorse che consentono di risolvere i problemi di distribuzione dell'app in Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md). Questo articolo contiene suggerimenti per risolvere questo errore.

-   Cercare una risposta nel [forum di TechNet su Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  Se il problema non è stato affrontato in precedenza, pubblicare la domanda per ricevere i suggerimenti della community.

-   Aprire una richiesta di supporto. Il supporto tecnico di Intune potrà fornire un'assistenza migliore dopo che è stato definito il problema e sono stati raccolti i dati disponibili.

    Per creare una richiesta di supporto [visitare l'interfaccia di amministrazione di Office 365](https://portal.office.com/admin/default.aspx). Per altre informazioni sulle opzioni di supporto, vedere [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

## <a name="find-community-resources"></a>Trovare risorse della community
È possibile trovare altre informazioni utili in queste risorse della community:

-   La [Microsoft Intune Survival Guide](http://social.technet.microsoft.com/wiki/contents/articles/23431.microsoft-intune-survival-guide.aspx) (guida essenziale di Microsoft Intune) contiene collegamenti a numerose risorse utili per configurare, gestire e risolvere i problemi relativi a Intune.

-   [Blog di Intune](http://blogs.technet.com/b/windowsintune/)

-   [Intune su Twitter](https://twitter.com/MSIntune)

-   [Forum su Intune](https://social.technet.microsoft.com/Forums/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)

### <a name="next-steps"></a>Passaggi successivi
Gli argomenti seguenti illustrano la risoluzione dei problemi per problemi specifici. Se tali informazioni non risultano utili, contattare il supporto tecnico Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

[Risolvere i problemi di Endpoint Protection in Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md)

[Risolvere i problemi di accesso alle risorse aziendali con Microsoft Intune](troubleshoot-company-resource-access-problems-with-microsoft-intune.md)

[Risolvere i problemi di distribuzione dell'app in Microsoft Intune](troubleshoot-app-deployment-problems-in-microsoft-intune.md)

[Risolvere i problemi di registrazione dei dispositivi in Intune](troubleshoot-device-enrollment-in-intune.md)

[Risolvere i problemi relativi ai criteri in Microsoft Intune](troubleshoot-policies-in-microsoft-intune.md)

[Risolvere i problemi di installazione client in Microsoft Intune](troubleshoot-client-setup-in-microsoft-intune.md)

[Risolvere i problemi degli aggiornamenti software in Microsoft Intune](troubleshoot-software-updates-in-microsoft-intune.md)

