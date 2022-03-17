---
title: Omówienie Windows 10 dołączania Windows 11 Microsoft 365 urządzeniach
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
description: Urządzenia Windows 10 i Windows 11 na Microsoft 365
ms.openlocfilehash: dc2324f9ab8105d51730071f84397c8648c9a9de
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525061"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>Omówienie dołączania Windows 10 i Windows 11 Microsoft 365 urządzeniach

**Dotyczy:**

- [Microsoft 365 punktu końcowego ochrony przed utratą danych (DLP)](./endpoint-dlp-learn-about.md)
- [Zarządzanie ryzykiem w niejawnym programie testów](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Microsoft 365 do usługi jest wymagane do tego, aby urządzenia z systemem Windows 10 Windows i Windows 11 były dołączane do usługi w celu wysyłania danych monitorowania do usług w celu ochrony przed utratą danych w punktach końcowych oraz zarządzania ryzykiem w niejawnym programie testów.
 
Microsoft 365 DLP punktu końcowego umożliwia monitorowanie Windows 10 lub Windows 11 urządzeń i wykrywanie, kiedy używane i udostępniane są poufne elementy. Zapewnia to widoczność i kontrolę potrzebną do prawidłowego ich działania i ochrony oraz zapobiegania ryzykownych zachowaniom, które mogłoby je naruszyć. Aby uzyskać więcej informacji na temat wszystkich usług firmy Microsoft w zakresie ochrony przed utratą danych, zobacz [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md). Aby dowiedzieć się więcej o ochronie przed utratą danych w punktach końcowych, zobacz [Informacje na temat ochrony przed utratą danych w punktach końcowych](endpoint-dlp-learn-about.md).

W zarządzaniu ryzykiem w niejawnym programie testów są używane pełne szerokości usługi i wskaźniki innych firm, które ułatwiają szybkie identyfikowanie i trygorzy w przypadku ryzykownych działań użytkowników. Za pomocą dzienników firmy Microsoft 365 i usługi Microsoft Graph zarządzanie ryzykiem w ramach niejawnego programu testów umożliwia definiowanie konkretnych zasad w celu identyfikowania wskaźników ryzyka i podjęcia działań w celu ich zmniejszenia. Aby uzyskać więcej informacji, zobacz [Informacje na temat zarządzania ryzykiem w niejawnym programie testów w programie Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365).

Dołączanie urządzeń jest udostępniane w programach Microsoft 365 i Microsoft Defender for Endpoint (MDE). Jeśli urządzenia zostały już przez Ciebie podłączone do aplikacji MDE, pojawią się one na liście urządzeń zarządzanych i nie musisz nic więcej zrobić, aby na nich wychować. Urządzenia dołączające w Centrum zgodności są również w nich dołączane do usługi MDE.

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="skusubscriptions-licensing"></a>Licencjonowanie subskrypcji/licencji na subskrypcje sKU

Tutaj możesz sprawdzić wymagania [dotyczące licencjonowania](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="permissions"></a>Uprawnienia

Aby włączyć zarządzanie urządzeniami, musisz być członkiem dowolnej z tych ról:

- Administrator globalny
- Administrator zabezpieczeń
- Administrator zgodności

Jeśli chcesz wyświetlać ustawienia zarządzania urządzeniami za pomocą konta niestandardowego, musi ono być w jednej z tych ról:

- Administrator globalny
- Administrator zgodności
- Administrator danych dot. zgodności
- Czytelnik globalny

Jeśli chcesz użyć konta niestandardowego w celu uzyskania dostępu do strony dołączania/wy logowania, musi ono pełnić jedną z tych ról:

- Administrator globalny
- Administrator zgodności

Jeśli chcesz włączyć/wyłączyć monitorowanie urządzeń za pomocą konta niestandardowego, musi ono być w jednej z tych ról:

- Administrator globalny
- Administrator zgodności

### <a name="prepare-your-windows-devices"></a>Przygotowywanie Windows urządzeniach

Upewnij się, że Windows urządzenia, na których musisz się wychować, spełniają te wymagania.

1. Musi być uruchomiona Windows 10 x64 kompilacja 1809 lub Windows 11.

2. Wersja klienta ochrony przed złośliwym oprogramowaniem to 4.18.2110 lub nowsza. Sprawdź bieżącą wersję, otwierając aplikację Zabezpieczenia Windows, wybierz ikonę Ustawienia, a następnie wybierz pozycję Informacje. Numer wersji jest podany w obszarze Wersja klienta ochrony przed złośliwym oprogramowaniem. Zaktualizuj oprogramowanie do najnowszej wersji klienta ochrony przed złośliwym oprogramowaniem, instalując Windows KB4052623.

   > [!NOTE]
   > Żaden z Zabezpieczenia Windows nie musi być aktywny, ale musi być włączony monitor [ochrony](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus) w czasie rzeczywistym i zachowania.

3. Następujące aktualizacje Windows dla Windows 10 są instalowane na urządzeniach, które będą monitorowane.

   > [!NOTE]
   > Te aktualizacje nie są wymaganiem wstępnym do zainstalowania urządzenia, ale zawierają poprawki dla ważnych problemów, dlatego muszą zostać zainstalowane przed użyciem produktu.
   >
    > - Dla Windows 10 1809 – KB4559003, KB4577069, KB4580390
    > - Dla Windows 10 1903 lub 1909 — KB4559004, KB4577062, KB4580386
    > - Dla Windows 10 2004 — KB4568831, KB4577063

4. Wszystkie urządzenia muszą być jednym z tych:

   - [Dołączono do usługi Azure Active Directory (Azure AD)](/azure/active-directory/devices/concept-azure-ad-join)
   - [Sprzężone z hybrydową usługą Azure](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [Zarejestrowano usługę AAD](/azure/active-directory/user-help/user-help-register-device-on-network)

5. Zainstalowana i Microsoft Office jest obsługiwana wersja pakietu. Aby zapewnić najbardziej niezawodną ochronę i środowisko użytkownika, Aplikacje Microsoft 365 zainstalowano wersję 16.0.14701.0 lub nowszą.
> [!NOTE]
   > - Jeśli używasz tego Office 365 — 4577063 KB.
   > - Jeśli używasz miesięcznego kanału Enterprise w Aplikacje Microsoft 365 2004–2008, musisz zaktualizować go do wersji 2009 lub nowszej. Zobacz [Historia aktualizacji dla Aplikacje Microsoft 365 (wymienione według daty) dla](/officeupdates/update-history-microsoft365-apps-by-date) bieżących wersji. Aby dowiedzieć się więcej o znanym problemie, zobacz sekcję Office pakietu w sekcji Informacje o wersji dotyczące wersji [bieżącego kanału w 2020 r](/officeupdates/current-channel#version-2010-october-27).

6. Jeśli masz punkty końcowe, które łączą się z Internetem za pomocą serwera proxy urządzenia, wykonaj procedury podane w tece Konfigurowanie ustawień serwera proxy urządzenia i połączenia internetowego na [temat ochrony informacji](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="onboarding-windows-10-or-windows-11-devices"></a>Dołączanie do Windows 10 lub Windows 11 urządzeń

Aby monitorować i chronić poufne elementy na urządzeniu, musisz włączyć monitorowanie urządzeń i włączyć swoje punkty końcowe. Obie te czynności są wykonywane w portalu Microsoft 365 zgodności.

Jeśli chcesz wboardować urządzenia, które nie zostały jeszcze w nim podłączone, pobierzesz odpowiedni skrypt i wdrożysz go na tych urządzeniach. Wykonaj poniższe procedury dołączania urządzeń.

Jeśli masz już urządzenia, które są już podłączone do programu [Microsoft Defender for Endpoint](/windows/security/threat-protection/), będą one już wyświetlane na liście urządzeń zarządzanych.

W tym scenariuszu wdrażania na urządzeniach Windows 10 lub Windows 11 urządzeń, które jeszcze nie zostały na swoim urządzeniu.

1. Otwórz [Centrum zgodności firmy Microsoft](https://compliance.microsoft.com). Wybierz **Ustawienia** >  **w celu wymusania monitorowania urządzenia**.

   > [!NOTE]
   > Włączanie dołączania do urządzenia trwa zwykle około 60 sekund, ale skontaktuj się z pomocą techniczną firmy Microsoft na maksymalnie 30 minut przed jej rozpoczęciem.

2. Otwórz stronę ustawień Centrum zgodności i wybierz pozycję **Urządzenia w układzie .**

   > [!div class="mx-imgBorder"]
   > ![włącz zarządzanie urządzeniami.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

3. Wybierz **pozycję Zarządzanie urządzeniami** , aby otworzyć **listę** Urządzenia. 

> [!NOTE]
> Jeśli wcześniej wdrożono program Microsoft Defender dla punktu końcowego, wszystkie urządzenia, które zostały wdrożone w trakcie tego procesu, będą wymienione na **liście Urządzenia** . Nie trzeba ich ponownie wychować.

4. Wybierz **pozycję Dołączanie** , aby rozpocząć proces dołączania.

5. Z listy Metody wdrażania wybierz sposób wdrażania na tych dodatkowych urządzeniach, a następnie **pobierz pakiet**.

6. Z poniższej tabeli wybierz odpowiednią procedurę, która ma być obserwowana:

Temat | Opis
:---|:---
[Na urządzeniach Windows 10 lub 11 urządzeń przy użyciu zasady grupy](device-onboarding-gp.md) | Użyj zasady grupy, aby wdrożyć pakiet konfiguracji na urządzeniach.
[Urządzenia Windows 10 lub 11 urządzeń przy użyciu Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | Aby wdrożyć pakiet konfiguracji na urządzeniach, możesz użyć wersji Microsoft Endpoint Configuration Manager (bieżąca gałąź) w wersji 1606 lub Microsoft Endpoint Configuration Manager (bieżąca gałąź) w wersji 1602 lub wcześniejszej.
[Na urządzeniach Windows 10 lub 11 urządzeń za pomocą narzędzi do zarządzania urządzeniami przenośnymi](device-onboarding-mdm.md) | Skorzystaj z narzędzi do zarządzania urządzeniami przenośnymi Microsoft Intune, aby wdrożyć pakiet konfiguracyjnych na urządzeniu.
[Dołączanie Windows 10 lub 11 urządzeń przy użyciu skryptu lokalnego](device-onboarding-script.md) | Dowiedz się, jak wdrożyć pakiet konfiguracji na punktach końcowych za pomocą skryptu lokalnego.
[Dołączanie nietrwałych urządzeń infrastruktury pulpitów wirtualnych (VDI, Non-persistent Virtual Desktop Infrastructure)](device-onboarding-vdi.md) | Dowiedz się, jak za pomocą pakietu konfiguracji skonfigurować urządzenia VDI.

Po dojechiniu urządzenia powinno ono być widoczne na liście urządzeń, a także rozpocząć raportowanie dzienników aktywności inspekcji w Eksploratorze aktywności.

### <a name="viewing-endpoint-dlp-alerts-in-dlp-alerts-management-dashboard"></a>Wyświetlanie alertów DLP punktu końcowego na pulpicie nawigacyjnym zarządzania alertami DLP

1. Otwórz stronę Ochrona przed utratą danych w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centrum zgodności platformy Microsoft 365</a> i wybierz pozycję Alerty.

2. Aby wyświetlić alerty dotyczące zasad DLP w punktach końcowych, zobacz procedury konfigurowania i wyświetlania alertów dotyczących zasad [DLP](dlp-configure-view-alerts-policies.md) .

### <a name="viewing-endpoint-dlp-data-in-activity-explorer"></a>Wyświetlanie danych DLP punktu końcowego w Eksploratorze aktywności

1. Otwórz stronę [Klasyfikacja danych](https://compliance.microsoft.com/dataclassification?viewid=overview) dla swojej domeny w Centrum zgodności usługi Microsoft 365 i wybierz pozycję Eksplorator aktywności.

2. Zapoznaj się z procedurami w [tece Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md) , aby uzyskać dostęp do wszystkich danych dla urządzeń z punktami końcowymi i filtrować je.

   > [!div class="mx-imgBorder"]
   > ![filtr Eksploratora aktywności dla urządzeń końcowych.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)


## <a name="see-also"></a>Zobacz też

- [Informacje na temat zarządzania ryzykiem w niejawnym programie testów w programie Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- [Informacje na temat ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-learn-about.md)
- [Korzystanie z ochrony przed utratą danych w punkcie końcowym](endpoint-dlp-using.md)
- [Informacje na temat ochrony przed utratą danych](dlp-learn-about-dlp.md)
- [Tworzenie, testowanie i dostosowywanie zasad DLP](create-test-tune-dlp-policy.md)
- [Wprowadzenie do Eksploratora aktywności](data-classification-activity-explorer.md)
- [Ochrona punktu końcowego w usłudze Microsoft Defender](/windows/security/threat-protection/)
- [Narzędzia i metody dołączania do Windows 10 komputerów](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 subskrypcji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Urządzenia przyłączone do usługi Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Pobierz nowy Microsoft Edge na podstawie Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
