---
title: Rimuovere certificati SCEP o PKCS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Gli amministratori possono usare l'azione di cancellazione o di ritiro per rimuovere i certificati da Microsoft Intune. Esistono alcuni scenari in cui i certificati vengono rimossi automaticamente, ad esempio se si annulla la registrazione di un dispositivo o si rimuove un criterio di conformità. In alcuni scenari i certificati rimangono automaticamente nel dispositivo, ad esempio quando la licenza di Intune viene smarrita o rimossa. Vedere le diverse modalità per i dispositivi Android, Android, iOS, macOS e Windows.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d4287322fd494c97cf24feb8cc16435a4405f2af
ms.sourcegitcommit: 7a649a5995600fb91817643e20a5565caedbb8f2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/26/2018
ms.locfileid: "50150108"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Rimuovere i certificati SCEP e PKCS in Microsoft Intune

In Microsoft Intune è possibile aggiungere i certificati SCEP e PKCS ai dispositivi. Questi certificati si possono rimuovere anche quando si [cancella](devices-wipe.md#wipe) o si [ritira](devices-wipe.md#retire) il dispositivo. Esistono alcuni altri scenari in cui i certificati vengono rimossi automaticamente e alcuni scenari in cui i certificati rimangono nel dispositivo.

Questo articolo illustra alcuni scenari comuni e l'impatto sui certificati SCEP e PKCS.

> [!NOTE]
> Per rimuovere e revocare i certificati per un utente che viene rimosso da Active Directory (AD) o Azure AD, assicurarsi di seguire i passaggi nell'ordine indicato:
>
>    1. Cancellare o ritirare il dispositivo dell'utente
>    2. Rimuovere l'utente da Active Directory o Azure Active Directory

## <a name="windows-devices"></a>Dispositivi Windows

#### <a name="scep-certificates"></a>Certificati SCEP

- Un certificato SCEP viene revocato *e* rimosso quando:

  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)
  - Il dispositivo viene rimosso dal gruppo di Azure Active Directory (AD)
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo
  - Il profilo di configurazione viene rimosso dall'assegnazione del gruppo

- Un certificato SCEP viene revocato quando:
  - L'amministratore modifica o aggiorna il profilo SCEP

- Il certificato radice viene rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo

- I certificati SCEP **rimangono** nel dispositivo (i certificati non vengono revocati né rimossi) quando:
  - Un utente finale perde la licenza di Intune
  - L'amministratore ritira la licenza di Intune
  - L'amministratore rimuove l'utente o il gruppo da Azure AD

#### <a name="pkcs-certificates"></a>Certificati PKCS

- Un certificato PKCS viene revocato *e* rimosso quando:

  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)

- Il certificato radice viene rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)

- I certificati PKCS **rimangono** nel dispositivo (i certificati non vengono revocati né rimossi) quando:
  - Un utente finale perde la licenza di Intune
  - L'amministratore ritira la licenza di Intune
  - L'amministratore rimuove l'utente o il gruppo da Azure AD
  - L'amministratore modifica o aggiorna il profilo PKCS
  - Il profilo di configurazione viene rimosso dall'assegnazione del gruppo
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo 


## <a name="ios-devices"></a>Dispositivi iOS

#### <a name="scep-certificates"></a>Certificati SCEP

- Un certificato SCEP viene revocato *e* rimosso quando:

  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)
  - Il dispositivo viene rimosso dal gruppo di Azure Active Directory (AD)
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo
  - Il profilo di configurazione viene rimosso dall'assegnazione del gruppo

- Un certificato SCEP viene revocato quando:
  - L'amministratore modifica o aggiorna il profilo SCEP

- Il certificato radice viene rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo

- I certificati SCEP **rimangono** nel dispositivo (i certificati non vengono revocati né rimossi) quando:
  - Un utente finale perde la licenza di Intune
  - L'amministratore ritira la licenza di Intune
  - L'amministratore rimuove l'utente o il gruppo da Azure AD

#### <a name="pkcs-certificates"></a>Certificati PKCS

- Un certificato PKCS viene revocato *e* rimosso quando:

  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)

- Un certificato PKCS viene rimosso quando:
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo
  - Il profilo di configurazione viene rimosso dall'assegnazione del gruppo
  
- Il certificato radice viene rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)

- I certificati PKCS **rimangono** nel dispositivo (i certificati non vengono revocati né rimossi) quando:
  - Un utente finale perde la licenza di Intune
  - L'amministratore ritira la licenza di Intune
  - L'amministratore rimuove l'utente o il gruppo da Azure AD
  - L'amministratore modifica o aggiorna il profilo PKCS

## <a name="android--android-enterprise-devices"></a>Dispositivi Android e Android Enterprise

#### <a name="scep-certificates"></a>Certificati SCEP

- Un certificato SCEP viene revocato *e* rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)

- Un certificato SCEP viene revocato quando:
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)
  - Il dispositivo viene rimosso dal gruppo di Azure Active Directory (AD)
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo
  - Il profilo di configurazione viene rimosso dall'assegnazione del gruppo
  - L'amministratore rimuove l'utente o il gruppo da Azure Active Directory (AD)
  - L'amministratore modifica o aggiorna il profilo SCEP

- Il certificato radice viene rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)

- I certificati SCEP **rimangono** nel dispositivo (i certificati non vengono revocati né rimossi) quando:
  - Un utente finale perde la licenza di Intune
  - L'amministratore ritira la licenza di Intune
  - L'amministratore rimuove l'utente o il gruppo da Azure AD

#### <a name="pkcs-certificates"></a>Certificati PKCS

- Un certificato PKCS viene revocato *e* rimosso quando:

  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)

- Il certificato radice viene rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [cancellazione](devices-wipe.md#wipe)
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)

- I certificati PKCS **rimangono** nel dispositivo (i certificati non vengono revocati né rimossi) quando:
  - Un utente finale perde la licenza di Intune
  - L'amministratore ritira la licenza di Intune
  - L'amministratore rimuove l'utente o il gruppo da Azure AD
  - L'amministratore modifica o aggiorna il profilo PKCS
  - Il profilo di configurazione viene rimosso dall'assegnazione del gruppo
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo 

## <a name="macos-certificates"></a>Certificati macOS

#### <a name="scep-certificates"></a>Certificati SCEP

- Un certificato SCEP viene revocato *e* rimosso quando:
  - Un utente finale annulla la registrazione
  - L'amministratore esegue un'azione di [ritiro](devices-wipe.md#retire)
  - Il dispositivo viene rimosso dal gruppo di Azure Active Directory (AD)
  - I criteri di conformità vengono rimossi dall'assegnazione del gruppo
  - Il profilo di configurazione viene rimosso dall'assegnazione del gruppo

- Un certificato SCEP viene revocato quando:
  - L'amministratore modifica o aggiorna il profilo SCEP

- I certificati SCEP **rimangono** nel dispositivo (i certificati non vengono revocati né rimossi) quando:
  - Un utente finale perde la licenza di Intune
  - L'amministratore ritira la licenza di Intune
  - L'amministratore rimuove l'utente o il gruppo da Azure AD

> [!NOTE]
> L'uso dell'azione di [cancellazione](devices-wipe.md#wipe) per ripristinare le impostazioni predefinite i nei dispositivi macOS non è supportato.

#### <a name="pkcs-certificates"></a>Certificati PKCS

I certificati PKCS non sono supportati in macOS.

