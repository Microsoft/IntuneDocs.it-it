---
title: Aggiungere le impostazioni personalizzate per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo personalizzato per usare le impostazioni OMA-URI per i dispositivi che eseguono Windows 10 in Microsoft Intune. Usare un profilo personalizzato per aggiungere le impostazioni personalizzate.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e3d2784e0242498fbae43ab61034a5be31b0952
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206772"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Usare le impostazioni personalizzate per dispositivi Windows 10 in Intune

Con Microsoft Intune è possibile aggiungere o creare impostazioni personalizzate per i dispositivi Windows 10 usando i "profili personalizzati". I profili personalizzati sono una funzionalità di Intune. Sono progettati per aggiungere impostazioni dei dispositivi e funzionalità non incluse in Intune.

I profili personalizzati Windows 10 usano impostazioni Open Mobile Alliance Uniform Resource Identifier (OMA-URI) per configurare funzionalità diverse. Tali impostazioni vengono in genere usate dai produttori di dispositivi mobili per controllare le funzionalità del dispositivo. 

Windows 10 rende disponibili molte impostazioni CSP (Configuration Service Provider, provider di servizi di configurazione), ad esempio il [provider di servizi di configurazione dei criteri](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Se si sta cercando una determinata impostazione, tenere presente che il [profilo di restrizione del dispositivo Windows 10](device-restrictions-windows-10.md) contiene numerose impostazioni predefinite. Pertanto, potrebbe non essere necessario immettere valori personalizzati.

Questo articolo:

- Descrive come creare un profilo personalizzato per dispositivi Windows 10
- Contiene un elenco delle impostazioni OMA-URI consigliate
- Offre un esempio di profilo personalizzato che apre una connessione VPN

## <a name="create-the-profile"></a>Creare il profilo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di profilo valido è **il profilo personalizzato di Windows 10**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
    - **Tipo di profilo**: selezionare **personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
    - **OMA-URI (maiuscole/minuscole)**: immettere l'OMA-URI da usare come impostazione.
    - **Tipo di dati**: selezionare il tipo di dati da usare per questa impostazione OMA-URI. Le opzioni disponibili sono:

        - Stringa
        - Stringa (file XML)
        - Data e ora
        - Intero
        - A virgola mobile
        - Boolean
        - Base64 (file)

    - **Valore**: immettere il valore dati da associare all'impostazione OMA-URI immessa. Il valore varia a seconda del tipo di dati selezionato. Ad esempio, se si seleziona **Data e ora**, selezionare il valore dalla selezione data.

    Dopo aver aggiunto alcune impostazioni, è possibile selezionare **Esporta**. **Esporta** crea un elenco di tutti i valori aggiunti in un file con valori delimitati da virgole (file con estensione csv).

5. Selezionare **OK** per salvare le modifiche. Continuare ad aggiungere altre impostazioni in base alle esigenze.
6. Al termine, selezionare **OK** > **Crea** per creare il profilo di Intune. Una volta completata l'operazione, il profilo viene visualizzato nell'elenco **Dispositivi - Profili di configurazione**.

## <a name="example"></a>Esempio

Nell'esempio seguente l'impostazione **Connectivity/AllowVPNOverCellular** è abilitata. Questa impostazione consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

![Esempio di un criterio personalizzato contenente le impostazioni VPN](./media/custom-settings-windows-10/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Individuare i criteri che è possibile configurare

Un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows 10 è disponibile in [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione).

Non tutte le impostazioni sono compatibili con tutte le versioni di Windows 10. In [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione) sono indicate le versioni supportate per ogni provider CSP.

Inoltre, Intune non supporta tutte le impostazioni elencate in [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione). Per verificare se Intune supporta l'impostazione desiderata, aprire l'articolo relativo all'impostazione. La pagina di ogni impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare le operazioni **Add** o **Replace** e **Get**. Se il valore restituito dall'operazione **Get** non corrisponde al valore fornito dalle operazioni **Add** o **Replace**, Intune segnala un errore di conformità.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).
