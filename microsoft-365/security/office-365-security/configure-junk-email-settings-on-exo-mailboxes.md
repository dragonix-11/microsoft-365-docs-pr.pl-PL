---
title: Konfigurowanie ustawień wiadomości-śmieci w Exchange Online pocztowych
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się, jak skonfigurować ustawienia wiadomości-śmieci w Exchange Online pocztowych. Wiele z tych ustawień jest dostępnych dla użytkowników w Outlook lub Outlook w sieci Web.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9e2db8fc6c88e3945081d3b2800aa5ea9cd57a11
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682466"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Konfigurowanie ustawień wiadomości-śmieci w Exchange Online pocztowych

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365, w których skrzynki pocztowe znajdują się Exchange Online, ustawienia ochrony przed spamem w organizacji są kontrolowane przez Exchange Online Protection (EOP). Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem w uciekaniu poczty eOP](anti-spam-protection.md).

Istnieją jednak również określone ustawienia ochrony przed spamem, które administratorzy mogą skonfigurować dla poszczególnych skrzynek pocztowych w Exchange Online:

> [!NOTE]
> Teraz program EOP używa własnego agenta dostarczania przepływu poczty e-mail do rozsyłania wiadomości do folderu Wiadomości-śmieci zamiast używać reguły wiadomości-śmieci. Parametr _Enabled_ w **poleceniach cmdlet Set-MailboxJunkEmailConfiguration** nie ma już wpływu na przepływ poczty e-mail. Program EOP rozsyła wiadomości na podstawie akcji ustawionych w zasadach ochrony przed spamem. Lista zablokowanych Sejf i lista zablokowanych nadawców użytkownika nadal będzie działać jak zwykle.

- Przenoszenie wiadomości do folderu Wiadomości-śmieci na podstawie zasad ochrony przed spamem: Jeśli zasady ochrony przed spamem są skonfigurowane z akcją Przenieś wiadomość do folderu Wiadomości-śmieci w celu werdyktu filtrowania spamu, wiadomość jest przenoszony do folderu **Wiadomości-śmieci** po dostarczaniu wiadomości do skrzynki pocztowej. Aby uzyskać więcej informacji na temat werdyktów filtrowania spamu w zasadach ochrony przed spamem, zobacz Konfigurowanie zasad ochrony [przed spamem w u usługi EOP](configure-your-spam-filter-policies.md). Podobnie, jeśli funkcja automatycznego przeczyszczania wiadomości (ZAP) o zerowej godzinie ustali, że dostarczona wiadomość jest spamem lub wiadomością wyłudzaną, zostanie ona przeniesiona do folderu Wiadomości-śmieci w celu przeniesienia wiadomości do folderu Wiadomości-śmieci w czynnościach werdyktowych filtrowania spamu. Aby uzyskać więcej informacji na temat funkcji ZAP, zobacz [Automatyczne przeczyszczanie zerowej godziny (ZAP) w programie Exchange Online](zero-hour-auto-purge.md).

- **Ustawienia** wiadomości-śmieci, które użytkownicy konfigurują dla siebie w programie Outlook lub Outlook w sieci Web: Lista bezpiecznych adresów to lista Sejf nadawców, lista adresatów programu Sejf i lista Zablokowani nadawcy w każdej skrzynce pocztowej. Pozycje na tych listach określają, czy wiadomość zostanie przeniesiona do skrzynki odbiorczej, czy do folderu Wiadomości-śmieci. Użytkownicy mogą skonfigurować kolekcję listy bezpiecznych adresów dla swoich skrzynek pocztowych w Outlook lub Outlook w sieci Web (dawniej znany jako Outlook Web App). Administratorzy mogą skonfigurować kolekcję listy bezpiecznych adresów w skrzynce pocztowej dowolnego użytkownika.

Usługa EOP może przenosić wiadomości do folderu Wiadomości-śmieci na podstawie akcji werdyktu filtrowania spamu Przenieś wiadomości do folderu Wiadomości-śmieci lub listy zablokowanych nadawców w skrzynce pocztowej i zapobiega dostarczaniu wiadomości do folderu Wiadomości-śmieci (na podstawie listy nadawców usługi Sejf w skrzynce pocztowej).

Administratorzy mogą za pomocą programu Exchange Online PowerShell konfigurować wpisy w zbiorze listy bezpiecznych adresów w skrzynkach pocztowych (na liście Sejf nadawców, na liście Sejf adresatów i na liście zablokowanych nadawców).

> [!NOTE]
> Wiadomości od nadawców dodanych przez użytkowników do własnych list Sejf nadawców pomijają filtrowanie zawartości w ramach EOP (wartość SCL wynosi -1). Aby uniemożliwić użytkownikom dodawanie wpisów do listy Sejf nadawców w programie Outlook, użyj programu zasady grupy zgodnie z informacjami w sekcji Informacje o ustawieniach wiadomości-śmieci w programie [Outlook](#about-junk-email-settings-in-outlook) w dalszej części tego artykułu. Filtrowanie zasad, filtrowanie zawartości i program Defender Office 365 będą nadal stosowane do wiadomości.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Procedury z tego Exchange Online można wykonać tylko za pomocą programu PowerShell. Aby nawiązać połączenie Exchange Online PowerShell, zobacz Połączenie[, Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury z tego artykułu Exchange Online w programie Exchange Online mieć przypisane uprawnienia. W szczególności potrzebna jest rola  Adresaci poczty (która jest domyślnie przypisana do grup ról Zarządzanie **organizacją, Zarządzanie** adresatami i Niestandardowy adresaci poczty) lub Opcje użytkownika  (która jest domyślnie przypisana do grup ról Zarządzanie  organizacją i Pomoc  technicznej). Aby dodać użytkowników do grup ról w Exchange Online, zobacz [Modyfikowanie grup ról w Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups). Użytkownicy z uprawnieniami domyślnymi mogą wykonać te same procedury we własnej skrzynce pocztowej, o ile mają dostęp do programu [Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

- W środowiskach hybrydowych, w których program EOP chroni lokalne Exchange pocztowe, musisz skonfigurować reguły przepływu poczty e-mail (nazywane także regułami transportu) w lokalnym programie Exchange. Te reguły przepływu poczty tłumaczą werdykt filtrowania spamu usługi EOP, dzięki czemu reguła wiadomości-śmieci w skrzynce pocztowej może przenieść wiadomość do folderu Wiadomości-śmieci. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usługi EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- Sejf dla udostępnionych skrzynek pocztowych nie są domyślnie synchronizowane z usługami Azure AD i EOP.

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Konfigurowanie Exchange Online listy bezpiecznych adresów w skrzynce pocztowej za pomocą programu PowerShell

Zbiór listy bezpiecznych adresów w skrzynce pocztowej zawiera listę Sejf nadawców, listę Sejf adresatów oraz listę zablokowanych nadawców. Domyślnie użytkownicy mogą skonfigurować kolekcję listy bezpiecznych adresów we własnej skrzynce pocztowej w Outlook lub Outlook w sieci Web. Administratorzy mogą używać odpowiednich parametrów w poleceniach **cmdlet Set-MailboxJunkEmailConfiguration** , aby skonfigurować kolekcję listy bezpiecznych adresów w skrzynce pocztowej użytkownika. Te parametry opisano w poniższej tabeli.

|Parametr na Set-MailboxJunkEmailConfiguration|Outlook w sieci Web ustawienia|
|---|---|
|_BlockedSendersAndDomains_|**Przenoszenie wiadomości e-mail od tych nadawców lub domen do folderu Wiadomości-śmieci**|
|_ContactsTrusted_|**Ufaj wiadomościom e-mail od moich kontaktów**|
|_TrustedListsOnly_|**Ufaj tylko wiadomościom e-mail z adresów na Sejf nadawców i domen oraz na listach Sejf adresowych**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Nie przekieruj wiadomości e-mail od tych nadawców do folderu Wiadomości-śmieci**|

<sup>\*</sup>**Uwagi**:

- W **Exchange Online domeny na** liście Sejf nadawców lub _parametru TrustedSendersAndDomains_ nie są rozpoznawane, dlatego używaj tylko adresów e-mail. W autonomicznej usłudze EOP z synchronizacją katalogów wpisy domen nie są domyślnie synchronizowane, ale możesz włączyć synchronizację dla domen. Aby uzyskać więcej informacji, [zobacz KB3019657](https://support.microsoft.com/help/3019657).
- Nie można bezpośrednio zmodyfikować listy adresatów usługi Sejf przy użyciu polecenia cmdlet **Set-MailboxJunkEmailConfiguration** (parametr _TrustedRecipientsAndDomains_ nie działa). Zmodyfikuj listę Sejf nadawców, a te zmiany zostaną zsynchronizowane z listą Sejf adresatów.

Aby skonfigurować kolekcję listy bezpiecznych adresów w skrzynce pocztowej, użyj następującej składni:

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Aby wprowadzić wiele wartości i zastąpić wszelkie istniejące wpisy parametrów _BlockedSendersAndDomains_ i _TrustedSendersAndDomains_ , użyj następującej składni: `"<Value1>","<Value2>"...`. Aby dodać lub usunąć jedną lub więcej wartości bez wpływu na inne istniejące wpisy, użyj następującej składni: `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

W tym przykładzie konfigurowane są następujące ustawienia kolekcji listy bezpiecznych adresów w skrzynce pocztowej Ori Epsteina:

- Dodaj wartość shopping@fabrikam.com do listy Zablokowani nadawcy.
- Usuń wartość chris@fourthcoffee.com z Sejf nadawców i listy Sejf adresatów.
- Konfiguruje kontakty w folderze Kontakty tak, aby były traktowane jako zaufani nadawcy.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

W tym przykładzie domena contoso.com z listy Zablokowani nadawcy we wszystkich skrzynkach pocztowych użytkowników w organizacji.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Jeśli użytkownik nigdy nie otworzył swojej skrzynki pocztowej, po uruchomieniu poprzednich poleceń może zostać wyświetlony komunikat o błędzie. Aby pominąć ten błąd w przypadku operacji zbiorczych, dodaj `-ErrorAction SilentlyContinue` do polecenia **Set-MailboxJunkEmailConfiguration** .
> - Filtr Outlook-śmieci ma dodatkowe ustawienia zbierania listy bezpiecznych adresów (na przykład: Automatycznie dodaj osoby, do których wysyłam wiadomość e-mail Sejf **listę nadawców**). Aby uzyskać więcej informacji, zobacz Używanie filtrów [wiadomości-śmieci do kontrolowania, które wiadomości są wyświetlane](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Skąd wiadomo, że to działanie się powiodło?

Aby sprawdzić, czy zbiór listy bezpiecznych adresów został pomyślnie skonfigurowany w skrzynce pocztowej, użyj dowolnej z następujących procedur:

- Zamień _\<MailboxIdentity\>_ na nazwę, alias lub adres e-mail skrzynki pocztowej i uruchom następujące polecenie w celu zweryfikowania wartości właściwości:

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Jeśli lista wartości jest zbyt długa, użyj tej składni:

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>Informacje o ustawieniach wiadomości-śmieci w aplikacji Outlook

Aby włączyć, wyłączyć i skonfigurować ustawienia filtru wiadomości-śmieci po stronie klienta dostępne w programie Outlook, użyj zasady grupy. Aby uzyskać więcej informacji, zobacz Pliki szablonów administracyjnych (ADMX/ADML) i Narzędzie do dostosowywania wiadomości Office dla systemów [Aplikacje Microsoft 365 dla przedsiębiorstw, Office 2019 i Office 2016](https://www.microsoft.com/download/details.aspx?id=49030) oraz Jak wdrożyć ustawienia wiadomości-śmieci, takie jak lista nadawców w programie Sejf, za pomocą programu [zasady grupy ](https://support.microsoft.com/help/2252421).

Gdy filtr wiadomości-śmieci usługi Outlook  \>  \> jest ustawiony na wartość domyślną Bez automatycznego filtrowania w opcjach domowych **wiadomości-śmieci** \> **, program** Outlook nie próbuje klasyfikować wiadomości jako spam, ale nadal używa zbioru bezpiecznych adresów (listy nadawców usługi Sejf, Sejf   listę adresatów i listę zablokowanych nadawców), aby przenieść wiadomości do folderu Wiadomości-śmieci po dostarczeniu. Aby uzyskać więcej informacji o tych ustawieniach, zobacz [Omówienie filtru wiadomości-śmieci](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

Jeśli filtr wiadomości Outlook wiadomości-śmieci ma ustawioną wartość  Niski lub **Wysoki, filtr** wiadomości-śmieci usługi Outlook używa własnej technologii filtru SmartScreen do identyfikowania i przenoszenia spamu do folderu Wiadomości-śmieci. Ta klasyfikacja spamu jest oddzielona od poziomu ufności spamu określanego przez firmę EOP. W rzeczywistości program Outlook filtr SCL usługi EOP (o ile usługa EOP nie oznaczyła wiadomości w celu pominięcia filtrowania spamu) i używa własnych kryteriów w celu określenia, czy wiadomość jest spamem. Oczywiście może się okazać, że werdykt spamu z Outlook e-mail może być taki sam. Aby uzyskać więcej informacji o tych ustawieniach, [zobacz Zmienianie poziomu ochrony w filtrze wiadomości-śmieci](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b).

> [!NOTE]
> W listopadzie 2016 r. firma Microsoft zaprzestała tworzenia aktualizacji definicji spamu dla filtrów SmartScreen w aplikacjach Exchange i Outlook. Istniejące definicje spamu w filtrze SmartScreen zostały pozostawione, ale ich skuteczność prawdopodobnie będzie się pogarszać z czasem. Aby uzyskać więcej informacji, [zobacz Zaniechanie obsługi filtru SmartScreen w Outlook i Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

Dlatego Outlook wiadomości-śmieci może używać zbioru bezpiecznych adresów i klasyfikacji spamu skrzynki pocztowej do przenoszenia wiadomości do folderu Wiadomości-śmieci.

Outlook i Outlook w sieci Web obsługuje kolekcję listy bezpiecznych adresów. Kolekcja listy bezpiecznych adresów jest zapisywana w skrzynce Exchange Online pocztowej, więc zmiany w kolekcji listy bezpiecznych adresów w programie Outlook są wyświetlane w programie Outlook w sieci Web i odwrotnie.

## <a name="limits-for-junk-email-settings"></a>Limity dotyczące ustawień wiadomości-śmieci

Zbiór bezpiecznych adresów (lista Sejf nadawców, lista Sejf adresatów i lista zablokowanych nadawców) przechowywany w skrzynce pocztowej użytkownika jest również synchronizowany z usługą EOP. Dzięki synchronizacji katalogów zbiór listy bezpiecznych adresów jest synchronizowany z usługą Azure AD.

- Zbiór listy bezpiecznych adresów w skrzynce pocztowej użytkownika ma ograniczenie do 510 KB, które obejmuje wszystkie listy, oraz dodatkowe ustawienia filtru wiadomości-śmieci. Jeśli użytkownik przekroczy ten limit, otrzyma komunikat o błędzie Outlook który wygląda następująco:

  > Nie można/Nie można dodać do listy wiadomości-śmieci na serwerze. Rozmiary plików na serwerze są  przesune. Filtr wiadomości-śmieci na serwerze będzie wyłączony do momentu zmniejszenia rozmiaru list wiadomości-śmieci do dozwolonego przez serwer.

  Aby uzyskać więcej informacji na temat tego limitu i sposobu jego zmiany, zobacz [KB2669081](https://support.microsoft.com/help/2669081).

- Zsynchronizowana kolekcja listy bezpiecznych adresów w uchcie usługi EOP ma następujące limity synchronizacji:
  - Łącznie jest 1024 pozycji na liście Sejf nadawców, liście adresatów Sejf i kontaktach zewnętrznych, jeśli jest włączona opcja Ufaj  wiadomościom e-mail od moich kontaktów.
  - Łącznie 500 wpisów na liście Zablokowani nadawcy i Zablokowane domeny.

  Po osiągnięciu limitu 1024 wpisów są już następujące zdarzenia:

  - Lista wstrzymuje akceptowanie wpisów w programie PowerShell Outlook w sieci Web, ale błąd nie jest wyświetlany.

    Outlook użytkownicy nadal mogą dodawać więcej niż 1024 wpisy, aż osiągną limit liczby Outlook 510 KB. Outlook użyć tych dodatkowych wpisów, o ile filtr usługi EOP nie blokuje wiadomości przed dostarczeniem jej do skrzynki pocztowej (reguły przepływu poczty, ochrona przed fałszowaniem itp.).

- W przypadku synchronizacji katalogów wpisy są synchronizowane z usługą Azure AD w następującej kolejności:
  1. Kontakty poczty, jeśli **jest włączona opcja Ufaj wiadomościom e-mail** od moich kontaktów.
  2. Lista Sejf nadawców i lista Sejf adresatów są łączone, odduplikowane i sortowane alfabetycznie po każdej zmianie dotyczącej pierwszych 1024 wpisów.

  Zostaną użyte pierwsze 1024 wpisy, a odpowiednie informacje będą stemplowane w nagłówkach wiadomości.

  Wpisy powyżej 1024, które nie zostały zsynchronizowane z usługą Azure AD, są przetwarzane przez program Outlook (nie Outlook w sieci Web) i w nagłówkach wiadomości nie są oznaczane żadne informacje.

Jak widać, włączenie ustawienia Ufaj  wiadomościom e-mail od moich kontaktów zmniejsza liczbę Sejf nadawców i adresatów Sejf, które można synchronizować. Jeśli taka funkcja może stanowić problem, zalecamy jej wyłączenie zasady grupy pomocą funkcji:

- Nazwa pliku: outlk16.opax
- Ustawienie zasad: **Ufaj wiadomościom e-mail od kontaktów**
