---
title: Test e convalida di Intune | Documentazione Microsoft
description: Questo articolo illustra tutti i dettagli che devono essere presi in considerazione durante il test e la convalida di una soluzione Intune in configurazione solo cloud nel proprio ambiente.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f3ba0c5a58132c9749fb8ad7e134d1323952a3de
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="intune-testing-and-validation"></a>Test e convalida di Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

La fase di test deve avvenire durante e dopo la fase di implementazione. Sarà necessario disporre di account, gruppi e dispositivi di test per il testing di tutti gli scenari IT (amministrazione) e per gli utenti finali (caso d'uso) identificati in precedenza.

È consigliabile incorporare il personale help desk o di supporto IT nella fase di test, in modo che venga creata la documentazione di supporto e il personale help desk o di supporto IT acquisisca familiarità con il supporto del prodotto. Se un componente o uno scenario non funziona in base ai casi d'uso, assicurarsi di documentare le modifiche necessarie e includere il motivo per cui è stata apportata una modifica.

## <a name="before-you-begin"></a>Prima di iniziare

È consigliabile documentare quanto segue:

-   **Criteri di test:** identifica i benchmark rispetto ai quali eseguire le misurazioni.

-   **Componenti di progettazione:** devono essere presenti in almeno un criterio di test.

Se un componente di progettazione non è presente in almeno un criterio di test allineato a un requisito o uno scenario, valutare se il componente di progettazione è necessario o meno. Assicurarsi inoltre di avere i seguenti elementi:

-   **Account:** gli account usati durante i test devono essere account di test che dispongono delle licenze per EMS e Office 365 per testare tutti gli scenari dei casi d'uso.

-   **Dispositivi:** i dispositivi usati in questa fase devono essere dispositivi di test, di cui sia possibile eseguire la cancellazione dei dati o il ripristino delle impostazioni di fabbrica.

-   **Componenti di integrazione:** tutti i componenti di integrazione (connettore di certificati, Intune Service to Service Connector per Exchange ospitato e Intune On-premises Exchange Connector) devono essere installati e configurati, se necessario.

Possono essere necessarie modifiche di progettazione per far fronte a difficoltà impreviste. Inoltre, tutte le modifiche di progettazione devono essere completamente documentate con il motivo per ogni modifica. Ecco un esempio per illustrare una possibile modifica:

-   Si potrebbe rilevare che i requisiti del Servizio Registrazione dispositivi di rete (NDES) non sono soddisfatti e che è possibile configurare i profili VPN e Wi-Fi con una CA radice che soddisfa gli stessi requisiti senza un'implementazione di NDES.

Durante il processo di test e convalida si potrebbero riscontrare difficoltà o problemi che richiedono indicazioni tecniche o procedure specializzate di risoluzione dei problemi. È consigliabile richiedere assistenza tramite i canali di supporto Microsoft.

-   [Informazioni su come ottenere supporto per Intune](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Suggerimenti generali per la risoluzione dei problemi di Microsoft Intune](/intune-classic/troubleshoot/general-troubleshooting-tips-for-microsoft-intune).

-   [Informazioni su come ottenere supporto per Microsoft Intune.]/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Come contattare il supporto telefonico assistito per Microsoft Intune](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>Test di convalida funzionale

La convalida funzionale comprende il test di ogni componente e configurazione per determinare che funzioni correttamente. Un esempio di test di convalida è riportato nella tabella seguente.

![Tabella 1 sezione 9](../media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Test di convalida dei casi d'uso

Il test di convalida dei casi d'uso deve essere eseguito per verificare che gli scenari siano completi e funzionali. Esistono due tipi di scenari dei casi d'uso: amministratore IT e utente finale.

### <a name="it-admin"></a>Amministratore IT

Il test di convalida per l'amministratore IT deve essere eseguito per convalidare il corretto funzionamento di un'azione amministrativa eseguita su un dispositivo o un utente. Di seguito è riportato un esempio di uno scenario di convalida end-to-end per l'amministratore IT.

![Tabella 2 sezione 9](../media/section-9-image-2-table.PNG)

### <a name="end-user"></a>Utente finale

Il test di convalida per l'utente finale deve essere eseguito per convalidare che l'esperienza utente finale sia come previsto e venga presentata correttamente in tutte le comunicazioni per gli utenti. È importante convalidare che l'esperienza utente finale sia corretta, perché un errore di convalida può causare una riduzione dei tassi di adozione e un aumento del volume di chiamate all'help desk.

![Tabella 3 sezione 9](../media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>Passaggi successivi

Dopo avere testato e convalidato gli scenari funzionali e per i casi d'uso di Intune, si è pronti per l'implementazione di Intune in produzione. Per altre informazioni, vedere [Risorse aggiuntive](additional-resources.md).

