---
title: Zarządzanie inspekcją skrzynki pocztowej
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: aaca8987-5b62-458b-9882-c28476a66918
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Rejestrowanie inspekcji skrzynki pocztowej jest domyślnie włączone w Microsoft 365 (nazywane również domyślnym inspekcją skrzynki pocztowej lub domyślnie "inspekcją skrzynki pocztowej"). Ta konfiguracja oznacza, że niektóre akcje wykonywane przez właścicieli skrzynek pocztowych, delegatów i administratorów są automatycznie rejestrowane w dzienniku inspekcji skrzynki pocztowej, gdzie można wyszukiwać działania wykonywane w skrzynce pocztowej.
ms.openlocfilehash: d5d966cf4d5b7c58c15df4ce8d4039331ebca8c4
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972634"
---
# <a name="manage-mailbox-auditing"></a>Zarządzanie inspekcją skrzynki pocztowej

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Od stycznia 2019 r. firma Microsoft domyślnie włącza rejestrowanie inspekcji skrzynek pocztowych dla wszystkich organizacji. Oznacza to, że niektóre akcje wykonywane przez właścicieli skrzynek pocztowych, delegatów i administratorów są automatycznie rejestrowane, a odpowiednie rekordy inspekcji skrzynki pocztowej będą dostępne podczas wyszukiwania ich w dzienniku inspekcji skrzynki pocztowej. Przed domyślnym włączeniem inspekcji skrzynki pocztowej trzeba było ją ręcznie włączyć dla każdej skrzynki pocztowej użytkownika w organizacji.

Poniżej przedstawiono niektóre zalety domyślnego przeprowadzania inspekcji skrzynek pocztowych:

- Inspekcja jest włączana automatycznie podczas tworzenia nowej skrzynki pocztowej. Nie trzeba ręcznie włączać go dla nowych użytkowników.
- Nie musisz zarządzać inspekcją akcji skrzynki pocztowej. Wstępnie zdefiniowany zestaw akcji skrzynki pocztowej jest domyślnie poddawany inspekcji dla każdego typu logowania (Administrator, Delegat i Właściciel).
- Gdy firma Microsoft wyda nową akcję skrzynki pocztowej, akcja może zostać automatycznie dodana do listy akcji skrzynki pocztowej, które są domyślnie poddawane inspekcji (z zastrzeżeniem, że użytkownik ma odpowiednią licencję). Oznacza to, że nie trzeba monitorować dodawania nowych akcji w skrzynkach pocztowych.
- Masz spójne zasady inspekcji skrzynek pocztowych w całej organizacji (ponieważ przeprowadzasz inspekcję tych samych akcji dla wszystkich skrzynek pocztowych).

> [!NOTE]
>
> - Ważne jest, aby pamiętać o domyślnym wydaniu inspekcji skrzynki pocztowej: nie musisz nic robić, aby zarządzać inspekcją skrzynek pocztowych. Aby jednak dowiedzieć się więcej, dostosować inspekcję skrzynek pocztowych z ustawień domyślnych lub całkowicie ją wyłączyć, ten artykuł może Ci pomóc.
> - Domyślnie tylko zdarzenia inspekcji skrzynki pocztowej dla użytkowników E5 są dostępne w wyszukiwaniach dzienników inspekcji w portalu zgodności usługi Microsoft Purview lub za pośrednictwem interfejsu API działania zarządzania Office 365. Aby uzyskać więcej informacji, zobacz sekcję [Więcej informacji](#more-information) w tym artykule.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Sprawdź, czy inspekcja skrzynki pocztowej jest domyślnie włączona

Aby sprawdzić, czy inspekcja skrzynki pocztowej jest domyślnie włączona dla organizacji, uruchom następujące polecenie w [programie Exchange Online programu PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

Wartość **False** wskazuje, że inspekcja skrzynki pocztowej jest domyślnie włączona dla organizacji. Ta domyślnie wartość organizacyjna zastępuje ustawienie inspekcji skrzynki pocztowej w określonych skrzynkach pocztowych. Jeśli na przykład inspekcja skrzynki pocztowej jest wyłączona dla skrzynki pocztowej (właściwość *AuditEnabled* to **False** w skrzynce pocztowej), domyślne akcje skrzynki pocztowej będą nadal poddawane inspekcji dla skrzynki pocztowej, ponieważ inspekcja skrzynki pocztowej jest domyślnie włączona dla organizacji.

Aby inspekcja skrzynek pocztowych była wyłączona dla określonych skrzynek pocztowych, należy skonfigurować obejście inspekcji skrzynki pocztowej dla właściciela skrzynki pocztowej i innych użytkowników, którzy zostali delegowani do skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz sekcję [Pomiń rejestrowanie inspekcji skrzynki pocztowej](#bypass-mailbox-audit-logging) w dalszej części tego artykułu.

> [!NOTE]
> Po domyślnym włączeniu inspekcji skrzynki pocztowej dla organizacji właściwość *AuditEnabled* dla skrzynek pocztowych, których dotyczy problem, nie zostanie zmieniona z **False** na **True**. Innymi słowy inspekcja skrzynki pocztowej domyślnie ignoruje właściwość *AuditEnabled* w skrzynkach pocztowych.

## <a name="supported-mailbox-types"></a>Obsługiwane typy skrzynek pocztowych

W poniższej tabeli przedstawiono typy skrzynek pocztowych, które są obecnie domyślnie obsługiwane przez inspekcję skrzynki pocztowej:

|Typ skrzynki pocztowej|Obsługiwane|
|---|:---:|
|Skrzynki pocztowe użytkownika|![Znacznik wyboru.](../media/checkmark.png)|
|Udostępnione skrzynki pocztowe|![Znacznik wyboru.](../media/checkmark.png)|
|skrzynki pocztowe grupy Microsoft 365|![Znacznik wyboru.](../media/checkmark.png)|
|Skrzynki pocztowe zasobów||
|Skrzynki pocztowe folderów publicznych||

## <a name="logon-types-and-mailbox-actions"></a>Typy logowania i akcje skrzynki pocztowej

Typy logowania klasyfikują użytkownika, który wykonał inspekcję akcji w skrzynce pocztowej. Na poniższej liście opisano typy logowania używane w rejestrowaniu inspekcji skrzynki pocztowej:

- **Właściciel**: właściciel skrzynki pocztowej (konto skojarzone ze skrzynką pocztową).
- **Delegowanie**:
  - Użytkownik, któremu przypisano uprawnienie SendAs, SendOnBehalf lub FullAccess do innej skrzynki pocztowej.
  - Administrator, któremu przypisano uprawnienie FullAccess do skrzynki pocztowej użytkownika.
- **Administrator**:
  - Skrzynka pocztowa jest przeszukiwana przy użyciu jednego z następujących narzędzi zbierania elektronicznych materiałów dowodowych firmy Microsoft:
    - Wyszukiwanie zawartości w Centrum zgodności.
    - eDiscovery lub eDiscovery (Premium) w Centrum zgodności.
    - In-Place zbierania elektronicznych materiałów dowodowych w Exchange Online.
  - Dostęp do skrzynki pocztowej jest uzyskiwany za pomocą edytora Microsoft Exchange Server MAPI.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Akcje skrzynki pocztowej dla skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych

W poniższej tabeli opisano akcje skrzynki pocztowej dostępne w rejestrowaniu inspekcji skrzynki pocztowej dla skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych.

- Znacznik wyboru (![Znacznik wyboru.](../media/checkmark.png)) wskazuje, że akcja skrzynki pocztowej może być rejestrowana dla typu logowania (nie wszystkie akcje są dostępne dla wszystkich typów logowania).
- Gwiazdka ( <sup>\*</sup> ) po znaczniku wyboru wskazuje, że akcja skrzynki pocztowej jest domyślnie rejestrowana dla typu logowania.
- Pamiętaj, że administrator z uprawnieniami pełnego dostępu do skrzynki pocztowej jest uważany za pełnomocnika.

|Akcja skrzynki pocztowej|Opis|Administrator|Delegata|Właściciel|
|---|---|:---:|:---:|:---:|
|**DodajfolderPermissions**|Chociaż ta wartość jest akceptowana jako akcja skrzynki pocztowej, jest już uwzględniona w akcji **UpdateFolderPermissions** i nie jest poddana inspekcji oddzielnie. Innymi słowy, nie używaj tej wartości.||||
|**ApplyRecord**|Element jest oznaczony jako rekord.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|
|**Kopii**|Wiadomość została skopiowana do innego folderu.|![Znacznik wyboru.](../media/checkmark.png)|||
|**Tworzenie**|Element został utworzony w folderze Kalendarz, Kontakty, Wersja robocza, Notatki lub Zadania w skrzynce pocztowej (na przykład zostanie utworzone nowe żądanie spotkania). Tworzenie, wysyłanie lub odbieranie komunikatu nie jest poddawane inspekcji. Ponadto tworzenie folderu skrzynki pocztowej nie jest poddawane inspekcji.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)|
|**FolderBind**|Uzyskano dostęp do folderu skrzynki pocztowej. Ta akcja jest również rejestrowana, gdy administrator lub pełnomocnik otworzy skrzynkę pocztową. <br/><br/> **Uwaga**: rekordy inspekcji dla akcji powiązania folderów wykonywanych przez delegatów są konsolidowane. Jeden rekord inspekcji jest generowany dla indywidualnego dostępu do folderu w ciągu 24 godzin.|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)||
|**HardDelete**|Komunikat został usunięty z folderu Elementy możliwe do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|Użytkownik zalogował się do swojej skrzynki pocztowej.|||![Znacznik wyboru](../media/checkmark.png)|
|**MailItemsAccessed**|**Uwaga**: ta wartość jest dostępna tylko dla użytkowników z licencjami E5/A5/G5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie inspekcji usługi Microsoft Purview (Premium)](set-up-advanced-audit.md). <br/><br/> Dostęp do danych poczty są uzyskiwane za pomocą protokołów poczty e-mail i klientów.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**MessageBind**|**Uwaga**: ta wartość jest dostępna tylko dla użytkowników *bez* licencji E5/A5/G5. <br/><br/> Komunikat został wyświetlony w okienku podglądu lub otwarty przez administratora.|![Znacznik wyboru](../media/checkmark.png)|||
|**ModifyFolderPermissions**|Chociaż ta wartość jest akceptowana jako akcja skrzynki pocztowej, jest już uwzględniona w akcji **UpdateFolderPermissions** i nie jest poddana inspekcji oddzielnie. Innymi słowy, nie używaj tej wartości.||||
|**Przenieść**|Wiadomość została przeniesiona do innego folderu.|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|
|**MoveToDeletedItems**|Komunikat został usunięty i przeniesiony do folderu Elementy usunięte.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**RecordDelete**|Element oznaczony jako rekord został usunięty nietrwale (przeniesiony do folderu Elementy możliwe do odzyskania). Elementów oznaczonych jako rekordy nie można trwale usunąć (przeczyszczać z folderu Elementy możliwe do odzyskania).|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|
|**RemoveFolderPermissions**|Chociaż ta wartość jest akceptowana jako akcja skrzynki pocztowej, jest już uwzględniona w akcji **UpdateFolderPermissions** i nie jest poddana inspekcji oddzielnie. Innymi słowy, nie używaj tej wartości.||||
|**SearchQueryInitiated**|**Uwaga**: ta wartość jest dostępna tylko dla użytkowników z licencjami E5/A5/G5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie inspekcji usługi Microsoft Purview (Premium)](set-up-advanced-audit.md). <br/><br/> Osoba używa Outlook (Windows, Mac, iOS, Android lub Outlook w sieci Web) lub aplikacji Poczta dla Windows 10 do wyszukiwania elementów w skrzynce pocztowej.|||![Znacznik wyboru](../media/checkmark.png)|
|**Wyślij**|**Uwaga**: ta wartość jest dostępna tylko dla użytkowników z licencjami E5/A5/G5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie inspekcji usługi Microsoft Purview (Premium)](set-up-advanced-audit.md). <br/><br/> Użytkownik wysyła wiadomość e-mail, odpowiada na wiadomość e-mail lub przekazuje wiadomość e-mail.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>||![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Wiadomość została wysłana przy użyciu uprawnienia SendAs. Oznacza to, że inny użytkownik wysłał wiadomość tak, jakby pochodziła od właściciela skrzynki pocztowej.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Wiadomość została wysłana przy użyciu uprawnienia SendOnBehalf. Oznacza to, że inny użytkownik wysłał wiadomość w imieniu właściciela skrzynki pocztowej. Wiadomość wskazuje adresatowi, kto został wysłany w imieniu i kto faktycznie wysłał wiadomość.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Komunikat został trwale usunięty lub usunięty z folderu Elementy usunięte. Elementy usunięte nietrwale są przenoszone do folderu Elementy możliwe do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**Aktualizacja**|Komunikat lub dowolna z jego właściwości została zmieniona.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|Delegowanie kalendarza zostało przypisane do skrzynki pocztowej. Delegowanie kalendarza daje innej osobie w tej samej organizacji uprawnienia do zarządzania kalendarzem właściciela skrzynki pocztowej.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>||![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Do elementu poczty jest stosowana inna etykieta przechowywania (do elementu może być przypisana tylko jedna etykieta przechowywania).|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|
|**UpdateFolderPermissions**|Zmieniono uprawnienie folderu. Uprawnienia folderu określają, którzy użytkownicy w organizacji mogą uzyskiwać dostęp do folderów w skrzynce pocztowej i wiadomości znajdujących się w tych folderach.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|Dodano, usunięto lub zmieniono regułę skrzynki odbiorczej. Reguły skrzynki odbiorczej są używane do przetwarzania komunikatów w skrzynce odbiorczej użytkownika na podstawie określonych warunków i wykonywania akcji po spełnieniu warunków reguły, takich jak przenoszenie komunikatu do określonego folderu lub usuwanie komunikatu.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|

> [!IMPORTANT]
> Jeśli akcje skrzynki pocztowej zostały dostosowane do inspekcji dla dowolnego typu logowania *przed* domyślnym włączeniem inspekcji skrzynki pocztowej w organizacji, dostosowane ustawienia zostaną zachowane w skrzynce pocztowej i nie zostaną zastąpione domyślną akcją skrzynki pocztowej zgodnie z opisem w tej sekcji. Aby przywrócić domyślne wartości akcji skrzynki pocztowej inspekcji (co można zrobić w dowolnym momencie), zobacz sekcję [Przywracanie domyślnych akcji skrzynki pocztowej](#restore-the-default-mailbox-actions) w dalszej części tego artykułu.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Akcje skrzynki pocztowej dla skrzynek pocztowych grupy Microsoft 365

Domyślnie inspekcja skrzynek pocztowych powoduje, że rejestrowanie inspekcji skrzynki pocztowej Microsoft 365 skrzynki pocztowe grupy, ale nie można dostosować tego, co jest rejestrowane (nie można dodawać ani usuwać akcji skrzynki pocztowej, które są rejestrowane dla dowolnego typu logowania).

W poniższej tabeli opisano akcje skrzynki pocztowej, które są domyślnie rejestrowane w skrzynkach pocztowych grupy Microsoft 365 dla każdego typu logowania.

Pamiętaj, że administrator z uprawnieniami pełnego dostępu do skrzynki pocztowej grupy Microsoft 365 jest uważany za pełnomocnika.

|Akcja skrzynki pocztowej|Opis|Administrator|Delegata|Właściciel|
|---|---|:---:|:---:|:---:|
|**Tworzenie**|Tworzenie elementu kalendarza. Tworzenie, wysyłanie lub odbieranie komunikatu nie jest poddawane inspekcji.|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|Komunikat został usunięty z folderu Elementy możliwe do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**MoveToDeletedItems**|Komunikat został usunięty i przeniesiony do folderu Elementy usunięte.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Wiadomość została wysłana przy użyciu uprawnienia SendAs.|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Wiadomość została wysłana przy użyciu uprawnienia SendOnBehalf.|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Komunikat został trwale usunięty lub usunięty z folderu Elementy usunięte. Elementy usunięte nietrwale są przenoszone do folderu Elementy możliwe do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**Aktualizacja**|Komunikat lub dowolna z jego właściwości została zmieniona.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Sprawdź, czy domyślne akcje skrzynki pocztowej są rejestrowane dla każdego typu logowania

Inspekcja skrzynki pocztowej domyślnie dodaje nową właściwość *DefaultAuditSet* do wszystkich skrzynek pocztowych. Wartość tej właściwości wskazuje, czy domyślne akcje skrzynki pocztowej (zarządzane przez firmę Microsoft) są poddawane inspekcji w skrzynce pocztowej.

Aby wyświetlić wartość w skrzynkach pocztowych użytkownika lub udostępnionych skrzynkach pocztowych, zastąp \<MailboxIdentity\> ciąg nazwą, aliasem, adresem e-mail lub główną nazwą użytkownika (nazwą użytkownika) skrzynki pocztowej i uruchom następujące polecenie w Exchange Online programu PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

Aby wyświetlić wartość w skrzynkach pocztowych grupy Microsoft 365, zastąp \<MailboxIdentity\> ciąg nazwą, aliasem lub adresem e-mail udostępnionej skrzynki pocztowej i uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

Wartość `Admin, Delegate, Owner` wskazuje:

- Domyślne akcje skrzynki pocztowej dla wszystkich trzech typów logowania są poddawane inspekcji. Jest to jedyna wartość widoczna w skrzynkach pocztowych grupy Microsoft 365.
- Administrator *nie* zmienił akcji skontrolowanej skrzynki pocztowej dla żadnego typu logowania w skrzynce pocztowej użytkownika lub udostępnionej skrzynce pocztowej. Pamiętaj, że jest to domyślny stan po domyślnym włączeniu inspekcji skrzynki pocztowej w organizacji.

Jeśli administrator kiedykolwiek zmienił akcje skrzynki pocztowej, które są poddawane inspekcji dla typu logowania (przy użyciu parametrów *AuditAdmin*, *AuditDelegate* lub *AuditOwner* w poleceniu cmdlet **Set-Mailbox** ), wartość właściwości będzie inna.

Na przykład wartość `Owner` właściwości *DefaultAuditSet* w skrzynce pocztowej użytkownika lub udostępnionej skrzynce pocztowej wskazuje:

- Domyślne akcje skrzynki pocztowej właściciela skrzynki pocztowej są poddawane inspekcji.
- Akcje skontrolowanych skrzynek pocztowych dla `Delegate` typów logowania i `Admin` zostały zmienione z akcji domyślnych.

Pusta wartość właściwości *DefaultAuditSet* wskazuje, że akcje skrzynki pocztowej dla wszystkich trzech typów logowania zostały zmienione w skrzynce pocztowej użytkownika lub udostępnionej skrzynce pocztowej.

Aby uzyskać więcej informacji, zobacz [sekcję Zmień lub przywróć akcje skrzynki pocztowej zarejestrowane domyślnie](#change-or-restore-mailbox-actions-logged-by-default) w tym artykule

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Wyświetlanie akcji skrzynki pocztowej, które są rejestrowane w skrzynkach pocztowych

Aby wyświetlić akcje skrzynki pocztowej, które są obecnie rejestrowane w skrzynkach pocztowych użytkownika lub udostępnionych skrzynkach pocztowych, zastąp \<MailboxIdentity\> ciąg nazwą, aliasem, adresem e-mail lub główną nazwą użytkownika (nazwą użytkownika) skrzynki pocztowej i uruchom co najmniej jedno z następujących poleceń w programie Exchange Online programu PowerShell.

> [!NOTE]
> Mimo że możesz dodać `-GroupMailbox` przełącznik do następujących poleceń **Get-Mailbox** dla skrzynek pocztowych Microsoft 365 Grupuj, nie wierz w zwracane wartości. Domyślne i statyczne akcje skrzynki pocztowej, które są poddawane inspekcji dla skrzynek pocztowych grupy Microsoft 365, zostały opisane w sekcji [Akcje skrzynki pocztowej dla skrzynek pocztowych grupy Microsoft 365](#mailbox-actions-for-microsoft-365-group-mailboxes) wcześniej w tym artykule.

#### <a name="owner-actions"></a>Akcje właściciela

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditOwner
```

#### <a name="delegate-actions"></a>Delegowanie akcji

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditDelegate
```

#### <a name="admin-actions"></a>Akcje administratora

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditAdmin
```

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Domyślnie rejestrowane akcje zmiany lub przywracania skrzynki pocztowej

Jak wyjaśniono wcześniej, jedną z kluczowych zalet domyślnego przeprowadzania inspekcji skrzynek pocztowych jest: nie musisz zarządzać inspekcją akcji skrzynek pocztowych. Firma Microsoft robi to za Ciebie, a my automatycznie dodamy nowe akcje skrzynki pocztowej, które mają być domyślnie poddane inspekcji po ich wydaniu.

Jednak twoja organizacja może być wymagana do inspekcji innego zestawu akcji skrzynki pocztowej dla skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych. W procedurach w tej sekcji pokazano, jak zmienić akcje skrzynki pocztowej, które są poddawane inspekcji dla każdego typu logowania, oraz jak przywrócić domyślne akcje zarządzane przez firmę Microsoft.

> [!IMPORTANT]
> Jeśli użyjesz poniższych procedur, aby dostosować akcje skrzynki pocztowej, które są rejestrowane w skrzynkach pocztowych użytkowników lub udostępnionych skrzynkach pocztowych, żadne nowe domyślne akcje skrzynki pocztowej wydane przez firmę Microsoft nie będą automatycznie poddawane inspekcji w tych skrzynkach pocztowych. Musisz ręcznie dodać wszystkie nowe akcje skrzynki pocztowej do dostosowanej listy akcji.

### <a name="change-the-mailbox-actions-to-audit"></a>Zmienianie akcji skrzynki pocztowej na inspekcję

Możesz użyć parametrów *AuditAdmin*, *AuditDelegate* lub *AuditOwner* w poleceniu cmdlet **Set-Mailbox**, aby zmienić akcje skrzynki pocztowej, które są poddawane inspekcji dla skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych (nie można dostosować inspekcji akcji dla skrzynek pocztowych grupy Microsoft 365).

Możesz użyć dwóch różnych metod, aby określić akcje skrzynki pocztowej:

- *Zastąp* (zastąp) istniejące akcje skrzynki pocztowej przy użyciu tej składni: `action1,action2,...actionN`.
- *Dodaj lub usuń* akcje skrzynki pocztowej bez wpływu na inne istniejące wartości przy użyciu tej składni: `@{Add="action1","action2",..."actionN"}` lub `@{Remove="action1","action2",..."actionN"}`.

W tym przykładzie akcje skrzynki pocztowej administratora dla skrzynki pocztowej o nazwie "Gabriela Laureano" są zmieniane przez zastąpienie domyślnych akcji za pomocą funkcji SoftDelete i HardDelete.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

W tym przykładzie do skrzynki pocztowej laura@contoso.onmicrosoft.com zostanie dodana akcja właściciela mailboxLogin.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

W tym przykładzie usunięto akcję delegata MoveToDeletedItems dla skrzynki pocztowej Dyskusji zespołowej.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Niezależnie od używanej metody dostosowywanie skontrolowanych akcji skrzynki pocztowej w skrzynkach pocztowych użytkowników lub udostępnionych skrzynkach pocztowych ma następujące wyniki:

- W przypadku niestandardowego typu logowania akcje skontrolowanych skrzynek pocztowych nie są już zarządzane przez firmę Microsoft.
- Dostosowany typ logowania nie jest już wyświetlany w wartości właściwości *DefaultAuditSet* dla skrzynki pocztowej zgodnie z [wcześniejszym opisem](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type).

### <a name="restore-the-default-mailbox-actions"></a>Przywracanie domyślnych akcji skrzynki pocztowej

> [!NOTE]
> Poniższe procedury nie mają zastosowania do skrzynek pocztowych grupy Microsoft 365 (są one ograniczone do akcji domyślnych opisanych [tutaj](#mailbox-actions-for-microsoft-365-group-mailboxes)).

Jeśli dostosowano akcje skrzynki pocztowej, które są poddawane inspekcji w skrzynce pocztowej użytkownika lub udostępnionej skrzynce pocztowej, możesz przywrócić domyślne akcje skrzynki pocztowej dla jednego lub wszystkich typów logowania przy użyciu tej składni:

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Można określić wiele wartości *DefaultAuditSet* rozdzielonych przecinkami

W tym przykładzie są przywracane domyślne akcje inspekcji skrzynki pocztowej dla wszystkich typów logowania w mark@contoso.onmicrosoft.com skrzynki pocztowej.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

W tym przykładzie przywraca domyślne akcje skontrolowanych skrzynek pocztowych dla typu logowanie administratora w chris@contoso.onmicrosoft.com skrzynki pocztowej, ale pozostawia dostosowane akcje skontrolowanych skrzynek pocztowych dla typów logowania Delegat i Właściciel.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

Przywracanie domyślnych akcji skontrolowanych skrzynek pocztowych dla typu logowania ma następujące wyniki:

- Bieżąca lista akcji skrzynki pocztowej jest zastępowana domyślnymi akcjami skrzynki pocztowej dla typu logowania.
- Wszystkie nowe akcje skrzynki pocztowej wydane przez firmę Microsoft są automatycznie dodawane do listy inspekcji akcji dla typu logowania.
- Wartość właściwości *DefaultAuditSet* dla skrzynki pocztowej jest aktualizowana w celu uwzględnienia przywróconego typu logowania.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Domyślnie wyłącz inspekcję skrzynek pocztowych dla organizacji

Inspekcję skrzynek pocztowych można domyślnie wyłączyć dla całej organizacji, uruchamiając następujące polecenie w programie Exchange Online programu PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

Domyślne wyłączenie inspekcji skrzynki pocztowej ma następujące wyniki:

- Inspekcja skrzynek pocztowych jest wyłączona dla Twojej organizacji.
- Od momentu domyślnego wyłączenia inspekcji skrzynki pocztowej żadne akcje skrzynki pocztowej nie są poddawane inspekcji, nawet jeśli inspekcja jest włączona w skrzynce pocztowej (właściwość *AuditEnabled* w skrzynce pocztowej ma **wartość True**).
- Inspekcja skrzynek pocztowych nie jest włączona dla nowych skrzynek pocztowych, a ustawienie właściwości *AuditEnabled* w nowej lub istniejącej skrzynce pocztowej na **wartość True** zostanie zignorowane.
- Wszystkie ustawienia skojarzenia pomijania inspekcji skrzynki pocztowej (skonfigurowane przy użyciu polecenia cmdlet **Set-MailboxAuditBypassAssociation** ) są ignorowane.
- Istniejące rekordy inspekcji skrzynki pocztowej są przechowywane do momentu wygaśnięcia limitu wieku dziennika inspekcji dla rekordu.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Domyślnie włącz inspekcję skrzynek pocztowych

Aby ponownie włączyć inspekcję skrzynki pocztowej dla organizacji, uruchom następujące polecenie w programie Exchange Online programu PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Pomijanie rejestrowania inspekcji skrzynki pocztowej

Obecnie nie można wyłączyć inspekcji skrzynek pocztowych dla określonych skrzynek pocztowych, gdy inspekcja skrzynek pocztowych jest domyślnie włączona w organizacji. Na przykład ustawienie właściwości *AuditEnabled* skrzynki pocztowej na **wartość False** jest ignorowane.

Jednak nadal możesz użyć polecenia cmdlet **Set-MailboxAuditBypassAssociation** w programie Exchange Online programu PowerShell, aby zapobiec zarejestrowaniu *wszystkich* akcji skrzynki pocztowej przez określonych użytkowników, niezależnie od tego, gdzie występują akcje. Przykład:

- Akcje właściciela skrzynki pocztowej wykonywane przez pominiętych użytkowników nie są rejestrowane.
- Akcje delegowania wykonywane przez pomijanych użytkowników w skrzynkach pocztowych innych użytkowników (w tym w udostępnionych skrzynkach pocztowych) nie są rejestrowane.
- Akcje administratora wykonywane przez pominiętych użytkowników nie są rejestrowane.

Aby pominąć rejestrowanie inspekcji skrzynki pocztowej dla określonego użytkownika, zastąp \<MailboxIdentity\> ciąg nazwą użytkownika, adresem e-mail, aliasem lub główną nazwą użytkownika (nazwą użytkownika) i uruchom następujące polecenie:

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Aby sprawdzić, czy inspekcja jest pomijana dla określonego użytkownika, uruchom następujące polecenie:

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

Wartość **True** wskazuje, że rejestrowanie inspekcji skrzynki pocztowej jest pomijane dla użytkownika.

## <a name="more-information"></a>Więcej informacji

- Mimo że domyślne logowanie inspekcji skrzynki pocztowej jest włączone dla wszystkich organizacji, tylko użytkownicy z licencjami E5 będą zwracać zdarzenia dziennika inspekcji skrzynki pocztowej w [przeszukiwaniu dzienników inspekcji w portalu zgodności usługi Microsoft Purview](search-the-audit-log-in-security-and-compliance.md) lub **domyślnie** za pośrednictwem [interfejsu API działania zarządzania Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

  Aby pobrać wpisy dziennika inspekcji skrzynki pocztowej dla użytkowników bez licencji E5/A5/G5, można użyć dowolnego z następujących obejść:

  - Ręcznie włącz inspekcję skrzynek pocztowych w poszczególnych skrzynkach pocztowych (uruchom polecenie `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true`). Po wykonaniu tej czynności możesz użyć przeszukiwania dzienników inspekcji w portalu zgodności usługi Microsoft Purview lub za pośrednictwem interfejsu API działania zarządzania Office 365.

    > [!NOTE]
    > Jeśli inspekcja skrzynki pocztowej jest już widoczna jako włączona w skrzynce pocztowej, ale wyszukiwanie nie zwraca żadnych wyników, zmień wartość parametru *AuditEnabled* na `$false` , a następnie z powrotem na `$true`.

  - Użyj następujących poleceń cmdlet w programie Exchange Online programu PowerShell:
    - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) , aby wyszukać dziennik inspekcji skrzynki pocztowej dla określonych użytkowników.
    - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) , aby wyszukać dziennik inspekcji skrzynki pocztowej dla określonych użytkowników i wysłać wyniki za pośrednictwem poczty e-mail do określonych adresatów.

  - Użyj centrum administracyjnego Exchange (EAC) w Exchange Online, aby wykonać następujące czynności:
    - [Eksportowanie dzienników inspekcji skrzynki pocztowej](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)
    - [Uruchamianie raportu dostępu do skrzynki pocztowej innej niż właściciel](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Domyślnie rekordy dziennika inspekcji skrzynki pocztowej są przechowywane przez 90 dni przed ich usunięciem. Limit wieku rekordów dziennika inspekcji można zmienić za pomocą parametru *AuditLogAgeLimit* w poleceniu cmdlet **Set-Mailbox** w programie Exchange Online programu PowerShell. Jednak zwiększenie tej wartości nie umożliwia wyszukiwania zdarzeń starszych niż 90 dni w dzienniku inspekcji.

  Jeśli zwiększysz limit wieku, musisz użyć polecenia cmdlet [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) w programie Exchange Online programu PowerShell, aby wyszukać w dzienniku inspekcji skrzynki pocztowej użytkownika rekordy starsze niż 90 dni.

- Jeśli właściwość *AuditLogAgeLimit* dla skrzynki pocztowej została zmieniona przed domyślnym włączeniem inspekcji skrzynki pocztowej dla organizacji, istniejący limit wieku dziennika inspekcji skrzynki pocztowej nie zostanie zmieniony. Innymi słowy, domyślnie inspekcja skrzynki pocztowej nie wpływa na bieżący limit wieku rekordów inspekcji skrzynki pocztowej.

- Aby zmienić wartość *AuditLogAgeLimit* w skrzynce pocztowej grupy Microsoft 365, należy uwzględnić `-GroupMailbox` przełącznik w poleceniu **Set-Mailbox**.

- Rekordy dziennika inspekcji skrzynki pocztowej są przechowywane w podfoldecie (o nazwie *Audits*) w folderze Elementy możliwe do odzyskania w skrzynce pocztowej każdego użytkownika. Należy pamiętać o następujących kwestiach dotyczących rekordów inspekcji skrzynki pocztowej i folderu Elementy możliwe do odzyskania:

  - Rekordy inspekcji skrzynki pocztowej są liczone względem limitu przydziału magazynu folderu Elementy możliwe do odzyskania, który domyślnie wynosi 30 GB (limit przydziału ostrzeżenia wynosi 20 GB). Limit przydziału magazynu jest automatycznie zwiększany do 100 GB (z limitem przydziału ostrzeżenia 90 GB), gdy:
    - Blokada jest umieszczana w skrzynce pocztowej.
    - Skrzynka pocztowa jest przypisana do zasad przechowywania w Centrum zgodności.

  - Rekordy inspekcji skrzynki pocztowej są również liczone względem [limitu folderu Elementy możliwe do odzyskania](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits). Maksymalnie 3 miliony elementów (rekordy inspekcji) można przechowywać w podfoldecie Inspekcje.

    > [!NOTE]
    > Jest mało prawdopodobne, że domyślnie inspekcja skrzynki pocztowej będzie mieć wpływ na limit przydziału magazynu lub limit folderu dla folderu Elementy możliwe do odzyskania.

    - W programie Exchange Online programu PowerShell można uruchomić następujące polecenie, aby wyświetlić rozmiar i liczbę elementów w podfoldecie Inspekcje w folderze Elementy możliwe do odzyskania:

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - Nie można bezpośrednio uzyskać dostępu do rekordu dziennika inspekcji w folderze Elementy możliwe do odzyskania; Zamiast tego należy użyć polecenia cmdlet **Search-MailboxAuditLog** lub przeszukać dziennik inspekcji, aby znaleźć i wyświetlić rekordy inspekcji skrzynki pocztowej.

- Jeśli skrzynka pocztowa zostanie wstrzymana lub przypisana do zasad przechowywania w Centrum zgodności, rekordy dziennika inspekcji będą przechowywane przez czas zdefiniowany przez właściwość *AuditLogAgeLimit* skrzynki pocztowej (domyślnie 90 dni). Aby dłużej przechowywać rekordy dziennika inspekcji dla skrzynek pocztowych, należy zwiększyć wartość *AuditLogAgeLimit* skrzynki pocztowej.

- W środowisku z wieloma obszarami geograficznymi inspekcja skrzynki pocztowej obejmującej wiele obszarów geograficznych nie jest obsługiwana. Jeśli na przykład użytkownik ma przypisane uprawnienia dostępu do udostępnionej skrzynki pocztowej w innej lokalizacji geograficznej, akcje skrzynki pocztowej wykonywane przez tego użytkownika nie są rejestrowane w dzienniku inspekcji skrzynki pocztowej udostępnionej skrzynki pocztowej. Exchange zdarzenia inspekcji administratora są obecnie dostępne tylko dla lokalizacji domyślnej.
