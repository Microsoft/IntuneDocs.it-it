---
# required metadata

title: Impostazioni dei criteri di conformità per i dispositivi Android | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Impostazioni dei criteri di conformità per i dispositivi Android in Microsoft Intune

Le impostazioni dei criteri descritte in questo argomento si applicano ai dispositivi che eseguono Android 4.0 e versioni successive oppure Samsung KNOX 4.0 e versioni successive.

Per informazioni su altre piattaforme, selezionare una delle voci seguenti:
> [!div class="op_single_selector"]
- [Impostazioni dei criteri di conformità per i dispositivi iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Impostazioni dei criteri di conformità per i dispositivi Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Impostazioni di sicurezza del sistema
### Password
- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password
  per poter accedere al dispositivo.

-  **Lunghezza minima password**: specificare il numero minimo di cifre o caratteri che la password dell'utente deve contenere.

- **Qualità password:** abilitare quest'impostazione per configurare i requisiti delle password per i dispositivi Android. È possibile scegliere tra:
  -   **Protezione biometrica bassa**
  - **Richiesto**
  -   **Almeno numerico**
  -   **Almeno alfabetico**
  -   **Almeno alfanumerico**
  -   **Alfanumerico con simboli**

- **Minuti di inattività prima che venga richiesta la password:** specifica il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni):** selezionare il numero di giorni che mancano alla scadenza della password attuale,
  quando l'utente deve creare una nuova password.

- **Ricorda cronologia password:** usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di
  creare password già usate in precedenza.

- **Impedisci riutilizzo delle password precedenti:** se si seleziona **Ricorda cronologia password**, specificare il
  numero di password usate in precedenza che non è possibile tornare a usare.

- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività:**
  Questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti finali viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione
  **Minuti di inattività prima che venga richiesta la password**.

### Encryption
- **Richiedi crittografia sul dispositivo mobile:** impostare questa opzione su **Sì** per richiedere che il dispositivo sia
  crittografato per la connessione alle risorse. I dispositivi sono
  crittografati quando si configura l'impostazione **Richiedi una password per
  sbloccare i dispositivi mobili**.

## Impostazioni dell'integrità dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted**: se si attiva questa impostazione,
  i dispositivi jailbroken verranno valutati come non conformi.

## Impostazioni delle proprietà dei dispositivi
- **Versione minima richiesta del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo,
  viene segnalato come non conforme.
  Viene visualizzato un collegamento a informazioni per eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.

- **Versione massima richiesta del sistema operativo:** quando un dispositivo usa una versione del
  sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali risulta bloccato e l'utente deve contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.


<!--HONumber=May16_HO1-->


