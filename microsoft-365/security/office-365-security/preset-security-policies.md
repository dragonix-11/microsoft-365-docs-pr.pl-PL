---
title: Wstępnie ustawione zasady zabezpieczeń
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
description: Administratorzy mogą dowiedzieć się, jak stosować standardowe i ścisłe ustawienia zasad w funkcjach ochrony Exchange Online Protection (EOP) i Ochrona usługi Office 365 w usłudze Microsoft Defender
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ffce562fbcbdf8ca9d6c19265166400163be7acf
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607658"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Wstępne ustawienie zasad zabezpieczeń w usłudze EOP i ochronie usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Wstępnie ustawione zasady zabezpieczeń zapewniają scentralizowaną lokalizację do stosowania wszystkich zalecanych zasad spamu, złośliwego oprogramowania i wyłudzania informacji użytkownikom jednocześnie. Nie można skonfigurować ustawień zasad. Zamiast tego są one ustawiane przez nas i są oparte na naszych obserwacjach i środowiskach w centrach danych, aby zachować równowagę między trzymaniem szkodliwych treści z dala od użytkowników a unikaniem niepotrzebnych zakłóceń.

W pozostałej części tego artykułu opisano wstępnie ustawione zasady zabezpieczeń i sposób ich konfigurowania.

## <a name="what-preset-security-policies-are-made-of"></a>Jakie są wstępnie ustawione zasady zabezpieczeń

Wstępnie ustawione zasady zabezpieczeń składają się z następujących elementów:

- Profile
- Policies (zasady)
- Ustawienia zasad

Ponadto kolejność pierwszeństwa jest ważna, jeśli wiele wstępnie ustawionych zasad zabezpieczeń i innych zasad ma zastosowanie do tej samej osoby.

### <a name="profiles-in-preset-security-policies"></a>Profile w wstępnie ustawionych zasadach zabezpieczeń

Profil określa poziom ochrony. Dostępne są następujące profile:

- **Standardowa ochrona**: profil ochrony punktu odniesienia, który jest odpowiedni dla większości użytkowników.
- **Ścisła ochrona**: bardziej agresywny profil ochrony dla wybranych użytkowników (użytkownicy o wysokiej wartości lub użytkownicy o wysokim priorytecie).

  W przypadku **ochrony standardowej** i **ścisłej ochrony** należy użyć reguł z warunkami i wyjątkami, aby określić wewnętrznych adresatów, do których mają zastosowanie zasady (warunki adresatów).

  Dostępne warunki i wyjątki to:

  - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty e-mail.
  - **Grupy**:
    - Członkowie określonych grup dystrybucyjnych lub grup zabezpieczeń z obsługą poczty.
    - Określona Grupy Microsoft 365.
  - **Domeny**: Wszyscy adresaci w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

  Warunek lub wyjątek można użyć tylko raz, ale można określić wiele wartości dla warunku lub wyjątku. Wiele wartości tego samego warunku lub wyjątku używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). Różne warunki lub wyjątki używają logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

  > [!IMPORTANT]
  > Wiele różnych warunków lub wyjątków nie są addytywne; są inkluzywne. Zasady są stosowane _tylko_ do tych adresatów, którzy pasują do _wszystkich_ filtrów określonych adresatów. Na przykład należy skonfigurować warunek filtru adresata w zasadach z następującymi wartościami:
  >
  > - Adresatem jest: romain@contoso.com
  > - Odbiorca jest członkiem: Kierownictwo
  >
  > Zasady są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, zasady nie są do niego stosowane.
  >
  > Podobnie, jeśli używasz tego samego filtru adresata co wyjątek od zasad, zasady nie są stosowane do romain@contoso.com _tylko_ wtedy, gdy jest on również członkiem grup Kadra kierownicza. Jeśli nie jest członkiem grupy, polityka nadal ma do niego zastosowanie.

- **Wbudowana ochrona** (tylko Ochrona usługi Office 365 w usłudze Defender): profil, który umożliwia ochronę tylko bezpiecznych linków i bezpiecznych załączników. Ten profil skutecznie udostępnia domyślne zasady dla bezpiecznych linków i bezpiecznych załączników, które nigdy nie miały domyślnych zasad.

  W przypadku **ochrony wbudowanej** wstępnie ustawione zasady zabezpieczeń są domyślnie włączone dla wszystkich Ochrona usługi Office 365 w usłudze Defender klientów. Chociaż nie zalecamy tego, można również skonfigurować wyjątki na podstawie **użytkowników**, **grup** i **domen** , aby ochrona nie była stosowana do konkretnych użytkowników.

Dopóki zasady nie zostaną przypisane do użytkowników, zasady zabezpieczeń **standardowego** i **ścisłego** ustawienia wstępnego nie są przypisane do nikoja. Z kolei zasady zabezpieczeń wbudowanej **ochrony są** domyślnie przypisane do wszystkich adresatów, ale można skonfigurować wyjątki.

### <a name="policies-in-preset-security-policies"></a>Zasady w wstępnie ustawionych zasadach zabezpieczeń

Wstępnie ustawione zasady zabezpieczeń używają odpowiednich zasad z różnych funkcji ochrony w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender. Te zasady są tworzone _po_ przypisaniu wstępnie ustawionych zasad zabezpieczeń **ochrony standardowej** lub **ścisłej ochrony** do użytkowników. Nie można modyfikować ustawień w tych zasadach.

- **zasady Exchange Online Protection (EOP**): te zasady znajdują się we wszystkich organizacjach platformy Microsoft 365 z Exchange Online skrzynkami pocztowymi i autonomicznymi organizacjami EOP bez Exchange Online skrzynek pocztowych:

  - [Zasady ochrony przed spamem](configure-your-spam-filter-policies.md) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń** i **Ścisłe wstępnie ustawione zasady zabezpieczeń**.
  - [Zasady ochrony przed złośliwym oprogramowaniem](configure-anti-malware-policies.md) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń** i **Ścisłe wstępnie ustawione zasady zabezpieczeń**.
  - [Zasady ochrony przed wyłudzaniem informacji (ochrona przed fałszowaniem)](set-up-anti-phishing-policies.md#spoof-settings) o nazwie **Standardowa wstępnie ustawiona zasada zabezpieczeń** i **ścisłe zasady zabezpieczeń** (ustawienia fałszowania).

  > [!NOTE]
  > Zasady dotyczące wychodzącego spamu nie są częścią wstępnie ustawionych zasad zabezpieczeń. Domyślne zasady spamu wychodzącego automatycznie chronią elementy członkowskie wstępnie ustawionych zasad zabezpieczeń. Możesz też utworzyć niestandardowe zasady spamu wychodzącego, aby dostosować ochronę dla członków wstępnie ustawionych zasad zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie filtrowania spamu wychodzącego w ramach operacji EOP](configure-the-outbound-spam-policy.md).

- **zasady Ochrona usługi Office 365 w usłudze Microsoft Defender**: te zasady znajdują się w organizacjach z subskrypcjami dodatków Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Defender:
  - Zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Defender o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń** i **ścisłe zasady zabezpieczeń wstępnie ustawione**, które obejmują:
    - Te same [ustawienia fałszowania](set-up-anti-phishing-policies.md#spoof-settings) , które są dostępne w zasadach ochrony przed wyłudzaniem informacji w ramach EOP.
    - [Ustawienia personifikacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Zaawansowane progi wyłudzania informacji](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Zasady bezpiecznych łączy](set-up-safe-links-policies.md) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń**, **Ścisłe wstępnie ustawione zasady zabezpieczeń** i **Wbudowane zasady ochrony**.
  - [Zasady bezpiecznych załączników](set-up-safe-attachments-policies.md) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń**, **Ścisłe wstępnie ustawione zasady zabezpieczeń** i **Wbudowane zasady ochrony**.

Ochronę EOP można stosować do innych użytkowników niż Ochrona usługi Office 365 w usłudze Defender ochrony lub zastosować operacje EOP i Ochrona usługi Office 365 w usłudze Defender do tych samych adresatów.

### <a name="policy-settings-in-preset-security-policies"></a>Ustawienia zasad w wstępnie ustawionych zasadach zabezpieczeń

Nie można modyfikować ustawień zasad w profilach ochrony. Wartości ustawień zasad ochrony **standardowej**, **ścisłej** i **wbudowanej** są opisane w artykule [Zalecane ustawienia dotyczące EOP i zabezpieczeń Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md).

> [!NOTE]
> W Ochrona usługi Office 365 w usłudze Defender ochrony należy zidentyfikować nadawców w celu [ochrony przed personifikacją użytkowników](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) oraz domeny wewnętrzne lub zewnętrzne w celu [ochrony przed personifikacją domeny](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).
>
> Wszystkie domeny, których jesteś właścicielem ([akceptowane domeny](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)), automatycznie otrzymują ochronę przed personifikacją domeny w wstępnie ustawionych zasadach zabezpieczeń.
>
> Wszyscy adresaci automatycznie otrzymują ochronę przed personifikacją z [analizy skrzynki pocztowej](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) w wstępnie ustawionych zasadach zabezpieczeń.

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Kolejność pierwszeństwa dla wstępnie ustawionych zasad zabezpieczeń i innych zasad

W przypadku zastosowania wielu zasad do użytkownika stosowana jest następująca kolejność od najwyższego priorytetu do najniższego priorytetu:

1. **Ścisłe** zasady zabezpieczeń ustawień wstępnych ochrony
2. Wstępnie ustawione zasady zabezpieczeń **ochrony w warstwie Standardowa**
3. Niestandardowe zasady zabezpieczeń
4. **Wbudowane zasady zabezpieczeń wstępnie** ustawione dla bezpiecznych linków i bezpiecznych załączników oraz domyślne zasady ochrony przed złośliwym oprogramowaniem, ochroną przed spamem i wyłudzaniem informacji.

Innymi słowy, ustawienia zasad **ścisłej ochrony** zastępują ustawienia standardowych zasad **ochrony** , które zastępują ustawienia zasad niestandardowych, które przesłaniają ustawienia z **wbudowanych** zasad zabezpieczeń (bezpieczne linki i bezpieczne załączniki) oraz zasad domyślnych (antyspamowych, chroniących przed złośliwym oprogramowaniem i chroniących przed wyłudzaniem informacji).

Jeśli na przykład ustawienie zabezpieczeń istnieje w usłudze Ochrona w warstwie **Standardowa** , a administrator włączył ochronę w warstwie **Standardowa** dla użytkownika, zostanie zastosowane ustawienie Ochrony w warstwie **Standardowa** zamiast tego, co jest skonfigurowane dla tego ustawienia w zasadach niestandardowych lub w zasadach domyślnych (dla tego samego użytkownika). Pamiętaj, że możesz mieć część organizacji, do której chcesz zastosować tylko zasady **ochrony standardowej** lub **ścisłej** , stosując zasady niestandardowe do innych użytkowników w organizacji w celu spełnienia określonych potrzeb.

**Wbudowana ochrona** nie ma wpływu na adresatów w istniejących zasadach bezpiecznych linków ani bezpiecznych załączników. Jeśli masz już skonfigurowaną **ochronę standardową**, **ścisłą ochronę** lub niestandardowe zasady bezpiecznych linków lub bezpiecznych załączników, te zasady są _zawsze_ stosowane _przed_ **wbudowaną ochroną**, więc nie ma to wpływu na adresatów, którzy są już zdefiniowani w istniejących zasadach wstępnych lub niestandardowych.

## <a name="assign-preset-security-policies-to-users"></a>Przypisywanie wstępnie ustawionych zasad zabezpieczeń do użytkowników

### <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj polecenia <https://security.microsoft.com/presetSecurityPolicies>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Łączenie z programem PowerShell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby skonfigurować wstępnie ustawione zasady zabezpieczeń, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do wstępnie ustawionych zasad zabezpieczeń, musisz być członkiem grupy ról **Czytelnik globalny** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwaga**: dodanie użytkowników do odpowiedniej roli usługi Azure Active Directory w Centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w usłudze Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Używanie portalu Microsoft 365 Defender do przypisywania wstępnie ustawionych zasad zabezpieczeń standardowych i ścisłych do użytkowników

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Zasady współpracy** \> & poczty e-mail **& Reguły** \> **zasad zagrożeń** **Wstępnie ustawione zasady** \> zabezpieczeń w sekcji **Zasady szablonów**. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj polecenia <https://security.microsoft.com/presetSecurityPolicies>.

2. Na stronie **Ustawienia wstępne zasad zabezpieczeń** kliknij pozycję **Zarządzaj** w sekcjach **Ochrona** standardowa lub **Ścisła ochrona** .

3. Kreator **zastosuj ochronę w warstwie Standardowa** lub **Zastosuj ścisłą ochronę** rozpoczyna się w wysuwnym oknie.

   Na stronie **Zastosuj Exchange Online Protection** zidentyfikuj wewnętrznych adresatów, do których mają zastosowanie [zabezpieczenia EOP](#policies-in-preset-security-policies) (warunki adresatów):
   - **Wszyscy adresaci**
   - **Konkretni adresaci**:
     - **Użytkownicy**
     - **Grupy**
     - **Domeny**

     Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

     W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   - **Brak**

   - **Wyklucz tych adresatów**: aby dodać wyjątki dla adresatów wewnętrznych, których dotyczą zasady (wyjątki adresatów), wybierz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie same jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

   > [!NOTE]
   > W organizacjach bez Ochrona usługi Office 365 w usłudze Defender kliknięcie przycisku **Dalej** spowoduje przejście do strony **Przegląd**. Pozostałe kroki/strony przed stroną **Przeglądanie** są dostępne tylko w organizacjach z Ochrona usługi Office 365 w usłudze Defender.

4. Na stronie **Zastosuj ochronę Ochrona usługi Office 365 w usłudze Defender** zidentyfikuj wewnętrznych adresatów, do których mają zastosowanie [zabezpieczenia Ochrona usługi Office 365 w usłudze Defender](#policies-in-preset-security-policies) (warunki adresatów).

   Ustawienia i zachowanie są dokładnie takie same, jak **zabezpieczenia EOP stosowane do** strony w poprzednim kroku.

   Możesz również wybrać wcześniej **wybranych adresatów** , aby używać tych samych adresatów, którzy wybrali ochronę EOP na poprzedniej stronie.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Ochrona przed personifikacją** kliknij przycisk **Dalej**.

6. Na **stronie Dodawanie adresów e-mail do flagi podczas personifikacji przez osoby atakujące** dodaj wewnętrznych i zewnętrznych nadawców chronionych przez [ochronę przed personifikacją użytkowników](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > Wszyscy adresaci automatycznie otrzymują ochronę przed personifikacją z [analizy skrzynki pocztowej](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) w wstępnie ustawionych zasadach zabezpieczeń.

   Każdy wpis składa się z nazwy wyświetlanej i adresu e-mail. Wprowadź każdą wartość w polach, a następnie kliknij przycisk **Dodaj**. Powtórz ten krok tyle razy, ile jest to konieczne.

   Można określić maksymalnie 350 użytkowników i nie można określić tego samego użytkownika w ustawieniach ochrony przed personifikacją użytkowników w wielu zasadach.

   Aby usunąć istniejący wpis z listy, kliknij przycisk ![Usuń użytkownika z ikony ochrony przed personifikacją.](../../media/m365-cc-sc-remove.png).

   Po zakończeniu kliknij przycisk **Dalej**.

7. Na stronie **Dodawanie domen do flagi podczas personifikacji przez osoby atakujące** dodaj domeny wewnętrzne i zewnętrzne chronione przez [ochronę przed personifikacją domeny](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > Wszystkie domeny, których jesteś właścicielem ([akceptowane domeny](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)), automatycznie otrzymują ochronę przed personifikacją domeny w wstępnie ustawionych zasadach zabezpieczeń.

   Wszyscy nadawcy w określonych domenach są chronieni przez ochronę przed personifikacją domeny.

   Wprowadź domenę w polu, a następnie kliknij przycisk **Dodaj**. Powtórz ten krok tyle razy, ile jest to konieczne.

   Aby usunąć istniejący wpis z listy, wybierz wpis, a następnie kliknij przycisk ![Usuń domenę z ikony ochrony przed personifikacją.](../../media/m365-cc-sc-remove.png).

   Maksymalna liczba domen, które można określić na potrzeby ochrony przed personifikacją domeny we wszystkich zasadach ochrony przed wyłudzaniem informacji, wynosi 50.

   Po zakończeniu kliknij przycisk **Dalej**.

8. Na stronie **Dodawanie zaufanych adresów e-mail i domen, aby nie były oznaczane jako personifikacja** , wprowadź adresy e-mail i domeny nadawcy, które mają zostać wykluczone z ochrony przed personifikacją. Komunikaty od tych nadawców nigdy nie zostaną oflagowane jako atak personifikacji, ale nadawcy nadal podlegają skanowaniu za pomocą innych filtrów w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Defender.

   Wprowadź adres e-mail lub domenę w polu, a następnie kliknij przycisk **Dodaj**. Powtórz ten krok tyle razy, ile jest to konieczne.

   Aby usunąć istniejący wpis z listy, wybierz wpis, a następnie kliknij przycisk ![Usuń wyjątki ikony ochrony przed personifikacją.](../../media/m365-cc-sc-remove.png).

   Po zakończeniu kliknij przycisk **Dalej**.

9. Na stronie **Przejrzyj i potwierdź te zasady** sprawdź wybrane opcje, a następnie kliknij przycisk **Potwierdź**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Użyj portalu Microsoft 365 Defender, aby zmodyfikować przypisania standardowych i ścisłych wstępnie ustawionych zasad zabezpieczeń

Kroki modyfikowania przypisania wstępnie ustawionych zasad zabezpieczeń **ochrony standardowej** lub **ścisłej ochrony** są takie same, jak wtedy, gdy początkowo [przypisano wstępnie ustawione zasady zabezpieczeń do użytkowników](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Aby wyłączyć wstępnie ustawione zasady zabezpieczeń **ochrony standardowej** lub **ścisłej ochrony** przy zachowaniu istniejących warunków i wyjątków, przesuń przełącznik do pozycji **Wyłączone** ![przełączanie wyłączone.](../../media/scc-toggle-off.png) Aby włączyć zasady, przesuń przełącznik do pozycji **Włączone** ![przełączanie.](../../media/scc-toggle-on.png)

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Użyj portalu Microsoft 365 Defender, aby zmodyfikować przypisania wstępnie ustawionych zasad zabezpieczeń wbudowanej ochrony

Pamiętaj, że wbudowane zasady zabezpieczeń **wstępnie ustawione ochrony** są przypisywane do wszystkich adresatów i nie mają wpływu na adresatów zdefiniowanych w zasadach zabezpieczeń wstępnie ustawionych w ramach **ochrony standardowej** lub **ścisłej ochrony** , niestandardowych zasad bezpiecznych linków ani bezpiecznych załączników.

W związku z tym zazwyczaj nie zalecamy wyjątków od **wbudowanych zasad zabezpieczeń wstępnie** ustawionych ochrony.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Zasady współpracy** \> & poczty e-mail **& Reguły** \> **zasad zagrożeń** **Wstępnie ustawione zasady** \> zabezpieczeń w sekcji **Zasady szablonów**. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj polecenia <https://security.microsoft.com/presetSecurityPolicies>.

2. Na stronie **Ustawienia wstępne zasad zabezpieczeń** wybierz pozycję **Dodaj wykluczenia (niezalecane)** w sekcji **Wbudowana ochrona** .

3. Na wyświetlonym **wysuwnym Wyklucz z wbudowanej ochrony** zidentyfikuj wewnętrznych adresatów wykluczonych z wbudowanej ochrony bezpiecznych linków i bezpiecznych załączników:
   - **Użytkownicy**
   - **Grupy**
   - **Domeny**

   Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń wykluczenia z wbudowanej ikony ochrony.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy użytkownikowi pomyślnie przypisano zasady **ochrony standardowej** lub **zabezpieczeń ścisłej ochrony** , użyj ustawienia ochrony, w którym wartość domyślna jest inna niż ustawienie **ochrony standardowej** , które różni się od ustawienia **Ścisła ochrona** .

Na przykład w przypadku wiadomości e-mail wykrytych jako spam (nie spam o wysokim poziomie ufności) sprawdź, czy wiadomość została dostarczona do folderu Wiadomości-śmieci dla użytkowników **ochrony standardowej** i poddana kwarantannie dla użytkowników **o ścisłej ochronie** .

W przypadku [poczty zbiorczej](bulk-complaint-level-values.md) sprawdź, czy wartość BCL 6 lub nowsza dostarcza wiadomość do folderu Wiadomości-śmieci dla użytkowników **ochrony w warstwie Standardowa** , a wartość BCL 4 lub nowsza podda wiadomości kwarantannie dla użytkowników **ścisłej ochrony** .
