---
# required metadata

title: Impostazioni dei criteri di conformità per i dispositivi iOS | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Impostazioni dei criteri di conformità per i dispositivi iOS in Microsoft Intune

Le impostazioni dei criteri descritte in questo argomento si applicano ai dispositivi che eseguono iOS 6 e versioni successive.

Per informazioni su altre piattaforme, selezionare una delle voci seguenti:
> [!div class="op_single_selector"]
- [Impostazioni dei criteri di conformità per i dispositivi Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Impostazioni dei criteri di conformità per i dispositivi Windows](windows-compliance-policy-settings-in-microsoft-intune.md)

## Impostazioni di sicurezza del sistema
### Password
- **Richiedi una password per sbloccare i dispositivi mobili:** impostare l'opzione su **Sì** per richiedere agli utenti di immettere una password per poter accedere al dispositivo. I dispositivi iOS che usano la password vengono crittografati.

- **Consenti password semplici:** impostare l'opzione su **Sì** per consentire agli utenti di creare password semplici come '**1234**' o '**1111**' 

-  **Lunghezza minima password**: specificare il numero minimo di cifre o caratteri che la password dell'utente deve contenere.
- **Tipo di password richiesto:** specificare se gli utenti devono creare una password **alfanumerica** o **numerica**.

- **Numero minimo di set di caratteri:** se **Tipo di password richiesto** è impostato su **Alfanumerico**, usare questa impostazione per specificare il numero minimo di set di caratteri che la password deve contenere. I quattro set di caratteri sono:
  -   Lettere minuscole
  -   Lettere maiuscole
  -   Simboli
  -   Numeri

  Se per questa impostazione viene usato un numero più alto, gli utenti dovranno creare password più complesse.

  Per i dispositivi iOS, questa impostazione si riferisce al numero di caratteri speciali (ad esempio **!**, **#**, **&amp;**) che è necessario includere nella password.
- **Minuti di inattività prima che venga richiesta la password:** specifica il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni):** selezionare il numero di giorni che mancano alla scadenza della password attuale, quando l'utente deve creare una nuova password.

- **Ricorda cronologia password:** usare questa impostazione insieme a **Impedisci riutilizzo delle password precedenti** per impedire all'utente di creare password già usate in precedenza.

- **Impedisci riutilizzo delle password precedenti:** se l'opzione **Ricorda cronologia password** è selezionata, specificare il numero di password usate in precedenza che non è possibile riutilizzare.

- **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività:** questa impostazione deve essere usata insieme all'impostazione **Minuti di inattività prima che venga richiesta la password**. Agli utenti finali viene richiesto di immettere una password per accedere a un dispositivo che è rimasto inattivo per il tempo specificato nell'impostazione **Minuti di inattività prima che venga richiesta la password**.

### Profilo di posta elettronica
- **L'account di posta elettronica deve essere gestito da Intune:** se questa opzione è impostata su **Sì**, il dispositivo deve usare il profilo di posta elettronica distribuito al dispositivo stesso. Il dispositivo è considerato non conforme nelle seguenti situazioni:
  - Il profilo di posta elettronica deve essere distribuito anche al gruppo di utenti al quale appartiene l'utente oggetto della verifica di conformità; in caso contrario i dispositivi degli utenti verranno considerati non conformi.
  - Il dispositivo viene segnalato come non conforme se l'utente ha già configurato un account di posta elettronica nel dispositivo che corrisponde al profilo di posta elettronica di Intune distribuito al dispositivo stesso. Intune non può sovrascrivere il profilo con provisioning dell'utente, quindi non può gestirlo. Per garantire la conformità è necessario rimuovere le impostazioni di posta elettronica esistenti, quindi installare il profilo di posta elettronica gestito da Intune.


- **Selezionare il profilo di posta elettronica che deve essere gestito da Intune:**
   se è stata selezionata l'opzione **L'account di posta elettronica deve essere gestito da Intune**, scegliere **Seleziona** per specificare il profilo di posta elettronica di Intune. Il profilo di posta elettronica deve essere presente nel dispositivo.

     Per consultare dettagli sui profili di posta elettronica, vedere [Configure access to corporate email using email profiles with Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md) (Configurare l'accesso alla posta elettronica aziendale usando profili di posta elettronica con Microsoft Intune).

## Impostazioni dell'integrità dei dispositivi

- **Il dispositivo non deve essere jailbroken o rooted:** se si abilita questa impostazione, i dispositivi jailbroken non risultano conformi.

##  Proprietà dispositivo
- **Minimum OS required** (Versione minima richiesta del sistema operativo): quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, verrà segnalato come non conforme.
Viene visualizzato un collegamento a informazioni per eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e dopo l'aggiornamento potrà accedere alle risorse aziendali.

- **Maximum OS version allowed** (Versione massima consentita del sistema operativo): quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali risulterà bloccato e l'utente dovrà contattare l'amministratore IT. Fino a quando la regola non viene modificata in modo da consentire la versione del sistema operativo, non è possibile usare questo dispositivo per accedere alle risorse aziendali.


<!--HONumber=Jun16_HO2-->


