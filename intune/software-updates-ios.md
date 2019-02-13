---
title: Configurare i criteri di aggiornamento software per iOS in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune è possibile creare o aggiungere criteri di configurazione per limitare l'installazione automatica di aggiornamenti software nei dispositivi iOS gestiti da o sotto la supervisione di Intune. È possibile scegliere la data e ora in cui l'installazione degli aggiornamenti non verrà effettuata. È anche possibile assegnare questi criteri a gruppi, utenti o dispositivi e verificare la presenza di eventuali errori di installazione.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
search.appverid: MET150
ms.openlocfilehash: d73dc96c966b93f26269cc53527a787824c94d3b
ms.sourcegitcommit: 00fe2b601e3becbe5d644fcbd35a706da3b43af2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652630"
---
# <a name="configure-ios-update-policies-in-intune"></a>Configurare i criteri di aggiornamento per iOS in Intune

I criteri di aggiornamento software consentono di forzare l'installazione automatica dell'aggiornamento del sistema operativo più recente disponibile nei dispositivi iOS con supervisione. Questa funzionalità è disponibile solo per i dispositivi con supervisione. Quando si configurano criteri, è possibile aggiungere i giorni e gli orari in cui si vuole che i dispositivi non installino aggiornamenti. 

Il dispositivo si collega a Intune ogni 8 ore. Se è disponibile un aggiornamento (al di fuori dell'orario sottoposto a restrizioni), il dispositivo scarica e installa l'aggiornamento più recente del sistema operativo. Non è necessario alcun intervento dell'utente per aggiornare il dispositivo. I criteri non impediscono a un utente di aggiornare manualmente il sistema operativo.

Questa funzionalità supporta i dispositivi che eseguono iOS 10.3 e versioni successive. L'impostazione del ritardo è disponibile in iOS 11.3 e versioni successive.

## <a name="configure-the-policy"></a>Configurare i criteri
1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Aggiornamenti software** > **Criteri di aggiornamento per iOS** > **Crea**.
4. Immettere un nome e una descrizione per i criteri.
5. Selezionare **Impostazioni**. 

    Specificare nel dettaglio quando non viene imposta l'installazione degli aggiornamenti più recenti nei dispositivi iOS. Queste impostazioni creano un intervallo di tempo limitato. È possibile configurare i **giorni** della settimana, il **fuso orario**, l'**ora di inizio**, l'**ora di fine** e specificare se si vuole **ritardare la visibilità dell'aggiornamento software (in giorni)** per immettere gli utenti. È possibile selezionare un intervallo di ritardo degli aggiornamenti software da 1 a 90 giorni. Quando l'intervallo di ritardo scade, gli utenti ricevono una notifica per l'aggiornamento alla versione del sistema operativo meno recente che era disponibile quando è stato attivato il ritardo. Per rifiutare esplicitamente l'impostazione di un ritardo degli aggiornamenti software, immettere 0. Queste impostazioni degli aggiornamenti verranno applicate solo ai dispositivi iOS con supervisione.
  
    Se ad esempio iOS 12.a è disponibile il **1 gennaio** e **Delay OS Updates** (Ritarda aggiornamenti sistema operativo) è impostata su **5 days** (5 giorni), tale versione non appare come aggiornamento disponibile in nessun dispositivo per utenti finali assegnato al profilo. Al **sesto giorno** dopo il rilascio, l'aggiornamento appare come disponibile e tutti gli utenti finali possono avviare l'aggiornamento.


6. Selezionare **OK** per salvare le modifiche. Selezionare **Crea** per creare i criteri.

I criteri vengono creati e visualizzati nell'elenco dei criteri. Il software MDM di Apple non consente di imporre a un dispositivo di installare gli aggiornamenti entro un'ora o data determinata. 

## <a name="change-the-restricted-times-for-the-policy"></a>Modificare gli intervalli di tempo dotati di restrizioni per il criterio

1. In **Aggiornamenti software** selezionare **Criteri di aggiornamento per iOS**.
2. Scegliere dei criteri esistenti > **Proprietà**.
3. Aggiornare il periodo con limitazioni:
    
    1. Scegliere i giorni della settimana
    2. Scegliere il fuso orario nel quale verranno applicati i criteri
    3. Immettere l'ora di inizio e fine della disattivazione

    > [!NOTE]
    > Se sia **Ora di inizio** sia **Ora di fine** sono impostate sulle 12:00, il controllo ora di manutenzione è disattivato.

## <a name="assign-the-policy-to-users"></a>Assegnare i criteri agli utenti

I criteri esistenti vengono assegnati a gruppi, utenti o dispositivi. Dopo l'assegnazione, i criteri vengono applicati.

1. In **Aggiornamenti software** selezionare **Criteri di aggiornamento per iOS**.
2. Scegliere dei criteri esistenti > **Assegnazioni**. 
3. Selezionare gruppi, utenti o dispositivi Azure Active Directory da includere o escludere dai criteri.
4. Scegliere **Salva** per distribuire i criteri agli utenti.

I dispositivi usati dagli utenti a cui sono destinati i criteri vengono valutati per la conformità degli aggiornamenti. Questo criterio supporta anche i dispositivi senza utente.

## <a name="monitor-device-installation-failures"></a>Monitorare gli errori di installazione nei dispositivi
<!-- 1352223 -->
**Aggiornamenti software** > **Errori di installazione per dispositivi iOS** include un elenco di dispositivi iOS con supervisione che sono stati oggetto di criteri di aggiornamento e hanno provato a eseguire l'aggiornamento, ma nei quali l'operazione non è riuscita. Per ogni dispositivo, è possibile visualizzare il motivo per cui l'aggiornamento automatico non è riuscito. I dispositivi integri e aggiornati non vengono visualizzati nell'elenco. Un dispositivo è aggiornato se include l'ultimo aggiornamento supportato dal dispositivo stesso.

