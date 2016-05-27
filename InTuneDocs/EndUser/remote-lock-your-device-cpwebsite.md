---
# required metadata

title: Bloccare in remoto un dispositivo dal sito Web del portale aziendale | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Bloccare in remoto un dispositivo dal sito Web del portale aziendale

Se il dispositivo è stato smarrito o rubato, è possibile bloccarlo tramite l'opzione Blocco remoto sul [sito Web del portale aziendale](http://portal.manage.microsoft.com). Blocco remoto funziona per i tipi di dispositivo seguenti:

Piattaforma  |Dettagli sul supporto  
---------|---------
Android | Supportato       
iOS | Supportato
Windows 10 Mobile | Supportato solo se per il telefono è impostato un passcode     
Windows 10 Desktop | Non supportato  
Windows Phone 8.1 | Supportato solo se per il telefono è impostato un passcode
Windows Phone 8.0 | Non supportato
PC (Windows 8.0 e versioni precedenti) | Non supportato       
PC (Windows 8.1) | Non supportato

</br>
Per usare Blocco remoto per bloccare il dispositivo:

1.  Nel [sito Web del portale aziendale](http://portal.manage.microsoft.com) toccare il nome del dispositivo da bloccare.

2.  Toccare **Blocco remoto**..

    Dopo aver toccato **Blocco remoto** viene visualizzato lo stato "Blocco remoto in sospeso".  Quando Blocco remoto ha esito positivo, lo stato passa a "Blocco remoto riuscito."

    Lo stato viene visualizzato in tre posizioni:

    * L'area delle notifiche del sito Web. 
    * La pagina dei dettagli del dispositivo.
    * Il riquadro contenente il nome del dispositivo nella sezione Dispositivi personali della pagina.

    Se viene visualizzata la notifica "Blocco remoto non riuscito", attendere qualche minuto e quindi tentare nuovamente di bloccare il dispositivo. Dopo aver toccato il pulsante per riprovare, lo stato diventa nuovamente "Blocco remoto in sospeso". 

    Se il tentativo ha esito negativo, contattare l'amministratore IT per ricevere assistenza. Se il dispositivo viene ritrovato e si vuole rimuovere il blocco dopo aver usato Blocco remoto, immettere il passcode.


### Vedere anche
[Uso del sito Web del portale aziendale](using-the-intune-company-portal-website.md)

<!--HONumber=May16_HO1-->


