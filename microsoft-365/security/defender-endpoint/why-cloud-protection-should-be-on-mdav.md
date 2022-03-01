---
title: Dlaczego ochrona chmury powinna być włączona dla Program antywirusowy Microsoft Defender
description: Sprawdź, dlaczego ochrona chmury powinna być włączona dla Program antywirusowy Microsoft Defender. Pomaga ona w pracy z wieloma funkcjami zabezpieczeń w programie Microsoft Defender for Endpoint
keywords: Program antywirusowy Microsoft Defender, ochrona w chmurze, funkcje zabezpieczeń, przykładowe przesyłanie
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/22/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 0dc1279f59ac272031067c415354f1f615ead205
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009573"
---
# <a name="why-cloud-protection-should-be-enabled-for-microsoft-defender-antivirus"></a>Dlaczego ochrona chmury powinna być włączona dla Program antywirusowy Microsoft Defender

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Program antywirusowy Microsoft Defender

Program antywirusowy Microsoft Defender ochrony chmury pomaga chronić przed złośliwym oprogramowaniem w punktach końcowych i w całej sieci. Zalecamy, aby ochrona chmury została włączona, ponieważ pewne funkcje i możliwości zabezpieczeń w programie Microsoft Defender for Endpoint działają tylko wtedy, gdy jest włączona ochrona w chmurze. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="Diagram przedstawiający rzeczy, które zależą od ochrony chmury":::](enable-cloud-protection-microsoft-defender-antivirus.md)

W poniższej tabeli podsumowano funkcje i możliwości, które zależą od ochrony chmury: <br/><br/>

| Funkcja/funkcja  | Wymaganie subskrypcji |  Opis  |
|---------|---------|--------|
| Sprawdzanie zgodności z metadanymi w chmurze  | Microsoft Defender for Endpoint Plan 1 lub Plan 2 (autonomiczny lub uwzględniony w planie, Microsoft 365 E3 lub E5) | Usługa Program antywirusowy Microsoft Defender w chmurze korzysta z modeli uczenia maszynowego jako dodatkowej warstwy obrony. Te modele uczenia maszynowego zawierają metadane, więc w przypadku wykrycia podejrzanego lub złośliwego pliku ich metadane są sprawdzane. <br/><br/>Aby dowiedzieć się więcej, zobacz Blog: Poznaj zaawansowane technologie w podstawowym zakresie ochrony programu [Microsoft Defender for Endpoint następnej generacji](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)  |
| Ochrona chmury i przesyłanie próbek | Microsoft Defender for Endpoint Plan 1 lub Plan 2 (autonomiczny lub uwzględniony w planie, Microsoft 365 E3 lub E5) | Pliki i pliki wykonywalne mogą być wysyłane do usługi Program antywirusowy Microsoft Defender w chmurze w celu detonacji i analizy. <br/><br/>Aby dowiedzieć się więcej, zobacz [Ochrona chmury i przykładowe przesyłanie w aplikacji Program antywirusowy Microsoft Defender](cloud-protection-microsoft-antivirus-sample-submission.md).<br/><br/>**UWAGA**: Automatyczne przesyłanie próbek korzysta z ochrony chmury, ale można je też skonfigurować jako ustawienie autonomiczne.         |
| Ochrona przed naruszeniami | Microsoft Defender for Endpoint Plan 2 (Standalone or included in a plan like Microsoft 365 E5) | Ochrona przed naruszeniami ułatwia ochronę przed niechcianymi zmianami w ustawieniach zabezpieczeń organizacji. Aby wymusić ochronę przed naruszeniami w portalu Microsoft 365 Defender, należy włączyć ochronę w chmurze. <br/><br/>Aby dowiedzieć się więcej, zobacz [Ochrona ustawień zabezpieczeń za pomocą ochrony przed naruszeniami](prevent-changes-to-security-settings-with-tamper-protection.md).        |
| Blokuj na pierwszy rzut oka | Microsoft Defender for Endpoint Plan 1 lub Plan 2 (autonomiczny lub uwzględniony w planie, Microsoft 365 E3 lub E5) | Zablokuj na pierwszy rzut oka wykrywa nowe złośliwe oprogramowanie i blokuje je w ciągu kilku sekund. Po wykryciu podejrzanego lub złośliwego pliku zablokuj możliwości funkcji ochrony w chmurze na pierwszy rzut oka i stosuje heuristics, uczenie maszynowe oraz automatyczną analizę pliku w celu ustalenia, czy plik jest zagrożeniem.<br/><br/>Aby dowiedzieć się więcej, [zobacz Co to jest "blok na pierwszy rzut oka"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)   |
| Aktualizacje podpisu dla służb ratunkowych | Microsoft Defender for Endpoint Plan 2 (Standalone or included in a plan like Microsoft 365 E5) | W przypadku wykrycia złośliwej zawartości wdrażane są aktualizacje i poprawki dotyczące podpisów dla służb ratunkowych. Zamiast czekać na następną zwykłą aktualizację, możesz otrzymać te poprawki i aktualizacje w ciągu kilku minut.   |
| Wykrywanie punktu końcowego i odpowiedź (EDR) w trybie blokowania | Microsoft Defender for Endpoint Plan 2 (Standalone or included in a plan like Microsoft 365 E5) | EDR trybie blokowania zapewnia dodatkową ochronę, gdy Program antywirusowy Microsoft Defender nie jest podstawowym produktem antywirusowym na urządzeniu. EDR trybie blokowania środki zaradcze dotyczące artefaktów znalezionych EDR w trakcie skanów wygenerowanych przez inne firmy, które nie zostały pominięte w podstawowym rozwiązaniu antywirusowym innych niż firma Microsoft. Po włączeniu dla urządzeń z programem Program antywirusowy Microsoft Defender jako podstawowym rozwiązaniem antywirusowym program EDR w trybie blokowania zapewnia dodatkową korzyść z automatycznego korygowania artefaktów zidentyfikowanych podczas skanowania EDR wygenerowanych. <br/><br/>Aby dowiedzieć się więcej, zobacz [EDR w trybie blokowania](edr-in-block-mode.md).|
| Reguły zmniejszania obszaru podatnego na ataki | Microsoft Defender for Endpoint Plan 1 lub Plan 2 (autonomiczny lub uwzględniony w planie, Microsoft 365 E3 lub E5) | Zmniejszenie powierzchni ataków ma na celu zmniejszenie liczby miejsc i sposobów, w jakie punkty końcowe organizacji są narażone na cyberataki. Reguły zmniejszania powierzchni ataków to inteligentne reguły, które można skonfigurować w celu zatrzymania złośliwego oprogramowania. Niektóre reguły wymagają, aby ochrona chmury została włączona w celu pełnego działania. Są to między innymi następujące reguły: <br/>— Zablokować uruchamianie plików wykonywalnych, jeśli nie spełniają one kryteriów listy osób, wieku lub listy zaufanych. <br/>- Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup <br/>- Blokowanie uruchamiania niezaufanych programów z dysków wymiennych <br/><br/>Aby dowiedzieć się więcej, zobacz [Stosowanie reguł usuwania powierzchni ataków w celu zapobiegania zainfekowaniu złośliwym oprogramowaniem](attack-surface-reduction.md).  |
| Wskaźniki naruszenia bezpieczeństwa (IoCs) | Microsoft Defender for Endpoint Plan 2 (Standalone or included in a plan like Microsoft 365 E5) | W programie Defender for Endpoint można skonfigurować wykrywanie, zapobieganie i wykluczenie obiektów. Na przykład za pomocą wskaźników "zezwalaj" można definiować wyjątki dla skanowania i Program antywirusowy Microsoft Defender w programie Defender dla punktu końcowego. Ponadto za pomocą wskaźników "alertów i bloków" można zapobiegać wykonaniu plików lub procesów oraz śledzić te działania za pomocą alertów, które można wyświetlać w portalu Microsoft 365 Defender. <br/><br/>Aby dowiedzieć się więcej, zobacz [Tworzenie wskaźników](manage-indicators.md).    |

> [!TIP]
> Aby dowiedzieć się więcej o programie Defender dla planów punktów końcowych, zobacz [Program Microsoft Defender dla planu punktu końcowego 1 i planu 2](defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>Następne kroki

Teraz, gdy masz omówienie ochrony chmury i jej roli w programie Program antywirusowy Microsoft Defender, poniżej przedstawiono kilka następnych kroków:

1. **[Włączanie ochrony w chmurze](enable-cloud-protection-microsoft-defender-antivirus.md)**. Ochronę chmury można włączyć Microsoft Endpoint Manager poleceń cmdlet programu Microsoft Endpoint Manager (które teraz obejmują polecenia cmdlet Microsoft Endpoint Configuration Manager i Microsoft Intune), zasady grupy lub PowerShell.

2. **[Określ poziom ochrony w chmurze](specify-cloud-protection-level-microsoft-defender-antivirus.md)**. Możesz określić poziom ochrony oferowany przez chmurę przy użyciu Microsoft Endpoint Manager lub zasady grupy. Poziom ochrony wpływa na ilość informacji udostępnianych w chmurze i na to, jak bardzo nowe pliki są blokowane.

3. **[Konfigurowanie i sprawdzanie poprawności połączeń sieciowych Program antywirusowy Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)**. Istnieją pewne adresy URL firmy Microsoft, z których sieć i punkty końcowe muszą być w stanie nawiązać połączenie, aby ochrona chmury działała efektywnie. Ten artykuł zawiera listę adresów URL, które powinny być dozwolone za pośrednictwem reguł filtrowania sieci lub zapory, oraz instrukcje potwierdzenia, że sieć jest poprawnie zarejestrowanych w ramach ochrony chmury.

4. **[Konfigurowanie funkcji blokowania na pierwszy rzut oka](configure-block-at-first-sight-microsoft-defender-antivirus.md)**. Funkcja "blokuj na pierwszy rzut oka" może zablokować nowe złośliwe oprogramowanie w ciągu kilku sekund, bez konieczności oczekiwania godzin na tradycyjne analizy zabezpieczeń. Możesz go włączyć i skonfigurować przy użyciu Microsoft Endpoint Manager lub zasady grupy.

5. **[Konfigurowanie limitu czasu blokowania chmury](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)**. Program antywirusowy Microsoft Defender możliwość uruchamiania podejrzanych plików podczas zapytania przez naszą usługę ochrony w chmurze. Możesz skonfigurować czas, przez jaki plik nie będzie mógł być uruchomiony, używając Microsoft Endpoint Manager lub zasady grupy.
