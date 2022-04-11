---
title: Wyłączanie protokołów TLS 1.0 i 1.1 dla Microsoft 365
description: Opis wycofywania i wyłączania protokołu TLS 1.0 i 1.1 dla Microsoft 365.
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
ms.openlocfilehash: 519b2c025236be49f2f1c96e098c841f789c079b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759672"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>Wyłączanie protokołów TLS 1.0 i 1.1 dla Microsoft 365

> [!IMPORTANT]
> Tymczasowo wstrzymaliśmy wyłączenie protokołu TLS 1.0 i 1.1 dla klientów komercyjnych z powodu covid-19. Ponieważ łańcuchy dostaw zostały skorygowane i niektóre kraje otwierają się z powrotem, 15 października 2020 r. ponownie uruchomiliśmy wdrożenie egzekwowania protokołu TLS 1.2. Wdrażanie będzie kontynuowane w kolejnych tygodniach i miesiącach.

Od 31 października 2018 r. protokoły TLS (Transport Layer Security) 1.0 i 1.1 są przestarzałe dla usługi Microsoft 365. Efekt dla użytkowników końcowych jest minimalny. Ta zmiana jest ogłaszana od ponad dwóch lat, a pierwsze publiczne ogłoszenie zostało dokonane w grudniu 2017 r. Ten artykuł jest przeznaczony tylko do obsługi klienta lokalnego Office 365 w odniesieniu do usługi Office 365, ale może również dotyczyć lokalnych problemów z protokołem TLS z Office i Office Online Server/Office Web Apps.

W przypadku SharePoint i OneDrive należy zaktualizować i skonfigurować platformę .NET do obsługi protokołu TLS 1.2. Aby uzyskać informacje, zobacz [Jak włączyć protokół TLS 1.2 na klientach](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>omówienie Office 365 i protokołu TLS

Klient Office korzysta z usługi internetowej Windows (WINHTTP) do wysyłania i odbierania ruchu za pośrednictwem protokołów TLS. Klient Office może używać protokołu TLS 1.2, jeśli usługa internetowa komputera lokalnego może używać protokołu TLS 1.2. Wszyscy klienci Office mogą używać protokołów TLS, ponieważ protokoły TLS i SSL są częścią systemu operacyjnego i nie są specyficzne dla klienta Office.

### <a name="on-windows-8-and-later-versions"></a>W Windows 8 i nowszych wersjach

Domyślnie protokoły TLS 1.2 i 1.1 są dostępne, jeśli żadne urządzenia sieciowe nie są skonfigurowane do odrzucania ruchu TLS 1.2.

### <a name="on-windows-7"></a>W Windows 7

Protokoły TLS 1.1 i 1.2 nie są dostępne bez aktualizacji [kb 3140245](https://support.microsoft.com/help/3140245) . Aktualizacja rozwiązuje ten problem i dodaje następujący klucz podrzędny rejestru:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows 7 użytkowników, którzy nie mają tej aktualizacji, ma wpływ na 31 października 2018 r. [Kb 3140245](https://support.microsoft.com/help/3140245) zawiera szczegółowe informacje o tym, jak zmienić ustawienia WINHTTP, aby włączyć protokoły TLS.

#### <a name="more-information"></a>Więcej informacji

Wartość klucza rejestru **DefaultSecureProtocols** opisana w artykule KB określa, które protokoły sieciowe mogą być używane:

|Wartość DefaultSecureProtocols|Protokół włączony|
|---|---|
|0x00000008|Domyślnie włącz protokół SSL 2.0|
|0x00000020|Domyślnie włącz protokół SSL 3.0|
|0x00000080|Domyślnie włącz protokół TLS 1.0|
|0x00000200|Domyślnie włącz protokół TLS 1.1|
|0x00000800|Domyślnie włącz protokół TLS 1.2|

## <a name="office-clients-and-tls-registry-keys"></a>Office klientów i kluczy rejestru TLS

W Office 365 możesz zapoznać się z artykułem [KB 4057306 Przygotowanie do obowiązkowego użycia protokołu TLS 1.2](https://support.microsoft.com/help/4057306). Jest to ogólny artykuł dla administratorów IT i oficjalna dokumentacja dotycząca zmiany protokołu TLS 1.2.

W poniższej tabeli przedstawiono odpowiednie wartości klucza rejestru w Office 365 klientów po 31 października 2018 r.

|Włączone protokoły dla usługi Office 365 po 31 października 2018 r.|Wartość szesnastkowa|
|---|---|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|Protokół TLS 1.2|0x00000800|

> [!IMPORTANT]
> Nie używaj protokołów SSL 2.0 i 3.0, które można również ustawić przy użyciu klucza **DefaultSecureProtocols** . Protokoły SSL 2.0 i 3.0 są uważane za nieaktualne i niezabezpieczone protokoły. Najlepszym rozwiązaniem jest zakończenie korzystania z protokołu SSL 2.0 i SSL 3.0, chociaż decyzja o tym ostatecznie zależy od tego, co najlepiej spełnia Twoje potrzeby produktu. Aby uzyskać więcej informacji na temat luk w zabezpieczeniach protokołu SSL 3.0, zobacz [KB 3009008](https://support.microsoft.com/help/3009008).

Możesz użyć domyślnego kalkulatora Windows w trybie programisty, aby skonfigurować te same wartości klucza rejestru referencyjnego. Aby uzyskać więcej informacji, zobacz [KB 3140245 Update , aby włączyć protokoły TLS 1.1 i TLS 1.2 jako domyślne bezpieczne protokoły w winhttp w Windows](https://support.microsoft.com/help/3140245).

Niezależnie od tego, czy zainstalowano aktualizację Windows 7 ([KB 3140245](https://support.microsoft.com/help/3140245)), klucz podrzędny rejestru DefaultSecureProtocols nie jest obecny i musi zostać dodany ręcznie lub za pośrednictwem obiektu zasad grupy (GPO). Oznacza to, że jeśli nie musisz dostosowywać protokołów zabezpieczeń, które są włączone lub ograniczone, ten klucz nie jest wymagany. Wymagana jest tylko aktualizacja Windows 7 z dodatkiem SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)).

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>Aktualizowanie i konfigurowanie .NET Framework do obsługi protokołu TLS 1.2

Aby korzystać z protokołu TLS 1.2, należy zaktualizować aplikacje wywołujące interfejsy API Microsoft 365 za pośrednictwem protokołu TLS 1.0 lub TLS 1.1. Wartość domyślna platformy .NET 4.5 to TLS 1.1. Aby zaktualizować konfigurację platformy .NET, zobacz [Jak włączyć protokół Transport Layer Security (TLS) 1.2 na klientach](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>Więcej informacji

Aby uzyskać więcej informacji, zobacz [Przygotowywanie do obowiązkowego użycia protokołu TLS 1.2 w Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

## <a name="references"></a>Informacje

Poniższe zasoby zawierają wskazówki ułatwiające upewnienie się, że klienci używają protokołu TLS 1.2 lub nowszej wersji oraz wyłączania protokołu TLS 1.0 i 1.1:

- Jeśli masz klientów z systemem Windows 7, którzy łączą się z usługą Office 365, upewnij się, że protokół TLS 1.2 jest domyślnym protokołem zabezpieczeń w usłudze WinHTTP w systemie Windows. Aby uzyskać więcej informacji, zobacz [KB 3140245 — update to enable TLS 1.1 and TLS 1.2 as default secure protocols in WinHTTP in Windows (Kb 3140245 — aktualizacja w celu włączenia protokołu TLS 1.1 i TLS 1.2 jako domyślnych protokołów bezpieczeństwa w usłudze WinHTTP w Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- Aby rozwiązać problem słabego użycia protokołu TLS przez usunięcie zależności protokołu TLS 1.0 i 1.1, zobacz [Obsługa protokołu TLS 1.2 w firmie Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- [Nowe funkcje usług IIS](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) ułatwiają znajdowanie klientów w systemie [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) i [Windows Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334), którzy łączą się z usługą za pomocą słabych protokołów zabezpieczeń.
- Uzyskaj więcej informacji na temat [sposobu rozwiązania problemu protokołu TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- Aby uzyskać ogólne informacje dotyczące naszego podejścia do zabezpieczeń, przejdź do [Centrum zaufania usługi Office 365](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [Przygotowanie do wycofania TLS 1.0/1.1 — Office 365 Skype dla firm](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Wskazówki programu Exchange Server TLS, część 1: Przygotuj się na protokół TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Uwagi dotyczące programu Exchange Server TLS, część 2: Włączanie obsługi protokołu TLS 1.2 i identyfikacja klientów, którzy go nie używają](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Uwagi dotyczące programu Exchange Server TLS, część 3: Wyłączanie protokołu TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [Włączanie obsługi protokołu TLS 1.1 i TLS 1.2 w witrynie Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
