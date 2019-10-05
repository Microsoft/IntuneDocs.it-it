---
title: Aggiungere le impostazioni personalizzate per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo personalizzato per usare le impostazioni OMA-URI per i dispositivi che eseguono Windows 10 in Microsoft Intune. Usare un profilo personalizzato per aggiungere le impostazioni personalizzate.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51ee389351dd0ccccf69f01e932f7374ca38b03b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735064"
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

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il profilo, ad esempio `windows 10 custom profile`.
    - **Descrizione:** immettere una descrizione per il profilo.
    - **Piattaforma**: scegliere **Windows 10 e versioni successive**.
    - **Tipo di profilo**: scegliere **Personalizzato**.

4. In **Impostazioni OMA-URI personalizzate** selezionare **Aggiungi**. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome univoco per l'impostazione OMA-URI per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: immettere una descrizione che offra una panoramica dell'impostazione e altri dettagli importanti.
    - **OMA-URI (maiuscole/minuscole)** : immettere il valore OMA-URI che si vuole usare come impostazione.
    - **Tipo di dati**: immettere il tipo di dati da usare per l'impostazione OMA-URI. Le opzioni disponibili sono:

        - Stringa
        - Stringa (file XML)
        - Data e ora
        - Integer
        - A virgola mobile
        - Boolean
        - Base64 (file)

    - **Valore**: immettere il valore dati da associare all'impostazione OMA-URI immessa. Il valore varia a seconda del tipo di dati selezionato. Ad esempio, se si sceglie **Data e ora**, selezionare il valore dalla selezione data.

    Dopo aver aggiunto alcune impostazioni, è possibile selezionare **Esporta**. **Esporta** crea un elenco di tutti i valori aggiunti in un file con valori delimitati da virgole (file con estensione csv).

5. Selezionare **OK** per salvare le modifiche. Continuare ad aggiungere altre impostazioni in base alle esigenze.
6. Al termine, scegliere **OK** > **Crea** per creare il profilo di Intune. Il profilo viene visualizzato nell'elenco **Configurazione del dispositivo - Profili**.

## <a name="example"></a>Esempio

Nell'esempio seguente l'impostazione **Connectivity/AllowVPNOverCellular** è abilitata. Questa impostazione consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

![Esempio di un criterio personalizzato contenente le impostazioni VPN](./media/custom-settings-windows-10/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Individuare i criteri che è possibile configurare

Un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows 10 è disponibile in [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione).

Non tutte le impostazioni sono compatibili con tutte le versioni di Windows 10. In [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione) sono indicate le versioni supportate per ogni provider CSP.

Inoltre, Intune non supporta tutte le impostazioni elencate in [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione). Per verificare se Intune supporta l'impostazione desiderata, aprire l'articolo relativo all'impostazione. La pagina di ogni impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare le operazioni **Add** o **Replace** e **Get**. Se il valore restituito dall'operazione **Get** non corrisponde al valore fornito dalle operazioni **Add** o **Replace**, Intune segnala un errore di conformità.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. È ora necessario [assegnare il profilo](device-profile-assign.md).
