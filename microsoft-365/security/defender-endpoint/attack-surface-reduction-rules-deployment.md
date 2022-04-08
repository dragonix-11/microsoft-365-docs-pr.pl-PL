---
title: Omówienie wdrażania reguł zmniejszania obszaru ataków (ASR)
description: Zawiera omówienie i wskazówki dotyczące wymagań wstępnych dotyczących wdrażania reguł zmniejszania obszaru ataków (ASR).
keywords: Wdrażanie reguł zmniejszania obszaru ataków, wdrażanie usługi ASR, włączanie reguł asr, konfigurowanie usługi ASR, system zapobiegania włamaniom do hostów, reguły ochrony, reguły ochrony przed lukami w zabezpieczeniach, reguły antyeksploatowania, reguły wykorzystujące luki w zabezpieczeniach, reguły zapobiegania zakażeniom, Ochrona punktu końcowego w usłudze Microsoft Defender, konfigurowanie reguł usługi ASR
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 8743d13939e73e25cefd08724d9a2f8d5a7fa410
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705543"
---
# <a name="attack-surface-reduction-asr-rules-deployment-overview"></a>Omówienie wdrażania reguł zmniejszania obszaru ataków (ASR)

Powierzchnie ataków to wszystkie miejsca, w których organizacja jest narażona na ataki cybernetyczne i ataki. Obszar ataków organizacji obejmuje wszystkie miejsca, w których osoba atakująca może naruszyć bezpieczeństwo urządzeń lub sieci organizacji. Zmniejszenie obszaru ataków oznacza ochronę urządzeń i sieci organizacji, co sprawia, że osoby atakujące mają mniej sposobów ataku. Konfigurowanie reguł zmniejszania obszaru ataków (ASR) — jednej z wielu funkcji zabezpieczeń znajdujących się w Ochrona punktu końcowego w usłudze Microsoft Defender — może pomóc.

Reguły usługi ASR dotyczą pewnych zachowań oprogramowania, takich jak:

- Uruchamianie plików wykonywalnych i skryptów, które próbują pobrać lub uruchomić pliki
- Uruchamianie zaciemnionych lub w inny sposób podejrzanych skryptów
- Zachowania, których aplikacje zwykle nie występują podczas normalnej codziennej pracy

Zmniejszając różne powierzchnie ataków, możesz przede wszystkim zapobiec atakom.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Podczas wstępnego przygotowywania ważne jest, aby zrozumieć możliwości systemów, które zostaną wprowadzone. Zrozumienie możliwości pomoże Ci określić, które reguły usługi ASR są najważniejsze dla ochrony organizacji. Ponadto istnieje kilka wymagań wstępnych, które należy spełnić podczas przygotowywania wdrożenia usługi ASR.

>[!IMPORTANT]
>Ten przewodnik zawiera obrazy i przykłady ułatwiające podjęcie decyzji o sposobie konfigurowania reguł usługi ASR. te obrazy i przykłady mogą nie odzwierciedlać najlepszych opcji konfiguracji środowiska.

Przed rozpoczęciem zapoznaj się [z omówieniem zmniejszania obszaru podatnego na ataki](overview-attack-surface-reduction.md) i [demistyfikacją reguł zmniejszania obszaru podatnego na ataki — część 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) , aby uzyskać podstawowe informacje. Aby zrozumieć obszary pokrycia i potencjalny wpływ, zapoznaj się z bieżącym zestawem reguł usługi ASR; zobacz [Dokumentacja reguł zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md).  Podczas zapoznania się z zestawem reguł usługi ASR zanotuj mapowania identyfikatorów GUID dla reguł; zobacz: [Macierz reguł i identyfikatorów GUID usługi ASR](attack-surface-reduction-rules-reference.md#asr-rules-and-guids-matrix).

Reguły asr to tylko jedna z możliwości zmniejszania obszaru ataków w ramach Ochrona punktu końcowego w usłudze Microsoft Defender. Ten dokument zawiera bardziej szczegółowe informacje na temat efektywnego wdrażania reguł usługi ASR w celu powstrzymania zaawansowanych zagrożeń, takich jak oprogramowanie wymuszające okup obsługiwane przez człowieka i inne zagrożenia.  

### <a name="rules-by-category"></a>Reguły według kategorii

Jak opisano w artykule [Używanie reguł zmniejszania obszaru ataków w celu zapobiegania infekcji złośliwym oprogramowaniem](attack-surface-reduction.md), w środowisku MDE istnieje wiele reguł zmniejszania obszaru ataków, które można włączyć w celu ochrony organizacji. Poniżej przedstawiono reguły podzielone według kategorii:

<br/>

| Zagrożenia polimorficzne | Przenoszenie poprzeczne & kradzież poświadczeń | Reguły aplikacji zwiększających produktywność |  Reguły poczty e-mail | Reguły skryptów | Reguły błędów |
|:---|:---|:---|:---|:---|:---|
| Blokuj uruchamianie plików wykonywalnych, chyba że spełniają one częstość występowania (1000 maszyn), wiek (24 godziny) lub kryteria listy zaufanych | Blokuj tworzenie procesów pochodzących z poleceń PSExec i WMI | Blokowanie tworzenia zawartości wykonywalnej przez aplikacje Office | Blokuj zawartość wykonywalną z klienta poczty e-mail i poczty internetowej | Blokuj zaciemniony kod JS/VBS/PS/macro | Blokowanie nadużyć wobec wykorzystywanych kierowców <sup>podpisanych w trudnej sytuacji [[1](#fn1)]<sup></sup>  |
| Blokuj niezaufane i niepodpisane procesy uruchamiane z portu USB | Blokuj kradzież poświadczeń z podsystemu Windows lokalnego urzędu zabezpieczeń (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Blokowanie tworzenia procesów podrzędnych przez aplikacje Office |  Blokuj tworzenie procesów podrzędnych tylko Office aplikacjom komunikacyjnym | Blokuj uruchamianie pobranej zawartości wykonywalnej JS/VBS | |
| Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup | Blokuj trwałość za pośrednictwem subskrypcji zdarzeń WMI | Blokuj Office aplikacjom wstrzykiwanie kodu do innych procesów | Blokowanie tworzenia procesów podrzędnych przez aplikacje komunikacji Office | | |
| | | Zablokuj programowi Adobe Reader tworzenie procesów podrzędnych | | | |

(<a id="fn1">1</a>) _Blokowanie nadużywania wykorzystywanych, narażonych na zagrożenia sterowników podpisanych_ nie jest obecnie dostępne w zabezpieczeniach punktu końcowego MEM. Tę regułę można skonfigurować przy użyciu [identyfikatora OMA-URI MEM](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) Niektóre reguły usługi ASR generują znaczny szum, ale nie blokują funkcjonalności. Jeśli na przykład aktualizujesz przeglądarę Chrome; Przeglądarka Chrome będzie uzyskiwać dostęp do lsass.exe; hasła są przechowywane w systemie lsass na urządzeniu. Przeglądarka Chrome nie powinna jednak uzyskiwać dostępu do lsass.exe urządzeń lokalnych. Jeśli włączysz regułę, aby zablokować dostęp do lsass, spowoduje to wygenerowanie wielu zdarzeń. Te zdarzenia są dobrymi zdarzeniami, ponieważ proces aktualizacji oprogramowania nie powinien uzyskiwać dostępu lsass.exe. Włączenie tej reguły zablokuje dostęp aktualizacji przeglądarki Chrome do systemu lsass, ale nie zablokuje aktualizacji przeglądarki Chrome. Dotyczy to również innych aplikacji, które wywołują niepotrzebne wywołania lsass.exe. _Blokuj dostęp do reguły lsass_ zablokuje niepotrzebne wywołania lsass, ale nie zablokuje uruchamiania aplikacji.

### <a name="infrastructure-requirements"></a>Wymagania dotyczące infrastruktury

Mimo że istnieje wiele metod implementowania reguł usługi ASR, ten przewodnik jest oparty na infrastrukturze składającej się z następujących elementów:

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- urządzenia Windows 10 i Windows 11
- licencje Ochrona punktu końcowego w usłudze Microsoft Defender E5 lub Windows E5

Aby w pełni wykorzystać reguły i raportowanie usługi ASR, zalecamy korzystanie z licencji Microsoft 365 Defender E5 lub Windows E5 i A5. Dowiedz się więcej: [Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender](minimum-requirements.md).

>[!Note]
>Istnieje wiele metod konfigurowania reguł usługi ASR. Reguły usługi ASR można skonfigurować przy użyciu: Microsoft Endpoint Manager (MEM), PowerShell, zasady grupy, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Jeśli używasz innej konfiguracji infrastruktury niż wymieniona w _wymaganiach dotyczących infrastruktury_ (powyżej), możesz dowiedzieć się więcej na temat wdrażania reguł zmniejszania obszaru ataków przy użyciu innych konfiguracji tutaj: [Włącz reguły zmniejszania obszaru ataków](enable-attack-surface-reduction.md).  

### <a name="asr-rules-dependencies"></a>Zależności reguł usługi ASR

Program antywirusowy Microsoft Defender musi być włączona i skonfigurowana jako podstawowe rozwiązanie antywirusowe i musi być w następującym trybie:

- Podstawowe rozwiązanie antywirusowe/chroniące przed złośliwym kodem  
- Stan: Tryb aktywny

Program antywirusowy Microsoft Defender nie może być w żadnym z następujących trybów:

- Pasywne
- Tryb pasywny z wykrywaniem i reagowaniem punktów końcowych (EDR) w trybie bloku
- Ograniczone okresowe skanowanie (LPS)
- Wył.

Zobacz: [Ochrona i Program antywirusowy Microsoft Defender dostarczane w chmurze](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>Usługa Cloud Protection (MAPS) musi być włączona

Program antywirusowy Microsoft Defender bezproblemowo współpracuje z usługami firmy Microsoft w chmurze. Te usługi ochrony w chmurze, nazywane również usługą Microsoft Advanced Protection Service (MAPS), zwiększają standardową ochronę w czasie rzeczywistym, zapewniając prawdopodobnie najlepszą ochronę antywirusową. Ochrona w chmurze ma kluczowe znaczenie dla zapobiegania naruszeniom złośliwego oprogramowania i krytycznego składnika reguł usługi ASR.
[Włącz ochronę dostarczaną przez chmurę w Program antywirusowy Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>składniki Program antywirusowy Microsoft Defender muszą być bieżącymi wersjami

Następujące Program antywirusowy Microsoft Defender wersje składników muszą być nie więcej niż dwie wersje starsze niż najbardziej dostępna wersja:

- **wersja aktualizacji platformy Program antywirusowy Microsoft Defender** — platforma Program antywirusowy Microsoft Defender jest aktualizowana co miesiąc.
- **Program antywirusowy Microsoft Defender wersji aparatu** — aparat Program antywirusowy Microsoft Defender jest aktualizowany co miesiąc.
- **Program antywirusowy Microsoft Defender analizy zabezpieczeń** — firma Microsoft stale aktualizuje analizę zabezpieczeń usługi Microsoft Defender (znaną również jako definicja i podpis) w celu rozwiązania najnowszych zagrożeń oraz uściślenia logiki wykrywania.

Utrzymywanie bieżących wersji Program antywirusowy Microsoft Defender pomaga zmniejszyć liczbę reguł asr wyników fałszywie dodatnich i zwiększa możliwości wykrywania Program antywirusowy Microsoft Defender. Aby uzyskać więcej informacji na temat bieżących wersji i sposobu aktualizowania różnych składników Program antywirusowy Microsoft Defender, odwiedź [stronę obsługa platformy Program antywirusowy Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>Zastrzeżeniem

Niektóre reguły nie działają dobrze, jeśli niepodpisane, wewnętrznie opracowane aplikacje i skrypty są w dużym użyciu. Wdrażanie reguł usługi ASR jest trudniejsze, jeśli podpisywanie kodu nie jest wymuszane.

## <a name="asr-rules-deployment-steps"></a>Kroki wdrażania reguł usługi ASR

Podobnie jak w przypadku każdej nowej implementacji na szeroką skalę, która może potencjalnie mieć wpływ na operacje biznesowe, ważne jest, aby być metodycznym w planowaniu i implementacji. Ze względu na zaawansowane możliwości reguł usługi ASR w zapobieganiu złośliwemu oprogramowaniu należy starannie zaplanować i wdrożyć te reguły, aby upewnić się, że działają najlepiej w przypadku unikatowych przepływów pracy klientów. Aby pracować w środowisku, musisz dokładnie planować, testować, implementować i obsługiwać reguły usługi ASR.  

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="Fazy wdrażania reguł usługi ASR" lightbox="images/asr-rules-deployment-phases.png":::

>[!Note]
>W przypadku klientów, którzy korzystają z rozwiązania HIPS firmy innej niż Microsoft i przechodzą na Ochrona punktu końcowego w usłudze Microsoft Defender reguły zmniejszania obszaru podatnego na ataki: firma Microsoft zaleca klientom równoległe uruchamianie rozwiązania HIPS z wdrożeniem reguł usługi ASR do momentu przejścia z trybu inspekcji na tryb bloku. Należy pamiętać, że aby uzyskać zalecenia dotyczące wykluczeń, należy skontaktować się z dostawcą oprogramowania antywirusowego innej firmy.  

## <a name="additional-topics-in-this-deployment-collection"></a>Dodatkowe tematy w tej kolekcji wdrożeń

[Reguły zmniejszania obszaru ataków testowych (ASR)](attack-surface-reduction-rules-deployment-test.md)

[Włączanie reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-implement.md)

[Operacjonalizowanie reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

[Dokumentacja reguł zmniejszania obszaru ataków (ASR)](attack-surface-reduction-rules-reference.md)

## <a name="reference"></a>Odwołanie

### <a name="blogs"></a>Blogi

[Demistyfikacja reguł zmniejszania obszaru podatnego na ataki — część 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Demistyfikacja reguł zmniejszania powierzchni ataków — część 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Demistyfikacja reguł zmniejszania powierzchni ataków — część 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Demistyfikacja reguł zmniejszania obszaru podatnego na ataki — część 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>Kolekcja usługi ASR

[Omówienie zmniejszania obszaru podatnego na ataki](overview-attack-surface-reduction.md)

[Używanie reguł zmniejszania obszaru ataków w celu zapobiegania infekcji złośliwym oprogramowaniem](attack-surface-reduction.md)

[Włączanie reguł zmniejszania obszaru ataków — alternatywne konfiguracje](enable-attack-surface-reduction.md)

[Dokumentacja reguł zmniejszania obszaru podatnego na ataki](attack-surface-reduction-rules-reference.md)

[Zmniejszanie obszaru podatnego na ataki — często zadawane pytania](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)

[Ochrona i Program antywirusowy Microsoft Defender dostarczane przez chmurę](cloud-protection-microsoft-defender-antivirus.md)

[Włączanie ochrony dostarczanej w chmurze w Program antywirusowy Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md)

[Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia, nazwy lub lokalizacji](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[obsługa platformy Program antywirusowy Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md)

[Omówienie spisu w centrum administracyjnym Aplikacje Microsoft 365](/deployoffice/admincenter/inventory)

[Tworzenie planu wdrożenia dla Windows](/windows/deployment/update/create-deployment-plan)

[Używanie kontroli dostępu opartej na rolach (RBAC) i tagów zakresu dla rozproszonej infrastruktury IT w Intune](/mem/intune/fundamentals/scope-tags)

[Przypisywanie profilów urządzeń w Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Lokacje zarządzania

[centrum administracyjne Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home)

[Zmniejszanie obszaru podatnego na ataki](https://security.microsoft.com/asr?viewid=detections)

[Konfiguracje reguł usługi ASR](https://security.microsoft.com/asr?viewid=configuration)

[Wykluczenia reguł usługi ASR](https://security.microsoft.com/asr?viewid=exclusions)
