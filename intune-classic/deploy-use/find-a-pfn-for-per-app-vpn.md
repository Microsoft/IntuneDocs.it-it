---
title: Trovare un nome di famiglia di pacchetti (PFN) per una rete VPN per app
description: Trovare un nome della famiglia di pacchetti per configurare una VPN per app.
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 74643d1d-4fd9-4cff-ac79-1a42281d2f76
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tycast
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f4b5d71e46fbc78ebadf52e96bb75eedecc291ee
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn-configuration"></a>Trovare un nome della famiglia di pacchetti (PFN) per la configurazione VPN per app

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È possibile trovare un PFN per configurare una VPN per app in due modi diversi.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Trovare un PFN di un'app installata in un computer Windows 10

Se l'app in uso è già installata in un computer Windows 10, è possibile usare il cmdlet di PowerShell [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) per ottenere il PFN.

la sintassi di Get-AppxPackage è:

` Parameter Set: __AllParameterSets`
` Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]`

> [!NOTE]
Può essere necessario eseguire PowerShell come amministratore per recuperare il PFN.

Ad esempio, per ottenere informazioni su tutte le app universali installate nel computer, usare `Get-AppxPackage`.

Per ottenere informazioni su un'app di cui si conosce il nome o parte del nome, usare `Get-AppxPackage *<app_name>`. Si noti l'uso del carattere jolly, utile se non si conosce il nome completo dell'app. Ad esempio, per ottenere informazioni per OneNote, usare `Get-AppxPackage *OneNote`.


Di seguito sono visualizzate le informazioni recuperate per OneNote:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>Trovare un PFN se l'app non è installata in un computer

1.  Accedere a https://www.microsoft.com/store/apps.
2.  Immettere il nome dell'app nella barra di ricerca. Nell'esempio, cercare OneNote.
3.  Scegliere il collegamento all'app. Si noti che l'URL include una serie di lettere nella parte finale. Nell'esempio, l'URL è simile al seguente: `https://www.microsoft.com/store/apps/onenote/9wzdncrfhvjl`.
4.  Incollare l'URL `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata` in una scheda differente. Sostituire `<app id>` con l'ID app ottenuto da https://www.microsoft.com/store/apps, ovvero la serie di lettere presente nella parte finale dell'URL del passaggio 3. Nell'esempio relativo a OneNote, incollare: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

Le informazioni desiderate vengono visualizzate in Microsoft Edge. In Internet Explorer scegliere **Apri** per visualizzare le informazioni. Il valore PFN è indicato nella prima riga. Di seguito sono riportati i risultati dell'esempio:


`{`
`  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",`
`  "packageIdentityName": "Microsoft.Office.OneNote",`
`  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",`
`  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"`
`}`
