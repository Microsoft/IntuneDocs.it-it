---
title: Creare un ruolo personalizzato in Intune
description: Informazioni su come creare un ruolo personalizzato in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569184"
---
# <a name="create-a-custom-role-in-intune"></a>Creare un ruolo personalizzato in Intune

È possibile creare un ruolo di Intune personalizzato che include le autorizzazioni necessarie per un ruolo professionale specifico. Ad esempio, se un gruppo del reparto IT gestisce le applicazioni, i criteri e i profili di configurazione, è possibile aggiungere tutte queste autorizzazioni insieme in un ruolo personalizzato. Dopo aver creato un ruolo personalizzato, è possibile [assegnare](assign-role.md) il ruolo a tutti gli utenti che necessitano di tali autorizzazioni.

Per creare, modificare o assegnare ruoli, l'account deve disporre di una delle seguenti autorizzazioni in Azure AD:
- **Amministratore globale**
- **Amministratore del servizio Intune**

## <a name="to-create-a-custom-role"></a>Per creare un ruolo personalizzato

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Amministrazione del tenant** > **Ruoli** > **Tutti i ruoli** > **Crea**.

2. Nella pagina **Informazioni di base** immettere un nome e una descrizione per il nuovo ruolo e quindi scegliere **Avanti**.

3. Nella pagina **Autorizzazioni** scegliere le autorizzazioni da usare con il ruolo.

4. Nella pagina **Ambito (tag)** scegliere i tag per il ruolo. Questo ruolo può accedere alle risorse che hanno questi tag. Scegliere **Avanti**.

5. Al termine, nella pagina **Rivedi e crea** scegliere **Crea**. Il nuovo ruolo viene visualizzato nell'elenco del pannello **Ruoli di Intune- Tutti i ruoli**.

## <a name="copy-a-role"></a>Copiare un ruolo

È anche possibile copiare un ruolo esistente.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Amministrazione del tenant** > **Ruoli** > **Tutti i ruoli** > selezionare la casella di controllo per un ruolo nell'elenco > **Duplicato**.

2. Nella pagina **Informazioni di base** immettere un nome. Assicurarsi di usare un nome univoco.

3. Tutte le autorizzazioni e i tag di ambito del ruolo originale risulteranno già selezionati. Successivamente, è possibile modificare il **nome**, la **descrizione**, le **autorizzazioni** e **i tag di ambito** del ruolo duplicato.

4. Dopo aver apportato tutte le modifiche desiderate, scegliere **Avanti** per visualizzare la pagina **Rivedi e crea**. Selezionare **Crea**. 

## <a name="next-steps"></a>Passaggi successivi
- [Assegnare un ruolo a un utente](assign-role.md)
- [Informazioni sul controllo degli accessi in base al ruolo in Intune](role-based-access-control.md)


