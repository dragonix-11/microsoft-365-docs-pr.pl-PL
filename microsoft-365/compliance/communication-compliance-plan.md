---
title: Planowanie zgodności komunikacji
description: Dowiedz się więcej o planowaniu korzystania ze zgodności komunikacyjnej w organizacji.
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
ms.openlocfilehash: 77579a97016d37dd9bfc12f88db62200fbca0ccc
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2022
ms.locfileid: "63014785"
---
# <a name="plan-for-communication-compliance"></a>Planowanie zgodności komunikacji

Przed rozpoczęciem [pracy nad](communication-compliance.md) zgodnością w zakresie komunikacji w organizacji należy uwzględnić ważne działania i zagadnienia związane z planowaniem, które należy przejrzeć przez Twoje zespoły ds. technologii informatycznych i zarządzania zgodnością. Dokładne zrozumienie i zaplanowanie wdrożenia w następujących obszarach pomoże zapewnić płynne wdrożenie i korzystanie z funkcji zgodności komunikacyjnej zgodnie z najlepszymi rozwiązaniami.

> [!IMPORTANT]
> Zgodność komunikacji jest obecnie dostępna w dzierżawach hostowanych w regionach geograficznych i krajach obsługiwanych przez zależności usługi Azure. Aby sprawdzić, czy zgodność komunikacji jest obsługiwana przez Twoją organizację, zobacz Dostępność usługi [Azure dependency według kraju/regionu](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="transitioning-from-supervision-in-office-365"></a>Przejście z nadzorem w Office 365

W przypadku organizacji korzystających z nadzorów w Office 365 należy od razu zaplanować przejście do zasad zgodności komunikacji w programie Microsoft 365 oraz zrozumieć te ważne kwestie:

- Rozwiązanie pod nadzorem Office 365 zostało w pełni zastąpione przez rozwiązanie do zapewnienia zgodności komunikacyjnej w Microsoft 365. Zalecamy tworzenie nowych zasad w zakresie zgodności z komunikacją, które mają takie same ustawienia jak istniejące zasady pod nadzorem, aby korzystać z nowych ulepszeń badania i rozwiązywania problemów.
- Wiadomości zapisane pod nadzorem Office 365 zgodności zasad nie mogą być przenoszone ani udostępniane w celu zapewnienia zgodności komunikacji w Microsoft 365.
- W przypadku organizacji, w których oba rozwiązania są używane obok siebie podczas procesu przejścia, zasady używane w każdym rozwiązaniu muszą mieć unikatowe nazwy zasad. Grupy i niestandardowe słowniki słów kluczowych mogą być udostępniane między rozwiązaniami w okresie przejścia.

Aby uzyskać informacje o wycofania z pracy Office 365, zobacz Przewodnik po [programie Microsoft 365, aby](https://www.microsoft.com/microsoft-365/roadmap) uzyskać szczegółowe informacje.

## <a name="work-with-stakeholders-in-your-organization"></a>Praca z uczestnikami projektu w organizacji

Zidentyfikuj odpowiednie osoby biorące udział w projektach w organizacji, aby współpracować w zakresie działań dotyczących alertów dotyczących zgodności komunikacji. Niektóre zalecane osoby biorące udział w planowaniu wstępnym i end-to-end communication [compliance](communication-compliance.md#workflow) przepływ pracy to osoby z następujących obszarów organizacji:

- Technologia informacyjna
- Zgodność
- Prywatność
- Bezpieczeństwo
- Zasoby ludzkie
- Legal

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Planowanie przepływu pracy badania i rozwiązywania problemów

### <a name="permissions"></a>Uprawnienia

Wybierz dedykowanych uczestników projektu, aby monitorować i przeglądać alerty i sprawy w regularny sposób [w Centrum zgodności platformy Microsoft 365.](https://compliance.microsoft.com/) Upewnij się, że rozumiesz sposób przypisywania użytkowników i uczestników projektu do różnych grup ról zgodności komunikacji w organizacji.

> [!IMPORTANT]
> Po skonfigurowaniu grup ról może upłynąć do 30 minut, aby uprawnienia grupy ról dotyczyły przypisanych użytkowników w organizacji.

Do konfigurowania początkowych uprawnień w celu zarządzania funkcjami zgodności komunikacji jest używanych sześć grup ról. Aby zapewnić **zgodność komunikacji** jako opcję menu w programie Centrum zgodności platformy Microsoft 365 i kontynuować te kroki konfiguracji, musisz mieć przypisaną jedną z następujących ról lub grup ról:

- Azure Active Directory [*administrator globalny*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*administratora*](/azure/active-directory/roles/permissions-reference#compliance-administrator) zgodności
- Centrum zgodności platformy Microsoft 365 [*ról Zarządzanie*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) organizacją
- Centrum zgodności platformy Microsoft 365 [*ról Administrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) zgodności
- *Communication Compliance* role group
- *Grupa ról Administrator zgodności komunikacji*

Członkowie następujących ról mają te same uprawnienia rozwiązania zawarte w grupie ról Administrator *zgodności* komunikacji:

- Azure Active Directory *administrator globalny*
- Azure Active Directory *administratora zgodności*
- Centrum zgodności platformy Microsoft 365 *zarządzanie organizacją*
- Centrum zgodności platformy Microsoft 365 *zgodności*

> [!IMPORTANT]
> Upewnij się, że w grupach ról Zgodność z komunikacją lub Administrator  zgodności komunikacji (w zależności od wybranej opcji) zawsze jest co najmniej jeden użytkownik, aby konfiguracja zgodności komunikacji nie była dostępna w scenariuszu "zero administratora", jeśli określone osoby opuszczają Twoją organizację.

W zależności od tego, jak chcesz zarządzać zasadami i alertami zgodności komunikacji, konieczne będzie przypisanie użytkowników do określonych grup ról w celu zarządzania różnymi zestawami funkcji zgodności komunikacji. Użytkownikom z różnymi zakresami obowiązków w zakresie zgodności można przypisać określone grupy ról w celu zarządzania różnymi obszarami funkcji zgodności komunikacji. Możesz także przypisać wszystkie konta użytkowników dla wyznaczonych administratorów, analityków, osób oglądających i osoby przeglądowe do grupy ról *Zgodność* z komunikacją. Korzystaj z jednej lub wielu grup ról, aby jak najlepiej dopasować się do wymagań zarządzania zgodnością.

Podczas konfigurowania zgodności komunikacji i zarządzania zgodnością wybierz jedną z tych opcji grupy ról rozwiązania:

|**Rola**|**Uprawnienia roli**|
|:-----|:-----|
| **Zgodność komunikacji** | Ta grupa ról pozwala zarządzać zgodnością komunikacji dla organizacji w jednej grupie. Dodając wszystkie konta użytkowników przeznaczone dla wyznaczonych administratorów, analityków, osób oglądających i wyeks odpowiednie osoby, możesz skonfigurować uprawnienia do zgodności komunikacji w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień zgodności komunikacji. Ta konfiguracja jest najprostszym sposobem szybkiego rozpoczęcia pracy z przepisami komunikacji i dobrze pasuje do organizacji, które nie potrzebują osobnych uprawnień zdefiniowanych dla osobnych grup użytkowników. Użytkownicy, którzy tworzą zasady jako administrator zgodności komunikacji, muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online. |
| **Administrator zgodności komunikacji** | Ta grupa ról umożliwia wstępne skonfigurowanie zgodności komunikacji, a później podział administratorów zgodności komunikacji na zdefiniowaną grupę. Użytkownicy przypisani do tej grupy ról mogą tworzyć, odczytywać, aktualizować i usuwać zasady zgodności komunikacji, ustawienia globalne i przypisania grup ról. Użytkownicy przypisani do tej grupy ról nie mogą wyświetlać alertów o wiadomościach. Użytkownicy, którzy tworzą zasady jako administrator zgodności komunikacji, muszą mieć swoją skrzynkę pocztową hostowaną w Exchange Online. |
| **Analityk zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak analitycy zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać zasady przypisane do nich jako recenzenty, wyświetlać metadane wiadomości (bez zawartości wiadomości), eskalować do dodatkowych recenzentów lub wysyłać do użytkowników powiadomienia. Analitycy nie mogą rozstrzygić oczekujących alertów. |
| **Działania w zakresie zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak uprawnienia do zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać metadane i zawartość wiadomości, eskalacji do dodatkowych recenzentów, eskalować do sprawy Advanced eDiscovery, wysyłać powiadomienia do użytkowników i rozwiązywać alert. |
| **Przeglądarka zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą zarządzać raportami do komunikacji. Użytkownicy przypisani do tej grupy ról mają dostęp do wszystkich widżetów raportowania na stronie głównej zgodności komunikacji i mogą wyświetlać wszystkie raporty zgodności komunikacji. |

### <a name="supervised-users"></a>Nadzór nad użytkownikami

Przed rozpoczęciem korzystania ze zgodności komunikacji należy określić, kto musi przejrzeć ich komunikację. W zasadach adresy e-mail użytkowników identyfikują osoby lub grupy osób pod nadzorem. Przykładami tych grup są grupy Microsoft 365, Exchange, społeczności Yammer i Microsoft Teams kanały. Możesz też wykluczyć konkretnych użytkowników lub grupy z skanowania za pomocą określonej grupy wykluczeń lub listy grup. Aby uzyskać więcej informacji na temat typów grup obsługiwanych w zasadach zgodności komunikacji, zobacz [Wprowadzenie do zgodności komunikacji](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance).

> [!IMPORTANT]
> Użytkownicy objęci zasadami zgodności komunikacji muszą posiadać licencję Zgodność platformy Microsoft 365 E5, licencję Office 365 Enterprise E3 z dodatku Advanced Compliance lub być objęci subskrypcją usługi Office 365 Enterprise E5. Jeśli nie masz jeszcze planu Enterprise E5 i chcesz wypróbować zgodność z komunikacją, możesz utworzyć konto w celu wypróbowania Office 365 Enterprise [E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Recenzentzy

Tworząc zasady zgodności komunikacji, musisz określić, kto przegląda wiadomości o nadzorowanych użytkownikach. W zasadach adresy e-mail użytkowników identyfikują osoby lub grupy osób do przeglądu komunikacji nadzorowanej. Wszyscy recenzentzy muszą mieć skrzynki pocztowe hostowane w programie Exchange Online, muszą zostać przypisani do grup ról  Analityk zgodności komunikacji lub Komunikacji i muszą zostać przypisani do zasad, które muszą zbadać. Po dodaniu recenzentów do zasad automatycznie otrzymuje on wiadomość e-mail z powiadomieniem o przypisaniu do zasad i linkami do informacji o procesie sprawdzania.

### <a name="groups-for-supervised-users-and-reviewers"></a>Grupy dla użytkowników nadzorowanych i recenzentów

Aby uprościć konfigurację, utwórz grupy dla osób, które chcą przeglądać komunikację, oraz grupy dla osób przeglądających te informacje. Jeśli korzystasz z grup, może być ich kilka. Na przykład jeśli chcesz przeskanować komunikację między dwiema różnymi grupami osób lub określić grupę, która nie jest nadzorowana. Po przypisaniu grupy dystrybucyjnej do zasad zasady monitoruje wszystkie wiadomości e-mail od poszczególnych użytkowników w grupie dystrybucyjnej. Podczas przypisywania grupy Microsoft 365 w zasadach zasady monitoruje wszystkie wiadomości e-mail wysyłane do tej grupy, a nie poszczególne wiadomości e-mail otrzymane przez poszczególnych członków grupy.

Dodawanie grup i list dystrybucyjnych do zasad zgodności komunikacji stanowi część ogólnego zestawu reguł i warunków, więc maksymalna liczba grup i list dystrybucyjnych, które obsługuje zasada, różni się w zależności od liczby warunków dodanych również do zasad. Każda zasada powinna obsługiwać około 20 grup lub list dystrybucyjnych w zależności od liczby dodatkowych warunków w zasadach.

Skorzystaj z poniższego wykresu, aby ułatwić konfigurowanie grup w organizacji pod celu stosowania zasad zgodności komunikacji:

| **Członek zasad** | **Obsługiwane grupy** | **Nieobsługiwane grupy** |
|:-----|:-----|:-----|
|Nadzór nad użytkownikami <br> Wykluczeni użytkownicy | Grupy dystrybucyjne <br> Microsoft 365 grupy | Dynamiczne grupy dystrybucyjne <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty <br> Microsoft 365 grup z członkostwem dynamicznym |
| Recenzentzy | Brak | Grupy dystrybucyjne <br> Dynamiczne grupy dystrybucyjne <br> Zagnieżdżone grupy dystrybucyjne <br> Grupy zabezpieczeń z obsługą poczty |

### <a name="privacy"></a>Prywatność

Ochrona prywatności użytkowników, którzy mają zgodność z zasadami, jest ważna i może ułatwić promowanie obiektowości w przeglądach analizy i analizy danych w przypadku alertów zgodności komunikacji. To ustawienie dotyczy tylko nazw użytkowników wyświetlanych w rozwiązaniu do zgodności komunikacji. Nie wpływa to na sposób wyświetlania nazw w innych rozwiązaniach zgodności ani w centrum administracyjnym.

W przypadku użytkowników, którzy mają zgodność ze zgodnością komunikacji, możesz wybrać jedno z następujących ustawień w **ustawieniach zgodności komunikacji**:

- **Wyświetlanie zaimnkowanych** wersji nazw użytkowników: Nazwy użytkowników są anonimizowane, aby  uniemożliwić użytkownikom w grupie ról analityka zgodności komunikacji wyświetlanie osób skojarzonych z alertami zasad. Użytkownicy w grupie ról *Zgodności komunikacyjnej będą* zawsze widzieć nazwy użytkowników, a nie wersje zanonimizowane. Na przykład użytkownik Grace Taylor może pojawić się z przypadkowym pseudonimem, takim jak "AnonIS8-988" we wszystkich obszarach działania w zakresie zgodności komunikacji. Wybranie tego ustawienia powoduje, że wszyscy użytkownicy mają aktualne i przeszłe dopasowania oraz mają zastosowanie do wszystkich zasad. Po wybrać tę opcję informacje zawarte w profilu użytkownika w szczegółach alertu zgodności komunikacji nie będą dostępne. Nazwy użytkowników są jednak wyświetlane podczas dodawania nowych użytkowników do istniejących zasad lub przypisywania użytkowników do nowych zasad. Jeśli wyłączysz to ustawienie, nazwy użytkowników będą wyświetlane dla wszystkich użytkowników, którzy mają dopasowania do bieżących lub wcześniejszych zasad.
- **Nie pokazuj anonimizowanych** wersji nazw użytkowników: Nazwy użytkowników są wyświetlane dla wszystkich bieżących i przeszłych zgodności zasad dla alertów zgodności komunikacji. Dla wszystkich alertów dotyczących zgodności komunikacji są wyświetlane informacje z profilu użytkownika (imię i nazwisko, tytuł, alias oraz organizacja lub dział).

## <a name="plan-for-policies"></a>Planowanie zasad

Tworzenie zasad zgodności komunikacji jest szybkie i łatwe dzięki wstępnie [](communication-compliance-policies.md#policy-templates) zdefiniowanym szablonom do przechowywania nieodpowiedniej zawartości, informacji poufnych i zgodności z przepisami. Niestandardowe zasady zgodności komunikacji zapewniają elastyczność w zakresie wykrywania i badania problemów specyficznych dla organizacji i wymagań.

Planując zasady zgodności komunikacji, rozważ następujące obszary:

- Rozważ możliwość dodania wszystkich użytkowników w organizacji jako zakres zasad zgodności komunikacji. Zidentyfikowanie konkretnych użytkowników jako zakresów poszczególnych zasad jest przydatne w pewnych okolicznościach, jednak większość organizacji powinna uwzględniać wszystkich użytkowników w zasadach zgodności komunikacji zoptymalizowanych pod kątem molestowania lub wykrywania molestowania.
- Skonfiguruj wartość procentową przeglądanych wiadomości na poziomie 100%, aby upewnić się, że zasady wychwytują wszystkie problemy, na które mogą nas martwić w komunikacji z Twoją organizacją.
- Możesz skanować komunikację [ze źródeł innych firm w](communication-compliance-channels.md#third-party-sources) poszukiwaniu danych zaimportowanych do skrzynek pocztowych w Twojej Microsoft 365 organizacji. Aby uwzględnić przegląd komunikacji na tych platformach, musisz skonfigurować łącznik z tymi usługami, zanim wiadomości będą monitorowane przez zasady komunikacji.
- Zasady mogą obsługiwać języki monitorowania inne niż angielski w niestandardowych zasadach zgodności komunikacji. Tworzenie [niestandardowego słownika słów](communication-compliance-policies.md#custom-keyword-dictionaries) kluczowych dla obraźliwych wyrazów w wybranej wersji językowej lub tworzenie własnego modelu uczenia maszynowego przy użyciu przeszkolnych klasyfikatorów w Microsoft 365.[](classifier-get-started-with.md)
- Wszystkie organizacje mają różne standardy komunikacji i potrzeby w zakresie zasad. Monitorowanie określonych słów kluczowych przy użyciu warunków zasad zgodności [komunikacji](communication-compliance-policies.md#conditional-settings) lub monitorowanie określonych typów informacji z niestandardowymi [typami informacji poufnych](create-a-custom-sensitive-information-type.md).

## <a name="creating-a-communication-compliance-policy-walkthrough"></a>Tworzenie instruktażu dotyczących zasad zgodności komunikacji

Chcesz uzyskać szczegółowe informacje dotyczące konfigurowania nowych zasad zgodności komunikacji i rozwiązywania problemów z alertem? Obejrzyj poniższy 15-minutowy klip wideo, aby zobaczyć, jak zasady zgodności komunikacji mogą ułatwić wykrywanie nieodpowiednich wiadomości, badanie potencjalnych naruszeń i rozwiązywanie problemów ze zgodnością.
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RWNchy]
<br>

## <a name="ready-to-get-started"></a>Wszystko gotowe do rozpoczęcia?

Aby skonfigurować zgodność komunikacji dla organizacji usługi Microsoft 365, zobacz Konfigurowanie zgodności komunikacji dla usługi Microsoft 365 lub zapoznaj się z analizą przypadku firmy [Contoso](communication-compliance-case-study.md) i tym, jak szybko skonfigurowali zasady zgodności komunikacji w celu monitorowania nieodpowiedniej zawartości w programie [Microsoft Teams](communication-compliance-configure.md), Exchange Online i Yammer komunikacji.
