---
title: Ochrona punktu końcowego w usłudze Microsoft Defender
description: Program Microsoft Defender for Endpoint to platforma zabezpieczeń punktów końcowych przedsiębiorstwa, która pomaga chronić przed zaawansowanymi trwałymi zagrożeniami.
keywords: wprowadzenie do programu Microsoft Defender for Endpoint, wprowadzenie do programu Microsoft Defender for Endpoint,ity, advanced persistent threat, enterprise security, machine behavioral sensor, cloud security, analytics, threat intelligence, threat intelligence, attack surface reduction, next-generation protection, automated investigation and remediation, microsoft threat experts, secure score, advanced hunting, Microsoft 365 Defender, cyber threat hunting
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: high
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.custom: intro-overview
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c4308c203093d2170cc1a6316db824ee9935363f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019349"
---
# <a name="microsoft-defender-for-endpoint"></a>Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Program Microsoft Defender for Endpoint to platforma zabezpieczeń punktów końcowych przedsiębiorstwa, która ma ułatwić sieciom przedsiębiorstwa zapobieganie zaawansowanym zagrożeniam, wykrywanie, badanie i reagowanie na nie.

> [!TIP]
> Wkrótce usługa Microsoft Defender for Endpoint będzie dostępna w dwóch planach. W tym artykule opisano funkcje i możliwości zawarte w programie Microsoft Defender for Endpoint Plan 2. [Dowiedz się więcej o programie Microsoft Defender dla planu 1 i planu 2 dla punktów końcowych](defender-endpoint-plan-1-2.md).
> 

<p><p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Program Defender for Endpoint korzysta z następującej kombinacji technologii wbudowanej Windows 10 i niezawodnej usługi firmy Microsoft w chmurze:

- **Czujnik zachowania** punktu końcowego: Czujnik osadzony w programie Windows 10 zbiera i przetwarza sygnały dźwiękowe z systemu operacyjnego i przesyła te dane czujnika do Twojego prywatnego, odizolego i odizolego wystąpienia usługi Microsoft Defender for Endpoint w chmurze.

- Analiza zabezpieczeń w **chmurze: wykorzystanie** dużych danych, nauka urządzeń i unikatowe urządzenia firmy Microsoft na całym ekosystemie Windows, produktach w chmurze przedsiębiorstwa (takich jak Office 365) i zasobami online sygnały zachowania są tłumaczone na szczegółowe informacje, wykrywanie i zalecane odpowiedzi na zaawansowane zagrożenia.

- Inteligencja **zagrożeń:** wygenerowana przez firmy Microsoft, zespoły zabezpieczeń i ulepszona przez analizę zagrożeń udostępnianą przez partnerów, analizy zagrożeń umożliwia u defendera punktu końcowego identyfikowanie narzędzi, technik i procedur atakujących oraz generowanie alertów podczas obserwowania ich w zbieranych danych czujnika.

<center><h2>Ochrona punktu końcowego w usłudze Microsoft Defender</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="Threat & Vulnerability Management"> <br><b>Zarządzanie & zagrożeniami</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Zmniejszenie powierzchni ataków</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Ochrona następnej generacji</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>Wykrywanie punktu końcowego i odpowiedź</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>Zautomatyzowane badanie i rozwiązywanie problemów</b></a></center></td>
<td><center><a href="#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>Microsoft Threat Experts</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>Scentralizowane konfigurowanie i administrowanie interfejsami API</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

<p></p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0]

> [!TIP]
>
> - Dowiedz się więcej o najnowszych ulepszeniach w programie Defender for Endpoint: Co nowego w [programie Microsoft Defender for Endpoint](whats-new-in-microsoft-defender-endpoint.md).
> - Program Microsoft Defender for Endpoint zademonstrował wiodące w branży kable i funkcje wykrywania w ostatnim czasie oceny miTRE. Przeczytaj: [Szczegółowe informacje z miTRE ATT&oceny na podstawie CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

<a name="tvm"></a>

**[Zarządzanie & zagrożeniami](next-gen-threat-and-vuln-mgt.md)**

Ta wbudowana funkcja wykorzystuje zmieniające się ryzyko podejście do odnajdowania, priorytetyzowania i korygowania luk w punktach końcowych i błędnej konfiguracji.

<a name="asr"></a>

**[Zmniejszenie powierzchni ataków](overview-attack-surface-reduction.md)**

Zestaw możliwości zmniejszania powierzchni ataków zapewnia pierwszą linię obrony w stosie. Upewniając się, że ustawienia konfiguracji są poprawnie ustawione i stosowane są techniki wykorzystywania wpływu wykorzystywania wykorzystywania, te funkcje opierają się na atakach i wykorzystywaniu. Ten zestaw funkcji obejmuje również ochronę [sieci](network-protection.md) i ochronę sieci [Web](web-protection-overview.md), które regulowają dostęp do złośliwych adresów IP, domen i adresów URL.

<a name="ngp"></a>

**[Ochrona następnej generacji](next-generation-protection.md)**

Aby dodatkowo zwiększyć obwod zabezpieczeń sieci, usługa Microsoft Defender for Endpoint używa ochrony następnej generacji w celu wychwytania wszystkich typów wyłaniających się zagrożeń.

<a name="edr"></a>

**[Wykrywanie punktu końcowego i odpowiedź](overview-endpoint-detection-response.md)**

Funkcje wykrywania punktu końcowego i reakcji są dostępne w celu wykrywania i zbadania zaawansowanych zagrożeń, które mogą przesuną się poza dwa pierwsze słupy zabezpieczeń, oraz reagowania na nie. [Zaawansowane wyszukiwanie](advanced-hunting-overview.md) zapewnia oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które umożliwia aktywne znajdowanie naruszeń i tworzenie niestandardowych wykrywanie.

<a name="ai"></a>

**[Zautomatyzowane badanie i rozwiązywanie problemów](automated-investigations.md)**

Program Microsoft Defender for Endpoint oferuje funkcje automatycznego badania i rozwiązywania problemów, które ułatwiają szybkie reagowanie na zaawansowane ataki w ciągu kilku minut.

<a name="ss"></a>

**[Microsoft Secure Score dla urządzeń](tvm-microsoft-secure-score-devices.md)**

Program Defender for Endpoint zawiera ocenę zabezpieczeń firmy Microsoft dla urządzeń, ułatwiając dynamiczne ocenianie stanu zabezpieczeń sieci przedsiębiorstwa, identyfikowanie systemów niechronionych i stosowanie zalecanych działań w celu poprawy ogólnego bezpieczeństwa organizacji.

<a name="mte"></a>

**[Microsoft Threat Experts](microsoft-threat-experts.md)**

Nowe zarządzane usługi chłoowania pod zagrożeniami w programie Microsoft Defender for Endpoint zapewniają proaktywne działania chłonia, priorytetyzowanie oraz dodatkowe informacje, dzięki którym możesz jeszcze bardziej identyfikować zagrożenia i odpowiednio reagować na nie.

> [!IMPORTANT]
> Klienci korzystający z usługi Defender for Endpoint muszą złożyć wniosek o usługę Microsoft Threat Experts zarządzania zagrożeniami, aby otrzymywać proaktywne powiadomienia o atakach ukierunkowanych i współpracować z ekspertami na żądanie. Experts on Demand to usługa dodatkowa. Powiadomienia o atakach kierowanej są zawsze uwzględniane po zaakceptowaniu Cię do Microsoft Threat Experts usłudze chłoniania zagrożeń.
>
> Jeśli jeszcze się nie zarejestrowani i chcesz odświadczyć korzyści,  \> przejdź do Ustawienia **Zaawansowane** \>  \> funkcje ogólne i **Microsoft Threat Experts** zastosowania. Po zaakceptowaniu otrzymasz korzyści z powiadomień o atakach kierowanej i rozpocznij 90-dniową wersję próbną ekspertów na żądanie. Skontaktuj się z przedstawicielem firmy Microsoft, aby uzyskać pełną subskrypcję usługi Experts on Demand.

<a name="apis"></a>

**[Scentralizowane konfigurowanie i administrowanie interfejsami API](management-apis.md)**

Zintegruj usługę Microsoft Defender for Endpoint z istniejącymi przepływami pracy.

<a name="mtp"></a>

**[Integracja z rozwiązaniami firmy Microsoft](threat-protection-integration.md)**

Program Defender for Endpoint jest bezpośrednio zintegrowany z różnymi rozwiązaniami firmy Microsoft, między innymi:

- Microsoft Defender dla chmury
- Microsoft Sentinel
- Intune
- Usługa Microsoft Defender dla aplikacji w chmurze
- Microsoft Defender for Identity
- Program Microsoft Defender dla Office
- Skype dla firm

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

Program Microsoft 365 Defender, program Defender for Endpoint i różne rozwiązania zabezpieczeń firmy Microsoft tworzą ujednolicony pakiet ochrony przed naruszeniem i po naruszeniu zabezpieczeń przedsiębiorstwa, który natywnie integruje się między punktami końcowymi, tożsamościami, pocztą e-mail i aplikacjami w celu wykrywania, zapobiegania, zbadania i automatycznego reagowania na zaawansowane ataki i automatycznego reagowania na nie.


## <a name="training-for-security-analysts"></a>Szkolenie dla analityków zabezpieczeń

Dzięki tej ścieżce nauki z witryny Microsoft Learn możesz zrozumieć usługę Defender for Endpoint i dowiedzieć się, w jaki sposób może ona zapobiegać, wykrywać i badać zagrożenia dla punktów końcowych Twojej organizacji oraz odpowiadać na nie — Twoich urządzeń i systemów.

|Szkolenie:|Wykrywanie cyberataków i reagowanie na nie za pomocą Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender ikony szkolenia.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Defender for Endpoint to rozwiązanie zabezpieczeń punktu końcowego, które oferuje zarządzanie lukami w zabezpieczeniach, ochronę punktu końcowego, wykrywanie i reagowanie w punktach końcowych, ochronę przed zagrożeniami na urządzeniach przenośnych i usługi zarządzane w jednej, ujednoliconej platformie.<p> 2 godz. 25 min - ścieżka Edukacja - 9 modułów|

> [!div class="nextstepaction"]
> [Rozpoczynanie >](/learn/paths/defender-endpoint-fundamentals/)
