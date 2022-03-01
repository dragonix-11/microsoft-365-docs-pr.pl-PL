---
title: Tworzenie niestandardowych reguł wykrywania i zarządzanie nimi w aplikacji Microsoft 365 Defender
description: Dowiedz się, jak tworzyć niestandardowe reguły wykrywania i zarządzać nimi na podstawie zaawansowanych zapytań myśliwnych.
keywords: zaawansowane szukanie, szukanie zagrożeń, cyberzagrożenia, Microsoft 365 Defender, microsoft 365, m365, wyszukiwanie, zapytanie, telemetria, wykrywanie niestandardowe, reguły, schemat, kusto, RBAC, uprawnienia, Program Microsoft Defender for Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 473d58cde13f1f776c31184b2b50e74e23810b22
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2022
ms.locfileid: "63014673"
---
# <a name="create-and-manage-custom-detections-rules"></a>Tworzenie reguł wykrywania niestandardowego i zarządzanie nimi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender
- Ochrona punktu końcowego w usłudze Microsoft Defender

Niestandardowe reguły wykrywania to reguły, które można projektować i poprawiać przy użyciu [zaawansowanych zapytań myśliwnych](advanced-hunting-overview.md) . Te reguły umożliwiają aktywne monitorowanie różnych zdarzeń i stanów systemu, w tym podejrzewanych naruszeń zabezpieczeń i nieprawidłowo skonfigurowanych punktów końcowych. Można je tak skonfigurować, aby były uruchamiane w regularnych interwałach, generując alerty i uruchamiając akcje reagowania, gdy tylko zostaną one zes względu na dopasowania.

## <a name="required-permissions-for-managing-custom-detections"></a>Wymagane uprawnienia do zarządzania wykrywaniami niestandardowymi

Aby zarządzać wykrywaniami niestandardowymi, musisz mieć przypisaną jedną z tych ról:

- **Administrator zabezpieczeń** — użytkownicy z tą rolą [Azure Active Directory mogą](/azure/active-directory/roles/permissions-reference#security-administrator) zarządzać ustawieniami zabezpieczeń w portalu usługi Microsoft 365 Defender oraz innych portalach i usługach.

- **Operator zabezpieczeń** — użytkownicy z tą rolą [Azure Active Directory](/azure/active-directory/roles/permissions-reference#security-operator) mogą zarządzać alertami i mieć dostęp globalny tylko do odczytu do funkcji związanych z zabezpieczeniami, w tym do wszystkich informacji w portalu Microsoft 365 Defender-mail. Ta rola jest wystarczająca do zarządzania wykrywaniami niestandardowymi tylko wtedy, gdy w uchwale programu Microsoft Defender dla punktu końcowego jest wyłączona kontrola dostępu oparta na rolach. Jeśli masz skonfigurowany RBAC, potrzebujesz również uprawnienia do zarządzania ustawieniami zabezpieczeń dla programu Defender dla punktu końcowego.

Możesz także zarządzać niestandardowymi wykrywaniami, które dotyczą danych z określonych Microsoft 365 Defender, jeśli masz do nich uprawnienia. Jeśli masz uprawnienia do zarządzania tylko dla Microsoft 365 Defender dla Office, możesz tworzyć wykrywanie niestandardowe, używając tabel, `Email` ale nie `Identity` tabel.  

Aby zarządzać wymaganymi uprawnieniami, **administrator globalny może** :

- Przypisz **rolę administratora zabezpieczeń** lub operatora zabezpieczeń w **obszarze** [centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com/) **RolesSecurity** >  **admin**.
- Sprawdź ustawienia RBAC dla programu Microsoft Defender pod polem [Endpoint Microsoft 365 Defender](https://security.microsoft.com/) w **Ustawienia** >  **PermissionsRoles** > . Wybierz odpowiednią rolę, aby przypisać **uprawnienia do zarządzania ustawieniami** zabezpieczeń.

> [!NOTE]
> Aby zarządzać niestandardowymi wykrywaniami, **operatory zabezpieczeń będą** potrzebować uprawnienia do zarządzania ustawieniami zabezpieczeń w programie Microsoft Defender for Endpoint, jeśli jest włączona RBAC.

## <a name="create-a-custom-detection-rule"></a>Tworzenie reguły wykrywania niestandardowego
### <a name="1-prepare-the-query"></a>1. Przygotowywanie zapytania.

W portalu Microsoft 365 Defender przejdź do tematu **Zaawansowane** szukanie i wybierz istniejące zapytanie lub utwórz nowe zapytanie. Podczas używania nowego zapytania uruchom je, aby zidentyfikować błędy i zrozumieć możliwe wyniki.

>[!IMPORTANT]
>Aby zapobiec zwracaniu zbyt wielu alertów przez usługę, każda reguła jest ograniczona do generowania tylko 100 alertów przy każdym jej uruchamianiu. Przed utworzeniem reguły dostosuj zapytanie, aby uniknąć alertów o normalnych, dniowych działaniach.


#### <a name="required-columns-in-the-query-results"></a>Kolumny wymagane w wynikach zapytania
Aby utworzyć regułę wykrywania niestandardowego, zapytanie musi zwrócić następujące kolumny:

- `Timestamp`— służy do ustawienia sygnatury czasowej wygenerowanych alertów
- `ReportId`— umożliwia wyświetlanie odnośników dla oryginalnych rekordów
- Jedna z następujących kolumn identyfikująca określone urządzenia, użytkowników lub skrzynki pocztowe:
    - `DeviceId`
    - `DeviceName`
    - `RemoteDeviceName`
    - `RecipientEmailAddress`
    - `SenderFromAddress` (nadawca koperty Return-Path adres e-mail)
    - `SenderMailFromAddress` (adres nadawcy wyświetlany przez klienta poczty e-mail)
    - `RecipientObjectId`
    - `AccountObjectId`
    - `AccountSid`
    - `AccountUpn`
    - `InitiatingProcessAccountSid`
    - `InitiatingProcessAccountUpn`
    - `InitiatingProcessAccountObjectId`

>[!NOTE]
>Obsługa dodatkowych jednostek zostanie dodana, gdy nowe tabele zostaną dodane do [zaawansowanego schematu myśliwskiej](advanced-hunting-schema-tables.md).

Proste zapytania, takie jak te, które `project` `summarize` nie używają operatora do dostosowywania lub agregowania wyników, zwykle zwracają te wspólne kolumny.

Istnieją różne sposoby zapewnienia, że bardziej złożone zapytania zwracają te kolumny. Jeśli na przykład `DeviceId`wolisz agregować i policzyć według encji w kolumnie takiej jak , `Timestamp` `ReportId` nadal możesz ją zwrócić i uzyskać ją z ostatniego wydarzenia obejmującego każde unikatowe `DeviceId`.


> [!IMPORTANT]
> Unikaj filtrowania niestandardowych wykrywania przy użyciu kolumny `Timestamp` . Dane używane do wykrywania niestandardowego są wstępnie filtrowane według częstotliwości wykrywania.


Poniższe przykładowe zapytanie zlicza unikatowe urządzenia () z`DeviceId` wykrywaniem oprogramowania antywirusowego i używa tej liczby do znalezienia tylko urządzeń z więcej niż pięcioma wykryciami. Aby zwrócić najpóźniejszą `Timestamp` wartość, a odpowiadający jej `ReportId`operator , `summarize` jest używany operator z funkcją `arg_max` .

```kusto
DeviceEvents
| where ingestion_time() > ago(1d)
| where ActionType == "AntivirusDetection"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| where count_ > 5
```

> [!TIP]
> Aby uzyskać lepszą wydajność zapytania, ustaw filtr czasu, który będzie odpowiadać zamierzonej częstotliwości uruchamiania reguły. Ponieważ najmniej częste uruchamianie jest _co 24 godziny_, filtrowanie za przeszły dzień obejmie wszystkie nowe dane.

### <a name="2-create-new-rule-and-provide-alert-details"></a>2. Utwórz nową regułę i podaj szczegóły alertu.

Przy użyciu zapytania w edytorze zapytań wybierz pozycję **Utwórz regułę wykrywania** i określ następujące szczegóły alertu:

- **Nazwa wykrywania** — nazwa reguły wykrywania; powinny być unikatowe
- **Częstotliwość** — interwał uruchamiania zapytania i wykonywania akcji. [Zobacz dodatkowe wskazówki poniżej](#rule-frequency)
- **Tytuł alertu** — tytuł wyświetlany z alertami wyzwolony przez regułę; powinny być unikatowe
- **Ważność** — potencjalne ryzyko składnika lub działania wskazanego przez regułę
- **Kategoria** — składnik lub działanie zagrożeń określone przez regułę
- **MiTRE ATT&CK —** jedna lub więcej technik ataków zidentyfikowanych przez regułę zgodnie z dokumentacją w dokumencie [MITRE ATT&CK](https://attack.mitre.org/). Ta sekcja jest ukryta dla określonych kategorii alertów, takich jak złośliwe oprogramowanie, oprogramowanie wymuszające okup, podejrzane działania i niechciane oprogramowanie
- **Opis** — więcej informacji o składniku lub działaniu zidentyfikowanym przez regułę 
- **Zalecane działania** — dodatkowe działania, które mogą być podejmowane przez inne odpowiedzi w odpowiedzi na alert

#### <a name="rule-frequency"></a>Częstotliwość stosowania reguł
Po zapisaniu nowej reguły jest ona uruchamiana i sprawdzana podejmuje dopasowania z ostatnich 30 dni. Reguła będzie ponownie uruchamiana w stałych odstępach czasu, stosując czas trwania wyszukiwania na podstawie częstotliwości, która zostanie przez Ciebie wybrać:

- **Każda 24 godziny** — działa co 24 godziny, sprawdzając dane z ostatnich 30 dni
- **Co 12 godzin** — działa co 12 godzin, sprawdzając dane z ostatnich 24 godzin
- **Co 3 godziny** — działa co 3 godziny, sprawdzając dane z ostatnich 6 godzin
- **Co godzinę** — działa co godzinę, sprawdzając dane z ostatnich 2 godzin

Podczas edytowania reguły zmiany zostaną uruchomione w czasie następnego uruchomienia zaplanowanym zgodnie z ustawioną częstotliwością.



>[!TIP]
> Dopasuj filtry czasu w zapytaniu do czasu trwania wyszukiwania. Wyniki, które nie znajdują się w czasie trwania wyszukiwania, są ignorowane.  

Wybierz częstotliwość, która jest dosyć ściśle monitorowana. Zastanów się, czy Twoja organizacja może odpowiadać na alerty.

### <a name="3-choose-the-impacted-entities"></a>3. Wybierz jednostki, których to wpływ.
Zidentyfikuj kolumny w wynikach zapytania, w których oczekujesz znalezienia głównej jednostki, której dotyczy problem lub na które ma to wpływ. Zapytanie może na przykład zwracać adresy nadawcy (`SenderFromAddress` lub `SenderMailFromAddress`) i adresata (`RecipientEmailAddress`). Określenie, która z tych kolumn reprezentuje główną jednostkę, której dotyczy ten wpływ, ułatwia agregowanie odpowiednich alertów, skorelowanych zdarzeń i docelowych działań reakcji.

Możesz wybrać tylko jedną kolumnę dla każdego typu encji (skrzynka pocztowa, użytkownik lub urządzenie). Kolumn, które nie są zwracane przez zapytanie, nie można wybrać.

### <a name="4-specify-actions"></a>4. Określanie akcji.
Reguła wykrywania niestandardowego może automatycznie podjąć działania na urządzeniach, plikach lub użytkownikach zwracanych przez zapytanie.

#### <a name="actions-on-devices"></a>Akcje na urządzeniach
Te akcje są stosowane do urządzeń w `DeviceId` kolumnie wyników zapytania:
- **Wyizoluj** urządzenie — używa programu Microsoft Defender for Endpoint w celu zastosowania pełnej izolacji sieci, uniemożliwiając urządzeniu połączenie się z dowolną aplikacją lub usługą. [Dowiedz się więcej o programie Microsoft Defender w celu izolacji komputera punktu końcowego](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-devices-from-the-network)
- **Zbierz pakiet badania** — zbiera informacje o urządzeniu w pliku ZIP. [Dowiedz się więcej o pakiecie badania programu Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices)
- **Uruchamianie skanowania antywirusowego** — wykonuje pełne Program antywirusowy Windows Defender skanowania na urządzeniu
- **Inicjowanie** badania — inicjuje [zautomatyzowane badanie](m365d-autoir.md) urządzenia
- **Ogranicz uruchamianie aplikacji** — ustawia ograniczenia na urządzeniu, aby zezwolić na uruchamianie tylko plików podpisanych za pomocą certyfikatu wydanego przez firmę Microsoft. [Dowiedz się więcej o ograniczeniach aplikacji w programie Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/respond-machine-alerts#restrict-app-execution)

#### <a name="actions-on-files"></a>Akcje dotyczące plików
 Jeśli ta opcja jest zaznaczona, możesz `SHA1`zastosować akcję Kwarantanna pliku do plików w , `InitiatingProcessSHA1`, `SHA256`lub kolumnie `InitiatingProcessSHA256` wyników zapytania. Ta akcja spowoduje usunięcie pliku z jego bieżącej lokalizacji i umieszczenie jego kopii w kwarantannie.

#### <a name="actions-on-users"></a>Akcje dotyczące użytkowników
Jeśli ta **opcja jest** zaznaczona, oznaczanie użytkownika jako naruszonego jest podejmowane na użytkownikach w `AccountObjectId`kolumnie , `InitiatingProcessAccountObjectId`lub w `RecipientObjectId` kolumnie wyników zapytania. Ta akcja ustawia poziom ryzyka użytkowników na "wysoki" w Azure Active Directory, co powoduje wyzwolenie odpowiednich [zasad ochrony tożsamości](/azure/active-directory/identity-protection/overview-identity-protection).

> [!NOTE]
> Akcja zezwalania lub blokowania dla niestandardowych reguł wykrywania nie jest obecnie obsługiwana w Microsoft 365 Defender.

### <a name="5-set-the-rule-scope"></a>5. Ustawianie zakresu reguły.
Ustaw zakres, aby określić, które urządzenia są objęte regułą. Ten zakres wpływa na reguły, które sprawdzają urządzenia i nie mają wpływu na reguły, które sprawdzają tylko skrzynki pocztowe, konta użytkowników i tożsamości.

Ustawiając zakres, możesz wybrać:

- Wszystkie urządzenia
- Określone grupy urządzeń

Zapytanie będą dotyczyć tylko danych z urządzeń, których dotyczy kwerenda. Ponadto akcje będą podejmowane tylko na tych urządzeniach.

### <a name="6-review-and-turn-on-the-rule"></a>6. Przejrzyj i włącz regułę.
Po przejrzeniu reguły wybierz pozycję **Utwórz** , aby ją zapisać. Reguła wykrywania niestandardowego zostanie uruchomiona natychmiast. Jest ono uruchamiane ponownie na podstawie skonfigurowanej częstotliwości sprawdzania dopasowania, generowania alertów i podjęcia działań dotyczących odpowiedzi.


>[!Important] 
>Wykrywanie niestandardowe należy regularnie sprawdzać pod względem wydajności i skuteczności. Aby upewnić się, że są tworzyne wykrywanie wyzwalanie prawdziwych alertów, po pewnym czasie należy przejrzeć istniejące wykrywanie niestandardowe, korzystając z procedury opisanej w tece Zarządzanie istniejącymi niestandardowymi regułami [wykrywania](#manage-existing-custom-detection-rules). <br>  
Możesz zachować kontrolę nad szerokim i specyficznym zakresem niestandardowych wykrywania, dzięki czemu wszelkie alerty fałszowe generowane przez wykrywanie niestandardowe mogą wskazywać na konieczność modyfikowania określonych parametrów reguł.


## <a name="manage-existing-custom-detection-rules"></a>Zarządzanie istniejącymi regułami wykrywania niestandardowego
Możesz wyświetlić listę istniejących reguł wykrywania niestandardowego, sprawdzić ich poprzednie uruchomienia i sprawdzić wyzwolone przez nie alerty. Regułę można także uruchomić na żądanie i zmodyfikować.

>[!TIP]
> Alerty podniesione przez wykrywanie niestandardowe są dostępne za pośrednictwem alertów i interfejsów API zdarzeń. Aby uzyskać więcej informacji, zobacz [Obsługiwane Microsoft 365 Defender API](api-supported.md).

### <a name="view-existing-rules"></a>Wyświetlanie istniejących reguł

Aby wyświetlić wszystkie istniejące reguły wykrywania niestandardowego, przejdź do **strony Reguły wykrywania w aplikacji** **HuntingCustom** > . Na stronie są podane wszystkie reguły z następującymi informacjami o uruchomieniu:

- **Ostatnie uruchomienie —** gdy reguła została ostatnio uruchamiana w celu sprawdzenia, czy kwerendy są dopasowania i generują alerty
- **Stan ostatniego uruchomienia —** czy reguła została pomyślnie uruchomiono
- **Następne uruchomienie** — następne zaplanowane uruchomienie
- **Stan** — czy reguła została włączona, czy wyłączona

### <a name="view-rule-details-modify-rule-and-run-rule"></a>Wyświetlanie szczegółów reguły, modyfikowanie reguły i uruchamianie reguły

Aby wyświetlić pełne informacje na temat niestandardowej reguły wykrywania, przejdź do **strony Reguły wykrywania w** aplikacji **HuntingCustom** > , a następnie wybierz jej nazwę. Następnie możesz wyświetlić ogólne informacje dotyczące reguły, w tym informacje o stanie jej uruchomienia i zakresie. Strona zawiera również listę wyzwalanych alertów i akcji.

![Strona szczegółów reguły wykrywania niestandardowego.](../../media/custom-detect-rules-view.png)<br>
*Szczegóły reguły wykrywania niestandardowego*

Na tej stronie możesz również podjąć następujące działania dotyczące reguły:

- **Uruchom** — uruchom regułę natychmiast. Powoduje to również zresetowanie interwału następnego uruchomienia.
- **Edytowanie** — modyfikowanie reguły bez modyfikowania zapytania
- **Modyfikowanie zapytania** — edytowanie zapytania podczas wyszukiwania zaawansowanego
-  /  Włącz **Wyłączanie —** włączanie lub zatrzymywanie uruchamiania reguły
- **Usuwanie** — wyłączanie reguły i jej usuwanie

### <a name="view-and-manage-triggered-alerts"></a>Wyświetlanie alertów wyzwalanych i zarządzanie nimi

Na ekranie szczegółów reguły (**HuntingCustom** >  **detections** > **[Rule name]**) przejdź do tematu Alerty wyzwalane **, która** zawiera listę alertów wygenerowanych na podstawie dopasowania do reguły. Wybierz alert, aby wyświetlić szczegółowe informacje na jego temat i podjąć następujące działania:

- Zarządzaj alertem, ustawiając jego stan i klasyfikację (alert prawda lub fałsz)
- Łączenie alertu z zdarzeniem
- Uruchom zapytanie, które wyzwoliło alert podczas wyszukiwania zaawansowanego

### <a name="review-actions"></a>Przejrzyj akcje
Na ekranie szczegółów reguły (**HuntingCustom** >  **detections** > **[Rule name]**) przejdź do części Akcje wyzwalane **, która** zawiera listę akcji podjętych na podstawie dopasowania do reguły.

>[!TIP]
>Aby szybko wyświetlić informacje i podjąć działania dotyczące elementu w tabeli, użyj kolumny zaznaczenia [&#10003;] po lewej stronie tabeli.

>[!NOTE]
>Niektóre kolumny w tym artykule mogą nie być dostępne w programie Microsoft Defender for Endpoint. [Włącz Microsoft 365 Defender](m365d-enable.md), aby poszukać zagrożeń przy użyciu większej liczby źródeł danych. Możesz przenieść zaawansowane przepływy pracy wyszukiwania z programu Microsoft Defender for Endpoint do programu Microsoft 365 Defender, korzystając z procedury migrowania zaawansowanych zapytań myśliwnych z programu [Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md).

## <a name="see-also"></a>Zobacz też
- [Wykrywanie niestandardowe — omówienie](custom-detections-overview.md)
- [Omówienie zaawansowanego wyszukiwania](advanced-hunting-overview.md)
- [Poznaj zaawansowany język zapytań myśliwski](advanced-hunting-query-language.md)
- [Migrowanie zaawansowanych zapytań myśliwnych z programu Microsoft Defender dla punktu końcowego](advanced-hunting-migrate-from-mde.md)
