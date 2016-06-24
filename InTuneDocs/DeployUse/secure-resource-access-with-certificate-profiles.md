---
# required metadata

title: Abilitare l'accesso alle risorse aziendali usando i profili certificato con Microsoft Intune | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune
Quando si abilita l'accesso alle risorse aziendali tramite profili VPN, Wi-Fi o di posta elettronica, è possibile proteggere tale accesso con un certificato installato in ogni dispositivo utente. Ecco come funziona:

1. Assicurarsi che sia implementata l'infrastruttura di certificazione corretta, come descritto nell'articolo relativo alla [configurazione dell'infrastruttura di certificazione](configure-certificate-infrastructure.md)..

2. Installare innanzitutto un certificato radice (o un certificato CA intermedio) in ogni dispositivo in modo che il dispositivo riconosca la legittimità dell'autorità di certificazione. Questa operazione si esegue creando e distribuendo un **profilo certificato attendibile**. Quando si distribuisce questo profilo, i dispositivi da gestire con Intune richiederanno e riceveranno il certificato radice. È necessario creare un profilo separato per ogni piattaforma. Il **profilo certificato attendibile** è disponibile per le piattaforme:
 -  iOS 7.1 e versioni successive
 -  Mac OS X 10.9 e versioni successive
 -  Android 4.0 e versioni successive
 -  Windows 8.1 e versioni successive
 -  Windows Phone 8.1 e versioni successive

3. Fare in modo che ogni dispositivo richieda un certificato da usare per l'autenticazione dell'accesso a posta elettronica, VPN e Wi-Fi, come descritto nell'articolo relativo alla [configurazione dei profili certificato di Intune](configure-intune-certificate-profiles.md). È possibile creare e distribuire un **profilo certificato PKCS #12 (.PFX)** o un **profilo certificato SCEP** per i dispositivi su queste piattaforme:
 
-  Android 4.0 e versioni successive
-  iOS 7.1 e versioni successive
-  Windows 10 (per dispositivi desktop e mobili) e versioni successive 

Usare il **profilo certificato SCEP** per:
-   Mac OS X 10.9 e versioni successive
-   Windows Phone 8.1 e versioni successive

È necessario creare un profilo separato per ogni piattaforma. Quando si crea il profilo, questo viene associato al **profilo del certificato radice attendibile** già creato.

> [!NOTE]           
> -    Se non è presente un'autorità di certificazione globale (enterprise), è necessario crearla. 
>- Se, in base alle piattaforme dei dispositivi, si decide di usare il profilo Simplified Certificate Enrollment Protocol (SCEP), è necessario anche configurare un del servizio Registrazione dispositivi di rete (NDES).
>-  Se si prevede di usare i profili SCEP o PFX, è necessario scaricare e configurare Connettore di certificati di Microsoft Intune.
> La configurazione di tutti questi elementi è descritta nell'argomento relativo alla [configurazione dell'infrastruttura di certificazione](configure-certificate-infrastructure.md)..

### Passaggi successivi
- [Configurare l'infrastruttura di certificazione](configure-certificate-infrastructure.md)
- [Configurare i profili certificato di Intune](configure-intune-certificate-profiles.md)



<!--HONumber=May16_HO1-->


