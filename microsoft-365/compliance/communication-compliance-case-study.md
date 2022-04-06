---
title: Analiza przypadku — firma Contoso szybko konfiguruje nieodpowiednie zasady dotyczące tekstu dla Microsoft Teams, Exchange i komunikacji Yammer tekstowej
description: Analiza przypadku firmy Contoso i sposób szybkiego konfigurowania zasad zgodności komunikacji w celu monitorowania nieodpowiednich tekstów w wiadomościach e-mail Microsoft Teams, Exchange Online i Yammer komunikacji.
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
ms.openlocfilehash: 7235bbdfb956369eebe960568921bc4bba86651a
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595131"
---
# <a name="case-study---contoso-quickly-configures-an-inappropriate-text-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Analiza przypadku — firma Contoso szybko konfiguruje nieodpowiednie zasady dotyczące tekstu dla Microsoft Teams, Exchange i komunikacji Yammer tekstowej

Zgodność komunikacji w programie Microsoft 365 pozwala zminimalizować ryzyko związane z komunikacją, pomagając wykrywać, przechwytywać i działać na wiadomościach z nieodpowiednim tekstem w organizacji. nieodpowiedni tekst może zawierać wulgarne, zagrożenia, molestowanie lub nieodpowiednie obrazy. Wstępnie zdefiniowane i niestandardowe zasady umożliwiają skanowanie komunikacji wewnętrznej i zewnętrznej w poszukiwaniu dopasowania zasad, aby umożliwić ich sprawdzenie przez wyznaczonych recenzentów. Recenzentzy mogą badać zeskanowane wiadomości e-mail, wiadomości e-Microsoft Teams, Yammer lub inne firmy w organizacji i podjąć odpowiednie działania naprawcze, aby upewnić się, że są one zgodne ze standardami wiadomości Twojej organizacji.

Contoso Corporation to fikcyjna organizacja, która musi szybko skonfigurować zasady do monitorowania nieodpowiedniego tekstu. Używali oni usługi Microsoft 365 przede wszystkim do obsługi poczty e-mail, Microsoft Teams i usługi Yammer, ale mają nowe wymagania dotyczące wymuszania stosowania zasad firmy dotyczących molestowania w miejscu pracy. Administratorzy IT firmy Contoso i specjaliści ds. zgodności mają podstawową wiedzę na temat podstaw pracy z usługą Microsoft 365 i szukają wszystkich wskazówek dotyczących szybkiego rozpoczynania pracy ze zgodnością z komunikacją.

W tej analizie przypadku zostaną obejmiene podstawowe informacje dotyczące szybkiego konfigurowania zasad zgodności komunikacji w celu monitorowania komunikacji w przypadku nieodpowiedniego tekstu. Wskazówki te obejmują:

- Krok 1. Planowanie zgodności komunikacji
- Krok 2. Uzyskiwanie dostępu do zgodności komunikacji w programie Microsoft 365
- Krok 3. Konfigurowanie wymagań wstępnych i tworzenie zasad zgodności komunikacji
- Krok 4. Badanie i rozwiązywanie problemów dotyczących alertów

## <a name="step-1-planning-for-communication-compliance"></a>Krok 1. Planowanie zgodności komunikacji

Administratorzy IT i specjaliści ds. zgodności firmy Contoso uczestniczyli w internetowych seminariach internetowych na temat rozwiązań zgodności w programie Microsoft 365 i zdecydowali, że zasady zgodności komunikacji pomogą im spełnić zaktualizowane wymagania dotyczące zasad firmy dotyczących ograniczania molestowania w miejscu pracy. Współpracując, opracowali plan tworzenia i włączania zasad zgodności komunikacji, które będą monitorować nieodpowiedni tekst w czatach wysyłanych w programie Microsoft Teams, wiadomościach prywatnych i konwersacjach społeczności w programie Yammer oraz w wiadomościach e-mail wysyłanych w programie Exchange Online. Ich plan obejmuje identyfikowanie:

- Administratorzy IT, którzy potrzebują dostępu do funkcji zgodności komunikacji.
- Specjaliści ds. zgodności, którzy muszą tworzyć zasady komunikacji i zarządzać nimi.
- Specjaliści ds. zgodności i inni współpracownicy z innych działów (dział kadr, dział prawny itp.), którzy muszą zbadać i rozwiązać alerty o zgodności komunikacji.
- Użytkownicy, którzy będą mieć dostęp do nieodpowiednich zasad tekstowych dotyczących zgodności komunikacji.

### <a name="licensing"></a>Licencjonowanie

Pierwszym krokiem jest potwierdzenie, że licencjonowanie oprogramowania Contoso w Microsoft 365 obsługuje rozwiązanie do zapewnienia zgodności komunikacji. Aby uzyskać dostęp do zgodności komunikacji i korzystać z niej, administratorzy IT firmy Contoso muszą sprawdzić, czy firma Contoso ma jedną z następujących funkcji:

- Microsoft 365 E5/A5/F5/G5 (wersja płatna lub próbna)
- Microsoft 365 E3/A3/F3/G5 + Microsoft 365 E5 zgodności ze standardem Microsoft 365 E5/A5/F5/G5
- Microsoft 365 E3/A3/F3/G5 + Microsoft 365 E5/A5/F5/G5 Zarządzanie ryzykiem w ramach niejawnego programu testów
- Office 365 Enterprise E5 (płatna lub próbna)
- Office 365 A5 (płatna lub próbna)
- Office 365 Enterprise E3 + Office 365 Advanced Compliance (nie jest już dostępna dla nowych subskrypcji, zobacz uwagę)

Użytkownikom uwzględnionym w zasadach zgodności komunikacji należy przypisać jedną z powyższych licencji. Aby uzyskać więcej informacji na temat subskrypcji i licencjonowania, [Microsoft 365 wskazówki dotyczące zabezpieczeń & zgodnością](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Office 365 Advanced Compliance jest już sprzedawana jako subskrypcja autonomiczna. Gdy wygasają bieżące subskrypcje, klienci powinni przejść do jednej z powyższych subskrypcji, która zawiera takie same lub dodatkowe funkcje zgodności.

Administratorzy IT firmy Contoso mogą wykonać następujące czynności, aby zweryfikować obsługę licencjonowania dla firmy Contoso:

1. Administratorzy IT logują się do Centrum administracyjne platformy Microsoft 365 <https://admin.microsoft.com> i przejdź do witryny Centrum administracyjne platformy Microsoft 365 > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">**BillingLicenses**</a> > .

2. Tutaj potwierdzili oni, że mają jedną z opcji [licencji,](communication-compliance-configure.md#subscriptions-and-licensing) która obejmuje obsługę zgodności komunikacji.

![Licencjonowanie zgodności komunikacji.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Uprawnienia dotyczące zgodności komunikacji

Do konfigurowania uprawnień do zarządzania funkcjami zgodności komunikacji jest używanych pięć grup ról. Aby **udostępnić zgodność komunikacji** jako opcję menu w programie Centrum zgodności platformy Microsoft 365 i kontynuować te kroki konfiguracji, administratorom firmy Contoso zostanie przypisana rola *Administrator zgodności komunikacji*.

Firma Contoso decyduje się na  przypisanie do grupy ról Zgodności komunikacji wszystkich administratorów zgodności komunikacji, analityków, osób, które chcesz do niej przypisać, oraz osób przeglądowych. Ułatwia to firmie Contoso szybkie rozpoczynanie pracy i najlepiej spełnia wymagania dotyczące zarządzania zgodnością.

|**Rola**|**Uprawnienia roli**|
|:-----|:-----|
| **Zgodność komunikacji** | Ta grupa ról pozwala zarządzać zgodnością komunikacji dla organizacji w jednej grupie. Dodając wszystkie konta użytkowników przeznaczone dla wyznaczonych administratorów, analityków, osób oglądających i wyeks odpowiednie osoby, możesz skonfigurować uprawnienia do zgodności komunikacji w jednej grupie. Ta grupa ról zawiera wszystkie role uprawnień zgodności komunikacji. Ta konfiguracja jest najprostszym sposobem szybkiego rozpoczęcia pracy z przepisami komunikacji i dobrze pasuje do organizacji, które nie potrzebują osobnych uprawnień zdefiniowanych dla osobnych grup użytkowników. |
| **Administrator zgodności komunikacji** | Ta grupa ról umożliwia wstępne skonfigurowanie zgodności komunikacji, a później podział administratorów zgodności komunikacji na zdefiniowaną grupę. Użytkownicy przypisani do tej grupy ról mogą tworzyć, odczytywać, aktualizować i usuwać zasady zgodności komunikacji, ustawienia globalne i przypisania grup ról. Użytkownicy przypisani do tej grupy ról nie mogą wyświetlać alertów o wiadomościach. |
| **Analityk zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak analitycy zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać zasady przypisane do nich jako recenzenty, wyświetlać metadane wiadomości (bez zawartości wiadomości), eskalować do dodatkowych recenzentów lub wysyłać do użytkowników powiadomienia. Analitycy nie mogą rozstrzygić oczekujących alertów. |
| **Działania w zakresie zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą działać jak uprawnienia do zgodności komunikacji. Użytkownicy przypisani do tej grupy ról mogą wyświetlać metadane i zawartość wiadomości, eskalacji do dodatkowych recenzentów, eskalować do sprawy Advanced eDiscovery, wysyłać powiadomienia do użytkowników i rozwiązywać alert. |
| **Przeglądarka zgodności komunikacji** | Ta grupa umożliwia przypisywanie uprawnień użytkownikom, którzy będą zarządzać raportami do komunikacji. Użytkownicy przypisani do tej grupy ról mają dostęp do wszystkich widżetów raportowania na stronie głównej zgodności komunikacji i mogą wyświetlać wszystkie raporty zgodności komunikacji. |

1. Administratorzy IT firmy Contoso logują się [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com/permissions) stronie uprawnień za pomocą poświadczeń dla konta administratora globalnego i wybierz link, aby wyświetlać role i zarządzać nimi w Microsoft 365.
2. W Centrum zgodności platformy Microsoft 365 przejdź <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**do strony Uprawnienia**</a> i wybierz link, aby wyświetlić role w aplikacji i zarządzać nimi Office 365.
3. Administratorzy zaznaczą *grupę ról Zgodność* komunikacji, a następnie pozycję **Edytuj grupę ról**.
4. Administratorzy **wybierzą pozycję Wybierz członków** w lewym okienku nawigacji, a następnie wybierz pozycję **Edytuj**.
5. **Wybierają pozycję Dodaj**, a następnie zaznaczają pole wyboru dla wszystkich użytkowników firmy Contoso, którzy będą zarządzać zgodnością komunikacji, badaniem i przeglądaniem alertów.
6. Administratorzy **wybierzą pozycję Dodaj**, a następnie pozycję **Gotowe**.
7. Wybieraj **pozycję Zapisz,** aby dodać użytkowników contoso do grupy ról. Wybiera pozycję **Zamknij,** aby ukończyć procedurę.

## <a name="step-2-accessing-communication-compliance-in-microsoft-365"></a>Krok 2. Uzyskiwanie dostępu do zgodności komunikacji w programie Microsoft 365

Po skonfigurowaniu uprawnień do zgodności komunikacji administratorzy IT firmy Contoso i specjaliści ds. zgodności przypisani do grupy ról Zgodność komunikacji mogą uzyskać dostęp do rozwiązania zgodności komunikacyjnej w Microsoft 365. Administratorzy IT firmy Contoso i specjaliści ds. zgodności mają kilka sposobów uzyskiwania dostępu do zgodności z komunikacją i mogą rozpocząć tworzenie nowych zasad:

- Rozpoczynanie bezpośrednio od rozwiązania do zapewnienia zgodności komunikacji
- Rozpoczynając od Centrum zgodności platformy Microsoft 365
- Rozpoczynanie od Microsoft 365 rozwiązania
- Rozpoczynając od Centrum administracyjne platformy Microsoft 365

### <a name="starting-directly-from-the-communication-compliance-solution"></a>Rozpoczynanie bezpośrednio od rozwiązania do zapewnienia zgodności komunikacji

Najszybszym sposobem uzyskania dostępu do rozwiązania jest zalogowanie się bezpośrednio do rozwiązania do zapewnienia zgodności **z przepisami** komunikacji (<https://compliance.microsoft.com/supervisoryreview>). Za pomocą tego linku administratorzy IT firmy Contoso i specjaliści ds. zgodności zostaną kierowani do pulpitu nawigacyjnego Przegląd zgodności komunikacji, gdzie można szybko sprawdzać stan alertów i tworzyć nowe zasady na podstawie wstępnie zdefiniowanych szablonów.

![Omówienie zgodności komunikacji.](../media/communication-compliance-case-overview.png)

### <a name="starting-from-the-microsoft-365-compliance-center"></a>Rozpoczynając od Centrum zgodności platformy Microsoft 365

Innym łatwym sposobem na uzyskanie dostępu do rozwiązania zgodności komunikacyjnej dla administratorów IT i specjalistów [ds. zgodności](https://compliance.microsoft.com) firmy Contoso jest zalogowanie się bezpośrednio do Centrum zgodności platformy Microsoft 365. Po zalogowaniu się użytkownicy muszą po prostu zaznaczyć  kontrolkę Pokaż wszystkie, aby wyświetlić wszystkie rozwiązania zgodności, a następnie  wybrać rozwiązanie do zgodności komunikacji, aby rozpocząć.

![Centrum zgodności.](../media/communication-compliance-case-center.png)

### <a name="starting-from-the-microsoft-365-solution-catalog"></a>Rozpoczynanie od Microsoft 365 rozwiązania

Administratorzy IT firmy Contoso i specjaliści ds. zgodności mogą również zdecydować się na uzyskanie dostępu do rozwiązania do zgodności komunikacji, wybierając Microsoft 365 wykaz rozwiązań. Wybierając pozycję **Wykaz w** **sekcji Rozwiązania** w lewym okienku nawigacji w witrynie sieci **Centrum zgodności platformy Microsoft 365**, mogą oni otworzyć wykaz rozwiązań z listą wszystkich Microsoft 365 zgodności. Przewiń w dół do sekcji **Zarządzanie ryzykiem niejawnego programu testów** , a następnie wybierz pozycję Zgodność komunikacji, aby rozpocząć. Administratorzy IT firmy Contoso także używają kontrolki pokaż w nawigacji, aby przypiąć rozwiązanie do zachowania zgodności komunikacji do okienka nawigacji po lewej stronie, aby mieć do niego szybszy dostęp, gdy zalogują się w przyszłości.

![Wykaz rozwiązań.](../media/communication-compliance-case-solution.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>Rozpoczynając od Centrum administracyjne platformy Microsoft 365

Aby uzyskać dostęp do zgodności komunikacji na początku Centrum administracyjne platformy Microsoft 365, administratorzy IT i specjaliści ds. zgodności firmy Contoso logują się do Centrum administracyjne platformy Microsoft 365 [(https://admin.microsoft.com)](https://admin.microsoft.com)i przejdź do [ Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com)

![Link zgodności komunikacji.](../media/communication-compliance-case-compliance-link.png)

Spowoduje to otwarcie **centrum zabezpieczeń Office 365** zgodności i wybranie linku do strony **Centrum zgodności platformy Microsoft 365** się na banerze u góry strony.

![Office 365 zabezpieczeń i zgodności.](../media/communication-compliance-case-scc.png)

Gdy zaznaczysz listę **Centrum zgodności platformy Microsoft 365**, administratorzy IT firmy Contoso wybierzą pozycję **Pokaż wszystko**, aby wyświetlić pełną listę rozwiązań zgodności.

![Menu zgodności komunikacji.](../media/communication-compliance-case-show-all.png)

Po wybraniu **opcji Pokaż wszystko** administratorzy IT firmy Contoso mogą uzyskać dostęp do rozwiązania do zgodności komunikacji.

![Omówienie zgodności komunikacji.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Krok 3. Konfigurowanie wymagań wstępnych i tworzenie zasad zgodności komunikacji

Aby rozpocząć pracę z zasadami zgodności komunikacji, administratorzy IT firmy Contoso muszą skonfigurować kilka wymagań wstępnych przed skonfigurowaniem nowych zasad w celu monitorowania nieodpowiedniego tekstu. Gdy te wymagania wstępne zostaną spełnione, administratorzy IT i specjaliści ds. zgodności firmy Contoso mogą skonfigurować nowe specjaliści ds. zasad i zgodności mogą rozpocząć badania i korygować wszelkie wygenerowane alerty.

### <a name="enabling-auditing-in-microsoft-365"></a>Włączanie inspekcji w programie Microsoft 365

Zgodność komunikacji wymaga dzienników inspekcji w celu pokazania alertów i śledzenia działań naprawczych realizowanych przez recenzentów. Dzienniki inspekcji to podsumowanie wszystkich działań skojarzonych ze zdefiniowanymi zasadami organizacji lub zawsze, gdy istnieją zmiany w zasadach zgodności komunikacji.

Administratorzy IT firmy Contoso przejrzyj i wykonaj instrukcje krok po kroku [, aby](turn-audit-log-search-on-or-off.md) włączyć inspekcję. Po włączeniu inspekcji jest wyświetlany komunikat informujący, że dziennik inspekcji jest przygotowywany i że mogą oni uruchomić wyszukiwanie w ciągu kilku godzin po zakończeniu przygotowywania. Administratorzy IT firmy Contoso muszą wykonać tę czynność tylko raz.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Konfigurowanie Yammer w trybie natywnym

Zgodność komunikacji wymaga, aby dzierżawa Yammer organizacji w trybie natywnym w celu monitorowania nieodpowiedniego tekstu w wiadomościach prywatnych i konwersacjach społeczności publicznej.

Administratorzy IT firmy Contoso upewnij się, że przeglądają informacje zawarte w artykule Omówienie trybu natywnego programu Yammer w programie [Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode) i postępuj zgodnie z instrukcjami uruchamiania narzędzia do migracji z artykułu Konfigurowanie sieci Yammer pod Microsoft 365 [natywnym](/yammer/configure-your-yammer-network/native-mode).

### <a name="setting-up-a-group-for-in-scope-users"></a>Konfigurowanie grupy dla użytkowników w zakresie

Specjaliści ds. zgodności Firmy Contoso chcą dodać wszystkich użytkowników do zasad komunikacji, które będą monitorować w przypadku nieodpowiedniego tekstu. Mogą oddzielnie dodawać poszczególne konta użytkowników do zasad, ale zdecydowali, że jest to znacznie łatwiejsze i oszczędzają czas na używaniu grupy  dystrybucyjnej Wszyscy użytkownicy dla użytkowników dla tych zasad.

Muszą utworzyć nową grupę, aby uwzględnić wszystkich użytkowników firmy Contoso, więc mogą wykonać następujące czynności:

1. Administratorzy IT firmy Contoso logują się do Centrum administracyjne platformy Microsoft 365 [(https://admin.microsoft.com)](https://admin.microsoft.com) i przejdź do Centrum administracyjne platformy Microsoft 365 > **Grupy** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
2. Wybieraj **pozycję Dodaj grupę** i wykonaj zadania kreatora, aby utworzyć nową *Microsoft 365 lub* *grupę dystrybucyjną*.

    ![Grupy.](../media/communication-compliance-case-all-employees.png)

3. Po utworzeniu nowej grupy należy dodać do niej wszystkich użytkowników firmy Contoso. Otwierają **centrum Exchange** [administracyjnego (https://outlook.office365.com/ecp)](https://outlook.office365.com/ecp) i przeszli do Exchange **admin** **centerrecipientsGroups** >  > .<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a> Administratorzy IT firmy Contoso zaznaczą obszar Członkostwo i nową grupę *Wszyscy* pracownicy, a następnie  wybierz kontrolkę Edytuj, aby dodać wszystkich użytkowników firmy Contoso do nowej grupy w kreatorze.

    ![Exchange administracyjnego.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-monitor-for-inappropriate-text"></a>Tworzenie zasad do monitorowania w przypadku nieodpowiedniego tekstu

Po zakończeniu wszystkich wymagań wstępnych administratorzy IT i specjaliści ds. zgodności firmy Contoso mogą skonfigurować zasady zgodności komunikacji w celu monitorowania nieodpowiedniego tekstu. Skonfigurowanie tych zasad za pomocą nowego nieodpowiedniego szablonu zasad tekstowych jest proste i szybkie.

1. Administratorzy IT i specjaliści ds. zgodności firmy Contoso logują się do **Centrum zgodności platformy Microsoft 365 i w** okienku nawigacji po lewej **stronie wybierz pozycję** Zgodność komunikacji. Ta akcja spowoduje otwarcie **pulpitu nawigacyjnego Przegląd** , który zawiera szybkie linki do szablonów zasad zgodności komunikacji. Wybierają szablon **Monitor dla nieodpowiedniego** tekstu, wybierając **Wprowadzenie** szablonu.

    ![Szablon tekstowy zgodny ze zgodnością komunikacji.](../media/communication-compliance-case-template.png)

2. W kreatorze szablonów zasad administratorzy IT firmy Contoso i specjaliści ds. zgodności współpracują ze sobą, aby wypełnić trzy wymagane **pola: Nazwa** **zasad, Użytkownicy** lub grupy nadzorowane i **Recenzentzy**.
3. Ponieważ kreator zasad już zasugerował nazwę zasad, administratorzy IT i specjaliści ds. zgodności decydują się, aby zachować sugerowaną nazwę i skupić się na pozostałych polach. Wybiera grupę *Wszyscy* użytkownicy w obszarze Użytkownicy lub  grupy do nadzorowania, a następnie wybiera ekspertów ds. zgodności, którzy powinni zbadać i rozwiązać działania alertów dotyczących zasad dla pola **Recenzenty**. Ostatnim krokiem do skonfigurowania zasad i rozpoczęcia zbierania informacji alertów jest wybranie **opcji Utwórz zasady**.

    ![Kreator tekstów nieodpowiednich dla komunikacji.](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Krok 4. Badanie i rozwiązywanie problemów z alertami

Po skonfigurowaniu zasad zgodności komunikacji w celu monitorowania nieodpowiedniego tekstu następnym krokiem dla specjalistów ds. zgodności Contoso będzie badanie i rozwiązywanie wszelkich alertów wygenerowanych przez te zasady. Pełne przetwarzanie komunikacji ze wszystkich kanałów źródłowych komunikacji oraz alerty na pulpicie **nawigacyjnym alertów** zajmie do 24 godzin.

Po wygenerowaniu alertów specjaliści ds. zgodności firmy Contoso [](communication-compliance-investigate-remediate.md) będą postępować zgodnie z instrukcjami przepływu pracy w celu zbadania i rozwiązania nieodpowiednich problemów z tekstem.