---
title: Obracanie lub obracanie klucza klienta lub klucza dostępności
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak roll the customer root keys stored in Azure Key Vault that are used with the Customer Key. Usługi obejmują Exchange Online, Skype dla firm, SharePoint Online, OneDrive dla Firm i Teams plików.
ms.openlocfilehash: 5f2de108d493e4b6d4233f4a932a24f524e468bb
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998974"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Obracanie lub obracanie klucza klienta lub klucza dostępności

> [!CAUTION]
> Klucz szyfrowania używaj z kluczem klienta tylko wtedy, gdy twoje wymagania dotyczące zabezpieczeń lub zgodności określają, że musisz go zbędnieć. Ponadto nie usuwaj żadnych kluczy, które są lub były skojarzone z zasadami. Po przywłaceni klawiszy zawartość będzie szyfrowana za pomocą poprzednich klawiszy. Na przykład aktywne skrzynki pocztowe będą często szyfrowane, nieaktywne, rozłączone i wyłączone, a także nadal będą szyfrowane przy użyciu poprzednich kluczy. SharePoint Online wykonuje kopię zapasową zawartości na potrzeby przywracania i odzyskiwania, więc zawartość nadal może być archiwizowana przy użyciu starszych kluczy.

## <a name="about-rolling-the-availability-key"></a>Informacje o wycofywaniu klucza dostępności

Firma Microsoft nie udostępnia klientom bezpośredniej kontroli nad kluczem dostępności. Na przykład możesz wyłącznie obracać (obracać) klucze, których jesteś właścicielem w magazynie kluczy platformy Azure. Microsoft 365 klucze dostępności w zdefiniowanym wewnętrznej harmonogramie. Dla tych kluczowych rzutów nie ma żadnej umowy dotyczącej poziomu usług dla klientów. Microsoft 365 klucza dostępności przy użyciu Microsoft 365 usługi w zautomatyzowanym, nie ręcznym procesie. Administratorzy firmy Microsoft mogą zainicjować proces wycofywania. Klucz jest rzutowany za pomocą automatycznych mechanizmów bez bezpośredniego dostępu do magazynu kluczy. Dostęp do magazynu tajnego klucza dostępności nie jest zapewniany administratorom firmy Microsoft. Klucz dostępności jest używany w tym samym mechanizmie, który został użyty do wstępnego wygenerowania klucza. Aby uzyskać więcej informacji o kluczu dostępności, zobacz [Opis klucza dostępności](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online i Skype dla firm dostępności mogą być w praktyce rzutowane przez klientów tworzących nowy element DEP, ponieważ dla każdego funkcji DEP, który tworzysz, jest generowany unikatowy klucz dostępności. Klucze dostępności dla plików usług SharePoint Online, OneDrive dla Firm i Teams istnieją na poziomie lasu i są współużytkowanie między deps i klientami, co oznacza, że rolling odbywa się tylko w zdefiniowanym wewnętrznie harmonogramie firmy Microsoft. Aby zminimalizować ryzyko niewdajania klucza dostępności przy każdym utworzeniu nowego funkcji DEP, funkcje SharePoint, OneDrive i Teams roll klucz pośredni dzierżawy (TIK), klucz zawijany przez klucze główne klienta i klucz dostępności przy każdym utworzeniu nowego funkcji DEP.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Żądanie nowej wersji każdego istniejącego klucza głównego, który chcesz zsuną

Podczas rzutowania klucza żądasz nowej wersji istniejącego klucza. Aby zażądać nowej wersji istniejącego klucza, użyj tego samego polecenia cmdlet [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey), o takiej samej składni jak podczas tworzenia klucza. Po zakończeniu wycofywania dowolnego klucza skojarzonego z zasadami szyfrowania danych (DEP, Data Encryption Policy) uruchom kolejne polecenie cmdlet, aby upewnić się, że klucz klienta zaczyna używać nowego klucza. Wykonaj ten krok w każdym magazynie kluczy platformy Azure (AKV).

Przykład:

1. Zaloguj się do subskrypcji platformy Azure za pomocą aplikacji Azure PowerShell. Aby uzyskać instrukcje, [zobacz Logowanie się za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Uruchom Add-AzKeyVaultKey cmdlet, jak pokazano w poniższym przykładzie:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   W tym przykładzie, ponieważ klucz o nazwie **Contoso-CK-EX-NA-VaultA1-Key001** istnieje w magazynie **Contoso-CK-EX-NA-VaultA1** , polecenie cmdlet tworzy nową wersję klucza. Ta operacja zachowuje poprzednie wersje klucza w historii wersji klucza. Poprzednia wersja klucza jest potrzebna do odszyfrowania danych, które nadal szyfruje. Po zakończeniu wycofywania dowolnego klucza skojarzonego z funkcjami DEP uruchom dodatkowe polecenie cmdlet, aby upewnić się, że klucz klienta zacznie używać nowego klucza. W poniższych sekcjach bardziej szczegółowo opisano polecenia cmdlet.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Aktualizowanie kluczy dla deps z wieloma obciążeniami pracą

Podczas wycofywania jednego z kluczy magazynu kluczy platformy Azure skojarzonego z usługą DEP używaną z wieloma obciążeniami pracą należy zaktualizować tę usługę, aby wskazać nowy klucz. Ten proces nie powoduje obrócenia klucza dostępności.

Aby poinstruować klucz klienta, aby użyć nowego klucza do szyfrowania wielu obciążeń, wykonaj następujące czynności:

1. Na komputerze lokalnym, używając konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji, połącz się z programem [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) w oknie Windows PowerShell.

2. Uruchom Set-M365DataAtRestEncryptionPolicy cmdlet.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Gdzie *nazwa_* zasad to nazwa lub unikatowy identyfikator zasad. Na przykład: Contoso_Global.

Przykład:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>Aktualizowanie klawiszy dla Exchange Online IP

Podczas rzutowania jednego z kluczy magazynu kluczy platformy Azure skojarzonego z funkcjami DEP używanymi z usługą Exchange Online i Skype dla firm należy zaktualizować usługę DEP, aby wskazać nowy klucz. Klucz dostępności nie zostanie obrócony.

Aby poinstruować klucz klienta, aby używać nowego klucza do szyfrowania skrzynek pocztowych, uruchom Set-DataEncryptionPolicy cmdlet w następujący sposób:

1. Uruchom polecenie cmdlet Set-DataEncryptionPolicy w programie Azure PowerShell:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Aby sprawdzić wartość właściwości DataEncryptionPolicyID skrzynki pocztowej, skorzystaj z procedury opisanej w tece Określanie funkcji [DEP przypisanej do skrzynki pocztowej](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). Wartość tej właściwości zmienia się, gdy usługa stosuje zaktualizowany klucz.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Aktualizowanie klawiszy dla plików SharePoint online, OneDrive dla Firm i Teams internetowych

SharePoint online umożliwia tylko rzutnie jednego klucza na raz. Jeśli chcesz roll both keys in a key vault, wait for the first operation to complete. Firma Microsoft zaleca, aby zrównać operacje w celu uniknięcia tego problemu. Po wycofaniu jednego z kluczy magazynu kluczy platformy Azure skojarzonego z funkcjami DEP używanymi z usługą SharePoint Online i usługą OneDrive dla Firm musisz zaktualizować funkcje DEP, aby wskazać nowy klucz. Klucz dostępności nie zostanie obrócony.

1. Uruchom następujące Update-SPODataEncryptionPolicy cmdlet:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   To polecenie cmdlet uruchamia operację roll klucza dla usługi SharePoint Online i OneDrive dla Firm, ale akcja nie zostanie ukończona natychmiast.

2. Aby wyświetlić postęp operacji zb. klucz, uruchom polecenie cmdlet Get-SPODataEncryptionPolicy w następujący sposób:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>Artykuły pokrewne

- [Szyfrowanie usługi przy użyciu klucza klienta dla Office 365](customer-key-overview.md)

- [Konfigurowanie klucza klienta dla Office 365](customer-key-set-up.md)

- [Zarządzanie kluczem klienta dla Office 365](customer-key-manage.md)

- [Informacje o kluczu dostępności](customer-key-availability-key-understand.md)
