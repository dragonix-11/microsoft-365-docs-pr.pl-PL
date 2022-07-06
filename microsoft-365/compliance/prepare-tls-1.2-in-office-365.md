---
title: Przygotowanie do protokołu TLS 1.2 w usłudze Office 365 i usłudze Office 365 GCC
description: Sposób przygotowania do użycia TLS 1.2 dla wszystkich połączeń typu klient-serwer i przeglądarka-serwer w usłudze Office 365 i Office 365 GCC po wyłączeniu protokołu TLS 1.0 i 1.1.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: shmehta
ms.reviewer: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: 9edbbb463d04447ee4babcd66b4d6e320663209a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639759"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a>Przygotowanie do protokołu TLS 1.2 w usłudze Office 365 i usłudze Office 365 GCC

## <a name="summary"></a>Podsumowanie

W celu zapewnienia najwyższej klasy szyfrowania naszym klientom, firma Microsoft planuje zaprzestać korzystania z technologii Transport Layer Security (TLS) 1.0 i 1.1 w usłudze Office 365 i Office 365 GCC. Rozumiemy, że bezpieczeństwo danych jest ważne, i zależy nam na przejrzystości wprowadzanych zmian, wpływających na stosowanie usługi TLS.

[Wdrożenie protokołu Microsoft TLS 1.0](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) nie wykazało dotychczas luk w zabezpieczeniach. Jednak z uwagi na możliwe ataki w przyszłości przy użyciu protokołu TLS niższych wersji i innych luk w zabezpieczeniach, firma Microsoft zaprzestała wsparcia protokołu TLS 1.0 i 1.1 w usłudze Microsoft Office 365 i Office 365 GCC.

Aby uzyskać informacje dotyczące usuwania zależności TLS 1.0 i 1.1, zobacz następujący oficjalny dokument: [Rozwiązywanie problemu TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).

Po uaktualnieniu do protokołu TLS 1.2 upewnij się, że używane zestawy szyfrowania są obsługiwane przez usługę Azure Front Door. Rozwiązania Microsoft 365 i Azure Front Door mają niewielkie różnice w obsłudze zestawu szyfrowania. Aby uzyskać szczegółowe informacje, zobacz [Jakie są bieżące zestawy szyfrowania obsługiwane przez usługę Azure Front Door?](/azure/frontdoor/concept-end-to-end-tls#supported-cipher-suites).

## <a name="more-information"></a>Więcej informacji

Od stycznia 2020 r. rozpoczęliśmy już wycofywanie TLS 1.0 i 1.1. Wszelkie klienty, urządzenia lub usługi łączące się z usługą Office 365 za pośrednictwem protokołu TLS 1.0 lub 1.1 w naszych wystąpieniach DoD lub GCC High nie są obsługiwane. W przypadku naszych klientów komercyjnych Office 365 wycofanie protokołów TLS 1.0 i 1.1 rozpocznie się 15 października 2020 r., a wdrożenie będzie kontynuowane w kolejnych tygodniach i miesiącach.

Zalecamy, aby wszystkie kombinacje typu klient-serwer i przeglądarka-serwer korzystały z szyfrowania TLS 1.2 (lub nowszej wersji), aby zachować połączenie z usługami Office 365. Należy zaktualizować określone kombinacje typu klient-serwer i przeglądarka-serwer.

  > [!NOTE]
  > W przypadku przepływu poczty przychodzącej SMTP po wycofaniu protokołu TLS 1.0 i 1.1 będziemy akceptować tylko połączenie TLS 1.2. Będziemy jednak nadal akceptować połączenie SMTP, które jest niezaszyfrowane bez żadnego protokołu TLS. Chociaż nie zalecamy transmisji wiadomości e-mail bez szyfrowania.

Aby korzystać z protokołu TLS 1.2, należy zaktualizować aplikacje, które wywołują interfejsy API platformy Microsoft 365 za pośrednictwem protokołu TLS 1.0 lub TLS 1.1. Wartość domyślna platformy .NET 4.5 to TLS 1.1. Aby zaktualizować konfigurację platformy .NET, zobacz [Jak włączyć protokół Transport Layer Security (TLS) 1.2 na klientach](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Następujący klienci nie są w stanie korzystać z TLS 1.2. Zaktualizuj klientów, aby zapewnić ciągły dostęp do usługi.

- Access 4.3 i starsze wersje
- Firefox wersja 5.0 i starsze wersje
- Program Internet Explorer 8-10 w systemach Windows 7 i starszych wersjach
- Internet Explorer 10 w Windows Phone 8
- Safari 6.0.4/OS X10.8.4 i wcześniejsze wersje

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a>TLS 1.2 dla usługi Microsoft Teams Rooms i urządzenia Surface Hub

Microsoft Teams Rooms (wcześniej znany jako Skype Room System V2 SRS V2) obsługuje TLS 1.2 od grudnia 2018. Zaleca się, aby urządzenia Rooms były zainstalowane w wersji 4.0.64.0 lub nowszej aplikacji Microsoft Teams Rooms. Aby uzyskać więcej informacji, zapoznaj się z [Informacjami o wydaniu](/microsoftteams/room-systems/srs2-release-note). Zmiany są zgodne wstecz i do przodu.

Surface Hub wydał obsługę TLS 1.2 w maju 2019.

Obsługa protokołu TLS 1.2 dla produktów Microsoft Teams Rooms i Surface Hub wymaga również następujących zmian kodu po stronie serwera:

- Zmiany na serwerze usługi Skype dla firm Online zostały wprowadzone na żywo w kwietniu 2019 r. Teraz usługa Skype dla firm Online obsługuje łączenie urządzeń Microsoft Teams Rooms i Surface Hub w usłudze TLS 1.2.
- Klienci programu Skype dla firm Server muszą zainstalować aktualizację zbiorczą (CU), aby używać protokołu TLS 1.2 dla systemów Teams Rooms i urządzeń Surface Hub.

  - W programie Skype dla firm Server 2015 CU9 został już wydany w maju 2019.
  - W przypadku programu Skype dla firm Server 2019 CU1 była wcześniej planowana na kwiecień 2019 r., ale została opóźniona do czerwca 2019 r.

  > [!NOTE]
  > Klienci lokalni programu Skype dla firm nie powinni wyłączać protokołu TLS 1.0/1.1 przed zainstalowaniem określonych CU dla programu Skype dla serwera dla firm.

Jeśli korzystasz z infrastruktury lokalnej w scenariuszach hybrydowych lub usług federacyjnych Active Directory, upewnij się, że infrastruktura może obsługiwać zarówno połączenia przychodzące, jak i wychodzące, które korzystają z TLS 1.2.

## <a name="references"></a>Informacje

Poniższe zasoby zawierają wskazówki pomagające w zapewnieniu, że klienci korzystają z TLS 1.2 lub nowszej wersji i wyłączeniu protokołu TLS 1.0 i 1.1.

- Jeśli masz klientów z systemem Windows 7, którzy łączą się z usługą Office 365, upewnij się, że protokół TLS 1.2 jest domyślnym protokołem zabezpieczeń w usłudze WinHTTP w systemie Windows. Aby uzyskać więcej informacji, zobacz [KB 3140245 – Aktualizacja, aby włączyć protokół TLS 1.1 i TLS 1.2 jako domyślne protokoły zabezpieczeń w WinHTTP w systemie Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- [Mechanizmy szyfrowania TLS obsługiwane przez usługę Office 365](/microsoft-365/compliance/technical-reference-details-about-encryption#tls-cipher-suites-supported-by-office-365)
- Aby zareagować na słabe użycie protokołu TLS, usuwając zależności TLS 1.0 i 1.1, zobacz [Wsparcie  protokołu TLS 1.2 w Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Nowe funkcje usług IIS](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) ułatwiają znajdowanie klientów w systemie [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) i [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334), którzy łączą się z usługą za pomocą słabych protokołów zabezpieczeń.
- Uzyskaj więcej informacji na temat [sposobu rozwiązania problemu protokołu TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- Aby uzyskać ogólne informacje dotyczące naszego podejścia do zabezpieczeń, przejdź do [Centrum zaufania usługi Office 365](https://www.microsoft.com/trustcenter/cloudservices/office365).
- Aby zidentyfikować wersję protokołu TLS używaną przez klientów SMTP, zobacz [SMTP Auth clients insight and report in the Security & Compliance Center (Analiza klientów uwierzytelniania SMTP i raport w Centrum zgodności & zabezpieczeń](../security/office-365-security/mfi-smtp-auth-clients-report.md)).
- [Przygotowanie do wycofania TLS 1.0/1.1 — Office 365 Skype dla firm](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Wskazówki programu Exchange Server TLS, część 1: Przygotuj się na protokół TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Uwagi dotyczące programu Exchange Server TLS, część 2: Włączanie obsługi protokołu TLS 1.2 i identyfikacja klientów, którzy go nie używają](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Uwagi dotyczące programu Exchange Server TLS, część 3: Wyłączanie protokołu TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Włączanie obsługi protokołu TLS 1.1 i TLS 1.2 w witrynie Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
- [Włączanie obsługi protokołu TLS i obsługi protokołu SSL w programie SharePoint 2013](/sharepoint/security-for-sharepoint-server/enable-tls-and-ssl-support-in-sharepoint-2013)
- [Włączanie obsługi protokołu TLS 1.1 i TLS 1.2 w programie SharePoint Server 2016](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016)
- [Włącz obsługę protokołów TLS 1.1 i TLS 1.2 w SharePoint Server 2019](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2019)
