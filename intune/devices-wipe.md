---
title: Usare il ripristino delle impostazioni predefinite oppure rimuovere i dati aziendali nei dispositivi con Intune
titlesuffix: Azure portal
description: Informazioni su come rimuovere i dati aziendali in un dispositivo o come eseguire il ripristino delle impostazioni predefinite del dispositivo.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4ee4e9b4abb99e280bf2529f9f60d295096426c0
ms.sourcegitcommit: 4e0ed4087a1e596831fa215135824ca5d38e33f7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="remove-devices-by-using-factory-reset-or-remove-company-data"></a>Rimuovere i dispositivi con il ripristino delle impostazioni predefinite o rimuovere i dati aziendali

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile rimuovere da Intune i dispositivi non più necessari, che devono essere reimpiegati o che sono andati persi. È possibile farlo eseguendo un comando di **rimozione dei dati aziendali** o di **ripristino delle impostazioni predefinite**. Gli utenti possono anche inviare un comando remoto dall'app Portale aziendale Intune ai dispositivi privati registrati in Intune.

> [!NOTE]
> Prima di rimuovere un utente da Azure Active Directory, inviare un comando di **ripristino delle impostazioni predefinite** o di **rimozione dei dati aziendali** a tutti i dispositivi associati all'utente. Se si rimuovono utenti con dispositivi gestiti da Azure Active Directory, Intune non può più inviare il comando di ripristino delle impostazioni predefinite o di rimozione dei dati aziendali a tali dispositivi.

## <a name="factory-reset"></a>Ripristino delle impostazioni di fabbrica

Il **ripristino delle impostazioni predefinite** consente di reimpostare le impostazioni di fabbrica di un dispositivo, rimuovendo tutti i dati e le impostazioni aziendali e dell'utente. Il dispositivo viene rimosso dalla gestione di Intune. Il ripristino delle impostazioni predefinite è utile per reimpostare un dispositivo prima di consegnarlo a un nuovo utente o nei casi in cui il dispositivo è stato smarrito o rubato. Prestare attenzione quando si seleziona il ripristino delle impostazioni predefinite. Non sarà possibile recuperare i dati nel dispositivo.

### <a name="to-factory-reset-a-device"></a>Per ripristinare le impostazioni predefinite di un dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
4. Scegliere il nome del dispositivo di cui si vuole eseguire il ripristino delle impostazioni predefinite.
5. Nel pannello che mostra il nome del dispositivo scegliere **Ripristino delle impostazioni predefinite**
6. Per Windows 10 versione 1709 o successiva, è disponibile l'opzione aggiuntiva "Mantieni lo stato della registrazione e l'account utente". 
    
    |Mantenuti tramite ripristino delle impostazioni predefinite|Non mantenuti|
    | -------------|------------|
    |Account utente associati al dispositivo|File dell'utente|
    |Stato del computer \(aggiunto a un dominio, aggiunto ad Azure Active Directory)| App installate dell'utente \(app dello Store e Win32)|
    |Registrazione MDM|Impostazioni del dispositivo non predefinite|
    |App installate OEM \(app dello Store e Win32)||
    |Profilo utente||
    |Dati utente esterni al profilo utente||
    |Accesso automatico dell'utente|| 
    
         
7. Scegliere **Sì** per confermare il ripristino delle impostazioni predefinite.

Se il dispositivo è acceso e connesso, un comando di ripristino delle impostazioni predefinite non richiede più di 15 minuti per propagarsi a tutti i tipi di dispositivo.

## <a name="remove-company-data"></a>Rimuovere i dati aziendali

Il comando **Rimuovi i dati aziendali** consente di rimuovere i dati delle app (se applicabile), le impostazioni e i profili di posta elettronica assegnati tramite Intune. La rimozione dei dati aziendali lascia i dati personali dell'utente nel dispositivo. Il dispositivo viene rimosso dalla gestione di Intune. Le tabelle seguenti descrivono i dati che vengono rimossi e l'effetto sui dati che rimangono nel dispositivo dopo la rimozione dei dati aziendali.

### <a name="ios"></a>iOS

|Tipo di dati|iOS|
|-------------|-------|
|App aziendali e dati associati installati da Intune|Le app vengono disinstallate e vengono rimossi i dati dell'app aziendale.<br /><br />I dati delle app Microsoft che usano la gestione delle app mobili vengono rimossi. L'app non viene rimossa.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|
|Agente di gestione|Il profilo di gestione viene rimosso.|
|Posta elettronica|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato.|
|Outlook|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per iOS vengono rimossi.|
|Separazione di Azure Active Directory (AD)|Il record di Azure AD viene rimosso.|
|Contatti | I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere rimossi. <br /> <br />Attualmente è supportata solo l'app Outlook.

### <a name="android"></a>Android

|Tipo di dati|Android|Android Samsung KNOX Standard|
|-------------|-----------|------------------------|
|Collegamenti Web|Rimosso.|Rimosso.|
|App Google Play non gestite|Le app e i dati rimangono installati.|Le app e i dati rimangono installati.|
|App line-of-business non gestite|Le app e i dati rimangono installati.|Le app vengono disinstallate e, di conseguenza, i dati locali delle app vengono rimossi. Non vengono rimossi dati esterni all'app, ad esempio quelli in una scheda SD.|
|App Google Play gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e sono inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati, ma non vengono rimossi.|
|App line-of-business gestite|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e sono inutilizzabili, ma non vengono rimossi.|I dati dell'app vengono rimossi. L'app non viene rimossa. I dati protetti dalla crittografia MAM all'esterno dell'app (ad esempio, in una scheda SD) restano crittografati e sono inutilizzabili, ma non vengono rimossi.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|
|Impostazioni del profilo certificato|Certificati revocati, ma non rimossi.|Certificati rimossi e revocati.|
|Agente di gestione|Il privilegio di amministratore del dispositivo viene revocato.|Il privilegio di amministratore del dispositivo viene revocato.|
|Posta elettronica|n/a (i profili di posta elettronica non sono supportati dai dispositivi Android)|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato.|
|Outlook|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per Android vengono rimossi.|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per Android vengono rimossi.|
|Separazione di Azure Active Directory (AD)|Il record di Azure AD viene rimosso.|Il record di Azure AD viene rimosso.|
|Contatti | I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere rimossi. <br /> <br />Attualmente è supportata solo l'app Outlook.|I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere rimossi. <br /> <br />Attualmente è supportata solo l'app Outlook.

### <a name="android-for-work"></a>Android for Work

La rimozione dei dati aziendali da un dispositivo Android for Work consente di rimuovere tutti i dati, le app e le impostazioni nel profilo di lavoro in tale dispositivo. Il dispositivo viene così ritirato dalla gestione con Intune. Il ripristino delle impostazioni predefinite non è supportato per Android for Work.

### <a name="windows"></a>Windows

|Tipo di dati|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|App aziendali e dati associati installati da Intune|Ai file protetti da EFS verrà revocata la chiave e l'utente non sarà in grado di aprire i file.|Le app aziendali non verranno rimosse.|Vengono disinstallate le app installate inizialmente tramite il portale aziendale e vengono rimossi i dati dell'app aziendale.|Le app vengono disinstallate e le chiavi di trasferimento locale vengono rimosse.<br>Per Windows 10 versione 1703 (Creators Update) e versioni successive, le app di Office 365 ProPlus non vengono rimosse.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|Non supportata.|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|Certificati rimossi e revocati.|Non supportata.|Certificati rimossi e revocati.|
|Posta elettronica|Rimuove le applicazioni di posta elettronica abilitate per EFS, tra cui i messaggi e gli allegati dell'applicazione Posta di Windows.|Non supportata.|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato.|Rimuove le applicazioni di posta elettronica abilitate per EFS, tra cui i messaggi e gli allegati dell'applicazione Posta di Windows. Rimuove gli account di posta elettronica di cui Intune ha effettuato il provisioning.|
|Separazione di Azure Active Directory (AD)|No.|No.|Il record di Azure AD viene rimosso.|Non applicabile. Windows 10 non supporta la rimozione dei dati aziendali per dispositivi appartenenti ad Azure Active Directory.|

### <a name="to-remove-company-data"></a>Per rimuovere i dati aziendali

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
4. Scegliere il nome del dispositivo da cui si vuole rimuovere i dati aziendali.
5. Nel pannello che mostra il nome del dispositivo scegliere **Rimuovi i dati aziendali** e quindi scegliere **Sì** per confermare.

Se il dispositivo è acceso e connesso, un comando di rimozione dei dati non richiede più di 15 minuti per propagarsi a tutti i tipi di dispositivo.

## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Eliminare dispositivi dal portale di Azure Active Directory

A causa di problemi di comunicazione o dispositivi mancanti, potrebbe essere necessario eliminare dispositivi da Azure Active Directory (AD). Il comando di eliminazione non rimuove un dispositivo dalla gestione, ma è possibile usare **Elimina** per rimuovere dal portale di Azure i record dei dispositivi che si è certi siano irraggiungibili oppure che molto probabilmente non comunicheranno più con Azure.

1.  Accedere ad [Azure Active Directory nel portale di Azure](http://aka.ms/accessaad) con le credenziali di amministratore. È anche possibile accedere al [portale di Office 365](https://portal.office.com) e quindi scegliere **Amministrazione** &gt; **Azure AD** usando il collegamento sul lato sinistro della pagina.
3.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si dispone di un account a pagamento, questa operazione non richiede l'uso di una carta di credito né un pagamento. Fare clic sul collegamento per l'abbonamento relativo alla **registrazione gratuita di Azure Active Directory**.
4.  Selezionare **Active Directory** e quindi l'organizzazione.
5.  Selezionare la scheda **Utenti** .
6.  Selezionare l'utente di cui si desidera eliminare i dispositivi.
7.  Scegliere **Dispositivi**.
8.  Rimuovere i dispositivi nel modo opportuno, ad esempio quelli che non sono più in uso o quelli con definizioni errate.
