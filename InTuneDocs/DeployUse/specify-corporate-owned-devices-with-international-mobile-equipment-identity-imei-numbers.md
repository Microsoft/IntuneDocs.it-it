---
title: Specificare i dispositivi aziendali con i numeri IMEI (International Mobile Equipment Identity)
ms.custom: na
ms.reviewer: na
ms.service: microsoft-intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
author: NathBarn
---
# Specificare i dispositivi aziendali con i numeri IMEI (International Mobile Equipment Identity)
Microsoft Intune consente agli amministratori di importare i numeri IMEI (International Mobile Equipment Identity) per le piattaforme per dispositivi mobili dotate di un numero IMEI per identificare i dispositivi mobili aziendali. Una volta registrati in Intune, i dispositivi con numeri IMEI importati vengono contrassegnati come aziendali, che possono essere usati per l'applicazione di criteri diversi da quelli applicati ai dispositivi personali.
## Aggiungere numeri IMEI (International Mobile Equipment Identity) in Intune
1. Nella [console di amministrazione di Microsoft Intune](http://manage.microsoft.com) fare clic su **Gruppi** &gt; **Tutti i dispositivi** &gt; **Dispositivi aziendali preregistrati** &gt; **Per IMEI (tutte le piattaforme)**, quindi fare clic su **Aggiungi dispositivi...**. È possibile aggiungere dispositivi in due modi:

    -   **Caricare un file CSV contenente i numeri di serie**: creare un elenco delimitato da virgole (CSV) composto da due colonne senza intestazione e limitato a 5 MB o 5000 dispositivi per ogni file CSV.

        |||
        |-|-|
        |&lt;IMEI #1&gt;|&lt;Dettagli dispositivo 1 &gt;|
        |&lt;IMEI #2&gt;|&lt;Dettagli dispositivo 2&gt;|
        Il file con estensione CSV quando viene visualizzato in un editor di testo viene visualizzato come:

        ```
        AA-BBBBBB-CCCCCC-D,PO 1234
        AA-BBBBBB-CCCCCC-E,PO 1234
        ```

    -   **Aggiungere manualmente i dettagli dispositivo**: immettere il numero IMEI e i dettagli per un massimo di cinque dispositivi.

   I *dettagli* sono per uso amministrativo in modo da poter identificare il numero IMEI associato a un dispositivo. Queste informazioni non vengono inviate al dispositivo, ma verranno visualizzate nella console di Intune. 

2.   Fare clic su **Avanti**.
3.  Nel riquadro **Verifica dispositivi** è possibile verificare i numeri IMEI dei dispositivi importati. È anche possibile decidere se sovrascrivere i **Dettagli** per i numeri IMEI da reimportare. È possibile deselezionare la casella di controllo **Sovrascrivi** per mantenere i dettagli correnti. Fare clic su **Fine** per importare i numeri IMEI.
4.  I numeri IMEI e le descrizioni vengono aggiunti all'elenco **Per IMEI (tutte le piattaforme)**. 

Quando il dispositivo con tale numero IMEI viene registrato, in genere quando un utente installa l'app Portale aziendale e completa il processo di registrazione, il dispositivo verrà contrassegnato come aziendale e verrà visualizzato come registrato nel gruppo **Dispositivi IMEI**.



<!--HONumber=Apr16_HO4-->


