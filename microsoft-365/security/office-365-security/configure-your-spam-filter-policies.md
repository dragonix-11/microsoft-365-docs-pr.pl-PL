---
title: Konfigurowanie zasad filtru spamu
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
description: Administratorzy mogą dowiedzieć się, jak wyświetlać, tworzyć, modyfikować i usuwać zasady ochrony przed spamem w u Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8550d55553b1c406fa21ce362e201a8bbe3d5aea
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681309"
---
# <a name="configure-anti-spam-policies-in-eop"></a>Konfigurowanie zasad ochrony przed spamem w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 z skrzynkami pocztowymi w organizacjach Exchange Online lub autonomicznych organizacjach usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online przychodzące wiadomości e-mail są automatycznie chronione przed spamem przez usługę EOP. W ramach ogólnej ochrony przed spamem w organizacji EOP są używane zasady ochrony przed spamem (nazywane również zasadami filtrowania spamu lub filtrami zawartości). Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem](anti-spam-protection.md).

Administratorzy mogą wyświetlać, edytować i konfigurować (ale nie usuwać) domyślne zasady ochrony przed spamem. W celu większej szczegółowości możesz również tworzyć niestandardowe zasady ochrony przed spamem, które dotyczą konkretnych użytkowników, grup lub domen w organizacji. Zasady niestandardowe zawsze mają priorytet nad zasadami domyślnymi, ale priorytet (kolejność działania) zasad niestandardowych można zmienić.

Zasady ochrony przed spamem można skonfigurować w portalu usługi Microsoft 365 Defender lub w programie PowerShell (Exchange Online PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online  skrzynki pocztowe).

Podstawowe elementy zasad ochrony przed spamem to:

- **Zasady filtrowania spamu**: Określa akcje dotyczące werdyktów filtrowania spamu oraz opcje powiadomień.
- **Reguła filtru spamu**: Określa priorytet i filtry adresatów (do których mają zastosowanie zasady) dla zasad filtrowania spamu.

Różnica między tymi dwoma elementami nie jest widoczna w przypadku zarządzania zasadami ochrony przed spamem w portalu Microsoft 365 Defender wiadomości:

- Gdy tworzysz zasady ochrony przed spamem, w rzeczywistości jednocześnie tworzysz regułę filtrowania spamu i skojarzone z nią zasady filtrowania spamu, używając dla obu tych zasad tej samej nazwy.
- Podczas modyfikowania zasad ochrony przed spamem ustawienia dotyczące nazwy, priorytetu, włączonego lub wyłączonego oraz filtrów adresatów modyfikują regułę filtru spamu. Wszystkie inne ustawienia modyfikują skojarzone zasady filtru spamu.
- Gdy usuniesz zasady ochrony przed spamem, reguła filtru spamu i skojarzone z nimi zasady filtrowania spamu zostaną usunięte.

W Exchange Online PowerShell lub autonomicznym programie PowerShell usługi EOP zasady i reguła są zarządzane osobno. Aby uzyskać więcej informacji, zobacz sekcję Konfigurowanie zasad ochrony przed [spamem Exchange Online programu PowerShell lub autonomicznego programu EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies) w dalszej części tego artykułu.

Każda organizacja ma wbudowane zasady ochrony przed spamem o nazwie Domyślne, które mają następujące właściwości:

- Zasady są stosowane do wszystkich adresatów w organizacji, nawet jeśli z nimi nie jest skojarzona reguła filtru spamu (filtry adresatów).
- Zasady mają niestandardową wartość priorytetu **Najniższa wartość,** których nie można modyfikować (zasady są zawsze stosowane jako ostatnie). Wszystkie zasady niestandardowe, które tworzysz, zawsze mają wyższy priorytet.
- Zasady są zasadami domyślnymi (właściwość **IsDefault** `True`ma wartość ) i nie można usunąć zasad domyślnych.

Aby zwiększyć skuteczność filtrowania spamu, możesz utworzyć niestandardowe zasady ochrony przed spamem z bardziej rygorystycznymi ustawieniami, które są stosowane do konkretnych użytkowników lub grup użytkowników.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby dodawać, modyfikować i usuwać zasady ochrony przed spamem, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do zasad ochrony przed spamem, musisz być członkiem grup ról  Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Aby uzyskać informacje na temat naszych zalecanych ustawień zasad ochrony przed spamem, zobacz Ustawienia zasad ochrony [przed spamem eOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Nie można całkowicie wyłączyć filtrowania spamu, ale można użyć reguły przepływu poczty e-mail (nazywanej również regułą transportu), aby pominąć większość filtrowania spamu dla wiadomości przychodzącej (na przykład jeśli rozsyłasz wiadomości e-mail za pośrednictwem usługi ochrony innej firmy lub urządzenia przed dostarczeniem do firmy Microsoft 365). Aby uzyskać więcej informacji, zobacz Ustawianie poziomu ufności filtru spamu (SCL) w wiadomościach za pomocą [reguł przepływu poczty](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).
  - Wiadomości służące do wyłudzania informacji o wysokiej pewności są nadal filtrowane. Nie ma to wpływu na inne funkcje w u chodzie o EOP (na przykład wiadomości są zawsze skanowane w poszukiwaniu złośliwego oprogramowania).
  - Jeśli chcesz pominąć filtrowanie spamu w przypadku skrzynek pocztowych usługi SecOps lub symulowania wyłudzania informacji, nie używaj reguł przepływu poczty e-mail. Aby uzyskać więcej informacji, zobacz Konfigurowanie symulowania wyłudzania informacji innej firmy użytkownikom i niefiltrowanych wiadomości do skrzynek pocztowych [usługi SecOps](configure-advanced-delivery.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-spam-policies"></a>Tworzenie zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender-mail

Utworzenie niestandardowych zasad ochrony przed spamem w portalu Microsoft 365 Defender umożliwia utworzenie reguły filtru spamu i skojarzonych z nią zasad filtru spamu, używając jednocześnie tej samej nazwy dla obu zasad.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz zasady** , a następnie wybierz **pozycję Przychodzący** z listy rozwijanej.

3. Zostanie otwarty kreator zasad. Na stronie **Nadaj nazwę zasadom** skonfiguruj następujące ustawienia:
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

5. Na **wyświetlonej stronie Ustawienia &-mail** poczty e-mail skonfiguruj następujące ustawienia:

   - Próg **zbiorczej** poczty e-mail: określa poziom skargi zbiorczej wiadomości wyzwalający określoną akcję w ramach werdyktu zbiorczego filtrowania spamu skonfigurowanego na następnej stronie. Wyższa wartość oznacza, że wiadomość jest mniej pożądana (bardziej prawdopodobna jest spam). Wartość domyślna to 7. Aby uzyskać więcej informacji, zobacz Poziom skarg zbiorczych [w](bulk-complaint-level-values.md) UOS i Jaka jest różnica między wiadomościami-śmieciami a masową [pocztą e-mail?](what-s-the-difference-between-junk-email-and-bulk-email.md).

     Domyślnie w programie PowerShell jest włączone tylko ustawienie _MarkAsSpamBulkMail_ w `On` zasadach ochrony przed spamem. To ustawienie znacznie wpływa na wyniki werdyktu filtrowania zbiorczego:

     - **_ZnacznikAsSpamBulkMail_** jest wł.: Wartość BCL większa niż lub równa progowi jest konwertowana na wartość SCL 6 odpowiadającą werdyktowi filtrowania spamu **, a** akcja werdyktu  filtrowania zbiorczego jest podejmowane w wiadomości.
     - **_ZnacznikAsSpamBulkMail_** jest wyłączony: Wiadomość jest oznaczana sygnaturą BCL, ale w  przypadku werdyktu  filtrowania zbiorczego nie jest podejmowane żadne działanie. W efekcie próg BCL i **akcja** werdyktu filtrowania zbiorczego nie mają znaczenia.

   - **Zwiększ wynik spamu**, **Oznacz jako spam**<sup>\*</sup> i **Tryb** testowania: Ustawienia zaawansowanego filtru spamu (ASF, Advanced Spam Filter) domyślnie wyłączone.

     Aby uzyskać szczegółowe informacje na temat tych ustawień, zobacz [Zaawansowane ustawienia filtru spamu w uieceniu wiadomości e-mail.](advanced-spam-filtering-asf-options.md)

      <sup>\*</sup> Ustawienia **Zawiera określone języki** **i z tych krajów** nie są częścią programowania asf.

   - **Zawiera określone języki**: Kliknij to pole i wybierz pozycję **Wł** **lub** Wył z listy rozwijanej. Po włączeniu zostanie wyświetlone okno. Zacznij wpisywać nazwę języka w polu. Zostanie wyświetlona przefiltrowana lista obsługiwanych języków. Gdy znajdziesz język, którego szukasz, wybierz go. Powtarzaj ten krok tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij pozycję Usuń ![ikonę Usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   - **Z listy rozwijanej te kraje** _: Kliknij to pole i wybierz pozycję _ *On** **lub Off** z listy rozwijanej. Po włączeniu zostanie wyświetlone okno. Zacznij wpisywać nazwę kraju w polu. Zostanie wyświetlona przefiltrowana lista obsługiwanych krajów. Gdy znajdziesz kraj, którego szukasz, wybierz go. Powtarzaj ten krok tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij pozycję Usuń ![ikonę Usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na **wyświetlonej** stronie Akcje skonfiguruj następujące ustawienia:

   - **Akcje wiadomości**: Wybierz lub przejrzyj akcję, która ma być podejmowane w związku z wiadomościami na podstawie następujących werdyktów filtrowania spamu:
     - **Spam**
     - **Duża pewność, że spam**
     - **Wyłudzanie informacji**
     - **Wyłudzanie informacji o wysokiej pewności**
     - **Zbiorcze**

     Dostępne akcje dotyczące werdyktów filtrowania spamu opisano w poniższej tabeli.

     - Znacznik wyboru ( ![Znacznik wyboru.](../../media/checkmark.png)) wskazuje, że akcja jest dostępna (nie wszystkie akcje są dostępne we wszystkich werdyktach).
     - Gwiazdka ( <sup>\*</sup> ) po znaczniku wyboru wskazuje domyślną akcję werdyktu filtrowania spamu.

     |Akcja|Spam|High (Wysoki)<br>ufność<br>spam|Wyłudzanie informacji|High (Wysoki)<br>ufność<br>wyłudzanie informacji|Zbiorcze|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**Przenoszenie wiadomości do folderu Wiadomości-śmieci**: Wiadomość jest dostarczana do skrzynki pocztowej i przenoszony do folderu Wiadomości-śmieci. <sup>1</sup>|![Znacznik wyboru.](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)<sup>\*</sup>|
     |**Dodaj nagłówek X-header**: dodaje nagłówek X do nagłówka wiadomości i dostarcza wiadomość do skrzynki pocztowej. <p> Nazwę pola nagłówka X (nie wartości) należy wprowadzić później w **polu tekstowym Dodaj ten nagłówek X** . <p> W **przypadku** **werdyktów spamu** i spamu o dużej pewności wiadomość jest przenoszony do folderu Wiadomości-śmieci. <sup>1;2</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)||![Znacznik wyboru](../../media/checkmark.png)|
     |**Przed wierszem tematu tekst**: dodaje tekst na początku wiersza tematu wiadomości. Wiadomość zostanie dostarczona do skrzynki pocztowej i przeniesiona do folderu Wiadomości-śmieci. <sup>1;2</sup> <p> Tekst należy wprowadzić później w wierszu Przed **wierszem tematu prefiksu przy użyciu tego pola tekstowego** .|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)||![Znacznik wyboru](../../media/checkmark.png)|
     |**Przekierowywanie wiadomości na adres** e-mail: wysyła wiadomość do innych adresatów zamiast do zamierzonych adresatów. <p> Adresatów określisz później w polu **Przekieruj na ten adres e-mail** .|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|
     |**Usuwanie wiadomości**: W trybie dyskretnym usuwa całą wiadomość wraz ze wszystkimi załącznikami.|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)||![Znacznik wyboru](../../media/checkmark.png)|
     |**Poddaj wiadomość** kwarantannie: wysyła wiadomość do kwarantanny zamiast do zamierzonych adresatów. <p> Czas, przez jaki wiadomość ma być przechowywane w kwarantannie później w polu **Kwarantanna,** możesz określić. <p> Zasady kwarantanny [stosowane do poddanych](quarantine-policies.md) kwarantannie wiadomości dla werdyktu filtru spamu określa się w **polu Wybierz zasady** , które zostanie wyświetlone. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md). <sup>3</sup>|![Znacznik wyboru.](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)|![Znacznik wyboru](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../../media/checkmark.png)|
     |**Brak akcji**|||||![Znacznik wyboru](../../media/checkmark.png)|

     > <sup>1 Program</sup> EOP używa teraz własnego agenta dostarczania przepływu poczty e-mail do rozsyłania wiadomości do folderu Wiadomości-śmieci, zamiast używać reguły wiadomości-śmieci. Parametr _Enabled_ w **poleceniach cmdlet Set-MailboxJunkEmailConfiguration** nie ma już wpływu na przepływ poczty e-mail. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień wiadomości-śmieci Exchange Online pocztowych](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > W środowiskach hybrydowych, w których program EOP chroni lokalne Exchange pocztowe, musisz skonfigurować reguły przepływu poczty e-mail (nazywane także regułami transportu) w lokalnym programie Exchange. Te reguły przepływu poczty tłumaczą werdykt filtrowania spamu usługi EOP, dzięki czemu reguła wiadomości-śmieci w skrzynce pocztowej może przenieść wiadomość do folderu Wiadomości-śmieci. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usługi EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).
     >
     > <sup>2</sup> Możesz użyć tej wartości jako warunku w zasadach przepływu poczty e-mail do filtrowania lub rozsyłania wiadomości.
     >
     > <sup>3</sup> Puste pole **Wybierz wartość zasad** oznacza, że są używane domyślne zasady kwarantanny dla tego konkretnego werdyktu. Podczas późniejszego edytowania zasad ochrony przed spamem lub wyświetlania ustawień jest wyświetlana domyślna nazwa zasad kwarantanny. Aby uzyskać więcej informacji na temat domyślnych zasad kwarantanny, które są używane dla werdyktów filtru spamu, zobacz [tę tabelę](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **Zachowywanie spamu w** kwarantannie przez tę liczbę dni: Określa, jak długo wiadomość ma być zachowywana  w kwarantannie, jeśli jako akcję werdyktu filtrowania spamu wybrano opcję Poddaj wiadomość kwarantannie. Po upływie tego okresu wiadomość jest usuwana i nie można jej odzyskać. Prawidłowa wartość wynosi od 1 do 30 dni.

     > [!NOTE]
     > Wartość domyślna domyślnych zasad ochrony przed spamem i nowych zasad ochrony przed spamem tworzyć w programie PowerShell wynosi 15 dni. Wartość domyślna nowych zasad ochrony przed spamem tworzyć w portalu ochrony przed Microsoft 365 Defender spamem wynosi 30 dni.
     >
     > To ustawienie określa również, jak długo są zachowywane wiadomości poddane kwarantannie przez zasady ochrony przed **wyłudzaniem** informacji. Aby uzyskać więcej informacji, zobacz [Poddaj wiadomości kwarantannie w programie EOP i Defender for Office 365](quarantine-email-messages.md).

   - **Dodaj ten tekst nagłówka X**: To pole jest wymagane i dostępne tylko w przypadku, gdy jako akcję dodawania nagłówka X do werdyktu filtrowania spamu wybrano pozycję Dodaj nagłówek **X** . Wartość jest określana jako nazwa pola *nagłówka* , która jest dodawana do nagłówka wiadomości. Wartość pola *nagłówka jest* zawsze `This message appears to be spam`.

     Maksymalna długość to 255 znaków, a wartość nie może zawierać spacji ani dwukropków (:).

     Na przykład po wprowadzeniu wartości `X-This-is-my-custom-header`nagłówek X dodawany do wiadomości to `X-This-is-my-custom-header: This message appears to be spam.`

     Jeśli zostanie włączona wartość zawierająca spacje lub dwukropki (:), włączona wartość zostanie zignorowana i domyślny nagłówek X zostanie dodany do wiadomości (`X-This-Is-Spam: This message appears to be spam.`).

   - **Przed wierszem tematu** tym tekstem: To pole jest wymagane i dostępne tylko w przypadku, gdy  jako akcja werdyktu filtrowania spamu wybrano opcję Przed wierszem tematu i tekstem. Wprowadź tekst, który ma być wyświetlany na początku wiersza tematu wiadomości.

   - **Przekieruj** na ten adres e-mail: To pole jest wymagane i  dostępne tylko w przypadku, gdy jako akcję werdyktu filtrowania spamu została wybrana opcja Przekieruj wiadomość na adres e-mail. Wprowadź adres e-mail, na który chcesz dostarczyć wiadomość. Możesz wprowadzić wiele wartości rozdzielonych średnikami (;).

   - **Włączanie funkcji Wskazówki**: Domyślnie funkcje Wskazówki włączone, ale można je wyłączyć, czyszcząc pole wyboru.

   - **Włączanie automatycznego przeczyszczania** bez godziny: zap wykrywa i podejmuje działanie na wiadomościach, które już zostały dostarczone do Exchange Online pocztowych. Aby uzyskać więcej informacji, zobacz [Automatyczne przeczyszczanie bez godzin — ochrona przed spamem i złośliwym oprogramowaniem](zero-hour-auto-purge.md).

     Zap jest domyślnie włączone. Gdy zap jest włączone, dostępne są następujące ustawienia:

     - **Włącz ZAP dla wiadomości wyłudzających** informacje: Domyślnie funkcja ZAP jest włączona dla wykrywania wyłudzania informacji, ale można ją wyłączyć, czyszcząc pole wyboru.
     - **Włącz ZAP dla wiadomości-śmieci**: Domyślnie funkcja ZAP jest włączona dla wykrywania spamu, ale możesz ją wyłączyć, czyszcząc pole wyboru.

   > [!NOTE]
   > Powiadomienia użytkowników końcowych o spamie zostały zastąpione powiadomieniami kwarantanny _w zasadach_ kwarantanny. Powiadomienia kwarantanny zawierają informacje o wiadomościach poddanych kwarantannie dla wszystkich obsługiwanych funkcji ochrony (nie tylko zasad ochrony przed spamem i werdyktów zasad ochrony przed wyłudzaniem informacji). Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na **wyświetlonym &** listy zablokowanych możesz skonfigurować nadawców wiadomości według adresu e-mail lub domeny poczty e-mail, w przypadku których pominiesz filtrowanie spamu.

   W sekcji **Dozwolone** możesz skonfigurować dozwolonych nadawców i dozwolone domeny. W sekcji **Zablokowane** możesz dodać zablokowanych nadawców i zablokowane domeny.

   > [!IMPORTANT]
   >
   > Przed dodaniem domen do listy dozwolonych domen należy bardzo starannie przemyśleć te domeny. Aby uzyskać więcej informacji, zobacz [Tworzenie list bezpiecznych nadawców w uchęce EOP](create-safe-sender-lists-in-office-365.md).
   >
   > Nigdy nie dodawaj swoich [zaakceptowanych domen](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) ani typowych domen (na przykład microsoft.com lub office.com) do listy dozwolonych domen. Jeśli te domeny mogą pominąć filtrowanie spamu, atakujący mogą łatwo wysyłać do organizacji wiadomości podszywające się pod te zaufane domeny.
   >
   > Ręczne blokowanie domen przez dodanie ich do listy zablokowanych domen nie jest niebezpieczne, ale może zwiększyć Obciążenie administracyjne. Aby uzyskać więcej informacji, zobacz [Tworzenie list zablokowanych nadawców w uchęce EOP](create-block-sender-lists-in-office-365.md).
   >
   > Może się jednak tak dzieje, że nasze filtry przeoczysz wiadomość, nie zgodzisz się z werdyktem filtrowania lub zajmie nam trochę czasu, aby nasze systemy na to nagoniły. W takich przypadkach dostępne są listy zezwalających i listy zablokowanych, które zastępują bieżące werdykty filtrowania. Jednak tych list należy używać oszczędnie i tymczasowo: listy długie mogą stać się nieuprawnialne, a nasz stos filtrowania powinien robić to, co powinno robić. Jeśli chcesz zachować dozwoloną domenę przez dłuższy czas, musisz poinformować nadawcę, aby sprawdzić, czy jego domena została uwierzytelniona, i w przypadku, gdy nie jest, ustawić dla niego wartość DMARC odrzucone.

   Czynności dodawania wpisów do dowolnej listy są takie same:

   1. Kliknij link dla listy, którą chcesz skonfigurować:
      - **Dozwolone** \> **Nadawcy**: Kliknij **pozycję Zarządzaj nadawcami (nn**).
      - **Dozwolone** \> **Domeny**: Kliknij pozycję **Zezwalaj na domeny**.
      -  \> Zablokowane **Nadawcy**: Kliknij **pozycję Zarządzaj nadawcami (nn**).
      -  \> Zablokowane **Domeny**: Kliknij pozycję **Blokuj domeny**.

   2. W wyświetlonym wysuwu wykonaj następujące czynności:
      1. Kliknij ![ikonę Utwórz.](../../media/m365-cc-sc-create-icon.png) **Dodaj nadawców lub** **Dodaj domeny**.
      2. W **wyświetlonym oknie dialogowym** Dodawanie  nadawców lub Dodaj domeny wprowadź adres e-mail nadawcy w polu Nadawca  lub w domenie **w polu** Domena. Podczas pisania wartość będzie wyświetlana poniżej tego pola. Po zakończeniu wpisywania adresu e-mail lub domeny wybierz wartość poniżej tego pola.
      3. Powtórz poprzedni krok tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

      Po zakończeniu kliknij pozycję **Dodaj nadawców** lub **Dodaj domeny**.

      Z powrotem na wysuwanych głównych ekranach nadawcy i domeny, które zostały dodane przez Ciebie, są wymienione na stronie. Aby usunąć pozycję z tej strony, wykonaj następujące czynności:

      1. Zaznacz co najmniej jeden wpis z listy. Możesz również użyć pola **Wyszukaj,** aby znaleźć wartości na liście.
      2. Po zaznaczeniu co najmniej jednego wpisu ikona usuwania ![Ikona Usuń.](../../media/m365-cc-sc-delete-icon.png) .
      3. Kliknij ikonę usuwania ![Ikona Usuń.](../../media/m365-cc-sc-delete-icon.png) , aby usunąć zaznaczone pozycje.

      Po zakończeniu kliknij pozycję **Gotowe**.

      Na stronie **Zezwalaj na & zablokowanych kliknij** przycisk **Dalej** , gdy będziesz czytać, aby kontynuować.

8. Na **wyświetlonej** stronie Recenzja przejrzyj ustawienia. Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Utwórz**.

9. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-spam-policies"></a>Wyświetlanie zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender-mail

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** odszukaj jedną z następujących wartości:
   - Wartość **Typ** to Niestandardowe **zasady ochrony przed spamem.**
   - Wartość **Name (** Nazwa) to **Zasady przychodzące ochrony przed spamem (domyślne)**

   Na liście zasad ochrony przed spamem są wyświetlane następujące właściwości:

   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**
   - **Type**

3. Po wybraniu zasad ochrony przed spamem przez kliknięcie nazwy ustawienia zasad są wyświetlane w wysuwanych menu.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-spam-policies"></a>Modyfikowanie zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender-mail

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy zasady ochrony przed spamem, klikając nazwę:
   - Zasady niestandardowe, których wartość w kolumnie **Typ** to Niestandardowe zasady **ochrony przed spamem**.
   - Zasady domyślne o **nazwie Zasady przychodzące ochrony przed spamem (domyślne)**

3. W wyświetlonym wysuwanych szczegółach zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji o ustawieniach, zobacz poprzednią sekcję Tworzenie zasad ochrony przed [spamem](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) w portalu Microsoft 365 Defender w tym artykule.

   W przypadku domyślnych zasad ochrony przed spamem  sekcja Zastosowane do nie jest dostępna (zasady dotyczą wszystkich użytkowników) i nie można zmienić jej nazwy.

Aby włączyć lub wyłączyć zasady albo ustawić kolejność priorytetu zasad, zobacz poniższe sekcje.

### <a name="enable-or-disable-anti-spam-policies"></a>Włączanie lub wyłączanie zasad ochrony przed spamem

Nie można wyłączyć domyślnych zasad ochrony przed spamem.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** z listy Niestandardowe zasady ochrony przed **spamem** , klikając nazwę.

3. U góry wyświetlonego wysuwana informacja o zasadach zostanie wyświetlona jedna z następujących wartości:
   - **Zasady wyłączone**: Aby włączyć zasady, kliknij ikonę ![Włącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz** .
   - **Zasady wł**.: Aby wyłączyć zasady, kliknij ikonę ![Wyłącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij **pozycję Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanych szczegółach zasad.

Na stronie głównej zasad wartość **Status** zasad będzie wł **.** lub **wyłączona**.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Ustawianie priorytetu niestandardowych zasad ochrony przed spamem

Domyślnie zasady ochrony przed spamem mają priorytet, który zależy od kolejności ich utworzenia (nowsze zasady mają niższy priorytet niż starsze zasady). Numer niższego priorytetu oznacza wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Dwa zasady nie mogą mieć tego samego priorytetu i przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszej zasady.

Aby zmienić priorytet zasad, kliknij pozycję Zwiększ priorytet lub  Zmniejsz priorytet we  właściwościach zasad (nie można bezpośrednio zmodyfikować numeru Priorytet w portalu Microsoft 365 Defender). Zmiana priorytetu zasad jest sensowna tylko w przypadku wielu zasad.

 **Uwagi**:

- W portalu Microsoft 365 Defender można zmieniać priorytet zasad ochrony przed spamem dopiero po ich utworzeniu. W programie PowerShell możesz zastąpić domyślny priorytet podczas tworzenia reguły filtru spamu (która może mieć wpływ na priorytet istniejących reguł).
- Zasady ochrony przed spamem są przetwarzane w kolejności ich wyświetlania (pierwsza zasada ma **wartość Priorytet** 0). Domyślne zasady ochrony przed spamem mają wartość priorytetu Najniższa **wartość i nie** można jej zmienić.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z wartością **Typ** z listy Niestandardowe zasady ochrony przed **spamem** , klikając nazwę.

3. U góry wyświetlonego wysuwu szczegółów zasad zobaczysz komunikat Zwiększ priorytet lub Zmniejsz  priorytet na podstawie  bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady ochrony przed spamem o **wartości Priorytet** **0** mają dostęp tylko do opcji **Zmniejsz priorytet** .
   - W zasadach ochrony przed spamem o najmniejszej wartości **Priorytet** (na przykład **3**) jest dostępna tylko opcja **Zwiększ** priorytet.
   - Jeśli masz co najmniej trzy zasady ochrony przed spamem, zasady dotyczące wartości o najwyższym i najniższym priorytecie  mają zarówno opcje Zwiększ priorytet, jak **i Zmniejsz priorytet**.

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Ikona Zwiększ priorytet** lub ![Zmniejsz priorytet](../../media/m365-cc-sc-decrease-icon.png) **Zmniejszanie priorytetu** w celu zmiany **wartości Priorytet** .

4. Po zakończeniu kliknij pozycję **Zamknij w wysuwanych** szczegółach zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-spam-policies"></a>Usuwanie niestandardowych zasad ochrony przed spamem za pomocą portalu Microsoft 365 Defender-mail

Gdy korzystasz z portalu Microsoft 365 Defender usunąć niestandardowe zasady ochrony przed spamem, reguła filtru spamu i odpowiadające im zasady filtrowania spamu są usuwane. Nie można usunąć domyślnych zasad ochrony przed spamem.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** z listy Niestandardowe zasady ochrony przed **spamem** , klikając nazwę. W górnej części wyświetlonego wysuwania szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Ikona usuwania zasad](../../media/m365-cc-sc-delete-icon.png) **Usuń zasady**.

3. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>Konfigurowanie Exchange Online ochrony przed spamem przy użyciu programu PowerShell lub autonomicznego programu PowerShell usługi EOP

Jak opisano wcześniej, zasady ochrony przed spamem obejmują zasady filtrowania spamu oraz regułę filtrowania spamu.

W Exchange Online Programu PowerShell lub autonomicznego programu PowerShell usługi EOP różnica między zasadami filtrowania spamu a regułami filtrowania spamu jest widoczna. Do zarządzania zasadami filtrowania spamu używa się polecenia cmdlet **-HostedContentFilterPolicy, a do zarządzania regułami filtrowania spamu używa się polecenia cmdlet -HostedContentFilterRule.\*** **\***

- W programie PowerShell najpierw tworzysz zasady filtru spamu, a następnie tworzysz regułę filtru spamu identyfikującą zasady, których ta reguła dotyczy.
- W programie PowerShell ustawienia zasad filtrowania spamu i reguły filtru spamu są zmieniane osobno.
- Po usunięciu zasad filtru spamu z programu PowerShell odpowiednia reguła filtru spamu nie jest automatycznie usuwana i odwrotnie.

Następujące ustawienia zasad ochrony przed spamem są dostępne tylko w programie PowerShell:

- Domyślny _parametr MarkAsSpamBulkMail_`On`. Efekty tego ustawienia zostały opisane w sekcji Używanie portalu [Microsoft 365 Defender do](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) tworzenia zasad ochrony przed spamem we wcześniejszej części tego artykułu.
- Następujące ustawienia powiadomień użytkowników końcowych o kwarantannie antyspamowej:
  - Parametr _DownloadLink_, który pokazuje lub ukrywa link do narzędzia do raportowania wiadomości-śmieci dla sieci Outlook.
  - Parametr _EndUserSpamNotificationCustomSubject_ , który umożliwia dostosowanie wiersza tematu powiadomienia.

### <a name="use-powershell-to-create-anti-spam-policies"></a>Tworzenie zasad ochrony przed spamem przy użyciu programu PowerShell

Tworzenie zasad ochrony przed spamem w programie PowerShell jest procesem dwuetapowym:

1. Utwórz zasady filtru spamu.
2. Utwórz regułę filtru spamu określającą zasady filtrowania spamu, których ta reguła dotyczy.

 **Uwagi**:

- Możesz utworzyć nową regułę filtru spamu i przypisać do tej reguły istniejące, nieskojarzonych zasad filtrowania spamu. Reguła filtru spamu nie może być skojarzona z więcej niż jedną zasadami filtru spamu.
- W programie PowerShell możesz skonfigurować następujące ustawienia nowych zasad filtrowania spamu, które nie są dostępne w portalu programu Microsoft 365 Defender, dopóki nie zostaną one skonfigurowane po ich utworzeniu:
  - Utwórz nowe zasady jako wyłączone (_włączone dla_ `$false` polecenia cmdlet **New-HostedContentFilterRule** ).
  - Ustaw priorytet zasad podczas tworzenia (_Priority__\<Number\>_) dla polecenia cmdlet **New-HostedContentFilterRule**.

- Nowe zasady filtrowania spamu, które tworzysz w programie PowerShell, nie są widoczne w portalu usługi Microsoft 365 Defender, dopóki nie przypiszesz ich do reguły filtru spamu.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>Krok 1. Tworzenie zasad filtru spamu przy użyciu programu PowerShell

Aby utworzyć zasady filtrowania spamu, użyj tej składni:

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

W tym przykładzie są owane zasady filtrowania spamu o nazwie  Kierownictwo Contoso z następującymi ustawieniami:

- Poddaj kwarantannie wiadomości, jeśli werdykt filtrowania spamu jest spamem [](quarantine-policies.md) lub spamem o dużej pewności, i użyj domyślnych zasad kwarantanny dla wiadomości poddanych kwarantannie (nie używamy parametrów _SpamQuarantineTag_ ani _HighConfidenceSpamQuarantineTag_).
- BCL 7, 8 lub 9 wyzwala akcję w przypadku werdyktu zbiorczego filtrowania spamu wiadomości e-mail.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania zasad kwarantanny do używania w zasadach filtru [spamu](quarantine-policies.md#anti-spam-policies-in-powershell), zobacz Określanie zasad kwarantanny w zasadach ochrony przed spamem za pomocą programu PowerShell.[](quarantine-policies.md)

#### <a name="step-2-use-powershell-to-create-a-spam-filter-rule"></a>Krok 2. Tworzenie reguły filtru spamu przy użyciu programu PowerShell

Aby utworzyć regułę filtru spamu, użyj tej składni:

```PowerShell
New-HostedContentFilterRule -Name "<RuleName>" -HostedContentFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

W tym przykładzie jest ana nowa reguła filtrowania spamu o nazwie  Kierownictwo Contoso z tymi ustawieniami:

- Z regułą są skojarzone zasady filtru spamu o nazwie  Kierownictwo Firmy Contoso.
- Reguła dotyczy członków grupy o nazwie Grupa kadry kierowniczej Contoso.

```PowerShell
New-HostedContentFilterRule -Name "Contoso Executives" -HostedContentFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-HostedContentFilterRule](/powershell/module/exchange/new-hostedcontentfilterrule).

### <a name="use-powershell-to-view-spam-filter-policies"></a>Wyświetlanie zasad filtrowania spamu za pomocą programu PowerShell

Aby zwrócić listę podsumowania wszystkich zasad filtrowania spamu, uruchom to polecenie:

```PowerShell
Get-HostedContentFilterPolicy
```

Aby zwrócić szczegółowe informacje dotyczące określonych zasad filtrowania spamu, użyj tej składni:

```PowerShell
Get-HostedContentFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

W tym przykładzie zwracane są wszystkie wartości właściwości zasad filtru spamu o nazwie  Kierownictwo.

```PowerShell
Get-HostedContentFilterPolicy -Identity "Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

### <a name="use-powershell-to-view-spam-filter-rules"></a>Wyświetlanie reguł filtru spamu przy użyciu programu PowerShell

Aby wyświetlić istniejące reguły filtru spamu, użyj następującej składni:

```PowerShell
Get-HostedContentFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Aby zwrócić listę podsumowania wszystkich reguł filtru spamu, uruchom to polecenie:

```PowerShell
Get-HostedContentFilterRule
```

Aby przefiltrować listę według włączonych lub wyłączonych reguł, uruchom następujące polecenia:

```PowerShell
Get-HostedContentFilterRule -State Disabled
```

```PowerShell
Get-HostedContentFilterRule -State Enabled
```

Aby zwrócić szczegółowe informacje na temat określonej reguły filtru spamu, użyj tej składni:

```PowerShell
Get-HostedContentFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

W tym przykładzie zwracane są wszystkie wartości właściwości reguły filtru spamu o nazwie  Kierownictwo Contoso.

```PowerShell
Get-HostedContentFilterRule -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-HostedContentFilterRule](/powershell/module/exchange/get-hostedcontentfilterrule).

### <a name="use-powershell-to-modify-spam-filter-policies"></a>Modyfikowanie zasad filtrowania spamu za pomocą programu PowerShell

Oprócz poniższych elementów te same ustawienia są dostępne po zmodyfikowaniu zasad filtrowania spamu w programie PowerShell, jak w przypadku tworzenia zasad zgodnie z opisem w kroku [1. Tworzenie](#step-1-use-powershell-to-create-a-spam-filter-policy) zasad filtru spamu we wcześniejszej części tego artykułu przy użyciu programu PowerShell.

- Przełącznik _MakeDefault_, który zmienia określone zasady w zasady domyślne (stosowane do wszystkich, zawsze ma najniższy  priorytet i nie można ich usuwać), jest dostępny tylko po zmodyfikowaniu zasad filtrowania spamu w programie PowerShell.
- Nie można zmienić nazwy zasad filtru spamu (polecenie cmdlet **Set-HostedContentFilterPolicy** nie ma _parametru Name_ ). Zmiana nazwy zasad ochrony przed spamem w portalu Microsoft 365 Defender umożliwia jedynie zmianę nazwy reguły filtru _spamu_.

Aby zmodyfikować zasady filtrowania spamu, użyj tej składni:

```PowerShell
Set-HostedContentFilterPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania zasad kwarantanny do używania w zasadach filtru [spamu](quarantine-policies.md#anti-spam-policies-in-powershell), zobacz Określanie zasad kwarantanny w zasadach ochrony przed spamem za pomocą programu PowerShell.[](quarantine-policies.md)

### <a name="use-powershell-to-modify-spam-filter-rules"></a>Modyfikowanie reguł filtru spamu za pomocą programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły filtru spamu w programie PowerShell, jest parametr _Enabled_ umożliwiający utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły filtru spamu, zobacz następną sekcję.

W przeciwnym razie podczas modyfikowania reguły filtru spamu w programie PowerShell nie są dostępne żadne dodatkowe ustawienia. Podczas tworzenia reguły są dostępne te same ustawienia, co opisano w sekcji Krok 2. Tworzenie reguły filtru spamu we wcześniejszej części tego artykułu przy użyciu programu [PowerShell](#step-2-use-powershell-to-create-a-spam-filter-rule) .

Aby zmodyfikować regułę filtru spamu, użyj tej składni:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" <Settings>
```

W tym przykładzie zmieniono nazwę istniejącej reguły filtru spamu o nazwie `{Fabrikam Spam Filter}`.

```powershell
Set-HostedContentFilterRule -Identity "{Fabrikam Spam Filter}" -Name "Fabrikam Spam Filter"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-HostedContentFilterRule](/powershell/module/exchange/set-hostedcontentfilterrule).

### <a name="use-powershell-to-enable-or-disable-spam-filter-rules"></a>Włączanie lub wyłączanie reguł filtru spamu przy użyciu programu PowerShell

Włączenie lub wyłączenie reguły filtrowania spamu w programie PowerShell włącza lub wyłącza wszystkie zasady ochrony przed spamem (regułę filtru spamu i przypisane zasady filtrowania spamu). Nie można włączyć ani wyłączyć domyślnych zasad ochrony przed spamem (są one zawsze stosowane do wszystkich adresatów).

Aby włączyć lub wyłączyć regułę filtru spamu w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-HostedContentFilterRule | Disable-HostedContentFilterRule> -Identity "<RuleName>"
```

W tym przykładzie wyłączyno regułę filtru spamu o nazwie Dział marketingu.

```PowerShell
Disable-HostedContentFilterRule -Identity "Marketing Department"
```

W tym przykładzie ta sama reguła jest włączana.

```PowerShell
Enable-HostedContentFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Enable-HostedContentFilterRule](/powershell/module/exchange/enable-hostedcontentfilterrule) i [Disable-HostedContentFilterRule](/powershell/module/exchange/disable-hostedcontentfilterrule).

### <a name="use-powershell-to-set-the-priority-of-spam-filter-rules"></a>Ustawianie priorytetu reguł filtru spamu przy użyciu programu PowerShell

Wartość najwyższego priorytetu, jaki można ustawić dla reguły, wynosi 0. Najniższa wartość, która można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć wpływ na inne reguły kaskadowe. Jeśli na przykład masz pięć reguł niestandardowych (priorytet od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły filtru spamu w programie PowerShell, użyj następującej składni:

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie dla reguły o nazwie Dział marketingu jest ustawiany priorytet na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich numery priorytetów są zwiększane o 1).

```PowerShell
Set-HostedContentFilterRule -Identity "Marketing Department" -Priority 2
```

**Uwagi**:

- Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj zamiast tego _parametru Priority_ polecenia cmdlet **New-HostedContentFilterRule** .
- Domyślne zasady filtru spamu nie mają odpowiadającej jej reguły filtru spamu i zawsze mają niemodyfikowalny priorytet o wartości **Najniżej**.

### <a name="use-powershell-to-remove-spam-filter-policies"></a>Usuwanie zasad filtrowania spamu za pomocą programu PowerShell

W przypadku usunięcia zasad filtrowania spamu przy użyciu programu PowerShell odpowiednia reguła filtru spamu nie jest usuwana.

Aby usunąć zasady filtru spamu w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedContentFilterPolicy -Identity "<PolicyName>"
```

W tym przykładzie zasady filtru spamu o nazwie Dział marketingu są usuwane.

```PowerShell
Remove-HostedContentFilterPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-HostedContentFilterPolicy](/powershell/module/exchange/remove-hostedcontentfilterpolicy).

### <a name="use-powershell-to-remove-spam-filter-rules"></a>Usuwanie reguł filtru spamu za pomocą programu PowerShell

Usunięcie reguły filtru spamu za pomocą programu PowerShell nie powoduje usunięcia odpowiednich zasad filtrowania spamu.

Aby usunąć regułę filtru spamu w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedContentFilterRule -Identity "<PolicyName>"
```

W tym przykładzie jest usuwana reguła filtru spamu o nazwie Dział marketingu.

```PowerShell
Remove-HostedContentFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-HostedContentFilterRule](/powershell/module/exchange/remove-hostedcontentfilterrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

### <a name="send-a-gtube-message-to-test-your-spam-policy-settings"></a>Wysyłanie wiadomości z witryny GTUBE w celu przetestowania ustawień zasad dotyczących spamu

> [!NOTE]
> Te kroki będą działać tylko wtedy, gdy organizacja poczty e-mail, z która wysyłasz wiadomość GTUBE, nie skanuje w poszukiwaniu spamu wychodzącego. Jeśli tak, nie można wysłać wiadomości testowej.

Test ogólny na niezamawiane masową pocztę e-mail (GTUBE) to ciąg tekstowy dołączany do wiadomości testowej w celu zweryfikowania ustawień ochrony przed spamem w organizacji. Komunikat GTUBE jest podobny do pliku tekstowego European Institute for Computer Antivirus Research (EICAR) do testowania ustawień złośliwego oprogramowania.

W jednym wierszu wiadomości e-mail można dołączyć następujący tekst z serwisu GTUBE bez spacji i podziałów wiersza:

```text
XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
```
