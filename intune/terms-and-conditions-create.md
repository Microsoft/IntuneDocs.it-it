---
title: Impostare i termini e le condizioni in Microsoft Intune
titlesuffix: ''
description: Impostare i termini e le condizioni visualizzati dagli utenti nel portale aziendale per Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ecc5228eef9e9d7be5ba567db6b32c84e95df1b6
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032300"
---
# <a name="terms-and-conditions-for-user-access"></a>Termini e condizioni per l'accesso degli utenti

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'amministratore di Intune può richiedere agli utenti di accettare termini e condizioni aziendali prima di usare il Portale aziendale per:
- registrare dispositivi,
- accedere a risorse quali app aziendali e posta elettronica.
La configurazione dei termini e delle condizioni è facoltativa.

È possibile creare più set di termini e condizioni e assegnarli a gruppi diversi, ad esempio per supportare lingue diverse.

Esistono due modi per creare termini e condizioni aziendali:
- con Intune, come descritto in questo articolo,
- tramite la [funzionalità Condizioni per l'utilizzo di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou). Per individuare il metodo più adatto alle proprie esigenze, vedere il post di blog [Choosing the right Terms solution for your organization](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409) (Scelta della soluzione relativa ai termini più adatta all'organizzazione). 

## <a name="create-terms-and-conditions"></a>Creare termini e condizioni
Completare i passaggi seguenti per creare i termini e le condizioni. Il nome visualizzato e la descrizione sono destinati all'uso amministrativo, mentre le proprietà dei termini e delle condizioni vengono visualizzate agli utenti nel portale aziendale.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro di **Intune** scegliere **Registrazione del dispositivo** > **Termini e condizioni**.
2. Scegliere **Crea**.
![Screenshot del portale di Azure che mostra il pulsante Crea per i termini e le condizioni](media/terms-create-terms.png)
3. Nel riquadro espanso specificare le informazioni seguenti:

   - **Nome visualizzato**: nome per i termini e le condizioni nel portale di Azure. Questo nome non viene visualizzato agli utenti.

   - **Descrizione**: dettagli facoltativi che permettono di identificare questo set di condizioni nel portale di Azure.

4. Scegliere la freccia accanto a **Define terms of use** (Definisci le condizioni per l'utilizzo) per aprire il riquadro Termini e condizioni e quindi immettere le informazioni seguenti:

   ![Screenshot della schermata di accettazione di termini e condizioni per l'utente finale con riepilogo dei termini](./media/terms-summary-create.png)

   - **Titolo**: nome delle condizioni che verrà visualizzato agli utenti nel portale aziendale sopra **Riepilogo**.
   - **Riepilogo delle condizioni**: testo che spiega il significato dell'accettazione delle condizioni da parte degli utenti. Ad esempio, "Se si registra il dispositivo, si accettano le condizioni per l'utilizzo definite da Contoso. Leggere attentamente le condizioni prima di continuare."
   - **Termini e condizioni**: termini e condizioni visualizzati dagli utenti, che devono accettarli o rifiutarli.

5. Scegliere **OK** > **Crea**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Modalità di visualizzazione delle condizioni agli utenti
L'esempio seguente mostra **Titolo** e **Riepilogo delle condizioni** nella console di amministrazione e nel portale aziendale.

![Screenshot di Titolo e Riepilogo delle condizioni nella console di amministrazione e nel portale aziendale.](./media/terms-summary-terms.png)

L'esempio seguente mostra i termini e le condizioni nella console di amministrazione e nel portale aziendale.

![Screenshot dei termini e delle condizioni nella console di amministrazione e nel portale aziendale.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Assegnare termini e condizioni

È possibile assegnare termini e condizioni a gruppi di utenti, che devono accettarli prima di usare il portale aziendale.

1. Nel portale di Azure scegliere **Registrazione del dispositivo** e quindi **Termini e condizioni**.
2. Nell'elenco dei termini e delle condizioni scegliere i termini da assegnare > **Gestisci** > **Assegnazioni**.
![Screenshot del riquadro Assegna gruppi del portale di Azure in cui vengono visualizzati i pulsanti Selezione gruppo e Seleziona per l'assegnazione di termini e condizioni](media/terms-assign-groups.png)
3. Scegliere **Selezionare i gruppi da includere** > scegliere i gruppi a cui assegnare i termini > **Seleziona**. Non è possibile assegnare termini e condizioni ai gruppi dinamici.
4. Nel riquadro **Gruppi assegnati** scegliere **Salva**.  I termini e le condizioni sono ora assegnati a utenti in gruppi selezionati. Agli utenti verrà chiesto di accettare i termini e le condizioni al successivo accesso al portale aziendale. I termini e le condizioni devono essere accettati una sola volta. Gli utenti con più dispositivi non dovranno accettarli in ogni dispositivo.


## <a name="monitor-terms-and-conditions"></a>Monitorare termini e condizioni

1. Nel portale di Azure scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**. 
1. Nel riquadro di Intune scegliere **Registrazione del dispositivo** > **Termini e condizioni**.
2. Nell'elenco dei termini e delle condizioni scegliere i termini per i quali si vuole visualizzare l'accettazione > **Creazione di report sull'accettazione**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Gestire più versioni di termini e condizioni
È possibile modificare i termini e le condizioni e gestirne le versioni. Ogni volta che si apporta una modifica significativa ai termini e alle condizioni, è necessario:
- aumentare il numero di versione,
- richiedere agli utenti di accettare i nuovi termini e condizioni. Mantenere il numero di versione corrente se nella nuova versione, ad esempio, vengono corretti errori di digitazione o viene modificata la formattazione.

1. Nel portale di Azure scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel riquadro di Intune scegliere **Registrazione del dispositivo** > **Termini e condizioni** > scegliere i termini e le condizioni da modificare > **Proprietà**.

4. Nel riquadro **Proprietà** scegliere **Termini e condizioni** e quindi modificare **Titolo**, **Riepilogo delle condizioni** e **Termini e condizioni** in base alle esigenze. Se dopo le modifiche è necessario che gli utenti esprimano di nuovo l'accettazione dei termini e delle condizioni, scegliere **Richiedi agli utenti di accettare di nuovo e incrementa il numero di versione a**

4.  Scegliere **OK** > **Salva**.

Gli utenti devono accettare i termini e le condizioni aggiornati una sola volta. Gli utenti con più dispositivi non dovranno accettarli in ogni dispositivo.
