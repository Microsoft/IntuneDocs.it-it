---
title: Risolvere i conflitti di criteri tra Intune e gli oggetti Criteri di gruppo
titlesuffix: Microsoft Intune
description: Informazioni su come risolvere i conflitti tra criteri di configurazione di Intune e criteri di gruppo.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.openlocfilehash: 2aee866d06a31c0fe188dd8fb313609043f0092f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190066"
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>Risolvere i conflitti di criteri tra Microsoft Intune e gli oggetti Criteri di gruppo

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Intune usa criteri che consentono di gestire le impostazioni nei PC Windows. Ad esempio, è possibile usare un criterio per controllare le impostazioni di Windows Firewall nei PC. Molte impostazioni di Intune sono simili alle impostazioni che è possibile configurare con i Criteri di gruppo di Windows. A volte, però, i due metodi possono entrare in conflitto.

In questo caso, i criteri di gruppo a livello di dominio hanno la precedenza sui criteri di Intune, a meno che un PC non sia in grado di connettersi al dominio. In questo caso, i criteri di Intune si applicano al PC client.

## <a name="what-to-do-if-you-are-using-group-policy"></a>Che cosa fare se si usa Criteri di gruppo
Verificare che i criteri applicati non siano gestiti da Criteri di gruppo. Per evitare conflitti, è possibile applicare uno o più dei metodi seguenti:

-   Spostare i PC in un'unità organizzativa Active Directory in cui non sono stati applicati i Criteri di gruppo prima di installare il client di Intune. È inoltre possibile bloccare l'ereditarietà di Criteri di gruppo nelle unità organizzative che includono PC registrati in Intune ai quali non si vuole che vengano applicate le impostazioni di Criteri di gruppo.

-   Usare un filtro gruppo di sicurezza per limitare gli oggetti Criteri di gruppo solo ai PC gestiti da Intune.

-   Disabilitare o rimuovere gli oggetti Criteri di gruppo che sono in conflitto con i criteri di Intune.

Per altre informazioni sui Criteri di gruppo di Active Directory e Windows, vedere la documentazione di Windows Server.

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>Come filtrare gli oggetti Criteri di gruppo esistenti per evitare conflitti con i criteri di Intune
Se sono stati identificati oggetti Criteri di gruppo con impostazioni in conflitto con Intune, è possibile usare i filtri del gruppo di sicurezza per limitare tali oggetti ai soli PC non gestiti da Intune.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

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

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Gli oggetti Criteri di gruppo possono essere applicati solo ai gruppi di sicurezza specificati nell'area **Filtri di sicurezza** della console Gestione Criteri di gruppo per l'oggetto selezionato. Per impostazione predefinita, gli oggetti Criteri di gruppo vengono applicati ai membri del gruppo *Authenticated Users*.

-   Nello snap-in **Utenti e computer di Active Directory** creare un nuovo gruppo di sicurezza contenente i computer e gli account utente che non si vogliono gestire con Intune. Ad esempio, è possibile denominare il gruppo *Non appartenenti a Microsoft Intune*.

-   Nella console di gestione dei criteri di gruppo, nella scheda **Delega** relativa all'oggetto Criteri di gruppo selezionato, fare clic con il pulsante destro del mouse sul nuovo gruppo di sicurezza per delegare le appropriate autorizzazioni **Lettura** e **Applica Criteri di gruppo** sia agli utenti che ai computer del gruppo di sicurezza. Le autorizzazioni**Applica Criteri di gruppo** si trovano nella finestra di dialogo **Avanzate** .

-   Quindi, applicare il filtro del nuovo gruppo di sicurezza all'oggetto Criteri di gruppo selezionato e rimuovere il filtro predefinito **Authenticated Users**.

È necessario gestire la registrazione del nuovo gruppo di sicurezza in seguito a modifiche del servizio Intune.

### <a name="see-also"></a>Vedere anche
[Gestire i PC Windows con Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
