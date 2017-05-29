---
title: "Distribuire e monitorare i criteri di conformità | Documentazione Microsoft"
description: "Usare le istruzioni dettagliate in questo argomento per distribuire e monitorare i criteri di conformità del dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 40826175eb7c71220a521ac45bb8b9b9e84dec4a
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>Distribuire e monitorare i criteri di conformità di un dispositivo in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>Distribuire i criteri di conformità
Distribuire i criteri di conformità [creati](create-a-device-compliance-policy-in-microsoft-intune.md) a uno o più gruppi di utenti nell'organizzazione. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata sui dispositivi dell’utente.

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire e quindi scegliere **Gestisci distribuzione**.
![Screenshot della pagina dei criteri di conformità con l'opzione di menu Gestisci distribuzione nella parte superiore](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  Nella finestra di dialogo **Gestisci distribuzione** selezionare uno o più gruppi in cui si vuole distribuire il criterio e quindi scegliere **Aggiungi** > **OK**.
![Screenshot della finestra di dialogo Gestisci distribuzione](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) Usare i gruppi di Active Directory che sono già stati creati e sincronizzati con Intune oppure creare manualmente questi gruppi nella console di Intune. Per altre informazioni su come distribuire i criteri, vedere [Distribuire un criterio di configurazione](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Usare il riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** per identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene inoltre visualizzato nell'area di lavoro **Dashboard** .

> [!IMPORTANT]
> Se non sono stati distribuiti i criteri di conformità e abilitati i criteri di accesso condizionale di Exchange, a tutti i dispositivi di destinazione verrà consentito l'accesso.

## <a name="monitor-the-compliance-policy"></a>Monitorare i criteri di conformità

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>Per visualizzare i dispositivi non conformi ai criteri di conformità

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Gruppi** > **Tutti i dispositivi**.

2.  Fare doppio clic sul nome di un dispositivo nell'elenco di dispositivi.

3.  Scegliere la scheda **Criteri** per visualizzare un elenco di criteri per il dispositivo.

4.  Nell'elenco a discesa **Filtri** scegliere **Non è conforme ai criteri di conformità**.
![Screenshot che mostra l'elenco delle opzioni nell'elenco dei filtri](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>Per visualizzare i report di attestazione dell'integrità

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Report**.

2.  Nella pagina **Report di attestazione dell'integrità - Creare un nuovo report** è possibile visualizzare un report con tutti i dati di attestazione dell'integrità di Windows 10 raccolti da Intune. È anche possibile creare un report con un subset di dati usando i filtri. I filtri possono essere basati sul tipo di dispositivo, sul sistema operativo o solo su un subset di punti dati.

## <a name="how-intune-resolves-policy-conflicts"></a>Come vengono risolti i conflitti di criteri in Intune
Possono verificarsi conflitti se vengono applicati più criteri di Intune a un dispositivo. Se le impostazioni dei criteri si sovrappongono, Intune risolve eventuali conflitti in base alle regole seguenti:

-   Se le impostazioni in conflitto hanno origine da criteri di configurazione di Intune e da criteri di conformità, le impostazioni nei criteri di conformità hanno la precedenza rispetto a quelle dei criteri di configurazione, anche se queste ultime sono più sicure.

-   Se sono stati distribuiti più criteri di conformità, Intune userà quelli più sicuri.

## <a name="next-steps"></a>Passaggi successivi
Per informazioni su come usare i criteri di conformità con i criteri di accesso condizionale per controllare l'accesso ai servizi nell'organizzazione, vedere [Limitare l'accesso alla posta elettronica e ai servizi di Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).


### <a name="see-also"></a>Vedere anche
[Introduzione ai criteri di conformità del dispositivo in Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)

