---
title: Jak Exchange Online używa protokołu TLS do zabezpieczania połączeń poczty e-mail
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
description: Dowiedz się, jak Exchange Online i microsoft 365 używają protokołu Transport Layer Security (TLS) i funkcji forward Secrecy (FS) do zabezpieczania komunikacji e-mail. Uzyskaj również informacje o certyfikacie wystawionym przez firmę Microsoft dla Exchange Online.
ms.openlocfilehash: 93f71e38e3063aeec0c423dbfea25ac463a3e46f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641565"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>Jak Exchange Online używa protokołu TLS do zabezpieczania połączeń poczty e-mail

Dowiedz się, jak Exchange Online i microsoft 365 używają protokołu Transport Layer Security (TLS) i funkcji forward Secrecy (FS) do zabezpieczania komunikacji e-mail. Zawiera również informacje o certyfikacie wystawionym przez firmę Microsoft dla Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>Podstawy protokołu TLS dla platformy Microsoft 365 i Exchange Online

Transport Layer Security (TLS) i SSL, które pojawiły się przed protokołem TLS, to protokoły kryptograficzne, które zabezpieczają komunikację za pośrednictwem sieci przy użyciu certyfikatów zabezpieczeń do szyfrowania połączenia między komputerami. Protokół TLS zastępuje protokół Secure Sockets Layer (SSL) i jest często nazywany protokołem SSL 3.1. Exchange Online używa protokołu TLS do szyfrowania połączeń między serwerami programu Exchange a połączeniami między serwerami programu Exchange i innymi serwerami, takimi jak lokalne serwery programu Exchange lub serwery poczty adresatów. Po zaszyfrowanym połączeniu wszystkie dane wysyłane za pośrednictwem tego połączenia są wysyłane za pośrednictwem zaszyfrowanego kanału. Jeśli jednak przekażesz komunikat, który został wysłany za pośrednictwem połączenia zaszyfrowanego za pomocą protokołu TLS, ten komunikat nie musi być szyfrowany. Protokół TLS nie szyfruje komunikatu, tylko połączenie.
  
Jeśli chcesz zaszyfrować komunikat, użyj technologii szyfrowania, która szyfruje zawartość komunikatu. Na przykład można użyć Szyfrowanie wiadomości w Microsoft Purview lub S/MIME. Aby uzyskać informacje na temat szyfrowania wiadomości w Office 365, zobacz [Szyfrowanie wiadomości e-mail w Office 365](email-encryption.md) i [Szyfrowanie komunikatów](ome.md).
  
Użyj protokołu TLS w sytuacjach, w których chcesz skonfigurować bezpieczny kanał korespondencji między firmą Microsoft a organizacją lokalną lub inną organizacją, taką jak partner. Exchange Online zawsze próbuje najpierw użyć protokołu TLS w celu zabezpieczenia poczty e-mail, ale nie może, jeśli druga strona nie oferuje zabezpieczeń protokołu TLS. Czytaj dalej, aby dowiedzieć się, jak zabezpieczyć całą pocztę do serwerów lokalnych lub ważnych partnerów przy użyciu *łączników*.

Aby zapewnić naszym klientom najlepsze w klasie szyfrowanie, firma Microsoft ma przestarzałe wersje TLS (Transport Layer Security) w wersjach 1.0 i 1.1 w [Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) i [Office 365 GCC](tls-1-2-in-office-365-gcc.md). Można jednak nadal używać niezaszyfrowanego połączenia SMTP bez żadnego protokołu TLS. Nie zalecamy transmisji wiadomości e-mail bez szyfrowania.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>Jak Exchange Online używa protokołu TLS między klientami Exchange Online

Exchange Online serwery zawsze szyfrują połączenia z innymi serwerami Exchange Online w naszych centrach danych za pomocą protokołu TLS 1.2. Gdy wysyłasz wiadomość do adresata w organizacji, Exchange Online automatycznie wysyła komunikat za pośrednictwem zaszyfrowanego połączenia przy użyciu protokołu TLS. Exchange Online wysyła również wiadomości e-mail wysyłane do innych klientów za pośrednictwem zaszyfrowanych połączeń przy użyciu protokołu TLS zabezpieczonego przy użyciu funkcji Przekazywania tajemnicy.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Jak platforma Microsoft 365 korzysta z protokołu TLS między platformą Microsoft 365 a zewnętrznymi, zaufanymi partnerami

Domyślnie Exchange Online zawsze używa *oportunistycznego protokołu TLS*. Oportunistyczny protokół TLS oznacza, Exchange Online zawsze próbuje zaszyfrować połączenia z najbezpieczniejszą wersją protokołu TLS, a następnie działa w dół listy szyfrów TLS, dopóki nie znajdzie takiego, na który obie strony mogą się zgodzić. Jeśli nie skonfigurowano Exchange Online w celu zapewnienia, że komunikaty do tego adresata muszą korzystać z bezpiecznych połączeń, domyślnie komunikat zostanie wysłany bez szyfrowania, jeśli organizacja adresata nie obsługuje szyfrowania TLS. Oportunistyczny protokół TLS jest wystarczający dla większości firm. Jednak w przypadku firm, które mają wymagania dotyczące zgodności, takie jak organizacje medyczne, bankowe lub rządowe, można skonfigurować Exchange Online, aby wymagać lub wymuszać protokół TLS. Aby uzyskać instrukcje, zobacz [Konfigurowanie przepływu poczty przy użyciu łączników w Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
Jeśli zdecydujesz się skonfigurować protokół TLS między organizacją a zaufaną organizacją partnerskią, Exchange Online może używać *wymuszonego protokołu TLS* do tworzenia zaufanych kanałów komunikacji. Wymuszony protokół TLS wymaga od organizacji partnerskiej uwierzytelnienia w celu Exchange Online przy użyciu certyfikatu zabezpieczeń w celu wysyłania wiadomości e-mail. Twój partner będzie musiał zarządzać własnymi certyfikatami. Exchange Online używa łączników do ochrony wiadomości wysyłanych przed nieautoryzowanym dostępem przed ich przybyciem do dostawcy poczty e-mail adresata. Aby uzyskać informacje na temat konfigurowania przepływu poczty za pomocą łączników, zobacz [Konfigurowanie przepływu poczty przy użyciu łączników w Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>Wdrożenia protokołu TLS i Exchange Server hybrydowego

Jeśli zarządzasz wdrożeniem hybrydowym programu Exchange, lokalny serwer Exchange musi uwierzytelnić się na platformie Microsoft 365 przy użyciu certyfikatu zabezpieczeń w celu wysyłania wiadomości e-mail do adresatów, których skrzynki pocztowe znajdują się tylko w Office 365. W związku z tym należy zarządzać własnymi certyfikatami zabezpieczeń dla lokalnych serwerów programu Exchange. Należy również bezpiecznie przechowywać i obsługiwać te certyfikaty serwera. Aby uzyskać więcej informacji na temat zarządzania certyfikatami we wdrożeniach hybrydowych, zobacz [Wymagania dotyczące certyfikatów dla wdrożeń hybrydowych](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Jak skonfigurować wymuszony protokół TLS dla Exchange Online w Office 365

W przypadku Exchange Online klientów, aby wymuszony protokół TLS działał w celu zabezpieczenia wszystkich wysłanych i odebranych wiadomości e-mail, należy skonfigurować więcej niż jeden łącznik wymagający protokołu TLS. Będziesz potrzebować jednego łącznika dla wiadomości wysyłanych do skrzynek pocztowych użytkowników i innego łącznika dla wiadomości wysyłanych ze skrzynek pocztowych użytkowników. Utwórz te łączniki w centrum administracyjnym programu Exchange w Office 365. Aby uzyskać instrukcje, zobacz [Konfigurowanie przepływu poczty przy użyciu łączników w Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>Informacje o certyfikacie protokołu TLS dla Exchange Online

Informacje o certyfikacie używane przez Exchange Online są opisane w poniższej tabeli. Jeśli Twój partner biznesowy konfiguruje wymuszony protokół TLS na serwerze poczty e-mail, musisz przekazać im te informacje. Ze względów bezpieczeństwa nasze certyfikaty zmieniają się od czasu do czasu. Bieżący certyfikat jest ważny od 24 września 2020 r.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>Bieżące informacje o certyfikacie ważne od 24 września 2020 r.
  
| Atrybut | Value |
|:-----|:-----|
|Główny wystawca urzędu certyfikacji|Urząd certyfikacji DigiCert — 1|
|Nazwa certyfikatu|mail.protection.outlook.com|
|Organizacji|Microsoft Corporation|
|Jednostka organizacyjna|www.digicert.com|
|Siła klucza certyfikatu|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>Uzyskaj więcej informacji na temat protokołu TLS, certyfikatów i platformy Microsoft 365 oraz pobierz certyfikaty

[Łańcuchy szyfrowania platformy Microsoft 365 i pliki do pobrania certyfikatów](encryption-office-365-certificate-chains.md)

[Łańcuchy szyfrowania platformy Microsoft 365 i pliki do pobrania certyfikatów — DOD i GCC High](encryption-office-365-certificate-chains-itar.md)

Aby uzyskać listę obsługiwanych zestawów szyfrowania, zobacz [Informacje techniczne dotyczące szyfrowania](technical-reference-details-about-encryption.md).
  
[Konfigurowanie łączników na potrzeby bezpiecznego przepływu poczty w organizacji partnerskiej](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Łączniki z rozszerzonymi zabezpieczeniami poczty e-mail](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Szyfrowanie w usłudze Microsoft 365](encryption.md)
