---
title: Porównanie funkcji zabezpieczeń w Microsoft 365 dla małych i średnich firm
description: Opis różnic między usługami Defender dla Firm i Defender for Endpoint. Wiedza o tym, co obejmuje każdy plan, może pomóc w podjęciu przejmowej decyzji dotyczącej firmy.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: 793c078621424bca89ccc4c6d88c79054ab059cd
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526030"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Porównanie programu Microsoft Defender dla firm z programem Microsoft 365 Business Premium

> [!IMPORTANT]
> Program Microsoft Defender dla firm jest wprowadzany [dla Microsoft 365 Business Premium](../../business-premium/index.md) klientów od 1 marca 2022 r. Autonomiczna subskrypcja usługi Defender dla firm jest w wersji Preview i będzie stopniowo wprowadzana u klientów i partnerów IT, którzy zarejestrują się tutaj, [aby poprosić](https://aka.ms/mdb-preview) o to. Wersja Preview zawiera [początkowy zestaw scenariuszy](mdb-tutorials.md#try-these-preview-scenarios), a my będziemy regularnie dodawać funkcje.
> 
> Niektóre informacje w tym artykule dotyczą wstępnie dzierżawionych produktów/usług, które mogą zostać znacząco zmodyfikowane przed ich komercyjną premierą. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, dotyczących podanych tutaj informacji. 

Firma Microsoft oferuje wiele różnych rozwiązań i usług w chmurze, w tym kilka różnych planów dla małych i średnich firm. Na [przykład Microsoft 365 Business Premium funkcje](../../business/microsoft-365-business-overview.md) zabezpieczeń i zarządzania urządzeniami oraz funkcje zwiększające produktywność, takie Office aplikacje. Ten artykuł ma na celu pomóc w wyjaśnieniach, jakie funkcje zabezpieczeń, takie jak ochrona urządzeń, są zawarte w programach Microsoft 365 Business Premium, Microsoft Defender for Business i Microsoft Defender for Endpoint.

Usługa Microsoft Defender dla firm jest dostępna jako autonomiczna oferta lub jako Microsoft 365 Business Premium (począwszy od 1 marca 2022 r.).

>
> **Masz minutę?**
> Prosimy o <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">krótką ankietę na temat programu Microsoft Defender dla firm</a>. Chcemy ją usłyszeć!
>

**Ten artykuł dotyczy:**

- [Porównanie programu Microsoft Defender dla firm (wersja autonomiczna) z programem Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [Porównanie programu Defender dla firm (wersja autonomiczna) z usługą Microsoft Defender for Endpoint dla przedsiębiorstw](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)

**Nie musisz mieć subskrypcji usługi Microsoft 365, aby kupować i używać programu Microsoft Defender dla firm.** Program Microsoft Defender dla firm jest dostępny Microsoft 365 Business Premium i jest dostępny jako autonomiczne rozwiązanie zabezpieczeń dla małych i średnich firm. Jeśli masz już program Microsoft 365 Business Basic lub Standard, rozważ dodanie uaktualnienia do programu Microsoft 365 Business Premium lub dodania usługi Microsoft Defender for Business w celu uzyskania większej liczby możliwości ochrony przed zagrożeniami. 

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Porównanie funkcji zabezpieczeń programu Microsoft Defender dla firm z programem Microsoft 365 Business Premium

> [!NOTE]
> Ten artykuł ma na celu omówienie na wysokim poziomie funkcji ochrony przed zagrożeniami, które są zawarte w programach Microsoft Defender dla Firm (jako plan autonomiczny) i Microsoft 365 Business Premium (który zawiera program Defender dla firm). Ten artykuł nie jest przeznaczony do opisu usługi ani dokumentu umowy licencyjnej. Aby uzyskać więcej informacji, zobacz [Microsoft 365 licencjonowania zabezpieczeń i zgodności &.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

**Począwszy od 1 marca 2022 r., rozpocznie się uruchamianie usługi Defender dla firm w ramach programu Microsoft 365 Business Premium. Autonomiczna oferta usługi Defender dla firm jest nadal w wersji Preview.**

W poniższej tabeli porównano funkcje zabezpieczeń i możliwości usługi Defender dla firm (wersja autonomiczna) z programem Microsoft 365 Business Premium. 

 <br/><br/>

| Funkcja/funkcja | [Microsoft Defender for Business](mdb-overview.md)<br/>(wersja autonomiczna, obecnie w wersji Preview) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(obejmuje program Defender dla firm) |
|:---|:---|:---|
| Ochrona poczty e-mail | Tak <br/>- [Skanowanie wiadomości e-mail za pomocą Program antywirusowy Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) | Tak <br/>- [Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) <br/>- [Skanowanie wiadomości e-mail za pomocą Program antywirusowy Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Ochrona przed programem Antispam | Tak <br/>- W przypadku urządzeń | Tak <br/>- W przypadku urządzeń<br/>— w Microsoft 365 e-mail, takiej jak wiadomości i załączniki |
| Ochrona przed złośliwym oprogramowaniem | Tak<br/>- W przypadku urządzeń | Tak <br/>- W przypadku urządzeń<br/>— w Microsoft 365 e-mail, takiej jak wiadomości i załączniki |
| [Ochrona następnej generacji](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (ochrona antywirusowa i ochrona przed złośliwym oprogramowaniem) | Tak<br/>— Program antywirusowy Microsoft Defender jest dołączony do Windows 10 i nowszych  | Tak <br/>— Program antywirusowy Microsoft Defender jest dołączony do Windows 10 i nowszych<br/>- Zasady ochrony następnej generacji dla urządzeń podłączonych do urządzenia |
| [Zmniejszenie powierzchni ataków](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(Reguły ASR w programie Windows 10 lub nowszym i ochrona zapory) | Tak  | Tak  |
| [Wykrywanie punktu końcowego i odpowiedź](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(wykrywanie oparte na zachowaniu i akcje ręcznej odpowiedzi) | Tak | Tak |
| [Zautomatyzowane badanie i odpowiedź](../defender-endpoint/automated-investigations.md) | Tak | Tak |
| [Zagrożenia & zarządzanie lukami w zabezpieczeniach](../defender-endpoint/tvm-dashboard-insights.md) | Tak | Tak |
| Scentralizowane zarządzanie i raportowanie  | Tak  | Tak  |
| [Interfejsy API](../defender-endpoint/apis-intro.md) <br/>(na przykład w celu integracji z aplikacjami niestandardowymi lub rozwiązaniami raportowania)  | Tak | Tak |


## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Porównanie programu Microsoft Defender dla firm z programem Microsoft Defender dla punktów końcowych (plany 1 i 2)

Program Defender dla firm zapewnia funkcje programu Defender dla programu Endpoint klasy korporacyjnej dla małych i średnich firm. 

W poniższej tabeli porównano funkcje zabezpieczeń i możliwości usługi Defender dla firm z programem Microsoft Defender for Endpoint Plans 1 i 2. <br/><br/>

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

- [Zobacz wymagania dotyczące programu Microsoft Defender dla firm](mdb-requirements.md)

- [Uzyskaj usługę Microsoft Defender dla firm](get-defender-business.md)

- [Dowiedz się, jak skonfigurować program Microsoft Defender dla firm](mdb-setup-configuration.md) 
