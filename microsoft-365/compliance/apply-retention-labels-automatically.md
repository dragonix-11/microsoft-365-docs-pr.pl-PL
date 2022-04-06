---
title: Automatyczne stosowanie etykiety przechowywania w celu zachowania lub usunięcia zawartości
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Tworzenie zasad przechowywania z automatycznymi etykietami, aby można było automatycznie stosować etykiety w celu zachowania tego, co jest potrzebne, i usunięcia tego, co nie jest potrzebne
ms.openlocfilehash: 2d141ef349c456b9e8397ea1c96a4e450eaa73fc
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500443"
---
# <a name="automatically-apply-a-retention-label-to-retain-or-delete-content"></a>Automatyczne stosowanie etykiety przechowywania w celu zachowania lub usunięcia zawartości

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Ten scenariusz nie jest obsługiwany w przypadku rekordów [prawnych](records-management.md#records) ani etykiet domyślnych dla struktury porządkowej, takiej jak zestaw dokumentów lub biblioteka w programie SharePoint, ani folderu w Exchange. Te scenariusze wymagają [opublikowania zasad etykiet przechowywania](create-apply-retention-labels.md).

Jedną z najbardziej zaawansowanych funkcji etykiet [przechowywania](retention.md) jest możliwość ich automatycznego stosowania do zawartości, która jest taka, jak w określonych warunkach. W takim przypadku osoby w Twojej organizacji nie muszą stosować etykiet przechowywania. Microsoft 365 pracę za nich.
  
Automatyczne stosowanie etykiet przechowywania jest bardzo zaawansowane, ponieważ:
  
- Nie musisz przeszkolić użytkowników nad wszystkimi klasyfikacjami.
    
- Nie musisz polegać na użytkownikach, aby prawidłowo klasyfikować całą zawartość.
    
- Użytkownicy nie muszą już znać zasad zarządzania danymi — mogą skoncentrować się na pracy.
    
Etykiety przechowywania można stosować do zawartości automatycznie, jeśli do zawartości nie zastosowano jeszcze etykiety przechowywania i zawiera ona informacje poufne, słowa kluczowe lub właściwości, które można wyszukiwać, albo dopasowanie do przeszkolnych [klasyfikatorów](classifier-get-started-with.md). Teraz w wersji Preview możesz również automatycznie zastosować etykietę przechowywania do załączników w chmurze, które są przechowywane SharePoint lub OneDrive.

> [!TIP]
> Właściwości, które można wyszukiwać, [Teams nagrań spotkań](#microsoft-teams-meeting-recordings) i elementów[, do których zastosowano etykietę wrażliwości](#identify-files-and-emails-that-have-a-sensitivity-label).

Procesy automatycznego stosowania etykiety przechowywania na podstawie tych warunków:

![Diagram ról i zadań związanych z automatycznym stosowaniem etykiet.](../media/32f2f2fd-18a8-43fd-839d-72ad7a43e069.png)

Skorzystaj z poniższych instrukcji, aby wykonać dwa kroki administracyjne.

> [!NOTE]
> W przypadku automatycznych zasad etykiet po stronie usługi z warunkami są stosowane automatycznie etykiety przechowywania do elementów. Etykietę przechowywania można również automatycznie zastosować przy użyciu zasad etykiety w następujących czynnościach: 
>
> - Stosowanie etykiety przechowywania do modelu opisowego dokumentu w programie SharePoint Syntex
> - Stosowanie domyślnej etykiety przechowywania dla SharePoint i Outlook
> - Stosowanie etykiety przechowywania do wiadomości e-mail przy użyciu Outlook przechowywania
>
> Aby zobaczyć te scenariusze, [zobacz Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md).

## <a name="before-you-begin"></a>Przed rozpoczęciem

Administrator globalny w Twojej organizacji ma pełne uprawnienia do tworzenia i edytowania etykiet przechowywania oraz ich zasad. Jeśli nie logujesz się jako administrator globalny, zobacz informacje o uprawnieniach do zarządzania [](get-started-with-records-management.md#permissions) rekordami lub [informacjami w zależności](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels) od używasz rozwiązania.

Upewnij się, [że utworzono etykiety przechowywania,](file-plan-manager.md#create-retention-labels) które chcesz zastosować do elementów.

## <a name="how-to-create-an-auto-apply-retention-label-policy"></a>Jak utworzyć zasady etykiet przechowywania z automatycznym zastosowaniem

Przed utworzeniem zasad etykiet przechowywania zdecyduj, czy będą one **adaptacyjne** , czy **statyczne**. Aby uzyskać więcej informacji, zobacz [Adaptacyjne lub statyczne zakresy zasad przechowywania](retention.md#adaptive-or-static-policy-scopes-for-retention). Jeśli zdecydujesz się na korzystanie z adaptacyjnych zasad, musisz utworzyć co najmniej jeden adaptacyjny zakres przed utworzeniem zasad etykiet przechowywania, a następnie wybrać je podczas tworzenia procesu tworzenia zasad etykiet przechowywania. Aby uzyskać instrukcje, [zobacz Informacje o konfiguracji dotyczące adaptacyjnych zakresów](retention-settings.md#configuration-information-for-adaptive-scopes).

Podczas tworzenia zasad automatycznego stosowania należy wybrać etykietę przechowywania, która zostanie automatycznie zastosuje do zawartości, na podstawie warunków określonych przez użytkownika.

1. W [Centrum zgodności platformy Microsoft 365 przejdź](https://compliance.microsoft.com/) do jednej z następujących lokalizacji:
    
    - Jeśli używasz zarządzania rekordami:
        - **Rozwiązania** >  **Karta Zasady** > > **zarządzania rekordami** > **i Automatyczne stosowanie etykiety**
    
    - W przypadku korzystania z zarządzania informacjami:
        - **Rozwiązania** >  **Zarządzanie informacjami** >  **Karta Zasady** etykiet > **automatyczne stosowanie etykiety**
    
    Nie widzisz swojego rozwiązania od razu w okienku nawigacji? Najpierw wybierz pozycję **Pokaż wszystko**.

2. Wprowadź nazwę i opis zasad auto etykiet, a następnie wybierz pozycję **Dalej**.

3. W **przypadku opcji Wybierz typ zawartości, do której chcesz zastosować tę etykietę**, wybierz jeden z dostępnych warunków. Aby uzyskać więcej informacji na temat dostępnych opcji, zobacz sekcję Konfigurowanie warunków automatycznego stosowania etykiet [przechowywania](#configuring-conditions-for-auto-apply-retention-labels) na tej stronie.

4. W przypadku **strony Wybierz typ zasad przechowywania** do utworzenia wybierz pozycję **Adaptacyjny** lub Statyczny **, w** zależności od wyboru dokonanego w [instrukcjach Przed rozpoczęciem](#before-you-begin) . Jeśli nie masz jeszcze utworzonych zakresów adaptacyjnych, możesz wybrać pozycję  Adaptacyjny, ale ponieważ nie będzie żadnych adaptacyjnych zakresów do wyboru, nie możesz zakończyć działania kreatora za pomocą tej opcji.

5. W zależności od wybranego zakresu:
    
    - Jeśli wybrano **adaptacyjny**: Na  stronie Wybieranie zakresów i lokalizacji adaptacyjnych zasad wybierz pozycję  Dodaj zakresy i wybierz co najmniej jeden z utworzonych adaptacyjnych zakresów. Następnie wybierz jedną lub więcej lokalizacji. Lokalizacje, które można wybrać, zależą od [dodanych typów](retention-settings.md#configuration-information-for-adaptive-scopes) zakresów. Jeśli na przykład dodano tylko typ zakresu **użytkownika, będzie** można wybrać adres e-mail Exchange ale  nie SharePoint **witryn.** 
    
    - Jeśli wybrano **pozycję Statyczny**: **Na stronie** Wybieranie lokalizacji włącz lub wyłącz dowolną z tych lokalizacji. Dla każdej lokalizacji możesz pozostawić ją domyślną, aby zastosować zasady do całej [lokalizacji, lub](retention-settings.md#a-policy-that-applies-to-entire-locations) określić [uwzględniania i wykluczania](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions)
    
    Aby uzyskać informacje o dostępnych lokalizacjach, zobacz [Lokalizacje](retention-settings.md#locations).

6. Postępuj zgodnie z monitami kreatora, aby wybrać etykietę przechowywania, a następnie przejrzyj i prześlij opcje konfiguracji.

Aby edytować istniejące zasady etykiet przechowywania (typ zasad to **Automatyczne** stosowanie), zaznacz je, a następnie wybierz opcję Edytuj, aby  uruchomić **konfigurację Edytuj zasady** przechowywania.

Po oznaczeniu zawartości etykietą za pomocą zasad automatycznego stosowania etykiety nie można automatycznie usuwać ani zmieniać zastosowanej etykiety przez zmianę zawartości, zasad, nowych zasad automatycznego stosowania etykiet. Aby uzyskać więcej informacji, zobacz [Tylko jedna etykieta przechowywania na raz](retention.md#only-one-retention-label-at-a-time).

> [!NOTE]
> Zasady automatycznego stosowania etykiet przechowywania nigdy nie zastąpią istniejącej etykiety przechowywania, która jest stosowana do zawartości. Jeśli chcesz zmienić etykietę zawartości przy użyciu skonfigurowanych warunków, musisz ręcznie usunąć bieżącą etykietę przechowywania z istniejącej zawartości.

### <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Konfigurowanie warunków automatycznego stosowania etykiet przechowywania

Etykiety przechowywania można stosować do zawartości automatycznie, gdy zawiera ona:

- [Określone typy informacji poufnych](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)

- [Określone słowa kluczowe lub właściwości, które można wyszukiwać, zgodne z tworzyć zapytania](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Dopasowanie dla klasyfikatorów przeszkolnych](#auto-apply-labels-to-content-by-using-trainable-classifiers)

Etykiety przechowywania można też automatycznie stosować do nowo udostępnionych załączników [w chmurze](#auto-apply-labels-to-cloud-attachments).

Podczas konfigurowania etykiet przechowywania w celu automatycznego stosowania na podstawie informacji poufnych, słów kluczowych lub właściwości, które można wyszukiwać, lub przeszkolnych klasyfikatorów, skorzystaj z poniższej tabeli, aby określić, kiedy etykiety przechowywania mogą być stosowane automatycznie.

Exchange:

|Warunek|Elementy przesyłane (wysłane lub odebrane) |Istniejące elementy (dane w spoczynku)|
|:-----|:-----|:-----|
|Typy informacji poufnych — wbudowane| Tak | Nie |
|Typy informacji poufnych — niestandardowe| Tak | Nie |
|Określone słowa kluczowe lub właściwości, które można wyszukiwać| Tak |Tak |
|Klasyfikatory z możliwością szkolenia| Tak | Tak (tylko ostatnie sześć miesięcy) |

SharePoint i OneDrive:

|Warunek|Nowe lub zmodyfikowane elementy |Istniejące elementy |
|:-----|:-----|:-----|
|Typy informacji poufnych — wbudowane| Tak | Tak |
|Typy informacji poufnych — niestandardowe| Tak | Nie |
|Określone słowa kluczowe lub właściwości, które można wyszukiwać| Tak |Tak |
|Klasyfikatory z możliwością szkolenia| Tak | Tak (tylko ostatnie sześć miesięcy) |

Ponadto w tym SharePoint nie są obsługiwane elementy, które są w wersji roboczej lub które nigdy nie zostały opublikowane.

#### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Automatyczne stosowanie etykiet do zawartości z określonymi typami informacji poufnych

> [!IMPORTANT]
> W przypadku wiadomości e-mail, które są automatycznie stosowane przez identyfikację informacji poufnych, są automatycznie uwzględniane wszystkie skrzynki pocztowe, w tym skrzynki pocztowe z Microsoft 365 grup.
> 
> Mimo że skrzynki pocztowe grupy zazwyczaj były uwzględniane przez wybranie lokalizacji grupy **Grupy Microsoft 365, Grupy Microsoft 365** w przypadku tej konkretnej konfiguracji zasad lokalizacja grup obejmuje tylko witryny SharePoint połączone z grupą Microsoft 365 grupy.

Po utworzeniu zasad automatycznego stosowania etykiet przechowywania dla informacji poufnych jest wyświetlona ta sama lista szablonów zasad co w przypadku tworzenia zasad ochrony przed utratą danych (DLP). Każdy szablon jest wstępnie skonfigurowany do wyszukiwania konkretnych typów informacji poufnych. W poniższym przykładzie typy informacji poufnych znajdują się w  kategorii Prywatność oraz w szablonie danych umożliwiających identyfikację użytkownika **(PII**):

![Szablony zasad z typami informacji poufnych.](../media/sensitive-info-configuration.png)

Aby dowiedzieć się więcej o typach informacji poufnych, zobacz [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types). Obecnie w [tym scenariuszu nie są](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) obsługiwane dokładne typy informacji poufnych i linie papilarne dokumentów.[](document-fingerprinting.md)

Po wybraniu szablonu zasad można dodawać lub usuwać wszelkie typy informacji poufnych, a także zmieniać poziom ufności i liczbę wystąpień. W poprzednim przykładowym zrzucie ekranu te opcje zostały zmienione, dzięki czemu etykieta przechowywania będzie stosowana automatycznie tylko wtedy, gdy:
  
- Wykrywany typ informacji poufnych zapewnia dokładność dopasowania (czyli poziom  ufności[) co](sensitive-information-type-learn-about.md#more-on-confidence-levels) najmniej średniej ufności dla dwóch typów informacji poufnych oraz wysoką pewność dla jednego  z nich. Wiele typów informacji poufnych jest definiowanych za pomocą wielu wzorców, w przypadku których wzorzec o większej dokładności dopasowania wymaga więcej dowodów (na przykład słów kluczowych, dat lub adresów), a wzorzec o mniejszej dokładności dopasowania wymaga mniej dowodu. Im niższy poziom ufności, tym łatwiej zawartości odpowiada warunek, ale wraz z możliwością większej liczby wyników fałszywie dodatnich.

- Zawartość zawiera od 1 do 9 wystąpień dowolnego z tych trzech typów informacji poufnych. Wartość domyślna **to** **Dowolna**.

Aby uzyskać więcej informacji na temat tych opcji, zobacz poniższe wskazówki z dokumentacji DLP Dostosowywanie reguł tak, aby były łatwiejsze [lub trudniejsze do dopasowania](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Typy informacji poufnych mają dwa różne sposoby definiowania parametrów maksymalnej liczby unikatowych wystąpień. Aby dowiedzieć się więcej, zobacz [Obsługiwane wartości liczby wystąpień dla usługi SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Aby rozważyć automatyczne stosowanie etykiet przechowywania przy użyciu typów informacji poufnych:

- W przypadku korzystania z niestandardowych typów informacji poufnych nie można automatycznie oznaczać istniejących elementów w polach SharePoint i OneDrive.

- W przypadku wiadomości e-mail nie możesz wybrać konkretnych adresatów, których chcesz uwzględnić lub wykluczyć; obsługiwane jest **tylko ustawienie** Wszyscy adresaci i tylko w przypadku tej konfiguracji obejmuje skrzynki pocztowe z Microsoft 365 grup. 

#### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Automatyczne stosowanie etykiet do zawartości ze słowami kluczowymi lub właściwościami, które można wyszukiwać

Etykiety można automatycznie stosować do zawartości za pomocą zapytania zawierającego określone wyrazy, frazy lub wartości właściwości, które można wyszukiwać. Zapytanie można uściślić za pomocą operatorów wyszukiwania, takich jak ORAZ, LUB i NIE.

![Edytor zapytań.](../media/new-retention-query-editor.png)

Aby uzyskać więcej informacji na temat składni zapytania w języku słowa kluczowego (KQL), zobacz Informacje o składni języka KQL [słów kluczowych](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

Zasady oparte na zapytaniach stosowane automatycznie używają tego samego indeksu wyszukiwania, co wyszukiwanie zawartości zbierania elektronicznych materiałów dowodowych w celu identyfikowania zawartości. Aby uzyskać więcej informacji na temat właściwości, których można użyć, zobacz Zapytania słów kluczowych i [warunki wyszukiwania dotyczące wyszukiwania zawartości](keyword-queries-and-search-conditions.md).

W przypadku używania słów kluczowych lub właściwości uwzględnianych w wyszukiwaniu w celu automatycznego stosowania etykiet przechowywania należy uwzględnić kilka elementów:

- Na SharePoint właściwości przeszukane i właściwości niestandardowe nie są obsługiwane w tych zapytaniach KQL i dla dokumentów należy używać tylko wstępnie zdefiniowanych właściwości zarządzanych. Za pomocą mapowań na poziomie dzierżawy można jednak używać wstępnie zdefiniowanych właściwości zarządzanych, które są domyślnie włączone jako obiekty uściślające (RefinableDate00-19, RefinableString00-99, RefinableInt00-49, RefinableDecimals00-09 i RefinableDouble00-09). Aby uzyskać więcej informacji, zobacz [Omówienie właściwości przeszukanych](/SharePoint/technical-reference/crawled-and-managed-properties-overview) i zarządzanych w programie SharePoint Server, a aby uzyskać instrukcje, zobacz Tworzenie [nowej właściwości zarządzanej](/sharepoint/manage-search-schema#create-a-new-managed-property).

- Jeśli zamapujesz właściwość niestandardową na jedną z właściwości uściślijących, odczekaj 24 godziny przed użyciem jej w zapytaniu KQL do przechowywania etykiety przechowywania.

- Mimo SharePoint nazw właściwości zarządzanych za pomocą aliasów nie należy ich używać KQL etykietach. Zawsze określ rzeczywistą nazwę właściwości zarządzanej, na przykład "RefinableString01".

- Aby wyszukać wartości zawierające spacje lub znaki specjalne, należy użyć znaków podwójnego cudzysłowu (`" "`) w celu wyszukania frazy, `subject:"Financial Statements"`na przykład .

- Użyj właściwości *DocumentLink* zamiast *Path,* aby dopasować element na podstawie jego adresu URL. 

- Symbole wieloznaczne w sufiksie ( `*cat`takie jak ) lub symbole wieloznaczne z podciągami ( `*cat*`na przykład ) nie są obsługiwane. Obsługiwane są jednak symbole wieloznaczne w prefiksie ( `cat*`na przykład ).

- Należy pamiętać, że elementy częściowo indeksowane mogą być odpowiedzialne za to, że nie należy oznaczać oczekiwanych elementów etykietami lub oznaczać elementy, których chcesz wykluczyć z etykiet, gdy używasz operatora NOT. Aby uzyskać więcej informacji, zobacz [Częściowo indeksowane elementy w przeszukiwaniu zawartości](partially-indexed-items-in-content-search.md).


Przykładowe zapytania:

| Obciążenie pracą | Przykład |
|:-----|:-----|
|Exchange   | `subject:"Financial Statements"` |
|Exchange   | `recipients:garthf@contoso.com` |
|SharePoint | `contenttype:document` |
|SharePoint | `site:https://contoso.sharepoint.com/sites/teams/procurement AND contenttype:document`|
|Exchange lub SharePoint | `"customer information" OR "private"`|

Bardziej złożone przykłady:

Poniższe zapytanie dla zapytania SharePoint dokumentów programu Word lub arkuszy kalkulacyjnych programu Excel, gdy te pliki zawierają hasło słów **kluczowych,** **hasła** lub **pw**:

```
(password OR passwords OR pw) AND (filetype:doc* OR filetype:xls*)
```

Poniższe zapytanie dla programu Exchange identyfikuje dowolny dokument programu Word lub plik PDF zawierający wyraz **nda** lub frazę "umowa o nie  ujawnianiu", jeśli te dokumenty są dołączone do wiadomości e-mail:

```
(nda OR "non disclosure agreement") AND (attachmentnames:.doc* OR attachmentnames:.pdf)
```

Poniższe zapytanie dla zapytania SharePoint dokumenty zawierające numer karty kredytowej: 

```
sensitivetype:"credit card number"
```

Poniższe zapytanie zawiera kilka typowych słów kluczowych pomocnych w identyfikowaniu dokumentów lub wiadomości e-mail zawierających treści prawne:

```
ACP OR (Attorney Client Privilege*) OR (AC Privilege)
```

Poniższe zapytanie zawiera typowe słowa kluczowe pomocne w identyfikowaniu dokumentów lub wiadomości e-mail do zasobów ludzkich: 

```
(resume AND staff AND employee AND salary AND recruitment AND candidate)
```

W tym ostatnim przykładzie zastosowano najlepsze rozwiązanie, takie jak zawsze w przypadku operatorów między słowami kluczowymi. Spacja między słowami kluczowymi (lub dwoma wyrażeniami właściwość:wartość) jest taka sama jak użycie funkcji ORAZ. Dodając operatory zawsze, łatwiej jest zobaczyć, że to przykładowe zapytanie identyfikuje tylko zawartość zawierającą wszystkie te słowa kluczowe, a nie zawartość zawierającą jakiekolwiek słowa kluczowe. Jeśli zamierzasz identyfikować zawartość zawierającą jakiekolwiek słowa kluczowe, określ lub zamiast and (ORAZ). Jak pokazano w tym przykładzie, gdy zawsze określasz operatory, łatwiej jest poprawnie zinterpretować zapytanie. 

##### <a name="microsoft-teams-meeting-recordings"></a>Microsoft Teams nagrań spotkań

> [!NOTE]
> Możliwość zachowywania i usuwania Teams spotkań nie będzie działać, zanim nagrania zostaną zapisane w OneDrive lub SharePoint. Aby uzyskać więcej informacji, zobacz [Używanie funkcji OneDrive dla Firm i SharePoint Online lub Stream do nagrywania spotkań](/MicrosoftTeams/tmr-meeting-recording-change).

Aby zidentyfikować Microsoft Teams spotkań, które są przechowywane na kontach OneDrive użytkowników lub w SharePoint, w edytorze zapytań słów kluczowych określ następujące **elementy**:

```
ProgID:Media AND ProgID:Meeting
```

Nagrania spotkań są w większości przypadków zapisywane w OneDrive. Jednak w przypadku spotkań na kanale są one zapisywane w SharePoint.

##### <a name="identify-files-and-emails-that-have-a-sensitivity-label"></a>Identyfikowanie plików i wiadomości e-mail z etykietą wrażliwości

Aby zidentyfikować pliki w SharePoint lub wiadomościach OneDrive i Exchange e-mail, do których zastosowano konkretną etykietę [wrażliwości,](sensitivity-labels.md) w edytorze zapytań słów kluczowych określ następujące **wartości**:

```
InformationProtectionLabelId:<GUID>
```

Aby znaleźć identyfikator GUID, użyj polecenia cmdlet [Get-Label](/powershell/module/exchange/get-label) z programu [Security & Compliance Center w programie PowerShell](/powershell/exchange/scc-powershell):

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid
````

#### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Automatyczne stosowanie etykiet do zawartości przy użyciu przeszkolnych klasyfikatorów

Po wybraniu opcji dla klasyfikatora przeszkolonego możesz wybrać co najmniej jednego z przeszkolonych lub niestandardowych klasyfikatorów przeszkolonych:

![Wybierz klasyfikatora, który jest przeszkolny.](../media/retention-label-classifers.png)

> [!CAUTION]
> Wyszkodziliśmy wstępnie  przeszkolonych klasyfikatorów w języku obraźliwym, ponieważ został w nim wyszkolonych duża liczba wyników fałszywie dodatnich. Nie używaj tego klasyfikatora, a jeśli obecnie go używasz, zalecamy przeniesienie procesów biznesowych, a zamiast tego użyj wcześniej przeszkolonych klasyfikatorów: Molestowanie **kierowane,** **Profanity** i Zagrożenia.

Aby automatycznie zastosować etykietę przy użyciu tej opcji, SharePoint witryny i skrzynki pocztowe muszą mieć co najmniej 10 MB danych.

Aby uzyskać więcej informacji na temat przeszkolnych klasyfikatorów, zobacz [Informacje na temat przeszkolnych klasyfikatorów](classifier-learn-about.md).

> [!TIP]
> Jeśli używasz klasyfikatorów przeszkolnych na Exchange, zobacz Jak ponownie przeszkolenie klasyfikatora [w Eksploratorze zawartości](classifier-how-to-retrain-content-explorer.md).

Aby uwzględnić zastosowanie w przypadku korzystania z klasyfikatorów przeszkolnych w celu automatycznego stosowania etykiet przechowywania:

- Nie można automatycznie oznaczać SharePoint i OneDrive starszych niż sześć miesięcy.

#### <a name="auto-apply-labels-to-cloud-attachments"></a>Automatyczne stosowanie etykiet do załączników w chmurze

> [!NOTE]
> Ta opcja jest stopniowo wprowadzana w wersji Preview i może ulec zmianie.

Tej opcji może być konieczne, jeśli wymagane jest przechwytywanie i zachowywanie wszystkich kopii plików w dzierżawie wysyłanych przez użytkowników za pośrednictwem komunikacji. Tej opcji należy używać w połączeniu z zasadami przechowywania samych usług komunikacyjnych, usług Exchange i Teams.

> [!IMPORTANT]
> Po wybraniu etykiety do użycia w celu automatycznego stosowania etykiet przechowywania dla załączników w chmurze upewnij się, że ustawienie przechowywania  etykiet Rozpocznij okres przechowywania na podstawie wartości Gdy elementy zostały **oznaczone etykietą**.

Załączniki w chmurze, czasami nazywane także nowoczesnych załącznikami, to mechanizm udostępniania, który używa osadzonych linków do plików przechowywanych w chmurze. Obsługują one scentralizowane przechowywanie zawartości udostępnianej ze wspólnymi korzyściami, takimi jak kontrola wersji. Załączniki w chmurze nie są dołączonymi kopiami pliku ani linkiem tekstowym adresu URL do pliku. Pomocne może okazać się odwoływać się do wizualnych list kontrolnych obsługiwanych załączników w chmurze w [Outlook i](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-outlook) [Teams](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-teams).

Po wybraniu opcji zastosowania etykiety przechowywania do załączników w chmurze w celu zapewnienia zgodności jest tworzona kopia tego pliku w czasie udostępniania. Wybrana etykieta przechowywania zostanie zastosowana do kopii, a następnie będzie można ją zidentyfikować przy użyciu zbierania elektronicznych materiałów dowodowych. Użytkownicy nie wiedzą o kopii przechowywanej w bibliotece Zachowywanie. Etykieta przechowywania nie jest stosowana do samej wiadomości ani do oryginalnego pliku.

Jeśli plik zostanie zmodyfikowany i ponownie udostępniony, nowa kopia pliku w nowej wersji zostanie zapisana w bibliotece Hold hold (Przechowywanie). Aby uzyskać więcej informacji, łącznie z przyczynami stosowania  ustawienia Kiedy elementy były oznaczone etykietą, zobacz Jak działa przechowywanie w [załącznikach w chmurze](retention-policies-sharepoint.md#how-retention-works-with-cloud-attachments).

Załączniki w chmurze obsługiwane dla tej opcji to pliki, takie jak dokumenty, klipy wideo i obrazy, które są przechowywane SharePoint i OneDrive. Na Teams obsługiwane są załączniki w chmurze udostępniane w wiadomościach czatu oraz standardowe i prywatne kanały. Załączniki w chmurze udostępniane za pośrednictwem zaproszeń na spotkania i aplikacji Teams niż Outlook nie są obsługiwane. Załączniki w chmurze muszą być udostępniane przez użytkowników. Załączniki w chmurze wysyłane przez boty nie są obsługiwane.

Mimo że ta opcja nie jest wymagana, zalecamy upewnienie się, że dla Twoich witryn SharePoint i kont usługi OneDrive włączono obsługę wersji, dzięki czemu udostępniona wersja może zostać dokładnie przechwycona. Jeśli funkcja sporządzania wersji nie jest włączona, ostatnia dostępna wersja zostanie zachowana. Dokumenty w wersji roboczej lub nigdy nie opublikowane nie są obsługiwane.

Po wybraniu etykiety do użycia w celu automatycznego stosowania etykiet przechowywania dla załączników w chmurze upewnij się, że ustawienie przechowywania  etykiet Rozpocznij okres przechowywania na podstawie znajduje się na pozycji Kiedy oznaczono **elementy**. 

Podczas konfigurowania lokalizacji dla tej opcji możesz wybrać:

- **SharePoint** udostępnionych plików przechowywanych w witrynach SharePoint do komunikacji, witryn zespołowych, które nie są połączone przez Microsoft 365 grupy i witryny klasyczne. 
- **Grupy Microsoft 365** udostępnionych plików, które są przechowywane w witrynach zespołowych połączonych Microsoft 365 grupy.
- **OneDrive dla plików** udostępnionych przechowywanych w folderze OneDrive.

Aby zachować lub usunąć oryginalne pliki, wiadomości e-mail lub wiadomości e-mail oraz wiadomości Teams e-mail, należy utworzyć osobne zasady przechowywania.

> [!NOTE]
> Jeśli chcesz, aby przechowywane załączniki w chmurze wygasały jednocześnie z wiadomościami, które je zawierały, skonfiguruj etykietę przechowywania tak, aby zachowywała, a następnie usuwała akcje i chronometrażu co zasady przechowywania dla aplikacji Exchange i Teams.

Aby rozważyć automatyczne stosowanie etykiet przechowywania do załączników w chmurze:

- Tylko nowo udostępnione załączniki w chmurze będą automatycznie oznaczane w celu przechowywania.

- Załączniki w chmurze Teams i Outlook nie są obsługiwane.

- Następujące elementy nie są obsługiwane jako załączniki w chmurze, które mogą być zachowywane:
    - SharePoint, stron, list, formularzy, folderów, zestawów dokumentów OneNote stron.
    - Pliki udostępniane przez użytkowników, którzy nie mają dostępu do tych plików.
    - Pliki usuwane przed wysłaniem załącznika w chmurze. Może się tak zdarzyć, jeśli użytkownik skopiuje i wklei wcześniej udostępniony załącznik z innej wiadomości, bez uprzedniego potwierdzania, że plik jest nadal dostępny. Ktoś przesyła starą wiadomość, gdy plik zostanie teraz usunięty.
    - Pliki udostępniane przez gości lub użytkowników spoza organizacji.
    - Pliki w wersjach roboczych wiadomości e-mail i wiadomości, które nie są wysyłane.
    - Puste pliki.

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Jak długo trwa okres przechowywania etykiet przechowywania

W przypadku automatycznego stosowania etykiet przechowywania na podstawie informacji poufnych, słów kluczowych, właściwości uwzględnianych w wyszukiwaniu lub przeszkolnych klasyfikatorów zastosowanie etykiet przechowywania może potrwać do siedmiu dni:
  
![Diagram przedstawiający zastosowanie etykiet automatycznego stosowania.](../media/retention-labels-autoapply-timings.png)

Jeśli po upływie siedmiu dni etykiety oczekiwane nie są wyświetlane, sprawdź stan  zasad auto zastosuj, wybierając je na stronie Zasady etykiet w Centrum  zgodności. Jeśli zobaczysz stan Wyłączone (błąd **)** i w szczegółach lokalizacji zostanie wyświetlony komunikat informujący, że wdrożenie zasad (dla programu SharePoint) trwa dłużej niż oczekiwano, lub próby ponownego wdrożenia zasad (dla programu OneDrive), spróbuj ponownie uruchomić polecenie [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell, aby ponownie sprawdzić rozkład zasad:

1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Uruchom następujące polecenie:
    
    ```PowerShell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

## <a name="updating-retention-labels-and-their-policies"></a>Aktualizowanie etykiet przechowywania i ich zasad

W przypadku automatycznego stosowania zasad etykiet przechowywania, które są skonfigurowane dla informacji poufnych, słów kluczowych lub właściwości, które można wyszukiwać, lub dopasowania do klasyfikatorów przeszkolnych: Jeśli etykieta przechowywania z tych zasad jest już stosowana do zawartości, zmiana w konfiguracji wybranej etykiety i zasad zostanie automatycznie zastosowana do tej zawartości oprócz zawartości, która została nowo zidentyfikowana.

Aby zastosować automatycznie zasady etykiet przechowywania skonfigurowane dla załączników w chmurze: Ponieważ te zasady dotyczą nowo udostępnionych plików, a nie do istniejących plików, zmiana konfiguracji wybranej etykiety i zasad zostanie automatycznie zastosowana tylko do nowo udostępnionej zawartości.

Po utworzeniu i zapisaniu etykiety lub zasad nie można zmienić niektórych ustawień, takich jak:
- Nazwy etykiet przechowywania i ich zasad, typ zakresu (adaptacyjny lub statyczny) i ustawienia przechowywania z wyjątkiem okresu przechowywania. Nie można jednak zmienić okresu przechowywania, gdy okres przechowywania jest oparty na oznaczaniu elementów etykietą.
- Opcja oznaczania elementów jako rekordu.

### <a name="deleting-retention-labels"></a>Usuwanie etykiet przechowywania

Możesz usunąć etykiety przechowywania, które nie są obecnie uwzględnione w żadnych zasadach etykiet przechowywania, które nie są skonfigurowane na wypadek przechowywania na podstawie zdarzeń, lub oznaczać elementy jako rekordy prawne.

W przypadku etykiet przechowywania, które można usunąć, jeśli zostały one zastosowane do elementów, usunięcie zakończy się niepowodzeniem i zostanie wyświetlony link do Eksploratora zawartości identyfikujący elementy oznaczone etykietą.

Jednak wyświetlanie oznaczonych elementów w Eksploratorze zawartości może potrwać do dwóch dni. W tym scenariuszu etykieta przechowywania może zostać usunięta bez pokazywania linku do Eksploratora zawartości.

## <a name="locking-the-policy-to-prevent-changes"></a>Blokowanie zasad w celu uniemożliwinia zmian

Jeśli chcesz się upewnić, że nikt nie będzie miał możliwości wyłączenia zasad, usunięcia zasad lub ich mniej restrykcyjnych, zobacz Używanie blokady zachowywania do ograniczania zmian zasad przechowywania i zasad etykiet [przechowywania](retention-preservation-lock.md).

## <a name="next-steps"></a>Następne kroki

Aby ułatwić śledzenie etykiet zastosowanych na pomocą zasad automatycznego oznaczania:

- [Monitorowanie etykiet przechowywania](retention.md#monitoring-retention-labels)
- [Korzystanie z wyszukiwania zawartości w celu znalezienia całej zawartości z określoną etykietą przechowywania](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)
- [Akcje przechowywania inspekcji](retention.md#auditing-retention-actions)

Zobacz Sekcję Zarządzanie cyklem życia dokumentów przechowywanych w programie [SharePoint](auto-apply-retention-labels-scenario.md) za pomocą etykiet przechowywania można znaleźć w przykładowym scenariuszu, w którym stosowane są zasady automatycznego stosowania etykiet przechowywania z właściwościami zarządzanymi w programie SharePoint, oraz Przechowywanie oparte na zdarzeniach, aby rozpocząć okres przechowywania.
