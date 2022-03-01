---
title: Stosowanie reguł zmniejszania powierzchni ataków w celu zapobiegania zainfekowaniu złośliwym oprogramowaniem
description: Reguły ograniczania powierzchni ataków mogą zapobiegać używaniu aplikacji i skryptów w celu zainfekowania urządzeń złośliwym oprogramowaniem.
keywords: Reguły zmniejszania powierzchni ataków, asr, hips, host intrusion prevention system, protection rules, anti-exploit, antiexploit, exploit, prevention, Microsoft Defender for Endpoint
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
ms.collection: m365initiative-m365-defender
ms.date: 1/18/2022
ms.openlocfilehash: 3f3daaa068f067c8d4ffbbf40a4d8ba1d32d04b9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011402"
---
# <a name="attack-surface-reduction-rules-overview"></a>Omówienie reguł zmniejszania powierzchni ataków

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="why-attack-surface-reduction-rules-are-important"></a>Dlaczego reguły ograniczania powierzchni ataków są ważne

Miejsce ataków organizacji obejmuje wszystkie miejsca, w których atakujący mogą naruszonć urządzenia lub sieci organizacji. Zmniejszenie powierzchni ataków oznacza ochronę urządzeń i sieci organizacji, co pozostawia atakującym mniej sposobów przeprowadzania ataków. Skonfigurowanie reguł ograniczania powierzchni ataków w programie Microsoft Defender dla punktu końcowego może pomóc!

Reguły zmniejszania powierzchni ataków mają na celu określone zachowania oprogramowania, takie jak:

- Uruchamianie plików wykonywalnych i skryptów próbujących pobierać lub uruchamiać pliki
- Uruchamianie skryptów zasłoconych lub w inny sposób podejrzanych skryptów
- Wykonywanie czynności, których aplikacje zwykle nie inicjują podczas normalnej, codziennie pracy

Takie zachowania oprogramowania są czasami widoczne w aplikacji o zgodnej z prawem wersji. Takie zachowania są często uznawane za ryzykowne, ponieważ są często wykorzystywane przez atakujących za pośrednictwem złośliwego oprogramowania. Reguły ograniczania powierzchni ataków mogą ograniczać ryzykowne zachowania oparte na oprogramowaniu i pomagać chronić twoją organizację.

Aby uzyskać więcej informacji na temat konfigurowania reguł zmniejszania powierzchni ataków, zobacz [Włączanie reguł ograniczania powierzchni ataków](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Ocena wpływu reguły przed wdrożeniem

Możesz ocenić wpływ reguły ograniczania powierzchni ataków na Twoją sieć, otwierając w programie Zarządzanie zagrożeniami i lukami zalecenia dotyczące [bezpieczeństwa dla tej Zarządzanie zagrożeniami i lukami](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="Reguła ograniczania powierzchni ataków jest reco zabezpieczeń.":::

W okienku szczegółów zalecenia sprawdź wpływ na użytkowników, aby określić procent urządzeń, na których urządzenia mogą zaakceptować nowe zasady umożliwiające regułę w trybie blokowania bez negatywnego wpływu na wydajność.

Zobacz [Wymagania w](enable-attack-surface-reduction.md#requirements) artykule "Włączanie reguł ograniczania powierzchni ataków", aby uzyskać informacje na temat obsługiwanych systemów operacyjnych i dodatkowych informacji o wymaganiach.

## <a name="audit-mode-for-evaluation"></a>Tryb inspekcji do oceny

Użyj [trybu inspekcji,](audit-windows-defender.md) aby ocenić wpływ reguł zmniejszania powierzchni ataków na Twoją organizację, jeśli jest włączona. Najpierw uruchom wszystkie reguły w trybie inspekcji, aby zrozumieć, jak wpływają one na Twoje aplikacje biznesowe. Wiele aplikacji biznesowych zostało napisanych z ograniczonymi problemami z zabezpieczeniami i mogą one wykonywać zadania podobne do złośliwego oprogramowania. Monitorowanie danych inspekcji i [dodawanie wykluczeń dotyczących](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) niezbędnych aplikacji pozwala wdrożyć reguły ograniczania poziomu ataków bez zmniejszania produktywności.

## <a name="warn-mode-for-users"></a>Tryb ostrzegawki dla użytkowników

(**NOWOŚĆ**!) Przed trybem  ostrzeżeniem włączono reguły ograniczania powierzchni ataków, które można było skonfigurować jako tryb inspekcji lub tryb blokowania. W nowym trybie ostrzegawczym w przypadku zablokowania zawartości przez regułę zmniejszania powierzchni ataków użytkownicy widzą okno dialogowe z ostrzeżeniem, że zawartość jest zablokowana. W tym oknie dialogowym jest również dostępna opcja odblokowania zawartości. Użytkownik może następnie ponowić próbę działania i operacja zostanie ukończona. Gdy użytkownik odblokuje zawartość, zawartość pozostaje odblokowana przez 24 godziny, a następnie blokuje życiorysy.

Tryb ostrzegania ułatwia organizacji zastosowanie reguł zmniejszania powierzchni ataków bez uniemożliwiania użytkownikom uzyskiwania dostępu do zawartości potrzebnej do wykonywania swoich zadań.

### <a name="requirements-for-warn-mode-to-work"></a>Wymagania dotyczące działania trybu ostrzegawki

Tryb ostrzegawki jest obsługiwany na urządzeniach z następującymi wersjami Windows:

- [Windows 10, wersja 1809](/windows/whats-new/whats-new-windows-10-version-1809) lub nowszy
- Windows 11
- [Windows Server w wersji 1809](/windows-server/get-started/whats-new-in-windows-server-1809) lub nowszej

Program antywirusowy Microsoft Defender być uruchomiona z ochroną w czasie rzeczywistym w [trybie aktywnym](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

Upewnij się też, [że Program antywirusowy Microsoft Defender i aktualizacje](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) dotyczące ochrony przed złośliwym oprogramowaniem.

- Minimalne wymaganie wydania platformy: `4.18.2008.9`
- Minimalne wymaganie zwolnienia aparatu: `1.1.17400.5`

Aby uzyskać więcej informacji i uzyskać aktualizacje, zobacz [Aktualizacja platformy ochrony przed złośliwym oprogramowaniem Programu Microsoft Defender](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>Przypadki, w których tryb  warnowania nie jest obsługiwany

Tryb ostrzegania nie jest obsługiwany w przypadku trzech reguł zmniejszania powierzchni ataków podczas ich konfigurowania w Microsoft Endpoint Manager. (Jeśli używasz tego zasady grupy do konfigurowania reguł zmniejszania powierzchni ataków, obsługiwany jest tryb ostrzegania). Trzy reguły, które nie obsługują trybu ostrzegania podczas ich konfigurowania w aplikacji Microsoft Endpoint Manager są następujące:

- [Blokowanie uruchamiania pobranej zawartości](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) wykonywalnego (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`) przez język JavaScript lub VBScript
- [Blokowanie okresu dzięki subskrypcji zdarzeń usługi WMI](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [Korzystanie z zaawansowanej ochrony przed oprogramowaniem wymuszającym](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) okup (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

Ponadto tryb ostrzegawki nie jest obsługiwany na urządzeniach ze starszymi wersjami Windows. W takich przypadkach reguły ograniczania powierzchni ataków skonfigurowane do uruchamiania w trybie  ostrzeżeniem działają w trybie blokowania.

## <a name="notifications-and-alerts"></a>Powiadomienia i alerty

Za każdym razem, gdy zostanie wyzwolona reguła zmniejszania powierzchni ataków, na urządzeniu zostanie wyświetlone powiadomienie. Możesz dostosować [powiadomienie, modyfikując](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) je wraz ze szczegółami twojej firmy i informacjami kontaktowymi.

Ponadto w przypadku uruchomienia pewnych reguł zmniejszania powierzchni ataków są generowane alerty.

Powiadomienia i wszelkie wygenerowane alerty można wyświetlać w portalu Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">wiadomości</a>.

Aby uzyskać szczegółowe informacje na temat powiadomień i funkcji alertów, zobacz: Zgodnie z [regułami alertu](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details) i szczegółów powiadomień w artykule Informacje dotyczące reguł ograniczania powierzchni **ataków**.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Zaawansowane wydarzenia z zmniejszania powierzchni podczas wyszukiwania i ataków

Za pomocą zaawansowanego wyszukiwania możesz wyświetlać zdarzenia zmniejszenia powierzchni ataków. Aby usprawnić ilość danych przychodzących, z czasami zaawansowanego wyszukiwania można zobaczyć tylko unikatowe procesy dla każdej godziny. Czas zmniejszenia powierzchni ataków jest pierwszym zdarzeniem widocznym w ciągu godziny.

Załóżmy na przykład, że zdarzenie zmniejszenia powierzchni ataków występuje na 10 urządzeniach w godzinie 2:00. Załóżmy, że pierwsze zdarzenie wystąpiło o 2:15, a ostatnie o 2:45. W przypadku zaawansowanego wyszukiwania zobaczysz jedno wystąpienie tego wydarzenia (mimo że rzeczywiście wystąpiło na 10 urządzeniach), a jego sygnatura czasowa będzie miała czas 2:15 PM.

Aby uzyskać więcej informacji na temat zaawansowanego wyszukiwania, zobacz [Aktywne wyszukiwanie zagrożeń za pomocą zaawansowanego wyszukiwania](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Funkcje zmniejszania powierzchni ataków w Windows wersjach

Możesz ustawić reguły zmniejszania powierzchni ataków dla urządzeń z dowolną z następujących wersji i wersji programu Windows:

- Windows 10 Pro, [wersja 1709](/windows/whats-new/whats-new-windows-10-version-1709) lub nowsza
- Windows 10 Enterprise, [wersja 1709](/windows/whats-new/whats-new-windows-10-version-1709) lub nowsza
- Windows Server w [wersji 1803 (półroczny kanał)](/windows-server/get-started/whats-new-in-windows-server-1803) lub nowszej
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)

  >[!NOTE]
  >Windows Server 2016 i Windows Server 2012 R2 muszą zostać naniesone zgodnie z instrukcjami podanymi w te sposób: Windows [onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), aby ta funkcja działała.

Mimo że reguły zmniejszania powierzchni ataków nie wymagają licencji [Windows E5](/windows/deployment/deploy-enterprise-licenses), jeśli masz Windows E5, możesz uzyskać zaawansowane możliwości zarządzania. Funkcje zaawansowane — dostępne tylko w Windows E5 — obejmują:

- Monitorowanie, analiza i przepływy pracy dostępne w [programie Defender dla punktu końcowego](microsoft-defender-endpoint.md)
- Funkcje raportowania i konfiguracji w [programie Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Te funkcje zaawansowane nie są dostępne w przypadku licencji Windows Professional E3 Windows E3. Jeśli jednak masz te licencje, możesz użyć podglądu zdarzeń i dzienników Program antywirusowy Microsoft Defender, aby przejrzeć zdarzenia reguły ograniczania powierzchni ataków.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Przeglądanie zdarzeń zmniejszenia powierzchni ataków w portalu Microsoft 365 Defender ataków

Program Defender for Endpoint udostępnia szczegółowe raportowanie zdarzeń i bloków w ramach scenariuszy analizy alertów.

Możesz zapytanie dotyczące programu Defender dla danych punktu końcowego [w programie Microsoft 365 Defender](microsoft-defender-endpoint.md), używając [zaawansowanego wyszukiwania](/microsoft-365/security/defender/advanced-hunting-query-language). 

Oto przykładowe zapytanie:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Przeglądanie zdarzeń zmniejszenia powierzchni ataków w Windows Zdarzeń

Możesz przejrzeć dziennik Windows, aby wyświetlić zdarzenia generowane przez reguły ograniczania powierzchni ataków:

1. Pobierz pakiet [oceny i](https://aka.ms/mp7z2w) wyodrębnij plik *cfa-events.xml* w łatwo dostępnej lokalizacji na urządzeniu.

2. Wprowadź wyrazy (*Podgląd zdarzeń*) w menu Start, aby otworzyć Windows zdarzeń.

3. W **obszarze Akcje** wybierz pozycję **Importuj widok niestandardowy...**.

4. Wybierz plik, *cfa-events.xml* , z którego został wyodrębniony. Ewentualnie skopiuj [kod XML bezpośrednio](event-views.md).

5. Wybierz przycisk **OK**.

Możesz utworzyć widok niestandardowy, który filtruje zdarzenia w celu pokazania tylko następujących zdarzeń, z których wszystkie są związane z kontrolowanym dostępem do folderu:

|Identyfikator zdarzenia|Opis|
|---|---|
|5007|Zdarzenie w przypadku zmiany ustawień|
|1121|Zdarzenie, gdy reguła zostanie wyzb. w trybie blokowania|
|1122|Zdarzenie, gdy reguła jest w trybie inspekcji|

"Wersja aparatu" wymieniona w dzienniku zdarzeń ograniczania powierzchni ataków jest generowana przez program Defender for Endpoint, a nie przez system operacyjny. Program Defender for Endpoint jest zintegrowany z systemami Windows 10 i Windows 11, więc ta funkcja działa na wszystkich urządzeniach z zainstalowanymi systemami Windows 10 i Windows 11.
