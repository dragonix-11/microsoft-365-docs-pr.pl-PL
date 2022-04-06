---
title: Warunki, wyjątki i akcje zasad DLP
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
recommendations: false
description: dowiedz się więcej o warunkach i wyjątkach dotyczących zasad dlp
ms.openlocfilehash: 9b735d139950399fb80e9063e7d9fdd1176c2d2b
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500062"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>Warunki, wyjątki i akcje zasad DLP

Warunki i wyjątki w zasadach DLP identyfikują poufne elementy, do których są stosowane zasady. Akcje określają, co się stanie, jeśli warunek wyjątku zostanie spełniony.

- Warunki określają, co należy uwzględnić
- Wyjątki określają, co wykluczyć.
- Akcje określają, co się stanie jako konsekwencja spełnionego warunku lub wyjątku

Większość warunków i wyjątków ma jedną właściwość, która obsługuje co najmniej jedną wartość. Jeśli na przykład zasady DLP są stosowane do Exchange e-mail, nadawca jest wymagany od  nadawcy wiadomości. Niektóre warunki mają dwie właściwości. Na przykład nagłówek wiadomości  zawiera dowolny z tych warunków, wymaga jednej właściwości do określenia pola nagłówka wiadomości, a drugiej właściwości określającej tekst do wyszukiwania w polu nagłówka. Niektóre warunki lub wyjątki nie mają żadnych właściwości. Na przykład warunek Załącznik **jest chroniony hasłem** , po prostu wyszukuje załączniki w wiadomościach, które są chronione hasłem.

Akcje zwykle wymagają dodatkowych właściwości. Jeśli na przykład reguła zasad DLP przekierowuje wiadomość, musisz określić, dokąd wiadomość jest przekierowywany.
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>Warunki i wyjątki dotyczące zasad DLP

W poniższych sekcjach tabele zawierają opis warunków i wyjątków dostępnych w programie DLP.

- [Nadawcy](#senders)
- [Adresaci](#recipients)
- [Temat lub treść wiadomości](#message-subject-or-body)
- [Załączniki](#attachments)
- [Nagłówki wiadomości](#message-headers)
- [Właściwości wiadomości](#message-properties)

### <a name="senders"></a>Nadawcy

W przypadku użycia adresu nadawcy jako warunku lub wyjątku rzeczywistego pola, w którym szukana wartość jest szukana, różni się w zależności od skonfigurowanej lokalizacji adresu nadawcy. Domyślnie reguły DLP używają adresu nagłówka jako adresu nadawcy.

![Obraz nagłówka wiadomości e-mail z różnicą między adresem koperty (P1) a adresem nagłówka (P2)](../media/dlp-conditions-exceptions-meetinginvite-callouts.png)

Na poziomie dzierżawy możesz skonfigurować lokalizację adresu nadawcy, która będzie używana we wszystkich regułach, o ile nie zostanie zastąpiona jedną regułą. Aby skonfigurować konfigurację zasad DLP dzierżawy w celu oceny adresu nadawcy z koperty we wszystkich regułach, możesz uruchomić następujące polecenie:

```PowerShell
Set-PolicyConfig –SenderAddressLocation Envelope
```

Aby skonfigurować lokalizację adresu nadawcy na poziomie reguły DLP, parametr to _SenderAddressLocation_. Dostępne wartości:

- **Nagłówek**: Sprawdzaj tylko nadawców w nagłówkach wiadomości (na przykład w polach **Od**, **Nadawca** lub **Odpowiedz** ). Jest to wartość domyślna.

- **Koperta**: Sprawdzaj tylko nadawców z koperty wiadomości (wartość **MAIL FROM** użyta w transmisji SMTP, która zwykle jest przechowywana w polu **Return-Path** ).

- **Nagłówek lub koperta** (`HeaderOrEnvelope`) Sprawdź nadawców w nagłówku wiadomości i na kopercie wiadomości.
<br>

|warunek lub wyjątek w zasadie DLP|Parametry warunków/wyjątków w programie Microsoft 365 PowerShell|typ właściwości|opis|
|---|---|---|---|
|Nadawca:|warunek: *Od* <br/> wyjątek: *ExceptIfFrom*|Adresy|Wiadomości wysyłane przez określone skrzynki pocztowe, użytkowników poczty, kontakty Microsoft 365 grupy w organizacji.|
|Nadawca jest członkiem |_FromMemberOf_ <br/> _ExceptIfFromMemberOf_|Adresy|Wiadomości wysyłane przez członka określonej grupy dystrybucyjnej, grupy zabezpieczeń z obsługą poczty lub Microsoft 365 dystrybucyjnej.|
|Adres IP nadawcy to|warunek: *SenderIPRanges*<br/> wyjątek: *ExceptIfSenderIPRanges*|IPAddressRanges|Wiadomości, w których adres IP nadawcy odpowiada określoneowi adresowi IP lub mieści się w określonym zakresie adresów IP.|
|Adres nadawcy zawiera wyrazy|warunek: *FromAddressContainsWords* <br/> wyjątek: *ExceptIfFromAddressContainsWords*|Wyrazy|Wiadomości zawierające określone wyrazy w adresie e-mail nadawcy.|
|Adres nadawcy odpowiada wzorcom|warunek: *FromAddressMatchesPatterns* <br/> wyjątek: *ExceptFromAddressMatchesPatterns*|Desenie|Wiadomości, w których adres e-mail nadawcy zawiera wzorce tekstu zgodne z określonymi wyrażeniami regularnymi.|
|Domena nadawcy to|warunek: *SenderDomainIs* <br/> wyjątek: *ExceptIfSenderDomainIs*|DomainName|Wiadomości, w których domena adresu e-mail nadawcy odpowiada określonej wartości. Jeśli chcesz znaleźć domeny nadawcy zawierające określoną  domenę (na przykład dowolną poddomenę domeny), użyj warunku Adres nadawcy **jest** dopasowywany(*FromAddressMatchesPatterns*) i określ domenę, stosując składnię: '\.domaincom\.$'.|
|Zakres nadawcy|warunek: *FromScope* <br/> wyjątek: *ExceptIfFromScope*|UserScopeFrom|Wiadomości wysyłane przez wewnętrznych lub zewnętrznych nadawców.|
|Określone właściwości nadawcy zawierają dowolny z tych wyrazów.|warunek: *SenderADAttributeContainsWords* <br/> wyjątek: *ExceptIfSenderADAttributeContainsWords*|Pierwsza właściwość: `ADAttribute` <p> Druga właściwość: `Words`|Wiadomości, w których określony atrybut usługi Active Directory nadawcy zawiera dowolny z określonych wyrazów.|
|Określone właściwości nadawcy są zgodne z tymi wzorcami tekstu|warunek: *SenderADAttributeMatchesPatterns* <br/> wyjątek: *ExceptIfSenderADAttributeMatchesPatterns*|Pierwsza właściwość: `ADAttribute` <p> Druga właściwość: `Patterns`|Wiadomości, w których określony atrybut usługi Active Directory nadawcy zawiera wzorce tekstu zgodne z określonymi wyrażeniami regularnymi.|
|

### <a name="recipients"></a>Adresaci

<br>

****

|warunek lub wyjątek w zasadie DLP|Parametry warunków/wyjątków w programie Microsoft 365 PowerShell|typ właściwości|opis|
|---|---|---|---|
|Adresatem jest|warunek: *SentTo* <br/> wyjątek: *ExceptIfSentTo*|Adresy|Wiadomości, w których jednym z adresatów jest określona skrzynka pocztowa, użytkownik poczty lub kontakt pocztowy w organizacji. Adresaci mogą znaleźć się w polach **Do**, **DW** lub **UDW** wiadomości.|
|Domena adresata to|warunek: *RecipientDomainIs* <br/> wyjątek: *ExceptIfRecipientDomainIs*|DomainName|Wiadomości, w których domena adresu e-mail adresata jest dosyć określona.|
|Adres adresata zawiera wyrazy|warunek: *AnyOfRecipientAddressContainsWords* <br/> wyjątek: *ExceptIfAnyOfRecipientAddressContainsWords*|Wyrazy|Wiadomości zawierające określone wyrazy w adresie e-mail adresata. <br/>**Uwaga**: ten warunek nie dotyczy wiadomości wysyłanych do adresów proxy adresatów. Ta trafia tylko na wiadomości wysyłane na podstawowy adres e-mail adresata.|
|Adres adresata pasuje do wzorców|warunek: *AnyOfRecipientAddressMatchesPatterns* <br/> wyjątek: *ExceptIfAnyOfRecipientAddressMatchesPatterns*|Desenie|Wiadomości, w których adres e-mail adresata zawiera wzorce tekstu zgodne z określonymi wyrażeniami regularnymi. <br/> **Uwaga**: ten warunek nie dotyczy wiadomości wysyłanych do adresów proxy adresatów. Ta trafia tylko na wiadomości wysyłane na podstawowy adres e-mail adresata.|
|Wysłane do członka|warunek: *SentToMemberOf* <br/> wyjątek: *ExceptIfSentToMemberOf*|Adresy|Wiadomości zawierające adresatów, którzy są członkami określonej grupy dystrybucyjnej, grupy zabezpieczeń z obsługą poczty lub Microsoft 365 dystrybucyjnej. Grupa może się znaleźć w polach **Do**, **DW** lub **UDW** wiadomości.|
|Określone właściwości adresata zawierają dowolny z tych wyrazów. |_RecipientADAttributeContainsWords_ <br/> _ExceptIfRecipientADAttributeContainsWords_|Pierwsza właściwość: `ADAttribute` <p> Druga właściwość: `Words`|Wiadomości, w których określony atrybut usługi Active Directory adresata zawiera dowolny z określonych wyrazów. <p> Zwróć uwagę, **że atrybut Country** wymaga dwulitowej wartości kodu kraju (na przykład DE dla Niemiec).|
|Określone właściwości adresata są zgodne z tymi wzorcami tekstu |_RecipientADAttributeMatchesPatterns_ <br/> _ExceptIfRecipientADAttributeMatchesPatterns_|Pierwsza właściwość: `ADAttribute` <p> Druga właściwość: `Patterns`|Wiadomości zawierające określony atrybut usługi Active Directory adresata zawierają wzorce tekstu zgodne z określonymi wyrażeniami regularnymi.|
|

### <a name="message-subject-or-body"></a>Temat lub treść wiadomości

<br>

****

|warunek lub wyjątek w zasadie DLP|Parametry warunków/wyjątków w programie Microsoft 365 PowerShell|typ właściwości|opis|
|---|---|---|---|
|Temat zawiera wyrazy lub frazy|warunek: *SubjectContainsWords* <br/> wyjątek: *ExceptIf SubjectContainsWords*|Wyrazy|Wiadomości z określonymi wyrazami w polu Temat.|
|Temat odpowiada wzorcom|warunek: *SubjectMatchesPatterns* <br/> wyjątek: *ExceptIf SubjectMatchesPatterns*|Desenie|Wiadomości, w których pole Temat zawiera wzorce tekstu zgodne z określonymi wyrażeniami regularnymi.|
|Zawartość zawiera|warunek: *ContentContainsSensitiveInformation* <br/> exception *ExceptIfContentContainsSensitiveInformation*|SensitiveInformationTypes|Wiadomości lub dokumenty zawierające informacje poufne, zdefiniowane przez zasady ochrony przed utratą danych (DLP).|
|Wzorzec dopasowania Temat lub Treść|warunek: *SubjectOrBodyMatchesPatterns* <br/> wyjątek: *ExceptIfSubjectOrBodyMatchesPatterns*|Desenie|Wiadomości, w których pole tematu lub treść wiadomości zawierają wzorce tekstu zgodne z określonymi wyrażeniami regularnymi.|
|Temat lub Treść zawiera wyrazy|warunek: *SubjectOrBodyContainsWords* <br/> wyjątek: *ExceptIfSubjectOrBodyContainsWords*|Wyrazy|Wiadomości z określonymi wyrazami w polu tematu lub w treści wiadomości|
|

### <a name="attachments"></a>Załączniki

<br>

****

|warunek lub wyjątek w zasadie DLP|Parametry warunków/wyjątków w programie Microsoft 365 PowerShell|typ właściwości|opis|
|---|---|---|---|
|Załącznik jest chroniony hasłem|warunek: *DocumentIsPasswordProtected* <br/> wyjątek: *ExceptIfDocumentIsPasswordProtected*|brak|Wiadomości, w których załącznik jest chroniony hasłem (i dlatego nie można ich zeskanować). Wykrywanie haseł działa tylko w Office, plikach .zip plikach i plikach 0,7z.|
|Rozszerzenie pliku załącznika to|warunek: *ContentExtensionMatchesWords* <br/> wyjątek: *ExceptIfContentExtensionMatchesWords*|Wyrazy|Wiadomości, w których rozszerzenie pliku załącznika jest takie, jak dowolne z określonych wyrazów.|
|Nie można było zeskanować zawartości dowolnego załącznika wiadomości e-mail|warunek: *DocumentIsUnsupported* <br/>wyjątek: *ExceptIf DocumentIsUnsupported*|nie dotyczy|Wiadomości, w których załącznik nie został natywnie rozpoznany przez Exchange Online.|
|Zawartość każdego załącznika wiadomości e-mail nie ukończono skanowania|warunek: *ProcessingLimitExceeded* <br/> wyjątek: *ExceptIfProcessingLimitExceeded*|nie dotyczy|Wiadomości, w przypadku których aparat reguł nie mógł ukończyć skanowania załączników. Możesz użyć tego warunku do utworzenia reguł, które współpracują ze sobą w celu identyfikowania i przetwarzania wiadomości, w przypadku których nie można w pełni zeskanować zawartości.|
|Nazwa dokumentu zawiera wyrazy|warunek: *DocumentNameMatchesWords* <br/> wyjątek: *ExceptIfDocumentNameMatchesWords*|Wyrazy|Wiadomości, w których nazwa pliku załącznika odpowiada dowolnej z określonych wyrazów.|
|Nazwa dokumentu pasuje do wzorców|warunek: *DocumentNameMatchesPatterns* <br/> wyjątek: *ExceptIfDocumentNameMatchesPatterns*|Desenie|Wiadomości, w których nazwa pliku załącznika zawiera wzorce tekstu zgodne z określonymi wyrażeniami regularnymi.|
|Właściwość dokumentu to|warunek: *ContentPropertyContainsWords* <br/> wyjątek: *ExceptIfContentPropertyContainsWords*|Wyrazy|Wiadomości lub dokumenty, w których rozszerzenie pliku załącznika jest takie, jak dowolne z określonych wyrazów.|
|Rozmiar dokumentu jest równy lub większy niż|warunek: *DocumentSizeOver* <br/> wyjątek: *ExceptIfDocumentSizeOver*|Rozmiar|Wiadomości, w których załącznik jest większy lub równy określonej wartości.|
|Zawartość każdego załącznika zawiera dowolny z tych wyrazów.|warunek: *DocumentContainsWords* <br/> wyjątek: *ExceptIfDocumentContainsWords*|`Words`|Wiadomości, w których załącznik zawiera określone wyrazy.|
|Każda zawartość załączników pasuje do tych wzorców tekstu|warunek: *DokumentMatchesPatterns* <br/> wyjątek: *ExceptIfDocumentMatchesPatterns*|`Patterns`|Wiadomości zawierające załączniki zawierające wzorce tekstu zgodne z określonymi wyrażeniami regularnymi.|
|

### <a name="message-headers"></a>Nagłówki wiadomości

<br>

****

|warunek lub wyjątek w zasadie DLP|Parametry warunków/wyjątków w programie Microsoft 365 PowerShell|typ właściwości|opis|
|---|---|---|---|
|Nagłówek zawiera wyrazy lub frazy|warunek: *HeaderContainsWords* <br/> wyjątek: *ExceptIfHeaderContainsWords*|Tabela skrótów|Wiadomości zawierające określone pole nagłówka i wartość tego pola nagłówka zawierają określone wyrazy.|
|Nagłówek odpowiada wzorcom|warunek: *HeaderMatchesPatterns* <br/> wyjątek: *ExceptIfHeaderMatchesPatterns*|Tabela skrótów|Wiadomości zawierające określone pole nagłówka i wartość tego pola nagłówka zawierają określone wyrażenia regularne.|

### <a name="message-properties"></a>Właściwości wiadomości

<br>

****

|warunek lub wyjątek w zasadie DLP|Parametry warunków/wyjątków w programie Microsoft 365 PowerShell|typ właściwości|opis|
|---|---|---|---|
|Ważność|warunek: *WithImportance* <br/> wyjątek: *ExceptIfWithImportance*|Ważność|Wiadomości oznaczone określonym poziomem ważności.|
|Zestaw znaków zawartości zawiera wyrazy|warunek: *ContentCharacterSetContainsWords* <br/> *ExceptIfContentCharacterSetContainsWords*|Zestawy znaków|Wiadomości, które mają dowolną z nazw określonego zestawu znaków.|
|Zastępuje nadawcę|warunek: *HasSenderOverride* <br/> wyjątek: *ExceptIfHasSenderOverride*|nie dotyczy|Wiadomości, w przypadku których nadawca postanowił zastąpić zasady ochrony przed utratą danych (DLP). Aby uzyskać więcej informacji o zasadach ochrony przed utratą danych, zobacz [Informacje na temat ochrony przed utratą danych](./dlp-learn-about-dlp.md).|
|Dopasowania typu wiadomości|warunek: *MessageTypeMatches* <br/> wyjątek: *ExceptIfMessageTypeMatches*|MessageType (Typ komunikatu)|Wiadomości określonego typu. **Uwaga**: Dostępne typy wiadomości to: Odpowiedź automatyczna, Automatyczne przesyłanie dalej, Zaszyfrowane (S/MIME), Kalendarz, Zarządzanie uprawnieniami (zarządzanie prawami), Poczta głosowa, Podpisane, Potwierdzenie przeczytania i Żądanie zatwierdzenia. |
|Rozmiar wiadomości jest większy lub równy|warunek: *MessageSizeOver* <br/> wyjątek: *ExceptIfMessageSizeOver*|`Size`|Wiadomości, w których całkowity rozmiar (wiadomość plus załączniki) jest większy lub równy określonej wartości. **Uwaga**: Limity rozmiaru wiadomości w skrzynkach pocztowych są sprawdzane przed regułami przepływu poczty. Wiadomość, która jest za duża w przypadku skrzynki pocztowej, zostanie odrzucona, zanim reguła z tym warunkiem będzie mogła działać na tej wiadomości.|
|

## <a name="actions-for-dlp-policies"></a>Akcje dotyczące zasad DLP

W poniższej tabeli opisano akcje dostępne w ramach zasad DLP.

<br>

****

|akcja w programie DLP|Parametry akcji w programie Microsoft 365 PowerShell|typ właściwości|opis|
|---|---|---|---|
|Ustawianie nagłówka|SetHeader (UstawGłówny)|Pierwsza właściwość: *Nazwa nagłówka* </br> Druga właściwość: *Wartość nagłówka*|Parametr SetHeader określa akcję reguły DLP, która dodaje lub modyfikuje pole nagłówka i wartość w nagłówku wiadomości. Ten parametr ma składnię "Nazwa Nagłówka:Wartość_nagłówka". Można określić wiele par nazwy nagłówka i wartości rozdzielonych przecinkami.|
|Usuwanie nagłówka|RemoveHeader|Pierwsza właściwość: *MessageHeaderField*</br> Druga właściwość: *String*|Parametr RemoveHeader określa akcję reguły DLP, która usuwa pole nagłówka z nagłówka wiadomości. Ten parametr ma składnię "Nazwa Nagłówka" lub "Nazwa_nagłówka:Wartość_nagłówka". Można określić wiele nazw nagłówków lub nazw nagłówków i par wartości rozdzielonych przecinkami.|
|Przekierowywanie wiadomości do konkretnych użytkowników|*RedirectMessageTo*|Adresy|Przekierowuje wiadomość do określonych adresatów. Wiadomość nie jest dostarczana do oryginalnych adresatów i do nadawcy ani do oryginalnych adresatów nie jest wysyłane żadne powiadomienie.|
|Przesyłanie wiadomości dalej do zatwierdzenia do menedżera nadawcy|Umiarkowane|Pierwsza właściwość: *ModerateMessageByManager*</br> Druga właściwość: *Wartość logiczna*|Parametr Moderate określa akcję reguły DLP, która wysyła wiadomość e-mail do moderatora. Ten parametr ma składnię: @{ModerateMessageByManager = <$true \|$false>;|
|Przesyłanie wiadomości do zatwierdzenia określonym zatwierdzającym|Umiarkowane|Pierwsza właściwość: *ModerateMessageByUser*</br>Druga właściwość: *Adresy*|Parametr Moderate określa akcję reguły DLP, która wysyła wiadomość e-mail do moderatora. Ten parametr ma składnię: @{ ModerateMessageByUser = @("emailaddress1","emailaddress2",..."emailaddressN")}|
|Dodawanie adresata|AddRecipients|Pierwsza właściwość: *Pole*</br>Druga właściwość: *Adresy*|Dodaje co najmniej jednego adresata do pola Do/DW/UDW wiadomości. Ten parametr ma składnię: @{<AddToRecipients \|CopyTo \|BlindCopyTo> = "adres_e-mail"}|
|Dodawanie menedżera nadawcy jako adresata|AddRecipients|Pierwsza właściwość: *AddedManagerAction*</br>Druga właściwość: *Pole*|Dodaje menedżera nadawcy do wiadomości jako określony typ adresata (Do, DW, UDW) lub przekierowuje wiadomość do menedżera nadawcy bez powiadomienia nadawcy lub adresata. Ta akcja działa tylko wtedy, gdy atrybut Menedżera nadawcy jest zdefiniowany w usłudze Active Directory. Ten parametr ma składnię: @{AddManagerAsRecipientType = "<To \|DW \|UDW>"}|
Przedimek tematu|PrependSubject|Ciąg|Dodaje określony tekst na początku pola Temat wiadomości. Rozważ użycie spacji lub dwukropka (:) jako ostatni znak określonego tekstu, aby odróżnić go od pierwotnego tekstu tematu.</br>Aby zapobiec dodaniu tego samego ciągu do wiadomości, które już zawierają tekst w temacie (na przykład odpowiedzi), dodaj od reguły wyjątek "Temat zawiera wyrazy" (ExceptIfSubjectContainsWords).|
|Stosowanie zastrzeżenia w formacie HTML|ApplyHtmlDisclaimer|Pierwsza właściwość: *Tekst*</br>Druga właściwość: *Lokalizacja*</br>Trzecia właściwość: *Akcja rezerwowa*|Stosuje określone zastrzeżenie języka HTML do wymaganej lokalizacji wiadomości.</br>Ten parametr ma składnię: @{ Text = " " ; Location = <Dołącz \|>; FallbackAction = <Wrap \|Ignore \|Reject> }|
|Usuwanie Office 365 wiadomości i ochrony praw|RemoveRMSTemplate|nie dotyczy|Usuwa Office 365 szyfrowania zastosowanego do wiadomości e-mail|
|Dostarczanie wiadomości do hostowanej kwarantanny |_Kwarantanna_|nie dotyczy| Ta akcja jest obecnie dostępna w **publicznej wersji zapoznawczej**. W tej fazie w wiadomościach e-mail poddanych kwarantannie przez zasady DLP będzie pokazywany typ zasad ExchangeTransportRule.</br> Wiadomość jest dostarczana do kwarantanny w u usługi EOP. Aby uzyskać więcej informacji, zobacz [Poddaj wiadomościom w kwarantannie usługi EOP](/microsoft-365/security/office-365-security/quarantine-email-messages).|
|

<!--|Modify Subject|ModifySubject|PswsHashTable | Remove text from the subject line that matches a specific pattern and replace it with different text. See the example below. You can: </br>- **Replace** all matches in the subject with the replacement text </br>- **Append** to remove all matches in the subject and inserts the replacement text at the end of the subject. </br>- **Prepend** to remove all matches and inserts the replacement text at the beginning of the subject. See ModifySubject parameter in, /powershell/module/exchange/new-dlpcompliancerule|-->

