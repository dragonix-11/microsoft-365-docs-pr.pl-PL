---
title: Wyślij powiadomienia e-mail i pokaż porady dotyczące zasad dla zasad DLP
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleNotifyUser
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Dowiedz się, jak dodać poradę o zasadach do zasad ochrony przed utratą danych (DLP, Data Loss Prevention), aby poinformować użytkownika, że pracuje z zawartością, która powoduje konflikt z zasadami DLP.
ms.openlocfilehash: 793ae9410ff40d989fffa4dfeae457ff0e61e392
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021331"
---
# <a name="send-email-notifications-and-show-policy-tips-for-dlp-policies"></a>Wyślij powiadomienia e-mail i pokaż porady dotyczące zasad dla zasad DLP

Przy użyciu zasad ochrony przed utratą danych (DLP, data loss prevention) możesz identyfikować, monitorować i chronić informacje poufne w różnych Office 365. Chcesz, aby osoby w Twojej organizacji, które pracują z tym poufnymi informacjami, zachować zgodność z zasadami DLP, ale nie chcesz niepotrzebnie blokować im pracy wykonywanej przez te osoby. W tym miejscu mogą pomóc powiadomienia e-mail i porady dotyczące zasad.

![Pasek komunikatów z poradami Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Podczas tworzenia zasad DLP w Centrum zgodności można skonfigurować powiadomienia użytkowników w taki sposób, aby:

- Wyślij wiadomość e-mail z powiadomieniem do osób, które opisują problem.

- Wyświetlanie porady dotyczącej zasad dla zawartości, która powoduje konflikt z zasadami DLP:

  - W przypadku poczty e-mail w Outlook w sieci Web i Outlook 2013 lub nowszej porada o zasadach jest wyświetlana u góry wiadomości nad adresatami podczas jej sporządzania.

  - W przypadku dokumentów OneDrive dla Firm lub SharePoint Online porada o zasadach jest wskazywana przez ikonę ostrzeżenia, która pojawia się na pozycji. Aby wyświetlić więcej informacji, możesz zaznaczyć element, a następnie wybrać **ikonę okienka** ![Informacje.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) w prawym górnym rogu strony, aby otworzyć okienko szczegółów.

  - W przypadku dokumentów Excel, PowerPoint i Word przechowywanych w witrynie programu OneDrive dla Firm lub witrynie SharePoint Online zawartej w zasadach DLP porada jest wyświetlana na pasku komunikatów i w widoku Backstage (**Informacje** menu \> **Plik**).

## <a name="add-user-notifications-to-a-dlp-policy"></a>Dodawanie powiadomień użytkowników do zasad DLP

Po utworzeniu zasad DLP możesz włączyć powiadomienia **użytkowników**. Gdy powiadomienia użytkownika są włączone, funkcja Microsoft 365 wysyła zarówno powiadomienia e-mail, jak i porady dotyczące zasad. Możesz określić, do kogo są wysyłane powiadomienia e-mail, tekst wiadomości e-mail i tekst porady dotyczącej zasad.

1. Przejdź do [https://(https://compliance.microsoft.com/permissions](https://(https://compliance.microsoft.com/permissions).

2. Zaloguj się przy użyciu konta służbowego. Jesteś teraz w Centrum zgodności &amp; zabezpieczeń.

3. W Centrum zgodności zabezpieczeń &amp; po \> lewej stronie nawigacji \> **Zasady ochrony przed utratą** \> **danych** \> **+ Utwórz zasady**.

    ![Przycisk Utwórz zasady.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)

4. Wybierz szablon zasad DLP, który chroni typy informacji poufnych, **których potrzebujesz dalej**\>.

    Aby rozpocząć od pustego szablonu, wybierz pozycję **Niestandardowe** \> **zasady niestandardowe dalej**\>.

5. Nadaj zasadom nazwę \> **Dalej**.

6. Aby wybrać lokalizacje, które mają być chronine przez zasady DLP, wykonaj jedną z następujących czynności:

   - Wybierz **pozycję Wszystkie lokalizacje w Office 365** \> **Dalej**.

   - Wybierz **pozycję Pozwól mi wybrać konkretne lokalizacje** \> **Dalej**.

   Aby uwzględnić lub wykluczyć całą lokalizację, taką jak Exchange e-mail lub wszystkie konta OneDrive, włącz lub wyłącz  stan tej lokalizacji.

   Aby uwzględnić tylko określone SharePoint witryn lub kont OneDrive, przełącz opcję **Status** na wł., a następnie kliknij linki w obszarze Dołącz, aby  wybrać określone witryny lub konta.

7. Wybierz **pozycję Użyj ustawień zaawansowanych Dalej**\>.

8. Wybierz **pozycję + Nowa reguła**.

9. W edytorze reguł w obszarze **Powiadomienia użytkownika** włącz status.

    ![Sekcja powiadomień użytkownika w edytorze reguł.](../media/47705927-c60b-4054-a072-ab914f33d15d.png)

> [!NOTE]
> Powiadomienia e-mail są wysyłane bez ochrony.

## <a name="options-for-configuring-email-notifications"></a>Opcje konfigurowania powiadomień e-mail

Dla każdej reguły zasad DLP możesz:

- Wyślij powiadomienie do osób, które wybierzesz. Mogą to być między innymi właściciel zawartości, osoba, która jako ostatnia zmodyfikował zawartość, właściciel witryny, w której jest przechowywana zawartość, lub określony użytkownik.

- Dostosuj tekst zawarty w powiadomieniu przy użyciu kodu HTML lub tokenów. Aby uzyskać więcej informacji, zobacz sekcję poniżej.

> [!NOTE]
>  Powiadomienia e-mail mogą być wysyłane tylko do poszczególnych adresatów — nie do grup ani list dystrybucyjnych. Tylko nowa zawartość będzie wyzwalać powiadomienie e-mail. Edytowanie istniejącej zawartości powoduje wyzwolenie porad dotyczących zasad, ale nie powiadomienia e-mail.

![Opcje powiadomień e-mail.](../media/4e7b9500-2a78-44e6-9067-09f4bfd50301.png)

### <a name="default-email-notification"></a>Domyślne powiadomienie e-mail

Powiadomienia mają wiersz tematu, który rozpoczyna się od wykonanej akcji, na przykład "Powiadomienie", "Wiadomość zablokowana" w przypadku wiadomości e-mail lub "Zablokowano dostęp" w przypadku dokumentów. Jeśli powiadomienie dotyczy dokumentu, w treści komunikat z powiadomieniem znajduje się link, który przenosi Cię do witryny, w której jest przechowywany dokument, i otwiera poradę o zasadach dla dokumentu, gdzie możesz rozwiązać wszelkie problemy (zobacz sekcję poniżej o poradach dotyczących zasad). Jeśli powiadomienie dotyczy wiadomości, powiadomienie zawiera jako załącznik wiadomość, która jest zgodnie z zasadami DLP.

![Komunikat z powiadomieniem.](../media/35813d40-5fd8-425f-9624-55655e74fa6b.png)

Domyślnie powiadomienia wyświetlają tekst podobny do poniższego w przypadku elementu w witrynie. Tekst powiadomienia jest konfigurowany oddzielnie dla każdej reguły, więc wyświetlany tekst różni się w zależności od tego, która reguła jest do nich dopasowana.

|**Jeśli reguła zasad DLP działa tak...**|**Z domyślnym powiadomieniem dla SharePoint lub OneDrive dla Firm jest to...**|**Następnie domyślne powiadomienie dotyczące wiadomości Outlook informuje, że...**|
|:-----|:-----|:-----|
|Wysyła powiadomienie, ale nie zezwala na zastępowanie  <br/> |Ten element powoduje konflikt z zasadami w organizacji.  <br/> |Twoja wiadomość e-mail powoduje konflikty z zasadami w Twojej organizacji.  <br/> |
|Blokuje dostęp, wysyła powiadomienie i zezwala na zastępowanie  <br/> |Ten element powoduje konflikt z zasadami w organizacji. Jeśli nie rozwiążesz tego konfliktu, dostęp do tego pliku może być zablokowany.  <br/> |Twoja wiadomość e-mail powoduje konflikty z zasadami w Twojej organizacji. Wiadomość nie została dostarczona do wszystkich adresatów.  <br/> |
|Blokuje dostęp i wysyła powiadomienie  <br/> |Ten element powoduje konflikt z zasadami w organizacji. Dostęp do tego elementu jest zablokowany dla wszystkich oprócz właściciela, ostatniego modyfikatora i głównego administratora zbioru witryn.  <br/> |Twoja wiadomość e-mail powoduje konflikty z zasadami w Twojej organizacji. Wiadomość nie została dostarczona do wszystkich adresatów.  <br/> |

### <a name="custom-email-notification"></a>Niestandardowe powiadomienie e-mail

Możesz utworzyć niestandardowe powiadomienie e-mail zamiast wysyłać domyślne powiadomienie e-mail do użytkowników końcowych lub administratorów. Niestandardowe powiadomienie e-mail obsługuje format HTML i ma limit 5000 znaków. Kod HTML umożliwia dołączanie do powiadomienia obrazów, formatowania i innych elementów marki.

Możesz także użyć następujących tokenów, aby dostosować powiadomienie e-mail. Te tokeny to zmienne, które są zamieniane na określone informacje w wysyłanym powiadomieniu.

|**Token**|**Opis**|
|:-----|:-----|
|%%AppliedActions%%  <br/> |Akcje zastosowane do zawartości.  <br/> |
|%%ContentURL%%  <br/> |Adres URL dokumentu w witrynie SharePoint Online lub OneDrive dla Firm sieci Web.  <br/> |
|%%MatchedConditions%%  <br/> |Warunki, które zostały spełnione przez zawartość. Użyj tego tokenu, aby poinformować użytkowników o możliwych problemach z zawartością.  <br/> |

![Komunikat z powiadomieniem o miejscu wyświetlania tokenów.](../media/cd3f36b3-40db-4f30-99e4-190750bd1955.png)

## <a name="options-for-configuring-policy-tips"></a>Opcje konfigurowania porad dotyczących zasad

Dla każdej reguły w zasadach DLP możesz skonfigurować porady dotyczące zasad, aby:

- Po prostu powiadom osobę, że zawartość powoduje konflikt z zasadami DLP, aby ta osoba może podjąć działania w celu rozwiązania konfliktu. Możesz użyć tekstu domyślnego (patrz poniższe tabele) lub wprowadzić tekst niestandardowy na temat zasad danej organizacji.

- Zezwalaj tej osobie na zastępowanie zasad DLP. Opcjonalnie możesz:

  - Wymagaj od tej osoby wprowadzenia uzasadnienia biznesowego w celu zastępowania zasad. Te informacje są rejestrowane i możesz je wyświetlić w raportach ochrony przed zagrożeniami DLP **w sekcji** Raporty w Centrum &amp; zgodności zabezpieczeń.

  - Zezwalaj tej osobie na zgłaszanie wyników fałszywie dodatnich i zastępowanie zasad DLP. Te informacje są również rejestrowane do celów raportowania, dzięki czemu można precyzyjnie dostosować reguły za pomocą wyników fałszywie dodatnich.

![Opcje porad dotyczące zasad.](../media/0d2f2c68-028a-4900-afe6-1d9fce5303ef.png)

Na przykład do witryn internetowych mogą być stosowane zasady D OneDrive dla Firm LP wykrywace informacje umożliwiające identyfikację użytkownika (PII) oraz trzy reguły:

1. Pierwsza reguła: Jeśli w dokumencie zostanie wykrytych mniej niż pięć wystąpień tych poufnych informacji, **a** dokument zostanie udostępniony osobom w organizacji, akcja Wyślij powiadomienie wyświetli poradę o zasadach. Porady dotyczące zasad nie są konieczne, ponieważ ta reguła oznacza po prostu powiadamianie osób i blokowanie dostępu.

2. Druga reguła: Jeśli w dokumencie zostanie wykrytych więcej niż pięć wystąpień tych poufnych informacji, a dokument zostanie udostępniony osobom w organizacji, akcja Zablokuj dostęp  do zawartości ogranicza uprawnienia do pliku, **a** akcja Wyślij powiadomienie umożliwia użytkownikom zastępowanie akcji czynów tej reguły przez podanie uzasadnienia biznesowego. Twoja firma czasami wymaga udostępniania danych PII przez osoby wewnętrzne i nie chcesz, aby zasady DLP blokowały tę pracę.

3. Trzecia reguła: Jeśli w dokumencie zostanie wykrytych więcej niż pięć wystąpień tych poufnych informacji, a dokument zostanie udostępniony osobom spoza organizacji, akcja Zablokuj dostęp  do zawartości ogranicza uprawnienia do pliku, **a** akcja Wyślij powiadomienie nie umożliwia użytkownikom zastępowania akcji tej reguły, ponieważ informacje są udostępniane zewnętrznie. W żadnym wypadku osoby w Twojej organizacji nie mogą udostępniać danych pii poza organizacją.

### <a name="user-override-support"></a>Obsługa zastępowania użytkowników

Poniżej podano kilka drobnych informacji dotyczących zastępowania reguły za pomocą porad dotyczących zasad:

- Opcja zastępowania jest dla reguły i zastępuje wszystkie jej akcje (oprócz wysyłania powiadomienia, którego nie można zastąpić).

- Możliwe jest, że zawartość będzie odpowiadać kilku regułom w zasadach DLP, ale będzie wyświetlana tylko porada z zasad najbardziej restrykcyjnych i o najwyższym priorytecie. Na przykład porada policyjna od reguły, która blokuje dostęp do zawartości, będzie wyświetlana na poradzie dotyczącej zasad od reguły, która po prostu wyśle powiadomienie. Zapobiega to kaskadowemu tworzeniu się porad dotyczących zasad.

- Jeśli porady dotyczące zasad w najbardziej restrykcyjnej  regułie umożliwiają użytkownikom zastępowanie tej reguły, zastąpienie tej reguły zastępuje również wszystkie inne reguły, które pasują do zawartości.

- Jeśli akcja NotifyAllowOverride jest ustawiona na wartość WithoutJustification albo WithJustification lub FlasePositives, upewnij się, że dla ustawienia BlockAccess jest ustawiona wartość true, a dla funkcji BlockAccessScope jest odpowiednia wartość. W przeciwnym razie pojawi się porada zasad, ale użytkownik nie znajdzie opcji zastąpienia wiadomości e-mail na uzasadnienie.

#### <a name="availability-of-override"></a>Dostępność zastępowania

|Reguła powiadomień |Akcja powiadamiania/blokowania  |Dostępne zastępowanie  |Wymagaj uzasadnienia  |
|---------|---------|---------|---------|
|Tylko powiadomienia     |Powiadom         |Nie         |Nie         |
|Notify + AllowOverride     |Powiadom         |Nie         |Nie         |
|Notify + AllowOverride + False positive     |Powiadom         |Nie         |Nie         |
|Powiadom + AllowOverride + Z justowanie     |Powiadom         |Nie         |Nie         |
|Powiadom + AllowOverride + False positive + Bez justowania    |Powiadom         |Nie         |Nie         |
|Notify + AllowOverride + False positive + With justification     |Powiadom         |Nie         |Nie         |
|Powiadom + Zablokuj     |Blokuj         |Nie         |Nie         |
|Notify + Block + AllowOverride     |Blokuj         |Tak         |Nie         |
|Notify + Block + AllowOverride + False positive     |Blokuj         |Tak         |Nie         |
|Notify + Block + AllowOverride + With justification     |Blokuj         |Tak         |Tak         |
|Notify + Block + AllowOverride + False positive + Without justification     |Blokuj         |Tak         |Nie         |
|Notify + Block + AllowOverride + False positive + With justification     |Blokuj         |Tak         |Tak         |


## <a name="policy-tips-on-onedrive-for-business-sites-and-sharepoint-online-sites"></a>Porady dotyczące zasad OneDrive dla Firm witryn i witryn SharePoint Online

Jeśli dokument w witrynie usługi OneDrive dla Firm lub witrynie SharePoint Online jest taki jak reguła w zasadach DLP, a ta reguła korzysta z porad dotyczących zasad, porady dotyczące zasad są wyświetlane w dokumencie za pomocą specjalnych ikon:

1. Jeśli reguła wyśle powiadomienie o pliku, zostanie wyświetlona ikona ostrzeżenia.

2. Jeśli reguła blokuje dostęp do dokumentu, zostanie wyświetlona ikona zablokowanego dokumentu.

   ![Ikony porad dotyczących zasad w dokumentach OneDrive konta e-mail.](../media/d3e9f772-03f9-4d28-82f8-3064784332a2.png)

Aby podjąć działania dotyczące dokumentu, możesz wybrać element i \> wybrać **ikonę okienka** ![Informacje.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) w prawym górnym rogu strony, aby otworzyć \> okienko szczegółów Wyświetl **poradę o zasadach**.

Porada zasad zawiera listę problemów z zawartością **, a jeśli** porady dotyczące zasad są skonfigurowane przy użyciu tych opcji, możesz wybrać pozycję **Rozwiąż, a** następnie zastąpić  poradę zasad lub Zgłosić wynik fałszywie dodatni.

![Okienko informacji z wyświetloną poradą o zasadach.](../media/0a191e70-80f0-4702-90f4-7a5b7aabcaab.png)

![Porada o zasadach z opcją zastępowania.](../media/e250bff9-41d5-4ce4-82ea-1dc2d043fab1.png)

Zasady DLP są synchronizowane z witrynami, a zawartość jest sprawdzana względem nich okresowo i asynchronicznie, dlatego może wystąpić krótkie opóźnienie między czasem tworzenia zasad DLP a czasem rozpoczęcia przeglądania porad dotyczących zasad. Może wystąpić podobne opóźnienie co w przypadku rozpoznania lub zastąpienia porady dotyczącej zasad do czasu, gdy ikona w dokumencie w witrynie zgasza.

### <a name="default-text-for-policy-tips-on-sites"></a>Domyślny tekst porad dotyczących zasad dotyczących witryn

Domyślnie porady dotyczące zasad wyświetlają tekst podobny do poniższego w przypadku elementu w witrynie. Tekst powiadomienia jest konfigurowany oddzielnie dla każdej reguły, więc wyświetlany tekst różni się w zależności od tego, która reguła jest do nich dopasowana.

|**Jeśli reguła zasad DLP działa tak...**|**W takim przypadku porada domyślna zasad jest taka...**|
|:-----|:-----|
|Wysyła powiadomienie, ale nie zezwala na zastępowanie  <br/> |Ten element powoduje konflikt z zasadami w organizacji.  <br/> |
|Blokuje dostęp, wysyła powiadomienie i zezwala na zastępowanie  <br/> |Ten element powoduje konflikt z zasadami w organizacji. Jeśli nie rozwiążesz tego konfliktu, dostęp do tego pliku może być zablokowany.  <br/> |
|Blokuje dostęp i wysyła powiadomienie  <br/> |Ten element powoduje konflikt z zasadami w organizacji. Dostęp do tego elementu jest zablokowany dla wszystkich oprócz właściciela, ostatniego modyfikatora i głównego administratora zbioru witryn.  <br/> |

### <a name="custom-text-for-policy-tips-on-sites"></a>Tekst niestandardowy do porad dotyczących zasad w witrynach

Tekst porad dotyczących zasad można dostosować oddzielnie od powiadomienia e-mail. W przeciwieństwie do tekstu niestandardowego dla powiadomień e-mail (zobacz sekcję powyżej) niestandardowy tekst porad dotyczących zasad nie akceptuje kodu HTML ani tokenów. Zamiast tego niestandardowy tekst porad dotyczących zasad jest zwykłym tekstem z ograniczeniem do 256 znaków.

## <a name="policy-tips-in-outlook-on-the-web-and-outlook-2013-and-later"></a>Porady dotyczące zasad w Outlook w sieci Web i Outlook 2013 i nowszych

Podczas redagowania nowej wiadomości e-mail w programach Outlook w sieci Web i Outlook 2013 i nowszych zobaczysz poradę co do zasad, jeśli dodasz zawartość, która jest taka jak reguła w zasadach ochrony przed zasadami DLP, a ta reguła korzysta z porad dotyczących zasad. Porada o zasadach jest wyświetlana u góry wiadomości, powyżej adresatów, podczas gdy wiadomość jest komponowana.

![Porada co do zasad u góry wiadomości, która jest komponowana.](../media/9b3b6b74-17c5-4562-82d5-d17ecaaa8d95.png)

Porady dotyczące zasad działają niezależnie od tego, czy informacje poufne są wyświetlane w treści wiadomości, w wierszu tematu, czy nawet w załączniku do wiadomości, jak pokazano w przykładzie.

![Porada zasad pokazująca, że załącznik powoduje konflikt z zasadami DLP.](../media/59ae6655-215f-47d9-ad1d-39c0d1e61740.png)

Jeśli porady dotyczące zasad są skonfigurowane tak, aby zezwalały na zastępowanie,  \>  \> możesz wybrać pozycję Pokaż szczegóły Zastępowanie wprowadź uzasadnienie biznesowe lub zgłoś wynik fałszywie **dodatni.**\>

![Porada o zasadach w wiadomości rozwiniętej w celu pokazania opcji Zastąp.](../media/28bfb997-48a6-41f0-8682-d5e62488458a.png)

![Okno dialogowe porada o zasadach, w którym można zastąpić poradę o zasadach.](../media/f97e836c-04bd-44b4-aec6-ed9526ea31f8.png)

Pamiętaj, że podczas dodawania informacji poufnych do wiadomości e-mail mogą wystąpić opóźnienia między dodaniem poufnych informacji a tym, kiedy pojawi się porada o zasadach.

### <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions"></a>Outlook 2013 i nowszych obsługuje wyświetlanie porad dotyczących zasad tylko dla niektórych warunków

Obecnie program Outlook 2013 i nowszej obsługuje wyświetlanie porad dotyczących zasad tylko dla tych warunków:

- Zawartość zawiera
- Zawartość jest udostępniana

Wyjątki są traktowane jako warunki i wszystkie te warunki działają w programie Outlook, gdzie będą one do siebie dorównać i wymuszać akcje zabezpieczające przed zawartością. Jednak pokazywanie użytkownikom porad dotyczących zasad nie jest jeszcze obsługiwane. Ponadto Outlook wyświetlania porad dotyczących zasad DLP stosowanych do dynamicznej grupy dystrybucyjnej.

### <a name="policy-tips-in-the-exchange-admin-center-vs-the-security-amp-compliance-center"></a>Porady dotyczące zasad w centrum Exchange a Centrum zgodności &amp; zabezpieczeń

Porady dotyczące zasad mogą działać zarówno z zasadami DLP, jak i regułami przepływu poczty <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">e-mail</a> utworzonymi w centrum administracyjnym programu Exchange lub z zasadami DLP &amp; utworzonymi w Centrum zgodności zabezpieczeń, ale nie obiema. Jest tak, ponieważ te zasady są przechowywane w różnych lokalizacjach, ale porady dotyczące zasad mogą rysować tylko z jednej lokalizacji.

Jeśli w centrum administracyjnym usługi Exchange skonfigurowano porady dotyczące zasad, &amp; porady dotyczące zasad skonfigurowane w Centrum zgodności zabezpieczeń nie będą wyświetlane użytkownikom w programach Outlook w sieci Web i Outlook 2013 ani nowszych do momentu wyłączenia porad w centrum administracyjnym usługi Exchange. Dzięki temu bieżące reguły przepływu poczty Exchange (nazywane także regułami transportu) &amp; będą nadal działać do momentu przełączenia się do Centrum zgodności zabezpieczeń.

Pamiętaj, że chociaż porady dotyczące zasad mogą rysować tylko z jednej lokalizacji, powiadomienia e-mail są zawsze wysyłane, nawet jeśli korzystasz z zasad DLP &amp; zarówno w Centrum zgodności zabezpieczeń, jak i w centrum administracyjnym usługi Exchange.

### <a name="default-text-for-policy-tips-in-email"></a>Domyślny tekst porad dotyczących zasad w wiadomości e-mail

Domyślnie porady dotyczące zasad wyświetlają tekst podobny do poniższego w przypadku wiadomości e-mail.

|**Jeśli reguła zasad DLP działa tak...**|**W takim przypadku porada domyślna zasad jest taka...**|
|:-----|:-----|
|Wysyła powiadomienie, ale nie zezwala na zastępowanie  <br/> |Twoje konflikty poczty e-mail z zasadami w Twojej organizacji.  <br/> |
|Blokuje dostęp, wysyła powiadomienie i zezwala na zastępowanie  <br/> |Twoje konflikty poczty e-mail z zasadami w Twojej organizacji.  <br/> |
|Blokuje dostęp i wysyła powiadomienie  <br/> |Twoje konflikty poczty e-mail z zasadami w Twojej organizacji.  <br/> |

## <a name="policy-tips-in-excel-powerpoint-and-word"></a>Porady dotyczące zasad Excel, PowerPoint i Word

Gdy osoby pracują z poufnej zawartości w klasycznych Excel, PowerPoint i Word, porady dotyczące zasad mogą informować je w czasie rzeczywistym o tym, że zawartość powoduje konflikty z zasadami DLP. Wymaga to:

- Dokument Office jest przechowywany w witrynie OneDrive dla Firm lub SharePoint Online.

- Witryna jest zawarta w zasadach DLP skonfigurowanych do korzystania z porad dotyczących zasad.

Office komputerów stacjonarnych automatycznie synchronizują zasady DLP bezpośrednio z usługi Office 365, a następnie skanuj dokumenty, aby upewnić się, że nie są one w konflikcie z Zasadami DLP i wyświetlaj porady dotyczące zasad w czasie rzeczywistym.

> [!NOTE]
> Office klasyczne przeskanują dokumenty samodzielnie, aby ustalić, czy powinny być wyświetlane porady dotyczące zasad DLP; nie są w nich wyświetlane porady dotyczące zasad SharePoint Witryny online lub witryny usługi OneDrive dla Firm, które zostały już określone, powinny być wyświetlane w pliku. W związku z tym porada o zasadach DLP może nie być zawsze widzisz w aplikacjach klasycznych, które są SharePoint Online lub OneDrive dla Firm witryny. Natomiast w Office sieci Web są wyświetlane tylko porady dotyczące zasad DLP, które SharePoint witryny online lub witryny OneDrive dla Firm wcześniej określone powinny być wyświetlane.

W zależności od sposobu, w jaki konfigurujesz porady dotyczące zasad DLP, można po prostu zignorować poradę zasad, zastąpić zasady lub bez ich uzasadnienia biznesowego albo zgłosić wynik fałszywie dodatni.

Porady dotyczące zasad są wyświetlane na pasku komunikatów.

![Pasek komunikatów z poradami o zasadach w Excel 2016.](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Porady dotyczące zasad są również wyświetlane w widoku Backstage (na **karcie** Plik).

![W programie Backstage porada co do zasad jest Excel 2016.](../media/44c561f6-8f3f-4878-b1b0-b7543f8a4120.png)

Jeśli porady dotyczące zasad w zasadach DLP są skonfigurowane przy użyciu tych opcji, możesz wybrać pozycję  Rozwiąż,  aby zastąpić poradę o zasadach **lub Zgłosić wynik** fałszywie dodatni.

![Opcje porad dotyczące zasad w programie Backstage w Excel 2016.](../media/5b3857ba-907e-456e-ae43-888b594c049c.png)

W każdym z tych Office komputerów stacjonarnych inne osoby mogą wyłączać porady dotyczące zasad. Jeśli ta ustawienie jest wyłączona, porady dotyczące zasad, które są prostymi powiadomieniami, nie będą wyświetlane na pasku komunikatów ani w widoku Backstage (na **karcie** Plik). Jednak porady dotyczące zasad blokowania i zastępowania nadal będą wyświetlane, a otrzymają one nadal powiadomienie e-mail. Ponadto wyłączenie porad dotyczących zasad nie powoduje zwolnienia dokumentu z żadnych zastosowanych do niego zasad DLP.

### <a name="default-text-for-policy-tips-in-excel-2016-powerpoint-2016-and-word-2016"></a>Domyślny tekst porad dotyczących zasad w Excel 2016, PowerPoint 2016 i Word 2016

Domyślnie porady dotyczące zasad wyświetlają tekst podobny do poniższego na pasku komunikatów i w widoku Backstage otwartego dokumentu. Tekst powiadomienia jest konfigurowany oddzielnie dla każdej reguły, więc wyświetlany tekst różni się w zależności od tego, która reguła jest do nich dopasowana.

|**Jeśli reguła zasad DLP działa tak...**|**W takim przypadku porada domyślna zasad jest taka...**|
|:-----|:-----|
|Wysyła powiadomienie, ale nie zezwala na zastępowanie  <br/> |Ten plik powoduje konflikt z zasadami w organizacji. Przejdź do menu **Plik,** aby uzyskać więcej informacji.  <br/> |
|Blokuje dostęp, wysyła powiadomienie i zezwala na zastępowanie  <br/> |Ten plik powoduje konflikt z zasadami w organizacji. Jeśli nie rozwiążesz tego konfliktu, dostęp do tego pliku może być zablokowany. Przejdź do menu **Plik,** aby uzyskać więcej informacji.  <br/> |
|Blokuje dostęp i wysyła powiadomienie  <br/> |Ten plik powoduje konflikt z zasadami w organizacji. Jeśli nie rozwiążesz tego konfliktu, dostęp do tego pliku może być zablokowany. Przejdź do menu **Plik,** aby uzyskać więcej informacji.  <br/> |

### <a name="custom-text-for-policy-tips-in-excel-powerpoint-and-word"></a>Niestandardowy tekst porad dotyczących zasad w Excel, PowerPoint i Word

Tekst porad dotyczących zasad można dostosować oddzielnie od powiadomienia e-mail. W przeciwieństwie do tekstu niestandardowego dla powiadomień e-mail (zobacz sekcję powyżej) niestandardowy tekst porad dotyczących zasad nie akceptuje kodu HTML ani tokenów. Zamiast tego niestandardowy tekst porad dotyczących zasad jest zwykłym tekstem z ograniczeniem do 256 znaków.

## <a name="more-information"></a>Więcej informacji

- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie zasad DLP na podstawie szablonu](create-a-dlp-policy-from-a-template.md)
- [Warunki, wyjątki i akcje zasad DLP (wersja zapoznawcza)](./dlp-microsoft-teams.md)
- [Tworzenie zasad DLP w celu ochrony dokumentów za pomocą fci lub innych właściwości](protect-documents-that-have-fci-or-other-properties.md)
- [Szablony zasad DLP](what-the-dlp-policy-templates-include.md)
- [Definicje jednostki typu informacji poufnych](sensitive-information-type-entity-definitions.md)
