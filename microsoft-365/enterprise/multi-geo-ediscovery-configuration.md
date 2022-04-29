---
title: Konfigurowanie zbierania elektronicznych materiałów dowodowych Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
ms.collection: Strat_SP_gtc
description: Dowiedz się, jak za pomocą parametru Region skonfigurować funkcję zbierania elektronicznych materiałów dowodowych do użycia w lokalizacjach satelitarnych w Microsoft 365 Multi-Geo.
ms.openlocfilehash: a220e68e6dbe010f2eab6876dc2813dcd84d5d6d
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130938"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 konfiguracji zbierania elektronicznych materiałów dowodowych

[Funkcje zbierania elektronicznych materiałów dowodowych (Premium)](../compliance/overview-ediscovery-20.md) umożliwiają administratorowi zbierania elektronicznych elektronicznych materiałów dowodowych przeszukiwanie wszystkich obszarów geograficznych bez konieczności używania filtru zabezpieczeń "Region". Dane są eksportowane do wystąpienia platformy Azure centralnej lokalizacji dzierżawy z wieloma lokalizacjami geograficznymi.

Bez możliwości zbierania elektronicznych materiałów dowodowych (Premium) menedżer zbierania elektronicznych materiałów dowodowych lub administrator dzierżawy z wieloma obszarami geograficznymi będzie mógł przeprowadzać zbierania elektronicznych materiałów dowodowych tylko w centralnej lokalizacji tej dzierżawy. Aby obsługiwać możliwość przeprowadzania zbierania elektronicznych materiałów dowodowych dla lokalizacji satelitarnych, nowy parametr filtru zabezpieczeń zgodności o nazwie "Region" jest dostępny za pośrednictwem programu PowerShell. Ten parametr może być używany przez dzierżawców, których centralna lokalizacja znajduje się w Ameryka Północna, Europie lub Regionie Azji i Pacyfiku. eDiscovery (Premium) jest zalecane dla dzierżawców, których centralna lokalizacja nie znajduje się w Ameryka Północna, Europie lub Regionie Azji i Pacyfiku i którzy muszą wykonywać zbierania elektronicznych materiałów dowodowych w lokalizacjach geograficznych satelitów.

Administrator globalny Microsoft 365 musi przypisać uprawnienia menedżera zbierania elektronicznych materiałów dowodowych, aby umożliwić innym osobom wykonywanie zbierania elektronicznych materiałów dowodowych i przypisać parametr "Region" w odpowiednim filtrze zabezpieczeń zgodności w celu określenia regionu do przeprowadzania zbierania elektronicznych materiałów dowodowych jako lokalizacji satelitarnej, w przeciwnym razie nie zostanie przeprowadzone żadne zbierania elektronicznych materiałów dowodowych dla lokalizacji satelitarnej. Obsługiwany jest tylko jeden filtr zabezpieczeń "Region" na użytkownika, więc wszystkie regiony muszą znajdować się w tym samym filtrze zabezpieczeń.

Gdy dla określonej lokalizacji satelitarnej ustawiono rolę Menedżera zbierania elektronicznych materiałów dowodowych lub administratora, menedżer zbierania elektronicznych materiałów dowodowych lub administrator będzie mógł wykonywać tylko akcje wyszukiwania zbierania elektronicznych materiałów dowodowych względem witryn SharePoint i OneDrive lokacji znajdujących się w tej lokalizacji satelitarnej. Jeśli menedżer zbierania elektronicznych materiałów dowodowych lub administrator podejmie próbę wyszukania SharePoint lub OneDrive lokacji poza określoną lokalizacją satelitarną, żadne wyniki nie zostaną zwrócone. Ponadto gdy menedżer zbierania elektronicznych materiałów dowodowych lub administrator lokalizacji satelitarnej wyzwala eksport, dane są eksportowane do wystąpienia platformy Azure w tym regionie. Pomaga to organizacjom zachować zgodność, nie zezwalając na eksportowanie zawartości przez kontrolowane granice.

> [!NOTE]
> Jeśli menedżer zbierania elektronicznych materiałów dowodowych musi przeszukiwać wiele SharePoint lokalizacji satelitarnych, konieczne będzie utworzenie innego konta użytkownika dla Menedżera zbierania elektronicznych materiałów dowodowych, który określa alternatywną lokalizację satelitarną, w której znajdują się OneDrive lub SharePoint lokacje.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Aby ustawić filtr zabezpieczeń zgodności dla regionu:

1. [Połączenie do programu PowerShell Microsoft 365 Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell)

2. Należy stosować następującą składnię:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Przykład:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Zobacz artykuł [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) , aby uzyskać dodatkowe parametry i składnię.
