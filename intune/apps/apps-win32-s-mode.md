---
title: Abilitare app Win32 in dispositivi in modalità S
titleSuffix: Microsoft Intune
description: Informazioni su come abilitare le app Win32 nei dispositivi in modalità S usando Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3a9eb45898102e9d5fcde88f69026467255c513
ms.sourcegitcommit: d2d18eef64bcf16eec1a48fcb67f1362537c0245
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2019
ms.locfileid: "73445274"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>Abilitare app Win32 in dispositivi in modalità S

La [modalità S di Windows 10](https://docs.microsoft.com/windows/deployment/s-mode) è un sistema operativo bloccato che esegue solo le app dello Store. Per impostazione predefinita, i dispositivi in modalità S di Windows non consentono l'installazione e l'esecuzione di app Win32. Questi dispositivi includono un singolo *criterio di base Win 10S* che impedisce l'esecuzione di app Win32 nel dispositivo in modalità S. Tuttavia, creando e usando un **criterio supplementare per la modalità S** in Intune è possibile installare ed eseguire app Win32 in dispositivi gestiti in modalità S di Windows 10. Usando gli strumenti di PowerShell del [Controllo delle applicazioni di Windows Defender (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) è possibile creare uno o più criteri supplementari per la modalità S di Windows. È necessario firmare i criteri supplementari con il [servizio Firma di Device Guard (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) o con [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) e quindi caricare e distribuire i criteri tramite Intune. In alternativa, è possibile firmare i criteri supplementari con un certificato di firma del codice dell'organizzazione, ma il metodo preferito consiste nell'usare il servizio Firma di Device Guard (DGSS). Nell'istanza in cui viene usato il certificato di firma del codice dell'organizzazione, il certificato radice a cui è concatenato il certificato di firma del codice deve essere presente nel dispositivo.

Assegnando il criterio supplementare per la modalità S in Intune, si consente al dispositivo di fare un'eccezione per il criterio per la modalità S esistente del dispositivo che consente di usare il catalogo delle app firmate corrispondenti. Il criterio imposta un elenco di app consentite (catalogo delle app) che possono essere usate nel dispositivo in modalità S.

> [!NOTE]
> Le app Win32 nei dispositivi in modalità S sono supportate solo nell'aggiornamento di Windows 10 di novembre 2019 (build 18363) o versioni successive.

<!-- Add WDAC tooling diagram  -->

I passaggi per consentire l'esecuzione delle app Win32 in un dispositivo Windows 10 in modalità S sono i seguenti:

1. Abilitare i dispositivi in modalità S tramite Intune come parte del processo di registrazione di Windows 10 S.
2. Creare un criterio supplementare per consentire l'esecuzione di app Win32:
   - Per creare un criterio supplementare, è possibile usare gli strumenti del [Controllo delle applicazioni di Windows Defender (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control). L'ID criterio di base all'interno del criterio deve corrispondere all'ID criterio di base per la modalità S (hardcoded nel client). Assicurarsi anche che la versione dei criteri sia successiva alla versione precedente.
   - Usare il servizio Firma di Device Guard (DGSS) per firmare i criteri supplementari. Per altre informazioni, vedere [Firmare i criteri di integrità del codice con Firma di Device Guard](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing).
   - Per caricare il criterio supplementare firmato in Intune, è necessario creare un criterio supplementare per la modalità S di Windows 10 (vedere di seguito).
3. L'uso dei cataloghi delle app Win32 viene consentito tramite Intune:
   - È possibile creare i file di catalogo (1 per ogni app) e firmarli usando il servizio Firma di Device Guard (DGSS) o un'altra infrastruttura di certificazione.
   - Il catalogo firmato viene inserito nel file *con estensione intunewin* usando lo [Strumento di preparazione di contenuti Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730). Per altre informazioni, vedere [Gestione di app Win32 - Preparare il contenuto delle app Win32 per il caricamento](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload).
   - Intune applica il catalogo delle app firmato per installare l'app Win32 nel dispositivo in modalità S usando l'[estensione di gestione di Intune](~/apps/intune-management-extension.md).

> [!NOTE]
> I bundle `.appx` e `.appx` line-of-business (LOB) in modalità S di Windows 10 verranno supportati tramite la firma di Microsoft Store per le aziende.
>
> I **criteri supplementari per la modalità S** per le app devono essere distribuiti tramite l'estensione di gestione di Intune.
>
> I criteri per la modalità S vengono applicati a livello di dispositivo. Nel dispositivo verranno uniti più criteri di destinazione. Il criteri uniti verranno applicati nel dispositivo.

Per creare un criterio supplementare per la modalità S di Windows 10, seguire questa procedura:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel riquadro **Intune** selezionare **App client** > **Criteri supplementari per la modalità S** > **Crea criterio**.
3. Prima di aggiungere il **file dei criteri**, è necessario crearlo e firmarlo. Per altre informazioni, vedere:
    - [Creare un criterio del Controllo di applicazioni di Windows Defender usando gli strumenti di PowerShell e convertirlo in un formato binario](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Eseguire l'accesso con il servizio Firma di Device Guard](https://go.microsoft.com/fwlink/?linkid=2095629) **(opzione consigliata)**

4. Nella pagina **Informazioni di base** aggiungere i valori seguenti:

    | Valore | Descrizione |
    |--------------|------------------------------------------------|
    | File del criterio | File contenente il criterio del Controllo di applicazioni di Windows Defender. |
    | Name | Nome del criterio. |
    | Descrizione | [Facoltativo] Descrizione del criterio. |

5. Fare clic su **Avanti: Tag di ambito**.<br>
   Nella pagina **Tag di ambito** è possibile configurare facoltativamente i tag di ambito per determinare chi può visualizzare il criterio dell'app in Intune. Per altre informazioni sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](~/fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

6. Fare clic su **Avanti: Assegnazioni**.<br>
   La pagina **Assegnazioni** consente di assegnare il criterio a utenti e dispositivi. Si noti che è possibile assegnare un criterio a un dispositivo indipendentemente dal fatto che il dispositivo sia gestito da Intune o meno.
7. Fare clic su **Avanti: Rivedi e crea** per verificare i valori immessi per il profilo.
8. Al termine, fare clic su **Crea** per creare il criterio supplementare per la modalità S in Intune. 

Dopo la creazione, il criterio verrà aggiunto all'elenco dei criteri supplementari per la modalità S in Intune. Dopo l'assegnazione, il criterio viene distribuito nei dispositivi. Si noti che è necessario distribuire l'app allo stesso gruppo di sicurezza del criterio supplementare. È possibile iniziare a specificare come destinazione e assegnare le app a questi dispositivi. Ciò consentirà agli utenti finali di installare ed eseguire le app nei dispositivi in modalità S.

## <a name="removal-of-s-mode-policy"></a>Rimozione dei criteri per la modalità S

Attualmente, per rimuovere il criterio supplementare per la modalità S dal dispositivo, è necessario assegnare e distribuire un criterio vuoto per sovrascrivere il criterio supplementare per la modalità S esistente.

## <a name="policy-reporting"></a>Creazione di report dei criteri

Per il criterio supplementare per la modalità S, che viene applicato a livello di dispositivo, è possibile creare report solo a livello di dispositivo. La creazione di report a livello di dispositivo è disponibile per condizioni di riuscita e di errore. 

Valori di report visualizzati nella console di Intune per i criteri di report per la modalità S:
- **Operazione riuscita**: Il criterio supplementare per la modalità S è attivo.
- **Sconosciuto**: Lo stato del criterio supplementare per la modalità S non è noto.
- **TokenError**: Il criterio supplementare per la modalità S ha una struttura corretta ma si verifica un errore durante l'autorizzazione del token.
- **NotAuthorizedByToken**: Il token non autorizza il criterio supplementare per la modalità S.
- **PolicyNotFound**: Il criterio supplementare per la modalità S non viene trovato.

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni, vedere [App Win32 in modalità S](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s).
- Per altre informazioni sull'aggiunta di app a Intune, vedere [Aggiungere app in Microsoft Intune](apps-add.md).
- Per altre informazioni sulle app Win32, vedere [Gestione di app Win32 in Intune](~/apps/apps-win32-app-management.md).
