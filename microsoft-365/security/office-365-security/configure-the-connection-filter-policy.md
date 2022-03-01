---
title: Konfigurowanie domyślnych zasad filtru połączenia
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
description: Administratorzy mogą dowiedzieć się, jak skonfigurować filtrowanie połączeń w u Exchange Online Protection (EOP), aby zezwalać na wiadomości e-mail z serwerów poczty e-mail lub blokować je.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2fbc481468fca8562c11e89b2e6c9dfa6361126a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032151"
---
# <a name="configure-connection-filtering"></a>Konfigurowanie filtrowania połączeń

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


Jeśli jesteś klientem usługi Microsoft 365 ze skrzynkami pocztowymi w u Exchange Online lub klientem usługi autonomicznej usługi Exchange Online Protection (EOP) bez Exchange Online  korzystasz z filtrowania połączeń w UOKI (a w szczególności domyślnych zasad filtrowania połączeń) do identyfikowania dobrych lub złych źródłowych serwerów poczty e-mail na pomocą ich adresów IP. Kluczowe składniki domyślnych zasad filtrowania połączenia to:

- **Lista zezwalań adresów IP**: Pomiń filtrowanie spamu dla wszystkich wiadomości przychodzących ze źródłowych serwerów poczty e-mail podanych według adresów IP lub zakresów adresów IP. W scenariuszach, w których filtrowanie spamu nadal występuje w przypadku wiadomości z tych źródeł, zobacz scenariusze, w których wiadomości ze źródeł na liście adresów [IP](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) są nadal filtrowane w dalszej części tego artykułu. Aby uzyskać więcej informacji na temat dopasowania listy adresów IP do ogólnej strategii dotyczącej bezpiecznych nadawców, zobacz Tworzenie list bezpiecznych [nadawców w uścisce EOP](create-safe-sender-lists-in-office-365.md).

- **Lista zablokowanych adresów IP**: Blokuj wszystkie wiadomości przychodzące ze źródłowych serwerów poczty e-mail, które określasz według adresu IP lub zakresu adresów IP. Wiadomości przychodzące są odrzucane, nie są oznaczane jako spam i nie zachodzi żadne dodatkowe filtrowanie. Aby uzyskać więcej informacji na temat tego, jak lista zablokowanych adresów IP powinna być dopasowana do strategii ogólnej listy zablokowanych nadawców, zobacz Tworzenie list zablokowanych [nadawców w uścisce usługi EOP](create-block-sender-lists-in-office-365.md).

- **Sejf listy***: Lista* bezpiecznych adresów to dynamiczna lista zezwalań w centrum danych firmy Microsoft, która nie wymaga konfiguracji klienta. Firma Microsoft identyfikuje te zaufane źródła poczty e-mail od subskrypcji do różnych list innych firm. Włączenie lub wyłączenie korzystania z listy bezpiecznych adresów. na liście bezpiecznych adresów nie można skonfigurować źródłowych serwerów poczty e-mail. Filtrowanie spamu jest pomijane na wiadomościach przychodzących z serwerów poczty e-mail na liście bezpiecznych adresów.

W tym artykule opisano sposób konfigurowania domyślnych zasad filtrowania połączeń w portalu usługi Microsoft 365 Microsoft 365 Defender lub w programie PowerShell (Exchange Online PowerShell dla organizacji Microsoft 365 ze skrzynkami pocztowymi w Exchange Online ; autonomiczny program PowerShell usługi EOP dla organizacji bez Exchange Online skrzynek pocztowych). Aby uzyskać więcej informacji na temat korzystania przez usługę EOP z filtrowania połączeń, należy do ogólnych ustawień ochrony przed spamem w organizacji, zobacz Ochrona [przed spamem](anti-spam-protection.md).

> [!NOTE]
> Lista adresów IP, lista bezpiecznych adresów IP i lista zablokowanych adresów IP to jedna z części ogólnej strategii zezwalania na pocztę e-mail w organizacji lub blokowania jej. Aby uzyskać więcej informacji, zobacz [Tworzenie list bezpiecznych nadawców](create-safe-sender-lists-in-office-365.md) i [Tworzenie list zablokowanych nadawców](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Otwierasz portal Microsoft 365 Defender w witrynie <https://security.microsoft.com>. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

- Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Aby nawiązać połączenie z autonomicznym programem PowerShell usługi EOP, [Połączenie się z Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie **Exchange Online** mieć przypisane uprawnienia:
  - Aby zmodyfikować domyślne zasady filtru połączenia, musisz być członkiem grup ról Zarządzanie **organizacją** lub **Administrator** zabezpieczeń.
  - Aby mieć dostęp tylko do odczytu do domyślnych zasad filtru połączenia, musisz być członkiem grup ról  Czytnik globalny lub **Czytnik** zabezpieczeń.

  Aby uzyskać więcej informacji, zobacz [Uprawnienia w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Uwagi**:

  - Dodanie użytkowników do odpowiedniej Azure Active Directory w aplikacji centrum administracyjne platformy Microsoft 365 zapewnia użytkownikom wymagane uprawnienia i uprawnienia do innych funkcji w  aplikacji Microsoft 365. Aby uzyskać więcej informacji, zobacz [Informacje o rolach administratorów](../../admin/add-users/about-admin-roles.md).
  - Grupa **ról Zarządzanie organizacją tylko do** odczytu w [programie Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) również zapewnia dostęp tylko do odczytu tej funkcji.

- Aby znaleźć źródłowe adresy IP serwerów poczty e-mail (nadawców), na które chcesz zezwolić lub które chcesz zablokować, możesz sprawdzić pole nagłówka adresu IP (**CIP**, Connecting IP) w nagłówku wiadomości. Aby wyświetlić nagłówek wiadomości w różnych klientach poczty e-mail, zobacz [Wyświetlanie nagłówków wiadomości internetowych w programie Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- Lista adresów IP ma pierwszeństwo przed listą zablokowanych adresów IP (adres na obu listach nie jest zablokowany).

- Lista adresów IP i lista zablokowanych adresów IP obsługują maksymalnie 1273 wpisy, gdzie wpis to jeden adres IP, zakres adresów IP lub adres IP CiDR (Classless InterDomain Routing).

## <a name="use-the-microsoft-365-defender-portal-to-modify-the-default-connection-filter-policy"></a>Modyfikowanie domyślnych zasad filtru połączenia za pomocą portalu Microsoft 365 Defender połączeń

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** wybierz z listy pozycję Zasady filtru połączenia **(** domyślne), klikając nazwę zasad.

3. W wyświetlonym wysuwanych szczegółach zasad skonfiguruj dowolne z następujących ustawień:

   - **Sekcja Opis** : Kliknij **pozycję Edytuj nazwę i opis**. W **wyświetlonym wysuwanych informacjach** Edytuj nazwę i opis wprowadź opcjonalny tekst opisowy w **polu** Opis.

     Po zakończeniu kliknij przycisk **Zapisz**.

   - **Sekcja Filtrowanie połączenia**: Kliknij **pozycję Edytuj zasady filtru połączenia**. W wyświetlonym wysuwu skonfiguruj następujące ustawienia:

     - **Zawsze zezwalaj na wiadomości z następujących adresów IP lub z następujących zakresów** adresów IP: Jest to lista adresów IP Allow (Zezwalaj na adresy IP). Kliknij w polu, wprowadź wartość, a następnie naciśnij klawisz Enter lub wybierz pełną wartość wyświetlaną poniżej tego pola. Prawidłowe wartości to
       - Pojedynczy adres IP: Na przykład 192.168.1.1.
       - Zakres adresów IP: Na przykład: 192.168.0.1-192.168.0.254.
       - IP CIDR: Na przykład 192.168.0.1/25. Prawidłowe wartości maski podsieci to od /24 do /32. Aby pominąć filtrowanie spamu dla /1 do /23, zobacz sekcję Pomijanie filtrowania [spamu dla adresu IP CIDR](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) poza dostępnym zakresem w dalszej części tego artykułu.

       Powtarzaj ten krok tyle razy, ile to konieczne. Aby usunąć istniejącą wartość, kliknij przycisk usuń. ![Ikona usuń.](../../media/m365-cc-sc-remove-selection-icon.png) obok tej wartości.

     Aby dodać adres IP lub zakres adresów IP, kliknij w polu i wpisz gokliknij polecenie **Dodaj** ![ikonę Dodaj](../../media/ITPro-EAC-AddIcon.png). Aby usunąć wpis, zaznacz go w pozycji Dozwolony **adres IP**, a następnie kliknij pozycję **Usuń**![](../../media/scc-remove-icon.png). Po zakończeniu kliknij przycisk **Zapisz**.

   - **Zawsze blokuj wiadomości z następujących adresów IP lub z następujących zakresów** adresów IP: Jest to lista zablokowanych adresów IP. Wprowadź jeden adres IP, zakres adresów IP lub adres IP CIDR w polu zgodnie z wcześniejszym opisem w polu Zawsze zezwalaj na wiadomości z następujących adresów **IP lub z następującego ustawienia zakresu** adresów.

   - **Włącz listę bezpiecznych adresów**: Włącz lub wyłącz korzystanie z listy bezpiecznych adresów w celu zidentyfikowania znanych, dobrych nadawców, dla których filtrowanie spamu zostanie pominięte. Aby użyć listy bezpiecznych adresów, zaznacz to pole wyboru.

   Po zakończeniu kliknij przycisk **Zapisz**.

4. Na wysuwanych szczegółach zasad kliknij pozycję **Zamknij**.

## <a name="use-the-microsoft-365-defender-portal-to-view-the-default-connection-filter-policy"></a>Wyświetlanie domyślnych zasad filtru połączenia za pomocą portalu Microsoft 365 Defender połączenia

1. W portalu Microsoft 365 Defender <https://security.microsoft.com>pod adresem przejdź  \> do sekcji Zasady &-mail & **zasady** \>  \> zagrożeń dotyczące ochrony przed **spamem** **w sekcji Zasady**. Aby przejść bezpośrednio do strony **Zasady ochrony przed spamem**, użyj .<https://security.microsoft.com/antispam>

2. Na stronie **Zasady ochrony przed spamem** na liście zasad są wyświetlane następujące właściwości:

   - **Nazwa**: Ta wartość to **Domyślne zasady filtrowania** połączenia dla domyślnych zasad filtru połączenia.
   - **Stan**: ta wartość jest **zawsze włączona** dla domyślnych zasad filtru połączenia.
   - **Priority** (Priorytet): ta wartość jest **najniższa** w przypadku domyślnych zasad filtrowania połączeń.
   - **Typ**: Ta wartość jest pusta dla domyślnych zasad filtru połączenia.

3. Po wybraniu domyślnych zasad filtru połączenia ustawienia zasad są wyświetlane w wysuwanych menu.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Modyfikowanie Exchange Online filtrowania połączenia za pomocą programu PowerShell lub autonomicznego programu PowerShell usługi EOP

Należy stosować następującą składnię:

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Uwagi**:

- Prawidłowe wartości adresów IP lub zakresów adresów IP to:
  - Pojedynczy adres IP: Na przykład 192.168.1.1.
  - Zakres adresów IP: Na przykład: 192.168.0.1-192.168.0.254.
  - IP CIDR: Na przykład 192.168.0.1/25. Prawidłowe wartości maski sieci to od /24 do /32.
- Aby *zastąpić* wszelkie istniejące wpisy wartościami, użyj następującej składni: `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN`.
- Aby *dodać lub usunąć adresy* IP lub zakresy adresów bez wpływu na inne istniejące wpisy, użyj następującej składni: `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`.
- Aby opróżnić listę adresów IP lub listę zablokowanych adresów IP, użyj wartości `$null`.

W tym przykładzie skonfigurowano listę adresów IP oraz listę zablokowanych adresów IP z określonymi adresami IP i zakresami adresów IP.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

W tym przykładzie do listy adresów IP są dodano i usuwane określone adresy IP i zakresy adresów IP.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-HostedConnectionFilterPolicy](/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Skąd wiadomo, że to działanie się powiodło?

Aby sprawdzić, czy domyślne zasady filtrowania połączeń zostały pomyślnie zmodyfikowane, wykonaj dowolną z następujących czynności:

- Na stronie **Ochrona przed spamem** <https://security.microsoft.com/antispam>w portalu Microsoft 365 Defender wybierz z listy pozycję Zasady filtrowania połączenia **(** Domyślne), klikając nazwę zasad, a następnie zweryfikuj ustawienia.

- W Exchange Online PowerShell lub autonomiczny program PowerShell usługi EOP uruchom następujące polecenie i sprawdź ustawienia:

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- Wysyłanie wiadomości testowej z wpisu na liście adresów IP ze zezwalaniem.

## <a name="additional-considerations-for-the-ip-allow-list"></a>Dodatkowe zagadnienia dotyczące listy zezwalań adresów IP

W poniższych sekcjach przedstawiono dodatkowe elementy, o których należy wiedzieć podczas konfigurowania listy adresów IP ze zezwalaniem.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Pomiń filtrowanie spamu dla adresu IP CIDR spoza dostępnego zakresu

Jak opisano wcześniej w tym artykule, na liście adresów IP można używać tylko adresu IP CIDR z maską sieci /24 do /32. Aby pominąć filtrowanie spamu w wiadomościach ze źródłowych serwerów poczty e-mail w zakresie od /1 do /23, musisz użyć reguł przepływu poczty e-mail Exchange (nazywanych również regułami transportu). Zalecamy jednak, aby nie robić tego, jeśli to możliwe, ponieważ wiadomości zostaną zablokowane, jeśli adres IP z zakresu adresów IP od /1 do /23 CIDR znajduje się na dowolnej zastrzeżonej lub innej liście zablokowanych list firmy Microsoft.

Teraz, gdy w pełni wiesz o potencjalnych problemach, możesz utworzyć regułę przepływu poczty e-mail z następującymi ustawieniami (co najmniej), aby mieć pewność, że wiadomości z tych adresów IP pomijają filtrowanie spamu:

- Warunek **reguły:** \>  \> zastosuj tę regułę, jeśli adres **IP** \> nadawcy znajduje się w dowolnym z tych zakresów lub jest dokładnie taki sam (wprowadź swój adres IP CIDR z maską sieci /1 do /23).
- Akcja reguły: **Zmodyfikuj właściwości wiadomości** \> Ustaw poziom ufności spamu **(SCL) Pomijanie** \> **filtrowania spamu**.

Można sprawdzić regułę, przetestować ją, aktywować w określonym czasie i wybrać inne opcje. Zalecamy przetestowanie reguły przez określony czas, zanim ją wyegzekwuje. Aby uzyskać więcej informacji, zobacz [Zarządzanie regułami przepływu poczty e-mail w Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Pomiń filtrowanie spamu w wybranych domenach poczty e-mail z tego samego źródła

Zazwyczaj dodanie adresu IP lub zakresu adresów IP do listy adresów IP allow list oznacza, że wszystkie przychodzące wiadomości z tego źródła poczty e-mail są zaufane. Ale co zrobić, jeśli to źródło wysyła wiadomości e-mail z wielu domen i chcesz pominąć filtrowanie spamu dla niektórych z tych domen, ale nie inne? W tym celu nie można używać samej listy adresów IP, ale można używać listy adresów IP w połączeniu z regułą przepływu poczty e-mail.

Na przykład źródłowy serwer poczty e-mail 192.168.1.25 wysyła wiadomości e-mail z domen contoso.com, fabrikam.com i tailspintoys.com, ale chcesz pominąć filtrowanie spamu tylko w przypadku wiadomości od nadawców z usługi fabrikam.com. W tym celu wykonaj następujące czynności:

1. Dodaj 192.168.1.25 do listy adresów IP allow list.

2. Skonfiguruj regułę przepływu poczty e-mail przy użyciu co najmniej następujących ustawień:
   - Warunek **reguły:** \>  \> zastosuj tę regułę, jeśli adres **IP** \> nadawcy znajduje się w dowolnym z tych zakresów lub jest dokładnie taki sam jak 192.168.1.25 (ten sam adres IP lub zakres adresów IP, który został dodany do listy adresów IP w poprzednim kroku).
   - Akcja reguły: **Zmodyfikuj właściwości wiadomości** \> **Ustaw poziom ufności spamu (SCL)** \> **0**.
   - Wyjątek reguły: **domena** \> **nadawcy jest fabrikam.com** \> (tylko domena lub domeny, których filtrowanie spamu chcesz pominąć).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>Scenariusze, w których wiadomości ze źródeł na liście zezwalań adresów IP są nadal filtrowane

Wiadomości z serwera poczty e-mail na liście zezwalań adresów IP nadal podlegają filtrowaniu spamu w następujących scenariuszach:

- Adres IP na liście zezwalań adresów IP jest również skonfigurowany w lokalnym łączniku ruchu przychodzącego opartego na adresie IP w  dowolnej dzierżawie w usłudze Microsoft 365 (niech to nazwa Dzierżawa **A) oraz** Dzierżawa A i serwer EOP, który najpierw napotka komunikat, że oba występują w tym samym lesie *usługi Active Directory* w centrach danych firmy Microsoft. W tym scenariuszu protokół **IPV:CAL**  jest dodawany do nagłówków wiadomości przed spamem [(co](anti-spam-message-headers.md) oznacza, że wiadomość została pominięta w filtrowaniu spamu), ale wiadomość nadal podlega filtrowaniu spamu.

- Dzierżawa zawierająca listę adresów IP i serwer usługi EOP, który po raz pierwszy napotka komunikat, zdarza się, że znajdują się w różnych lasach *usługi Active Directory* w centrach danych firmy Microsoft. W tym scenariuszu **protokół IPV:CAL**  nie jest dodawany do nagłówków wiadomości, więc wiadomość nadal podlega filtrowaniu spamu.

Jeśli napotkasz jeden z tych scenariuszy, możesz utworzyć regułę przepływu poczty e-mail z następującymi ustawieniami (co najmniej), aby upewnić się, że wiadomości z problematycznych adresów IP pomijają filtrowanie spamu:

- Warunek reguły: **Zastosuj tę regułę, jeśli** \>  \> adres IP nadawcy znajduje się w dowolnym z tych zakresów lub jest **dokładnie** \> taki sam (Twój adres IP lub adresy IP).
- Akcja reguły: **Zmodyfikuj właściwości wiadomości** \> Ustaw poziom ufności spamu **(SCL) Pomijanie** \> **filtrowania spamu**.

## <a name="new-to-microsoft-365"></a>Nie chcesz Microsoft 365?

****

![Ikona skrótu do usługi LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Nie chcesz Microsoft 365?** Zapoznaj się z bezpłatnymi **kursami wideo Microsoft 365 administratorami i informatykami**, które są dostępne w serwisie LinkedIn Edukacja.
