---
title: Ustawienia usługi ASF w ramach EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b286f853-b484-4af0-b01f-281fffd85e7a
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorzy mogą dowiedzieć się więcej o ustawieniach zaawansowanego filtru spamu (ASF), które są dostępne w zasadach ochrony przed spamem w Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 75fca937049e71576e1dd599b4cc0f7fba2a2211
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647672"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>Ustawienia zaawansowanego filtru spamu (ASF) w funkcji EOP

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

We wszystkich organizacjach Microsoft 365 ustawienia zaawansowanego filtru spamu (ASF) w zasadach ochrony przed spamem w usłudze EOP umożliwiają administratorom oznaczanie wiadomości jako spamu na podstawie określonych właściwości wiadomości. Usługa ASF jest przeznaczona specjalnie dla tych właściwości, ponieważ są one często spotykane w spamie. W zależności od właściwości wykrywanie asf oznacza wiadomość jako **spam** lub **spam o wysokim poziomie ufności**.

> [!NOTE]
> Włączenie co najmniej jednego ustawienia asf jest agresywnym podejściem do filtrowania spamu. Nie można zgłaszać komunikatów, które są filtrowane przez usługę ASF jako fałszywie dodatnie. Komunikaty, które zostały przefiltrowane przez usługę ASF, można zidentyfikować według:
>
> - Okresowe powiadomienia o kwarantannie ze spamu i werdykty filtru spamu o wysokim poziomie ufności.
> - Obecność przefiltrowanych komunikatów w kwarantannie.
> - Określone `X-CustomSpam:` pola nagłówka X, które są dodawane do komunikatów zgodnie z opisem w tym artykule.

W poniższych sekcjach opisano ustawienia i opcje asf dostępne w zasadach ochrony przed spamem w portalu Microsoft 365 Defender oraz w programie Exchange Online programu PowerShell lub autonomicznego programu PowerShell EOP ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) i [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem w ramach EOP](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>Włączanie, wyłączanie lub testowanie ustawień asf

Dla każdego ustawienia asf dostępne są następujące opcje w zasadach ochrony przed spamem:

- **Włączone: usługa** ASF dodaje odpowiednie pole nagłówka X do wiadomości i oznacza wiadomość jako **spam** (SCL 5 lub 6 dla [ustawienia Zwiększanie oceny spamu](#increase-spam-score-settings)) lub **Spam o wysokim poziomie ufności** (SCL 9 dla [opcji Oznacz jako ustawienia spamu](#mark-as-spam-settings)).
- **Wyłączone**: ustawienie asf jest wyłączone. Jest to wartość domyślna i zalecamy, aby jej nie zmieniać.
- **Test: program** ASF dodaje odpowiednie pole nagłówka X do komunikatu. To, co dzieje się z komunikatem, jest określane przez wartość **trybu testowego** (*TestModeAction*):
  - **Brak**: wykrywanie usługi ASF nie ma wpływu na dostarczanie komunikatów. Komunikat nadal podlega innym typom filtrowania i reguł w ramach EOP.
  - **Dodaj domyślny tekst nagłówka X (*AddXHeader*)**: wartość `X-CustomSpam: This message was filtered by the custom spam filter option` nagłówka X jest dodawana do komunikatu. Możesz użyć tej wartości w regułach skrzynki odbiorczej lub regułach przepływu poczty (nazywanych również regułami transportu), aby wpłynąć na dostarczanie wiadomości.
  - **Wyślij komunikat Bcc (*BccMessage*)**: Określone adresy e-mail (wartość parametru *TestModeBccToRecipients* w programie PowerShell) są dodawane do pola Bcc wiadomości, a wiadomość jest dostarczana do dodatkowych adresatów Bcc. W portalu Microsoft 365 Defender wiele adresów e-mail należy rozdzielić średnikami (;). W programie PowerShell rozdzielasz wiele adresów e-mail przecinkami.

  **Uwagi**:

  - Tryb testowania nie jest dostępny dla następujących ustawień asf:
    - **Filtrowanie identyfikatora nadawcy warunkowego: błąd twardy** (*MarkAsSpamFromAddressAuthFail*)
    - **NDR backscatter**(*MarkAsSpamNdrBackscatter*)
    - **Rekord SPF: twardy błąd** (*MarkAsSpamSpfRecordHardFail*)
  - Ta sama akcja trybu testowego jest stosowana do *wszystkich* ustawień asf ustawionych na **test**. Nie można skonfigurować różnych akcji trybu testowego dla różnych ustawień asf.

## <a name="increase-spam-score-settings"></a>Zwiększanie ustawień oceny spamu

Następujące ustawienia **zwiększania oceny spamu** asf ustawiają poziom ufności spamu (SCL) wykrytych wiadomości na 5 lub 6, co odpowiada werdyktowi filtru **spamu** i odpowiedniej akcji w zasadach ochrony przed spamem.

|Ustawienie zasad ochrony przed spamem|Opis|Dodano nagłówek X|
|---|---|---|
|**Linki obrazów do zdalnych witryn internetowych** <p> *IncreaseScoreWithImageLinks*|Komunikaty zawierające `<Img>` linki tagów HTML do witryn zdalnych (na przykład przy użyciu protokołu http) są oznaczone jako spam.|`X-CustomSpam: Image links to remote sites`|
|**Numeryczny adres IP w adresie URL** <p> *IncreaseScoreWithNumericIps*|Wiadomości zawierające numeryczne adresy URL (zazwyczaj adresy IP) są oznaczone jako spam.|`X-CustomSpam: Numeric IP in URL`|
|**Przekierowanie adresu URL do innego portu** <p> *IncreaseScoreWithRedirectToOtherPort*|Komunikat zawierający hiperlinki przekierowujące do portów TCP innych niż 80 (HTTP), 8080 (alternatywny protokół HTTP) lub 443 (HTTPS) jest oznaczony jako spam.|`X-CustomSpam: URL redirect to other port`|
|**Linki do witryn .biz lub .info** <p> *IncreaseScoreWithBizOrInfoUrls*|Wiadomości zawierające `.biz` treść wiadomości lub `.info` linki są oznaczone jako spam.|`X-CustomSpam: URL to .biz or .info websites`|

## <a name="mark-as-spam-settings"></a>Oznacz jako ustawienia spamu

Następujące ustawienia **Oznacz jako spam** ASF ustawiają listę SCL wykrytych wiadomości na 9, co odpowiada werdyktowi **filtru spamu o wysokim poziomie ufności** i odpowiedniej akcji w zasadach ochrony przed spamem.

|Ustawienie zasad ochrony przed spamem|Opis|Dodano nagłówek X|
|---|---|---|
|**Puste komunikaty** <p> *MarkAsSpamEmptyMessages*|Wiadomości bez tematu, brak zawartości w treści wiadomości i brak załączników są oznaczone jako spam o wysokim poziomie ufności.|`X-CustomSpam: Empty Message`|
|**Tagi osadzone w kodzie HTML** <p> *MarkAsSpamEmbedTagsInHtml*|Wiadomość zawierająca `<embed>` tagi HTML jest oznaczona jako spam o wysokim poziomie ufności. <p> Ten tag umożliwia osadzanie różnych rodzajów dokumentów w dokumencie HTML (na przykład dźwięków, filmów wideo lub obrazów).|`X-CustomSpam: Embed tag in html`|
|**Język JavaScript lub VBScript w języku HTML** <p> *MarkAsSpamJavaScriptInHtml*|Komunikaty korzystające z języka JavaScript lub Visual Basic Script Edition w języku HTML są oznaczone jako spam o wysokim poziomie ufności. <p> Te języki skryptów są używane w wiadomościach e-mail w celu automatycznego wykonania określonych akcji.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**Tagi formularzy w języku HTML** <p> *MarkAsSpamFormTagsInHtml*|Wiadomości zawierające `<form>` tagi HTML są oznaczone jako spam o wysokim poziomie ufności. <p> Ten tag służy do tworzenia formularzy witryny internetowej. Reklamy e-mail często zawierają ten tag w celu uzyskania informacji od odbiorcy.|`X-CustomSpam: Form tag in html`|
|**Tagi ramek lub ramek w języku HTML** <p> *MarkAsSpamFramesInHtml*|Wiadomości zawierające `<frame>` tagi LUB `<iframe>` HTML są oznaczone jako spam o wysokim poziomie ufności. <p> Tagi te są używane w wiadomościach e-mail do formatowania strony do wyświetlania tekstu lub grafiki.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**Błędy internetowe w kodzie HTML** <p> *MarkAsSpamWebBugsInHtml*|*Usterka sieci Web* (znana również jako *sygnalizator internetowy*) to element graficzny (często tak mały, jak jeden piksel po jednym pikselu), który jest używany w wiadomościach e-mail w celu określenia, czy wiadomość została odczytana przez adresata. <p> Komunikaty zawierające błędy internetowe są oznaczone jako spam o wysokim poziomie ufności. <p> Uzasadnione biuletyny mogą korzystać z błędów internetowych, chociaż wielu uważa to za naruszenie prywatności. |`X-CustomSpam: Web bug`|
|**Tagi obiektów w kodzie HTML** <p> *MarkAsSpamObjectTagsInHtml*|Wiadomości zawierające `<object>` tagi HTML są oznaczone jako spam o wysokim poziomie ufności. <p> Ten tag umożliwia uruchamianie wtyczek lub aplikacji w oknie HTML.|`X-CustomSpam: Object tag in html`|
|**Wyrazy wrażliwe** <p> *MarkAsSpamSensitiveWordList*|Firma Microsoft utrzymuje dynamiczną, ale nieedytowalną listę słów skojarzonych z potencjalnie obraźliwymi wiadomościami. <p> Wiadomości zawierające wyrazy z listy wyrazów poufnych w treści tematu lub wiadomości są oznaczone jako spam o wysokim poziomie ufności.|`X-CustomSpam: Sensitive word in subject/body`|
|**Rekord SPF: niepowodzenie twarde** <p> *MarkAsSpamSpfRecordHardFail*|Komunikaty wysyłane z adresu IP, który nie jest określony w rekordzie SPF Sender Policy Framework (SPF) w systemie DNS dla źródłowej domeny poczty e-mail, są oznaczone jako spam o wysokim poziomie ufności. <p> Tryb testowy nie jest dostępny dla tego ustawienia.|`X-CustomSpam: SPF Record Fail`|

Następujące ustawienia **Oznacz jako spam** ASF ustawiają listę SCL wykrytych wiadomości na wartość 6, co odpowiada werdyktowi filtru **spamu** i odpowiedniej akcji w zasadach ochrony przed spamem.

|Ustawienie zasad ochrony przed spamem|Opis|Dodano nagłówek X|
|---|---|---|
|**Filtrowanie identyfikatora nadawcy kończy się niepowodzeniem** <p> *MarkAsSpamFromAddressAuthFail*|Komunikaty, które nie sprawdzają warunkowego identyfikatora nadawcy, są oznaczone jako spam. <p> To ustawienie łączy sprawdzanie SPF z sprawdzaniem identyfikatora nadawcy, aby chronić przed nagłówkami wiadomości zawierającymi sfałszowanych nadawców. <p> Tryb testowy nie jest dostępny dla tego ustawienia.|`X-CustomSpam: SPF From Record Fail`|
|**Backscatter** <p> *MarkAsSpamNdrBackscatter*|*Backscatter to bezużyteczne* raporty o braku dostarczania (znane również jako żądania NDR lub wiadomości bounce) spowodowane przez sfałszowanych nadawców w wiadomościach e-mail. Aby uzyskać więcej informacji, zobacz [Backscatter messages and EOP (Tworzenie kopii zapasowych komunikatów i EOP](backscatter-messages-and-eop.md)). <p> Nie musisz konfigurować tego ustawienia w następujących środowiskach, ponieważ dostarczane są uzasadnione żądania NDR, a zaplecze jest oznaczone jako spam: <ul><li>Microsoft 365 organizacje ze skrzynkami pocztowymi Exchange Online.</li><li>Lokalne organizacje poczty e-mail, w których kierujesz *wychodzącą* pocztę e-mail za pośrednictwem EOP.</li></ul> <p> W autonomicznych środowiskach EOP, które chronią przychodzące wiadomości e-mail do lokalnych skrzynek pocztowych, włączenie lub wyłączenie tego ustawienia ma następujący wynik: <ul><li> **Włączone**: dostarczane są uzasadnione żądania NDR, a zaplecze jest oznaczone jako spam.</li><li>**Wyłączone**: Uzasadnione żądania NDR i backscatter przechodzą przez normalne filtrowanie spamu. Do oryginalnego nadawcy wiadomości zostanie dostarczona większość legalnych NDR. Niektóre, ale nie wszystkie, backscatter jest oznaczony jako spam. Z definicji backscatter może być dostarczany tylko do sfałszowanego nadawcy, a nie do oryginalnego nadawcy.</li></ul> <p> Tryb testowy nie jest dostępny dla tego ustawienia.|`X-CustomSpam: Backscatter NDR`|
