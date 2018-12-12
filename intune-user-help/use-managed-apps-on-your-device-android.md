---
title: Usare le app gestite nel dispositivo Android | Documentazione Microsoft
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ed10a62c-b026-4ad3-ac41-641933522df2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 60df25542e69422e15a2a57473a3fbfa2cc413a5
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959503"
---
# <a name="use-managed-apps-on-your-android-device"></a>Usare le app gestite nel dispositivo Android
Le app gestite sono configurate per soddisfare i requisiti di sicurezza dell'organizzazione e proteggere i dati aziendali e dell'istituto di istruzione. Queste app vengono rese disponibili all'utente nel dispositivo per essere installate o usate automaticamente. 

Prima che l'utente riceva e installi un'app gestita, l'organizzazione ne configura le autorizzazioni. Queste possono limitare le funzionalità dell'app o le interazioni dell'utente per proteggere i dati delle app dalla condivisione o visualizzazione da parte di utenti non autorizzati. Ad esempio, un'organizzazione può impedire l'uso della funzione di copia e incolla nell'app. Oppure impedire all'utente di salvare i dati nello spazio di archiviazione locale del dispositivo.

Per ottimizzare la protezione dei dati, l'organizzazione può configurare diverse app gestite che interagiscono tra loro. Ad esempio:
1. L'utente si connette alla rete dell'organizzazione in un'app Managed Browser, ad esempio Microsoft Edge.
2. Fa clic su un collegamento per aprire il file di presentazione del peer.
3. Un'app gestita appropriata, ad esempio Microsoft PowerPoint, apre il file.

Le organizzazioni possono richiedere l'uso di un'app gestita per eseguire un'operazione, ad esempio aprire un file di lavoro o accedere a un collegamento Web. Se l'utente non ha l'app, può non essere in grado di continuare l'operazione. Alcune app gestite vengono rese disponibili per l'installazione, ma non sono obbligatorie.

## <a name="how-do-i-know-im-using-a-managed-app"></a>Come si capisce che si sta usando un'app gestita?
Quando si accede per la prima volta a dati aziendali o dell'istituto di istruzione in un'app gestita, si riceve un messaggio simile a quello dello screenshot riportato di seguito. Il messaggio chiede di riavviare l'app per continuare.

![Screenshot della finestra di messaggio visualizzato quando un utente apre un'app gestita in un dispositivo. Il messaggio dice: "L'organizzazione non protegge i propri dati in questa app. Per continuare è necessario riavviare l'app" ed è seguito dal pulsante OK.](./media/managed-apps-message.png)

## <a name="commonly-managed-apps"></a>App gestite comuni  
Di seguito sono riportati esempi di app gestite normalmente obbligatorie o disponibili in aziende e istituti di istruzione:

-   Microsoft Edge

-   Microsoft Outlook

-   Microsoft Word, Excel e PowerPoint

## <a name="how-do-i-get-managed-apps"></a>Come si ottengono le app gestite?
In primo luogo, è necessario installare il Portale aziendale e, se richiesta, ottenere la gestione del dispositivo. Successivamente, esistono tre modi per ottenere le app gestite.
* L'organizzazione installa automaticamente le app nel dispositivo al momento della registrazione. Per altre informazioni sulla registrazione, vedere [Registrare il dispositivo in Intune](enroll-your-device-in-Intune-android.md).
* L'organizzazione rende disponibili le app gestite all'utente nel Portale aziendale. Passare all'app o al sito Web Portale aziendale per cercare, visualizzare e installare queste app. 
* Installare un'app da Google Play Store e quindi accedere all'app con il proprio account aziendale o dell'istituto di istruzione.  

## <a name="what-can-my-company-support-manage-in-an-app"></a>Che cosa può gestire il supporto tecnico dell'azienda in un'app?
L'elenco seguente descrive le impostazioni che il supporto tecnico dell'azienda può gestire all'interno di un'app. Queste impostazioni influenzano il modo in cui l'utente apre, visualizza e usa i dati aziendali o dell'istituto di istruzione nel proprio dispositivo:

* Accesso a specifici siti Web  

* Accesso ai siti Web interni dell'azienda usando Microsoft Edge e il proxy di Azure Active Directory  

* Versione minima dell'app, versione del sistema operativo

* Possibilità di condividere e trasferire dati tra app  

* Come e dove si salvano i file  

* Funzionalità copia e incolla  

* Requisiti di accesso PIN  

* Modalità di accesso, con le credenziali aziendali  

* Possibilità di eseguire il backup dei dati nel cloud  

* Possibilità di acquisire screenshot  

* Requisiti di crittografia dati  

Per altre informazioni sulle applicazioni gestite nel dispositivo, contattare il supporto tecnico dell'azienda. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
