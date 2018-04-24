---
title: Profilo VPN per app per Android con Pulse Secure
description: È possibile creare un profilo VPN per app specifiche per i dispositivi Android gestiti da Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fb4b6ad21b83d6ed2844238091f2e24e0d15cea5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="use-a-custom-policy-to-create-a-per-app-vpn-profile-for-android-devices"></a>Usare criteri personalizzati per creare un profilo VPN per app per dispositivi Android

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

È possibile creare un profilo VPN per app specifiche per i dispositivi Android 5.0 e versione successiva gestiti da Intune. Creare innanzitutto un profilo VPN che usa il tipo di connessione Pulse Secure o Citrix. Definire quindi criteri di configurazione personalizzati che associano il profilo ad app specifiche. 

Dopo aver distribuito i criteri ai gruppi di utenti o ai dispositivi Android, gli utenti devono avviare la VPN Pulse Secure o Citrix. La connessione quindi consentirà il traffico solo dalle app specificate per usare la connessione VPN aperta.

> [!NOTE]
>
> Per questo profilo sono supportati solo i tipi di connessione Pulse Secure e Citrix.


### <a name="step-1-create-a-vpn-profile"></a>Passaggio 1: Creare un profilo VPN

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** > **Aggiungi criterio**.
2. Per selezionare un modello per il nuovo criterio, espandere **Android** e quindi scegliere **Profilo VPN (Android 4 e versioni successive)**.
3. Nel modello in **Tipo di connessione** scegliere **Pulse Secure** o **Citrix**.
4. Completare e salvare il profilo VPN. Per altri dettagli sui profili VPN vedere [Connessioni VPN in Microsoft Intune](../deploy-use/vpn-connections-in-microsoft-intune.md).

> [!NOTE]
>
> Prendere nota del valore **Nome connessione VPN (visualizzato agli utenti)** specificato quando si crea il profilo VPN. Questo valore sarà necessario nel passaggio successivo. Ad esempio **MyAppVpnProfile**.

### <a name="step-2-create-a-custom-configuration-policy"></a>Passaggio 2: Creare criteri di configurazione personalizzati

   1. Nella console di amministrazione di Intune scegliere **Criteri** > **Aggiungi criterio** > **Android** > **Configurazione personalizzata** > **Crea criterio**.
   2. Immettere un nome per il criterio.
   3. In **Impostazioni URI OMA** scegliere **Aggiungi**.
   4. Immettere un nome per l'impostazione.
   5. In **Tipo di dati** specificare **Stringa**.
   6. In **URI OMA** specificare la stringa seguente: **./Vendor/MSFT/VPN/Profile/*nome*/PackageList**, dove *nome* è il nome del profilo VPN annotato nel passaggio 1. Con il nome di esempio, citato in precedenza la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   Per l'opzione **Valore** creare un elenco separato da punti e virgola dei pacchetti da associare al profilo. Ad esempio, se si vuole che Excel e il browser Google Chrome usino la connessione VPN, digitare: **com.microsoft.office.excel;com.android.chrome**.

![Esempio di criteri personalizzati VPN per app Android](./media/android_per_app_vpn_oma_uri.png)

#### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Impostare l'elenco di app come blacklist o whitelist (facoltativo)
  È possibile specificare un elenco di app che *non possono* usare la connessione VPN tramite il valore **BLACKLIST**. Tutte le app non incluse nell'elenco si connetteranno mediante la VPN.
In alternativa, è possibile usare il valore **WHITELIST** per specificare un elenco di app che *possono* usare la connessione VPN. Le app non incluse nell'elenco non si connetteranno mediante la VPN.
  1.    In **Impostazioni URI OMA** scegliere **Aggiungi**.
  2.    Immettere un nome per l'impostazione.
  3.    In **Tipo di dati** specificare **Stringa**.
  4.    Per **URI OMA** usare la stringa seguente: **./Vendor/MSFT/VPN/Profile/*nome*/Mode**, dove *nome* è il nome del profilo VPN annotato nel passaggio 1. Con il nome di esempio citato in precedenza la stringa sarà **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
  5.    In **Valore** immettere **BLACKLIST** o **WHITELIST**.



### <a name="step-3-deploy-both-policies"></a>Passaggio 3: Distribuire entrambi i criteri

È necessario distribuire *entrambi* i criteri agli *stessi* gruppi di Intune.

1.  Nell'area di lavoro **Criteri** selezionare il criterio che si vuole distribuire e quindi scegliere **Gestisci distribuzione**.
2.  Nella finestra di dialogo **Gestisci distribuzione** :
    -   **Per distribuire il criterio**, selezionare uno o più gruppi a cui distribuire il criterio, quindi scegliere **Aggiungi** > **OK**.
    -   **Per chiudere la finestra di dialogo senza distribuire il criterio**, scegliere **Annulla**.

Un riepilogo dello stato e gli avvisi visualizzati nella pagina **Panoramica** dell'area di lavoro **Criteri** consentono di identificare i problemi relativi ai criteri che richiedono attenzione. Un riepilogo dello stato viene visualizzato nell'area di lavoro **Dashboard**.
