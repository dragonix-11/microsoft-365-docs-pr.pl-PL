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
ms.openlocfilehash: 2a74fce0242f0206218d6f7f2f13e61d9f0a3b6f
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847120"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Wstępne ustawienie zasad zabezpieczeń w usłudze EOP i ochronie usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

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

- **Wbudowana ochrona** (tylko Ochrona usługi Office 365 w usłudze Defender): profil, który umożliwia ochronę tylko linków Sejf i załączników Sejf. Ten profil skutecznie udostępnia domyślne zasady dla linków Sejf i załączników Sejf, które nigdy nie miały domyślnych zasad.

  W przypadku **ochrony wbudowanej** wstępnie ustawione zasady zabezpieczeń są domyślnie włączone dla wszystkich Ochrona usługi Office 365 w usłudze Defender klientów. Chociaż nie zalecamy tego, można również skonfigurować wyjątki na podstawie **użytkowników**, **grup** i **domen** , aby ochrona nie była stosowana do konkretnych użytkowników.

Dopóki zasady nie zostaną przypisane do użytkowników, zasady zabezpieczeń **standardowego** i **ścisłego** ustawienia wstępnego nie są przypisane do nikoja. Z kolei zasady zabezpieczeń wbudowanej **ochrony są** domyślnie przypisane do wszystkich adresatów, ale można skonfigurować wyjątki.

### <a name="policies-in-preset-security-policies"></a>Zasady w wstępnie ustawionych zasadach zabezpieczeń

Wstępnie ustawione zasady zabezpieczeń używają odpowiednich zasad z różnych funkcji ochrony w ramach operacji EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender. Te zasady są tworzone _po_ przypisaniu wstępnie ustawionych zasad zabezpieczeń **ochrony standardowej** lub **ścisłej ochrony** do użytkowników. Nie można modyfikować ustawień w tych zasadach.

- **zasady Exchange Online Protection (EOP**): obejmuje to organizacje Microsoft 365 z Exchange Online skrzynkami pocztowymi i autonomicznymi organizacjami EOP bez Exchange Online skrzynek pocztowych:

  - [Zasady ochrony przed spamem](configure-your-spam-filter-policies.md) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń** i **Ścisłe wstępnie ustawione zasady zabezpieczeń**.
  - [Zasady ochrony przed złośliwym oprogramowaniem](configure-anti-malware-policies.md) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń** i **Ścisłe wstępnie ustawione zasady zabezpieczeń**.
  - [Zasady ochrony przed wyłudzaniem informacji EOP](set-up-anti-phishing-policies.md#spoof-settings) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń** i **Rygorystyczne ustawienia zabezpieczeń** (ustawienia fałszowania).

- **zasady Ochrona usługi Office 365 w usłudze Microsoft Defender**: obejmuje to organizacje z subskrypcjami dodatków Microsoft 365 E5 lub Ochrona usługi Office 365 w usłudze Defender:
  - Zasady ochrony przed wyłudzaniem informacji w Ochrona usługi Office 365 w usłudze Microsoft Defender o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń** i **ścisłe zasady zabezpieczeń wstępnie ustawione**, które obejmują:
    - Te same [ustawienia fałszowania](set-up-anti-phishing-policies.md#spoof-settings) , które są dostępne w zasadach ochrony przed wyłudzaniem informacji w ramach EOP.
    - [Ustawienia personifikacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Zaawansowane progi wyłudzania informacji](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Sejf Łączy zasady](set-up-safe-links-policies.md) o nazwie **Standardowa wstępnie ustawiona zasada zabezpieczeń**, **ścisłe zasady zabezpieczeń wstępnie ustawione** i **wbudowane zasady ochrony**.
  - [Sejf zasady załączników](set-up-safe-attachments-policies.md) o nazwie **Standardowe wstępnie ustawione zasady zabezpieczeń**, **Ścisłe wstępnie ustawione zasady zabezpieczeń** i **Wbudowane zasady ochrony**.

Zabezpieczenia EOP można stosować do innych użytkowników niż Ochrona usługi Office 365 w usłudze Microsoft Defender ochrony.

### <a name="policy-settings-in-preset-security-policies"></a>Ustawienia zasad w wstępnie ustawionych zasadach zabezpieczeń

Nie można modyfikować ustawień zasad w profilach ochrony. Wartości ustawień zasad ochrony **standardowej**, **ścisłej** i **wbudowanej** są opisane w artykule [Zalecane ustawienia dotyczące EOP i zabezpieczeń Ochrona usługi Office 365 w usłudze Microsoft Defender](recommended-settings-for-eop-and-office365.md).

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Kolejność pierwszeństwa dla wstępnie ustawionych zasad zabezpieczeń i innych zasad

W przypadku zastosowania wielu zasad do użytkownika stosowana jest następująca kolejność od najwyższego priorytetu do najniższego priorytetu:

1. **Ścisłe** zasady zabezpieczeń ustawień wstępnych ochrony
2. Wstępnie ustawione zasady zabezpieczeń **ochrony w warstwie Standardowa**
3. Niestandardowe zasady zabezpieczeń
4. **Wbudowane** wstępnie ustawione zasady zabezpieczeń i domyślne zasady zabezpieczeń

Innymi słowy, ustawienia zasad **ścisłej ochrony** zastępują ustawienia standardowych zasad **ochrony**, które zastępują ustawienia zasad niestandardowych, które zastępują ustawienia z **wbudowanych** zasad zabezpieczeń wstępnie ustawionych ochrony (Sejf Linki i załączniki Sejf) oraz domyślnych zasad (antyspamowych, chroniących przed złośliwym oprogramowaniem i chroniących przed wyłudzaniem informacji).

Jeśli na przykład ustawienie zabezpieczeń istnieje w usłudze Ochrona w warstwie **Standardowa** , a administrator włączył ochronę w warstwie **Standardowa** dla użytkownika, zostanie zastosowane ustawienie Ochrony w warstwie **Standardowa** zamiast tego, co jest skonfigurowane dla tego ustawienia w zasadach niestandardowych lub w zasadach domyślnych (dla tego samego użytkownika). Pamiętaj, że możesz mieć część organizacji, do której chcesz zastosować tylko zasady **ochrony standardowej** lub **ścisłej** , stosując zasady niestandardowe do innych użytkowników w organizacji w celu spełnienia określonych potrzeb.

**Wbudowana ochrona** nie ma wpływu na adresatów w istniejących zasadach linków Sejf ani załączników Sejf. Jeśli skonfigurowano już **ochronę standardową**, **ścisłą ochronę** lub niestandardowe Sejf Linki lub zasady załączników Sejf, zasady te są _zawsze_ stosowane _przed_ **wbudowaną ochroną**, więc nie ma to wpływu na adresatów, którzy są już zdefiniowani w istniejących zasadach wstępnych lub niestandardowych.

## <a name="assign-preset-security-policies-to-users"></a>Przypisywanie wstępnie ustawionych zasad zabezpieczeń do użytkowników

### <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj polecenia <https://security.microsoft.com/presetSecurityPolicies>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby skonfigurować wstępnie ustawione zasady zabezpieczeń, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do wstępnie ustawionych zasad zabezpieczeń, musisz być członkiem grupy ról **Czytelnik globalny** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwaga**: dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Używanie portalu Microsoft 365 Defender do przypisywania wstępnie ustawionych zasad zabezpieczeń standardowych i ścisłych do użytkowników

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Zasady współpracy** \> & poczty e-mail **& Reguły** \> **zasad zagrożeń** **Wstępnie ustawione zasady** \> zabezpieczeń w sekcji **Zasady szablonów**. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj polecenia <https://security.microsoft.com/presetSecurityPolicies>.

2. Na stronie **Ustawienia wstępne zasad zabezpieczeń** kliknij pozycję **Zarządzaj** w sekcjach **Ochrona** standardowa lub **Ścisła ochrona** .

3. Kreator **zastosuj ochronę w warstwie Standardowa** lub **Zastosuj ścisłą ochronę** rozpoczyna się w wysuwnym oknie. Na stronie **Ochrona EOP zidentyfikuj** wewnętrznych adresatów, do których mają zastosowanie [zabezpieczenia EOP](#policies-in-preset-security-policies) (warunki adresatów):
   - **Użytkownicy**
   - **Grupy**
   - **Domeny**

   Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   - **Wyklucz tych użytkowników, grupy i domeny**: aby dodać wyjątki dla wewnętrznych adresatów, których dotyczą zasady (wyjątki adresatów), wybierz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie same jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

4. W Ochrona usługi Office 365 w usłudze Microsoft Defender organizacjach zostaniesz przekierowany do **Ochrona usługi Office 365 w usłudze Defender ochrony ma zastosowanie do** strony w celu zidentyfikowania adresatów wewnętrznych, których [dotyczy Ochrona usługi Office 365 w usłudze Microsoft Defender ochrony](#policies-in-preset-security-policies) mają zastosowanie do (warunków adresatów).

   Ustawienia i zachowanie są dokładnie takie same, jak **zabezpieczenia EOP stosowane do** strony w poprzednim kroku.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Przejrzyj i potwierdź zmiany** sprawdź wybrane opcje, a następnie kliknij przycisk **Potwierdź**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Użyj portalu Microsoft 365 Defender, aby zmodyfikować przypisania standardowych i ścisłych wstępnie ustawionych zasad zabezpieczeń

Kroki modyfikowania przypisania wstępnie ustawionych zasad zabezpieczeń **ochrony standardowej** lub **ścisłej ochrony** są takie same, jak wtedy, gdy początkowo [przypisano wstępnie ustawione zasady zabezpieczeń do użytkowników](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Aby wyłączyć wstępnie ustawione zasady zabezpieczeń **ochrony standardowej** lub **ścisłej ochrony** przy zachowaniu istniejących warunków i wyjątków, przesuń przełącznik do pozycji **Wyłączone** ![przełączanie wyłączone.](../../media/scc-toggle-off.png) Aby włączyć zasady, przesuń przełącznik do pozycji **Włączone** ![przełączanie.](../../media/scc-toggle-on.png)

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Użyj portalu Microsoft 365 Defender, aby zmodyfikować przypisania wstępnie ustawionych zasad zabezpieczeń wbudowanej ochrony

Pamiętaj, że wbudowane zasady zabezpieczeń **wstępnie** ustawionej ochrony są przypisywane do wszystkich adresatów i nie mają wpływu na adresatów zdefiniowanych w zasadach zabezpieczeń wstępnie ustawionych w **warstwie Standardowa** lub **Ścisła ochrona** albo niestandardowych Sejf Linkach lub zasadach załączników Sejf.

W związku z tym zazwyczaj nie zalecamy wyjątków od **wbudowanych zasad zabezpieczeń wstępnie** ustawionych ochrony.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do pozycji **Zasady współpracy** \> & poczty e-mail **& Reguły** \> **zasad zagrożeń** **Wstępnie ustawione zasady** \> zabezpieczeń w sekcji **Zasady szablonów**. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj polecenia <https://security.microsoft.com/presetSecurityPolicies>.

2. Na stronie **Ustawienia wstępne zasad zabezpieczeń** wybierz pozycję **Dodaj wykluczenia (niezalecane)** w sekcji **Wbudowana ochrona** .

3. Na wyświetlonym **wysuwnym Wyklucz z wbudowanej ochrony** zidentyfikuj wewnętrznych adresatów wykluczonych z wbudowanej ochrony Sejf Łącza i załączniki Sejf:
   - **Użytkownicy**
   - **Grupy**
   - **Domeny**

   Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy użytkownikowi pomyślnie przypisano zasady **ochrony standardowej** lub **zabezpieczeń ścisłej ochrony** , użyj ustawienia ochrony, w którym wartość domyślna jest inna niż ustawienie **ochrony standardowej** , które różni się od ustawienia **Ścisła ochrona** .

Na przykład w przypadku wiadomości e-mail wykrytych jako spam (nie spam o wysokim poziomie ufności) sprawdź, czy wiadomość została dostarczona do folderu Wiadomości-śmieci dla użytkowników **ochrony standardowej** i poddana kwarantannie dla użytkowników **o ścisłej ochronie** .

W przypadku [poczty zbiorczej](bulk-complaint-level-values.md) sprawdź, czy wartość BCL 6 lub nowsza dostarcza wiadomość do folderu Wiadomości-śmieci dla użytkowników **ochrony w warstwie Standardowa** , a wartość BCL 4 lub nowsza podda wiadomości kwarantannie dla użytkowników **ścisłej ochrony** .
