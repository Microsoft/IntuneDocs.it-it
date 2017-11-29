---
title: "Abilitare la conformità con Google Play Protect con Intune"
titleSuffix: Azure portal
description: "Informazioni su come creare un criterio di conformità per i dispositivi Android per abilitare Google Play Protect."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d610bc338c1bcf81ed3bc71f1357e001914c5877
ms.sourcegitcommit: 71e6e80b7370024624ce2e5fad1ca5b372975748
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Come creare un criterio di conformità del dispositivo per abilitare Google Play Protect

È possibile creare un nuovo criterio di conformità per la piattaforma Android per verificare la conformità con Google Play Protect (GPP).

I criteri di conformità che richiedono queste impostazioni possono poi essere assegnati a un gruppo di dispositivi o utenti di Android. Se queste impostazioni non sono abilitate in un dispositivo, risulterà non conforme.

## <a name="create-a-compliance-policy"></a>Creare i criteri di conformità

1. Accedere al portale di Azure. Scegliere **Altri servizi** > **Monitoraggio e gestione** + **Intune**.
2. Scegliere **Conformità del dispositivo** nel gruppo **Gestisci**. 
3. Scegliere **Criteri**e quindi **Crea criterio**.
4. Digitare **Nome** e **Descrizione** per il criterio.
5. Selezionare **Android** per la piattaforma.
6. Scegliere **Impostazioni** > **Integrità del dispositivo**.
7. Configurare le impostazioni di **Google Play Protect**.
8. Dopo aver configurato le impostazioni di Google Play Protect, specificare le impostazioni **Sicurezza** e **Proprietà dispositivo**. Al termine, scegliere **Salva**.

## <a name="configure-the-google-play-protect-settings"></a>Configurare le impostazioni di Google Play Protect

 - **Google Play Services è configurato**  
   Richiede che l'app Google Play Services sia installata e abilitata. Google Play Services consente gli aggiornamenti della sicurezza e rappresenta una dipendenza di base per molte funzionalità di sicurezza nei dispositivi Google certificati.
 - **Provider di sicurezza aggiornato**  
   Richiede un provider di sicurezza aggiornato che può proteggere un dispositivo dalle vulnerabilità note.
 - **Analisi delle minacce nelle app**  
   Richiede l'abilitazione della funzionalità **Verifica app** Android.
    > [!Note]  
    > Nella piattaforma Android legacy, questa funzionalità è un'impostazione di conformità. Intune consente solo di verificare se questa impostazione è abilitata a livello di dispositivo. Nei dispositivi con profili di lavoro, in precedenza Android for Work, questa impostazione è disponibile come impostazione dei criteri di configurazione. Ciò consente agli amministratori di abilitare l'impostazione per un dispositivo.

    Se l'organizzazione usa i profili di lavoro Android, è possibile abilitare **Analisi delle minacce nelle app** per i dispositivi registrati. Stabilire un profilo del dispositivo e richiedere l'impostazione di sicurezza del sistema. Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune](device-restrictions-android-for-work.md).

 - **Attestazione del dispositivo SafetyNet**  
   Impostare il livello di integrità dell'attestazione del dispositivo SafetyNet che deve essere raggiunto. I livelli includono **Non configurato**, **Verifica l'integrità di base** e **Verifica l'integrità di base e i dispositivi certificati**.




## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'utilizzo dei criteri di conformità dei dispositivi di Intune, vedere [Introduzione alla conformità dei dispositivi Intune](device-compliance-get-started.md).