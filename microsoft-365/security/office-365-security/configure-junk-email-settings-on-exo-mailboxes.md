---
title: Konfigurowanie ustawień wiadomości-śmieci w skrzynkach pocztowych Exchange Online
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
description: Administratorzy mogą dowiedzieć się, jak skonfigurować ustawienia wiadomości-śmieci w Exchange Online skrzynkach pocztowych. Wiele z tych ustawień jest dostępnych dla użytkowników w Outlook lub Outlook w sieci Web.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ac7ac0f40c24c81cf916917b1b87626e032f8055
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130894"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Konfigurowanie ustawień wiadomości-śmieci w skrzynkach pocztowych Exchange Online

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W Microsoft 365 organizacji ze skrzynkami pocztowymi w Exchange Online organizacyjne ustawienia ochrony przed spamem są kontrolowane przez Exchange Online Protection (EOP). Aby uzyskać więcej informacji, zobacz [Ochrona przed spamem w ramach EOP](anti-spam-protection.md).

Istnieją jednak również określone ustawienia ochrony przed spamem, które administratorzy mogą skonfigurować w poszczególnych skrzynkach pocztowych w Exchange Online:

> [!NOTE]
> Usługa EOP używa teraz własnego agenta dostarczania przepływu poczty, aby kierować wiadomości do folderu Wiadomości-śmieci zamiast używać reguły wiadomości-śmieci. Parametr _Enabled_ w poleceniu cmdlet **Set-MailboxJunkEmailConfiguration** nie ma już żadnego wpływu na przepływ poczty. Funkcja EOP kieruje komunikaty na podstawie akcji ustawionych w zasadach ochrony przed spamem. Lista nadawców Sejf użytkownika i lista zablokowanych nadawców będą nadal działać jak zwykle.

- **Przenieś wiadomości do folderu Wiadomości-śmieci w oparciu o zasady ochrony przed spamem**: Gdy zasady ochrony przed spamem są skonfigurowane za pomocą akcji **Przenieś wiadomość do folderu Wiadomości-śmieci** na potrzeby werdyktu filtrowania spamu, wiadomość zostanie przeniesiona do folderu Wiadomości-śmieci po dostarczeniu wiadomości do skrzynki pocztowej. Aby uzyskać więcej informacji na temat werdyktów filtrowania spamu w zasadach ochrony przed spamem, zobacz [Konfigurowanie zasad ochrony przed spamem w usłudze EOP](configure-your-spam-filter-policies.md). Podobnie, jeśli automatyczne przeczyszczanie o wartości zero godzin (ZAP) stwierdzi, że dostarczona wiadomość jest spamem lub phish, wiadomość zostanie przeniesiona do folderu Wiadomości-śmieci dla akcji **Przenoszenie wiadomości do folderu wiadomości-śmieci** filtrowania spamu. Aby uzyskać więcej informacji na temat zap, zobacz [Zero godzin auto przeczyszczania (ZAP) w Exchange Online](zero-hour-auto-purge.md).

- **Ustawienia wiadomości-śmieci, które użytkownicy konfigurują dla siebie w Outlook lub Outlook w sieci Web**: _kolekcja listy bezpiecznej_ to lista Sejf nadawców, lista adresatów Sejf i lista Zablokowanych nadawców w każdej skrzynce pocztowej. Wpisy na tych listach określają, czy wiadomość została przeniesiona do skrzynki odbiorczej, czy do folderu Wiadomości-śmieci. Użytkownicy mogą skonfigurować kolekcję safelist dla własnej skrzynki pocztowej w Outlook lub Outlook w sieci Web (wcześniej znanej jako Outlook Web App). Administratorzy mogą skonfigurować kolekcję safelist w dowolnej skrzynce pocztowej użytkownika.

Usługa EOP może przenieść wiadomości do folderu Wiadomości-śmieci na podstawie akcji werdyktu filtrowania spamu **Przenieś wiadomość do folderu Wiadomości-śmieci** lub listy Zablokowanych nadawców w skrzynce pocztowej i uniemożliwić dostarczanie wiadomości do folderu Wiadomości-śmieci (na podstawie listy nadawców Sejf w skrzynce pocztowej).

Administratorzy mogą używać programu Exchange Online programu PowerShell do konfigurowania wpisów w kolekcji safelist w skrzynkach pocztowych (lista nadawców Sejf, lista adresatów Sejf i lista Zablokowanych nadawców).

> [!NOTE]
> Komunikaty od nadawców dodane przez użytkowników do własnych Sejf listy nadawców pominie filtrowanie zawartości w ramach EOP (lista SCL to -1). Aby uniemożliwić użytkownikom dodawanie wpisów do listy nadawców Sejf w Outlook, użyj zasady grupy, jak wspomniano w sekcji [Informacje o wiadomościach-śmieciach w sekcji Outlook](#about-junk-email-settings-in-outlook) w dalszej części tego artykułu. Filtrowanie zasad, filtrowanie zawartości i sprawdzanie Ochrona usługi Office 365 w usłudze Defender będą nadal stosowane do komunikatów.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Do wykonywania procedur w tym artykule można używać tylko programu Exchange Online Programu PowerShell. Aby nawiązać połączenie z programem Exchange Online programu PowerShell, zobacz [Połączenie to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Aby można było wykonać procedury opisane w tym artykule, musisz mieć przypisane uprawnienia w Exchange Online. W szczególności potrzebna jest rola **Adresaci poczty** (przypisana domyślnie do grup ról **Zarządzanie organizacją**, **Zarządzanie adresatami** i **Adresaci poczty niestandardowej** ) lub rola **Opcje użytkownika** (domyślnie przypisana do grup ról **Zarządzanie organizacją** i **Pomoc techniczna** ). Aby dodać użytkowników do grup ról w Exchange Online, zobacz [Modyfikowanie grup ról w Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups). Należy pamiętać, że użytkownicy z uprawnieniami domyślnymi mogą wykonywać te same procedury we własnej skrzynce pocztowej, o ile mają [dostęp do Exchange Online programu PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

- W środowiskach hybrydowych, w których funkcja EOP chroni lokalne Exchange skrzynki pocztowe, należy skonfigurować reguły przepływu poczty (nazywane również regułami transportu) w lokalnych Exchange. Te reguły przepływu poczty tłumaczą werdykt filtrowania spamu EOP, aby reguła wiadomości-śmieci w skrzynce pocztowej mogła przenieść wiadomość do folderu Wiadomości-śmieci. Aby uzyskać szczegółowe informacje, zobacz [Configure EOP to deliver spam to the Junk Email folder in hybrid environments (Konfigurowanie EOP w celu dostarczania spamu do folderu Wiadomości-śmieci w środowiskach hybrydowych](/exchange/standalone-eop/configure-eop-spam-protection-hybrid)).

- Sejf nadawcy udostępnionych skrzynek pocztowych nie są synchronizowane z Azure AD i EOP zgodnie z projektem.

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Konfigurowanie kolekcji safelist w skrzynce pocztowej przy użyciu Exchange Online programu PowerShell

Kolekcja safelist w skrzynce pocztowej zawiera listę nadawców Sejf, listę adresatów Sejf i listę Zablokowanych nadawców. Domyślnie użytkownicy mogą skonfigurować kolekcję safelist we własnej skrzynce pocztowej w Outlook lub Outlook w sieci Web. Administratorzy mogą używać odpowiednich parametrów w poleceniu cmdlet **Set-MailboxJunkEmailConfiguration** w celu skonfigurowania kolekcji listy bezpiecznej w skrzynce pocztowej użytkownika. Te parametry zostały opisane w poniższej tabeli.

|Parametr na Set-MailboxJunkEmailConfiguration|ustawienie Outlook w sieci Web|
|---|---|
|_BlockedSendersAndDomains_|**Przenoszenie wiadomości e-mail z tych nadawców lub domen do folderu Wiadomości-śmieci**|
|_KontaktyZaufane_|**Zaufaj wiadomości e-mail od moich kontaktów**|
|_TrustedListsOnly_|**Ufaj tylko adresom e-mail z moich Sejf nadawców i domen oraz Sejf list adresowych**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Nie przenosij wiadomości e-mail od tych nadawców do folderu Wiadomości-śmieci**|

<sup>\*</sup>**Uwagi**:

- W Exchange Online **wpisy domeny na liście nadawców** Sejf lub parametr _TrustedSendersAndDomains_ nie są rozpoznawane, więc używaj tylko adresów e-mail. W autonomicznej operacji EOP z synchronizacją katalogów wpisy domeny nie są domyślnie synchronizowane, ale można włączyć synchronizację domen. Aby uzyskać więcej informacji, zobacz [KB3019657](https://support.microsoft.com/help/3019657).
- Nie można bezpośrednio zmodyfikować listy adresatów Sejf przy użyciu polecenia cmdlet **Set-MailboxJunkEmailConfiguration** (parametr _TrustedRecipientsAndDomains_ nie działa). Modyfikujesz listę Sejf nadawców i te zmiany są synchronizowane z listą adresatów Sejf.

Aby skonfigurować kolekcję safelist w skrzynce pocztowej, użyj następującej składni:

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Aby wprowadzić wiele wartości i zastąpić wszystkie istniejące wpisy parametrów _BlockedSendersAndDomains_ i _TrustedSendersAndDomains_ , użyj następującej składni: `"<Value1>","<Value2>"...`. Aby dodać lub usunąć co najmniej jedną wartość bez wpływu na inne istniejące wpisy, użyj następującej składni: `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

W tym przykładzie skonfigurowano następujące ustawienia dla kolekcji safelist w skrzynce pocztowej Ori Epsteina:

- Dodaj wartość shopping@fabrikam.com do listy Zablokowanych nadawców.
- Usuń wartość chris@fourthcoffee.com z listy nadawców Sejf i listy adresatów Sejf.
- Konfiguruje kontakty w folderze Kontakty tak, aby były traktowane jako zaufani nadawcy.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

W tym przykładzie usunięto contoso.com domeny z listy zablokowanych nadawców we wszystkich skrzynkach pocztowych użytkowników w organizacji.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Jeśli użytkownik nigdy nie otworzył swojej skrzynki pocztowej, może wystąpić błąd podczas uruchamiania poprzednich poleceń. Aby pominąć ten błąd w przypadku operacji zbiorczych, dodaj `-ErrorAction SilentlyContinue` polecenie **Set-MailboxJunkEmailConfiguration** .
> - Filtr wiadomości-śmieci Outlook ma dodatkowe ustawienia kolekcji safelist (na przykład **automatycznie dodaj osoby, które wysyłam pocztą e-mail do listy nadawców Sejf**). Aby uzyskać więcej informacji, zobacz [Używanie filtrów wiadomości-śmieci do kontrolowania wyświetlanych komunikatów](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Skąd wiadomo, że to działanie się powiodło?

Aby sprawdzić, czy kolekcja safelist została pomyślnie skonfigurowana w skrzynce pocztowej, użyj dowolnej z następujących procedur:

- Zastąp _\<MailboxIdentity\>_ ciąg nazwą, aliasem lub adresem e-mail skrzynki pocztowej i uruchom następujące polecenie, aby zweryfikować wartości właściwości:

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Jeśli lista wartości jest za długa, użyj tej składni:

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>Informacje o ustawieniach wiadomości-śmieci w Outlook

Aby włączyć, wyłączyć i skonfigurować ustawienia filtru wiadomości-śmieci po stronie klienta, które są dostępne w Outlook, użyj zasady grupy. Aby uzyskać więcej informacji, zobacz [Pliki szablonów administracyjnych (ADMX/ADML) i narzędzie do dostosowywania Office dla Aplikacje Microsoft 365 dla przedsiębiorstw, Office 2019 r. i Office 2016](https://www.microsoft.com/download/details.aspx?id=49030) r. oraz [Jak wdrożyć ustawienia wiadomości-śmieci, takie jak lista nadawców Sejf, za pomocą polecenia zasady grupy](https://support.microsoft.com/help/2252421).

Gdy filtr wiadomości-śmieci Outlook jest ustawiony na wartość domyślną **Brak automatycznego filtrowania** **w** \> **opcjach** opcji \> **wiadomości-śmieci** dla **użytkowników** \> domowych, Outlook nie próbuje sklasyfikować wiadomości jako spamu, ale nadal używa kolekcji listy bezpiecznych wiadomości (lista nadawców Sejf, Sejf  Lista adresatów i lista zablokowanych nadawców), aby przenieść wiadomości do folderu Wiadomości-śmieci po dostarczeniu. Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Omówienie filtru wiadomości-śmieci](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

> [!NOTE]
> W Microsoft 365 organizacjach zalecamy pozostawienie filtru wiadomości-śmieci w Outlook ustawić wartość **Brak automatycznego filtrowania**, aby zapobiec niepotrzebnym konfliktom (zarówno pozytywnym, jak i negatywnym) z werdyktami filtrowania spamu z EOP.

Gdy filtr Outlook wiadomości-śmieci jest ustawiony na **wartość Niska** lub **Wysoka**, filtr wiadomości-śmieci Outlook używa własnej technologii filtru SmartScreen do identyfikowania i przenoszenia spamu do folderu Wiadomości-śmieci. Ta klasyfikacja spamu jest oddzielona od poziomu ufności spamu (SCL) określonego przez EOP. W rzeczywistości Outlook ignoruje listę SCL z EOP (chyba że EOP oznaczył wiadomość w celu pominięcia filtrowania spamu) i używa własnych kryteriów w celu określenia, czy wiadomość jest spamem. Oczywiście, jest możliwe, że werdykt spamu z EOP i Outlook może być taki sam. Aby uzyskać więcej informacji na temat tych ustawień, zobacz [Zmienianie poziomu ochrony w filtrze wiadomości-śmieci](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b).

> [!NOTE]
> W listopadzie 2016 r. firma Microsoft przestała produkować aktualizacje definicji spamu dla filtrów SmartScreen w Exchange i Outlook. Istniejące definicje spamu smartscreen pozostały w miejscu, ale ich skuteczność prawdopodobnie z czasem będzie spadać. Aby uzyskać więcej informacji, zobacz [Wycofywanie obsługi filtru SmartScreen w Outlook i Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

W związku z tym filtr wiadomości-śmieci Outlook może używać kolekcji listy bezpiecznej skrzynki pocztowej i własnej klasyfikacji spamu do przenoszenia wiadomości do folderu Wiadomości-śmieci.

Zarówno Outlook, jak i Outlook w sieci Web obsługują kolekcję safelist. Kolekcja safelist jest zapisywana w skrzynce pocztowej Exchange Online, więc zmiany kolekcji safelist w Outlook są wyświetlane w Outlook w sieci Web i na odwrót.

## <a name="limits-for-junk-email-settings"></a>Limity ustawień wiadomości-śmieci

Kolekcja safelist (lista nadawców Sejf, lista Sejf adresatów i lista zablokowanych nadawców), która jest przechowywana w skrzynce pocztowej użytkownika, jest również synchronizowana z funkcją EOP. W przypadku synchronizacji katalogów kolekcja safelist jest synchronizowana z Azure AD.

- Kolekcja safelist w skrzynce pocztowej użytkownika ma limit 510 KB, który obejmuje wszystkie listy oraz dodatkowe ustawienia filtru wiadomości-śmieci. Jeśli użytkownik przekroczy ten limit, otrzyma błąd Outlook, który wygląda następująco:

  > Nie można dodać do listy wiadomości-śmieci serwera/ nie można ich dodać. Rozmiar dozwolony na serwerze jest większy. Filtr Wiadomości-śmieci na serwerze zostanie wyłączony, dopóki listy wiadomości-śmieci nie zostaną zmniejszone do rozmiaru dozwolonego przez serwer.

  Aby uzyskać więcej informacji na temat tego limitu i sposobu jego zmiany, zobacz [KB2669081](https://support.microsoft.com/help/2669081).

- Zsynchronizowana kolekcja safelist w ramach operacji EOP ma następujące limity synchronizacji:
  - 1024 całkowita liczba wpisów na liście nadawców Sejf, lista adresatów Sejf i kontakty zewnętrzne, jeśli **włączona jest zaufana wiadomość e-mail od moich kontaktów**.
  - 500 wszystkich wpisów na liście zablokowanych nadawców i zablokowanych domen.

  Po osiągnięciu limitu wejścia na 1024 dzieje się następująca sytuacja:

  - Lista przestaje akceptować wpisy w programie PowerShell i Outlook w sieci Web, ale nie jest wyświetlany żaden błąd.

    Outlook użytkownicy mogą nadal dodawać więcej niż 1024 wpisy, dopóki nie osiągną limitu Outlook wynoszącego 510 KB. Outlook mogą używać tych dodatkowych wpisów, o ile filtr EOP nie blokuje wiadomości przed dostarczeniem do skrzynki pocztowej (reguły przepływu poczty, zabezpieczenia przed fałszowaniem itp.).

- W przypadku synchronizacji katalogów wpisy są synchronizowane z Azure AD w następującej kolejności:
  1. Kontakty poczty, jeśli **adres e-mail zaufania od moich kontaktów** jest włączony.
  2. Lista nadawców Sejf i lista adresatów Sejf są łączone, dezduplikowane i sortowane alfabetycznie za każdym razem, gdy wprowadzono zmianę dla pierwszych wpisów 1024.

  Używane są pierwsze 1024 wpisy, a odpowiednie informacje są ostemplowane w nagłówkach wiadomości.

  Wpisy w wersji 1024, które nie zostały zsynchronizowane z Azure AD, są przetwarzane przez Outlook (nie Outlook w sieci Web), a żadne informacje nie są ostemplowane w nagłówkach wiadomości.

Jak widać, włączenie ustawienia **Ufaj wiadomości e-mail z moich kontaktów** zmniejsza liczbę Sejf nadawców i adresatów Sejf, które można zsynchronizować. Jeśli jest to problemem, zalecamy użycie zasady grupy, aby wyłączyć tę funkcję:

- Nazwa pliku: outlk16.opax
- Ustawienie zasad: **Ufaj wiadomości e-mail od kontaktów**
