---
title: Profilo VPN per app per Android - Pulse Secure
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: Informazioni su come creare un profilo VPN per app specifiche per i dispositivi Android gestiti da Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 0cf638348df2f01d70c0765a4932abc3eb801f23
ms.lasthandoff: 02/18/2017


---

# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Usare un profilo personalizzato di Microsoft Intune per creare un profilo VPN per ogni app per dispositivi Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

È possibile creare un profilo VPN per app specifiche per i dispositivi Android 5.0 e versione successiva gestiti da Intune. Creare innanzitutto un profilo VPN che usa il tipo di connessione Pulse Secure. Definire quindi criteri di configurazione personalizzati che associano il profilo ad app specifiche.

Dopo aver distribuito i criteri ai gruppi di utenti o ai dispositivi Android, gli utenti devono avviare la VPN PulseSecure. PulseSecure quindi consentirà il traffico solo dalle app specificate per usare la connessione VPN aperta.

> [!NOTE]
>
> Per questo profilo è supportato solo il tipo di connessione Pulse Secure.


## <a name="step-1-create-a-vpn-profile"></a>Passaggio 1: Creare un profilo VPN


1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
2. Nell'elenco del pannello dei profili scegliere **Crea profilo**.
3. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** facoltativa per il profilo VPN.
4. Dall'elenco a discesa **Piattaforma** scegliere **Android**.
5. Dall'elenco a discesa dei tipi di **profilo** scegliere **VPN**.
3. Scegliere **Impostazioni** > **Configura** e quindi configurare il profilo VPN in base alle impostazioni in [Come configurare le impostazioni VPN](how-to-configure-vpn-settings.md) e [Impostazioni VPN Intune per dispositivi Android](vpn-for-android.md).

Prendere nota del nome del profilo VPN per usarlo nel passaggio successivo. Ad esempio **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Passaggio 2: Creare criteri di configurazione personalizzati

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili fare clic su **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo personalizzato.
5. Dall'elenco a discesa **Piattaforma** scegliere **Android**.
6. Dall'elenco a discesa dei tipi di **profilo** scegliere **Personalizzato**.
7. Scegliere **Impostazioni** > **Configura**.
3. Nel pannello **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
    - Immettere un nome per l'impostazione.
    - In **Tipo di dati** specificare **Stringa**.
    - In **URI OMA** specificare la stringa seguente: **./Vendor/MSFT/VPN/Profile/*nome*/PackageList** dove *nome* è il nome del profilo VPN annotato nel Passaggio 1. In questo esempio, la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
    - Per l'opzione **Valore** creare un elenco separato da punti e virgola dei pacchetti da associare al profilo. Ad esempio, se si vuole che Excel e il browser Google Chrome usino la connessione VPN, digitare: **com.microsoft.office.excel;com.android.chrome**.

![Esempio di criteri personalizzati VPN per app Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Impostare l'elenco di app come blacklist o whitelist (facoltativo)
  È possibile specificare un elenco di app che *non possono* usare la connessione VPN tramite il valore **BLACKLIST**. Tutte le app non incluse nell'elenco si connetteranno mediante la VPN.
In alternativa, è possibile usare il valore **WHITELIST** per specificare un elenco di app che *possono* usare la connessione VPN. Le app non incluse nell'elenco non si connetteranno mediante la VPN.
  1.    Nel pannello **Impostazioni OMA-URI personalizzate** scegliere **Aggiungi**.
  2.    Immettere un nome per l'impostazione.
  3.    In **Tipo di dati** specificare **Stringa**.
  4.    Per **URI OMA** usare la stringa seguente: **./Vendor/MSFT/VPN/Profile/*nome*/Mode** dove *nome* è il nome del profilo VPN annotato nel Passaggio 1. Con il nome di esempio citato in precedenza la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    In **Valore** immettere **BLACKLIST** o **WHITELIST**.



## <a name="step-3-assign-both-policies"></a>Passaggio 3: assegnare entrambi i criteri

Seguire le istruzioni in [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md) per assegnare entrambi i profili agli utenti o ai dispositivi necessari.

