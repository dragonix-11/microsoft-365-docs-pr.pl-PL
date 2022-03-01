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
description: Rejestrowanie inspekcji skrzynki pocztowej jest domyślnie włączone w programie Microsoft 365 (jest to domyślnie nazywane domyślną inspekcją skrzynki pocztowej lub inspekcją skrzynki pocztowej). Oznacza to, że niektóre działania wykonywane przez właścicieli, pełnomocników i administratorów skrzynek pocztowych są automatycznie rejestrowane w dzienniku inspekcji skrzynki pocztowej, w którym można wyszukiwać działania wykonywane w skrzynce pocztowej.
ms.openlocfilehash: 957e0a00a480746d6a70bf70ee02d725f43194f8
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010440"
---
# <a name="manage-mailbox-auditing"></a>Zarządzanie inspekcją skrzynki pocztowej

Począwszy od stycznia 2019 r., firma Microsoft domyślnie włączona jest rejestrowanie inspekcji skrzynki pocztowej dla wszystkich organizacji. Oznacza to, że niektóre działania wykonywane przez właścicieli, pełnomocników i administratorów skrzynek pocztowych są rejestrowane automatycznie, a odpowiadające im rekordy inspekcji skrzynki pocztowej będą dostępne po wyszukaniu ich w dzienniku inspekcji skrzynki pocztowej. Przed domyślnym włączeniem inspekcji skrzynki pocztowej trzeba było ręcznie włączyć tę funkcję dla wszystkich skrzynek pocztowych użytkowników w organizacji.

Oto kilka zalet domyślnej inspekcji skrzynki pocztowej:

- Inspekcja jest włączana automatycznie podczas tworzenia nowej skrzynki pocztowej. Nie musisz ręcznie włączać tej funkcji dla nowych użytkowników.
- Nie musisz zarządzać akcjami skrzynki pocztowej, które są pod inspekcją. Wstępnie zdefiniowany zestaw akcji skrzynki pocztowej jest domyślnie inspekcji dla każdego typu logowania (Administrator, Pełnomocnik i Właściciel).
- Po wydaniu przez firmę Microsoft nowej akcji skrzynki pocztowej ta akcja może zostać automatycznie dodana do listy akcji skrzynki pocztowej, które są domyślnie poddawane inspekcji (pod warunkiem, że użytkownik ma odpowiednią licencję). Oznacza to, że nie musisz monitorować dodawania nowych akcji w skrzynkach pocztowych.
- W organizacji są spójne zasady inspekcji skrzynek pocztowych (ponieważ inspekcja ma takie same akcje dla wszystkich skrzynek pocztowych).

> [!NOTE]
>
> - Ważną rzeczą, o którą należy pamiętać domyślnie o wydaniu inspekcji skrzynki pocztowej jest to, że nie musisz nic robić, aby zarządzać inspekcją skrzynki pocztowej. Jednak ten artykuł może być pomocny, jeśli chcesz dowiedzieć się więcej, dostosować inspekcję skrzynki pocztowej przy pomocą ustawień domyślnych lub całkowicie ją wyłączyć.
> - Domyślnie w przeszukiwaniu dziennika inspekcji w programie Centrum zgodności platformy Microsoft 365 lub za pośrednictwem interfejsu API działań zarządzania Office 365 skrzynki pocztowej są dostępne tylko zdarzenia inspekcji skrzynki pocztowej dla użytkowników usługi E5. Aby uzyskać więcej informacji, zobacz [sekcję Więcej](#more-information) informacji w tym artykule.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Sprawdzanie, czy inspekcja skrzynek pocztowych jest domyślnie włączona

Aby sprawdzić, czy inspekcja skrzynek pocztowych jest domyślnie włączona w organizacji, uruchom następujące polecenie w [programie Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

Wartość **Fałsz** oznacza, że inspekcja skrzynek pocztowych jest domyślnie włączona dla organizacji. Ta opcja domyślnie zastępuje ustawienie inspekcji skrzynki pocztowej dla określonych skrzynek pocztowych. Jeśli na przykład inspekcja skrzynek pocztowych jest wyłączona dla skrzynki pocztowej (właściwość *AuditEnabled* dla skrzynki pocztowej ma wartość False), domyślne akcje skrzynki pocztowej nadal będą w tej skrzynce pocztowej inspekcją, ponieważ inspekcja skrzynek pocztowych jest domyślnie włączona dla organizacji.

Aby inspekcja skrzynek pocztowych była wyłączona dla określonych skrzynek pocztowych, należy skonfigurować obejście inspekcji skrzynki pocztowej dla właściciela skrzynki pocztowej i innych użytkowników, którym delegowano dostęp do skrzynki pocztowej. Aby uzyskać więcej informacji, zobacz sekcję [Pomijanie](#bypass-mailbox-audit-logging) rejestrowania inspekcji skrzynki pocztowej w tym artykule.

> [!NOTE]
> Jeśli inspekcja skrzynek pocztowych jest domyślnie włączona dla organizacji, właściwość *AuditEnabled* dla skrzynek pocztowych, których dotyczy problem, nie zostanie zmieniona z **Fałsz** na **Prawda**. Innymi słowy, inspekcja skrzynek pocztowych domyślnie ignoruje właściwość *AuditEnabled* w skrzynkach pocztowych.

## <a name="supported-mailbox-types"></a>Obsługiwane typy skrzynek pocztowych

W poniższej tabeli przedstawiono typy skrzynek pocztowych, które są obecnie obsługiwane przez inspekcję skrzynek pocztowych domyślnie:

<br>

****

|Typ skrzynki pocztowej|Obsługiwane|
|---|:---:|
|Skrzynki pocztowe użytkowników|![Znacznik wyboru.](../media/checkmark.png)|
|Udostępnione skrzynki pocztowe|![Znacznik wyboru.](../media/checkmark.png)|
|Microsoft 365 skrzynek pocztowych grupy|![Znacznik wyboru.](../media/checkmark.png)|
|Skrzynki pocztowe zasobów||
|Skrzynki pocztowe folderów publicznych||
|

## <a name="logon-types-and-mailbox-actions"></a>Typy logowania i akcje skrzynki pocztowej

Typy logowania sklasyfikują użytkownika, który poddał inspekcji akcje w skrzynce pocztowej. Na poniższej liście opisano typy logowania używane w rejestrowaniu inspekcji skrzynki pocztowej:

- **Właściciel**: właściciel skrzynki pocztowej (konto skojarzone ze skrzynką pocztową).
- **Pełnomocnik**:
  - Użytkownik, do którym przypisano uprawnienie SendAs, SendOnBehalf lub FullAccess do innej skrzynki pocztowej.
  - Administrator, który ma uprawnienie Pełny dostęp do skrzynki pocztowej użytkownika.
- **Administrator**:
  - Skrzynka pocztowa jest przeszukiwana przy użyciu jednego z następujących narzędzi zbierania elektronicznych materiałów dowodowych firmy Microsoft:
    - Wyszukiwanie zawartości w Centrum zgodności.
    - zbierania elektronicznych materiałów dowodowych Advanced eDiscovery w Centrum zgodności.
    - In-Place zbierania elektronicznych materiałów dowodowych w programie Exchange Online.
  - Do skrzynki pocztowej można uzyskać dostęp za pomocą Microsoft Exchange Server MAPI.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Akcje dotyczące skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych

W poniższej tabeli opisano akcje dotyczące skrzynek pocztowych dostępne w rejestrowaniu inspekcji skrzynki pocztowej dla skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych.

- Znacznik wyboru (![Znacznik wyboru.](../media/checkmark.png)) wskazuje, że czynność skrzynki pocztowej może zostać zarejestrowana dla typu logowania (nie wszystkie akcje są dostępne dla wszystkich typów logowania).
- Gwiazdka ( <sup>\*</sup> ) po znaczniku wyboru wskazuje, że akcja skrzynki pocztowej jest rejestrowana domyślnie dla typu logowania.
- Pamiętaj, że administrator z uprawnieniem pełnego dostępu do skrzynki pocztowej jest uznawany za pełnomocnika.

<br>

****

|Akcja Skrzynka pocztowa|Opis|Administrator|Pełnomocnik|Właściciel|
|---|---|:---:|:---:|:---:|
|**AddFolderPermissions**|Mimo że ta wartość jest akceptowana jako akcja skrzynki pocztowej, jest już uwzględniona w akcji **UpdateFolderPermissions** i nie jest osobno uwzględniana. Innymi słowy, nie używaj tej wartości.||||
|**ZastosujRekord**|Element jest oznaczony jako rekord.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|
|**Kopiuj**|Wiadomość została skopiowana do innego folderu.|![Znacznik wyboru.](../media/checkmark.png)|||
|**Tworzenie**|Utworzono element w folderze Kalendarz, Kontakty, Notatki lub Zadania w skrzynce pocztowej (na przykład utworzono nowe wezwanie na spotkanie). Tworzenie, wysyłanie ani odbieranie wiadomości nie jest inspekcją. Ponadto nie jest inspekcją tworzenia folderu skrzynki pocztowej.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)|
|**FolderBind**|Uzyskano dostęp do folderu skrzynki pocztowej. Ta akcja jest również rejestrowana, gdy administrator lub pełnomocnik otwiera skrzynkę pocztową. <br/><br/> **Uwaga**: Skonsolidowane zostaną rekordy inspekcji dotyczące działań powiązywania folderów wykonywanych przez pełnomocników. W ciągu 24 godzin dla dostępu do poszczególnych folderów jest generowany jeden rekord inspekcji.|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru.](../media/checkmark.png)||
|**HardDelete**|Wiadomość została przeczyszczona z folderu Elementy do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|Użytkownik zalogował się do swojej skrzynki pocztowej.|||![Znacznik wyboru](../media/checkmark.png)|
|**MailItemsAccessed**|**Uwaga**: Ta wartość jest dostępna tylko dla użytkowników subskrypcji na usługi zgodności E5 lub E5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie inspekcji zaawansowanej w programie Microsoft 365](set-up-advanced-audit.md). <p> Dostęp do danych poczty uzyskuje się za pośrednictwem protokołów poczty i klientów.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**MessageBind**|**Uwaga**: ta wartość jest dostępna tylko dla użytkowników E3 (użytkowników bez subskrypcji dodatków E5 lub E5 Compliance). <p> Wiadomość została wyświetlona w okienku podglądu lub otwarta przez administratora.|![Znacznik wyboru](../media/checkmark.png)|||
|**ModifyFolderPermissions**|Mimo że ta wartość jest akceptowana jako akcja skrzynki pocztowej, jest już uwzględniona w akcji **UpdateFolderPermissions** i nie jest osobno uwzględniana. Innymi słowy, nie używaj tej wartości.||||
|**Przenieś**|Wiadomość została przeniesiona do innego folderu.|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|
|**MoveToDeletedItems**|Wiadomość została usunięta i przeniesiona do folderu Elementy usunięte.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**RecordDelete**|Element oznaczony jako rekord został "miękkiego usunięcia" (przeniesiono do folderu Elementy do odzyskania). Elementów oznaczonych jako rekordy nie można trwale usuwać (usuwanych z folderu Elementy do odzyskania).|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|
|**RemoveFolderPermissions**|Mimo że ta wartość jest akceptowana jako akcja skrzynki pocztowej, jest już uwzględniona w akcji **UpdateFolderPermissions** i nie jest osobno uwzględniana. Innymi słowy, nie używaj tej wartości.||||
|**SearchQueryInitiated**|**Uwaga**: Ta wartość jest dostępna tylko dla użytkowników subskrypcji na usługi zgodności E5 lub E5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie inspekcji zaawansowanej w programie Microsoft 365](set-up-advanced-audit.md). <p> Użytkownik używa programu Outlook (Windows, Mac, iOS, Android Outlook w sieci Web) lub aplikacji Poczta dla systemu Windows 10 do wyszukiwania elementów w skrzynce pocztowej.|||![Znacznik wyboru](../media/checkmark.png)|
|**Wyślij**|**Uwaga**: Ta wartość jest dostępna tylko dla użytkowników subskrypcji na usługi zgodności E5 lub E5. Aby uzyskać więcej informacji, zobacz [Konfigurowanie inspekcji zaawansowanej w programie Microsoft 365](set-up-advanced-audit.md). <p> Użytkownik wysyła wiadomość e-mail, odpowiada na wiadomość e-mail lub przesyła dalej wiadomość e-mail.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>||![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Wiadomość została wysłana przy użyciu uprawnienia Wyślij jako. Oznacza to, że inny użytkownik wysłał tę wiadomość tak, jakby pochodziła od właściciela skrzynki pocztowej.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Wiadomość została wysłana przy użyciu uprawnienia Wyślij w imieniu. Oznacza to, że inny użytkownik wysłał tę wiadomość w imieniu właściciela skrzynki pocztowej. Ta wiadomość wskazuje adresata, w imieniu którym wysłano wiadomość, i kto faktycznie wysłał tę wiadomość.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Wiadomość została trwale usunięta lub usunięta z folderu Elementy usunięte. Elementy usunięte "miękkie" są przenoszone do folderu Elementy do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**Aktualizacja**|Zmieniono wiadomość lub dowolną z jej właściwości.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|Do skrzynki pocztowej przypisano delegowanie kalendarza. Delegowanie kalendarza nadaje innej osobie w tej samej organizacji uprawnienia do zarządzania kalendarzem właściciela skrzynki pocztowej.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>||![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Do elementu poczty jest stosowana inna etykieta przechowywania (do elementu może być przypisana tylko jedna etykieta przechowywania).|![Znacznik wyboru.](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|![Znacznik wyboru](../media/checkmark.png)|
|**UpdateFolderPermissions**|Uprawnienie folderu zostało zmienione. Uprawnienia folderów kontrolują, którzy użytkownicy w organizacji mogą uzyskać dostęp do folderów w skrzynce pocztowej oraz do wiadomości znajdujących się w tych folderach.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|Dodano, usunięto lub zmieniono regułę skrzynki odbiorczej. Reguły skrzynki odbiorczej są używane do przetwarzania wiadomości w Skrzynce odbiorczej użytkownika na podstawie określonych warunków i do podjęcia działań, gdy zostaną spełnione warunki reguły, takich jak przeniesienie wiadomości do określonego folderu lub usunięcie wiadomości.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|

> [!IMPORTANT]
> Jeśli dostosowano akcje skrzynki pocztowej do inspekcji dla dowolnego typu logowania, zanim inspekcja skrzynki pocztowej była domyślnie włączona w organizacji, dostosowane ustawienia są zachowywane w skrzynce pocztowej i nie są zastępowane domyślnymi akcjami skrzynki pocztowej zgodnie z opisem w tej sekcji. Aby przywrócić domyślne wartości akcji skrzynki pocztowej inspekcji (można to zrobić w dowolnym momencie), zobacz sekcję [](#restore-the-default-mailbox-actions) Przywracanie domyślnych akcji skrzynki pocztowej w dalszej części tego artykułu.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Akcje skrzynki pocztowej Microsoft 365 skrzynek pocztowych grupy

Domyślnie inspekcja skrzynki pocztowej powoduje, że rejestrowanie inspekcji skrzynki pocztowej jest Microsoft 365 skrzynkami pocztowymi grupy, ale nie można dostosowywać rejestrowanej zawartości (nie można dodawać ani usuwać akcji skrzynki pocztowej rejestrowanej dla żadnego typu logowania).

W poniższej tabeli opisano akcje skrzynki pocztowej, które są domyślnie rejestrowane Microsoft 365 skrzynek pocztowych grupy dla każdego typu logowania.

Pamiętaj, że administrator z uprawnieniem Pełny dostęp do skrzynki Microsoft 365 grupy jest uznawany za pełnomocnika.

<br>

****

|Akcja Skrzynka pocztowa|Opis|Administrator|Pełnomocnik|Właściciel|
|---|---|:---:|:---:|:---:|
|**Tworzenie**|Tworzenie elementu kalendarza. Tworzenie, wysyłanie ani odbieranie wiadomości nie jest inspekcją.|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|Wiadomość została przeczyszczona z folderu Elementy do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**MoveToDeletedItems**|Wiadomość została usunięta i przeniesiona do folderu Elementy usunięte.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|Wiadomość została wysłana przy użyciu uprawnienia Wyślij jako.|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Wiadomość została wysłana przy użyciu uprawnienia Wyślij w imieniu.|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>||
|**SoftDelete**|Wiadomość została trwale usunięta lub usunięta z folderu Elementy usunięte. Elementy usunięte "miękkie" są przenoszone do folderu Elementy do odzyskania.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|**Aktualizacja**|Zmieniono wiadomość lub dowolną jej właściwość.|![Znacznik wyboru.](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|![Znacznik wyboru](../media/checkmark.png)<sup>\*</sup>|
|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Sprawdzanie, czy dla każdego typu logowania rejestrowane są domyślne akcje skrzynki pocztowej

Domyślnie inspekcja skrzynki pocztowej dodaje nową właściwość *DefaultAuditSet* do wszystkich skrzynek pocztowych. Wartość tej właściwości wskazuje, czy domyślne akcje skrzynki pocztowej (zarządzane przez firmę Microsoft) są w tej skrzynce pocztowej sprawdzane.

Aby wyświetlić wartość w skrzynkach pocztowych użytkowników lub udostępnionych skrzynkach pocztowych, \<MailboxIdentity\> zastąp je nazwą, aliasem, adresem e-mail lub główną nazwą użytkownika (nazwa użytkownika) skrzynki pocztowej i uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

Aby wyświetlić wartość na Microsoft 365 grupy, \<MailboxIdentity\> zamień ją na nazwę, alias lub adres e-mail udostępnionej skrzynki pocztowej i uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

Wartość wskazuje `Admin, Delegate, Owner` :

- Inspekcją są domyślnie akcje skrzynki pocztowej dla wszystkich trzech typów logowania. Jest to jedyna wartość, która jest Microsoft 365 skrzynkach pocztowych grupy.
- Administrator nie *zmienił działań w skrzynce* pocztowej, dla których nie zmieniono żadnego typu logowania w skrzynce pocztowej użytkownika lub udostępnionej skrzynce pocztowej. Zwróć uwagę, że po włączeniu domyślnej inspekcji skrzynki pocztowej jest ona domyślnie włączona w organizacji.

Jeśli administrator kiedykolwiek zmienił akcje skrzynki pocztowej, które są pod kontrolą pod uwagę w przypadku typu logowania (przy użyciu parametrów *AuditAdmin*, *AuditDelegate* lub *AuditOwner* dla polecenia cmdlet **Set-Mailbox** ), wartość właściwości będzie inna.

Na przykład wartość właściwości `Owner` *DefaultAuditSet* dla skrzynki pocztowej użytkownika lub udostępnionej skrzynki pocztowej wskazuje:

- Inspekcją są domyślnie podejmowane akcje skrzynki pocztowej właściciela skrzynki pocztowej.
- Akcje skrzynki pocztowej inspekcji dla typów `Delegate` `Admin` logowania i zostały zmienione w porównaniu z akcjami domyślnymi.

Pusta wartość właściwości *DefaultAuditSet* wskazuje, że akcje skrzynki pocztowej dla wszystkich trzech typów logowania zostały zmienione w skrzynce pocztowej użytkownika lub udostępnionej skrzynce pocztowej.

Aby uzyskać więcej informacji, zobacz sekcję Zmienianie lub przywracanie akcji skrzynki pocztowej [rejestrowanych](#change-or-restore-mailbox-actions-logged-by-default) domyślnie w tym artykule.

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Wyświetlanie akcji skrzynki pocztowej, które są zalogowane do skrzynek pocztowych

Aby wyświetlić akcje skrzynki pocztowej, które są obecnie zalogowane do skrzynek pocztowych użytkowników lub udostępnionych skrzynek pocztowych, \<MailboxIdentity\> zastąp je nazwą, aliasem, adresem e-mail lub główną nazwą użytkownika (nazwa użytkownika) skrzynki pocztowej, a następnie uruchom co najmniej jedno z następujących poleceń w programie Exchange Online PowerShell.

> [!NOTE]
> Przełącznik można dodać do następujących `-GroupMailbox` poleceń **Get-Mailbox** dla skrzynek pocztowych grupy Microsoft 365, ale nie należy chcieć, aby zwracane wartości zostały zwrócone. Domyślne i statyczne akcje skrzynek pocztowych, które są Microsoft 365 w skrzynkach pocztowych grupy są opisane w sekcji Akcje [](#mailbox-actions-for-microsoft-365-group-mailboxes) skrzynki pocztowej dla skrzynek pocztowych grupy Microsoft 365 we wcześniejszej części tego artykułu.

#### <a name="owner-actions"></a>Akcje właściciela

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditOwner
```

#### <a name="delegate-actions"></a>Akcje pełnomocnika

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditDelegate
```

#### <a name="admin-actions"></a>Akcje administratora

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditAdmin
```

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Zmienianie lub przywracanie rejestrowanych domyślnie akcji skrzynki pocztowej

Jak wyjaśniono wcześniej, jedną z kluczowych zalet domyślnego stosowania inspekcji skrzynki pocztowej jest: nie musisz zarządzać akcjami skrzynki pocztowej, które są pod inspekcją. Firma Microsoft zrobi to za Ciebie i automatycznie dodamy nowe akcje skrzynki pocztowej do domyślnej inspekcji w trakcie ich wydań.

Jednak organizacja może być wymagana do inspekcji innego zestawu akcji skrzynki pocztowej dla skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych. Procedury w tej sekcji pokazują, jak zmienić akcje skrzynki pocztowej, które są pod kontrolą dla każdego typu logowania, oraz jak przywrócić domyślne akcje zarządzane przez firmę Microsoft.

> [!IMPORTANT]
> Jeśli użyjesz poniższych procedur w celu dostosowania akcji skrzynki pocztowej zalogowanych do skrzynek pocztowych użytkowników lub udostępnionych skrzynek pocztowych, nowe domyślne akcje dotyczące skrzynek pocztowych publikowane przez firmę Microsoft nie będą automatycznie rejestrowane w tych skrzynkach pocztowych. Konieczne będzie ręczne dodanie nowych akcji skrzynki pocztowej do dostosowanej listy akcji.

### <a name="change-the-mailbox-actions-to-audit"></a>Zmienianie akcji skrzynki pocztowej na inspekcję

Za pomocą parametrów *AuditAdmin*, *AuditDelegate* lub *AuditOwner* w poleceniu cmdlet **Set-Mailbox** możesz zmienić akcje skrzynki pocztowej, które są pod inspekcji dotyczące skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych użytkowników (nie można dostosowywać akcji inspekcji skrzynek pocztowych grupy programu Microsoft 365).

Możesz użyć dwóch różnych metod określania akcji skrzynki pocztowej:

- *Zastąp* (zastąp) istniejące akcje skrzynki pocztowej, używając następującej składni: `action1,action2,...actionN`.
- *Dodaj lub usuń akcje skrzynki* pocztowej bez wpływu na inne istniejące wartości, używając tej składni: `@{Add="action1","action2",..."actionN"}` lub `@{Remove="action1","action2",..."actionN"}`.

W tym przykładzie akcje administracyjne skrzynki pocztowej o nazwie "Laureano" administratorów skrzynki pocztowej otrzymały nazwę "Laureano", które domyślnie mają być akcje SoftDelete i HardDelete.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

W tym przykładzie do skrzynki pocztowej jest dodano akcję Właściciela skrzynki pocztowejLogin laura@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

W tym przykładzie usuwa akcję pełnomocnika MoveToDeletedItems dla skrzynki pocztowej Dyskusja zespołu.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Bez względu na używaną metodę dostosowywanie akcji skrzynki pocztowej inspekcji w skrzynkach pocztowych użytkowników lub udostępnionych skrzynkach pocztowych ma następujące wyniki:

- W przypadku dostosowanego typu logowania firma Microsoft nie zarządza już akcjami skrzynki pocztowej inspekcji.
- Dostosowany typ logowania nie jest już wyświetlany w wartości właściwości *DefaultAuditSet* skrzynki pocztowej zgodnie z wcześniejszym [opisem](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type).

### <a name="restore-the-default-mailbox-actions"></a>Przywracanie domyślnych akcji skrzynki pocztowej

> [!NOTE]
> Poniższe procedury nie dotyczą skrzynek pocztowych Microsoft 365 grup (są one ograniczone do akcji domyślnych opisanych [tutaj](#mailbox-actions-for-microsoft-365-group-mailboxes)).

Jeśli dostosowano akcje skrzynki pocztowej, które są inspekcji w skrzynce pocztowej użytkownika lub udostępnionej skrzynce pocztowej, możesz przywrócić domyślne akcje skrzynki pocztowej dla jednego lub wszystkich typów logowania, używając następującej składni:

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Możesz określić wiele wartości *DefaultAuditSet rozdzielonych* przecinkami

W tym przykładzie przywrócono domyślne akcje skrzynki pocztowej, które są pod kontrolą dla wszystkich typów logowania na mark@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

W tym przykładzie przywrócono domyślne akcje skrzynki pocztowej inspekcji dla typu logowania Administrator w skrzynce chris@contoso.onmicrosoft.com, ale pozostawia dostosowane akcje skrzynki pocztowej dla typów logowania Pełnomocnik i Właściciel.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

Aby przywrócić domyślne akcje skrzynki pocztowej zweryfikowane jako typ logowania, można uzyskać następujące wyniki:

- Bieżąca lista akcji skrzynki pocztowej zostanie zastąpiona domyślnymi akcjami skrzynki pocztowej dla tego typu logowania.
- Wszystkie nowe akcje skrzynki pocztowej publikowane przez firmę Microsoft są automatycznie dodawane do listy inspekcji akcji dla tego typu logowania.
- Wartość *właściwości DefaultAuditSet* skrzynki pocztowej zostanie zaktualizowana, aby uwzględniała przywrócony typ logowania.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Domyślne włączanie inspekcji skrzynki pocztowej dla organizacji

Inspekcję skrzynki pocztowej można wyłączyć domyślnie dla całej organizacji, uruchamiając następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

Domyślnie wyłączenie inspekcji skrzynki pocztowej powoduje następujące wyniki:

- Inspekcja skrzynek pocztowych jest wyłączona w Twojej organizacji.
- Od czasu wyłączenia inspekcji skrzynki pocztowej domyślnie żadne akcje skrzynki pocztowej nie są inspekcje, nawet jeśli w skrzynce pocztowej włączono inspekcję (właściwość *AuditEnabled* tej skrzynki pocztowej ma wartość **True**).
- Inspekcja skrzynek pocztowych nie jest włączona dla nowych skrzynek pocztowych, a ustawienie właściwości *AuditEnabled* dla nowej lub istniejącej skrzynki pocztowej na wartość **True** zostanie zignorowane.
- Wszelkie ustawienia skojarzenia obejść skojarzenia z pominięciem inspekcji skrzynki pocztowej (skonfigurowane przy użyciu polecenia cmdlet **Set-MailboxAuditBypassAssociation** ) są ignorowane.
- Istniejące rekordy inspekcji skrzynki pocztowej są zachowywane do momentu wygaśnięcia limitu wieku dziennika inspekcji dla rekordu.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Domyślne włączanie inspekcji skrzynki pocztowej

Aby ponownie włączyć inspekcję skrzynki pocztowej dla organizacji, uruchom następujące polecenie w programie Exchange Online PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Pomijanie rejestrowania inspekcji skrzynki pocztowej

Obecnie nie można wyłączyć inspekcji skrzynek pocztowych dla określonych skrzynek pocztowych, jeśli inspekcja skrzynek pocztowych jest domyślnie włączona w organizacji. Na przykład ustawienie właściwości *skrzynki pocztowej AuditEnabled* na **False jest** ignorowane.

Jednak nadal możesz użyć polecenia cmdlet **Set-MailboxAuditBypassAssociation** w programie Exchange Online PowerShell, aby uniemożliwić  rejestrowane dowolne i wszystkie akcje skrzynki pocztowej przez określonych użytkowników, niezależnie od miejsca wystąpienia akcji. Przykład:

- Akcje właściciela skrzynki pocztowej wykonywane przez użytkowników pomijanych nie są rejestrowane.
- Akcje pełnomocników wykonywane przez użytkowników pomijanych w skrzynkach pocztowych innych użytkowników (w tym udostępnionych skrzynkach pocztowych) nie są rejestrowane.
- Czynności administracyjne wykonywane przez użytkowników pomijanych nie są rejestrowane.

Aby pominąć rejestrowanie inspekcji skrzynki pocztowej dla określonego użytkownika, \<MailboxIdentity\> zastąp go nazwą, adresem e-mail, aliasem lub główną nazwą użytkownika (nazwa użytkownika) i uruchom następujące polecenie:

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Aby sprawdzić, czy inspekcja jest pomijana dla określonego użytkownika, uruchom następujące polecenie:

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

Wartość Prawda **oznacza** , że rejestrowanie inspekcji skrzynki pocztowej użytkownika jest pomijane.

## <a name="more-information"></a>Więcej informacji

- Mimo że rejestrowanie inspekcji skrzynki pocztowej domyślnie jest włączone dla wszystkich organizacji, tylko użytkownicy z licencjami E5 domyślnie zwracają zdarzenia dziennika inspekcji skrzynki pocztowej w przeszukiwaniu dziennika inspekcji w programie [Centrum zgodności platformy Microsoft 365](search-the-audit-log-in-security-and-compliance.md) lub za pomocą interfejsu [API](/office/office-365-management-api/office-365-management-activity-api-reference) działań zarządzania **Office 365.**

  Aby pobrać wpisy dziennika inspekcji skrzynki pocztowej dla użytkowników bez licencji E5, możesz:

  - Ręczne włączanie inspekcji skrzynki pocztowej dla poszczególnych skrzynek pocztowych (uruchom to polecenie, `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true`). Po jej zakończeniu możesz korzystać z przeszukiwania dziennika inspekcji w Centrum zgodności platformy Microsoft 365 lub za pomocą interfejsu API działań zarządzania Office 365 zarządzaniem.

    > [!NOTE]
    > Jeśli inspekcja skrzynki pocztowej wydaje się już włączona w skrzynce pocztowej, ale w wynikach wyszukiwania nie są zwracane żadne wyniki, zmień wartość parametru _AuditEnabled na wartość parametru AuditEnabled_`$false`, a następnie z powrotem na `$true`.

  - Użyj następujących poleceń cmdlet w programie Exchange Online PowerShell:
    - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) , aby przeszukać dziennik inspekcji skrzynki pocztowej dla określonych użytkowników.
    - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) to search the mailbox audit log for specific users and have the results sent via email to specified recipients.

  - W centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego w programie</a> Exchange Online wykonaj następujące czynności:
    - [Eksportowanie dzienników inspekcji skrzynki pocztowej](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)
    - [Uruchamianie raportu o dostępie do skrzynki pocztowej bez właściciela](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Domyślnie rekordy dziennika inspekcji skrzynki pocztowej są zachowywane przez 90 dni przed ich usunięciem. Limit wieku rekordów dziennika inspekcji można zmienić, używając parametru *AuditLogAgeLimit* polecenia cmdlet **Set-Mailbox** w programie Exchange Online PowerShell. Jednak zwiększenie tej wartości nie umożliwia wyszukiwania w dzienniku inspekcji zdarzeń starszych niż 90 dni.

  Jeśli zwiększysz limit wieku, musisz użyć polecenia cmdlet [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) w programie Exchange Online PowerShell, aby przeszukać dziennik inspekcji skrzynki pocztowej użytkownika w poszukiwaniu rekordów starszych niż 90 dni.

- Jeśli zmieniono właściwość *AuditLogAgeLimit* skrzynki pocztowej przed rozpoczęciem inspekcji skrzynki pocztowej, która jest domyślnie włączona dla organizacji, nie zostanie zmieniony istniejący limit wieku dziennika inspekcji skrzynki pocztowej. Oznacza to, że domyślnie inspekcja skrzynek pocztowych nie ma wpływu na bieżący limit wieku rekordów inspekcji skrzynki pocztowej.

- Aby zmienić wartość *ustawienia AuditLogAgeLimit* w skrzynce pocztowej grupy Microsoft 365, `-GroupMailbox` należy uwzględnić przełącznik w **poleceniu Set-Mailbox**.

- Rekordy dziennika inspekcji skrzynki pocztowej są przechowywane w podfolderze (o nazwie *Inspekcje*) w folderze Elementy odzyskiwalne w skrzynce pocztowej każdego użytkownika. Pamiętaj o następujących kwestiach dotyczących rekordów inspekcji skrzynki pocztowej i folderu Elementy do odzyskania:

  - Rekordy inspekcji skrzynki pocztowej są wliczane do przydziału miejsca do magazynowania folderu Elementy do odzyskania, który domyślnie wynosi 30 GB (przydział ostrzeżenia wynosi 20 GB). Przydział miejsca do magazynowania zostanie automatycznie zwiększony do 100 GB (z przydziałem ostrzegawczym 90 GB) w przypadku:
    - Skrzynka pocztowa jest umieszczana w miejscu.
    - Skrzynka pocztowa zostanie przypisana do zasad przechowywania w Centrum zgodności.

  - Rekordy inspekcji skrzynki pocztowej także są [wliczane do limitu folderów folderu Elementy do odzyskania](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits). W podfolderze Inspekcje można przechowywać maksymalnie 3 miliony elementów (rekordów inspekcji).

    > [!NOTE]
    > Jest mało prawdopodobne, że inspekcja skrzynek pocztowych domyślnie będzie mieć wpływ na przydział magazynowania lub limit folderów folderu Elementy do odzyskania.

    - W programie PowerShell Exchange Online uruchomić następujące polecenie, aby wyświetlić rozmiar i liczbę elementów w podfolderze Inspekcje w folderze Elementy do odzyskania:

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - W folderze Elementy do odzyskania nie można bezpośrednio uzyskać dostępu do rekordu dziennika inspekcji. Zamiast tego możesz użyć polecenia cmdlet **Search-MailboxAuditLog** lub przeszukać dziennik inspekcji w celu znalezienia i wyświetlenia rekordów inspekcji skrzynki pocztowej.

- Jeśli skrzynka pocztowa została umieszczona w stanie przechowywania lub przypisana do zasad przechowywania w Centrum zgodności, rekordy dziennika inspekcji są zachowywane przez czas określony przez właściwość *AuditLogAgeLimit* skrzynki pocztowej (domyślnie 90 dni). Aby zachować rekordy dziennika inspekcji dłużej dla skrzynek pocztowych w hold, musisz zwiększyć wartość *auditLogAgeLimit* skrzynki pocztowej.

- W środowisku z wieloma lokalizacjami geograficznymi inspekcja skrzynek pocztowych między geolokalizacji nie jest obsługiwana. Jeśli na przykład użytkownikowi przypisano uprawnienia dostępu do udostępnionej skrzynki pocztowej w innej lokalizacji geograficznej, akcje skrzynki pocztowej wykonywane przez tego użytkownika nie są rejestrowane w dzienniku inspekcji skrzynki pocztowej udostępnionej skrzynki pocztowej. Exchange inspekcji administratora są obecnie dostępne tylko dla lokalizacji domyślnej.
