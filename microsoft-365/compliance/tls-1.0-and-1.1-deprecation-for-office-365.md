---
title: Wyłączanie TLS 1.0 i 1.1 dla Microsoft 365
description: W tym artykule opisano wyłączanie i wyłączanie funkcji TLS 1.0 i 1.1 dla Microsoft 365.
author: workshay
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: fasqiu
ms.reviewer: krowley
appliesto:
- Microsoft 365 Apps for enterprise
- Office 365 Business
- Office 365 Personal
- Office Online Server
- Office Web Apps
ms.openlocfilehash: 3084232f267a1180425d2daa3fcd2ba2fbcbd063
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973667"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>Wyłączanie TLS 1.0 i 1.1 dla Microsoft 365

> [!IMPORTANT]
> Chwilowo wstrzymać wyłączenie usług TLS 1.0 i 1.1 dla klientów komercyjnych z powodu funkcji COVID-19. W związku z dopasowaniem łańcuchów dostaw i ponownym otwarciem niektórych krajów ponownie uruchomiliśmy stosowanie zasad TLS 1.2 15 października 2020 r. Prace będą kontynuowane w kolejnych tygodniach i miesiącach.

Z dniem 31 października 2018 r. protokoły TLS (Transport Layer Security) 1.0 i 1.1 są przestarzałe dla tej usługi Microsoft 365. Efekt dla użytkowników końcowych jest minimalny. Ta zmiana była publicznie publiczna przez ponad dwa lata, a pierwsze ogłoszenie publiczne zostało wprowadzone w grudniu 2017 r. Ten artykuł dotyczy tylko klienta lokalnego usługi Office 365 w odniesieniu do usługi Office 365, ale może również dotyczyć lokalnych problemów z listą TLS dotyczących aplikacji Office i Office Online Server/Office Web Apps.

Aby SharePoint i OneDrive, musisz zaktualizować i skonfigurować program .NET na potrzeby obsługi TLS 1.2. Aby uzyskać informacje, [zobacz Jak włączyć funkcję TLS 1.2 w klientach](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>Omówienie Office 365 i TLS

Klient Office wysyła i odbiera ruch za pośrednictwem protokołów TLS Windows sieci Web (WINHTTP). Klient Office może używać TLS 1.2, jeśli usługa sieci Web komputera lokalnego może używać TLS 1.2. Wszyscy Office mogą używać protokołów TLS, ponieważ protokoły TLS i SSL są częścią systemu operacyjnego, a nie specyficzne dla Office klienta.

### <a name="on-windows-8-and-later-versions"></a>W Windows 8 i nowszych wersjach

Domyślnie protokoły TLS 1.2 i 1.1 są dostępne, jeśli żadne urządzenia sieciowe nie są skonfigurowane w taki sposób, aby odrzucały ruch TLS 1.2.

### <a name="on-windows-7"></a>W dniu Windows 7

Protokoły TLS 1.1 i 1.2 nie są dostępne bez aktualizacji bazy [wiedzy](https://support.microsoft.com/help/3140245) 3140245 KB. Aktualizacja rozwiązuje ten problem i dodaje następujący pod klucz rejestru:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows 7 użytkowników, którzy nie mają tej aktualizacji, będzie dotyczyć od 31 października 2018 r. [Artykuł 3140245](https://support.microsoft.com/help/3140245) z informacjami na temat sposobu zmieniania ustawień WINHTTP w celu włączenia protokołów TLS.

#### <a name="more-information"></a>Więcej informacji

Wartość klucza rejestru **DefaultSecureProtocols** , który opisano w tym artykule bazy wiedzy, określa, których protokołów sieciowych można używać:

|Wartość DefaultSecureProtocols|Włączono protokół|
|-|-|
|0x00000008|Domyślne włączanie protokołu SSL 2.0|
|0x00000020|Domyślne włączanie protokołu SSL 3.0|
|0x00000080|Domyślnie włącz wartość TLS 1.0|
|0x00000200|Domyślne włączanie TLS 1.1|
|0x00000800|Domyślne włączanie TLS 1.2|

## <a name="office-clients-and-tls-registry-keys"></a>Office klientów i kluczy rejestru TLS

Możesz skorzystać z bazy wiedzy 4057306 przygotowanie się do obowiązkowego użycia ciągu [TLS 1.2](https://support.microsoft.com/help/4057306) w Office 365. Jest to ogólny artykuł dla administratorów IT i jego oficjalna dokumentacja dotycząca zmiany WLS 1.2.

W poniższej tabeli przedstawiono odpowiednie wartości kluczy rejestru Office 365 klientach po 31 października 2018 r.

|Włączone protokoły dla Office 365 usługi po 31 października 2018 r.|Wartość szesnastkowa|
|-|-|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> Nie używaj protokołów SSL 2.0 i 3.0, które można również ustawić przy użyciu klucza **DefaultSecureProtocols** . Protokoły SSL 2.0 i 3.0 są traktowane jako nieaktualne i niezabezpieczone protokoły. Najlepszym rozwiązaniem jest zakończenie używania protokołów SSL 2.0 i SSL 3.0, chociaż ostatecznie decyzja o tym zależy od tego, co najlepiej odpowiada potrzebom produktu. Aby uzyskać więcej informacji na temat luk w zabezpieczeniach protokołu SSL 3.0, zobacz bazy [wiedzy 3009008](https://support.microsoft.com/help/3009008).

Za pomocą domyślnego kalkulatora Windows w trybie programisty można skonfigurować te same wartości kluczy rejestru odwołania. Aby uzyskać więcej informacji, zobacz Aktualizacja [bazy wiedzy 3140245 aby włączyć protokoły TLS 1.1 i TLS 1.2](https://support.microsoft.com/help/3140245) jako domyślne protokoły bezpieczne w winhttp w Windows.

Niezależnie od tego, czy jest zainstalowana aktualizacja Windows 7 ([KB 3140245](https://support.microsoft.com/help/3140245)), pod klucz rejestru DefaultSecureProtocols nie jest dostępny i należy go dodać ręcznie lub za pośrednictwem obiektu zasad grupy . To oznacza, że jeśli nie ma potrzeby dostosowywania protokołów bezpiecznego działania włączono lub ograniczono, ten klucz nie jest wymagany. Potrzebujesz tylko aktualizacji Windows 7 z dodatkiem SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)).

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>Aktualizowanie i konfigurowanie .NET Framework obsługi TLS 1.2

Aby korzystać z interfejsów API usługi TLS 1.0 lub TLS 1.1, należy zaktualizować aplikacje wywołujące interfejsy API usługi Microsoft 365 przez TLS 1.0 lub TLS 1.1. Program .NET 4.5 domyślnie ma wartość TLS 1.1. Aby zaktualizować konfigurację programu .NET, zobacz Jak włączyć na klientach transport [Layer Security (TLS) 1.2](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji, [zobacz Przygotowanie do obowiązkowego użycia TLS 1.2](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) w Office 365.

## <a name="references"></a>Informacje

Poniższe zasoby zawierają wskazówki pomocne w upewnice się, że klienci używają usługi TLS w wersji 1.2 lub nowszej oraz aby wyłączyć obsługę adresów TLS w wersji 1.0 i 1.1:

- Jeśli masz klientów z systemem Windows 7, którzy łączą się z usługą Office 365, upewnij się, że protokół TLS 1.2 jest domyślnym protokołem zabezpieczeń w usłudze WinHTTP w systemie Windows. Aby uzyskać więcej informacji, zobacz bazy wiedzy 3140245 — aktualizacja w celu włączenia protokołów [TLS 1.1 i TLS 1.2](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in) jako domyślnych protokołów bezpiecznego w winieHTTP w Windows.
- Aby rozwiązać ten temat w przypadku słabego użycia TLS przez usunięcie zależności TLS 1.0 i 1.1, zobacz Obsługa [TLS 1.2 w firmie Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Nowe funkcje usług IIS](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) ułatwiają znajdowanie klientów w systemie [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) i [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334), którzy łączą się z usługą za pomocą słabych protokołów zabezpieczeń.
- Uzyskaj więcej informacji na temat [rozwiązywania problemu z TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- Aby uzyskać ogólne informacje dotyczące naszego podejścia do zabezpieczeń, przejdź do [Centrum zaufania usługi Office 365](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [Przygotowanie do wycofania TLS 1.0/1.1 — Office 365 Skype dla firm](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Wskazówki programu Exchange Server TLS, część 1: Przygotuj się na protokół TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Uwagi dotyczące programu Exchange Server TLS, część 2: Włączanie obsługi protokołu TLS 1.2 i identyfikacja klientów, którzy go nie używają](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Uwagi dotyczące programu Exchange Server TLS, część 3: Wyłączanie protokołu TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Włączanie obsługi protokołu TLS 1.1 i TLS 1.2 w witrynie Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)

