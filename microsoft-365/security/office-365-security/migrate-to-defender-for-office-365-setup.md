---
title: 'Migrowanie do Ochrona usługi Office 365 w usłudze Microsoft Defender Faza 2: Konfiguracja'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: migrationguides
description: Wykonaj kroki, aby rozpocząć migrację z usługi ochrony lub urządzenia innej firmy w celu Ochrona usługi Office 365 w usłudze Microsoft Defender ochrony.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 34e975be9a937177706fd7db6605d2ef25edcad3
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043550"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Migrowanie do Ochrona usługi Office 365 w usłudze Microsoft Defender — faza 2: konfiguracja

**Dotyczy:**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)

<br>

|[![Faza 1. Przygotowanie.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Faza 1. Przygotowanie](migrate-to-defender-for-office-365-prepare.md)|![Faza 2. Konfigurowanie.](../../media/phase-diagrams/setup.png) <br> Faza 2. Konfiguracja|[![Faza 3. Dołączanie.](../../media/phase-diagrams/onboard.png#lightbox)](migrate-to-defender-for-office-365-onboard.md) <br> [Faza 3. Dołączenie](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Jesteś tutaj!*||

Witamy w **fazie 2: Konfigurowanie** **[migracji do Ochrona usługi Office 365 w usłudze Microsoft Defender](migrate-to-defender-for-office-365.md#the-migration-process)**! Ta faza migracji obejmuje następujące kroki:

1. [Tworzenie grup dystrybucyjnych dla użytkowników pilotażowych](#step-1-create-distribution-groups-for-pilot-users)
2. [Konfigurowanie przesyłania przez użytkownika na potrzeby raportowania komunikatów użytkowników](#step-2-configure-user-submission-for-user-message-reporting)
3. [Obsługa lub tworzenie reguły przepływu poczty SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Konfigurowanie rozszerzonego filtrowania dla łączników](#step-4-configure-enhanced-filtering-for-connectors)
5. [Tworzenie zasad ochrony pilotażowej](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>Krok 1. Tworzenie grup dystrybucyjnych dla użytkowników pilotażowych

Grupy dystrybucyjne są wymagane w Microsoft 365 dla następujących aspektów migracji:

- **Wyjątki dla reguły przepływu poczty SCL=-1**: Chcesz, aby użytkownicy pilotażowi uzyskali pełny efekt ochrony Ochrona usługi Office 365 w usłudze Defender, dlatego ich przychodzące wiadomości muszą być skanowane przez Ochrona usługi Office 365 w usłudze Defender. Można to zrobić, definiując użytkowników pilotażowych w odpowiednich grupach dystrybucyjnych w Microsoft 365 i konfigurując te grupy jako wyjątki od reguły przepływu poczty SCL=-1.

  Jak opisano w kroku [2 dołączania: (opcjonalnie) Wykluczenie użytkowników pilotażowych z filtrowania według istniejącej usługi ochrony](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service), należy rozważyć wykluczenie tych samych użytkowników pilotażowych ze skanowania przez istniejącą usługę ochrony. Wyeliminowanie możliwości filtrowania według istniejącej usługi ochrony i polegania wyłącznie na Ochrona usługi Office 365 w usłudze Defender jest najlepszą i najbliższą reprezentacją tego, co stanie się po zakończeniu migracji.

- **Testowanie określonych funkcji ochrony Ochrona usługi Office 365 w usłudze Defender**: nawet w przypadku użytkowników pilotażowych nie chcesz włączać wszystkiego jednocześnie. Zastosowanie podejścia etapowego dla funkcji ochrony, które są dostępne dla użytkowników pilotażowych, znacznie ułatwi rozwiązywanie problemów i dostosowywanie. Mając to na uwadze, zalecamy następujące grupy dystrybucji:
  - **Grupa pilotażowa Sejf Attachments**: Na przykład **MDOPilot\_SafeAttachments**
  - **Grupa pilotażowa Sejf Links**: na przykład **MDOPilot\_SafeLinks**
  - **Grupa pilotażowa dotycząca standardowych ustawień zasad ochrony przed spamem i wyłudzaniem informacji**: na przykład **MDOPilot\_SpamPhish\_Standard**
  - **Grupa pilotażowa dotycząca rygorystycznych ustawień zasad ochrony przed spamem i wyłudzaniem informacji**: na przykład **MDOPilot\_SpamPhish\_Strict**

Aby uzyskać jasność, użyjemy tych konkretnych nazw grup w tym artykule, ale możesz korzystać z własnej konwencji nazewnictwa.

Gdy wszystko będzie gotowe do rozpoczęcia testowania, dodaj te grupy jako wyjątki do [reguły przepływu poczty SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Podczas tworzenia zasad dla różnych funkcji ochrony w Ochrona usługi Office 365 w usłudze Defender użyjesz tych grup jako warunków definiujących, do kogo mają zastosowanie zasady.

**Uwagi**:

- Terminy Standard i Strict pochodzą z [zalecanych przez nas ustawień zabezpieczeń](recommended-settings-for-eop-and-office365.md), które są również używane w [wstępnie ustawionych zasadach zabezpieczeń](preset-security-policies.md). W idealnym przypadku zalecamy zdefiniowanie użytkowników pilotażowych w standardowych i ścisłych zasadach zabezpieczeń wstępnie ustawionych, ale nie możemy tego zrobić. Dlaczego? Ponieważ nie można dostosować ustawień w wstępnie ustawionych zasad zabezpieczeń (w szczególności akcji wykonywanych w komunikatach). Podczas testowania migracji chcesz zobaczyć, co Ochrona usługi Office 365 w usłudze Defender zrobić z komunikatami, sprawdzić, co chcesz zrobić, i ewentualnie dostosować konfiguracje zasad, aby umożliwić lub zapobiec tym wynikom.

  Dlatego zamiast używać wstępnie ustawionych zasad zabezpieczeń, ręcznie utworzysz zasady niestandardowe z ustawieniami bardzo podobnymi do, ale w niektórych przypadkach różnią się od ustawień standardowych i ścisłych zasad zabezpieczeń wstępnie ustawionych.

- Jeśli chcesz eksperymentować z ustawieniami **, które znacznie** różnią się od zalecanych wartości standardowych lub ścisłych, rozważ utworzenie dodatkowych i określonych grup dystrybucyjnych dla użytkowników pilotażowych w tych scenariuszach. Za pomocą analizatora konfiguracji możesz sprawdzić, jak bezpieczne są ustawienia. Aby uzyskać instrukcje, zobacz [Configuration analyzer for protection policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Analizator konfiguracji dla zasad ochrony w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](configuration-analyzer-for-security-policies.md)).

  W przypadku większości organizacji najlepszym rozwiązaniem jest rozpoczęcie od zasad ściśle zgodnych z zalecanymi ustawieniami standardowymi. Po tak dużej ilości obserwacji i opinii, jak możesz to zrobić w dostępnym okresie, możesz później przejść do bardziej agresywnych ustawień. Ochrona przed personifikacją i dostarczanie do folderu Wiadomości-śmieci a dostarczenie do kwarantanny może wymagać dostosowania.

  Jeśli używasz dostosowanych zasad, upewnij się, że są one stosowane _przed_ zasadami zawierającymi zalecane ustawienia migracji. Jeśli użytkownik jest identyfikowany w wielu zasadach tego samego typu (na przykład w przypadku ochrony przed wyłudzaniem informacji), tylko jedna zasada tego typu jest stosowana do użytkownika (na podstawie wartości priorytetu zasad). Aby uzyskać więcej informacji, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>Krok 2. Konfigurowanie przesyłania przez użytkownika na potrzeby raportowania komunikatów użytkowników

Ważną częścią migracji jest możliwość identyfikowania wyników fałszywie dodatnich lub fałszywie ujemnych z Ochrona usługi Office 365 w usłudze Defender.

Możesz określić skrzynkę pocztową Exchange Online do odbierania wiadomości zgłaszanych przez użytkowników jako złośliwe lub złośliwe. Aby uzyskać więcej instrukcji, zobacz [Ustawienia komunikatów zgłoszonych przez użytkownika](user-submission.md). Ta skrzynka pocztowa może odbierać kopie wiadomości przesłanych przez użytkowników do firmy Microsoft lub skrzynka pocztowa może przechwytywać wiadomości bez zgłaszania ich do firmy Microsoft (jesteś zespołem ds. zabezpieczeń, który może ręcznie analizować i przesyłać wiadomości). Jednak takie podejście do przechwytywania nie umożliwia usłudze automatycznego dostrajania i uczenia się.

Upewnij się również, że wszyscy użytkownicy programu pilotażowego mają zainstalowaną obsługiwaną aplikację do raportowania komunikatów w Outlook, która jest zgodna z przesyłaniem przez użytkownika. Te aplikacje obejmują:

- [Dodatek Komunikat raportu](enable-the-report-message-add-in.md)
- [Dodatek Raport wyłudzający informacje](enable-the-report-phish-add-in.md)
- Obsługiwane narzędzia raportowania innych firm zgodnie z [opisem tutaj](user-submission.md#third-party-reporting-tools).

Nie lekceważ znaczenia tego kroku. Dane przesyłane przez użytkowników zapewnią ci pętlę opinii, której potrzebujesz, aby zweryfikować dobre, spójne środowisko użytkownika końcowego przed migracją i po niej. Ta opinia ułatwia podejmowanie świadomych decyzji dotyczących konfiguracji zasad, a także zapewnia zarządzanie raportami opartymi na danych, że migracja przebiegła bezproblemowo.

Zamiast polegać na danych, które są wspierane przez środowisko całej organizacji, więcej niż jedna migracja doprowadziła do emocjonalnych spekulacji opartych na pojedynczym negatywnym środowisku użytkownika. Ponadto jeśli korzystasz z symulacji wyłudzania informacji, możesz użyć opinii użytkowników, aby poinformować Cię, kiedy widzą coś ryzykownego, co może wymagać zbadania.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>Krok 3. Obsługa lub tworzenie reguły przepływu poczty SCL=-1

Ponieważ przychodząca wiadomość e-mail jest kierowana przez inną usługę ochrony, która znajduje się przed Microsoft 365, jest bardzo prawdopodobne, że masz już regułę przepływu poczty (znaną również jako reguła transportu) w Exchange Online, która ustawia poziom ufności spamu (SCL) wszystkich wiadomości przychodzących do wartości -1 (pomijanie filtrowania spamu). Większość usług ochrony innych firm zachęca do stosowania tej reguły przepływu poczty SCL=-1 dla Microsoft 365 klientów, którzy chcą korzystać ze swoich usług.

Jeśli używasz innego mechanizmu do zastąpienia stosu filtrowania firmy Microsoft (na przykład listy dozwolonych adresów IP), zalecamy przełączenie się do korzystania z reguły przepływu poczty SCL=-1, **o ile** cała przychodząca poczta internetowa do Microsoft 365 pochodzi z usługi ochrony innej firmy (brak przepływów poczty bezpośrednio z Internetu do Microsoft 365).

Reguła przepływu poczty SCL=-1 jest ważna podczas migracji z następujących powodów:

- Za pomocą [Eksploratora zagrożeń](email-security-in-microsoft-defender.md) możesz sprawdzić, które funkcje w stosie firmy Microsoft *działałyby* na komunikatach bez wpływu na wyniki istniejącej usługi ochrony.
- Możesz stopniowo dostosowywać, kto jest chroniony przez stos filtrowania Microsoft 365, konfigurując wyjątki od reguły przepływu poczty SCL=-1. Wyjątki będą członkami pilotażowych grup dystrybucyjnych, które zalecamy w dalszej części tego artykułu.

  Przed lub podczas wycinania rekordu MX do Microsoft 365 wyłączysz tę regułę, aby włączyć pełną ochronę stosu ochrony Microsoft 365 dla wszystkich adresatów w organizacji.

Aby uzyskać więcej informacji, zobacz [Używanie reguł przepływu poczty do ustawiania poziomu ufności spamu (SCL) w wiadomościach w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Uwagi**:

- Jeśli planujesz zezwolić na przepływ poczty internetowej przez istniejącą usługę ochrony **i** bezpośrednio do Microsoft 365 w tym samym czasie, musisz ograniczyć regułę przepływu poczty SCL=-1 (pocztę, która pomija filtrowanie spamu) do poczty, która przeszła tylko przez istniejącą usługę ochrony. Nie chcesz, aby niefiltrowana poczta internetowa była lądowana w skrzynkach pocztowych użytkowników w Microsoft 365.

  Aby poprawnie zidentyfikować pocztę, która została już przeskanowana przez istniejącą usługę ochrony, możesz dodać warunek do reguły przepływu poczty SCL=-1. Przykład:

  - **W przypadku usług ochrony opartej na chmurze**: możesz użyć wartości nagłówka i nagłówka, która jest unikatowa dla Twojej organizacji. Komunikaty z nagłówkiem nie są skanowane według Microsoft 365. Komunikaty bez nagłówka są skanowane według Microsoft 365
  - **W przypadku lokalnych usług ochrony lub urządzeń**: możesz użyć źródłowych adresów IP. Komunikaty ze źródłowych adresów IP nie są skanowane przez Microsoft 365. Komunikaty, które nie pochodzą ze źródłowych adresów IP, są skanowane przez Microsoft 365.

- Nie należy polegać wyłącznie na rekordach MX, aby kontrolować, czy poczta jest filtrowana. Nadawcy mogą łatwo ignorować rekord MX i wysyłać wiadomości e-mail bezpośrednio do Microsoft 365.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>Krok 4. Konfigurowanie rozszerzonego filtrowania dla łączników

Pierwszą rzeczą do wykonania jest skonfigurowanie [rozszerzonego filtrowania łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (znanego również jako *pomijanie listy*) w łączniku używanym do przepływu poczty z istniejącej usługi ochrony do Microsoft 365. Możesz użyć [raportu Komunikaty przychodzące,](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) aby ułatwić identyfikację łącznika.

Rozszerzone filtrowanie łączników jest wymagane przez Ochrona usługi Office 365 w usłudze Defender, aby zobaczyć, skąd faktycznie pochodzą wiadomości internetowe. Ulepszone filtrowanie łączników znacznie zwiększa dokładność stosu filtrowania firmy Microsoft (w szczególności [analizę podróbek](anti-spoofing-protection.md), a także możliwości po naruszeniu zabezpieczeń w [Eksploratorze zagrożeń](threat-explorer.md) i [zautomatyzowanym badaniu & Response (AIR)](automated-investigation-response-office.md)).

Aby poprawnie włączyć filtrowanie rozszerzone dla łączników, należy dodać **publiczne** adresy \*\* IP **wszystkich\*\*** usług innych firm i/lub lokalnych hostów systemu poczty e-mail, które kierują pocztę przychodzącą do Microsoft 365.

Aby potwierdzić, że rozszerzone filtrowanie łączników działa, sprawdź, czy komunikaty przychodzące zawierają jeden lub oba z następujących nagłówków:

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>Krok 5. Tworzenie zasad ochrony pilotażowej

Tworząc zasady produkcyjne, nawet jeśli nie są one stosowane do wszystkich użytkowników, możesz przetestować funkcje po naruszeniu zabezpieczeń, takie jak [Eksplorator zagrożeń](threat-explorer.md), i przetestować integrację Ochrona usługi Office 365 w usłudze Defender z procesami zespołu reagowania na zabezpieczenia.

> [!IMPORTANT]
> Zasady mogą być ograniczone do użytkowników, grup lub domen. Nie zalecamy mieszania wszystkich trzech w jednej zasad, ponieważ tylko użytkownicy, którzy pasują do wszystkich trzech, będą wchodzić w zakres zasad. W przypadku zasad pilotażowych zalecamy używanie grup lub użytkowników. W przypadku zasad produkcyjnych zalecamy używanie domen. Niezwykle ważne jest zrozumienie, że **tylko** podstawowa domena poczty e-mail użytkownika określa, czy użytkownik wchodzi w zakres zasad. Dlatego jeśli przełączysz rekord MX dla domeny pomocniczej użytkownika, upewnij się, że jego domena podstawowa jest również objęta zasadami.

### <a name="create-pilot-safe-attachments-policies"></a>Tworzenie zasad załączników Sejf pilotażowych

[Sejf Załączniki](safe-attachments.md) to najłatwiejsza funkcja Ochrona usługi Office 365 w usłudze Defender do włączenia i przetestowania przed przełączeniem rekordu MX. Sejf Załączniki mają następujące korzyści:

- Minimalna konfiguracja.
- Bardzo małe prawdopodobieństwo fałszywie dodatnich wyników.
- Podobne zachowanie do ochrony przed złośliwym oprogramowaniem, które jest zawsze włączone i nie ma na nie wpływu reguła przepływu poczty SCL=-1.

Utwórz zasady załączników Sejf dla użytkowników pilotażowych.

Aby uzyskać zalecane ustawienia, zobacz [Zalecane ustawienia zasad Sejf Załączniki](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Należy pamiętać, że zalecenia standardowe i ścisłe są takie same. Aby utworzyć zasady, zobacz [Konfigurowanie zasad Sejf załączników](set-up-safe-attachments-policies.md). Pamiętaj, aby użyć grupy **MDOPilot\_SafeAttachments** jako warunku zasad (do których mają zastosowanie zasady).

> [!IMPORTANT]
> Obecnie nie ma domyślnych zasad Sejf Załączniki. Przed przełączeniem rekordów MX zalecamy posiadanie zasad Sejf Załączniki, które chronią całą organizację.

### <a name="create-pilot-safe-links-policies"></a>Tworzenie zasad linków Sejf pilotażowych

> [!NOTE]
> Nie obsługujemy opakowywania ani ponownego pisania już opakowanych lub ponownie napisanych linków. Jeśli bieżąca usługa ochrony już zawija lub ponownie zapisuje linki w wiadomościach e-mail, musisz wyłączyć tę funkcję dla użytkowników pilotażowych. Jednym ze sposobów zapewnienia, że tak się nie stanie, jest wykluczenie domeny adresu URL innej usługi w zasadach Sejf Links.
>
> Sejf Ochrona linków dla obsługiwanych aplikacji Office jest ustawieniem globalnym, które ma zastosowanie do wszystkich licencjonowanych użytkowników. Możesz ją włączyć lub wyłączyć globalnie, a nie dla określonych użytkowników. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ochrony linków Sejf dla aplikacji Office 365](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Utwórz zasady linków Sejf dla użytkowników pilotażowych. Szanse na wyniki fałszywie dodatnie w linkach Sejf również są dość niskie, ale należy rozważyć przetestowanie tej funkcji na mniejszej liczbie użytkowników pilotażowych niż Sejf załączników. Ponieważ ta funkcja ma wpływ na środowisko użytkownika, należy rozważyć plan edukacji użytkowników.

Aby zapoznać się z zalecanymi ustawieniami, zobacz [Zalecane ustawienia zasad Sejf Łącza](recommended-settings-for-eop-and-office365.md#safe-links-settings). Należy pamiętać, że zalecenia standardowe i ścisłe są takie same. Aby utworzyć zasady, zobacz [Konfigurowanie zasad linków Sejf](set-up-safe-links-policies.md). Pamiętaj, aby użyć grupy **MDOPilot\_SafeLinks** jako warunku zasad (do których mają zastosowanie zasady).

> [!IMPORTANT]
> Obecnie nie ma domyślnych zasad Sejf Łącza. Przed przełączeniem rekordów MX zalecamy posiadanie zasad Sejf Linki, które chronią całą organizację.

### <a name="create-pilot-anti-spam-policies"></a>Tworzenie pilotażowych zasad ochrony przed spamem

Utwórz dwie zasady ochrony przed spamem dla użytkowników pilotażowych:

- Zasady używające ustawień standardowych. Użyj grupy **MDOPilot\_SpamPhish\_Standard** jako warunku zasad (do których mają zastosowanie zasady).
- Zasady, które używają ustawień ścisłych. Użyj grupy **MDOPilot\_SpamPhish\_Strict** jako warunku zasad (którego dotyczą zasady). Te zasady powinny mieć wyższy priorytet (mniejszą liczbę) niż zasady z ustawieniami standardowymi.

Aby zapoznać się z zalecanymi ustawieniami standardowymi i ścisłymi, zobacz [Zalecane ustawienia zasad ochrony przed spamem](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings). Aby utworzyć zasady, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Tworzenie pilotażowych zasad ochrony przed wyłudzaniem informacji

Utwórz dwie zasady ochrony przed wyłudzaniem informacji dla użytkowników pilotażowych:

- Zasady korzystające z ustawień standardowych z wyjątkiem akcji wykrywania personifikacji, jak opisano poniżej. Użyj grupy **MDOPilot\_SpamPhish\_Standard** jako warunku zasad (do których mają zastosowanie zasady).
- Zasady korzystające z ustawień ścisłych z wyjątkiem akcji wykrywania personifikacji zgodnie z poniższym opisem. Użyj grupy **MDOPilot\_SpamPhish\_Strict** jako warunku zasad (którego dotyczą zasady). Te zasady powinny mieć wyższy priorytet (mniejszą liczbę) niż zasady z ustawieniami standardowymi.

W przypadku wykrywania fałszowania zalecaną akcją Standardowa jest **przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**, a zalecaną ścisłą akcją jest **kwarantanna wiadomości**. Użyj analizy fałszowania, aby obserwować wyniki. Przesłonięcia zostały wyjaśnione w następnej sekcji. Aby uzyskać więcej informacji, zobacz [Spoof intelligence insight in EOP (Fałszowanie analizy w ramach EOP](learn-about-spoof-intelligence.md)).

W przypadku wykrywania personifikacji zignoruj zalecane akcje standardowe i ścisłe dla zasad pilotażowych. Zamiast tego użyj wartości **Nie stosuj żadnej akcji** dla następujących ustawień:

- **Jeśli komunikat zostanie wykryty jako personifikowany użytkownik**
- **Jeśli komunikat zostanie wykryty jako domena personifikowana**
- **Jeśli analiza skrzynki pocztowej wykryje personifikowanego użytkownika**

Użyj szczegółowych informacji o personifikacji, aby obserwować wyniki. Aby uzyskać więcej informacji, zobacz [Szczegółowe informacje o personifikacji w Ochrona usługi Office 365 w usłudze Defender](impersonation-insight.md).

Dostosujesz ochronę przed fałszowaniem (dostosujesz zezwalanie i bloki) i włączysz każdą akcję ochrony przed personifikacją, aby poddać kwarantannie lub przenieść wiadomości do folderu Wiadomości-śmieci (na podstawie zaleceń standardowych lub ścisłych). W razie potrzeby możesz obserwować wyniki i dostosowywać ich ustawienia.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Ochrona przed spoofingiem](anti-spoofing-protection.md)
- [Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Konfigurowanie zasad ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Następny krok

**Gratulacje**! Ukończono fazę **konfiguracji** [migracji do Ochrona usługi Office 365 w usłudze Microsoft Defender](migrate-to-defender-for-office-365.md#the-migration-process)!

- Przejdź do [fazy 3: dołączanie](migrate-to-defender-for-office-365-onboard.md).
