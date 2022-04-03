---
title: Przygotowywanie zabezpieczenia na wypadek pierwszego zdarzenia
description: Skonfiguruj pocztę Microsoft 365 dzierżawy dla pierwszego zdarzenia w programie Microsoft 365 Defender.
keywords: zdarzenia, alerty, badanie, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: c31a6e43e66b6e1ffeace75ac2d8419cc764174f
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499138"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>Przygotowywanie zabezpieczenia na wypadek pierwszego zdarzenia

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Przygotowanie do obsługi zdarzeń wymaga skonfigurowania wystarczającej ochrony sieci organizacji przed różnymi rodzajami zdarzeń zabezpieczających. Aby zmniejszyć ryzyko zdarzeń dotyczących zabezpieczeń, National Institute of Standards and Technology (NIST) zaleca stosowanie kilku praktyk w zakresie zabezpieczeń, takich jak ocena ryzyka, zabezpieczanie hosta, bezpieczne konfigurowanie sieci i zapobieganie złośliwemu oprogramowaniu. 

Microsoft 365 Defender pomoc w zakresie kilku aspektów zapobiegania incydentom: 

- Implementowanie struktury [Zero Trust](/security/zero-trust/) projektu
- Określanie wpisu w zabezpieczeniach przez przypisanie wyniku za pomocą bezpiecznego [wyniku firmy Microsoft](microsoft-secure-score.md)
- Zapobieganie zagrożeń w przypadku oceny luk w zabezpieczeniach w zarządzaniu [zagrożeniami i lukami](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Opis najnowszych zagrożeń bezpieczeństwa, aby przygotować się na nie za pomocą analizy [zagrożeń](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>Krok nr 1. Implementowanie Zero Trust

[Zero Trust](/security/zero-trust/) to zintegrowana strategia bezpieczeństwa uwzględniająca złożony charakter każdego nowoczesnego środowiska, łącznie z pracownikami telefonów komórkowych oraz użytkownikami, urządzeniami, aplikacjami i danymi niezależnie od tego, gdzie się znajdują. Udostępniając jedno okienko szyby w celu spójnego zarządzania wszystkimi wykrywaniami, program Microsoft 365 Defender może ułatwić zespołowi ds. zabezpieczeń wdrażanie zasad Zero Trust.[](/security/zero-trust/#guiding-principles-of-zero-trust) 

Składniki programu Microsoft 365 Defender mogą wyświetlać naruszenia reguł, które zostały zaimplementowane w celu ustanawiania zasad dostępu warunkowego dla programu Zero Trust przez integrowanie danych z Ochrona punktu końcowego w usłudze Microsoft Defender  lub innych dostawców zabezpieczeń mobilnych jako źródła informacji dla zasad zgodności urządzeń i implementacji zasad dostępu warunkowego opartych na urządzeniach. 

Ryzyko związane z urządzeniem ma bezpośredni wpływ na to, jakie zasoby będą dostępne dla użytkownika tego urządzenia. Odmowa dostępu do zasobów na podstawie określonych kryteriów to główny motyw programu Zero Trust, a program Microsoft 365 Defender udostępnia informacje potrzebne do określenia kryteriów poziomu zaufania. Na przykład Microsoft 365 Defender udostępnić poziom wersji oprogramowania urządzenia za pośrednictwem strony Zarządzanie zagrożeniami i lukami w zabezpieczeniach, natomiast zasady dostępu warunkowego ograniczają urządzenia, które są nieaktualne lub narażone na wersje.

Automatyzacja to kluczowy element wdrażania i utrzymywania środowiska Zero Trust, a także zmniejszania liczby alertów, które mogą doprowadzić do zdarzeń reagowania na incydenty (IR). Składniki usługi Microsoft 365 Defender, takie jak działania [naprawcze (znane](m365d-autoir.md) jako badania w związku z incydentem w portalu Microsoft 365 Defender), akcje powiadamiania, a nawet tworzenie biletów pomocy technicznej, na przykład w [SerwisNow](https://microsoft.service-now.com/sp/).

## <a name="step-2-determine-your-organizations-security-posture"></a>Krok nr 2. Określanie środków na bezpieczeństwo organizacji

Następnie organizacje mogą używać programu [Microsoft Secure Score](microsoft-secure-score.md) w programie Microsoft 365 Defender do określania bieżącej wydajności zabezpieczeń i rozważać zalecenia dotyczące sposobu jej ulepszania. Im wyższa jest ocena, tym więcej zaleceń dotyczących zabezpieczeń i działań udoskonalania zostały wykonane przez organizację. Zalecenia dotyczące bezpiecznego wyniku można podjąć w różnych produktach i umożliwić organizacjom podnoszenie swoich wyników jeszcze wyżej. 

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="Strona Microsoft Secure Score w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/first-incident-prepare/first-incident-secure-score.png":::
 
## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>Krok nr 3. Ocena luki w zabezpieczeniach organizacji

Zapobieganie incydentom może usprawnić działania związane z zabezpieczeniami w celu skupienia się na ważnych i ważnych zdarzeniach zabezpieczających w wydarzeniach, które mają miejsce w wydarzeniach. Luki w zabezpieczeniach oprogramowania są często punktem wejścia, który można zapobiec atakom, które mogą prowadzić do kradzieży danych, utraty danych lub przerwy w działaniu firmy. Jeśli żadne ataki nie będą się wytrzymywać, działania związane z zabezpieczeniami muszą starać się osiągnąć i utrzymać akceptowalny poziom luki w zabezpieczeniach [swojej organizacji](../defender-endpoint/tvm-exposure-score.md) .

Aby sprawdzić postęp poprawiania oprogramowania, odwiedź stronę Zarządzanie [](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) zagrożeniami i lukami w programie Defender for Endpoint, do której można uzyskać dostęp w programie Microsoft 365 Defender za pośrednictwem karty **Więcej** zasobów.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="Strona Zagrożenia i luk w zabezpieczeniach w portalu Microsoft 365 Defender sieci Web" lightbox="../../media/first-incident-prepare/first-incident-vulnerability.png"::: 
 
## <a name="4-understand-emerging-threats"></a>4. Zrozumienie wyłaniających się zagrożeń

Korzystaj [z analizy zagrożeń](threat-analytics.md) w portalu Microsoft 365 Defender, aby być na bieżąco z bieżącymi zagrożeniami bezpieczeństwa. Specjalista ds. bezpieczeństwa Firmy Microsoft tworzy raporty opisujące szczegółowo najnowsze cyberzagrożenia, aby zrozumieć, jak mogą one wpłynąć na Twoją subskrypcję Microsoft 365, urządzenia i użytkowników. Raporty te mogą obejmować:

- Aktywne działania podszywają się pod użytkowników i ich kampanie
- Popularne i nowe techniki ataków
- Krytyczne luki w zabezpieczeniach
- Typowe powierzchnie ataków
- Rozpowszechnione złośliwe oprogramowanie

Analiza zagrożeń przeszukuje również konfigurację i alerty, aby określić, jaki jest Twój ryzyko i czy do raportu mają zastosowanie aktywne alerty.

Możesz wdrożyć zalecenia dotyczące wyłaniających się zagrożeń, aby wzmocnić swoją pozycję zabezpieczeń i zminimalizować obszar ataków.

Poczekaj w harmonogramie na regularne sprawdzanie sekcji [Analiza](threat-analytics.md) zagrożeń w portalu Microsoft 365 Defender zagrożenia. Aby uzyskać [więcej informacji, zobacz przykładowe operacje Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender) zabezpieczeń.

## <a name="next-step"></a>Następny krok

[![Krok 1. Dowiedz się, jak ujednić i analizować zdarzenia.](../../media/first-incident-overview/first-incident-path-step1.png)](first-incident-analyze.md)

Dowiedz się, jak [ujednić i analizować zdarzenia](first-incident-analyze.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Badanie zdarzeń](investigate-incidents.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
