---
title: Impostazioni Istruzione di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni Istruzione per i dispositivi Windows 10. Usare queste impostazioni in un profilo di configurazione del dispositivo con l'app Test ed esami, scegliere la modalità di accesso di utenti e studenti, monitorare lo schermo durante il test e altro ancora in Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae26d35a50ffd2b5b40f262ddebeab8d53d87223
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846690"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configurare l'app Test ed esami nei dispositivi Windows 10 tramite Intune

Questo articolo illustra tutte le impostazioni relative alla formazione di Microsoft Intune configurabili per i dispositivi che eseguono Windows 10 e versioni successive. Usando l'app, gli studenti possono accedere a un dispositivo ed eseguire un test.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo e quindi assegnate o distribuite ai dispositivi con Microsoft Intune.

L'[app Test ed esami in Intune](education-settings-configure.md) offre altre informazioni su questa funzionalità.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Impostazioni di Test ed esami

- **Tipo di account**: scegliere la modalità di accesso degli utenti al test. Le opzioni disponibili sono:
  - Account di Azure AD
  - Account di dominio
  - Account locale
- **Nome utente dell'account**: immettere il nome utente dell'account usato con l'app Test ed esami. È possibile immettere gli account nel formato seguente:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **URL della valutazione**: immettere l'URL del test che dovrà essere eseguito dagli utenti. Per altre informazioni su come ottenere l'URL, vedere la [documentazione relativa a Test ed esami](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Monitoraggio dello schermo**: Scegliere **Consenti** per monitorare l'attività dello schermo mentre gli utenti eseguono il test. L'opzione **Non configurato** impedisce il monitoraggio dello schermo durante il test.
- **Suggerimento di testo**: scegliere **Consenti** per consentire a chi esegue il test di visualizzare i suggerimenti di testo. **Non configurato**: blocca i suggerimenti di testo mentre gli utenti eseguono il test.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma potrebbe non essere ancora operativo. Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
