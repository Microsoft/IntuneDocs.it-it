---
title: Impostazioni personalizzate di Intune per dispositivi Windows Holographic for Business
titlesuffix: Azure portal
description: "Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Windows Holographic for Business\"."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae46aef10ca294637a4d433ce273d3c53e695d64
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>Impostazioni personalizzate per i dispositivi Windows Holographic for Business in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Usare il profilo **personalizzato** di Microsoft Intune per Windows Holographic for Business per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows Holographic for Business rende disponibili molte impostazioni dei provider di servizi di configurazione (CSP). Per una panoramica sui provider di servizi di configurazione, vedere [Introduzione ai provider di servizi di configurazione per i professionisti IT](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Per i provider di servizi di configurazione specifici supportati da Windows Holographic, vedere [Provider di servizi di configurazione supportati in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Se si sta cercando una determinata impostazione, tenere presente che il [profilo di restrizione del dispositivo Windows Holographic for Business](device-restrictions-windows-holographic.md) contiene molte impostazioni predefinite per cui non è necessario specificare valori personalizzati.

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** scegliere **Impostazioni** per aggiungere una o più impostazioni URI OMA.
3. Nel pannello **Impostazioni OMA-URI personalizzate** fare clic su **Aggiungi** per aggiungere un nuovo valore. È anche possibile fare clic su **Esporta** per creare un elenco di tutti i valori configurati in un file con valori delimitati da virgole (estensione CSV).
4. Per ogni impostazione URI OMA che si vuole aggiungere, immettere le informazioni seguenti. Usare l'elenco in questo argomento per informazioni sulle impostazioni che è possibile usare:
    - **Nome impostazione**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione impostazione**: immettere facoltativamente una descrizione per l'impostazione.
    - **Tipo di dati**: scegliere tra:
        - **Stringa**
        - **Stringa (XML)**
        - **Data e ora**
        - **Intero**
        - **A virgola mobile**
        - **Booleano**
    - **URI OMA (maiuscole/minuscole)**: specificare l'impostazione URI OMA per cui si vuole fornire un'impostazione.
    - **Valore**: specificare il valore da associare all'impostazione URI OMA specificata.
5. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.
Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="supported-custom-settings"></a>Impostazioni personalizzate supportate

Windows Holographic for Business supporta le impostazioni personalizzate seguenti:


|Nome impostazione|URI OMA|Tipo di dati  |
|---------|---------|---------|
|AllowFastReconnect     |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Integer (0: non è consentito, 1: consentito)|
|AllowVPN     |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Integer (0: non è consentito, 1: consentito)|



## <a name="how-to-find-the-policies-you-can-configure"></a>Come trovare i criteri che è possibile configurare

È possibile trovare un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows Holographic in [Provider di servizi di configurazione supportati in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens). Non tutte le impostazioni sono compatibili con tutte le versioni di Windows Holographic. La tabella nell'argomento di Windows indica quali versioni sono supportate per ogni CSP.

Intune inoltre non supporta tutte le impostazioni elencate nell'argomento. Per verificare se Intune supporta l'impostazione desiderata, aprire l'argomento relativo all'impostazione. Ogni pagina relativa a un'impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare l'operazione **Add** o **Replace**.


