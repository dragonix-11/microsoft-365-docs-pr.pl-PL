---
title: Tocz lub obracaj klucz klienta lub klucz dostępności
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
description: Dowiedz się, jak rzucić klucze główne klienta przechowywane na platformie Azure Key Vault używane z kluczem klienta. Usługi obejmują pliki Exchange Online, Skype dla firm, SharePoint Online, OneDrive dla Firm i Teams.
ms.openlocfilehash: f34e79ee772df1a88058625c0b2df5f62413bcfd
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017339"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Tocz lub obracaj klucz klienta lub klucz dostępności

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!CAUTION]
> Klucz szyfrowania używany z kluczem klienta jest rzutowany tylko wtedy, gdy wymagania dotyczące zabezpieczeń lub zgodności wymagają wprowadzenia klucza. Ponadto nie usuwaj żadnych kluczy, które są lub były skojarzone z zasadami. Podczas przerzucania kluczy zawartość zostanie zaszyfrowana przy użyciu poprzednich kluczy. Na przykład aktywne skrzynki pocztowe będą często ponownie szyfrowane, nieaktywne, odłączone i wyłączone skrzynki pocztowe mogą nadal być szyfrowane przy użyciu poprzednich kluczy. SharePoint Online wykonuje kopie zapasowe zawartości na potrzeby przywracania i odzyskiwania, więc zawartość może nadal być archiwizowana przy użyciu starszych kluczy.

## <a name="about-rolling-the-availability-key"></a>Informacje o wprowadzaniu klucza dostępności

Firma Microsoft nie ujawnia klientom bezpośredniej kontroli nad kluczem dostępności. Na przykład możesz rzutować (obracać) tylko klucze, które należy do Ciebie w usłudze Azure Key Vault. Microsoft 365 rzutuje klucze dostępności zgodnie z harmonogramem zdefiniowanym wewnętrznie. Nie ma umowy dotyczącej poziomu usług (SLA) dla tych kluczowych rzutów. Microsoft 365 obraca klucz dostępności przy użyciu kodu usługi Microsoft 365 w zautomatyzowanym, nieręcznego procesie. Administratorzy firmy Microsoft mogą zainicjować proces rzutowania. Klucz jest wdrażany przy użyciu zautomatyzowanych mechanizmów bez bezpośredniego dostępu do magazynu kluczy. Dostęp do magazynu kluczy tajnych klucza dostępności nie jest aprowizowany dla administratorów firmy Microsoft. Stopniowe użycie klucza dostępności wykorzystuje ten sam mechanizm używany do początkowego generowania klucza. Aby uzyskać więcej informacji na temat klucza dostępności, zobacz [Omówienie klucza dostępności](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online i Skype dla firm klucze dostępności mogą być skutecznie wdrażane przez klientów tworzących nowy program DEP, ponieważ dla każdego utworzonego programu DEP jest generowany unikatowy klucz dostępności. Klucze dostępności dla plików SharePoint Online, OneDrive dla Firm i Teams istnieją na poziomie lasu i są współużytkowane przez dostawców USŁUG i klientów, co oznacza, że wdrażanie odbywa się tylko zgodnie z harmonogramem zdefiniowanym wewnętrznie przez firmę Microsoft. Aby zminimalizować ryzyko nieusunięć klucza dostępności przy każdym utworzeniu nowego programu DEP, SharePoint, OneDrive i Teams przerzucania klucza pośredniego dzierżawy (TIK), klucza opakowanego przez klucz główny klienta i klucz dostępności za każdym razem, gdy zostanie utworzony nowy program DEP.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Zażądaj nowej wersji każdego istniejącego klucza głównego, który chcesz wdrożyć

Podczas rzutowania klucza żądasz nowej wersji istniejącego klucza. Aby zażądać nowej wersji istniejącego klucza, należy użyć tego samego polecenia cmdlet [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) z tą samą składnią, której użyto do utworzenia klucza. Po zakończeniu wdrażania dowolnego klucza skojarzonego z zasadami szyfrowania danych (DEP) uruchom kolejne polecenie cmdlet, aby upewnić się, że klucz klienta zaczyna korzystać z nowego klucza. Wykonaj ten krok w każdej usłudze Azure Key Vault (AKV).

Przykład:

1. Zaloguj się do subskrypcji platformy Azure przy użyciu Azure PowerShell. Aby uzyskać instrukcje, zobacz [Logowanie za pomocą Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Uruchom polecenie cmdlet Add-AzKeyVaultKey, jak pokazano w poniższym przykładzie:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   W tym przykładzie ponieważ klucz o nazwie **Contoso-CK-EX-NA-VaultA1-Key001** istnieje w magazynie **Contoso-CK-EX-NA-VaultA1** , polecenie cmdlet tworzy nową wersję klucza. Ta operacja zachowuje poprzednie wersje klucza w historii wersji klucza. Do odszyfrowania danych, które są nadal szyfrowane, potrzebna jest poprzednia wersja klucza. Po zakończeniu wdrażania dowolnego klucza skojarzonego z programem DEP uruchom dodatkowe polecenie cmdlet, aby upewnić się, że klucz klienta zaczyna używać nowego klucza. W poniższych sekcjach opisano polecenia cmdlet bardziej szczegółowo.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Aktualizowanie kluczy dla depsów z wieloma obciążeniami

Po wdrożeniu jednego z kluczy usługi Azure Key Vault skojarzonych z programem DEP używanym z wieloma obciążeniami należy zaktualizować program DEP, aby wskazywał nowy klucz. Ten proces nie powoduje rotacji klucza dostępności.

Aby poinstruować klienta, aby używał nowego klucza do szyfrowania wielu obciążeń, wykonaj następujące kroki:

1. Na komputerze lokalnym, używając konta służbowego z uprawnieniami administratora globalnego lub administratora zgodności w organizacji, [połącz się z programem Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Uruchom polecenie cmdlet Set-M365DataAtRestEncryptionPolicy.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Gdzie *PolicyName* jest nazwą lub unikatowym identyfikatorem zasad. Na przykład Contoso_Global.

Przykład:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>Aktualizowanie kluczy dla Exchange Online adresów DEPs

Po wdrożeniu jednego z kluczy usługi Azure Key Vault skojarzonych z programem DEP używanym z Exchange Online i Skype dla firm należy zaktualizować program DEP, aby wskazywał nowy klucz. Nie powoduje to rotacji klucza dostępności.

Aby poinstruować klienta, aby używał nowego klucza do szyfrowania skrzynek pocztowych, uruchom polecenie cmdlet Set-DataEncryptionPolicy w następujący sposób:

1. Uruchom polecenie cmdlet Set-DataEncryptionPolicy w Azure PowerShell:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Aby sprawdzić wartość właściwości DataEncryptionPolicyID dla skrzynki pocztowej, wykonaj kroki opisane w [artykule Określanie programu DEP przypisanego do skrzynki pocztowej](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). Wartość tej właściwości zmienia się, gdy usługa zastosuje zaktualizowany klucz.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Aktualizowanie kluczy dla plików SharePoint Online, OneDrive dla Firm i Teams

SharePoint Online umożliwia przerzucenie tylko jednego klucza naraz. Jeśli chcesz rzucić oba klucze w magazynie kluczy, poczekaj na ukończenie pierwszej operacji. Firma Microsoft zaleca rozłożenie operacji w celu uniknięcia tego problemu. Po wdrożeniu jednego z kluczy usługi Azure Key Vault skojarzonych z programem DEP używanym z usługą SharePoint Online i OneDrive dla Firm należy zaktualizować program DEP, aby wskazywał nowy klucz. Nie powoduje to rotacji klucza dostępności.

1. Uruchom polecenie cmdlet Update-SPODataEncryptionPolicy w następujący sposób:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Mimo że to polecenie cmdlet uruchamia operację rzutowania kluczy dla SharePoint Online i OneDrive dla Firm, akcja nie kończy się natychmiast.

2. Aby wyświetlić postęp operacji rzutowania kluczy, uruchom polecenie cmdlet Get-SPODataEncryptionPolicy w następujący sposób:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>Powiązane artykuły:

- [Szyfrowanie usługi przy użyciu klucza klienta](customer-key-overview.md)

- [Konfigurowanie klucza klienta](customer-key-set-up.md)

- [Zarządzanie kluczem klienta](customer-key-manage.md)

- [Dowiedz się więcej o kluczu dostępności](customer-key-availability-key-understand.md)
