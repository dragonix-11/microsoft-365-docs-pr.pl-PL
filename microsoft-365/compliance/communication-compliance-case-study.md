---
title: Analiza przypadku — firma Contoso konfiguruje zasady nieodpowiedniego tekstu
description: Analiza przypadku firmy Contoso i sposób szybkiego konfigurowania zasad zgodności komunikacji w celu wykrywania nieodpowiedniego tekstu w usłudze Microsoft Teams, Exchange Online i komunikacji usługi Yammer.
keywords: Microsoft 365, Microsoft Purview, zgodność, zgodność z komunikacją
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.custom:
- admindeeplinkMAC
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- remotework
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d5a26aaa78b1a67acf3dd39ec3fbfa0b3fcb26b9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639016"
---
# <a name="case-study---contoso-quickly-configures-an-inappropriate-text-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Analiza przypadku — firma Contoso szybko konfiguruje nieodpowiednie zasady tekstowe dotyczące komunikacji z usługami Microsoft Teams, Exchange i Yammer

Zgodność w komunikacji w Microsoft Purview pomaga zminimalizować ryzyko związane z komunikacją, pomagając wykrywać, przechwytywać i działać na komunikatach z nieodpowiednim tekstem w organizacji. nieodpowiedni tekst może obejmować wulgaryzmy, groźby, nękanie i nieodpowiednie obrazy. Wstępnie zdefiniowane i niestandardowe zasady umożliwiają skanowanie komunikacji wewnętrznej i zewnętrznej pod kątem dopasowań zasad, aby mogły zostać zbadane przez wyznaczonych recenzentów. Recenzenci mogą badać zeskanowaną pocztę e-mail, usługę Microsoft Teams, usługę Yammer lub komunikację innych firm w organizacji i podejmować odpowiednie działania korygujące, aby upewnić się, że są one zgodne ze standardami wiadomości organizacji.

Contoso Corporation to fikcyjna organizacja, która musi szybko skonfigurować zasady w celu wykrywania nieodpowiedniego tekstu. Korzystali oni głównie z platformy Microsoft 365 do obsługi poczty e-mail, usługi Microsoft Teams i usługi Yammer dla swoich użytkowników, ale mają nowe wymagania dotyczące wymuszania zasad firmy dotyczących nękania w miejscu pracy. Administratorzy IT i specjaliści ds. zgodności firmy Contoso mają podstawową wiedzę na temat podstaw pracy z platformą Microsoft 365 i szukają kompleksowych wskazówek dotyczących szybkiego rozpoczęcia pracy ze zgodnością z komunikacją.

Ta analiza przypadku obejmuje podstawy szybkiego konfigurowania zasad zgodności komunikacji w celu wykrywania nieodpowiedniego tekstu. Te wskazówki obejmują:

- Krok 1 . Planowanie zgodności komunikacji
- Krok 2. Uzyskiwanie dostępu do zgodności z komunikacją
- Krok 3. Konfigurowanie wymagań wstępnych i tworzenie zasad zgodności komunikacji
- Krok 4. Badanie i korygowanie alertów

## <a name="step-1-planning-for-communication-compliance"></a>Krok 1. Planowanie zgodności komunikacji

Administratorzy IT i specjaliści ds. zgodności firmy Contoso wzięli udział w seminariach internetowych dotyczących rozwiązań zgodności w usłudze Microsoft 365 i zdecydowali, że zasady zgodności komunikacji pomogą im spełnić zaktualizowane wymagania dotyczące zasad firmy w celu ograniczenia nękania w miejscu pracy. Wspólnie opracowali plan tworzenia i włączania zasad zgodności komunikacji, które będą wykrywać nieodpowiednie komunikaty. Ta konfiguracja obejmuje wykrywanie tekstu dla czatów wysyłanych w usłudze Microsoft Teams, wiadomości prywatnych i konwersacji społeczności w usłudze Yammer oraz wiadomości e-mail wysyłanych w Exchange Online. Ich plan obejmuje identyfikację:

- Administratorzy IT, którzy potrzebują dostępu do funkcji zgodności komunikacji.
- Specjaliści ds. zgodności, którzy muszą tworzyć zasady komunikacji i zarządzać nimi.
- Specjaliści ds. zgodności i inni współpracownicy z innych działów (Human Resources, Legal itp.), którzy muszą badać i korygować alerty zgodności komunikacji.
- Użytkownicy, którzy będą w zakresie zasady zgodności komunikacji nieodpowiedni tekst.

### <a name="licensing"></a>Licencjonowanie

Pierwszym krokiem jest potwierdzenie, że licencjonowanie platformy Microsoft 365 firmy Contoso obejmuje obsługę rozwiązania do zapewniania zgodności z komunikacją. Aby uzyskać dostęp do zgodności z komunikacją i korzystać z niej, administratorzy IT firmy Contoso muszą sprawdzić, czy firma Contoso ma jedną z następujących funkcji:

- subskrypcja Microsoft 365 E5/A5/F5/G5 (wersja płatna lub próbna)
- subskrypcja Microsoft 365 E3/A3/F3/G5 + dodatek zgodności Microsoft 365 E5/A5/F5/G5
- subskrypcja Microsoft 365 E3/A3/F3/G5 + dodatek Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- subskrypcja Office 365 Enterprise E5 (wersja płatna lub próbna)
- subskrypcja Office 365 A5 (wersja płatna lub próbna)
- Office 365 Enterprise subskrypcję E3 + dodatek Office 365 Advanced Compliance (nie jest już dostępny dla nowych subskrypcji, zobacz uwaga)

Użytkownikom uwzględnionym w zasadach zgodności komunikacji należy przypisać jedną z powyższych licencji. Aby uzyskać więcej informacji na temat subskrypcji i licencjonowania, zobacz [Wskazówki dotyczące zabezpieczeń & zgodności z usługą Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Office 365 Advanced Compliance nie jest już sprzedawana jako subskrypcja autonomiczna. Po wygaśnięciu bieżących subskrypcji klienci powinni przejść do jednej z powyższych subskrypcji, która zawiera te same lub dodatkowe funkcje zgodności.

Administratorzy IT firmy Contoso wykonaj następujące kroki, aby zweryfikować obsługę licencjonowania dla firmy Contoso:

1. Administratorzy IT logują się do Centrum administracyjne platformy Microsoft 365 <https://admin.microsoft.com> i przechodzą do Centrum administracyjne platformy Microsoft 365 ><a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">**licencji rozliczeniowych**</a> > .

2. W tym miejscu potwierdzają, że mają jedną z [opcji licencji](communication-compliance-configure.md#subscriptions-and-licensing) , która obejmuje obsługę zgodności z komunikacją.

![Licencjonowanie zgodności komunikacji.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Uprawnienia do zgodności komunikacji

Istnieje pięć grup ról używanych do konfigurowania uprawnień do zarządzania funkcjami zgodności komunikacji. Aby udostępnić **zgodność z komunikacją** jako opcję menu w portal zgodności Microsoft Purview i kontynuować te kroki konfiguracji, administratorzy firmy Contoso mają przypisaną rolę *Administracja zgodności z komunikacją*.

Firma Contoso postanawia użyć grupy ról *Zgodność z komunikacją* , przypisując do grupy wszystkich administratorów zgodności z komunikacją, analityków, badaczy i osób przeglądających. Ta konfiguracja grupy ról ułatwia firmie Contoso szybkie rozpoczęcie pracy i najlepiej odpowiada wymaganiom dotyczącym zarządzania zgodnością.

|**Rola**|**Uprawnienia roli**|
|:-----|:-----|
| **Zgodność z komunikacją** | Ta grupa ról służy do zarządzania zgodnością komunikacji dla organizacji w jednej grupie. Dodając wszystkie konta użytkowników dla wyznaczonych administratorów, analityków, badaczy i osób przeglądających, możesz skonfigurować uprawnienia do zgodności komunikacji w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień zgodności komunikacji. Ta konfiguracja grupy ról jest najprostszym sposobem szybkiego rozpoczęcia pracy ze zgodnością z komunikacją i jest dobrym rozwiązaniem dla organizacji, które nie potrzebują oddzielnych uprawnień zdefiniowanych dla oddzielnych grup użytkowników. |
| **Administracja zgodności z komunikacją** | Użyj tej grupy ról, aby początkowo skonfigurować zgodność z komunikacją, a później segregować administratorów zgodności komunikacji do zdefiniowanej grupy. Użytkownicy przypisani do tej grupy ról mogą tworzyć, odczytywać, aktualizować i usuwać zasady zgodności komunikacji, ustawienia globalne i przypisania grup ról. Użytkownicy przypisani do tej grupy ról nie mogą wyświetlać alertów komunikatów. |
| **Analityk zgodności komunikacji** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą pełnić rolę analityków zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać zasady, w których są przypisani jako recenzenci, wyświetlać metadane komunikatów (nie zawartość komunikatów), eskalować do dodatkowych recenzentów lub wysyłać powiadomienia do użytkowników. Analitycy nie mogą rozwiązywać oczekujących alertów. |
| **Badacz zgodności z komunikacją** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą pełnić rolę badaczy zgodności z komunikacją. Użytkownicy przypisani do tej grupy ról mogą wyświetlać metadane komunikatów i zawartość, eskalować do dodatkowych recenzentów, eskalować do sprawy zbierania elektronicznych materiałów dowodowych (Premium), wysyłać powiadomienia do użytkowników i rozwiązywać alert. |
| **Podgląd zgodności komunikacji** | Ta grupa służy do przypisywania uprawnień do użytkowników, którzy będą zarządzać raportami komunikacji. Użytkownicy przypisani do tej grupy ról mogą uzyskiwać dostęp do wszystkich widżetów raportowania na stronie głównej zgodności komunikacji i mogą wyświetlać wszystkie raporty zgodności komunikacji. |

1. Administratorzy IT firmy Contoso logują się na stronie uprawnień [portal zgodności Microsoft Purview](https://compliance.microsoft.com/permissions) przy użyciu poświadczeń konta administratora globalnego i wybierają link do wyświetlania ról i zarządzania nimi na platformie Microsoft 365.
2. W portal zgodności Microsoft Purview przechodzą do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a> i wybierają link do wyświetlania ról i zarządzania nimi w Office 365.
3. Administratorzy wybierają grupę ról *Zgodność z komunikacją* , a następnie wybierają pozycję **Edytuj grupę ról**.
4. Administratorzy wybierają pozycję **Wybierz członków** w okienku nawigacji po lewej stronie, a następnie wybierz pozycję **Edytuj**.
5. Wybierają pozycję **Dodaj** , a następnie zaznaczają pole wyboru dla wszystkich użytkowników firmy Contoso, którzy będą zarządzać zgodnością komunikacji, badać i przeglądać alerty.
6. Administratorzy wybierają pozycję **Dodaj**, a następnie wybierz pozycję **Gotowe**.
7. Wybierają pozycję **Zapisz** , aby dodać użytkowników firmy Contoso do grupy ról. Wybierają pozycję **Zamknij** , aby wykonać kroki.

## <a name="step-2-accessing-communication-compliance"></a>Krok 2. Uzyskiwanie dostępu do zgodności z komunikacją

Po skonfigurowaniu uprawnień do zgodności z komunikacją administratorzy IT i specjaliści ds. zgodności firmy Contoso przypisani do grupy ról Zgodność komunikacji mogą uzyskać dostęp do rozwiązania do zapewniania zgodności komunikacji w usłudze Microsoft Purview. Administratorzy IT i specjaliści ds. zgodności firmy Contoso mają kilka sposobów uzyskiwania dostępu do zgodności z komunikacją i rozpoczynania tworzenia nowych zasad:

- Uruchamianie bezpośrednio z rozwiązania do zapewniania zgodności z komunikacją
- Począwszy od portal zgodności Microsoft Purview
- Począwszy od katalogu rozwiązań Usługi Microsoft Purview
- Począwszy od Centrum administracyjne platformy Microsoft 365

### <a name="starting-directly-from-the-communication-compliance-solution"></a>Uruchamianie bezpośrednio z rozwiązania do zapewniania zgodności z komunikacją

Najszybszym sposobem uzyskania dostępu do rozwiązania jest zalogowanie się bezpośrednio do rozwiązania **do zapewniania zgodności z komunikacją** (<https://compliance.microsoft.com/supervisoryreview>). Korzystając z tego linku, administratorzy IT i specjaliści ds. zgodności firmy Contoso zostaną przekierowani do strony głównej zgodności z komunikacją, na której można szybko przejrzeć stan alertów i utworzyć nowe zasady na podstawie wstępnie zdefiniowanych szablonów.

![Strona główna zgodności z komunikacją.](../media/communication-compliance-home.png)

### <a name="starting-from-the-microsoft-purview-compliance-portal"></a>Począwszy od portal zgodności Microsoft Purview

Innym łatwym sposobem uzyskiwania dostępu do rozwiązania zgodności z komunikacją przez administratorów IT i specjalistów ds. zgodności firmy Contoso jest zalogowanie się bezpośrednio do [portal zgodności Microsoft Purview](https://compliance.microsoft.com). Po zalogowaniu użytkownicy muszą po prostu wybrać kontrolkę **Pokaż wszystko** , aby wyświetlić wszystkie rozwiązania zgodności, a następnie wybrać rozwiązanie **do zgodności z komunikacją** , aby rozpocząć pracę.

![Centrum zgodności.](../media/communication-compliance-compliance-portal.png)

### <a name="starting-from-the-microsoft-purview-solution-catalog"></a>Począwszy od katalogu rozwiązań Usługi Microsoft Purview

Administratorzy IT i specjaliści ds. zgodności firmy Contoso mogą również wybrać dostęp do rozwiązania zgodności z komunikacją, wybierając katalog rozwiązań Microsoft Purview. Wybierając pozycję **Wykaz** w sekcji **Rozwiązania** w obszarze nawigacji po lewej stronie w **portal zgodności Microsoft Purview**, mogą otworzyć wykaz rozwiązań z listą wszystkich rozwiązań usługi Microsoft Purview. Przewiń w dół do sekcji **Zarządzanie ryzykiem wewnętrznym** , administratorzy IT firmy Contoso mogą wybrać pozycję Zgodność z komunikacją, aby rozpocząć pracę. Administratorzy IT firmy Contoso decydują się również na użycie kontrolki nawigacji Pokaż w, aby przypiąć rozwiązanie zgodności z komunikacją do okienka nawigacji po lewej stronie, aby uzyskać szybszy dostęp po zalogowaniu się w przyszłości.

![Wykaz rozwiązań.](../media/m365-solution-catalog-home.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>Począwszy od Centrum administracyjne platformy Microsoft 365

Aby uzyskać dostęp do zgodności komunikacji po rozpoczęciu od Centrum administracyjne platformy Microsoft 365, administratorzy IT i specjaliści ds. zgodności firmy Contoso logują się do Centrum administracyjne platformy Microsoft 365 [(https://admin.microsoft.com)](https://admin.microsoft.com) i przejdź do strony [ portal zgodności Microsoft Purview](https://compliance.microsoft.com)

![Link do zgodności z komunikacją.](../media/communication-compliance-case-compliance-link.png)

Ta akcja powoduje otwarcie **centrum zabezpieczeń i zgodności Office 365** i musi wybrać link do **portal zgodności Microsoft Purview** podanym na banerze w górnej części strony.

![Office 365 centrum zabezpieczeń i zgodności.](../media/communication-compliance-case-scc.png)

W **portal zgodności Microsoft Purview** administratorzy IT firmy Contoso wybierają pozycję **Pokaż wszystko**, aby wyświetlić pełną listę rozwiązań zgodności.

![Menu zgodności komunikacji.](../media/communication-compliance-case-show-all.png)

Po wybraniu pozycji **Pokaż wszystko** administratorzy IT firmy Contoso mogą uzyskać dostęp do rozwiązania do zapewniania zgodności z komunikacją.

![Omówienie zgodności z komunikacją.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Krok 3. Konfigurowanie wymagań wstępnych i tworzenie zasad zgodności komunikacji

Aby rozpocząć pracę z zasadami zgodności komunikacji, istnieje kilka wymagań wstępnych, które administratorzy IT firmy Contoso muszą skonfigurować przed skonfigurowaniem nowych zasad w celu wykrycia nieodpowiedniego tekstu. Po spełnieniu tych wymagań wstępnych administratorzy IT i specjaliści ds. zgodności firmy Contoso mogą skonfigurować nowe zasady, a specjaliści ds. zgodności mogą rozpocząć badanie i korygowanie wszelkich wygenerowanych alertów.

### <a name="enabling-auditing-in-microsoft-365"></a>Włączanie inspekcji na platformie Microsoft 365

Zgodność z komunikacją wymaga dzienników inspekcji w celu wyświetlania alertów i śledzenia akcji korygowania podejmowanych przez recenzentów. Dzienniki inspekcji są podsumowaniem wszystkich działań skojarzonych ze zdefiniowanymi zasadami organizacyjnymi lub za każdym razem, gdy nastąpi zmiana zasad zgodności komunikacji.

Administratorzy IT firmy Contoso przejrzyj i wykonaj [instrukcje krok po kroku](turn-audit-log-search-on-or-off.md) , aby włączyć inspekcję. Po włączeniu inspekcji zostanie wyświetlony komunikat informujący, że dziennik inspekcji jest przygotowywany i że może uruchomić wyszukiwanie w ciągu kilku godzin po zakończeniu przygotowywania. Administratorzy IT firmy Contoso muszą wykonać tę akcję tylko raz.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Konfigurowanie dzierżawy usługi Yammer dla trybu natywnego

Zgodność z komunikacją wymaga, aby dzierżawa usługi Yammer dla organizacji była w trybie natywnym w celu wykrywania nieodpowiedniego tekstu w wiadomościach prywatnych i konwersacjach społeczności publicznej.

Administratorzy IT firmy Contoso upewnij się, że zapoznają się z informacjami w [artykule Omówienie trybu natywnego usługi Yammer w usłudze Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode) i wykonaj kroki uruchamiania narzędzia do migracji w artykule [Konfigurowanie sieci usługi Yammer dla trybu natywnego dla platformy Microsoft 365](/yammer/configure-your-yammer-network/native-mode) .

### <a name="setting-up-a-group-for-in-scope-users"></a>Konfigurowanie grupy dla użytkowników w zakresie

Specjaliści ds. zgodności firmy Contoso chcą dodać wszystkich użytkowników do zasad komunikacji, które wykryje nieodpowiedni tekst. Mogą zdecydować się na osobne dodanie każdego konta użytkownika do zasad, ale zdecydowali, że korzystanie z grupy dystrybucyjnej Wszyscy użytkownicy dla tych zasad jest znacznie łatwiejsze i pozwala zaoszczędzić czas na korzystanie z grupy dystrybucyjnej Wszyscy **użytkownicy** .

Muszą utworzyć nową grupę, aby uwzględnić wszystkich użytkowników firmy Contoso, aby wykonać następujące kroki:

1. Administratorzy IT firmy Contoso logują się do Centrum administracyjne platformy Microsoft 365 [(https://admin.microsoft.com)](https://admin.microsoft.com) i przejdź do Centrum administracyjne platformy Microsoft 365 > **grup** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
2. Wybierają **pozycję Dodaj grupę** i ukończ pracę kreatora, aby utworzyć nową *grupę platformy Microsoft 365* lub *grupę dystrybucyjną*.

    ![Grupy.](../media/communication-compliance-case-all-employees.png)

3. Po utworzeniu nowej grupy należy dodać wszystkich użytkowników firmy Contoso do nowej grupy. Otwierają **centrum administracyjne programu Exchange** [(https://outlook.office365.com/ecp)](https://outlook.office365.com/ecp) i przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**pozycji Grupy**</a> **adresatów** >  **centrum administracyjnego** >  programu Exchange. Administratorzy IT firmy Contoso wybierają obszar Członkostwo i nową grupę *Wszyscy pracownicy* , które utworzyli, i wybierz **kontrolkę Edytuj** , aby dodać wszystkich użytkowników firmy Contoso do nowej grupy w kreatorze.

    ![Centrum administracyjne programu Exchange.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-detect-inappropriate-text"></a>Tworzenie zasad w celu wykrywania nieodpowiedniego tekstu

Po spełnieniu wszystkich wymagań wstępnych administratorzy IT i specjaliści ds. zgodności firmy Contoso są gotowi skonfigurować zasady zgodności komunikacji w celu wykrywania nieodpowiedniego tekstu. Konfigurowanie tych zasad przy użyciu nowego szablonu zasad nieodpowiedniego tekstu jest proste i szybkie.

1. Administratorzy IT i specjaliści ds. zgodności firmy Contoso logują się do **portal zgodności Microsoft Purview** i wybierają pozycję **Zgodność z komunikacją** w okienku nawigacji po lewej stronie. Ta akcja powoduje otwarcie pulpitu nawigacyjnego **Przegląd** , który zawiera szybkie linki do szablonów zasad zgodności komunikacji. Wybierają szablon **Monitoruj pod kątem nieodpowiedniego tekstu** , wybierając pozycję **Rozpocznij** dla szablonu.

    ![Szablon tekstu niezgodności z komunikacją.](../media/communication-compliance-case-template.png)

2. W kreatorze szablonów zasad administratorzy IT i specjaliści ds. zgodności firmy Contoso współpracują ze sobą w celu ukończenia trzech wymaganych pól: **nazwa zasad**, **Użytkownicy lub grupy do nadzorowania** oraz **Recenzenci**.
3. Ponieważ kreator zasad już zaproponował nazwę zasad, administratorzy IT i specjaliści ds. zgodności decydują się zachować sugerowaną nazwę i skupić się na pozostałych polach. Wybierają grupę *Wszyscy użytkownicy* dla pola **Użytkownicy lub grupy do nadzorowania** i wybierają specjalistów ds. zgodności, którzy powinni badać i korygować alerty zasad dla pola **Recenzenci** . Ostatnim krokiem skonfigurowania zasad i rozpoczęcia zbierania informacji o alertach jest **wybranie pozycji Utwórz zasady**.

    ![Kreator nieodpowiedniego tekstu zgodności z komunikacją.](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Krok 4. Badanie i korygowanie alertów

Po skonfigurowaniu zasad zgodności komunikacji w celu wykrycia nieodpowiedniego tekstu następnym krokiem dla specjalistów ds. zgodności firmy Contoso będzie zbadanie i skorygowanie wszelkich alertów generowanych przez zasady. Pełne przetwarzanie komunikacji we wszystkich kanałach źródłowych komunikacji i wyświetlanie alertów na **pulpicie nawigacyjnym alertów** potrwa do godziny.

Po wygenerowaniu alertów specjaliści ds. zgodności firmy Contoso będą postępować zgodnie z [instrukcjami przepływu pracy](communication-compliance-investigate-remediate.md) , aby zbadać i rozwiązać problemy z nieodpowiednim tekstem.
