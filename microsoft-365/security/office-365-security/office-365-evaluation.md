---
title: Ocena Ochrona usługi Office 365 w usłudze Microsoft Defender
description: Ochrona usługi Office 365 w usłudze Defender w trybie oceny tworzy zasady Ochrona usługi Office 365 w usłudze Defender poczty e-mail, które rejestrują werdykty, takie jak złośliwe oprogramowanie, ale nie działają na komunikatach.
keywords: ocena Office 365, Ochrona usługi Office 365 w usłudze Microsoft Defender, ocena usługi Office 365, wypróbowanie usług Office 365, Microsoft Defender, Ochrona punktu końcowego w usłudze Microsoft Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0f5d82e9baaca7209f8a91a7f1984aa38e3102e6
ms.sourcegitcommit: 74518b920b4166adccc10ea1581a62c44bb14edb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738757"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Ocena Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Ochrona usługi Office 365 w usłudze Microsoft Defender ocena jest dostępna w publicznej wersji zapoznawczej. Ta wersja zapoznawcza jest dostarczana bez umowy dotyczącej poziomu usług. Niektóre funkcje mogą nie być obsługiwane lub mogą mieć ograniczone możliwości.

Przeprowadzenie dokładnej oceny produktów zabezpieczających może pomóc w podejmowaniu świadomych decyzji dotyczących uaktualnień i zakupów. Pomaga to wypróbować możliwości produktu zabezpieczeń, aby ocenić, w jaki sposób może on pomóc zespołowi ds. operacji zabezpieczeń w codziennych zadaniach.

Środowisko oceny [Ochrona usługi Office 365 w usłudze Microsoft Defender](defender-for-office-365.md) ma na celu wyeliminowanie złożoności konfiguracji urządzenia i środowiska, dzięki czemu można skoncentrować się na ocenie możliwości Ochrona usługi Office 365 w usłudze Microsoft Defender. W trybie oceny wszystkie wiadomości wysyłane do Exchange Online skrzynek pocztowych można oceniać bez wskazywania rekordów MX firmie Microsoft. Ta funkcja ma zastosowanie tylko do ochrony poczty e-mail, a nie do klientów Office, takich jak Word, SharePoint lub Teams.

Jeśli nie masz jeszcze licencji, która obsługuje Ochrona usługi Office 365 w usłudze Microsoft Defender, możesz rozpocząć [bezpłatną 30-dniową ocenę](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) i przetestować możliwości w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Będziesz cieszyć się szybką konfiguracją i w razie potrzeby możesz ją łatwo wyłączyć.

> [!NOTE]
> Jeśli korzystasz z portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>, możesz rozpocząć ocenę Ochrona usługi Office 365 w usłudze Defender tutaj: **Zasady współpracy** \> & poczty e-mail **& zasady** \> **zasad** \> zagrożeń **w sekcji** **Inne**. Aby przejść bezpośrednio do strony **Tryb ewaluacji** , użyj polecenia <https://security.microsoft.com/atpEvaluation>.

## <a name="how-the-evaluation-works"></a>Jak działa ocena

Ochrona usługi Office 365 w usłudze Defender w trybie oceny tworzy zasady Ochrona usługi Office 365 w usłudze Defender poczty e-mail, które rejestrują werdykty, takie jak złośliwe oprogramowanie, ale nie działają na komunikatach. Nie musisz zmieniać konfiguracji rekordu MX.

W trybie oceny [Sejf Załączniki](safe-attachments.md), [linki Sejf](safe-links.md) i [analizy skrzynek pocztowych w zasadach ochrony przed złośliwym kodem](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) są konfigurowane w Twoim imieniu. Wszystkie zasady Ochrona usługi Office 365 w usłudze Defender są tworzone w trybie braku wymuszania w tle i nie są dla Ciebie widoczne.

W ramach konfiguracji tryb oceny konfiguruje również [rozszerzone filtrowanie dla łączników](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (nazywane również _pomijaniem listy_). Ta konfiguracja zwiększa dokładność filtrowania, zachowując informacje o adresach IP i nadawcy, które w przeciwnym razie są tracone, gdy poczta przechodzi przez bramę zabezpieczeń poczty e-mail (ESG) przed Ochrona usługi Office 365 w usłudze Defender. Ulepszone filtrowanie łączników zwiększa również dokładność filtrowania istniejących zasad ochrony przed spamem i wyłudzaniem informacji Exchange Online Protection (EOP).

Ulepszone filtrowanie łączników zwiększa dokładność filtrowania, ale może zmienić możliwość dostarczania niektórych komunikatów, jeśli masz grupę ESG przed Ochrona usługi Office 365 w usłudze Defender i obecnie nie pomijasz filtrowania EOP. Wpływ jest ograniczony do zasad EOP; Ochrona usługi Office 365 w usłudze Defender zasady skonfigurowane w ramach oceny są tworzone w trybie braku wymuszania. Aby zminimalizować potencjalny wpływ na środowisko produkcyjne, można pominąć większość filtrowania EOP, tworząc regułę przepływu poczty (znaną również jako reguła transportu), aby ustawić poziom ufności wiadomości (SCL) wiadomości na -1. Aby uzyskać szczegółowe informacje, zobacz [Używanie reguł przepływu poczty do ustawiania poziomu ufności spamu (SCL) w wiadomościach w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

Po skonfigurowaniu trybu oceny będziesz mieć raport dzienny z maksymalnie 90-dniowymi danymi kwantyfikującymi komunikaty, które zostałyby zablokowane, gdyby zasady zostały zaimplementowane (na przykład usunięcie, wysłanie na śmieci, kwarantanna). Raporty są generowane dla wszystkich wykrywania Ochrona usługi Office 365 w usłudze Defender i EOP. Raporty są agregowane według technologii wykrywania (na przykład personifikacji) i mogą być filtrowane według zakresu czasu. Ponadto raporty komunikatów można tworzyć na żądanie w celu tworzenia niestandardowych tabel przestawnych lub komunikatów szczegółowych za pomocą Eksploratora.

Dzięki uproszczonemu środowisku konfiguracji możesz skupić się na następujących zagadnieniach:

- Uruchamianie oceny
- Uzyskiwanie szczegółowego raportu
- Analizowanie raportu pod kątem akcji
- Przedstawianie wyniku oceny

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="licensing"></a>Licencjonowanie

Aby uzyskać dostęp do oceny, musisz spełnić wymagania licencyjne. Każda z następujących licencji będzie działać:

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 1
- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2
- Microsoft 365 E5, Zabezpieczenia platformy Microsoft 365 E5
- Office 365 E5

Jeśli nie masz jednej z tych licencji, musisz uzyskać licencję próbną.

#### <a name="trial"></a>Wersja próbna

Aby uzyskać licencję próbną dla Ochrona usługi Office 365 w usłudze Microsoft Defender, musisz mieć **rolę administratora rozliczeń** lub **rolę administratora globalnego**. Zażądaj uprawnień od osoby, która ma rolę administratora globalnego. [Dowiedz się więcej o subskrypcjach i licencjach](../../commerce/licenses/subscriptions-and-licenses.md)

Gdy masz odpowiednią rolę, zalecaną ścieżką jest uzyskanie licencji próbnej dla Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2) w Centrum administracyjne platformy Microsoft 365 at<https://admin.microsoft.com>, a następnie **przejście do** \> **pozycji Rozliczenia Zakup usług**  a następnie znajdź i wybierz wersję próbną Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2). Możesz też przejść bezpośrednio do strony wersji próbnej, korzystając z <https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)> opcji Wersja próbna obejmuje 30-dniową bezpłatną wersję próbną dla 25 licencji.

Będziesz mieć 30-dniowe okno z oceną do monitorowania i raportowania zaawansowanych zagrożeń. Możesz również kupić płatną subskrypcję, jeśli chcesz korzystać z pełnych możliwości Ochrona usługi Office 365 w usłudze Defender.

### <a name="roles"></a>Ról

**Exchange Online role** są wymagane do skonfigurowania Ochrona usługi Office 365 w usłudze Defender w trybie oceny. Przypisanie Microsoft 365 zgodności lub roli administratora zabezpieczeń nie będzie działać.

- [Dowiedz się więcej o uprawnieniach w Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Dowiedz się więcej o przypisywaniu ról administratora](../../admin/add-users/assign-admin-roles.md)

Potrzebne są następujące role:

|Zadanie|Rola (w Exchange Online)|
|---|---|
|Uzyskaj bezpłatną wersję próbną lub kup Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2)|Rola administratora rozliczeń lub rola administratora globalnego|
|Tworzenie zasad oceny|Rola Domeny zdalne i akceptowane; Rola administratora zabezpieczeń|
|Edytowanie zasad oceny|Rola Domeny zdalne i akceptowane; Rola administratora zabezpieczeń|
|Usuwanie zasad oceny|Rola Domeny zdalne i akceptowane; Rola administratora zabezpieczeń |
|Wyświetlanie raportu ewaluacji|Rola administratora zabezpieczeń lub rola czytelnika zabezpieczeń|

### <a name="enhanced-filtering-for-connectors"></a>Rozszerzone filtrowanie łączników

Zasady Exchange Online Protection, takie jak ochrona zbiorcza i ochrona przed spamem, pozostaną takie same. Jednak ocena włącza rozszerzone filtrowanie łączników, co może mieć wpływ na przepływ poczty i zasady Exchange Online Protection, chyba że zostały pominięte.

Ulepszone filtrowanie łączników umożliwia dzierżawcom korzystanie z ochrony przed fałszowaniem. Ochrona przed fałszowaniem nie jest obsługiwana, jeśli używasz bramy zabezpieczeń poczty e-mail bez włączenia rozszerzonego filtrowania łączników.

### <a name="urls"></a>Adresy url

Adresy URL zostaną zdetonowane podczas przepływu poczty. Jeśli nie chcesz detonować określonych adresów URL, odpowiednio zarządzaj listą dozwolonych adresów URL. Aby uzyskać szczegółowe informacje [, zobacz Zarządzanie listą dozwolonych/zablokowanych dzierżaw](tenant-allow-block-list.md) .

Linki adresów URL w treściach wiadomości e-mail nie będą zawijane, aby zmniejszyć wpływ na klientów.

### <a name="email-routing"></a>Routing poczty e-mail

Przygotuj odpowiednie szczegóły, które będą potrzebne do skonfigurowania sposobu, w jaki poczta e-mail jest obecnie kierowana, w tym nazwę łącznika przychodzącego kierującego pocztę. Jeśli używasz tylko Exchange Online Protection, nie będziesz mieć łącznika. [Dowiedz się więcej o przepływie poczty i routingu poczty e-mail](/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Obsługiwane scenariusze routingu poczty e-mail obejmują:

- **Partner innej firmy i/lub lokalny dostawca usług**: łącznik przychodzący, który chcesz ocenić, używa dostawcy innej firmy i/lub używasz rozwiązania do zabezpieczeń poczty e-mail w środowisku lokalnym.
- **Tylko Microsoft Exchange Online Protection**: dzierżawa, którą chcesz ocenić, używa Office 365 zabezpieczeń poczty e-mail, a rekord Mail Exchange (MX) wskazuje firmie Microsoft.

### <a name="email-security-gateway"></a>Brama zabezpieczeń poczty e-mail

Jeśli używasz bramy zabezpieczeń poczty e-mail innej firmy, musisz znać nazwę dostawcy. Jeśli używasz lokalnej grupy ESG lub nieobsługiwanych dostawców, musisz znać publiczne adresy IP dla urządzeń.

Do obsługiwanych partnerów innych firm należą:

- Barracuda
- IronPort
- Mimecast
- Punkt dowodu
- Sophos
- Symantec
- Trend Micro

### <a name="scoping"></a>Zakresu

Będziesz mieć możliwość określania zakresu oceny do łącznika ruchu przychodzącego. Jeśli nie skonfigurowano łącznika, zakres oceny umożliwi administratorom zbieranie danych od dowolnego użytkownika w dzierżawie w celu oceny Ochrona usługi Office 365 w usłudze Defender.

## <a name="get-started-with-the-evaluation"></a>Wprowadzenie z oceną

Znajdź kartę konfiguracji Ochrona usługi Office 365 w usłudze Microsoft Defender oceny w portalu Microsoft 365 Defender z następujących punktów dostępu:

- **Punkty końcowe** \> **Zarządzanie lukami w** \> zabezpieczeniach **Pulpit nawigacyjny** (<https://security.microsoft.com/tvm_dashboard>)
- Współpraca \> **& poczty e-mail** **Zasady & reguł** \> **Zasady zagrożeń** (<https://security.microsoft.com/threatpolicy>)
- **Raporty** \> Współpraca \> **& poczty e-mail** **Raporty współpracy & poczty e-mail** (<https://security.microsoft.com/emailandcollabreport>)

## <a name="setting-up-the-evaluation"></a>Konfigurowanie oceny

Po uruchomieniu przepływu konfiguracji dla oceny zostaną wyświetlone dwie opcje routingu. W zależności od potrzeb organizacji w zakresie konfiguracji i ewaluacji routingu poczty możesz wybrać, czy używasz dostawcy usług innych firm i/lub lokalnego, czy tylko Microsoft Exchange Online.

- Jeśli używasz partnera innej firmy i/lub lokalnego dostawcy usług, musisz wybrać nazwę dostawcy z menu rozwijanego. Podaj inne szczegóły związane z łącznikiem.

- Wybierz **Microsoft Exchange Online**, jeśli rekord MX wskazuje firmę Microsoft i masz Exchange Online skrzynkę pocztową.

Przejrzyj ustawienia i w razie potrzeby je edytuj. Następnie wybierz pozycję **Utwórz ocenę**. Powinien zostać wyświetlony komunikat z potwierdzeniem wskazujący, że konfiguracja została ukończona.

Raport oceny Ochrona usługi Office 365 w usłudze Microsoft Defender jest generowany raz dziennie. Wypełnienie danych może potrwać do 24 godzin.

### <a name="exchange-mail-flow-rules-optional"></a>Exchange reguł przepływu poczty (opcjonalnie)

Jeśli masz istniejącą bramę, włączenie trybu oceny spowoduje aktywowanie rozszerzonego filtrowania dla łączników. Ta funkcja zwiększa dokładność filtrowania przez zmianę przychodzącego adresu IP nadawcy. Ta funkcja może zmienić werdykty filtru, a jeśli nie pomijasz Exchange Online Protection, może to zmienić możliwość dostarczania niektórych komunikatów. W takim przypadku warto tymczasowo pominąć filtrowanie w celu przeanalizowania wpływu. Aby pominąć filtrowanie, utwórz regułę przepływu poczty (znaną również jako reguła transportu) w centrum administracyjnym Exchange (EAC), która ustawia listę SCL komunikatów na <https://admin.exchange.microsoft.com/#/transportrules> -1 (jeśli jeszcze jej nie masz). Aby uzyskać instrukcje, zobacz [Używanie reguł przepływu poczty do ustawiania poziomu ufności spamu (SCL) w wiadomościach w Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

## <a name="evaluate-capabilities"></a>Ocena możliwości

Po wygenerowaniu raportu oceny zobacz, ile zaawansowanych linków do zagrożeń, zaawansowanych załączników zagrożeń i potencjalnych personifikacji zostało zidentyfikowanych w wiadomościach e-mail i obszarach roboczych współpracy w organizacji.

Po wygaśnięciu wersji próbnej możesz nadal uzyskiwać dostęp do raportu przez 90 dni. Nie będzie jednak zbierać więcej informacji. Jeśli chcesz nadal korzystać z Ochrona usługi Office 365 w usłudze Microsoft Defender po wygaśnięciu wersji próbnej, upewnij się, że [kupisz płatną subskrypcję dla Ochrona usługi Office 365 w usłudze Microsoft Defender (plan 2)](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA).

Możesz przejść do **Ustawienia**, aby zaktualizować routing lub wyłączyć ocenę w dowolnym momencie. Należy jednak ponownie przejść przez ten sam proces konfiguracji, jeśli zdecydujesz się kontynuować ocenę po jej wyłączeniu.

## <a name="provide-feedback"></a>Przekazywanie opinii

Twoja opinia pomaga nam lepiej chronić środowisko przed zaawansowanymi atakami. Podziel się swoim doświadczeniem i wrażeniami z możliwości produktów i wyników oceny.

Wybierz pozycję **Przekaż opinię** , aby poinformować nas, co myślisz.
