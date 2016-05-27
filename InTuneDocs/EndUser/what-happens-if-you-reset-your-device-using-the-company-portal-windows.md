---
# required metadata

title: Cosa succede se si reimposta il dispositivo personale con il Portale aziendale? | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1ee6e275-d1ec-4da3-bbef-d5da2c61a02a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Cosa succede se si reimposta il dispositivo personale con il Portale aziendale?

Quando si usa il Portale aziendale o il sito Web del Portale aziendale per reimpostare il dispositivo Windows, alcune app e impostazioni nel dispositivo potrebbero essere eliminate, inclusi alcuni dati personali. Le conseguenze nei singoli dispositivi dipendono dal tipo di dispositivo e da come viene usato, come descritto nella tabella seguente. Per istruzioni su come reimpostare il dispositivo perso o rubato, vedere [Ripristinare (cancellare) un dispositivo smarrito o rubato](reset-erase-your-lost-or-stolen-device-windows.md).

|Configurazione e gestione del dispositivo|Tipo di dispositivo|
|---------------------------------------|---------------|
|L'amministratore IT gestisce il dispositivo mobile|**Windows 10, Windows Phone 8.1 e Windows Phone 8**</br>Il dispositivo non sarà più visualizzato nel portale aziendale e il portale aziendale proverà a ripristinare le impostazioni predefinite del dispositivo. I dati, le app e le impostazioni personali verranno rimossi.<br /><br />**Windows RT**<br />Non è possibile reimpostare un dispositivo Windows RT a meno che non sia usato solo per la posta elettronica.|
|Il dispositivo può accedere solo alla posta elettronica aziendale|**Windows Phone 8.1 e Windows Phone 8**<br />Il dispositivo non sarà più visualizzato nel portale aziendale e verranno eliminati l'account di posta elettronica aziendale e i messaggi di posta elettronica non salvati.<br /><br />**Windows RT**<br />Il dispositivo non sarà più visualizzato nel portale aziendale e verranno eliminati l'account di posta elettronica aziendale e i messaggi di posta elettronica non salvati.<br /><br />**Computer Windows 7 o Windows Vista**<br />Non è possibile reimpostare un computer che esegue Windows 7 o versioni precedenti che viene usato solo per la posta elettronica.<br /><br />**Computer Windows 8.1 e Windows 8**<br />Il dispositivo non sarà più visualizzato nel portale aziendale e verranno eliminati l'account di posta elettronica aziendale e i messaggi di posta elettronica non salvati.|
|PC e portatili|**Computer Windows 8.1 e Windows 8**<br />Non è possibile reimpostare un computer che esegue Windows 8 o Windows 8.1 a meno che non sia usato solo per la posta elettronica.<br /><br />**Computer Windows 7 o Windows Vista**<br />Non è possibile reimpostare un computer che esegue Windows 7 o versioni precedenti.|

### Vedere anche
[Uso del dispositivo Windows con Intune](using-your-windows-device-with-intune.md)

<!--HONumber=May16_HO1-->


