---
title: Impostazioni personalizzate di Intune per dispositivi Windows 10
titlesuffix: Azure portal
description: "Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Windows 10.\""
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9f5faacd4b78df809d96ed5c5ece4fb7c0237a3c
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Impostazioni personalizzate per i dispositivi Windows 10 in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Usare il profilo **personalizzato** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows 10 rende disponibili molte impostazioni CSP (Configuration Service Provider, provider di servizi di configurazione), ad esempio il [provider di servizi di configurazione dei criteri](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Se si sta cercando una determinata impostazione, tenere presente che il [profilo di restrizione del dispositivo Windows 10](device-restrictions-windows-10.md) contiene molte impostazioni integrate in Intune per cui non è necessario specificare valori personalizzati.

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
Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="example"></a>Esempio
Nella schermata seguente è stata abilitata l'impostazione **Connectivity/AllowVPNOverCellular**. Ciò consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

> ![Esempio di un criterio personalizzato contenente le impostazioni VPN](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Come trovare i criteri che è possibile configurare

Per un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows 10, vedere [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione) nella raccolta di documentazione di Windows.

Non tutte le impostazioni sono compatibili con tutte le versioni di Windows 10. La tabella nell'argomento di Windows indica quali versioni sono supportate per ogni CSP.

Intune inoltre non supporta tutte le impostazioni elencate nell'argomento. Per verificare se Intune supporta l'impostazione desiderata, aprire l'argomento relativo all'impostazione. Ogni pagina relativa a un'impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare l'operazione **Add** o **Replace**.


