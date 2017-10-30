<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisiti delle credenziali di Azure AD e Intune

L'autenticazione e l'autorizzazione si basano sulle credenziali di Azure AD e sul controllo degli accessi in base al ruolo di Intune (RBAC). Tutti gli amministratori globali e gli amministratori del servizio Intune per il tenant hanno accesso al data warehouse per impostazione predefinita. Usare i ruoli di Intune per fornire accesso per più utenti, offrendo loro l'accesso alla **risorsa di creazione report**.

I requisiti per l'accesso al data warehouse di Intune (inclusa l'API) sono i seguenti:

  -  Licenza di Intune assegnata all'utente
  -  L'utente deve essere uno dei seguenti:
      -  Amministratore globale di Azure AD
      -  Amministratore del servizio Intune
      -  Utente con accesso basato sui ruoli alla risorsa **Report**