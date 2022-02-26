---
title: Używanie polecenia AllowSelfServicePurchase w module MS Commerce PowerShell
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
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
- AdminSurgePortfolio
- commerce_ssp
search.appverid:
- MET150
description: Dowiedz się, jak za pomocą polecenia cmdlet AllowSelfServicePurchase programu PowerShell włączyć lub wyłączyć zakup samoobsługowy.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 12/15/2021
ms.openlocfilehash: ebe01b9ed55b13d1d61ae1a59dca3bdb6373f285
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "62974147"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>Używanie polecenia AllowSelfServicePurchase w module MS Commerce PowerShell

Moduł **MS Commerce** PowerShell jest teraz dostępny w [galerii programu PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery). Moduł zawiera wartość **parametru PolicyID** dla **parametru AllowSelfServicePurchase** , która pozwala kontrolować, czy użytkownicy w organizacji mogą kupować samodzielnie.

Moduł **MS Commerce** PowerShell umożliwia:

- Wyświetlanie stanu domyślnego wartości **parametru AllowSelfServicePurchase** — niezależnie od tego, czy jest włączona, czy wyłączona
- Wyświetlanie listy produktów, które mają zastosowanie, i tego, czy zakup samoobsługowy został włączony, czy wyłączony
- Wyświetlanie lub modyfikowanie bieżącego ustawienia konkretnego produktu w celu jego włączenia lub wyłączenia

## <a name="requirements"></a>Wymagania

Aby korzystać z **modułu MS Commerce** PowerShell, potrzebujesz:

- Urządzenie Windows 10 urządzenia
- PowerShell 5 lub poniżej. Obecnie program PowerShell 6.x/7.x nie jest obsługiwany w tym module.
- Uprawnienia administratora urządzenia
- Rola administratora globalnego lub administratora rozliczeń dla dzierżawy

## <a name="install-the-mscommerce-powershell-module"></a>Instalowanie modułu MS Commerce PowerShell

Zainstaluj moduł **MS Commerce** PowerShell na urządzeniu Windows 10 raz, a następnie zaimportuj go do każdej sesji programu PowerShell, która zostanie uruchamiana. Pobierz moduł **MS Commerce** PowerShell z [Galerii programu PowerShell](https://aka.ms/allowselfservicepurchase-powershell-gallery).

Aby zainstalować moduł **MS Commerce** PowerShell z **programem PowerShellGet**, uruchom następujące polecenie:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>Importowanie pliku MS Commerce do sesji programu PowerShell

Po zainstalowaniu modułu na urządzeniu Windows 10 następnie zaimportuj go do każdej sesji programu PowerShell, która zostanie uruchamiana. Aby zaimportować ją do sesji programu PowerShell, uruchom następujące polecenie:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Połączenie do programu MS Commerce przy użyciu poświadczeń

Aby połączyć się z modułem programu PowerShell za pomocą poświadczeń, uruchom następujące polecenie.

```powershell
Connect-MSCommerce
```

To polecenie łączy bieżącą sesję programu PowerShell z dzierżawą Azure Active Directory dzierżawy. Polecenie monituje o nazwę użytkownika i hasło dzierżawy, z którą chcesz się połączyć. Jeśli dla twoich poświadczeń włączono uwierzytelnianie wieloskładnikowe, możesz użyć interakcyjnej opcji, aby się zalogować.

## <a name="view-details-for-allowselfservicepurchase"></a>Wyświetlanie szczegółów dla usługi AllowSelfServicePurchase

Aby wyświetlić opis wartości parametru **AllowSelfServicePurchase** i stanu domyślnego, zależnie od organizacji, uruchom następujące polecenie:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Wyświetlanie listy produktów kupowanych samodzielnie i ich stanu

Aby wyświetlić listę wszystkich dostępnych produktów do samodzielnego zakupu oraz stan każdego z nich, uruchom następujące polecenie:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

W poniższej tabeli wymieniono dostępne produkty i ich **productId**.

| Rezultat | ProductId |
|-----------------------------|--------------|
| Power Apps na użytkownika | CFQ7TTC0KP0P |
| Power Automate na użytkownika | CFQ7TTC0KP0N |
| Power Automate RPA | CFQ7TTC0KXG6  |
| Power BI Premium (autonomiczna) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project (plan 1)* | CFQ7TTC0HDB1 |
| Project (plan 3)* | CFQ7TTC0HDB0 |
| Visio (plan 1)* | CFQ7TTC0HD33 |
| Visio (plan 2)* | CFQ7TTC0HD32 |
| Windows 365 Enterprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows 365 Business z Windows hybrydowym | CFQ7TTC0HX99 |

*Te identyfikatory zostały zmienione. Jeśli wcześniej blokowano produkty używające starych identyfikatorów, są one automatycznie blokowane przy użyciu nowych identyfikatorów. Nie jest wymagana dodatkowa praca.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>Wyświetlanie lub ustawianie stanu dla usługi AllowSelfServicePurchase

Po wyświetleniu listy produktów dostępnych do zakupu samoobsługowego można wyświetlić lub zmodyfikować ustawienie określonego produktu.

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

## <a name="example-script-to-disable-allowselfservicepurchase"></a>Przykład skryptu umożliwiającego wyłączenie funkcji AllowSelfServicePurchase

W poniższym przykładzie przedstawiono sposób importowania modułu **MS Commerce**, logowania się przy użyciu konta, uzyskania produktu **ProductId** dla programu Power Automate, a następnie wyłączenia opcji **AllowSelfServicePurchase** dla tego produktu.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

Jeśli dla produktu istnieje wiele wartości, można uruchomić polecenie osobno dla każdej wartości, jak pokazano w poniższym przykładzie:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>Rozwiązywanie problemów

### <a name="problem"></a>Problem

Zostanie wyświetlony następujący komunikat o błędzie:

> HandleError: Nie można pobrać zasad przy użyciu wartości PolicyId 'AllowSelfServicePurchase', ErrorMessage — połączenie źródłowe zostało zamknięte: Wystąpił nieoczekiwany błąd podczas wysyłania.

Może to być spowodowane starszą wersją usługi Transport Layer Security (TLS). Aby połączyć tę usługę, musisz korzystać z usługi TLS 1.2 lub większej

### <a name="solution"></a>Rozwiązanie

Uaktualnij do wersji TLS 1.2. Następująca składnia aktualizuje protokół zabezpieczeń ServicePointManager na TLS1.2:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

Aby dowiedzieć się więcej, [zobacz Jak włączyć funkcję TLS 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>Zawartość pokrewna

[Zarządzanie zakupami samoobsługi (administrator)](manage-self-service-purchases-admins.md) (artykuł)

[Często zadawane pytania dotyczące zakupu samoobsługi](self-service-purchase-faq.yml) (artykuł)
