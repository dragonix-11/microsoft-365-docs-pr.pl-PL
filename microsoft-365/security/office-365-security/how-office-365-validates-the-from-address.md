---
title: Jak program EOP sprawdza poprawność adresu Od w celu zapobiegania próbom wyłudzania informacji
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
description: Administratorzy mogą dowiedzieć się więcej o typach adresów e-mail akceptowanych lub odrzucanych przez usługę Exchange Online Protection (EOP) i witrynę Outlook.com, aby zapobiec próbom wyłudzania informacji.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 412b6eb7045051c21a88c8b4b2ba5e80a06832dd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986438"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>Jak program EOP sprawdza poprawność adresu Od w celu zapobiegania próbom wyłudzania informacji

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Ataki służące do wyłudzania informacji stanowią ciągłe zagrożenie dla każdej organizacji poczty e-mail. Oprócz adresów e-mail sfałszowanych (sfałszowanych [)](anti-spoofing-protection.md) nadawców atakujący często używają wartości w adresie Nadawca, które naruszają standardy internetowe. Aby zapobiec wyłudzaniu informacji tego typu, Exchange Online Protection (EOP) i Outlook.com wymagają teraz, aby wiadomości przychodzące zawierały adres Od zgodny ze standardem RFC zgodnie z opisem w tym artykule. Wymuszanie zostało włączone w listopadzie 2017 r.

**Uwagi**:

- Jeśli regularnie otrzymujesz wiadomości e-mail od organizacji, które mają adresy Od w sposób opisany w tym artykule, zachęć te organizacje do zaktualizowania serwerów poczty e-mail w celu zapewnienia zgodności z nowoczesnymi standardami zabezpieczeń.

- Te wymagania nie mają wpływu na powiązane pole Nadawca (używane przez pole Wyślij w imieniu i listy adresowe). Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: Co mamy na myśli, gdy używamy "nadawcy [" wiadomości e-mail?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email).

## <a name="an-overview-of-email-message-standards"></a>Omówienie standardów wiadomości e-mail

Standardowa wiadomość e-mail SMTP składa się z *koperty* wiadomości i jej zawartości. Koperta wiadomości zawiera informacje wymagane do przekazywania i dostarczania wiadomości między serwerami SMTP. Zawartość wiadomości zawiera pola nagłówka wiadomości (zbiorczo *nazywane nagłówkiem* wiadomości) i treść wiadomości. Koperta wiadomości jest opisana w [dokumencie RFC 5321](https://tools.ietf.org/html/rfc5321), a nagłówek wiadomości jest opisany w dokumencie [RFC 5322](https://tools.ietf.org/html/rfc5322). Adresaci nigdy nie widzą rzeczywistej koperty wiadomości, ponieważ jest generowana przez proces transmisji wiadomości i w rzeczywistości nie jest ona częścią wiadomości.

- Adres `5321.MailFrom` (znany także jako adres **MAIL FROM** , nadawca P1 lub nadawca koperty) to adres e-mail używany w transmisji SMTP wiadomości. Ten adres e-mail jest zwykle rejestrowany w polu nagłówka **return-ścieżka** w nagłówku wiadomości (chociaż nadawca może wyznaczyć inny adres **e-mail** ze ścieżką zwrotną).

- Nadawca (nazywany również nadawcą Od lub P2) jest adresem e-mail w polu  nagłówka Od i jest adresem e-mail nadawcy wyświetlanym w klientach poczty e-mail.`5322.From` W centrum wymagań w tym artykule znajduje się adres Od.

Adres Od jest zdefiniowany szczegółowo w kilku zapytaniech ofertowych (na przykład WFC 5322 sekcjach 3.2.3, 3.4 i 3.4.1 i [RFC 3696](https://tools.ietf.org/html/rfc3696)). Istnieje wiele odmian adresowania oraz to, co jest uznawane za prawidłowe lub nieprawidłowe. Aby zachować prostotę, zalecamy następujący format i definicje:

`From: "Display Name" <EmailAddress>`

- **Nazwa wyświetlana**: opcjonalna fraza opisującą właściciela adresu e-mail.

  - Zalecamy, aby zawsze ująć nazwę wyświetlaną w podwójny cudzysłów ("), jak pokazano. Jeśli nazwa wyświetlana zawiera przecinek, należy  ująć ten ciąg w cudzysłów podwójny na kod RFC 5322.
  - Jeśli adres Od zawiera nazwę wyświetlaną, wartość EmailAddress musi być ujęta w nawiasy kwadratowe (< >), jak pokazano.
  - Firma Microsoft zdecydowanie zaleca wstawienie spacji między nazwą wyświetlaną a adresem e-mail.

- **EmailAddress**: Adres e-mail ma format `local-part@domain`:

  - **local-part**: ciąg identyfikujący skrzynkę pocztową skojarzoną z adresem. Ta wartość jest unikatowa w obrębie domeny. Często jest używana nazwa użytkownika lub identyfikator GUID właściciela skrzynki pocztowej.
  - **domena**: w pełni kwalifikowana nazwa domeny (FQDN) serwera poczty e-mail hostowego skrzynkę pocztową identyfikowaną przez lokalną część adresu e-mail.

  Oto kilka dodatkowych kwestii, które należy uwzględnić w wartości EmailAddress:

  - Tylko jeden adres e-mail.
  - Zalecamy, aby nie rozdzielać nawiasów kątowych spacjami.
  - Nie dołączaj dodatkowego tekstu po adresie e-mail.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Przykłady prawidłowych i nieprawidłowych adresów Od

Prawidłowe są następujące adresy e-mail z adresu e-mail:

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Zalecane, ponieważ istnieją spacje między nawiasami kątowymi a adresem e-mail).

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` Ta nazwa nie jest zalecana, ponieważ nazwa wyświetlana nie jest ujęta w cudzysłów.

Następujące adresy e-mail od są nieprawidłowe:

- **Brak adresu od**: niektóre automatyczne wiadomości nie zawierają adresu Od. W przeszłości, gdy Microsoft 365 lub Outlook.com odebrano wiadomość bez adresu Od, usługa dodała następujący domyślny adres od: w celu dostarczania wiadomości:

  `From: <>`

  Teraz wiadomości z pustym adresem Od nie będą już akceptowane.

- `From: Microsoft 365 sender@contoso.com` (Nazwa wyświetlana jest obecna, ale adres e-mail nie jest ujęty w nawiasy kątowe).

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` Tekst po adresie e-mail.

- `From: Sender, Example <sender.example@contoso.com>` (Nazwa wyświetlana zawiera przecinek, ale nie jest ujęta w cudzysłów).

- `From: "Microsoft 365 <sender@contoso.com>"` (Cała wartość jest nieprawidłowo ujęta w cudzysłów).

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` (Nazwa wyświetlana jest obecna, ale adres e-mail nie jest ujęty w nawiasy kątowe).

- `From: Microsoft 365<sender@contoso.com>` (Brak odstępu między nazwą wyświetlaną a lewym nawiasem kątowym).

- `From: "Microsoft 365"<sender@contoso.com>` (Brak odstępu między zamykającym podwójnym cudzysłowem a lewym nawiasem kątowym).

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Pomijanie automatycznych odpowiedzi w domenie niestandardowej

Tej wartości nie można użyć do `From: <>` pomiń automatycznych odpowiedzi. Zamiast tego należy skonfigurować pusty rekord MX dla domeny niestandardowej. Automatyczne odpowiedzi (i wszystkie odpowiedzi) są w sposób naturalny pomijane, ponieważ nie ma opublikowanego adresu, na który serwer odpowiada, na który mogą wysyłać wiadomości.

- Wybierz domenę poczty e-mail, która nie może odbierać poczty e-mail. Jeśli na przykład domena podstawowa jest contoso.com, możesz wybrać pozycję noreply.contoso.com.

- Pusty rekord MX dla tej domeny składa się z jednego okresu.

Przykład:

```text
noreply.contoso.com IN MX .
```

Aby uzyskać więcej informacji na temat konfigurowania rekordów MX, zobacz [Tworzenie rekordów DNS dla](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) Microsoft 365.

Aby uzyskać więcej informacji na temat publikowania rekordu MX wartości null, zobacz [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Override From address enforcement

Aby obejść wymagania dotyczące adresu Od dla przychodzącej poczty e-mail, możesz użyć listy adresów IP (filtrowania połączeń) lub reguł przepływu poczty (nazywanych także regułami transportu), jak opisano w artykule Tworzenie list bezpiecznych nadawców w programie [Microsoft 365](create-safe-sender-lists-in-office-365.md).

Nie możesz zastąpić wymagań dotyczących adresu Od dla wychodzących wiadomości e-mail, które wysyłasz z Microsoft 365. Ponadto w Outlook.com nie zezwalają na zastępowanie jakichkolwiek zastąpień, nawet za pośrednictwem pomocy technicznej.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Inne sposoby zapobiegania cyberprzestępczości i ochrony przed cyberprzestępczością w Microsoft 365

Aby uzyskać więcej informacji na temat sposobu, w jaki można wzmocnić organizację przed wyłudzaniem informacji, spamem, naruszeniem danych i innymi zagrożeniami, zobacz [10](../../admin/security-and-compliance/secure-your-business-data.md) najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm.