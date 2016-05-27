---
# required metadata

title: Annullare la registrazione del dispositivo da Intune se sono state rifiutate le Condizioni per l'utilizzo | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Annullare la registrazione del dispositivo da Intune se sono state rifiutate le Condizioni per l'utilizzo

Il modo migliore per annullare la registrazione del dispositivo Android è accettare le Condizioni per l'utilizzo, accedere all'app Portale aziendale e quindi usare [queste istruzioni](unenroll-your-device-from-intune-android.md) per annullare la registrazione. Tuttavia, se le Condizioni per l'utilizzo sono state rifiutate durante il tentativo di accesso all'app Portale aziendale, non saranno consentiti altri tentativi di accesso all'app Portale aziendale e, pertanto, sarà necessario usare queste istruzioni "alternative" per annullare la registrazione del dispositivo.

Quando si disinstalla l'app Portale aziendale, viene anche annullata la registrazione del dispositivo da Intune, quindi il dispositivo non potrà più accedere alle risorse aziendali.  Per altre informazioni su cosa accade quando viene annullata la registrazione, vedere [Cosa succede se si annulla la registrazione del dispositivo da Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Prima di disinstallare l'app Portale aziendale, è necessario passare all'impostazione **Device Administrators** e disattivare **Portale aziendale**. La procedura può variare leggermente a seconda del dispositivo Android in uso.

Per annullare la registrazione del dispositivo da Intune e disinstallare l'app Portale aziendale:

1.  Passare a **Impostazioni** &gt; **Sicurezza &amp; Blocco schermo** &gt; **Amministratori dispositivo**.

    Al termine di questo passaggio la registrazione del dispositivo verrà immediatamente annullata.

2.  Deselezionare la casella di controllo accanto a **Portale aziendale** o disattivare il portale..

    Ora è possibile disinstallare l'app Portale aziendale.


### Vedere anche
[Uso del dispositivo Android con Intune](using-your-android-device-with-intune.md)

<!--HONumber=May16_HO1-->


