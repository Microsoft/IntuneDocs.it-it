---
# required metadata

title: Scegliere come gestire i dispositivi | Microsoft Intune
description:
keywords:
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Scegliere come gestire i dispositivi
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] consente di gestire una gamma di dispositivi *registrandoli* nel servizio. Gli utenti possono quindi usare un *portale aziendale* per eseguire una serie di operazioni, ad esempio registrare il dispositivo, cercare e installare app, verificare la conformità del dispositivo ai criteri aziendali e contattare il supporto.

## Modi di gestione dei dispositivi mobili
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] può gestire le piattaforme dei dispositivi seguenti:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Suggerimento</h5>
  <p>I dispositivi registrati precedentemente che eseguono una versione di iOS precedente alla versione supportata rimarranno registrati. Vedere la documentazione per ogni [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per assicurarsi che la versione di iOS sia supportata dalla funzionalità.</p>
</div>

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] può gestire i dispositivi degli utenti noti come dispositivi BYOD (Bring Your Own Device). Può anche gestire i dispositivi di proprietà dell’azienda, anche nei casi in cui l'azienda fornisce un elenco di dispositivi tra cui gli utenti possono scegliere, noto come CYOD (Choose Your Own Device).

### Registrazione dei dispositivi nella gestione
I dispositivi mobili con sistemi operativi come iOS, Android e Windows Phone devono essere registrati sempre. Tuttavia, il modo in cui i dispositivi vengono registrati dipende dalle esigenze dell'azienda:

|Tipo di registrazione|BYOD|CYOD|Dispositivo condiviso con account manager|Dispositivo condiviso senza account utente|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Descrizione**|Dispositivo personale registrato tramite Microsoft Intune|Dispositivo di proprietà dell'azienda per utente singolo|Dispositivo di proprietà dell'azienda gestito con un account di gestione condiviso da più utenti|Dispositivo di proprietà dell'azienda senza utente associato e usato da molti utenti.|
|**Utente del dispositivo**|Owner|Utente assegnato|Nessun account utente specifico|Nessun utente specifico|
|**Utente che effettua la registrazione**|Owner|Amministratore|Gestione dispositivi|Qualsiasi utente|
|**Utente che annulla la registrazione**|Proprietario o amministratore|Amministratore|Amministratore|Amministratore|
|**Utente che può reimpostare**|Proprietario o amministratore|Amministratore|Amministratore|Amministratore|

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Suggerimento</h5>
  <p>Per un elenco completo delle funzionalità offerte dalla registrazione dei dispositivi, vedere [Funzionalità di gestione dei dispositivi mobili](mobile-device-management-capabilities-in-microsoft-intune.md).</p>
</div>



## Modi di gestione di PC Windows
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] può gestire PC che eseguono Windows Vista e versioni successive di Windows tramite il client computer Intune. Tuttavia, per i PC Windows è possibile scegliere di registrarli o di installare il software client per PC di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] che offre alcune funzionalità non disponibili durante la registrazione dei dispositivi. Nella maggior parte dei casi, il dispositivo Windows viene registrato con Intune che offre un maggior numero di funzionalità rispetto al client computer.

È consigliabile usare il client computer Intune per:
<ul>
<li>Usare qualsiasi funzionalità del client computer Microsoft Intune per gestire i PC Windows.</li>
<li>Gestire un PC Windows che esegue un sistema operativo non supportato per la registrazione.</li>
</ul>

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Suggerimento</h5>
  <p>Per un elenco completo delle funzionalità offerte dall'installazione del client computer Intune su PC Windows supportati, vedere [Funzionalità di gestione di PC Windows](windows-pc-management-capabilities-in-microsoft-intune.md).</p>
</div>

## Gestione di Exchange ActiveSync
È anche possibile gestire i dispositivi con Exchange ActiveSync. A tale scopo è necessario installare On-Premises Connector o usare Service to Service Connector incorporato per connettersi a Exchange Server.

Per altre informazioni sui requisiti hardware e software per l'installazione di On-Premises Connector, vedere [Requirements for the On-Premises Connector](../deploy-use/intune-on-premises-exchange-connector#requirements-for-the-on-premises-connector) (Requisiti per On-Premises Connector).

Per informazioni sull'uso di On-Premises Connector o di Service to Service Connector con Exchange, vedere [Gestione dei dispositivi mobili con Exchange ActiveSync e Intune](../deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).



## Passaggi successivi
Si sono apprese alcune funzionalità che è possibile usare per la registrazione dei dispositivi in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. È ora necessario [registrare i dispositivi](../deploy-use/enroll-devices-in-microsoft-intune). Dopo aver registrato i dispositivi, sarà possibile usare tutte le funzionalità descritte in questo argomento. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->


<!--HONumber=May16_HO4-->


