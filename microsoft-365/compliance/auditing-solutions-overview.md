---
title: Microsoft 365 rozwiązań inspekcji
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
description: Dowiedz się, jak inspekcjić działania użytkowników i administratorów w Microsoft 365 organizacji.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 92fb008e7fe03b4871b8838d78965c1508a20fdc
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63494530"
---
# <a name="auditing-solutions-in-microsoft-365"></a>Rozwiązania inspekcji w programie Microsoft 365

Microsoft 365 rozwiązania inspekcji zapewniają zintegrowane rozwiązanie, które pomaga organizacjom w efektywnym reagowaniu na zdarzenia związane z zabezpieczeniami, dochodzeniach sądowych, badaniach wewnętrznych i zobowiązaniach dotyczących zgodności. Tysiące operacji wykonywanych przez użytkowników i administratorów w dziesiątkach Microsoft 365 usług i rozwiązań są rejestrowane, rejestrowane i przechowywane w ujednoliconym dzienniku inspekcji organizacji. Rekordy inspekcji dotyczące tych zdarzeń mogą przeszukiwać administratorzy zabezpieczeń, administratorzy IT, zespoły ds. ryzyka w ramach niejawnego programu testów oraz osoby z grupy osób o zgodności z przepisami w organizacji. Ta funkcja zapewnia wgląd w działania wykonywane w całej organizacji Microsoft 365 organizacji.

## <a name="microsoft-365-auditing-solutions"></a>Microsoft 365 rozwiązań inspekcji

Microsoft 365 dwa rozwiązania inspekcji: inspekcja podstawowa i inspekcja zaawansowana.

![Najważniejsze funkcje inspekcji podstawowej i zaawansowanej.](..\media\AuditingSolutionsComparison.png)

### <a name="basic-audit"></a>Inspekcja podstawowa

Inspekcja podstawowa umożliwia rejestrowanie i wyszukiwanie działań zweryfikowanych oraz zapewnianie możliwości dochodzenia sądowego, it, zgodności i dochodzenia prawnego.

- **Domyślnie włączone**. Inspekcja podstawowa jest domyślnie włączona dla wszystkich organizacji z odpowiednią subskrypcją. Oznacza to, że rekordy dotyczące działań inspekcji zostaną zarejestrowane i będzie można je przeszukiwać. Jedyną wymaganą konfiguracją jest przypisanie uprawnień niezbędnych do uzyskiwania dostępu do narzędzia do przeszukiwania dziennika inspekcji (i odpowiadającego mu polecenia cmdlet) oraz upewnienia się, że do użytkownika jest przypisana odpowiednia licencja dla funkcji zaawansowanej inspekcji.
- **Tysiące zdarzeń inspekcji, które można wyszukiwać**. Istnieje możliwość wyszukania szerokiego zakresu działań, które mają miejsce w większości Microsoft 365 w organizacji. Aby uzyskać częściową listę działań, które można wyszukać, zobacz [Działania zweryfikowane.](search-the-audit-log-in-security-and-compliance.md#audited-activities) Aby uzyskać listę usług i funkcji, które obsługują rejestrowane działania, zobacz Typ rekordu [dziennika inspekcji](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).
- **Narzędzie do przeszukiwania inspekcji w Centrum zgodności platformy Microsoft 365**. Aby wyszukać rekordy inspekcji, użyj narzędzia Centrum zgodności platformy Microsoft 365 przeszukiwania dziennika inspekcji. Możesz wyszukiwać określone działania, działania wykonywane przez określonych użytkowników oraz działania, które wystąpiły w zakresie dat. Oto zrzut ekranu przedstawiający narzędzie Wyszukiwanie inspekcji w Centrum zgodności.

   ![Narzędzie do przeszukiwania dziennika inspekcji w Centrum zgodności platformy Microsoft 365.](../media/AuditLogSearchToolMCC.png)

- **Polecenie cmdlet Search-UnifiedAuditLog**. Możesz także użyć polecenia cmdlet **Search-UnifiedAuditLog** w programie Exchange Online PowerShell (źródłowym poleceniu cmdlet narzędzia wyszukiwania), aby wyszukać zdarzenia inspekcji lub użyć ich w skrypcie. Więcej informacji można znaleźć w następujących artykułach:

  - [Polecenie cmdlet Search-UnifiedAuditLog — informacje](/powershell/module/exchange/search-unifiedauditlog)
  - [Przeszukiwanie dziennika inspekcji za pomocą skryptu programu PowerShell](audit-log-search-script.md)

- **Eksportowanie rekordów inspekcji do pliku CSV**. Po uruchomieniu narzędzia przeszukiwania dziennika inspekcji w centrum zgodności można wyeksportować rekordy inspekcji zwrócone przez wyszukiwanie do pliku CSV. Umożliwia to używanie funkcji Microsoft Excel i filtrowania według różnych właściwości rekordu inspekcji. Możesz również użyć funkcji przekształcania Excel Power Query, aby podzielić poszczególne właściwości obiektu JSON Dane inspekcji na własną kolumnę. Umożliwia to efektywne wyświetlanie i porównywanie podobnych danych dla różnych zdarzeń. Aby uzyskać więcej informacji, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

- **Dostęp do dzienników inspekcji za Office 365 API działań zarządzania**. Trzecią metodą uzyskiwania dostępu do rekordów inspekcji i pobierania ich jest użycie interfejsu API działań Office 365 zarządzania. Dzięki temu organizacje mogą przechowywać dane inspekcji przez dłuższy czas niż domyślne 90 dni i importować dane inspekcji do rozwiązania SIEM. Aby uzyskać więcej informacji, [zobacz Office 365 interfejsu API działań zarządzania](/office/office-365-management-api/office-365-management-activity-api-reference).

- **90-dniowe przechowywanie dziennika inspekcji**. Gdy użytkownik lub administrator wykonuje rejestrowane działania, w dzienniku inspekcji organizacji jest generowany i przechowywany rekord inspekcji. W ramach inspekcji podstawowej rekordy są przechowywane przez 90 dni, co oznacza, że można wyszukiwać działania, które miały miejsce w ciągu ostatnich trzech miesięcy.

### <a name="advanced-audit"></a>Inspekcja zaawansowana

Zaawansowana inspekcja bazuje na możliwościach inspekcji podstawowej, udostępniając zasady przechowywania dziennika inspekcji, dłuższe przechowywanie rekordów inspekcji, ważne zdarzenia o wysokiej wartości oraz wyższy dostęp do przepustowości interfejsu API działań zarządzania Office 365 zarządzania.

- **Zasady przechowywania dziennika inspekcji**. Możesz utworzyć niestandardowe zasady przechowywania dziennika inspekcji, aby przechowywać rekordy inspekcji przez dłuższy czas do jednego roku (i do 10 lat dla użytkowników z wymaganą licencją dodatku). Zasady możesz tworzyć w celu zachowywania rekordów inspekcji w oparciu o usługę, w której mają miejsce działania, określone działania pod inspekcją lub użytkownika, który wykonuje inspekcję.

- **Dłuższe przechowywanie rekordów inspekcji**. Exchange, SharePoint i Azure Active Directory są domyślnie przechowywane przez jeden rok. Rekordy inspekcji dotyczące wszystkich innych działań są domyślnie zachowywane przez 90 dni. Za pomocą zasad przechowywania dziennika inspekcji można także skonfigurować dłuższe okresy przechowywania.

- **Ważne, istotne zdarzenia inspekcji zaawansowanej o wysokiej wartości**. Inspekcja rekordów dotyczących ważnych zdarzeń może ułatwić organizacji przeprowadzenie dochodzenia sądowego i zapewniania zgodności przez zapewnienie widoczności zdarzeń, takich jak czas dostępu do elementów poczty, czas odpowiedzi i wiadomości przesyłanych dalej lub kiedy i co użytkownik wyszukiwał w usługach Exchange Online i SharePoint Online. Te ważne wydarzenia mogą ułatwić badanie możliwych naruszeń bezpieczeństwa i ustalenie zakresu naruszenia bezpieczeństwa.

- **Wyższa przepustowość dla interfejsu API Office 365 zarządzania**. Zaawansowana inspekcja zapewnia organizacjom większą przepustowość dostępu do dzienników inspekcji za pośrednictwem Office 365 API działań zarządzania. Mimo że do wszystkich organizacji (z inspekcją podstawową lub zaawansowaną) wstępnie przydzielono 2000 żądań na minutę, ten limit dynamicznie się zwiększy w zależności od liczby miejsc w organizacji i subskrypcji licencji. W wyniku tego w organizacjach, w których inspekcja zaawansowana ma przepustowość dwukrotnie większą niż w organizacjach z inspekcją podstawową, ta przepustowość jest niemal dwukrotnie  razy 90-

Aby uzyskać bardziej szczegółowe informacje na temat funkcji zaawansowanej inspekcji, zobacz [Inspekcja zaawansowana w programie Microsoft 365](advanced-audit.md).

## <a name="comparison-of-key-capabilities"></a>Porównanie kluczowych funkcji

W poniższej tabeli porównano kluczowe funkcje dostępne w przypadku inspekcji podstawowej i inspekcji zaawansowanej. Wszystkie funkcje inspekcji podstawowej są dostępne w ramach inspekcji zaawansowanej.

|Funkcja|Inspekcja podstawowa|Inspekcja zaawansowana|
|:------|:-------------|:-------------|
|Domyślnie włączone|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Tysiące zdarzeń inspekcji, które można wyszukiwać|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Narzędzie do przeszukiwania inspekcji w Centrum zgodności platformy Microsoft 365|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Search-UnifiedAuditLog cmdlet|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Eksportowanie rekordów inspekcji do pliku CSV|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Dostęp do dzienników inspekcji za Office 365 API działań zarządzania <sup>1</sup>|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)</sup>|
|90-dniowe przechowywanie dziennika inspekcji|![Obsługiwane.](../media/check-mark.png)|![Obsługiwane.](../media/check-mark.png)|
|Okres przechowywania dziennika inspekcji — 1 rok||![Obsługiwane.](../media/check-mark.png)|
|10-letnia przechowywanie dziennika inspekcji <sup>2</sup>||![Obsługiwane](../media/check-mark.png)|
|Zasady przechowywania dziennika inspekcji||![Obsługiwane](../media/check-mark.png)|
|Ważne wydarzenia o wysokiej wartości||![Obsługiwane](../media/check-mark.png)|
||||
> [!NOTE]
> <sup>1 Zaawansowana</sup> inspekcja obejmuje wyższy dostęp do przepustowości interfejsu API działań Office 365 zarządzania, który zapewnia szybszy dostęp do danych inspekcji.<br/><sup>2</sup> Oprócz wymaganego licencjonowania dla inspekcji zaawansowanej (opisanej w następnej sekcji) użytkownikowi należy przypisać 10-letnią licencję przechowywania dziennika inspekcji, aby zachować rekordy inspekcji przez 10 lat.

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

W poniższych sekcjach przedstawiono wymagania dotyczące licencjonowania w przypadku inspekcji podstawowej i zaawansowanej. Funkcja inspekcji podstawowej jest dostępna w ramach inspekcji zaawansowanej.

### <a name="basic-audit"></a>Inspekcja podstawowa

- Microsoft 365 Business Basic subskrypcji
- Aplikacje Microsoft 365 dla firm
- Microsoft 365 Enterprise E3
- Microsoft 365 Business Premium
- Microsoft 365 Education A3
- Microsoft 365 dla instytucji rządowych G3
- Microsoft 365 dla instytucji rządowych G1
- Microsoft 365 frontline F1 lub F3 albo dodatek F5 Security
- Office 365 Enterprise E3
- Office 365 Enterprise E1
- Office 365 Education A1
- Office 365 Education A3

### <a name="advanced-audit"></a>Inspekcja zaawansowana

- Microsoft 365 Enterprise E5
- Microsoft 365 Enterprise E3 + Zgodność platformy Microsoft 365 E5 subskrypcji
- Microsoft 365 Enterprise E3 + Microsoft 365 E5 zbierania elektronicznych materiałów dowodowych i dodatków Inspekcja
- Microsoft 365 Education A5
- Microsoft 365 Education A3 + Microsoft 365 A5 Zgodności z przepisami
- Microsoft 365 Education A3 + Microsoft 365 A5 zbierania elektronicznych materiałów dowodowych i dodatku Inspekcja
- Microsoft 365 dla instytucji rządowych G5
- Microsoft 365 dla instytucji rządowych G3 + Microsoft 365 zgodności z przepisami Microsoft 365 G5
- Microsoft 365 dla instytucji rządowych G3 + Microsoft 365 usługi zbierania elektronicznych materiałów dowodowych i inspekcji usługi Microsoft 365 G5
- Microsoft 365 Frontline F5 Compliance lub F5 Security & Compliance add-on
- Office 365 Enterprise E5
- Office 365 Education A5

## <a name="set-up-microsoft-365-auditing-solutions"></a>Konfigurowanie Microsoft 365 inspekcji

Aby rozpocząć korzystanie z rozwiązań inspekcji w programie Microsoft 365, zobacz następujące wskazówki dotyczące konfiguracji.

### <a name="set-up-basic-audit"></a>Konfigurowanie inspekcji podstawowej

Pierwszym krokiem jest skonfigurowanie inspekcji podstawowej, a następnie rozpoczęcie przeszukiwania dziennika inspekcji.

![Przepływ pracy w celu skonfigurowania inspekcji podstawowej.](../media/BasicAuditingWorkflow.png)

1. Upewnij się, że organizacja ma subskrypcję, która obsługuje inspekcję podstawową, i — jeśli to — subskrypcję, która obsługuje inspekcję zaawansowaną.

2. Przypisz uprawnienia w Exchange Online osobom w organizacji, które będą używać narzędzia do przeszukiwania dziennika inspekcji w programie Centrum zgodności platformy Microsoft 365 lub użyj polecenia cmdlet **Search-UnifiedAuditLog**. W szczególności użytkownikom należy przypisać rolę dziennika inspekcji View-Only lub Dzienniki inspekcji w programie Exchange Online.

3. Przeszukiwanie dziennika inspekcji. Po zakończeniu wykonywania kroków 1 i 2 użytkownicy w twojej organizacji mogą używać narzędzia do przeszukiwania dziennika inspekcji (lub odpowiadającego mu polecenia cmdlet) do wyszukiwania działań inspekcji.

Aby uzyskać bardziej szczegółowe instrukcje, [zobacz Konfigurowanie inspekcji podstawowej](set-up-basic-audit.md).

### <a name="set-up-advanced-audit"></a>Konfigurowanie inspekcji zaawansowanej

Jeśli Twoja organizacja ma subskrypcję, która obsługuje inspekcję zaawansowaną, wykonaj poniższe czynności, aby skonfigurować dodatkowe funkcje i korzystać z nich w ramach inspekcji zaawansowanej.

![Przepływ pracy do skonfigurowania inspekcji zaawansowanej.](../media/AdvancedAuditWorkflow.png)

1. Konfigurowanie inspekcji zaawansowanej dla użytkowników. Ten krok składa się z następujących zadań:

   - Sprawdzanie, czy do użytkowników przypisano odpowiednią licencję lub licencję dodatku dla inspekcji zaawansowanej.
  
   - Włączenie planu usługi/aplikacji inspekcji zaawansowanej musi być dla tych użytkowników.
  
   - Włączanie inspekcji ważnych zdarzeń, a następnie włączanie dla tych użytkowników planu aplikacji/usługi zaawansowanej inspekcji.

2. Włącz funkcję Advanced Audit events (Zaawansowane inspekcje), która ma być rejestrowana, gdy użytkownicy wykonują wyszukiwania w usługach Exchange Online i SharePoint Online.

3. Konfigurowanie zasad przechowywania dziennika inspekcji. Poza zasadami domyślnymi, które zachowują rekordy inspekcji usług Exchange, SharePoint i Azure AD przez jeden rok, możesz utworzyć dodatkowe zasady przechowywania dziennika inspekcji, aby spełnić wymagania zespołów ds. zabezpieczeń organizacji, it i zgodności.

4. Wyszukaj istotne zdarzenia inspekcji zaawansowanej i inne działania podczas prowadzenia dochodzenia sądowego. Po zakończeniu wykonywania kroków 1 i 2 możesz wyszukać w dzienniku inspekcji zdarzenia zaawansowanej inspekcji i inne działania w ramach dochodzenia sądowego w sprawie naruszonych kont oraz innych rodzajów badań zabezpieczeń lub zgodności.

Aby uzyskać bardziej szczegółowe instrukcje, [zobacz Konfigurowanie inspekcji zaawansowanej](set-up-advanced-audit.md).

## <a name="training"></a>Szkolenia

Szkolenie zespołu ds. bezpieczeństwa, administratorów IT i członków zespołu ds. zgodności w ramach podstawowych funkcji inspekcji podstawowej i inspekcji zaawansowanej może ułatwić organizacji szybkie rozpoczynanie pracy z inspekcją w celu pomocy w badaniach. Microsoft 365 udostępnia następujące zasoby, które pomogą tym użytkownikom w organizacji w rozpoczynaniu inspekcji: Opis funkcji zbierania elektronicznych materiałów dowodowych i [inspekcji w programie Microsoft 365](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
