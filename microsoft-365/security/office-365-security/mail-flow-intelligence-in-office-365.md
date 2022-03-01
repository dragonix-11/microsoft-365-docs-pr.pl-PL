---
title: Inteligencja przepływu poczty
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: troubleshooting
ms.custom: ''
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c29f75e5-c16e-409e-a123-430691e38276
description: Administratorzy mogą uzyskać informacje na temat kodów błędów skojarzonych z dostarczaniem wiadomości przy użyciu łączników (nazywanych również analizą przepływu poczty e-mail).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 57d8a9ec9bb40961ecf0b53f52198bde00e8bc03
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021306"
---
# <a name="mail-flow-intelligence-in-eop"></a>Inteligencja przepływu poczty e-mail w u usługi EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

W organizacjach Microsoft 365 ze skrzynkami pocztowymi w organizacjach usługi Exchange Online lub autonomicznej usługi Exchange Online Protection (EOP) bez skrzynek pocztowych usługi Exchange Online zazwyczaj za pomocą łącznika można rozsyłać wiadomości e-mail z usługi EOP do lokalnego środowiska poczty e-mail. Za pomocą łącznika można również rozsyłać wiadomości z programu Microsoft 365 do organizacji partnerskiej. Gdy Microsoft 365 nie można dostarczyć tych wiadomości za pośrednictwem łącznika, są one w kolejce w Microsoft 365. Microsoft 365 będzie ponawiać próby dostarczenia dla każdej wiadomości przez 24 godziny. Po 24 godzinach wiadomość w kolejce wygaśnie, a wiadomość zostanie zwrócona pierwotnej nadawcy w raporcie o niedostarczeniu (nazywanym również raportem o niedostarczeniu lub wiadomością zwróconą).

Microsoft 365 generuje błąd, gdy nie można dostarczyć wiadomości za pomocą łącznika. Najbardziej typowe błędy i ich rozwiązania opisano w tym artykule. Zbiorczo błędy kolejkowania i powiadamiania o niedostarczanych wiadomościach wysyłanych za pomocą łączników są nazywane analizą _przepływu poczty e-mail_.

## <a name="error-code-450-44312-dns-query-failed"></a>Kod błędu: Nie powiodło się zapytanie DNS 450 4.4.312

Zazwyczaj ten błąd oznacza, że Microsoft 365 nawiązywał połączenie z hostem inteligentnym określonym na łączniku, ale zapytanie DNS w celu znalezienia adresów IP hosta inteligentnego nie powiodło się. Możliwe przyczyny tego błędu są takie:

- Występuje problem z usługą hostingu DNS Twojej domeny (strona, która utrzymuje autorytatywne serwery nazw Twojej domeny).

- Twoja domena niedawno wygasła, więc nie można pobrać rekordu MX.

- Rekord MX domeny niedawno się zmienił i na serwerach DNS nadal wcześniej były przechowywane informacje DNS dla Twojej domeny w pamięci podręcznej.

### <a name="how-do-i-fix-error-code-450-44312"></a>Jak naprawić kod błędu 450 4.4.312?

- We współpracy z usługą hostingu DNS określ i rozwiąż problem z domeną.

- Jeśli błąd pochodzi z Twojej organizacji partnerskiej (na przykład z usługi chmury innej firmy usługodawca), skontaktuj się z partnerem, aby rozwiązać ten problem.

## <a name="error-code-450-44315-connection-timed-out"></a>Kod błędu: Udano czas połączenia 450 4.4.315

Zazwyczaj oznacza to, Microsoft 365 nie może nawiązać połączenia z docelowym serwerem poczty e-mail. Szczegóły błędu wyjaśnią problem. Przykład:

- Twój lokalnych serwerów poczty e-mail jest zamknięty.

- W ustawieniach hosta inteligentnego łącznika występuje błąd, więc Microsoft 365 próbuje nawiązać połączenie z nieprawidłowym adresem IP.

### <a name="how-do-i-fix-error-code-450-44315"></a>Jak naprawić kod błędu 450 4.4.315?

- Dowiedz się, który scenariusz dotyczy Ciebie, i wprowadzić konieczne korekty. Jeśli na przykład przepływ poczty e-mail działa poprawnie i ustawienia łącznika nie zostały zmienione, należy sprawdzić lokalne środowisko poczty e-mail, aby sprawdzić, czy serwer jest u dołu lub czy w infrastrukturze sieciowej wpłynęły jakieś zmiany (na przykład zmieniono dostawców usług internetowych, więc masz teraz inne adresy IP).

- Jeśli błąd pochodzi z Twojej organizacji partnerskiej (na przykład z usługi chmury innej firmy usługodawca), skontaktuj się z partnerem, aby rozwiązać ten problem.

## <a name="error-code-450-44316-connection-refused"></a>Kod błędu: 450 4.4.316 Połączenie zostało odrzucone

Zazwyczaj ten błąd oznacza, Microsoft 365 wystąpił błąd połączenia podczas próby nawiązania połączenia z docelowym serwerem poczty e-mail. Prawdopodobną przyczyną tego błędu jest zablokowanie połączeń przez zaporę z Microsoft 365 IP. Ten błąd może też być projektowany, jeśli lokalna poczta e-mail została już całkowicie zmigrowana do Microsoft 365 i wyłączenia lokalnego środowiska poczty e-mail.

### <a name="how-do-i-fix-error-code-450-44316"></a>Jak naprawić kod błędu 450 4.4.316?

- Jeśli masz skrzynki pocztowe w środowisku lokalnym, musisz zmodyfikować ustawienia zapory, aby zezwolić na połączenia z adresów IP usługi Microsoft 365 na porcie TCP 25 z lokalnymi serwerami poczty e-mail. Aby uzyskać listę adresów IP Microsoft 365 IP, zobacz adresy URL Microsoft 365 [zakresów adresów IP](../../enterprise/urls-and-ip-address-ranges.md).

- Jeśli nie ma więcej wiadomości, które powinny być dostarczane do środowiska lokalnego,  kliknij pozycję Napraw teraz w alercie, aby Microsoft 365 natychmiast odrzucić wiadomości z nieprawidłowymi adresatami. Zmniejszy to ryzyko przekroczenia limitu przydziału dla nieprawidłowych adresatów w organizacji, co może mieć wpływ na normalne dostarczanie wiadomości. Możesz też ręcznie rozwiązać ten problem, instrukcje poniżej:

  - W centrum Exchange wyłącz lub usuń łącznik, który dostarcza pocztę e-mail Microsoft 365 do lokalnego środowiska poczty e-mail:

    1. W SAC w miejscu <https://admin.exchange.microsoft.com>przejdź do **łączników przepływu poczty e-mail**\>. Aby przejść bezpośrednio do strony **Łączniki** , użyj funkcji <https://admin.exchange.microsoft.com/#/connectors>.

    2. Wybierz łącznik z **wartością Office 365** i  **Wartością Aby** wartościować serwer poczty  e-mail Twojej organizacji, a następnie wykonaj jedną z następujących czynności:
       - Usuń łącznik, klikając **ikonę** ![Usuń usuń.](../../media/adf01106-cc79-475c-8673-065371c1897b.gif)
       - Wyłącz łącznik, klikając **ikonę** ![Edytuj.](../../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) i **czyszcząc pola włącz.**

  - Zmień zaakceptowaną domenę w Microsoft 365, która jest skojarzona z lokalnym środowiskiem poczty e-mail, z **przekazywania** wewnętrznego na **autorytatywny**. Aby uzyskać instrukcje, [zobacz Zarządzanie zaakceptowanymi domenami w Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).

  **Uwaga**: Zazwyczaj te zmiany dotyczą od 30 minut do jednej godziny. Po upływie jednej godziny upewnij się, że nie jest już wyświetlany komunikat o błędzie.

- Jeśli błąd pochodzi z Twojej organizacji partnerskiej (na przykład z usługi cloud usługodawca), musisz skontaktować się z partnerem, aby rozwiązać ten problem.

## <a name="error-code-450-44317-cannot-connect-to-remote-server"></a>Kod błędu: 450 4.4.317 Nie można połączyć się z serwerem zdalnym

Zazwyczaj ten błąd oznacza, że Microsoft 365 się z docelowym serwerem poczty e-mail, ale serwer odpowiedział z natychmiastowym błędem lub nie spełnia wymagań dotyczących połączenia. Szczegóły błędu wyjaśnią problem. Przykład:

- Docelowy serwer poczty e-mail odpowiedział z komunikatem o błędzie "Usługa jest dostępna", który wskazuje, że serwer nie może utrzymać komunikacji z usługą Microsoft 365.
- Łącznik jest skonfigurowany w taki sposób, aby wymagał TLS, ale docelowy serwer poczty e-mail nie obsługuje usługi TLS.

### <a name="how-do-i-fix-error-code-450-44317"></a>Jak naprawić kod błędu 450 4.4.317?

- Sprawdź ustawienia I certyfikaty usługi TLS na lokalnych serwerach poczty e-mail oraz ustawienia usługi TLS na łączniku.
- Jeśli błąd pochodzi z Twojej organizacji partnerskiej (na przykład z usługi cloud usługodawca), musisz skontaktować się z partnerem, aby rozwiązać ten problem.

## <a name="error-code-450-44318-connection-was-closed-abruptly"></a>Kod błędu: 450 4.4.318 Połączenie zostało nagle zamknięte

Zazwyczaj ten błąd oznacza, Microsoft 365 ma trudności z komunikacją z lokalnym środowiskiem poczty e-mail, dlatego połączenie zostało przerwane. Możliwe przyczyny tego błędu są takie:

- Zapora korzysta z reguł filtrowania pakietów SMTP i te reguły nie działają poprawnie.
- Lokalny serwer poczty e-mail nie działa poprawnie (na przykład usługa zawiesza się, ulega awarii lub zasoby systemowe są niskie), co powoduje przeoowanie czasu przez serwer i zamknięcie połączenia z Microsoft 365.
- Występują problemy z siecią między środowiskiem lokalnym a Microsoft 365.

### <a name="how-do-i-fix-error-code-450-44318"></a>Jak naprawić kod błędu 450 4.4.318?

- Dowiedz się, który scenariusz dotyczy Ciebie, i wprowadzić konieczne korekty.
- Jeśli przyczyną problemu są problemy z siecią między środowiskiem lokalnym a Microsoft 365, skontaktuj się z zespołem ds. sieci, aby rozwiązać ten problem.
- Jeśli błąd pochodzi z Twojej organizacji partnerskiej (na przykład z usługi cloud usługodawca), musisz skontaktować się z partnerem, aby rozwiązać ten problem.

## <a name="error-code-450-47320-certificate-validation-failed"></a>Kod błędu: Nie powiodło się sprawdzanie poprawności certyfikatu 450 4.7.320

Zazwyczaj ten błąd oznacza, Microsoft 365 wystąpił błąd podczas próby zweryfikowania certyfikatu docelowego serwera poczty e-mail. Szczegóły błędu będą wyjaśniać ten błąd. Przykład:

- Certyfikat wygasł
- Niezgodność podmiotu certyfikatu
- Certyfikat jest już nieprawidłowy

### <a name="how-do-i-fix-error-code-450-47320"></a>Jak naprawić kod błędu 450 4.7.320?

- Napraw certyfikat lub ustawienia na łączniku tak, aby można było dostarczać Microsoft 365 wiadomości w kolejce.
- Jeśli błąd pochodzi z Twojej organizacji partnerskiej (na przykład z usługi cloud usługodawca), musisz skontaktować się z partnerem, aby rozwiązać ten problem.

## <a name="other-error-codes"></a>Inne kody błędów

Microsoft 365 mają trudności z dostarczaniem wiadomości do lokalnego lub partnerskiego serwera poczty e-mail. Użyj informacji **o serwerze docelowym** w błędzie, aby zbadać problem w środowisku, lub zmodyfikuj łącznik w przypadku błędu konfiguracji.

Jeśli błąd pochodzi z Twojej organizacji partnerskiej (na przykład z usługi cloud usługodawca), musisz skontaktować się z partnerem, aby rozwiązać ten problem.
