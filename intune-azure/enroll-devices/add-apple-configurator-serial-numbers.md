---
title: Aggiungere i numeri di serie di Apple Configurator
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni su come aggiungere numeri di serie a dispositivi iOS di proprietà dell&quot;azienda con Apple Configurator."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d408aa38-7d1e-40df-9067-246e53f6e26f
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 26d253f013195cc18f9a97b8259c603d707d22bf
ms.lasthandoff: 02/18/2017


---

# <a name="add-apple-configurator-serial-numbers"></a>Aggiungere i numeri di serie di Apple Configurator

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare la procedura seguente per aggiungere i numeri di serie a Intune quando si vuole [registrare dispositivi iOS di proprietà dell'azienda con Apple Configurator e Assistente configurazione](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md). È possibile aggiungere i numeri di serie uno alla volta o caricare un file di testo in formato CSV con i numeri di serie. Dopo aver aggiunto i numeri di serie, è possibile assegnare a questi un profilo. Il profilo contiene le impostazioni di gestione specifiche che si desiderano applicare ai dispositivi.

Altri metodi per la registrazione di dispositivi iOS sono descritti in [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (Scegliere la modalità di registrazione dei dispositivi iOS in Intune).

**Per aggiungere numeri di serie di Apple Configurator a Intune**

1. Creare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere l'identificatore IMEI nella colonna a sinistra e i dettagli nella colonna destra. Il limite massimo corrente per l'elenco è di 500 righe. In un editor di testo, l'elenco CSV è simile al seguente:

    F7TLWCLBX196, dettagli del dispositivo</br>
    DLXQPCWVGHMJ, dettagli del dispositivo

2. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

3.  Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Registrazione Apple**.

4. In **Gestisci le impostazioni di registrazione di Apple Configurator** selezionare **Numeri di serie di Apple Configurator**.

5. Nel panello **Numeri di serie di Apple Configurator** selezionare **Aggiungi**.

6. Nel pannello **Aggiungi i numeri di serie** selezionare un profilo da applicare ai numeri di serie che si stanno importando. Se si sta importando un file con nuovi dettagli che sovrascriveranno quelli esistenti, selezionare "Sovrascrivere i dettagli per gli identificatori esistenti." per sostituire i dettagli esistenti con i nuovi.

7. Localizzare il file con estensione CSV dei numeri di serie e selezionare **Aggiungi**.

## <a name="assign-a-profile-to-specific-serial-numbers"></a>Assegnare un profilo a numeri di serie specifici

Intune consente di assegnare i profili da due diverse posizioni nel portale di Azure. A tale scopo, è possibile usare la procedura seguente oppure assegnare i profili dal pannello Profili di registrazione di Apple Configurator, che consente di creare il profilo (vedere [Enroll iOS devices with Apple Configurator by using Setup Assistant](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md) (Registrare dispositivi iOS con Apple Configurator usando Assistente configurazione). È possibile usare la procedura seguente per assegnare il profilo solo se il profilo è già stato creato.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Registrazione Apple**.

3. Nel pannello **Numeri di serie di Apple Configurator** selezionare i numeri di serie a cui si desidera assegnare un profilo, quindi scegliere **Assegna profilo**.

4. Nel pannello **Assegna profilo** selezionare il profilo che si desidera assegnare e quindi scegliere **Assegna**.

## <a name="delete-serial-numbers"></a>Eliminare i numeri di serie
È possibile eliminare i numeri di serie importati in precedenza. È possibile eliminare i numeri di serie solo se è stata innanzitutto annullata la registrazione del dispositivo. Una volta rimosso un numero di serie, non è possibile usare Apple Configurator tramite Assistente configurazione a meno che non venga nuovamente aggiunto il numero di serie.

## <a name="view-the-state-of-a-device"></a>Visualizzare lo stato di un dispositivo
I numeri di serie del dispositivo possono presentare due stati:

- Registrato: il dispositivo è registrato e connesso al servizio Intune
- Non contattato: il dispositivo non si è mai connesso al servizio Intune.
- Reimpostazione in sospeso: il dispositivo è registrato, ma è stata apportata una modifica (ad esempio, le impostazioni di registrazione o il profilo DEP applicato sono stati modificati). Se si modifica il profilo DEP di un dispositivo, le modifiche non vengono applicate fino a quando non viene annullata la registrazione del dispositivo, quindi rieseguita.

**Per visualizzare lo stato di un numero di serie**

Nel pannello **Numeri di serie di Apple Configurator** selezionare il numero di serie di cui si desidera visualizzare lo stato e cercare l'elemento **Stato**.

