---
title: Używanie reguł zmniejszania obszaru ataków w celu zapobiegania infekcji złośliwym oprogramowaniem
description: Reguły zmniejszania obszaru podatnego na ataki mogą pomóc w zapobieganiu używaniu aplikacji i skryptów do infekowania urządzeń złośliwym oprogramowaniem.
keywords: Reguły zmniejszania obszaru ataków, asr, biodra, system zapobiegania włamaniom hosta, zasady ochrony, antyeksploatacja, antyeksploatacja, luki w zabezpieczeniach, zapobieganie zakażeniom, Ochrona punktu końcowego w usłudze Microsoft Defender
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
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.technology: mde
ms.topic: article
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.openlocfilehash: a5ca2613028e892229da1888c6176cb729e0cf1b
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469585"
---
# <a name="attack-surface-reduction-rules-overview"></a>Omówienie reguł zmniejszania obszaru podatnego na ataki

**Dotyczy:**

- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Program antywirusowy Microsoft Defender

**Platformy**
- System Windows

## <a name="why-attack-surface-reduction-rules-are-important"></a>Dlaczego reguły zmniejszania obszaru podatnego na ataki są ważne

Obszar ataków organizacji obejmuje wszystkie miejsca, w których osoba atakująca może naruszyć bezpieczeństwo urządzeń lub sieci organizacji. Zmniejszenie obszaru ataków oznacza ochronę urządzeń i sieci organizacji, co sprawia, że osoby atakujące mają mniej sposobów przeprowadzania ataków. Konfigurowanie reguł zmniejszania obszaru ataków w Ochrona punktu końcowego w usłudze Microsoft Defender może pomóc!

Reguły zmniejszania obszaru ataków dotyczą pewnych zachowań oprogramowania, takich jak:

- Uruchamianie plików wykonywalnych i skryptów, które próbują pobrać lub uruchomić pliki
- Uruchamianie zaciemnionych lub w inny sposób podejrzanych skryptów
- Wykonywanie zachowań, których aplikacje zwykle nie inicjują podczas normalnej codziennej pracy

Takie zachowania oprogramowania są czasami widoczne w legalnych aplikacjach. Jednak te zachowania są często uważane za ryzykowne, ponieważ są często nadużywane przez osoby atakujące za pośrednictwem złośliwego oprogramowania. Reguły zmniejszania obszaru podatnego na ataki mogą ograniczać ryzykowne zachowania oparte na oprogramowaniu i pomagać w zachowaniu bezpieczeństwa organizacji.

Aby uzyskać więcej informacji na temat konfigurowania reguł zmniejszania obszaru podatnego na ataki, zobacz [Włączanie reguł zmniejszania obszaru podatnego na ataki](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Ocena wpływu reguły przed wdrożeniem

Możesz ocenić, w jaki sposób reguła zmniejszania obszaru ataków może wpłynąć na sieć, otwierając zalecenie dotyczące zabezpieczeń dla tej reguły w [Zarządzanie zagrożeniami i lukami](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="Zalecenie usługi ASR" lightbox="images/asrrecommendation.png":::

W okienku szczegółów rekomendacji sprawdź wpływ na użytkownika, aby określić, jaki procent urządzeń może zaakceptować nowe zasady umożliwiające regułę w trybie blokowania bez negatywnego wpływu na produktywność.

Aby uzyskać informacje na temat obsługiwanych systemów operacyjnych i dodatkowych informacji o wymaganiach, zobacz [Artykuł "](enable-attack-surface-reduction.md#requirements) Włączanie reguł zmniejszania obszaru podatnego na ataki".

## <a name="audit-mode-for-evaluation"></a>Tryb inspekcji na potrzeby oceny

Użyj [trybu inspekcji](audit-windows-defender.md) , aby ocenić, jak reguły zmniejszania obszaru ataków wpłyną na organizację, jeśli zostaną włączone. Najpierw uruchom wszystkie reguły w trybie inspekcji, aby zrozumieć, jak wpływają one na aplikacje biznesowe. Wiele aplikacji biznesowych jest pisanych z ograniczonymi problemami dotyczącymi zabezpieczeń i mogą wykonywać zadania w sposób podobny do złośliwego oprogramowania. Dzięki monitorowaniu danych [inspekcji i dodawaniu wykluczeń dla niezbędnych](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) aplikacji można wdrożyć reguły zmniejszania obszaru ataków bez obniżania produktywności.

## <a name="warn-mode-for-users"></a>Tryb ostrzeżenia dla użytkowników

(**NOWY**!) Przed rozpoczęciem działania trybu ostrzegania reguły zmniejszania obszaru ataków, które są włączone, można ustawić na tryb inspekcji lub tryb blokady. W nowym trybie ostrzegania za każdym razem, gdy zawartość jest blokowana przez regułę zmniejszania obszaru ataków, użytkownicy widzą okno dialogowe wskazujące, że zawartość jest zablokowana. W oknie dialogowym jest również dostępna opcja odblokowania zawartości. Następnie użytkownik może ponowić próbę wykonania akcji i zakończyć operację. Gdy użytkownik odblokuje zawartość, zawartość pozostaje odblokowana przez 24 godziny, a następnie blokuje wznowienie.

Tryb ostrzeżenia pomaga organizacji mieć reguły zmniejszania obszaru ataków bez uniemożliwiania użytkownikom dostępu do zawartości potrzebnej do wykonywania zadań.

### <a name="requirements-for-warn-mode-to-work"></a>Wymagania dotyczące trybu ostrzegania do działania

Tryb ostrzegania jest obsługiwany na urządzeniach z następującymi wersjami Windows:

- [Windows 10, wersja 1809](/windows/whats-new/whats-new-windows-10-version-1809) lub nowsze
- Windows 11
- [Windows Server, wersja 1809 lub nowsza](/windows-server/get-started/whats-new-in-windows-server-1809)

Program antywirusowy Microsoft Defender musi działać z ochroną w czasie rzeczywistym w [trybie aktywnym](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

Upewnij się również, [Program antywirusowy Microsoft Defender i aktualizacje oprogramowania chroniącego przed złośliwym kodem](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) są zainstalowane.

- Minimalne wymagania dotyczące wydania platformy: `4.18.2008.9`
- Minimalne wymagania dotyczące wydania aparatu: `1.1.17400.5`

Aby uzyskać więcej informacji i uzyskać aktualizacje, zobacz [Update for Microsoft Defender antimalware platform (Aktualizacja dla platformy ochrony przed złośliwym kodem w usłudze Microsoft Defender](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform)).

### <a name="cases-where-warn-mode-is-not-supported"></a>Przypadki, w których tryb ostrzeżenia nie jest obsługiwany

Tryb ostrzegania nie jest obsługiwany w przypadku trzech reguł zmniejszania obszaru ataków podczas konfigurowania ich w Microsoft Endpoint Manager. (Jeśli używasz zasady grupy do konfigurowania reguł zmniejszania obszaru ataków, tryb ostrzegania jest obsługiwany). Trzy reguły, które nie obsługują trybu ostrzeżenia podczas konfigurowania ich w Microsoft Endpoint Manager, są następujące:

- [Blokuj uruchamianie pobranej zawartości wykonywalnej](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`) w języku JavaScript lub VBScript
- [Blokuj trwałość za pośrednictwem subskrypcji zdarzeń WMI](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym okup](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

Ponadto tryb ostrzegania nie jest obsługiwany na urządzeniach ze starszymi wersjami Windows. W takich przypadkach reguły zmniejszania obszaru ataków skonfigurowane do uruchamiania w trybie ostrzeżenia będą uruchamiane w trybie bloku.

## <a name="notifications-and-alerts"></a>Powiadomienia i alerty

Za każdym razem, gdy wyzwalana jest reguła zmniejszania obszaru ataków, na urządzeniu jest wyświetlane powiadomienie. Powiadomienie można [dostosować przy](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) użyciu danych firmy i informacji kontaktowych.

Ponadto po wyzwoleniu niektórych reguł zmniejszania obszaru ataków są generowane alerty.

Powiadomienia i wszystkie wygenerowane alerty można wyświetlić w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalu Microsoft 365 Defender</a>.

Aby uzyskać szczegółowe informacje na temat funkcji powiadomień i alertów, zobacz: [Alert dla reguły i szczegóły powiadomień](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details) w artykule **Informacje o regułach zmniejszania obszaru podatnego na ataki**.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Zaawansowane zdarzenia zmniejszania obszaru zagrożeń i ataków

Możesz użyć zaawansowanego wyszukiwania zagrożeń, aby wyświetlić zdarzenia redukcji obszaru ataków. Aby usprawnić ilość danych przychodzących, tylko unikatowe procesy dla każdej godziny są widoczne w przypadku zaawansowanego wyszukiwania zagrożeń. Czas zdarzenia redukcji powierzchni ataku to pierwszy raz, gdy zdarzenie jest widoczne w ciągu godziny.

Załóżmy na przykład, że zdarzenie redukcji obszaru ataków występuje na 10 urządzeniach w godzinie 14:00. Załóżmy, że pierwsze zdarzenie miało miejsce o godzinie 2:15, a ostatnie o 2:45. W przypadku zaawansowanego wyszukiwania zagrożeń zobaczysz jedno wystąpienie tego zdarzenia (nawet jeśli faktycznie miało miejsce na 10 urządzeniach), a jego sygnaturą czasową będzie godzina 14:15.

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania zagrożeń, zobacz [Proaktywne wyszukiwanie zagrożeń z zaawansowanym wyszukiwaniem zagrożeń](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Funkcje zmniejszania obszaru ataków w wersjach Windows

Możesz ustawić reguły zmniejszania obszaru podatnego na ataki dla urządzeń, na których działa dowolna z następujących wersji i wersji Windows:

- Windows 10 Pro, [wersja 1709 lub nowsza](/windows/whats-new/whats-new-windows-10-version-1709)
- Windows 10 Enterprise, [wersja 1709 lub nowsza](/windows/whats-new/whats-new-windows-10-version-1709)
- Windows Server, [wersja 1803 (półroczny kanał)](/windows-server/get-started/whats-new-in-windows-server-1803) lub nowszy
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh801901(v=ws.11))

  >[!NOTE]
  >Windows Server 2016 i Windows Server 2012 R2 należy dołączyć, korzystając z instrukcji zawartych w temacie [Dołączanie serwerów Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała.

Mimo że reguły zmniejszania obszaru ataków nie wymagają [licencji Windows E5](/windows/deployment/deploy-enterprise-licenses), jeśli masz Windows E5, uzyskasz zaawansowane możliwości zarządzania. Zaawansowane możliwości — dostępne tylko w Windows E5 — obejmują:

- Monitorowanie, analiza i przepływy pracy dostępne w [usłudze Defender for Endpoint](microsoft-defender-endpoint.md)
- Możliwości raportowania i konfiguracji w [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Te zaawansowane możliwości nie są dostępne z licencją Windows Professional lub Windows E3. Jeśli jednak masz te licencje, możesz użyć dzienników Podgląd zdarzeń i Program antywirusowy Microsoft Defender, aby przejrzeć zdarzenia reguły zmniejszania obszaru ataków.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Przeglądanie zdarzeń zmniejszania obszaru ataków w portalu Microsoft 365 Defender

Usługa Defender for Endpoint udostępnia szczegółowe raportowanie zdarzeń i bloków w ramach scenariuszy badania alertów.

Możesz wykonywać zapytania dotyczące usługi Defender pod kątem danych punktu końcowego w [Microsoft 365 Defender](microsoft-defender-endpoint.md) przy użyciu [zaawansowanego wyszukiwania zagrożeń](/microsoft-365/security/defender/advanced-hunting-query-language). 

Oto przykładowe zapytanie:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Przejrzyj zdarzenia zmniejszania obszaru ataków w Windows Podgląd zdarzeń

Możesz przejrzeć dziennik zdarzeń Windows, aby wyświetlić zdarzenia generowane przez reguły zmniejszania obszaru ataków:

1. Pobierz [pakiet ewaluacyjny](https://aka.ms/mp7z2w) i wyodrębnij plik *cfa-events.xml* do łatwo dostępnej lokalizacji na urządzeniu.

2. Wprowadź wyrazy *Podgląd zdarzeń* do menu Start, aby otworzyć Windows Podgląd zdarzeń.

3. W obszarze **Akcje** wybierz pozycję **Importuj widok niestandardowy...**.

4. Wybierz plik *cfa-events.xml* , z którego został wyodrębniony. Alternatywnie [skopiuj plik XML bezpośrednio](event-views.md).

5. Wybierz przycisk **OK**.

Można utworzyć widok niestandardowy, który filtruje zdarzenia w celu wyświetlenia tylko następujących zdarzeń, z których wszystkie są związane z kontrolowanym dostępem do folderów:

|Identyfikator zdarzenia|Opis|
|---|---|
|5007|Zdarzenie po zmianie ustawień|
|1121|Zdarzenie, gdy reguła jest uruchamiana w trybie bloku|
|1122|Zdarzenie, gdy reguła jest uruchamiana w trybie inspekcji|

"Wersja aparatu" wymieniona dla zdarzeń redukcji obszaru ataków w dzienniku zdarzeń jest generowana przez usługę Defender for Endpoint, a nie przez system operacyjny. Usługa Defender for Endpoint jest zintegrowana z Windows 10 i Windows 11, więc ta funkcja działa na wszystkich urządzeniach z zainstalowanymi Windows 10 lub Windows 11.

> [!TIP]
> Jeśli szukasz informacji dotyczących programu antywirusowego dla innych platform, zobacz:
> - [Ustaw preferencje dla ochrony punktu końcowego usługi Microsoft Defender w systemie macOS](mac-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na komputerze Mac](microsoft-defender-endpoint-mac.md)
> - [Ustawienia zasad ochrony antywirusowej systemu macOS dla programu antywirusowego Microsoft Defender dla usługi Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Ustaw preferencje dla ochrony punktu końcowego w usłudze Microsoft Defender w systemie Linux](linux-preferences.md)
> - [Ochrona punktu końcowego w usłudze Microsoft Defender na Linuxie](microsoft-defender-endpoint-linux.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu Android](android-configure.md)
> - [Konfiguruj ochronę punktu końcowego w usłudze Microsoft Defender w opcjach systemu iOS](ios-configure-features.md)
