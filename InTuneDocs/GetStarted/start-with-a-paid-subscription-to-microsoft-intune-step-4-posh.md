---
title: Gestire le licenze di Intune tramite PowerShell | Microsoft Intune
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2d31c80-c32c-4315-8271-1b0cf9a1f78a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2847c9af38ae0ddddc8d76d548ae7abddc63e4c1
ms.openlocfilehash: e0eca2ecc9948c7caf15d5df5e6e106428b8b964


---

# Gestire le licenze Intune tramite PowerShell
Perché gli utenti possano accedere al servizio Intune o registrare i propri dispositivi nella gestione, è necessario assegnare loro una licenza per la sottoscrizione di Intune, come descritto nell'articolo relativo alla [gestione delle licenze Intune](start-with-a-paid-subscription-to-microsoft-intune-step-4.md). È tuttavia possibile che le organizzazioni che usano Enterprise Mobility Suite (EMS) di Microsoft contengano utenti che necessitano solo di Azure Active Directory Premium o dei servizi di Intune nel pacchetto EMS. È possibile assegnare un servizio o un sottoinsieme di servizi tramite i [cmdlet di PowerShell per Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx). 

Per assegnare in modo selettivo le licenze utente per i servizi EMS, aprire PowerShell come amministratore su un computer dotato del [Modulo di Azure Active Directory per Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule). È possibile installare PowerShell su un computer locale o su un server ADFS.

È necessario creare una nuova definizione dello SKU della licenza da applicare solo ai piani del servizio desiderati. A tale scopo, disabilitare i piani a cui non si desidera applicare la nuova definizione. Ad esempio, è possibile creare una definizione dello SKU che non assegna una licenza di Intune. Per visualizzare un elenco dei servizi disponibili, digitare:
 
    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus 

È possibile eseguire il comando seguente per escludere il piano di servizio di Intune. È possibile usare lo stesso metodo per espandere un intero gruppo di sicurezza o usare filtri più granulari. 

**Esempio 1** Creare un nuovo utente nella riga di comando e assegnare una licenza di EMS senza abilitare la parte di Intune della licenza:

    Connect-MsolService 
        
    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS 
    

Verificare con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Esempio 2** Disabilitare la parte di Intune della licenza EMS per un utente a cui è già stata assegnata una licenza:

    Connect-MsolService 
    
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -RemoveLicenses IAPProdPartnerTest:EMS
    
    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS
 
Verificare con:
 
    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com" .Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

### Passaggi successivi
A questo punto, il passaggio 4 della *Guida introduttiva a Intune* è stato completato.
>[!div class="step-by-step"]

>[&larr; **Sync users to Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md) (Sincronizzare utenti su Intune) [**Organize users and devices** (Organizzare utenti e dispositivi) &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  



<!--HONumber=Jun16_HO4-->


