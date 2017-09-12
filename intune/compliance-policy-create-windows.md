---
title: "Come creare un criterio di conformità per Windows"
titleSuffix: Azure portal
description: "Informazioni sulle modalità di creazione dei criteri di conformità per i dispositivi Windows.\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 13fc7783-d4de-47d0-b1b8-4c8710a9e6ab
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 76d1bb091553fbe5a1220c818289f59f4ef4100b
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-windows-devices-in-intune"></a>Come creare i criteri di conformità per i dispositivi Windows in Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I criteri di conformità vengono creati per ogni piattaforma.  È possibile creare i criteri di conformità nel portale di Azure. Per altre informazioni sui criteri di conformità consultare l'argomento [What is a device compliance](device-compliance.md)(Che cos'è la conformità dei dispositivi). Per altre informazioni sui prerequisiti che è necessario soddisfare prima di creare i criteri di conformità, consultare l'argomento [Get started with device compliance](device-compliance-get-started.md) (Introduzione alla conformità dei dispositivi).

La tabella seguente descrive il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

---------------------------

| **Impostazione di criteri** | **Windows 8.1 e versioni successive** | **Windows Phone 8.1 e versioni successive** |
|----| ----| --- |
| **Configurazione di PIN o password** | Corretto | Corretto |   
| **Crittografia dispositivo** | Non applicabile | Corretto |   
| **Dispositivo jailbroken o rooted** | Non applicabile | Non applicabile |  
| **Profilo di posta elettronica** | Non applicabile | Non applicabile |   
| **Versione minima del sistema operativo** | In quarantena | In quarantena |   
| **Versione massima del sistema operativo** | In quarantena | In quarantena |   
| **Attestazione dell'integrità di Windows** | In quarantena: Windows 10 e Windows 10 Mobile|Non applicabile: Windows 8.1 |

-------------------------------

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)+

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:+

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Creare i criteri di conformità nel portale di Azure

1. Dal pannello **Intune** scegliere **Imposta la conformità dei dispositivi**. In **Gestisci** scegliere **All device compliance policies** (Tutti i criteri di conformità dei dispositivi) e scegliere **Crea**.
2. Digitare un nome e una descrizione, quindi scegliere la piattaforma a cui si desidera applicare questi criteri.
3. Scegliere **Requisiti per la conformità** per aprire il relativo pannello.  È possibile specificare le impostazioni **Protezione**, **Integrità del dispositivo** e **Proprietà del dispositivo**. Al termine, scegliere **OK**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

Per assegnare agli utenti i criteri di conformità, scegliere un criterio configurato. I criteri esistenti sono reperibili nel pannello **Criteri di conformità**.

1. Scegliere il criterio da assegnare agli utenti, quindi selezionare **Assegnazioni**. Si apre il pannello da cui è possibile selezionare i **Gruppi di sicurezza Azure Active Directory** e assegnarli ai criteri.
2. Scegliere **Seleziona gruppi** per aprire il pannello che consente di visualizzare i gruppi di sicurezza di Azure AD.  Se si sceglie **Seleziona** il criterio verrà distribuito agli utenti.

Il criterio è stato applicato agli utenti.  I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password per poter accedere al dispositivo.
- **Consenti password semplici:** impostare l'opzione su **Sì** per consentire agli utenti di creare password semplici come "**1234**" o "**1111**".
- **Lunghezza minima password**: specificare il numero minimo di cifre o caratteri che la password dell'utente deve contenere.
- **Tipo di password richiesto:** specificare se gli utenti devono creare una password **alfanumerica** o **numerica**.

Per i dispositivi che eseguono Windows e prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida se la lunghezza minima della password è maggiore di otto caratteri e il numero minimo di set di caratteri è maggiore di due.

- **Numero minimo di set di caratteri:** se **Tipo di password richiesto** è impostato su **Alfanumerico**, questa impostazione specifica il numero minimo di set di caratteri che la password deve contenere. I quattro set di caratteri sono:
  - Lettere minuscole
  - Lettere maiuscole
  - Simboli
  - Numeri

Se per questa impostazione viene usato un numero più alto, gli utenti dovranno creare password più complesse. Per i dispositivi che eseguono Windows e prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida se la lunghezza minima della password è maggiore di otto caratteri e il numero minimo di set di caratteri è maggiore di due.

- **Minuti di inattività prima che venga richiesta la password:** specifica il tempo di inattività prima che l'utente debba immettere nuovamente la password.
- **Scadenza password (giorni):** selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Ricorda cronologia password:** usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.
- **Impedisci riutilizzo delle password precedenti:** se l'opzione **Ricorda cronologia password** è selezionata, specificare il numero di password usate in precedenza che non è possibile riutilizzare.
- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività:** questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti finali viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

**Questa impostazione si applica solo ai dispositivi Windows 10 Mobile.**

### <a name="encryption"></a>Crittografia

- **Richiedi crittografia sul dispositivo mobile:** impostare questa opzione su **Sì** per richiedere che il dispositivo sia crittografato per la connessione alle risorse.



## <a name="device-health-settings"></a>Impostazioni dell'integrità dei dispositivi

- **Richiedi che i dispositivi siano segnalati come integri:** è possibile impostare una regola per richiedere che i dispositivi **Windows 10 Mobile** vengano segnalati come integri nei criteri di conformità nuovi o esistenti. Se questa impostazione è abilitata, i dispositivi Windows 10 vengono valutati tramite il servizio di attestazione dell'integrità in base ai punti dati seguenti:
  - **Abilitazione della funzionalità BitLocker:** se la funzionalità BitLocker è attiva, il dispositivo è in grado di proteggere i dati archiviati nell'unità da accessi non autorizzati, quando il sistema è spento o passa allo stato di ibernazione. Crittografia unità BitLocker di Windows crittografa tutti i dati archiviati nel volume del sistema operativo Windows. BitLocker usa il TPM per proteggere il sistema operativo Windows e i dati utente e consente di garantire che un computer non venga manomesso anche se viene perso, rubato o lasciato incustodito. Se il computer è dotato di un TPM compatibile, BitLocker usa il TPM per bloccare le chiavi di crittografia che proteggono i dati. Di conseguenza, non è possibile accedere alle chiavi finché il TPM non ha verificato lo stato del computer.
  - **Abilitazione della funzionalità Integrità del codice:** l'integrità del codice è una funzionalità che verifica l'integrità di un driver o di un file di sistema ogni volta che viene caricato in memoria. L'integrità del codice rileva se un driver o un file di sistema non firmato viene caricato nel kernel o se un file di sistema è stato modificato da software dannoso eseguito da un account utente con privilegi di amministratore.
  - **Abilitazione della funzionalità Avvio protetto:** quando è abilitato l'avvio protetto, il sistema viene forzato a eseguire l'avvio in uno stato attendibile predefinito. Inoltre, quando è abilitato l'avvio protetto, i componenti di base usati per avviare il computer devono avere le firme di crittografia corrette considerate attendibili dall'organizzazione che ha prodotto il dispositivo. Il firmware UEFI effettua questa verifica prima dell'avvio del computer. Se un file è stato manomesso modificandone la firma, il sistema non verrà avviato.

Per informazioni su come funziona il servizio di attestazione dell'integrità, vedere l'articolo relativo al [CSP per l'attestazione dell'integrità](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Minimum OS required** (Versione minima richiesta del sistema operativo): quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.
- **Maximum OS version allowed** (Versione massima consentita del sistema operativo): quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali risulterà bloccato e l'utente dovrà contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.

<!---## Compliance policy settings for Windows PCs--->

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Lunghezza minima password:** supportata in Windows 8.1.

Specificare il numero minimo di cifre o caratteri che la password dell'utente deve contenere.

Per i dispositivi che prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida se **Lunghezza minima password** è maggiore di 8 caratteri e **Numero minimo di set di caratteri** è maggiore di 2 caratteri.

- **Tipo di password richiesto**: supportata in Windows RT, Windows RT 8.1 e Windows 8.1.

Specificare se gli utenti devono creare una password **alfanumerica** o **numerica**.

- **Numero minimo di set di caratteri**: supportata in Windows RT, Windows RT 8.1 e Windows 8.1. Se **Tipo di password richiesto** è impostato su **Alfanumerico**, questa impostazione specifica il numero minimo di set di caratteri che la password deve contenere. I quattro set di caratteri sono:
  - Lettere minuscole
  - Lettere maiuscole
  - Simboli
  - Numeri: se per questa impostazione viene usato un numero più alto, gli utenti dovranno creare password più complesse.

Per i dispositivi che prevedono l'accesso con un account Microsoft, i criteri di conformità non eseguono correttamente la convalida se **Lunghezza minima password** è maggiore di 8 caratteri e **Numero minimo di set di caratteri** è maggiore di 2 caratteri.

- **Minuti di inattività prima che venga richiesta la password:** supportata in Windows RT, Windows RT 8.1 e Windows 8.1

Specificare il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni)**: supportata in Windows RT, Windows RT 8.1 e Windows 8.1.

Selezionare il numero di giorni che mancano alla scadenza della password attuale, quando l'utente deve creare una nuova password.

- **Ricorda cronologia password:** supportata in Windows RT, Windows RT e Windows 8.1.

Usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate precedentemente.

- **Impedisci riutilizzo delle password precedenti:** supportata in Windows RT, Windows RT 8.1 e Windows 8.1

Se l'opzione **Ricorda cronologia password** è selezionata, specificare il numero di password usate in precedenza che non è possibile riutilizzare.


## <a name="device-health-settings"></a>Impostazioni dello stato dei dispositivi

- **Richiedi che i dispositivi siano segnalati come integri:** supportata nei dispositivi Windows 10. È possibile impostare una regola per richiedere che i dispositivi Windows 10 vengano riportati come integri nei criteri di conformità nuovi o esistenti. Se questa impostazione è abilitata, i dispositivi Windows 10 vengono valutati tramite il servizio di attestazione dell'integrità in base ai punti dati seguenti:
  - **Abilitazione della funzionalità BitLocker:** se la funzionalità BitLocker è attiva, il dispositivo è in grado di proteggere i dati archiviati nell'unità da accessi non autorizzati, quando il sistema è spento o passa allo stato di ibernazione. Crittografia unità BitLocker di Windows crittografa tutti i dati archiviati nel volume del sistema operativo Windows. BitLocker usa il TPM per proteggere il sistema operativo Windows e i dati utente e consente di garantire che un computer non venga manomesso anche se viene perso, rubato o lasciato incustodito. Se il computer è dotato di un TPM compatibile, BitLocker usa il TPM per bloccare le chiavi di crittografia che proteggono i dati. Di conseguenza, non è possibile accedere alle chiavi finché il TPM non ha verificato lo stato del computer.
  - **Abilitazione della funzionalità Integrità del codice:** l'integrità del codice è una funzionalità che verifica l'integrità di un driver o di un file di sistema ogni volta che viene caricato in memoria. L'integrità del codice rileva se un driver o un file di sistema non firmato viene caricato nel kernel o se un file di sistema è stato modificato da software dannoso eseguito da un account utente con privilegi di amministratore.
  - **Abilitazione della funzionalità Avvio protetto:** quando è abilitato l'avvio protetto, il sistema viene forzato a eseguire l'avvio in uno stato attendibile predefinito. Inoltre, quando è abilitato l'avvio protetto, i componenti di base usati per avviare il computer devono avere le firme di crittografia corrette considerate attendibili dall'organizzazione che ha prodotto il dispositivo. Il firmware UEFI effettua questa verifica prima dell'avvio del computer. Se un file è stato manomesso modificandone la firma, il sistema non verrà avviato.
  - **Abilitazione della funzionalità Antimalware ad esecuzione anticipata:** la funzionalità Antimalware ad esecuzione anticipata fornisce protezione per i computer della rete all'avvio e prima dell'inizializzazione di driver di terze parti.

Per informazioni su come funziona il servizio di attestazione dell'integrità, vedere l'articolo relativo al [CSP per l'attestazione dell'integrità](https://msdn.microsoft.com/library/dn934876.aspx).

## <a name="device-property-settings"></a>Impostazioni delle proprietà dei dispositivi

- **Versione minima richiesta del sistema operativo:** supportata in Windows 8.1 e Windows 10.

Qui è necessario specificare il numero major.minor.build. Il numero di versione deve corrispondere alla versione restituita dal comando ```winver```.

Quando un dispositivo ha una versione precedente rispetto alla versione del sistema operativo specificata, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.

- **Versione massima consentita del sistema operativo:** supportata in Windows 8.1 e Windows 10.

Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali risulterà bloccato e l'utente dovrà contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.

Per trovare la versione del sistema operativo da usare per le impostazioni **Versione minima richiesta del sistema operativo** e **Versione massima consentita del sistema operativo**, eseguire il comando **winver** dal prompt dei comandi. Il comando winver restituisce la versione segnalata del sistema operativo.

- I PC Windows 8.1 restituiscono la versione **3**. Se la regola della versione del sistema operativo è impostata su Windows 8.1 per Windows, il dispositivo risulta non conforme anche se il sistema operativo installato è Windows 8.1.
- Per i PC che eseguono Windows 10, la versione deve essere impostata come &quot;10.0&quot; più il numero di build del sistema operativo restituito dal comando winver.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
