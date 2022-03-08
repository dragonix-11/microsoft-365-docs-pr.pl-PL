---
title: Konfigurowanie zasad Sejf Linków w programie Microsoft Defender dla Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: bdd5372d-775e-4442-9c1b-609627b94b5d
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak wyświetlać, tworzyć, modyfikować i usuwać Sejf Linki do stron internetowych oraz ustawienia linków Sejf linków globalnych w programie Microsoft Defender dla Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7d4cbaccab3eca371114eec92fe1bf89b2c0e353
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312981"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Konfigurowanie zasad Sejf Linków w programie Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych korzystających z programu [Microsoft Defender dla Office 365](defender-for-office-365.md). Jeśli jesteś użytkownikiem domowym i szukasz informacji na temat bezpiecznych linków w u Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sejf Linki w programie [Microsoft Defender dla programu Office 365](defender-for-office-365.md) zapewniają skanowanie adresów URL przychodzących wiadomości e-mail w przepływie poczty e-mail oraz czas weryfikacji kliknięciem adresów URL i linków w wiadomościach e-mail oraz w innych lokalizacjach. Aby uzyskać więcej informacji, zobacz [linki Sejf w programie Microsoft Defender dla Office 365](safe-links.md).

Mimo że nie istnieją domyślne zasady Sejf, wstępnie ustawione zasady zabezpieczeń wbudowanej  ochrony zapewniają ochronę linków programu Sejf wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach Sejf Linków). Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender for Office 365](preset-security-policies.md).

Możesz również użyć procedur określonej w tym artykule, aby utworzyć Sejf linków do witryn, które dotyczą konkretnych użytkowników, grup lub domen.

> [!NOTE]
>
> Poza zasadami linków do stron **Sejf konfigurowane** są ustawienia globalne Sejf linków. Aby uzyskać instrukcje, [zobacz Konfigurowanie ustawień globalnych Sejf linków w programie Microsoft Defender dla Office 365](configure-global-settings-for-safe-links.md).
>
> Administratorzy powinni rozważyć różne ustawienia konfiguracji linków Sejf sieci. Jedną z dostępnych opcji jest uwzględnianie informacji umożliwiających identyfikację użytkownika w Sejf linków. Ta funkcja umożliwia *zespołom Security Ops* badanie potencjalnego naruszenia bezpieczeństwa użytkownika, podjęcia działań naprawczych i ograniczenia kosztownych naruszeń zabezpieczeń.

Zasady programu Sejf Links można skonfigurować w portalu usługi Microsoft 365 Defender lub w programie PowerShell (Exchange Online PowerShell dla uprawnionych organizacji Microsoft 365 ze skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online, ale za pomocą programu Microsoft Defender Office 365 subskrypcji dodatków).

Podstawowe elementy zasad grupy Sejf łącza:

- Zasady bezpiecznych **linków: włącz** ochronę linków w programie Sejf, włącz skanowanie adresów URL w czasie rzeczywistym, określ, czy przed dostarczeniem wiadomości ma się odczekać na ukończenie skanowania w czasie rzeczywistym, włącz skanowanie wiadomości wewnętrznych, określ, czy chcesz śledzić kliknięcia adresów URL użytkowników, oraz określ, czy chcesz zezwolić użytkownikom na kliknięcie pierwotnego adresu URL.
- **Reguła bezpiecznych linków**: określa priorytet i filtry adresatów (do kogo mają zastosowanie zasady).

Różnica między tymi dwoma elementami nie jest widoczna, gdy zarządzasz zasadami linków do stron Sejf w portalu Microsoft 365 Defender sieci:

- Gdy tworzysz zasady Sejf linków, w rzeczywistości tworzysz jednocześnie regułę bezpiecznych linków i skojarzone z nią zasady bezpiecznych linków, używając dla obu tych zasad tej samej nazwy.
- Podczas modyfikowania zasad usługi Sejf, ustawienia dotyczące nazwy, priorytetu, włączonego lub wyłączonego oraz filtrów adresatów modyfikują regułę bezpiecznych łączy. Wszystkie inne ustawienia modyfikują skojarzone zasady bezpiecznych linków.
- Gdy usuniesz zasady Sejf linków, reguła bezpiecznych linków i skojarzone z nimi zasady bezpiecznych linków zostaną usunięte.

W Exchange Online PowerShell lub autonomicznym programie PowerShell usługi EOP zasady i reguła są zarządzane osobno. Aby uzyskać więcej informacji, zobacz sekcję Konfigurowanie zasad Exchange Online programu PowerShell lub autonomicznego programu [EOP Power Sejf Shell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) w dalszej części tego artykułu.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu, musisz mieć przypisane uprawnienia:
  - Aby tworzyć, modyfikować i usuwać zasady usługi Sejf Links, musisz być członkiem grup ról Zarządzanie organizacją lub **Administrator** zabezpieczeń **w portalu usługi** Microsoft 365 Defender i członkiem grupy ról Zarządzanie organizacją w programie Exchange Online. 
  - Aby mieć dostęp tylko do odczytu do Sejf linków, musisz być członkiem grup ról Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender i](permissions-microsoft-365-security-center.md) [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Dodanie użytkowników do odpowiedniej Azure Active Directory głównej w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender oraz uprawnienia do innych funkcji w  Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  . - Grupa **ról Zarządzanie organizacją tylko** do odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) umożliwia również dostęp tylko do odczytu tej funkcji.

- Aby uzyskać informacje o naszych zalecanych Sejf zasadach dotyczących linków, [zobacz Sejf ustawienia zasad linków](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Zezwalaj na zastosowanie nowych lub zaktualizowanych zasad do 6 godzin.

- [Nowe funkcje są stale dodawane do programu Microsoft Defender dla Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). W związku z dodaniem nowych funkcji może być konieczne dostosowanie istniejących zasad Sejf linków.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Tworzenie zasad Microsoft 365 Defender w portalu Sejf sieci Sejf

Utworzenie niestandardowych zasad Sejf linków w portalu usługi Microsoft 365 Defender powoduje utworzenie reguły bezpiecznych linków i skojarzonych z nią zasad bezpiecznych linków jednocześnie przy użyciu tej samej nazwy dla obu tych zasad.

1. W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Zasady & e-mail **& zasady** \>  \> zagrożeń Sejf **linki** **do** zasad. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

2. Na stronie **Sejf kliknij** ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.

3. Zostanie **otwarty kreator Sejf linków** do stron sieci Web. Na stronie **Nadaj nazwę zasadom** skonfiguruj następujące ustawienia:

   - **Nazwa**. Wprowadź unikatową nazwę opisową zasad.
   - **Opis**. Wprowadź opcjonalny opis zasad.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na **wyświetlonej stronie Użytkownicy i** domeny określ adresatów wewnętrznych, do których mają zastosowanie zasady (warunki adresata):
   - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty w organizacji.
   - **Grupy**: Określone grupy dystrybucyjne, grupy zabezpieczeń z obsługą poczty lub Microsoft 365 w organizacji.
   - **Domeny**: Wszyscy adresaci w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

   Kliknij w odpowiednim polu, zacznij wpisywać wartość i wybierz odpowiednią wartość z wyników. Powtórz ten proces tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   W przypadku użytkowników lub grup możesz użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale odpowiadające im nazwy wyświetlane są wyświetlane w wynikach. Dla użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Wiele wartości w tym samym warunku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). W różnych warunkach jest stosować logikę AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

   - **Wyklucz tych użytkowników,** grup i domen: Aby dodać wyjątki dla adresatów wewnętrznych, których zasady dotyczą (wyjątki adresata), zaznacz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie, jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na **wyświetlonej stronie** Ustawienia ochrony skonfiguruj następujące ustawienia:
   - **Wybierz akcję dla nieznanych, potencjalnie złośliwych adresów URL** w wiadomościach: Wybierz pozycję Wł Sejf, aby włączyć ochronę linków w wiadomościach e-mail. Jeśli to ustawienie jest włączyć, dostępne są następujące ustawienia:
     - **Stosowanie funkcji skanowania w czasie rzeczywistym w** celu wykrycia podejrzanych linków i linków, które wskazują pliki: zaznacz tę opcję, aby włączyć skanowanie linków w wiadomościach e-mail w czasie rzeczywistym. Jeśli to ustawienie jest dostępne, dostępne jest następujące ustawienie:
       - **Przed dostarczeniem** wiadomości poczekaj na ukończenie skanowania adresów URL: wybierz tę opcję, aby przed dostarczeniem wiadomości czekać na ukończenie skanowania adresu URL w czasie rzeczywistym.
     - **Stosowanie Sejf** do wiadomości e-mail wysyłanych w organizacji: wybierz tę opcję, aby zastosować zasady połączeń Sejf do wiadomości między nadawcami wewnętrznymi i adresatami wewnętrznymi.
   - **Wybierz akcję dla** nieznanych lub potencjalnie złośliwych adresów URL w programie Microsoft Teams: Wybierz  pozycję Wł Sejf, aby włączyć ochronę linków w Teams. Zwróć uwagę, że może to potrwać do 24 godzin.
   - **Nie śledź kliknięć użytkownika**: Pozostaw to ustawienie niewyznane, aby włączyć śledzenie kliknięć adresów URL w wiadomościach e-mail przez użytkowników.
   - **Nie zezwalaj użytkownikom na** klikanie w celu oryginalnego adresu URL: zaznacz tę opcję, aby zablokować użytkownikom możliwość klikania pierwotnego adresu URL na stronach [ostrzegawczych](safe-links.md#warning-pages-from-safe-links).
   - **Nie redaguj następujących adresów URL**: Zezwala na dostęp do określonych adresów URL, które w przeciwnym razie byłyby blokowane przez Sejf url.

     W polu wpisz adres URL lub wartość, a następnie kliknij przycisk **Dodaj**. Powtarzaj ten krok tyle razy, ile to konieczne.

     Aby usunąć istniejący wpis, kliknij pozycję ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok wpisu.

     Aby uzyskać informacje na temat składni wprowadzania, zobacz Składnia wpisów dla [listy "Nie zapisuj ponownie następujących adresów URL"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

   Aby uzyskać szczegółowe informacje na temat tych ustawień, zobacz [Sejf ustawienia](safe-links.md#safe-links-settings-for-email-messages) linków dla wiadomości e-mail i Sejf [ustawienia linków dla Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   Aby uzyskać więcej zalecanych wartości w ustawieniach zasad standardowych i ścisłych, [zobacz Sejf ustawienia zasad łączy](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na **wyświetlonej stronie** Powiadomienie wybierz jedną z następujących wartości dla ustawienia **Jak chcesz powiadomić użytkowników?**:
   - **Używanie domyślnego tekstu powiadomień**
   - **Użyj niestandardowego tekstu powiadomienia**: Jeśli wybierzesz tę wartość (długość nie może przekraczać 200 znaków), zostaną wyświetlone następujące ustawienia:
     - **Użyj Microsoft Translator do automatycznej lokalizacji**
     - **Niestandardowy tekst powiadomienia**: Wprowadź niestandardowy tekst powiadomienia w tym polu.

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na **wyświetlonej** stronie Recenzja przejrzyj ustawienia. Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

8. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Wyświetlanie zasad Microsoft 365 Defender linków w portalu Sejf użytkowników

1. W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Zasady & e-mail **& zasady** \>  \> zagrożeń Sejf **linki** **do** zasad. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

2. Na **stronie Sejf Linki** do stron sieci Web na liście zasad połączeń programu Sejf są wyświetlane następujące właściwości:
   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**

3. Po wybraniu zasady przez kliknięcie jej nazwy ustawienia zasad są wyświetlane w wysuwanych menu.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Modyfikowanie zasad Microsoft 365 Defender łącza sieci Sejf za pomocą portalu Sejf linków

1. W portalu Microsoft 365 Defender przejdź do **sekcji Zasady i reguły & zasady** \>  \> zagrożeń **w** \> sekcji **Sejf linków**.

2. Na stronie **Sejf wybierz** zasady z listy, klikając nazwę.

3. W wyświetlonym wysuwanych szczegółach zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji o ustawieniach, zobacz poprzednią sekcję Tworzenie zasad Microsoft 365 Defender [w portalu Sejf linków](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) w tym artykule.

Aby włączyć lub wyłączyć zasady albo ustawić kolejność priorytetu zasad, zobacz poniższe sekcje.

### <a name="enable-or-disable-safe-links-policies"></a>Włączanie lub wyłączanie zasad Sejf linków

1. W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Zasady & e-mail **& zasady** \>  \> zagrożeń Sejf **linki** **do** zasad. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

2. Na stronie **Sejf wybierz** zasady z listy, klikając nazwę.

3. U góry wyświetlonego wysuwana informacja o zasadach zostanie wyświetlona jedna z następujących wartości:
   - **Zasady wyłączone**: Aby włączyć zasady, kliknij ikonę ![Włącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz** .
   - **Zasady wł**.: Aby wyłączyć zasady, kliknij ikonę ![Wyłącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij **pozycję Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanych szczegółach zasad.

Na stronie głównej zasad wartość **Status** zasad będzie wł **.** lub **wyłączona**.

### <a name="set-the-priority-of-safe-links-policies"></a>Ustawianie priorytetu zasad Sejf połączeń

Domyślnie nowe Sejf mają priorytet, który zależy od kolejności ich utworzenia (nowsze zasady mają niższy priorytet niż starsze zasady). Numer niższego priorytetu oznacza wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Dwa zasady nie mogą mieć tego samego priorytetu i przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszej zasady.

Aby zmienić priorytet zasad, kliknij pozycję Zwiększ priorytet lub  Zmniejsz priorytet we  właściwościach zasad (nie można bezpośrednio zmodyfikować numeru Priorytet w portalu Microsoft 365 Defender). Zmiana priorytetu zasad jest sensowna tylko w przypadku wielu zasad.

**Uwaga**:

- W portalu Microsoft 365 Defender można zmienić priorytet zasad połączeń Sejf linków tylko po ich utworzeniu. W programie PowerShell można zastąpić domyślny priorytet podczas tworzenia reguły bezpiecznych linków (która może mieć wpływ na priorytet istniejących reguł).
- Sejf są przetwarzane w kolejności ich wyświetlania (pierwsza zasada ma wartość **Priorytet** 0). Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz Kolejność i [pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

1. W portalu Microsoft 365 Defender przejdź  \> <https://security.microsoft.com>do sekcji Zasady & e-mail **& zasady** \>  \> zagrożeń Sejf **linki** **do** zasad. Aby przejść bezpośrednio do **strony Sejf,** użyj .<https://security.microsoft.com/safelinksv2>

2. Na stronie **Sejf wybierz** zasady z listy, klikając nazwę.

3. U góry wyświetlonego wysuwu szczegółów zasad zobaczysz komunikat Zwiększ priorytet lub Zmniejsz  priorytet na podstawie  bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady o wartości **Priorytet** **0** mają dostęp tylko do opcji **Zmniejsz priorytet** .
   - Zasady o najmniejszej **wartości Priorytet** (na przykład **3**) mają dostęp tylko do opcji **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady, dla zasad o najwyższym i najniższym priorytecie są dostępne  zarówno opcje Zwiększ priorytet, jak **i Zmniejsz priorytet**.

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Ikona Zwiększ priorytet** lub ![Zmniejsz priorytet](../../media/m365-cc-sc-decrease-icon.png) **Zmniejszanie priorytetu** w celu zmiany **wartości Priorytet** .

4. Po zakończeniu kliknij pozycję **Zamknij w wysuwanych** szczegółach zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Usuwanie zasad Microsoft 365 Defender linków w portalu Sejf użytkowników

1. W portalu  Microsoft 365 Defender przejdź \> do sekcji & e-mail i zasad współpracy **& zasad** \>  \> zagrożeń Sejf **linków** **do** zasad.

2. Na stronie **Sejf wybierz** zasady z listy, klikając nazwę. W górnej części wyświetlonego wysuwania szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Ikona usuwania zasad](../../media/m365-cc-sc-delete-icon.png) **Usuń zasady**.

3. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Konfigurowanie Exchange Online programu PowerShell lub autonomicznego programu Power Sejf Shell usługi EOP

Zgodnie z wcześniejszym opisem zasady Sejf linków obejmują zasady bezpiecznych linków i bezpieczne linki.

W programie PowerShell widoczna jest różnica między zasadami bezpiecznych linków a regułami bezpiecznych linków. Zasady bezpiecznych linków można **\*** zarządzać przy użyciu polecenia cmdlet -SafeLinksPolicy, **\*** a regułami bezpiecznych linków można zarządzać przy użyciu polecenia cmdlet -SafeLinksRule.

- W programie PowerShell najpierw tworzysz zasady bezpiecznych linków, a następnie tworzysz regułę bezpiecznych linków identyfikującą zasady, których ta reguła dotyczy.
- W programie PowerShell ustawienia w zasadach bezpiecznych linków i regułę bezpiecznych linków można modyfikować osobno.
- Po usunięciu zasad bezpiecznych linków z programu PowerShell odpowiednia reguła bezpiecznych linków nie jest usuwana automatycznie i odwrotnie.

### <a name="use-powershell-to-create-safe-links-policies"></a>Tworzenie zasad linków do Sejf programu PowerShell

Tworzenie zasad Sejf linków sieciowych w programie PowerShell jest procesem dwuetapowym:

1. Tworzenie zasad bezpiecznych linków.
2. Utwórz regułę bezpiecznych linków określającą zasady bezpiecznych linków, których ta reguła dotyczy.

> [!NOTE]
>
> - Możesz utworzyć nową regułę bezpiecznych linków i przypisać do tej reguły istniejące, nieskojarzonych zasady bezpiecznych linków. Reguły bezpiecznych linków nie można skojarzyć z więcej niż jedną zasadą bezpiecznych linków.
>
> - W programie PowerShell można skonfigurować następujące ustawienia nowych bezpiecznych linków, które nie są dostępne w portalu programu Microsoft 365 Defender do momentu utworzenia zasad:
>   - Utwórz nowe zasady jako wyłączone (_włączone w_ `$false` poleceniach cmdlet **New-SafeLinksRule** ).
>   - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) dla polecenia cmdlet **New-SafeLinksRule**.
>
> - Nowe zasady bezpiecznych linków, które tworzysz w programie PowerShell, nie są widoczne w portalu usługi Microsoft 365 Defender, dopóki nie przypiszesz ich do reguły bezpiecznych linków.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>Krok 1. Tworzenie zasad bezpiecznych linków za pomocą programu PowerShell

Aby utworzyć zasady bezpiecznych linków, użyj poniższej składni:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-IsEnabled <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-DoNotAllowClickThrough <$true | $false>] [-DoNotTrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - Aby uzyskać szczegółowe informacje na temat składni wprowadzania dla parametru _DoNotRewriteUrls_ , zobacz Składnia wpisów listy "Nie zapisuj ponownie następujących adresów [URL"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).
>
> - Aby uzyskać dodatkową składnię dla parametru _DoNotRewriteUrls_ podczas modyfikowania istniejących bezpiecznych linków za pomocą polecenia cmdlet **Set-SafeLinksPolicy** , zobacz sekcję Modyfikowanie zasad bezpiecznych linków za pomocą programu [PowerShell](#use-powershell-to-modify-safe-links-policies) w dalszej części tego artykułu.

W tym przykładzie są owane zasady bezpiecznych linków o nazwie Contoso All z następującymi wartościami:

- Włącz skanowanie i ponowne wysyłanie adresów URL w wiadomościach e-mail.
- Włącz skanowanie adresów URL w programie Teams.
- Włącz skanowanie klikowanych adresów URL w czasie rzeczywistym, w tym klikane linki, które wskazują pliki.
- Przed dostarczeniem wiadomości poczekaj na ukończenie skanowania adresów URL.
- Włącz skanowanie adresów URL i ponowne pismo wiadomości wewnętrznych.
- Śledź kliknięcia użytkowników związane z ochroną usługi Sejf Links (nie używamy parametru _DoNotTrackUserClicks_, $false wartość domyślna to $false, co oznacza śledzenie kliknięć użytkownika).
- Nie zezwalaj użytkownikom na klikanie w celu oryginalnego adresu URL.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -IsEnabled $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -DoNotAllowClickThrough $true
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>Krok 2. Tworzenie reguły bezpiecznych linków przy użyciu programu PowerShell

Aby utworzyć regułę bezpiecznych linków, użyj poniższej składni:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

W tym przykładzie jest  biurze tworzenia reguły bezpiecznych linków o nazwie Contoso All z następującymi warunkami:

- Reguła jest skojarzona z zasadami bezpiecznych linków o nazwie Contoso All.
- Ta reguła dotyczy wszystkich adresatów w contoso.com domeny.
- Ponieważ nie używamy parametru _Priority_ , używany jest priorytet domyślny.
- Reguła jest włączona (nie używamy _parametru Enabled_ , a wartość domyślna to `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Wyświetlanie zasad bezpiecznych linków za pomocą programu PowerShell

Aby wyświetlić istniejące bezpieczne zasady linków, użyj następującej składni:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

W tym przykładzie zostanie wyświetlona lista podsumowania wszystkich bezpiecznych zasad linków.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

W tym przykładzie są zwracane szczegółowe informacje dotyczące zasad bezpiecznych linków o nazwie  Kierownictwo Contoso.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Wyświetlanie reguł bezpiecznych linków za pomocą programu PowerShell

Aby wyświetlić istniejące bezpieczne reguły linków, użyj następującej składni:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Ten przykład zwraca listę podsumowania wszystkich reguł bezpiecznych linków.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

Aby przefiltrować listę według włączonych lub wyłączonych reguł, uruchom następujące polecenia:

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

W tym przykładzie są zwracane szczegółowe informacje dotyczące reguły bezpiecznych linków o nazwie  Kierownictwo Contoso.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Modyfikowanie zasad bezpiecznych linków za pomocą programu PowerShell

Zasad bezpiecznych linków nie można zmienić w programie PowerShell (polecenie cmdlet **Set-SafeLinksPolicy** nie ma _parametru Name_ ). Po zmianie nazwy zasad Sejf linków w portalu Microsoft 365 Defender zmienisz tylko nazwę reguły bezpiecznych _linków_.

Jedyną dodatkową kwestią podczas modyfikowania zasad bezpiecznych linków w programie PowerShell jest dostępna składnia parametru _DoNotRewriteUrls_ (listy "Nie redaguj następujących adresów [URL](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)):

- Aby dodać wartości, które zastąpią wszelkie istniejące wpisy, użyj następującej składni: `"Entry1","Entry2,..."EntryN"`.
- Aby dodać lub usunąć wartości bez wpływu na inne istniejące wpisy, użyj następującej składni: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

W przeciwnym razie po utworzeniu zasad bezpiecznych linków będą dostępne te same ustawienia, co opisano w sekcji Krok 1. Tworzenie zasad bezpiecznych linków za pomocą programu [PowerShell](#step-1-use-powershell-to-create-a-safe-links-policy) we wcześniejszej części tego artykułu.

Aby zmodyfikować zasady bezpiecznych linków, użyj poniższej składni:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Modyfikowanie reguł bezpiecznych linków za pomocą programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły bezpiecznych linków w programie PowerShell, jest parametr _Enabled_ umożliwiający utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące bezpieczne reguły linków, zobacz następną sekcję.

W przeciwnym razie podczas tworzenia reguły będą dostępne te same ustawienia, co opisano w sekcji Krok 2. Tworzenie reguły bezpiecznych linków za pomocą programu [PowerShell](#step-2-use-powershell-to-create-a-safe-links-rule) we wcześniejszej części tego artykułu.

Aby zmodyfikować regułę bezpiecznych linków, użyj poniższej składni:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Włączanie lub wyłączanie reguł bezpiecznych linków za pomocą programu PowerShell

Włączenie lub wyłączenie reguły bezpiecznych linków w programie PowerShell włącza lub wyłącza całą zasadę Sejf Łączy (regułę bezpiecznych linków i przypisaną zasadę bezpiecznych linków).

Aby włączyć lub wyłączyć regułę bezpiecznych linków w programie PowerShell, użyj poniższej składni:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

W tym przykładzie wyłączyno regułę bezpiecznych linków o nazwie Dział marketingu.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

W tym przykładzie ta sama reguła jest włączana.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) i [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Ustawianie priorytetu reguł bezpiecznych linków przy użyciu programu PowerShell

Wartość najwyższego priorytetu, jaki można ustawić dla reguły, wynosi 0. Najniższa wartość, która można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć wpływ na inne reguły kaskadowe. Jeśli na przykład masz pięć reguł niestandardowych (priorytet od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły bezpiecznych linków w programie PowerShell, użyj następującej składni:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie dla reguły o nazwie Dział marketingu jest ustawiany priorytet na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich numery priorytetów są zwiększane o 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj zamiast tego _parametru Priority_ polecenia cmdlet **New-SafeLinksRule** .

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>Usuwanie zasad bezpiecznych linków za pomocą programu PowerShell

W przypadku usunięcia zasad bezpiecznych linków za pomocą programu PowerShell odpowiednia reguła bezpiecznych linków nie jest usuwana.

Aby usunąć zasady bezpiecznych linków w programie PowerShell, użyj poniższej składni:

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

W tym przykładzie zasady bezpiecznych linków o nazwie Dział marketingu są usuwane.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Usuwanie reguł bezpiecznych linków za pomocą programu PowerShell

Usunięcie reguły bezpiecznych linków za pomocą programu PowerShell nie powoduje usunięcia odpowiednich zasad bezpiecznych linków.

Aby usunąć regułę bezpiecznych linków w programie PowerShell, użyj poniższej składni:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

W tym przykładzie jest usuwana reguła bezpiecznych linków o nazwie Dział marketingu.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

Aby sprawdzić, Sejf linki skanują wiadomości, sprawdź dostępną usługę Microsoft Defender dla Office 365 raportów. Aby uzyskać więcej informacji, zobacz Wyświetlanie raportów dotyczących usługi [Defender dla](view-reports-for-mdo.md) Office 365 [i Używanie Eksploratora w Microsoft 365 Defender sieci.](threat-explorer.md)

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

Aby sprawdzić, czy zasady połączeń połączeń programu Sejf zostały pomyślnie utworzone, zmodyfikowane lub usunięte, wykonaj dowolną z następujących czynności:

- Na stronie **Sejf w** <https://security.microsoft.com/safelinksv2>portalu Microsoft 365 Defender sieci Web sprawdź listę zasad, wartości ich statusów i **wartości Priorytet**. Aby wyświetlić więcej szczegółów, wybierz zasady z listy, a następnie wyświetl szczegóły w wysuwanych listach.

- W Exchange Online PowerShell lub Exchange Online Protection PowerShell \<Name\> zastąp zasady lub regułę nazwą, uruchom następujące polecenie i sprawdź ustawienia:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
