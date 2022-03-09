---
title: Konfigurowanie Microsoft 365 multi-Geo eDiscovery
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
description: Dowiedz się, jak za pomocą parametru Region skonfigurować zbierania elektronicznych materiałów dowodowych do użycia w lokalizacjach satelitarnych Microsoft 365 wielu lokalizacji geograficznych.
ms.openlocfilehash: b0366470984abbdc0ed0b3e407ca8ef6b5a5743f
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400940"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Microsoft 365 multi-Geo eDiscovery configuration

[Advanced eDiscovery](../compliance/overview-ediscovery-20.md) umożliwiają administratorowi zbierania elektronicznych materiałów dowodowych z wieloma lokalizacjami geograficznymi przeszukiwanie wszystkich lokalizacji geograficznych bez konieczności korzystania z filtru zabezpieczeń "Region". Dane są eksportowane do wystąpienia platformy Azure, która jest centralną lokalizacją dzierżawy wielowymiarowej. To samo dzieje się w przypadku stosowania wstrzymywania w statystyce, jednak statystyka wstrzymywania wewnątrz trzymania nie będzie wyświetlana bez filtru zabezpieczeń "Region". Statystyki dotyczące hold'a pokazujące 0 nie oznacza, że zawiedzienie zakończyło się niepowodzeniem, o ile jest on pokazywany jako Wł. (pomyślnie).

Bez zaawansowanych funkcji zbierania elektronicznych materiałów dowodowych menedżer zbierania elektronicznych materiałów dowodowych lub administrator dzierżawy wielodostępowej będzie mógł przeprowadzać zbierania elektronicznych materiałów dowodowych tylko w lokalizacji centralnej tej dzierżawy. W celu zapewnienia obsługi możliwości zbierania elektronicznych materiałów dowodowych dla lokalizacji satelitarnych za pośrednictwem programu PowerShell dostępny jest nowy parametr filtru zabezpieczeń zgodności o nazwie "Region". Ten parametr może być używany przez dzierżawców, których lokalizacja centralna znajduje się w Ameryce Północnej, Europie lub Azji i Pacyfiku. Advanced eDiscovery jest zalecane dla dzierżawców, których lokalizacja centralna nie znajduje się w Ameryce Północnej, Europie ani Azji i Pacyfiku i którzy muszą przeprowadzać zbierania elektronicznych materiałów dowodowych w lokalizacji geolokalizacji satelitarnych. 

Administrator globalny usługi Microsoft 365 musi przypisać uprawnienia Menedżera zbierania elektronicznych materiałów dowodowych w celu umożliwienia innym osobom wykonywania zbierania elektronicznych materiałów dowodowych i przypisania parametru "Region" w obowiązującym filtrze zabezpieczeń zgodności w celu określenia regionu przeprowadzania zbierania elektronicznych materiałów dowodowych jako lokalizacji satelitarnej. W przeciwnym razie nie zostanie przeprowadzone zbierania elektronicznych materiałów dowodowych w lokalizacji satelitarnej. Obsługiwany jest tylko jeden filtr zabezpieczeń "Region" na użytkownika, więc wszystkie regiony muszą być wewnątrz tego samego filtru zabezpieczeń.

Gdy dla określonej lokalizacji satelitarnej zostanie ustawiona rola Menedżer zbierania elektronicznych materiałów dowodowych lub Administrator, menedżer zbierania elektronicznych materiałów dowodowych lub administrator będzie mógł wykonywać akcje wyszukiwania zbierania elektronicznych materiałów dowodowych tylko w witrynach SharePoint i witrynach programu OneDrive znajdujących się w tej lokalizacji satelitarnej. Jeśli Menedżer zbierania elektronicznych materiałów dowodowych lub administrator spróbuje przeszukać witryny SharePoint lub OneDrive poza określoną lokalizacją satelitarną, żadne wyniki nie zostaną zwrócone. Ponadto gdy Menedżer zbierania elektronicznych materiałów dowodowych lub administrator lokalizacji satelitarnej wyzwala eksport, dane są eksportowane do wystąpienia platformy Azure tego regionu. Ułatwia to organizacjom zachowanie zgodności, nie zezwalając na eksportowanie zawartości przez kontrolowane obramowanie.

> [!NOTE]
> Jeśli menedżer zbierania elektronicznych materiałów dowodowych musi przeszukiwać wiele lokalizacji satelitarnych programu SharePoint, dla Menedżera zbierania elektronicznych materiałów dowodowych musi zostać utworzone inne konto użytkownika, które określa alternatywną lokalizację satelitarną, w której znajdują się witryny programu OneDrive lub SharePoint.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Aby ustawić filtr zabezpieczeń zgodności dla regionu:

1. [Połączenie do Microsoft 365 centrum & zgodności w programie PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. Należy stosować następującą składnię:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Przykład:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Dodatkowe parametry i składnię można znaleźć w artykule [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) .
