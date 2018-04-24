---
title: Impostazioni personalizzate di Microsoft Intune per dispositivi Windows 10
titlesuffix: ''
description: Informazioni sulle impostazioni personalizzate che è possibile usare in un profilo personalizzato di Windows 10.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c8e0d56c91b710a86949844d2fd455e4183488f5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>Impostazioni dei dispositivi personalizzate di Microsoft Intune per dispositivi che eseguono Windows 10

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Usare il profilo **personalizzato** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows 10 rende disponibili molte impostazioni CSP (Configuration Service Provider, provider di servizi di configurazione), ad esempio il [provider di servizi di configurazione dei criteri](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Se si sta cercando una determinata impostazione, tenere presente che il [profilo di restrizione del dispositivo Windows 10](device-restrictions-windows-10.md) contiene molte impostazioni integrate in Intune per cui non è necessario specificare valori personalizzati.

## <a name="configure-custom-settings"></a>Configurare le impostazioni personalizzate

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
1. Nel riquadro **Impostazioni OMA-URI personalizzate** fare clic su **Aggiungi** per aggiungere un nuovo valore. È anche possibile fare clic su **Esporta** per creare un elenco di tutti i valori configurati in un file con valori delimitati da virgole (estensione CSV).
1. Per ogni impostazione URI OMA che si vuole aggiungere, immettere le informazioni seguenti. Usare l'elenco in questo articolo per informazioni sulle impostazioni che è possibile usare:
    - **Nome**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: immettere facoltativamente una descrizione per l'impostazione.
    - **URI OMA (maiuscole/minuscole)**: specificare l'impostazione URI OMA per cui si vuole fornire un'impostazione.
    - **Tipo di dati**: scegliere tra:
        - **Stringa**
        - **Stringa (XML)**
        - **Data e ora**
        - **Intero**
        - **A virgola mobile**
        - **Booleano**
        - **Base64**
    - **Valore**: specificare il valore o il file da associare all'impostazione URI OMA specificata.
1. Al termine selezionare **OK**, tornare alla pagina **Crea profilo** e scegliere **Crea**.
Il profilo viene creato e visualizzato nel riquadro dell'elenco dei profili.

## <a name="example"></a>Esempio
Nella schermata seguente è stata abilitata l'impostazione **Connectivity/AllowVPNOverCellular**. Ciò consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

> ![Esempio di un criterio personalizzato contenente le impostazioni VPN](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Come trovare i criteri che è possibile configurare

Per un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows 10, vedere [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione) nella raccolta di documentazione di Windows.

Non tutte le impostazioni sono compatibili con tutte le versioni di Windows 10. La tabella nell'articolo di Windows indica quali versioni sono supportate per ogni CSP.

Intune inoltre non supporta tutte le impostazioni elencate nell'articolo. Per verificare se Intune supporta l'impostazione desiderata, aprire l'articolo relativo all'impostazione. Ogni pagina relativa a un'impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare l'operazione **Add** o **Replace**.
