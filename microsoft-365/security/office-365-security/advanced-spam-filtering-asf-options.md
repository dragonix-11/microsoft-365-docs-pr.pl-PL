---
title: Ustawienia asf w ucieknie eop
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
description: Administratorzy mogą dowiedzieć się więcej o ustawieniach Zaawansowanego filtru spamu (ASF) dostępnych w zasadach ochrony przed spamem w programie Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6a34507866be90a197fcbed7bd1038cbcec61c84
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682312"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>Ustawienia zaawansowanego filtru spamu (ASF) w uchcie eop

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

We wszystkich Microsoft 365 e-mail ustawienia Zaawansowanego filtru spamu w zasadach ochrony przed spamem w u administratorach usługi EOP umożliwiają administratorom oznaczanie wiadomości jako spamu na podstawie określonych właściwości wiadomości. Zasady ASF są przeznaczone specjalnie do tych właściwości, ponieważ często występują w spamie. W zależności od właściwości wykrywanie asf spowoduje oznaczenie wiadomości jako **spamu lub** **spamu o dużej pewności**.

> [!NOTE]
> Włączenie jednego lub większej liczby ustawień asf to agresywne podejście do filtrowania spamu. Nie można raportować wiadomości filtrowanych według asf jako wyników fałszywie dodatnich. Wiadomości filtrowane za pomocą filtru ASF można identyfikować według:
>
> - Okresowe powiadomienia kwarantanny o spamie i werdykty filtru spamu o dużej pewności.
> - Obecność odfiltrowanych wiadomości w kwarantannie.
> - Określone pola `X-CustomSpam:` nagłówka X dodawane do wiadomości zgodnie z opisem w tym artykule.

W poniższych sekcjach opisano ustawienia i opcje ochrony przed spamem dostępne w zasadach ochrony przed spamem w portalu usługi Microsoft 365 Defender oraz w programie Exchange Online PowerShell lub autonomicznym programie PowerShell usługi EOP ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) i [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)). Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad ochrony przed spamem w u usługi EOP](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>Włączanie, wyłączanie lub testowanie ustawień asf

Dla każdego ustawienia asf w zasadach ochrony przed spamem są dostępne następujące opcje:

- **Wł.:** AsF dodaje odpowiednie pole nagłówka X do wiadomości i oznacza wiadomość jako **spam** (SCL 5 lub 6 w przypadku ustawienia Zwiększ liczbę [spamu](#increase-spam-score-settings)) lub Spam o wysokiej **pewności (** SCL 9 w przypadku ustawień Oznacz jako [spam](#mark-as-spam-settings)).
- **Wyłączone**: ustawienie asf (AsF) jest wyłączone. Jest to wartość domyślna i nie zalecamy jej zmieniania.
- **Test**: AsF dodaje odpowiednie pole nagłówka X do wiadomości. To, co się stanie z komunikatem, zależy od **wartości testowej** (*TestModeAction*):
  - **Brak**: Wykrycie asf nie ma wpływu na dostarczanie wiadomości. Wiadomość nadal podlega innym typom filtrowania i reguł w umacie EOP.
  - **Dodawanie domyślnego tekstu nagłówka X (*AddXHeader*)**: Wartość nagłówka X `X-CustomSpam: This message was filtered by the custom spam filter option` jest dodawana do wiadomości. Tej wartości możesz użyć w regułach skrzynki odbiorczej lub w zasadach przepływu poczty e-mail (nazywanych również regułami transportu), aby wpływać na dostarczenie wiadomości.
  - **Wyślij wiadomość UDW (*UDW*)**: Określone adresy e-mail (wartość parametru *TestModeBccToRecipients* w programie PowerShell) są dodawane do pola UDW wiadomości, a wiadomość jest dostarczana do dodatkowych adresatów z pola UDW. W portalu Microsoft 365 Defender rozdziel wiele adresów e-mail średnikami (;). W programie PowerShell można oddzielić wiele adresów e-mail przecinkami.

  **Uwagi**:

  - Tryb testowania nie jest dostępny w następujących ustawieniach asf:
    - **Filtrowanie warunkowego identyfikatora nadawcy: trudno nie powieść** (*MarkAsSpamFromAddressAuthFail*)
    - **Backscatter z niedostarczeniu**(*MarkAsSpamNdrBackscatter*)
    - **Rekord SPF: trudno nie powieść** (*MarkAsSpamSpfRecordFail*)
  - Ta sama akcja trybu testowania jest stosowana do *wszystkich ustawień* asf, dla których ustawiono wartość **Test**. Nie można konfigurować różnych akcji trybu testowania dla różnych ustawień asf.

## <a name="increase-spam-score-settings"></a>Zwiększanie ustawień wyników spamu

Poniższe **ustawienia Zwiększ** wynik asf spamu ustawiaj poziom ufności filtru spamu (SCL) wykrytych wiadomości na 5 lub 6, który odpowiada  werdyktowi filtru spamu i odpowiadającemu mu akcji w zasadach ochrony przed spamem.

|Ustawienie zasad ochrony przed spamem|Opis|Dodano nagłówek X|
|---|---|---|
|**Obraz linków do zdalnych witryn internetowych** <p> *IncreaseScoreWithImageLinks*|Wiadomości zawierające linki do `<Img>` tagów HTML do witryn zdalnych (na przykład przy użyciu http) są oznaczane jako spam.|`X-CustomSpam: Image links to remote sites`|
|**Liczbowy adres IP w adresie URL** <p> *IncreaseScoreWithNumericIps*|Wiadomości zawierające adresy URL oparte na wartościach liczbowych (zazwyczaj adresy IP) są oznaczane jako spam.|`X-CustomSpam: Numeric IP in URL`|
|**Przekierowanie adresu URL do innego portu** <p> *IncreaseScoreWithRedirectToOtherPort*|Wiadomość, która zawiera hiperlinki przekierowują do portów TCP innych niż 80 (HTTP), 8080 (alternatywny protokół HTTP) lub 443 (HTTPS) są oznaczane jako spam.|`X-CustomSpam: URL redirect to other port`|
|**Linki do witryn internetowych .biz lub .info** <p> *IncreaseScoreWithBizOrInfoUrls*|Wiadomości zawierające treść `.biz` wiadomości lub `.info` linki w jej treści są oznaczane jako spam.|`X-CustomSpam: URL to .biz or .info websites`|

## <a name="mark-as-spam-settings"></a>Ustawienia oznaczania jako spamu

Poniższe ustawienia **Oznacz jako spam** asf ustawiają wartość SCL wykrytych wiadomości na 9, co odpowiada werdyktowi filtru spamu o wysokiej pewności i odpowiadającej mu akcji w zasadach ochrony przed spamem.

|Ustawienie zasad ochrony przed spamem|Opis|Dodano nagłówek X|
|---|---|---|
|**Puste wiadomości** <p> *MarkAsSpamEmptyMessages*|Wiadomości bez tematu, treści wiadomości i załączników są oznaczane jako spam o dużej pewności.|`X-CustomSpam: Empty Message`|
|**Tagi osadzone w języku HTML** <p> *MarkAsSpamEmbedTagsInHtml*|Wiadomość z tagami `<embed>` HTML jest oznaczana jako spam o dużej pewności. <p> Ten tag umożliwia osadzanie różnych rodzajów dokumentów w dokumencie HTML (na przykład dźwięków, klipów wideo lub obrazów).|`X-CustomSpam: Embed tag in html`|
|**Język JavaScript lub VBScript w języku HTML** <p> *MarkAsSpamJavaScriptInHtml*|Wiadomości z kodem JavaScript lub Visual Basic Script Edition w formacie HTML są oznaczane jako spam o dużej pewności. <p> Te języki skryptów są używane w wiadomościach e-mail w celu automatycznego wykonywania określonych akcji.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**Tagi formularzy w języku HTML** <p> *MarkAsSpamFormTagsInHtml*|Wiadomości zawierające tagi `<form>` HTML są oznaczane jako spam o dużej pewności. <p> Ten tag służy do tworzenia formularzy witryny sieci Web. Ogłoszenia e-mail często zawierają ten tag w celu pozyskiwania informacji od adresata.|`X-CustomSpam: Form tag in html`|
|**Znaczniki ramki lub elementu iframe w języku HTML** <p> *MarkAsSpamFramesInHtml*|Wiadomości zawierające tagi `<frame>` HTML `<iframe>` są oznaczane jako spam o dużej pewności. <p> Te tagi są używane w wiadomościach e-mail do formatowania strony w celu wyświetlania tekstu lub grafiki.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**Usterki sieci Web w języku HTML** <p> *MarkAsSpamWebBugsInHtml*|Błąd *sieci Web* (nazywany także sygnałem nawigacyjnym sieci *Web*) to element graficzny (często o rozmiarze jednego piksela na jeden piksel) używany w wiadomościach e-mail w celu określenia, czy wiadomość została odczytana przez adresata. <p> Wiadomości zawierające usterki sieci Web są oznaczane jako spam o dużej pewności. <p> W biuletynach może być konieczne korzystanie z błędów internetowych, chociaż wielu z nich uznaje to za naruszenie prywatności. |`X-CustomSpam: Web bug`|
|**Tagi obiektów w języku HTML** <p> *MarkAsSpamObjectTagsInHtml*|Wiadomości zawierające tagi `<object>` HTML są oznaczane jako spam o dużej pewności. <p> Ten tag umożliwia wtyczkom i aplikacjom uruchamianie ich w oknie języka HTML.|`X-CustomSpam: Object tag in html`|
|**Wyrazy poufne** <p> *MarkAsSpamSensitiveWordList*|Firma Microsoft przechowuje dynamiczną, ale nieedytowalna listę wyrazów skojarzonych z potencjalnie obraźliwymi wiadomościami. <p> Wiadomości zawierające wyrazy z poufnej listy wyrazów w temacie lub w treści wiadomości są oznaczane jako spam o dużej pewności.|`X-CustomSpam: Sensitive word in subject/body`|
|**Rekord SPF: trudno nie powieść** <p> *MarkAsSpamSpfRecordOrdFail*|Wiadomości wysyłane z adresu IP, który nie jest określony w rekordzie SPF Sender Policy Framework (SPF) w systemie DNS dla źródłowej domeny poczty e-mail są oznaczane jako spam o dużej pewności. <p> Tryb testowania nie jest dostępny w przypadku tego ustawienia.|`X-CustomSpam: SPF Record Fail`|

Poniższe ustawienia **Oznacz jako spam** (AsF) ustawiają wartość SCL wykrytych wiadomości na 6, która odpowiada  werdyktowi filtru spamu i odpowiadającej mu akcji w zasadach ochrony przed spamem.

|Ustawienie zasad ochrony przed spamem|Opis|Dodano nagłówek X|
|---|---|---|
|**Trudno nie można przefiltrować identyfikatora nadawcy** <p> *MarkAsSpamFromAddressAuthFail*|Wiadomości, których trudno nie sprawdzić warunkowego identyfikatora nadawcy, są oznaczane jako spam. <p> To ustawienie łączy sprawdzanie SPF z sprawdzaniem identyfikatora nadawcy w celu ochrony przed nagłówkami wiadomości, które zawierają nadawców podszyty. <p> Tryb testowania nie jest dostępny w przypadku tego ustawienia.|`X-CustomSpam: SPF From Record Fail`|
|**Backscatter** <p> *MarkAsSpamNdrBackscatter*|*Wiadomość typu backscatter* to bezużyteczne raporty o niedo dostarczenia (nazywane również raportami o niedo dostarczenia lub wiadomościach odsuwu) spowodowane przez podszyte nadawców w wiadomościach e-mail. Aby uzyskać więcej informacji, zobacz [Wiadomości backscatter i EOP](backscatter-messages-and-eop.md). <p> Nie musisz konfigurować tego ustawienia w następujących środowiskach, ponieważ są dostarczane wiarygodne konta OND, a wiadomość typu backscatter jest oznaczana jako spam: <ul><li>Microsoft 365 firm, które Exchange Online skrzynki pocztowe.</li><li>Lokalne organizacje poczty e-mail, do których *przekierowywają wychodzące wiadomości* e-mail za pośrednictwem usługi EOP.</li></ul> <p> W autonomicznych środowiskach usługi EOP, które chronią przychodzące wiadomości e-mail do lokalnych skrzynek pocztowych, włączenie lub wyłączenie tego ustawienia ma następujący wynik: <ul><li> **Wł**.: Są dostarczane wiarygodne wiadomości ondr, a wiadomość typu backscatter jest oznaczana jako spam.</li><li>**Wyłączone**: Normalne filtry wiadomości e-mail i wiadomości typu backscatter przejść przez normalne filtrowanie spamu. Większość legalnych wiadomości ondr zostanie dostarczona do pierwotnego nadawcy wiadomości. Niektóre (ale nie wszystkie) wiadomości typu backscatter są oznaczane jako spam. Z definicji wiadomości backscatter mogą być dostarczane tylko do nadawcy sfałszowanego, a nie do pierwotnego nadawcy.</li></ul> <p> Tryb testowania nie jest dostępny w przypadku tego ustawienia.|`X-CustomSpam: Backscatter NDR`|
