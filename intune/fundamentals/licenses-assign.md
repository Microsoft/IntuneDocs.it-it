---
title: Assegnare licenze di Microsoft Intune
description: Assegnare licenze agli utenti in modo che possano registrare i dispositivi in Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a62cc6ef2f1b3bd6f305fe6fa23a24f95d3dd37
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207358"
---
# <a name="assign-licenses-to-users-so-they-can-enroll-devices-in-intune"></a>Assegnare licenze agli utenti in modo che possano registrare i dispositivi in Intune

Indipendentemente dal fatto che si decida di aggiungere gli utenti manualmente o di sincronizzarli da Active Directory locale, è necessario assegnare una licenza di Intune a ogni utente prima che gli utenti possano registrare i propri dispositivi in Intune. Per un elenco di licenze, vedere [Licenze che includono Intune](../licenses.md).

> [!NOTE]
> Anche gli utenti a cui vengono assegnati criteri di protezione delle app di Intune e che non registrano i propri dispositivi in Microsoft Intune necessitano di una licenza di Intune per ricevere i criteri. 

## <a name="assign-an-intune-license-microsoft-endpoint-manager-admin-center"></a>Assegnare una licenza di Intune con l'interfaccia di amministrazione di Microsoft Endpoint Manager

È possibile usare l'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) per aggiungere manualmente gli utenti basati sul cloud e assegnare licenze ad account utente basati sul cloud e account sincronizzati con Azure AD dall'istanza locale di Active Directory.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **Utenti** > **Tutti gli utenti** > scegliere un utente > **Licenze** > **Assegnazioni**.

2. Scegliere la casella per **Intune** > **Salva**.

   ![Screenshot della sezione Licenze di prodotto dell'interfaccia di amministrazione di Microsoft 365.](./media/licenses-assign/mem-assign-license.png)

3. L'account utente dispone ora delle autorizzazioni necessarie per usare il servizio e registrare dispositivi nella gestione.

> [!NOTE]
> Gli utenti vengono visualizzati nel portale classico di Intune solo dopo che hanno registrato un dispositivo usando il client PC di Intune. È anche possibile selezionare un gruppo di utenti per modificare le licenze contemporaneamente, selezionando le opzioni per aggiungere o sostituire una licenza per tutti gli utenti selezionati.

## <a name="assign-an-intune-license-by-using-azure-active-directory"></a>Assegnare una licenza di Intune con Azure Active Directory

È anche possibile assegnare le licenze di Intune agli utenti usando Azure Active Directory. Per altre informazioni, vedere l'[articolo Assegnare licenze agli utenti in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal). 

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>Usare School Data Sync per assegnare licenze Education agli utenti di Intune

Le organizzazioni che operano nel settore dell'istruzione possono usare School Data Sync (SDS) per assegnare licenze Intune per Education agli utenti sincronizzati. È sufficiente selezionare la casella di controllo Intune per Education durante la configurazione del profilo SDS.  

![Screenshot dell'impostazione del profilo SDS](./media/licenses-assign/i4e-sds-profile-setup-setting.png)

Quando si assegna una licenza Intune per Education, assicurarsi di assegnare anche una licenza di Intune A Direct.

![Screenshot della configurazione della licenza del prodotto](./media/licenses-assign/i4e-set-licenses.png)

Per altre informazioni su SDS, vedere questa [panoramica di School Data Sync](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

## <a name="how-user-and-device-licenses-affect-access-to-services"></a>Effetti delle licenze utente e dispositivo sull'accesso ai servizi

* Ogni **utente** a cui viene assegnata una licenza software utente può accedere ai servizi online e al software correlato, incluso il software System Center, e usarli per gestire le applicazioni e fino a 15 dispositivi MDM. L'agente PC di Intune consente 5 computer e 1 macchina virtuale per licenza utente.
* È possibile acquistare le licenze per i dispositivi separatamente dalle licenze utente. Le licenze dispositivo non devono essere assegnate ai dispositivi. Ogni dispositivo che accede e usa i servizi online e il software correlato (incluso il software System Center) deve avere una licenza dispositivo.
* Se un dispositivo è usato da più di un utente, per ognuno è richiesta una licenza software dispositivo oppure tutti gli utenti devono avere una licenza software utente.

## <a name="understanding-the-type-of-licenses-you-have-purchased"></a>Informazioni sul tipo di licenze acquistate

La modalità con cui è stato acquistato Intune determina le informazioni di sottoscrizione:

- Se Intune è stato acquistato tramite un contratto Enterprise Agreement, è possibile trovare le informazioni sulla sottoscrizione nel portale dei contratti multilicenza in **Sottoscrizioni**.
- Se Intune è stato acquistato tramite Cloud Solution Provider, contattare il rivenditore.
- Se Intune è stato acquistato con un numero di carta di credito o una fattura, le licenze sono basate su utente.

## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Usare PowerShell per gestire in modo selettivo le licenze utente di EMS
Le organizzazioni che usano Microsoft Enterprise Mobility Suite + Security (precedentemente noto come Enterprise Mobility Suite) possono contenere utenti che necessitano solo di Azure Active Directory Premium o dei servizi di Intune nel pacchetto EMS. È possibile assegnare un servizio o un sottoinsieme di servizi tramite i [cmdlet di PowerShell per Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Per assegnare in modo selettivo le licenze utente per i servizi EMS, aprire PowerShell come amministratore su un computer dotato del [Modulo di Azure Active Directory per Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule). È possibile installare PowerShell su un computer locale o su un server ADFS.

È necessario creare una nuova definizione dello SKU della licenza da applicare solo ai piani del servizio desiderati. A tale scopo, disabilitare i piani a cui non si desidera applicare la nuova definizione. Ad esempio, è possibile creare una definizione dello SKU che non assegna una licenza di Intune. Per visualizzare un elenco dei servizi disponibili, digitare:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

È possibile eseguire il comando seguente per escludere il piano di servizio di Intune. È possibile usare lo stesso metodo per espandere un intero gruppo di sicurezza o usare filtri più granulari.

**Esempio 1**<br>
Creare un nuovo utente nella riga di comando e assegnare una licenza di EMS senza abilitare la parte di Intune della licenza:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS

Verificare con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Esempio 2**<br>
Disabilitare la parte di Intune della licenza EMS per un utente a cui è già stata assegnata una licenza:

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

Verificare con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/licenses-assign/posh-addlic-verify.png)
