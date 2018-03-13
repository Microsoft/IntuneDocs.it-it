---
title: Informazioni sull'esperienza di registrazione dei dispositivi iOS
titlesuffix: Microsoft Intune
description: Informazioni sull'esperienza di registrazione tramite la registrazione completa di un dispositivo iOS.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18a3225ef81d7f13b8656326540e30cf5ee07f1e
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="understand-the-users-experience-enrolling-an-ios-device"></a>Informazioni sull'esperienza utente per la registrazione di un dispositivo iOS

Microsoft Intune consente di offrire agli utenti la possibilità di usare i dispositivi mobili, mantenendo protetti i dati aziendali. Poiché gli utenti finali interagiscono con Intune nei dispositivi anziché nella console di amministrazione, si vorrà garantire un'esperienza di registrazione semplice. Per questa ragione è possibile combinare criteri di conformità ben definiti e la propria esperienza per dimostrare empatia nei confronti degli utenti. Ciò è particolarmente importante poiché gli utenti sapranno esattamente quali informazioni sono visibili all'amministratore:

| Elementi non visibili all'IT | Elementi visibili all'IT |
|---|---|
| Cronologia delle chiamate e delle esplorazioni Web | Modello |
| Percorso | Numero di serie |
| Posta elettronica personale | Versione del sistema operativo |
| Messaggi di testo | Nomi di app |
| Contatti | Proprietario |
| Password per gli account personali | Nome dispositivo |
| Eventi del calendario | Produttore (per i dispositivi non prodotti da Apple) |
| Immagini, incluse quelle nell'app Foto o nel rullino della fotocamera | Numero di telefono (il numero completo per i dispositivi di lavoro e solo le ultime quattro cifre per i dispositivi personali) |

## <a name="how-do-i-enroll-a-device"></a>Come si registra un dispositivo?

La registrazione di un dispositivo è la prima esperienza che faranno molti utenti finali quando accedono alle risorse aziendali. [Comprendere il processo di registrazione](end-user-educate.md) può consentire di trasformare un'esperienza complessa in un'esperienza semplice.

1. Aprire l'**App Store** e cercare **Portale aziendale di Intune**.
2. Scaricare l'app **Portale aziendale di Microsoft Intune**.
3. Aprire l'app **Portale aziendale**, immettere l'indirizzo di posta elettronica e la password dell'utente test, quindi toccare **Accedi**.
4. Sostituire la password temporanea con una nuova.
5. Nella pagina **Configurazione dell'accesso aziendale** toccare **Registrazione del dispositivo**.
6. Nella pagina **Vantaggi della registrazione del dispositivo** leggere le informazioni sulle operazioni che possono essere eseguite durante la registrazione del dispositivo e quindi toccare **Continua**.
7. Rivedere l'elenco degli accessi concessi a un utente con la registrazione, quindi toccare **Continua**.
8. Rivedere i dati che gli amministratori IT possono e non possono visualizzare in un dispositivo, quindi toccare **Continua**.
9. Nella pagina **Operazioni successive** leggere le informazioni sulle operazioni che vengono eseguite durante la registrazione, quindi toccare **Registra**.
10. Nella pagina **Installa profilo** toccare **Installa**, quindi immettere il passcode del dispositivo, se richiesto.
11. Toccare **Installa**.
12. Toccare di nuovo **Installa** per indicare che l'avviso è stato letto.
13. Nella finestra popup **Avviso** toccare **Considera attendibile**.
14. Quando la schermata indica che il profilo è stato installato, toccare **Fine**.
15. Nella schermata viene visualizzato il messaggio "Registrazione dispositivo" e quindi viene indicato che l'operazione è stata eseguita correttamente. Viene visualizzata una finestra popup in cui viene chiesto di aprire la pagina nel portale aziendale. Toccare **Apri**.
16. Viene nuovamente visualizzata la schermata **Configurazione dell'accesso aziendale**. Se non sono stati specificati criteri di test, il dispositivo dovrebbe essere conforme. Se sono stati specificati criteri di test, quando si tocca **Conformità del dispositivo** vengono elencate le operazioni da eseguire per rendere il dispositivo sicuro.

## <a name="next-steps"></a>Passaggi successivi

[Introduzione all'aggiunta di app](get-started-apps.md): illustra come trovare le app e aggiungerle ai dispositivi per consentire ai dipendenti di svolgere il proprio lavoro.

## <a name="learn-more"></a>Altre informazioni

* [Opzioni di registrazione per Intune](enrollment-options.md)
* [Abilitare un dispositivo Bring Your Own Device (BYOD) con Intune](byod-enable.md)
* [Formazione degli utenti finali su registrazione e gestione dei dispositivi](end-user-educate.md)
