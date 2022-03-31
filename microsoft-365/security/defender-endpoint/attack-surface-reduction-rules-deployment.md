---
title: Wymagania wstępne wdrażania reguł asr
description: Ten temat zawiera omówienie i wstępnie wymagane wskazówki dotyczące wdrażania reguł ograniczania powierzchni ataków (ASR).
keywords: Wdrażanie reguł ograniczania powierzchni ataków, wdrażanie asr, włączanie reguł asr, konfigurowanie funkcji asr, systemu ochrony przed nieuprawnianiem hostów, reguł ochrony, reguł ochrony przed wykorzystywaniem luk, ochrony przed wykorzystywaniem, regułami wykorzystania luk, regułami zapobiegania powstawaniu dzieci, Ochrona punktu końcowego w usłudze Microsoft Defender, konfigurowanie reguł asr
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
ms.openlocfilehash: 4703867449877a35d6621b76072b9420a0cdbdec
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520556"
---
# <a name="asr-rules-deployment-prerequisites"></a>Wymagania wstępne wdrażania reguł asr

## <a name="before-you-begin"></a>Przed rozpoczęciem

Powierzchnie ataków to wszystkie miejsca, w których Twoja organizacja jest narażona na cyberataki i ataki. Powierzchnie ataków organizacji obejmują wszystkie miejsca, w których atakujący mogą naruszonć urządzenia lub sieci organizacji. Zmniejszenie powierzchni ataków oznacza ochronę urządzeń i sieci organizacji, co pozostawia atakującym mniej sposobów ataków. Skonfigurowanie reguł zmniejszania powierzchni ataków (ASR, Attack Surface Reduction) — jednej z wielu funkcji zabezpieczeń, które można Ochrona punktu końcowego w usłudze Microsoft Defender — może pomóc.

Reguły ASR mają na celu określone zachowania oprogramowania, takie jak:

- Uruchamianie plików wykonywalnych i skryptów próbujących pobierać lub uruchamiać pliki
- Uruchamianie skryptów zasłoconych lub w inny sposób podejrzanych skryptów
- Zachowania, które aplikacje zwykle nie występują w trakcie normalnej pracy

Zmniejszenie różnych powierzchni ataków pozwala zapobiec atakom w pierwszej kolejności.

Podczas wstępnego przygotowania należy pamiętać o zrozumieniu możliwości systemów, które należy wprowadzić. Znajomość tych możliwości pomoże w określeniu, które reguły asr są najważniejsze dla ochrony organizacji. Ponadto istnieje kilka wymagań wstępnych, w których należy wziąć udział w przygotowaniu wdrożenia usługi ASR.

>[!IMPORTANT]
>Ten przewodnik zawiera obrazy i przykłady, które ułatwiają skonfigurowanie reguł asr. te obrazy i przykłady mogą nie odzwierciedlać najlepszych opcji konfiguracji dla Twojego środowiska.

Przed rozpoczęciem zapoznaj się z [](overview-attack-surface-reduction.md)omówieniem zmniejszenia powierzchni ataków i Reguł zmniejszania powierzchni ataków bez zamierzeniu [— część 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420), aby uzyskać informacje o podstawach. Aby zrozumieć obszary zasięgu i potencjalny wpływ, zapoznaj się z bieżącym zestawem reguł asr. zobacz [Informacje dotyczące reguł zmniejszania powierzchni ataków](attack-surface-reduction-rules-reference.md).  Podczas poznania zestawu reguł ASR warto zanotować mapowania identyfikatorów GUID  per-rule. zobacz: [Reguły asr i macierz identyfikatorów GUID](attack-surface-reduction-rules-reference.md#asr-rules-and-guids-matrix).

Reguły ASR to tylko jedna funkcja funkcji ograniczania powierzchni ataków w Ochrona punktu końcowego w usłudze Microsoft Defender. Ten dokument zawiera bardziej szczegółowe informacje na temat skutecznego wdrażania reguł asr w celu zatrzymania zaawansowanych zagrożeń, takich jak oprogramowanie wymuszające okup obsługiwane przez człowieka i inne zagrożenia.  

### <a name="rules-by-category"></a>Reguły według kategorii

Jak opisano [w](attack-surface-reduction.md) tece Używaj reguł zmniejszania powierzchni ataków, aby zapobiegać zainfekowaniu złośliwym oprogramowaniem, istnieje wiele reguł usuwania powierzchni ataków w ramach usługi MDE, które możesz włączyć do ochrony swojej organizacji. Poniżej przedstawiono reguły podzielone według kategorii:

<br/>

| Zagrożenia polymorphic | Ruchy boczne i & kradzież poświadczeń | Reguły aplikacji zwiększających produktywność |  Reguły poczty e-mail | Reguły skryptów | Różne reguły |
|:---|:---|:---|:---|:---|:---|
| Blokuj uruchamianie plików wykonywalnych, jeśli nie spełniają one wymagań co najmniej 1000 komputerów, wieku (24 godziny) lub kryteriów listy zaufanych | Blokowanie procesów pochodzących z poleceń PSExec i WMI | Blokowanie Office tworzenia zawartości wykonywalnego przez aplikacje | Blokowanie pliku wykonywalnego zawartości z klienta poczty e-mail i poczty internetowej | Blokowanie kodu makra JS/VBS/PS/makra | Blokowanie nadużyć wykorzystywania w celu wykorzystania podpisanych sterowników <sup>[[1](#fn1)]<sup></sup>  |
| Blokowanie niezaufanych i niepodpisanych procesów uruchamianych z usb | Blokowanie kradzieży poświadczeń z podsystemu Windows Security Authority (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Blokowanie Office aplikacji przed tworzeniem procesów podrzędnych |  Blokowanie tworzenia procesów Office do komunikacji tylko przez aplikacje komunikacyjne | Blokowanie uruchamiania pobranej zawartości wykonywanej przez JS/VBS | |
| Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup | Blokowanie utrwaloności za pośrednictwem subskrypcji zdarzeń usługi WMI | Blokowanie Office aplikacji z uwzględnieniem kodu w innych procesach | Blokowanie Office aplikacji do komunikacji z tworzeniem procesów podrzędnych | | |
| | | Blokowanie tworzenia procesów podrzędnych przez program Adobe Reader | | | |

(<a id="fn1">1</a>) Blokowanie _nadużyć wykorzystywania wyeksowanych_ podatnych na zagrożenia sterowników podpisanych nie jest obecnie dostępne w zabezpieczeniach punktów końcowych MEM. Tę regułę można skonfigurować przy [użyciu narzędzia OMA-URI MEM](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) Niektóre reguły asr generują dużo szumu, ale nie blokują funkcjonalności. Jeśli na przykład aktualizujesz przeglądarkę Chrome; Przeglądarka Chrome będzie mieć dostęp do lsass.exe; hasła są przechowywane w lsass na urządzeniu. Jednak przeglądarka Chrome nie powinna mieć dostępu do urządzenia lsass.exe. Włączenie reguły blokowania dostępu do lsass spowoduje wygenerowanie wielu zdarzeń. Są to dobre zdarzenia, ponieważ proces aktualizacji oprogramowania nie powinien mieć dostępu do lsass.exe. Włączenie tej reguły zablokuje dostęp do aktualizacji przeglądarki Chrome, ale nie zablokuje możliwości aktualizacji w przeglądarce Chrome. jest tak też w przypadku innych aplikacji, które niepotrzebnie dzwonią do lsass.exe. Reguła _blokowania dostępu do lsass blokuje_ niepotrzebne połączenia z usługą lsass, ale nie blokuje uruchamiania aplikacji.

### <a name="infrastructure-requirements"></a>Wymagania dotyczące infrastruktury

Chociaż istnieje wiele metod implementowania reguł asr, ten przewodnik jest oparty na infrastrukturze składającej się z:

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- Windows 10 i Windows 11 urządzenia
- Ochrona punktu końcowego w usłudze Microsoft Defender E5 lub Windows E5

Aby w pełni wykorzystać reguły asr i raportowanie, zalecamy używanie licencji usługi Microsoft 365 Defender E5 lub Windows E5 i A5. Dowiedz się więcej: [Minimalne wymagania dotyczące Ochrona punktu końcowego w usłudze Microsoft Defender](minimum-requirements.md).

>[!Note]
>Istnieje wiele metod konfigurowania reguł asr. Reguły ASR można skonfigurować przy użyciu: Microsoft Endpoint Manager (MEM), PowerShell, zasady grupy, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Jeśli korzystasz z konfiguracji infrastruktury innej niż wymieniona w powyższych  wymaganiach dotyczących infrastruktury, [tutaj możesz dowiedzieć](enable-attack-surface-reduction.md) się więcej o wdrażaniu reguł ograniczania powierzchni ataków przy użyciu innych konfiguracji: Włączanie reguł ograniczania powierzchni ataków.  

### <a name="asr-rules-dependencies"></a>Zależności reguł ASR

Program antywirusowy Microsoft Defender musi być włączone i skonfigurowane jako podstawowe rozwiązanie antywirusowe, a także musi być w następującym trybie:

- Podstawowe rozwiązanie antywirusowe/ochrony przed złośliwym oprogramowaniem  
- Stan: tryb aktywny

Program antywirusowy Microsoft Defender nie mogą być w żadnym z następujących trybów:

- Strona pasywna
- Tryb pasywny z wykrywaniem punktu końcowego i odpowiedzią (EDR) w trybie blokowania
- Ograniczone skanowanie okresowe (LPS)
- Wyłączone

Zobacz: [Ochrona i ochrona w chmurze Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>Musi być włączona ochrona w chmurze (MAPY)

Program antywirusowy Microsoft Defender bezproblemowo współpracuje z usługami firmy Microsoft w chmurze. Te usługi ochrony w chmurze, nazywane także usługą Microsoft Advanced Protection Service (MAPS), rozszerzają standardową ochronę w czasie rzeczywistym, zapewniając prawdopodobnie najlepszą ochronę antywirusową. Ochrona chmury jest bardzo ważna w celu zapobiegania naruszeniem bezpieczeństwa przez złośliwe oprogramowanie i krytycznym składnikiem reguł asr.
[Włączanie ochrony w chmurze w programie Program antywirusowy Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Program antywirusowy Microsoft Defender składniki muszą być wersjami bieżącymi

Następujące Program antywirusowy Microsoft Defender składowe nie mogą być starsze niż dwie wersje, które są obecnie najbardziej dostępne:

- **Program antywirusowy Microsoft Defender aktualizacji platformy — Program antywirusowy Microsoft Defender** platformie jest aktualizowana co miesiąc.
- **Program antywirusowy Microsoft Defender wersji aparatu — Program antywirusowy Microsoft Defender** jest aktualizowany co miesiąc.
- **Program antywirusowy Microsoft Defender** zabezpieczeń — firma Microsoft stale aktualizuje analizę zabezpieczeń programu Microsoft Defender (znaną także jako definicja i podpis) w celu rozwiązania najnowszych zagrożeń oraz udoskonalenia logiki wykrywania.

Utrzymywanie Program antywirusowy Microsoft Defender wersji pomaga zmniejszyć reguły ASR wyników fałszywie dodatnich i zwiększyć Program antywirusowy Microsoft Defender wykrywania. Aby uzyskać więcej szczegółowych informacji na temat bieżących wersji i sposobu aktualizowania poszczególnych składników Program antywirusowy Microsoft Defender odwiedź Program antywirusowy Microsoft Defender [pomocy technicznej platformy](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>Zastrzeżenie

Niektóre reguły nie działają dobrze, jeśli wyeksłowane, wewnętrznie opracowane aplikacje i skrypty są w wysokim użyciu. Wdrażanie reguł ASR jest trudniejsze, jeśli podpisywanie kodu nie jest wymuszane.

## <a name="asr-rules-deployment-steps"></a>Kroki wdrażania reguł ASR

Tak jak w przypadku każdej nowej, szerokiej implementacji, która może mieć potencjalnie wpływ na twoją działalność biznesową, ważne jest, aby w planowaniu i implementacji znaleźć się w metodyce. Ze względu na zaawansowane możliwości reguł ASR w celu zapobiegania złośliwemu oprogramowaniu konieczne jest staranne planowanie i wdrażanie tych reguł, aby zagwarantować, że będą one najlepiej działać w przypadku unikatowych przepływów pracy klienta. Aby pracować w środowisku, należy starannie zaplanować, przetestować, zaimplementować i operacyjnie reguły asr.  

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="Fazy wdrażania reguł asr" lightbox="images/asr-rules-deployment-phases.png":::

>[!Note]
>W przypadku klientów korzystających z systemu HIPS innych niż firma Microsoft i które przejdą do zasad zmniejszania powierzchni ataków firmy Ochrona punktu końcowego w usłudze Microsoft Defender: firma Microsoft zaleca klientom wdrożenie rozwiązania HIPS obok własnego wdrożenia reguł ASR do momentu przejścia z trybu inspekcji do trybu blokowania. Pamiętaj, że aby uzyskać zalecenia dotyczące wykluczeń, musisz się z dostawcą oprogramowania antywirusowego innej firmy.  

## <a name="additional-topics-in-this-deployment-collection"></a>Dodatkowe tematy w tym zbiorze wdrożeń

[Etap 1. Planowanie](attack-surface-reduction-rules-deployment-plan.md)

[Etap 2. Testowanie](attack-surface-reduction-rules-deployment-test.md)

[Etap 3. Implementowanie](attack-surface-reduction-rules-deployment-implement.md)

[Etap 4. Operacyjne](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="reference"></a>Odwołanie

### <a name="blogs"></a>Blogi

[Reguły zmniejszania powierzchni ataków bez zadyskonu — część 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Bezmyślne reguły zmniejszania powierzchni ataków — część 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Bezmyślne reguły zmniejszania powierzchni ataków — część 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Bezmyślne reguły zmniejszania powierzchni ataków — część 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>Kolekcja ASR

[Omówienie zmniejszania powierzchni ataków](overview-attack-surface-reduction.md)

[Stosowanie reguł zmniejszania powierzchni ataków w celu zapobiegania zainfekowaniu złośliwym oprogramowaniem](attack-surface-reduction.md)

[Włączanie reguł ograniczania powierzchni ataków](enable-attack-surface-reduction.md)

[Informacje dotyczące reguł zmniejszania powierzchni ataków](attack-surface-reduction-rules-reference.md)

[Zmniejszenie powierzchni ataków — często zadawane pytania](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Rozwiązywanie problemów z wynikami fałszywie pozytywnymi/negatywnymi w ochronie punktu końcowego w usłudze Microsoft Defender](defender-endpoint-false-positives-negatives.md)

[Ochrona i Program antywirusowy Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

[Włączanie ochrony w chmurze w aplikacji Program antywirusowy Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md)

[Konfigurowanie i weryfikowanie wykluczeń na podstawie rozszerzenia, nazwy lub lokalizacji](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[Program antywirusowy Microsoft Defender platformy](manage-updates-baselines-microsoft-defender-antivirus.md)

[Omówienie spisu w centrum Aplikacje Microsoft 365 administracyjnego](/deployoffice/admincenter/inventory)

[Tworzenie planu wdrażania dla Windows](/windows/deployment/update/create-deployment-plan)

[Używanie kontroli dostępu opartej na rolach (RBAC, role based access control) i tagów zakresów dla rozpowszechniania it w Intune](/mem/intune/fundamentals/scope-tags)

[Przypisywanie profilów urządzeń w Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Witryny zarządzania

[Microsoft Endpoint Manager administracyjne](https://endpoint.microsoft.com/#home)

[Zmniejszanie obszaru podatnego na ataki](https://security.microsoft.com/asr?viewid=detections)

[Konfiguracje reguł asr](https://security.microsoft.com/asr?viewid=configuration)

[Reguły ASR Wykluczenia](https://security.microsoft.com/asr?viewid=exclusions)
