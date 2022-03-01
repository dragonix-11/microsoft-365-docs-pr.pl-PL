---
title: Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak tworzyć, modyfikować i usuwać zasady ochrony przed wyłudzaniem informacji dostępne w organizacjach usługi Exchange Online Protection (EOP) z Exchange Online pocztowymi lub bez nich.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6321dcb41e276ccd03d048033e063572506a3c0f
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010703"
---
# <a name="configure-anti-phishing-policies-in-eop"></a>Konfigurowanie zasad ochrony przed wyłudzaniem informacji w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online istnieją domyślne zasady ochrony przed wyłudzaniem informacji, które zawierają ograniczoną liczbę włączonych funkcji ochrony przed fałszowaniami. . Aby uzyskać więcej informacji, zobacz [Ustawienia fałszowania w zasadach ochrony przed wyłudzaniem informacji](set-up-anti-phishing-policies.md#spoof-settings).

Administratorzy mogą wyświetlać, edytować i konfigurować (ale nie usuwać) domyślne zasady ochrony przed wyłudzaniem informacji. W celu większej szczegółowości możesz również tworzyć niestandardowe zasady ochrony przed wyłudzaniem informacji, które dotyczą konkretnych użytkowników, grup lub domen w organizacji. Zasady niestandardowe zawsze mają priorytet nad zasadami domyślnymi, ale priorytet (kolejność działania) zasad niestandardowych można zmienić.

Organizacje z Exchange Online pocztowymi mogą konfigurować zasady ochrony przed wyłudzaniem informacji w portalu usługi Microsoft 365 Defender lub w programie Exchange Online PowerShell. Autonomiczne organizacje EOP mogą korzystać tylko z portalu Microsoft 365 Defender firmowego.

Aby uzyskać informacje na temat tworzenia i modyfikowania bardziej zaawansowanych zasad ochrony przed wyłudzaniem informacji dostępnych w programie Microsoft Defender dla programu Office 365, zobacz Konfigurowanie zasad ochrony przed wyłudzaniem informacji w programie [Microsoft Defender](configure-mdo-anti-phishing-policies.md) dla systemu Office 365.

Podstawowe elementy zasad ochrony przed wyłudzaniem informacji są takie:

- **Zasady ochrony przed wyłudzaniem** informacji: Określa ustawienia ochrony przed wyłudzaniem informacji, które mają być włączane lub wyłączane, oraz akcje służące do stosowania opcji.
- **Reguła anti-phish**: Określa priorytet i filtry adresatów (do których mają zastosowanie zasady) dla zasad anty wyłudowych.

Różnica między tymi dwoma elementami nie jest widoczna w przypadku zarządzania zasadami ochrony przed wyłudzaniem informacji w portalu Microsoft 365 Defender sieci:

- Gdy tworzysz zasady ochrony przed wyłudzaniem informacji, w rzeczywistości tworzysz jednocześnie politykę anty wyłudzającą informacje i skojarzone z nią zasady anty wyłudzania informacji, używając tej samej nazwy dla obu tych zasad.
- Podczas modyfikowania zasad ochrony przed wyłudzaniem informacji ustawienia dotyczące nazwy, priorytetu, włączonego lub wyłączonego oraz filtrów adresatów modyfikują regułę anti-phish. Wszystkie inne ustawienia modyfikują skojarzone zasady ochrony przed wyłudami.
- Po usunięciu zasad ochrony przed wyłudzaniem informacji reguła anty wyłudzająca informacje i skojarzone z nią zasady anty wyłudzania informacji zostaną usunięte.

W Exchange Online PowerShell zasady i reguła są zarządzane osobno. Aby uzyskać więcej informacji, zobacz sekcję Exchange Online [PowerShell](#use-exchange-online-powershell-to-configure-anti-phishing-policies) do konfigurowania zasad ochrony przed wyłudzaniem informacji w dalszej części tego artykułu.

Każda organizacja ma wbudowane zasady ochrony przed wyłudzaniem informacji o nazwie Office365 AntiPhish Default, które mają następujące właściwości:

- Zasady są stosowane do wszystkich adresatów w organizacji, mimo że z tą zasadami nie jest skojarzona żadna reguła anty wyłudowa (filtry adresatów).
- Zasady mają niestandardową wartość priorytetu **Najniższa wartość,** których nie można modyfikować (zasady są zawsze stosowane jako ostatnie). Wszystkie zasady niestandardowe, które tworzysz, zawsze mają wyższy priorytet.
- Zasady są zasadami domyślnymi (właściwość **IsDefault** `True`ma wartość ) i nie można usunąć zasad domyślnych.

Aby zwiększyć skuteczność ochrony przed wyłudzaniem informacji, możesz utworzyć niestandardowe zasady ochrony przed wyłudzaniem informacji, które będą bardziej rygorystyczne i będą stosowane do konkretnych użytkowników lub grup użytkowników.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

  W autonomicznym programie PowerShell usługi EOP nie można zarządzać zasadami ochrony przed wyłudzaniem informacji.

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby dodawać, modyfikować i usuwać zasady ochrony przed wyłudzaniem informacji, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do zasad ochrony przed wyłudzaniem informacji, musisz być członkiem grup ról Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko** do odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również dostęp tylko do odczytu tej funkcji <sup>\*</sup>.

- Aby uzyskać informacje na temat naszych zalecanych ustawień zasad ochrony przed wyłudzaniem informacji, zobacz Ustawienia zasad ochrony przed wyłudzaniem informacji [eOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

- Odnów maksymalnie 30 minut na zastosowanie zaktualizowanych zasad.

- Aby uzyskać informacje o tym, gdzie w potoku filtrowania są stosowane zasady ochrony przed wyłudzaniem informacji, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Tworzenie zasad ochrony przed Microsoft 365 Defender wyłudzaniem informacji przy użyciu portalu sieci Microsoft 365 Defender

Utworzenie niestandardowych zasad ochrony przed wyłudzaniem informacji w portalu Microsoft 365 Defender powoduje utworzenie reguły anti-phish i skojarzonych z nią zasad anty wyłudzających informacje w tym samym czasie przy użyciu tej samej nazwy dla obu tych zasad.

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji & **e-mail** i zasad współpracy **& zasady** \>  \> zagrożeń zapobiegające wyłudzaniu **informacji.** Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **ochrona przed wyłudzaniem** informacji kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.

3. Zostanie otwarty kreator zasad. Na stronie **Nazwa zasad** skonfiguruj następujące ustawienia:
   - **Nazwa**. Wprowadź unikatową nazwę opisową zasad.
   - **Opis**. Wprowadź opcjonalny opis zasad.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na **wyświetlonej stronie Użytkownicy,** grupy i domeny zidentyfikuj adresatów wewnętrznych, których dotyczą zasady (warunki adresata):
   - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty w organizacji.
   - **Grupy**: Określone grupy dystrybucyjne, grupy zabezpieczeń z obsługą poczty lub Microsoft 365 w organizacji.
   - **Domeny**: Wszyscy adresaci w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

   Kliknij w odpowiednim polu, zacznij wpisywać wartość i wybierz odpowiednią wartość z wyników. Powtórz ten proces tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   W przypadku użytkowników lub grup możesz użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale odpowiadające im nazwy wyświetlane są wyświetlane w wynikach. Dla użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Wiele wartości w tym samym warunku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). W różnych warunkach jest stosować logikę AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

   - **Wyklucz tych użytkowników,** grup i domen: Aby dodać wyjątki dla adresatów wewnętrznych, których zasady dotyczą (wyjątki adresata), zaznacz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie, jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na **wyświetlonej &** ochrony przed wyłudzaniem informacji użyj pola wyboru Włącz  analizę fałszowania, aby włączyć lub wyłączyć analizę fałszowania. Wartość domyślna jest włączona (zaznaczona) i zalecamy pozostawienie jej włączonej. Na następnej stronie konfigurujesz akcję, która ma być akcją mającą na celu spoofedywną wiadomość.

   Aby wyłączyć analizę fałszowania, wyczyść to pole wyboru.

   > [!NOTE]
   > Nie musisz wyłączać ochrony przed fałszowaniem, jeśli rekord MX nie oznacza Microsoft 365. Zamiast tego włącz funkcję rozszerzonego filtrowania dla łączników. Aby uzyskać instrukcje, [zobacz Ulepszone filtrowanie łączników w programie Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na **wyświetlonej** stronie Akcje skonfiguruj następujące ustawienia:
   - **Jeśli wiadomość zostanie wykryta jako fałsz**: To ustawienie jest dostępne tylko wtedy, gdy na poprzedniej stronie wybrano opcję Włącz analizę fałszowania. Wybierz jedną z następujących akcji na liście rozwijanej dla wiadomości od zablokowanych sfałszowanych nadawców:
     - **Przenoszenie wiadomości do folderów wiadomości-śmieci adresatów**
     - **Poddaj** kwarantannie wiadomość: Jeśli wybierzesz  tę akcję, zostanie wyświetlone okno Zastosuj zasady kwarantanny, w którym wybierzesz zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez ochronę przed fałszerami. Zasady kwarantanny określają, co użytkownicy mogą robić w kwarantannie wiadomości i czy użytkownicy otrzymują powiadomienia kwarantanny. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

       Pusta wartość **Zastosuj zasady kwarantanny** oznacza, że są używane domyślne zasady kwarantanny (DefaultFullAccessPolicy do wykrywania fałszowania). Podczas późniejszego edytowania zasad ochrony przed wyłudzaniem informacji lub wyświetlania ustawień jest wyświetlana domyślna nazwa zasad kwarantanny. Aby uzyskać więcej informacji na temat domyślnych zasad kwarantanny, które są używane do obsługiwanych werdyktów filtrowania ochrony, zobacz [tę tabelę](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **Porady dotyczące bezpieczeństwa & wskaźników**:
     - **Pokazywanie pierwszego kontaktu porada dotycząca bezpieczeństwa**: Aby uzyskać więcej informacji, zobacz Pierwszy kontakt [porada dotycząca bezpieczeństwa](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - **Pokaż (?)**<sup>\*</sup> dla nieuwierzytanych nadawców w celu fałszowania: Dodaje znak zapytania (?) do zdjęcia nadawcy w polu Od w programie Outlook jeśli wiadomość nie przejdzie testów SPF lub DKIM i wiadomość  nie przejdzie uwierzytelniania DMARC lub [złożonego](email-validation-and-authentication.md#composite-authentication).
     - **Pokaż tag "za pośrednictwem**<sup>\*</sup>": dodaje tag za pośrednictwem (chris@contoso.com za pośrednictwem fabrikam.com) do adresu Od, jeśli różni się on od domeny w podpisie DKIM lub w adresie **MAIL FROM** .

     Aby włączyć ustawienie, zaznacz to pole wyboru. Aby ją wyłączyć, wyczyść to pole wyboru.

     <sup>\*</sup> To ustawienie jest dostępne tylko wtedy, **gdy na** poprzedniej stronie wybrano opcję Włącz analizę fałszowania. Aby uzyskać więcej informacji, zobacz [Nieuwierzyta nadawca](set-up-anti-phishing-policies.md#unauthenticated-sender).

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na **wyświetlonej** stronie Recenzja przejrzyj ustawienia. Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

8. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Wyświetlanie zasad ochrony przed Microsoft 365 Defender wyłudzaniem informacji przy użyciu portalu sieci Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji & **e-mail** i zasad współpracy **& zasady** \>  \> zagrożeń zapobiegające wyłudzaniu **informacji.** Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **Ochrona przed wyłudzaniem** informacji na liście zasad są wyświetlane następujące właściwości:

   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**
   - **Ostatnia modyfikacja**

3. Po wybraniu zasady przez kliknięcie jej nazwy ustawienia zasad są wyświetlane w wysuwanych menu.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Modyfikowanie zasad ochrony przed wyłudzaniem informacji za pomocą portalu Microsoft 365 Defender-mail

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji & **e-mail** i zasad współpracy **& zasady** \>  \> zagrożeń zapobiegające wyłudzaniu **informacji.** Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **Ochrona przed wyłudzaniem** informacji wybierz zasady z listy, klikając nazwę.

3. W wyświetlonym wysuwanych szczegółach zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji o ustawieniach, zobacz sekcję Używanie portalu [Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) do tworzenia zasad ochrony przed wyłudzaniem informacji we wcześniejszej części tego artykułu.

   W przypadku domyślnych zasad ochrony przed wyłudzaniem informacji sekcja Użytkownicy **,** grupy i domeny nie jest dostępna (zasady dotyczą wszystkich użytkowników) i nie można zmienić ich nazw.

Aby włączyć lub wyłączyć zasady albo ustawić kolejność priorytetu zasad, zobacz poniższe sekcje.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Włączanie lub wyłączanie niestandardowych zasad ochrony przed wyłudzaniem informacji

Nie można wyłączyć domyślnych zasad ochrony przed wyłudzaniem informacji.

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji & **e-mail** i zasad współpracy **& zasady** \>  \> zagrożeń zapobiegające wyłudzaniu **informacji.** Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **Ochrona przed wyłudzaniem** informacji wybierz z listy zasady niestandardowe, klikając nazwę.

3. U góry wyświetlonego wysuwana informacja o zasadach zostanie wyświetlona jedna z następujących wartości:
   - **Zasady wyłączone**: Aby włączyć zasady, kliknij ikonę ![Włącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz** .
   - **Zasady wł**.: Aby wyłączyć zasady, kliknij ikonę ![Wyłącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij **pozycję Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanych szczegółach zasad.

Na stronie głównej zasad wartość **Status** zasad będzie wł **.** lub **wyłączona**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Ustawianie priorytetu niestandardowych zasad ochrony przed wyłudzaniem informacji

Domyślnie zasady ochrony przed wyłudzaniem informacji mają priorytet na podstawie kolejności ich utworzenia (nowsze zasady mają niższy priorytet niż starsze zasady). Numer niższego priorytetu oznacza wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Dwa zasady nie mogą mieć tego samego priorytetu i przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszej zasady.

Aby zmienić priorytet zasad, kliknij pozycję Zwiększ priorytet lub  Zmniejsz priorytet we  właściwościach zasad (nie można bezpośrednio zmodyfikować numeru Priorytet w portalu Microsoft 365 Defender). Zmiana priorytetu zasad jest sensowna tylko w przypadku wielu zasad.

 **Uwagi**:

- W portalu Microsoft 365 Defender sieciOwym priorytet zasad ochrony przed wyłudzaniem informacji można zmienić tylko po ich utworzeniu. W programie PowerShell można zastąpić domyślny priorytet podczas tworzenia reguły zapobiegającej wyłudowi (która może mieć wpływ na priorytet istniejących reguł).
- Zasady ochrony przed wyłudzaniem informacji są przetwarzane w kolejności ich wyświetlania (pierwsza zasada ma **wartość Priorytet** 0). Domyślne zasady ochrony przed wyłudzaniem informacji mają wartość priorytetu **Najniższa wartość** i nie można jej zmienić.

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji & **e-mail** i zasad współpracy **& zasady** \>  \> zagrożeń zapobiegające wyłudzaniu **informacji.** Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **Ochrona przed wyłudzaniem** informacji wybierz z listy zasady niestandardowe, klikając nazwę.

3. U góry wyświetlonego wysuwu szczegółów zasad zobaczysz komunikat Zwiększ priorytet lub Zmniejsz  priorytet na podstawie  bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady o wartości **Priorytet** **0** mają dostęp tylko do opcji **Zmniejsz priorytet** .
   - Zasady o najmniejszej **wartości Priorytet** (na przykład **3**) mają dostęp tylko do opcji **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady, dla zasad o najwyższym i najniższym priorytecie są dostępne  zarówno opcje Zwiększ priorytet, jak **i Zmniejsz priorytet**.

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Ikona Zwiększ priorytet** lub ![Zmniejsz priorytet](../../media/m365-cc-sc-decrease-icon.png) **Zmniejszanie priorytetu** w celu zmiany **wartości Priorytet** .

4. Po zakończeniu kliknij pozycję **Zamknij w wysuwanych** szczegółach zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Usuwanie niestandardowych zasad ochrony przed wyłudzaniem informacji przy użyciu portalu Microsoft 365 Defender-mail

W przypadku usunięcia Microsoft 365 Defender wyłudzania informacji za pomocą portalu internetowego reguła anty wyłudzająca informacje i odpowiadające im zasady ochrony przed wyłudzaniem informacji są usuwane. Nie można usunąć domyślnych zasad ochrony przed wyłudzaniem informacji.

1. W portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji & **e-mail** i zasad współpracy **& zasady** \>  \> zagrożeń zapobiegające wyłudzaniu **informacji.** Aby przejść bezpośrednio do strony ochrony **przed wyłudzaniem** informacji, użyj .<https://security.microsoft.com/antiphishing>

2. Na stronie **Ochrona przed wyłudzaniem** informacji wybierz z listy zasady niestandardowe, klikając nazwę.

3. W górnej części wyświetlonego wysuwania szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Ikona usuwania zasad](../../media/m365-cc-sc-delete-icon.png) **Usuń zasady**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Konfigurowanie Exchange Online wyłudzania informacji przy użyciu programu PowerShell

Jak opisano wcześniej, zasady ochrony przed wyłudzaniem informacji składają się z zasad przeciw wyłudzających informacje i regułę anty wyłudzającą informacje.

W Exchange Online programu PowerShell różnica między zasadami ochrony przed wyłudami a regułami anti-phish jest widoczna. Do zarządzania zasadami wyłudzyniami używa się polecenia cmdlet -AntiPhishPolicy, a do zarządzania regułami anti-phish **\*należy używać polecenia cmdlet -AntiPhishRule**.**\***

- W programie PowerShell najpierw tworzysz zasady antyszowe, a następnie tworzysz regułę antyszyryjną identyfikującą zasady, których ta reguła dotyczy.
- W programie PowerShell ustawienia zasad ochrony przed wyłudami są modyfikowane oddzielnie.
- Po usunięciu zasad ochrony przed wyłudami w programie PowerShell odpowiadająca jej reguła antyszyryjna nie jest usuwana automatycznie i odwrotnie.

> [!NOTE]
> Poniższe procedury programu PowerShell nie są dostępne w autonomicznych organizacjach usługi EOP używających programu Exchange Online Protection PowerShell.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Tworzenie zasad ochrony przed wyłudzaniem informacji przy użyciu programu PowerShell

Tworzenie zasad przeciw wyłudzaniu informacji w programie PowerShell jest procesem dwuetapowym:

1. Tworzenie zasad ochrony przed wyłudami.
2. Utwórz regułę anti-phish określającą zasady ochrony przed wyłudami, których ta reguła dotyczy.

 **Uwagi**:

- Możesz utworzyć nową regułę anty wyłudzona i przypisać do tej reguły istniejące, nieskojarzonych zasady antyszówiwne. Reguła anti-phish nie może być skojarzona z więcej niż jedną zasadami anty wyłudzywu.

- W programie PowerShell można skonfigurować następujące ustawienia nowych zasad ochrony przed wyłudami, które nie są dostępne w portalu Microsoft 365 Defender, dopóki nie zostaną one skonfigurowane:

  - Utwórz nowe zasady jako wyłączone (_włączone dla_ `$false` polecenia cmdlet **New-AntiPhishRule** ).
  - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) dla polecenia cmdlet **New-AntiPhishRule**.

- Nowe zasady ochrony przed wyłudami, które tworzysz w programie PowerShell, nie są widoczne w portalu programu Microsoft 365 Defender, dopóki nie zostaną przypisane do reguły anty wyłudowej.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Krok 1. Tworzenie zasad anti-phish przy użyciu programu PowerShell

Aby utworzyć zasady ochrony przed wyłudami, użyj tej składni:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSpoofIntelligence <$true | $false>] [-AuthenticationFailAction <MoveToJmf | Quarantine>] [-EnableUnauthenticatedSender <$true | $false>] [-EnableViaTag <$true | $false>] [-SpoofQuarantineTag <QuarantineTagName>]
```

W tym przykładzie są  tworzyne zasady ochrony przed wyłudami o nazwie Kwarantanna badawcza z następującymi ustawieniami:

- Opis jest: Zasady działu badań.
- Zmienia domyślną akcję wykrywania fałszowania na kwarantannę i używa domyślnych [](quarantine-policies.md) zasad kwarantanny dla wiadomości poddanych kwarantannie (nie używamy _parametru SpoofQuarantineTag_).

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania zasad kwarantanny do używania w zasadach ochrony przed wyłudzaniem informacji, zobacz Określanie zasad kwarantanny w zasadach ochrony przed wyłudzaniem informacji za pomocą programu [PowerShell](quarantine-policies.md#anti-phishing-policies).[](quarantine-policies.md)

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Krok 2. Tworzenie reguły anti-phish przy użyciu programu PowerShell

Aby utworzyć regułę anti-phish, użyj tej składni:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

W tym przykładzie jest dowa reguła antyszyryjna o nazwie Dział badań o następujących warunkach:

- Reguła jest skojarzona z zasadami ochrony przed wyłudami o nazwie Kwarantanna badawcza.
- Reguła dotyczy członków grupy o nazwie Dział badań.
- Ponieważ nie używamy parametru _Priority_ , używany jest priorytet domyślny.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Wyświetlanie zasad ochrony przed wyłudami za pomocą programu PowerShell

Aby wyświetlić istniejące zasady ochrony przed wyłudami, użyj następującej składni:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

W tym przykładzie jest zwracana lista podsumowania wszystkich zasad anti-phish wraz z określonymi właściwościami.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

W tym przykładzie zwracane są wszystkie wartości właściwości zasad anty wyłudzających o nazwie Kadra kierownicza.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Wyświetlanie reguł ochrony przed wyłudami w programie PowerShell

Aby wyświetlić istniejące reguły ochrony przed wyłudami, użyj następującej składni:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

W tym przykładzie jest zwracana lista podsumowania wszystkich reguł anti-phish wraz z określonymi właściwościami.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Aby przefiltrować listę według włączonych lub wyłączonych reguł, uruchom następujące polecenia:

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

W tym przykładzie zwracane są wszystkie wartości właściwości reguły anty wyłudzających informacje o nazwie  Kierownictwo Contoso.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Modyfikowanie zasad ochrony przed wyłudamiami przy użyciu programu PowerShell

Oprócz poniższych elementów te same ustawienia są dostępne podczas modyfikowania zasad ochrony przed wyłudami w programie PowerShell, jak podczas tworzenia zasad zgodnie z opisem w Kroku 1. Tworzenie zasad ochrony przed wyłudami w tym artykule za pomocą programu [PowerShell](#step-1-use-powershell-to-create-an-anti-phish-policy) .

- Przełącznik _MakeDefault_, który zmienia określone zasady w zasady domyślne (stosowane do wszystkich, zawsze o niskim  priorytecie i nie można ich usuwać), jest dostępny tylko po zmodyfikowaniu zasad ochrony przed wyłudamiania informacji w programie PowerShell.
- Nie można zmienić nazwy zasad anti-phish (polecenie cmdlet **Set-AntiPhishPolicy** nie ma _parametru Name_ ). Zmiana nazwy zasad ochrony przed wyłudzaniem informacji w portalu Microsoft 365 Defender umożliwia jedynie zmianę nazwy reguły przeciw _wyłudzającej informacje_.

Aby zmodyfikować zasady ochrony przed wyłudami, użyj tej składni:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania zasad kwarantanny do używania w zasadach ochrony przed wyłudzaniem informacji, zobacz Określanie zasad kwarantanny w zasadach ochrony przed wyłudzaniem informacji za pomocą programu [PowerShell](quarantine-policies.md#anti-phishing-policies).[](quarantine-policies.md)

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Modyfikowanie reguł wyłudowych za pomocą programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły anti-phish w programie PowerShell, jest parametr _Enabled_ , który umożliwia utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły ochrony przed wyłudami, zobacz następną sekcję.

W przeciwnym razie podczas tworzenia reguły będą dostępne te same ustawienia, co opisano w sekcji Krok [2. Tworzenie reguły anti-phish](#step-2-use-powershell-to-create-an-anti-phish-rule) w tym artykule za pomocą programu PowerShell.

Aby zmodyfikować regułę anti-phish, użyj tej składni:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Włączanie lub wyłączanie reguł ochrony przed wyłudamiami za pomocą programu PowerShell

Włączenie lub wyłączenie reguły ochrony przed wyłudzaniem informacji w programie PowerShell włącza lub wyłącza całą zasadę ochrony przed wyłudzaniem informacji (czyli regułę anty wyłudzającą informacje i przypisane zasady ochrony przed wyłudzaniem informacji). Nie można włączyć ani wyłączyć domyślnych zasad ochrony przed wyłudzaniem informacji (są one zawsze stosowane do wszystkich adresatów).

Aby włączyć lub wyłączyć regułę anti-phish w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

W tym przykładzie wyłączyno regułę anti-phish o nazwie Dział marketingu.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

W tym przykładzie ta sama reguła jest włączana.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) i [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Ustawianie priorytetu reguł ochrony przed wyłudamiami za pomocą programu PowerShell

Wartość najwyższego priorytetu, jaki można ustawić dla reguły, wynosi 0. Najniższa wartość, która można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć wpływ na inne reguły kaskadowe. Jeśli na przykład masz pięć reguł niestandardowych (priorytet od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły anti-phish w programie PowerShell, użyj następującej składni:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie dla reguły o nazwie Dział marketingu jest ustawiany priorytet na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich numery priorytetów są zwiększane o 1).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Uwagi**:

- Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj zamiast tego _parametru Priority_ dla polecenia cmdlet **New-AntiPhishRule** .
- Domyślne zasady ochrony przed wyłudami nie mają odpowiadającej jej reguły anti-phish i zawsze mają niemodyfikowalny priorytet o wartości **Najniżej**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Usuwanie zasad ochrony przed wyłudami za pomocą programu PowerShell

W przypadku usunięcia zasad anti-phish przy użyciu programu PowerShell odpowiednia reguła antyszybka nie jest usuwana.

Aby usunąć zasady ochrony przed wyłudami w programie PowerShell, użyj tej składni:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

W tym przykładzie zasady ochrony przed wyłudami o nazwie Dział marketingu są usuwane.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Usuwanie reguł wyłudowych za pomocą programu PowerShell

Usunięcie reguły antyszybowej za pomocą programu PowerShell nie powoduje usunięcia odpowiednich zasad ochrony przed wyłudami.

Aby usunąć regułę anti-phish w programie PowerShell, użyj tej składni:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

W tym przykładzie jest usuwana reguła antyszybka o nazwie Dział marketingu.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Usuwanie błędu AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

Aby sprawdzić, czy zasady ochrony przed wyłudzaniem informacji zostały pomyślnie skonfigurowane w u usługi EOP, wykonaj dowolną z następujących czynności:

- Na stronie **Ochrona przed wyłudzaniem** informacji w Microsoft 365 Defender <https://security.microsoft.com/antiphishing>sieci Web sprawdź listę zasad, ich wartości **statusu** i **wartości Priority** (Priorytet). Aby wyświetlić więcej szczegółów, wybierz zasady z listy, klikając nazwę i wyświetlając szczegóły w wyświetlonym wysuwaniu.

- W Exchange Online PowerShell \<Name\> zastąp zasady lub regułę nazwą, uruchom następujące polecenie i sprawdź ustawienia:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
