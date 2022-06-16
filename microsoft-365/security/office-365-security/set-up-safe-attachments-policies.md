---
title: Konfigurowanie zasad załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender
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
description: Dowiedz się, jak zdefiniować zasady Sejf Załączniki, aby chronić organizację przed złośliwymi plikami w wiadomości e-mail.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 46b69c1bea0f967fe22c031397a8887f3399c99b
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115570"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Konfigurowanie zasad załączników Sejf w Ochrona usługi Office 365 w usłudze Microsoft Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Ten artykuł jest przeznaczony dla klientów biznesowych, którzy [mają Ochrona usługi Office 365 w usłudze Microsoft Defender](whats-new-in-defender-for-office-365.md). Jeśli jesteś użytkownikiem domowym, który szuka informacji o skanowaniu załączników w Outlook, zobacz [Zaawansowane zabezpieczenia Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sejf Załączniki to funkcja w [Ochrona usługi Office 365 w usłudze Microsoft Defender](whats-new-in-defender-for-office-365.md), która używa środowiska wirtualnego do sprawdzania załączników w przychodzących wiadomościach e-mail po ich skanowaniu za pomocą [ochrony przed złośliwym oprogramowaniem w Exchange Online Protection (EOP)](anti-malware-protection.md) , ale przed dostarczeniem do adresatów. Aby uzyskać więcej informacji, zobacz [Sejf Załączniki w Ochrona usługi Office 365 w usłudze Microsoft Defender](safe-attachments.md).

Mimo że nie ma domyślnych zasad Sejf Załączniki, wbudowane zasady zabezpieczeń **wstępnie ustawione ochrony** zapewniają ochronę Sejf załączników wszystkim adresatom (użytkownikom, którzy nie są zdefiniowani w niestandardowych zasadach załączników Sejf). Aby uzyskać więcej informacji, zobacz [Preset security policies in EOP and Ochrona usługi Office 365 w usłudze Microsoft Defender (Ustawienia wstępne zasad zabezpieczeń w usłudze EOP i Ochrona usługi Office 365 w usłudze Microsoft Defender](preset-security-policies.md)). Procedury opisane w tym artykule umożliwiają również tworzenie zasad Sejf Załączniki, które mają zastosowanie do określonych użytkowników, grup lub domen.

Zasady załączników Sejf można skonfigurować w portalu Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla kwalifikujących się organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomicznym programem PowerShell EOP dla organizacji bez Exchange Online skrzynki pocztowe, ale z Ochrona usługi Office 365 w usłudze Defender subskrypcjami dodatków).

Podstawowe elementy zasad załączników Sejf to:

- **Zasady bezpiecznego załącznika**: określa akcje wykrywania nieznanego złośliwego oprogramowania, czy wysyłać wiadomości z załącznikami złośliwego oprogramowania na określony adres e-mail oraz czy dostarczać wiadomości, jeśli skanowanie Sejf załączników nie może zakończyć się.
- **Reguła bezpiecznego załącznika**: określa filtry priorytetu i adresata (do kogo mają zastosowanie zasady).

Różnica między tymi dwoma elementami nie jest oczywista podczas zarządzania zasadami Sejf Załączniki w portalu Microsoft 365 Defender:

- Podczas tworzenia zasad Sejf Załączniki tworzysz regułę bezpiecznego załącznika i skojarzone zasady bezpiecznego załącznika w tym samym czasie, używając tej samej nazwy dla obu.
- Podczas modyfikowania zasad Sejf Załączniki ustawienia związane z nazwą, priorytetem, włączoną lub wyłączoną, a filtry adresatów modyfikują regułę bezpiecznego załącznika. Wszystkie inne ustawienia modyfikują skojarzone zasady bezpiecznego załącznika.
- Po usunięciu zasad Sejf Załączniki zostanie usunięta reguła bezpiecznego załącznika i skojarzone zasady bezpiecznego załącznika.

W programie Exchange Online programie PowerShell lub autonomicznym programie PowerShell EOP zasady i reguła są zarządzane oddzielnie. Aby uzyskać więcej informacji, zobacz sekcję [Use Exchange Online PowerShell or standalone EOP PowerShell to configure Sejf Attachments policies (Konfigurowanie zasad Sejf załączników](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies)) w dalszej części tego artykułu.

> [!NOTE]
> W obszarze ustawień globalnych ustawień Sejf Załączniki należy skonfigurować funkcje, które nie są zależne od zasad załączników Sejf. Aby uzyskać instrukcje[, zobacz Włączanie załączników Sejf dla SharePoint, OneDrive oraz dokumentów Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) i [Sejf w Microsoft 365 E5](safe-docs.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Przed wykonaniem procedur w tym artykule potrzebne są uprawnienia:
  - Aby tworzyć, modyfikować i usuwać zasady załączników Sejf, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** w portalu Microsoft 365 Defender **i** członkiem grupy ról **Zarządzanie organizacją** w Exchange Online.
  - Aby uzyskać dostęp tylko do odczytu do zasad załączników Sejf, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** w portalu Microsoft 365 Defender.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w portalu Microsoft 365 Defender](permissions-microsoft-365-security-center.md) i [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia w portalu Microsoft 365 Defender _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Aby zapoznać się z naszymi zalecanymi ustawieniami zasad Sejf Załączniki, zobacz [Sejf Ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- Zaczekaj do 30 minut na zastosowanie nowych lub zaktualizowanych zasad.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>Tworzenie zasad załączników Sejf przy użyciu portalu Microsoft 365 Defender

Utworzenie niestandardowych zasad Sejf Załączniki w portalu Microsoft 365 Defender tworzy regułę bezpiecznego załącznika i skojarzone zasady bezpiecznego załącznika w tym samym czasie przy użyciu tej samej nazwy dla obu.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> **zagrożeń** \> **Sejf załączniki** w sekcji Zasady. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz**.

3. Zostanie otwarty kreator zasad. Na stronie **Nazwa zasad** skonfiguruj następujące ustawienia:
   - **Nazwa**: wprowadź unikatową, opisową nazwę zasad.
   - **Opis**: wprowadź opcjonalny opis zasad.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na wyświetlonej stronie **Użytkownicy i domeny** zidentyfikuj wewnętrznych adresatów, których dotyczą zasady (warunki adresatów):
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

5. Na stronie **Ustawienia** skonfiguruj następujące ustawienia:

   - **Sejf Odpowiedzi na nieznane złośliwe oprogramowanie załączników**: Wybierz jedną z następujących wartości:
     - **Wyłączone**: zazwyczaj nie zalecamy tej wartości.
     - **Monitor**
     - **Blokuj**: jest to wartość domyślna i zalecana wartość w standardowych i ścisłych [wstępnie ustawionych zasad zabezpieczeń](preset-security-policies.md).
     - **Zastąpić**
     - **Dostarczanie dynamiczne (funkcja w wersji zapoznawczej)**

     Te wartości zostały wyjaśnione w [ustawieniach zasad Sejf Załączniki](safe-attachments.md#safe-attachments-policy-settings).

   - **Zasady kwarantanny**: wybierz zasady kwarantanny, które mają zastosowanie do komunikatów poddawanych kwarantannie przez Sejf Załączniki (**Blokuj**, **Zastąp** lub **Dynamiczne dostarczanie**). Zasady kwarantanny określają, co użytkownicy mogą zrobić w przypadku komunikatów poddanych kwarantannie oraz czy użytkownicy otrzymują powiadomienia o kwarantannie. Aby uzyskać więcej informacji, zobacz [Zasady kwarantanny](quarantine-policies.md).

     Pusta wartość oznacza, że są używane domyślne zasady kwarantanny (AdminOnlyAccessPolicy do wykrywania poczty e-mail przez Sejf załączników). Po późniejszej edycji zasad Sejf Załączniki lub wyświetleniu ustawień wyświetlana jest domyślna nazwa zasad kwarantanny.

   - **Przekierowywanie wiadomości z wykrytymi załącznikami**: jeśli wybierzesz pozycję **Włącz przekierowanie**, możesz określić adres e-mail w polu **Wyślij wiadomości zawierające zablokowane, monitorowane lub zastąpione załączniki do określonego pola adresu e-mail** , aby wysyłać wiadomości zawierające załączniki złośliwego oprogramowania do analizy i badania.

     Zalecenia dotyczące standardowych i ścisłych ustawień zasad to włączenie przekierowania. Aby uzyskać więcej informacji, zobacz [Sejf Ustawienia załączników](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - **Zastosuj odpowiedź wykrywania załączników Sejf, jeśli skanowanie nie może zakończyć się (przekroczenie limitu czasu lub błędy)**: Akcja określona przez **Sejf Odpowiedzi na nieznane złośliwe oprogramowanie załączników** są wykonywane w przypadku komunikatów, nawet jeśli skanowanie załączników Sejf nie może zakończyć się. Jeśli wybrano tę opcję, zawsze wybierz pozycję **Włącz przekierowanie** i określ adres e-mail do wysyłania wiadomości zawierających załączniki złośliwego oprogramowania. W przeciwnym razie komunikaty mogą zostać utracone.

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na wyświetlonej stronie **Przegląd** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Prześlij**.

7. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>Wyświetlanie zasad załączników Sejf przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> **zagrożeń** \> **Sejf załączniki** w sekcji Zasady. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** na liście zasad są wyświetlane następujące właściwości:
   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**

3. Po wybraniu zasad przez kliknięcie nazwy ustawienia zasad są wyświetlane w wysuwnym oknie.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>Modyfikowanie zasad załączników Sejf przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender w witrynie <https://security.microsoft.com>przejdź  do obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące zagrożeń** \>  \> **Sejf załączniki** w sekcji Zasady. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** wybierz zasady z listy, klikając nazwę.

3. W wyświetlonym wysuwu szczegółów zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji na temat ustawień, zobacz sekcję [Używanie portalu Microsoft 365 Defender do tworzenia zasad załączników Sejf](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) wcześniej w tym artykule.

Aby włączyć lub wyłączyć zasady lub ustawić kolejność priorytetów zasad, zobacz następujące sekcje.

### <a name="enable-or-disable-safe-attachments-policies"></a>Włączanie lub wyłączanie zasad załączników Sejf

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> **zagrożeń** \> **Sejf załączniki** w sekcji Zasady. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** wybierz zasady z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz jedną z następujących wartości:
   - **Zasady wyłączone**: aby włączyć zasady, kliknij pozycję ![Włącz ikonę.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz pozycję** .
   - **Zasady włączone**: aby wyłączyć zasady, kliknij pozycję Wyłącz ikonę ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij pozycję **Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanym oknie szczegółów zasad.

Po powrocie na stronę zasad głównych wartość **Stan** zasad będzie **włączona** lub **wyłączona**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Ustawianie priorytetu zasad załączników Sejf

Domyślnie Sejf zasady załączników mają priorytet oparty na kolejności, w jakiej zostały utworzone (nowsze zasady mają niższy priorytet niż starsze zasady). Niższy numer priorytetu wskazuje wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

Aby uzyskać więcej informacji na temat kolejności pierwszeństwa oraz sposobu oceniania i stosowania wielu zasad, zobacz [Kolejność i pierwszeństwo ochrony poczty e-mail](how-policies-and-protections-are-combined.md).

Sejf zasady załączników są wyświetlane w kolejności ich przetwarzania (pierwsza zasada ma wartość **Priorytet** 0).

**Uwaga**: w portalu Microsoft 365 Defender można zmienić priorytet zasad Sejf Załączniki tylko po jego utworzeniu. W programie PowerShell można zastąpić priorytet domyślny podczas tworzenia reguły bezpiecznego załącznika (co może mieć wpływ na priorytet istniejących reguł).

Aby zmienić priorytet zasad, kliknij pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** we właściwościach zasad (nie możesz bezpośrednio zmodyfikować numeru **Priorytet** w portalu Microsoft 365 Defender). Zmiana priorytetu zasad ma sens tylko wtedy, gdy masz wiele zasad.

1. W portalu Microsoft 365 Defender przejdź do obszaru Zasady  współpracy \> **& poczty e-mail** **& zasady dotyczące zagrożeń** \>  \> **Sejf załączniki** w sekcji Zasady.

2. Na stronie **Sejf Załączniki** wybierz zasady z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** na podstawie bieżącej wartości priorytetu i liczby zasad:
   - Zasady z **wartością Priorytet** **0** mają dostępną tylko opcję **Zmniejsz priorytet** .
   - Zasady z najniższą **wartością priorytetu** (na przykład **3**) mają dostępną tylko opcję **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady, zasady między wartościami o najwyższym i najniższym priorytecie mają dostępne opcje **Zwiększanie priorytetu** i **Zmniejszanie priorytetu** .

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Zwiększ priorytet** lub ![Zmniejsz priorytet **ikona**](../../media/m365-cc-sc-decrease-icon.png) Zmniejsz priorytet, aby zmienić wartość **Priorytet**.

4. Po zakończeniu kliknij przycisk **Zamknij** w wysuwanym oknie szczegółów zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>Usuwanie zasad załączników Sejf przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& reguły** \> **zagrożeń** \> **Sejf załączniki** w sekcji Zasady. Aby przejść bezpośrednio do strony **załączników Sejf**, użyj polecenia <https://security.microsoft.com/safeattachmentv2>.

2. Na stronie **Sejf Załączniki** wybierz z listy zasady niestandardowe, klikając nazwę zasad.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Usuń ikonę](../../media/m365-cc-sc-delete-icon.png) zasad **Usuń zasady**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Konfigurowanie zasad załączników Sejf przy użyciu Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP

Zgodnie z wcześniejszym opisem zasady załączników Sejf składają się z zasad bezpiecznego załącznika i reguły bezpiecznego załącznika.

W programie PowerShell widoczna jest różnica między zasadami bezpiecznego załącznika a regułami bezpiecznego załącznika. Zasady bezpiecznego załącznika można zarządzać przy użyciu **\*poleceń cmdlet -SafeAttachmentPolicy** i zarządzać regułami bezpiecznego załącznika przy użyciu **\*poleceń cmdlet -SafeAttachmentRule** .

- W programie PowerShell najpierw utworzysz zasady bezpiecznego załącznika, a następnie utworzysz regułę bezpiecznego załącznika, która identyfikuje zasady, do których ma zastosowanie reguła.
- W programie PowerShell ustawienia zasad bezpiecznego załącznika i reguły bezpiecznego załącznika są modyfikowane oddzielnie.
- Po usunięciu zasad bezpiecznego załącznika z programu PowerShell odpowiednia reguła bezpiecznego załącznika nie zostanie automatycznie usunięta i na odwrót.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Tworzenie zasad załączników Sejf przy użyciu programu PowerShell

Tworzenie zasad załączników Sejf w programie PowerShell to proces dwuetapowy:

1. Utwórz zasady bezpiecznego załącznika.
2. Utwórz regułę bezpiecznego załącznika określającą zasady bezpiecznego załącznika, do których ma zastosowanie reguła.

 **Uwagi**:

- Możesz utworzyć nową regułę bezpiecznego załącznika i przypisać do niej istniejące, nieskojarzone zasady bezpiecznego załącznika. Reguły bezpiecznego załącznika nie można skojarzyć z więcej niż jedną zasadą bezpiecznego załącznika.

- W programie PowerShell można skonfigurować następujące ustawienia dla nowych zasad bezpiecznego załącznika, które nie są dostępne w portalu Microsoft 365 Defender, dopóki nie zostaną utworzone zasady:
  - Utwórz nowe zasady jako wyłączone (_włączone_ `$false` w poleceniu cmdlet **New-SafeAttachmentRule** ).
  - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) w poleceniu cmdlet **New-SafeAttachmentRule**).

- Nowe zasady bezpiecznego załącznika utworzone w programie PowerShell nie są widoczne w portalu Microsoft 365 Defender, dopóki zasady nie zostaną przypisane do reguły bezpiecznego załącznika.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>Krok 1. Tworzenie zasad bezpiecznego załącznika przy użyciu programu PowerShell

Aby utworzyć zasady bezpiecznego załącznika, użyj tej składni:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

W tym przykładzie tworzone są zasady bezpiecznego załącznika o nazwie Contoso All z następującymi wartościami:

- Blokuj komunikaty zawierające złośliwe oprogramowanie przez skanowanie dokumentów Sejf (nie używamy parametru _Action_, a wartość domyślna to `Block`).
- Domyślne [zasady kwarantanny](quarantine-policies.md) są używane (AdminOnlyAccessPolicy), ponieważ nie używamy parametru _QuarantineTag_ .
- Przekierowanie jest włączone, a komunikaty zawierające złośliwe oprogramowanie są wysyłane do sec-ops@contoso.com w celu przeprowadzenia analizy i zbadania.
- Jeśli skanowanie załączników Sejf jest niedostępne lub występują błędy, nie dostarczaj komunikatu (nie używamy parametru _ActionOnError_, a wartość domyślna to `$true`).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania [zasad kwarantanny](quarantine-policies.md) do użycia w zasadach bezpiecznego załącznika, zobacz [Używanie programu PowerShell do określania zasad kwarantanny w zasadach Sejf Załączniki](quarantine-policies.md#safe-attachments-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>Krok 2. Tworzenie reguły bezpiecznego załącznika przy użyciu programu PowerShell

Aby utworzyć regułę bezpiecznego załącznika, użyj tej składni:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

W tym przykładzie utworzono regułę bezpiecznego załącznika o nazwie Contoso All z następującymi warunkami:

- Reguła jest skojarzona z zasadami bezpiecznego załącznika o nazwie Contoso All.
- Reguła ma zastosowanie do wszystkich adresatów w domenie contoso.com.
- Ponieważ nie używamy parametru _Priority_ , używany jest priorytet domyślny.
- Reguła jest włączona (nie używamy parametru _Enabled_ , a wartość domyślna to `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Wyświetlanie zasad bezpiecznego załącznika przy użyciu programu PowerShell

Aby wyświetlić istniejące zasady bezpiecznego załącznika, użyj następującej składni:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Ten przykład zwraca listę podsumowania wszystkich zasad bezpiecznego załącznika.

```PowerShell
Get-SafeAttachmentPolicy
```

Ten przykład zwraca szczegółowe informacje dotyczące zasad bezpiecznego załącznika o nazwie Kierownictwo firmy Contoso.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Wyświetlanie reguł bezpiecznego załącznika przy użyciu programu PowerShell

Aby wyświetlić istniejące reguły bezpiecznego załącznika, użyj następującej składni:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Ten przykład zwraca listę podsumowania wszystkich reguł bezpiecznego załącznika.

```PowerShell
Get-SafeAttachmentRule
```

Aby filtrować listę według reguł włączonych lub wyłączonych, uruchom następujące polecenia:

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

Ten przykład zwraca szczegółowe informacje dotyczące reguły bezpiecznego załącznika o nazwie Kierownictwo firmy Contoso.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Modyfikowanie zasad bezpiecznego załącznika przy użyciu programu PowerShell

Nie można zmienić nazwy zasad bezpiecznego załącznika w programie PowerShell (polecenie cmdlet **Set-SafeAttachmentPolicy** nie ma parametru _Name_ ). Po zmianie nazwy zasad Sejf Załączniki w portalu Microsoft 365 Defender zmieniasz tylko nazwę _reguły_ bezpiecznego załącznika.

W przeciwnym razie te same ustawienia są dostępne podczas tworzenia zasad bezpiecznego załącznika zgodnie z opisem w sekcji [Krok 1: Tworzenie zasad bezpiecznego załącznika za pomocą programu PowerShell we wcześniejszej](#step-1-use-powershell-to-create-a-safe-attachment-policy) części tego artykułu.

Aby zmodyfikować zasady bezpiecznego załącznika, użyj tej składni:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> Aby uzyskać szczegółowe instrukcje dotyczące określania [zasad kwarantanny](quarantine-policies.md) do użycia w zasadach bezpiecznego załącznika, zobacz [Używanie programu PowerShell do określania zasad kwarantanny w zasadach Sejf Załączniki](quarantine-policies.md#safe-attachments-policies-in-powershell).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Modyfikowanie reguł bezpiecznego załącznika przy użyciu programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły bezpiecznego załącznika w programie PowerShell, jest parametr _Enabled_ , który umożliwia utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły bezpiecznego załącznika, zobacz następną sekcję.

W przeciwnym razie te same ustawienia są dostępne podczas tworzenia reguły zgodnie z opisem w sekcji [Krok 2: Tworzenie reguły bezpiecznego załącznika za pomocą programu PowerShell we wcześniejszej](#step-2-use-powershell-to-create-a-safe-attachment-rule) części tego artykułu.

Aby zmodyfikować regułę bezpiecznego załącznika, użyj tej składni:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Włączanie lub wyłączanie reguł bezpiecznego załącznika za pomocą programu PowerShell

Włączenie lub wyłączenie reguły bezpiecznego załącznika w programie PowerShell umożliwia lub wyłącza całą zasadę załączników Sejf (regułę bezpiecznego załącznika i przypisane zasady bezpiecznego załącznika).

Aby włączyć lub wyłączyć regułę bezpiecznego załącznika w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

W tym przykładzie wyłączono regułę bezpiecznego załącznika o nazwie Dział marketingu.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

W tym przykładzie włączono tę samą regułę.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) i [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Ustawianie priorytetu reguł bezpiecznego załącznika przy użyciu programu PowerShell

Wartość o najwyższym priorytecie, którą można ustawić dla reguły, to 0. Najniższa wartość, którą można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć kaskadowy wpływ na inne reguły. Jeśli na przykład masz pięć reguł niestandardowych (priorytety od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły bezpiecznego załącznika w programie PowerShell, użyj następującej składni:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie ustawiono priorytet reguły o nazwie Dział marketingu na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich priorytety są zwiększane o 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Uwaga**: Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj parametru _Priority_ w poleceniu cmdlet **New-SafeAttachmentRule** .

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Usuwanie zasad bezpiecznego załącznika przy użyciu programu PowerShell

W przypadku korzystania z programu PowerShell w celu usunięcia zasad bezpiecznego załącznika odpowiednia reguła bezpiecznego załącznika nie zostanie usunięta.

Aby usunąć zasady bezpiecznego załącznika w programie PowerShell, użyj tej składni:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

W tym przykładzie usunięto zasady bezpiecznego załącznika o nazwie Dział marketingu.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Usuwanie reguł bezpiecznego załącznika przy użyciu programu PowerShell

Jeśli używasz programu PowerShell do usunięcia reguły bezpiecznego załącznika, odpowiednie zasady bezpiecznego załącznika nie zostaną usunięte.

Aby usunąć regułę bezpiecznego załącznika w programie PowerShell, użyj tej składni:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

W tym przykładzie usunięto regułę bezpiecznego załącznika o nazwie Dział marketingu.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Skąd wiesz, że te procedury zadziałają?

Aby sprawdzić, czy zostały pomyślnie utworzone, zmodyfikowane lub usunięte Sejf zasad załączników, wykonaj dowolne z następujących czynności:

- Na stronie **załączników Sejf** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/safeattachmentv2>sprawdź listę zasad, ich wartości **stanu** i wartości **priorytetu**. Aby wyświetlić więcej szczegółów, wybierz zasady z listy, klikając nazwę i wyświetlając szczegóły w wysuwanej oknie.

- W Exchange Online programu PowerShell lub Exchange Online Protection programu PowerShell zastąp \<Name\> ciąg nazwą zasad lub reguły, uruchom następujące polecenie i sprawdź ustawienia:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Aby sprawdzić, czy Sejf Załączniki skanują komunikaty, sprawdź dostępne Ochrona usługi Office 365 w usłudze Defender raporty. Aby uzyskać więcej informacji, zobacz [Wyświetlanie raportów dla Ochrona usługi Office 365 w usłudze Defender](view-reports-for-mdo.md) i [Korzystanie z Eksploratora w portalu Microsoft 365 Defender](threat-explorer.md).
