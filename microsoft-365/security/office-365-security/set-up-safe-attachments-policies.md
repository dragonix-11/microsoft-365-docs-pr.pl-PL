---
title: Konfigurowanie zasad Sejf załączników w programie Microsoft Defender dla Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: Dowiedz się, jak zdefiniować zasady Sejf załączników w celu ochrony organizacji przed złośliwymi plikami w wiadomościach e-mail.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4cc0f2e3e87c288383880ba5b69f3b6b5d303c40
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032139"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Konfigurowanie zasad Sejf załączników w programie Microsoft Defender dla Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych korzystających z programu [Microsoft Defender dla Office 365](whats-new-in-defender-for-office-365.md). Jeśli jesteś użytkownikiem domowym i szukasz informacji na temat skanowania załączników w aplikacji Outlook, zobacz Zaawansowane zabezpieczenia [Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sejf Załączniki to funkcja w programie [Microsoft Defender](whats-new-in-defender-for-office-365.md) dla programu Office 365, która używa środowiska wirtualnego do sprawdzania załączników przychodzących wiadomości e-mail po ich zeskanowaniu przez ochronę przed złośliwym oprogramowaniem w programie [Exchange Online Protection (EOP),](anti-malware-protection.md) ale przed dostarczeniem ich do adresatów. Aby uzyskać więcej informacji, [zobacz Sejf w programie Microsoft Defender dla Office 365](safe-attachments.md).

Chociaż nie istnieją domyślne zasady załączników załączników programu Sejf, wstępnie ustawione  zasady zabezpieczeń wbudowanej ochrony zapewniają ochronę załączników programu Sejf wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach załączników Sejf). Aby uzyskać więcej informacji, zobacz [Wstępnie ustawione zasady zabezpieczeń w usługach EOP i Microsoft Defender for Office 365](preset-security-policies.md). Możesz także użyć procedur określonej w tym artykule, aby utworzyć Sejf załączników, które dotyczą konkretnych użytkowników, grup lub domen.

Zasady załączników programu Sejf można skonfigurować w portalu usługi Microsoft 365 Defender lub w programie PowerShell (Exchange Online PowerShell dla uprawnionych organizacji Microsoft 365 ze skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online, ale za pomocą programu Defender Office 365 subskrypcji dodatków).

Podstawowe elementy zasad załączników wiadomości Sejf załączników to:

- **Zasady bezpiecznych załączników**: Określa akcje wykrywania nieznanego złośliwego oprogramowania, wysyłanie wiadomości z załącznikami złośliwego oprogramowania na określony adres e-mail oraz określenie, czy wiadomości mają być odbierane, jeśli skanowanie załączników nie jest Sejf.
- **Reguła bezpiecznych załączników**: Określa priorytet i filtry adresatów (adresatów, których dotyczą zasady).

Różnica między tymi dwoma elementami nie jest widoczna, gdy zarządzasz zasadami załączników Sejf w portalu Microsoft 365 Defender wiadomości:

- Gdy tworzysz zasady załączników Sejf, w rzeczywistości jednocześnie tworzysz bezpieczną regułę załączników i skojarzone z nimi zasady bezpiecznych załączników, używając tej samej nazwy dla obu zasad.
- Podczas modyfikowania zasad załączników Sejf, ustawienia dotyczące nazwy, priorytetu, włączonego lub wyłączonego oraz filtrów adresatów modyfikują regułę bezpiecznych załączników. Wszystkie inne ustawienia modyfikują skojarzone bezpieczne zasady załączników.
- Gdy usuniesz zasady załączników Sejf załączników, reguła bezpiecznych załączników i skojarzone z nimi zasady bezpiecznych załączników zostaną usunięte.

W Exchange Online PowerShell lub autonomicznym programie PowerShell usługi EOP zasady i reguła są zarządzane osobno. Aby uzyskać więcej informacji, zobacz sekcję Używanie programu PowerShell Exchange Online lub autonomicznego programu [PowerShell usługi EOP](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) do konfigurowania Sejf załączników w dalszej części tego artykułu.

> [!NOTE]
> W obszarze ustawień globalnych w Sejf Załączniki konfigurujesz funkcje, które nie są zależne od zasad Sejf załączników. Aby uzyskać instrukcje, zobacz [Włączanie Sejf załączników wiadomości SharePoint, OneDrive i](turn-on-mdo-for-spo-odb-and-teams.md) Microsoft Teams [oraz Sejf dokumenty w](safe-docs.md) Microsoft 365 E5.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby wykonać procedury z tego artykułu, musisz mieć odpowiednie uprawnienia:
  - Aby tworzyć, modyfikować i usuwać zasady załączników programu Sejf, musisz być członkiem grup ról Zarządzanie organizacją lub  **Administrator** zabezpieczeń **w portalu Microsoft 365 Defender** oraz członkiem grupy ról Zarządzanie organizacją w programie Exchange Online.
  - Aby mieć dostęp tylko do odczytu do Sejf załączników, musisz być członkiem grup ról Czytnik globalny lub Czytnik  zabezpieczeń w portalu  Microsoft 365 Defender zabezpieczeń.

  Aby uzyskać więcej informacji, [zobacz Uprawnienia w portalu Microsoft 365 Defender i](permissions-microsoft-365-security-center.md) [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory głównej w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender oraz uprawnienia do innych funkcji w  Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Aby uzyskać nasze zalecane ustawienia dotyczące Sejf załączników, [zobacz Sejf Ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- Odmów do 30 minut na zastosowanie nowych lub zaktualizowanych zasad.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>Używanie portalu Microsoft 365 Defender do tworzenia Sejf załączników

Utworzenie niestandardowych zasad Sejf załączników w portalu Microsoft 365 Defender powoduje utworzenie jednocześnie reguły bezpiecznych załączników i skojarzonych z nimi bezpiecznych zasad załączników przy użyciu tej samej nazwy dla obu tych zasad.

1.  W portalu Microsoft 365 Defender  \> <https://security.microsoft.com>przejdź do sekcji Zasady & e-mail & **zasad** \> \> zagrożeń Sejf **załączników** **w** sekcji Zasady. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

2. Na stronie **Sejf załączników** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.

3. Zostanie otwarty kreator zasad. Na stronie **Nadaj nazwę zasadom** skonfiguruj następujące ustawienia:
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

   - **Wyklucz** tych użytkowników, grup i domen: Aby dodać wyjątki dla adresatów wewnętrznych, których zasady dotyczą (wyjątków, których dotyczą zasady), zaznacz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie, jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na stronie **Ustawienia** skonfiguruj następujące ustawienia:

   - **Sejf załączników odpowiedź z nieznanym złośliwym** oprogramowaniem: Wybierz jedną z następujących wartości:
     - **Wyłączone**: zazwyczaj nie zalecamy tej wartości.
     - **Monitor**
     - **Blokowanie**: jest to wartość domyślna i zalecana w przypadku standardowych i ściśle [wstępnie ustawionych zasad zabezpieczeń](preset-security-policies.md).
     - **Zamień**
     - **Dostarczanie dynamiczne (funkcja podglądu)**

     Te wartości o wyjaśniono w [Sejf zasad Załączniki](safe-attachments.md#safe-attachments-policy-settings).

   - **Zasady kwarantanny**: wybierz zasady kwarantanny dotyczące wiadomości poddanych kwarantannie przez Sejf załączników (**Blokowanie****,** zamienianie lub **Dostarczanie dynamiczne**). Zasady kwarantanny określają, co użytkownicy mogą robić w kwarantannie wiadomości i czy użytkownicy otrzymują powiadomienia kwarantanny. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

     Pusta wartość oznacza, że są używane domyślne zasady kwarantanny (AdminOnlyAccessPolicy do wykrywania poczty e-mail przez Sejf załączników). Podczas późniejszego edytowania Sejf Załączniki lub wyświetlania ustawień jest wyświetlana domyślna nazwa zasad kwarantanny.

   - Przekierowywanie wiadomości z wykrytymi załącznikami **. Jeśli** wybierzesz opcję Włącz przekierowywanie **, możesz** określić adres e-mail w polu Wysyłaj wiadomości zawierające zablokowane **,** monitorowane lub zamieniane załączniki do określonego adresu e-mail, aby wysyłać wiadomości zawierające załączniki zawierające złośliwe oprogramowanie do analizy i analizy.

     Zaleceniem dla ustawień zasad standardowych i ścisłych jest włączenie przekierowywania. Aby uzyskać więcej informacji, [zobacz Sejf Ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - Stosowanie odpowiedzi wykrywania **załączników** w programie Sejf, jeśli skanowanie nie jest ukończone (limit czasu lub błędy): Akcja określona przez program **Sejf** Załączniki w nieznanym złośliwym oprogramowaniu są podejmowane na wiadomościach nawet wtedy, gdy skanowanie załączników nie jest Sejf. Jeśli wybrano tę opcję, zawsze wybieraj pozycję **Włącz** przekierowywanie i określ adres e-mail, aby wysyłać wiadomości zawierające załączniki zawierające złośliwe oprogramowanie. W przeciwnym razie wiadomości mogą zostać utracone.

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na **wyświetlonej** stronie Recenzja przejrzyj ustawienia. Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

7. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>Wyświetlanie zasad Microsoft 365 Defender załączników za pomocą Sejf załączników

1.  W portalu Microsoft 365 Defender  \> <https://security.microsoft.com>przejdź do sekcji Zasady & e-mail & **zasad** \> \> zagrożeń Sejf **załączników** **w** sekcji Zasady. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

2. Na stronie **Sejf Załączniki** na liście zasad są wyświetlane następujące właściwości:
   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**

3. Po wybraniu zasady przez kliknięcie jej nazwy ustawienia zasad są wyświetlane w wysuwanych menu.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>Modyfikowanie Microsoft 365 Defender załączników za pomocą Sejf załączników

1. IW portalu Microsoft 365 Defender pod <https://security.microsoft.com>adresem przejdź  \> do sekcji Zasady & e-mail **& zasad** \>  \> zagrożeń Sejf **załączników** **w** sekcji Zasady. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

2. Na stronie **Sejf** wybierz zasady z listy, klikając nazwę.

3. W wyświetlonym wysuwanych szczegółach zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji na temat tych ustawień, zobacz sekcję Tworzenie Microsoft 365 Defender [sieci](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) Sejf we wcześniejszej części tego artykułu.

Aby włączyć lub wyłączyć zasady albo ustawić kolejność priorytetu zasad, zobacz poniższe sekcje.

### <a name="enable-or-disable-safe-attachments-policies"></a>Włączanie lub wyłączanie zasad Sejf załączników

1.  W portalu Microsoft 365 Defender  \> <https://security.microsoft.com>przejdź do sekcji Zasady & e-mail & **zasad** \> \> zagrożeń Sejf **załączników** **w** sekcji Zasady. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

2. Na stronie **Sejf** wybierz zasady z listy, klikając nazwę.

3. U góry wyświetlonego wysuwana informacja o zasadach zostanie wyświetlona jedna z następujących wartości:
   - **Zasady wyłączone**: Aby włączyć zasady, kliknij ikonę ![Włącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz** .
   - **Zasady wł**.: Aby wyłączyć zasady, kliknij ikonę ![Wyłącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij **pozycję Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanych szczegółach zasad.

Na stronie głównej zasad wartość **Status** zasad będzie wł **.** lub **wyłączona**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Ustawianie priorytetu zasad Sejf załączników

Domyślnie zasady załączników Sejf mają priorytet na podstawie kolejności ich tworzenia (nowsze zasady mają niższy priorytet niż starsze zasady). Numer niższego priorytetu oznacza wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Dwa zasady nie mogą mieć tego samego priorytetu i przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszej zasady.

Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz Kolejność i [pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

Sejf Załączniki są wyświetlane w kolejności ich przetwarzania (pierwsza zasada ma **wartość Priorytet** 0).

**Uwaga**: w portalu Microsoft 365 Defender priorytet zasad Załączniki wiadomości można zmieniać tylko po ich utworzeniu Sejf załączników. Podczas tworzenia reguły bezpiecznego załącznika (która może mieć wpływ na priorytet istniejących reguł) w programie PowerShell można zastąpić priorytet domyślny.

Aby zmienić priorytet zasad, kliknij pozycję Zwiększ priorytet lub  Zmniejsz priorytet we  właściwościach zasad (nie można bezpośrednio zmodyfikować numeru Priorytet w portalu Microsoft 365 Defender). Zmiana priorytetu zasad jest sensowna tylko w przypadku wielu zasad.

1. W portalu Microsoft 365 Defender przejdź  \> do sekcji Zasady & e-mail **& zasady** \>  \> zagrożeń Sejf **załączników** **w sekcji** Zasady.

2. Na stronie **Sejf** wybierz zasady z listy, klikając nazwę.

3. U góry wyświetlonego wysuwu szczegółów zasad zobaczysz komunikat Zwiększ priorytet lub Zmniejsz  priorytet na podstawie  bieżącej wartości priorytetu i liczby zasad:
   - Zasady o wartości **Priorytet** **0** mają dostęp tylko do opcji **Zmniejsz priorytet** .
   - Zasady o najmniejszej **wartości Priorytet** (na przykład **3**) mają dostęp tylko do opcji **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady, dla zasad o najwyższym i najniższym priorytecie są dostępne  zarówno opcje Zwiększ priorytet, jak **i Zmniejsz priorytet**.

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Ikona Zwiększ priorytet** lub ![Zmniejsz priorytet](../../media/m365-cc-sc-decrease-icon.png) **Zmniejszanie priorytetu** w celu zmiany **wartości Priorytet** .

4. Po zakończeniu kliknij pozycję **Zamknij w wysuwanych** szczegółach zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>Usuwanie zasad załączników załączników w portalu Microsoft 365 Defender wiadomości Sejf wiadomości

1.  W portalu Microsoft 365 Defender  \> <https://security.microsoft.com>przejdź do sekcji Zasady & e-mail & **zasad** \> \> zagrożeń Sejf **załączników** **w** sekcji Zasady. Aby przejść bezpośrednio do strony **Sejf załączników**, użyj .<https://security.microsoft.com/safeattachmentv2>

2. Na Sejf **Załączniki** wybierz z listy zasady niestandardowe, klikając nazwę zasad.

3. W górnej części wyświetlonego wysuwania szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Ikona usuwania zasad](../../media/m365-cc-sc-delete-icon.png) **Usuń zasady**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Konfigurowanie Exchange Online programu PowerShell lub autonomicznego programu Power Sejf Shell usługi EOP

Zgodnie z wcześniejszym opisem zasady załączników Sejf załączników obejmują bezpieczne zasady załączników i regułę bezpiecznego załącznika.

W programie PowerShell różnica między bezpiecznymi zasadami załączników a regułami bezpiecznych załączników jest widoczna. Do zarządzania zasadami bezpiecznych załączników używa się polecenia cmdlet **-SafeAttachmentPolicy, a do zarządzania regułami bezpiecznych załączników używa się polecenia cmdlet -SafeAttachmentRule.\*** **\***

- W programie PowerShell należy najpierw utworzyć bezpieczne zasady załączników, a następnie utworzyć regułę bezpiecznego załącznika identyfikującą zasady, których ta reguła dotyczy.
- W programie PowerShell ustawienia w zasadach bezpiecznych załączników i bezpiecznej reguły załączników są modyfikowane osobno.
- Po usunięciu z programu PowerShell bezpiecznych zasad załączników odpowiednia reguła bezpiecznego załącznika nie jest usuwana automatycznie i odwrotnie.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Tworzenie zasad załączników załączników za Sejf programu PowerShell

Tworzenie zasad Sejf załączników w programie PowerShell jest procesem dwuetapowym:

1. Utwórz zasady bezpiecznych załączników.
2. Utwórz bezpieczną regułę załączników określającą zasady bezpiecznych załączników, których ta reguła dotyczy.

 **Uwagi**:

- Możesz utworzyć nową bezpieczną regułę załączników i przypisać do niego istniejące, nieskojarzonych zasady bezpiecznych załączników. Z regułą bezpiecznych załączników nie można skojarzyć więcej niż jednej bezpiecznej zasady załączników.

- W programie PowerShell można skonfigurować następujące ustawienia nowych bezpiecznych zasad załączników, które nie są dostępne w portalu programu Microsoft 365 Defender do momentu ich utworzenia:
  - Utwórz nowe zasady jako wyłączone (_włączone w_ `$false` poleceniach cmdlet **New-SafeAttachmentRule** ).
  - Ustaw priorytet zasad podczas tworzenia (_Priority__\<Number\>_) dla polecenia cmdlet **New-SafeAttachmentRule**.

- Nowe bezpieczne zasady załączników, które tworzysz w programie PowerShell, nie są widoczne w portalu programu Microsoft 365 Defender, dopóki nie przypiszesz ich do bezpiecznej reguły załączników.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>Krok 1. Tworzenie bezpiecznych zasad załączników za pomocą programu PowerShell

Aby utworzyć bezpieczne zasady dotyczące załączników, użyj tej składni:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

W tym przykładzie są tworzyne bezpieczne zasady załączników o nazwie Contoso All z następującymi wartościami:

- Zablokuj wiadomości zawierające złośliwe oprogramowanie, używając funkcji skanowania Sejf (nie używamy parametru _Action_, a wartość domyślna to `Block`).
- Domyślne zasady [kwarantanny](quarantine-policies.md) są używane (AdminOnlyAccessPolicy), ponieważ nie używamy _parametru QuarantineTag_ .
- Przekierowywanie jest włączone, a wiadomości, które zostały znalezione jako zawierające złośliwe oprogramowanie, są wysyłane sec-ops@contoso.com analizy i analizy.
- Jeśli Sejf załączników nie jest dostępne lub występują błędy, nie dostarczaj wiadomości (nie używamy parametru _ActionOnError_, a wartość domyślna to `$true`).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania zasad [kwarantanny](quarantine-policies.md) do używania w bezpiecznych zasadach załączników, zobacz Określanie zasad kwarantanny za pomocą programu PowerShell w programie [Sejf Załączniki](quarantine-policies.md#safe-attachments-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>Krok 2. Tworzenie reguły bezpiecznego załącznika przy użyciu programu PowerShell

Aby utworzyć regułę bezpiecznych załączników, użyj tej składni:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

W tym przykładzie jest  biurze tworzenia bezpiecznej reguły załączników o nazwie Contoso All z następującymi warunkami:

- Reguła jest skojarzona z bezpiecznymi zasadami załączników o nazwie Contoso All.
- Ta reguła dotyczy wszystkich adresatów w contoso.com domeny.
- Ponieważ nie używamy parametru _Priority_ , używany jest priorytet domyślny.
- Reguła jest włączona (nie używamy _parametru Enabled_ , a wartość domyślna to `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Wyświetlanie zasad bezpiecznych załączników przy użyciu programu PowerShell

Aby wyświetlić istniejące bezpieczne zasady załączników, użyj następującej składni:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

W tym przykładzie zostanie wyświetlona lista podsumowania wszystkich bezpiecznych zasad załączników.

```PowerShell
Get-SafeAttachmentPolicy
```

W tym przykładzie są zwracane szczegółowe informacje dotyczące bezpiecznych zasad załączników o nazwie Kadra kierownicza Firmy Contoso.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Wyświetlanie reguł bezpiecznych załączników przy użyciu programu PowerShell

Aby wyświetlić istniejące bezpieczne reguły załączników, użyj następującej składni:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

W tym przykładzie zostanie wyświetlona lista podsumowania wszystkich bezpiecznych reguł załączników.

```PowerShell
Get-SafeAttachmentRule
```

Aby przefiltrować listę według włączonych lub wyłączonych reguł, uruchom następujące polecenia:

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

W tym przykładzie są zwracane szczegółowe informacje dotyczące reguły bezpiecznych załączników o nazwie Kierownictwo Contoso.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Modyfikowanie zasad bezpiecznych załączników przy użyciu programu PowerShell

W programie PowerShell nie można zmienić nazwy zasady bezpiecznych załączników (polecenie cmdlet **Set-SafeAttachmentPolicy** nie _ma parametru Name_ ). Po zmianie nazwy Sejf załączników w portalu Microsoft 365 Defender załączników zmieniasz tylko nazwę reguły bezpiecznych _załączników_.

W przeciwnym razie po utworzeniu bezpiecznych zasad załączników są dostępne te same ustawienia, co opisano w sekcji Krok 1. Tworzenie bezpiecznych zasad załączników za pomocą programu [PowerShell](#step-1-use-powershell-to-create-a-safe-attachment-policy) we wcześniejszej części tego artykułu.

Aby zmodyfikować bezpieczne zasady dotyczące załączników, użyj tej składni:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania zasad [kwarantanny](quarantine-policies.md) do używania w bezpiecznych zasadach załączników, zobacz Określanie zasad kwarantanny za pomocą programu PowerShell w programie [Sejf Załączniki](quarantine-policies.md#safe-attachments-policies-in-powershell).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Modyfikowanie bezpiecznych reguł załączników za pomocą programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły bezpiecznego załącznika w programie PowerShell, jest parametr _Enabled_ umożliwiający utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące bezpieczne reguły załączników, zobacz następną sekcję.

W przeciwnym razie podczas tworzenia reguły będą dostępne te same ustawienia, co opisano w sekcji Krok 2. Tworzenie bezpiecznej reguły załączników za pomocą programu [PowerShell](#step-2-use-powershell-to-create-a-safe-attachment-rule) we wcześniejszej części tego artykułu.

Aby zmodyfikować regułę bezpiecznych załączników, użyj tej składni:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Włączanie lub wyłączanie reguł bezpiecznych załączników przy użyciu programu PowerShell

Włączenie lub wyłączenie reguły bezpiecznego załącznika w programie PowerShell włącza lub wyłącza całą zasadę załączników załączników Sejf (regułę bezpiecznych załączników i przypisane zasady bezpiecznych załączników).

Aby włączyć lub wyłączyć regułę bezpiecznego załącznika w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

W tym przykładzie wyłączyno regułę bezpiecznych załączników o nazwie Dział marketingu.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

W tym przykładzie ta sama reguła jest włączana.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) i [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Ustawianie priorytetu bezpiecznych reguł załączników za pomocą programu PowerShell

Wartość najwyższego priorytetu, jaki można ustawić dla reguły, wynosi 0. Najniższa wartość, która można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć wpływ na inne reguły kaskadowe. Jeśli na przykład masz pięć reguł niestandardowych (priorytet od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet bezpiecznej reguły załączników w programie PowerShell, użyj następującej składni:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie dla reguły o nazwie Dział marketingu jest ustawiany priorytet na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich numery priorytetów są zwiększane o 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Uwaga**: Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj zamiast tego _parametru Priority_ polecenia cmdlet **New-SafeAttachmentRule** .

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Usuwanie bezpiecznych zasad załączników przy użyciu programu PowerShell

Podczas usuwania bezpiecznych zasad załączników za pomocą programu PowerShell odpowiednia reguła bezpiecznego załącznika nie jest usuwana.

Aby usunąć zasady bezpiecznych załączników w programie PowerShell, użyj tej składni:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

W tym przykładzie zasady bezpiecznych załączników o nazwie Dział marketingu są usuwane.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Usuwanie bezpiecznych reguł załączników za pomocą programu PowerShell

Gdy usuwasz regułę bezpiecznych załączników za pomocą programu PowerShell, odpowiadające im zasady bezpiecznych załączników nie są usuwane.

Aby usunąć regułę bezpiecznego załącznika w programie PowerShell, użyj tej składni:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

W tym przykładzie jest usuwana reguła bezpiecznych załączników o nazwie Dział marketingu.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiadomo, że te procedury działały?

Aby sprawdzić, czy zasady załączników załączników zostały pomyślnie utworzone, zmodyfikowane lub usunięte Sejf, wykonaj dowolną z następujących czynności:

- Na stronie **Sejf** <https://security.microsoft.com/safeattachmentv2>Załączniki w portalu Microsoft 365 Defender w miejscu sprawdź listę zasad, wartości ich statusów i **wartości Priorytet**. Aby wyświetlić więcej szczegółów, wybierz zasady z listy, klikając nazwę, a następnie wyświetl szczegóły w wysuwanych listach.

- W Exchange Online PowerShell lub Exchange Online Protection PowerShell \<Name\> zastąp zasady lub regułę nazwą, uruchom następujące polecenie i sprawdź ustawienia:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Aby sprawdzić, Sejf załączniki skanują wiadomości, sprawdź, czy w dostępnym programie Defender są Office 365 raporty. Aby uzyskać więcej informacji, zobacz Wyświetlanie raportów dotyczących usługi [Defender dla](view-reports-for-mdo.md) Office 365 [i Używanie Eksploratora w Microsoft 365 Defender sieci.](threat-explorer.md)
