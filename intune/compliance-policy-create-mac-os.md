---
title: "Come creare i criteri di conformità per macOS"
titleSuffix: Azure portal
description: "Informazioni sulle modalità di creazione dei criteri di conformità per i dispositivi macOS.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0444183e-f924-4605-96a8-48fdfbc58fd1
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3cf085ff2ee4668ea4c14718719c466bcb982b10
ms.sourcegitcommit: d4623cbfe296ae370c3d88c3213fffbda255e474
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="create-a-device-compliance-policy-for-macos-devices-with-intune"></a>Creare criteri di conformità per i dispositivi macOS con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="before-you-begin"></a>Prima di iniziare

Prima di creare e assegnare i criteri di conformità dei dispositivi, esaminare i concetti relativi ai criteri di conformità dei dispositivi in Intune.

- Per altre informazioni sui criteri di conformità dei dispositivi, vedere [Introduzione alla conformità dei dispositivi in Intune](device-compliance.md).

> [!IMPORTANT]
> È necessario creare criteri di conformità per ogni piattaforma. Le impostazioni dei criteri di conformità dei dispositivi in Intune dipendono dalle funzionalità della piattaforma, che sono impostazioni esposte tramite il protocollo di gestione dei dispositivi mobili.

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

-------------------------------


| **Impostazione di criteri** | **macOS 10.11 e versioni successive** |
| --- | --- |
| **Configurazione di PIN o password** | Corretto |   
| **Crittografia dispositivo** | Corretto (impostando il PIN) |
| **Profilo di posta elettronica** | In quarantena |
|**Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** | In quarantena |  
| **Attestazione dell'integrità di Windows** | Non applicabile |  
----------------------------


**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="macos-compliance-policy-settings"></a>Impostazioni dei criteri di conformità MacOS

Quando si crea un nuovo criterio di conformità dei dispositivi con Intune è possibile scegliere tra diverse categorie con varie impostazioni:

- Integrità del dispositivo

- Proprietà dispositivo

- Protezione del sistema

### <a name="device-health"></a>Integrità del dispositivo

- **Richiedi la protezione dell'integrità del sistema**: impostare su **Rendi obbligatorio** per verificare se nei dispositivi macOS sia già stata abilitata la protezione dell'integrità del sistema.

### <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse aziendali.

- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali è bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.

### <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

#### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: impostare l'opzione su **Rendi obbligatorio** per richiedere agli utenti di immettere una password prima di poter accedere al dispositivo.

- **Password semplici**: impostare questa opzione su **Blocca** per impedire all'utente di creare una password semplice come **1234** o **1111**.

- **Lunghezza minima password**: specifica il numero minimo di cifre o caratteri per la password.

- **Tipo di password**: specificare se l'utente deve creare una password di tipo **Alfanumerico** o **Numerico**.

- **Number of non-alphanumeric character in password** (Numero di caratteri non alfanumerici nella password): se **Tipo di password richiesto** è impostato su **Alfanumerico**, usare questa impostazione per specificare il numero minimo di set di caratteri che la password deve avere. 

    > [!NOTE]
    > Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

    > [!IMPORTANT]
    > Per i dispositivi macOS, questa impostazione si riferisce al numero di caratteri speciali (ad esempio **!** , **#** , **&amp;** ) che è necessario includere nella password.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: specifica il tempo di inattività prima che l'utente debba immettere di nuovo la password.

- **Scadenza password (giorni)**: selezionare la durata in giorni della password (tra 1 e 250). Dopo questo periodo di tempo, gli utenti devono crearne una nuova.

- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non possono essere riutilizzate.

    > [!IMPORTANT]
    > Quando cambiano i requisiti per le password in un dispositivo macOS, la modifica diventa effettiva al successivo cambiamento della password da parte dell'utente. Ad esempio, se si imposta il limite di lunghezza della password a otto cifre e il dispositivo macOS usa attualmente una password a 6 cifre, il dispositivo rimane conforme fino a quando l'utente non aggiorna la password nel dispositivo.

## <a name="to-create-a-device-compliance-policy"></a>Per creare i criteri di conformità dei dispositivi

1. Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune.

2. Dopo l'accesso viene visualizzato il **dashboard di Azure**.

3. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

4. Scegliere **Intune**. Verrà visualizzato il **dashboard di Intune**.

5. Scegliere **Conformità del dispositivo** e quindi scegliere **Criteri** in **Gestisci**.

6. Scegliere **Crea criterio**.

7. Digitare un nome e una descrizione, quindi scegliere la piattaforma a cui si desidera applicare questi criteri.

8. Viene visualizzato il pannello **macOS compliance policy** (Criteri di conformità macOS). Scegliere le categorie di impostazioni di conformità del dispositivo **Sicurezza**, **Integrità del dispositivo** e **Proprietà del dispositivo** per specificare le impostazioni.

10. Dopo aver scelto le impostazioni, scegliere **OK** in ogni categoria di impostazioni di conformità del dispositivo.

11. Scegliere **OK** e quindi fare clic su **Crea**.

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

Per assegnare agli utenti i criteri di conformità, scegliere un criterio configurato. I criteri esistenti sono disponibili nel pannello **Criteri di conformità**.

1. Scegliere i criteri di conformità del dispositivo da assegnare agli utenti e quindi selezionare **Assegnazioni**. Si apre il pannello da cui è possibile selezionare i **Gruppi di sicurezza Azure Active Directory** e assegnarli ai criteri.

2. Scegliere **Seleziona gruppi** per aprire il pannello che consente di visualizzare i gruppi di sicurezza di Azure AD.

3. Scegliere **Selezione** e quindi **Salva** per assegnare i criteri di conformità del dispositivo ai gruppi di sicurezza di Azure AD.

4. Dopo aver completato l'assegnazione dei criteri di conformità del dispositivo ai gruppi, è possibile chiudere il pannello **Assegnazioni**.

    > [!TIP]
    > Per impostazione predefinita, i dispositivi verificano la conformità ogni 8 ore, ma gli utenti possono forzare il processo tramite l'app Portale aziendale di Intune.

## <a name="next-steps"></a>Passaggi successivi

[Come monitorare i criteri di conformità dei dispositivi](compliance-policy-monitor.md)
