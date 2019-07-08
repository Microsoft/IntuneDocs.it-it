---
title: Rimuovere certificati SCEP o PKCS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Gli amministratori possono usare l'azione di cancellazione o di ritiro per rimuovere i certificati da Microsoft Intune. Esistono alcuni scenari in cui i certificati vengono rimossi automaticamente, ad esempio se si annulla la registrazione di un dispositivo o si rimuove un criterio di conformità. In alcuni scenari i certificati rimangono automaticamente nel dispositivo, ad esempio quando la licenza di Intune viene smarrita o rimossa. Vedere le diverse modalità per i dispositivi Android, Android, iOS, macOS e Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: de2f201e6a7d0181847db5d212625c9eed9ea698
ms.sourcegitcommit: 9c06d8071b9affeda32e367bfe85d89bc524ed0b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413779"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Rimuovere i certificati SCEP e PKCS in Microsoft Intune

In Microsoft Intune, è possibile usare profili di certificato SCEP (Simple Certificate Enrollment Protocol) e PKCS (Public Key Cryptography Standards) per aggiungere certificati ai dispositivi. 

Questi certificati possono essere rimossi quando si [cancella](devices-wipe.md#wipe) o si [ritira](devices-wipe.md#retire) il dispositivo. Esistono anche scenari in cui i certificati vengono rimossi automaticamente e in cui i certificati rimangono nel dispositivo. Questo articolo illustra alcuni scenari comuni e l'impatto sui certificati SCEP e PKCS.

> [!NOTE]
> Per rimuovere e revocare i certificati per un utente che viene rimosso da Active Directory locale o Azure Active Directory (Azure AD), assicurarsi di seguire i passaggi nell'ordine indicato:
>
> 1. Cancellare o ritirare il dispositivo dell'utente.
> 2. Rimuovere l'utente da Active Directory locale o Azure AD.

## <a name="manually-deleted-certificates"></a>Certificati eliminati manualmente  

L'eliminazione manuale di un certificato è uno scenario che si applica a più piattaforme e certificati di cui viene eseguito il provisioning con i profili certificato SCEP o PKCS. Ad esempio, un utente potrebbe eliminare un certificato da un dispositivo, che rimane incluso come destinazione per i criteri relativi ai certificati.  

In questo scenario, dopo l'eliminazione del certificato, la volta successiva che il dispositivo si connette a Intune risulta non conforme perché manca il certificato previsto. Intune rilascia quindi un nuovo certificato per ripristinare la conformità per il dispositivo. Per ripristinare il certificato non è necessaria alcuna azione aggiuntiva.  


## <a name="windows-devices"></a>Dispositivi Windows

#### <a name="scep-certificates"></a>Certificati SCEP

Un certificato SCEP viene revocato *e* rimosso quando:

- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).
- Il dispositivo viene rimosso da un gruppo di Azure AD.
- Il profilo certificato viene rimosso dall'assegnazione del gruppo.

Un certificato SCEP viene revocato quando:
- Un amministratore modifica o aggiorna il profilo SCEP.

Un certificato radice viene rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

I certificati SCEP *rimangono* nel dispositivo (i certificati non vengono revocati né rimossi) quando:
- Un utente perde la licenza di Intune.
- Un amministratore ritira la licenza di Intune.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.

#### <a name="pkcs-certificates"></a>Certificati PKCS

Un certificato PKCS viene revocato *e* rimosso quando:

- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

Un certificato radice viene rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

I certificati PKCS *rimangono* nel dispositivo (i certificati non vengono revocati né rimossi) quando:
- Un utente perde la licenza di Intune.
- Un amministratore ritira la licenza di Intune.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.
- Un amministratore modifica o aggiorna il profilo PKCS.
- Il profilo certificato viene rimosso dall'assegnazione del gruppo.


## <a name="ios-devices"></a>Dispositivi iOS

#### <a name="scep-certificates"></a>Certificati SCEP

Un certificato SCEP viene revocato *e* rimosso quando:

- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).
- Il dispositivo viene rimosso dal gruppo di Azure AD.
- Il profilo certificato viene rimosso dall'assegnazione del gruppo.

Un certificato SCEP viene revocato quando:
- Un amministratore modifica o aggiorna il profilo SCEP.

Un certificato radice viene rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

I certificati SCEP *rimangono* nel dispositivo (i certificati non vengono revocati né rimossi) quando:
- Un utente perde la licenza di Intune.
- Un amministratore ritira la licenza di Intune.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.

#### <a name="pkcs-certificates"></a>Certificati PKCS

Un certificato PKCS viene revocato *e* rimosso quando:

- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

Un certificato PKCS viene rimosso quando:
- Il profilo certificato viene rimosso dall'assegnazione del gruppo.
  
Un certificato radice viene rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

I certificati PKCS *rimangono* nel dispositivo (i certificati non vengono revocati né rimossi) quando:
- Un utente perde la licenza di Intune.
- Un amministratore ritira la licenza di Intune.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.
- Un amministratore modifica o aggiorna il profilo PKCS.

## <a name="android-knox-devices"></a>Dispositivi Android KNOX

#### <a name="scep-certificates"></a>Certificati SCEP

Un certificato SCEP viene revocato *e* rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).

Un certificato SCEP viene revocato quando:
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).
- Il dispositivo viene rimosso da un gruppo di Azure AD.
- Il profilo certificato viene rimosso dall'assegnazione del gruppo.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.
- Un amministratore modifica o aggiorna il profilo SCEP.

Un certificato radice viene rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

I certificati SCEP *rimangono* nel dispositivo (i certificati non vengono revocati né rimossi) quando:
- Un utente perde la licenza di Intune.
- Un amministratore ritira la licenza di Intune.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.

#### <a name="pkcs-certificates"></a>Certificati PKCS

Un certificato PKCS viene revocato *e* rimosso quando:

- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

Un certificato radice viene rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue l'azione di [cancellazione](devices-wipe.md#wipe).
- Un amministratore esegue l'azione di [ritiro](devices-wipe.md#retire).

I certificati PKCS *rimangono* nel dispositivo (i certificati non vengono revocati né rimossi) quando:
- Un utente perde la licenza di Intune.
- Un amministratore ritira la licenza di Intune.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.
- Un amministratore modifica o aggiorna il profilo PKCS.
- Il profilo certificato viene rimosso dall'assegnazione del gruppo.
  
  
> [!NOTE]
> I dispositivi Android for Work non vengono convalidati per gli scenari precedenti. I dispositivi Android legacy, ovvero i dispositivi non Samsung e i dispositivi con un profilo non Work, non sono abilitati per la rimozione di certificati. 

## <a name="macos-certificates"></a>Certificati macOS

#### <a name="scep-certificates"></a>Certificati SCEP

Un certificato SCEP viene revocato *e* rimosso quando:
- Un utente annulla la registrazione.
- Un amministratore esegue un'azione di [ritiro](devices-wipe.md#retire).
- Il dispositivo viene rimosso da un gruppo di Azure AD.
- Il profilo certificato viene rimosso dall'assegnazione del gruppo.

Un certificato SCEP viene revocato quando:
- Un amministratore modifica o aggiorna il profilo SCEP.

I certificati SCEP *rimangono* nel dispositivo (i certificati non vengono revocati né rimossi) quando:
- Un utente perde la licenza di Intune.
- Un amministratore ritira la licenza di Intune.
- Un amministratore rimuove l'utente o il gruppo da Azure AD.

> [!NOTE]
> L'uso dell'azione di [cancellazione](devices-wipe.md#wipe) per ripristinare le impostazioni predefinite i nei dispositivi macOS non è supportato.

#### <a name="pkcs-certificates"></a>Certificati PKCS

I certificati PKCS non sono supportati in macOS.

