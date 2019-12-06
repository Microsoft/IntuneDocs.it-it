---
title: Personalizzare il profilo VPN per app per Android
titleSuffix: Microsoft Intune
description: Informazioni su come creare un profilo VPN per app specifiche per i dispositivi Android gestiti da Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62f418e396c5030a47ea0bcb31914cd4e1069c40
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319847"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Usare un profilo personalizzato di Microsoft Intune per creare un profilo VPN per ogni app per dispositivi Android

È possibile creare un profilo VPN per app specifiche per i dispositivi Android 5.0 e versione successiva gestiti da Intune. Creare prima un profilo VPN che usa il tipo di connessione Pulse Secure o Citrix. Definire quindi criteri di configurazione personalizzati che associano il profilo ad app specifiche.

> [!NOTE]
> Per usare la VPN per app nei dispositivi Android Enterprise, è anche possibile seguire questi passaggi. È tuttavia consigliabile usare i [criteri di configurazione dell'app](../apps/app-configuration-policies-use-android.md) per l'app client VPN.

Dopo aver assegnato i criteri ai gruppi di utenti o ai dispositivi Android, gli utenti devono avviare la VPN Pulse Secure o Citrix. Il client VPN consente quindi il traffico solo dalle app specificate per usare la connessione VPN aperta.

> [!NOTE]
>
> Per questo profilo sono supportati solo i tipi di connessione Pulse Secure e Citrix.

## <a name="step-1-create-a-vpn-profile"></a>Passaggio 1: Creare un profilo VPN

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio un buon nome di profilo è **Profilo VPN Android per app per l'intera azienda**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: Selezionare **Android**.
    - **Tipo di profilo**: selezionare **VPN**.

4. Scegliere **Impostazioni** > **Configura**. Configurare quindi il profilo VPN. Per altre informazioni, vedere [Come configurare le impostazioni VPN](vpn-settings-configure.md) e [Impostazioni VPN di Intune per dispositivi Android](vpn-settings-android.md).

Prendere nota del valore **Nome connessione** specificato quando si crea il profilo VPN. Questo nome sarà necessario nel passaggio successivo. Ad esempio **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Passaggio 2: Creare criteri di configurazione personalizzati

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: Immettere un nome descrittivo per il profilo personalizzato. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio un buon nome di profilo è **Profilo VPN Android OMA-URI personalizzato per l'intera azienda**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: Selezionare **Android**.
    - **Tipo di profilo**: Selezionare **Personalizzato**.

4. Scegliere **Impostazioni** > **Configura**.
5. Nel riquadro **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
    - **Nome**: Immettere un nome per l'impostazione.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **OMA-URI**: Immettere `./Vendor/MSFT/VPN/Profile/*Name*/PackageList` dove *Name* è il nome della connessione annotato nel passaggio 1. In questo esempio la stringa è `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Tipo di dati**: Immettere **String**.
    - **Valore**: Immettere un elenco separato da punti e virgola dei pacchetti da associare al profilo. Se ad esempio si vuole che Excel e il browser Google Chrome usino la connessione VPN, immettere `com.microsoft.office.excel;com.android.chrome`.

![Esempio di criteri personalizzati VPN per app Android](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Impostare l'elenco di app come blacklist o whitelist (facoltativo)

Usare il valore *BLACKLIST* per specificare un elenco di app che **non possono** usare la connessione VPN. Tutte le altre app si connettono mediante la VPN. Oppure usare il valore **WHITELIST** per specificare un elenco di app che *possono* usare la connessione VPN. Le app non incluse nell'elenco non si connettono tramite la VPN.

1. Nel riquadro **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
2. Immettere un nome per l'impostazione.
3. In **OMA-URI** immettere `./Vendor/MSFT/VPN/Profile/*Name*/Mode` dove *Name* è il nome del profilo VPN annotato nel passaggio 1. In questo esempio la stringa è `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. In **Tipo di dati** immettere **String**.
5. In **Valore** immettere **BLACKLIST** o **WHITELIST**.

## <a name="step-3-assign-both-policies"></a>Passaggio 3: Assegnare entrambi i criteri

[Assegnare entrambi i profili di dispositivo](device-profile-assign.md) agli utenti o ai dispositivi appropriati.
