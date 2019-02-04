---
title: Impostazioni di Windows Hello for Business in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni per PIN, biometria e anti-spoofing in un profilo di protezione delle identità per usare e configurare Windows Hello for Business nei dispositivi Windows 10 in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b5eb25c48e3724fdc9277a790d01908e976c75be
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54832358"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Impostazioni per i dispositivi Windows 10 (e versioni successive) per abilitare Windows Hello for Business in Intune

Questo articolo elenca e descrive le impostazioni di Windows Hello for Business che è possibile controllare nei dispositivi Windows 10 in Intune. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per usare un PIN o l'impronta digitale per l'accesso e altro ancora.

Come amministratore di Intune, è possibile creare e assegnare queste impostazioni a dispositivi Windows 10 e versioni successive.

Per altre informazioni sui profili di Windows Hello for Business in Intune, vedere [Configurare le impostazioni di Identity Protection in Microsoft Intune](identity-protection-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello for Business

- **Configurare Windows Hello for Business**: per usare questa funzionalità e configurare le impostazioni, scegliere **Abilita**.
- **Lunghezza minima del PIN**: immettere la lunghezza minima del PIN consentita nei dispositivi. La lunghezza del PIN predefinita è di sei caratteri. La lunghezza minima del PIN è quattro (4) caratteri.
- **Lunghezza massima del PIN**: immettere la lunghezza massima del PIN consentita nei dispositivi. La lunghezza del PIN predefinita è di sei (6) caratteri. La lunghezza massima del PIN è 127 caratteri.  
- **Lettere minuscole nel PIN**: è possibile applicare un PIN più efficace richiedendo agli utenti finali di includere lettere minuscole. Le opzioni disponibili sono:

  - **Non consentito** (impostazione predefinita): impedisce agli utenti di usare lettere minuscole nel PIN. Questo comportamento si verifica anche se l'impostazione non è configurata.
  - **Consentito**: consente agli utenti di usare lettere minuscole nel PIN, ma non è obbligatorio.
  - **Obbligatoria**: gli utenti devono includere almeno una lettera minuscola nel PIN. Ad esempio, di solito si richiede almeno una lettera maiuscola e un carattere speciale.

- **Lettere maiuscole nel PIN**: è possibile applicare un PIN più efficace richiedendo agli utenti finali di includere lettere maiuscole. Le opzioni disponibili sono:

  - **Non consentito** (impostazione predefinita): impedisce agli utenti di usare lettere maiuscole nel PIN. Questo comportamento si verifica anche se l'impostazione non è configurata.
  - **Consentito**: consente agli utenti di usare lettere maiuscole nel PIN, ma non è obbligatorio.
  - **Obbligatoria**: gli utenti devono includere almeno una lettera maiuscola nel PIN. Ad esempio, di solito si richiede almeno una lettera maiuscola e un carattere speciale.

- **Caratteri speciali nel PIN**: è possibile applicare un PIN più efficace richiedendo agli utenti finali di includere caratteri speciali. Le opzioni disponibili sono:

  - **Non consentito** (impostazione predefinita): impedisce agli utenti di usare caratteri speciali nel PIN. Questo comportamento si verifica anche se l'impostazione non è configurata.
    I caratteri speciali includono: `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Consentito**: consente agli utenti di usare caratteri speciali nel PIN, ma non è obbligatorio.
  - **Obbligatoria**: gli utenti devono includere almeno un carattere speciale nel PIN. Ad esempio, di solito si richiede almeno una lettera maiuscola e un carattere speciale.

- **Scadenza PIN (giorni)**: Si consiglia di specificare un periodo di scadenza dopo il quale gli utenti finali devono modificare il PIN. L'impostazione predefinita è 41 giorni.

- **Ricorda cronologia PIN**: Limita il riutilizzo di PIN usati in precedenza. Per impostazione predefinita, non è possibile riutilizzare gli ultimi 5 PIN.  
- **Abilita il recupero del PIN**: consente all'utente di modificare il PIN con il servizio di ripristino PIN di Windows Hello for Business.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Usa un modulo TPM (Trusted Platform Module)**: Un chip TPM (Trusted Platform Module) fornisce un livello aggiuntivo di sicurezza dei dati. Scegliere uno dei valori seguenti:  
  - **Abilita**: Solo i dispositivi con un modulo TPM accessibile possono eseguire il provisioning di Windows Hello for Business.
  - **Non configurata**: Tutti i dispositivi possono eseguire il provisioning di Windows Hello for Business, anche quando non esiste alcun modulo TPM utilizzabile. I dispositivi tentano per prima cosa di usare un modulo TPM, ma se non ve ne sono disponibili, i dispositivi possono usare la crittografia software.  

- **Consenti autenticazione biometrica**: Abilita l'autenticazione biometrica, ad esempio il riconoscimento facciale o delle impronte digitali, come alternativa a un PIN di Windows Hello for Business. Gli utenti devono comunque configurare un PIN aziendale in caso di errore dell'autenticazione biometrica. Scegliere tra:

  - **Abilita**: Windows Hello for Business consente l'autenticazione biometrica.
  - **Non configurato** (impostazione predefinita): Windows Hello for Business impedisce l'autenticazione biometrica per tutti i tipi di account.

- **Usa anti-spoofing avanzato, se disponibile**: scegliere se le funzionalità di anti-spoofing di Windows Hello vengono usate nei dispositivi che le supportano. Ad esempio, il rilevamento della fotografia di un viso anziché di un viso reale.

  - **Abilita**: Windows richiede a tutti gli utenti di usare la funzionalità di anti-spoofing per il riconoscimento facciale, se supportata.  
  - **Non configurato** (impostazione predefinita): Windows rispetta le configurazioni di anti-spoofing del dispositivo.

- **Certificato per risorse locali**: 

  - **Abilita**: Consente a Windows Hello for Business di usare i certificati per l'autenticazione a risorse locali.
  - **Non configurato** (impostazione predefinita): Impedisce a Windows Hello for Business di usare i certificati per l'autenticazione a risorse locali.  

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).