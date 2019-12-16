---
title: Impostare i termini e le condizioni in Microsoft Intune
titleSuffix: ''
description: Impostare i termini e le condizioni visualizzati dagli utenti nel portale aziendale per Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fb5818609763753878fec7a84fd8c19eb154f88
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955440"
---
# <a name="terms-and-conditions-for-user-access"></a>Termini e condizioni per l'accesso degli utenti

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'amministratore di Intune può richiedere agli utenti di accettare termini e condizioni aziendali prima di usare il Portale aziendale per:
- registrare dispositivi,
- accedere a risorse quali app aziendali e posta elettronica.

La configurazione dei termini e delle condizioni è facoltativa.

È possibile creare più set di termini e condizioni e assegnarli a gruppi diversi, ad esempio per supportare lingue diverse.

Esistono due modi per creare termini e condizioni aziendali:
- con Intune, come descritto in questo articolo,
- tramite la [funzionalità Condizioni per l'utilizzo di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)

Per individuare il metodo più adatto alle proprie esigenze, vedere il post di blog [Choosing the right Terms solution for your organization](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) (Scelta della soluzione relativa ai termini più adatta all'organizzazione). 

## <a name="create-terms-and-conditions"></a>Creare termini e condizioni
Completare i passaggi seguenti per creare i termini e le condizioni. Il nome visualizzato e la descrizione sono destinati all'uso amministrativo, mentre le proprietà dei termini e delle condizioni vengono visualizzate agli utenti nel portale aziendale.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Amministrazione del tenant** > **Termini e condizioni**.
2. Scegliere **Crea**.
3. Nella pagina **Basic** specificare le informazioni seguenti:

   - **Nome**: nome per i termini e le condizioni nel portale di Azure. Questo nome non viene visualizzato agli utenti.
   - **Description**: dettagli facoltativi che permettono di identificare questo set di condizioni nel portale di Azure.

    ![Screenshot del portale di Azure che mostra la pagina Basic per i termini e le condizioni](./media/terms-and-conditions-create/terms-basics-page.png)

4. Scegliere **Avanti** per passare alla pagina **Termini** e specificare le informazioni seguenti:

   - **Titolo**: nome delle condizioni che verrà visualizzato agli utenti nel portale aziendale sopra **Riepilogo**.
   - **Termini e condizioni**: termini e condizioni visualizzati dagli utenti, che devono accettarli o rifiutarli.
   - **Riepilogo delle condizioni**: testo che spiega il significato dell'accettazione delle condizioni da parte degli utenti. Ad esempio, "Se si registra il dispositivo, si accettano le condizioni per l'utilizzo definite da Contoso. Leggere attentamente le condizioni prima di continuare."

5. Scegliere **Avanti** per passare alla pagina **Tag di ambito**.

6. Scegliere **Selezionare i tag di ambito**, selezionare i tag di ambito da assegnare a questi termini e condizioni, quindi scegliere **Seleziona**. 

7. Scegliere **Avanti** per passare alla pagina **Assegnazioni** e scegliere una delle opzioni seguenti per **Assegna a**:
    - **Tutti gli utenti**: Scegliere questa opzione per assegnare i termini e le condizioni a tutti gli utenti.
    - **Seleziona gruppi**: Scegliere questa opzione per assegnare i termini e le condizioni a tutti nei gruppi identificati scegliendo **Selezionare i gruppi da includere**.

8. Scegliere **Avanti** > **Crea**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Modalità di visualizzazione delle condizioni agli utenti
L'esempio seguente mostra **Titolo** e **Riepilogo delle condizioni** nella console di amministrazione e nel portale aziendale.

![Screenshot di Titolo e Riepilogo delle condizioni nella console di amministrazione e nel portale aziendale.](./media/terms-and-conditions-create/terms-summary-terms.png)

L'esempio seguente mostra i termini e le condizioni nella console di amministrazione e nel portale aziendale.

![Screenshot dei termini e delle condizioni nella console di amministrazione e nel portale aziendale.](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>Monitorare termini e condizioni

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Amministrazione del tenant** > **Termini e condizioni**.
2. Nell'elenco dei termini e delle condizioni scegliere i termini per i quali si vuole visualizzare l'accettazione > **Creazione di report sull'accettazione**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Gestire più versioni di termini e condizioni
È possibile modificare i termini e le condizioni e gestirne le versioni. Ogni volta che si apporta una modifica significativa ai termini e alle condizioni, è necessario:
- aumentare il numero di versione,
- richiedere agli utenti di accettare i nuovi termini e condizioni

Non modificare il numero di versione corrente se, ad esempio, si correggono errori di digitazione o si modifica la formattazione.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), scegliere **Amministrazione del tenant** > **Termini e condizioni** > scegliere i termini e le condizioni da modificare > **Proprietà**.

2. Nel riquadro **Proprietà** scegliere **Termini e condizioni** e quindi modificare **Titolo**, **Riepilogo delle condizioni** e **Termini e condizioni** in base alle esigenze. Se dopo le modifiche è necessario che gli utenti esprimano di nuovo l'accettazione dei termini e delle condizioni, scegliere **Richiedi agli utenti di accettare di nuovo e incrementa il numero di versione a**

3. Scegliere **OK** > **Salva**.

Gli utenti devono accettare i termini e le condizioni aggiornati una sola volta. Gli utenti con più dispositivi non dovranno accettarli in ogni dispositivo.
