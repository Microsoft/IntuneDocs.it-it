---
title: Usare un PIN per accedere ai dispositivi Windows 10 con Microsoft Intune - Azure | Microsoft Docs
description: Usare Windows Hello for Business per consentire agli utenti di accedere ai dispositivi usando un PIN, un'impronta digitale e altro. Creare un profilo di configurazione di protezione dell'identità in Intune per i dispositivi Windows 10 con queste impostazioni e assegnare il profilo ai gruppi di utenti e ai gruppi di dispositivi.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4fce03913042675588ea12e5399e6f5a1be04946
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188241"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Usare Windows Hello for Business nei dispositivi Windows 10 con Microsoft Intune

Windows Hello for Business è un metodo per accedere ai dispositivi Windows che sostituisce password, smart card e smart card virtuali. Intune include delle impostazioni predefinite che consentono agli amministratori di configurare e usare Windows Hello for Business. Ad esempio, è possibile usare queste impostazioni per:

- Abilitare Windows Hello for Business per dispositivi e utenti
- Impostare i requisiti del PIN del dispositivo, inclusa una lunghezza minima o massima del PIN
- Consentire i movimenti, ad esempio un'impronta digitale, che gli utenti possono e non possono usare per accedere ai dispositivi

Questa funzionalità si applica ai dispositivi che eseguono:

- Windows 10 e versioni successive
- Windows 10 Mobile
- Windows Holographic for Business

Intune usa "profili di configurazione" per creare e personalizzare queste impostazioni per le esigenze dell'organizzazione. Dopo aver aggiunto queste funzionalità in un profilo, eseguire il push o distribuire queste impostazioni ai gruppi di utenti e dispositivi nell'organizzazione.

Questo articolo illustra come creare un profilo di configurazione del dispositivo. Per un elenco di tutte le impostazioni e delle operazioni corrispondenti, vedere [Impostazioni dei dispositivi Windows 10 per abilitare Windows Hello for Business](identity-protection-windows-settings.md).

## <a name="create-the-device-profile"></a>Creare il profilo del dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.

3. Immettere le proprietà seguenti:

   - **Nome**: immettere un nome descrittivo per il nuovo profilo.
   - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
   - **Piattaforma**: selezionare **Windows 10 e versioni successive**. Windows Hello for Business è supportato solo nei dispositivi che eseguono Windows 10 e versioni successive.
   - **Tipo di profilo**: selezionare **Protezione dell'identità**.

4. Nel riquadro *Windows Hello for Business* configurare le opzioni seguenti:

   - **Configurare Windows Hello for Business**: scegliere come configurare Windows Hello for Business:

     - **Non configurato** (impostazione predefinita): [effettua il provisioning di Windows Hello for Business](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) nel dispositivo. Quando si assegnano i profili di Identity Protection solo agli utenti, per impostazione predefinita il contesto del dispositivo è **Non configurato**.

     - **Disabilitato**: selezionare questa opzione se non si vuole usare Windows Hello for Business. Questa opzione disabilita Windows Hello for Business per tutti gli utenti.

     - **Attivata**: scegliere questa opzione per [effettuare il provisioning](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning) e configurare le impostazioni di Windows Hello for Business in Intune. Immettere le impostazioni da configurare. Per un elenco di tutte le impostazioni e delle operazioni corrispondenti, vedere [Impostazioni dei dispositivi Windows 10 per abilitare Windows Hello for Business](identity-protection-windows-settings.md).

   - **Usa le chiavi di sicurezza per l'accesso**: abilitare la chiave di sicurezza di Windows Hello come credenziale di accesso per tutti i PC nel tenant.

     - **Attiva**
     - **Non configurato** (impostazione predefinita)

5. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco dei profili. Successivamente [assegnare](../configuration/device-profile-assign.md) questo profilo ai gruppi di utenti e dispositivi in base alle esigenze.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/identity-protection-configure/disable-android-camera.png)

-->

## <a name="next-steps"></a>Passaggi successivi

- Visualizzare un elenco di tutte [le impostazioni e delle operazioni corrispondenti](identity-protection-windows-settings.md).
- [Assegnare il profilo](../configuration/device-profile-assign.md) e [monitorarne lo stato](../configuration/device-profile-monitor.md).
