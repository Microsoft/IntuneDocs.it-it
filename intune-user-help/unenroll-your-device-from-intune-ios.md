---
title: Rimuovere il dispositivo iOS da Intune | Microsoft Docs
description: Descrive come rimuovere un dispositivo iOS da Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: bd5384945158f3d0ef3035eaf9bc2f8375d8b153
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859016"
---
# <a name="remove-your-ios-device-from-intune"></a>Rimuovere il dispositivo iOS da Intune

Quando il dispositivo iOS viene rimosso da Intune, il dispositivo non potrà più accedere alle risorse aziendali né verrà più gestito da Intune.


## <a name="removing-the-device-from-my-devices"></a>Rimozione del dispositivo da Dispositivi personali

Per rimuovere il dispositivo da Intune, seguire questa procedura o guardare il video:


1. Nell'app Portale aziendale toccare **Dispositivi** e selezionare il dispositivo di cui annullare la registrazione. Se toccando **Dispostivi** viene visualizzato un solo dispositivo, si accede direttamente alla schermata dei dettagli di quel dispositivo.

2. Toccare i puntini di sospensione accanto a **RINOMINA** > **Rimuovi dispositivo** > **Rimuovi**.  

    |![Screenshot della schermata Dispositivi nell'app Portale aziendale, con le opzioni possibili dopo che è stato selezionato Rimuovi. Vengono illustrati i pulsanti "Rimuovi dispositivo", "Ripristino delle impostazioni predefinite" e "Annulla".](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![Screenshot della schermata Dispositivi nell'app Portale aziendale, con le opzioni possibili dopo che è stato selezionato il pulsante Rimuovi dispositivo. Vengono illustrati il pulsante "Rimuovi" evidenziato in rosso e i pulsanti "Altre informazioni" e "Annulla" evidenziati in blu.](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


    Quando si annulla la registrazione del dispositivo da Intune, si verificano gli eventi seguenti:

    - Il dispositivo non verrà più visualizzato nel portale aziendale.

    - Non sarà più possibile installare app dal portale aziendale.

    - Le impostazioni modificate nel dispositivo quando è stato aggiunto, ad esempio la disattivazione della fotocamera o la richiesta di una password di una certa lunghezza, non sono più valide.

    - Dal dispositivo potrebbe non essere più possibile accedere ad alcune risorse della società, quali condivisioni di file o siti Web interni.

    - Non è più possibile usare app aziendali e dati aziendali sul dispositivo.

    - Potrebbe non essere più possibile connettersi alla rete aziendale usando il Wi-Fi o una rete privata virtuale (VPN).

    - I profili di posta elettronica aziendale vengono rimossi dal dispositivo.

    - I dispositivi configurati solo per la posta elettronica non verranno più visualizzati nel sito Web o nell'app Portale aziendale.

    - Le app vengono disinstallate e vengono rimossi i dati dell'app aziendale.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Rimozione dei dati raccolti dall'app Portale aziendale

Il Portale aziendale archivia i dati locali in tre posizioni del dispositivo.

- **Log informazioni**: i dati sulle attività dell'app standard raccolti da Microsoft, ad esempio per quanto tempo l'app restava aperta o se si arresta in modo anomalo, vengono automaticamente cancellati quando si rimuove il dispositivo dal Portale aziendale.

- **Analisi di Apple**: dati sulle attività di arresto anomalo dell'app standard raccolti da Apple. Queste informazioni possono essere rimosse soltanto ripristinando il dispositivo sulle impostazioni predefinite. Questa operazione cancellerà tutte le informazioni personali sul dispositivo. A tale scopo, aprire **Impostazioni** > **Generale** > **Ripristina** > **Erase All Content and Settings** (Cancella tutti i contenuti e tutte le impostazioni).

- **Keychain**: il dispositivo archivia le password e altre informazioni usate per accedere al keychain. Le app Microsoft condividono le informazioni di accesso con qualsiasi app sviluppata da Microsoft disponibile nel dispositivo, ad esempio Microsoft Outlook e Microsoft Authenticator. Come per Analisi di Apple, queste informazioni possono essere rimosse soltanto ripristinando il dispositivo sulle impostazioni predefinite. Questa operazione cancellerà tutte le informazioni personali sul dispositivo. A tale scopo, aprire **Impostazioni** > **Generale** > **Ripristina** > **Erase All Content and Settings** (Cancella tutti i contenuti e tutte le impostazioni).


Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
