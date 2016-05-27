---
# required metadata

title: Risolvere i conflitti di criteri tra Intune e gli oggetti Criteri di gruppo | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Risolvere i conflitti di criteri tra Microsoft Intune e gli oggetti Criteri di gruppo
Intune usa i criteri che consentono di gestire le impostazioni nei computer gestiti. Ad esempio, è possibile usare un criterio per controllare le impostazioni di Windows Firewall nei computer. Molte impostazioni di Intune sono simili alle impostazioni che è possibile configurare con i Criteri di gruppo di Windows. Tuttavia, è possibile che, in alcuni casi, i due metodi possano essere in conflitto.

In caso di conflitti, i criteri di gruppo a livello di dominio hanno la precedenza sui criteri di Intune, a meno che un computer non sia in grado di connettersi al dominio. In questo caso, i criteri di Intune si applicano al computer client.

## Che cosa fare se si usa Criteri di gruppo
Verificare che i criteri applicati non siano gestiti da Criteri di gruppo. Per evitare conflitti, è possibile applicare uno o più dei seguenti metodi:

-   Spostare i computer in un'unità organizzativa Active Directory in cui non sono stati applicati i Criteri di gruppo prima di installare il client di Intune. È inoltre possibile bloccare l'ereditarietà di Criteri di gruppo nelle unità organizzative che includono computer registrati in Intune ai quali non si vuole che vengano applicate le impostazioni di Criteri di gruppo.

-   Usare un filtro WMI o un filtro di sicurezza per limitare gli oggetti Criteri di gruppo solo ai computer gestiti da Intune. Per informazioni ed esempi su come eseguire l'operazione, vedere la sezione seguente [Come filtrare gli oggetti Criteri di gruppo esistenti per evitare conflitti con i criteri di Microsoft Intune](resolve-gpo-and-microsoft-intune-policy-conflicts.md#BKMK_Filter).

-   Disabilitare o rimuovere gli oggetti Criteri di gruppo che sono in conflitto con i criteri di Intune.

Per altre informazioni sui Criteri di gruppo di Active Directory e Windows, vedere la documentazione di Windows Server.

## Come filtrare gli oggetti Criteri di gruppo esistenti per evitare conflitti con i criteri di Intune
Se sono stati identificati gli oggetti Criteri di gruppo le cui impostazioni possano determinare conflitti con Intune, usare uno dei metodi filtro seguenti per limitare tali oggetti ai soli computer non gestiti tramite Intune.

### Usare i filtri WMI
I filtri WMI consentono di applicare selettivamente oggetti Criteri di gruppo ai computer che soddisfino le condizioni di una query. Per applicare un filtro WMI, distribuire un'istanza di classe WMI a tutti i computer aziendali prima della loro registrazione al servizio Intune.

#### Per applicare i filtri WMI a un oggetto Criteri di gruppo

1.  Creare un file oggetto di gestione copiando e incollando quanto indicato di seguito in un file di testo e salvarlo nel percorso desiderato come **WIT.mof**. Il file contiene l'istanza di classe WMI distribuita nei computer da registrare al servizio Intune.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  Distribuire il file usando uno script di avvio o Criteri di gruppo. Di seguito viene indicato il comando di distribuzione dello script di avvio. Prima di registrare i computer client al servizio Intune, è necessario distribuire l'istanza di classe WMI.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;percorso del file MOF&gt;\wit.mof**

3.  Per creare i filtri WMI, eseguire uno dei comandi seguenti, in base al fatto che l'oggetto Criteri di gruppo da filtrare venga applicato ai PC gestiti tramite Intune oppure a quelli non gestiti tramite Intune.

    -   Per gli oggetti Criteri di gruppo applicati ai computer non gestiti tramite Intune, usare il comando seguente:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   Per gli oggetti Criteri di gruppo applicati ai computer gestiti tramite Intune, usare il comando seguente:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Nella console di Gestione Criteri di gruppo, modificare l'oggetto Criteri di gruppo da applicare al filtro WMI creato nel passaggio precedente.

    -   Per gli oggetti Criteri di gruppo da applicare solo ai computer da gestire tramite Intune, applicare il filtro **WindowsIntunePolicyEnabled=1**..

    -   Per gli oggetti Criteri di gruppo da applicare solo ai computer da non gestire tramite Intune, applicare il filtro **WindowsIntunePolicyEnabled=0**..

Per altre informazioni sull'applicazione dei filtri WMI in Criteri di gruppo, vedere il post del blog relativo a [filtri di sicurezza, filtri WMI e destinazioni a livello di elemento nelle preferenze dei Criteri di gruppo](http://go.microsoft.com/fwlink/?LinkId=177883)..

### Usare filtri dei gruppi di sicurezza
Con Criteri di gruppo è possibile applicare oggetti Criteri di gruppo ai soli gruppi di sicurezza specificati nell'area **Filtri di sicurezza** della Console Gestione Criteri di gruppo per l'oggetto selezionato. Per impostazione predefinita, gli oggetti Criteri di gruppo vengono applicati ai membri del gruppo **Authenticated Users**..

-   Nello snap-in **Utenti e computer di Active Directory** creare un nuovo gruppo di sicurezza contenente i computer e gli account utente che non si vogliono gestire tramite Intune. Ad esempio, è possibile denominare il gruppo **Non appartenenti a Microsoft Intune**..

-   Nella console di gestione dei criteri di gruppo, nella scheda **Delega** relativa all'oggetto Criteri di gruppo selezionato, fare clic con il pulsante destro del mouse sul nuovo gruppo di sicurezza per delegare le appropriate autorizzazioni **Lettura** e **Applica Criteri di gruppo** sia agli utenti che ai computer del gruppo di sicurezza. Le autorizzazioni**Applica Criteri di gruppo** si trovano nella finestra di dialogo **Avanzate** .

-   Quindi, applicare il filtro del nuovo gruppo di sicurezza all'oggetto Criteri di gruppo selezionato e rimuovere il filtro predefinito **Authenticated Users** .

È necessario gestire la registrazione del nuovo gruppo di sicurezza in seguito a modifiche del servizio Intune.

### Vedere anche
[Gestire i PC Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO1-->


