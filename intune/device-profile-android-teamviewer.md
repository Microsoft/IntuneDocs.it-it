---
title: Come amministrare in remoto i dispositivi con TeamViewer
titlesuffix: Azure portal
description: Informazioni su come amministrare in remoto i dispositivi con TeamViewer."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8bb3061baf42b011c98cf7b196e939448f91cff4
ms.sourcegitcommit: bb2c181fd6de929cf1e5d3856e048d617eb72063
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/20/2017
---
# <a name="provide-remote-assistance-for-intune-managed-devices"></a>Offrire assistenza remota per dispositivi gestiti da Intune

Con Intune è possibile usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per offrire assistenza remota agli utenti di dispositivi gestiti. Usare le informazioni in questo argomento per iniziare.

## <a name="before-you-start"></a>Prima di iniziare

### <a name="supported-devices"></a>Dispositivi supportati

I dispositivi seguenti gestiti da Intune supportano l'amministrazione remota:

- Dispositivi Android gestiti da Intune
- Dispositivi Windows gestiti da Intune che eseguono Windows 10, Windows 10 Mobile e versioni successive.

>[!NOTE]
>Windows Holographic (HoloLens), Windows Team (Surface Hub) e Windows 10 S non sono supportati dal software TeamViewer



### <a name="required-permissions"></a>Autorizzazioni richieste

Verificare che all'utente del portale di Azure siano assegnate le autorizzazioni seguenti come [ruolo di Intune](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Per consentire all'amministratore di modificare le impostazioni di TeamViewer Connector, concedere l'autorizzazione **Aggiornare l'assistenza remota**.
- Per consentire all'amministratore di avviare una nuova richiesta di assistenza remota, concedere l'autorizzazione **Richiedere l'assistenza remota**. Gli utenti con l'autorizzazione **Richiedere l'assistenza remota** possono richiedere di avviare una sessione per qualsiasi utente, senza limiti derivanti dall'ambito di assegnazione del ruolo di Intune. Gli ambiti di assegnazione del ruolo di Intune non limitano i dispositivi o gli utenti per cui è possibile avviare richieste di assistenza remota.

>[!NOTE]
>Abilitando TeamViewer, si consente a TeamViewer Connector per Intune di creare sessioni di TeamViewer, leggere i dati di Active Directory e salvare il token di accesso dell'account TeamViewer.

### <a name="configure-the-intune-teamviewer-connector"></a>Configurare TeamViewer Connector per Intune

Prima di poter offrire assistenza remota ai dispositivi, è necessario configurare TeamViewer Connector per Intune, eseguendo la procedura seguente:


1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Installazione** > **TeamViewer Connector**.
5. Nel pannello **TeamViewer Connector** fare clic su **Abilita** e quindi visualizzare e accettare il contratto di licenza del servizio TeamViewer.
6. Scegliere **Accedere a TeamViewer per l'autorizzazione**.
7. Verrà visualizzata una pagina Web del sito di TeamViewer. Immettere le credenziali della licenza di TeamViewer e quindi fare clic su **Accedi**.


## <a name="how-to-remotely-administer-a-device"></a>Come amministrare in remoto un dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi** scegliere **Gestisci** > **Tutti i dispositivi**.
5. Selezionare il dispositivo che si vuole amministrare in remoto e quindi nel pannello delle proprietà del dispositivo scegliere **Altro** > **Nuova sessione di assistenza remota**.
6. Dopo la connessione di Intune al servizio TeamViewer, verranno visualizzate alcune informazioni sul dispositivo. Scegliere **Connetti** per avviare la sessione remota.

![Esempio di TeamViewer in Android](./media/android-teamviewer.png)

Nella finestra di TeamViewer è possibile eseguire una serie di azioni remote nel dispositivo, incluso il controllo remoto del dispositivo. Per informazioni dettagliate sulle azioni è possibile eseguire, vedere la [documentazione di TeamViewer](https://www.teamviewer.com/support/documents/).

Al termine, chiudere la finestra di TeamViewer.

## <a name="next-steps"></a>Passaggi successivi

Un utente finale vedrà un flag di notifica sull'icona dell'app Portale aziendale nel dispositivo e un'altra notifica all'apertura dell'app, quindi potrà accettare la richiesta di assistenza remota.

