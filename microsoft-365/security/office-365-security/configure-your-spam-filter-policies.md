---
title: Konfigurowanie zasad filtrowania spamu
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 316544cb-db1d-4c25-a5b9-c73bbcf53047
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorzy mogą dowiedzieć się, jak wyświetlać, tworzyć, modyfikować i usuwać zasady ochrony przed spamem w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d72b99b73a7c399147360364fc2de0a6cee6435b
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128728"
---
# <a name="configure-anti-spam-policies-in-eop"></a>Konfigurowanie zasad ochrony przed spamem w ramach EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych przychodzące wiadomości e-mail są automatycznie chronione przed spamem przez EOP. Funkcja EOP używa zasad ochrony przed spamem (znanych również jako zasady filtrowania spamu lub zasady filtrowania zawartości) w ramach ogólnej ochrony organizacji przed spamem. Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem](anti-spam-protection.md).

Administratorzy mogą wyświetlać, edytować i konfigurować (ale nie usuwać) domyślne zasady ochrony przed spamem. Aby uzyskać większy stopień szczegółowości, można również utworzyć niestandardowe zasady ochrony przed spamem, które mają zastosowanie do określonych użytkowników, grup lub domen w organizacji. Zasady niestandardowe zawsze mają pierwszeństwo przed zasadami domyślnymi, ale można zmienić priorytet (kolejność uruchamiania) zasad niestandardowych.

Zasady ochrony przed spamem można skonfigurować w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomicznym programem PowerShell EOP dla organizacji bez Exchange Online  skrzynki pocztowe).

Podstawowe elementy zasad ochrony przed spamem to:

- **Zasady filtrowania spamu**: określa akcje dotyczące werdyktów filtrowania spamu i opcji powiadomień.
- **Reguła filtru spamu**: określa priorytet i filtry adresatów (do kogo mają zastosowanie zasady) dla zasad filtru spamu.

Różnica między tymi dwoma elementami nie jest oczywista podczas zarządzania zasadami ochrony przed spamem w portalu Microsoft 365 Defender:

- Podczas tworzenia zasad ochrony przed spamem tworzysz regułę filtru spamu i skojarzone zasady filtru spamu w tym samym czasie, używając tej samej nazwy dla obu tych zasad.
- Podczas modyfikowania zasad ochrony przed spamem ustawienia związane z nazwą, priorytetem, włączoną lub wyłączoną, a filtry adresatów modyfikują regułę filtru spamu. Wszystkie inne ustawienia modyfikują skojarzone zasady filtrowania spamu.
- Po usunięciu zasad ochrony przed spamem zostanie usunięta reguła filtru spamu i skojarzone z nimi zasady filtrowania spamu.

W programie Exchange Online programie PowerShell lub autonomicznym programie PowerShell EOP zasady i reguła są zarządzane oddzielnie. Aby uzyskać więcej informacji, zobacz sekcję [Use Exchange Online PowerShell or standalone EOP PowerShell to configure anti-spam policies (Konfigurowanie zasad ochrony przed spamem](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies)) w dalszej części tego artykułu.

Każda organizacja ma wbudowane zasady ochrony przed spamem o nazwie Default, które mają następujące właściwości:

- Zasady są stosowane do wszystkich adresatów w organizacji, mimo że z zasadami nie jest skojarzona żadna reguła filtru spamu (filtry adresatów).
- Zasady mają niestandardową wartość priorytetu **Najniższa** , którą nie można zmodyfikować (zasady są zawsze stosowane jako ostatnie). Wszystkie utworzone zasady niestandardowe mają zawsze wyższy priorytet.
- Zasady to zasady domyślne (właściwość **IsDefault** ma wartość `True`) i nie można usunąć zasad domyślnych.

Aby zwiększyć skuteczność filtrowania spamu, można utworzyć niestandardowe zasady ochrony przed spamem z bardziej rygorystycznymi ustawieniami stosowanymi do określonych użytkowników lub grup użytkowników.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby dodawać, modyfikować i usuwać zasady ochrony przed spamem, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do zasad ochrony przed spamem, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Aby zapoznać się z naszymi zalecanymi ustawieniami zasad ochrony przed spamem, zobacz [Ustawienia zasad ochrony przed spamem w usłudze EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Nie można całkowicie wyłączyć filtrowania spamu, ale możesz użyć reguły przepływu poczty (znanej również jako reguła transportu), aby pominąć większość filtrowania spamu w wiadomościach przychodzących (na przykład w przypadku kierowania wiadomości e-mail za pośrednictwem usługi ochrony lub urządzenia innej firmy przed dostarczeniem do Microsoft 365). Aby uzyskać więcej informacji, zobacz [Używanie reguł przepływu poczty do ustawiania poziomu ufności spamu (SCL) w wiadomościach](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).
  - Komunikaty wyłudzające informacje o wysokim poziomie pewności są nadal filtrowane. Nie ma to wpływu na inne funkcje EOP (na przykład komunikaty są zawsze skanowane pod kątem złośliwego oprogramowania).
  - Jeśli musisz pominąć filtrowanie spamu dla skrzynek pocztowych SecOps lub symulacji wyłudzania informacji, nie używaj reguł przepływu poczty. Aby uzyskać więcej informacji, zobacz [Konfigurowanie dostarczania symulacji wyłudzania informacji innym firmom użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych Usługi SecOps](configure-advanced-delivery.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-spam-policies"></a>Tworzenie zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender

Utworzenie niestandardowych zasad ochrony przed spamem w portalu Microsoft 365 Defender powoduje utworzenie reguły filtru spamu i skojarzonych zasad filtru spamu w tym samym czasie przy użyciu tej samej nazwy dla obu.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz zasady,** a następnie wybierz pozycję **Przychodzący** z listy rozwijanej.

3. Zostanie otwarty kreator zasad. Na **stronie Nazwa zasad** skonfiguruj następujące ustawienia:
   - **Nazwa**: wprowadź unikatową, opisową nazwę zasad.
   - **Opis**: wprowadź opcjonalny opis zasad.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na wyświetlonej stronie **Użytkownicy, grupy i domeny** zidentyfikuj wewnętrznych adresatów, których dotyczą zasady (warunki adresatów):
   - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty e-mail.
   - **Grupy**:
     - Członkowie określonych grup dystrybucyjnych lub grup zabezpieczeń z obsługą poczty.
     - Określona Grupy Microsoft 365.
   - **Domeny**: Wszyscy adresaci w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

   Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Wiele wartości w tym samym warunku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

   - **Wyklucz tych użytkowników, grupy i domeny**: aby dodać wyjątki dla wewnętrznych adresatów, których dotyczą zasady (wyjątki adresatów), wybierz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie same jak warunki.

   > [!IMPORTANT]
   > Wiele różnych warunków lub wyjątków nie są addytywne; są inkluzywne. Zasady są stosowane _tylko_ do tych adresatów, którzy pasują do _wszystkich_ filtrów określonych adresatów. Na przykład należy skonfigurować warunek filtru adresata w zasadach z następującymi wartościami:
   >
   > - Adresatem jest: romain@contoso.com
   > - Odbiorca jest członkiem: Kierownictwo
   >
   > Zasady są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, zasady nie są do niego stosowane.
   >
   > Podobnie, jeśli używasz tego samego filtru adresata co wyjątek od zasad, zasady nie są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, polityka nadal ma do niego zastosowanie.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na wyświetlonej stronie **Próg zbiorczej poczty e-mail & właściwości spamu** skonfiguruj następujące ustawienia:

   - **Próg zbiorczej poczty e-mail**: określa poziom skarg zbiorczych (BCL) wiadomości wyzwalającej określoną akcję dla **werdyktu** filtrowania zbiorczego spamu skonfigurowanego na następnej stronie. Wyższa wartość wskazuje, że wiadomość jest mniej pożądana (bardziej prawdopodobne, że będzie przypominać spam). Wartość domyślna to 7. Aby uzyskać więcej informacji, zobacz [Poziom skarg zbiorczych (BCL) w usłudze EOP](bulk-complaint-level-values.md) i [Jaka jest różnica między wiadomościami-śmieciami a zbiorczą wiadomością e-mail?](what-s-the-difference-between-junk-email-and-bulk-email.md).

     Domyślnie ustawienie tylko programu PowerShell _MarkAsSpamBulkMail_ jest `On` w zasadach ochrony przed spamem. To ustawienie znacząco wpływa na wyniki werdyktu filtrowania **zbiorczego** :

     - **_MarkAsSpamBulkMail_ jest włączone**: lista BCL większa lub równa progowi jest konwertowana na listę SCL 6, która odpowiada werdyktowi filtrowania **spamu**, a akcja dotycząca werdyktu filtrowania **zbiorczego** jest podejmowana w wiadomości.
     - **_MarkAsSpamBulkMail_ jest wyłączony**: wiadomość jest ostemplowana listą BCL, ale nie jest podejmowana _żadna akcja_ dotycząca werdyktu filtrowania **zbiorczego** . W efekcie próg BCL i **akcja werdyktu filtrowania zbiorczego** nie mają znaczenia.

   - **Zwiększ wskaźnik spamu**, **oznacz jako tryb spamu**<sup>\*</sup> i **testu**: ustawienia zaawansowanego filtru spamu (ASF), które są domyślnie wyłączone.

     Aby uzyskać szczegółowe informacje na temat tych ustawień, zobacz [Zaawansowane ustawienia filtru spamu w EOP](advanced-spam-filtering-asf-options.md).

      <sup>\*</sup> Ustawienia **Zawiera określone języki** i **z tych krajów** nie są częścią usługi ASF.

   - **Zawiera określone języki**: kliknij pole i wybierz pozycję **Włączone** lub **Wyłączone** z listy rozwijanej. Jeśli ją włączysz, zostanie wyświetlone pole. Zacznij wpisywać nazwę języka w polu. Zostanie wyświetlona filtrowana lista obsługiwanych języków. Po znalezieniu języka, którego szukasz, wybierz go. Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij pozycję Usuń ![ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   - **Z tych krajów** _: kliknij pole i wybierz pozycję _ *On** lub **Off** z listy rozwijanej. Jeśli ją włączysz, zostanie wyświetlone pole. Zacznij wpisywać nazwę kraju w polu. Zostanie wyświetlona filtrowana lista obsługiwanych krajów. Po znalezieniu kraju, którego szukasz, wybierz go. Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij pozycję Usuń ![ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na wyświetlonej stronie **Akcje** skonfiguruj następujące ustawienia:

   - **Akcje wiadomości**: wybierz lub przejrzyj akcję do wykonania w oparciu o następujące werdykty filtrowania spamu:
     - **Spam**
     - **Spam o wysokim poziomie ufności**
     - **Wyłudzanie informacji**
     - **Wyłudzanie informacji o dużej pewności**
     - **Zbiorczego**

     Dostępne akcje dotyczące werdyktów filtrowania spamu opisano w poniższej tabeli.

     - Znacznik wyboru ( ![Znacznik wyboru.](../../media/checkmark.png)) wskazuje, że akcja jest dostępna (nie wszystkie działania są dostępne dla wszystkich werdyktów).
     - Gwiazdka ( <sup>\*</sup> ) po znaczniku wyboru wskazuje domyślną akcję werdyktu filtrowania spamu.

     |Akcja|Spam|High (Wysoki)<br>Zaufania<br>Spam|Wyłudzanie informacji|High (Wysoki)<br>Zaufania<br>Phishing|Zbiorczego|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**Przenieś wiadomość do folderu Wiadomości-śmieci**: wiadomość jest dostarczana do skrzynki pocztowej i przenoszona do folderu Wiadomości-śmieci. <sup>1</sup>|![Znacznik wyboru.](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)<sup>\*</sup>|
     |**Dodaj nagłówek X**: dodaje nagłówek X do nagłówka wiadomości i dostarcza wiadomość do skrzynki pocztowej. <p> Nazwę pola nagłówka X (a nie wartość) w dalszej części pola **tekstowego Dodaj ten nagłówek X** . <p> **W przypadku** werdyktów spamu i **spamu o wysokim poziomie zaufania** wiadomość zostanie przeniesiona do folderu Wiadomości-śmieci. <sup>1,2</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)||![Znacznik wyboru](../../media/checkmark.png)|
     |**Przedsyłanie wiersza tematu z tekstem**: dodaje tekst na początku wiersza tematu wiadomości. Wiadomość jest dostarczana do skrzynki pocztowej i przenoszona do folderu Wiadomości-śmieci. <sup>1,2</sup> <p> Wprowadź tekst w dalszej części **wiersza tematu Prefix z tym polem tekstowym** .|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)||![Znacznik wyboru](../../media/checkmark.png)|
     |**Przekieruj wiadomość na adres e-mail**: wysyła wiadomość do innych adresatów zamiast do zamierzonych adresatów. <p> Adresatów należy określić w dalszej części pola **Przekierowanie do tego adresu e-mail** .|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|
     |**Usuń komunikat**: w trybie dyskretnym usuwa całą wiadomość, w tym wszystkie załączniki.|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)||![Znacznik wyboru](../../media/checkmark.png)|
     |**Komunikat kwarantanny**: wysyła komunikat do kwarantanny zamiast do zamierzonych adresatów. <p> Określasz, jak długo komunikat powinien być przechowywany w kwarantannie później w polu **Kwarantanna** . <p> Zasady [kwarantanny](quarantine-policies.md) , które mają zastosowanie do komunikatów poddanych kwarantannie dla werdyktu filtru spamu, można określić w **wyświetlonym polu Wybierz zasady** . Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md). <sup>3.</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../../media/checkmark.png)|
     |**Brak akcji**|||||![Znacznik wyboru](../../media/checkmark.png)|

     > <sup>1</sup> EOP używa teraz własnego agenta dostarczania przepływu poczty, aby kierować wiadomości do folderu Wiadomości-śmieci zamiast używać reguły wiadomości-śmieci. Parametr _Enabled_ w poleceniu cmdlet **Set-MailboxJunkEmailConfiguration** nie ma już żadnego wpływu na przepływ poczty. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci w Exchange Online skrzynkach pocztowych](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > W środowiskach hybrydowych, w których funkcja EOP chroni lokalne Exchange skrzynki pocztowe, należy skonfigurować reguły przepływu poczty (nazywane również regułami transportu) w lokalnych Exchange. Te reguły przepływu poczty tłumaczą werdykt filtrowania spamu EOP, aby reguła wiadomości-śmieci w skrzynce pocztowej mogła przenieść wiadomość do folderu Wiadomości-śmieci. Aby uzyskać szczegółowe informacje, zobacz [Configure EOP to deliver spam to the Junk Email folder in hybrid environments (Konfigurowanie EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid)).
     >
     > <sup>2</sup> Możesz użyć wartości jako warunku w regułach przepływu poczty, aby filtrować lub kierować wiadomość.
     >
     > <sup>3</sup> Pusta wartość **Wybierz wartość zasad** oznacza, że są używane domyślne zasady kwarantanny dla danego werdyktu. Po późniejszej edycji zasad ochrony przed spamem lub wyświetleniu ustawień wyświetlana jest domyślna nazwa zasad kwarantanny. Aby uzyskać więcej informacji na temat domyślnych zasad kwarantanny używanych do werdyktów filtru spamu, zobacz [tę tabelę](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).
     >
     > Użytkownicy nie mogą wydawać własnych komunikatów, które zostały poddane kwarantannie jako wyłudzanie informacji o wysokim poziomie zaufania. W najlepszym razie administratorzy mogą skonfigurować zasady kwarantanny, aby użytkownicy mogli zażądać wydania komunikatów wyłudzających informacje o wysokim poziomie ufności w kwarantannie.

   - **Zachowaj spam w kwarantannie przez tyle dni**: określa czas przechowywania wiadomości w kwarantannie, jeśli **wybrano komunikat kwarantanny** jako akcję dotyczącą werdyktu filtrowania spamu. Po upływie okresu komunikat zostanie usunięty i nie będzie można go odzyskać. Prawidłowa wartość wynosi od 1 do 30 dni.

     > [!NOTE]
     > Wartość domyślna to 15 dni w domyślnych zasadach ochrony przed spamem i w nowych zasadach ochrony przed spamem utworzonych w programie PowerShell. Wartość domyślna to 30 dni w nowych zasadach ochrony przed spamem tworzonych w portalu Microsoft 365 Defender.
     >
     > To ustawienie określa również czas przechowywania komunikatów, które zostały poddane kwarantannie przez zasady **ochrony przed wyłudzaniem informacji** . Aby uzyskać więcej informacji, zobacz [Komunikaty poddane kwarantannie w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Defender](quarantine-email-messages.md).

   - **Dodaj ten tekst nagłówka X**: to pole jest wymagane i dostępne tylko wtedy, gdy wybrano opcję **Dodaj nagłówek X** jako akcję werdyktu filtrowania spamu. Określona wartość to *nazwa* pola nagłówka dodana do nagłówka komunikatu. *Wartość* pola nagłówka to zawsze `This message appears to be spam`.

     Maksymalna długość to 255 znaków, a wartość nie może zawierać spacji ani dwukropków (:).

     Jeśli na przykład wprowadzisz wartość `X-This-is-my-custom-header`, nagłówek X dodany do komunikatu będzie `X-This-is-my-custom-header: This message appears to be spam.`

     Jeśli wprowadzisz wartość zawierającą spacje lub dwukropki (:), wprowadzona wartość zostanie zignorowana, a domyślny nagłówek X zostanie dodany do komunikatu (`X-This-Is-Spam: This message appears to be spam.`).

   - **Przedślij wiersz tematu z tym tekstem**: to pole jest wymagane i dostępne tylko wtedy, gdy wybrano **pozycję Przedślij wiersz tematu z tekstem** jako akcję dla werdyktu filtrowania spamu. Wprowadź tekst, który ma zostać dodany na początku wiersza tematu wiadomości.

   - **Przekieruj na ten adres e-mail**: to pole jest wymagane i dostępne tylko wtedy, gdy **wybrano opcję Przekierowanie wiadomości na adres e-mail** jako akcję werdyktu filtrowania spamu. Wprowadź adres e-mail, na którym chcesz dostarczyć wiadomość. Można wprowadzić wiele wartości rozdzielonych średnikami (;).

   - **Włącz Wskazówki bezpieczeństwa**: domyślnie włączono Wskazówki bezpieczeństwa, ale można je wyłączyć, wyczyszczając pole wyboru.

   - **Włącz automatyczne przeczyszczanie o zerowej godzinie (ZAP)** : zap wykrywa i podejmuje działania w przypadku komunikatów, które zostały już dostarczone do Exchange Online skrzynek pocztowych. Aby uzyskać więcej informacji, zobacz [Automatyczne przeczyszczanie zerogodzin — ochrona przed spamem i złośliwym oprogramowaniem](zero-hour-auto-purge.md).

     Zap jest domyślnie włączony. Po włączeniu zap, dostępne są następujące ustawienia:

     - **Włącz zap dla wiadomości wyłudzających informacje**: domyślnie zap jest włączona dla wykrywania wyłudzania informacji, ale można go wyłączyć przez wyczyszczenie pola wyboru.
     - **Włącz zap dla wiadomości niepożądanych**: domyślnie zap jest włączona dla wykrywania spamu, ale można go wyłączyć przez wyczyszczenie pola wyboru.

   > [!NOTE]
   > Powiadomienia o spamie użytkowników końcowych zostały zastąpione _powiadomieniami kwarantanny_ w zasadach kwarantanny. Powiadomienia kwarantanny zawierają informacje o komunikatach objętych kwarantanną dla wszystkich obsługiwanych funkcji ochrony (nie tylko zasad ochrony przed spamem i werdyktów dotyczących zasad ochrony przed wyłudzaniem informacji). Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na wyświetlonym **wysuwu listy bloków Zezwalaj &** można skonfigurować nadawców wiadomości za pomocą adresu e-mail lub domeny poczty e-mail, które mogą pominąć filtrowanie spamu.

   W sekcji **Dozwolone** można skonfigurować dozwolonych nadawców i dozwolone domeny. W sekcji **Zablokowane** możesz dodać zablokowanych nadawców i zablokowane domeny.

   > [!IMPORTANT]
   >
   > Przed dodaniem domen do listy dozwolonych domen należy bardzo uważnie się zastanowić. Aby uzyskać więcej informacji, zobacz [Tworzenie list bezpiecznych nadawców w ramach EOP](create-safe-sender-lists-in-office-365.md)
   >
   > Nigdy nie należy dodawać [własnych zaakceptowanych domen](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) lub domen wspólnych (na przykład microsoft.com lub office.com) do listy dozwolonych domen. Jeśli te domeny mogą pomijać filtrowanie spamu, osoby atakujące mogą łatwo wysyłać do organizacji wiadomości podszywające się pod te zaufane domeny.
   >
   > Ręczne blokowanie domen przez dodanie domen do listy zablokowanych domen nie jest niebezpieczne, ale może zwiększyć obciążenie administracyjne. Aby uzyskać więcej informacji, zobacz [Create block sender lists in EOP (Tworzenie list nadawców blokowych w ramach EOP](create-block-sender-lists-in-office-365.md)).
   >
   > Będą chwile, kiedy nasze filtry przegapią komunikat, nie zgadzasz się z werdyktem filtrowania lub nadrabianie zaległości przez nasze systemy zajmuje trochę czasu. W takich przypadkach lista dozwolonych i lista zablokowanych są dostępne w celu zastąpienia bieżących werdyktów filtrowania. Należy jednak używać tych list oszczędnie i tymczasowo: listy longs mogą stać się niezarządzane, a nasz stos filtrowania powinien robić to, co powinno robić. Jeśli zamierzasz zachować dozwoloną domenę przez dłuższy czas, musisz poinformować nadawcę, aby sprawdził, czy domena jest uwierzytelniona, i ustawić opcję odrzucenia DMARC, jeśli tak nie jest.

   Kroki dodawania wpisów do dowolnej listy są takie same:

   1. Kliknij link do listy, którą chcesz skonfigurować:
      - **Dozwolone** \> **Nadawcy**: kliknij pozycję **Zarządzaj nadawcami (nn).**
      - **Dozwolone** \> **Domeny**: kliknij pozycję **Zezwalaj na domeny**.
      - **Zablokowany** \> **Nadawcy**: kliknij pozycję **Zarządzaj nadawcami (nn).**
      - **Zablokowany** \> **Domeny**: kliknij pozycję **Blokuj domeny**.

   2. W wyświetlonym wysuwie wykonaj następujące czynności:
      1. Kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Dodaj nadawców** lub **Dodaj domeny**.
      2. W wyświetlonym wysuwu **Dodaj nadawców** lub **Dodaj domeny** wprowadź adres e-mail nadawcy w polu **Nadawca** lub domenie w polu **Domena** . Podczas wpisywania wartość jest wyświetlana poniżej pola. Po zakończeniu wpisywania adresu e-mail lub domeny wybierz wartość poniżej pola.
      3. Powtórz poprzedni krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

      Po zakończeniu kliknij pozycję **Dodaj nadawców** lub **Dodaj domeny**.

      Po powrocie do głównego okna wysuwanego nadawcy lub dodane domeny zostaną wyświetlone na stronie. Aby usunąć wpis z tej strony, wykonaj następujące czynności:

      1. Wybierz co najmniej jeden wpis z listy. Możesz również użyć pola **Wyszukaj** , aby znaleźć wartości na liście.
      2. Po wybraniu co najmniej jednego wpisu ikona usuwania ![Ikona usuwania.](../../media/m365-cc-sc-delete-icon.png) Pojawia się.
      3. Kliknij ikonę usuwania ![Ikona usuwania.](../../media/m365-cc-sc-delete-icon.png) w celu usunięcia wybranych wpisów.

      Po zakończeniu kliknij pozycję **Gotowe**.

      Po powrocie na stronę **Listy zablokowanych & zezwalaj** kliknij przycisk **Dalej** po przeczytaniu, aby kontynuować.

8. Na wyświetlonej stronie **Przegląd** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Utwórz**.

9. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-spam-policies"></a>Wyświetlanie zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** poszukaj jednej z następujących wartości:
   - Wartość **Typ** to **Niestandardowe zasady ochrony przed spamem**
   - Wartość **Nazwa** to **Zasady ruchu przychodzącego ochrony przed spamem (domyślne)**

   Na liście zasad ochrony przed spamem są wyświetlane następujące właściwości:

   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**
   - **Type**

3. Po wybraniu zasad ochrony przed spamem przez kliknięcie nazwy ustawienia zasad są wyświetlane w wysuwnym oknie.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-spam-policies"></a>Modyfikowanie zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy zasady ochrony przed spamem, klikając nazwę:
   - Zasady niestandardowe utworzone w miejscu, w którym wartością w kolumnie **Typ** są **niestandardowe zasady ochrony przed spamem**.
   - Domyślne zasady o nazwie **Zasady ruchu przychodzącego ochrony przed spamem (domyślne).**

3. W wyświetlonym wysuwu szczegółów zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji na temat ustawień, zobacz poprzednią sekcję [Używanie portalu Microsoft 365 Defender do tworzenia zasad ochrony przed spamem](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) w tym artykule.

   W przypadku domyślnych zasad ochrony przed spamem sekcja **Zastosowane do** nie jest dostępna (zasady dotyczą wszystkich użytkowników) i nie można zmienić nazwy zasad.

Aby włączyć lub wyłączyć zasady lub ustawić kolejność priorytetów zasad, zobacz następujące sekcje.

### <a name="enable-or-disable-anti-spam-policies"></a>Włączanie lub wyłączanie zasad ochrony przed spamem

Nie można wyłączyć domyślnych zasad ochrony przed spamem.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** **niestandardowych zasad ochrony przed spamem** z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz jedną z następujących wartości:
   - **Zasady wyłączone**: aby włączyć zasady, kliknij pozycję ![Włącz ikonę.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz pozycję** .
   - **Zasady włączone**: aby wyłączyć zasady, kliknij pozycję Wyłącz ikonę ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij pozycję **Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanym oknie szczegółów zasad.

Po powrocie na stronę zasad głównych wartość **Stan** zasad będzie **włączona** lub **wyłączona**.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Ustawianie priorytetu niestandardowych zasad ochrony przed spamem

Domyślnie zasady ochrony przed spamem mają priorytet oparty na kolejności, w jakiej zostały utworzone (nowsze zasady mają niższy priorytet niż starsze zasady). Niższy numer priorytetu wskazuje wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

Aby zmienić priorytet zasad, kliknij pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** we właściwościach zasad (nie możesz bezpośrednio zmodyfikować numeru **Priorytet** w portalu Microsoft 365 Defender). Zmiana priorytetu zasad ma sens tylko wtedy, gdy masz wiele zasad.

 **Uwagi**:

- W portalu Microsoft 365 Defender można zmienić priorytet zasad ochrony przed spamem dopiero po jego utworzeniu. W programie PowerShell można zastąpić priorytet domyślny podczas tworzenia reguły filtru spamu (co może mieć wpływ na priorytet istniejących reguł).
- Zasady ochrony przed spamem są przetwarzane w kolejności ich wyświetlania (pierwsze zasady mają wartość **Priorytet** 0). Domyślne zasady ochrony przed spamem mają wartość priorytetu **Najniższa** i nie można jej zmienić.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** **niestandardowych zasad ochrony przed spamem** z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** na podstawie bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady ochrony przed spamem z **wartością Priorytet** **0** mają dostępną tylko opcję **Zmniejsz priorytet** .
   - Zasady ochrony przed spamem o najniższej wartości **Priorytet** (na przykład **3**) mają dostępną tylko opcję **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady ochrony przed spamem, zasady między wartościami o najwyższym i najniższym priorytecie mają dostępne opcje **Zwiększanie priorytetu** i **Zmniejszanie priorytetu** .

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Zwiększ priorytet** lub ![Zmniejsz priorytet **ikona**](../../media/m365-cc-sc-decrease-icon.png) Zmniejsz priorytet, aby zmienić wartość **Priorytet**.

4. Po zakończeniu kliknij przycisk **Zamknij** w wysuwanym oknie szczegółów zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-spam-policies"></a>Usuwanie niestandardowych zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender

W przypadku korzystania z portalu Microsoft 365 Defender w celu usunięcia niestandardowych zasad ochrony przed spamem zarówno reguła filtru spamu, jak i odpowiednie zasady filtru spamu są usuwane. Nie można usunąć domyślnych zasad ochrony przed spamem.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** **niestandardowych zasad ochrony przed spamem** z listy, klikając nazwę. W górnej części wyświetlonego menu wysuwanego szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Usuń ikonę](../../media/m365-cc-sc-delete-icon.png) zasad **Usuń zasady**.

3. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>Konfigurowanie zasad ochrony przed spamem przy użyciu Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP

Zgodnie z wcześniejszym opisem zasady ochrony przed spamem składają się z zasad filtru spamu i reguły filtru spamu.

W Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP widoczna jest różnica między zasadami filtrowania spamu a regułami filtru spamu. Zasady filtrowania spamu można zarządzać przy użyciu poleceń cmdlet -HostedContentFilterPolicy i zarządzać regułami filtrowania spamu **przy użyciu poleceń cmdlet -HostedContentFilterRule.\*** **\***

- W programie PowerShell najpierw utworzysz zasady filtru spamu, a następnie utworzysz regułę filtru spamu, która identyfikuje zasady, do których ma zastosowanie reguła.
- W programie PowerShell należy oddzielnie zmodyfikować ustawienia zasad filtru spamu i reguły filtru spamu.
- Gdy usuniesz zasady filtru spamu z programu PowerShell, odpowiednia reguła filtru spamu nie zostanie automatycznie usunięta i na odwrót.

Następujące ustawienia zasad ochrony przed spamem są dostępne tylko w programie PowerShell:

- Domyślnie jest to `On` parametr _MarkAsSpamBulkMail_. Efekty tego ustawienia zostały wyjaśnione we wcześniejszej części tego artykułu w sekcji [Używanie portalu Microsoft 365 Defender do tworzenia zasad ochrony przed spamem](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies).
- Następujące ustawienia powiadomień o kwarantannie spamu użytkowników końcowych:
  - Parametr _DownloadLink_, który pokazuje lub ukrywa link do narzędzia raportowania wiadomości-śmieci dla Outlook.
  - Parametr _EndUserSpamNotificationCustomSubject_ , którego można użyć do dostosowania wiersza tematu powiadomienia.

### <a name="use-powershell-to-create-anti-spam-policies"></a>Tworzenie zasad ochrony przed spamem przy użyciu programu PowerShell

Tworzenie zasad ochrony przed spamem w programie PowerShell to proces dwuetapowy:

1. Utwórz zasady filtru spamu.
2. Utwórz regułę filtru spamu określającą zasady filtru spamu, do których ma zastosowanie reguła.

 **Uwagi**:

- Możesz utworzyć nową regułę filtru spamu i przypisać do niej istniejące, nieskojarzone zasady filtru spamu. Reguły filtru spamu nie można skojarzyć z więcej niż jedną zasadą filtru spamu.
- Możesz skonfigurować następujące ustawienia dla nowych zasad filtru spamu w programie PowerShell, które nie są dostępne w portalu Microsoft 365 Defender, dopóki nie utworzysz zasad:
  - Utwórz nowe zasady jako wyłączone (_włączone_ `$false` w poleceniu cmdlet **New-HostedContentFilterRule** ).
  - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) w poleceniu cmdlet **New-HostedContentFilterRule**).

- Nowe zasady filtrowania spamu utworzone w programie PowerShell nie są widoczne w portalu Microsoft 365 Defender, dopóki zasady nie zostaną przypisane do reguły filtru spamu.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>Krok 1. Tworzenie zasad filtrowania spamu przy użyciu programu PowerShell

Aby utworzyć zasady filtrowania spamu, użyj tej składni:

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

W tym przykładzie tworzone są zasady filtrowania spamu o nazwie Contoso Executives z następującymi ustawieniami:

- Wiadomości kwarantanny, gdy werdykt filtrowania spamu jest spamem lub spamem o wysokim poziomie ufności, i używają domyślnych [zasad kwarantanny](quarantine-policies.md) dla komunikatów poddanych kwarantannie (nie używamy parametrów _SpamQuarantineTag_ ani _HighConfidenceSpamQuarantineTag_ ).
- Lista BCL 7, 8 lub 9 wyzwala akcję dla werdyktu filtrowania spamu wiadomości e-mail zbiorczej.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania [zasad kwarantanny](quarantine-policies.md) do użycia w zasadach filtru spamu, zobacz [Używanie programu PowerShell do określania zasad kwarantanny w zasadach ochrony przed spamem](quarantine-policies.md#anti-spam-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-spam-filter-rule"></a>Krok 2. Tworzenie reguły filtru spamu przy użyciu programu PowerShell

Aby utworzyć regułę filtru spamu, użyj tej składni:

```PowerShell
New-HostedContentFilterRule -Name "<RuleName>" -HostedContentFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

W tym przykładzie zostanie utworzona nowa reguła filtru spamu o nazwie Contoso Executives z następującymi ustawieniami:

- Zasady filtrowania spamu o nazwie Contoso Executives są skojarzone z regułą.
- Reguła ma zastosowanie do członków grupy o nazwie Contoso Executives Group.

```PowerShell
New-HostedContentFilterRule -Name "Contoso Executives" -HostedContentFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-HostedContentFilterRule](/powershell/module/exchange/new-hostedcontentfilterrule).

### <a name="use-powershell-to-view-spam-filter-policies"></a>Wyświetlanie zasad filtrowania spamu przy użyciu programu PowerShell

Aby zwrócić listę podsumowań wszystkich zasad filtrowania spamu, uruchom następujące polecenie:

```PowerShell
Get-HostedContentFilterPolicy
```

Aby zwrócić szczegółowe informacje o określonych zasadach filtrowania spamu, użyj tej składni:

```PowerShell
Get-HostedContentFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Ten przykład zwraca wszystkie wartości właściwości dla zasad filtru spamu o nazwie Kierownictwo.

```PowerShell
Get-HostedContentFilterPolicy -Identity "Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

### <a name="use-powershell-to-view-spam-filter-rules"></a>Wyświetlanie reguł filtrowania spamu za pomocą programu PowerShell

Aby wyświetlić istniejące reguły filtru spamu, użyj następującej składni:

```PowerShell
Get-HostedContentFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Aby zwrócić listę podsumowań wszystkich reguł filtrowania spamu, uruchom następujące polecenie:

```PowerShell
Get-HostedContentFilterRule
```

Aby filtrować listę według reguł włączonych lub wyłączonych, uruchom następujące polecenia:

```PowerShell
Get-HostedContentFilterRule -State Disabled
```

```PowerShell
Get-HostedContentFilterRule -State Enabled
```

Aby zwrócić szczegółowe informacje o określonej regule filtru spamu, użyj tej składni:

```PowerShell
Get-HostedContentFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Ten przykład zwraca wszystkie wartości właściwości reguły filtru spamu o nazwie Kierownictwo firmy Contoso.

```PowerShell
Get-HostedContentFilterRule -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-HostedContentFilterRule](/powershell/module/exchange/get-hostedcontentfilterrule).

### <a name="use-powershell-to-modify-spam-filter-policies"></a>Modyfikowanie zasad filtrowania spamu przy użyciu programu PowerShell

Inne niż następujące elementy te same ustawienia są dostępne podczas modyfikowania zasad filtrowania spamu w programie PowerShell, jak podczas tworzenia zasad zgodnie z opisem w [sekcji Krok 1: Tworzenie zasad filtrowania spamu za pomocą programu PowerShell we wcześniejszej](#step-1-use-powershell-to-create-a-spam-filter-policy) części tego artykułu.

- Przełącznik _MakeDefault_ , który zamienia określone zasady w zasady domyślne (stosowane do wszystkich użytkowników, zawsze **najniższy** priorytet i nie można ich usunąć) jest dostępny tylko po zmodyfikowaniu zasad filtru spamu w programie PowerShell.
- Nie można zmienić nazwy zasad filtru spamu (polecenie cmdlet **Set-HostedContentFilterPolicy** nie ma parametru _Name_ ). Po zmianie nazwy zasad ochrony przed spamem w portalu Microsoft 365 Defender zmieniasz tylko nazwę _reguły_ filtru spamu.

Aby zmodyfikować zasady filtru spamu, użyj tej składni:

```PowerShell
Set-HostedContentFilterPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania [zasad kwarantanny](quarantine-policies.md) do użycia w zasadach filtru spamu, zobacz [Używanie programu PowerShell do określania zasad kwarantanny w zasadach ochrony przed spamem](quarantine-policies.md#anti-spam-policies-in-powershell).

### <a name="use-powershell-to-modify-spam-filter-rules"></a>Modyfikowanie reguł filtrowania spamu przy użyciu programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły filtru spamu w programie PowerShell, jest parametr _Enabled_ , który umożliwia utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły filtrowania spamu, zobacz następną sekcję.

W przeciwnym razie podczas modyfikowania reguły filtru spamu w programie PowerShell nie są dostępne żadne dodatkowe ustawienia. Te same ustawienia są dostępne podczas tworzenia reguły zgodnie z opisem w sekcji [Krok 2: Używanie programu PowerShell do utworzenia reguły filtru spamu we wcześniejszej](#step-2-use-powershell-to-create-a-spam-filter-rule) części tego artykułu.

Aby zmodyfikować regułę filtru spamu, użyj tej składni:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" <Settings>
```

W tym przykładzie zmienia nazwę istniejącej reguły filtru spamu o nazwie `{Fabrikam Spam Filter}`.

```powershell
Set-HostedContentFilterRule -Identity "{Fabrikam Spam Filter}" -Name "Fabrikam Spam Filter"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-HostedContentFilterRule](/powershell/module/exchange/set-hostedcontentfilterrule).

### <a name="use-powershell-to-enable-or-disable-spam-filter-rules"></a>Włączanie lub wyłączanie reguł filtrowania spamu za pomocą programu PowerShell

Włączenie lub wyłączenie reguły filtru spamu w programie PowerShell umożliwia lub wyłącza całe zasady ochrony przed spamem (regułę filtru spamu i przypisane zasady filtrowania spamu). Nie można włączyć ani wyłączyć domyślnych zasad ochrony przed spamem (są zawsze stosowane do wszystkich adresatów).

Aby włączyć lub wyłączyć regułę filtru spamu w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-HostedContentFilterRule | Disable-HostedContentFilterRule> -Identity "<RuleName>"
```

Ten przykład wyłącza regułę filtru spamu o nazwie Dział marketingu.

```PowerShell
Disable-HostedContentFilterRule -Identity "Marketing Department"
```

W tym przykładzie włączono tę samą regułę.

```PowerShell
Enable-HostedContentFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Enable-HostedContentFilterRule](/powershell/module/exchange/enable-hostedcontentfilterrule) i [Disable-HostedContentFilterRule](/powershell/module/exchange/disable-hostedcontentfilterrule).

### <a name="use-powershell-to-set-the-priority-of-spam-filter-rules"></a>Ustawianie priorytetu reguł filtrowania spamu przy użyciu programu PowerShell

Wartość o najwyższym priorytecie, którą można ustawić dla reguły, to 0. Najniższa wartość, którą można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć kaskadowy wpływ na inne reguły. Jeśli na przykład masz pięć reguł niestandardowych (priorytety od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły filtru spamu w programie PowerShell, użyj następującej składni:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie ustawiono priorytet reguły o nazwie Dział marketingu na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich priorytety są zwiększane o 1).

```PowerShell
Set-HostedContentFilterRule -Identity "Marketing Department" -Priority 2
```

**Uwagi**:

- Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj parametru _Priority_ w poleceniu cmdlet **New-HostedContentFilterRule** .
- Domyślne zasady filtrowania spamu nie mają odpowiedniej reguły filtru spamu i zawsze mają niemodyfikowalną wartość priorytetu **Najniższa**.

### <a name="use-powershell-to-remove-spam-filter-policies"></a>Usuwanie zasad filtrowania spamu przy użyciu programu PowerShell

W przypadku usuwania zasad filtru spamu przy użyciu programu PowerShell odpowiednia reguła filtru spamu nie jest usuwana.

Aby usunąć zasady filtru spamu w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedContentFilterPolicy -Identity "<PolicyName>"
```

W tym przykładzie usunięto zasady filtru spamu o nazwie Dział marketingu.

```PowerShell
Remove-HostedContentFilterPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-HostedContentFilterPolicy](/powershell/module/exchange/remove-hostedcontentfilterpolicy).

### <a name="use-powershell-to-remove-spam-filter-rules"></a>Usuwanie reguł filtrowania spamu przy użyciu programu PowerShell

Jeśli używasz programu PowerShell do usunięcia reguły filtru spamu, odpowiednie zasady filtru spamu nie zostaną usunięte.

Aby usunąć regułę filtru spamu w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedContentFilterRule -Identity "<PolicyName>"
```

W tym przykładzie usunięto regułę filtru spamu o nazwie Dział marketingu.

```PowerShell
Remove-HostedContentFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-HostedContentFilterRule](/powershell/module/exchange/remove-hostedcontentfilterrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

### <a name="send-a-gtube-message-to-test-your-spam-policy-settings"></a>Wysyłanie wiadomości GTUBE w celu przetestowania ustawień zasad dotyczących spamu

> [!NOTE]
> Te kroki będą działać tylko wtedy, gdy organizacja poczty e-mail, z której wysyłasz wiadomość GTUBE, nie skanuje pod kątem spamu wychodzącego. Jeśli tak się stanie, nie możesz wysłać komunikatu testowego.

Ogólny test dla niechcianej wiadomości e-mail zbiorczej (GTUBE) to ciąg tekstowy dołączony do wiadomości testowej w celu zweryfikowania ustawień ochrony przed spamem w organizacji. Wiadomość GTUBE jest podobna do pliku tekstowego Europejskiego Instytutu Badań antywirusowych (EICAR) do testowania ustawień złośliwego oprogramowania.

Dołącz następujący tekst GTUBE do wiadomości e-mail w jednym wierszu bez spacji lub podziałów wierszy:

```text
XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
```
