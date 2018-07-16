---
title: Abilitare la conformità con Google Play Protect con Microsoft Intune
titleSuffix: ''
description: Informazioni su come creare un criterio di conformità per i dispositivi Android per abilitare Google Play Protect.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 346e69b56d9ee690e2bc3f3970e47d6d25ddcff7
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905173"
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Come creare un criterio di conformità del dispositivo per abilitare Google Play Protect

È possibile creare un nuovo criterio di conformità per la piattaforma Android per verificare la conformità con Google Play Protect (GPP).

I criteri di conformità che richiedono queste impostazioni possono poi essere assegnati a un gruppo di dispositivi o utenti di Android. Se queste impostazioni non sono abilitate in un dispositivo, risulterà non conforme.

## <a name="create-a-compliance-policy"></a>Creare i criteri di conformità

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
2. Scegliere **Conformità del dispositivo** nel gruppo **Gestisci**. 
3. Scegliere **Criteri** e quindi **Crea criterio**.
4. Digitare **Nome** e **Descrizione** per il criterio.
5. Selezionare **Android** per la piattaforma.
6. Scegliere **Impostazioni** > **Integrità del dispositivo**.
7. Configurare le impostazioni di **Google Play Protect**.
8. Dopo aver configurato le impostazioni di Google Play Protect, specificare le impostazioni **Sicurezza del sistema** e **Proprietà dispositivo**. Al termine, scegliere **OK**.

## <a name="configure-the-google-play-protect-settings"></a>Configurare le impostazioni di Google Play Protect

 - **Google Play Services è configurato**  
   Richiede che l'app Google Play Services sia installata e abilitata. Google Play Services consente gli aggiornamenti della sicurezza e rappresenta una dipendenza di base per molte funzionalità di sicurezza nei dispositivi Google certificati.
 - **Provider di sicurezza aggiornato**  
   Richiede un provider di sicurezza aggiornato che può proteggere un dispositivo dalle vulnerabilità note.
 - **Analisi delle minacce nelle app**  
   Richiede l'abilitazione della funzionalità **Verifica app** Android.
    > [!Note]  
    > Nella piattaforma Android legacy, questa funzionalità è un'impostazione di conformità. Intune consente solo di verificare se questa impostazione è abilitata a livello di dispositivo. Nei dispositivi con profili di lavoro Android questa impostazione è disponibile come impostazione dei criteri di configurazione. Ciò consente agli amministratori di abilitare l'impostazione per un dispositivo.

    Se l'organizzazione usa i profili di lavoro Android, è possibile abilitare **Analisi delle minacce nelle app** per i dispositivi registrati. Stabilire un profilo del dispositivo e richiedere l'impostazione di sicurezza del sistema. Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi del profilo di lavoro Android in Intune](device-restrictions-android-for-work.md).

 - **Attestazione del dispositivo SafetyNet**  
   Impostare il livello di integrità dell'attestazione del dispositivo SafetyNet che deve essere raggiunto. I livelli includono **Non configurato**, **Verifica l'integrità di base** e **Verifica l'integrità di base e i dispositivi certificati**.




## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'utilizzo dei criteri di conformità dei dispositivi di Intune, vedere [Introduzione alla conformità dei dispositivi Intune](device-compliance-get-started.md).