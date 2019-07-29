---
title: Configurare le impostazioni di Endpoint Protection in Microsoft Intune - Azure | Microsoft Docs
description: Creare le impostazioni di Endpoint Protection quando si crea un profilo del dispositivo macOS o Windows 10 in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: d0e3e67cd227c5ce8ac2cb42f79bdea1da8e2d75
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375117"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Aggiungere le impostazioni di Endpoint Protection in Intune  

Con Intune, è possibile usare profili di configurazione dei dispositivi per la gestione delle comuni funzionalità di sicurezza di Endpoint Protection nei dispositivi, tra cui:  
- Firewall   
- BitLocker  
- App consentite e bloccate  
- Windows Defender e crittografia  

Ad esempio, è possibile creare un profilo di Endpoint Protection che consente solo agli utenti macOS di installare le app dal Mac App Store. In alternativa, abilitare Windows SmartScreen durante l'esecuzione di app nei dispositivi Windows 10.  

Prima di creare un profilo, rivedere gli articoli seguenti che illustrano in dettaglio le impostazioni di Endpoint Protection che Intune può gestire per ogni piattaforma supportata:  
   - [Impostazioni macOS](endpoint-protection-macos.md)  
   - [Impostazioni Windows 10](endpoint-protection-windows-10.md)  

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Creare un profilo del dispositivo contenente le impostazioni di Endpoint Protection  

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.  
4. Inserire un **Nome** e una **Descrizione** per il profilo di Endpoint Protection.  
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni personalizzate. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:  
   - **macOS**  
   - **Windows 10 e versioni successive**  
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Endpoint Protection**.  
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Per altre informazioni, vedere gli argomenti indicati di seguito.  
   - [Impostazioni macOS](endpoint-protection-macos.md)  
   - [Impostazioni Windows 10](endpoint-protection-windows-10.md)  

8. Dopo aver configurato le impostazioni applicabili, selezionare **Crea** nella pagina **Crea profilo**.  

   Il profilo viene creato e visualizzato nella pagina dell'elenco dei profili. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).  

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Aggiungere regole del firewall personalizzate per dispositivi Windows 10  
***Le regole del firewall personalizzate sono disponibili in anteprima pubblica.***  

Quando si configura Windows Defender Firewall come parte di un profilo che include regole di protezione endpoint per Windows 10, è possibile configurare regole personalizzate per i firewall. Le regole personalizzate consentono di espandere il set predefinito di regole firewall supportate per Windows 10.  

Quando si pianificano profili con regole del firewall personalizzate tenere presenti le informazioni seguenti, che potrebbero influire sulla scelta della modalità di raggruppamento delle regole del firewall nei profili:  
- Ogni profilo supporta fino a 150 regole del firewall. Quando si usano più di 150 regole creare profili aggiuntivi, ognuno con un limite di 150 regole.  
- Per ogni profilo, se non è possibile applicare una singola regola, nessuna delle regole in tale profilo viene eseguita e nessuna delle regole viene applicata al dispositivo.  
- Quando non è possibile applicare una regola, tutte le regole nel profilo vengono segnalate come non riuscite. Intune non è in grado di identificare quale singola regola non è andata a buon fine.  

Le regole del firewall che Intune può gestire sono descritte in dettaglio nel [provider del servizio di configurazione (CSP) firewall]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) di Windows. Per esaminare l'elenco delle impostazioni personalizzate del firewall per i dispositivi Windows 10 supportati da Intune, vedere [Regole del firewall personalizzate](endpoint-protection-windows-10.md#custom-firewall-rules).  

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Per aggiungere regole del firewall personalizzate a un profilo Endpoint Protection  

1. In Intune selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.  

2. In *Piattaforma* selezionare **Windows 10 e versioni successive** e in *Tipo di profilo* selezionare **Endpoint Protection**.  

3. Selezionare **Windows Defender Firewall** per aprire la pagina di configurazione e quindi in *Regole del firewall* selezionare **Aggiungi** per aprire la pagina **Crea regola**.  

4. Specificare le impostazioni per la regola del firewall e quindi fare clic su **OK** per salvarle. Per esaminare le opzioni di regole del firewall personalizzate disponibili nella documentazione, vedere [Regole del firewall personalizzate](endpoint-protection-windows-10.md#custom-firewall-rules).  

5. Dopo il salvataggio, la regola viene visualizzata nella pagina *Windows Defender Firewall* dell'elenco di regole.  

6. Per modificare una regola, selezionare la regola nell'elenco per aprire la pagina **Modifica regola**.  

7. Per eliminare una regola da un profilo, selezionare i puntini di sospensione **(…)** per la regola e quindi selezionare **Elimina**.  

8. Per modificare l'ordine di visualizzazione delle regole selezionare l'icona *freccia su o freccia giù* nella parte superiore dell'elenco regole.  


## <a name="next-steps"></a>Passaggi successivi  

Per assegnare un profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).  
