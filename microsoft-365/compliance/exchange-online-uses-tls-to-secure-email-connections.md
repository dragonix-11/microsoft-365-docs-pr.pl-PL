---
title: Jak Exchange Online poczty e-mail przy Exchange Online TLS (Transport Layer Security)
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/08/2021
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4cde0cda-3430-4dc0-b489-f2c0736c929f
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: Dowiedz się, Exchange Online i Microsoft 365 używać zabezpieczeń TLS (Transport Layer Security) i funkcji przesyłania dalej (Forward Secrecy) do zabezpieczania komunikacji za pomocą poczty e-mail. Uzyskaj też informacje na temat certyfikatu wystawionego przez firmę Microsoft dla Exchange Online.
ms.openlocfilehash: 1caf4a8425f4a8e7c340e8a52d785027e99a1618
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "62998144"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>Jak Exchange Online usługi TLS do zabezpieczania połączeń e-mail

Dowiedz się, Exchange Online i Microsoft 365 używać zabezpieczeń TLS (Transport Layer Security) i funkcji przesyłania dalej (Forward Secrecy) do zabezpieczania komunikacji za pomocą poczty e-mail. Zawiera również informacje o certyfikacie wystawionym przez firmę Microsoft dla Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>Podstawowe informacje o adresach TLS Microsoft 365 i Exchange Online

Transport Layer Security (TLS) i SSL (wcześniej TLS) to protokoły kryptograficzne zabezpieczające komunikację przez sieć przy użyciu certyfikatów zabezpieczeń w celu zaszyfrowania połączenia między komputerami. TLS to Secure Sockets Layer (SSL) i jest często nazywane SSL 3.1. Exchange Online usługi TLS do szyfrowania połączeń między serwerami Exchange i połączeniami między Exchange serwerami Exchange i innymi serwerami, takimi jak lokalne serwery poczty Exchange lub serwery poczty adresatów. Po zaszyfrowanym połączeniu wszystkie dane wysyłane przez to połączenie są wysyłane przez zaszyfrowany kanał. Jeśli jednak przesyłasz dalej wiadomość wysłaną za pośrednictwem połączenia szyfrowanego TLS, ta wiadomość nie musi być zaszyfrowana. Usługa TLS nie szyfruje wiadomości, a jedynie połączenie.
  
Jeśli chcesz zaszyfrować wiadomość, użyj technologii szyfrowania, która szyfruje zawartość wiadomości. Możesz na przykład użyć szyfrowania wiadomości Office lub S/MIME. Aby [uzyskać informacje](email-encryption.md) na temat szyfrowania wiadomości w Office 365, zobacz Szyfrowanie wiadomości e-Office 365 i Szyfrowanie wiadomości usługi Office 365 [(OME](ome.md)).
  
Korzystaj z usługi TLS w sytuacjach, w których chcesz skonfigurować bezpieczny kanał korespondencji między firmą Microsoft a Twoją organizacją lokalną lub inną organizacją, taką jak partner. Exchange Online zawsze próbuje użyć najpierw TLS do zabezpieczenia poczty e-mail, ale nie może to zrobić, jeśli inna strona nie oferuje zabezpieczeń TLS. Czytaj dalej, aby dowiedzieć się, jak można zabezpieczyć całą pocztę do serwerów lokalnych lub ważnych partnerów za pomocą *łączników*.

W celu zapewnienia najlepszego w swojej klasie szyfrowania dla klientów firma Microsoft posiada przestarzałe wersje 1.0 i 1.1 usługi Transport Layer Security (TLS) w wersji [Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) i [Office 365 GCC](tls-1-2-in-office-365-gcc.md). Można jednak nadal korzystać z nieszyfrowanego połączenia SMTP bez użycia protokołu TLS. Nie zalecamy transmisji wiadomości e-mail bez szyfrowania.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>Jak Exchange Online TLS między Exchange Online klientami

Exchange Online zawsze szyfrują połączenia z innymi Exchange Online w naszych centrach danych przy użyciu szyfrowania TLS 1.2. Gdy wysyłasz wiadomość do adresata w Twojej organizacji, usługa Exchange Online wysyła tę wiadomość automatycznie za pośrednictwem zaszyfrowanego połączenia przy użyciu TLS. Exchange Online wysyła także wiadomości e-mail wysyłane do innych klientów za pośrednictwem zaszyfrowanych połączeń przy użyciu usługi TLS, które są zabezpieczone przy użyciu funkcji Przesyłania dalej.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Jak Microsoft 365 TLS między Microsoft 365 i zewnętrznymi, zaufanymi partnerami

Domyślnie w Exchange Online *TLS jest zawsze używana domyślną wartość TLS*. Opportunistic TLS oznacza, że program Exchange Online zawsze próbuje najpierw zaszyfrować połączenia przy użyciu najbezpieczniejszej wersji klucza TLS, Exchange Online następnie działa w dół listy szyfrów TLS, aż znajdzie ją, na którą obie strony mogą się zgadzać. Jeśli nie skonfigurowano programu Exchange Online w celu zapewnienia, że wiadomości do tego adresata muszą korzystać z bezpiecznych połączeń, domyślnie wiadomość zostanie wysłana bez szyfrowania, jeśli organizacja adresata nie obsługuje szyfrowania TLS. Dpowiedniowy TLS jest wystarczający dla większości firm. Jednak dla firm, które mają wymagania dotyczące zgodności z przepisami, na przykład medycznej, bankowej lub rządowej, możesz skonfigurować usługę Exchange Online, aby wymagać lub wymuszać TLS. Aby uzyskać instrukcje, [zobacz Konfigurowanie przepływu poczty e-mail przy użyciu łączników Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
Jeśli zdecydujesz się skonfigurować usługę TLS między organizacją a zaufaną organizacją partnerską, możesz Exchange Online używać wymuszanej usługi *TLS* do tworzenia zaufanych kanałów komunikacji. Wymuszona ochrona przed zagrożeniami (TLS) wymaga, aby Twoja organizacja partnerska Exchange Online uwierzytelniać się za pomocą certyfikatu zabezpieczeń w celu wysyłania do Ciebie poczty. Twój partner będzie musiał zarządzać własnymi certyfikatami. Exchange Online łączników w celu ochrony wiadomości wysyłanych przed nieautoryzowanym dostępem do dostawcy poczty e-mail adresata. Aby uzyskać informacje na temat konfigurowania przepływu poczty e-mail za pomocą łączników, zobacz Konfigurowanie przepływu poczty za [pomocą łączników w Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>TLS i wdrożenia Exchange Server hybrydowych

Jeśli zarządzasz wdrożeniem hybrydowym programu Exchange, na lokalnym serwerze Exchange musi zostać uwierzytelniony Microsoft 365 przy użyciu certyfikatu zabezpieczeń, aby wysyłać pocztę do adresatów, których skrzynki pocztowe znajdują się tylko w Office 365. W wyniku tego musisz zarządzać własnymi certyfikatami zabezpieczeń dla lokalnych serwerów Exchange serwerach. Ponadto należy bezpiecznie przechowywać i zachowywać te certyfikaty serwera. Aby uzyskać więcej informacji na temat zarządzania certyfikatami we wdrożeniach hybrydowych, zobacz [Wymagania dotyczące certyfikatów dla wdrożeń hybrydowych](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Jak skonfigurować wymuszaną wartość TLS dla Exchange Online w Office 365

W Exchange Online klientów w celu wymuszania pracy przez TLS w celu zabezpieczenia wszystkich wysłanych i otrzymywanych wiadomości e-mail należy skonfigurować więcej niż jeden łącznik, który wymaga usługi TLS. Potrzebujesz jednego łącznika dla wiadomości wysyłanych do skrzynek pocztowych użytkowników, a innego łącznika dla wiadomości wysyłanych ze skrzynek pocztowych użytkowników. Utwórz te łączniki w centrum Exchange administracyjnego w programie Office 365. Aby uzyskać instrukcje, [zobacz Konfigurowanie przepływu poczty e-mail przy użyciu łączników Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>Informacje o certyfikacie TLS dla Exchange Online

Informacje o certyfikacie używane przez Exchange Online opisano w poniższej tabeli. Jeśli partner biznesowy konfigurowania wymuszanej usługi TLS na serwerze poczty e-mail, musisz udostępnić temu partnerowi te informacje. Ze względów bezpieczeństwa nasze certyfikaty są od czasu do czasu zmieniane. Bieżący certyfikat jest ważny od 24 września 2020 r.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>Bieżące informacje o certyfikacie ważne od 24 września 2020 r.
  
| Atrybut | Value |
|:-----|:-----|
|Główny wystawca urzędu certyfikacji|DigiCert CA — 1|
|Nazwa certyfikatu|mail.protection.outlook.com|
|Organizacja|Microsoft Corporation|
|Jednostka organizacji|www.digicert.com|
|Siłę klucza certyfikatu|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>Uzyskiwanie dodatkowych informacji na temat usługi TLS, certyfikatów i Microsoft 365 pobierania certyfikatów

[Microsoft 365 szyfrowania i pobierania certyfikatów](encryption-office-365-certificate-chains.md)

[Microsoft 365 szyfrowania i pobierania certyfikatów — DOD i GCC High](encryption-office-365-certificate-chains-itar.md)

Aby uzyskać listę obsługiwanych pakietów cipher, zobacz [Informacje techniczne dotyczące szyfrowania](technical-reference-details-about-encryption.md).
  
[Konfigurowanie łączników w celu zapewnienia bezpiecznego przepływu poczty e-mail w organizacji partnerskiej](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Łączniki z rozszerzonymi zabezpieczeniami poczty e-mail](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Szyfrowanie w Microsoft 365](encryption.md)
