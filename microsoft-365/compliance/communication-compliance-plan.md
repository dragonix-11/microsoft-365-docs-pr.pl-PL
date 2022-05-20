---
title: Zaplanuj zgodności w komunikacji
description: Dowiedz się więcej o planowaniu korzystania ze zgodności komunikacji w organizacji.
keywords: Microsoft 365, Microsoft Purview, zgodność, zgodność z komunikacją
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 22e5ed11c97ed00449cb62439e105bd1e6dc78e7
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599552"
---
# <a name="plan-for-communication-compliance"></a>Zaplanuj zgodności w komunikacji

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Przed rozpoczęciem pracy ze [zgodnością komunikacji](communication-compliance.md) w organizacji istnieją ważne działania związane z planowaniem i zagadnienia, które powinny zostać przejrzane przez zespoły ds. technologii informatycznych i zarządzania zgodnością. Dokładne zrozumienie i planowanie wdrożenia w następujących obszarach pomoże zapewnić, że implementacja i korzystanie z funkcji zgodności z komunikacją przebiega bezproblemowo i jest zgodne z najlepszymi rozwiązaniami dla rozwiązania.

Aby uzyskać więcej informacji i omówienie procesu planowania dotyczącego zgodności i ryzykownych działań w organizacji, zobacz [Uruchamianie programu do zarządzania ryzykiem wewnętrznym](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

> [!IMPORTANT]
> Zgodność z komunikacją jest obecnie dostępna w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi platformy Azure. Aby sprawdzić, czy zgodność komunikacji jest obsługiwana w organizacji, zobacz [Dostępność zależności platformy Azure według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="transitioning-from-supervision-in-office-365"></a>Przejście z nadzoru w Office 365

W przypadku organizacji korzystających z zasad nadzoru w Office 365 należy natychmiast zaplanować przejście do zasad zgodności komunikacji w Microsoft Purview i zrozumieć te ważne kwestie:

- Rozwiązanie nadzoru w Office 365 zostało w pełni zastąpione rozwiązaniem zgodności z komunikacją w Microsoft Purview. Zalecamy utworzenie nowych zasad w zakresie zgodności z komunikacją, które mają takie same ustawienia jak istniejące zasady nadzoru, aby korzystać z nowych ulepszeń badania i korygowania.
- Komunikatów zapisanych w nadzorze w Office 365 dopasowania zasad nie można przenosić ani udostępniać w celu zapewnienia zgodności z komunikacją.
- W przypadku organizacji z obydwoma rozwiązaniami używanymi obok siebie podczas procesu przejścia zasady używane w każdym rozwiązaniu muszą mieć unikatowe nazwy zasad. Grupy i niestandardowe słowniki słów kluczowych mogą być współużytkowane między rozwiązaniami w okresie przejściowym.

Aby uzyskać informacje o wycofaniu nadzoru w Office 365, zobacz [plan Microsoft 365,](https://www.microsoft.com/microsoft-365/roadmap) aby uzyskać szczegółowe informacje.

## <a name="work-with-stakeholders-in-your-organization"></a>Praca z osobami biorącymi udział w projekcie w organizacji

Zidentyfikuj odpowiednie osoby biorące udział w projekcie w organizacji, aby współpracować w celu podejmowania działań dotyczących alertów zgodności komunikacji. Niektóre zalecane osoby biorące udział w projekcie, które należy wziąć pod uwagę, obejmują planowanie początkowe i kompleksowy [przepływ pracy zgodności z komunikacją](communication-compliance.md#workflow) to osoby z następujących obszarów organizacji:

- Technologia informacyjna
- Zgodność
- Prywatność
- Bezpieczeństwo
- Zasoby ludzkie
- Prawnych

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Planowanie przepływu pracy badania i korygowania

### <a name="permissions"></a>Uprawnienia

Wybierz dedykowanych uczestników projektu, aby monitorować i przeglądać alerty i przypadki w regularnym okresie [w portal zgodności Microsoft Purview](https://compliance.microsoft.com/). Upewnij się, że rozumiesz sposób przypisywania użytkowników i osób biorących udział w projekcie do różnych grup ról zgodności komunikacji w organizacji.

> [!IMPORTANT]
> Po skonfigurowaniu grup ról stosowanie uprawnień grupy ról do przypisanych użytkowników w całej organizacji może potrwać do 30 minut.

Istnieje sześć grup ról używanych do konfigurowania początkowych uprawnień do zarządzania funkcjami zgodności komunikacji. Aby zapewnić **zgodność z komunikacją** jako opcję menu w portal zgodności Microsoft Purview i kontynuować wykonywanie tych kroków konfiguracji, musisz zostać przypisany do jednej z następujących ról lub grup ról:

- rola [*administratora globalnego*](/azure/active-directory/roles/permissions-reference#global-administrator) Azure Active Directory
- rola [*administratora zgodności*](/azure/active-directory/roles/permissions-reference#compliance-administrator) Azure Active Directory
- grupa ról [*zarządzania organizacją*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portal zgodności Microsoft Purview
- grupa ról [*administratora zgodności*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portal zgodności Microsoft Purview
- *Grupa ról Zgodność z komunikacją*
- *Grupa ról administratora zgodności komunikacji*

Członkowie następujących ról mają te same uprawnienia rozwiązania dołączone do grupy ról *Administrator zgodności komunikacji* :

- *administrator globalny* Azure Active Directory
- *administrator zgodności* Azure Active Directory
- *zarządzanie organizacją* portal zgodności Microsoft Purview
- *administrator zgodności* portal zgodności Microsoft Purview

> [!IMPORTANT]
> Upewnij się, że zawsze masz co najmniej jednego użytkownika w grupach ról *Zgodność z komunikacją* lub *Zgodność z komunikacją Administrator* (w zależności od wybranej opcji), aby konfiguracja zgodności komunikacji nie wchodziła do scenariusza "zero administratora", jeśli określoni użytkownicy opuszczają organizację.

W zależności od sposobu zarządzania zasadami zgodności komunikacji i alertami należy przypisać użytkowników do określonych grup ról, aby zarządzać różnymi zestawami funkcji zgodności komunikacji. Możesz przypisać użytkowników z różnymi obowiązkami zgodności do określonych grup ról w celu zarządzania różnymi obszarami funkcji zgodności komunikacji. Możesz też zdecydować się na przypisanie wszystkich kont użytkowników wyznaczonym administratorom, analitykom, badaczom i widzom do grupy ról *Zgodność z komunikacją* . Użyj jednej grupy ról lub wielu grup ról, aby najlepiej dopasować wymagania dotyczące zarządzania zgodnością.

Wybierz spośród tych opcji grupy ról rozwiązania podczas konfigurowania zgodności z komunikacją i zarządzania nimi:

|**Rola**|**Uprawnienia roli**|
|:-----|:-----|
| **Zgodność z komunikacją** | Ta grupa ról służy do zarządzania zgodnością komunikacji dla organizacji w jednej grupie. Dodając wszystkie konta użytkowników dla wyznaczonych administratorów, analityków, badaczy i osób przeglądających, możesz skonfigurować uprawnienia do zgodności komunikacji w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień zgodności komunikacji. Ta konfiguracja jest najprostszym sposobem szybkiego rozpoczęcia pracy ze zgodnością z komunikacją i jest dobrym rozwiązaniem dla organizacji, które nie potrzebują oddzielnych uprawnień zdefiniowanych dla oddzielnych grup użytkowników. Użytkownicy tworzący zasady jako administrator zgodności komunikacji muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online. |
| **Administrator zgodności komunikacji** | Użyj tej grupy ról, aby początkowo skonfigurować zgodność z komunikacją, a później segregować administratorów zgodności komunikacji do zdefiniowanej grupy. Użytkownicy przypisani do tej grupy ról mogą tworzyć, odczytywać, aktualizować i usuwać zasady zgodności komunikacji, ustawienia globalne i przypisania grup ról. Użytkownicy przypisani do tej grupy ról nie mogą wyświetlać alertów komunikatów. Użytkownicy tworzący zasady jako administrator zgodności komunikacji muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online. |
| **Analityk zgodności komunikacji** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą pełnić rolę analityków zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać zasady, w których są przypisani jako recenzenci, wyświetlać metadane komunikatów (nie zawartość komunikatów), eskalować do dodatkowych recenzentów lub wysyłać powiadomienia do użytkowników. Analitycy nie mogą rozpoznać oczekujących alertów. |
| **Badacz zgodności z komunikacją** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą pełnić rolę badaczy zgodności z komunikacją. Użytkownicy przypisani do tej grupy ról mogą wyświetlać metadane komunikatów i zawartość, eskalować do dodatkowych recenzentów, eskalować do sprawy zbierania elektronicznych materiałów dowodowych (Premium), wysyłać powiadomienia do użytkowników i rozwiązywać alert. |
| **Podgląd zgodności komunikacji** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą zarządzać raportami komunikacji. Użytkownicy przypisani do tej grupy ról mogą uzyskiwać dostęp do wszystkich widżetów raportowania na stronie głównej zgodności komunikacji i mogą wyświetlać wszystkie raporty zgodności komunikacji. |

### <a name="supervised-users"></a>Użytkownicy nadzorowane

Przed rozpoczęciem korzystania ze zgodności z komunikacją należy określić, kto wymaga przejrzenia ich komunikacji. W zasadach adresy e-mail użytkowników identyfikują osoby lub grupy osób do nadzorowania. Niektóre przykłady tych grup to Grupy Microsoft 365, listy dystrybucyjne oparte na Exchange, społeczności Yammer i kanały Microsoft Teams. Można również wykluczyć określonych użytkowników lub grupy ze skanowania za pomocą określonej grupy wykluczeń lub listy grup. Aby uzyskać więcej informacji na temat typów grup obsługiwanych w zasadach zgodności komunikacji, zobacz [Wprowadzenie ze zgodnością z komunikacją](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance).

> [!IMPORTANT]
> Użytkownicy objęci zasadami zgodności z komunikacją muszą mieć licencję Zgodność platformy Microsoft 365 E5, licencję Office 365 Enterprise E3 z dodatkiem Zaawansowana zgodność lub być uwzględnieni w subskrypcji Office 365 Enterprise E5. Jeśli nie masz istniejącego planu Enterprise E5 i chcesz wypróbować zgodność z [komunikacją, możesz utworzyć konto próbne Office 365 Enterprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Wszyscy oceniający

Podczas tworzenia zasad zgodności komunikacji należy określić, kto przegląda komunikaty nadzorowanych użytkowników. W zasadach adresy e-mail użytkowników identyfikują osoby lub grupy osób do przeglądania nadzorowanej komunikacji. Wszyscy recenzenci muszą mieć skrzynki pocztowe hostowane w Exchange Online, muszą być przypisane do grup ról *Analityk zgodności komunikacji* lub *Badacz zgodności komunikacji* i muszą zostać przypisane do zasad, które muszą zostać zbadane. Gdy recenzenci są dodawani do zasad, automatycznie otrzymują wiadomość e-mail z powiadomieniem o przypisaniu do zasad i udostępniają linki do informacji o procesie przeglądu.

### <a name="groups-for-supervised-users-and-reviewers"></a>Grupy dla nadzorowanych użytkowników i recenzentów

Aby uprościć konfigurację, utwórz grupy dla osób, które potrzebują przejrzanych komunikacji, i grup dla osób przeglądających te komunikaty. Jeśli używasz grup, może być potrzebnych kilka. Jeśli na przykład chcesz skanować komunikację między dwiema odrębnymi grupami osób lub chcesz określić grupę, która nie jest nadzorowana. Po przypisaniu grupy dystrybucyjnej w zasadach zasady monitorują wszystkie wiadomości e-mail od każdego użytkownika w grupie dystrybucyjnej. Po przypisaniu grupy Microsoft 365 w zasadach zasady monitorują wszystkie wiadomości e-mail wysyłane do tej grupy, a nie poszczególne wiadomości e-mail odebrane przez każdego członka grupy.

Dodawanie grup i list dystrybucyjnych do zasad zgodności komunikacji jest częścią ogólnych warunków i reguł, dlatego maksymalna liczba grup i list dystrybucyjnych obsługiwanych przez zasady różni się w zależności od liczby warunków dodanych do zasad. Każda zasada powinna obsługiwać około 20 grup lub list dystrybucyjnych, w zależności od liczby dodatkowych warunków występujących w zasadach.

Użyj poniższego wykresu, aby ułatwić konfigurowanie grup w organizacji pod kątem zasad zgodności z komunikacją:

| **Członek zasad** | **Obsługiwane grupy** | **Nieobsługiwanych grup** |
|:-----|:-----|:-----|
|Użytkownicy nadzorowane <br> Wykluczeni użytkownicy | Grupy dystrybucyjne <br> Grupy Microsoft 365 | Dynamiczne grupy dystrybucji <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty <br> Microsoft 365 grupy z członkostwem dynamicznym |
| Wszyscy oceniający | Brak | Grupy dystrybucyjne <br> Dynamiczne grupy dystrybucji <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty |

### <a name="privacy"></a>Prywatność

Ochrona prywatności użytkowników, którzy mają dopasowania zasad, jest ważna i może pomóc w promowaniu obiektywizmu w badaniach danych i przeglądach analiz dla alertów zgodności komunikacji. To ustawienie dotyczy tylko nazw użytkowników wyświetlanych w rozwiązaniu zgodności komunikacji. Nie ma to wpływu na sposób wyświetlania nazw w innych rozwiązaniach zgodności ani w centrum administracyjnym.

W przypadku użytkowników z dopasowaniem zgodności komunikacji możesz wybrać jedno z następujących ustawień w **obszarze Ustawienia zgodności komunikacji**:

- **Pokaż zanonimizowane wersje nazw użytkowników: nazwy użytkowników** są anonimizowane, aby uniemożliwić użytkownikom w grupie ról *analityka zgodności komunikacji* wyświetlanie, kto jest skojarzony z alertami zasad. Użytkownicy w grupie ról *Badacz zgodności komunikacji* zawsze będą widzieć nazwy użytkowników, a nie zanonimizowane wersje. Na przykład użytkownik "Grace Taylor" będzie wyświetlany z losowym pseudonimem, takim jak "AnonIS8-988" we wszystkich obszarach środowiska zgodności z komunikacją. Wybranie tego ustawienia powoduje zanonimizowanie wszystkich użytkowników z bieżącymi i wcześniejszymi dopasowaniami zasad i ma zastosowanie do wszystkich zasad. Informacje o profilu użytkownika w szczegółach alertu zgodności komunikacji nie będą dostępne po wybraniu tej opcji. Jednak nazwy użytkowników są wyświetlane podczas dodawania nowych użytkowników do istniejących zasad lub przypisywania użytkowników do nowych zasad. Jeśli zdecydujesz się wyłączyć to ustawienie, nazwy użytkowników będą wyświetlane dla wszystkich użytkowników, którzy mają bieżące lub wcześniejsze dopasowania zasad.
- **Nie pokazuj zanonimizowanych wersji nazw użytkowników**: nazwy użytkowników są wyświetlane dla wszystkich bieżących i przeszłych dopasowań zasad dla alertów zgodności komunikacji. Informacje o profilu użytkownika (nazwa, tytuł, alias oraz organizacja lub dział) są wyświetlane dla użytkownika dla wszystkich alertów dotyczących zgodności komunikacji.

## <a name="plan-for-policies"></a>Planowanie zasad

Tworzenie zasad zgodności komunikacji jest szybkie i łatwe dzięki [wstępnie zdefiniowanym szablonom](communication-compliance-policies.md#policy-templates) dotyczącym nieodpowiedniej zawartości, informacji poufnych i zgodności z przepisami. Niestandardowe zasady zgodności komunikacji umożliwiają elastyczne wykrywanie i badanie problemów specyficznych dla organizacji i wymagań.

Podczas planowania zasad zgodności z komunikacją należy wziąć pod uwagę następujące obszary:

- Rozważ dodanie wszystkich użytkowników w organizacji jako zakresu zasad zgodności komunikacji. Identyfikowanie określonych użytkowników jako w zakresie poszczególnych zasad jest przydatne w pewnych okolicznościach, jednak większość organizacji powinna uwzględniać wszystkich użytkowników w zasadach zgodności komunikacji zoptymalizowanych pod kątem wykrywania molestowania lub dyskryminacji.
- Skonfiguruj procent komunikacji do przejrzenia na poziomie 100%, aby upewnić się, że zasady wychwytują wszystkie problemy związane z komunikacją dla organizacji.
- Możesz skanować komunikację ze [źródeł innych firm](communication-compliance-channels.md#third-party-sources) pod kątem danych zaimportowanych do skrzynek pocztowych w organizacji Microsoft 365. Aby uwzględnić przegląd komunikacji na tych platformach, należy skonfigurować łącznik dla tych usług, zanim komunikaty spełniające warunki zasad będą monitorowane przez zasady komunikacji.
- Zasady mogą obsługiwać języki monitorowania inne niż angielski w niestandardowych zasadach zgodności komunikacji. Utwórz [niestandardowy słownik słów kluczowych](communication-compliance-policies.md#custom-keyword-dictionaries) zawierający obraźliwe słowa w wybranym języku lub skompiluj własny model uczenia maszynowego przy użyciu [klasyfikatorów z możliwością trenowania](classifier-get-started-with.md) w Microsoft 365.
- Wszystkie organizacje mają różne standardy komunikacyjne i wymagania dotyczące zasad. Monitoruj pod kątem określonych słów kluczowych przy użyciu [warunków zasad](communication-compliance-policies.md#conditional-settings) zgodności komunikacji lub monitoruj pod kątem określonych typów informacji z [niestandardowymi typami informacji poufnych](create-a-custom-sensitive-information-type.md).

## <a name="creating-a-communication-compliance-policy-walkthrough"></a>Przewodnik po tworzeniu zasad zgodności komunikacji

Chcesz zapoznać się z szczegółowym przewodnikiem konfigurowania nowych zasad zgodności komunikacji i korygowania alertu? Zapoznaj się z poniższym 15-minutowym filmem wideo, aby zobaczyć pokaz sposobu, w jaki zasady zgodności komunikacji mogą pomóc w wykrywaniu nieodpowiednich komunikatów, badaniu potencjalnych naruszeń i korygowaniu problemów ze zgodnością.
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RWNchy]
<br>

## <a name="ready-to-get-started"></a>Chcesz rozpocząć pracę?

Aby skonfigurować zgodność komunikacji dla organizacji Microsoft 365, zobacz [Konfigurowanie zgodności z komunikacją](communication-compliance-configure.md) lub zapoznaj się z [analizą przypadku firmy Contoso](communication-compliance-case-study.md) oraz jak szybko skonfigurowali zasady zgodności komunikacji w celu monitorowania pod kątem nieodpowiedniej zawartości w Microsoft Teams, Exchange Online i Yammer  Komunikacji.
