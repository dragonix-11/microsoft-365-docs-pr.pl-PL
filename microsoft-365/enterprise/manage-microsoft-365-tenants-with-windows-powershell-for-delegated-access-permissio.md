---
title: Zarządzanie Microsoft 365 dzierżawami za pomocą Windows PowerShell daP
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: Z tego artykułu dowiesz się, jak za pomocą programu PowerShell dla Microsoft 365 zarządzać dziesiątami klientów.
ms.openlocfilehash: ff74cc0ec710996c66a659034f4fb4a49ee57ab1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977607"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Zarządzanie Microsoft 365 dostępu za pomocą Windows PowerShell dla partnerów dap (Delegated Access Permissions)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Windows PowerShell umożliwia partnerom programu Syndication i Dostawca rozwiązań w chmurze (CSP) łatwe administrowanie ustawieniami sprzedaży klientów i zgłaszanie ich w przypadku tych ustawień, które nie są dostępne w p centrum administracyjne platformy Microsoft 365. Zauważ, że aby konto administratora partnera nawiązyło połączenie z dziesiątami klientów, wymagane są uprawnienia administratora w imieniu klienta (AOBO).

Partnerzy w programie DaP (Delegated Access Permission) to partnerzy usług Syndication i Dostawcy rozwiązań w chmurze (CSP). Są często dostawcami sieci lub telekomunikacyjnych dla innych firm. Oferują one Microsoft 365 subskrypcji w swoje oferty usług dla swoich klientów. Gdy sprzeda subskrypcję usługi Microsoft 365, są mu automatycznie udzielane uprawnienia administrowania w imieniu klienta (AOBO), aby można było administrować tymi usługami i raportować na ich temat.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Procedury w tym temacie wymagają nawiązania połączenia z [programem Połączenie w Microsoft 365 programie PowerShell](connect-to-microsoft-365-powershell.md).

Potrzebne są również poświadczenia administratora dzierżawy partnerskiej.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

### <a name="list-all-tenant-ids"></a>Lista wszystkich identyfikatorów dzierżawy

> [!NOTE]
> Jeśli masz więcej niż 500 dzierżaw, zakres składni polecenia cmdlet za pomocą funkcji  _-All_ lub _-MaxResultsParameters_. Dotyczy to innych cmdlet, które mogą dać duże dane wyjściowe, takie jak **Get-MsolUser**.

Aby wyświetlić listę wszystkich identyfikatorów dzierżawy klienta, do których masz dostęp, uruchom to polecenie.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

Spowoduje to wyświetlenie listy wszystkich dzierżaw klientów według **dzierżawy TenantId**.

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Uzyskiwanie identyfikatora dzierżawy przy użyciu nazwy domeny

Aby uzyskać pole **TenantId** określonej dzierżawy klienta według nazwy domeny, uruchom to polecenie. Zastąp _<domainname.onmicrosoft.com>_ rzeczywistą nazwą domeny dzierżawy klienta, której chcesz użyć.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Lista wszystkich domen dla dzierżawy

Aby pobrać wszystkie domeny dla dowolnej dzierżawy klienta, uruchom to polecenie. Zamienianie  _\<customer TenantId value>_ na rzeczywistą wartość.

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

Jeśli zarejestrowano dodatkowe domeny, zostaną zwrócone wszystkie domeny skojarzone z polem **tenantId klienta**.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Uzyskiwanie mapowania wszystkich dzierżaw i zarejestrowanych domen

Poprzedni program PowerShell dla programu Microsoft 365 pokazuje sposób pobierania identyfikatorów lub domen dzierżawy, ale nie obu jednocześnie, oraz bez przejrzystego mapowania między nimi wszystkich. To polecenie generuje listę wszystkich identyfikatorów dzierżawy klienta i ich domen.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Pobierz wszystkich użytkowników dla dzierżawy

Spowoduje to wyświetlenie **wartości UserPrincipalName** (Nazwa użytkownika), **DisplayName** (Nazwa wyświetlana) i **isLicensed (JestLicencjonowana** ) dla wszystkich użytkowników w określonej dzierżawie. Zamienianie _\<customer TenantId value>_ na rzeczywistą wartość.

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Uzyskiwanie wszystkich szczegółowych informacji o użytkowniku

Aby wyświetlić wszystkie właściwości określonego użytkownika, uruchom to polecenie. Zamienianie  _\<customer TenantId value>_ i _\<user principal name value>_ zamienianie na wartości rzeczywiste.

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Dodawanie użytkowników, ustawianie opcji i przypisywanie licencji

Zbiorcze tworzenie, konfiguracja i licencjonowanie usług Microsoft 365 jest szczególnie efektywne dzięki użyciu programu PowerShell do Microsoft 365. W tym dwuetapowym procesie najpierw należy utworzyć wpisy dla wszystkich użytkowników, których chcesz dodać do pliku w formacie wartości rozdzielanych przecinkami (CSV), a następnie zaimportować ten plik przy użyciu programu PowerShell dla systemu Microsoft 365.

#### <a name="create-a-csv-file"></a>Tworzenie pliku CSV

Utwórz plik CSV, używając tego formatu:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

gdzie:

- **Lokalizacja użytkowania**: Wartość tego ustawienia to dwuliterowy kod ISO kraju/regionu użytkownika. Kody krajów i regionów można znaleźć na platformie przeglądania [onlineISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Na przykład kod dla Stanów Zjednoczonych to Stany Zjednoczone, a kod dla Brazylii to BR.

- **LicenseAssignment**: Wartość w tym formacie jest używana w tym formacie: `syndication-account:<PROVISIONING_ID>`. Jeśli na przykład przypisujesz użytkownikom dzierżawy klienta O365_Business_Premium licencji, wartość **LicenseAssignment** wygląda następująco: **syndication-account:O365_Business_Premium**. W portalu partnera programu Syndication znajdziesz PROVISIONING_IDs, do których masz dostęp jako partner programu Syndication lub partnera CSP.

#### <a name="import-the-csv-file-and-create-the-users"></a>Importowanie pliku CSV i tworzenie użytkowników

Po utworzeniu pliku CSV uruchom to polecenie, aby utworzyć konta użytkowników z nie wygasających hasłami, które użytkownik musi zmienić przy pierwszym loganiu i które przypisuje mu licencję podaną przez Ciebie. Pamiętaj, aby zastąpić właściwą nazwę pliku CSV.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Zobacz też

[Pomoc dla partnerów](https://go.microsoft.com/fwlink/p/?LinkId=533477)
