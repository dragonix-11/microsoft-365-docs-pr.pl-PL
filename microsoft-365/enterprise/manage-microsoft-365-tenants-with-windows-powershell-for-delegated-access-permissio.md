---
title: Zarządzanie dzierżawami Microsoft 365 przy użyciu Windows PowerShell dla partnerów dap
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: W tym artykule dowiesz się, jak zarządzać dzierżawami klientów za pomocą programu PowerShell dla Microsoft 365.
ms.openlocfilehash: 11869157a5ed106d1aea0a4ce0e21716be1cc78f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096793"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Zarządzanie dzierżawami Microsoft 365 przy użyciu Windows PowerShell dla partnerów z uprawnieniami dostępu delegowanego (DAP)

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Windows PowerShell umożliwia partnerom syndykacji i Dostawca rozwiązań w chmurze (CSP) łatwe administrowanie ustawieniami dzierżawy klientów, które nie są dostępne w Centrum administracyjne platformy Microsoft 365. Należy pamiętać, że uprawnienia administrowania w imieniu (AOBO) są wymagane, aby konto administratora partnera łączyło się z dzierżawami klientów.

Partnerami z uprawnieniami dostępu delegowanego (DAP) są partnerzy syndykacji i dostawcy rozwiązań w chmurze (CSP). Są one często sieci lub dostawców telekomunikacyjnych do innych firm. Łączą Microsoft 365 subskrypcje w swoje oferty usług dla swoich klientów. Gdy sprzedają subskrypcję Microsoft 365, automatycznie otrzymują uprawnienia administrowania w imieniu (AOBO) do dzierżaw klienta, aby mogli administrować dzierżawami klientów i raportować je.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

Procedury opisane w tym temacie wymagają nawiązania połączenia z [Połączenie w celu Microsoft 365 za pomocą programu PowerShell](connect-to-microsoft-365-powershell.md).

Potrzebne są również poświadczenia administratora dzierżawy partnera.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

### <a name="list-all-tenant-ids"></a>Wyświetlanie listy wszystkich identyfikatorów dzierżawy

> [!NOTE]
> Jeśli masz więcej niż 500 dzierżaw, należy określić zakres składni poleceń cmdlet za pomocą parametru  _-All_ lub _-MaxResultsParameter_. Dotyczy to innych poleceń cmdlet, które mogą dawać duże dane wyjściowe, takie jak **Get-MsolUser**.

Aby wyświetlić listę wszystkich identyfikatorów dzierżawy klienta, do których masz dostęp, uruchom to polecenie.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

Spowoduje to wyświetlenie listy wszystkich dzierżaw klientów według **identyfikatora TenantId**.

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Uzyskiwanie identyfikatora dzierżawy przy użyciu nazwy domeny

Aby uzyskać **identyfikator TenantId** dla określonej dzierżawy klienta według nazwy domeny, uruchom to polecenie. Zastąp _<domainname.onmicrosoft.com>_ rzeczywistą nazwą domeny żądanej dzierżawy klienta.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Wyświetlanie listy wszystkich domen dla dzierżawy

Aby uzyskać wszystkie domeny dla jednej dzierżawy klienta, uruchom to polecenie. Zastąp  _\<customer TenantId value>_ element wartością rzeczywistą.

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

Jeśli zarejestrowano dodatkowe domeny, spowoduje to zwrócenie wszystkich domen skojarzonych z **identyfikatorem TenantId** klienta.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Pobieranie mapowania wszystkich dzierżaw i zarejestrowanych domen

Poprzednie polecenia programu PowerShell dla Microsoft 365 pokazały, jak pobrać identyfikatory dzierżawy lub domeny, ale nie oba w tym samym czasie i bez wyraźnego mapowania między nimi wszystkimi. To polecenie generuje listę wszystkich identyfikatorów dzierżawy klienta i ich domen.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Pobieranie wszystkich użytkowników dla dzierżawy

Spowoduje to wyświetlenie **stanu UserPrincipalName**, **DisplayName** i **isLicensed** dla wszystkich użytkowników określonej dzierżawy. Zastąp _\<customer TenantId value>_ element wartością rzeczywistą.

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Uzyskiwanie wszystkich szczegółów dotyczących użytkownika

Jeśli chcesz wyświetlić wszystkie właściwości określonego użytkownika, uruchom to polecenie. Zastąp  _\<customer TenantId value>_ wartości i _\<user principal name value>_ wartościami rzeczywistymi.

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Dodawanie użytkowników, ustawianie opcji i przypisywanie licencji

Zbiorcze tworzenie, konfigurowanie i licencjonowanie użytkowników Microsoft 365 jest szczególnie wydajne przy użyciu programu PowerShell dla Microsoft 365. W tym dwuetapowym procesie najpierw utworzysz wpisy dla wszystkich użytkowników, których chcesz dodać w pliku wartości rozdzielanej przecinkami (CSV), a następnie zaimportujesz ten plik przy użyciu programu PowerShell dla Microsoft 365.

#### <a name="create-a-csv-file"></a>Tworzenie pliku CSV

Utwórz plik CSV przy użyciu następującego formatu:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

Gdzie:

- **UsageLocation**: wartość tego parametru to dwuliterowy kod kraju/regionu ISO użytkownika. Kody krajów/regionów można sprawdzić na platformie [przeglądania onlineISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Na przykład kod dla Stany Zjednoczone to USA, a kod dla Brazylii to BR.

- **LicenseAssignment**: ta wartość używa następującego formatu: `syndication-account:<PROVISIONING_ID>`. Jeśli na przykład przypisujesz użytkownikom dzierżawy klienta O365_Business_Premium licencji, wartość **LicenseAssignment** wygląda następująco: **syndication-account:O365_Business_Premium**. PROVISIONING_IDs znajdziesz w portalu syndykacji partnerów, do których masz dostęp jako partner syndykacji lub dostawcy CSP.

#### <a name="import-the-csv-file-and-create-the-users"></a>Importowanie pliku CSV i tworzenie użytkowników

Po utworzeniu pliku CSV uruchom to polecenie, aby utworzyć konta użytkowników z hasłami, które użytkownik musi zmienić podczas pierwszego logowania i które przypisują określoną licencję. Pamiętaj, aby zastąpić poprawną nazwę pliku CSV.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Zobacz też

[Pomoc dla partnerów](https://go.microsoft.com/fwlink/p/?LinkId=533477)
