---
title: Impostazioni di Intune Endpoint Protection per Windows 10
titleSuffix: Intune on Azure
description: "Informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni di Endpoint Protection nei dispositivi Windows 10.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4994656afcf1cdb97fdcd3877f6dabdadfb7d374
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Impostazioni di Endpoint Protection per Windows 10 e versioni successive in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il profilo di Endpoint Protection consente di controllare le funzionalità di sicurezza dei dispositivi Windows 10, ad esempio BitLocker.

Usare le informazioni in questo argomento per apprendere come creare profili di Endpoint Protection.

## <a name="create-an-endpoint-protection-profile"></a>Creare un profilo di Endpoint Protection

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere i valori di **Nome** e **Descrizione** per il profilo delle funzionalità dei dispositivi.
5. Dall'elenco a discesa **Piattaforma** selezionare **Windows 10 e versioni successive**.
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Endpoint Protection**. 
7. Nel pannello **Crittografia di Windows** configurare le impostazioni volute. I dettagli in questo argomento consentono di comprendere la funzione di ogni impostazione. Al termine, scegliere **OK**.
8. Tornare al pannello **Crea profilo** e scegliere **Crea**.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="endpoint-protection-profile-settings-reference"></a>Informazioni di riferimento sulle impostazioni dei profili di Endpoint Protection

### <a name="windows-settings"></a>Impostazioni Windows

- **Richiedi la crittografia dei dispositivi (solo desktop)**: se questa impostazione è abilitata, viene richiesto di abilitare la crittografia dei dispositivi e di confermare che non è abilitata la crittografia di alcun altro provider. Se la crittografia di Windows è attivata mentre è attivo un altro metodo di crittografia, il dispositivo potrebbe diventare instabile.
- **Richiedi la crittografia della scheda di memoria (solo dispositivi mobili)**: abilitare questa impostazione per crittografare le eventuali schede di memoria rimovibile usate dal dispositivo.


### <a name="bitlocker-base-settings"></a>Impostazioni di base di BitLocker

- **Configura i metodi di crittografia**: abilitare questa impostazione per configurare gli algoritmi di crittografia per il sistema operativo, i dati e le unità rimovibili.
    - **Crittografia per le unità del sistema operativo**: scegliere il metodo di crittografia per le unità del sistema operativo. È consigliabile usare l'algoritmo XTS-AES.
    - **Crittografia per unità dati fisse**: scegliere il metodo di crittografia per le unità dati fisse (predefinite). È consigliabile usare l'algoritmo XTS-AES.
    - **Crittografia per unità dati rimovibili**: scegliere il metodo di crittografia per le unità dati rimovibili (predefinite). Se l'unità rimovibile viene usata con dispositivi che non eseguono Windows 10, è consigliabile usare l'algoritmo AES-CBC.


### <a name="bitlocker-os-drive-settings"></a>Impostazioni delle unità del sistema operativo di BitLocker

- **Richiedi l'autenticazione aggiuntiva all'avvio** - 
    - **Blocca BitLocker nei dispositivi senza chip TPM compatibile** - 
    - **Avvio TPM**: consente di configurare se il chip TPM è consentito, non consentito o obbligatorio. 
    - **PIN di avvio TPM**: consente di configurare se l'uso di un PIN di avvio con il chip TPM è consentito, non consentito o obbligatorio. 
    - **Chiave di avvio TPM**: consente di configurare se l'uso di una chiave di avvio con il chip TPM è consentito, non consentito o obbligatorio. 
    - **Chiave di avvio e PIN TPM**: consente di configurare se l'uso di una chiave e di un PIN di avvio con il chip TPM è consentito, non consentito o obbligatorio.
- **Lunghezza minima del PIN**: abilitare questa impostazione per configurare la lunghezza minima del PIN di avvio del chip TPM.
    - **Numero minimo di caratteri**: immettere il numero di caratteri obbligatorio per il PIN di avvio, **4**-**20**.
- **Abilita il ripristino delle unità del sistema operativo**: abilitare questa impostazione per controllare la modalità di ripristino delle unità del sistema operativo protette da BitLocker se le informazioni necessarie all'avvio non sono disponibili.
    - **Consenti l'agente di recupero dati basato su certificati**: abilitare questa impostazione se si vuole che sia possibile usare gli agenti di recupero dati con unità del sistema operativo protette da BitLocker.
    - **Creazione della password di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una password di ripristino di 48 cifre.
    - **Creazione della chiave di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una chiave di ripristino a 256 bit.
    - **Nascondi le opzioni di ripristino nell'installazione guidata di BitLocker** : abilitare questa impostazione per impedire agli utenti di visualizzare o modificare le opzioni di ripristino se BitLocker è attivato.
    - **Salva le informazioni di ripristino di BitLocker in AD DS**: consente l'archiviazione delle informazioni di ripristino di BitLocker in Active Directory.
    - **Configura l'archiviazione delle informazioni di ripristino di BitLocker in AD DS**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Active Directory. È possibile scegliere tra:
        - **Backup delle password di ripristino e dei pacchetti di chiavi**
        - **Backup solo delle password di ripristino**
    - **Richiedi l'archiviazione delle informazioni di ripristino in AD DS prima di abilitare BitLocker**: abilitare questa impostazione per consentire agli utenti di attivare BitLocker solo se il dispositivo è stato aggiunto al dominio e le informazioni di ripristino di BitLocker sono state archiviate in Active Directory.
- **Abilita l'URL e il messaggio di ripristino prima dell'avvio**: abilitare questa impostazione per configurare il messaggio e l'URL visualizzati nella schermata di recupero della chiave prima dell'avvio.
    - **Messaggio di ripristino prima dell'avvio**: consente di configurare la modalità di visualizzazione del messaggio di ripristino. È possibile scegliere tra:
        - **Usa URL e messaggio di ripristino predefiniti**
        - **Usa un messaggio di ripristino e un URL vuoti**
        - **Usa messaggio di ripristino personalizzato**
        - **Usa URL di ripristino personalizzato**


### <a name="bitlocker-fixed-data-drive-settings"></a>Impostazioni delle unità dati fisse BitLocker

- **Nega l'accesso in scrittura alle unità dati fisse non protette da BitLocker**: se questa impostazione è abilitata, è necessario abilitare la protezione BitLocker per tutte le unità dati fisse o predefinite perché sia possibile scrivere all'interno di esse.
- **Abilita il ripristino delle unità fisse**: abilitare questa impostazione per controllare la modalità di ripristino delle unità fisse protette da BitLocker se le informazioni necessarie all'avvio non sono disponibili.
    - **Consenti l'agente di recupero dati**: abilitare questa impostazione se si vogliono usare gli agenti di recupero dati con unità fisse protette da BitLocker.
    - **Creazione della password di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una password di ripristino di 48 cifre.  
    - **Creazione della chiave di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una chiave di ripristino a 256 bit.
    - **Nascondi le opzioni di ripristino nell'installazione guidata di BitLocker** : abilitare questa impostazione per impedire agli utenti di visualizzare o modificare le opzioni di ripristino se BitLocker è attivato.
    - **Salva le informazioni di ripristino di BitLocker in AD DS**: consente l'archiviazione delle informazioni di ripristino di BitLocker in Active Directory.
    - **Configura l'archiviazione delle informazioni di ripristino di BitLocker in AD DS**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Active Directory. È possibile scegliere tra:
        - **Backup delle password di ripristino e dei pacchetti di chiavi**
        - **Backup solo delle password di ripristino**
    - **Richiedi l'archiviazione delle informazioni di ripristino in AD DS prima di abilitare BitLocker**: abilitare questa impostazione per consentire agli utenti di attivare BitLocker solo se il dispositivo è stato aggiunto al dominio e le informazioni di ripristino di BitLocker sono state archiviate in Active Directory.


### <a name="bitlocker-removable-data-drive-settings"></a>Impostazioni delle unità dati rimovibili BitLocker

- **Nega l'accesso in scrittura alle unità dati rimovibili non protette da BitLocker**: specificare se la crittografia BitLocker è obbligatoria per le unità di archiviazione rimovibili.
    - **Blocca l'accesso in scrittura ai dispositivi configurati in un'altra organizzazione**: specificare se è possibile scrivere nelle unità dati rimovibili che appartengono a un'altra organizzazione.



## <a name="next-steps"></a>Passaggi successivi

Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).


