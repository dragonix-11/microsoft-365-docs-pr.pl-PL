---
title: Usługa Azure ExpressRoute dla Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Dowiedz się, jak używać usługi Azure ExpressRoute Office 365 i planować projekt implementacji sieci, jeśli wdrażasz za jej pomocą.
ms.openlocfilehash: 9a4f4be76751ec03610bd766f51ec91526ca18a4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986420"
---
# <a name="azure-expressroute-for-office-365"></a>Usługa Azure ExpressRoute dla Office 365

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Dowiedz się, jak usługa Azure ExpressRoute jest używana z usługą Office 365 i jak zaplanować projekt implementacji sieci, który będzie wymagany, jeśli wdrażasz usługę Azure ExpressRoute do użytku z usługą Office 365. Zagadnienia związane z architekturą i wydajnością sieci często skorzystają z usług infrastruktury i platformy działających na platformie Azure. W takich przypadkach zalecamy korzystanie z usługi ExpressRoute dla platformy Azure. Oferty "Oprogramowanie jako usługa", Office 365 i Dynamics 365, zostały tak zbudowane, aby można było bezpiecznie i niezawodnie uzyskiwać do nich dostęp za pośrednictwem Internetu. O wydajności i zabezpieczeniach Internetu oraz o tym, kiedy warto rozważyć usługę Azure ExpressRoute dla systemu Office 365, możesz przeczytać w artykule Ocena Office 365 [sieci.](assessing-network-connectivity.md)

> [!NOTE]
> Program Microsoft Defender for Endpoint nie zapewnia integracji z usługą Azure ExpressRoute. Nie stanowi to dla klientów możliwości zdefiniowania reguł usługi ExpressRoute, które umożliwiają łączność z sieci prywatnej z usługami w chmurze programu Microsoft Defender for Endpoint, jednak to klient musi zachowywać reguły w związku z rozwojem usługi lub infrastruktury chmury.

> [!NOTE]
> Nie zalecamy usługi ExpressRoute Microsoft 365 ponieważ w większości przypadków nie zapewnia ona najlepszego modelu łączności dla usługi. W związku z tym do korzystania z tego modelu łączności na potrzeby Microsoft 365 jest wymagana autoryzacja Microsoft 365. Przeglądamy każde żądanie klienta i autoryzowamy usługę ExpressRoute Microsoft 365 tylko w rzadkich przypadkach, gdy jest to konieczne. Przeczytaj przewodnik usługi [ExpressRoute dla usługi Microsoft 365](https://aka.ms/erguide), aby uzyskać więcej informacji i po kompleksowym przeglądzie dokumentu wraz z zespołami ds. produktywności, sieci i zabezpieczeń, skontaktuj się ze swoim zespołem ds. kont Microsoft, aby w razie potrzeby zgłosić wyjątek. Nieautoryzowane subskrypcje próbujące utworzyć filtry trasy dla Office 365 otrzymają [komunikat o błędzie](https://support.microsoft.com/kb/3181709).

## <a name="planning-azure-expressroute-for-office-365"></a>Planowanie usługi Azure ExpressRoute dla Office 365

Poza łącznością z Internetem możesz wybrać kierowanie podzestawu ruchu sieciowego usługi Office 365 za pośrednictwem połączenia bezpośredniego, które zapewnia przewidywalność i beza wyeks tym składników sieciowych na poziomie 99,95%. Usługa Azure ExpressRoute zapewnia dedykowane połączenie sieciowe z Office 365 innymi usługami w chmurze firmy Microsoft.

Niezależnie od tego, czy masz istniejącą sieć MPLS WAN, usługę ExpressRoute można dodać do swojej architektury sieci w jeden z trzech sposobów: za pośrednictwem obsługiwanego dostawcy współ lokalizacji wymiany w chmurze, dostawcy połączenia Ethernet typu punkt-punkt lub za pośrednictwem dostawcy połączenia MPLS. Sprawdź, [którzy dostawcy są dostępni w Twoim regionie](/azure/expressroute/expressroute-locations). Bezpośrednie połączenie ExpressRoute umożliwi łączność z aplikacjami, które opisano [Office 365 w poniższej tabeli](azure-expressroute.md#BKMK_WhatDoIGet). Ruch sieciowy dla wszystkich innych aplikacji i usług będzie nadal przechodził przez Internet.

Rozważmy poniższy diagram sieci wysokiego poziomu, który przedstawia typowego klienta usługi Office 365 łączącego się z centrami danych firmy Microsoft przez Internet w celu uzyskania dostępu do wszystkich aplikacji firmy Microsoft, takich jak Office 365, Windows Update i TechNet. Klienci używają podobnej ścieżki sieciowej niezależnie od tego, czy nawiążą połączenie z sieci lokalnej, czy z niezależnego połączenia internetowego.

![Office 365 sieciową.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Teraz spójrz na zaktualizowany diagram przedstawiający klienta usługi Office 365, który używa zarówno Internetu, jak i usługi ExpressRoute do łączenia się z usługą Office 365. Zwróć uwagę, że niektóre połączenia, takie jak publiczny system DNS Content Delivery Network węzły, nadal wymagają publicznego połączenia internetowego. Użytkownicy klienta, którzy nie znajdują się w budynku połączonym z usługą ExpressRoute, nawiązanie połączenia przez Internet.

![Office 365 za pomocą usługi ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

Nadal chcesz uzyskać więcej informacji? Dowiedz się, jak [zarządzać ruchem sieciowym za pomocą usługi Azure ExpressRoute](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) dla usługi Office 365 i jak skonfigurować usługę [Azure ExpressRoute na](/azure/expressroute/expressroute-faqs) Office 365. Nagraliśmy również 10-częściową serię szkoleń dotyczących usługi [Azure ExpressRoute](https://channel9.msdn.com/series/aer) dla usługi Office 365 w ramach kanału 9, aby ułatwić dogłębne wyjaśnienie tych pojęć.

## <a name="what-office-365-services-are-included"></a>Jakie Office 365 są dostępne?
<a name="BKMK_WhatDoIGet"> </a>

W poniższej tabeli wymieniono usługi Office 365 obsługiwane przez usługę ExpressRoute. Zapoznaj się z [artykułem Office 365 punktów końcowych](./urls-and-ip-address-ranges.md), aby dowiedzieć się, które żądania sieciowe dla tych aplikacji wymagają połączenia z Internetem.

| Dołączone aplikacje |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype dla firm <sup>Online1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint <sup>Online1</sup> <br/> OneDrive dla Firm <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|Portal i współużytk<sup>(1)</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD Połączenie <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> Każda z tych aplikacji ma wymagania dotyczące łączności internetowej, które nie są obsługiwane przez usługę ExpressRoute, zobacz Office 365 [punktów końcowych](./urls-and-ip-address-ranges.md), aby uzyskać więcej informacji.

Usługi, które nie są uwzględnione w usłudze ExpressRoute dla usługi Office 365, Aplikacje Microsoft 365 dla przedsiębiorstw pobieranie klientów, logowanie lokalnego dostawcy tożsamości i usługa Office 365 (obsługiwana przez firmę 21 Vianet) w Chinach.

## <a name="implementing-expressroute-for-office-365"></a>Implementowanie expressroute dla Office 365

Wdrażanie usługi ExpressRoute wymaga zaangażowania właścicieli aplikacji i sieci oraz starannego planowania w celu określenia nowej architektury [routingu](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) sieci, wymagań dotyczących przepustowości, miejsc wdrożenia zabezpieczeń, wysokiej dostępności itp. Aby zaimplementować expressRoute, musisz:

1. Pełne zrozumienie potrzeb zaspokajanych przez usługę ExpressRoute w planowaniu Office 365 twojej sieci. Zrozumienie, które aplikacje będą używać Internetu lub usługi ExpressRoute, i pełne zaplanowanie wydajności sieci, zabezpieczeń oraz potrzeb w zakresie wysokiej dostępności w kontekście używania zarówno Internetu, jak i usługi ExpressRoute do Office 365 sieci.

2. Określ lokalizacje ruchu wychodzącego i komunikacji równorzędnej zarówno dla ruchu internetowego,<sup></sup> jak i ruchu usługi ExpressRoute1.

3. Określ pojemność wymaganą dla połączeń internetowych i połączeń usługi ExpressRoute.

4. Należy realizować plan wdrożenia zabezpieczeń i innych standardowych kontrolek <sup>obwodu1</sup>.

5. Mieć ważne konto Microsoft Azure w celu zasubskrybowania usługi ExpressRoute.

6. Wybierz model łączności i [zatwierdzonego dostawcę](/azure/expressroute/expressroute-locations). Pamiętaj, że klienci mogą wybrać wiele modeli łączności lub wielu partnerów, a partner nie musi być taki sam jak Twój istniejący dostawca sieci.

7. Sprawdź poprawność wdrożenia przed kierowaniem ruchu do usługi ExpressRoute.

8. Opcjonalnie [możesz zaimplementować analizę QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) i ocenić rozszerzenie regionalne.

<sup>1</sup> Ważne zagadnienia dotyczące wydajności. Decyzje podjęte w tej sprawie mogą znacznie wpłynąć na opóźnienie, które ma kluczowe znaczenie dla aplikacji, takich jak Skype dla firm.

Aby uzyskać dodatkowe informacje, skorzystaj z [naszego przewodnika routingu](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) poza dokumentacją [usługi ExpressRoute](/azure/expressroute/expressroute-introduction).

Aby kupić usługę ExpressRoute dla usługi Office 365, musisz pracować z jednym lub większą liczbą zatwierdzonych [](/azure/expressroute/expressroute-locations) dostawców w celu zapewnienia obsługi odpowiedniej liczby obwodów o odpowiednim rozmiarze i liczbie obwodów za pomocą subskrypcji Premium ExpressRoute. Nie ma żadnych dodatkowych licencji do zakupu w Office 365.

Oto krótki link, który możesz użyć, aby tu wrócić: [https://aka.ms/expressrouteoffice365]()

Wszystko gotowe do zalogowania się do [expressRoute dla Office 365](https://aka.ms/ert)?

## <a name="related-topics"></a>Tematy pokrewne

[Ocena Office 365 sieci](assessing-network-connectivity.md)

[Zarządzanie łącznością sieciową za Office 365 ExpressRoute](managing-expressroute-for-connectivity.md)

[Routing za pomocą usługi ExpressRoute dla usługi Office 365](routing-with-expressroute.md)

[Planowanie sieci z usługą ExpressRoute dla sieci Office 365](network-planning-with-expressroute.md)

[Implementowanie expressroute dla Office 365](implementing-expressroute.md)

[Używanie społeczności BGP w u usługi ExpressRoute na Office 365 scenariuszy](bgp-communities-in-expressroute.md)

[Jakość multimediów i wydajność łączności sieciowej w Skype dla firm Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365 wydajności przy użyciu planu bazowego i historii wydajności](performance-tuning-using-baselines-and-history.md)

[Plan rozwiązywania problemów z wydajnością Office 365](performance-troubleshooting-plan.md)

[Adresy URL i zakresy adresów IP usługi Office 365](urls-and-ip-address-ranges.md)

[Office 365 sieci i dostosowywania wydajności](network-planning-and-performance.md)

## <a name="see-also"></a>Zobacz też

[Microsoft 365 Enterprise omówienie](microsoft-365-overview.md)
