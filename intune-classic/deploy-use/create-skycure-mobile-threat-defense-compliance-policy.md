---
title: "Creare i criteri di conformità di Skycure Mobile Threat Defense"
description: "Creare i criteri di conformità di Skycure Mobile Threat Defense nella console classica di Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 29caf162500e25c2a0151be92aabe4cc432e241b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>Creare i criteri di conformità di Skycure Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune con Skycure Mobile Threat Defense consente di rilevare le minacce nei dispositivi mobili e valutare i rischi in tali dispositivi. È possibile creare una regola dei criteri di conformità di Intune che valuta i rischi per determinare se il dispositivo è conforme. Si possono quindi usare i criteri di accesso condizionale per bloccare l'accesso ai servizi in base alla conformità del dispositivo.

## <a name="before-you-begin"></a>Prima di iniziare

Prerequisiti per i criteri di conformità con la protezione dalle minacce per il dispositivo di Skycure:

-   [Configurare l'integrazione di Skycure con Intune](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

-   [Abilitare la connessione a Skycure in Intune](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

Nell'ambito della configurazione di Skycure Mobile Threat Defense, nella console di Skycure è stato creato un criterio per la classificazione delle varie minacce in base ai livelli alto, medio e basso. È ora necessario impostare il livello di minaccia massimo consentito nei criteri di conformità di Intune.

## <a name="to-create-skycure-compliance-policy"></a>Per creare i criteri di conformità di Skycure

1.  Passare alla [console classica di Intune](https://manage.microsoft.com/) e immettere le proprie credenziali.

2.  Scegliere **Criteri** &gt; **Criteri di conformità**. È possibile usare criteri di conformità esistenti o crearne di nuovi.

3.  Scegliere **Aggiungi** &gt; **Integrità del dispositivo** e quindi abilitare **Protezione dalle minacce per il dispositivo**.

4.  Selezionare **Livello di minaccia massimo consentito**:

    a.  **Nessuno (protetto)**: questo è il livello più sicuro. Nel dispositivo non possono essere presenti minacce per poter accedere alle risorse aziendali. Se viene rilevata qualsiasi minaccia, il dispositivo viene valutato come non conforme.

    b.  **Basso**: il dispositivo è conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.

    c.  **Medio**: il dispositivo è conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.

    d.  **Alta**: questo è il livello meno sicuro. Questa impostazione consente tutti i livelli di minacce e usa Skycure Mobile Threat Defense solo a scopi di report.

> [!IMPORTANT]
> Se si creano criteri di accesso condizionale per Office 365 e altri servizi, questa valutazione di conformità viene considerata e per i dispositivi non conformi viene bloccato l'accesso a questi servizi fino alla risoluzione della condizione di minaccia.

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>Passaggi successivi

-   Creare criteri di accesso condizionale per:

    -   [Exchange Online](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange locale](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [Skype for Business Online](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)