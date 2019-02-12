---
title: Manca un certificato necessario per il dispositivo | Documentazione Microsoft
titlesuffix: Microsoft Intune
description: Il dispositivo non ha un certificato richiesto dal supporto tecnico dell'azienda.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc86a53dd790059297430fd6b08f1a699aafbc84
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850659"
---
# <a name="your-device-is-missing-a-required-certificate"></a>Manca un certificato necessario per il dispositivo

## <a name="whats-a-certificate"></a>Che cos'è un certificato?

La [crittografia](https://technet.microsoft.com/library/cc962030.aspx) è la scienza della protezione delle informazioni. La crittografia è sempre stata usata per passare messaggi codificati in modo da [garantire la riservatezza della comunicazione](https://technet.microsoft.com/library/cc962019.aspx). Nella sua forma più semplice, la crittografia sostituisce o traspone lettere per trasformare un messaggio codificato in un messaggio illeggibile, criptato o nascosto. Solo gli utenti con una chiave, o _certificato_, di decodifica possono convertire il messaggio codificato nel formato originale e leggibile. Il dispositivo Android usa i certificati con Intune per assicurarsi che le comunicazioni tra il dispositivo e le risorse dell'organizzazione, ad esempio posta elettronica e documenti, vengano mantenute sicure da un punto all'altro.

## <a name="fixing-certificate-issues"></a>Correzione dei problemi di certificato

Se il dispositivo Android non è registrato in Intune e non ha un determinato certificato richiesto dal supporto tecnico dell'azienda, non sarà possibile accedere all'app Portale aziendale dal dispositivo. Quando si tenta di accedere, verrà visualizzato il messaggio seguente:

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

Il primo passaggio da tentare consiste nel verificare se nel dispositivo [è presente un certificato generalmente preinstallato](your-device-is-missing-a-preinstalled-certificate-android.md).

Se il problema persiste, il supporto tecnico dell'azienda può [richiedere di installare un secondo certificato per maggiore sicurezza](your-device-is-missing-an-IT-required-certificate-android.md).

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
