---
title: Proteggere i dispositivi con Microsoft Intune
description: Informazioni su alcuni dei metodi che consentono a Intune di proteggere i dispositivi da accessi non autorizzati e altre minacce.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c866f2a8eebdb2f6c07314b745f65c06e3469e4e
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="protect-devices-with-microsoft-intune"></a>Proteggere i dispositivi con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune offre un set completo di funzionalità per la protezione dei dispositivi gestiti e dei dati archiviati in tali dispositivi. Leggere questo argomento per comprendere le nozioni fondamentali di queste funzionalità e per informazioni aggiuntive.

## <a name="general-ways-to-protect-all-devices"></a>Metodi generali per proteggere tutti i dispositivi

### <a name="device-configuration"></a>Configurazione del dispositivo
I [criteri di configurazione](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) di Intune consentono di proteggere e configurare i dispositivi controllando una vasta gamma di funzionalità e impostazioni. Ad esempio:
- È possibile limitare l'uso delle funzionalità hardware del dispositivo, ad esempio la fotocamera o il Bluetooth.
- È possibile configurare app conformi e non conformi. Se viene installata un'app non conforme si riceverà un avviso (e in alcune piattaforme è possibile bloccare l'installazione).

### <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Reimpostare i passcode quando gli utenti vengono bloccati dai dispositivi
Poiché il primo passaggio nella protezione dei dati aziendali nei dispositivi mobili prevede l'uso di un passcode per usare il dispositivo, a volte è necessario [reimpostare un passcode](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) o aiutare un utente a farlo rimuovendo il passcode o impostando in remoto un passcode temporaneo. È anche possibile [bloccare un dispositivo in remoto](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) se viene smarrito o rubato.

### <a name="retire-devices-and-remove-data"></a>Ritirare i dispositivi e rimuovere i dati
Quando un dispositivo deve essere [rimosso dalla gestione Intune](retire-devices-from-microsoft-intune-management.md) (ad esempio, un utente lascia l'azienda o il dispositivo viene smarrito o rubato), è probabile che sia necessario rimuovere i dati dal dispositivo. Intune offre un'ampia gamma di metodi per garantire la sicurezza dei dati aziendali.

### <a name="require-devices-to-be-compliant"></a>Richiedere la conformità dei dispositivi
Intune offre [criteri di conformità dei dispositivi](introduction-to-device-compliance-policies-in-microsoft-intune.md) che consentono di valutare (e in alcuni casi correggere) i dispositivi non conformi alle regole specificate. Ad esempio, è possibile segnalare dispositivi iOS jailbroken, se i dispositivi sono crittografati o se i dispositivi Windows 10 vengono segnalati come integri dal servizio di attestazione dell'integrità.

### <a name="protect-apps-and-the-data-they-use"></a>Proteggere le app e i dati che usano
Windows Intune offre una gamma di funzionalità che consentono di proteggere le app e i relativi dati. Ad esempio, i criteri di gestione delle applicazioni mobili consentono di impedire che i dati vengano sottoposti a backup da un'app protetta, di limitare le operazioni di copia e incolla in altre app, di richiedere un PIN per accedere a un'app e altro ancora. Per altre informazioni dettagliate sulla protezione delle app, vedere [Proteggere app e dati con Microsoft Intune](protect-apps-and-data-with-microsoft-intune.md).

### <a name="add-an-additional-layer-of-protection-to-devices"></a>Aggiungere un ulteriore livello di protezione ai dispositivi
[Multi-Factor Authentication (MFA)](multi-factor-authentication-azure-active-directory.md) costituisce un modo più sicuro per autenticare gli utenti di dispositivi in rete.  Con MFA, oltre a specificare nome utente e password, gli utenti devono confermare la propria identità con una telefonata o un SMS.

## <a name="further-capabilities-for-windows-devices"></a>Altre funzionalità per i dispositivi Windows

### <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Controllare le impostazioni di Windows Hello for Business nei dispositivi Windows
Con Intune è possibile eseguire l'integrazione con [Windows Hello for Business](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (precedentemente noto come Microsoft Passport), un metodo di accesso alternativo per Windows 10 e versioni successive che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale.

## <a name="further-capabilities-for-ios-devices"></a>Altre funzionalità per i dispositivi iOS

### <a name="bypass-activation-lock-on-ios-devices"></a>Eseguire il bypass del blocco attivazione su dispositivi iOS
Il blocco attivazione è una funzionalità che consente di proteggere i dispositivi degli utenti richiedendo l'ID Apple e la password prima di qualsiasi operazione di cancellazione o riattivazione del dispositivo. Tuttavia questo può causare problemi, ad esempio se l'utente lascia l'azienda senza rimuovere il blocco. [Il bypass del blocco attivazione iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) consente di rimuovere il blocco dai dispositivi iOS supervisionati e di riallocarli o di cancellarne il contenuto.



## <a name="protect-windows-pcs-managed-with-the-intune-client"></a>Proteggere i PC Windows gestiti con il client di Intune
Intune continua a supportare i criteri di sicurezza per i PC Windows non registrati ma gestiti con il software per client computer di Intune. Per scoprire come questi criteri aiutano a proteggere i PC Windows, vedere l'articolo [Usare i criteri per proteggere i PC Windows che eseguono il software client di Intune](policies-to-protect-windows-pcs-in-microsoft-intune.md).
