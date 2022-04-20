---
title: Rozwiązania inspekcji platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- m365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Dowiedz się, jak przeprowadzać inspekcję działań użytkowników i administratorów w organizacji Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2ab97dc632aeaf13109380fb9a5586594c63ebaa
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949062"
---
# <a name="auditing-solutions-in-microsoft-365"></a>Rozwiązania inspekcji w Microsoft 365

Microsoft 365 rozwiązania do inspekcji zapewniają zintegrowane rozwiązanie ułatwiające organizacjom skuteczne reagowanie na zdarzenia związane z zabezpieczeniami, badania kryminalistyczne, dochodzenia wewnętrzne i obowiązki w zakresie zgodności. Tysiące operacji użytkowników i administratorów wykonywanych w dziesiątkach usług i rozwiązań Microsoft 365 są przechwytywane, rejestrowane i zachowywane w ujednoliconym dzienniku inspekcji organizacji. Rekordy inspekcji dla tych zdarzeń można przeszukiwać za pomocą operacji zabezpieczeń, administratorów IT, zespołów ds. ryzyka dotyczącego informacji poufnych oraz badaczy zgodności i prawnych w organizacji. Ta funkcja zapewnia wgląd w działania wykonywane w organizacji Microsoft 365.

## <a name="microsoft-365-auditing-solutions"></a>Rozwiązania inspekcji platformy Microsoft 365

Usługa Microsoft Purview oferuje dwa rozwiązania inspekcji: Audit (Standard) i Audit (Premium).

![Kluczowe możliwości inspekcji (standardowej) i inspekcji (Premium).](..\media\AuditingSolutionsComparison.png)

### <a name="audit-standard"></a>Inspekcja (standardowa)

Usługa Microsoft Purview Audit (Standard) zapewnia możliwość rejestrowania i wyszukiwania inspekcji działań oraz wykonywania dochodzeń sądowych, informatycznych, zgodności i dochodzeń prawnych.

- **Domyślnie włączone**. Inspekcja (Standardowa) jest domyślnie włączona dla wszystkich organizacji z odpowiednią subskrypcją. Oznacza to, że rekordy dla inspekcji działań zostaną przechwycone i możliwe do przeszukiwania. Jedyną wymaganą konfiguracją jest przypisanie uprawnień niezbędnych do uzyskania dostępu do narzędzia wyszukiwania dzienników inspekcji (i odpowiedniego polecenia cmdlet) i upewnienie się, że użytkownikowi przypisano odpowiednią licencję na funkcje inspekcji usługi Microsoft Purview (Premium).
- **Tysiące zdarzeń inspekcji z możliwością wyszukiwania**. Możesz wyszukać szeroki zakres inspekcji wykonywanych działań, które są większością Microsoft 365 usług w organizacji. Aby uzyskać częściową listę działań, które można wyszukać, zobacz [Inspekcja działań](search-the-audit-log-in-security-and-compliance.md#audited-activities). Aby uzyskać listę usług i funkcji, które obsługują inspekcję działań, zobacz [Audit log record type (Typ rekordu dziennika inspekcji](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype)).
- **Narzędzie do wyszukiwania inspekcji w portalu zgodności usługi Microsoft Purview**. Użyj narzędzia do wyszukiwania dzienników inspekcji w portalu zgodności, aby wyszukać rekordy inspekcji. Możesz wyszukać określone działania, działania wykonywane przez określonych użytkowników i działania, które wystąpiły z zakresem dat. Oto zrzut ekranu przedstawiający narzędzie do wyszukiwania inspekcji w Centrum zgodności.

   ![Narzędzie do wyszukiwania dzienników inspekcji w portalu zgodności.](../media/AuditLogSearchToolMCC.png)

- **Polecenie cmdlet Search-UnifiedAuditLog**. Możesz również użyć polecenia cmdlet **Search-UnifiedAuditLog** w programie Exchange Online programu PowerShell (podstawowego polecenia cmdlet narzędzia wyszukiwania), aby wyszukać zdarzenia inspekcji lub użyć go w skrypcie. Więcej informacji można znaleźć w następujących artykułach:

  - [Dokumentacja poleceń cmdlet Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)
  - [Przeszukaj dziennik inspekcji za pomocą skryptu programu PowerShell](audit-log-search-script.md)

- **Eksportuj rekordy inspekcji do pliku CSV**. Po uruchomieniu narzędzia do wyszukiwania dzienników inspekcji w centrum zgodności można wyeksportować rekordy inspekcji zwrócone przez wyszukiwanie do pliku CSV. Dzięki temu można używać Microsoft Excel sortowania i filtrowania różnych właściwości rekordu inspekcji. Możesz również użyć funkcji przekształcania Excel Power Query, aby podzielić każdą właściwość w obiekcie AuditData JSON na własną kolumnę. Umożliwia to efektywne wyświetlanie i porównywanie podobnych danych dla różnych zdarzeń. Aby uzyskać więcej informacji, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

- **Dostęp do dzienników inspekcji za pośrednictwem interfejsu API działania zarządzania Office 365**. Trzecią metodą uzyskiwania dostępu do rekordów inspekcji i pobierania ich jest użycie interfejsu API działania zarządzania Office 365. Umożliwia to organizacjom przechowywanie danych inspekcji przez dłuższy czas niż domyślne 90 dni i umożliwia im importowanie danych inspekcji do rozwiązania SIEM. Aby uzyskać więcej informacji, zobacz [dokumentację interfejsu API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

- **90-dniowe przechowywanie dziennika inspekcji**. Gdy inspekcja działania jest wykonywana przez użytkownika lub administratora, rekord inspekcji jest generowany i przechowywany w dzienniku inspekcji organizacji. W obszarze Inspekcja (Standardowa) rekordy są przechowywane przez 90 dni, co oznacza, że można wyszukiwać działania, które wystąpiły w ciągu ostatnich trzech miesięcy.

### <a name="audit-premium"></a>Inspekcja (Premium)

Inspekcja (Premium) opiera się na możliwościach inspekcji (Standardowa), zapewniając zasady przechowywania dzienników inspekcji, dłuższe przechowywanie rekordów inspekcji, zdarzenia o wysokiej wartości i dostęp do interfejsu API działania zarządzania Office 365.

- **Inspekcja zasad przechowywania dzienników**. Możesz utworzyć niestandardowe zasady przechowywania dzienników inspekcji, aby przechowywać rekordy inspekcji przez dłuższy czas do jednego roku (i do 10 lat dla użytkowników z wymaganą licencją dodatku). Można utworzyć zasady do przechowywania rekordów inspekcji w oparciu o usługę, w której są wykonywane inspekcje działań, określone działania inspekcji lub użytkownika, który wykonuje inspekcję działania.

- **Dłuższe przechowywanie rekordów inspekcji**. Domyślnie rekordy inspekcji Exchange, SharePoint i Azure Active Directory są przechowywane przez jeden rok. Rekordy inspekcji dla wszystkich innych działań są domyślnie przechowywane przez 90 dni lub można użyć zasad przechowywania dzienników inspekcji, aby skonfigurować dłuższe okresy przechowywania.

- **Zdarzenia inspekcji o wysokiej wartości (Premium).** Rekordy inspekcji kluczowych zdarzeń mogą pomóc organizacji w prowadzeniu badań kryminalistycznych i zgodności, zapewniając wgląd w zdarzenia, takie jak czas uzyskiwania dostępu do elementów poczty lub kiedy elementy poczty zostały przekazane i przekazane, oraz kiedy i co użytkownik szukał w usłudze Exchange Online i SharePoint Online. Te kluczowe zdarzenia mogą pomóc w zbadaniu możliwych naruszeń i określeniu zakresu naruszenia zabezpieczeń.

- **Większa przepustowość interfejsu API działania zarządzania Office 365**. Inspekcja (Premium) zapewnia organizacjom większą przepustowość dostępu do dzienników inspekcji za pośrednictwem interfejsu API działania zarządzania Office 365. Mimo że wszystkie organizacje (z inspekcją (standardową) lub inspekcją (Premium)) są początkowo przydzielane według planu bazowego wynoszącego 2000 żądań na minutę, limit ten będzie dynamicznie zwiększany w zależności od liczby miejsc w organizacji i subskrypcji licencjonowania. Dzięki temu organizacje z funkcją Inspekcja (Premium) uzyskują około dwukrotnie wyższą przepustowość niż w organizacjach z usługą Audit (Standard).

Aby uzyskać bardziej szczegółowe informacje na temat funkcji inspekcji (Premium), zobacz [Inspekcja (Premium) w Microsoft 365](advanced-audit.md).

## <a name="comparison-of-key-capabilities"></a>Porównanie kluczowych możliwości

W poniższej tabeli porównano kluczowe możliwości dostępne w obszarze Inspekcja (Standardowa) i Inspekcja (Premium). Wszystkie funkcje inspekcji (w warstwie Standardowa) są zawarte w sekcji Inspekcja (Premium).

|Możliwości|Inspekcja (standardowa)|Inspekcja (Premium)|
|:------|:-------------|:-------------|
|Domyślnie włączone|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Tysiące zdarzeń inspekcji z możliwością wyszukiwania|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Narzędzie do wyszukiwania inspekcji w portalu zgodności|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|polecenie cmdlet Search-UnifiedAuditLog|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Eksportowanie rekordów inspekcji do pliku CSV|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Dostęp do dzienników inspekcji za pośrednictwem interfejsu API działania zarządzania Office 365 <sup>1</sup>|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)</sup>|
|90-dniowe przechowywanie dziennika inspekcji|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|1-letni okres przechowywania dziennika inspekcji||![Obsługiwane.](../media/check-mark.png)|
|10-letni okres przechowywania dziennika inspekcji <sup>2</sup>||![Obsługiwane](../media/check-mark.png)|
|Zasady przechowywania dzienników inspekcji||![Obsługiwane](../media/check-mark.png)|
|Zdarzenia o wysokiej wartości, kluczowe||![Obsługiwane](../media/check-mark.png)|
||||
> [!NOTE]
> <sup>1</sup> Inspekcja (Premium) obejmuje wyższy dostęp do interfejsu API działania zarządzania Office 365, który zapewnia szybszy dostęp do danych inspekcji.<br/><sup>2</sup> Oprócz wymaganej licencji na inspekcję (Premium) (opisanej w następnej sekcji), użytkownikowi musi zostać przypisany 10-letni dodatek Przechowywania dzienników inspekcji w celu zachowania rekordów inspekcji przez 10 lat.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

W poniższych sekcjach zidentyfikowano wymagania licencyjne dotyczące inspekcji (standardowej) i inspekcji (Premium). Funkcje inspekcji (Standardowa) są dołączone do funkcji Zaawansowana inspekcja.

### <a name="audit-standard"></a>Inspekcja (standardowa)

- subskrypcja Microsoft 365 Business Basic
- subskrypcja Aplikacje Microsoft 365 for Business
- subskrypcja Microsoft 365 Enterprise E3
- Microsoft 365 Business Premium
- subskrypcja Microsoft 365 Education A3
- subskrypcja Microsoft 365 Government G3
- subskrypcja Microsoft 365 Government G1
- subskrypcja Microsoft 365 Frontline F1 lub F3 lub dodatek F5 Security
- subskrypcja Office 365 Enterprise E3
- subskrypcja Office 365 Enterprise E1
- subskrypcja Office 365 Education A1
- subskrypcja Office 365 Education A3

### <a name="audit-premium"></a>Inspekcja (Premium)

- subskrypcja Microsoft 365 Enterprise E5
- subskrypcja Microsoft 365 Enterprise E3 + dodatek Zgodność platformy Microsoft 365 E5
- subskrypcja Microsoft 365 Enterprise E3 + dodatek Microsoft 365 E5 eDiscovery and Audit
- subskrypcja Microsoft 365 Education A5
- Microsoft 365 Education subskrypcji usługi A3 i dodatku Microsoft 365 A5 Compliance
- Microsoft 365 Education subskrypcji usługi A3 i dodatku Microsoft 365 A5 eDiscovery and Audit
- subskrypcja Microsoft 365 Government G5
- subskrypcja Microsoft 365 Government G3 + dodatek zgodności Microsoft 365 G5
- subskrypcja Microsoft 365 Government G3 + dodatek Microsoft 365 G5 eDiscovery and Audit
- Microsoft 365 dodatek Zgodność z zabezpieczeniami linii frontu F5 lub zgodność & zabezpieczeń F5
- subskrypcja Office 365 Enterprise E5
- subskrypcja Office 365 Education A5

## <a name="set-up-microsoft-365-auditing-solutions"></a>Konfigurowanie rozwiązań inspekcji Microsoft 365

Aby rozpocząć korzystanie z rozwiązań inspekcji w Microsoft 365, zapoznaj się z poniższymi wskazówkami dotyczącymi konfiguracji.

### <a name="set-up-audit-standard"></a>Konfigurowanie inspekcji (standardowa)

Pierwszym krokiem jest skonfigurowanie inspekcji (Standardowa), a następnie uruchomienie wyszukiwania dzienników inspekcji.

![Przepływ pracy do skonfigurowania inspekcji (Standardowa).](../media/BasicAuditingWorkflow.png)

1. Sprawdź, czy Twoja organizacja ma subskrypcję, która obsługuje usługę Audit (Standard), a w razie potrzeby subskrypcję, która obsługuje usługę Audit (Premium).

2. Przypisz uprawnienia w Exchange Online osobom w organizacji, które będą używać narzędzia do wyszukiwania dzienników inspekcji w portalu zgodności lub użyjesz polecenia cmdlet **Search-UnifiedAuditLog**. W szczególności użytkownicy muszą mieć przypisaną rolę dzienników inspekcji View-Only lub dzienników inspekcji w Exchange Online.

3. Przeszukaj dziennik inspekcji. Po wykonaniu kroków 1 i 2 użytkownicy w organizacji mogą używać narzędzia do wyszukiwania dzienników inspekcji (lub odpowiedniego polecenia cmdlet) do wyszukiwania inspekcji działań.

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Konfigurowanie inspekcji (standardowa)](set-up-basic-audit.md).

### <a name="set-up-audit-premium"></a>Konfigurowanie inspekcji (Premium)

Jeśli Twoja organizacja ma subskrypcję obsługą funkcji Inspekcja (Premium), wykonaj następujące kroki, aby skonfigurować i korzystać z dodatkowych funkcji w obszarze Inspekcja (Premium).

![Przepływ pracy do skonfigurowania inspekcji (Premium).](../media/AdvancedAuditWorkflow.png)

1. Skonfiguruj inspekcję (Premium) dla użytkowników. Ten krok składa się z następujących zadań:

   - Sprawdzanie, czy użytkownikom przypisano odpowiednią licencję lub licencję dodatku na potrzeby inspekcji (Premium).
  
   - Włączenie planu aplikacji/usługi Inspekcja (Premium) musi być przeznaczone dla tych użytkowników.
  
   - Włączanie inspekcji kluczowych zdarzeń, a następnie włączanie planu aplikacji/usługi inspekcji zaawansowanej dla tych użytkowników.

2. Włącz rejestrowanie zdarzeń inspekcji (Premium), gdy użytkownicy wykonują wyszukiwania w Exchange Online i SharePoint Online.

3. Skonfiguruj zasady przechowywania dzienników inspekcji. Oprócz domyślnych zasad, które zachowują rekordy inspekcji Exchange, SharePoint i Azure AD przez jeden rok, można utworzyć dodatkowe zasady przechowywania dzienników inspekcji, aby spełnić wymagania zespołów ds. operacji zabezpieczeń, IT i zgodności organizacji.

4. Wyszukaj kluczowe zdarzenia inspekcji (Premium) i inne działania podczas prowadzenia dochodzeń kryminalistycznych. Po wykonaniu kroków 1 i 2 możesz przeszukać dziennik inspekcji pod kątem zdarzeń inspekcji (Premium) i innych działań podczas badania kryminalistycznego naruszonego konta i innych typów badań zabezpieczeń lub zgodności.

Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Konfigurowanie inspekcji (Premium)](set-up-advanced-audit.md).

## <a name="training"></a>Szkolenia

Szkolenie zespołu ds. operacji zabezpieczeń, administratorów IT i zespołu badaczy zgodności w zakresie podstaw inspekcji (standard) i inspekcji (Premium) może pomóc organizacji szybciej rozpocząć pracę przy użyciu inspekcji, aby pomóc w badaniu. Microsoft 365 udostępnia następujący zasób ułatwiający tym użytkownikom w organizacji rozpoczęcie inspekcji: [Opisz możliwości zbierania elektronicznych materiałów dowodowych i inspekcji Microsoft 365](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
