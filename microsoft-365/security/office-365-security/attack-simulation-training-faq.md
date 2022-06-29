---
title: Zagadnienia dotyczące wdrażania szkolenia z symulacji ataków i często zadawane pytania
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection: m365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą poznać zagadnienia dotyczące wdrażania i często zadawane pytania dotyczące symulacji ataków i szkoleń w organizacjach Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 50f82d975e9dc4f534f9223b85fd9e841a3ad725
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490492"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a>Zagadnienia dotyczące wdrażania szkolenia z symulacji ataków i często zadawane pytania

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2](defender-for-office-365.md)

Trenowanie symulacji ataków umożliwia organizacjom Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 mierzenie ryzyka związanego z inżynierią społeczną i zarządzanie nim, umożliwiając tworzenie symulacji wyłudzania informacji i zarządzanie nimi, które są obsługiwane przez rzeczywiste ładunki wyłudzania informacji bez broni. Szkolenie hiper-ukierunkowane, realizowane we współpracy z zabezpieczeniami programu Terranova, pomaga poprawić wiedzę i zmienić zachowanie pracowników.

Aby uzyskać więcej informacji na temat rozpoczynania pracy z trenowaniem symulacji ataków, zobacz [Wprowadzenie do trenowania symulacji ataków](attack-simulation-training-get-started.md).

Podczas gdy całe środowisko tworzenia i planowania symulacji zostało zaprojektowane tak, aby było swobodne i bezproblemowe, uruchamianie symulacji w skali przedsiębiorstwa często wymaga planowania. Ten artykuł pomaga sprostać konkretnym wyzwaniom, które widzimy, gdy nasi klienci uruchamiają symulacje we własnych środowiskach.

## <a name="issues-with-end-user-experiences"></a>Problemy z środowiskami użytkowników końcowych

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a>Adresy URL symulacji wyłudzania informacji zablokowane przez bezpieczne przeglądanie google

Usługa reputacji adresu URL może zidentyfikować co najmniej jeden adres URL używany przez trenowanie symulacji ataków jako niebezpieczny. Bezpieczne przeglądanie Google w przeglądarce Google Chrome blokuje niektóre symulowane adresy URL wyłudzania informacji za pomocą komunikatu **zwodniczej witryny** . Chociaż współpracujemy z wieloma dostawcami reputacji adresów URL, aby zawsze zezwalać na nasze adresy URL symulacji, nie zawsze mamy pełne pokrycie.

:::image type="content" source="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png" alt-text="Ostrzeżenie o zwodniczej witrynie w Google Chrome" lightbox="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png":::

Należy pamiętać, że ten problem nie ma wpływu na przeglądarkę Microsoft Edge.

W ramach fazy planowania przed użyciem adresu URL w kampanii wyłudzania informacji sprawdź dostępność adresu URL w obsługiwanych przeglądarkach internetowych. Jeśli adresy URL są blokowane przez bezpieczne przeglądanie google, [postępuj zgodnie z poniższymi wskazówkami](https://support.google.com/chrome/a/answer/7532419) firmy Google, aby zezwolić na dostęp do adresów URL.

Aby uzyskać listę adresów URL, które są obecnie używane przez trenowanie symulacji ataków, zobacz [Wprowadzenie do trenowania symulacji ataków](attack-simulation-training-get-started.md) .

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a>Symulacja wyłudzania informacji i adresy URL administratora zablokowane przez rozwiązania serwera proxy sieci i sterowniki filtrów

Zarówno adresy URL symulacji wyłudzania informacji, jak i adresy URL administratora mogą zostać zablokowane lub usunięte przez pośrednie urządzenia lub filtry zabezpieczeń. Przykład:

- Zapory
- rozwiązania Web Application Firewall (WAF)
- Sterowniki filtrów innych firm (na przykład filtry trybu jądra)

Chociaż widzieliśmy, że niewielu klientów jest zablokowanych w tej warstwie, tak się dzieje. Jeśli wystąpią problemy, rozważ skonfigurowanie następujących adresów URL w celu obejścia skanowania przez urządzenia zabezpieczeń lub filtry zgodnie z wymaganiami:

- Symulowane adresy URL wyłudzania informacji zgodnie z opisem w artykule [Wprowadzenie do trenowania symulacji ataków](attack-simulation-training-get-started.md).
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a>Komunikaty symulacji nie są dostarczane do wszystkich użytkowników docelowych

Możliwe, że liczba użytkowników, którzy faktycznie otrzymują wiadomości e-mail symulacji, jest mniejsza niż liczba użytkowników, którzy zostali objęci symulacją. Następujące typy użytkowników zostaną wykluczone w ramach weryfikacji docelowej:

- Nieprawidłowe adresy e-mail adresatów.
- Użytkownicy-goście.
- Użytkownicy, którzy nie są już aktywni w usłudze Azure Active Directory (Azure AD).

Tylko prawidłowi użytkownicy niebędący gośćmi z prawidłową skrzynką pocztową zostaną uwzględnieni w symulacjach. Jeśli używasz grup dystrybucyjnych lub grup zabezpieczeń z obsługą poczty do kierowania użytkowników, możesz użyć polecenia cmdlet [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember) w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), aby wyświetlić i zweryfikować członków grupy dystrybucyjnej.

## <a name="issues-with-attack-simulation-training-reporting"></a>Problemy z raportowaniem trenowania symulacji ataków

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a>Raporty trenowania symulacji ataków nie zawierają żadnych szczegółów działania

Szkolenia dotyczące symulacji ataków są wyposażone w rozbudowane szczegółowe informacje umożliwiające podjęcie działań, które informują o postępie gotowości pracowników do realizacji zagrożeń. Jeśli raporty trenowania symulacji ataków nie są wypełnione danymi, sprawdź, czy wyszukiwanie dzienników inspekcji jest włączone w organizacji (domyślnie jest włączone).

Wyszukiwanie dzienników inspekcji jest wymagane przez trenowanie symulacji ataków, aby zdarzenia mogły być przechwytywane, rejestrowane i odczytywane z powrotem. Wyłączenie wyszukiwania dzienników inspekcji ma następujące konsekwencje dla trenowania symulacji ataków:

- Dane raportowania nie są dostępne we wszystkich raportach. Raporty będą wyświetlane jako puste.
- Przypisania trenowania są blokowane, ponieważ dane są niedostępne.

Aby włączyć wyszukiwanie dzienników inspekcji, zobacz [Włączanie lub wyłączanie wyszukiwania dzienników inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

> [!NOTE]
> Puste szczegóły działania mogą być również spowodowane tym, że żadne licencje E5 nie są przypisane do użytkowników. Sprawdź, czy co najmniej jedna licencja E5 jest przypisana do aktywnego użytkownika, aby upewnić się, że zdarzenia raportowania są przechwytywane i rejestrowane.

### <a name="simulation-reports-are-not-updated-immediately"></a>Raporty symulacji nie są natychmiast aktualizowane

Szczegółowe raporty symulacji nie są aktualizowane natychmiast po rozpoczęciu kampanii. Nie martw się; to zachowanie jest oczekiwane.

Każda kampania symulacji ma cykl życia. Po pierwszym utworzeniu symulacja jest w stanie **Zaplanowane** . Po rozpoczęciu symulacji przechodzi ona do stanu **W toku** . Po zakończeniu symulacja przechodzi do stanu **Ukończono** .

Gdy symulacja jest w stanie **Zaplanowane** , raporty symulacji będą w większości puste. Na tym etapie aparat symulacji rozwiązuje docelowe adresy e-mail użytkowników, rozszerza grupy dystrybucyjne, usuwa użytkowników-gości z listy itp.:

:::image type="content" source="../../media/attack-sim-training-faq-scheduled-state.png" alt-text="Szczegóły symulacji przedstawiające symulację w stanie Zaplanowane" lightbox="../../media/attack-sim-training-faq-scheduled-state.png":::

Gdy symulacja przejdzie do etapu **W toku** , zauważysz, że informacje zaczynają spływać do raportowania:

:::image type="content" source="../../media/attack-sim-training-faq-in-progress-state.png" alt-text="Szczegóły symulacji przedstawiające symulację w stanie W toku" lightbox="../../media/attack-sim-training-faq-in-progress-state.png":::

Aktualizacja poszczególnych raportów symulacji po przejściu do stanu **W toku** może potrwać do 30 minut. Dane raportu są nadal kompilowane, dopóki symulacja nie osiągnie stanu **Ukończono** . Aktualizacje raportowania występują w następujących interwałach:

- Co 10 minut przez pierwsze 60 minut.
- Co 15 minut po 60 minutach do 2 dni.
- Co 30 minut po 2 dniach aż do 7 dni.
- Co 60 minut po 7 dniach.

Widżety na stronie **Przegląd** zapewniają szybką migawkę stanu zabezpieczeń opartego na symulacjach organizacji w miarę upływu czasu. Ponieważ te widżety odzwierciedlają ogólną postawę zabezpieczeń i podróż w czasie, są one aktualizowane po zakończeniu każdej kampanii symulacji.

> [!NOTE]
> Aby wyodrębnić dane, możesz użyć opcji **Eksportuj** na różnych stronach raportowania.

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a>Komunikaty zgłaszane jako wyłudzanie informacji przez użytkowników nie są wyświetlane w raportach symulacji

Raporty symulacji w trenowaniu symulatora ataków zawierają szczegółowe informacje na temat aktywności użytkownika. Przykład:

- Użytkownicy, którzy klikną link w wiadomości.
- Użytkownicy, którzy zrezygnowali ze swoich poświadczeń.
- Użytkownicy, którzy zgłosili wiadomość jako wyłudzanie informacji.

Jeśli komunikaty zgłaszane przez użytkowników jako wyłudzanie informacji nie są przechwytywane w raportach symulacji symulacji ataków, może istnieć reguła przepływu poczty programu Exchange (znana również jako reguła transportu), która blokuje dostarczanie zgłoszonych wiadomości do firmy Microsoft. Sprawdź, czy reguły przepływu poczty nie blokują dostarczania na następujące adresy e-mail:

- junk@office365.microsoft.com
- abuse@messaging.microsoft.com
- phish@office365.microsoft.com
- nie\_junk@office365.microsoft.com

### <a name="users-are-assigned-training-after-they-report-a-simulated-message"></a>Użytkownicy są przypisani do szkolenia po zgłoszeniu symulowanego komunikatu

Jeśli użytkownicy mają przypisane szkolenie po zgłoszeniu komunikatu symulacji wyłudzania informacji, sprawdź, czy twoja organizacja ma **niestandardową skrzynkę pocztową** skonfigurowaną w **zasadach przesyłania użytkowników**. Podczas konfigurowania **niestandardowej skrzynki pocztowej** ta skrzynka pocztowa musi zostać wykluczona z zasad bezpiecznych łączy i bezpiecznych załączników zgodnie z [wymaganiami wstępnymi niestandardowej skrzynki pocztowej](user-submission.md).

Jeśli twoja organizacja ma **skonfigurowaną niestandardową skrzynkę pocztową** i nie skonfigurowała wymaganych wykluczeń, te wiadomości mogą zostać zdetonowane, co spowoduje przypisanie szkoleń.

## <a name="other-frequently-asked-questions"></a>Inne często zadawane pytania

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a>Pyt.: Jaka jest zalecana metoda kierowania do użytkowników kampanii symulacji?

Odjęcie: Dostępnych jest kilka opcji dla użytkowników docelowych:

- Uwzględnij wszystkich użytkowników (obecnie dostępnych dla organizacji z mniej niż 40 000 użytkowników).
- Wybierz określonych użytkowników.
- Wybierz użytkowników z pliku CSV (jeden adres e-mail na wiersz).
- Azure AD określania wartości docelowej opartej na grupach.

Odkryliśmy, że kampanie, w których docelowi użytkownicy są identyfikowane przez grupy Azure AD, są zazwyczaj łatwiejsze w zarządzaniu.

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a>Pyt.: Czy istnieją jakieś ograniczenia dotyczące kierowania użytkowników podczas importowania z pliku CSV lub dodawania użytkowników?

Odp.: Limit importowania adresatów z pliku CSV lub dodawania poszczególnych adresatów do symulacji wynosi 40 000.

Adresat może być pojedynczym użytkownikiem lub grupą. Grupa może zawierać setki lub tysiące adresatów, więc rzeczywisty limit nie jest ograniczony do liczby poszczególnych użytkowników.

Zarządzanie dużym plikiem CSV lub dodawanie wielu pojedynczych adresatów może być kłopotliwe. Użycie Azure AD grup upraszcza ogólne zarządzanie symulacją.

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a>Pyt.: Czy firma Microsoft dostarcza ładunki w innych językach?

Odp.: Obecnie istnieje ponad 40 zlokalizowanych ładunków dostępnych w ponad 10 językach: chińskim (uproszczonym), chińskim (tradycyjnym), angielskim, francuskim, niemieckim, włoskim, japońskim, koreańskim, portugalskim, rosyjskim, hiszpańskim i holenderskim. Zauważyliśmy, że wszelkie bezpośrednie lub maszynowe tłumaczenia istniejących ładunków na inne języki doprowadzą do nieścisłości i zmniejszą istotność.

Mimo to możesz utworzyć własny ładunek w wybranym języku przy użyciu niestandardowego środowiska tworzenia ładunku. Zdecydowanie zalecamy również zebranie istniejących ładunków, które były używane do kierowania do użytkowników w określonej lokalizacji geograficznej. Innymi słowy, pozwól, aby osoby atakujące lokalizowały zawartość.

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a>Pyt.: Jak mogę przełączyć się na inne języki dla portalu administracyjnego i środowiska szkoleniowego?

Odc. Na platformie Microsoft 365 lub Office 365 konfiguracja języka jest specyficzna i scentralizowana dla każdego konta użytkownika. Aby uzyskać instrukcje dotyczące sposobu zmiany ustawienia języka, zobacz [Zmienianie języka wyświetlania i strefy czasowej w usłudze Microsoft 365 dla firm](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).

Należy pamiętać, że synchronizacja zmiany konfiguracji może potrwać do 30 minut we wszystkich usługach.

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a>Pyt.: Czy mogę wyzwolić symulację testową, aby zrozumieć, jak wygląda przed rozpoczęciem pełnoprawnej kampanii?

Odpowiedź: Tak, możesz! Na ostatniej stronie **Przeglądanie symulacji** w kreatorze, aby utworzyć nową symulację, istnieje możliwość **wysłania testu**. Ta opcja spowoduje wysłanie przykładowego komunikatu symulacji wyłudzania informacji do aktualnie zalogowanego użytkownika. Po zweryfikowaniu wiadomości wyłudzającej informacje w skrzynce odbiorczej możesz przesłać symulację.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Przycisk Wyślij test na stronie Przeglądanie symulacji" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a>Pyt.: Czy mogę kierować do użytkowników należących do innej dzierżawy w ramach tej samej kampanii symulacji?

Odp. Nie. Obecnie symulacje obejmujące wiele dzierżaw nie są obsługiwane. Sprawdź, czy wszyscy użytkownicy docelowi znajdują się w tej samej dzierżawie. Wszyscy użytkownicy korzystający z wielu dzierżaw lub użytkownicy-goście zostaną wykluczeni z kampanii symulacji.

### <a name="q-how-does-region-aware-delivery-work"></a>Pyt.: Jak działa dostarczanie z obsługą regionów?

Odświadczanie: Dostarczanie z obsługą regionu używa atrybutu TimeZone skrzynki pocztowej docelowego użytkownika i logiki "nie wcześniej", aby określić, kiedy ma zostać dostarczona wiadomość. Rozważmy na przykład następujący scenariusz:

- O godzinie 7:00 w strefie czasowej Pacyfiku (UTC-8) administrator tworzy i planuje rozpoczęcie kampanii o godzinie 9:00 tego samego dnia.
- UserA znajduje się we wschodniej strefie czasowej (UTC-5).
- UserB znajduje się również w strefie czasowej Pacyfiku.

Tego samego dnia o godzinie 9:00 komunikat symulacji jest wysyłany do usługi UserB. W przypadku dostarczania z obsługą regionu komunikat nie jest wysyłany do użytkownika UserA tego samego dnia, ponieważ godzina 9:00 czasu pacyficznego to 12:00 czasu wschodniego. Zamiast tego wiadomość jest wysyłana do użytkownika UserA o godzinie 9:00 czasu wschodniego następnego dnia.

Dlatego podczas początkowego przebiegu kampanii z włączonym dostarczaniem z obsługą regionu może się wydawać, że komunikat symulacji został wysłany tylko do użytkowników w określonej strefie czasowej. Jednak w miarę upływu czasu coraz więcej użytkowników wchodzi w zakres, docelowi użytkownicy będą się zwiększać.


### <a name="q-does-microsoft-collect-or-store-any-information-that-users-enter-at-the-credential-harvest-sign-in-page-used-in-the-credential-harvest-simulation-technique"></a>Pyt.: Czy firma Microsoft zbiera lub przechowuje jakiekolwiek informacje wprowadzane przez użytkowników na stronie logowania Credential Harvest używanej w technice symulacji poświadczeń?

Odp. Nie. Wszelkie informacje wprowadzone na stronie logowania do zbioru poświadczeń są odrzucane w trybie dyskretnym. Tylko "kliknięcie" jest rejestrowane w celu przechwycenia zdarzenia naruszenia zabezpieczeń. Firma Microsoft nie zbiera, nie rejestruje ani nie przechowuje żadnych szczegółów wprowadzonych przez użytkowników w tym kroku.
