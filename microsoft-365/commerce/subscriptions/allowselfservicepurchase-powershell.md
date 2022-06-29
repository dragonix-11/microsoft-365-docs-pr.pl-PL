---
title: Użyj polecenia AllowSelfServicePurchase dla modułu MSCommerce programu PowerShell
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: ''
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
search.appverid:
- MET150
description: Dowiedz się, jak włączyć lub wyłączyć zakup samoobsługowy za pomocą polecenia cmdlet AllowSelfServicePurchase programu PowerShell.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 4/7/2022
ms.openlocfilehash: 7c9ac6a1e58049d188d4cd29441d8e0689f2c787
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530843"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Użyj polecenia AllowSelfServicePurchase dla modułu MSCommerce programu PowerShell

Moduł **MSCommerce** programu PowerShell jest teraz dostępny w [Galeria programu PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery). Moduł zawiera wartość parametru **PolicyID** dla **elementu AllowSelfServicePurchase** , która umożliwia kontrolowanie, czy użytkownicy w organizacji mogą dokonywać zakupów samoobsługowych.

Moduł **MSCommerce** PowerShell umożliwia:

- Wyświetl domyślny stan wartości parametru **AllowSelfServicePurchase** — niezależnie od tego, czy jest ona włączona, czy wyłączona
- Wyświetl listę odpowiednich produktów oraz informacje o tym, czy zakup samoobsługowy jest włączony, czy wyłączony
- Wyświetl lub zmodyfikuj bieżące ustawienie dla określonego produktu, aby je włączyć lub wyłączyć

## <a name="requirements"></a>Wymagania

Do korzystania z modułu **MSCommerce** programu PowerShell potrzebne są:

- Urządzenie Windows 10
- Program PowerShell 5 lub nośny. Obecnie program PowerShell 6.x/7.x nie jest obsługiwany w tym module.
- Uprawnienia administratora dla urządzenia
- Rola Administracja globalna lub Administracja rozliczeniowa dla dzierżawy

## <a name="install-the-mscommerce-powershell-module"></a>Instalowanie modułu MSCommerce programu PowerShell

Moduł **MSCommerce** programu PowerShell jest instalowany na urządzeniu Windows 10 raz, a następnie importowany do każdej uruchomionej sesji programu PowerShell. Pobierz moduł **MSCommerce** programu PowerShell z [Galeria programu PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery).

Aby zainstalować moduł **MSCommerce** Programu PowerShell za pomocą modułu **PowerShellGet**, uruchom następujące polecenie:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>Importowanie programu MSCommerce do sesji programu PowerShell

Po zainstalowaniu modułu na urządzeniu Windows 10 należy zaimportować go do każdej uruchomionej sesji programu PowerShell. Aby zaimportować go do sesji programu PowerShell, uruchom następujące polecenie:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Nawiązywanie połączenia z programem MSCommerce przy użyciu poświadczeń

Aby nawiązać połączenie z modułem programu PowerShell przy użyciu poświadczeń, uruchom następujące polecenie.

```powershell
Connect-MSCommerce
```

To polecenie łączy bieżącą sesję programu PowerShell z dzierżawą usługi Azure Active Directory. Polecenie wyświetli monit o podanie nazwy użytkownika i hasła dla dzierżawy, z którą chcesz nawiązać połączenie. Jeśli dla poświadczeń włączono uwierzytelnianie wieloskładnikowe, użyj opcji interaktywnej, aby się zalogować.

## <a name="view-details-for-allowselfservicepurchase"></a>Wyświetlanie szczegółów elementu AllowSelfServicePurchase

Aby wyświetlić opis wartości parametru **AllowSelfServicePurchase** i stanu domyślnego w oparciu o organizację, uruchom następujące polecenie:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Wyświetlanie listy produktów samoobsługowych i ich stanu

Aby wyświetlić listę wszystkich dostępnych produktów samoobsługowego zakupu i ich stan, uruchom następujące polecenie:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

W poniższej tabeli wymieniono dostępne produkty i ich **identyfikator ProductId**.

| Rezultat | Productid |
|-----------------------------|--------------|
| Usługa Power Apps na użytkownika* | CFQ7TTC0LH2H |
| Usługa Power Automate na użytkownika | CFQ7TTC0KP0N |
| Power Automate RPA | CFQ7TTC0KXG6  |
| Power BI Premium (autonomiczny) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project (plan 1)* | CFQ7TTC0HDB1 |
| Project (plan 3)* | CFQ7TTC0HDB0 |
| Visio (plan 1)* | CFQ7TTC0HD33 |
| Visio (plan 2)* | CFQ7TTC0HD32 |
| Windows 365 Enterprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows 365 Business z Korzyść użycia hybrydowego platformy Windows | CFQ7TTC0HX99 |
| Microsoft 365 F3 | CFQ7TTC0LH05 |

*Te identyfikatory uległy zmianie. Jeśli wcześniej zablokowano produkty przy użyciu starych identyfikatorów, są one automatycznie blokowane przy użyciu nowych identyfikatorów. Nie jest wymagana żadna dodatkowa praca.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Wyświetlanie lub ustawianie stanu opcji AllowSelfServicePurchase

Po wyświetleniu listy produktów dostępnych do zakupu samoobsługowego można wyświetlić lub zmodyfikować ustawienie dla określonego produktu.

Aby uzyskać ustawienie zasad dla określonego produktu, uruchom następujące polecenie:

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Aby włączyć ustawienie zasad dla określonego produktu, uruchom następujące polecenie:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

Aby wyłączyć ustawienie zasad dla określonego produktu, uruchom następujące polecenie:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>Przykładowy skrypt wyłączania funkcji AllowSelfServicePurchase

W poniższym przykładzie przedstawiono sposób importowania modułu **MSCommerce** , logowania się przy użyciu konta, uzyskiwania **identyfikatora ProductId** dla usługi Power Automate na użytkownika, a następnie wyłączania **opcji AllowSelfServicePurchase** dla tego produktu.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate per user'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

Jeśli istnieje wiele wartości dla produktu, możesz uruchomić polecenie indywidualnie dla każdej wartości, jak pokazano w poniższym przykładzie:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="problem"></a>Problem

Zostanie wyświetlony następujący komunikat o błędzie:

> HandleError: Nie można pobrać zasad o identyfikatorze PolicyId "AllowSelfServicePurchase", ErrorMessage — połączenie bazowe zostało zamknięte: wystąpił nieoczekiwany błąd podczas wysyłania.

Może to być spowodowane starszą wersją protokołu Transport Layer Security (TLS). Aby połączyć tę usługę, należy użyć protokołu TLS 1.2 lub nowszego

### <a name="solution"></a>Rozwiązanie

Uaktualnij do protokołu TLS 1.2. Poniższa składnia aktualizuje protokół zabezpieczeń ServicePointManager do protokołu TLS1.2:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

Aby dowiedzieć się więcej, zobacz [Jak włączyć protokół TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>Zawartość pokrewna

[Zarządzanie zakupami samoobsługowymi (Administracja)](manage-self-service-purchases-admins.md) (artykuł)

[Samoobsługowy zakup — często zadawane pytania](self-service-purchase-faq.yml) (artykuł)
