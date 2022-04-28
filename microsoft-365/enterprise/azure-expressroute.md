---
title: Usługa Azure ExpressRoute dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Dowiedz się, jak korzystać z usługi Azure ExpressRoute z Office 365 i planować projekt implementacji sieci, jeśli wdrażasz go za jego pomocą.
ms.openlocfilehash: bbb53913ede8a51d5e6d9bf6e39386cd3e8de304
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096859"
---
# <a name="azure-expressroute-for-office-365"></a>Usługa Azure ExpressRoute dla Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Dowiedz się, jak usługa Azure ExpressRoute jest używana z usługą Office 365 i jak zaplanować projekt implementacji sieci, który będzie wymagany w przypadku wdrażania usługi Azure ExpressRoute do użycia z Office 365. Infrastruktura i usługi platformy działające na platformie Azure często przynoszą korzyści, odnosząc się do architektury sieci i kwestii związanych z wydajnością. W takich przypadkach zalecamy korzystanie z usługi ExpressRoute dla platformy Azure. Oferty oprogramowania jako usługi, takie jak Office 365 i Dynamics 365, zostały utworzone w celu bezpiecznego i niezawodnego uzyskiwania dostępu za pośrednictwem Internetu. Informacje o wydajności i zabezpieczeniach Internetu oraz o tym, kiedy warto rozważyć usługę Azure ExpressRoute dla Office 365, można przeczytać w artykule [Ocena łączności sieciowej Office 365](assessing-network-connectivity.md).

> [!NOTE]
> Ochrona punktu końcowego w usłudze Microsoft Defender nie zapewnia integracji z usługą Azure ExpressRoute. Nie uniemożliwia to klientom definiowania reguł usługi ExpressRoute, które umożliwiają łączność z sieci prywatnej w celu Ochrona punktu końcowego w usłudze Microsoft Defender usług w chmurze, jednak utrzymanie reguł w miarę rozwoju infrastruktury usługi lub chmury zależy od klienta.

> [!NOTE]
> Nie zalecamy usługi ExpressRoute dla Microsoft 365, ponieważ w większości przypadków nie zapewnia ona najlepszego modelu łączności dla usługi. W związku z tym autoryzacja firmy Microsoft jest wymagana do używania tego modelu łączności dla Microsoft 365. Przeglądamy każde żądanie klienta i autoryzujemy usługę ExpressRoute pod kątem Microsoft 365 tylko w rzadkich scenariuszach, w których jest to konieczne. Przeczytaj [przewodnik expressroute for Microsoft 365](https://aka.ms/erguide), aby uzyskać więcej informacji i po kompleksowym przeglądzie dokumentu z zespołami ds. produktywności, sieci i zabezpieczeń, skontaktuj się z zespołem ds. konta Microsoft, aby w razie potrzeby przesłać wyjątek. Nieautoryzowane subskrypcje próbujące utworzyć filtry tras dla Office 365 otrzymają [komunikat o błędzie](https://support.microsoft.com/kb/3181709).

## <a name="planning-azure-expressroute-for-office-365"></a>Planowanie usługi Azure ExpressRoute dla Office 365

Oprócz łączności z Internetem możesz wybrać trasę podzestawu ruchu sieciowego Office 365 za pośrednictwem bezpośredniego połączenia, które oferuje przewidywalność i 99,95% umowy SLA czasu pracy dla składników sieci firmy Microsoft. Usługa Azure ExpressRoute zapewnia to dedykowane połączenie sieciowe z Office 365 i innymi usługami firmy Microsoft w chmurze.

Niezależnie od tego, czy masz istniejącą sieć WAN protokołu MPLS, usługę ExpressRoute można dodać do architektury sieci na jeden z trzech sposobów. za pośrednictwem obsługiwanego dostawcy lokalizacji współlokalizatora wymiany w chmurze, dostawcy połączenia punkt-punkt ethernet lub dostawcy połączenia MPLS. Zobacz, którzy [dostawcy są dostępni w Twoim regionie](/azure/expressroute/expressroute-locations). Bezpośrednie połączenie usługi ExpressRoute umożliwi łączność z aplikacjami opisanymi w artykule [Jakie usługi Office 365 są uwzględnione poniżej?](azure-expressroute.md#BKMK_WhatDoIGet) Ruch sieciowy dla wszystkich innych aplikacji i usług będzie nadal przechodził przez Internet.

Rozważmy poniższy diagram sieci wysokiego poziomu, który przedstawia typowy Office 365 klienta łączącego się z centrami danych firmy Microsoft przez Internet w celu uzyskania dostępu do wszystkich aplikacji firmy Microsoft, takich jak Office 365, Windows Update i TechNet. Klienci korzystają z podobnej ścieżki sieciowej niezależnie od tego, czy nawiązują połączenie z sieci lokalnej, czy z niezależnego połączenia internetowego.

![Office 365 łączności sieciowej.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Teraz przyjrzyj się zaktualizowanemu diagramowi przedstawiającemu Office 365 klienta, który łączy się z Office 365 przy użyciu Internetu i usługi ExpressRoute. Zwróć uwagę, że niektóre połączenia, takie jak publiczny system DNS i węzły Content Delivery Network, nadal wymagają publicznego połączenia z Internetem. Zwróć również uwagę, że użytkownicy klienta, którzy nie znajdują się w połączonym budynku usługi ExpressRoute, łączą się przez Internet.

![Office 365 łączności z usługą ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Nadal chcesz uzyskać więcej informacji? Dowiedz się, jak [zarządzać ruchem sieciowym za pomocą usługi Azure ExpressRoute dla Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) i dowiedz się, jak [skonfigurować usługę Azure ExpressRoute dla Office 365](/azure/expressroute/expressroute-faqs). Nagraliśmy również 10-częściową serię [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) w kanale Channel 9, aby dokładniej wyjaśnić pojęcia.

## <a name="what-office-365-services-are-included"></a>Jakie usługi Office 365 są wliczone w cenę?
<a name="BKMK_WhatDoIGet"> </a>

W poniższej tabeli wymieniono usługi Office 365 obsługiwane przez usługę ExpressRoute. Zapoznaj się z [artykułem Office 365 punktów końcowych](./urls-and-ip-address-ranges.md), aby dowiedzieć się, które żądania sieciowe dla tych aplikacji wymagają łączności z Internetem.

| Dołączone aplikacje |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype dla firm <sup>Online1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint <sup>Online1</sup> <br/> OneDrive dla Firm <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|Portal i <sup>udostępnione1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Połączenie <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> Każda z tych aplikacji ma wymagania dotyczące łączności z Internetem, które nie są obsługiwane za pośrednictwem usługi ExpressRoute, zobacz [artykuł Office 365 punktów końcowych](./urls-and-ip-address-ranges.md), aby uzyskać więcej informacji.

Usługi, które nie są dołączone do usługi ExpressRoute dla Office 365, są Aplikacje Microsoft 365 dla przedsiębiorstw pobierania przez klienta, logowania lokalnego dostawcy tożsamości i usługi Office 365 (obsługiwanej przez 21 Vianet) w Chinach.

## <a name="implementing-expressroute-for-office-365"></a>Implementowanie usługi ExpressRoute dla Office 365

Implementacja usługi ExpressRoute wymaga zaangażowania właścicieli sieci i aplikacji i wymaga starannego planowania w celu określenia nowej [architektury routingu sieciowego](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), wymagań dotyczących przepustowości, gdzie zostaną zaimplementowane zabezpieczenia, wysokiej dostępności itd. Aby zaimplementować usługę ExpressRoute, należy wykonać następujące czynności:

1. W pełni zrozum potrzebę, aby usługa ExpressRoute spełniała wymagania planowania łączności Office 365. Dowiedz się, jakie aplikacje będą korzystać z Internetu lub usługi ExpressRoute, i w pełni zaplanuj wymagania dotyczące pojemności sieci, zabezpieczeń i wysokiej dostępności w kontekście korzystania z Internetu i usługi ExpressRoute dla ruchu Office 365.

2. Określanie lokalizacji ruchu wychodzącego i komunikacji równorzędnej dla ruchu internetowego<sup></sup> i usługi ExpressRoute1.

3. Określ pojemność wymaganą przez Internet i połączenia usługi ExpressRoute.

4. Masz plan wdrożenia zabezpieczeń i innych standardowych kontrolek <sup>obwodowych1</sup>.

5. Masz prawidłowe konto Microsoft Azure, aby subskrybować usługę ExpressRoute.

6. Wybierz model łączności i [zatwierdzonego dostawcę](/azure/expressroute/expressroute-locations). Należy pamiętać, że klienci mogą wybrać wiele modeli łączności lub partnerów, a partner nie musi być taki sam jak istniejący dostawca sieci.

7. Zweryfikuj wdrożenie przed przekierowaniem ruchu do usługi ExpressRoute.

8. Opcjonalnie [zaimplementuj usługę QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) i oceń rozszerzenie regionalne.

<sup>1</sup> Ważne zagadnienia dotyczące wydajności. Decyzje w tym miejscu mogą znacząco wpłynąć na opóźnienie, które ma kluczowe znaczenie dla aplikacji, takich jak Skype dla firm.

Aby uzyskać dodatkowe informacje, skorzystaj z naszego [przewodnika routingu](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) oprócz [dokumentacji usługi ExpressRoute](/azure/expressroute/expressroute-introduction).

Aby kupić usługę ExpressRoute dla Office 365, musisz współpracować z co najmniej jednym [zatwierdzonym dostawcą](/azure/expressroute/expressroute-locations), aby aprowizować żądaną liczbę i obwody rozmiaru przy użyciu subskrypcji usługi ExpressRoute Premium. Nie ma żadnych dodatkowych licencji do zakupu od Office 365.

Oto krótki link, za pomocą którego możesz wrócić: [https://aka.ms/expressrouteoffice365]()

Chcesz zarejestrować się w [usłudze ExpressRoute dla Office 365](https://aka.ms/ert)?

## <a name="related-topics"></a>Tematy pokrewne

[Ocena łączności sieciowej Office 365](assessing-network-connectivity.md)

[Zarządzanie usługą ExpressRoute na potrzeby łączności Office 365](managing-expressroute-for-connectivity.md)

[Routing przy użyciu usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)

[Planowanie sieci za pomocą usługi ExpressRoute dla usługi Office 365](network-planning-with-expressroute.md)

[Implementowanie usługi ExpressRoute dla Office 365](implementing-expressroute.md)

[Używanie społeczności protokołu BGP w usłudze ExpressRoute na potrzeby scenariuszy Office 365](bgp-communities-in-expressroute.md)

[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365 dostrajanie wydajności przy użyciu punktów odniesienia i historii wydajności](performance-tuning-using-baselines-and-history.md)

[Plan rozwiązywania problemów z wydajnością dla Office 365](performance-troubleshooting-plan.md)

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

[Office 365 dostrajanie sieci i wydajności](network-planning-and-performance.md)

## <a name="see-also"></a>Zobacz też

[omówienie Microsoft 365 Enterprise](microsoft-365-overview.md)
