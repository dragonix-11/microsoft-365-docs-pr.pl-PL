---
title: Zagadnienia dotyczące wdrażania szkoleń w czasie ataków i często zadawane pytania
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
description: Administratorzy mogą dowiedzieć się więcej o zagadnieniach związanych z wdrażaniem i często zadawanych pytaniach dotyczących symulacyjnej i szkolenia w zakresie ataków w organizacjach Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender planie 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 57b4d684e52fd51a2ece279cc7322389a953a17c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467802"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a>Zagadnienia dotyczące wdrażania szkoleń w czasie ataków i często zadawane pytania

Szkolenie symulacyjne z atakami Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Microsoft Defender Organizacje planują 2 na mierzenie ryzyka socjowego i zarządzanie nim przez umożliwienie tworzenia i zarządzania symulacyjnych wyłudzania informacji obsługiwanych w świecie rzeczywistym, w których są odimowane łady służące do wyłudzania informacji. Szkolenia ukierunkowane na działanie hiper targeted, dostarczone we współpracy z zabezpieczeniamiNova, pomagają w ulepszaniu wiedzy i zmieniania zachowań pracowników.

Aby uzyskać więcej informacji na temat rozpoczynania szkolenia z symezyjną ataków, zobacz Wprowadzenie [szkolenia z użyciem symezyjnych](attack-simulation-training-get-started.md) ataków.

Mimo że całe środowisko tworzenia i planowania przebiegów symulacyjnych zostało zaprojektowane tak, aby było swobodne i nieczytarne, czasy bieżące na skalę przedsiębiorstwa często wymagają planowania. Ten artykuł pomaga w odniesieniu do konkretnych wyzwań, które widzą jako nasi klienci, podczas uruchamiania symulacyjnych w swoich środowiskach.

## <a name="issues-with-end-user-experiences"></a>Problemy ze środowiskami użytkownika końcowego

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a>Adresy URL symulowania wyłudzania informacji zablokowane przez przeglądanie Sejf Google

Usługa reputacji adresu URL może zidentyfikować co najmniej jeden z adresów URL używanych przez szkolenie symulacyjne z atakami jako niebezpieczne. Przeglądanie Sejf Google Chrome blokuje niektóre symulowane adresy URL służące do wyłudzania informacji z treściwą wiadomością **z wyprzedzeniem**. Mimo że pracujemy z wieloma dostawcami reputacji adresów URL, aby zawsze zezwalać na adresy URL symulowania, nie zawsze mamy pełny zakres.

:::image type="content" source="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png" alt-text="Ostrzeżenie z wyprzedzeniem dotyczące witryny z deceptywną witryną w przeglądarce Google Chrome" lightbox="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png":::

Zwróć uwagę, że ten problem nie wpływa Microsoft Edge.

W ramach fazy planowania sprawdź dostępność adresu URL w obsługiwanych przeglądarkach sieci Web, zanim użyjemy adresu URL w kampanii służącej do wyłudzania informacji. Jeśli adresy URL są zablokowane przez usługę Google [Sejf Przeglądania](https://support.google.com/chrome/a/answer/7532419) internetu, postępuj zgodnie z tą wytycznymi firmy Google, aby zezwolić na dostęp do adresów URL.

Aby uzyskać [Wprowadzenie](attack-simulation-training-get-started.md) adresów URL używanych obecnie w trakcie szkolenia symulacyjnego w zakresie ataków, zobacz korzystanie z szkolenia symulacyjnego w zakresie ataków.

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a>Symulacja wyłudzania informacji i adresy URL administratorów zablokowane przez sieciowe rozwiązania serwera proxy i sterowniki filtrów

Zarówno adresy URL dla symulacyjnych wyłudzania informacji, jak i adresy URL administratorów mogą być blokowane lub upuszczane przez pośrednie urządzenia zabezpieczające lub filtry. Przykład:

- Zapory
- Web Application Firewall (WAF)
- Sterowniki filtru innych firm (na przykład filtry trybu kernelgo)

W tej warstwie zablokowano kilku klientów, jednak tak się dzieje. Jeśli wystąpią problemy, rozważ skonfigurowanie następujących adresów URL tak, aby pomijać skanowanie urządzeń zabezpieczających lub filtry zgodnie z wymaganiami:

- Symulowane adresy URL służące do wyłudzania informacji, jak opisano [Wprowadzenie przy użyciu szkolenia z użyciem symezyjnej próby wyłudzenia informacji](attack-simulation-training-get-started.md).
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a>Wiadomości symulacyjne, które nie są dostarczane do wszystkich użytkowników docelowych

Możliwe, że liczba użytkowników, którzy w rzeczywistości otrzymują wiadomości e-mail z symulacyjnej wiadomości e-mail, jest mniejsza niż liczba użytkowników, którzy zostali docelowi w czasie symulacyjnej. W ramach sprawdzania poprawności docelowej zostaną wykluczone następujące typy użytkowników:

- Nieprawidłowe adresy e-mail adresatów.
- Użytkownicy goście.
- Użytkownicy, którzy nie są już aktywni w usłudze Azure Active Directory (Azure AD).

Tylko prawidłowi użytkownicy, którzy nie są gośćmi z prawidłową skrzynką pocztową, będą uwzględniane w symulacyjnych przykładach. Jeśli do kierowania użytkowników używasz grup dystrybucyjnych lub grup zabezpieczeń z obsługą poczty, możesz użyć polecenia cmdlet [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember) w programie [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), aby wyświetlać i sprawdzać poprawność członków grupy dystrybucyjnej.

## <a name="issues-with-attack-simulation-training-reporting"></a>Problemy z raportowaniem szkoleń dotyczących symulacyjnych ataków

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a>Raporty szkoleniowe dotyczące symulacyjnych ataków nie zawierają żadnych szczegółów aktywności

Szkolenie symulacyjne dotyczące ataków zapewnia rozbudowane, pozwala uzyskać szczegółowe informacje, które informują Cię o postępie gotowości pracowników do działania w związku z zagrożeniami. Jeśli raporty szkoleniowe dotyczące symulacyjnych ataków nie są wypełnione danymi, sprawdź, czy w organizacji włączona jest opcja przeszukiwania dziennika inspekcji (domyślnie jest włączona).

Przeszukiwanie dziennika inspekcji jest wymagane w ramach szkolenia symetanii ataków, aby można było przechwytywać, nagrywać i odczytywać zdarzenia. Wyłączenie przeszukiwania dziennika inspekcji ma następujące konsekwencje dla szkolenia z symezyjną ataków:

- Dane raportowania nie są dostępne we wszystkich raportach. Raporty będą wyświetlane jako puste.
- Zadania szkoleniowe są blokowane, ponieważ dane są niedostępne.

Aby włączyć przeszukiwanie dziennika inspekcji, zobacz Włączanie lub wyłączanie wyszukiwania [w dzienniku inspekcji](../../compliance/turn-audit-log-search-on-or-off.md).

> [!NOTE]
> Puste szczegóły aktywności mogą być również spowodowane tym, że do użytkowników nie przypisano żadnych licencji E5. Upewnij się, że do aktywnego użytkownika przypisano co najmniej jedną licencję E5, aby się upewnić, że zdarzenia raportowania zostały zarejestrowane.

### <a name="simulation-reports-are-not-updated-immediately"></a>Raporty symulacyjne nie są aktualizowane natychmiast

Szczegółowe raporty symulacyjne nie są aktualizowane od razu po uruchomieniu kampanii. Nie martw się. takie zachowanie jest oczekiwane.

Każda kampania symulacyjna ma cykl życia. Podczas tworzenia po raz pierwszy symulowany jest w stanie **Zaplanowano** . Po rozpoczęciem symulacyjnej przechodzi ona do stanu **W toku** . Po ukończeniu przejścia symulacyjne do stanu **Ukończono** .

Podczas gdy symulowanie znajduje **się w stanie** zaplanowanym, raporty symulacyjne będą przeważnie puste. Na tym etapie aparat symulowania rozwiązuje adresy e-mail użytkowników docelowych, rozszerza grupy dystrybucyjne, usuwa użytkowników gości z listy itp.:

:::image type="content" source="../../media/attack-sim-training-faq-scheduled-state.png" alt-text="Szczegóły symulacyjne przedstawiające czas symulowania w stanie według harmonogramu" lightbox="../../media/attack-sim-training-faq-scheduled-state.png":::

Gdy symulowanie przejdzie na **etap W toku** , zauważysz informacje, które zaczynają docierać do raportowania:

:::image type="content" source="../../media/attack-sim-training-faq-in-progress-state.png" alt-text="Szczegóły symulacyjne przedstawiające czas symulowania w stanie w toku" lightbox="../../media/attack-sim-training-faq-in-progress-state.png":::

Aktualizacja poszczególnych raportów symulacyjnych po przejściu do stanu W **toku** może potrwać do 30 minut. Dane raportu są nadal kompilowane, aż do momentu osiągnięcia przez symulacyjne **stanu Ukończono** . Aktualizacje raportowania występują w następujących interwałach:

- Co 10 minut dla pierwszych 60 minut.
- Co 15 minut po 60 minutach do 2 dni.
- Co 30 minut po 2 dniach do 7 dni.
- Co 60 minut po 7 dniach.

Widżety na stronie **Przegląd** zapewniają szybką migawkę czasu pracy zabezpieczeń opartej na symulacyjnej pracy organizacji. Ponieważ te widżety odzwierciedlają ogólne zadania w zakresie zabezpieczeń i podróże w czasie, są one aktualizowane po zakończeniu każdej kampanii symulacyjnej.

> [!NOTE]
> Możesz użyć opcji **Eksportuj na** różnych stronach raportów, aby wyodrębnić dane.

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a>Wiadomości zgłoszone przez użytkowników jako próby wyłudzenia informacji nie są wyświetlane w raportach symulacyjnych

Raporty symulacyjne w szkoleniach dotyczących ataków zawierają szczegółowe informacje na temat aktywności użytkowników. Przykład:

- Użytkownicy, którzy klikli link w wiadomości.
- Użytkownicy, którzy podali swoje poświadczenia.
- Użytkownicy, którzy zgłosili wiadomość jako wyłudzanie informacji.

Jeśli wiadomości zgłoszone przez użytkowników jako próby wyłudzenia informacji nie są przechwytywane w raportach symulacyjnych symulacyjnych ćwiczeń dotyczących ataków, może być tam reguła przepływu poczty e-mail programu Exchange (znana również jako reguła transportu), która blokuje dostarczenie zgłoszonych wiadomości do firmy Microsoft. Sprawdź, czy reguły przepływu poczty e-mail nie blokują dostarczania na następujące adresy e-mail:

- junk@office365.microsoft.com
- abuse@messaging.microsoft.com
- phish@office365.microsoft.com
- nie\_ junk@office365.microsoft.com

## <a name="other-frequently-asked-questions"></a>Inne często zadawane pytania

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a>P: Jaka jest zalecana metoda kierowania użytkowników na kampanie symulacyjne?

O: Dla użytkowników docelowych dostępnych jest kilka opcji:

- Uwzględnij wszystkich użytkowników (obecnie dostępnych dla organizacji, które mają mniej niż 40 000 użytkowników).
- Wybierz konkretnych użytkowników.
- Wybierz użytkowników z pliku CSV (po jednym adresie e-mail w wierszu).
- Kierowanie grupowe w usłudze Azure AD.

Odkryliśmy, że kampanie, w których użytkownicy docelowi są identyfikowani przez grupy usługi Azure AD, na ogół ułatwiają zarządzanie.

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a>P. Czy istnieją ograniczenia dotyczące określania docelowych użytkowników podczas importowania z pliku CSV lub dodawania użytkowników?

O. Limit importowania adresatów z pliku CSV lub dodawania poszczególnych adresatów do symulacyjnej wartości to 40 000.

Adresatem może być pojedynczy użytkownik lub grupa. Grupa może zawierać setki lub tysiące adresatów, więc rzeczywisty limit nie jest umieszczany na liczbie pojedynczych użytkowników.

Zarządzanie dużym plikiem CSV lub dodawanie wielu pojedynczych adresatów może być uciążliwe. Korzystanie z grup usługi Azure AD upraszcza ogólne zarządzanie symulacją.

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a>P: Czy firma Microsoft dostarcza  payloads w innych językach?

O. Obecnie dostępnych jest ponad 40 zlokalizowanych ładówek w ponad 10 językach: chiński (uproszczony), chiński (tradycyjny), angielski, francuski, niemiecki, japoński, koreański, portugalski, rosyjski, hiszpański i holenderski. Zauważyliśmy, że bezpośrednie lub maszynowe tłumaczenie istniejących przekierowywów na inne języki spowoduje nieścisłości i zmniejszy się istotność.

W związku z tym możesz utworzyć własny ład w wybranej wersji językowej przy użyciu niestandardowego interfejsu tworzenia ładowania. Zdecydowanie zalecamy również zbieranie istniejących zbiorów zbiorów, które zostały użyte do kierowania użytkowników do konkretnych lokalizacji geograficznych. Innymi słowy pozwolić atakującym na zlokalizowanej zawartości.

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a>P. Jak mogę przełączyć się na inne języki w portalu administracyjnym i w witrynie szkoleniowej?

O. W Microsoft 365 lub Office 365 konfiguracja języka jest konfigurowana i scentralizowana dla każdego konta użytkownika. Aby uzyskać instrukcje dotyczące zmieniania ustawienia języka, zobacz Zmienianie języka wyświetlania i strefy czasowej w [programie Microsoft 365 dla firm](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).

Zauważ, że synchronizacja zmiany konfiguracji może potrwać do 30 minut we wszystkich usługach.

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a>P. Czy mogę uruchomić symulowanie testowe, aby zrozumieć, jak wygląda przed uruchomieniem pełnej kampanii?

O: Tak, możesz! Na ostatniej **stronie symulacyjnej przeglądu** w kreatorze w celu utworzenia nowej symulacyjnej istnieje opcja **Wyślij test**. Ta opcja spowoduje wysłanie przykładowego komunikatu symulacyjnego wyłudzania informacji do obecnie zalogowanego użytkownika. Po zweryfikowaniu wiadomości służącej do wyłudzania informacji w skrzynce odbiorczej możesz przesłać symulację.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Przycisk Wyślij test na stronie symulacyjnej recenzji" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a>P. Czy można kierować użytkowników należących do innej dzierżawy w ramach tej samej kampanii symulacyjnej?

Odp. Nie. Obecnie nie są obsługiwane symulowania dla wielu dzierżaw. Sprawdź, czy wszyscy docelowi użytkownicy znajdują się w tej samej dzierżawie. Użytkownicy korzystający z różnych dzierżaw lub goście zostaną wykluczeni z kampanii symulacyjnej.

### <a name="q-how-does-region-aware-delivery-work"></a>P: Jak działa dostarczanie w przypadku regionów?

O: Do określenia czasu dostarczenia wiadomości w regionie jest używany atrybut TimeZone skrzynki pocztowej użytkownika docelowego oraz logika "nie wcześniej". Rozważ na przykład następujący scenariusz:

- O 7:00 w strefie czasowej Pacyfiku (UTC-8) administrator tworzy i planuje kampanię, która rozpocznie się o 9:00 tego samego dnia.
- UserA znajduje się w strefie czasowej wschodniego (UTC-5).
- UżytkownikB znajduje się również w strefie czasowej Pacyfiku.

Tego samego dnia o godzinie 9:00 komunikat symulacyjnej jest wysyłany do użytkownika UserB. Dzięki dostarczeniu dla regionu wiadomość nie jest wysyłana do użytkownika W tym samym dniu, ponieważ czasu pacyficznego o 23:00 czasu wschodniego jest godzina 12:00 czasu wschodniego. Zamiast tego wiadomość jest wysyłana do użytkownika UserA o godzinie 9:00 czasu wschodniego następnego dnia.

W związku z tym w początkowym uruchomieniu kampanii z włączonym dostarczaniem w regionie świadomym może się wydawać, że komunikat symulujący został wysłany tylko do użytkowników w określonej strefie czasowej. Jednak wraz z upływem czasu i dojściem większej liczby użytkowników docelowych spowoduje ich zwiększenie.
