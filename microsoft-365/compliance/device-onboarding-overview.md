---
title: Dołączanie urządzeń Windows 10 lub Windows 11 do platformy Microsoft 365 — omówienie
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Dołączanie urządzeń Windows 10 i Windows 11 do platformy Microsoft 365
ms.openlocfilehash: 630a159327dc5ce177caf819b21e77ec40929866
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635584"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>Omówienie dołączania urządzeń z systemami Windows 10 i Windows 11 do platformy Microsoft 365

**Dotyczy:**

- [Ochrona przed utratą danych punktu końcowego (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem wewnętrznym](insider-risk-management.md)

Ochrona przed utratą danych punktu końcowego (Endpoint DLP) i zarządzanie ryzykiem wewnętrznym wymagają dołączenia Windows 10 urządzeń z systemem Windows i Windows 11 do usługi, aby mogły wysyłać dane monitorowania do usług.
 
Punkt końcowy DLP umożliwia monitorowanie urządzeń Windows 10 lub Windows 11 oraz wykrywanie, kiedy są używane i udostępniane elementy poufne. Zapewnia to widoczność i kontrolę, której potrzebujesz, aby upewnić się, że są one prawidłowo używane i chronione oraz aby zapobiec ryzykownemu zachowaniu, które może je naruszyć. Aby uzyskać więcej informacji na temat wszystkich ofert DLP firmy Microsoft, zobacz [Dowiedz się więcej o zapobieganiu utracie danych](dlp-learn-about-dlp.md). Aby dowiedzieć się więcej na temat ochrony przed [utratą danych punktu końcowego, zobacz Dowiedz się więcej o zapobieganiu utracie danych punktu końcowego](endpoint-dlp-learn-about.md).

Zarządzanie ryzykiem wewnętrznym korzysta z pełnego zakresu wskaźników usług i innych firm, aby ułatwić szybkie identyfikowanie, klasyfikowanie i działanie na ryzykownych działaniach użytkowników. Dzięki użyciu dzienników z platformy Microsoft 365 i programu Microsoft Graph zarządzanie ryzykiem wewnętrznym umożliwia definiowanie określonych zasad w celu identyfikowania wskaźników ryzyka i podejmowania działań w celu ograniczenia tych zagrożeń. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o zarządzaniu ryzykiem wewnętrznym](insider-risk-management.md).

Dołączanie urządzeń jest współużytkowane przez platformę Microsoft 365 i Ochrona punktu końcowego w usłudze Microsoft Defender (MDE). Jeśli urządzenia zostały już dołączone do rozwiązania MDE, zostaną one wyświetlone na liście urządzeń zarządzanych i nie są wymagane żadne dalsze kroki w celu dołączenia tych konkretnych urządzeń. Dołączanie urządzeń w Centrum zgodności również dołącza je do rozwiązania MDE.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie jednostek SKU/subskrypcji

Sprawdź wymagania dotyczące licencjonowania [tutaj](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="permissions"></a>Uprawnienia

Aby włączyć zarządzanie urządzeniami, używane konto musi być członkiem dowolnej z następujących ról:

- Administrator globalny
- Administrator zabezpieczeń
- Administrator zgodności

Jeśli chcesz użyć konta niestandardowego do wyświetlania ustawień zarządzania urządzeniami, musi ono znajdować się w jednej z następujących ról:

- Administrator globalny
- Administrator zgodności
- Administrator danych dot. zgodności
- Czytelnik globalny

Jeśli chcesz użyć konta niestandardowego w celu uzyskania dostępu do strony dołączania/odłączania, musi ona znajdować się w jednej z następujących ról:

- Administrator globalny
- Administrator zgodności

Jeśli chcesz włączyć/wyłączyć monitorowanie urządzenia przy użyciu konta niestandardowego, musi ono pełnić jedną z następujących ról:

- Administrator globalny
- Administrator zgodności

### <a name="prepare-your-windows-devices"></a>Przygotowywanie urządzeń z systemem Windows

Upewnij się, że urządzenia z systemem Windows, które należy dołączyć, spełniają te wymagania.

1. Musi być uruchomiony Windows 10 kompilacji x64 1809 lub nowszej lub Windows 11.

2. Wersja klienta ochrony przed złośliwym kodem to 4.18.2110 lub nowsza. Sprawdź bieżącą wersję, otwierając aplikację Zabezpieczenia Windows, wybierz ikonę Ustawienia, a następnie wybierz pozycję Informacje. Numer wersji znajduje się w obszarze Wersja klienta ochrony przed złośliwym kodem. Zaktualizuj do najnowszej wersji klienta ochrony przed złośliwym kodem, instalując Windows Update KB4052623.

   > [!NOTE]
   > Żaden ze składników Zabezpieczenia Windows nie musi być aktywny, ale należy włączyć [ochronę w czasie rzeczywistym i monitor zachowania](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)).

3. Następujące Aktualizacje systemu Windows dla Windows 10 są instalowane dla urządzeń, które będą monitorowane.

   > [!NOTE]
   > Te aktualizacje nie są wymaganiem wstępnym do dołączenia urządzenia, ale zawierają poprawki ważnych problemów, dlatego należy zainstalować je przed użyciem produktu.
   >
    > - Dla Windows 10 1809 — KB4559003, KB4577069, KB4580390
    > - W przypadku Windows 10 1903 lub 1909 — KB4559004, KB4577062, KB4580386
    > - Dla Windows 10 2004 - KB4568831, KB4577063

4. Wszystkie urządzenia muszą być jednym z następujących:

   - [Dołączono do usługi Azure Active Directory (Azure AD)](/azure/active-directory/devices/concept-azure-ad-join)
   - [Sprzężone z hybrydową usługą Azure](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [Zarejestrowano usługę AAD](/azure/active-directory/user-help/user-help-register-device-on-network)

5. Jest zainstalowana i aktualna obsługiwana wersja pakietu Microsoft Office. Aby zapewnić najbardziej niezawodną ochronę i środowisko użytkownika, upewnij się, że zainstalowano Aplikacje Microsoft 365 wersji 16.0.14701.0 lub nowszej.
> [!NOTE]
   > - Jeśli używasz Office 365 — KB 4577063 jest wymagane.
   > - Jeśli korzystasz z miesięcznego kanału enterprise Aplikacje Microsoft 365 wersji 2004-2008, musisz zaktualizować go do wersji 2009 lub nowszej. Zobacz [Update history for Aplikacje Microsoft 365 (listed by date) for current versions (Historia aktualizacji dla Aplikacje Microsoft 365 (wymienione według daty)](/officeupdates/update-history-microsoft365-apps-by-date) dla bieżących wersji. Aby dowiedzieć się więcej na temat znanego problemu, zobacz sekcję Office Suite [dotyczącą informacji o wersji dla bieżących wersji kanału w 2020 roku](/officeupdates/current-channel#version-2010-october-27).

6. Jeśli masz punkty końcowe, które używają serwera proxy urządzenia do nawiązywania połączenia z Internetem, postępuj zgodnie z procedurami opisanymi w [temacie Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego dla Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="onboarding-windows-10-or-windows-11-devices"></a>Dołączanie urządzeń Windows 10 lub Windows 11

Aby można było monitorować i chronić poufne elementy na urządzeniu, należy włączyć monitorowanie urządzeń i dołączać do nich punkty końcowe. Obie te akcje są wykonywane w portal zgodności Microsoft Purview.

Jeśli chcesz dołączyć urządzenia, które nie zostały jeszcze dołączone, pobierzesz odpowiedni skrypt i wdrożysz go na tych urządzeniach. Postępuj zgodnie z poniższymi procedurami dołączania urządzenia.

Jeśli masz już urządzenia dołączone do [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/), zostaną one już wyświetlone na liście urządzeń zarządzanych.

W tym scenariuszu wdrażania dołączesz urządzenia Windows 10 lub Windows 11, które nie zostały jeszcze dołączone.

1. Otwórz [portal zgodności Microsoft Purview](https://compliance.microsoft.com). Wybierz pozycję **Ustawienia** > **Włącz monitorowanie urządzenia**.

   > [!NOTE]
   > Włączenie dołączania urządzenia zwykle trwa około 60 sekund, ale przed rozpoczęciem angażowania się w pomoc techniczną firmy Microsoft poczekaj do 30 minut.

2. Otwórz stronę Ustawienia Centrum zgodności i wybierz pozycję **Włącz monitorowanie urządzeń z systemem Windows**.

3. Wybierz pozycję **Zarządzanie urządzeniami** , aby otworzyć listę **Urządzenia** . 

> [!NOTE]
> Jeśli wcześniej wdrożono Ochrona punktu końcowego w usłudze Microsoft Defender, wszystkie urządzenia, które zostały dołączone podczas tego procesu, zostaną wyświetlone na liście **Urządzenia**. Nie ma potrzeby ponownego dołączania ich.

4. Wybierz pozycję **Dołączanie** , aby rozpocząć proces dołączania.

5. Wybierz sposób wdrażania na tych dodatkowych urządzeniach z listy **Metody wdrażania,** a następnie **pobierz pakiet**.

6. Wybierz odpowiednią procedurę do wykonania z poniższej tabeli:

Temat | Opis
:---|:---
[Dołączanie urządzeń Windows 10 lub 11 przy użyciu zasady grupy](device-onboarding-gp.md) | Użyj zasady grupy, aby wdrożyć pakiet konfiguracji na urządzeniach.
[Dołączanie urządzeń Windows 10 lub 11 przy użyciu programu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | Do wdrożenia pakietu konfiguracji na urządzeniach można użyć programu Microsoft Endpoint Configuration Manager (current branch) w wersji 1606 lub Microsoft Endpoint Configuration Manager (current branch) w wersji 1602 lub starszej.
[Dołączanie urządzeń Windows 10 lub 11 przy użyciu narzędzi mobile Zarządzanie urządzeniami](device-onboarding-mdm.md) | Użyj narzędzi Zarządzanie urządzeniami mobile lub Microsoft Intune, aby wdrożyć pakiet konfiguracji na urządzeniu.
[Dołączanie Windows 10 lub 11 urządzeń przy użyciu skryptu lokalnego](device-onboarding-script.md) | Dowiedz się, jak używać skryptu lokalnego do wdrażania pakietu konfiguracji w punktach końcowych.
[Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI)](device-onboarding-vdi.md) | Dowiedz się, jak skonfigurować urządzenia VDI przy użyciu pakietu konfiguracji.

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o zarządzaniu ryzykiem wewnętrznym](insider-risk-management.md)
- [Dowiedz się więcej o ochronie przed utratą danych punktu końcowego](endpoint-dlp-learn-about.md)
- [Korzystanie z ochrony przed utratą danych punktu końcowego](endpoint-dlp-using.md)
- [Dowiedz się więcej o ochronie przed utratą danych](dlp-learn-about-dlp.md)
- [Twórz, testuj i dostrajaj zasady DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora działań](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Narzędzia i metody dołączania maszyn Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Subskrypcja platformy Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [urządzenia przyłączone Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nową przeglądarkę Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
