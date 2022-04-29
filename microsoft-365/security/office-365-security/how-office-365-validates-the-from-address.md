---
title: Jak funkcja EOP weryfikuje adres Od, aby zapobiec wyłudzaniu informacji
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- OWC150
- MET150
ms.assetid: eef8408b-54d3-4d7d-9cf7-ad2af10b2e0e
ms.collection:
- M365-security-compliance
description: Administratorzy mogą dowiedzieć się więcej o typach adresów e-mail akceptowanych lub odrzucanych przez Exchange Online Protection (EOP) i Outlook.com, aby zapobiec wyłudzaniu informacji.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 92b7072e3127da71f423648c83fc94c17bed7caa
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131069"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>Jak funkcja EOP weryfikuje adres Od, aby zapobiec wyłudzaniu informacji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ataki wyłudzające informacje stanowią stałe zagrożenie dla dowolnej organizacji poczty e-mail. Oprócz [używania sfałszowanych (sfałszowanych) adresów e-mail nadawcy](anti-spoofing-protection.md) osoby atakujące często używają wartości w polu Adres od, które naruszają standardy internetowe. Aby zapobiec wyłudzaniu informacji tego typu, Exchange Online Protection (EOP) i Outlook.com wymagają teraz, aby komunikaty przychodzące zawierały adres Z zgodny z RFC zgodnie z opisem w tym artykule. To wymuszanie zostało włączone w listopadzie 2017 r.

**Uwagi**:

- Jeśli regularnie otrzymujesz wiadomości e-mail od organizacji, które mają źle sformułowane adresy Z zgodnie z opisem w tym artykule, zachęć te organizacje do zaktualizowania serwerów poczty e-mail w celu zachowania zgodności z nowoczesnymi standardami zabezpieczeń.

- Te wymagania nie mają wpływu na powiązane pole nadawcy (używane przez usługę Wyślij w imieniu i listy wysyłkowe). Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [Co mamy na myśli, gdy odwołujemy się do "nadawcy" wiadomości e-mail?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email).

## <a name="an-overview-of-email-message-standards"></a>Omówienie standardów wiadomości e-mail

Standardowa wiadomość e-mail SMTP składa się z *koperty wiadomości* i zawartości wiadomości. Koperta wiadomości zawiera informacje wymagane do przesyłania i dostarczania komunikatu między serwerami SMTP. Zawartość wiadomości zawiera pola nagłówka wiadomości (łącznie nazywane *nagłówkiem komunikatu*) i treść komunikatu. Koperta komunikatu jest opisana w dokumencie [RFC 5321](https://tools.ietf.org/html/rfc5321), a nagłówek komunikatu jest opisany w dokumencie [RFC 5322](https://tools.ietf.org/html/rfc5322). Adresaci nigdy nie widzą rzeczywistej koperty wiadomości, ponieważ jest ona generowana przez proces transmisji komunikatów i w rzeczywistości nie jest częścią wiadomości.

- Adres `5321.MailFrom` (znany również jako adres **MAIL FROM** , nadawca P1 lub nadawca koperty) to adres e-mail używany podczas transmisji wiadomości przez protokół SMTP. Ten adres e-mail jest zwykle rejestrowany w polu nagłówek **Return-Path** w nagłówku wiadomości (chociaż nadawca może wyznaczyć inny adres **e-mail ze ścieżką powrotną** ).

- Adres `5322.From` (znany również jako adres od lub nadawca P2) to adres e-mail w polu **Nagłówek od** i jest adresem e-mail nadawcy wyświetlanym w klientach poczty e-mail. Adres Od jest przedmiotem wymagań w tym artykule.

Adres From jest definiowany szczegółowo w kilku punktach Z (na przykład RFC 5322 sekcje 3.2.3, 3.4 i 3.4.1 i [RFC 3696](https://tools.ietf.org/html/rfc3696)). Istnieje wiele odmian dotyczących adresowania i tego, co jest uważane za prawidłowe lub nieprawidłowe. Aby zachować prostotę, zalecamy następujący format i definicje:

`From: "Display Name" <EmailAddress>`

- **Nazwa wyświetlana**: opcjonalna fraza opisująca właściciela adresu e-mail.

  - Zalecamy, aby zawsze umieszczać nazwę wyświetlaną w podwójnym cudzysłowie ("), jak pokazano poniżej. Jeśli nazwa wyświetlana zawiera przecinek, _należy ująć_ ciąg w podwójny cudzysłów na RFC 5322.
  - Jeśli adres Od zawiera nazwę wyświetlaną, wartość EmailAddress musi być ujęta w nawiasy kątowe (< >), jak pokazano poniżej.
  - Firma Microsoft zdecydowanie zaleca wstawienie miejsca między nazwą wyświetlaną a adresem e-mail.

- **EmailAddress**: adres e-mail używa formatu `local-part@domain`:

  - **local-part**: ciąg identyfikujący skrzynkę pocztową skojarzoną z adresem. Ta wartość jest unikatowa w domenie. Często używana jest nazwa użytkownika lub identyfikator GUID właściciela skrzynki pocztowej.
  - **domena**: w pełni kwalifikowana nazwa domeny (FQDN) serwera poczty e-mail hostującego skrzynkę pocztową określoną przez lokalną część adresu e-mail.

  Oto kilka dodatkowych zagadnień dotyczących wartości EmailAddress:

  - Tylko jeden adres e-mail.
  - Zalecamy, aby nie oddzielać nawiasów kątowych spacjami.
  - Nie dołączaj dodatkowego tekstu po adresie e-mail.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Przykłady prawidłowych i nieprawidłowych adresów z

Następujące adresy e-mail z są prawidłowe:

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Nie zaleca się, ponieważ istnieją spacje między nawiasami kątowymi a adresem e-mail).

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` (Nie jest to zalecane, ponieważ nazwa wyświetlana nie jest ujęta w podwójny cudzysłów).

Następujące adresy e-mail z są nieprawidłowe:

- **Nie z adresu**: niektóre automatyczne komunikaty nie zawierają adresu Od. W przeszłości, gdy Microsoft 365 lub Outlook.com odebrało komunikat bez adresu Od, usługa dodała następujące domyślne ustawienie Od: adres, aby komunikat był dostarczany:

  `From: <>`

  Teraz komunikaty z pustym adresem Od nie są już akceptowane.

- `From: Microsoft 365 sender@contoso.com` (Nazwa wyświetlana jest obecna, ale adres e-mail nie jest ujęty w nawiasy kątowe).

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` (Tekst po adresie e-mail).

- `From: Sender, Example <sender.example@contoso.com>` (Nazwa wyświetlana zawiera przecinek, ale nie jest ujęta w podwójny cudzysłów).

- `From: "Microsoft 365 <sender@contoso.com>"` (Cała wartość jest niepoprawnie ujęta w podwójny cudzysłów).

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` (Nazwa wyświetlana jest obecna, ale adres e-mail nie jest ujęty w nawiasy kątowe).

- `From: Microsoft 365<sender@contoso.com>` (Brak miejsca między nazwą wyświetlaną a lewym nawiasem kwadratowym).

- `From: "Microsoft 365"<sender@contoso.com>` (Brak miejsca między zamykaniem podwójnego cudzysłowu a lewym nawiasem kątowym).

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Pomijanie automatycznych odpowiedzi do domeny niestandardowej

Nie można użyć wartości `From: <>` do pominięcia automatycznych odpowiedzi. Zamiast tego należy skonfigurować rekord MX o wartości null dla domeny niestandardowej. Automatyczne odpowiedzi (i wszystkie odpowiedzi) są naturalnie pomijane, ponieważ nie ma opublikowanego adresu, na który serwer odpowiedzi może wysyłać komunikaty.

- Wybierz domenę poczty e-mail, która nie może odbierać wiadomości e-mail. Jeśli na przykład domena podstawowa jest contoso.com, możesz wybrać noreply.contoso.com.

- Rekord MX o wartości null dla tej domeny składa się z jednego okresu.

Przykład:

```text
noreply.contoso.com IN MX .
```

Aby uzyskać więcej informacji na temat konfigurowania rekordów MX, zobacz [Tworzenie rekordów DNS u dowolnego dostawcy hostingu DNS dla Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

Aby uzyskać więcej informacji na temat publikowania wartości null MX, zobacz [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Zastępowanie z wymuszania adresu

Aby pominąć wymagania dotyczące adresu Od dla przychodzącej poczty e-mail, można użyć listy dozwolonych adresów IP (filtrowania połączeń) lub reguł przepływu poczty (znanych również jako reguły transportu), zgodnie z opisem w artykule [Tworzenie list bezpiecznych nadawców w Microsoft 365](create-safe-sender-lists-in-office-365.md).

Nie można zastąpić wymagań dotyczących adresu Od dla wychodzącej poczty e-mail wysyłanej z Microsoft 365. Ponadto Outlook.com nie zezwala na przesłonięcia jakiegokolwiek rodzaju, nawet za pośrednictwem pomocy technicznej.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Inne sposoby zapobiegania i ochrony przed cyberprzestępczością w Microsoft 365

Aby uzyskać więcej informacji na temat wzmacniania organizacji przed wyłudzaniem informacji, spamem, naruszeniami danych i innymi zagrożeniami, zobacz [Top 10 ways to secure Microsoft 365 for business plans (10 najlepszych sposobów zabezpieczania Microsoft 365 dla planów biznesowych](../../admin/security-and-compliance/secure-your-business-data.md)).
