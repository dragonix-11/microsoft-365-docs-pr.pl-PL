---
title: Microsoft 365 kontroli izolacji
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
description: Dowiedz się, jak działają kontrolki izolacji Microsoft 365, pozwalając na współużytkowanie usług lub pozostawanie w miejscu w razie potrzeby.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 514b12e44d9e81a18b691ebf3196a3d21157e71b
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959263"
---
# <a name="microsoft-365-isolation-controls"></a>Microsoft 365 kontroli izolacji 

Firma Microsoft nieustannie pracuje nad zapewnieniem, że architektura wielodostępna oprogramowania Microsoft 365 obsługuje zabezpieczenia, poufność, prywatność, integralność, standardy lokalne, międzynarodowe i standardy [dotyczące dostępności na poziomie przedsiębiorstwa](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons). Skala i zakres usług oferowanych przez firmę Microsoft utrudnia zarządzanie problemami Microsoft 365 interakcjami ze strony użytkownika. Microsoft 365 usługi są udostępniane za pośrednictwem wielu globalnie rozproszonych centrów danych, z których każde jest wysoce zautomatyzowane i wymaga kontaktu z innymi użytkownikami albo dowolnego dostępu do zawartości klienta. Nasz personel obsługuje te usługi i centra danych przy użyciu automatycznych narzędzi i wysoce bezpiecznego dostępu zdalnego. 

Microsoft 365 składa się z wielu usług, które zapewniają istotne funkcje biznesowe i zapewniają cały proces Microsoft 365 biznesowego. Każda z tych usług jest samodzielna i została zaprojektowana pod kątem integracji ze sobą.

Microsoft 365 zaprojektowano z następującymi zasadami:

 - **[Architektura usługowa](/previous-versions/aa480021(v=msdn.10)):** projektowanie i opracowywanie oprogramowania w postaci usług współdziałania zapewniających dobrze zdefiniowane funkcje biznesowe.
 - **[Zapewnianie](https://www.microsoft.com/download/details.aspx?id=40872)** bezpieczeństwa operacyjnego: program, który wykorzystuje wiedzę uzyskaną dzięki różnym możliwościom [firmy Microsoft,](https://www.microsoft.com/sdl/default.aspx) w tym cyklowi opracowywania zabezpieczeń firmy Microsoft, Centrum reakcji firmy [Microsoft](https://technet.microsoft.com/library/dn440717.aspx) na zabezpieczenia oraz dogłębnej wiedzy na temat zagrożeń bezpieczeństwa i bezpieczeństwa.

Microsoft 365 usługi są ze sobą współzależne, ale są projektowane i implementowane w celu wdrażania i obsługiwania ich jako usługi wiadowe, niezależnie od siebie. Firma Microsoft oddziela obowiązki i obszary odpowiedzialności za Microsoft 365 w celu ograniczenia możliwości nieuprawnionej lub niezamierzonej modyfikacji lub niewłaściwego użycia zasobów organizacji. Microsoft 365 mają zdefiniowane role w ramach kompleksowego mechanizmu kontroli dostępu opartej na rolach.

## <a name="customer-content-isolation"></a>Izolacji zawartości klienta

Cała zawartość klienta w dzierżawie jest odizolowana od innych dzierżaw i od danych operacji i systemów używanych w zarządzaniu Microsoft 365. W całym programie wdrożono wiele Microsoft 365 ochrony, aby zminimalizować ryzyko naruszenia bezpieczeństwa Microsoft 365 usługi lub aplikacji. Ponadto wiele form ochrony uniemożliwia nieautoryzowany dostęp do informacji dzierżawcy lub samego systemu Microsoft 365 dzierżawy.

Aby uzyskać informacje o tym, jak firma Microsoft implementuje izolacji logiczne danych dzierżawy w Microsoft 365, zobacz Isolation [dzierżawy w Microsoft 365](microsoft-365-tenant-isolation-overview.md).