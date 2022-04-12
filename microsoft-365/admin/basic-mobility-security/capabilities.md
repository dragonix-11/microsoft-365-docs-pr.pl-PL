---
title: Możliwości funkcji Podstawowa mobilność i zabezpieczenia
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Usługa Basic Mobility and Security może pomóc w zabezpieczeniu urządzeń przenośnych i zarządzaniu nimi.
ms.openlocfilehash: 78cfa4582aa2e25a3b47a12d2e067082e8b41d07
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781232"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Możliwości funkcji Podstawowa mobilność i zabezpieczenia

Usługa Basic Mobility and Security może pomóc w zabezpieczeniu urządzeń przenośnych, takich jak iPhone, iPad, Android i Windows Phone używanych przez licencjonowanych użytkowników Microsoft 365 w organizacji. Możesz utworzyć zasady zarządzania urządzeniami przenośnymi z ustawieniami, które ułatwiają kontrolowanie dostępu do Microsoft 365 poczty e-mail i dokumentów organizacji dla obsługiwanych urządzeń przenośnych i aplikacji. W przypadku utraty lub kradzieży urządzenia można zdalnie wyczyścić urządzenie, aby usunąć poufne informacje organizacyjne.

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

Postępuj zgodnie z przewodnikiem po systemach operacyjnych Microsoft Intune, aby zapoznać się z minimalnymi obsługiwanymi systemami operacyjnymi dla urządzeń w ramach pakietu Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Intune obsługiwanych systemów operacyjnych](/mem/intune/fundamentals/supported-devices-browsers).

Aby zabezpieczyć następujące urządzenia i zarządzać nimi, możesz użyć pakietu Basic Mobility and Security.

- iOS
- Android (w tym Samsung Knox)<sup>1</sup>
- Windows <sup>2, 3</sup>

<sup>1</sup> Po czerwcu 2020 r. wersje systemu Android późniejsze niż 9 nie mogą zarządzać ustawieniami haseł, z wyjątkiem urządzeń z systemem Samsung Knox.

<sup>2.</sup> Kontrola dostępu dla urządzeń Windows 8.1 RT jest ograniczona do Exchange ActiveSync.

<sup>3.</sup> Kontrola dostępu dla Windows 10 wymaga subskrypcji obejmującej Azure AD — wersja Premium, a urządzenie musi zostać przyłączone do Azure Active Directory.

> [!NOTE]
> Urządzenia już zarejestrowane we wcześniejszych wersjach systemu operacyjnego nadal działają, chociaż możliwości mogą ulec zmianie bez powiadomienia.

Jeśli osoby w organizacji korzystają z urządzeń przenośnych, które nie są obsługiwane przez usługi Basic Mobility and Security, możesz zablokować dostęp aplikacji Exchange ActiveSync do Microsoft 365 poczty e-mail dla tych urządzeń, aby zwiększyć bezpieczeństwo danych organizacji. Aby uzyskać instrukcje dotyczące blokowania Exchange ActiveSync, zobacz [Manage device access settings in Basic Mobility and Security (Zarządzanie ustawieniami dostępu do urządzeń w usłudze Basic Mobility and Security](manage-device-access-settings.md)).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Kontrola dostępu do Microsoft 365 wiadomości e-mail i dokumentów

Obsługiwane aplikacje dla różnych typów urządzeń przenośnych w poniższej tabeli monitują użytkowników o zarejestrowanie się w usłudze Basic Mobility and Security, jeśli istnieją nowe zasady zarządzania urządzeniami przenośnymi, które mają zastosowanie do urządzenia użytkownika, a użytkownik nie zarejestrował urządzenia wcześniej. Jeśli urządzenie użytkownika nie jest zgodne z zasadami, w zależności od sposobu konfigurowania zasad użytkownik może mieć dostęp do Microsoft 365 zasobów w tych aplikacjach lub może mieć dostęp, ale Microsoft 365 zgłasza naruszenie zasad.

|Rezultat|iOS|Android|
|---|---|---|
|**Exchange** Exchange ActiveSync obejmuje wbudowane aplikacje poczty e-mail i aplikacje innych firm, takie jak TouchDown, które używają Exchange ActiveSync wersji 14.1 lub nowszej.|Poczty|Poczta e-mail|
|**Office** i **OneDrive dla Firm**|Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**Na telefonach i tabletach**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Tylko na telefonach:** <br/> Office Mobile|

> [!NOTE]
>
> - Obsługa systemów iOS 10.0 i nowszych obejmuje urządzenia iPhone i iPad.
> - Zarządzanie urządzeniami z systemem operacyjnym BlackBerry nie jest obsługiwane przez usługi Basic Security i Mobility. Użyj aplikacji BlackBerry Business Cloud Services (BBCS) firmy BlackBerry do zarządzania urządzeniami z systemem operacyjnym BlackBerry. Urządzenia Blackberry z systemem operacyjnym Android są obsługiwane jako standardowe urządzenia z systemem Android
> - Użytkownicy nie będą monitować o rejestrację i nie będą blokować ani zgłaszać naruszenia zasad, jeśli korzystają z przeglądarki mobilnej w celu uzyskania dostępu do witryn Microsoft 365 SharePoint, dokumentów w usłudze Office Online lub wiadomości e-mail w Outlook Web App.

Na poniższym diagramie przedstawiono, co się stanie, gdy użytkownik z nowym urządzeniem zaloguje się do aplikacji, która obsługuje kontrolę dostępu przy użyciu pakietu Basic Mobility and Security. Użytkownik ma zablokowany dostęp do Microsoft 365 zasobów w aplikacji, dopóki nie zarejestruje swojego urządzenia.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Podstawowa kontrola dostępu do mobilności i zabezpieczeń.":::

> [!NOTE]
> Zasady i reguły dostępu utworzone w usłudze Basic Mobility and Security dla Microsoft 365 Business Standard zastąpią zasady skrzynki pocztowej urządzeń przenośnych Exchange ActiveSync i reguły dostępu urządzeń utworzonych w centrum administracyjnym Exchange. Po zarejestrowaniu urządzenia w usłudze Basic Mobility and Security for Microsoft 365 Business Standard wszystkie Exchange ActiveSync zasad skrzynki pocztowej urządzeń przenośnych lub reguły dostępu urządzeń zostaną zignorowane. Aby dowiedzieć się więcej na temat Exchange ActiveSync, zobacz [Exchange ActiveSync w Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>Ustawienia zasad dla urządzeń przenośnych

Jeśli utworzysz zasady blokujące dostęp z włączonymi określonymi ustawieniami, użytkownicy będą blokować dostęp do Microsoft 365 zasobów w przypadku korzystania z obsługiwanej aplikacji wymienionej w obszarze [Kontrola dostępu dla Microsoft 365 poczty e-mail i dokumentów](capabilities.md).

Ustawienia, które mogą blokować użytkownikom dostęp do Microsoft 365 zasobów, znajdują się w następujących sekcjach:

- Bezpieczeństwo

- Szyfrowanie

- Złamane więzienie

- Zarządzany profil poczty e-mail

Na przykład na poniższym diagramie pokazano, co się dzieje, gdy użytkownik z zarejestrowanym urządzeniem nie jest zgodny z ustawieniem zabezpieczeń w zasadach zarządzania urządzeniami przenośnymi, które mają zastosowanie do urządzenia. Użytkownik loguje się do aplikacji, która obsługuje kontrolę dostępu przy użyciu pakietu Basic Mobility and Security. Dostęp do zasobów Microsoft 365 w aplikacji jest zablokowany, dopóki ich urządzenie nie będzie zgodne z ustawieniem zabezpieczeń.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Komunikat o zgodności z usługą Basic Mobility and Security.":::

W poniższych sekcjach wymieniono ustawienia zasad, których można użyć do zabezpieczania urządzeń przenośnych łączących się z zasobami organizacji Microsoft 365 i zarządzania nimi.

## <a name="security-settings"></a>Ustawienia zabezpieczeń

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Wymagaj hasła|Tak|Tak|Tak|
|Zapobiegaj prostemu haśle|Tak|Nie|Nie|
|Wymagaj hasła alfanumerycznego|Tak|Nie|Nie|
|Minimalna długość hasła|Tak|Tak|Tak|
|Liczba błędów logowania przed wyczyszczonym urządzeniem|Tak|Tak|Tak|
|Minuty braku aktywności przed zablokowaniem urządzenia|Tak|Tak|Tak|
|Wygaśnięcie hasła (dni)|Tak|Tak|Tak|
|Zapamiętywanie historii haseł i zapobieganie ponownemu użyciu|Tak|Tak|Tak|

## <a name="encryption-settings"></a>Ustawienia szyfrowania

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Wymagaj szyfrowania danych na <sup>urządzeniach1</sup>|Nie|Tak|Tak|

<sup>1</sup> W systemie Samsung Knox możesz również wymagać szyfrowania na kartach pamięci.

## <a name="jail-broken-setting"></a>Ustawienie przerwane w więzieniu

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Urządzenie nie może zostać złamane lub odblokowane przez dostęp do konta root|Tak|Tak|Tak|

## <a name="managed-email-profile-option"></a>Opcja zarządzanego profilu poczty e-mail

Poniższa opcja może zablokować użytkownikom dostęp do Microsoft 365 poczty e-mail, jeśli korzystają z ręcznie utworzonego profilu poczty e-mail. Użytkownicy urządzeń z systemem iOS muszą usunąć ręcznie utworzony profil poczty e-mail, aby mogli uzyskać dostęp do poczty e-mail. Po usunięciu profilu na urządzeniu zostanie automatycznie utworzony nowy profil. Aby uzyskać instrukcje dotyczące sposobu, w jaki użytkownicy końcowi mogą uzyskać zgodność, zobacz [Znajdowanie istniejącego konta e-mail](/intune-user-help/existing-company-email-account-found).

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Profil poczty e-mail jest zarządzany|Tak|Nie|Nie|

## <a name="cloud-settings"></a>Ustawienia chmury

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Wymagaj zaszyfrowanej kopii zapasowej|Tak|Nie|Nie|
|Blokuj tworzenie kopii zapasowych w chmurze|Tak|Nie|Nie|
|Blokuj synchronizację dokumentów|Tak|Nie|Nie|
|Blokuj synchronizację zdjęć|Tak|Nie|Nie|
|Zezwalaj na tworzenie kopii zapasowych google|nd.|Nie|Tak|
|Zezwalaj na automatyczną synchronizację konta Google|nd.|Nie|Tak|

## <a name="system-settings"></a>Ustawienia systemu

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Blokuj przechwytywanie ekranu|Tak|Nie|Tak|
|Blokuj wysyłanie danych diagnostycznych z urządzenia|Tak|Nie|Tak|

## <a name="application-settings"></a>Ustawienia aplikacji

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Blokowanie konferencji wideo na urządzeniu|Tak|Nie|Nie|
|Blokowanie dostępu do magazynu aplikacji|Tak|Nie|Tak|
|Wymagaj hasła podczas uzyskiwania dostępu do magazynu aplikacji|Nie|Tak|Tak|

## <a name="device-capabilities-settings"></a>Ustawienia możliwości urządzenia

|Nazwa ustawienia|iOS|Android|Samsung Knox|
|---|---|---|---|
|Blokuj połączenie z magazynem wymiennym|Tak|Tak|Nie|
|Blokuj połączenie Bluetooth|Tak|Tak|Nie|

## <a name="additional-settings"></a>Ustawienia dodatkowe

Następujące dodatkowe ustawienia zasad można ustawić przy użyciu poleceń cmdlet programu PowerShell centrum zgodności usługi Security &. Aby uzyskać więcej informacji, zobacz [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

|Nazwa ustawienia|iOS|Android|
|---|---|---|
|CameraEnabled|Tak|Tak|
|RegionRatings|Tak|Nie|
|MoviesRatings|Tak|Nie|
|TVShowsRating|Tak|Nie|
|AplikacjeRatings|Tak|Nie|
|AllowVoiceDialing|Tak|Nie|
|AllowVoiceAssistant|Tak|Nie|
|AllowAssistantWhileLocked|Tak|Nie|
|AllowPassbookWhileLocked|Tak|Nie|
|MaxPasswordGracePeriod|Tak|Nie|
|PasswordQuality|Nie|Tak|
|SystemSecurityTLS|Tak|Nie|
|WLANEnabled|Nie|Nie|

## <a name="settings-supported-by-windows"></a>Ustawienia obsługiwane przez Windows

Możesz zarządzać Windows 10 urządzeniami, rejestrując je jako urządzenia przenośne. Po wdrożeniu odpowiednich zasad użytkownicy z Windows 10 urządzeniami będą musieli zarejestrować się w usłudze Basic Mobility and Security przy pierwszym użyciu wbudowanej aplikacji poczty e-mail w celu uzyskania dostępu do Microsoft 365 poczty e-mail (wymaga subskrypcji usługi Azure AD w warstwie Premium).

Następujące ustawienia są obsługiwane w przypadku urządzeń Windows 10 zarejestrowanych jako urządzenia przenośne. To ustawienie nie zablokuje użytkownikom dostępu do Microsoft 365 zasobów.

### <a name="security-settings"></a>Ustawienia zabezpieczeń

- Wymagaj hasła alfanumerycznego

- Minimalna długość hasła

- Liczba błędów logowania przed wyczyszczonym urządzeniem

- Minuty braku aktywności przed zablokowaniem urządzenia

- Wygaśnięcie hasła (dni)

- Zapamiętywanie historii haseł i zapobieganie ponownemu użyciu

> [!NOTE]
> Następujące ustawienia regulujące hasła kontrolują tylko konta Windows lokalnych. te ustawienia nie mają wpływu na konta Windows udostępniane za pośrednictwem dołączania do domeny lub Azure Active Directory.

### <a name="system-settings"></a>Ustawienia systemu

Blokuj wysyłanie danych diagnostycznych z urządzenia.

### <a name="additional-settings"></a>Ustawienia dodatkowe

Te dodatkowe ustawienia zasad można ustawić przy użyciu poleceń cmdlet programu PowerShell:

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus

- AutoUpdateStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>Zdalne czyszczenie urządzenia przenośnego

Jeśli urządzenie zostanie utracone lub skradzione, możesz usunąć poufne dane organizacyjne i zapobiec dostępowi do zasobów organizacji Microsoft 365, wykonując czyszczenie z centrum zgodności usługi Security & > **Ochrona przed** >  utratą **danychZarządzanie urządzeniami**. Można przeprowadzić selektywne czyszczenie, aby usunąć tylko dane organizacyjne lub pełne czyszczenie, aby usunąć wszystkie informacje z urządzenia i przywrócić je do ustawień fabrycznych.

Aby uzyskać więcej informacji, zobacz [Czyszczenie urządzenia przenośnego w usłudze Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie pakietu Basic Mobility and Security dla Microsoft 365](overview.md) (artykuł)\
[Tworzenie zasad zabezpieczeń urządzeń w usłudze Basic Mobility and Security](create-device-security-policies.md) (artykuł)
