---
title: Personalizzare il profilo VPN per app per Android
titleSuffix: Microsoft Intune
description: Informazioni su come creare un profilo VPN per app specifiche per i dispositivi Android gestiti da Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/05/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 524f4cd77d85460940a885bc7950e7d476097e72
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72496119"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Usare un profilo personalizzato di Microsoft Intune per creare un profilo VPN per ogni app per dispositivi Android

[!INCLUDE[azure_portal](../includes/azure_portal.md)]

È possibile creare un profilo VPN per app specifiche per i dispositivi Android 5.0 e versione successiva gestiti da Intune. Creare prima un profilo VPN che usa il tipo di connessione Pulse Secure o Citrix. Definire quindi criteri di configurazione personalizzati che associano il profilo ad app specifiche.

Dopo aver assegnato i criteri ai gruppi di utenti o ai dispositivi Android, gli utenti devono avviare la VPN Pulse Secure o Citrix. Il client VPN consente quindi il traffico solo dalle app specificate per usare la connessione VPN aperta.

> [!NOTE]
>
> Per questo profilo sono supportati solo i tipi di connessione Pulse Secure e Citrix.


## <a name="step-1-create-a-vpn-profile"></a>Passaggio 1: Creare un profilo VPN


1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
2. Nell'elenco del riquadro dei profili scegliere **Crea profilo**.
3. Nel riquadro **Crea profilo** immettere un **nome** e una **descrizione** (facoltativa) per il profilo VPN.
4. Dall'elenco a discesa **Piattaforma** scegliere **Android**.
5. Dall'elenco a discesa dei tipi di **profilo** scegliere **VPN**.
3. Scegliere **Impostazioni** > **Configura** e quindi configurare il profilo VPN in base alle impostazioni in [Come configurare le impostazioni VPN](vpn-settings-configure.md) e [Impostazioni VPN Intune per dispositivi Android](vpn-settings-android.md).

Prendere nota del valore **Nome connessione** specificato quando si crea il profilo VPN. Questo nome sarà necessario nel passaggio successivo. Ad esempio **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Passaggio 2: Creare criteri di configurazione personalizzati

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.
2. Nel riquadro **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
3. Nella pagina dei profili fare clic su **Crea profilo**.
4. Nel riquadro **Crea profilo** immettere un **nome** e una **descrizione** per il profilo personalizzato.
5. Dall'elenco a discesa **Piattaforma** scegliere **Android**.
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Personalizzato**.
7. Scegliere **Impostazioni** > **Configura**.
3. Nel riquadro **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
    - Immettere un nome per l'impostazione.
    - In **URI OMA** specificare la stringa seguente: **./Vendor/MSFT/VPN/Profile/*nome*/PackageList**, dove *nome* è il nome della connessione annotato nel passaggio 1. In questo esempio, la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - In **Tipo di dati** specificare **Stringa**.
    - Per l'opzione **Valore** creare un elenco separato da punti e virgola dei pacchetti da associare al profilo. Ad esempio, se si vuole che Excel e il browser Google Chrome usino la connessione VPN, digitare: **com.microsoft.office.excel;com.android.chrome**.

![Esempio di criteri personalizzati VPN per app Android](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Impostare l'elenco di app come blacklist o whitelist (facoltativo)
  È possibile specificare un elenco di app che *non possono* usare la connessione VPN tramite il valore **BLACKLIST**. Tutte le altre app si connettono mediante la VPN.
In alternativa, è possibile usare il valore **WHITELIST** per specificare un elenco di app che *possono* usare la connessione VPN. Le app non incluse nell'elenco non si connettono mediante la VPN.
  1. Nel riquadro **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
  2. Immettere un nome per l'impostazione.
  3. Per **URI OMA** usare la stringa seguente: **./Vendor/MSFT/VPN/Profile/*nome*/Mode**, dove *nome* è il nome del profilo VPN annotato nel passaggio 1. Con il nome di esempio citato in precedenza la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  4. In **Tipo di dati** specificare **Stringa**.
  5. In **Valore** immettere **BLACKLIST** o **WHITELIST**.



## <a name="step-3-assign-both-policies"></a>Passaggio 3: Assegnare entrambi i criteri

Seguire le istruzioni in [Come assegnare i profili di dispositivo](device-profile-assign.md) per assegnare entrambi i profili agli utenti o ai dispositivi necessari.
