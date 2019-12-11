---
title: Controllo degli accessi in base al ruolo con Microsoft Intune
description: Informazioni sul controllo degli accessi in base al ruolo e su come permette di controllare chi può eseguire determinate operazioni e apportare modifiche in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a03366037f9b0eced70f0375b3f4b39401e3141
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509818"
---
# <a name="role-based-access-control-rbac-with-microsoft-intune"></a>Controllo degli accessi in base al ruolo con Microsoft Intune

Il controllo degli accessi in base al ruolo semplifica la gestione degli utenti che possono accedere alle risorse dell'organizzazione e di che cosa può fare ciascuno con tali risorse.  L'[assegnazione di ruoli](assign-role.md) agli utenti di Intune permette di limitare che cosa possono visualizzare e modificare. Ogni ruolo è associato a un set di autorizzazioni che determinano quali utenti che hanno tale ruolo possono accedere e che cosa possono modificare all'interno dell'organizzazione.

Per creare, modificare o assegnare ruoli, l'account deve disporre di una delle seguenti autorizzazioni in Azure AD:
- **Amministratore globale**
- **Amministratore del servizio Intune** (noto anche come **amministratore di Intune**)

Per consigli e suggerimenti sul controllo degli accessi in base al ruolo di Intune, è possibile vedere questa serie di cinque video che presentano esempi e procedure dettagliate: [1](https://www.youtube.com/watch?v=5deXLMLcnKY), [2](https://www.youtube.com/watch?v=38dnMBLuxbQ), [3](https://www.youtube.com/watch?v=6vqg9cAkMbY), [4](https://www.youtube.com/watch?v=5yOLajFFMHE), [5](https://www.youtube.com/watch?v=P5DDvsSF4Wk).

## <a name="roles"></a>Ruoli
Un ruolo definisce il set di autorizzazioni concesse agli utenti assegnati al ruolo.
È possibile usare ruoli sia predefiniti sia personalizzati. I ruoli predefiniti sono utili in alcuni scenari di Intune comuni. È possibile [creare ruoli personalizzati](create-custom-role.md) con il set esatto di autorizzazioni necessarie. Diversi ruoli di Azure Active Directory hanno autorizzazioni per Intune.
Per visualizzare un ruolo, scegliere **Intune** > **Ruoli** > **Tutti i ruoli** > scegliere un ruolo. Verranno visualizzate le pagine seguenti:

- **Proprietà**: nome, descrizione, tipo, assegnazioni e tag di ambito per il ruolo. 
- **Autorizzazioni**: elenca una lunga serie di interruttori che definiscono le autorizzazioni di cui dispone il ruolo.
- **Assegnazioni**: elenco di [assegnazioni di ruolo]( assign-role.md) che definiscono gli utenti che hanno accesso a determinati utenti/dispositivi. Un ruolo può avere più assegnazioni e un utente può essere incluso in più assegnazioni.

### <a name="built-in-roles"></a>Ruoli predefiniti
È possibile assegnare ruoli predefiniti a gruppi senza ulteriore configurazione. Non è possibile eliminare o modificare il nome, la descrizione, il tipo o le autorizzazioni di un ruolo predefinito.

- **Help Desk Operator** (Operatore help desk): consente di eseguire attività remote su utenti e dispositivi e assegnare applicazioni o criteri a utenti o dispositivi.
- **Policy and Profile Manager** (Gestione criteri e profili): gestisce i criteri di conformità, i profili di configurazione, la registrazione Apple, gli identificatori dei dispositivi aziendali e le baseline di sicurezza.
- **Read Only Operator** (Operatore sola lettura): consente di visualizzare informazioni su utenti, dispositivi, registrazione, configurazione e applicazioni. Non consente di apportare modifiche a Intune.
- **Application Manager** (Gestione applicazioni): consente di gestire le applicazioni per dispositivi mobili e gestite, di leggere le informazioni sui dispositivi e di visualizzare i profili di configurazione dei dispositivi.
- **Intune Role Administrator** (Amministratore dei ruoli di Intune): consentire di gestire i ruoli di Intune personalizzati e di aggiungere assegnazioni per i ruoli di Intune predefiniti. È l'unico ruolo di Intune che può assegnare autorizzazioni agli amministratori.
- **School Administrator** (Amministratore di istituto di istruzione): Gestisce i dispositivi Windows 10 in [Intune per Education](../introduction-intune-education.md).

### <a name="custom-roles"></a>Ruoli personalizzati
È possibile creare ruoli personalizzati con autorizzazioni personalizzate. Per altre informazioni sui ruoli personalizzati, vedere [Creare un ruolo personalizzato](create-custom-role.md).

### <a name="azure-active-directory-roles-with-intune-access"></a>Ruoli di Azure Active Directory con accesso in Intune
| Ruolo di Azure Active Directory | Tutti i dati di Intune | Dati di controllo di Intune |
| --- | :---: | :---: |
| Amministratore globale | Lettura/Scrittura | Lettura/Scrittura |
| Amministratore del servizio Intune | Lettura/Scrittura | Lettura/Scrittura |
| Amministratore accesso condizionale | Nessuno | Nessuno |
| Amministratore della protezione | Sola lettura | Sola lettura |
| Operatore di sicurezza | Sola lettura | Sola lettura |
| Ruolo con autorizzazioni di lettura per la sicurezza | Sola lettura | Sola lettura |
| Amministratore di conformità | Nessuno | Sola lettura |
| Amministratore dati di conformità | Nessuno | Sola lettura |
| Ruolo con autorizzazioni di lettura globali | Sola lettura | Sola lettura |

> [!TIP]
> Intune mostra inoltre tre estensioni di Azure AD: **Utenti**, **Gruppi** e **Accesso condizionale**, controllate tramite il controllo degli accessi in base al ruolo di Azure AD. Il ruolo **Amministratore account utente**, inoltre, consente di eseguire solo attività su utenti e gruppi di AAD e non dispone delle autorizzazioni complete per eseguire tutte le attività in Intune. Per altre informazioni, vedere [Autorizzazioni del ruolo di amministratore in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).
### <a name="roles-created-in-the-intune-classic-portal"></a>Ruoli creati nel portale classico di Intune
Solo gli utenti **Amministratori del servizio** con autorizzazioni "Completo" vengono inclusi nella migrazione dal portale classico di Intune a Intune nel portale di Azure. È necessario assegnare nuovamente gli utenti **Amministratori del servizio** di Intune con accesso "Sola lettura" o "Supporto tecnico" nei ruoli di Intune nel portale di Azure e rimuoverli dal portale classico.
> [!IMPORTANT]
> Potrebbe essere necessario mantenere l'accesso Amministratori del servizio Intune nel portale classico, se gli amministratori hanno ancora la necessità di gestire i PC con Intune.

## <a name="role-assignments"></a>Assegnazioni di ruolo
Un'assegnazione di ruolo definisce:

- Quali utenti sono assegnati al ruolo
- Quali risorse possono essere visualizzate dagli utenti
- Quali risorse possono essere modificate dagli utenti

È possibile assegnare ruoli sia predefiniti sia personalizzati agli utenti. Per potergli assegnare un ruolo di Intune, l'utente deve avere una licenza di Intune.
Per visualizzare un'assegnazione di ruolo, scegliere **Intune** > **Ruoli** > **Tutti i ruoli** > scegliere un ruolo > scegliere un'assegnazione. Verranno visualizzate le pagine seguenti:

- **Proprietà**: nome, descrizione, ruolo, membri, ambiti e tag dell'assegnazione.
- **Membri**: tutti gli utenti nei gruppi di sicurezza di Azure elencati hanno l'autorizzazione necessaria per gestire gli utenti/i dispositivi elencati in Ambito (gruppi).
- **Ambito (gruppi)** : tutti gli utenti/i dispositivi in questi gruppi di sicurezza di Azure possono essere gestiti dagli utenti in Membri.
- **[Ambito (tag)](scope-tags.md)** : Gli utenti in Membri possono visualizzare le risorse che hanno gli stessi tag di ambito.

### <a name="multiple-role-assignments"></a>Più assegnazioni di ruolo
Se un utente ha più assegnazioni di ruolo, autorizzazioni e tag di ambito, queste assegnazioni di ruolo si estendono ai diversi oggetti in questo modo:

- Le autorizzazioni di assegnazione e i tag di ambito si applicano solo agli oggetti, come criteri o app, all'interno dell'assegnazione del ruolo Ambito (gruppi). Le autorizzazioni di assegnazione e i tag di ambito non si applicano a oggetti in altre assegnazioni di ruolo, a meno che non vengano concesse in modo specifico dall'altra assegnazione.
- Le altre autorizzazioni (ad esempio Creazione, Lettura, Aggiornamento ed Eliminazione) si applicano a tutti gli oggetti dello stesso tipo (come tutti i criteri o tutte le app) in qualsiasi assegnazione dell'utente.
- Le autorizzazioni e i tag di ambito per oggetti di tipi diversi, come criteri o app, non si applicano le une alle altre. Un'autorizzazione di lettura per i criteri, ad esempio, non fornisce un'autorizzazione di lettura per le app nelle assegnazioni dell'utente.

## <a name="next-steps"></a>Passaggi successivi
- [Assegnare un ruolo a un utente](assign-role.md)
- [Creare un ruolo personalizzato](create-custom-role.md)
