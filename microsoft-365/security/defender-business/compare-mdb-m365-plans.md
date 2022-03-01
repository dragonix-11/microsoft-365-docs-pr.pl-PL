---
title: Porównanie programu Microsoft Defender dla firm z innymi planami Microsoft 365 biznesowych
description: Opis różnic między usługami Defender dla Firm i Defender for Endpoint. Wiedza o tym, co obejmuje każdy plan, może ułatwić podejmowanie przejętnych decyzji dla organizacji.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 02/26/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: 3d8270b2c8424668200e4242cb65e491a2cc6991
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027049"
---
# <a name="compare-microsoft-defender-for-business-preview-to-microsoft-365-business-premium"></a>Porównanie programu Microsoft Defender dla firm (wersja Preview) z programem Microsoft 365 Business Premium

> [!IMPORTANT]
> Usługa Microsoft Defender dla firm jest teraz w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj [, aby](https://aka.ms/mdb-preview) poprosić o to. W najbliższych tygodniach nawiązemy wstępną ofertę klientów i partnerów oraz rozszerzymy jej wersja zapoznawczą, aby rozszerzyć jej dostępność do ogólnej dostępności. Pamiętaj, że wersja Preview zostanie uruchamiana z [początkowym zestawem scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a funkcje będą regularnie dodajemy.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Firma Microsoft oferuje wiele różnych rozwiązań i usług w chmurze, w tym kilka różnych planów dla małych i średnich firm. Na [przykład Microsoft 365 Business Premium funkcje](../../business/microsoft-365-business-overview.md) zabezpieczeń i zarządzania urządzeniami oraz funkcje zwiększające produktywność, takie Office aplikacje. 

**Ten artykuł dotyczy:**

- [Porównanie programu Microsoft Defender dla firm (wersja Preview) z programem Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [Porównanie usług Defender for Business i Microsoft Defender for Endpoint dla przedsiębiorstw](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)


**Nie musisz mieć subskrypcji usługi Microsoft 365, aby kupować i używać programu Microsoft Defender dla firm (wersja Preview).** Program Microsoft Defender dla firm (w wersji Preview) to autonomiczne rozwiązanie zabezpieczające dla małych i średnich firm. Jeśli masz już inną subskrypcję (na przykład Microsoft 365 Business Basic lub Standard), rozważ dodanie usługi Microsoft Defender dla Firm, aby uzyskać więcej możliwości ochrony przed zagrożeniami. 

> [!TIP]
> Jeśli Twoja organizacja jest małą lub średnią firmą (300 lub mniej użytkowników) i chcesz zarejestrować się w programie Microsoft Defender for Business Preview, odwiedź stronę [https://aka.ms/MDB-Preview](https://aka.ms/MDB-Preview). Aby dowiedzieć się więcej, zobacz [Uzyskiwanie usługi Microsoft Defender dla firm](get-defender-business.md).

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Porównanie funkcji zabezpieczeń programu Microsoft Defender dla firm z programem Microsoft 365 Business Premium

> [!NOTE]
> Ten artykuł zawiera ogólne omówienie funkcji ochrony przed zagrożeniami, które są dostępne w programach Microsoft Defender for Business (w wersji Preview) i Microsoft 365 Business Premium. Ten artykuł nie jest przeznaczony do opisu usługi ani dokumentu umowy licencyjnej. Aby uzyskać więcej informacji, zobacz [Microsoft 365 licencjonowania zabezpieczeń i zgodności &.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

W poniższej tabeli porównano funkcje zabezpieczeń i możliwości usługi Defender dla firm z programem Microsoft 365 Business Premium, gdy program Defender dla firm jest w wersji Preview. Gdy program Defender dla firm stanie się ogólnie dostępny, zostanie on uwzględniony w Microsoft 365 Business Premium. <br/><br/>

| Funkcja/funkcja | [Microsoft Defender for Business](mdb-overview.md) (preview) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) |
|:---|:---|:---|
| Ochrona poczty e-mail | Tak ([skanowanie wiadomości e-mail](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) w programie Program antywirusowy Microsoft Defender) | Tak ([Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md)) |
| Ochrona przed programem Antispam | Tak (dla urządzeń) | Tak (w przypadku Microsoft 365 e-mail, takich jak wiadomości i załączniki) |
| Ochrona przed złośliwym oprogramowaniem | Tak (dla urządzeń) | Tak (w przypadku Microsoft 365 e-mail, takich jak wiadomości i załączniki) |
| [Ochrona następnej generacji](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (ochrona antywirusowa i ochrona przed złośliwym oprogramowaniem) | Tak (Program antywirusowy Microsoft Defender jest zawarta w Windows 10 i nowszych)  | Tak (Program antywirusowy Microsoft Defender jest zawarta w Windows 10 i nowszych) |
| [Zmniejszenie powierzchni ataków](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(reguły ograniczania powierzchni ataków i inna ochrona)  | Tak (wbudowane w funkcje Windows 10 i nowsze zasady zmniejszania powierzchni ataków oraz funkcje centralnie zarządzane) | Tak (wbudowane w reguły ograniczania powierzchni ataków w Windows 10 i nowszych) |
| [Wykrywanie punktu końcowego i odpowiedź](../defender-endpoint/overview-endpoint-detection-response.md) | Tak. Zawiera: <br/>- Wykrywanie oparte na zachowaniu <br/>— Ręczne akcje odpowiedzi <br/>— Odpowiedź na żywo   | Nie |
| [Zautomatyzowane badanie i odpowiedź](../defender-endpoint/automated-investigations.md) | Tak | Nie |
| [Zagrożenia & zarządzanie lukami w zabezpieczeniach](../defender-endpoint/tvm-dashboard-insights.md) | Tak | Nie |
| Scentralizowane zarządzanie i raportowanie | Tak. Możesz korzystać z urządzeń Windows klienckich i zarządzać nimi w portalu usługi Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) lub zarządzać urządzeniami w aplikacji Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). | Tak. Możesz zarządzać Windows klienckimi w aplikacji centrum administracyjne platformy Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)). Urządzenia muszą być podłączone w Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). |
| [Interfejsy API](../defender-endpoint/apis-intro.md) <br/>(umożliwia integrację z aplikacjami niestandardowymi lub rozwiązaniami raportowania)  | Tak | Tak |



## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Porównanie programu Microsoft Defender dla firm z programem Microsoft Defender dla punktów końcowych (plany 1 i 2)

Program Defender dla firm (wersja Preview) zapewnia możliwości programu Defender for Endpoint klasy korporacyjnej dla małych i średnich firm. W poniższej tabeli porównano funkcje zabezpieczeń i możliwości programu Defender dla firm (wersja Preview) z programem Microsoft Defender for Endpoint Plans 1 i 2. <br/><br/>

| Funkcja/funkcja | [Defender for Business](mdb-overview.md) (preview) | [Defender for Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md) | [Defender for Endpoint Plan 2](../defender-endpoint/microsoft-defender-endpoint.md) |
|:---|:---|:---|
| [Scentralizowane zarządzanie](../defender-endpoint/manage-atp-post-migration.md) <sup>[[1](#fn1)]</sup> | Tak | Tak | Tak |
| [Uproszczona konfiguracja klienta](mdb-simplified-configuration.md) | Tak | Nie | Nie |
| [Zagrożenia & zarządzanie lukami w zabezpieczeniach](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) | Tak | Nie | Tak |
| [Możliwości zmniejszania powierzchni ataków](../defender-endpoint/overview-attack-surface-reduction.md) | Tak | Tak | Tak |
| [Ochrona następnej generacji](../defender-endpoint/next-generation-protection.md) | Tak | Tak | Tak |
| [Wykrywanie punktu końcowego i odpowiedź](../defender-endpoint/overview-endpoint-detection-response.md) | Tak <sup>[[2](#fn2)]</sup> | Nie | Tak |
| [Zautomatyzowane badanie i odpowiedź](../defender-endpoint/automated-investigations.md) | Tak <sup>[[2](#fn2)]</sup> | Nie | Tak |
| [Czas chłoniania](../defender-endpoint/advanced-hunting-overview.md) zagrożeń i przechowywanie danych przez sześć miesięcy | Nie | Nie | Tak |
| [Analiza zagrożeń](../defender-endpoint/threat-analytics.md) | Tak <sup>[[2](#fn2)]</sup> | Nie | Tak |
| [Obsługa międzyplatformowa](../defender-endpoint/minimum-requirements.md) <br/>(Windows, macOS, iOS i Android OS) | Tak <sup>[[3](#fn3)]</sup> | Tak | Tak |
| [Microsoft Threat Experts](../defender-endpoint/microsoft-threat-experts.md) | Nie | Nie | Tak |
| Interfejsy API partnerów | Tak | Tak | Tak |
| [Microsoft 365 Lighthouse integracji z usługą](../../lighthouse/m365-lighthouse-overview.md) <br/>(Na potrzeby wyświetlania zdarzeń zabezpieczeń w dzierżawach klientów) | Tak | Nie | Nie |

(<a id="fn1">1</a>) Dołączanie urządzeń i zarządzanie nimi w portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) lub za pomocą innego narzędzia, takiego jak Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) Te funkcje są zoptymalizowane dla małych i średnich firm.

(<a id="fn3">3</a>) W trakcie programu w wersji Preview Windows klienckie są obsługiwane w portalu Microsoft 365 Defender sieci ([https://security.microsoft.com](https://security.microsoft.com)).

## <a name="next-steps"></a>Następne kroki

- [Zobacz wymagania dotyczące programu Microsoft Defender dla firm (wersja Preview)](mdb-requirements.md)

- [Dowiedz się, jak skonfigurować program Microsoft Defender dla firm (wersja Preview)](mdb-setup-configuration.md) 