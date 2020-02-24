---
title: Criteri di configurazione per le app gestite senza registrazione dei dispositivi
titleSuffix: Microsoft Intune
description: Informazioni su come configurare i criteri per le app gestite senza registrazione dei dispositivi.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4301afca471d0aa56fa1a0826ad7f88bcdf23de2
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414862"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

È possibile usare i criteri di configurazione delle app con le app gestite che supportano Intune App SDK anche su dispositivi non registrati. 

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Scegliere **App** > **Criteri di configurazione dell'app** > **Aggiungi** > **App gestite**.
3. Nella pagina **Informazioni di base** impostare i dettagli seguenti:
    - **Nome**: Il nome del profilo che verrà visualizzato nel portale di Azure.
    - **Descrizione**: La descrizione del profilo che verrà visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**: sono selezionate le app gestite.
4. Scegliere **Selezionare app pubbliche** o **Selezionare app personalizzate** per scegliere l'app che si intende configurare. Selezionare l'app dall'elenco di app già approvate e sincronizzate con Intune.
5. Fare clic su **Avanti** per visualizzare la pagina **Impostazioni**.
6. Per ogni impostazione di configurazione supportata dall'app digitare **Nome** e **Valore**. 

   Le app abilitate per Intune App SDK supportano le configurazioni in coppie chiave/valore. Per altre informazioni sulle configurazioni chiave-valore supportate, vedere la documentazione delle singole app. Si noti che è possibile usare token che verranno popolati in modo dinamico con i dati generati dall'applicazione. Per altre informazioni, vedere [Valori di configurazione per l'uso dei token](~/apps/app-configuration-policies-managed-app.md#configuration-values-for-using-tokens). Per informazioni sulle impostazioni dei criteri di configurazione dell'app Outlook per iOS/iPadOS, vedere [Gestione della configurazione dell'app Outlook per iOS/iPadOS con Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

    Per eliminare una configurazione scegliere i puntini di sospensione ( **...** ) e selezionare **Elimina**.  

7. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.
8. Fare clic su **Selezionare i gruppi da includere**.
9. Selezionare un gruppo nel riquadro **Selezionare i gruppi da includere** e fare clic su **Seleziona**.
10. Fare clic su **Selezionare i gruppi da escludere** per visualizzare il riquadro correlato.
11. Scegliere i gruppi da escludere e quindi fare clic su **Seleziona**.

    >[!NOTE]
    >Quando si aggiunge un gruppo, se sono già stati inclusi altri gruppi per un tipo di assegnazione specifico, tale gruppo risulterà preselezionato e non potrà essere modificato per gli altri tipi di assegnazione di inclusione. Di conseguenza, tale gruppo non potrà essere usato come gruppo escluso.

12. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**.
13. Fare clic su **Crea** per aggiungere i criteri di configurazione dell'app a Intune.

## <a name="configuration-values-for-using-tokens"></a>Valori di configurazione per l'uso dei token

Intune può generare token e inviarli all'app gestita. Se ad esempio la configurazione dell'app è in grado di usare un'impostazione di posta elettronica, è possibile aggiungere un indirizzo di posta elettronica dinamico usando un token. Digitare il nome previsto dall'app nel campo **Nome** e quindi digitare `\{\{mail\}\}` nel campo **Valore**.

Intune supporta i tipi di token seguenti nelle impostazioni di configurazione. Altre coppie chiave/valore personalizzate non sono supportate.

- \{\{userprincipalname\}\}, ad esempio John@contoso.com
- \{\{mail\}\}, ad esempio John@contoso.com
- \{\{partialupn\}\}, ad esempio John
- \{\{accountid\}\}, ad esempio fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\}, ad esempio 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\}, ad esempio John Doe
- \{\{PrimarySMTPAddress\}\}, ad esempio testuser@ad.domain.com

> [!Note]  
> I caratteri \{\{ e \}\} vengono usati solo dai tipi di token e non devono essere usati per altri scopi.

## <a name="next-steps"></a>Passaggi successivi

Procedere ad [assegnare](apps-deploy.md) e [monitorare](apps-monitor.md) normalmente l'app.
