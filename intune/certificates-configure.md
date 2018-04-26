---
title: Creare profili certificato in Microsoft Intune - Azure | Microsoft Docs
description: Per i dispositivi, aggiungere o creare un profilo certificato configurando l'ambiente di certificato SCEP o PKCS, esportare il certificato pubblico, creare il profilo nel portale di Azure e quindi assegnare SCEP o PKCS ai profili certificato in Microsoft Intune nel portale di Azure
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 89f8ddc105787bc7ff4f7cfc1e226d28589ecbbf
ms.sourcegitcommit: 9536300a6211bac4bdc733593a40c1ae47611de3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2018
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Configurare un profilo certificato per i dispositivi in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando si concede agli utenti l'accesso alle risorse aziendali tramite profili VPN, Wi-Fi o di posta elettronica, è possibile autenticare queste connessioni mediante i certificati. Quando si usano i certificati, non è necessario immettere nomi utente e password per l'autenticazione delle connessioni

È possibile usare Intune per assegnare questi certificati ai dispositivi gestiti. Intune supporta l'assegnazione e la gestione dei tipi di certificato seguenti:

- Simple Certificate Enrollment Protocol (SCEP)
- PKCS#12 (o PFX)

Ognuno di questi tipi di certificato ha prerequisiti e requisiti di infrastruttura specifici.

## <a name="overview"></a>Panoramica

1. Assicurarsi di avere l'infrastruttura di certificazione corretta. È possibile usare [certificati SCEP](certificates-scep-configure.md) e [certificati PKCS](certficates-pfx-configure.md).

2. Installare un certificato radice o un certificato dell'autorità di certificazione (CA) intermedio in ogni dispositivo, in modo che il dispositivo riconosca la legittimità dell'autorità di certificazione. A tale scopo, creare e assegnare un **profilo certificato attendibile**. Quando si assegna questo profilo, i dispositivi gestiti con Intune richiedono e ricevono il certificato radice. È necessario creare un profilo separato per ogni piattaforma. I profili certificato attendibili sono disponibili per le piattaforme seguenti:

    - iOS 8.0 e versioni successive
    - macOS 10.11 e versioni successive
    - Android 4.0 e versioni successive
    - Android for Work
    - Windows 8.1 e versioni successive
    - Windows Phone 8.1 e versioni successive
    - Windows 10 e versioni successive

3. Creare i profili certificato in modo che i dispositivi richiedano un certificato da usare per l'autenticazione dell'accesso a VPN, Wi-Fi e posta elettronica. È possibile creare e assegnare un profilo certificato **PKCS** o **SCEP** per i dispositivi che eseguono le piattaforme seguenti:

   - iOS 8.0 e versioni successive
   - Android 4.0 e versioni successive
   - Android for Work
   - Windows 10 (per dispositivi desktop e mobili) e versioni successive

   È possibile usare un profilo certificato **SCEP** solo per i dispositivi che eseguono le piattaforme seguenti:

   - macOS 10.9 e versioni successive
   - Windows Phone 8.1 e versioni successive

Assicurarsi di creare un profilo separato per ogni piattaforma dei dispositivi. Quando si crea il profilo, questo viene associato al profilo del certificato radice attendibile già creato.

### <a name="further-considerations"></a>Altre considerazioni

- Se non è presente un'autorità di certificazione globale (enterprise), è necessario crearla
- Se si usano profili SCEP, è necessario configurare un server del servizio Registrazione dispositivi di rete
- Se si prevede di usare i profili SCEP o PKCS, è necessario scaricare e configurare il Connettore di certificati di Microsoft Intune


## <a name="step-1-configure-your-certificate-infrastructure"></a>Passaggio 1: configurare l'infrastruttura di certificazione

Vedere uno degli argomenti seguenti per informazioni sulla configurazione dell'infrastruttura per i diversi tipi di profilo del certificato:

- [Configurare e gestire i certificati SCEP con Intune](certificates-scep-configure.md)
- [Configurare e gestire i certificati PKCS con Intune](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Passaggio 2: esportare il certificato CA radice attendibile

Esportare il certificato dell'Autorità di certificazione radice disponibile nell'elenco locale (CA) come certificato pubblico con estensione cer dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente. Non esportare la chiave privata (con estensione pfx).

Il certificato viene importato quando si configura un profilo certificato attendibile.

## <a name="step-3-create-trusted-certificate-profiles"></a>Passaggio 3: creare profili certificato attendibile
Creare un profilo certificato attendibile prima di creare un profilo certificato SCEP o PKCS. Sono necessari un profilo certificato attendibile e un profilo SCEP o PKCS per ogni piattaforma del dispositivo. La procedura per la creazione di certificati attendibili è simile per tutte le piattaforme dei dispositivi.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel riquadro dei profili scegliere **Crea profilo**.
4. Nel riquadro **Crea profilo** immettere un **nome** e una **descrizione** per il profilo certificato attendibile.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato attendibile. È attualmente possibile scegliere una delle piattaforme seguenti per le impostazioni del certificato:

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**

6. Dall'elenco a discesa **Tipo di profilo** scegliere **Certificato attendibile**.
7. Passare al certificato salvato nell'attività 1, quindi fare clic su **OK**.
8. Solo per i dispositivi Windows 8.1 e Windows 10, selezionare l'**Archivio di destinazione** per il certificato attendibile da:
    - **Archivio certificati computer - Radice**
    - **Archivio certificati computer - Intermedio**
    - **Archivio certificati utente - Intermedio**
8. Al termine scegliere **OK**, tornare alla pagina **Crea profilo** e selezionare **Crea**.

Il profilo viene creato e quindi visualizzato nell'elenco. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

È possibile che nei dispositivi Android venga visualizzato un messaggio che indica che un certificato attendibile è stato installato da terze parti.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Passaggio 4: creare profili certificato SCEP o PKCS

Per informazioni sulla configurazione e l'assegnazione dei diversi tipi di profilo del certificato, vedere uno degli argomenti seguenti:

- [Configurare e gestire i certificati SCEP con Intune](certificates-scep-configure.md)
- [Configurare e gestire i certificati PKCS con Intune](certficates-pfx-configure.md)

Dopo aver creato un profilo certificato attendibile, creare i profili certificato SCEP o PKCS per ogni piattaforma che si vuole usare. Quando si crea un profilo certificato SCEP, è necessario specificare un profilo certificato attendibile per la stessa piattaforma. In questo modo i due profili certificato risultano collegati, anche se è ancora necessario assegnarli separatamente.

## <a name="next-steps"></a>Passaggi successivi
Vedere [Come assegnare i profili di dispositivo](device-profile-assign.md) per informazioni generali sull'assegnazione dei profili di dispositivo.
