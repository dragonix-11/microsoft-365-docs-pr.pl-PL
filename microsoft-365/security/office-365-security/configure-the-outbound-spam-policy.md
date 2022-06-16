---
title: Konfigurowanie filtrowania spamu wychodzącego
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak wyświetlać, tworzyć, modyfikować i usuwać zasady spamu wychodzącego w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 690d4def4081812653cb533765f6c61cca7d1e90
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115834"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>Konfigurowanie filtrowania wychodzącego spamu w ramach operacji EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online lub autonomicznych organizacjach Exchange Online Protection (EOP) bez Exchange Online skrzynek pocztowych, wychodzące wiadomości e-mail wysyłane za pośrednictwem EOP są automatycznie sprawdzane pod kątem spamu i nietypowych działań wysyłania.

Spam wychodzący od użytkownika w organizacji zazwyczaj wskazuje konto, których bezpieczeństwo zostało naruszone. Podejrzane wiadomości wychodzące są oznaczone jako spam (niezależnie od poziomu ufności spamu lub listy SCL) i są kierowane przez [pulę dostarczania wysokiego ryzyka](high-risk-delivery-pool-for-outbound-messages.md), aby chronić reputację usługi (tj. zachować Microsoft 365 źródłowych serwerów poczty e-mail poza listami zablokowanych adresów IP). Administratorzy są automatycznie powiadamiani o podejrzanych wychodzących działaniach poczty e-mail i blokowani użytkownicy za pośrednictwem [zasad alertów](../../compliance/alert-policies.md).

W ramach ogólnej ochrony organizacji przed spamem EOP używa zasad spamu wychodzącego. Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem](anti-spam-protection.md).

Administratorzy mogą wyświetlać, edytować i konfigurować (ale nie usuwać) domyślnych zasad spamu wychodzącego. Aby uzyskać większy stopień szczegółowości, można również utworzyć niestandardowe zasady spamu wychodzącego, które mają zastosowanie do określonych użytkowników, grup lub domen w organizacji. Zasady niestandardowe zawsze mają pierwszeństwo przed zasadami domyślnymi, ale można zmienić priorytet (kolejność uruchamiania) zasad niestandardowych.

Zasady spamu wychodzącego można skonfigurować w portalu Microsoft 365 Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online; autonomicznym programem PowerShell EOP dla organizacji bez Exchange Online skrzynek pocztowych).

Podstawowe elementy zasad wychodzącego spamu w ramach operacji EOP to:

- **Zasady filtru spamu wychodzącego**: określa akcje dotyczące werdyktów filtrowania spamu wychodzącego i opcji powiadomień.
- **Reguła filtru spamu wychodzącego**: określa priorytet i filtry nadawcy (które dotyczą zasad) dla zasad filtru spamu wychodzącego.

Różnica między tymi dwoma elementami nie jest oczywista podczas zarządzania wychodzącymi zasadami spamu w portalu Microsoft 365 Defender:

- Podczas tworzenia zasad tworzysz regułę filtru spamu wychodzącego i skojarzone zasady filtru spamu wychodzącego w tym samym czasie, używając tej samej nazwy dla obu.
- Podczas modyfikowania zasad ustawienia związane z nazwą, priorytetem, włączonym lub wyłączonym oraz filtrami nadawcy modyfikują regułę filtru spamu wychodzącego. Wszystkie inne ustawienia modyfikują skojarzone zasady filtrowania spamu wychodzącego.
- Po usunięciu zasad zostanie usunięta reguła filtru spamu wychodzącego i skojarzone zasady filtru spamu wychodzącego.

W programie Exchange Online programie PowerShell lub autonomicznym programie PowerShell EOP zasady i reguła są zarządzane oddzielnie. Aby uzyskać więcej informacji, zobacz sekcję [Use Exchange Online PowerShell or standalone EOP PowerShell to configure outbound spam policies (Używanie Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP do konfigurowania zasad spamu wychodzącego](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) w dalszej części tego artykułu).

Każda organizacja ma wbudowane zasady spamu wychodzącego o nazwie Domyślne, które mają następujące właściwości:

- Zasady są stosowane do wszystkich nadawców w organizacji, mimo że z zasadami nie jest skojarzona żadna reguła filtru spamu wychodzącego (filtry nadawcy).
- Zasady mają niestandardową wartość priorytetu **Najniższa** , którą nie można zmodyfikować (zasady są zawsze stosowane jako ostatnie). Wszystkie utworzone zasady niestandardowe zawsze mają wyższy priorytet niż zasady o nazwie Domyślne.
- Zasady to zasady domyślne (właściwość **IsDefault** ma wartość `True`) i nie można usunąć zasad domyślnych.

Aby zwiększyć skuteczność filtrowania spamu wychodzącego, można utworzyć niestandardowe zasady spamu wychodzącego z bardziej rygorystycznymi ustawieniami stosowanymi do określonych użytkowników lub grup użytkowników.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby dodawać, modyfikować i usuwać wychodzące zasady spamu, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do wychodzących zasad spamu, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Aby zapoznać się z naszymi zalecanymi ustawieniami dla zasad dotyczących spamu wychodzącego, zobacz [Ustawienia zasad filtru spamu wychodzącego EOP](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings).

- Przekroczono domyślne [zasady alertów](../../compliance/alert-policies.md) o nazwie **Limit wysyłania wiadomości e-mail**, **wykryto podejrzane wzorce wysyłania wiadomości e-mail**, a **użytkownik nie może wysyłać wiadomości e-mail** , które już wysyłają powiadomienia e-mail do członków grupy **TenantAdmins** (**administratorzy globalni**) o nietypowej aktywności wychodzącej poczty e-mail i zablokowaniu użytkowników z powodu spamu wychodzącego. Aby uzyskać więcej informacji, zobacz [Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Zalecamy użycie tych zasad alertów zamiast opcji powiadomień w zasadach spamu wychodzącego.

## <a name="use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies"></a>Tworzenie zasad spamu wychodzącego przy użyciu portalu Microsoft 365 Defender

Utworzenie niestandardowych zasad spamu wychodzącego w portalu Microsoft 365 Defender tworzy regułę filtru spamu i skojarzone zasady filtrowania spamu w tym samym czasie przy użyciu tej samej nazwy dla obu.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz zasady,** a następnie wybierz pozycję **Wychodzące** z listy rozwijanej.

3. Zostanie otwarty kreator zasad. Na **stronie Nazwa zasad** skonfiguruj następujące ustawienia:
   - **Nazwa**: wprowadź unikatową, opisową nazwę zasad.
   - **Opis**: wprowadź opcjonalny opis zasad.

   Po zakończeniu kliknij przycisk **Dalej**.

4. Na wyświetlonej stronie **Użytkownicy, grupy i domeny** zidentyfikuj wewnętrznych nadawców, których dotyczą zasady (warunki adresatów):
   - **Użytkownicy**: określone skrzynki pocztowe, użytkownicy poczty lub kontakty poczty e-mail.
   - **Grupy**:
     - Członkowie określonych grup dystrybucyjnych lub grup zabezpieczeń z obsługą poczty.
     - Określona Grupy Microsoft 365.
   - **Domeny**: Wszyscy nadawcy w określonych [zaakceptowanych domenach](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) w organizacji.

   Kliknij odpowiednie pole, zacznij wpisywać wartość i wybierz żądaną wartość z wyników. Powtórz ten proces tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   W przypadku użytkowników lub grup można użyć większości identyfikatorów (nazwa, nazwa wyświetlana, alias, adres e-mail, nazwa konta itp.), ale w wynikach jest wyświetlana odpowiednia nazwa wyświetlana. W przypadku użytkowników wprowadź gwiazdkę (\*), aby wyświetlić wszystkie dostępne wartości.

   Wiele wartości w tym samym warunku używa logiki OR (na przykład _\<sender1\>_ lub _\<sender2\>_). Różne warunki używają logiki AND (na przykład _\<sender1\>_ i _\<member of group 1\>_).

   - **Wyklucz tych użytkowników, grupy i domeny**: aby dodać wyjątki dla wewnętrznych nadawców, których dotyczą zasady (wyjątki adresatów), wybierz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie same jak warunki.

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

5. Na otwartej stronie **Ustawienia ochrony** skonfiguruj następujące ustawienia:
   - **Limity wiadomości**: ustawienia w tej sekcji umożliwiają skonfigurowanie limitów dla wychodzących wiadomości e-mail z **Exchange Online** skrzynek pocztowych:
     - **Ustaw limit komunikatów zewnętrznych**: maksymalna liczba adresatów zewnętrznych na godzinę.
     - **Ustaw wewnętrzny limit komunikatów**: maksymalna liczba adresatów wewnętrznych na godzinę.
     - **Ustaw dzienny limit wiadomości**: maksymalna łączna liczba adresatów dziennie.

     Prawidłowa wartość to od 0 do 10000. Wartość domyślna to 0, co oznacza, że są używane wartości domyślne usługi. Aby uzyskać więcej informacji, zobacz [Wysyłanie limitów](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

    Wprowadź wartość w polu lub użyj strzałek zwiększania/zmniejszania w polu.

   - **Ograniczenie nałożone na użytkowników, którzy osiągną limit komunikatów**: wybierz akcję z listy rozwijanej po przekroczeniu któregokolwiek z limitów w sekcji **Ustawienia ochrony** .

     W przypadku wszystkich akcji nadawcy określoni w zasadach **alertów e-mail użytkownika nie mogą wysyłać alertów e-mail** (a w obszarze teraz nadmiarowym **Powiadom tych użytkowników i grupy, jeśli nadawca jest zablokowany z powodu wysyłania wychodzącego spamu** później na tej stronie) odbiera powiadomienia e-mail.

     - **Ogranicz użytkownikowi wysyłanie wiadomości e-mail do następnego dnia**: jest to wartość domyślna. Powiadomienia e-mail są wysyłane, a użytkownik nie będzie w stanie wysłać więcej wiadomości do następnego dnia, na podstawie czasu UTC. Nie ma możliwości zastąpienia tego bloku przez administratora.
       - Zasady alertów o nazwie **Użytkownik z ograniczeniami wysyłania wiadomości e-mail** powiadamiają administratorów (za pośrednictwem poczty e-mail i na stronie **Zdarzenia & alerty** \> **Wyświetl alerty** ).
       - Zostaną również powiadomieni o wszystkich adresatach określonych w **ustawieniach Powiadamianie określonych osób, jeśli nadawca zostanie zablokowany z powodu wysyłania wychodzącego spamu** .
       - Użytkownik nie będzie w stanie wysłać więcej komunikatów do następnego dnia, na podstawie czasu UTC. Nie ma możliwości zastąpienia tego bloku przez administratora.
     - **Ogranicz użytkownikowi możliwość wysyłania wiadomości e-mail**: wysyłane są powiadomienia e-mail, użytkownik jest **dodawany do użytkowników** <https://security.microsoft.com/restrictedusers> z ograniczeniami w portalu Microsoft 365 Defender, a użytkownik nie może wysyłać wiadomości e-mail, dopóki nie zostanie usunięty z **użytkowników z ograniczeniami** przez administratora. Gdy administrator usunie użytkownika z listy, użytkownik nie zostanie ponownie ograniczony na ten dzień. Aby uzyskać instrukcje, zobacz [Usuwanie użytkownika z portalu Użytkownicy z ograniczeniami po wysłaniu wiadomości e-mail ze spamem](removing-user-from-restricted-users-portal-after-spam.md).
     - **Brak akcji, tylko alert**: wysyłane są powiadomienia e-mail.

   - **Reguły przekazywania**: użyj ustawień w tej sekcji, aby kontrolować automatyczne przekazywanie wiadomości e-mail przez **Exchange Online skrzynek pocztowych** do nadawców zewnętrznych. Aby uzyskać więcej informacji, zobacz [Kontrolowanie automatycznego przekazywania zewnętrznych wiadomości e-mail w Microsoft 365](external-email-forwarding.md).

     > [!NOTE]
     > Po wyłączeniu automatycznego przekazywania adresat otrzyma raport o braku dostarczania (znany również jako NDR lub wiadomość bounce), jeśli zewnętrzni nadawcy wysyłają wiadomość e-mail do skrzynki pocztowej, która ma przekierowanie. Jeśli wiadomość jest wysyłana przez wewnętrznego nadawcę **, a** metoda przekazywania to [przekazywanie skrzynek pocztowych](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (nazywane również _przekazywaniem SMTP_), wewnętrzny nadawca otrzyma identyfikator NDR. Wewnętrzny nadawca nie otrzymuje NDR, jeśli przekierowywanie nastąpiło z powodu reguły skrzynki odbiorczej.

     Wybierz jedną z następujących akcji z listy rozwijanej **Reguły automatycznego przekazywania** :

     - **Automatyczne — sterowane przez system**: umożliwia filtrowanie spamu wychodzącego w celu kontrolowania automatycznego przekazywania zewnętrznych wiadomości e-mail. Jest to wartość domyślna.
     - **Włączone**: zasady nie wyłączają automatycznego przekazywania zewnętrznych wiadomości e-mail.
     - **Wyłączone**: zasady wyłączają wszystkie automatyczne przekazywanie zewnętrznych wiadomości e-mail.

   - **Powiadomienia**: użyj ustawień w sekcji, aby skonfigurować dodatkowych adresatów, którzy powinni otrzymywać kopie i powiadomienia o podejrzanych wychodzących wiadomościach e-mail:

     - **Wyślij kopię podejrzanego ruchu wychodzącego przekraczającego te limity do tych użytkowników i grup**: to ustawienie dodaje określonych adresatów do pola Bcc podejrzanych komunikatów wychodzących.

       > [!NOTE]
       > To ustawienie działa tylko w domyślnych zasadach spamu wychodzącego. Nie działa to w ramach niestandardowych zasad spamu wychodzącego, które tworzysz.

       Aby włączyć to ustawienie, zaznacz pole wyboru. W wyświetlonym polu kliknij pole, wprowadź prawidłowy adres e-mail, a następnie naciśnij klawisz Enter lub wybierz pełną wartość wyświetlaną poniżej pola.

       Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

   - **Powiadamiaj tych użytkowników i grupy, jeśli nadawca jest zablokowany z powodu wysyłania spamu wychodzącego**

     > [!IMPORTANT]
     >
     > - To ustawienie jest w trakcie wycofywania z zasad spamu wychodzącego.
     >
     > - Domyślne [zasady alertów](../../compliance/alert-policies.md) o nazwie **Użytkownik z ograniczeniami wysyłania wiadomości e-mail** wysyłają już powiadomienia e-mail do członków grupy **TenantAdmins** (**administratorzy globalni**), gdy użytkownicy są blokowani z powodu przekroczenia limitów w sekcji **Limity adresatów** . **Zdecydowanie zalecamy używanie zasad alertów zamiast tego ustawienia w zasadach spamu wychodzącego w celu powiadamiania administratorów i innych użytkowników**. Aby uzyskać instrukcje, zobacz [Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na wyświetlonej stronie **Przegląd** przejrzyj ustawienia. W każdej sekcji możesz wybrać pozycję **Edytuj** , aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Utwórz**.

7. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-outbound-spam-policies"></a>Wyświetlanie zasad spamu wychodzącego przy użyciu portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** poszukaj jednej z następujących wartości:
   - Wartość **Typ** to **Niestandardowe zasady spamu wychodzącego**
   - Wartość **Nazwa** to **Zasady ruchu wychodzącego ochrony przed spamem (domyślne)**

   Na liście zasad ochrony przed spamem są wyświetlane następujące właściwości:

   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**
   - **Type**

3. Po wybraniu wychodzących zasad spamu przez kliknięcie nazwy ustawienia zasad są wyświetlane w wysuwnym oknie.

## <a name="use-the-microsoft-365-defender-portal-to-modify-outbound-spam-policies"></a>Modyfikowanie zasad spamu wychodzącego za pomocą portalu Microsoft 365 Defender

1.  W portalu Microsoft 365 Defender przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— ochrona przed spamem** w sekcji Zasady.

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy zasady dotyczące spamu wychodzącego, klikając nazwę:
   - Zasady niestandardowe utworzone, w których wartość w kolumnie **Typ** to **Niestandardowe zasady spamu wychodzącego**.
   - Domyślne zasady o nazwie **Zasady ruchu wychodzącego antyspamowego (domyślne).**

3. W wyświetlonym wysuwu szczegółów zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji na temat ustawień, zobacz poprzednią [sekcję Używanie portalu Microsoft 365 Defender do tworzenia wychodzących zasad spamu](#use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies) w tym artykule.

   W przypadku domyślnych zasad spamu wychodzącego sekcja **Zastosowane do** nie jest dostępna (zasady dotyczą wszystkich użytkowników) i nie można zmienić nazwy zasad.

Aby włączyć lub wyłączyć zasady, ustawić kolejność priorytetów zasad lub skonfigurować powiadomienia użytkowników końcowych, zobacz następujące sekcje.

### <a name="enable-or-disable-custom-outbound-spam-policies"></a>Włączanie lub wyłączanie niestandardowych zasad spamu wychodzącego

Nie można wyłączyć domyślnych zasad spamu wychodzącego.

1.  W portalu Microsoft 365 Defender przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— ochrona przed spamem** w sekcji Zasady.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** **niestandardowych zasad spamu wychodzącego** z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz jedną z następujących wartości:
   - **Zasady wyłączone**: aby włączyć zasady, kliknij pozycję ![Włącz ikonę.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz pozycję** .
   - **Zasady włączone**: aby wyłączyć zasady, kliknij pozycję Wyłącz ikonę ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij pozycję **Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanym oknie szczegółów zasad.

Po powrocie na stronę zasad głównych wartość **Stan** zasad będzie **włączona** lub **wyłączona**.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Ustawianie priorytetu niestandardowych zasad spamu wychodzącego

Domyślnie zasady wychodzącego spamu mają priorytet oparty na kolejności, w jakiej zostały utworzone (nowsze zasady mają niższy priorytet niż starsze zasady). Niższy numer priorytetu wskazuje wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Żadne dwie zasady nie mogą mieć takiego samego priorytetu, a przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszych zasad.

Aby zmienić priorytet zasad, kliknij pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** we właściwościach zasad (nie możesz bezpośrednio zmodyfikować numeru **Priorytet** w portalu Microsoft 365 Defender). Zmiana priorytetu zasad ma sens tylko wtedy, gdy masz wiele zasad.

 **Uwagi**:

- W portalu Microsoft 365 Defender można zmienić priorytet zasad dotyczących spamu wychodzącego dopiero po jego utworzeniu. W programie PowerShell można zastąpić priorytet domyślny podczas tworzenia reguły filtru spamu (co może mieć wpływ na priorytet istniejących reguł).
- Zasady wychodzącego spamu są przetwarzane w kolejności, w jakiej są wyświetlane (pierwsze zasady mają wartość **Priorytet** 0). Domyślne zasady dotyczące spamu wychodzącego mają wartość priorytetu **Najniższa** i nie można jej zmienić.

1.  W portalu Microsoft 365 Defender przejdź do obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— ochrona przed spamem** w sekcji Zasady.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** **niestandardowych zasad spamu wychodzącego** z listy, klikając nazwę.

3. W górnej części wyświetlonego menu wysuwanego szczegółów zasad zobaczysz pozycję **Zwiększ priorytet** lub **Zmniejsz priorytet** na podstawie bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady dotyczące spamu wychodzącego o wartości **Priorytet** **0** mają dostępną tylko opcję **Zmniejsz priorytet** .
   - Zasady dotyczące spamu wychodzącego o najniższej wartości **Priorytet** (na przykład **3**) mają dostępną tylko opcję **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady dotyczące spamu wychodzącego, zasady między wartościami o najwyższym i najniższym priorytecie mają dostępne opcje **Zwiększanie priorytetu** i **Zmniejszanie priorytetu** .

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Zwiększ priorytet** lub ![Zmniejsz priorytet **ikona**](../../media/m365-cc-sc-decrease-icon.png) Zmniejsz priorytet, aby zmienić wartość **Priorytet**.

4. Po zakończeniu kliknij przycisk **Zamknij** w wysuwanym oknie szczegółów zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-outbound-spam-policies"></a>Usuwanie niestandardowych zasad spamu wychodzącego przy użyciu portalu Microsoft 365 Defender

W przypadku korzystania z portalu Microsoft 365 Defender w celu usunięcia niestandardowych zasad spamu wychodzącego zarówno reguła filtru spamu, jak i odpowiednie zasady filtru spamu są usuwane. Nie można usunąć domyślnych wychodzących zasad spamu.

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** **niestandardowych zasad spamu wychodzącego** z listy, klikając nazwę. W górnej części wyświetlonego menu wysuwanego szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Usuń ikonę](../../media/m365-cc-sc-delete-icon.png) zasad **Usuń zasady**.

3. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Konfigurowanie zasad spamu wychodzącego przy użyciu Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP

Zgodnie z wcześniejszym opisem zasady dotyczące spamu wychodzącego składają się z zasad filtru spamu wychodzącego i reguły filtru spamu wychodzącego.

W Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP widoczna jest różnica między zasadami filtru spamu wychodzącego a regułami filtru spamu wychodzącego. Zasady filtrowania spamu wychodzącego można zarządzać przy użyciu **\*poleceń cmdlet -HostedOutboundSpamFilterPolicy** i zarządzać regułami filtru spamu wychodzącego przy użyciu **\*poleceń cmdlet -HostedOutboundSpamFilterRule** .

- W programie PowerShell najpierw utworzysz zasady filtru spamu wychodzącego, a następnie utworzysz regułę filtru spamu wychodzącego, która identyfikuje zasady, do których ma zastosowanie reguła.
- W programie PowerShell można oddzielnie modyfikować ustawienia zasad filtru spamu wychodzącego i reguły filtru spamu wychodzącego.
- Po usunięciu wychodzących zasad filtru spamu z programu PowerShell odpowiednia reguła filtru spamu wychodzącego nie zostanie automatycznie usunięta i na odwrót.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Tworzenie wychodzących zasad spamu przy użyciu programu PowerShell

Tworzenie wychodzących zasad spamu w programie PowerShell to proces dwuetapowy:

1. Utwórz zasady filtru spamu wychodzącego.
2. Utwórz regułę filtru spamu wychodzącego określającą zasady filtru spamu wychodzącego, do których ma zastosowanie reguła.

   **Uwagi**:

   - Możesz utworzyć nową regułę filtru spamu wychodzącego i przypisać do niej istniejące, nieskojarzone zasady filtru spamu wychodzącego. Reguła filtru spamu wychodzącego nie może być skojarzona z więcej niż jedną zasadą filtru spamu wychodzącego.
   - W programie PowerShell można skonfigurować następujące ustawienia dla nowych zasad filtru spamu wychodzącego, które nie są dostępne w portalu Microsoft 365 Defender, dopóki nie zostaną utworzone zasady:
     - Utwórz nowe zasady jako wyłączone (_włączone_ `$false` w poleceniu cmdlet **New-HostedOutboundSpamFilterRule** ).
     - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) w poleceniu cmdlet **New-HostedOutboundSpamFilterRule**).
   - Nowe zasady filtru spamu wychodzącego utworzone w programie PowerShell nie są widoczne w portalu Microsoft 365 Defender, dopóki zasady nie zostaną przypisane do reguły filtru spamu wychodzącego.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>Krok 1. Tworzenie zasad filtru spamu wychodzącego przy użyciu programu PowerShell

Aby utworzyć zasady filtrowania spamu wychodzącego, użyj tej składni:

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

W tym przykładzie utworzono nowe zasady filtru spamu wychodzącego o nazwie Contoso Executives z następującymi ustawieniami:

- Limity szybkości adresatów są ograniczone do mniejszych wartości domyślnych. Aby uzyskać więcej informacji, zobacz [Wysyłanie limitów między opcjami Microsoft 365](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Po osiągnięciu jednego z limitów użytkownik nie może wysyłać komunikatów.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>Krok 2. Tworzenie reguły filtru spamu wychodzącego przy użyciu programu PowerShell

Aby utworzyć regułę filtru spamu wychodzącego, użyj tej składni:

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Sender filters> [<Sender filter exceptions>] [-Comments "<OptionalComments>"]
```

W tym przykładzie zostanie utworzona nowa reguła filtru spamu wychodzącego o nazwie Contoso Executives z następującymi ustawieniami:

- Zasady filtru spamu wychodzącego o nazwie Contoso Executives są skojarzone z regułą.
- Reguła ma zastosowanie do członków grupy o nazwie Contoso Executives Group.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Wyświetlanie wychodzących zasad filtrowania spamu przy użyciu programu PowerShell

Aby zwrócić listę podsumowań wszystkich zasad filtru spamu wychodzącego, uruchom następujące polecenie:

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Aby zwrócić szczegółowe informacje o określonych zasadach filtru spamu wychodzącego, użyj tej składni:

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Ten przykład zwraca wszystkie wartości właściwości dla zasad filtru spamu wychodzącego o nazwie Kierownictwo.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Wyświetlanie reguł filtru spamu wychodzącego przy użyciu programu PowerShell

Aby wyświetlić istniejące reguły filtru spamu wychodzącego, użyj następującej składni:

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Aby zwrócić listę podsumowań wszystkich reguł filtru spamu wychodzącego, uruchom następujące polecenie:

```PowerShell
Get-HostedOutboundSpamFilterRule
```

Aby filtrować listę według reguł włączonych lub wyłączonych, uruchom następujące polecenia:

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

Aby zwrócić szczegółowe informacje na temat określonej reguły filtru spamu wychodzącego, użyj tej składni:

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Ten przykład zwraca wszystkie wartości właściwości dla reguły filtru spamu wychodzącego o nazwie Contoso Executives.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Modyfikowanie zasad filtru spamu wychodzącego przy użyciu programu PowerShell

Te same ustawienia są dostępne podczas modyfikowania zasad filtrowania złośliwego oprogramowania w programie PowerShell, co w przypadku tworzenia zasad zgodnie z opisem w sekcji [Krok 1: Używanie programu PowerShell do tworzenia zasad filtru spamu wychodzącego we wcześniejszej](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) części tego artykułu.

> [!NOTE]
> Nie można zmienić nazwy wychodzących zasad filtru spamu (polecenie cmdlet **Set-HostedOutboundSpamFilterPolicy** nie ma parametru _Name_ ). Po zmianie nazwy wychodzących zasad spamu w portalu Microsoft 365 Defender zmieniasz tylko nazwę _reguły_ filtru spamu wychodzącego.

Aby zmodyfikować zasady filtru spamu wychodzącego, użyj tej składni:

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Modyfikowanie reguł filtru spamu wychodzącego przy użyciu programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły filtru spamu wychodzącego w programie PowerShell, jest parametr _Enabled_ , który umożliwia utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły filtru spamu wychodzącego, zobacz następną sekcję.

W przeciwnym razie podczas modyfikowania reguły filtru spamu wychodzącego w programie PowerShell nie są dostępne żadne dodatkowe ustawienia. Te same ustawienia są dostępne podczas tworzenia reguły zgodnie z opisem w sekcji [Krok 2: Tworzenie reguły filtru spamu wychodzącego przy użyciu programu PowerShell we wcześniejszej](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) części tego artykułu.

Aby zmodyfikować regułę filtru spamu wychodzącego, użyj tej składni:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Włączanie lub wyłączanie reguł filtru spamu wychodzącego przy użyciu programu PowerShell

Włączenie lub wyłączenie reguły filtru spamu wychodzącego w programie PowerShell włącza lub wyłącza całe zasady dotyczące spamu wychodzącego (reguła filtru spamu wychodzącego i przypisane zasady filtrowania spamu wychodzącego). Nie można włączyć ani wyłączyć domyślnych zasad spamu wychodzącego (są zawsze stosowane do wszystkich nadawców).

Aby włączyć lub wyłączyć regułę filtru spamu wychodzącego w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

Ten przykład wyłącza regułę filtru spamu wychodzącego o nazwie Dział marketingu.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

W tym przykładzie włączono tę samą regułę.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Enable-HostedOutboundSpamFilterRule](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) i [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Ustawianie priorytetu reguł filtru spamu wychodzącego przy użyciu programu PowerShell

Wartość o najwyższym priorytecie, którą można ustawić dla reguły, to 0. Najniższa wartość, którą można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć kaskadowy wpływ na inne reguły. Jeśli na przykład masz pięć reguł niestandardowych (priorytety od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły filtru spamu wychodzącego w programie PowerShell, użyj następującej składni:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie ustawiono priorytet reguły o nazwie Dział marketingu na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich priorytety są zwiększane o 1).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Uwagi**:

- Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj parametru _Priority_ w poleceniu cmdlet **New-HostedOutboundSpamFilterRule** .
- Domyślne zasady filtru spamu wychodzącego nie mają odpowiedniej reguły filtru spamu i zawsze mają niemodyfikowalną wartość priorytetu **Najniższa**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Usuwanie wychodzących zasad filtrowania spamu przy użyciu programu PowerShell

W przypadku usuwania wychodzących zasad filtrowania spamu przy użyciu programu PowerShell odpowiednia reguła filtru spamu wychodzącego nie zostanie usunięta.

Aby usunąć wychodzące zasady filtrowania spamu w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

W tym przykładzie usunięto wychodzące zasady filtrowania spamu o nazwie Dział marketingu.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Usuwanie reguł filtru spamu wychodzącego przy użyciu programu PowerShell

Jeśli używasz programu PowerShell do usunięcia reguły filtru spamu wychodzącego, odpowiednie zasady filtru spamu wychodzącego nie zostaną usunięte.

Aby usunąć regułę filtru spamu wychodzącego w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

W tym przykładzie usunięto regułę filtru spamu wychodzącego o nazwie Dział marketingu.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

[Usuwanie zablokowanych użytkowników z portalu Użytkownicy z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md)

[Pula dostarczania wysokiego ryzyka dla komunikatów wychodzących](high-risk-delivery-pool-for-outbound-messages.md)

[Ochrona przed spamem — często zadawane pytania](anti-spam-protection-faq.yml)

[Raport komunikatów przesyłanych automatycznie](mfi-auto-forwarded-messages-report.md)
