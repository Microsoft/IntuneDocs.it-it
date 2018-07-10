---
title: Impostazioni personalizzate per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Configurare le impostazioni personalizzate OMA-URI nei dispositivi che eseguono Windows 10 con un profilo personalizzato in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232827"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>Impostazioni OMA-URI personalizzate per i dispositivi Windows 10 - Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare il profilo **personalizzato** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire impostazioni OMA-URI (Open Mobile Alliance Uniform Resource Identifier). Queste impostazioni vengono usate per controllare le funzionalità nei dispositivi. Windows 10 rende disponibili molte impostazioni CSP (Configuration Service Provider, provider di servizi di configurazione), ad esempio il [provider di servizi di configurazione dei criteri](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Se si sta cercando un'impostazione specifica, tenere presente che il [profilo di restrizione del dispositivo Windows 10](device-restrictions-windows-10.md) contiene molte impostazioni integrate in Intune che non richiedono valori personalizzati.

## <a name="configure-custom-settings"></a>Configurare le impostazioni personalizzate

1. Creare un nuovo profilo di configurazione usando il tipo di profilo **Personalizzato**. La procedura è descritta in [Come configurare le impostazioni dispositivo personalizzate](custom-settings-configure.md).
2. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi** per creare una nuova impostazione. È anche possibile fare clic su **Esporta** per creare un elenco di tutti i valori configurati in un file con valori delimitati da virgole (estensione CSV).
3. Per ogni impostazione URI OMA che si vuole aggiungere, immettere le informazioni seguenti:

- **Nome**: immettere un nome univoco per l'impostazione OMA-URI per identificarla nell'elenco delle impostazioni.
- **Descrizione**: immettere facoltativamente una descrizione per l'impostazione.
- **URI OMA (maiuscole/minuscole)**: immettere il valore URI OMA per cui si vuole specificare un'impostazione.
- **Tipo di dati**: scegliere tra:
  - **Stringa**
  - **Stringa (XML)**
  - **Data e ora**
  - **Intero**
  - **A virgola mobile**
  - **Booleano**
  - **Base64**
- **Valore**: immettere il valore o un file da associare al valore OMA-URI immesso.

4. Al termine, selezionare **OK**. In **Crea profilo** selezionare **Crea**. Il profilo verrà creato e visualizzato nell'elenco dei profili.

## <a name="example"></a>Esempio
Nell'esempio seguente l'impostazione **Connectivity/AllowVPNOverCellular** è abilitata. Questa impostazione consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

![Esempio di un criterio personalizzato contenente le impostazioni VPN](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Individuare i criteri che è possibile configurare

Un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows 10 è disponibile in [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione).

Non tutte le impostazioni sono compatibili con tutte le versioni di Windows 10. In [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione) sono indicate le versioni supportate per ogni provider CSP.

Intune, inoltre, non supporta tutte le impostazioni elencate. Per verificare se Intune supporta l'impostazione desiderata, aprire l'articolo relativo all'impostazione. Ogni pagina relativa a un'impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare l'operazione **Add** o **Replace**.
