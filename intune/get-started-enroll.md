---
title: Introduzione alla registrazione di dispositivi
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f52c9d44a91ed6547aadd712db42ea68cfd01dc
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="getting-started-enrolling-devices"></a>Introduzione alla registrazione di dispositivi

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune consente di offrire agli utenti la possibilità di usare i dispositivi mobili, mantenendo protetti i dati aziendali. Poiché gli utenti finali interagiscono con Intune nei dispositivi anziché nella console di amministrazione, si vorrà garantire un'esperienza di registrazione semplice. Per questa ragione è possibile combinare criteri di conformità ben definiti e la propria esperienza per dimostrare empatia nei confronti degli utenti. Ciò è particolarmente importante poiché gli utenti sapranno esattamente quali informazioni sono visibili all'amministratore:

## <a name="what-it-cannot-see"></a>Elementi non visibili all'IT
* Cronologia delle chiamate e delle esplorazioni Web
* Percorso
* Posta elettronica personale
* Messaggi di testo
* Contatti
* Password per gli account personali
* Eventi del calendario
* Immagini, incluse quelle nell'app Foto o nel rullino della fotocamera

## <a name="what-it-can-see"></a>Elementi visibili all'IT
* Modello
* Numero di serie
* Versione del sistema operativo
* Nomi di app
* Proprietario
* Nome dispositivo
* Produttore (per i dispositivi non prodotti da Apple)
* Numero di telefono (il numero completo per i dispositivi di lavoro e solo le ultime quattro cifre per i dispositivi personali)

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
