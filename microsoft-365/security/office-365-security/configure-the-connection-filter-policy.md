---
title: Konfigurowanie domyślnych zasad filtrowania połączeń
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
ms.assetid: 6ae78c12-7bbe-44fa-ab13-c3768387d0e3
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się, jak skonfigurować filtrowanie połączeń w Exchange Online Protection (EOP) w celu zezwalania na wiadomości e-mail z serwerów poczty e-mail lub blokowania ich.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0c09f445bf3d204f9e22d116dc9fda4c3fea9735
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974130"
---
# <a name="configure-connection-filtering"></a>Konfigurowanie filtrowania połączeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Jeśli jesteś klientem Microsoft 365 ze skrzynkami pocztowymi w Exchange Online lub klientem autonomicznym Exchange Online Protection (EOP) bez Exchange Online  skrzynki pocztowe, należy użyć filtrowania połączeń w EOP (w szczególności domyślne zasady filtrowania połączeń) do identyfikowania dobrych lub złych źródłowych serwerów poczty e-mail według ich adresów IP. Kluczowe składniki domyślnych zasad filtrowania połączeń to:

- **Lista dozwolonych** adresów IP: pomiń filtrowanie spamu dla wszystkich wiadomości przychodzących ze źródłowych serwerów poczty e-mail określonych przez adres IP lub zakres adresów IP. W przypadku scenariuszy, w których filtrowanie spamu może nadal występować w przypadku wiadomości z tych źródeł, zobacz [Scenariusze, w których komunikaty ze źródeł na liście dozwolonych adresów IP są nadal filtrowane](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) w dalszej części tego artykułu. Aby uzyskać więcej informacji na temat dopasowania listy dozwolonych adresów IP do ogólnej strategii bezpiecznych nadawców, zobacz [Tworzenie list bezpiecznych nadawców w ramach EOP](create-safe-sender-lists-in-office-365.md).

- **Lista zablokowanych** adresów IP: blokuj wszystkie przychodzące komunikaty ze źródłowych serwerów poczty e-mail określonych przez adres IP lub zakres adresów IP. Przychodzące wiadomości są odrzucane, nie są oznaczone jako spam i nie ma dodatkowego filtrowania. Aby uzyskać więcej informacji o tym, jak lista zablokowanych adresów IP powinna pasować do ogólnej strategii zablokowanych nadawców, zobacz [Tworzenie list nadawców blokowych w usłudze EOP](create-block-sender-lists-in-office-365.md).

- **Sejf listy**: *lista bezpiecznych* jest dynamiczną listą dozwolonych w centrum danych firmy Microsoft, która nie wymaga konfiguracji klienta. Firma Microsoft identyfikuje te zaufane źródła poczty e-mail z subskrypcji do różnych list innych firm. Można włączyć lub wyłączyć korzystanie z listy bezpiecznych; Nie można skonfigurować źródłowych serwerów poczty e-mail na liście bezpiecznych. Filtrowanie spamu jest pomijane w przypadku wiadomości przychodzących z serwerów poczty e-mail na liście bezpiecznych.

W tym artykule opisano sposób konfigurowania domyślnych zasad filtrowania połączeń w portalu Microsoft 365 Microsoft 365 Defender lub w programie PowerShell (Exchange Online programu PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online ; autonomiczny program PowerShell EOP dla organizacji bez Exchange Online skrzynek pocztowych). Aby uzyskać więcej informacji na temat sposobu, w jaki funkcja EOP używa filtrowania połączeń, jest częścią ogólnych ustawień ochrony przed spamem w organizacji, zobacz [Ochrona przed spamem](anti-spam-protection.md).

> [!NOTE]
> Lista dozwolonych adresów IP, lista bezpiecznych adresów IP i lista zablokowanych adresów IP to jedna z części ogólnej strategii zezwalania na pocztę e-mail lub blokowania jej w organizacji. Aby uzyskać więcej informacji, zobacz [Tworzenie list bezpiecznych nadawców](create-safe-sender-lists-in-office-365.md) i [Tworzenie zablokowanych list nadawców](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwórz portal Microsoft 365 Defender pod adresem <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

- Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell EOP, zobacz [Połączenie do Exchange Online Protection programu PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w **Exchange Online**:
  - Aby zmodyfikować domyślne zasady filtrowania połączeń, musisz być członkiem grup ról **Zarządzanie organizacją** lub **Administrator zabezpieczeń** .
  - Aby uzyskać dostęp tylko do odczytu do domyślnych zasad filtrowania połączeń, musisz być członkiem grup ról **Czytelnik globalny** lub **Czytelnik zabezpieczeń** .

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej roli Azure Active Directory w Centrum administracyjne platformy Microsoft 365 daje użytkownikom wymagane uprawnienia _i_ uprawnienia do innych funkcji w Microsoft 365. Aby uzyskać więcej informacji, zobacz: [Role administratora — informacje](../../admin/add-users/about-admin-roles.md).
  - Grupa ról **Zarządzanie organizacją tylko do wyświetlania** w [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) zapewnia również dostęp tylko do odczytu do tej funkcji.

- Aby znaleźć źródłowe adresy IP serwerów poczty e-mail (nadawców), na które chcesz zezwolić lub zablokować, możesz sprawdzić pole nagłówka łączącego się adresu IP (**CIP**) w nagłówku wiadomości. Aby wyświetlić nagłówek wiadomości w różnych klientach poczty e-mail, zobacz [Wyświetlanie nagłówków wiadomości internetowych w Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- Lista dozwolonych adresów IP ma pierwszeństwo przed listą zablokowanych adresów IP (adres na obu listach nie jest zablokowany).

- Lista dozwolonych adresów IP i lista zablokowanych adresów IP obsługują maksymalnie 1273 wpisy, gdzie wpis jest pojedynczym adresem IP, zakresem adresów IP lub adresem IP cidr (Classless InterDomain Routing).

## <a name="use-the-microsoft-365-defender-portal-to-modify-the-default-connection-filter-policy"></a>Modyfikowanie domyślnych zasad filtrowania połączeń za pomocą portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy pozycję **Zasady filtrowania połączeń (domyślne),** klikając nazwę zasad.

3. W wyświetlonym wysuwu szczegółów zasad skonfiguruj dowolne z następujących ustawień:

   - **Sekcja opisu** : kliknij pozycję **Edytuj nazwę i opis**. W wyświetlonym wysuwu **Edytuj nazwę i opis** wprowadź opcjonalny tekst opisowy w polu **Opis** .

     Po zakończeniu kliknij przycisk **Zapisz**.

   - **Sekcja filtrowania połączeń**: kliknij pozycję **Edytuj zasady filtru połączeń**. W wyświetlonym wysuwie skonfiguruj następujące ustawienia:

     - **Zawsze zezwalaj na komunikaty z następujących adresów IP lub zakresu adresów**: jest to lista dozwolonych adresów IP. Kliknij w polu, wprowadź wartość, a następnie naciśnij klawisz Enter lub wybierz pełną wartość wyświetlaną poniżej pola. Prawidłowe wartości są
       - Pojedynczy adres IP: na przykład 192.168.1.1.
       - Zakres adresów IP: na przykład 192.168.0.1-192.168.0.254.
       - Adres IP CIDR: na przykład 192.168.0.1/25. Prawidłowe wartości maski podsieci to od /24 do /32. Aby pominąć filtrowanie spamu dla /1 do /23, zobacz [Pomijanie filtrowania spamu dla adresu IP CIDR poza dostępnym zakresem w dalszej](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) części tego artykułu.

       Powtórz ten krok tyle razy, ile jest to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń ![Usuń ikonę.](../../media/m365-cc-sc-remove-selection-icon.png) obok wartości.

     Aby dodać adres IP lub zakres adresów, kliknij w polu i wpisz itclick **Dodaj** ![ikonę.](../../media/ITPro-EAC-AddIcon.png). Aby usunąć wpis, wybierz wpis w **obszarze Dozwolony adres IP**, a następnie kliknij pozycję **Usuń**![](../../media/scc-remove-icon.png). Po zakończeniu kliknij przycisk **Zapisz**.

   - **Zawsze blokuj komunikaty z następujących adresów IP lub zakresu adresów**: jest to lista zablokowanych adresów IP. Wprowadź pojedynczy adres IP, zakres adresów IP lub adres IP CIDR w polu, jak opisano wcześniej w ustawieniu **Zawsze zezwalaj na komunikaty z następujących adresów IP lub zakresu adresów** .

   - **Włącz listę bezpiecznych**: włącz lub wyłącz używanie listy bezpiecznych w celu zidentyfikowania znanych, dobrych nadawców, którzy pomiń filtrowanie spamu. Aby użyć listy bezpiecznych, zaznacz pole wyboru.

   Po zakończeniu kliknij przycisk **Zapisz**.

4. Po powrocie do wysuwanego szczegółów zasad kliknij przycisk **Zamknij**.

## <a name="use-the-microsoft-365-defender-portal-to-view-the-default-connection-filter-policy"></a>Wyświetlanie domyślnych zasad filtrowania połączeń za pomocą portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do  obszaru Zasady współpracy \> **& poczty e-mail** **& Zasady dotyczące** \> **zagrożeń** \> **— zasady ochrony przed spamem** w sekcji Zasady. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem** , użyj polecenia <https://security.microsoft.com/antispam>.

2. Na stronie **Zasady ochrony przed spamem** na liście zasad są wyświetlane następujące właściwości:

   - **Nazwa**: Ta wartość to **Zasady filtru połączenia (domyślne)** dla domyślnych zasad filtru połączeń.
   - **Stan**: Ta wartość jest **zawsze włączona** dla domyślnych zasad filtru połączeń.
   - **Priorytet**: ta wartość jest **najniższa** dla domyślnych zasad filtru połączeń.
   - **Typ**: ta wartość jest pusta dla domyślnych zasad filtru połączeń.

3. Po wybraniu domyślnych zasad filtrowania połączeń ustawienia zasad są wyświetlane w wysuwanym okienku.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Użyj Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP, aby zmodyfikować domyślne zasady filtrowania połączeń

Należy stosować następującą składnię:

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Uwagi**:

- Prawidłowe wartości adresu IP lub zakresu adresów to:
  - Pojedynczy adres IP: na przykład 192.168.1.1.
  - Zakres adresów IP: na przykład 192.168.0.1-192.168.0.254.
  - Adres IP CIDR: na przykład 192.168.0.1/25. Prawidłowe wartości maski sieci to od /24 do /32.
- Aby *zastąpić* wszystkie istniejące wpisy określonymi wartościami, użyj następującej składni: `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN`.
- Aby *dodać lub usunąć* adresy IP lub zakresy adresów bez wpływu na inne istniejące wpisy, użyj następującej składni: `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`.
- Aby opróżnić listę dozwolonych adresów IP lub listę zablokowanych adresów IP, użyj wartości `$null`.

W tym przykładzie skonfigurowano listę dozwolonych adresów IP i listę zablokowanych adresów IP z określonymi adresami IP i zakresami adresów.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

W tym przykładzie dodano i usunięto określone adresy IP i zakresy adresów z listy dozwolonych adresów IP.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-HostedConnectionFilterPolicy](/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Skąd wiadomo, że to działanie się powiodło?

Aby sprawdzić, czy domyślne zasady filtru połączeń zostały pomyślnie zmodyfikowane, wykonaj dowolne z następujących kroków:

- Na stronie **Ochrona przed spamem** w portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com/antispam>wybierz pozycję **Zasady filtru połączeń (domyślne)** z listy, klikając nazwę zasad i sprawdź ustawienia.

- W Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP uruchom następujące polecenie i sprawdź ustawienia:

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- Wyślij komunikat testowy z wpisu na liście dozwolonych adresów IP.

## <a name="additional-considerations-for-the-ip-allow-list"></a>Dodatkowe zagadnienia dotyczące listy dozwolonych adresów IP

Poniższe sekcje identyfikują dodatkowe elementy, które należy znać podczas konfigurowania listy dozwolonych adresów IP.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Pomijanie filtrowania spamu dla adresu IP CIDR spoza dostępnego zakresu

Zgodnie z opisem we wcześniejszej części tego artykułu można używać tylko adresu IP CIDR z maską sieci /24 do /32 na liście dozwolonych adresów IP. Aby pominąć filtrowanie spamu w wiadomościach ze źródłowych serwerów poczty e-mail w zakresie od /1 do /23, należy użyć Exchange reguł przepływu poczty (znanych również jako reguły transportu). Zalecamy jednak, aby w ogóle tego nie robić, ponieważ komunikaty zostaną zablokowane, jeśli adres IP z zakresu adresów IP /1 do /23 CIDR pojawi się na dowolnej z list blokowych firmy Microsoft lub innych firm.

Teraz, gdy w pełni znasz potencjalne problemy, możesz utworzyć regułę przepływu poczty z następującymi ustawieniami (co najmniej), aby upewnić się, że wiadomości z tych adresów IP pominą filtrowanie spamu:

- Warunek reguły: **Zastosuj tę regułę, jeśli** \> **adres IP nadawcy znajduje się w dowolnym z tych zakresów lub dokładnie pasuje** \> (wprowadź adres IP CIDR z maską sieci /1 do /23). \>
- Akcja **reguły: zmodyfikuj właściwości** \> wiadomości **Ustaw poziom ufności spamu (SCL)** \> **Pomiń filtrowanie spamu**.

Możesz przeprowadzić inspekcję reguły, przetestować regułę, aktywować regułę w określonym okresie i inne opcje. Zalecamy przetestowanie reguły przez pewien czas przed jej wymuszeniem. Aby uzyskać więcej informacji, zobacz [Zarządzanie regułami przepływu poczty w Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Pomijanie filtrowania spamu w domenach selektywnej poczty e-mail z tego samego źródła

Zazwyczaj dodanie adresu IP lub zakresu adresów do listy dozwolonych adresów IP oznacza, że ufasz wszystkim przychodzącym wiadomościom ze źródła wiadomości e-mail. Ale co zrobić, jeśli to źródło wysyła wiadomość e-mail z wielu domen i chcesz pominąć filtrowanie spamu dla niektórych z tych domen, ale nie innych? W tym celu nie można użyć samej listy dozwolonych adresów IP, ale można użyć listy dozwolonych adresów IP w połączeniu z regułą przepływu poczty.

Na przykład źródłowy serwer poczty e-mail 192.168.1.25 wysyła wiadomości e-mail z domen contoso.com, fabrikam.com i tailspintoys.com, ale chcesz pominąć filtrowanie spamu dla wiadomości od nadawców w fabrikam.com. W tym celu wykonaj następujące czynności:

1. Dodaj 192.168.1.25 do listy dozwolonych adresów IP.

2. Skonfiguruj regułę przepływu poczty przy użyciu następujących ustawień (co najmniej):
   - Warunek reguły: **zastosuj tę regułę, jeśli** \> **adres IP nadawcy znajduje się w dowolnym z tych zakresów lub dokładnie odpowiada** \> wartości 192.168.1.25 (ten sam adres IP lub zakres adresów dodany do listy dozwolonych adresów IP w poprzednim kroku). \>
   - Akcja **reguły: zmodyfikuj właściwości** \> wiadomości **Ustaw poziom ufności spamu (SCL)** \> **0**.
   - Wyjątek **reguły: domena nadawcy** \> **jest** \> fabrikam.com (tylko domena lub domeny, które chcesz pominąć filtrowanie spamu).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>Scenariusze, w których komunikaty ze źródeł na liście dozwolonych adresów IP są nadal filtrowane

Wiadomości z serwera poczty e-mail na liście dozwolonych adresów IP nadal podlegają filtrowaniu spamu w następujących scenariuszach:

- Adres IP na liście dozwolonych adresów IP jest również skonfigurowany w lokalnym łączniku przychodzącym opartym na adresach IP w *dowolnej* dzierżawie w Microsoft 365 (wywołajmy tę dzierżawę A) **oraz** w dzierżawie A i na serwerze EOP, który po raz pierwszy napotka komunikat, znajdują się w *tym samym* lesie usługi Active Directory w centrach danych firmy Microsoft. W tym scenariuszu protokół **IPV:CAL** *jest* [dodawany do nagłówków wiadomości antyspamowych](anti-spam-message-headers.md) wiadomości (wskazujących pomijane filtrowanie spamu), ale wiadomość nadal podlega filtrowaniu spamu.

- Dzierżawa zawierająca listę dozwolonych adresów IP i serwer EOP, który po raz pierwszy napotka komunikat, znajduje się w *różnych* lasach usługi Active Directory w centrach danych firmy Microsoft. W tym scenariuszu protokół **IPV:CAL** *nie jest* dodawany do nagłówków komunikatów, więc wiadomość nadal podlega filtrowaniu spamu.

Jeśli wystąpi któryś z tych scenariuszy, możesz utworzyć regułę przepływu poczty z następującymi ustawieniami (co najmniej), aby upewnić się, że wiadomości z problematycznych adresów IP pominą filtrowanie spamu:

- Warunek reguły: **zastosuj tę regułę, jeśli** \> **adres IP nadawcy znajduje się w dowolnym z tych zakresów lub jest dokładnie zgodny** \> (twój adres IP lub adresy). \>
- Akcja **reguły: zmodyfikuj właściwości** \> wiadomości **Ustaw poziom ufności spamu (SCL)** \> **Pomiń filtrowanie spamu**.

## <a name="new-to-microsoft-365"></a>Nowość w Microsoft 365?

****

![Ikona skrótu do usługi LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Nowość w Microsoft 365?** Odkryj bezpłatne kursy wideo dla **administratorów Microsoft 365 i specjalistów IT**, które zostały ci przywiezione przez Edukacja LinkedIn.
