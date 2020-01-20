---
title: Crittografare i dispositivi con il metodo di crittografia supportato dalle piattaforme
titleSuffix: Microsoft Intune
description: Crittografare dispositivi con metodi di crittografia predefiniti, ad esempio BitLocker o FileVault, e gestire le chiavi di ripristino per tali dispositivi crittografati all'interno del portale di Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5209ce7fba30a156de055503751104f9090d49d7
ms.sourcegitcommit: e7052114324b80d0503b107c934bb90b8eb29704
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75756010"
---
# <a name="use-device-encryption-with-intune"></a>Usare la crittografia dei dispositivi con Intune

Usare Intune per gestire la crittografia predefinita di dischi o unità di dispositivi per proteggere i dati dei dispositivi stessi.

Configurare la crittografia del disco nell'ambito del profilo di configurazione del dispositivo per Endpoint Protection. Intune supporta le piattaforme e le tecnologie di crittografia seguenti:

- macOS: FileVault
- Windows 10 e versioni successive: BitLocker

Intune offre anche un [report di crittografia](encryption-monitor.md) predefinito con i dettagli sullo stato della crittografia in tutti i dispositivi gestiti.

## <a name="filevault-encryption-for-macos"></a>Crittografia FileVault per macOS

Usare Intune per configurare la crittografia del disco FileVault nei dispositivi che eseguono macOS. Usare quindi il report di crittografia di Intune per visualizzare i dettagli di crittografia per tali dispositivi e per gestire le chiavi di ripristino per i dispositivi crittografati con FileVault.

Si noti che la registrazione del dispositivo approvata dall'utente è necessaria per il funzionamento di FileVault nel dispositivo stesso. L'utente deve approvare manualmente il profilo di gestione dalle preferenze di sistema perché la registrazione sia considerata approvata dall'utente. 

FileVault è un programma di crittografia per dischi interi incluso in macOS. È possibile usare Intune per configurare FileVault nei dispositivi che eseguono **macOS 10.13 o versione successiva**.

Per configurare FileVault, creare un [profilo di configurazione del dispositivo](../configuration/device-profile-create.md) per Endpoint Protection per la piattaforma macOS. Le impostazioni di FileVault sono una delle categorie di impostazioni disponibili per Endpoint Protection di macOS.

È quindi necessario creare criteri di crittografia dei dispositivi con FileVault. Tali criteri vengono applicati ai dispositivi in due fasi. Prima il dispositivo viene preparato in modo da consentire a Intune di recuperare la chiave di ripristino ed eseguirne il backup. Questa operazione è detta deposito. Dopo il deposito della chiave, è possibile avviare la crittografia del disco.

![Impostazioni di FileVault](./media/encrypt-devices/filevault-settings.png)

Per informazioni dettagliate sulle impostazioni di FileVault che è possibile gestire con Intune, vedere [FileVault](endpoint-protection-macos.md#filevault) nell'articolo su Intune relativo alle impostazioni di Endpoint Protection per macOS.

### <a name="how-to-configure-macos-filevault"></a>Come configurare macOS FileVault

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. Impostare le opzioni seguenti:

   - Piattaforma: macOS
   - Tipo di profilo: Protezione degli endpoint

4. Selezionare **Impostazioni** > **FileVault**.

5. Per *FileVault*selezionare **Abilita**.

6. Per *Tipo di chiave di ripristino* è supportata solo l'opzione **Chiave personale**.

   Considerare la possibilità di aggiungere un messaggio per facilitare agli utenti finali il recupero della chiave di ripristino del dispositivo. Queste informazioni possono essere utili per gli utenti finali se si usa l'impostazione Rotazione della chiave di ripristino personale, che periodicamente può generare in modo automatico una nuova chiave di ripristino per un dispositivo.

   Ad esempio: per recuperare una chiave di ripristino smarrita o ruotata di recente, accedere al sito Web Portale aziendale di Intune da qualsiasi dispositivo. Nel portale passare a *Dispositivi*, selezionare il dispositivo con FileVault abilitato e quindi selezionare *Ottieni la chiave di ripristino*. Verrà visualizzata la chiave di ripristino corrente.

7. Configurare le [impostazioni di FileVault](endpoint-protection-macos.md#filevault) rimanenti in base alle esigenze aziendali e quindi selezionare **OK**.

  8. Completare la configurazione delle impostazioni aggiuntive e quindi salvare il profilo.  

### <a name="manage-filevault"></a>Gestire FileVault

Dopo che Intune ha crittografato un dispositivo macOS con FileVault, è possibile visualizzare e gestire le chiavi di ripristino di FileVault visualizzando il [report di crittografia](encryption-monitor.md) di Intune.

Dopo che Intune ha crittografato un dispositivo macOS con FileVault, è possibile visualizzare la chiave di ripristino personale di tale dispositivo dal Portale aziendale Web in qualsiasi dispositivo. Nel Portale aziendale Web scegliere il dispositivo macOS crittografato e quindi scegliere "Ottieni la chiave di ripristino" come azione del dispositivo remoto.

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>Recuperare la chiave di ripristino personale dai dispositivi macOS crittografati MEM

Gli utenti finali possono recuperare la propria chiave di ripristino personale (chiave di FileVault) usando l'app Portale aziendale iOS. Il dispositivo con la chiave di ripristino personale deve essere registrato in Intune e crittografato con FileVault in Intune. Con l'app Portale aziendale iOS l'utente finale può aprire una pagina Web che include la chiave di ripristino personale di FileVault. La chiave di ripristino può essere recuperata anche da Intune selezionando **Dispositivi** > *il dispositivo macOS crittografato e registrato* > **Ottieni la chiave di ripristino**. 

## <a name="bitlocker-encryption-for-windows-10"></a>Crittografia BitLocker per Windows 10

Usare Intune per configurare Crittografia unità BitLocker nei dispositivi che eseguono Windows 10. Usare quindi il report di crittografia di Intune per visualizzare i dettagli sulla crittografia per tali dispositivi. È anche possibile accedere a informazioni importanti per BitLocker dai dispositivi, come indicato in Azure Active Directory (Azure AD).

BitLocker è disponibile nei dispositivi che eseguono **Windows 10 o versione successiva**.

Configurare BitLocker quando si crea un [profilo di configurazione del dispositivo](../configuration/device-profile-create.md) per Endpoint Protection per la piattaforma Windows 10 o versione successiva. Le impostazioni di BitLocker si trovano nella categoria delle impostazioni Crittografia di Windows per Endpoint Protection di Windows 10.

![Impostazioni di BitLocker](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Come configurare BitLocker per Windows 10

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. Impostare le opzioni seguenti:

   - Piattaforma: Windows 10 e versioni successive
   - Tipo di profilo: Protezione degli endpoint

4. Selezionare **Impostazioni** > **Crittografia di Windows**.

5. Configurare le impostazioni per BitLocker in base alle esigenze aziendali e quindi selezionare **OK**.

6. Completare la configurazione delle impostazioni aggiuntive e quindi salvare il profilo.

### <a name="manage-bitlocker"></a>Gestire BitLocker

Dopo che Intune ha crittografato un dispositivo Windows 10 con BitLocker, è possibile visualizzare e recuperare le chiavi di ripristino di BitLocker visualizzando il [report di crittografia](encryption-monitor.md) di Intune.

### <a name="rotate-bitlocker-recovery-keys"></a>Ruotare le chiavi di ripristino di BitLocker

È possibile usare un'azione del dispositivo Intune per ruotare in modalità remota la chiave di ripristino di BitLocker di un dispositivo che esegue Windows 10 versione 1909 o successiva.

#### <a name="prerequisites"></a>Prerequisiti

Per supportare la rotazione della chiave di ripristino di BitLocker, è necessario che i dispositivi soddisfino i seguenti prerequisiti:

- I dispositivi devono eseguire Windows 10 versione 1909 o successiva

- Per i dispositivi aggiunti ad Azure AD e ad AD ibrido, il supporto per la rotazione delle chiavi deve essere abilitato:

  - **Rotazione delle password di ripristino basata su client**

  Questa impostazione è disponibile nella *crittografia di Windows* come parte di un criterio di configurazione del dispositivo per Windows 10 Endpoint Protection.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>Per ruotare la chiave di ripristino di BitLocker

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Tutti i dispositivi**.

3. Nell'elenco dei dispositivi gestiti selezionare un dispositivo, selezionare **Altro** e quindi selezionare l'azione remota del dispositivo **Rotazione delle chiavi BitLocker**.

## <a name="next-steps"></a>Passaggi successivi

Creare criteri di [conformità dei dispositivi](compliance-policy-create-windows.md).

Usare il report di crittografia per gestire:

- [Chiavi di ripristino di BitLocker](encryption-monitor.md#bitlocker-recovery-keys)
- [Chiavi di ripristino di FileVault](encryption-monitor.md#filevault-recovery-keys)

Rivedere le impostazioni di crittografia che è possibile configurare con Intune per:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
