---
title: Impostazioni dei criteri di configurazione di Windows Team| Microsoft Intune
description: Usare i **criteri di configurazione generale di Windows 10 Team** di Microsoft Intune per configurare le impostazioni per i dispositivi Windows 10 Team registrati, ad esempio Microsoft Surface Hub.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38194ef3-e26e-4682-958d-14b395fccba1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 75866e1854211ad42084f3ededaf1e3c0f6d5119


---

# Impostazioni dei criteri di configurazione di Windows Team in Microsoft Intune
Usare i **criteri di configurazione generale di Windows 10 Team** di Microsoft Intune per configurare le impostazioni per i dispositivi Windows 10 Team registrati, ad esempio Microsoft Surface Hub.

|Nome impostazione|Dettagli|
|----------------|-----------|
|**Consenti riattivazione automatica dello schermo se qualcuno è presente nella stanza**|Consente di riattivare automaticamente il dispositivo quando il sensore rileva la presenza di qualcuno nella stanza.|
|**Richiedi PIN per proiezione wireless**|Specifica se immettere un PIN prima di usare le funzionalità di proiezione wireless del dispositivo.|
|**Configura la finestra di manutenzione per il dispositivo**|Configura la finestra durante la quale cui è possibile eseguire gli aggiornamenti del dispositivo. È possibile configurare l'ora di inizio della finestra e la durata (tra 1 e 5 ore).|
|**Abilita Azure Operational Insights**|Azure Operational Insights, parte di Microsoft Operations Management Suite, raccoglie, archivia e analizza i dati dei file di log dai dispositivi Windows 10 Team.<br /><br />Per connettersi ad Azure Operational Insights, è necessario specificare un valore per **ID area di lavoro** e **Chiave dell'area di lavoro**.|
|**Abilita proiezione wireless Miracast**|Abilitare questa opzione se si vuole consentire al dispositivo Windows 10 Team di usare i dispositivi abilitati per Miracast per la proiezione.<br /><br />Se si abilita questa opzione, selezionare in **Scegli un canale Miracast** il canale Miracast usato per la proiezione del contenuto.|
|**Scegli le informazioni sulla riunione visualizzate nella schermata iniziale**|Se si abilita questa opzione, è possibile scegliere le informazioni che verranno visualizzate nel riquadro **Riunioni** riquadro della schermata **iniziale**. È possibile scegliere le opzioni seguenti:<br /><br />-   **Mostra solo organizzatore e ora**<br />-   **Mostra organizzatore, ora e oggetto (l'oggetto è nascosto per le riunioni private)**|
|**URL dell'immagine di sfondo per la schermata di blocco**|Abilitare questa impostazione per visualizzare uno sfondo personalizzato nella schermata **iniziale** dei dispositivi Windows 10 Team dall'URL specificato.<br /><br />L'immagine deve essere nel formato PNG e l'URL deve iniziare con **https://**.|


### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Oct16_HO4-->


