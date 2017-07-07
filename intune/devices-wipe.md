---
title: Cancellazione completa o selettiva sui dispositivi con Intune
titleSuffix: Intune on Azure
description: "Informazioni sulle modalità per eseguire la cancellazione selettiva dei dati aziendali su un dispositivo o per eseguire la cancellazione completa per il ripristino delle impostazioni predefinite del dispositivo.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2063612ee11d2bc7915ebe4bb28c67854a2599c3
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="use-full-or-selective-wipe"></a>Usare la cancellazione completa o selettiva

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile cancellare app e dati non più necessari dai dispositivi gestiti da Intune che vengono reimpiegati o sono andati persi. A tale scopo, Intune offre funzionalità di cancellazione completa e selettiva. Gli utenti possono anche inviare un comando di cancellazione remota dei dati del dispositivo dall'app Portale aziendale di Intune nei dispositivi privati registrati in Intune.

  > [!NOTE]
  > Questo argomento riguarda solo la cancellazione dei dispositivi gestiti con la gestione dei dispositivi mobili di Intune. Anche il [portale di Azure](https://portal.azure.com) può essere usato per [cancellare i dati aziendali dalle app](https://docs.microsoft.com/intune-classic/deploy-use/wipe-managed-company-app-data-with-microsoft-intune). È anche possibile [ritirare i computer gestiti con il software client di Intune](https://docs.microsoft.com/intune-classic/deploy-use/retire-a-windows-pc-with-microsoft-intune).

## <a name="full-wipe"></a>Cancellazione completa

La **cancellazione completa** ripristina le impostazioni predefinite di un dispositivo rimuovendo tutti i dati e le impostazioni dell'azienda e dell'utente. Il dispositivo verrà rimosso da Intune. La cancellazione completa è utile per la reimpostazione di un dispositivo prima di consegnarlo a un nuovo utente o nei casi in cui il dispositivo è stato smarrito o rubato.  **Prestare attenzione alla selezione della cancellazione completa. Non sarà possibile recuperare i dati nel dispositivo**.


> [!Warning]
> I dispositivi Windows 10 RTM (ossia precedenti a Windows 10 versione 1511) con meno di 4 GB di RAM possono diventare inaccessibili se cancellati. Per accedere a un dispositivo Windows 10 che non risponde più, è possibile avviare il dispositivo da un'unità USB.


**Per eseguire la cancellazione completa (ripristino delle impostazioni predefinite) di un dispositivo**:

1.  Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.

2.  Scegliere il nome del dispositivo da cancellare.

3.  Nel pannello che mostra il nome del dispositivo scegliere **Ripristino impostazioni predefinite**, quindi scegliere **Sì** per confermare la cancellazione.

Se il dispositivo è acceso e connesso, un comando di cancellazione non richiede più di 15 minuti per propagarsi a tutti i tipi di dispositivo.

### <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Per eliminare i dispositivi nel portale di Azure Active Directory

1.  Accedere a [http://aka.ms/accessaad](http://aka.ms/accessaad) oppure fare clic su **Amministrazione** &gt; **Azure AD** da [https://portal.office.com](https://portal.office.com).

2.  Accedere con l'ID organizzazione usando il collegamento sul lato sinistro della pagina.

3.  Creare una sottoscrizione di Azure, se non se ne possiede una. Se si dispone di un account a pagamento, questa operazione non richiede l'uso di una carta di credito né un pagamento. Fare clic sul collegamento per l'abbonamento relativo alla **registrazione gratuita di Azure Active Directory**.

4.  Selezionare **Active Directory** e quindi l'organizzazione.

5.  Selezionare la scheda **Utenti** .

6.  Selezionare l'utente di cui si desidera eliminare i dispositivi.

7.  Scegliere **Dispositivi**.

8.  Rimuovere i dispositivi nel modo opportuno, ad esempio quelli che non sono più in uso o quelli con definizioni errate.


## <a name="selective-wipe"></a>Cancellazione selettiva

La **cancellazione selettiva** rimuove i dati aziendali, compresi i dati sulla gestione delle app mobili (MAM), ove applicabile, le impostazioni e i profili di posta elettronica da un dispositivo. La cancellazione selettiva lascia i dati personali dell'utente sul dispositivo. Il dispositivo verrà rimosso da Intune. Le tabelle seguenti descrivono i dati che vengono rimossi e l'effetto sui dati che rimangono nel dispositivo dopo una cancellazione selettiva. (Le tabelle sono organizzate in base alla piattaforma.)

**iOS**

|Tipo di dati|iOS|
|-------------|-------|
|App aziendali e dati associati installati da Intune|Le app vengono disinstallate e vengono rimossi i dati dell'app aziendale.<br /><br />I dati delle app Microsoft che usano la gestione delle app mobili vengono rimossi. L'app non viene rimossa.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|
|Agente di gestione|Il profilo di gestione viene rimosso.|
|Posta elettronica|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato. Se Microsoft Exchange è ospitato in locale, i profili di posta elettronica e i messaggi di posta elettronica memorizzati nella cache non vengono rimossi.|
|Outlook|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per iOS vengono rimossi.</br>Eccezione: se Exchange è ospitato in locale, i messaggi di posta elettronica non vengono rimossi.|
|Separazione di Azure Active Directory (AAD)|Il record AAD viene rimosso.|
|Contatti | I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. <br /> <br />Attualmente è supportata solo l'app Outlook.

**Android**

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
|Outlook|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per Android vengono rimossi.</br>Eccezione: se Exchange è ospitato in locale, i messaggi di posta elettronica non vengono rimossi.|I messaggi di posta elettronica ricevuti dall'app Microsoft Outlook per Android vengono rimossi.</br>Eccezione: se Exchange è ospitato in locale, i messaggi di posta elettronica non vengono rimossi.|
|Separazione di Azure Active Directory (AAD)|Il record AAD viene rimosso.|Il record AAD viene rimosso.|
|Contatti | I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. <br /> <br />Attualmente è supportata solo l'app Outlook.|I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi.  Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. <br /> <br />Attualmente è supportata solo l'app Outlook.

**Android for Work**

L'esecuzione di una cancellazione selettiva in un dispositivo Android for Work consente di rimuovere tutti i dati, le app e le impostazioni nel profilo di lavoro in tale dispositivo. Il dispositivo viene così ritirato dalla gestione con Intune. La cancellazione completa non è supportata per Android for Work.

**Windows**

|Tipo di dati|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|App aziendali e dati associati installati da Intune|Ai file protetti da EFS verrà revocata la chiave e l'utente non sarà in grado di aprire i file.|Le app aziendali non verranno rimosse.|Vengono disinstallate le app installate inizialmente tramite il portale aziendale e vengono rimossi i dati dell'app aziendale.|Le app vengono disinstallate e le chiavi di trasferimento locale vengono rimosse.|
|Impostazioni|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|Le configurazioni impostate tramite criteri di Intune non vengono più applicate e gli utenti possono modificare le impostazioni.|
|Impostazioni del profilo Wi-Fi e VPN|Rimosso.|Rimosso.|Non supportata.|Rimosso.|
|Impostazioni del profilo certificato|Certificati rimossi e revocati.|Certificati rimossi e revocati.|Non supportata.|Certificati rimossi e revocati.|
|Posta elettronica|Rimuove le applicazioni di posta elettronica abilitate per EFS, tra cui i messaggi e gli allegati dell'applicazione Posta di Windows.|Non supportata.|I profili di posta elettronica di cui viene eseguito il provisioning tramite Intune vengono rimossi e il messaggio di posta elettronica memorizzato nella cache del dispositivo viene eliminato.|Rimuove le applicazioni di posta elettronica abilitate per EFS, tra cui i messaggi e gli allegati dell'applicazione Posta di Windows. Rimuove gli account di posta elettronica di cui Intune ha effettuato il provisioning.</br>**Eccezione**: se Exchange è ospitato in locale, gli account di posta elettronica non vengono rimossi.|
|Separazione di Azure Active Directory (AAD)|No.|No.|Il record AAD viene rimosso.|Non applicabile. Windows 10 non supporta la cancellazione selettiva per dispositivi appartenenti ad Azure Active Directory.|

**Per eseguire una cancellazione selettiva**:

1.  Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.

2.  Scegliere il nome del dispositivo da cancellare.

3.  Nel pannello che mostra il nome del dispositivo scegliere **Rimuovi i da...** (abbreviazione di Rimuovi i dati aziendali), quindi scegliere **Sì** per confermare la cancellazione.

Se il dispositivo è acceso e connesso, un comando di cancellazione non richiede più di 15 minuti per propagarsi a tutti i tipi di dispositivo.
