---
title: Konfigurowanie filtrowania spamu ruchu wychodzącego
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
description: Administratorzy mogą dowiedzieć się, jak wyświetlać, tworzyć, modyfikować i usuwać zasady spamu wychodzącego w u Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7f635eb17d458ca707f7a18d3eb1f7fe655bd2b9
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033031"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>Konfigurowanie filtrowania spamu ruchu wychodzącego w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w organizacjach usługi Exchange Online lub autonomicznej usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online wychodzące wiadomości e-mail wysyłane za pośrednictwem usługi EOP są automatycznie sprawdzane pod kątem spamu i nietypowej aktywności wysyłania.

Spam wychodzący od użytkownika w organizacji zazwyczaj oznacza naruszone konto. Podejrzane wiadomości wychodzące są oznaczane jako spam (niezależnie od poziomu ufności spamu lub poziomu ufności filtru spamu) i są kierowane przez pulę dostarczania wysokiego ryzyka w celu ochrony reputacji usługi (Microsoft 365 oznacza to, że źródłowe serwery poczty [e-mail](high-risk-delivery-pool-for-outbound-messages.md) nie są wyłączone z list zablokowanych adresów IP). Administratorzy są automatycznie powiadamiani o podejrzanych działaniach poczty e-mail wychodzących i zablokowani użytkownicy za pośrednictwem [zasad alertów](../../compliance/alert-policies.md).

EOP korzysta z zasad spamu wychodzącego w ramach ogólnej ochrony organizacji przed spamem. Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem](anti-spam-protection.md).

Administratorzy mogą wyświetlać, edytować i konfigurować (ale nie usuwać) domyślne zasady spamu ruchu wychodzącego. Aby uzyskać bardziej szczegółowe informacje, możesz również tworzyć niestandardowe zasady dotyczące spamu ruchu wychodzącego, które dotyczą konkretnych użytkowników, grup lub domen w organizacji. Zasady niestandardowe zawsze mają priorytet nad zasadami domyślnymi, ale priorytet (kolejność działania) zasad niestandardowych można zmienić.

Zasady dotyczące spamu wychodzącego można skonfigurować w portalu usługi Microsoft 365 Microsoft 365 Defender lub w programie Power Microsoft 365 Shell (Exchange Online PowerShell dla organizacji z skrzynkami pocztowymi w programie Exchange Online; autonomiczny program PowerShell usługi EOP dla organizacje bez Exchange Online skrzynek pocztowych).

Podstawowe elementy zasad ochrony przed spamem ruchu wychodzącego w u programie EOP to:

- **Zasady filtrowania spamu** ruchu wychodzącego: Określa akcje dla werdyktów filtrowania spamu ruchu wychodzącego i opcje powiadomień.
- **Reguła filtrowania spamu ruchu wychodzącego**: Określa priorytet i filtry adresatów (do których mają zastosowanie zasady) dla zasad filtrowania spamu ruchu wychodzącego.

Różnica między tymi dwoma elementami nie jest widoczna, gdy zarządzasz zasadami spamu wychodzącego w portalu poczty Microsoft 365 Defender sieci:

- Gdy tworzysz zasady, w rzeczywistości tworzysz regułę filtru spamu ruchu wychodzącego i skojarzone z nią zasady filtru spamu wychodzącego jednocześnie, używając tej samej nazwy dla obu zasad.
- Podczas modyfikowania zasad ustawienia dotyczące nazwy, priorytetu, włączonego lub wyłączonego oraz filtrów adresatów modyfikują regułę filtrowania spamu ruchu wychodzącego. Wszystkie inne ustawienia modyfikują skojarzone zasady filtrowania spamu ruchu wychodzącego.
- Gdy usuniesz zasady, reguła filtrowania spamu ruchu wychodzącego i skojarzone z nią zasady filtrowania spamu wychodzącego zostaną usunięte.

W Exchange Online PowerShell lub autonomicznym programie PowerShell usługi EOP zasady i reguła są zarządzane osobno. Aby uzyskać więcej informacji, zobacz sekcję Używanie programu [PowerShell Exchange Online lub autonomicznego programu PowerShell usługi EOP](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) do konfigurowania zasad spamu ruchu wychodzącego w dalszej części tego artykułu.

Każda organizacja ma wbudowane zasady dotyczące spamu wychodzącego o nazwie Domyślne, które mają następujące właściwości:

- Zasady te są stosowane do wszystkich adresatów w organizacji, nawet jeśli z tą zasadami nie jest skojarzona reguła filtrowania spamu ruchu wychodzącego (filtry adresatów).
- Zasady mają niestandardową wartość priorytetu **Najniższa wartość,** których nie można modyfikować (zasady są zawsze stosowane jako ostatnie). Wszystkie zasady niestandardowe, które tworzysz, zawsze mają wyższy priorytet niż zasady o nazwie Domyślne.
- Zasady są zasadami domyślnymi (właściwość **IsDefault** `True`ma wartość ) i nie można usunąć zasad domyślnych.

Aby zwiększyć skuteczność filtrowania spamu ruchu wychodzącego, możesz utworzyć niestandardowe zasady dotyczące spamu wychodzącego z bardziej rygorystycznymi ustawieniami, które są stosowane do konkretnych użytkowników lub grup użytkowników.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby dodawać, modyfikować i usuwać zasady dotyczące spamu wychodzącego, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do zasad spamu wychodzącego, musisz być członkiem grup  ról Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Aby uzyskać informacje o naszych zalecanych ustawieniach dotyczących zasad spamu wychodzącego, zobacz Ustawienia zasad filtru spamu ruchu wychodzącego [eOP](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings).

- Domyślne zasady [alertów](../../compliance/alert-policies.md) o nazwie Przekroczono limit wysyłania wiadomości e-mail **, Wykryto** podejrzane  wzorce wysyłania wiadomości e-mail i Użytkownik ograniczony do wysyłania wiadomości e-mail już wysyłał powiadomienia e-mail do członków grupy **Administratorzy** **dzierżawcy (** administratorzy globalni) o nietypowej aktywności poczty e-mail wychodzącej i zablokowanych użytkownikach z powodu spamu wychodzącego. Aby uzyskać więcej informacji, zobacz [Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Zalecamy używanie tych zasad alertów zamiast opcji powiadomień w zasadach spamu wychodzących.

## <a name="use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies"></a>Tworzenie zasad spamu wychodzącego za pomocą portalu poczty Microsoft 365 Defender-mail

Utworzenie niestandardowych zasad spamu wychodzącego w portalu poczty Microsoft 365 Defender powoduje utworzenie reguły filtru spamu i skojarzonych z nią zasad filtru spamu, używając jednocześnie tej samej nazwy dla obu zasad.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** kliknij ikonę ![Utwórz.](../../media/m365-cc-sc-create-icon.png) **Utwórz zasady** , a następnie wybierz **z** listy rozwijanej pozycję Wychodzące.

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

   - **Wyklucz** tych użytkowników, grup i domen: Aby dodać wyjątki dla adresatów wewnętrznych, których zasady dotyczą (wyjątków, których dotyczą zasady), zaznacz tę opcję i skonfiguruj wyjątki. Ustawienia i zachowanie są dokładnie takie, jak warunki.

   Po zakończeniu kliknij przycisk **Dalej**.

5. Na **otwartej stronie** Ustawienia ochrony skonfiguruj następujące ustawienia:
   - **Limity wiadomości**: Ustawienia w tej sekcji konfigurują limity wychodzących wiadomości e-mail z **Exchange Online pocztowych:**
     - **Ustawianie limitu wiadomości zewnętrznych**: Maksymalna liczba adresatów zewnętrznych na godzinę.
     - **Ustawianie wewnętrznego limitu wiadomości**: Maksymalna liczba adresatów wewnętrznych na godzinę.
     - **Ustaw dzienny limit wiadomości**: maksymalna całkowita liczba adresatów dziennie.

     Prawidłowa wartość to od 0 do 10000. Wartość domyślna to 0, co oznacza, że są używane ustawienia domyślne usługi. Aby uzyskać więcej informacji, zobacz [Limity wysyłania](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

    Wprowadź wartość w polu lub użyj strzałek zwiększania/zmniejszania w polu.

   - **Ograniczenie dotyczące użytkowników,** którzy osiągają limit wiadomości: Wybierz akcję z listy rozwijanej, jeśli przekroczono limity w sekcji Ustawienia  ochrony.

     W przypadku wszystkich akcji adresaci zablokowani w ustawieniach użytkownika z ograniczeniem wysyłania alertów e-mail (**a** teraz nadmiarowi powiadom tych użytkowników i grupy, jeśli nadawca zostanie zablokowany z powodu ustawienia spamu ruchu wychodzącego w dalszej części tej strony) otrzymują powiadomienia e-mail.

     - **Ograniczenie wysyłania poczty przez użytkownika do następnego** dnia: Jest to wartość domyślna. Powiadomienia e-mail zostaną wysłane i użytkownik nie będzie mógł wysłać więcej wiadomości do następnego dnia (w zależności od czasu UTC). Administrator nie może zastąpić tego bloku.
       - Zasady alertów o nazwie **Użytkownik ograniczony do** wysyłania wiadomości e-mail powiadomią administratorów (za pośrednictwem poczty e-mail i na stronie Alerty o **zdarzeniach & wyświetl** \> **alerty** ).
       - Powiadamiani są również adresaci zablokowani w przypadku zablokowania nadawcy z powodu wysyłania **spamu** wychodzącego w zasadach.
       - W zależności od czasu UTC użytkownik nie będzie mógł wysłać więcej wiadomości do następnego dnia. Administrator nie może zastąpić tego bloku.
     - Ograniczanie możliwości wysyłania poczty e-mail do użytkownika: Powiadomienia e-mail są wysyłane, <https://security.microsoft.com/restrictedusers> użytkownik jest dodawany do pozycji Użytkownicy z ograniczeniami w portalu usługi Microsoft 365 Defender i nie może wysyłać wiadomości  **e-mail**, dopóki nie zostanie usunięty z grupy Użytkownicy z ograniczeniami przez administratora. Gdy administrator usunie użytkownika z listy, nie zostanie ponownie ograniczony w tym dniu. Aby uzyskać instrukcje, [zobacz Usuwanie użytkownika z portalu Użytkownicy z ograniczeniami po wysłaniu wiadomości e-mail ze spamem](removing-user-from-restricted-users-portal-after-spam.md).
     - **Brak akcji, tylko alert**: Powiadomienia e-mail są wysyłane.

   - **Reguły przesyłania dalej**. Użyj ustawień w tej sekcji, aby sterować automatycznym przesyłaniem dalej poczty e-mail przez Exchange Online **do** nadawców zewnętrznych. Aby uzyskać więcej informacji, zobacz [Sterowanie automatycznym zewnętrznym przesyłaniem dalej poczty e-mail w Microsoft 365](external-email-forwarding.md).

     > [!NOTE]
     > Gdy automatyczne przesyłanie dalej jest wyłączone, adresat otrzyma raport o niedostarczeniu (nazywany również wiadomością o niedostarczeniu lub wiadomością zwrotną), jeśli nadawcy zewnętrzni wysyłają wiadomości e-mail do skrzynki pocztowej, która jest przesyłana dalej. Jeśli wiadomość jest wysyłana przez nadawcę wewnętrznego, a metodą przesyłania dalej jest przesyłanie dalej skrzynki [pocztowej (nazywane](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) też przesyłaniem dalej _SMTP_), nadawca wewnętrzny otrzyma wiadomość o niedostarczeniu. Nadawca wewnętrzny nie otrzyma wiadomości o niedostarczeniu, jeśli przesyłanie miało miejsce na skutek reguły skrzynki odbiorczej.

     Wybierz jedną z następujących akcji z listy rozwijanej **Automatic forwarding rules** (Reguły automatycznego przesyłania dalej):

     - **Automatyczne — sterowane przez system**: Umożliwia filtrowanie spamu wychodzącego do sterowania automatycznym zewnętrznym przesyłaniem dalej wiadomości e-mail. Jest to wartość domyślna.
     - **Wł**.: Automatyczne zewnętrzne przesyłanie dalej poczty e-mail nie jest wyłączone przez zasady.
     - **Wyłączone**: Zasady wyłączają wszystkie automatyczne zewnętrzne przesyłanie dalej wiadomości e-mail.

   - **Powiadomienia**: Użyj ustawień w tej sekcji, aby skonfigurować dodatkowych adresatów, którzy powinni otrzymywać kopie i powiadomienia o podejrzanych wychodzących wiadomościach e-mail:

     - **Wyślij kopię** podejrzanych połączeń wychodzących, które przekraczają te limity, do tych użytkowników i grup: To ustawienie dodaje określonych adresatów do pola UDW podejrzanych wiadomości wychodzących.

       > [!NOTE]
       > To ustawienie działa tylko w domyślnych zasadach spamu wychodzącego. Nie działa on w niestandardowych, niestandardowych zasadach spamu wychodzących, które tworzysz.

       Aby włączyć to ustawienie, zaznacz to pole wyboru. W wyświetlonym polu kliknij w polu, wprowadź prawidłowy adres e-mail, a następnie naciśnij klawisz Enter lub wybierz wyświetlaną wartość poniżej tego pola.

       Powtarzaj ten krok tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

   - **Powiadamianie tych użytkowników i grup w przypadku zablokowania nadawcy z powodu wysyłania spamu wychodzącego**

     > [!IMPORTANT]
     >
     > - To ustawienie jest wy przestarzałe z zasad spamu wychodzącego.
     >
     > - Domyślne zasady [alertów](../../compliance/alert-policies.md) o  nazwie Użytkownik z ograniczeniem wysyłania wiadomości e-mail już wysyłają powiadomienia e-mail do członków grupy **TenantAdmins** **(** administratorzy globalni), gdy użytkownicy zostaną zablokowani ze względu na przekroczenie limitów w sekcji Limity **adresatów.** **Zdecydowanie zalecamy korzystanie z zasad alertów** zamiast tego ustawienia w zasadach spamu ruchu wychodzącego do powiadamiania administratorów i innych użytkowników. Aby uzyskać instrukcje, [zobacz Weryfikowanie ustawień alertów dla użytkowników z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

   Po zakończeniu kliknij przycisk **Dalej**.

6. Na **wyświetlonej** stronie Recenzja przejrzyj ustawienia. Możesz wybrać pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Możesz też kliknąć przycisk **Wstecz** lub wybrać określoną stronę w kreatorze.

   Po zakończeniu kliknij pozycję **Utwórz**.

7. Na wyświetlonej stronie potwierdzenia kliknij pozycję **Gotowe**.

## <a name="use-the-microsoft-365-defender-portal-to-view-outbound-spam-policies"></a>Wyświetlanie zasad spamu wychodzącego za pomocą portalu poczty Microsoft 365 Defender-mail

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** odszukaj jedną z następujących wartości:
   - Wartość **Typ to** Niestandardowe **zasady dotyczące spamu wychodzącego**
   - Wartość **Nazwa to** Zasady **wychodzące przed spamem (domyślne)**

   Na liście zasad ochrony przed spamem są wyświetlane następujące właściwości:

   - **Nazwa**
   - **Stan**
   - **Priority (Priorytet)**
   - **Type**

3. Po wybraniu zasad spamu wychodzącego przez kliknięcie nazwy ustawienia zasad są wyświetlane w wysuwanych menu.

## <a name="use-the-microsoft-365-defender-portal-to-modify-outbound-spam-policies"></a>Modyfikowanie zasad spamu wychodzącego za pomocą portalu poczty Microsoft 365 Defender-mail

1. W portalu  Microsoft 365 Defender przejdź \> do sekcji Zasady & **e-mail** **& zasady** \>  \> zagrożeń zapobiegające spamowi w **sekcji** Zasady.

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy zasady dotyczące spamu ruchu wychodzącego, klikając nazwę:
   - Zasady niestandardowe, których wartość w kolumnie **Typ** to Niestandardowe zasady **dotyczące spamu wychodzącego**.
   - Zasady domyślne o **nazwie Zasady wychodzące przed spamem (domyślne)**

3. W wyświetlonym wysuwanych szczegółach zasad wybierz pozycję **Edytuj** w każdej sekcji, aby zmodyfikować ustawienia w sekcji. Aby uzyskać więcej informacji o ustawieniach, zobacz poprzednią sekcję Tworzenie zasad spamu wychodzącego Microsoft 365 Defender portalu poczty wychodzącej w tym artykule.[](#use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies)

   W przypadku domyślnych zasad spamu wychodzących  sekcja Zastosowane do nie jest dostępna (zasady dotyczą wszystkich użytkowników) i nie można zmienić ich nazw.

Aby włączyć lub wyłączyć zasady, ustawić kolejność priorytetu zasad lub skonfigurować powiadomienia użytkowników końcowych, zobacz poniższe sekcje.

### <a name="enable-or-disable-custom-outbound-spam-policies"></a>Włączanie lub wyłączanie niestandardowych zasad spamu ruchu wychodzącego

Nie można wyłączyć domyślnych zasad spamu wychodzącego.

1. W portalu  Microsoft 365 Defender przejdź \> do sekcji Zasady & **e-mail** **& zasady** \>  \> zagrożeń zapobiegające spamowi w **sekcji** Zasady.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** w pozycji Niestandardowe zasady **dotyczące spamu** wychodzącego z listy, klikając jej nazwę.

3. U góry wyświetlonego wysuwana informacja o zasadach zostanie wyświetlona jedna z następujących wartości:
   - **Zasady wyłączone**: Aby włączyć zasady, kliknij ikonę ![Włącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Włącz** .
   - **Zasady wł**.: Aby wyłączyć zasady, kliknij ikonę ![Wyłącz.](../../media/m365-cc-sc-turn-on-off-icon.png) **Wyłącz**.

4. W wyświetlonym oknie dialogowym potwierdzenia kliknij **pozycję Włącz** lub **Wyłącz**.

5. Kliknij **przycisk Zamknij** w wysuwanych szczegółach zasad.

Na stronie głównej zasad wartość **Status** zasad będzie wł **.** lub **wyłączona**.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Ustawianie priorytetu niestandardowych zasad spamu wychodzącego

Domyślnie zasady spamu wychodzącego mają priorytet na podstawie kolejności ich utworzenia (nowsze zasady mają niższy priorytet niż starsze zasady). Numer niższego priorytetu oznacza wyższy priorytet zasad (0 jest najwyższy), a zasady są przetwarzane w kolejności priorytetu (zasady o wyższym priorytecie są przetwarzane przed zasadami o niższym priorytecie). Dwa zasady nie mogą mieć tego samego priorytetu i przetwarzanie zasad zostanie zatrzymane po zastosowaniu pierwszej zasady.

Aby zmienić priorytet zasad, kliknij pozycję Zwiększ priorytet lub  Zmniejsz priorytet we  właściwościach zasad (nie można bezpośrednio zmodyfikować numeru Priorytet w portalu Microsoft 365 Defender). Zmiana priorytetu zasad jest sensowna tylko w przypadku wielu zasad.

 **Uwagi**:

- W portalu Microsoft 365 Defender wiadomości wychodzących priorytet zasad ochrony przed spamem można zmienić tylko po ich utworzeniu. W programie PowerShell możesz zastąpić domyślny priorytet podczas tworzenia reguły filtru spamu (która może mieć wpływ na priorytet istniejących reguł).
- Wychodzące zasady dotyczące spamu są przetwarzane w kolejności ich wyświetlania (pierwsza zasada ma **wartość Priorytet** 0). Domyślne zasady dotyczące spamu wychodzącego mają wartość priorytetu Najniższa **wartość i nie** można jej zmienić.

1. W portalu  Microsoft 365 Defender przejdź \> do sekcji Zasady & **e-mail** **& zasady** \>  \> zagrożeń zapobiegające spamowi w **sekcji** Zasady.

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** z listy Niestandardowe zasady **dotyczące spamu** wychodzącego, klikając nazwę.

3. U góry wyświetlonego wysuwu szczegółów zasad zobaczysz komunikat Zwiększ priorytet lub Zmniejsz  priorytet na podstawie  bieżącej wartości priorytetu i liczby zasad niestandardowych:
   - Zasady spamu ruchu wychodzącego z **wartością Priorytet** **0** mają dostęp tylko do **opcji Zmniejsz priorytet** .
   - Zasady spamu wychodzącego o najmniejszej wartości **Priorytet** (na przykład **3**) mają dostęp tylko opcję **Zwiększ priorytet** .
   - Jeśli masz co najmniej trzy zasady dotyczące spamu wychodzącego, zasady dotyczące najwyższego i najniższego priorytetu mają  zarówno opcje Zwiększ priorytet, jak **i Zmniejsz priorytet**.

   Kliknij ikonę ![Zwiększ priorytet.](../../media/m365-cc-sc-increase-icon.png) **Ikona Zwiększ priorytet** lub ![Zmniejsz priorytet](../../media/m365-cc-sc-decrease-icon.png) **Zmniejszanie priorytetu** w celu zmiany **wartości Priorytet** .

4. Po zakończeniu kliknij pozycję **Zamknij w wysuwanych** szczegółach zasad.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-outbound-spam-policies"></a>Usuwanie niestandardowych zasad spamu wychodzącego za pomocą portalu poczty Microsoft 365 Defender-mail

Gdy korzystasz z portalu poczty Microsoft 365 Defender usunąć niestandardowe zasady spamu wychodzącego, reguła filtru spamu i odpowiadające im zasady filtru spamu są usuwane. Nie można usunąć domyślnych zasad spamu wychodzącego.

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **ustawień ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wybierz zasady z **wartością Typ** w pozycji Niestandardowe zasady **dotyczące spamu** wychodzącego z listy, klikając jej nazwę. W górnej części wyświetlonego wysuwania szczegółów zasad kliknij ikonę ![Więcej akcji.](../../media/m365-cc-sc-more-actions-icon.png) **Więcej akcji** \> ![Ikona usuwania zasad](../../media/m365-cc-sc-delete-icon.png) **Usuń zasady**.

3. W wyświetlonym oknie dialogowym potwierdzenia kliknij przycisk **Tak**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Konfigurowanie zasad Exchange Online spamu za pomocą programu PowerShell lub autonomicznego programu EOP PowerShell

Jak opisano wcześniej, zasady spamu wychodzącego obejmują zasady filtrowania spamu ruchu wychodzącego i regułę filtrowania spamu ruchu wychodzącego.

W Exchange Online Programu PowerShell lub autonomicznego programu PowerShell usługi EOP różnica między zasadami filtrowania spamu ruchu wychodzącego a regułami filtrowania spamu wychodzącego jest widoczna. Zasady filtrowania spamu ruchu wychodzącego można zarządzać przy użyciu polecenia cmdlet **-HostedOutboundSpamFilterPolicy, a także zarządzać regułami filtrowania spamu ruchu wychodzącego przy użyciu polecenia cmdlet -HostedOutboundSpamFilterRule.\*** **\***

- W programie PowerShell najpierw tworzysz zasady filtrowania spamu ruchu wychodzącego, a następnie tworzysz regułę filtrowania spamu ruchu wychodzącego identyfikującą zasady, których ta reguła dotyczy.
- W programie PowerShell można oddzielnie zmodyfikować ustawienia w zasadach filtrowania spamu ruchu wychodzącego i w  regułach filtru spamu wychodzącego.
- Po usunięciu zasad filtrowania spamu ruchu wychodzącego z programu PowerShell odpowiednia reguła filtrowania spamu ruchu wychodzącego nie jest automatycznie usuwana i odwrotnie.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Tworzenie zasad spamu ruchu wychodzącego za pomocą programu PowerShell

Tworzenie zasad spamu ruchu wychodzącego w programie PowerShell jest procesem dwuetapowym:

1. Utwórz zasady filtrowania spamu ruchu wychodzącego.
2. Utwórz regułę filtrowania spamu ruchu wychodzącego określającą zasady filtrowania spamu ruchu wychodzącego, których ta reguła dotyczy.

   **Uwagi**:

   - Możesz utworzyć nową regułę filtrowania spamu ruchu wychodzącego i przypisać do tej reguły istniejące, nieskojarzone zasady filtru spamu wychodzącego. Reguła filtrowania spamu ruchu wychodzącego nie może być skojarzona z więcej niż jedną zasadami filtrowania spamu ruchu wychodzącego.
   - W programie PowerShell możesz skonfigurować następujące ustawienia nowych zasad filtrowania spamu ruchu wychodzącego, które są niedostępne w portalu poczty Microsoft 365 Defender, dopóki nie zostaną one skonfigurowane:
     - Utwórz nowe zasady jako wyłączone (_włączone dla_ `$false` polecenia cmdlet **New-HostedOutboundSpamFilterRule** ).
     - Ustaw priorytet zasad podczas tworzenia (_Priorytet__\<Number\>_) dla polecenia cmdlet **New-HostedOutboundSpamFilterRule**.
   - Nowe zasady filtrowania spamu ruchu wychodzącego, które tworzysz w programie PowerShell, nie są widoczne w portalu usługi Microsoft 365 Defender, dopóki nie przypiszesz ich do reguły filtru spamu ruchu wychodzącego.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>Krok 1. Tworzenie zasad filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell

Aby utworzyć zasady filtrowania spamu ruchu wychodzącego, użyj tej składni:

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

W tym przykładzie są wiązane nowe zasady filtrowania spamu wychodzącego o nazwie  Kierownictwo Contoso z następującymi ustawieniami:

- Limity stawek dla adresatów są ograniczone do mniejszych wartości domyślnych. Aby uzyskać więcej informacji, zobacz [Wysyłanie limitów za Microsoft 365 opcje](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Po osiągnięciu jednego z limitów nie można wysyłać wiadomości od użytkownika.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>Krok 2. Tworzenie reguły filtru spamu ruchu wychodzącego przy użyciu programu PowerShell

Aby utworzyć regułę filtrowania spamu ruchu wychodzącego, użyj tej składni:

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

W tym przykładzie jest ana nowa reguła filtrowania spamu ruchu wychodzącego o nazwie  Kierownictwo Contoso z tymi ustawieniami:

- Z regułą są skojarzone zasady filtrowania spamu ruchu wychodzącego o nazwie  Kierownictwo Contoso.
- Reguła dotyczy członków grupy o nazwie Grupa kadry kierowniczej Contoso.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Wyświetlanie zasad filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell

Aby zwrócić listę podsumowania wszystkich zasad filtrowania spamu ruchu wychodzącego, uruchom to polecenie:

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Aby zwrócić szczegółowe informacje dotyczące określonych zasad filtrowania spamu ruchu wychodzącego, użyj tej składni:

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

W tym przykładzie zwracane są wszystkie wartości właściwości zasad filtrowania spamu ruchu wychodzącego o nazwie  Kierownictwo.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Wyświetlanie reguł filtru spamu ruchu wychodzącego za pomocą programu PowerShell

Aby wyświetlić istniejące reguły filtrowania spamu ruchu wychodzącego, użyj następującej składni:

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Aby zwrócić listę podsumowania wszystkich reguł filtru spamu wychodzącego, uruchom to polecenie:

```PowerShell
Get-HostedOutboundSpamFilterRule
```

Aby przefiltrować listę według włączonych lub wyłączonych reguł, uruchom następujące polecenia:

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

Aby zwrócić szczegółowe informacje na temat określonej reguły filtru spamu ruchu wychodzącego, użyj tej składni:

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

W tym przykładzie zwracane są wszystkie wartości właściwości reguły filtru spamu ruchu wychodzącego o nazwie  Kierownictwo Contoso.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Modyfikowanie zasad filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell

Te same ustawienia są dostępne po zmodyfikowaniu zasad filtrowania złośliwego oprogramowania w programie PowerShell co podczas tworzenia zasad zgodnie z opisem w Kroku [1: Tworzenie](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) zasad filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell we wcześniejszej części tego artykułu.

> [!NOTE]
> Nie można zmienić nazwy zasad filtrowania spamu ruchu wychodzącego (polecenie cmdlet **Set-HostedOutboundSpamFilterPolicy** nie ma _parametru Name_ ). Zmiana nazwy zasad spamu ruchu wychodzącego w portalu poczty Microsoft 365 Defender umożliwia jedynie zmianę nazwy reguły filtru spamu ruchu _wychodzącego_.

Aby zmodyfikować zasady filtrowania spamu ruchu wychodzącego, użyj tej składni:

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Modyfikowanie reguł filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell

Jedynym ustawieniem, które nie jest dostępne podczas modyfikowania reguły filtrowania spamu ruchu wychodzącego w programie PowerShell, jest parametr _Enabled_ umożliwiający utworzenie wyłączonej reguły. Aby włączyć lub wyłączyć istniejące reguły filtrowania spamu ruchu wychodzącego, zobacz następną sekcję.

W przeciwnym razie podczas modyfikowania reguły filtru spamu ruchu wychodzącego w programie PowerShell nie są dostępne żadne dodatkowe ustawienia. Podczas tworzenia reguły są dostępne te same ustawienia, co opisano w sekcji Krok 2. Tworzenie reguły filtrowania spamu ruchu wychodzącego za pomocą programu [PowerShell](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) we wcześniejszej części tego artykułu.

Aby zmodyfikować regułę filtrowania spamu ruchu wychodzącego, użyj tej składni:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Włączanie lub wyłączanie reguł filtru spamu ruchu wychodzącego za pomocą programu PowerShell

Włączenie lub wyłączenie reguły filtrowania spamu ruchu wychodzącego w programie PowerShell włącza lub wyłącza całą zasadę spamu wychodzącego (regułę filtrowania spamu ruchu wychodzącego i przypisane zasady filtrowania spamu ruchu wychodzącego). Nie można włączyć ani wyłączyć domyślnych zasad spamu wychodzącego (są one zawsze stosowane do wszystkich adresatów).

Aby włączyć lub wyłączyć regułę filtrowania spamu ruchu wychodzącego w programie PowerShell, użyj tej składni:

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

W tym przykładzie wyłączyliśmy regułę filtrowania spamu ruchu wychodzącego o nazwie Dział marketingu.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

W tym przykładzie ta sama reguła jest włączana.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Enable-HostedOutboundSpamFilterRule](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) i [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Ustawianie priorytetu reguł filtru spamu ruchu wychodzącego za pomocą programu PowerShell

Wartość najwyższego priorytetu, jaki można ustawić dla reguły, wynosi 0. Najniższa wartość, która można ustawić, zależy od liczby reguł. Jeśli na przykład masz pięć reguł, możesz użyć wartości priorytetu od 0 do 4. Zmiana priorytetu istniejącej reguły może mieć wpływ na inne reguły kaskadowe. Jeśli na przykład masz pięć reguł niestandardowych (priorytet od 0 do 4) i zmienisz priorytet reguły na 2, istniejąca reguła o priorytecie 2 zostanie zmieniona na priorytet 3, a reguła o priorytecie 3 zostanie zmieniona na priorytet 4.

Aby ustawić priorytet reguły filtru spamu ruchu wychodzącego w programie PowerShell, użyj następującej składni:

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

W tym przykładzie dla reguły o nazwie Dział marketingu jest ustawiany priorytet na 2. Wszystkie istniejące reguły o priorytecie mniejszym lub równym 2 są zmniejszane o 1 (ich numery priorytetów są zwiększane o 1).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Uwagi**:

- Aby ustawić priorytet nowej reguły podczas jej tworzenia, użyj zamiast tego _parametru Priority_ polecenia cmdlet **New-HostedOutboundSpamFilterRule** .
- Domyślne zasady filtrowania spamu ruchu wychodzącego nie mają odpowiadającej jej reguły filtru spamu i zawsze mają niemodyfikowalny priorytet wartości **Najniżej**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Usuwanie zasad filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell

Gdy usuwasz zasady filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell, odpowiednia reguła filtru spamu ruchu wychodzącego nie jest usuwana.

Aby usunąć zasady filtrowania spamu ruchu wychodzącego w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

W tym przykładzie zasady filtrowania spamu ruchu wychodzącego o nazwie Dział marketingu są usuwane.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Usuwanie reguł filtru spamu ruchu wychodzącego za pomocą programu PowerShell

Gdy usuwasz regułę filtrowania spamu ruchu wychodzącego za pomocą programu PowerShell, odpowiadające im zasady filtrowania spamu wychodzącego nie są usuwane.

Aby usunąć regułę filtrowania spamu ruchu wychodzącego w programie PowerShell, użyj tej składni:

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

W tym przykładzie jest usuwana reguła filtrowania spamu ruchu wychodzącego o nazwie Dział marketingu.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Aby uzyskać więcej informacji

[Usuwanie zablokowanych użytkowników z portalu Użytkownicy z ograniczeniami](removing-user-from-restricted-users-portal-after-spam.md)

[Pula dostarczania wiadomości wysokiego ryzyka dla wiadomości wychodzących](high-risk-delivery-pool-for-outbound-messages.md)

[Ochrona przed spamem — często zadawane pytania](anti-spam-protection-faq.yml)

[Raport Wiadomości automatycznie przekazywane dalej](mfi-auto-forwarded-messages-report.md)
