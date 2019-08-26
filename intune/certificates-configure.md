---
title: Creare profili certificato in Microsoft Intune - Azure | Microsoft Docs
description: Per i dispositivi, aggiungere o creare un profilo certificato configurando l'ambiente di certificato SCEP o PKCS, esportare il certificato pubblico, creare il profilo nel portale di Azure e quindi assegnare SCEP o PKCS ai profili certificato in Microsoft Intune nel portale di Azure
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f13b5b92ca442f4b5ae05d3567f8385288d92909
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69582926"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Configurare un profilo certificato per i dispositivi in Microsoft Intune

È possibile concedere agli utenti l'accesso alle risorse aziendali tramite VPN, Wi-Fi o profili di posta elettronica. Tramite i certificati, è possibile autenticare queste connessioni. Quando si usano i certificati, gli utenti finali non devono immettere nomi utente e password per eseguire l'autenticazione.

È possibile usare Intune per assegnare questi certificati ai dispositivi gestiti. Intune supporta l'assegnazione e la gestione dei tipi di certificato seguenti:

- Simple Certificate Enrollment Protocol (SCEP)
- PKCS#12 (o PFX)

Ognuno di questi tipi di certificato ha prerequisiti e requisiti di infrastruttura specifici.


## <a name="overview"></a>Panoramica

1. Assicurarsi che sia configurata l'infrastruttura di certificazione corretta. È possibile usare [certificati SCEP](certificates-scep-configure.md) e [certificati PKCS](certficates-pfx-configure.md).

2. Installare un certificato radice o un certificato dell'autorità di certificazione (CA) intermedio in ogni dispositivo, in modo che il dispositivo riconosca la legittimità dell'autorità di certificazione. Per installare il certificato, creare e assegnare un **profilo certificato attendibile** a ogni dispositivo. Quando si assegna questo profilo, i dispositivi gestiti da Intune richiedono e ricevono il certificato radice. È necessario creare un profilo separato per ogni piattaforma. I profili certificato attendibili sono disponibili per le piattaforme seguenti:

    - iOS 8.0 e versioni successive
    - macOS 10.11 e versioni successive
    - Android 4.0 e versioni successive
    - Android Enterprise  
    - Windows 8.1 e versioni successive
    - Windows Phone 8.1 e versioni successive
    - Windows 10 e versioni successive

    > [!NOTE]  
    > I profili dei certificati non sono supportati nei dispositivi che eseguono *Android Enterprise per dispositivi dedicati*.

3. Creare i profili certificato in modo che i dispositivi richiedano un certificato da usare per l'autenticazione dell'accesso a VPN, Wi-Fi e posta elettronica. I tipi di profili seguenti sono disponibili per piattaforme diverse:  

   | Piattaforma     |Certificato PKCS|Certificato SCEP| Certificato importato PKCS | 
   |--------------|----------------|----------------|-------------------|
   | Android                | Sì    | Sì    | Sì    |
   | Android Enterprise     | Sì    | Sì    | Sì    |
   | iOS                    | Sì    | Sì    | Sì    |
   | macOS                  |        | Sì    | Sì    |
   | Windows Phone 8.1      |        | Sì    | Sì    |
   | Windows 8.1 e versioni successive  |        | Sì    |        |
   | Windows 10 e versioni successive   | Sì    | Sì    | Sì    |

   Assicurarsi di creare un profilo separato per ogni piattaforma dei dispositivi. Quando si crea il profilo, questo viene associato al profilo del certificato radice attendibile già creato.

### <a name="further-considerations"></a>Altre considerazioni

- Se non è presente un'autorità di certificazione globale (enterprise), è necessario crearla
- Se si usano profili SCEP, è necessario configurare un server del servizio Registrazione dispositivi di rete
- Se si prevede di usare i profili SCEP o PKCS, è necessario scaricare e configurare il Connettore di certificati di Microsoft Intune


## <a name="step-1-configure-your-certificate-infrastructure"></a>Passaggio 1: Configurare l'infrastruttura dei certificati

Vedere uno degli articoli seguenti per informazioni sulla configurazione dell'infrastruttura per ogni tipo di profilo certificato:

- [Configurare e gestire i certificati SCEP con Intune](certificates-scep-configure.md)
- [Configurare e gestire i certificati PKCS con Intune](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Passaggio 2: Esportare il certificato CA radice attendibile

Esportare il certificato dell'Autorità di certificazione radice disponibile nell'elenco locale (CA) come certificato pubblico con estensione cer dalla CA emittente o da qualsiasi dispositivo che consideri attendibile la CA emittente. Non esportare la chiave privata (con estensione pfx).

Il certificato viene importato quando si configura un profilo certificato attendibile.

## <a name="step-3-create-trusted-certificate-profiles"></a>Passaggio 3: Creare profili di certificati attendibili

Creare un profilo certificato attendibile prima di creare un profilo certificato SCEP o PKCS. Sono necessari un profilo certificato attendibile e un profilo SCEP o PKCS per ogni piattaforma del dispositivo. La procedura per la creazione di certificati attendibili è simile per tutte le piattaforme dei dispositivi.

1. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) selezionare **Configurazione del dispositivo** > **Gestisci** > **Profili** > **Crea profilo**.
2. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di profilo valido è **Profilo certificato attendibile per dispositivi con proprietario Android Enterprise** o **Profilo certificato attendibile per dispositivi iOS**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:

      - **Android**
      - **Android Enterprise** > **Solo proprietario del dispositivo**
      - **Android Enterprise** > **Solo profilo di lavoro**
      - **iOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 e versioni successive**
      - **Windows 10 e versioni successive**

    - **Tipo di profilo**: Scegliere **Certificato attendibile**.

3. Passare al certificato salvato in [Passaggio 2: Esportare il certificato CA radice attendibile](#step-2-export-your-trusted-root-ca-certificate) e quindi selezionare **OK**.
4. Solo per i dispositivi Windows 8.1 e Windows 10, selezionare l'**Archivio di destinazione** per il certificato attendibile da:

    - **Archivio certificati computer - Radice** (SCEP)
    - **Archivio certificati computer - Intermedio** (SCEP)
    - **Archivio certificati utente - Intermedio** (PKCS,SCEP)

5. Al termine scegliere **OK**, tornare alla pagina **Crea profilo** e selezionare **Crea**.

Il profilo viene creato e quindi visualizzato nell'elenco. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

   >[!NOTE]
   > È possibile che nei dispositivi Android venga visualizzato un messaggio che indica che un certificato attendibile è stato installato da terze parti.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Passaggio 4: Creare profili di certificati SCEP o PKCS

Vedere uno degli articoli seguenti per informazioni sulla configurazione e sull'assegnazione di ogni tipo di profilo certificato:

- [Configurare e gestire i certificati SCEP con Intune](certificates-scep-configure.md)
- [Configurare e gestire i certificati PKCS con Intune](certficates-pfx-configure.md)

Dopo aver creato un profilo certificato attendibile, creare i profili certificato SCEP o PKCS per ogni piattaforma che si vuole usare. Quando si crea un profilo certificato SCEP, è necessario specificare un profilo certificato attendibile per la stessa piattaforma. In questo modo i due profili certificato risultano collegati, anche se è ancora necessario assegnarli separatamente.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare i profili di dispositivo](device-profile-assign.md)  
[Usare S/MIME per firmare e crittografare la posta elettronica](certificates-s-mime-encryption-sign.md)  
[Usare un'autorità di certificazione di terze parti](certificate-authority-add-scep-overview.md)

## <a name="see-also"></a>Vedere anche

[Risoluzione dei problemi di configurazione del servizio Registrazione dispositivi di rete per l'uso con i profili certificato di Microsoft Intune](https://support.microsoft.com/help/4459540)

[Risoluzione dei problemi di distribuzione del profilo certificato SCEP in Microsoft Intune](https://support.microsoft.com/help/4457481)
