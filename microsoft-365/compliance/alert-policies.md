---
title: Microsoft 365 alertów
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkDEFENDER
description: Utwórz zasady alertów w portalu Centrum zgodności platformy Microsoft 365 sieci Microsoft 365 Defender w celu monitorowania potencjalnych zagrożeń, utraty danych i problemów z uprawnieniami.
ms.openlocfilehash: 9137c74cd2c32539a339a9cabc2d9f66f6923636
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "62974139"
---
# <a name="alert-policies-in-microsoft-365"></a>Zasady alertów w programie Microsoft 365

Za pomocą zasad alertów i pulpitu nawigacyjnego alertów w portalu Centrum zgodności platformy Microsoft 365 lub Microsoft 365 Defender można tworzyć zasady alertów, Microsoft 365 Defender następnie wyświetlać alerty generowane przez wykonywanie przez użytkowników działań, które są zgodne z warunkami zasad alertów. Istnieje kilka domyślnych zasad alertów, które ułatwiają monitorowanie działań, takich jak przypisywanie uprawnień administratora w programie Exchange Online, ataki złośliwego oprogramowania, kampanie wyłudzujące informacje oraz nietypowe poziomy usuwania plików i udostępniania zewnętrznego.

> [!TIP]
> Przejdź do sekcji [Domyślne zasady alertów](#default-alert-policies) w tym artykule, aby uzyskać listę i opis dostępnych zasad alertów.

Zasady alertów umożliwiają kategoryzowanie alertów wyzwalanych przez zasady, stosowanie zasad do wszystkich użytkowników w organizacji, ustawianie poziomu progowego dla wyzwalania alertu oraz decydowanie, czy alerty mają być odbierane w przypadku alertów. Istnieje również strona Alerty, na której można wyświetlać i filtrować alerty, ustawiać stan alertów, aby ułatwić zarządzanie alertami **, a następnie** odrzucać alerty po zajściu w stanach źródłowych zdarzenia.

> [!NOTE]
> Zasady alertów są dostępne dla organizacji z subskrypcją usług Microsoft 365 Enterprise, Office 365 Enterprise lub Office 365 Government E1/F1/G1, E3/F3/G3 lub E5/G5. Funkcja zaawansowana jest dostępna tylko dla organizacji z subskrypcją E5/G5 lub dla organizacji, które mają subskrypcję E1/F1/G1 lub E3/F3/G3 oraz program Microsoft Defender dla usługi Office 365 P2 lub Zgodność platformy Microsoft 365 E5 albo subskrypcję dodatków E5 eDiscovery i Audit. W tym temacie wyróżniona jest funkcja wymagająca subskrypcji E5/G5 lub dodatku. Należy również pamiętać, że zasady alertów są dostępne w środowiskach Office 365 GCC, GCC i DoD w USA.

## <a name="how-alert-policies-work"></a>Jak działają zasady alertów

Oto krótki przegląd zasad alertów i alertów wyzwalanych w przypadku, gdy działania użytkowników lub administratorów są spełnione warunki zasad alertu.

![Omówienie działania zasad alertów.](../media/M365ComplianceDefender-AlertPolicies-Overview.png)

1. Administrator w Twojej organizacji tworzy, konfiguruje i włącza zasady alertów za pomocą strony Zasady alertów  w Centrum zgodności platformy Microsoft 365 lub w portalu Microsoft 365 Defender alertów. Zasady alertów można również tworzyć przy użyciu polecenia cmdlet [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) w programie PowerShell w & Centrum zgodności.

   Aby utworzyć zasady alertów, musisz mieć przypisaną rolę Zarządzanie alertami lub Konfigurację organizacji w programie Centrum zgodności platformy Microsoft 365 lub portalu usługi Defender.

   > [!NOTE]
   > Zanim zasady będą wyzwalane przez alerty, może upłynie do 24 godzin od utworzenia lub zaktualizowania zasad alertów. Jest tak, ponieważ zasady muszą zostać zsynchronizowane z aparatem wykrywania alertów.

2. Użytkownik wykonuje działanie, które jest do warunków określonych w zasadach alertów. W przypadku ataków na złośliwe oprogramowanie zainfekowane wiadomości e-mail wysyłane do użytkowników w organizacji powodują wyzwolenie alertu.

3. Microsoft 365 generuje alert, który jest wyświetlany na stronie **Alerty** w programie Centrum zgodności platformy Microsoft 365 lub Portalu Defender. Ponadto jeśli zasady alertów są włączone dla powiadomień e-mail, firma Microsoft wysyła powiadomienie do listy adresatów. Alerty, które administrator lub inni użytkownicy mogą zobaczyć na stronie Alerty, są określane przez role przypisane do tego użytkownika. Aby uzyskać więcej informacji, zobacz [Uprawnienia RBAC wymagane do wyświetlania alertów](#rbac-permissions-required-to-view-alerts).

4. Administrator zarządza alertami w centrum zgodności. Zarządzanie alertami polega na przypisywaniu stanu alertu w celu śledzenia wszelkich badań i zarządzania nimi.

## <a name="alert-policy-settings"></a>Ustawienia zasad alertów

Zasady alertów składają się z zestawu reguł i warunków definiującego działanie użytkownika lub administratora generującego alert, listę użytkowników, którzy uruchamiają alert w przypadku wykonania działania, oraz próg, który określa, ile razy działanie musi wystąpić przed wyzwoleniem alertu. Kategoryzujesz również zasady i przypisujesz je do poziomu ważności. Te dwa ustawienia ułatwiają zarządzanie zasadami alertów (i alertami wyzwalanymi po dopasowaniu warunków zasad), ponieważ można filtrować według tych ustawień podczas zarządzania zasadami i wyświetlania alertów w Centrum zgodności. Możesz na przykład wyświetlić alerty, które są zgodne z warunkami z tej samej kategorii, lub wyświetlać alerty o tym samym poziomie ważności.

Aby wyświetlić i utworzyć zasady alertów:

### <a name="microsoft-365-compliance-center"></a>Centrum zgodności platformy Microsoft 365

Przejdź <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">do Centrum zgodności platformy Microsoft 365,</a> a następnie wybierz **pozycję** **ZasadyAlertAlert** >  >  **zasady**.

![W Centrum zgodności wybierz pozycję Zasady, a następnie w obszarze Alert wybierz pozycję Zasady alertów, aby wyświetlić i utworzyć zasady alertów.](../media/LaunchAlertPoliciesMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portalu

Przejdź do portalu <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> w obszarze Współpraca z innymi & e-mail **wybierz pozycję** **Zasady & Wsyłanie** >  **zasad**. Możesz również przejść bezpośrednio do .<https://security.microsoft.com/alertpolicies>

![W portalu usługi Defender wybierz pozycję Zasady & w obszarze Współpraca między kontami &-mail, a następnie wybierz pozycję Zasady alertów, aby wyświetlać i tworzyć zasady alertów.](../media/LaunchAlertPoliciesDefenderPortal.png)

> [!NOTE]
> Aby wyświetlać zasady alertów w Centrum zgodności lub portalu usługi DefenderView-Only musisz mieć przypisaną rolę zarządzanie alertami. Aby tworzyć i edytować zasady alertów, musisz mieć przypisaną rolę Zarządzanie alertami. Aby uzyskać więcej informacji, [zobacz Uprawnienia w Centrum zabezpieczeń i zgodności](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Zasady alertów obejmują następujące ustawienia i warunki.

- **Działanie, które śledzi alert**. Zasady tworzy się w celu śledzenia działania lub, w niektórych przypadkach, kilku powiązanych działań, takich jak udostępnianie pliku użytkownikowi zewnętrzneowi przez udostępnienie go, przypisywanie uprawnień dostępu lub tworzenie linku anonimowego. Gdy użytkownik wykonuje działanie określone przez zasady, jest wyzwalany alert na podstawie ustawień progu alertu.

    > [!NOTE]
    > Działania, które można śledzić, zależą od planu administracji Office 365 Enterprise amerykańskiego lub Office 365 Rząd Stanów Zjednoczonych. Na ogół działania związane z kampaniami złośliwego oprogramowania i atakami wyłudzania informacji wymagają subskrypcji E5/G5 lub subskrypcji E1/F1/G1 lub E3/F3/G3 z subskrypcją dodatkową usługi [Defender dla usługi Office 365](../security/office-365-security/defender-for-office-365.md) Plan 2.

- **Warunki aktywności**. W przypadku większości działań można zdefiniować dodatkowe warunki, które muszą być spełnione, aby wyzwolić alert. Typowe warunki to adresy IP (w związku z którym alert jest wyzwalany, gdy użytkownik wykonuje działanie na komputerze z określonym adresem IP lub w zakresie adresów IP), czy zostanie wyzwolony alert, jeśli określone działanie zostanie wykonane przez określonego użytkownika lub użytkownika, oraz czy to działanie jest wykonywane na określonej nazwie pliku lub adresie URL. Możesz również skonfigurować warunek wyzwalania alertu, gdy działanie jest wykonywane przez dowolnego użytkownika w organizacji. Dostępne warunki zależą od wybranego działania.

Tagi użytkowników można również zdefiniować jako warunek zasad alertu. W wyniku tego alerty wyzwalane przez zasady obejmują kontekst użytkownika, na który wpływa ta zasada. Można używać systemowych tagów użytkownika lub niestandardowych tagów użytkowników. Aby uzyskać więcej informacji, zobacz [Tagi użytkownika w programie Microsoft Defender dla Office 365](/microsoft-365/security/office-365-security/user-tags).

- **Po wyzwoleniu alertu**. Możesz skonfigurować ustawienie definiujące, jak często może wystąpić działanie przed wyzwoleniem alertu. Pozwala to skonfigurować zasady tak, aby generować alerty za każdym razem, gdy działanie jest takie, które są spełnione, kiedy zostanie przekroczony określony próg lub gdy wystąpienie działania, które jest śledzone, staje się nietypowe dla Twojej organizacji.

    ![Konfigurowanie sposobu wyzwalania alertów na podstawie czasu wystąpienia działania, progu lub nietypowej aktywności w organizacji.](../media/howalertsaretriggered.png)

    Jeśli wybierzesz to ustawienie na podstawie nietypowej aktywności, firma Microsoft ustali wartość planu bazowego definiującą normalną częstotliwość dla wybranego działania. Utworzenie tego planu bazowego trwa do siedmiu dni, podczas których alerty nie będą generowane. Po ustanowioniu planu bazowego jest wyzwalany alert, gdy częstotliwość działania śledzona przez zasady alertu znacznie przekracza wartość planu bazowego. W przypadku działań związanych z inspekcją (takich jak działania dotyczące plików i folderów) można ustalić plan bazowy na podstawie jednego użytkownika lub na podstawie wszystkich użytkowników w organizacji. w przypadku działań związanych ze złośliwym oprogramowaniem możesz ustalić plan bazowy na podstawie pojedynczej rodziny złośliwego oprogramowania, jednego adresata lub wszystkich wiadomości w organizacji.

    > [!NOTE]
    > Możliwość konfigurowania zasad alertów na podstawie progu lub nietypowej aktywności wymaga subskrypcji E5/G5, subskrypcji E1/F1/G1 lub E3/F3/G3 z programem Microsoft Defender dla usługi Office 365 P2, Zgodność platformy Microsoft 365 E5 lub Microsoft 365 zbierania elektronicznych materiałów dowodowych i subskrypcji dodatków do inspekcji. Organizacje z subskrypcją E1/F1/G1 i E3/F3/G3 mogą tworzyć zasady alertów tylko wtedy, gdy alert jest wyzwalany za każdym razem, gdy występuje działanie.

- **Kategoria alertów**. Aby ułatwić śledzenie alertów generowanych przez zasady i zarządzanie nimi, możesz przypisać do zasad jedną z następujących kategorii.

  - Ochrona przed utratą danych

  - Zarządzanie informacjami

  - Przepływ poczty e-mail

  - Uprawnienia

  - Zarządzanie zagrożeniami

  - Inne osoby

  W przypadku wystąpienia działania, które jest takie, które są spełnione przez zasady alertu, wygenerowany alert jest otagowany kategorią zdefiniowaną w tym ustawieniu. Umożliwia to śledzenie alertów o tej samej kategorii i zarządzanie nimi na stronie Alerty  w Centrum zgodności, ponieważ można sortować i filtrować alerty według kategorii.

- **Ważność alertu**. Podobnie jak w przypadku kategorii alertów, do alertów jest przypisywany atrybut **ważności (Niski****,** **Średni**, Wysoki lub Informacyjny). Podobnie jak w przypadku kategorii alertów, gdy działanie jest takie, które jest identyczne z warunkami zasad alertu, wygenerowany alert jest otagowany na takim samym poziomie ważności, jak ustawiony dla zasad alertów. Ponownie to umożliwia śledzenie alertów o takich samych ważnościach i zarządzanie nimi na stronie **Alerty** . Na przykład możesz filtrować listę alertów, aby były wyświetlane tylko alerty o  wysokim poziomie ważności.

    > [!TIP]
    > Podczas konfigurowania zasad alertów rozważ przypisanie większej wagi do działań, które mogą skutkować bardzo negatywnymi konsekwencjami, takimi jak wykrywanie złośliwego oprogramowania po dostarczeniu do użytkowników, wyświetlanie poufnych lub sklasyfikowanych danych, udostępnianie danych użytkownikom zewnętrznym lub inne działania, które mogą powodować utratę danych lub zagrożenia bezpieczeństwa. Może to ułatwić ustalanie priorytetów alertów oraz działań, które należy podjąć w celu zbadania i rozwiązania podstawowych przyczyn.

- **Zautomatyzowane badania**. Niektóre alerty wyzwolią automatyczne badania w celu zidentyfikowania potencjalnych zagrożeń i zagrożeń, które wymagają środków zaradczych lub zaradczych.  W większości przypadków alerty są wyzwalane przez wykrywanie złośliwych wiadomości e-mail lub działań, ale w niektórych przypadkach alerty są wyzwalane przez akcje administratora w portalu zabezpieczeń.  Aby uzyskać więcej informacji na temat zautomatyzowanych badań, zobacz Automatyczne badanie i [odpowiedź (AIR) w programie Microsoft Defender for Office 365](../security/office-365-security/office-365-air.md).

- **Powiadomienia e-mail**. Te zasady możesz tak skonfigurować, aby po wyzwoleniu alertu powiadomienia e-mail były wysyłane (lub nie były wysyłane) do listy użytkowników. Możesz także ustawić dzienny limit powiadomień, aby po osiągnięciu maksymalnej liczby powiadomień w tym dniu nie były już wysyłane żadne powiadomienia o alertach. Oprócz powiadomień e-mail Ty i inni administratorzy możecie wyświetlać alerty wyzwalane przez zasady na **stronie Alerty** . Rozważ włączenie powiadomień e-mail dla zasad alertów dotyczących określonej kategorii lub o wyższym poziomie ważności.

## <a name="default-alert-policies"></a>Domyślne zasady alertów

Firma Microsoft udostępnia wbudowane zasady alertów, które ułatwiają identyfikowanie nadużyć Exchange uprawnień administratora, działań złośliwego oprogramowania, potencjalnych zagrożeń zewnętrznych i wewnętrznych oraz zagrożeń związanych z zarządzaniem informacjami. Na stronie **Zasady alertów** nazwy tych wbudowanych zasad są pogrubione, a typ zasad jest zdefiniowany jako **System**. Te zasady są domyślnie włączone. Możesz wyłączyć te zasady (lub ponownie), skonfigurować listę adresatów, do których będą wysyłane powiadomienia e-mail, i ustawić dzienny limit powiadomień. Innych ustawień tych zasad nie można edytować.

W poniższej tabeli wymieniono i opisano dostępne domyślne zasady alertów oraz kategorię, do których przypisano poszczególne zasady. Kategoria służy do określania, które alerty użytkownik może wyświetlać na stronie Alerty. Aby uzyskać więcej informacji, zobacz [Uprawnienia RBAC wymagane do wyświetlania alertów](#rbac-permissions-required-to-view-alerts).

W tabeli po wskazywano również wszystkie Office 365 Enterprise i Office 365 amerykańskiego planu rządowego wymaganego dla każdego z nich. Niektóre domyślne zasady alertów są dostępne, jeśli twoja organizacja ma odpowiednią subskrypcję dodatkową oprócz subskrypcji E1/F1/G1 lub E3/F3/G3.
 
| Domyślne zasady alertów | Opis | Kategoria | Zautomatyzowane badanie | Enterprise subskrypcji |
|:-----|:-----|:-----|:-----|:-----|
|**Wykryto potencjalnie złośliwe kliknięcie adresu URL**|Generuje alert, gdy użytkownik chroniony za pomocą linków [Sejf organizacji](../security/office-365-security/safe-links.md) klika złośliwy link. To zdarzenie jest wyzwalane, gdy zmiany w adresie URL są identyfikowane przez usługę Microsoft Defender dla usługi Office 365 lub gdy użytkownicy zastępują strony linków programu Sejf (na podstawie zasad usługi Microsoft 365 dla firm Sejf Links organizacji). Te zasady alertów mają **ustawienie Wysoka** ważność. W przypadku klientów korzystających Office 365 P2, E5 i G5 ten alert automatycznie uruchamia automatyczne badanie i reagowanie w [Office 365.](../security/office-365-security/office-365-air.md) Aby uzyskać więcej informacji na temat zdarzeń, które powodują wyzwolenie tego alertu, zobacz [Konfigurowanie Sejf linków](../security/office-365-security/set-up-safe-links-policies.md).|Zarządzanie zagrożeniami|Tak|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Ukończono wynik przesyłania przez administratora**|Generuje alert [po zakończeniu](../security/office-365-security/admin-submission.md) procesu przesyłania przez administratora ponownego obiektu przesłanego. Alert zostanie wyzwolony za każdym razem, gdy na stronie Przesyłanie administratora zostanie ponownie renderowany wynik. Alerty te mają przypominać o przeglądaniu wyników poprzednich przesłań [,](https://compliance.microsoft.com/reportsubmission) przesyłaniu komunikatów zgłoszonych przez użytkowników w celu sprawdzenia najnowszych zasad i ponownego sprawdzania, a także ułatwiają ustalenie, czy zasady filtrowania w organizacji mają zamierzone skutki. Te zasady mają **ustawienie Ważności** informacji.|Zarządzanie zagrożeniami|Nie|E1/F1, E3/F3 lub E5|
|**Administrator wyzwolił ręczne badanie poczty e-mail**|Generuje alert, gdy administrator wyzwala ręczne badanie wiadomości e-mail z Eksploratora zagrożeń. Aby uzyskać więcej informacji, [zobacz Przykład: Administrator zabezpieczeń wyzwala badanie z Eksploratora zagrożeń](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer). Ten alert powiadamia organizację o tym, że badanie zostało rozpoczęte. Alert zawiera informacje o tym, kto go wyzwolił, i zawiera link do badania. Te zasady mają **ustawienie Ważności** informacji.|Zarządzanie zagrożeniami|Tak|Subskrypcja dodatku E5/G5 lub Microsoft Defender Office 365 P2|
|**Administrator wyzwolił badanie naruszenia bezpieczeństwa użytkowników**|Generuje alert, gdy administrator wyzwoli ręczne wykrywanie naruszenia bezpieczeństwa nadawcy lub adresata wiadomości e-mail za pomocą Eksploratora zagrożeń. Aby uzyskać więcej informacji, zobacz [Przykład: Administrator](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) zabezpieczeń wyzwala badanie z Eksploratora zagrożeń, w którym pokazano pokrewne ręczne wyzwalanie badania wiadomości e-mail. Ten alert powiadamia organizację o tym, że w organizacji rozpoczęto badanie bezpieczeństwa użytkowników. Alert zawiera informacje o tym, kto go wyzwolił, i zawiera link do badania. Te zasady mają **ustawienie średniego** ważności.|Zarządzanie zagrożeniami|Tak|Subskrypcja dodatku E5/G5 lub Microsoft Defender Office 365 P2|
|**Tworzenie reguły przesyłania dalej/przekierowywania**|Generuje alert, gdy ktoś z Twojej organizacji utworzy regułę skrzynki odbiorczej dla swojej skrzynki pocztowej, która będzie przesyłać dalej lub przekierowywać wiadomości na inne konto e-mail. Te zasady śledzi tylko reguły skrzynki odbiorczej utworzone przy użyciu programu Outlook w sieci Web (dawniej znanego jako Outlook Web App) lub Exchange Online PowerShell. Te zasady mają **ustawienie Ważności** informacji. Aby uzyskać więcej informacji na temat używania reguł skrzynki odbiorczej do przesyłania dalej i przekierowywania wiadomości e-mail w aplikacji Outlook w sieci Web, zobacz Automatyczne przesyłanie dalej wiadomości na inne konto za pomocą reguł Outlook w sieci Web w [programie Outlook w sieci Web](https://support.office.com/article/1433e3a0-7fb0-4999-b536-50e05cb67fed).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Rozpoczęte lub wyeksportowane wyszukiwanie zbierania elektronicznych materiałów dowodowych**|Generuje alert, gdy ktoś korzysta z narzędzia przeszukiwania zawartości w Centrum zabezpieczeń i zgodności. W przypadku wykonania następujących działań wyszukiwania zawartości jest wyzwalany alert: <br><br> <li> Rozpoczęto wyszukiwanie zawartości <li> Wyniki wyszukiwania zawartości są eksportowane <li> Eksportowany jest raport przeszukiwania zawartości <br><br> Alerty są również wyzwalane, gdy poprzednie działania wyszukiwania zawartości są wykonywane w ramach skojarzenia ze sprawą zbierania elektronicznych materiałów dowodowych. Te zasady mają **ustawienie Ważności** informacji. Aby uzyskać więcej informacji na temat działań przeszukiwania zawartości, zobacz [Wyszukiwanie działań zbierania elektronicznych materiałów dowodowych w dzienniku inspekcji](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-activities).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Podwyższenie Exchange administratora**|Generuje alert, gdy komuś przypisano uprawnienia administracyjne w Twojej organizacji Exchange Online organizacji. Na przykład po dodaniu użytkownika do grupy ról Zarządzanie organizacją w programie Exchange Online. Te zasady mają **ustawienie Niski** poziom ważności.|Uprawnienia|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Wiadomości e-mail zawierające złośliwy plik usunięte po dostarczeniu**|Generuje alert, gdy wszystkie wiadomości zawierające złośliwy plik zostaną dostarczone do skrzynek pocztowych w organizacji. W przypadku wystąpienia tego zdarzenia firma Microsoft usunie zainfekowane wiadomości z Exchange Online pocztowych za pomocą automatycznego przeczyszczania [bez godziny](../security/office-365-security/zero-hour-auto-purge.md). Te zasady mają ustawienie **ważności informacji** i automatycznie wyzwalają automatyczne badanie [i odpowiedź w Office 365](../security/office-365-security/office-365-air.md). Aby uzyskać więcej informacji na temat tych nowych zasad, zobacz [Nowe zasady alertów w programie Microsoft Defender dla systemu Office 365](new-defender-alert-policies.md).|Zarządzanie zagrożeniami|Tak|Subskrypcja dodatku E5/G5 lub Microsoft Defender Office 365 P2|
|**Wiadomości e-mail zawierające złośliwy adres URL usunięte po dostarczeniu**|Generuje alert, gdy wszystkie wiadomości zawierające złośliwy adres URL są dostarczane do skrzynek pocztowych w organizacji. W przypadku wystąpienia tego zdarzenia firma Microsoft usunie zainfekowane wiadomości z Exchange Online pocztowych za pomocą automatycznego przeczyszczania [bez godziny](../security/office-365-security/zero-hour-auto-purge.md). Te zasady mają ustawienie **ważności informacji** i automatycznie wyzwalają automatyczne badanie [i odpowiedź w Office 365](../security/office-365-security/office-365-air.md). Aby uzyskać więcej informacji na temat tych nowych zasad, zobacz [Nowe zasady alertów w programie Microsoft Defender dla systemu Office 365](new-defender-alert-policies.md).|Zarządzanie zagrożeniami|Tak|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Wiadomości e-mail z kampanii usunięte po dostarczeniu**|Generuje alert, gdy wszystkie wiadomości skojarzone [z kampanią](../security/office-365-security/campaigns.md) są dostarczane do skrzynek pocztowych w organizacji. W przypadku wystąpienia tego zdarzenia firma Microsoft usunie zainfekowane wiadomości z Exchange Online pocztowych za pomocą automatycznego przeczyszczania [bez godziny](../security/office-365-security/zero-hour-auto-purge.md). Te zasady mają ustawienie **ważności informacji** i automatycznie wyzwalają automatyczne badanie [i odpowiedź w Office 365](../security/office-365-security/office-365-air.md). Aby uzyskać więcej informacji na temat tych nowych zasad, zobacz [Nowe zasady alertów w programie Microsoft Defender dla systemu Office 365](new-defender-alert-policies.md).|Zarządzanie zagrożeniami|Tak|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Wiadomości e-mail usunięte po dostarczeniu**|Generuje alert, gdy wszystkie złośliwe wiadomości, które nie zawierają złośliwej jednostki (URL lub pliku) lub skojarzone z kampanią, zostaną dostarczone do skrzynek pocztowych w organizacji. W przypadku wystąpienia tego zdarzenia firma Microsoft usunie zainfekowane wiadomości z Exchange Online pocztowych za pomocą automatycznego przeczyszczania [bez godziny](../security/office-365-security/zero-hour-auto-purge.md). Te zasady mają ustawienie **ważności informacji** i automatycznie wyzwalają automatyczne badanie [i odpowiedź w Office 365](../security/office-365-security/office-365-air.md). Aby uzyskać więcej informacji na temat tych nowych zasad, zobacz [Nowe zasady alertów w programie Microsoft Defender dla systemu Office 365](new-defender-alert-policies.md).|Zarządzanie zagrożeniami|Tak|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Wiadomości e-mail zgłoszone przez użytkownika jako złośliwe oprogramowanie lub wyłudzy**|Generuje alert, gdy użytkownicy w organizacji zgłaszają wiadomości jako wiadomości wyłudzdzce informacje za pomocą dodatku Zgłoś wiadomość. Te zasady mają **ustawienie Niski** poziom ważności. Aby uzyskać więcej informacji na temat tego dodatku, zobacz [Korzystanie z dodatku Wiadomość raportu](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). W przypadku klientów korzystających Office 365 P2, E5 i G5 ten alert automatycznie uruchamia automatyczne badanie i reagowanie w [Office 365](../security/office-365-security/office-365-air.md).|Zarządzanie zagrożeniami|Tak|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Przekroczono limit wysyłania wiadomości e-mail**|Generuje alert, gdy ktoś w Twojej organizacji wysłał więcej poczty, niż jest dozwolone przez zasady spamu wychodzącego. Zazwyczaj oznacza to, że użytkownik wysyła zbyt dużo wiadomości e-mail lub że konto może zostać naruszone. Te zasady mają **ustawienie średniego** ważności. Jeśli na podstawie tych zasad alertu zostanie wygenerowany alert, warto sprawdzić, czy konto użytkownika [nie zostało naruszone](../security/office-365-security/responding-to-a-compromised-email-account.md).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Formularz zablokowany ze względu na potencjalną próbę wyłudzenia informacji**|Generuje alert, gdy ktoś w Organizacji ma ograniczenie do udostępniania formularzy i zbierania odpowiedzi przy użyciu programu Microsoft Forms ze względu na wykrycie powtarzających się prób wyłudzania informacji. Te zasady mają **ustawienie Wysoka ważność** .|Zarządzanie zagrożeniami|Nie|E1, E3/F3 lub E5|
|**Formularz oflagowany i potwierdzony jako wyłudzanie informacji**|Generuje alert, gdy formularz utworzony w programie Microsoft Forms z poziomu organizacji zostanie zidentyfikowany jako potencjalna wyłudzanie informacji za pośrednictwem zgłoszenia (Zgłoś nadużycie) i potwierdzony jako wyłudzanie informacji przez firmę Microsoft. Te zasady mają **ustawienie Wysoka** ważność.|Zarządzanie zagrożeniami|Nie|E1, E3/F3 lub E5|
|**Wiadomości zostały opóźnione**|Generuje alert, gdy firma Microsoft nie może dostarczać wiadomości e-mail do organizacji lokalnej lub serwera partnerskiego za pomocą łącznika. W takim przypadku wiadomość jest do kolejki w Office 365. Ten alert jest wyzwalany, gdy jest co najmniej 2000 wiadomości, które były w kolejce dłużej niż godzina. Te zasady mają **ustawienie Wysoka** ważność.|Przepływ poczty e-mail|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Kampania z złośliwym oprogramowaniem wykryta po dostarczeniu**|Generuje alert, gdy do skrzynek pocztowych w organizacji zostanie dostarczona niezwykle duża liczba wiadomości zawierających złośliwe oprogramowanie. W przypadku wystąpienia tego zdarzenia firma Microsoft usunie zainfekowane wiadomości Exchange Online skrzynkach pocztowych. Te zasady mają **ustawienie Wysoka** ważność.|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 lub Microsoft Defender Office 365 P2|
|**Wykryto i zablokowano kampanię złośliwego oprogramowania**|Generuje alert, gdy ktoś próbował wysłać do użytkowników w organizacji niezwykle dużą liczbę wiadomości e-mail zawierających określonego typu złośliwe oprogramowanie. W przypadku wystąpienia tego zdarzenia zainfekowane wiadomości są blokowane przez firmę Microsoft i nie są dostarczane do skrzynek pocztowych. Te zasady mają **ustawienie Niski** poziom ważności.|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Wykrywana kampania złośliwego oprogramowania SharePoint i OneDrive**|Generuje alert w przypadku wykrycia wyjątkowo dużej liczby złośliwego oprogramowania lub wirusów w plikach znajdujących się w witrynach sieci SharePoint lub kontach użytkowników OneDrive organizacji. Te zasady mają **ustawienie Wysoka** ważność.|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Złośliwe oprogramowanie nie zostało zamapowane, ponieważ zap jest wyłączone**| Generuje alert, gdy firma Microsoft wykryje wiadomość z złośliwym oprogramowaniem do skrzynki pocztowej, ponieważ Zero-Hour automatyczne przeczyszczanie wiadomości wyłudżania informacji jest wyłączone. Te zasady mają **ustawienie Ważności** informacji. |Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Wiadomości wyłudzane z powodu wyłączenia folderu wiadomości-śmieci użytkownika**|Generuje alert, gdy firma Microsoft wykryje, że folder wiadomości-śmieci użytkownika jest wyłączony, umożliwiając dostarczenie do skrzynki pocztowej wiadomości umożliwiającej wyłudzanie informacji o wysokiej pewności. Te zasady mają **ustawienie Ważności** informacji.|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Wiadomości phish dostarczane z powodu zastępowania WTR**|Generuje alert, gdy firma Microsoft wykryje regułę transportu Exchange (ETR), która zezwoliła na dostarczenie wiadomości o wysokiej pewności, służącej do wyłudzania informacji do skrzynki pocztowej. Te zasady mają **ustawienie Ważności** informacji. Aby uzyskać więcej informacji Exchange reguł transportu (reguły przepływu poczty), zobacz Reguły przepływu poczty [(reguły transportu) w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Wiadomości wyłudzywowe dostarczane z powodu zasad zezwalania na adresy IP**|Generuje alert, gdy firma Microsoft wykryje zasady zezwalania na adres IP, które zezwalają na dostarczenie wiadomości umożliwiającej wyłudzanie informacji o wysokiej pewności do skrzynki pocztowej. Te zasady mają **ustawienie Ważności** informacji. Aby uzyskać więcej informacji o zasadach zezwalania na połączenia IP (filtrowanie połączeń), zobacz Konfigurowanie domyślnych zasad [filtrowania połączeń — Office 365](../security/office-365-security/configure-the-connection-filter-policy.md).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Phish not zamapowany because ZAP is disabled**| Generuje alert, gdy firma Microsoft wykryje wiadomość wyłudzającą informacje o wysokiej pewności do skrzynki pocztowej, ponieważ Zero-Hour automatyczne przeczyszczanie wiadomości wyłudzających informacje jest wyłączone. Te zasady mają **ustawienie Ważności** informacji.|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Wiadomości wyłud inne dostarczane z powodu zastąpienia dzierżawy lub użytkownika1**<sup></sup>|Generuje alert, gdy firma Microsoft wykryje, że administrator lub użytkownik może zastąpić wiadomość wyłudzającą informacje do skrzynki pocztowej. Przykładami zastępować są reguły skrzynki odbiorczej lub przepływu poczty, które zezwalają na wiadomości od określonego nadawcy lub domeny, lub zasady ochrony przed spamem, które zezwalają na wiadomości od określonych nadawców lub domen. Te zasady mają **ustawienie Wysoka** ważność.|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Podejrzane działania w zakresie przesyłania dalej poczty e-mail**|Generuje alert, gdy ktoś z Twojej organizacji automatycznie wygeneruje wiadomość e-mail na podejrzane konto zewnętrzne. Jest to wczesne ostrzeżenie dotyczące zachowania, które może wskazywać, że konto zostało naruszone, ale nie jest wystarczająco poważne, aby ograniczyć użytkownika. Te zasady mają **ustawienie Wysoka** ważność. Chociaż zdarza się to rzadko, alert wygenerowany przez te zasady może być anomaly. Warto sprawdzić, czy konto użytkownika nie [zostało naruszone](../security/office-365-security/responding-to-a-compromised-email-account.md).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Wykryto podejrzane wzorce wysyłania wiadomości e-mail**|Generuje alert, gdy ktoś z Twojej organizacji wysłał podejrzaną wiadomość e-mail i istnieje ryzyko ograniczenia możliwości wysyłania wiadomości e-mail. Jest to wczesne ostrzeżenie dotyczące zachowania, które może wskazywać, że konto zostało naruszone, ale nie jest wystarczająco poważne, aby ograniczyć użytkownika. Te zasady mają **ustawienie średniego** ważności. Chociaż zdarza się to rzadko, alert wygenerowany przez te zasady może być anomaly. Warto jednak sprawdzić, czy konto użytkownika [nie zostało naruszone](../security/office-365-security/responding-to-a-compromised-email-account.md).|Zarządzanie zagrożeniami|Tak|E1/F1/G1, E3/F3/G3 lub E5/G5  |
|**Wpis listy zablokowanych/zezwalania na dzierżawę nie ma już wygasnąć**|Generuje alert, gdy wpis Listy zezwalania/blokowania dzierżawy ma nie zostać usunięty. To zdarzenie jest wyzwalane trzy dni przed datą wygaśnięcia, która jest oparta na utworzeniu lub ostatniej aktualizacji wpisu. Te zasady alertów mają **ustawienie Ważności** informacji. Ma to na celu poinformowanie administratorów o nadchodzących zmianach w filtrach, ponieważ może to oznaczać zablokowanie lub zezwalanie. W przypadku bloków można przedłużyć datę wygaśnięcia, aby zachować blokadę w miejscu. W przypadku gdy zezwalasz, musisz ponownie przesłać element, aby nasi analitycy mogą ponownie przyjrzeć się temu elementowi. Jeśli jednak zezwalanie zostało już zweryfikowane jako fałszywie dodatnie, wpis wygaśnie tylko w przypadku zaktualizowania filtrów systemowych, aby zezwolić na to w sposób naturalny. Aby uzyskać więcej informacji na temat zdarzeń, które powodują wyzwolenie tego alertu, zobacz Zarządzanie listą [zezwalania/blokowania dzierżawy](../security/office-365-security/tenant-allow-block-list.md).|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Dzierżawa z ograniczonymi możliwościami wysyłania wiadomości e-mail**|Generuje alert, gdy większość ruchu poczty e-mail z Twojej organizacji została wykryta jako podejrzana, a firma Microsoft ograniczyła twoją organizację do wysyłania wiadomości e-mail. Zbadaj wszelkie potencjalnie naruszone konta użytkowników i administratorów, nowe łączniki lub przekazywanie otwarte, a następnie skontaktuj się z pomocą techniczną firmy Microsoft w celu odblokowania organizacji. Te zasady mają **ustawienie Wysoka** ważność. Aby uzyskać więcej informacji o tym, dlaczego organizacje są blokowane, zobacz Rozwiązywanie problemów dotyczących dostarczania wiadomości e-mail związanych z kodem błędu [5.7.7xx w programie Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Dzierżawa z ograniczonymi możliwościami wysyłania nieudostępnianych wiadomości e-mail**|Generuje alert, gdy z niezarejestrowanych domen jest wysyłanych zbyt wiele wiadomości e-mail (nazywanych również domenami *niezarejestrowane* ). Office 365 odpowiednią ilość wiadomości e-mail z niezarejestrowanych domen, ale należy skonfigurować każdą domenę używaną do wysyłania wiadomości e-mail jako zaakceptowanych domen. Ten alert wskazuje, że wszyscy użytkownicy w organizacji nie mogą już wysyłać wiadomości e-mail. Te zasady mają **ustawienie Wysoka** ważność. Aby uzyskać więcej informacji o tym, dlaczego organizacje są blokowane, zobacz Rozwiązywanie problemów dotyczących dostarczania wiadomości e-mail związanych z kodem błędu [5.7.7xx w programie Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Nietypowe działania na plikach użytkowników zewnętrznych**|Generuje alert, gdy na plikach w organizacji wykonywanych jest niezwykle duża liczba działań SharePoint lub OneDrive przez użytkowników spoza organizacji. Obejmuje to działania, takie jak uzyskiwanie dostępu do plików, pobieranie plików i usuwanie plików. Te zasady mają **ustawienie Wysoka** ważność.|Zarządzanie informacjami|Nie|E5/G5, Microsoft Defender dla Office 365 P2 lub Microsoft 365 E5 subskrypcji dodatków|
|**Nietypowy rozmiar udostępniania plików zewnętrznych**|Generuje alert, gdy niezwykle duża liczba plików w SharePoint lub OneDrive jest udostępniana użytkownikom spoza organizacji. Te zasady mają **ustawienie średniego** ważności.|Zarządzanie informacjami|Nie|E5/G5, Defender dla Office 365 P2 lub Microsoft 365 E5 subskrypcji dodatku|
|**Nietypowy rozmiar usunięcia pliku**|Generuje alert, gdy w krótkim czasie zostanie usunięta niezwykle duża SharePoint lub OneDrive plików. Te zasady mają **ustawienie średniego** ważności.|Zarządzanie informacjami|Nie|E5/G5, Defender dla Office 365 P2 lub Microsoft 365 E5 subskrypcji dodatku|
|**Nietypowy wzrost liczby wiadomości e-mail zgłoszonych jako wyłudzy**|Generuje alert w przypadku znacznego wzrostu liczby osób w organizacji przy użyciu dodatku Raport wiadomości w programie Outlook do zgłaszania wiadomości jako wiadomości wyłudzających informacje. Te zasady mają **ustawienie średniego** ważności. Aby uzyskać więcej informacji na temat tego dodatku, zobacz [Korzystanie z dodatku Wiadomość raportu](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Phish personifikacji użytkownika dostarczona do skrzynki odbiorczej/**<sup>folderu1,2</sup><sup></sup>|Generuje alert, gdy firma Microsoft wykryje, że administrator lub użytkownik może zastąpić wiadomość wyłudzającą informacje o personifikacji użytkownika do skrzynki odbiorczej (lub innego folderu z ułatwieniami dostępu) skrzynki pocztowej. Przykładami zastępować są reguły skrzynki odbiorczej lub przepływu poczty, które zezwalają na wiadomości od określonego nadawcy lub domeny, lub zasady ochrony przed spamem, które zezwalają na wiadomości od określonych nadawców lub domen. Te zasady mają **ustawienie średniego** ważności.|Zarządzanie zagrożeniami|Nie|Subskrypcja dodatku E5/G5 Office 365 Defender dla komputerów Office 365 P2|
|**Użytkownik zażądał zwolnienia wiadomości poddanej kwarantannie**|Generuje alert, gdy użytkownik zażąda zwolnienia dla wiadomości poddanej kwarantannie. Aby zażądać wydania wiadomości poddanych kwarantannie, w zasadach kwarantanny jest wymagane uprawnienie Zezwalaj adresatom na żądanie publikacji wiadomości w kwarantannie **(**_PermissionToRequestRelease_) (na przykład z grupy wstępnie ustawionych uprawnień dostępu Ograniczony dostęp). Aby uzyskać więcej informacji, zobacz [Umożliwianie adresatom żądania wypuszczenia wiadomości z uprawnienia kwarantanny](../security/office-365-security/quarantine-policies.md#allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission). Te zasady mają **ustawienie Ważności** informacji.|Zarządzanie zagrożeniami|Nie|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Użytkownik z ograniczonymi możliwościami wysyłania wiadomości e-mail**|Generuje alert, gdy ktoś w Twojej organizacji ma ograniczenie dostępu do wysyłania poczty wychodzącej. Zazwyczaj powoduje to naruszone konto, a użytkownik znajduje się na stronie Użytkownicy z ograniczeniami w  Centrum zgodności platformy Microsoft 365. (Aby uzyskać dostęp do tej strony, przejdź do tematu **Zarządzanie zagrożeniami > przejrzyj > użytkowników z ograniczeniami**). Te zasady mają **ustawienie Wysoka** ważność. Aby uzyskać więcej informacji o użytkownikach z ograniczeniami, zobacz Usuwanie użytkownika, domeny lub adresu IP z listy zablokowanych po [wysłaniu wiadomości e-mail ze spamem](/office365/securitycompliance/removing-user-from-restricted-users-portal-after-spam).|Zarządzanie zagrożeniami|Tak|E1/F1/G1, E3/F3/G3 lub E5/G5|
|**Użytkownik ograniczony do udostępniania formularzy i zbierania odpowiedzi**|Generuje alert, gdy ktoś w Organizacji ma ograniczenie do udostępniania formularzy i zbierania odpowiedzi przy użyciu programu Microsoft Forms ze względu na wykrycie powtarzających się prób wyłudzania informacji. Te zasady mają **ustawienie Wysoka** ważność.|Zarządzanie zagrożeniami|Nie|E1, E3/F3 lub E5|

> [!NOTE]
> <sup>1</sup> Tymczasowo usunęliśmy te domyślne zasady alertów na podstawie opinii klientów. Pracujemy nad jego ulepszeniami i w niedalekiej przyszłości zastąpimy go nową wersją. Do tego czasu możesz utworzyć niestandardowe zasady alertów, które zastąpią tę funkcję, używając następujących ustawień: <ul><li>Aktywność jest wykrywana w wiadomościach e-mail wyłudzywowych w czasie dostarczania</li> <li>Mail nie jest zap'a</li> <li>Kierunek poczty: Przychodzący</li> <li>Stan dostarczenia poczty to Dostarczono</li> <li>Technologia wykrywania to przechowywanie złośliwych adresów URL, detonacja adresu URL, zaawansowany filtr wyłudzy, filtr informacji ogólnych, personifikacja domeny, personifikacja użytkownika i personifikacja marki</li></ul> Aby uzyskać więcej informacji na temat ochrony przed wyłudzaniem informacji w programie Office 365, zobacz Konfigurowanie zasad ochrony przed wyłudzaniem informacji i [wyłudzaniem informacji](../security/office-365-security/set-up-anti-phishing-policies.md).<br/><br/><sup>2 Aby ponownie</sup> utworzyć te zasady alertów, postępuj zgodnie z wskazówkami z poprzedniego przypisu dolnego, ale jako jedyną technologię wykrywanie wybierz personifikację użytkownika.

Nietypowe działania monitorowane przez niektóre wbudowane zasady są oparte na tym samym procesie co opisane wcześniej ustawienie progu alertu. Firma Microsoft określa wartość planu bazowego definiującą normalną częstotliwość dla działania "zwykle". Alerty są wyzwalane, gdy częstotliwość działań śledzona za pomocą wbudowanych zasad alertów znacznie przekracza wartość podstawową.

<a name="viewing-alerts"></a>

## <a name="view-alerts"></a>Wyświetlanie alertów

Gdy działanie wykonane przez użytkowników w organizacji jest zgodne z ustawieniami zasad alertu, jest generowany alert i wyświetlany na stronie Alerty w  Centrum zgodności lub w portalu usługi Defender. W zależności od ustawień zasad alertu po wyzwoleniu alertu do listy określonych użytkowników jest również wysyłane powiadomienie e-mail. W przypadku każdego alertu na pulpicie  nawigacyjnym na stronie Alerty jest wyświetlana nazwa odpowiednich zasad alertu, ważność i kategoria alertu (zdefiniowane w zasadach alertu) oraz liczba zdarzeń, w wyniku których wystąpiło działanie w wyniku wygenerowania alertu. Ta wartość jest określana na podstawie ustawienia progowego zasad alertu. Na pulpicie nawigacyjnym jest również pokazany stan poszczególnych alertów. Aby uzyskać więcej informacji na temat używania właściwości statusu do zarządzania alertami, zobacz [Zarządzanie alertami](#manage-alerts).

Aby wyświetlić alerty:

### <a name="microsoft-365-compliance-center"></a>Centrum zgodności platformy Microsoft 365

 Przejdź do, a <https://compliance.microsoft.com> następnie wybierz pozycję **Alerty**. Możesz również przejść bezpośrednio do .<https://compliance.microsoft.com/compliancealerts>

![W Centrum zgodności platformy Microsoft 365 wybierz pozycję Alerty.](../media/ViewAlertsMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portalu

Przejdź do <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalu,</a> a następnie wybierz pozycję **Alerty & alerty** > . Możesz również przejść bezpośrednio do .<https://security.microsoft.com/alerts>

![W portalu Microsoft 365 Defender wybierz pozycję Alerty o & zdarzeniach, a następnie wybierz pozycję Alerty.](../media/ViewAlertsDefenderPortal.png)

Za pomocą poniższych filtrów można wyświetlić podzestaw wszystkich alertów na **stronie Alerty** .

- **Stan.** Ten filtr umożliwia wyświetlanie alertów, które mają przypisany określony stan. Domyślny stan to **Aktywny**. Ty i inni administratorzy możecie zmieniać wartość stanu.

- **Zasady.** Ten filtr umożliwia wyświetlanie alertów, które są zgodne z ustawieniem co najmniej jednej zasady alertów. Możesz też wyświetlić wszystkie alerty dla wszystkich zasad alertów.

- **Zakres czasu.** Ten filtr umożliwia wyświetlanie alertów wygenerowanych w określonym zakresie dat i godzin.

- **Ważność.** Użyj tego filtru, aby wyświetlić alerty, które mają określoną ważność.

- **Kategoria.** Ten filtr umożliwia wyświetlanie alertów z co najmniej jednej kategorii alertów.

- **Tagi.** Ten filtr umożliwia wyświetlanie alertów z jednego lub większej liczby tagów użytkowników. Tagi są odzwierciedlane na podstawie oznakowanych skrzynek pocztowych lub użytkowników wyświetlanych w alertach. Aby [dowiedzieć się więcej, zobacz Tagi użytkowników Office 356 ATP](../security/office-365-security/user-tags.md).

- **Źródło.** Użyj tego filtru, aby wyświetlać alerty wyzwolone przez zasady alertów w Centrum zgodności lub alerty wyzwalane przez Office 365 Cloud App Security lub obie te zasady. Aby uzyskać więcej informacji na Office 365 Cloud App Security alertów, zobacz [Wyświetlanie alertów programu Defender dla aplikacji w chmurze](#viewing-cloud-app-security-alerts).

> [!IMPORTANT]
> Filtrowanie i sortowanie według tagów użytkowników jest obecnie dostępne w publicznej wersji Preview.
> Może on zostać znacznie zmodyfikowany przed jego premierą komercyjną. Firma Microsoft nie udziela żadnych gwarancji, jawnych ani domniemanych, w odniesieniu do podanych informacji na jej temat.

## <a name="alert-aggregation"></a>Agregacja alertów

Gdy w krótkim czasie występuje wiele zdarzeń, które są zgodne z warunkami zasad alertu, są one dodawane do istniejącego alertu przez proces nazywany *agregacją alertów*. Gdy zdarzenie wyzwala alert, alert jest generowany i wyświetlany na stronie **Alerty** oraz jest wysyłane powiadomienie. Jeśli to samo zdarzenie występuje w interwale agregacji, program Microsoft 365 szczegółowe informacje o nowym zdarzeniu do istniejącego alertu, zamiast wyzwalać nowy alert. Celem agregacji alertów jest ograniczenie "zmęczenia" alertów oraz skoncentrowanie się na mniejszej liczbie alertów dla tego samego zdarzenia.

Długość interwału agregacji zależy od Office 365 lub Microsoft 365 subskrypcji.

|Subskrypcja|Interwał agregacji|
|:---------|:---------:|
|Office 365 lub Microsoft 365 E5/G5|1 minuta|
|Defender for Office 365 Plan 2 |1 minuta|
|Dodatek zgodności usługi E5 lub dodatek Odnajdowanie i inspekcja w ramach usługi E5|1 minuta|
|Office 365 lub Microsoft 365 E1/F1/G1 lub E3/F3/G3|15 minut|
|Defender for Office 365 Plan 1 or Exchange Online Protection|15 minut|

Jeśli w interwale agregacji występują zdarzenia zgodne z tym samymi zasadami alertu, do pierwotnego alertu są dodawane szczegóły dotyczące kolejnego zdarzenia. W przypadku wszystkich zdarzeń w polu szczegółów są wyświetlane informacje o zagregowanych zdarzeniach, a w polu licznika trafień jest wyświetlana liczba zdarzeń z interwałem agregacji. Aby wyświetlić więcej informacji na temat wszystkich zagregowanych wystąpień zdarzeń, wyświetl listę aktywności.

Poniższy zrzut ekranu przedstawia alert z czterema zagregowanym zdarzeniami. Lista działań zawiera informacje o czterech wiadomościach e-mail, które są związane z alertem.

![Przykład agregacji alertów.](../media/AggregatedAlertExample.png)

Agregację alertów należy pamiętać o następujących kwestiach:

- Alerty wywoływane przez **potencjalnie złośliwe kliknięcie adresu URL** zostały wykryte domyślnie [zasady alertów](#default-alert-policies) nie są agregowane. Jest tak, ponieważ alerty wyzwalane przez te zasady są unikatowe dla każdego użytkownika i każdej wiadomości e-mail.

- Obecnie **właściwość alertu** Liczba trafień nie wskazuje liczby zagregowanych zdarzeń we wszystkich zasadach alertów. W przypadku alertów wyzwalanych przez te zasady alertów możesz wyświetlić zagregowane zdarzenia, klikając pozycję Wyświetl listę **wiadomości lub** **Wyświetl aktywność w** alercie. Pracujemy nad udostępnieniem liczby zagregowanych zdarzeń wymienionych we **właściwości alertów** Liczba trafień dla wszystkich zasad alertów.

## <a name="rbac-permissions-required-to-view-alerts"></a>Uprawnienia RBAC wymagane do wyświetlania alertów

Uprawnienia kontroli dostępu opartej na rolach (RBAC, Role Based Access Control) przypisane użytkownikom w organizacji określają alerty, które użytkownik może zobaczyć na **stronie Alerty** . Jak to się udało? Role zarządzania przypisane użytkownikom (na podstawie ich członkostwa w grupach ról w sieci Centrum zgodności platformy Microsoft 365 lub portalu Microsoft 365 Defender) określają kategorie alertów, które użytkownik może zobaczyć na stronie **Alerty**. Oto kilka przykładów:

- Członkowie grupy ról Zarządzanie rekordami mogą wyświetlać tylko alerty generowane przez zasady alertów, do których przypisano **kategorię Zarządzanie informacjami** .

- Członkowie grupy ról Administrator zgodności nie mogą wyświetlać alertów generowanych przez zasady alertów, do których przypisano **kategorię Zarządzanie zagrożeniami** .

- Członkowie grupy ról Menedżer zbierania elektronicznych materiałów dowodowych nie mogą wyświetlać żadnych alertów, ponieważ żadna z przypisanych ról nie umożliwia wyświetlania alertów z dowolnej kategorii alertów.

Ten projekt (oparty na uprawnieniach RBAC) pozwala określić, które alerty mogą być przeglądane (i zarządzane) przez użytkowników w określonych rolach stanowiska w organizacji.

W poniższej tabeli wymieniono role wymagane do wyświetlania alertów z 6 różnych kategorii alertów. Pierwsza kolumna w tabelach zawiera listę wszystkich ról w Centrum zgodności platformy Microsoft 365 lub portalu Microsoft 365 Defender tabel.  Znacznik wyboru oznacza, że użytkownik z przypisaną rolą może wyświetlać alerty z odpowiedniej kategorii alertów wymienionej w górnym wierszu.

Aby sprawdzić, do której kategorii są przypisane domyślne zasady alertów, zobacz tabelę w [tece Domyślne zasady alertów](#default-alert-policies).

|Rola|Zarządzanie informacjami|Ochrona przed utratą danych|Przepływ poczty e-mail|Uprawnienia|Zarządzanie zagrożeniami|Inne osoby|
|:---------|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|Dzienniki inspekcji|||||||
|Zarządzanie sprawą|||||||
|Administrator zgodności|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)||![Znacznik wyboru.](../media/checkmark.png)||![Znacznik wyboru.](../media/checkmark.png)|
|Wyszukiwanie zgodności|||||||
|Zarządzanie urządzeniami|||||||
|Zarządzanie rozsyłaniem|||||||
|Zarządzanie zgodnością DLP||![Znacznik wyboru.](../media/checkmark.png)|||||
|Eksportowanie|||||||
|Wstrzymaj|||||||
|Analityk ochrony informacji||![Znacznik wyboru.](../media/checkmark.png)|||||
|Ochrona informacji||![Znacznik wyboru.](../media/checkmark.png)|||||
|Zarządzanie alertami||||||![Znacznik wyboru.](../media/checkmark.png)|
|Konfiguracja organizacji||||||![Znacznik wyboru.](../media/checkmark.png)|
|Wersja zapoznawcza|||||||
|Zarządzanie rekordami|![Znacznik wyboru.](../media/checkmark.png)||||||
|Zarządzanie przechowywaniem|![Znacznik wyboru.](../media/checkmark.png)||||||
|Recenzja|||||||
|Odszyfrowywanie usługi RMS|||||||
|Zarządzanie rolami||||![Znacznik wyboru.](../media/checkmark.png)|||
|Wyszukiwanie i przeczyszczanie|||||||
|Administrator zabezpieczeń||![Znacznik wyboru.](../media/checkmark.png)||![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|
|Czytnik zabezpieczeń||![Znacznik wyboru.](../media/checkmark.png)||![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)
|Widok zapewniania ochrony usługi|||||||
|Administrator przeglądu nadzorczych|||||||
|View-Only dzienniki inspekcji|||||||
|View-Only zarządzanie urządzeniami|||||||
|View-Only zarządzania zgodnością DLP||![Znacznik wyboru.](../media/checkmark.png)|||||
|View-Only zarządzanie alertami||||||![Znacznik wyboru](../media/checkmark.png)|
|View-Only adresaci|||![Znacznik wyboru](../media/checkmark.png)||||
|View-Only zarządzanie rekordami|![Znacznik wyboru](../media/checkmark.png)||||||
|View-Only zarządzanie przechowywaniem|![Znacznik wyboru](../media/checkmark.png)||||||

> [!TIP]
> Aby wyświetlić role przypisane do poszczególnych domyślnych grup ról, uruchom następujące polecenia w programie PowerShell w centrum zabezpieczeń & zgodności:
>
> ```powershell
> $RoleGroups = Get-RoleGroup
> ```
>
> ```powershell
> $RoleGroups | foreach {Write-Output -InputObject `r`n,$_.Name,"-----------------------"; Get-RoleGroup $_.Identity | Select-Object -ExpandProperty Roles}
> ```
>
> Role przypisane do grupy ról można również wyświetlać w witrynie Centrum zgodności platformy Microsoft 365 lub w portalu Microsoft 365 Defender grupy. Przejdź na stronę **Uprawnienia** i wybierz grupę ról. Przypisane role zostaną wyświetlone na wysuwanych stronie.

<a name="manage-alerts"></a>

## <a name="manage-alerts"></a>Zarządzanie alertami

Po wygenerowaniu i wyświetlaniu alertów na stronie **Alerty** w Centrum zgodności możesz je sprawdzać, badać i rozwiązywać. Te same [uprawnienia RBAC, które](#rbac-permissions-required-to-view-alerts) zapewniają użytkownikom dostęp do alertów, również zapewniają im możliwość zarządzania alertami.

Oto kilka zadań, które możesz wykonać, aby zarządzać alertami.

- **Przypisywanie stanu do alertów.** Do alertów można przypisać jeden z następujących **stanów: Aktywny** (wartość domyślna **), Badanie**, **Rozwiązano** lub **Odrzucone**. Następnie możesz filtrować według tego ustawienia, aby wyświetlać alerty z tym samym ustawieniem statusu. To ustawienie stanu może ułatwić śledzenie procesu zarządzania alertami.

- **Wyświetl szczegóły alertu.** Możesz wybrać alert, aby wyświetlić stronę wysuwu ze szczegółami alertu. Szczegółowe informacje zależą od odpowiednich zasad alertów, ale zwykle zawierają następujące informacje:

  - Nazwa rzeczywistej operacji, która wyzwoliła alert, na przykład polecenia cmdlet lub operacji dziennika inspekcji.

  - Opis działania, które wyzwoliło alert.

  - Użytkownik (lub lista użytkowników), który wyzwolił alert. Ta wartość jest uwzględniana tylko w przypadku zasad alertów, które są ustawione w celu śledzenia jednego użytkownika lub jednego działania.

  - Liczba działań śledzona przez alert. Ta liczba może być dopasowana do rzeczywistej liczby powiązanych alertów wymienionych na stronie Alerty, ponieważ być może zostało wyzwolonych więcej alertów.

  - Link do listy działań, która zawiera element dla każdego działania, które wyzwoliło alert. Każda pozycja na tej liście określa, kiedy miało miejsce działanie, nazwa rzeczywistej operacji (na przykład "FileDeleted"), użytkownik, który wykonał działanie, obiekt (taki jak plik, sprawa zbierania elektronicznych materiałów dowodowych lub skrzynka pocztowa), na którym wykonano dane działanie, oraz adres IP komputera użytkownika. W przypadku alertów dotyczących złośliwego oprogramowania link ten zawiera listę wiadomości.

  - Nazwa (i link) odpowiednich zasad alertu.

- **Pomiń powiadomienia e-mail.** Dla alertu można wyłączyć (lub wyłączyć) powiadomienia e-mail ze strony wysuwu. Gdy pominiesz powiadomienia e-mail, firma Microsoft nie będzie wysyłać powiadomień, gdy wystąpią działania lub zdarzenia zgodne z warunkami zasad alertów. Alerty będą jednak wyzwalane, gdy działania wykonywane przez użytkowników będą zgodne z warunkami zasad alertu. Możesz również wyłączyć powiadomienia e-mail, edytując zasady alertów.

- **Rozwiązywanie alertów.** Alert można oznaczyć jako rozwiązany na stronie wysuwanego alertu (co oznacza stan alertu **jako Rozwiązany**). Jeśli nie zmienisz filtru, rozpoznane alerty nie są wyświetlane na **stronie Alerty** .

<a name="viewing-cloud-app-security-alerts"></a>

## <a name="view-defender-for-cloud-apps-alerts"></a>Wyświetlanie alertów programu Defender dla aplikacji w chmurze

Alerty wyzwalane przez Office 365 Cloud App Security są teraz wyświetlane na stronie **Alerty** w Centrum zgodności. Dotyczy to również alertów wyzwalanych przez zasady aktywności i alerty wyzwalane przez zasady wykrywania anomaly w Office 365 Cloud App Security. Oznacza to, że możesz wyświetlać wszystkie alerty w Centrum zgodności. Office 365 Cloud App Security jest dostępna tylko dla organizacji z subskrypcją usługi Office 365 Enterprise E5 lub Office 365 government G5 w USA. Aby uzyskać więcej informacji, zobacz [Omówienie programu Defender dla aplikacji w chmurze](/cloud-app-security/what-is-cloud-app-security).

Organizacje, które mają program Microsoft Defender dla aplikacji w chmurze w ramach subskrypcji Enterprise Mobility + Security E5 lub jako autonomiczną usługę, również mogą wyświetlać alerty usługi Defender dla aplikacji w chmurze związane z aplikacjami Microsoft 365 i usługami w Centrum zgodności platformy Microsoft 365 lub portalu Microsoft 365 Defender.

Aby wyświetlać w centrum zgodności lub w portalu usługi Defender tylko alerty usługi Defender dla aplikacji w  chmurze, użyj filtru źródłowego i wybierz **pozycję Defender for Cloud Apps**.

![Filtr Źródła umożliwia wyświetlanie tylko alertów usługi Defender dla aplikacji w chmurze.](../media/FilterCASAlerts.png)

Podobnie jak alert wyzwalany przez zasady alertu w Centrum zgodności, możesz wybrać alert usługi Defender dla aplikacji w chmurze, aby wyświetlić stronę wysuwu ze szczegółami tego alertu. Alert zawiera link do wyświetlania szczegółów i zarządzania alertem w portalu usługi Defender for Cloud Apps oraz link do odpowiedniej zasady usługi Defender dla aplikacji w chmurze, która wyzwoliła alert. Zobacz [Monitorowanie alertów w usłudze Defender dla aplikacji w chmurze](/cloud-app-security/monitor-alerts).

![Szczegóły alertu zawierają linki do portalu usługi Defender for Cloud Apps.](../media/CASAlertDetail.png)

> [!IMPORTANT]
> Zmiana stanu alertu usługi Defender dla aplikacji w chmurze w Centrum zgodności nie spowoduje zaktualizowania stanu rozwiązania dla tego samego alertu w portalu aplikacji usługi Defender dla chmury. Jeśli na przykład w Centrum zgodności oznaczysz stan alertu  jako Rozwiązany, stan alertu w portalu aplikacji usługi Defender dla chmury pozostanie niezmieniony. Aby rozwiązać lub odrzucić alert usługi Defender dla aplikacji w chmurze, zarządzaj alertem w portalu usługi Defender for Cloud Apps.
