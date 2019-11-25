---
title: Configurare le impostazioni di Endpoint Protection in Microsoft Intune - Azure | Microsoft Docs
description: Creare le impostazioni di Endpoint Protection quando si crea un profilo del dispositivo macOS o Windows 10 in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 45cdbfe98bca8f7b0e307ed47ad3f78193e6d04c
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164577"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Aggiungere le impostazioni di Endpoint Protection in Intune

Con Intune, è possibile usare profili di configurazione dei dispositivi per la gestione delle comuni funzionalità di sicurezza di Endpoint Protection nei dispositivi, tra cui:

- Firewall
- BitLocker
- App consentite e bloccate
- Microsoft Defender e crittografia

Ad esempio, è possibile creare un profilo di Endpoint Protection che consente solo agli utenti macOS di installare le app dal Mac App Store. In alternativa, abilitare Windows SmartScreen durante l'esecuzione di app nei dispositivi Windows 10.

Prima di creare un profilo, rivedere gli articoli seguenti che illustrano in dettaglio le impostazioni di Endpoint Protection che Intune può gestire per ogni piattaforma supportata:

- [Impostazioni macOS](endpoint-protection-macos.md)
- [Impostazioni Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Creare un profilo del dispositivo contenente le impostazioni di Endpoint Protection

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. Inserire un **Nome** e una **Descrizione** per il profilo di Endpoint Protection.

4. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni personalizzate. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:

   - **macOS**
   - **Windows 10 e versioni successive**

5. Dall'elenco a discesa **Tipo di profilo** scegliere **Endpoint Protection**.

6. Le impostazioni configurabili variano in base alla piattaforma scelta. Per altre informazioni, vedere gli argomenti indicati di seguito.

   - [Impostazioni macOS](endpoint-protection-macos.md)
   - [Impostazioni Windows 10](endpoint-protection-windows-10.md)

7. Dopo aver configurato le impostazioni applicabili, selezionare **Crea** nella pagina **Crea profilo**.

   Il profilo viene creato e visualizzato nella pagina dell'elenco dei profili. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](../configuration/device-profile-assign.md).

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Aggiungere regole del firewall personalizzate per dispositivi Windows 10

Quando si configura Microsoft Defender Firewall come parte di un profilo che include regole di Endpoint Protection per Windows 10, è possibile configurare regole personalizzate per i firewall. Le regole personalizzate consentono di espandere il set predefinito di regole firewall supportate per Windows 10.

Quando si pianificano profili con regole del firewall personalizzate tenere presenti le informazioni seguenti, che potrebbero influire sulla scelta della modalità di raggruppamento delle regole del firewall nei profili:

- Ogni profilo supporta fino a 150 regole del firewall. Quando si usano più di 150 regole creare profili aggiuntivi, ognuno con un limite di 150 regole.

- Per ogni profilo, se non è possibile applicare una singola regola, nessuna delle regole in tale profilo viene eseguita e nessuna delle regole viene applicata al dispositivo.

- Quando non è possibile applicare una regola, tutte le regole nel profilo vengono segnalate come non riuscite. Intune non è in grado di identificare quale singola regola non è andata a buon fine.  

Le regole del firewall che Intune può gestire sono descritte in dettaglio nel [provider del servizio di configurazione (CSP) firewall]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) di Windows. Per esaminare l'elenco delle impostazioni personalizzate del firewall per i dispositivi Windows 10 supportati da Intune, vedere [Regole del firewall personalizzate](endpoint-protection-windows-10.md#firewall-rules).

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Per aggiungere regole del firewall personalizzate a un profilo Endpoint Protection

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. In *Piattaforma* selezionare **Windows 10 e versioni successive** e in *Tipo di profilo* selezionare **Endpoint Protection**.

4. Selezionare **Microsoft Defender Firewall** per aprire la pagina di configurazione, quindi in *Regole del firewall* selezionare **Aggiungi** per aprire la pagina **Crea regola**.

5. Specificare le impostazioni per la regola del firewall e quindi fare clic su **OK** per salvarle. Per esaminare le opzioni di regole del firewall personalizzate disponibili nella documentazione, vedere [Regole del firewall personalizzate](endpoint-protection-windows-10.md#firewall-rules).

6. Dopo il salvataggio, la regola viene visualizzata nella pagina *Microsoft Defender Firewall* nell'elenco di regole.

7. Per modificare una regola, selezionare la regola nell'elenco per aprire la pagina **Modifica regola**.

8. Per eliminare una regola da un profilo, selezionare i puntini di sospensione **(…)** per la regola e quindi selezionare **Elimina**.

9. Per modificare l'ordine di visualizzazione delle regole selezionare l'icona *freccia su o freccia giù* nella parte superiore dell'elenco regole.

## <a name="next-steps"></a>Passaggi successivi

Per assegnare un profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](../configuration/device-profile-assign.md).
