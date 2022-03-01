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
description: Administratorzy mogą dowiedzieć się, jak stosować ustawienia zasad standardowych i ścisłych w funkcjach ochrony usług Exchange Online Protection (EOP) i Microsoft Defender for Office 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ff81eea4232693662a907695ea0cef0d94941ac6
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/17/2022
ms.locfileid: "63014857"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender dla systemu Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Wstępnie ustawione zasady zabezpieczeń zapewniają scentralizowaną lokalizację do stosowania wszystkich zalecanych zasad ochrony przed spamem, złośliwym oprogramowaniem i wyłudzania informacji jednocześnie do użytkowników. Ustawień zasad nie można konfigurować. Zamiast tego są one ustawiane przez nas i opierają się na naszych obserwacjach i doświadczeniach w centrach danych w celu zachowania równowagi między utrzymaniem szkodliwej zawartości przed użytkownikami i uniknięciem niepotrzebnych przerw w pracy.

W dalszej części tego artykułu opisano wstępnie ustawione zasady zabezpieczeń i sposób ich konfigurowania.

## <a name="what-preset-security-policies-are-made-of"></a>Jakie wstępnie ustawione zasady zabezpieczeń są

Wstępnie ustawione zasady zabezpieczeń składają się z następujących elementów:

- Profile
- Policies (zasady)
- Ustawienia zasad

Kolejność pierwszeństwa jest także ważna w przypadku wielu wstępnie ustawionych zasad zabezpieczeń i innych zasad dotyczących tej samej osoby.

### <a name="profiles-in-preset-security-policies"></a>Profile w wstępnie ustawionych zasadach zabezpieczeń

Profil określa poziom ochrony. Dostępne są następujące profile:

- **Standardowa ochrona**: profil ochrony według planu bazowego, który jest odpowiedni dla większości użytkowników.
- **Ścisła ochrona**: bardziej rygorystyczny profil ochrony dla wybranych użytkowników (użytkownicy o wysokich wartościach docelowych lub priorytetowi).

  W **przypadku ochrony standardowej** **i** ścisłej ochrony należy stosować reguły z warunkami i wyjątkami, które określają, do kogo są lub nie są stosowane profile.

  Dostępne warunki i wyjątki to:

  - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty w organizacji.
  - **Grupy**: Określone grupy dystrybucyjne, grupy zabezpieczeń z obsługą poczty lub Microsoft 365 w organizacji.
  - **Domeny**: Wszyscy adresaci w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

  Możesz użyć tylko raz warunku lub wyjątku, ale możesz określić wiele wartości dla warunku lub wyjątku. Wiele wartości takich samych warunków lub wyjątków używa logiki OR (na przykład _\<recipient1\>_ lub _\<recipient2\>_). W różnych warunkach lub wyjątkach jest używanie logiki AND (na przykład _\<recipient1\>_ i _\<member of group 1\>_).

- **Wbudowana ochrona (tylko w** programie Defender dla Office 365): profil, który umożliwia tylko Sejf linków i załączników Sejf załączników. Ten profil w praktyce udostępnia domyślne zasady dla linków Sejf i załączników Sejf, które nigdy nie miały zasad domyślnych.

  W **przypadku wbudowanej ochrony** wstępnie ustawione zasady zabezpieczeń są domyślnie włączone dla wszystkich usług Defender dla Office 365 klientów. Chociaż nie zalecamy tego, możesz też skonfigurować wyjątki na podstawie **użytkowników, grup** i domen, aby ochrona nie  była stosowana do konkretnych użytkowników.

Do czasu przypisania tych zasad do użytkowników zasady zabezpieczeń **Standardowe** i  Ścisłe wstępnie ustawione nie będą przypisywane do nikogo. Z kolei wstępnie ustawione zasady zabezpieczeń **Wbudowane** ustawienia ochrony są domyślnie przypisywane do wszystkich adresatów, ale można skonfigurować wyjątki.

### <a name="policies-in-preset-security-policies"></a>Zasady w wstępnie ustawionych zasadach zabezpieczeń

Wstępnie ustawione zasady zabezpieczeń korzystają z odpowiednich zasad poszczególnych funkcji ochrony w usługach EOP i Microsoft Defender for Office 365. Te zasady są tworzone _po przypisaniu_ użytkownikom zasad **zabezpieczeń Standardowa** ochrona lub **Ścisłe ustawienia** wstępne ochrony. Tych zasad nie można modyfikować.

- **Exchange Online Protection (EOP**): Dotyczy Microsoft 365 firm z Exchange Online pocztowymi i autonomicznymi organizacjami usługi EOP bez Exchange Online skrzynek pocztowych:

  - [Zasady ochrony przed spamem o](configure-your-spam-filter-policies.md) **nazwach Standardowe wstępnie ustawione zasady zabezpieczeń** **i Ścisłe wstępnie ustawione zasady zabezpieczeń**.
  - [Zasady ochrony przed złośliwym oprogramowaniem o](configure-anti-malware-policies.md) **nazwach Standardowe wstępnie ustawione zasady zabezpieczeń** **i Ścisłe wstępnie ustawione zasady zabezpieczeń**.
  - [Zasady ochrony przed wyłudzaniem informacji programu EOP](set-up-anti-phishing-policies.md#spoof-settings) o nazwach **Standardowe** wstępnie ustawione zasady zabezpieczeń i **Ścisłe wstępnie ustawione zasady zabezpieczeń** (ustawienia fałszowania).

- **Zasady programu Microsoft Defender dla Office 365**: Dotyczy to również organizacji z pakietem Microsoft 365 E5 lub usługi Defender Office 365 subskrypcji dodatków:
  - Zasady ochrony przed wyłudzaniem informacji w programie Microsoft Defender dla Office 365 o nazwie **Standardowe wstępnie** ustawione zasady zabezpieczeń oraz **Ścisłe wstępnie** ustawione zasady zabezpieczeń, takie jak:
    - Te same [ustawienia fałszowania](set-up-anti-phishing-policies.md#spoof-settings) , które są dostępne w zasadach ochrony przed wyłudzaniem informacji eOP.
    - [Ustawienia personifikacji](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Zaawansowane progi wyłudzania informacji](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Sejf linki o](set-up-safe-links-policies.md) **nazwach Standardowe** wstępnie ustawione zasady zabezpieczeń, Ścisłe wstępnie ustawione zasady **zabezpieczeń** i **Wbudowane zasady ochrony**.
  - [Sejf załączników o](set-up-safe-attachments-policies.md) nazwach Standardowe wstępnie ustawione zasady **zabezpieczeń**, **Ścisłe** wstępnie ustawione zasady zabezpieczeń i **Wbudowane zasady ochrony**.

Ochronę usługi EOP można stosować do innych użytkowników niż program Microsoft Defender, Office 365 ochrony.

### <a name="policy-settings-in-preset-security-policies"></a>Ustawienia zasad w wstępnie ustawionych zasadach zabezpieczeń

Nie można modyfikować ustawień zasad w profilach ochrony. Wartości **ustawień zasad** **ochrony** standardowej, ścisłej i wbudowanej opisano w te tematach Zalecane ustawienia usług [EOP i Microsoft Defender w Office 365 zabezpieczeń](recommended-settings-for-eop-and-office365.md).

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Kolejność pierwszeństwa wstępnie ustawionych zasad zabezpieczeń i innych zasad

W przypadku stosowania wielu zasad do użytkownika stosowana jest następująca kolejność od najwyższego priorytetu do najniższego:

1. **Ścisłe zasady zabezpieczeń wstępnie** ustawionej ochrony
2. **Standardowe zasady zabezpieczeń wstępnie** ustawionej ochrony
3. Niestandardowe zasady zabezpieczeń
4. **Wbudowane wstępnie ustawione zasady zabezpieczeń i** domyślne zasady zabezpieczeń

Innymi słowy ustawienia zasad Ścisłej ochrony zastępują ustawienia zasad Ochrony standardowej, które  zastępują ustawienia zasad niestandardowych, które zastępują ustawienia wstępnie ustawionych zasad ochrony wbudowanej (załączniki Sejf  Linki i załączniki do programu Sejf) oraz zasady domyślne (ochrona przed spamem, złośliwym oprogramowaniem i wyłudzaniem informacji).

Jeśli na przykład w opcji Ochrona standardowa istnieje ustawienie zabezpieczeń i administrator włączył ochronę standardową  dla użytkownika, ustawienie Standardowa ochrona zostanie  zastosowane zamiast ustawień skonfigurowanych dla tego ustawienia w zasadach niestandardowych lub zasadach domyślnych (dla tego samego użytkownika). Pamiętaj, że możesz mieć część organizacji, do której chcesz zastosować tylko zasady **ochrony** standardowej lub ścisłej, stosując zasady niestandardowe do innych użytkowników w organizacji w celu zaspokojenia określonych potrzeb.

**Wbudowana ochrona nie wpływa** na adresatów w istniejących zasadach Sejf wiadomości ani Sejf załączników. Jeśli skonfigurowano już zasady Ochrona  standardowa **, Ścisła** ochrona lub Niestandardowe zasady linków programu Sejf lub załączników programu Sejf, te zasady są zawsze stosowane przed  wbudowanej  **ochrony, więc** nie mają wpływu na adresatów, którzy są już zdefiniowani w tych istniejących wstępnie ustawionych lub niestandardowych zasadach.

## <a name="assign-preset-security-policies-to-users"></a>Przypisywanie wstępnie ustawionych zasad zabezpieczeń do użytkowników

### <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj przycisku <https://security.microsoft.com/presetSecurityPolicies>.

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby skonfigurować wstępnie ustawione zasady zabezpieczeń, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do wstępnie ustawionych zasad zabezpieczeń, musisz być członkiem grupy ról **czytnika** globalnego.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwaga**: Dodanie użytkowników do odpowiedniej roli Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w aplikacji  Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Przypisz użytkownikom standardowe i ścisłe wstępnie ustawione zasady zabezpieczeń za pomocą portalu Microsoft 365 Defender-

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady & e-mail **& Zasady** \>  \> zagrożeń Wstępnie ustawione zasady zabezpieczeń w sekcji Zasady **szablonów**. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj przycisku <https://security.microsoft.com/presetSecurityPolicies>.

2. Na stronie **Wstępnie ustawione zasady zabezpieczeń** kliknij pozycję **Zarządzaj** w sekcjach **Ochrona standardowa** lub **Ścisła ochrona** .

3. Kreator **Zastosuj standardową ochronę** **lub Zastosuj ścisłą ochronę** jest uruchamiany w wysuwanych widokach. Na stronie **Ochrona usług EOP** określ adresatów wewnętrznych, do których mają zastosowanie ochrona [EOP](#policies-in-preset-security-policies) (warunki adresata):
   - **Użytkownicy**
   - **Grupy**
   - **Domeny**

   Kliknij w odpowiednim polu, zacznij wpisywać wartość i wybierz odpowiednią wartość z wyników. Powtórz ten proces tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   W przypadku użytkowników lub grup możesz użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale odpowiadające im nazwy wyświetlane są wyświetlane w wynikach. Dla użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   - **Wyklucz tych użytkowników,** grup i domen: Aby dodać wyjątki dla adresatów wewnętrznych, których zasady dotyczą (wyjątki adresata), zaznacz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie, jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

4. W programie Microsoft Defender dla Office 365 organizacji jest podejrzeń do usługi **Defender for Office 365** w celu zidentyfikowania adresatów wewnętrznych, do których mają zastosowanie ochrona usługi [Microsoft Defender](#policies-in-preset-security-policies) dla systemu Office 365 (warunki dotyczące adresatów).

   Ustawienia i zachowanie są dokładnie takie, jak ustawienia **ochrony programu EOP dotyczą** strony w poprzednim kroku.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Sprawdzanie i potwierdzanie zmian** sprawdź wybrane opcje, a następnie kliknij przycisk **Potwierdź**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Użyj portalu Microsoft 365 Defender, aby zmodyfikować przypisania standardowych i ścisłych wstępnie ustawionych zasad zabezpieczeń.

Czynności, które należy wykonać w celu zmodyfikowania zasad  zabezpieczeń Ochrona standardowa lub Ścisłe ustawienia wstępne ochrony, są takie same jak w przypadku początkowego przypisania wstępnie ustawionych zasad zabezpieczeń [do użytkowników](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Aby wyłączyć zasady zabezpieczeń **Ochrona** **standardowa lub** Ścisłe ustawienia wstępne ochrony przy zachowaniu istniejących warunków i wyjątków,  ![przesuń przełącznik do opcji Wyłącz wyłączoną.](../../media/scc-toggle-off.png) Aby włączyć zasady, przesuń przełącznik do **włączoną** ![opcję Włączone](../../media/scc-toggle-on.png).

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Za pomocą Microsoft 365 Defender ustawień domyślnych zmodyfikuj przypisania wstępnie ustawionych zasad zabezpieczeń Wbudowany ochrona

Pamiętaj, że  wstępnie ustawione zasady zabezpieczeń Wbudowane ustawienia ochrony są przypisywane do wszystkich adresatów i nie mają wpływu na adresatów zdefiniowanych w zasadach zabezpieczeń Standardowa ochrona,  Ścisłe ustawienia wstępne ochrony ani niestandardowe zasady linków Sejf lub załączników programu Sejf.

W związku z tym zwykle nie zalecamy wyjątków od wstępnie ustawionych zasad zabezpieczeń **Wbudowany** ochrona.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady & e-mail **& Zasady** \>  \> zagrożeń Wstępnie ustawione zasady zabezpieczeń w sekcji Zasady **szablonów**. Aby przejść bezpośrednio do strony **Wstępnie ustawione zasady zabezpieczeń** , użyj przycisku <https://security.microsoft.com/presetSecurityPolicies>.

2. Na stronie **Wstępnie ustawione zasady zabezpieczeń** wybierz pozycję **Dodaj wykluczenia (zalecane)** w sekcji **Ochrona wbudowana** .

3. W **wyświetlonym wysuwanych** oknie wysuwana Wyklucz z wbudowanej ochrony określ adresatów wewnętrznych wykluczonych z wbudowanej ochrony załączników Sejf i Sejf załączników:
   - **Użytkownicy**
   - **Grupy**
   - **Domeny**

   Kliknij w odpowiednim polu, zacznij wpisywać wartość i wybierz odpowiednią wartość z wyników. Powtórz ten proces tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   W przypadku użytkowników lub grup możesz użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale odpowiadające im nazwy wyświetlane są wyświetlane w wynikach. Dla użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Po zakończeniu kliknij przycisk **Zapisz**.

### <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

Aby sprawdzić, czy zasady zabezpieczeń Ochrona standardowa lub  Ścisłe zasady ochrony  zostały pomyślnie przypisane do użytkownika, użyj ustawienia ochrony, w którym wartość domyślna jest inna niż ustawienie Ochrona  standardowa, które różni się od ustawienia Ścisła **ochrona.**

Na przykład w przypadku wiadomości e-mail wykrytych jako spam (o dużej pewności spamu) należy sprawdzić, czy wiadomość została dostarczona do folderu  Wiadomości-śmieci dla standardowych użytkowników ochrony i poddana kwarantannie w przypadku użytkowników o ścisłej **ochronie.**

W przypadku poczty masowej [sprawdź, czy](bulk-complaint-level-values.md) wartość BCL 6 lub wyższa dostarcza wiadomość do folderu Wiadomości-śmieci dla standardowych użytkowników ochrony, a wartość BCL 4 lub wyższa umożliwia kwarantannę wiadomości w przypadku użytkowników z ścisłą  ochroną.
