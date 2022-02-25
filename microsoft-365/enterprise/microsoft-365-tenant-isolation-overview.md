---
title: Izolacji dzierżawy w Microsoft 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Ten artykuł zawiera podsumowanie wymuszania izolacji dzierżawy przez firmę Microsoft w usługach w chmurze, takich jak Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b52d936bb00ac0adef0baf428cbc5f9a8f8aba49
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959262"
---
# <a name="tenant-isolation-in-microsoft-365"></a>Izolacji dzierżawy w Microsoft 365

Jedną z podstawowych zalet przetwarzania danych w chmurze jest pojęcie udostępnionej, wspólnej infrastruktury dla wielu klientów jednocześnie, prowadzącej do skalowania. To pojęcie jest nazywane *wielowątkową.* Firma Microsoft nieustannie pracuje nad zapewnieniem, że architektura wielu dzierżaw naszych usług w chmurze obsługuje standardy zabezpieczeń, poufności, prywatności, integralności i dostępności na poziomie przedsiębiorstwa.

Na podstawie znaczących inwestycji i doświadczeń zebranych z wiarygodnego przetwarzania danych i cyklu opracowywania zabezpieczeń usługi w chmurze firmy Microsoft opracowano przy [](https://www.microsoft.com/trust-center) założeniu[, że](https://www.microsoft.com/securityengineering/sdl/) wszystkie dzierżawy są potencjalnie hostowane we wszystkich innych dzierżawach. Zaimplementowano również środki zabezpieczeń, aby zapobiec wpływaniu akcji jednej dzierżawy na bezpieczeństwo lub usługi innej dzierżawy.  ani uzyskać dostępu do zawartości innej dzierżawy.

Dwa podstawowe cele utrzymania izolacji dzierżawy w środowisku wielodostępnym to:

1.    zapobieganie wyciekowi lub nieautoryzowanemu dostępowi do zawartości klientów w dzierżawach; i
2.    Zapobieganie negatywnym wpływowi akcji jednej dzierżawy na usługę dla innej dzierżawy

W całym okresie programu Microsoft 365 Microsoft 365 wdrożono wiele sposobów ochrony, aby uniemożliwić klientom naruszenie usług lub aplikacji albo uzyskanie nieautoryzowanego dostępu do informacji innych dzierżaw lub systemu Microsoft 365, w tym:

- Logiczna izolacji zawartości klienta w poszczególnych dzierżawach usług Microsoft 365 jest osiągana dzięki Azure Active Directory autoryzacji i kontroli dostępu opartej na rolach.
- SharePoint Online udostępnia mechanizmy izolacji danych na poziomie magazynu.
- Firma Microsoft stosuje rygorystyczne zabezpieczenia fizyczne, sprawdzanie tła oraz wielopoziomową strategię szyfrowania, aby chronić poufność i integralność zawartości klienta. Wszystkie Microsoft 365 danych mają kontrolki dostępu biometrycznego, przy użyciu których większość wydruków nadgarstków wymaga dostępu fizycznego. Ponadto wszyscy pracownicy firmy Microsoft w Stanach Zjednoczonych są zobowiązani do pomyślnego sprawdzenia standardowego tła w ramach procesu zatrudnienia. Aby uzyskać więcej informacji na temat kontrolek używanych na Microsoft 365 dostępu administracyjnego, zobacz Microsoft 365 [administracyjnych kontroli dostępu](/compliance/assurance/assurance-administrative-access-controls-overview).
- Microsoft 365 korzysta z technologii po stronie usługi, które szyfrują zawartość klienta w czasie spoczynku i podczas przesyłania, w tym funkcji BitLocker, szyfrowania według plików, protokołu TLS (Transport Layer Security) i IPsec (Internet Protocol Security). Aby uzyskać szczegółowe informacje na temat szyfrowania Microsoft 365, zobacz [Technologie szyfrowania](../compliance/office-365-encryption-in-the-microsoft-cloud-overview.md) danych w Microsoft 365.

Razem wymienione powyżej mechanizmy ochrony zapewniają zaawansowane, logiczne mechanizmy kontroli izolacji, które zapewniają ochronę przed zagrożeniami i ich ograniczanie odpowiada tylko w przypadku izolacji fizycznej.

## <a name="related-links"></a>Linki pokrewne

- [Isolation and Access Control in Azure Active Directory](microsoft-365-isolation-in-azure-active-directory.md)
- [Isolation dzierżawy w Office Graph i Delve](microsoft-365-isolation-in-graph-and-delve.md)
- [Isolation dzierżawy w Microsoft 365 wyszukiwania](microsoft-365-isolation-in-microsoft-365-search.md)
- [Limity zasobów](/compliance/assurance/assurance-resource-limits)
- [Monitorowanie i testowanie granic dzierżawy](/compliance/assurance/assurance-monitoring-and-testing)
- [Isolation and Access Control in Microsoft 365](microsoft-365-isolation-in-microsoft-365.md)