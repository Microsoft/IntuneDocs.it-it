---
title: Rimuovere certificati SCEP o PKCS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Gli amministratori possono usare l'azione di cancellazione o di ritiro per rimuovere i certificati da Microsoft Intune. Esistono alcuni scenari in cui i certificati vengono rimossi automaticamente, ad esempio se si annulla la registrazione di un dispositivo o si rimuove un criterio di conformità. In alcuni scenari i certificati rimangono automaticamente nel dispositivo, ad esempio quando la licenza di Intune viene smarrita o rimossa. Vedere le diverse modalità per i dispositivi Android, Android, iOS, macOS e Windows.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 977e7006d39ae76516d5b06019e463d1018aaa79
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229259"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Rimuovere i certificati SCEP e PKCS in Microsoft Intune

In Microsoft Intune, è possibile aggiungere i certificati Simple Certificate Enrollment Protocol (SCEP) e Public Key Cryptography Standards (PKCS) ai dispositivi. Questi certificati si possono rimuovere anche quando si [cancella](devices-wipe.md#wipe) o si [ritira](devices-wipe.md#retire) il dispositivo. 

Esistono alcuni altri scenari in cui i certificati vengono rimossi automaticamente e alcuni scenari in cui i certificati rimangono nel dispositivo. Questo articolo illustra alcuni scenari comuni e l'impatto sui certificati SCEP e PKCS.

> [!NOTE]
> Per rimuovere e revocare i certificati per un utente che viene rimosso da Active Directory locale o Azure Active Directory (Azure AD), assicurarsi di seguire i passaggi nell'ordine indicato:
>
> 1. Cancellare o ritirare il dispositivo dell'utente.
> 2. Rimuovere l'utente da Active Directory locale o Azure AD.

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

