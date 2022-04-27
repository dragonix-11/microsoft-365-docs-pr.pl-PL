---
title: Ochrona punktu końcowego w usłudze Microsoft Defender
description: Ochrona punktu końcowego w usłudze Microsoft Defender to platforma zabezpieczeń punktu końcowego przedsiębiorstwa, która pomaga chronić się przed zaawansowanymi trwałymi zagrożeniami.
keywords: wprowadzenie do Ochrona punktu końcowego w usłudze Microsoft Defender, wprowadzenie do Ochrona punktu końcowego w usłudze Microsoft Defender, cyberbezpieczeństwa, zaawansowanego trwałego zagrożenia, zabezpieczeń przedsiębiorstwa, czujnika zachowania maszyny, bezpieczeństwa chmury, analizy, zagrożenia inteligencja, redukcja powierzchni ataków, ochrona nowej generacji, zautomatyzowane badanie i korygowanie, eksperci od zagrożeń firmy Microsoft, wskaźnik bezpieczeństwa, zaawansowane wyszukiwanie zagrożeń, Microsoft 365 Defender, wyszukiwanie zagrożeń cybernetycznych
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
ms.openlocfilehash: 77766c153582f519aa0ba9853d18c216092747bc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092310"
---
# <a name="microsoft-defender-for-endpoint"></a>Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Ochrona punktu końcowego w usłudze Microsoft Defender to platforma zabezpieczeń punktu końcowego przedsiębiorstwa, która pomaga sieciom przedsiębiorstw w zapobieganiu zaawansowanym zagrożeniom, wykrywaniu i badaniu ich oraz reagowaniu na nie.

> [!TIP]
> Wkrótce Ochrona punktu końcowego w usłudze Microsoft Defender będą dostępne w dwóch planach. W tym artykule opisano funkcje i możliwości zawarte w planie Ochrona punktu końcowego w usłudze Microsoft Defender 2. [Dowiedz się więcej o Ochrona punktu końcowego w usłudze Microsoft Defender planie 1 i planie 2](defender-endpoint-plan-1-2.md).
> 

<p><p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Usługa Defender for Endpoint korzysta z następującej kombinacji technologii wbudowanej w Windows 10 i niezawodnej usługi firmy Microsoft w chmurze:

- **Czujniki behawioralne punktu końcowego**: osadzone w Windows 10 te czujniki zbierają i przetwarzają sygnały behawioralne z systemu operacyjnego i wysyłają te dane czujnika do prywatnego, izolowanego wystąpienia Ochrona punktu końcowego w usłudze Microsoft Defender w chmurze.

- **Analiza zabezpieczeń w chmurze**: wykorzystanie danych big data, uczenia urządzeń i unikatowej optyki firmy Microsoft w ekosystemie Windows, produktach w chmurze przedsiębiorstwa (takich jak Office 365) i zasobach online, sygnały behawioralne są tłumaczone na szczegółowe informacje, wykrywanie i zalecane reakcje na zaawansowane zagrożenia.

- **Analiza zagrożeń**: wygenerowana przez myśliwych firmy Microsoft, zespoły ds. zabezpieczeń i rozszerzona przez analizę zagrożeń dostarczaną przez partnerów, analiza zagrożeń umożliwia usłudze Defender for Endpoint identyfikowanie narzędzi, technik i procedur atakujących oraz generowanie alertów, gdy są one obserwowane w zbieranych danych czujników.

<center><h2>Ochrona punktu końcowego w usłudze Microsoft Defender</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="Threat & Vulnerability Management"> <br><b>Zarządzanie lukami w zabezpieczeniach & zagrożeń</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Zmniejszanie obszaru podatnego na ataki</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Ochrona nowej generacji</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>Wykrywanie i reagowanie na punkty końcowe</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>Zautomatyzowane badanie i korygowanie</b></a></center></td>
<td><center><a href="#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>Microsoft Threat Experts</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>Scentralizowana konfiguracja i administracja, interfejsy API</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

<p></p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0]

> [!TIP]
> - Dowiedz się więcej o najnowszych ulepszeniach w usłudze Defender for Endpoint: [Co nowego w Ochrona punktu końcowego w usłudze Microsoft Defender](whats-new-in-microsoft-defender-endpoint.md).
> - Ochrona punktu końcowego w usłudze Microsoft Defender przedstawiono wiodące w branży funkcje optyki i wykrywania w niedawnej ocenie MITRE. Przeczytaj: [Szczegółowe informacje z oceny opartej na&MITRE ATT](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).


> [!IMPORTANT]
> Możliwości na platformach innych niż Windows mogą różnić się od tych dla Windows. Aby uzyskać więcej informacji na temat możliwości dostępnych dla platform innych niż Windows, zobacz [Ochrona punktu końcowego w usłudze Microsoft Defender platform innych niż Windows](/microsoft-365/security/defender-endpoint/non-windows).

<a name="tvm"></a>

**[Zarządzanie lukami w zabezpieczeniach & zagrożeń](next-gen-threat-and-vuln-mgt.md)**

Ta wbudowana funkcja korzysta ze zmieniającego się w grze podejścia opartego na ryzyku do odnajdywania, określania priorytetów i korygowania luk w zabezpieczeniach punktów końcowych i błędnych konfiguracji.

<a name="asr"></a>

**[Zmniejszanie obszaru podatnego na ataki](overview-attack-surface-reduction.md)**

Zestaw możliwości zmniejszania obszaru podatnego na ataki zapewnia pierwszą linię obrony w stosie. Dzięki zapewnieniu prawidłowego ustawienia konfiguracji i zastosowaniu technik ograniczania ryzyka wykorzystujących luki w zabezpieczeniach możliwości są odporne na ataki i wykorzystywanie. Ten zestaw możliwości obejmuje również [ochronę sieci](network-protection.md) i [ochronę w Internecie](web-protection-overview.md), które regulują dostęp do złośliwych adresów IP, domen i adresów URL.

<a name="ngp"></a>

**[Ochrona nowej generacji](next-generation-protection.md)**

Aby jeszcze bardziej wzmocnić obwód zabezpieczeń sieci, Ochrona punktu końcowego w usłudze Microsoft Defender korzysta z ochrony nowej generacji przeznaczonej do przechwytywania wszystkich typów pojawiających się zagrożeń.

<a name="edr"></a>

**[Wykrywanie i reagowanie dotyczące punktów końcowych](overview-endpoint-detection-response.md)**

Funkcje wykrywania punktów końcowych i reagowania są stosowane w celu wykrywania, badania i reagowania na zaawansowane zagrożenia, które mogły przejść przez dwa pierwsze filary zabezpieczeń. [Zaawansowane wyszukiwanie zagrożeń](advanced-hunting-overview.md) udostępnia oparte na zapytaniach narzędzie do wyszukiwania zagrożeń, które umożliwia aktywne znajdowanie naruszeń i tworzenie wykrywania niestandardowego.

<a name="ai"></a>

**[Zautomatyzowane badanie i korygowanie](automated-investigations.md)**

W połączeniu z możliwością szybkiego reagowania na zaawansowane ataki Ochrona punktu końcowego w usłudze Microsoft Defender oferuje możliwości automatycznego badania i korygowania, które pomagają zmniejszyć liczbę alertów w ciągu kilku minut na dużą skalę.

<a name="ss"></a>

**[Wskaźnik bezpieczeństwa Microsoft dla urządzeń](tvm-microsoft-secure-score-devices.md)**

Usługa Defender for Endpoint zawiera wskaźnik bezpieczeństwa firmy Microsoft dla urządzeń, który ułatwia dynamiczną ocenę stanu zabezpieczeń sieci przedsiębiorstwa, identyfikowanie niechronionych systemów i podjęcie zalecanych działań w celu zwiększenia ogólnego bezpieczeństwa organizacji.

<a name="mte"></a>

**[Microsoft Threat Experts](microsoft-threat-experts.md)**

Nowa zarządzana usługa wyszukiwania zagrożeń Ochrona punktu końcowego w usłudze Microsoft Defender zapewnia proaktywne wyszukiwanie zagrożeń, określanie priorytetów oraz dodatkowy kontekst i szczegółowe informacje, które dodatkowo umożliwiają centrom operacji zabezpieczeń (SOC) szybkie i dokładne identyfikowanie zagrożeń i reagowanie na nie.

> [!IMPORTANT]
> Klienci usługi Defender for Endpoint muszą ubiegać się o Microsoft Threat Experts zarządzaną usługę wyszukiwania zagrożeń, aby uzyskać proaktywne powiadomienia o ukierunkowanych atakach i współpracować z ekspertami na żądanie. Eksperci na żądanie to usługa dodatkowa. Powiadomienia o atakach docelowych są zawsze uwzględniane po zaakceptowaniu do Microsoft Threat Experts zarządzanej usługi wyszukiwania zagrożeń.
>
> Jeśli nie jesteś jeszcze zarejestrowany i chcesz skorzystać z jego korzyści, przejdź do **Ustawienia** \> **Ogólne** \> **funkcje** \> zaawansowane **Microsoft Threat Experts** do zastosowania. Po zaakceptowaniu uzyskasz korzyści z powiadomień o ukierunkowanych atakach i rozpoczniesz 90-dniową wersję próbną ekspertów na żądanie. Skontaktuj się z przedstawicielem firmy Microsoft, aby uzyskać pełną subskrypcję Eksperci na żądanie.

<a name="apis"></a>

**[Scentralizowana konfiguracja i administracja, interfejsy API](management-apis.md)**

Zintegruj Ochrona punktu końcowego w usłudze Microsoft Defender z istniejącymi przepływami pracy.

<a name="mtp"></a>

**[Integracja z rozwiązaniami firmy Microsoft](threat-protection-integration.md)**

Usługa Defender for Endpoint bezpośrednio integruje się z różnymi rozwiązaniami firmy Microsoft, w tym:

- Microsoft Defender for Cloud
- Microsoft Sentinel
- Intune
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity
- Usługa Microsoft Defender dla Office
- Skype dla firm

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

Dzięki Microsoft 365 Defender, usłudze Defender for Endpoint i różnym rozwiązaniom zabezpieczeń firmy Microsoft należy utworzyć ujednolicony pakiet ochrony przedsiębiorstwa przed naruszeniami zabezpieczeń, który natywnie integruje się między punktami końcowymi, tożsamościami, pocztą e-mail i aplikacjami w celu wykrywania, zapobiegania, badania i automatycznego reagowania na zaawansowane ataki.


## <a name="training-for-security-analysts"></a>Szkolenia dla analityków zabezpieczeń

Korzystając z tej ścieżki szkoleniowej z usługi Microsoft Learn, możesz zrozumieć usługę Defender for Endpoint i dowiedzieć się, jak może ona pomóc w zapobieganiu zagrożeniom, wykrywaniu, badaniu i reagowaniu na nie w punktach końcowych organizacji — urządzeniach i systemach.

|Szkolenia:|Wykrywanie cyberataków i reagowanie na nie za pomocą Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender ikona trenowania.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Defender for Endpoint to rozwiązanie zabezpieczeń punktu końcowego, które oferuje zarządzanie lukami w zabezpieczeniach, ochronę punktów końcowych, wykrywanie i reagowanie w punktach końcowych, ochronę przed zagrożeniami mobilnymi i usługi zarządzane na jednej, ujednoliconej platformie.<p> 2 godz. 25 min — ścieżka Edukacja — 9 modułów|

> [!div class="nextstepaction"]
> [Rozpocznij >](/learn/paths/defender-endpoint-fundamentals/)
