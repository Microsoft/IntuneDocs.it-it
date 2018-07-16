---
title: Cancellare i dati in modo selettivo usando le azioni di accesso per i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Informazioni su come cancellare i dati in modo selettivo usando le azioni di accesso per i criteri di protezione delle app in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2cfd426a0ae7165a7aae60a90d104852fd834db6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909117"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Cancellare i dati in modo selettivo usando le azioni di accesso per i criteri di protezione delle app in Intune

I criteri di protezione delle app di Intune consentono di configurare impostazioni per impedire agli utenti finali di accedere a un'app o un account aziendale. Queste impostazioni riguardano la rilocazione dei dati e i requisiti di accesso definiti dall'organizzazione per aspetti quali dispositivi jail-broken e versioni minime del sistema operativo.
 
Usando queste impostazioni, è possibile scegliere in modo esplicito di cancellare i dati aziendali dell'organizzazione dal dispositivo dell'utente finale come azione da intraprendere in caso di non conformità. Per alcune impostazioni sarà possibile configurare più azioni, ad esempio il blocco dell'accesso e la cancellazione dei dati in base a diversi valori specificati.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Creare criteri di protezione delle app usando le azioni di accesso

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**.  
    Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App per dispositivi mobili** > **Criteri di protezione delle app**.
4. Fare clic su **Aggiungi criteri**. È anche possibile modificare criteri esistenti. 
5. Fare clic su **Configura le impostazioni obbligatorie** per visualizzare l'elenco di impostazioni configurabili per il criterio. 
6. Scorrendo verso il basso nel riquadro **Impostazioni** verrà visualizzata una sezione denominata **Azioni di accesso** con una tabella modificabile.

    ![Screenshot delle azioni di accesso per la protezione delle app di Intune](./media/apps-selective-wipe-access-actions01.png)

7. Selezionare una **impostazione** e immettere il **valore** che gli utenti devono soddisfare per accedere all'app aziendale. 
8. Selezionare l'**azione** da intraprendere se gli utenti non soddisfano i requisiti. In alcuni casi è possibile configurare più azioni per una singola impostazione. Per altre informazioni, vedere [Come creare e assegnare criteri di protezione delle app](app-protection-policies.md).

>[!NOTE]
> Per usare l'impostazione **Modello/i dispositivo**, inserire un elenco di identificatori di modello separati da punto e virgola. 

## <a name="policy-settings"></a>Impostazioni criteri 

La tabella delle impostazioni dei criteri di protezione delle app contiene le colonne **Impostazione**, **Valore** e **Azione**.

Per iOS è possibile configurare azioni per le impostazioni seguenti usando l'elenco a discesa della colonna **Impostazione**:
-  Numero massimo di tentativi di PIN
-  Periodo di prova offline
-  Dispositivi jailbroken/rooted
-  Versione minima del sistema operativo
-  Versione minima dell'app
-  Versione minima dell'SDK
-  Modello/i dispositivo

Per Android è possibile configurare azioni per le impostazioni seguenti usando l'elenco a discesa della colonna **Impostazione**:
-  Numero massimo di tentativi di PIN
-  Periodo di prova offline
-  Dispositivi jailbroken/rooted
-  Versione minima del sistema operativo
-  Versione minima dell'app
-  Versione minima della patch
-  Produttore/i dispositivo

Per impostazione predefinita, la tabella avrà righe popolate come le impostazioni configurate per **Periodo di prova offline** e **Numero massimo di tentativi di PIN**, se l'impostazione **Richiedi PIN per l'accesso** è impostata su **Sì**.
 
Per configurare un'impostazione, selezionarla dall'elenco a discesa nella colonna **Impostazione**. Dopo aver selezionato un'impostazione, viene abilitata la casella di testo modificabile nella colonna **Valore** sulla stessa riga, se è necessario impostare un valore. L'elenco a discesa viene inoltre abilitato nella colonna **Azione** con il set di azioni di avvio condizionale applicabili all'impostazione. 

L'elenco seguente riporta le azioni comuni:
-  **Blocca l'accesso**: blocca l'accesso dell'utente finale all'app aziendale.
-  **Cancella i dati**: cancella i dati aziendali dal dispositivo dell'utente finale.
-  **Avvisa**: visualizza una finestra di dialogo per l'utente finale come messaggio di avviso.

### <a name="additional-settings-and-actions"></a>Impostazioni e azioni aggiuntive 

In alcuni casi, ad esempio per l'impostazione **Versione minima del sistema operativo**, è possibile configurare l'impostazione per l'esecuzione di tutte le azioni applicabili in base ai diversi numeri di versione. 

![Screenshot delle azioni di accesso per la protezione delle app di Intune - Versione minima del sistema operativo](./media/apps-selective-wipe-access-actions05.png)

Al termine della configurazione di un'impostazione, la riga sarà posta nella visualizzazione di sola lettura e sarà disponibile per la modifica in qualsiasi momento. La riga avrà anche un elenco a discesa disponibile per la selezione nella colonna **Impostazione**. Le impostazioni già configurate che non consentono azioni multiple non saranno disponibili per la selezione nell'elenco a discesa.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui criteri di protezione delle app di Intune, vedere:
- [Come creare e assegnare criteri di protezione delle app](app-protection-policies.md) (How to create and assign app protection policies)
- [Impostazioni dei criteri di protezione delle app per iOS](app-protection-policy-settings-ios.md)
- [Impostazioni dei criteri di protezione delle app di Android in Microsoft Intune](app-protection-policy-settings-android.md) 


