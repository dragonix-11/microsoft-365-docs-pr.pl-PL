---
title: Śledzenie pojawiających się zagrożeń i reagowanie na nie za pomocą analizy zagrożeń Ochrona punktu końcowego w usłudze Microsoft Defender
ms.reviewer: ''
description: Omówienie pojawiających się zagrożeń i technik ataków oraz sposobu ich zatrzymywania. Oceń ich wpływ na organizację i oceń odporność organizacji.
keywords: analiza zagrożeń, ocena ryzyka, ograniczanie ryzyka systemu operacyjnego, ograniczanie mikrokodów, stan ograniczania ryzyka
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 455b80f590edf255362c7bb047c7aa1b23916666
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128571"
---
# <a name="track-and-respond-to-emerging-threats-through-threat-analytics"></a>Śledzenie pojawiających się zagrożeń i reagowanie na nie za pomocą analizy zagrożeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Z bardziej zaawansowanych przeciwników i nowych zagrożeń pojawiających się często i powszechnie, ważne jest, aby móc szybko:

- Ocena wpływu nowych zagrożeń
- Przejrzyj odporność na zagrożenia lub narażenie na nie
- Identyfikowanie akcji, które można podjąć w celu zatrzymania lub ograniczenia zagrożeń

Analiza zagrożeń to zestaw raportów ekspertów badaczy zabezpieczeń firmy Microsoft obejmujących najbardziej istotne zagrożenia, w tym:

- Aktywni aktorzy zagrożeń i ich kampanie
- Popularne i nowe techniki ataków
- Krytyczne luki w zabezpieczeniach
- Typowe powierzchnie ataków
- Powszechnie stosowane złośliwe oprogramowanie

Każdy raport zawiera szczegółową analizę zagrożenia i obszerne wskazówki dotyczące sposobu obrony przed tym zagrożeniem. Obejmuje ona również dane z sieci, wskazujące, czy zagrożenie jest aktywne i czy masz odpowiednie zabezpieczenia.

Obejrzyj ten krótki film wideo, aby dowiedzieć się więcej o tym, jak analiza zagrożeń może pomóc w śledzeniu najnowszych zagrożeń i ich zatrzymywaniu.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bw1f]

## <a name="required-roles-and-permissions"></a>Wymagane role i uprawnienia
W poniższej tabeli przedstawiono role i uprawnienia wymagane do uzyskania dostępu do usługi Threat Analytics. Role zdefiniowane w poniższej tabeli odwołują się do ról niestandardowych w poszczególnych portalach i nie są połączone z rolami globalnymi w Azure AD, nawet jeśli mają podobną nazwę.

| **Jedna z następujących ról jest wymagana do Microsoft 365 Defender**  | **Jedna z następujących ról jest wymagana dla usługi Defender for Endpoint**  | **Jedna z następujących ról jest wymagana dla Ochrona usługi Office 365 w usłudze Defender** | **Jedna z następujących ról jest wymagana w przypadku aplikacji Defender dla Chmury** | 
|---------|---------|---------|---------|
| Analiza zagrożeń | Dane alertów i zdarzeń: <ul><li>Wyświetlanie danych — operacje zabezpieczeń</li></ul>Środki zaradcze tvm:<ul><li>Wyświetlanie danych — zagrożenia i zarządzanie lukami w zabezpieczeniach</li></ul> | Dane alertów i zdarzeń:<ul> <li>Alerty zarządzania tylko do wyświetlania</li> <li>Zarządzaj alertami</li> <li>Konfiguracja organizacji</li><li>Dzienniki inspekcji</li> <li>Dzienniki inspekcji tylko do wyświetlania</li><li>Czytelnik zabezpieczeń</li> <li>Administrator zabezpieczeń</li><li>Adresaci tylko do wyświetlania</li> </ul> Uniemożliwiono próby wysłania wiadomości e-mail: <ul><li>Czytelnik zabezpieczeń</li> <li>Administrator zabezpieczeń</li><li>Adresaci tylko do wyświetlania</li> | Niedostępne dla użytkowników Defender dla Chmury Apps lub MDI |

## <a name="view-the-threat-analytics-dashboard"></a>Wyświetlanie pulpitu nawigacyjnego analizy zagrożeń

Pulpit nawigacyjny analizy zagrożeń to doskonały punkt dostępu do raportów, które są najbardziej istotne dla Twojej organizacji. Zawiera podsumowanie zagrożeń w następujących sekcjach:

- **Najnowsze zagrożenia**: wyświetla listę ostatnio opublikowanych raportów o zagrożeniach wraz z liczbą urządzeń z aktywnymi i rozwiązanymi alertami.
- **Zagrożenia o dużym wpływie**: wyświetla listę zagrożeń, które miały największy wpływ na organizację. W tej sekcji osadza zagrożenia według liczby urządzeń, które mają aktywne alerty.
- **Podsumowanie zagrożeń**: pokazuje ogólny wpływ śledzonych zagrożeń, pokazując liczbę zagrożeń z aktywnymi i rozwiązanymi alertami.

Wybierz zagrożenie na pulpicie nawigacyjnym, aby wyświetlić raport dla tego zagrożenia.

:::image type="content" source="images/ta_dashboard.png" alt-text="Pulpit nawigacyjny analizy zagrożeń" lightbox="images/ta_dashboard.png":::

## <a name="view-a-threat-analytics-report"></a>Wyświetlanie raportu analizy zagrożeń

Każdy raport analizy zagrożeń zawiera informacje w trzech sekcjach: **Przegląd**, **Raport analityka** i **Środki zaradcze**.

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Omówienie: szybkie zrozumienie zagrożenia, ocena jego wpływu i przegląd zabezpieczeń

Sekcja **Przegląd** zawiera podgląd szczegółowego raportu analityka. Zawiera ona również wykresy, które wyróżniają wpływ zagrożenia dla organizacji i narażenia na nieskonfigurowane i nieprzypisane urządzenia.

:::image type="content" source="images/ta-overview.png" alt-text="Sekcja Przegląd raportu analizy zagrożeń" lightbox="images/ta-overview.png":::
_Sekcja Omówienie raportu analizy zagrożeń_

#### <a name="assess-the-impact-to-your-organization"></a>Ocena wpływu na organizację

Każdy raport zawiera wykresy przeznaczone do dostarczania informacji o organizacyjnym wpływie zagrożenia:

- **Urządzenia z alertami**: pokazuje bieżącą liczbę odrębnych urządzeń, na które miało wpływ zagrożenie. Urządzenie jest klasyfikowane jako **aktywne** , jeśli istnieje co najmniej jeden alert skojarzony z tym zagrożeniem i **rozwiązane** , jeśli *wszystkie* alerty skojarzone z zagrożeniem na urządzeniu zostały rozwiązane.
- **Urządzenia z alertami w czasie**: pokazuje liczbę odrębnych urządzeń z **aktywnymi** i **rozwiązanymi** alertami w czasie. Liczba rozwiązanych alertów wskazuje, jak szybko organizacja reaguje na alerty związane z zagrożeniem. Najlepiej, aby na wykresie były wyświetlane alerty rozwiązane w ciągu kilku dni.

#### <a name="review-security-resilience-and-posture"></a>Przegląd odporności i stanu zabezpieczeń

Każdy raport zawiera wykresy, które zawierają omówienie odporności organizacji na dane zagrożenie:

- **Stan konfiguracji zabezpieczeń**: pokazuje liczbę urządzeń, które zastosowały zalecane ustawienia zabezpieczeń, które mogą pomóc w wyeliminowaniu zagrożenia. Urządzenia są uznawane za **bezpieczne** , jeśli zastosowały _wszystkie_ śledzone ustawienia.
- **Stan stosowania poprawek luk w zabezpieczeniach**: pokazuje liczbę urządzeń, które zastosowały aktualizacje zabezpieczeń lub poprawki, które eliminują luki w zabezpieczeniach wykorzystywane przez zagrożenie.

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Raport analityków: uzyskiwanie szczegółowych informacji ekspertów od badaczy zabezpieczeń firmy Microsoft

Przejdź do sekcji **Raport analityka** , aby zapoznać się ze szczegółowym zapisem ekspertów. Większość raportów zawiera szczegółowe opisy łańcuchów ataków, w tym taktykę i techniki mapowane na strukturę MITRE ATT&CK, wyczerpujące listy zaleceń i zaawansowane wskazówki [dotyczące wyszukiwania zagrożeń](advanced-hunting-overview.md) .

[Dowiedz się więcej o raporcie analityka](threat-analytics-analyst-reports.md)

### <a name="mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Środki zaradcze: przejrzyj listę środków zaradczych i stan urządzeń

W sekcji **Środki zaradcze** przejrzyj listę konkretnych zaleceń umożliwiających podjęcie działań, które mogą pomóc zwiększyć odporność organizacji na zagrożenie. Lista śledzonych środków zaradczych obejmuje:

- **Aktualizacje zabezpieczeń**: wdrażanie aktualizacji zabezpieczeń lub poprawek dla luk w zabezpieczeniach
- **ustawienia Program antywirusowy Microsoft Defender**
  - Wersja analizy zabezpieczeń
  - Ochrona dostarczana przez chmurę
  - Ochrona potencjalnie niechcianej aplikacji (PUA)
  - Ochrona w czasie rzeczywistym

Informacje o ograniczaniu ryzyka w tej sekcji zawierają dane z [Zarządzanie zagrożeniami i lukami](next-gen-threat-and-vuln-mgt.md), które zawierają również szczegółowe informacje szczegółowe z różnych linków w raporcie.

:::image type="content" source="images/ta-mitigations.png" alt-text="Sekcja Środki zaradcze raportu analizy zagrożeń" lightbox="images/ta-mitigations.png":::


_Sekcja Środki zaradcze raportu analizy zagrożeń_

## <a name="additional-report-details-and-limitations"></a>Dodatkowe szczegóły raportu i ograniczenia

Podczas korzystania z raportów należy pamiętać o następujących kwestiach:

- Zakres danych zależy od zakresu kontroli dostępu opartej na rolach (RBAC). Stan urządzeń zostanie wyświetlony w [grupach, do których można uzyskać dostęp](machine-groups.md).
- Wykresy odzwierciedlają tylko śledzone środki zaradcze. Sprawdź omówienie raportu, aby uzyskać dodatkowe środki zaradcze, które nie są wyświetlane na wykresach.
- Środki zaradcze nie gwarantują całkowitej odporności. Podane środki zaradcze odzwierciedlają najlepsze możliwe działania potrzebne do zwiększenia odporności.
- Urządzenia są liczone jako "niedostępne", jeśli nie przesłały danych do usługi.
- Statystyki związane z programem antywirusowym są oparte na ustawieniach Program antywirusowy Microsoft Defender. Urządzenia z rozwiązaniami antywirusowymi innych firm mogą być wyświetlane jako "uwidocznione".

## <a name="related-topics"></a>Tematy pokrewne

- [Proaktywne znajdowanie zagrożeń przy użyciu zaawansowanego wyszukiwania zagrożeń](advanced-hunting-overview.md)
- [Omówienie sekcji raportu analityka](threat-analytics-analyst-reports.md)
- [Ocena i rozwiązywanie problemów ze słabościami i ekspozycjami w zakresie zabezpieczeń](next-gen-threat-and-vuln-mgt.md)
