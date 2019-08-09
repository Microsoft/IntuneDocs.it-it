---
title: Crittografare dispositivi in Microsoft Intune usando i metodi di crittografia supportati dalle piattaforme
titleSuffix: Microsoft Intune
description: Crittografare dispositivi con metodi di crittografia predefiniti, ad esempio BitLocker o FileVault, e gestire le chiavi di ripristino per tali dispositivi crittografati all'interno del portale di Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 09b5e59f4af534d4919574631568a7581bb3fba9
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2019
ms.locfileid: "68756537"
---
# <a name="use-device-encryption-with-intune"></a>Usare la crittografia dei dispositivi con Intune  

Usare Intune per gestire la crittografia predefinita di dischi o unità di dispositivi per proteggere i dati dei dispositivi stessi.  

Configurare la crittografia del disco nell'ambito del profilo di configurazione del dispositivo per Endpoint Protection. Intune supporta le piattaforme e le tecnologie di crittografia seguenti:  
- macOS: FileVault   
- Windows 10 e versioni successive: BitLocker  

Intune offre anche un [report di crittografia](encryption-monitor.md) predefinito con i dettagli sullo stato della crittografia in tutti i dispositivi gestiti.  

## <a name="filevault-encryption-for-macos"></a>Crittografia FileVault per macOS  

Usare Intune per configurare la crittografia del disco FileVault nei dispositivi che eseguono macOS. Usare quindi il report di crittografia di Intune per visualizzare i dettagli di crittografia per tali dispositivi e per gestire le chiavi di ripristino per i dispositivi crittografati con FileVault.  

FileVault è un programma di crittografia per dischi interi incluso in macOS. È possibile usare Intune per configurare FileVault nei dispositivi che eseguono **macOS 10.13 o versione successiva**.  

Per configurare FileVault, creare un [profilo di configurazione del dispositivo](device-profile-create.md) per Endpoint Protection per la piattaforma macOS. Le impostazioni di FileVault sono una delle categorie di impostazioni disponibili per Endpoint Protection di macOS.  

È quindi necessario creare criteri di crittografia dei dispositivi con FileVault. Tali criteri vengono applicati ai dispositivi in due fasi. Prima il dispositivo viene preparato in modo da consentire a Intune di recuperare la chiave di ripristino ed eseguirne il backup. Questa operazione è detta deposito. Dopo il deposito della chiave, è possibile avviare la crittografia del disco.

![Impostazioni di FileVault](./media/encrypt-devices/filevault-settings.png)

Per informazioni dettagliate sulle impostazioni di FileVault che è possibile gestire con Intune, vedere [FileVault](endpoint-protection-macos.md#filevault) nell'articolo su Intune relativo alle impostazioni di Endpoint Protection per macOS.  

### <a name="how-to-configure-macos-filevault"></a>Come configurare macOS FileVault 

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e passare a **Configurazione del dispositivo** > **Profili** > **Crea profilo**.  

2. Impostare le opzioni seguenti:  

   - Piattaforma: macOS  
   - Tipo di profilo: Endpoint Protection  

3. Selezionare **Impostazioni** > **FileVault**.  

4. Per *FileVault*selezionare **Abilita**.  

5. Per *Tipo di chiave di ripristino* è supportata solo l'opzione **Chiave personale**.  

   Considerare la possibilità di aggiungere un messaggio per facilitare agli utenti finali il recupero della chiave di ripristino del dispositivo. Queste informazioni possono essere utili per gli utenti finali se si usa l'impostazione Rotazione della chiave di ripristino personale, che periodicamente può generare in modo automatico una nuova chiave di ripristino per un dispositivo.  

   Ad esempio: per recuperare una chiave di ripristino smarrita o ruotata di recente, accedere al sito Web Portale aziendale di Intune da qualsiasi dispositivo. Nel portale passare a *Dispositivi*, selezionare il dispositivo con FileVault abilitato e quindi selezionare *Ottieni la chiave di ripristino*. Verrà visualizzata la chiave di ripristino corrente.  

6. Configurare le [impostazioni di FileVault](endpoint-protection-macos.md#filevault) rimanenti in base alle esigenze aziendali e quindi selezionare **OK**.  

   > [!IMPORTANT]  
   > Si verifica un problema noto quando **Disabilita la richiesta alla disconnessione** è impostato su *Abilita*. Quando è impostato su *Abilita*, **Numero di volte per cui è consentito ignorare** deve essere impostato su un valore e non su *Non configurato*. Se è impostato su *Non configurato*, si verifica un problema con il profilo nel dispositivo. In questo scenario **Riepilogo dello stato del profilo** è segnalato come **Errore** nel dispositivo, senza altri dettagli.
   > 
   > Quando **Disabilita la richiesta alla disconnessione** è impostato su *Non configurato*, **Numero di volte per cui è consentito ignorare** può essere impostato su *Non configurato* o avere un valore.  
   > 
   > Il problema verrà risolto in un aggiornamento futuro. 

7. Completare la configurazione delle impostazioni aggiuntive e quindi salvare il profilo.  

### <a name="manage-filevault"></a>Gestire FileVault  

Dopo che Intune ha crittografato un dispositivo macOS con FileVault, è possibile visualizzare e gestire le chiavi di ripristino di FileVault visualizzando il [report di crittografia](encryption-monitor.md) di Intune.  

## <a name="bitlocker-encryption-for-windows-10"></a>Crittografia BitLocker per Windows 10  

Usare Intune per configurare Crittografia unità BitLocker nei dispositivi che eseguono Windows 10. Usare quindi il report di crittografia di Intune per visualizzare i dettagli sulla crittografia per tali dispositivi. È anche possibile accedere a informazioni importanti per BitLocker dai dispositivi, come indicato in Azure Active Directory (Azure AD).  

BitLocker è disponibile nei dispositivi che eseguono **Windows 10 o versione successiva**.  

Configurare BitLocker quando si crea un [profilo di configurazione del dispositivo](device-profile-create.md) per Endpoint Protection per la piattaforma Windows 10 o versione successiva. Le impostazioni di BitLocker si trovano nella categoria delle impostazioni Crittografia di Windows per Endpoint Protection di Windows 10.    

![Impostazioni di BitLocker](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>Come configurare BitLocker per Windows 10  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e passare a Configurazione del dispositivo > Profili > Crea profilo.  

2. Impostare le opzioni seguenti:  
   - Piattaforma: Windows 10 e versioni successive  
   - Tipo di profilo: Endpoint Protection  

3. Selezionare **Impostazioni** > **Crittografia di Windows**.

4. Configurare le impostazioni per BitLocker in base alle esigenze aziendali e quindi selezionare **OK**.  

5. Completare la configurazione delle impostazioni aggiuntive e quindi salvare il profilo.  

### <a name="manage-bitlocker"></a>Gestire BitLocker  

Dopo che Intune ha crittografato un dispositivo Windows 10 con BitLocker, è possibile visualizzare e recuperare le chiavi di ripristino di BitLocker visualizzando il [report di crittografia](encryption-monitor.md) di Intune.  

## <a name="next-steps"></a>Passaggi successivi  

Creare criteri di [conformità dei dispositivi](compliance-policy-create-windows.md)  

Usare il report di crittografia per gestire:  
- [Chiavi di ripristino di BitLocker](encryption-monitor.md#bitlocker-recovery-keys)
- [Chiavi di ripristino di FileVault](encryption-monitor.md#filevault-recovery-keys)

Rivedere le impostazioni di crittografia che è possibile configurare con Intune per:  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
