---
title: Migrowanie do programu Microsoft Defender Office 365 Etap 2. Konfiguracja
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
description: W celu rozpoczęcia migracji z usługi lub urządzenia ochrony innej firmy do programu Microsoft Defender w celu Office 365 ochrony.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cc16da76f4b863800bb4f1e7573bbe2fa106b4cf
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2022
ms.locfileid: "63013294"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Migrowanie do programu Microsoft Defender Office 365 — etap 2. Konfigurowanie

**Dotyczy:**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)

<br>

|[![Etap 1. Przygotowanie.](../../media/phase-diagrams/prepare.png)](migrate-to-defender-for-office-365-prepare.md) <br> [Etap 1. Przygotowywanie](migrate-to-defender-for-office-365-prepare.md)|![Etap 2. Konfigurowanie.](../../media/phase-diagrams/setup.png) <br> Etap 2. Konfigurowanie|[![Etap 3. Wsad.](../../media/phase-diagrams/onboard.png)](migrate-to-defender-for-office-365-onboard.md) <br> [Etap 3. Wniesienie](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Jesteś tutaj!*||

Etap **2: Konfigurowanie** migracji do programu **[Microsoft Defender](migrate-to-defender-for-office-365.md#the-migration-process)** dla systemu Office 365! Ten etap migracji obejmuje następujące kroki:

1. [Tworzenie grup dystrybucyjnych dla użytkowników pilotażowych](#step-1-create-distribution-groups-for-pilot-users)
2. [Konfigurowanie przesyłania użytkowników do raportowania wiadomości użytkownika](#step-2-configure-user-submission-for-user-message-reporting)
3. [Obsługa lub tworzenie reguły przepływu poczty SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Konfigurowanie ulepszonego filtrowania dla łączników](#step-4-configure-enhanced-filtering-for-connectors)
5. [Tworzenie zasad ochrony pilotażowej](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>Krok 1. Tworzenie grup dystrybucyjnych dla użytkowników pilotażowych

Grupy dystrybucyjne są wymagane Microsoft 365 w następujących aspektach migracji:

- Wyjątki od reguły **przepływu poczty SCL=-1**: chcesz, aby użytkownicy pilotażowi uzyskać pełny efekt ochrony usługi Defender dla usługi Office 365, więc ich wiadomości przychodzące muszą być skanowane przez program Defender w celu uzyskania dostępu do Office 365. Możesz to zrobić, definiując użytkowników pilotażowych w odpowiednich grupach dystrybucyjnych w programie Microsoft 365 i konfigurując te grupy jako wyjątki od reguły przepływu poczty SCL=-1.

  Zgodnie z opisem w kroku 2 w aplikacji [: (](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)Opcjonalnie) Wyklucz użytkowników pilotażowych z filtrowania według istniejącej usługi ochrony, rozważ możliwość wykluczania tych samych użytkowników pilotażowych z funkcji skanowania za pomocą istniejącej usługi ochrony. Wyeliminowanie możliwości filtrowania przez istniejącą usługę ochrony i wyłączności korzystania z usługi Defender dla systemu Office 365 jest najlepszą i najbliższą reprezentacją tego, co się stanie po ukończeniu migracji.

- **Testowanie poszczególnych funkcji ochrony Office 365** Defender: Nawet w przypadku użytkowników pilotażowych nie chcesz włączać wszystkich funkcji jednocześnie. Etapowe podejście do funkcji ochrony, które są dostępne dla użytkowników pilotażowych, znacznie ułatwi rozwiązywanie problemów i dostosowywanie ich. Z myślą o tym zalecamy następujące grupy dystrybucyjne:
  - **Grupa Sejf pilotażowa załączników**: **Na przykład MDOPilotSafeAttachments\_**
  - **Grupa Sejf pilotażowa**: **Na przykład MDOPilotSafeLinks\_**
  - **Grupa pilotażowa dla standardowych** ustawień zasad ochrony przed spamem i wyłudzania informacji: **Na przykład MDOPilotSpamPhishStandard\_\_**
  - **Grupa pilotażowa dla ustawień** ścisłych zasad ochrony przed spamem i wyłudzania informacji: **Na przykład MDOPilotSpamPhishStrict\_\_**

W celu zachowania przejrzystości użyjemy tych konkretnych nazw grup w tym artykule, ale możesz korzystać z własnej konwencji nazewnictwa.

Gdy wszystko będzie gotowe do rozpoczęcia testowania, dodaj te grupy jako wyjątki od reguły [przepływu poczty SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Podczas tworzenia zasad dla różnych funkcji ochrony w programie Defender Office 365 dla systemu Office 365 te grupy będą używać jako warunków, które określają, kogo dotyczą zasady.

**Uwagi**:

- Terminy Standardowy i Ścisłe pochodzą z naszych [zalecanych ustawień](recommended-settings-for-eop-and-office365.md) zabezpieczeń, które są również używane w wstępnie [ustawionych zasadach zabezpieczeń](preset-security-policies.md). Najlepiej byłoby określić użytkowników pilotażowych w ramach standardowych i ściśle wstępnie ustawionych zasad zabezpieczeń, ale nie możemy tego zrobić. Dlaczego? Ponieważ nie można dostosowywać ustawień w wstępnie ustawionych zasadach zabezpieczeń (w szczególności akcji, które są podejmowane na wiadomościach lub dostosowania ustawień ochrony personifikacji). Podczas testowania migracji chcesz sprawdzić, co program Defender dla systemu Office 365 zrobi dla wiadomości, sprawdzić, czy jest to możliwe, i ewentualnie dostosować konfiguracje zasad, aby zezwolić na te wyniki lub zapobiec ich.

  Zamiast wstępnie ustawionych zasad zabezpieczeń należy ręcznie utworzyć zasady niestandardowe z ustawieniami bardzo podobnymi do tych, które w niektórych przypadkach różnią się od ustawień standardowych i ścisłych wstępnie ustawionych zasad zabezpieczeń.

- Jeśli chcesz poeksperymentować z ustawieniami, które znacznie różnią się od naszych wartości zalecanych standardowo lub ściśle, rozważ utworzenie i użycie dodatkowych i określonych grup dystrybucyjnych dla użytkowników pilotażowych w tych scenariuszach. Za pomocą Analizatora konfiguracji możesz sprawdzić, jakie są zabezpieczenia Twoich ustawień. Aby uzyskać instrukcje, [zobacz Analizator konfiguracji do ochrony zasad ochrony w usługach EOP i Microsoft Defender for Office 365](configuration-analyzer-for-security-policies.md).

  W większości organizacji najlepiej jest zacząć od zasad ściśle dostosowanych do zalecanych ustawień standardowych. Po tak dużej uwagi i opinii, ile można zrobić w dostępnych ramach czasowych, możesz później przejść do bardziej agresywnych ustawień. Ochrona personifikacji i dostarczanie do folderu Wiadomości-śmieci a dostarczanie do kwarantanny może wymagać dostosowania.

  Jeśli korzystasz z zasad niestandardowych, po prostu upewnij się, że zostały  one zastosowane przed zasadami, które zawierają nasze zalecane ustawienia migracji. Jeśli użytkownik jest identyfikowany w wielu zasadach tego samego typu (na przykład w przypadku ochrony przed wyłudzaniem informacji), do użytkownika jest stosowana tylko jedna zasada tego typu (na podstawie wartości priorytetu zasad). Aby uzyskać więcej informacji, zobacz [Zamówienie i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>Krok 2. Konfigurowanie przesyłania użytkownika na przykład dla raportowania wiadomości użytkownika

Możliwość zidentyfikowania wyników fałszywie dodatnich lub wyników fałszywie ujemnych z programu Defender Office 365 jest ważną częścią migracji.

Możesz określić skrzynkę pocztową programu Exchange Online, aby odbierać wiadomości raportowe przez użytkowników jako złośliwe. Aby uzyskać więcej instrukcji, zobacz [Ustawienia wiadomości zgłoszonych przez użytkowników](user-submission.md). Ta skrzynka pocztowa może otrzymywać kopie wiadomości przesłanych przez użytkowników do firmy Microsoft, a także przechwycić wiadomości bez zgłaszania ich firmie Microsoft (zespół zabezpieczeń może ręcznie analizować i przesyłać wiadomości). Takie podejście do przecięcia nie umożliwia jednak usługi automatycznego dostrajania i nauki.

Należy również potwierdzić, że wszyscy użytkownicy w ramach pilotażu mają zainstalowaną obsługiwaną aplikację do raportowania wiadomości Outlook zgodną z przesyłaniem użytkowników. Są to między innymi następujące aplikacje:

- [The Report Message add-in](enable-the-report-message-add-in.md)
- [The Report Phishing add-in](enable-the-report-phish-add-in.md)
- Obsługiwane narzędzia do raportowania innych firm zgodnie z opisem [w tym miejscu](user-submission.md#third-party-reporting-tools).

Nie należy podkreślać ważności tego kroku. Dane z przesyłania użytkowników będą stanowiły pętlę opinii, która wymaga potwierdzenia dobrego, spójnego interfejsu użytkownika końcowego przed migracją i po jej zakończeniu. Ta opinia ułatwia podejmowanie świadomych decyzji dotyczących konfiguracji zasad, a także zapewnianie kierownictwu raportów na temat danych, że migracja przebiegła bezproblemowo.

Zamiast polegać na danych opartych na doświadczeniach całej organizacji, więcej niż jedna migracja skutkowała streszcją emocjonalną na podstawie jednego negatywnego doświadczenia użytkownika. Ponadto jeśli korzystasz z prób prób wyłudzania informacji, możesz skorzystać z opinii użytkowników, aby poinformować ich, kiedy dosyć dosyć ryzykownych sytuacji, które mogą wymagać analizy.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>Krok 3. Obsługa lub tworzenie reguły przepływu poczty SCL=-1

Ponieważ przychodząca poczta e-mail jest przekierowyana przez inną usługę ochrony, która znajduje się przed programem Microsoft 365, prawdopodobnie masz już w programie Exchange Online regułę przepływu poczty e-mail, która ustawia poziom ufności filtru spamu dla całej poczty przychodzącej na wartość -1 (omiń filtrowanie spamu). Większość usług ochrony innych firm zachęca do korzystania z tej reguły przepływu poczty SCL=-1 Microsoft 365 dla klientów, którzy chcą korzystać z ich usług.

Jeśli używasz innego mechanizmu zastępowania stosu filtrowania firmy Microsoft (na przykład listy zezwalań na adresy IP), zalecamy przełączenie się na regułę przepływu poczty SCL=-1, o ile cała  przychodzące do firmy Microsoft 365 poczta internetowa pochodzi z usługi ochrony innej firmy (żadna poczta nie przepływa bezpośrednio z Internetu do usługi Microsoft 365).

Reguła przepływu poczty SCL=-1 jest ważna podczas migracji z następujących powodów:

- Eksplorator zagrożeń pozwala [sprawdzić](email-security-in-microsoft-defender.md), które funkcje w stosie firmy Microsoft miałyby wpływ na wiadomości bez wpływu na wyniki istniejącej usługi ochrony.
- Użytkowników chronionych za pomocą stosu Microsoft 365 można dostosowywać, konfigurując wyjątki od reguły przepływu poczty SCL=-1. Wyjątki będą członkami pilotażowych grup dystrybucyjnych, co zalecamy w dalszej części tego artykułu.

  Przed i podczas odciętych rekordów MX do Microsoft 365 wyłączysz tę regułę, aby włączyć pełną ochronę stosu ochrony rekordu Microsoft 365 dla wszystkich adresatów w organizacji.

Aby uzyskać więcej informacji, zobacz Ustawianie poziomu ufności filtru spamu w wiadomościach w [programie Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Uwagi**:

- Jeśli planujesz umożliwić przepływ poczty internetowej przez istniejącą usługę ochrony i  jednocześnie bezpośrednio do usługi Microsoft 365, musisz ograniczyć regułę przepływu poczty SCL=-1 (która pomija filtrowanie spamu) do poczty, która przeszło tylko przez istniejącą usługę ochrony. Nie chcesz, aby niefiltrowana poczta internetowa trafiała do skrzynek pocztowych użytkowników w Microsoft 365.

  Aby poprawnie zidentyfikować pocztę, która została już przeskanowana przez istniejącą usługę ochrony, możesz dodać warunek do reguły przepływu poczty SCL=-1. Przykład:

  - **W przypadku usług ochrony w** chmurze: Możesz użyć wartości nagłówka i nagłówka, która jest unikatowa w Twojej organizacji. Wiadomości z nagłówkiem nie są skanowane za pomocą Microsoft 365. Wiadomości bez nagłówka są skanowane za pomocą Microsoft 365
  - **W przypadku lokalnych usług lub urządzeń** ochrony: Możesz użyć źródłowych adresów IP. Wiadomości ze źródłowych adresów IP nie są skanowane przez Microsoft 365. Wiadomości, które nie pochodzą ze źródłowych adresów IP, są skanowane przez Microsoft 365.

- Nie polegaj wyłącznie na rekordach MX, aby kontrolować, czy poczta jest filtrowana. Nadawcy mogą łatwo zignorować rekord MX i wysyłać wiadomości e-mail bezpośrednio do Microsoft 365.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>Krok 4. Konfigurowanie ulepszonego filtrowania łączników

Pierwszą rzeczą, którą należy zrobić, jest skonfigurowanie ulepszonego filtrowania łączników [(](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)nazywanego również pomiń na *liście) na* łączniku używanym do przepływu poczty z istniejącej usługi ochrony do Microsoft 365. Raport wiadomości [przychodzących pomaga](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) w zidentyfikowaniu łącznika.

Program Defender wymaga ulepszonego filtrowania łączników, aby program Office 365 w celu zobaczenia, skąd w rzeczywistości pochodziły wiadomości internetowe. Ulepszone filtrowanie łączników znacznie zwiększa dokładność stosu filtrowania firmy Microsoft (zwłaszcza analizy fałszowania[, a](anti-spoofing-protection.md) także funkcji po naruszeniu zabezpieczeń w Eksploratorze [](threat-explorer.md) zagrożeń i funkcji automatycznego wykrywania & [odpowiedzi (AIR](automated-investigation-response-office.md)).

Aby poprawnie włączyć rozszerzone filtrowanie łączników, musisz dodać publiczne **adresy IP** \***\*\***\* wszystkich usług innych firm i/lub lokalnych hostów systemu poczty e-mail, którzy przekierują pocztę przychodzących do Microsoft 365.

Aby upewnić się, że ulepszone filtrowanie łączników działa, upewnij się, że wiadomości przychodzące zawierają jeden lub oba z następujących nagłówków:

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>Krok 5. Tworzenie zasad ochrony pilotażowej

Tworząc zasady produkcyjne, nawet jeśli nie są one stosowane do wszystkich użytkowników, możesz przetestować funkcje, takie jak Eksplorator zagrożeń po [](threat-explorer.md) naruszeniu zabezpieczeń, i przetestować integrację usługi Defender dla programu Office 365 z procesami zespołu reagowania na zabezpieczenia.

> [!IMPORTANT]
> Zasady mogą być objęte zakresem użytkowników, grup lub domen. Nie zaleca się mieszania wszystkich trzech zasad, ponieważ tylko użytkownicy, którzy pasują do wszystkich trzech, będą wchodzić w zakres tych zasad. W przypadku zasad pilotażowych zalecamy korzystanie z grup lub użytkowników. W przypadku zasad produkcyjnych zalecamy używanie domen. Niezwykle ważne jest, aby zrozumieć, że  tylko podstawowa domena poczty e-mail użytkownika określa, czy użytkownik wchodzi w zakres tych zasad. Zatem jeśli przełączysz rekord MX dla domeny pomocniczej użytkownika, upewnij się, że jego domena podstawowa jest również objęta zasadami.

### <a name="create-pilot-safe-attachments-policies"></a>Tworzenie zasad załączników Sejf pilotażowych

[Sejf Załączniki to](safe-attachments.md) najłatwiejsza funkcja usługi Defender Office 365 włączyć i przetestować przed przełączeniem rekordu MX. Sejf mają następujące zalety:

- Minimalna konfiguracja.
- Bardzo mała szansa na wyniki fałszywie dodatnie.
- Podobne zachowanie do ochrony przed złośliwym oprogramowaniem, które jest zawsze wł. i na które nie wpływa reguła przepływu poczty SCL=-1.

Utwórz zasady załączników Sejf dla użytkowników pilotażowych.

Aby uzyskać zalecane ustawienia, zobacz [Zalecane Sejf ustawienia zasad Załączniki](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Należy pamiętać, że zalecenia Standardowe i Ścisłe są takie same. Aby utworzyć zasady, zobacz [Konfigurowanie zasad Sejf załączników](set-up-safe-attachments-policies.md). Pamiętaj, aby użyć **grupowych potwierdzeń MDOPilotSafeAttachments\_** jako warunku zasad (kogo dotyczą).

> [!IMPORTANT]
> Obecnie nie ma żadnych domyślnych Sejf załączników. Przed przełączeniem jakichkolwiek rekordów MX zalecamy stosowanie zasad załączników Sejf, które chronią całą organizację.

### <a name="create-pilot-safe-links-policies"></a>Tworzenie zasad Sejf pilotażowych

> [!NOTE]
> Zawijanie lub ponowne zawijanie już zawiniętych lub pisanych linków nie jest obsługuje. Jeśli bieżąca usługa ochrony już zawija lub ponownie zapisuje linki w wiadomościach e-mail, musisz wyłączyć tę funkcję dla użytkowników pilotażowych. Jednym ze sposobów na to, aby się nie pomylić, jest wyłączenie domeny adresu URL innej usługi z zasad Sejf linków.
>
> Sejf linki dla obsługiwanych Office to ustawienie globalne, które dotyczy wszystkich licencjonowanych użytkowników. Możesz ją włączyć lub wyłączyć globalnie, a nie dla określonych użytkowników. Aby uzyskać więcej informacji, [zobacz Konfigurowanie ochrony Sejf linków dla Office 365 aplikacji](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Utwórz zasady Sejf dla użytkowników pilotażowych. Szanse na wyniki fałszywie dodatnie w Sejf także są niskie, ale należy rozważyć przetestowanie tej funkcji u mniejszej liczby użytkowników pilotażowych niż w Sejf załączników. Ponieważ ta funkcja wpływa na środowisko użytkownika, należy rozważyć plan edukacji użytkowników.

Aby uzyskać informacje o zalecanych ustawieniach, [zobacz Zalecane Sejf ustawień zasad linków](recommended-settings-for-eop-and-office365.md#safe-links-settings). Należy pamiętać, że zalecenia Standardowe i Ścisłe są takie same. Aby utworzyć zasady, zobacz [Konfigurowanie Sejf linków](set-up-safe-links-policies.md). Pamiętaj, aby użyć grupy **MDOPilotSafeLinks\_** jako warunku zasad (kogo dotyczą).

> [!IMPORTANT]
> Obecnie nie ma żadnych domyślnych Sejf linków. Przed przełączeniem jakichkolwiek rekordów MX zalecamy stosowanie zasad Sejf Links, które chronią całą organizację.

### <a name="create-pilot-anti-spam-policies"></a>Tworzenie pilotażowych zasad ochrony przed spamem

Utwórz dwie zasady ochrony przed spamem dla użytkowników pilotażowych:

- Zasady z ustawieniami standardowymi. Użyj grupy **MDOPilotSpamPhishStandard\_\_ jako** warunku zasad (osoby, których dotyczą zasady).
- Zasady, które mają ustawienia Ścisłe. Użyj **grupowego rozwiązania MDOPilotSpamPhishStrict\_\_** jako warunku zasad (osoby, których dotyczą zasady). Te zasady powinny mieć wyższy priorytet (niższą liczbę) niż zasady z ustawieniami standardowymi.

Aby uzyskać zalecane ustawienia standardowe i ścisłe, zobacz Zalecane ustawienia [zasad ochrony przed spamem](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings). Aby utworzyć zasady, zobacz [Konfigurowanie zasad ochrony przed spamem](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Tworzenie pilotażowych zasad ochrony przed wyłudzaniem informacji

Utwórz dwie zasady ochrony przed wyłudzaniem informacji dla użytkowników pilotażowych:

- Zasady, które używa ustawień standardowych, z wyjątkiem akcji wykrywania personifikacji, jak opisano poniżej. Użyj grupy **MDOPilotSpamPhishStandard\_\_ jako** warunku zasad (osoby, których dotyczą zasady).
- Zasady, które mają ustawienia ścisłe, z wyjątkiem akcji wykrywania personifikacji, jak opisano poniżej. Użyj **grupowego rozwiązania MDOPilotSpamPhishStrict\_\_** jako warunku zasad (osoby, których dotyczą zasady). Te zasady powinny mieć wyższy priorytet (niższą liczbę) niż zasady z ustawieniami standardowymi.

W przypadku wykrywania fałszowania zalecaną czynnością standardową jest Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów **, a** zalecana akcja Ścisłe to Poddaj wiadomość **kwarantannie**. Używaj szczegółowych informacji o analizie fałszerzy, aby obserwować wyniki. W następnej sekcji wyjaśniono zastępowanie. Aby uzyskać więcej informacji, zobacz [Spoof intelligence insight in EOP (Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md)).

W przypadku wykrywania personifikacji zignoruj zalecane działania standardowe i ścisłe w ramach zasad pilotażowych. Zamiast tego użyj wartości **Nie zastosuj żadnej akcji** w następujących ustawieniach:

- **Jeśli wiadomość zostanie wykryta jako personifikowany użytkownik**
- **Jeśli wiadomość zostanie wykryta jako spersonifikowana domena**
- **Jeśli w analizie skrzynki pocztowej zostanie wykryty personifikowany użytkownik**

Użyj szczegółowych informacji o personifikacji, aby obserwować wyniki. Aby uzyskać więcej informacji, zobacz [Informacje o personifikacji w programie Defender dla Office 365](impersonation-insight.md).

Dostosujesz ochronę przed fałszerością (dostosuj dopuszcza i blokuje) i włączysz każdą akcję ochrony personifikacji w celu kwarantanny lub przenoszenia wiadomości do folderu Wiadomości-śmieci (na podstawie rekomendacji standardowych lub ścisłych). Możesz obserwować wyniki i dostosować ich ustawienia odpowiednio do potrzeb.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Ochrona przed fałszerami](anti-spoofing-protection.md)
- [Ustawienia personifikacji w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Skonfiguruj zasady ochrony przed wyłudzaniem informacji w programie Defender dla Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Następny krok

**Gratulacje**! Ukończono etap **konfiguracji migracji** do programu [Microsoft Defender dla systemu Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Przejdź do [fazy 3. Do pracy](migrate-to-defender-for-office-365-onboard.md).
