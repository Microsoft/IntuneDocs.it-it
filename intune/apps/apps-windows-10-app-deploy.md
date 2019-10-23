---
title: Distribuzione di app di Windows 10 con Microsoft Intune
titleSuffix: ''
description: Informazioni sugli scenari di distribuzione delle app di Windows 10 disponibili con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8ce24081eae1808d3db0c5078026b306fd209d5
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507249"
---
# <a name="windows-10-app-deployment-by-using-microsoft-intune"></a>Distribuzione di app di Windows 10 con Microsoft Intune 

Microsoft Intune supporta un'ampia gamma di tipi di app e scenari di distribuzione nei dispositivi Windows 10. Dopo avere aggiunto un'app a Intune, è possibile assegnarla a utenti e dispositivi. Questo articolo offre maggiori dettagli sugli scenari di Windows 10 supportati e descrive anche dettagli chiave di cui tenere conto quando si distribuiscono app in Windows. 

Le app line-of-business e Microsoft Store per le aziende sono i tipi di app che supportano i dispositivi Windows 10. Le estensioni file per le app di Windows sono msi, appx e appxbundle.  

> [!Note]
> Per distribuire app moderne, è necessario almeno quanto segue:
> - Per Windows 10 1803, [23 maggio 2018-KB4100403 (build del sistema operativo 17134.81)](https://support.microsoft.com/help/4100403/windows-10-update-kb4100403).
> - Per Windows 10 1709, [21 giugno 2018-KB4284822 (build del sistema operativo 16299.522)](https://support.microsoft.com/help/4284822).
>
> Solo Windows 10 1803 e versioni successive supportano l'installazione di app quando non è associato alcun utente primario.
>
> La distribuzione di app line-of-business non è supportata nei dispositivi che eseguono Windows 10 Home Edition.

## <a name="windows-10-lob-apps"></a>App line-of-business di Windows 10

È possibile firmare e caricare app line-of-business di Windows 10 nella console di amministrazione di Intune. Possono essere app moderne, ad esempio app per la piattaforma UWP (Universal Windows Platform) e pacchetti app Windows (AppX), nonché app per Win 32, ad esempio semplici file di pacchetti del programma di installazione app Microsoft (MSI). L'amministratore deve caricare e distribuire manualmente gli aggiornamenti delle app line-of business. Questi aggiornamenti vengono installati automaticamente nei dispositivi degli utenti che hanno installato l'app. Non è richiesto alcun intervento da parte degli utenti, che non hanno alcun controllo sugli aggiornamenti. 

## <a name="microsoft-store-for-business-apps"></a>App di Microsoft Store per le aziende

Le app di Microsoft Store per le aziende sono app moderne che si acquistano dal portale di amministrazione Microsoft Store per le aziende e vengono quindi sincronizzate in Microsoft Intune per la gestione. Tali app possono essere con licenza online oppure con licenza offline. Gli aggiornamenti vengono gestiti direttamente da Microsoft Store, senza necessità di altre azioni da parte dell'amministratore. È anche possibile impedire gli aggiornamenti di app specifiche usando un URI (Uniform Resource Identifier) personalizzato. Per altre informazioni, vedere [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates) (Gestione delle app aziendali - Impedire gli aggiornamenti automatici delle app). L'utente può anche disabilitare gli aggiornamenti per tutte le app di Microsoft Store per le aziende presenti nel dispositivo. 

### <a name="categorize-microsoft-store-for-business-apps"></a>Categorizzare le app di Microsoft Store per le aziende 
Per categorizzare le app di Microsoft Store per le aziende: 

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **App client** > **App**. Selezionare un'app di Microsoft Store per le aziende. Selezionare quindi **Informazioni sull'app** > **Categoria**. 
3. Selezionare una categoria.

## <a name="install-apps-on-windows-10-devices"></a>Installare app nei dispositivi Windows 10
A seconda del tipo di app, è possibile installare app in un dispositivo Windows 10 in uno dei due modi seguenti:

- **Contesto utente**: quando un'app viene distribuita nel contesto utente, l'app gestita viene installata per l'utente corrispondente nel momento in cui quest'ultimo accede al dispositivo. Si noti che l'installazione dell'app viene completata correttamente solo quando l'utente accede al dispositivo. 
  - Possono essere distribuite nel contesto utente le app line-of-business moderne e le app di Microsoft Store per le aziende, sia online che offline. Queste app supportano sia la finalità obbligatoria che quella disponibile.
  - Le app Win32 create come app in modalità utente o in Dual Mode possono essere distribuite nel contesto utente e supportano sia la finalità obbligatoria che quella disponibile. 
- **Contesto di dispositivo**: quando un'app viene distribuita nel contesto di dispositivo, Intune installa l'app gestita direttamente nel dispositivo.
  - Solo le app line-of-business moderne e le app di Microsoft Store per le aziende con licenza offline possono essere distribuite nel contesto di dispositivo. Queste app supportano solo la finalità obbligatoria.
  - Le app Win32 compilate come app in modalità computer o in Dual mode possono essere distribuite nel contesto di dispositivo e supportano solo la finalità obbligatoria.

> [!NOTE]
> Per le app Win32 compilate come app in Dual mode, l'amministratore deve scegliere se devono funzionare come app in modalità utente oppure in modalità computer per tutte le assegnazioni associate all'istanza attiva. Il contesto di distribuzione non può essere modificato per assegnazione.  

Quando un'app viene distribuita nel contesto di dispositivo, l'installazione riesce solo se il dispositivo di destinazione supporta il contesto di dispositivo. Inoltre, la distribuzione nel contesto di dispositivo comporta le condizioni seguenti:
- Se un'app viene distribuita in un contesto di dispositivo e viene destinata a un utente, l'installazione non riesce. Nella console di amministrazione vengono visualizzati lo stato e l'errore seguenti:
  - Stato: Operazione non riuscita.
  - Errore: Un utente non può fungere da destinazione di un'installazione nel contesto di dispositivo.
- Se un'app viene distribuita nel contesto di dispositivo ma è destinata a un dispositivo che non supporta tale contesto, l'installazione non riesce. Nella console di amministrazione vengono visualizzati lo stato e l'errore seguenti:
  - Stato: Operazione non riuscita.
  - Errore: Questa piattaforma non supporta installazioni del contesto di dispositivo. 

> [!Note]
> Dopo il salvataggio dell'assegnazione di un'app con una distribuzione specifica, non è possibile cambiare il contesto dell'assegnazione, fatta eccezione per le app moderne. Per le app moderne è possibile passare dal contesto utente al contesto di dispositivo. 

In caso di conflitto nei criteri per un utente o un dispositivo singolo, si applicano le priorità seguenti:
- Un criterio di contesto di dispositivo ha priorità più alta rispetto a un criterio di contesto utente. 
- Un criterio di installazione ha priorità più alta rispetto a un criterio di disinstallazione.

Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md). Per altre informazioni sui tipi di app in Intune, vedere [Aggiungere app in Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md)
- [Come monitorare le app](apps-monitor.md)
