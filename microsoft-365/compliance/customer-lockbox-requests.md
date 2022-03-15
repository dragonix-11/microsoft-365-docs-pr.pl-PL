---
title: Żądania skrytki klienta
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom: admindeeplinkMAC
description: Dowiedz się więcej o żądaniach skrytki klienta, które pozwalają kontrolować, w jaki sposób inżynier pomocy technicznej firmy Microsoft może uzyskać dostęp do Twoich danych, gdy występuje problem.
ms.openlocfilehash: 532b1b78c40725fa3558768a6b65beda9b8e05b2
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504834"
---
# <a name="customer-lockbox-in-office-365"></a>Skrytka klienta w aplikacji Office 365

Ten artykuł zawiera wskazówki dotyczące wdrażania i konfiguracji skrytki klienta. Skrytka klienta obsługuje żądania dostępu do danych w usługach Exchange Online, SharePoint Online i OneDrive dla Firm. Aby polecić pomoc techniczną dla innych usług, prześlij żądanie w portalu [opinii](https://feedbackportal.microsoft.com).

Aby zobaczyć opcje licencjonowania użytkowników w celu skorzystania z Microsoft 365 zgodności, zobacz wskazówki Microsoft 365 licencjonowania dotyczące zabezpieczeń [& zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

Skrytka klienta zapewnia, że firma Microsoft nie może uzyskać dostępu do zawartości w celu świadczenia usług bez Twojej jawnej zgody. Skrytka klienta wprowadza Cię do procesu przepływu pracy zatwierdzania, który firma Microsoft używa do zapewnienia, że tylko autoryzowane żądania zezwalają na dostęp do Twojej zawartości. Aby dowiedzieć się więcej o procesie przepływu pracy firmy Microsoft, zobacz Zarządzanie [dostępem z uprawnieniami w programie Microsoft 365](privileged-access-management-solution-overview.md).

Czasami inżynierowie firmy Microsoft pomagają rozwiązywać i rozwiązywać problemy z usługą. Zazwyczaj inżynierowie rozsyłają problemy przy użyciu rozbudowanych narzędzi do debugowania i telemetrii, które firma Microsoft ma dla swoich usług. Jednak w niektórych przypadkach uzyskanie dostępu do zawartości przez inżyniera firmy Microsoft wymaga określenia głównej przyczyny i rozwiązania problemu. Skrytka klienta wymaga, aby inżynier zażądał od Ciebie dostępu jako ostatniego kroku przepływu pracy zatwierdzania. Umożliwia ona zatwierdzanie lub odrzucanie żądania organizacji i zapewnianie kontroli dostępu bezpośredniego do zawartości.

### <a name="customer-lockbox-overview-video"></a>Klip wideo z omówieniem skrytki klienta

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>Przepływ pracy Skrytka klienta

Te kroki konspektu typowego przepływu pracy, gdy inżynier firmy Microsoft rozpoczyna żądanie skrytki klienta:

1. Osoba w organizacji ma problem z jego skrzynką pocztową Microsoft 365 pocztowej.

2. Gdy użytkownik rozwiąże problem, ale nie może go rozwiązać, otwiera żądanie pomocy technicznej za pomocą pomocy technicznej firmy Microsoft.

3. Inżynier pomocy technicznej firmy Microsoft przegląda żądanie usługi i ustala, czy należy uzyskać dostęp do dzierżawy organizacji, aby naprawić problem w Exchange Online.

4. Inżynier pomocy technicznej firmy Microsoft loguje się do narzędzia żądania skrytki klienta i składa żądanie dostępu do danych, które zawiera nazwę dzierżawy organizacji, numer żądania usługi i szacowany czas, przez który inżynier potrzebuje dostępu do danych.

5. Gdy kierownik pomocy technicznej firmy Microsoft zatwierdzi żądanie, skrytka klienta wysyła do organizacji wyznaczony osoba zatwierdzająca w wiadomości e-mail z powiadomieniem o oczekującym żądaniu dostępu od firmy Microsoft.

    ![Przykład powiadomienia e-mail skrytki klienta.](../media/CustomerLockbox1.png)

   Każda osoba z przypisaną rolą administratora [dostępu do skrytki](/office365/admin/add-users/about-admin-roles) klienta w aplikacji centrum administracyjne platformy Microsoft 365 może zatwierdzać żądania skrytki klienta.

6. Osoba zatwierdzająca podpisuje się do centrum administracyjne platformy Microsoft 365 i zatwierdza wniosek. Ten krok wyzwala tworzenie rekordu inspekcji dostępnego przez przeszukiwanie dziennika inspekcji. Aby uzyskać więcej informacji, zobacz [Inspekcja żądań skrytki klienta](#auditing-customer-lockbox-requests).

   Jeśli klient odrzuci żądanie lub nie zatwierdzi go w ciągu 12 godzin, wniosek wygasa i nie jest udzielany inżynierowi firmy Microsoft.

   > [!IMPORTANT]
   > Firma Microsoft nie dołącza żadnych linków do powiadomień e-mail skrytki klienta wymagających zalogowania się w Office 365.

7. Gdy osoba zatwierdzająca z organizacji zatwierdzi żądanie, inżynier firmy Microsoft otrzymuje komunikat o zatwierdzeniu, loguje się do dzierżawy w systemie Exchange Online i rozwiązuje problem klienta. Inżynierowie firmy Microsoft mają żądany czas trwania na rozwiązanie problemu, po którym dostęp zostaje automatycznie odwołany.

> [!NOTE]
> W dzienniku inspekcji są rejestrowane wszystkie akcje wykonane przez inżyniera firmy Microsoft. Możesz wyszukiwać i przeglądać te rekordy inspekcji.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>Włączanie i wyłączanie żądań skrytki klienta

Możesz włączyć kontrolki Skrytki klienta w centrum administracyjne platformy Microsoft 365. Po włączeniu skrytki klienta firma Microsoft musi uzyskać zgodę Twojej organizacji przed uzyskaniem dostępu do zawartości Twojej dzierżawy.

1. Za pomocą konta służbowego z przypisaną rolą administratora globalnego lub osoby zatwierdzającej dostęp do **skrytki** klienta przejdź do [https://admin.microsoft.com](https://admin.microsoft.com) strony i zaloguj się.

2. Wybierz **Ustawienia** >  **Org Ustawienia** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Security & Privacy**</a>.

3. Wybierz **pozycję Zabezpieczenia & prywatności**, a następnie wybierz **pozycję Skrytka klienta** w lewej kolumnie. Zaznacz pole **wyboru Wymagaj zatwierdzenia dla wszystkich żądań dostępu** do danych i zapisz zmiany, aby włączyć tę funkcję.

    ![Require approval for Customer Lockbox](../media/CustomerLockbox4-new.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>Zatwierdzanie lub odrzucanie żądania skrytki klienta

1. Za pomocą konta służbowego z przypisaną rolą administratora globalnego lub osoby zatwierdzającej dostęp do **skrytki** klienta przejdź do [https://admin.microsoft.com](https://admin.microsoft.com) strony i zaloguj się.

2. Wybierz **pozycję Pomoc > żądania skrytki klienta**.

    ![Kliknij pozycję Pomoc techniczna, a następnie kliknij pozycję Żądania skrytki klienta.](../media/CustomerLockbox5.png)

    Zostanie wyświetlona lista żądań skrytki klienta.

    ![Lista żądań skrytki klienta.](../media/CustomerLockbox6.png)

3. Wybierz żądanie skrytki klienta, a następnie wybierz pozycję **Zatwierdź** lub **Odmów**.

    ![Zatwierdzanie żądań skrytki klienta.](../media/CustomerLockbox7.png)

    Zostanie wyświetlony komunikat potwierdzający zatwierdzenie żądania skrytki klienta.

    ![Odrzucanie żądań skrytki klienta.](../media/CustomerLockbox8.png)

> [!NOTE]
> Użyj polecenia cmdlet Set-AccessToCustomerDataRequest, aby zatwierdzać, odrzucać lub anulować Microsoft 365 skrytki klienta, które kontrolują dostęp do Twoich danych przez inżynierów pomocy technicznej firmy Microsoft. Aby uzyskać więcej informacji, [zobacz Set-AccessToCustomerDataRequest](/powershell/module/exchange/set-accesstocustomerdatarequest).

## <a name="auditing-customer-lockbox-requests"></a>Inspekcja żądań skrytki klienta

Rekordy inspekcji, które odpowiadają żądaniam skrytki klienta, są rejestrowane w Microsoft 365 inspekcji. Dostęp do tych dzienników można uzyskać za pomocą narzędzia do przeszukiwania [dziennika](search-the-audit-log-in-security-and-compliance.md) inspekcji dostępnego Centrum zgodności platformy Microsoft 365. Działania związane z zaakceptowaniem lub odmową żądania skrytki klienta oraz działaniami wykonywanymi przez inżynierów firmy Microsoft (po zatwierdzeniu żądań dostępu) są również rejestrowane w dzienniku inspekcji. Możesz wyszukiwać i przeglądać te rekordy inspekcji.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>Wyszukiwanie w dzienniku inspekcji działań związanych z żądaniami skrytki klienta

Zanim będzie można używać dziennika inspekcji do śledzenia żądań skrytki klienta, należy wykonać pewne czynności, aby skonfigurować rejestrowanie inspekcji, na przykład przypisać uprawnienia do przeszukiwania dziennika inspekcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie inspekcji podstawowej w programie Microsoft 365](set-up-basic-audit.md). Po ukończeniu konfiguracji utwórz zapytanie wyszukiwania dziennika inspekcji w celu zwrócenia rekordów inspekcji związanych z Skrytka klienta, wykonać następujące czynności:

1. Przejdź do <https://compliance.microsoft.com>.
  
2. Zaloguj się przy użyciu konta z przypisanymi odpowiednimi uprawnieniami do przeszukiwania dziennika inspekcji.

3. W lewym okienku Centrum zgodności wybierz pozycję **Inspekcja**.

    Zostanie **wyświetlona** karta Wyszukiwanie **na stronie** Inspekcja.

    ![Strona przeszukiwania dziennika inspekcji.](../media/auditlogsearch1.png)
  
4. Skonfiguruj następujące kryteria wyszukiwania:

   1. **Data rozpoczęcia** **i Data zakończenia**. Wybierz zakres dat i godzin, aby wyświetlić zdarzenia, które wystąpiły w tym okresie.  

   2. **Działania**. Pozostaw to pole puste, aby wyszukiwanie zwracało rekordy inspekcji dla wszystkich działań. Jest to konieczne w celu zwrócenia wszelkich rekordów inspekcji związanych z żądaniami skrytki klienta i odpowiadającymi im działaniami wykonanymi przez inżynierów firmy Microsoft.

   3. **Użytkownicy**. Pozostaw to pole puste.

   4. **Plik, folder lub witryna**. Pozostaw to pole puste.

5. Kliknij **przycisk** Wyszukaj, aby uruchomić wyszukiwanie z użyciem kryteriów wyszukiwania.

    Wyniki wyszukiwania zostaną wyświetlone po chwili. Do strony będą dodawane kolejne wyniki wyszukiwania do czasu zakończenia wyszukiwania.

6. Kliknij nagłówek w kolumnie **Działanie,** aby posortować wyniki alfabetycznie na podstawie wartości w **kolumnie** Działanie.

7. Przewiń w dół i poszukaj rekordów inspekcji z działaniem **rekordu Set-AccessToCustomerDataRequest**. Rekordy z tym działaniem są powiązane z zatwierdzającą w Twojej organizacji zatwierdzaniem lub odrzucanie żądania skrytki klienta.

8. Możesz również kliknąć nagłówek w kolumnie **Użytkownik** , aby posortować wyniki alfabetycznie według wartości z **kolumny** Użytkownik. Poszukaj wartości operatora **firmy Microsoft**, która wskazuje działania wykonywane przez inżyniera firmy Microsoft w odpowiedzi na zatwierdzone żądanie skrytki klienta. W **kolumnie** Działanie jest wyświetlana akcja wykonana przez inżyniera.

      ![Filtrowanie według "Operatora Microsoft", aby wyświetlić rekordy inspekcji](../media/CustomerLockbox10.png)

9. Na liście wyników kliknij rekord inspekcji, aby go wyświetlić.

### <a name="export-the-audit-log-search-results"></a>Eksportowanie wyników przeszukiwania dziennika inspekcji

Możesz również wyeksportować wyniki przeszukiwania dziennika inspekcji do pliku CSV, a następnie otworzyć ten plik w programie Excel, aby skorzystać z funkcji filtrowania i sortowania, aby ułatwić znajdowanie i wyświetlanie rekordów inspekcji związanych z żądaniem dostępu do skrytki klienta.

Aby wyeksportować rekordy inspekcji, należy wykonać opisane wcześniej czynności w celu przeszukiwania dziennika inspekcji. Po zakończeniu wyszukiwania wybierz pozycję Eksportuj > **Pobierz wszystkie** wyniki u góry strony wyników wyszukiwania. Po zakończeniu procesu eksportowania możesz pobrać plik CSV na komputer lokalny. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Eksportowanie, konfigurowanie i wyświetlanie rekordów dziennika inspekcji](export-view-audit-log-records.md).

Po pobraniu pliku możesz otworzyć go w programie Excel a następnie przefiltrować w kolumnie Operacje, aby wyświetlić rekordy inspekcji dotyczące działań **set-AccessToCustomerDataRequest**. Możesz również filtrować według **kolumny UserIds** (przy użyciu wartości **Operator Microsoft**), aby wyświetlić rekordy inspekcji dotyczące działań wykonanych przez inżynierów firmy Microsoft.

> [!NOTE]
> Podczas wyświetlania rekordów inspekcji w pliku CSV dodatkowe informacje są zawarte w kolumnie **Dane** inspekcji. Informacje w tej kolumnie znajdują się w obiekcie JSON, który zawiera wiele właściwości skonfigurowanych jako *pary właściwość:* wartość rozdzielone przecinkami. Za pomocą funkcji przekształcania JSON w Edytorze dodatku Power Query w programie Excel można podzielić każdą właściwość w obiekcie JSON w kolumnie **Dane** inspekcji na wiele kolumn, dzięki czemu każda właściwość ma własną kolumnę. Ułatwia to interpretowanie tych informacji. Aby uzyskać szczegółowe instrukcje, zobacz [Formatowanie wyeksportowanego dziennika inspekcji za pomocą Edytora dodatku Power Query](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="use-powershell-to-search-and-export-audit-records"></a>Wyszukiwanie i eksportowanie rekordów inspekcji za pomocą programu PowerShell

Alternatywą dla narzędzia do przeszukiwania inspekcji w programie Centrum zgodności platformy Microsoft 365 jest uruchomienie polecenia cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) w programie Exchange Online PowerShell. Jedną z zalet programu PowerShell jest możliwość wyszukiwania konkretnie działań lub działań  wykonywanych przez inżynierów firmy Microsoft dotyczących żądania skrytki klienta w celu wyszukania działań lub działań wykonywanych przez inżynierów firmy Microsoft.

Po [nawiązania połączenia Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) uruchom jedno z następujących poleceń. Zamień symbole zastępcze na określony zakres dat.

#### <a name="search-for-set-accesstocustomerdatarequest-activities"></a>Wyszukiwanie Set-AccessToCustomerDataRequest działań

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -Operations Set-AccessToCustomerDataRequest
```

#### <a name="search-for-activities-performed-by-microsoft-engineers"></a>Wyszukiwanie działań wykonanych przez inżynierów firmy Microsoft

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -UserIds "Microsoft Operator"
```

Aby uzyskać więcej informacji i przykładów, zobacz Wyszukiwanie i eksportowanie rekordów dziennika inspekcji za pomocą programu [PowerShell](export-view-audit-log-records.md#use-powershell-to-search-and-export-audit-log-records).

Podaliśmy również skrypt programu PowerShell, który umożliwia przeszukiwanie dziennika inspekcji i eksportowanie wyników do pliku CSV. Aby uzyskać więcej informacji, zobacz Przeszukiwanie dziennika inspekcji za pomocą skryptu [programu PowerShell](audit-log-search-script.md).

### <a name="audit-record-for-a-customer-lockbox-request"></a>Rekord inspekcji dla żądania skrytki klienta

Gdy osoba w Twojej organizacji zatwierdzi lub zablokuje żądanie skrytki klienta, rekord inspekcji zostanie zarejestrowany w dzienniku inspekcji zawierający następujące informacje.

| Właściwość rekordu inspekcji| Opis|
|:---------- |:----------|
| Data       | Data i godzina zatwierdzenia lub odrzuconia żądania skrytki klienta.
| Adres IP | Adres IP urządzenia zatwierdzającego, który zatwierdził lub odrzucił wniosek. |
| Użytkownik       | Konto usługi jest BOXServiceAccount@\[customerforest.prod.outlook.com\].            |
| Działanie   | Set-AccessToCustomerDataRequest; jest to działanie inspekcji rejestrowane po zatwierdzeniu lub odmówiniu żądania skrytki klienta.                                |
| Element       | Identyfikator Guid żądania skrytki klienta                             |

Poniższy zrzut ekranu przedstawia przykład rekordu inspekcji, który odpowiada zatwierdzonemu żądaniu skrytki klienta. Jeśli żądanie skrytki klienta zostanie odrzucone, wartością parametru **ApprovalDecision** będzie Deny **(Odmów**).

![Rekord inspekcji zatwierdzonego żądania skrytki klienta.](../media/CustomerLockbox9.png)

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>Rekord inspekcji dla akcji wykonanej przez inżyniera firmy Microsoft

Działania wykonywane przez inżyniera firmy Microsoft po zatwierdzeniu żądania skrytki klienta (co może spowodować uzyskanie dostępu do zawartości klienta) są rejestrowane w dzienniku inspekcji. Rekordy te zawierają następujące informacje.

| Właściwość rekordu inspekcji| Opis|
|:---------- |:----------|
| Data       | Data wykonania akcji. Czas wykonania tej czynności zostanie ujmowany w ciągu 4 godzin od zatwierdzenia żądania skrytki klienta.              |
| Adres IP | Adres IP używanego urządzenia inżyniera firmy Microsoft. |
| Użytkownik       | Operator firmy Microsoft; ta wartość wskazuje, że rekord jest powiązany z żądaniem skrytki klienta.                                  |
| Działanie   | Nazwa działania wykonywanego przez inżyniera firmy Microsoft.|
| Element       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>Często zadawane pytania

#### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>Do Microsoft 365 klienta mają zastosowanie usługi Customer Lockbox?

Skrytka klienta jest obecnie obsługiwana w usługach Exchange Online, SharePoint Online i OneDrive dla Firm.

#### <a name="is-customer-lockbox-available-to-all-customers"></a>Czy Skrytka klienta jest dostępna dla wszystkich klientów?

Skrytka klienta jest dołączona do subskrypcji usługi Microsoft 365 lub Office 365 E5 i może być dodawana do innych planów za pomocą subskrypcji usługi Information Protection and Compliance lub dodatku Advanced Compliance. Aby [uzyskać więcej informacji, zobacz](https://products.office.com/business/office-365-enterprise-e5-business-software) Plany i ceny.

#### <a name="what-is-customer-content"></a>Co to jest zawartość dla klientów?

Zawartość klienta to dane tworzone przez użytkowników usług i Microsoft 365 aplikacji. Oto przykłady zawartości dla klientów:

- Treść wiadomości e-mail lub załączniki wiadomości e-mail

- SharePoint zawartości witryny

- Informacje w treści SharePoint pliku

- Skype dla firm pliku prezentacji

- Wiadomości błyskawiczne lub konwersacje głosowe

- Obiekty blob lub dane magazynu strukturalnego wygenerowane przez klienta (na SQL Kontenery)

- Informacje o zabezpieczeniach należących do klienta (na przykład certyfikaty, klucze szyfrowania i hasła)

- Wnioski i wszystkie kolejne wnioski, jeśli zawartość klienta pozostanie

Aby uzyskać więcej informacji na temat zawartości Office 365 klientów, zobacz Centrum Office 365 [zaufania](https://products.office.com/business/office-365-trust-center-privacy/).

#### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>KtoTo się z prośbą o dostęp do mojej zawartości?

Administratorzy globalni i każda osoba, która przypisała rolę administratora dostępu do skrytki klienta, jest powiadamiana o tym. Są to również ci sami użytkownicy, którzy mogą zatwierdzać żądania skrytki klienta.

#### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>KtoTo zatwierdzić lub odrzucić te wnioski w mojej organizacji?

Administratorzy globalni i każda osoba z przypisaną rolą administratora dostępu do skrytki klienta może zatwierdzać żądania skrytki klienta. Klienci kontrolują te przypisania ról w swoich organizacjach.

#### <a name="how-do-i-opt-in-to-customer-lockbox"></a>Jak wybrać opcję skrytki klienta?

Administrator globalny może włączyć i skonfigurować Skrytkę klienta w Microsoft 365 lub <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365</a>.

#### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>Jeśli zatwierdźę żądanie skrytki klienta, co może zrobić inżynier i jak będę wiedzieć, co zrobił inżynier firmy Microsoft?

Po zatwierdzeniu żądania skrytki klienta inżynier firmy Microsoft udzielił tych niezbędnych uprawnień do uzyskiwania dostępu do zawartości klienta za pomocą wstępnie zatwierdzonych żądań cmdlet. Działania podejmowane przez inżynierów firmy Microsoft w odpowiedzi na żądania skrytki klienta są rejestrowane i dostępne w dzienniku inspekcji w Centrum zabezpieczeń & zgodności.

#### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>Skąd wiadomo, że firma Microsoft jest w trakcie procesu zatwierdzania?

Możesz odsyłać do powiadomień e-mail o zatwierdzeniach wysyłanych do administratorów i osób zatwierdzających w Twojej organizacji z historią żądań Skrytki klienta [w centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

Skrytka klienta jest uwzględniona w najnowszym [raporcie inspekcji SOC 1 SSAE 16](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports). Najnowsze raporty można znaleźć w Portalu zaufania [usług firmy Microsoft](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports).

#### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>Czy firma Microsoft może zmodyfikować listę osób zatwierdzających dla mojej dzierżawy? Jeśli nie, jak to jest blokowane?

Tylko administrator globalny w Twojej organizacji może określać, kto może zatwierdzać żądania skrytki klienta. Oznacza to, że tylko członkowie grupy administratorów globalnych w organizacji Azure Active Directory mogą określać, kto może zatwierdzać żądania. Członkostwo w grupie administratorów globalnych w programie Azure Active Directory zarządzane jest tylko przez Twoją organizację.

#### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>Co zrobić, jeśli potrzebuję więcej informacji na temat wniosku o dostęp do zawartości w celu jego zatwierdzenia?

Każde żądanie skrytki klienta zawiera Microsoft 365 numeru zgłoszenia serwisowego. Aby uzyskać więcej informacji na temat zgłoszenia, możesz skontaktować się z pomocą techniczną firmy Microsoft i uzyskać więcej informacji na temat tego numeru usługi.

#### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>Po zatwierdzeniu żądania skrytki klienta, jak długo są ważne uprawnienia?

Obecnie maksymalny okres uprawnień dostępu przyznanych inżynierowi firmy Microsoft wynosi 4 godziny. Inżynier firmy Microsoft może również poprosić o krótszy okres.

#### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>Jak mogę uzyskać historię wszystkich żądań skrytki klienta?

Wszystkie żądania skrytki klienta są przeglądane w [centrum administracyjne platformy Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

#### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>Jak skorelować żądania dostępu do zawartości z powiązanymi dziennikami inspekcji?

Kanał aktywności Centrum zgodności zawiera działania dziennika skrytki klienta. Klienci mogą odsyłać odwołania do działań dziennika skrytki klienta z kanału aktywności w odniesieniu do obierania wiadomości e-mail.

#### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>Co się dzieje, gdy klient nie odpowiada na żądanie skrytki klienta?

Żądania skrytki klienta mają domyślny czas trwania 12 godzin. Jeśli nie odpowiesz na żądanie w ciągu 12 godzin, wygaśnie.

#### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>Co firma Microsoft robi, gdy klient odrzuca żądanie skrytki klienta?

Jeśli klient odrzuci żądanie skrytki klienta, nie ma dostępu do zawartości klienta. Jeśli użytkownik w Twojej organizacji nadal występuje problem z usługą wymagający od firmy Microsoft uzyskiwania dostępu do zawartości klienta w celu rozwiązania tego problemu, problem z usługą może być nadal występował, a firma Microsoft poinformuje o tym użytkownika.

#### <a name="how-do-i-set-up-alerts-whenever-a-request-has-been-approved"></a>Jak skonfigurować alerty po zatwierdzeniu wniosku?

Nie ma wbudowanej opcji powiadamiania administratorów. Jednak administratorzy mogą skonfigurować alerty za pomocą programu [Microsoft Defender dla aplikacji w chmurze](/cloud-app-security/getting-started-with-cloud-app-security#to-create-policies).

#### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>Czy Skrytka klienta chroni przed żądaniami danych od organów ścigania lub innych firm?

L.p. Firma Microsoft poważnie zwraca się do innych podmiotów o dane klientów. Firma Microsoft, jako usługodawca, zawsze wspiera prywatność danych klientów. W przypadku otrzymania wezwania firma Microsoft zawsze próbuje przekierować dane innej firmy do klienta w celu uzyskania tych informacji. (Przeczytaj blog Brada Smitha: [Ochrona danych klientów przed odłogiem rządowym](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). Okresowo publikujemy [szczegółowe informacje na temat](https://www.microsoft.com/corporate-responsibility/lerr) próśb firmy Microsoft o egzekwowanie prawa.

Aby uzyskać [więcej](https://www.microsoft.com/trustcenter/default.aspx) informacji, zobacz Centrum zaufania firmy Microsoft dotyczące żądań danych innych firm i sekcję "Ujawnianie danych klientów" w Warunkach usług [online](https://www.microsoft.com/Licensing/product-licensing/products.aspx) .

#### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>Jak firma Microsoft gwarantuje, że członek jego personelu nie będzie miał dostępu do zawartości klientów w Office 365 aplikacjach?

Firma Microsoft wdraża rozbudowane działania naprawcze za pośrednictwem systemów kontroli dostępu oraz środki wykrywające w celu zidentyfikowania i rozwiązania problemów mających na celu obejście tych systemów kontroli dostępu. Microsoft 365 to zasady o jak najmniejszych uprawnieniach i dostępie w czasie rzeczywistym. Dlatego żaden pracownik firmy Microsoft nie ma uprawnienia do ciągłego uzyskiwania dostępu do zawartości klienta. W przypadku uzyskania uprawnienia jest ono udzielone na ograniczony czas trwania. 

Microsoft 365 korzysta z systemu kontroli dostępu o nazwie *Skrytka* do przetwarzania żądań uprawnień, które przyznają możliwość wykonywania funkcji operacyjnych i administracyjnych w ramach usługi. Operator musi poprosić o dostęp do zawartości klienta przy użyciu skrytki, co następnie wymaga od drugiej osoby podjęcia działania w związku z żądaniem (na przykład zatwierdzić je) przed uzyskaniem dostępu. Ta druga osoba nie może być osobą żądawcą i musi zostać wyznaczona do zatwierdzania dostępu do zawartości klienta. Tylko w przypadku zatwierdzenia żądania operator uzyskuje tymczasowy dostęp do zawartości klienta. Po wygaśnięciu okresu podwyższenia blokada odwołuje dostęp.

Więcej informacji na [temat](https://www.microsoft.com/licensing/product-licensing/products) ogólnych rozwiązań bezpieczeństwa firmy Microsoft można znaleźć w Warunkach usług online.

#### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>W jakich okolicznościach inżynierowie firmy Microsoft potrzebują dostępu do mojej zawartości?

Najczęstszym scenariuszem, w którym inżynierowie firmy Microsoft potrzebują dostępu do zawartości klienta, jest zgłoszenie do pomocy technicznej wymagającej dostępu do rozwiązywania problemów. Podstawową zasadą Microsoft 365 jest to, że usługa działa bez dostępu firmy Microsoft do zawartości klientów. Niemal wszystkie operacje serwisowe wykonywane przez firmę Microsoft są w pełni zautomatyzowane i angażowane przez człowieka są ściśle kontrolowane i wyeksstrowane z dala od treści klienta. Celem tego Microsoft 365 dostępu do zawartości dla klientów w celu obsługi usługi nie jest konieczne, dopóki klient nie zatwierdzi konkretnego żądania dostępu firmy Microsoft.

#### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>Mam już myśl, że moje dane są bezpieczne za pomocą chmury firmy Microsoft, więc dlaczego potrzebuję skrytki klienta?

Skrytka klienta zapewnia dodatkową warstwę kontroli, oferując klientom możliwość nadawać klientom jawne autoryzacje dostępu do operacji usługi. Poprzez pokazanie, że procedury są stosowane w celu uzyskania jawnego autoryzacji dostępu do danych, skrytka klienta pomaga również klientom w spełnianiu określonych zobowiązań dotyczących zgodności, takich jak HIPAA i FEDRAMP.
