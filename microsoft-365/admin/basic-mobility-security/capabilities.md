---
title: Możliwości podstawowej mobilności i zabezpieczeń
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
description: Podstawowa mobilność i zabezpieczenia mogą ułatwić zabezpieczanie urządzeń przenośnych i zarządzanie nimi.
ms.openlocfilehash: 04ee7e7dfbc4937d4add2e4c27e7f686b596fadb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314885"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Możliwości podstawowej mobilności i zabezpieczeń

Podstawowa mobilność i zabezpieczenia mogą ułatwić zabezpieczanie urządzeń przenośnych, takich jak telefony iPhone, tablety iPad, urządzenia z systemem Android i Windows telefony Microsoft 365 używane przez licencjonowanych Microsoft 365 użytkowników w organizacji. Możesz tworzyć zasady zarządzania urządzeniami przenośnymi za pomocą ustawień, które pomagają kontrolować dostęp do poczty e-mail i dokumentów Microsoft 365 organizacji dla obsługiwanych urządzeń przenośnych i aplikacji. W przypadku zgubienia lub kradzieży urządzenia możesz je zdalnie wyczyścić w celu usunięcia poufnych informacji organizacyjnych.

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

Postępuj zgodnie Microsoft Intune podstawowymi systemami operacyjnymi, aby uzyskać informacje o minimalnych obsługiwanych systemach operacyjnych dla urządzeń przez pakiet Basic Mobility and Security. Aby uzyskać więcej informacji, zobacz [Obsługiwane systemy operacyjne Intune](/mem/intune/fundamentals/supported-devices-browsers).

Za pomocą funkcji Basic Mobility and Security możesz zabezpieczać następujące urządzenia i zarządzać nimi.

- iOS
- Android (w tym Samsung Knox)<sup>1</sup>
- Windows <sup>2, 3</sup>

<sup>1</sup> Po czerwcu 2020 r. wersje systemu Android nowsze niż 9 nie mogą zarządzać ustawieniami haseł z wyjątkiem urządzeń firmy Samsung Knox.

<sup>2</sup> Kontrola dostępu dla Windows 8.1 RT jest ograniczona do Exchange ActiveSync.

<sup>3</sup> Kontrola dostępu dla Windows 10 wymaga subskrypcji, która obejmuje Azure AD — wersja Premium, a urządzenie musi być przyłączone do Azure Active Directory.

> [!NOTE]
> Urządzenia już zarejestrowane we wcześniejszych wersjach systemu operacyjnego będą nadal działać, chociaż funkcje mogą ulec zmianie bez powiadomienia.

Jeśli osoby w Twojej organizacji korzystają z urządzeń przenośnych, które nie są obsługiwane przez pakiet Basic Mobility and Security, możesz zablokować dostęp aplikacji Microsoft 365 Exchange ActiveSync do poczty e-mail na tych urządzeniach w celu zapewnienia bezpieczeństwa danych twojej organizacji. Aby uzyskać instrukcje blokowania Exchange ActiveSync, zobacz [Zarządzanie ustawieniami dostępu do urządzeń w pakietach Basic Mobility i Security](manage-device-access-settings.md).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Kontrola dostępu do Microsoft 365 e-mail i dokumentów

Aplikacje obsługiwane dla różnych typów urządzeń przenośnych w poniższej tabeli monitują użytkowników o zarejestrowanie się w programie Basic Mobility and Security, jeśli istnieją nowe zasady zarządzania urządzeniami przenośnymi, które dotyczą urządzenia użytkownika i nie zostały wcześniej zarejestrowane. Jeśli urządzenie użytkownika nie jest zgodne z zasadami, w zależności od sposobu skonfigurowania zasad, użytkownik może mieć zablokowany dostęp do zasobów usługi Microsoft 365 w tych aplikacjach lub może mieć dostęp, ale program Microsoft 365 zgłasza naruszenie zasad.

|**Produkt**|**iOS**|**Android**|
|:-----|:-----|:-----|
|**Exchange** Exchange ActiveSync e-mail oraz aplikacje innych firm, takie jak TouchDown, które korzystają z Exchange ActiveSync 14.1 lub nowszego. |Poczta |Poczta e-mail |
| Office and  **OneDrive dla Firm** |Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**Na telefonach i tabletach**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Tylko na telefonach:** <br/> Office Mobile |

> [!NOTE]
>
> - Obsługa systemu iOS 10.0 i nowszych wersji obejmuje iPhone i iPad urządzenia.
> - Zarządzanie urządzeniami BlackBerry OS nie jest obsługiwane przez pakiet Basic Security and Mobility. Zarządzaj urządzeniami BlackBerry OS za pomocą usług BlackBerry Business Cloud Services (BBCS) firmy BlackBerry. Urządzenia Blackberry z systemem operacyjnym Android są obsługiwane jako standardowe urządzenia z systemem Android
> - Użytkownicy nie zostaną wyświetleniu monitu o zarejestrowanie się i nie będą blokowani ani zgłaszani w przypadku naruszenia zasad, jeśli uzyskają dostęp do witryn firmy Microsoft 365 SharePoint, dokumentów w uchwale Office Online ani wiadomości e-mail w aplikacji Outlook Web App.

Na poniższym diagramie przedstawiono, co się stanie, gdy użytkownik z nowym urządzeniem będzie się edytować do aplikacji obsługującej sterowanie dostępem z pakietem Basic Mobility and Security. Użytkownik ma zablokowany dostęp do zasobów Microsoft 365 aplikacji do czasu zarejestrowania swojego urządzenia.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Podstawowa kontrola dostępu do mobilności i zabezpieczeń.":::

> [!NOTE]
> Zasady i reguły dostępu utworzone w pakietach Basic Mobility and Security Microsoft 365 Business Standard zastąpią Exchange ActiveSync skrzynek pocztowych urządzeń przenośnych i reguły dostępu do urządzeń utworzone w centrum Exchange administracyjnego. Po zarejestrowaniu urządzenia w pakietach Basic Mobility and Security for Microsoft 365 Business Standard Exchange ActiveSync wszelkie zasady skrzynki pocztowej urządzenia przenośnego lub reguła dostępu do urządzenia zastosowana do urządzenia będą ignorowane. Aby dowiedzieć się więcej o Exchange ActiveSync, zobacz  [Exchange ActiveSync w Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>Ustawienia zasad dla urządzeń przenośnych

Jeśli utworzysz zasady blokowania dostępu z włączonymi określonymi ustawieniami, użytkownicy nie będą mieć dostępu do zasobów usługi Microsoft 365 podczas korzystania z obsługiwanej aplikacji wymienionej w kontrolce programu Access dla poczty e-mail i dokumentów platformy [Microsoft 365](capabilities.md).

Ustawienia, które mogą zablokować użytkownikom dostęp do zasobów Microsoft 365, znajdują się w tych sekcjach:

- Bezpieczeństwo

- Szyfrowanie

- Jail broken

- Profil zarządzanej poczty e-mail

Na przykład na poniższym diagramie przedstawiono, co się stanie, gdy użytkownik z zarejestrowanym urządzeniem jest niezgodny z ustawieniem zabezpieczeń w zasadach zarządzania urządzeniami przenośnymi, które dotyczą jego urządzenia. Użytkownik może się do aplikacji obsługującej sterowanie dostępem za pomocą funkcji Basic Mobility and Security. Zablokowano im dostęp do zasobów Microsoft 365 aplikacji, dopóki ich urządzenie nie będzie spełniało warunków ustawienia zabezpieczeń.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Komunikat o zgodności z podstawowymi zabezpieczeniami i mobilnością.":::

W poniższych sekcjach przedstawiono ustawienia zasad, które ułatwiają zabezpieczanie urządzeń przenośnych i zarządzanie nimi w celu nawiązania połączenia z zasobami Microsoft 365 organizacji.

## <a name="security-settings"></a>Ustawienia zabezpieczeń

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Wymaganie hasła|Tak|Tak|Tak|
|Zapobieganie prostemu hasłem|Tak|Nie|Nie|
|Wymaganie hasła alfanumeryczne|Tak|Nie|Nie|
|Minimalna długość hasła |Tak|Tak|Tak|
|Liczba niepowodzeń logowania przed wyczyszczeniem urządzenia |Tak|Tak|Tak|
|Minuty braku aktywności przed zablokowaniem urządzenia |Tak|Tak|Tak|
|Wygasanie hasła (dni) |Tak|Tak|Tak|
|Zapamiętuj historię haseł i zapobiegaj ponownemu używaniu |Tak|Tak|Tak|

## <a name="encryption-settings"></a>Ustawienia szyfrowania

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Wymagaj szyfrowania danych na <sup>urządzeniach1</sup> |Nie|Tak|Tak|

<sup>1</sup> W przypadku systemu Samsung Knox można również wymagać szyfrowania na kartach pamięci.

## <a name="jail-broken-setting"></a>Ustawienie ze złamanym oprawą

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Urządzenie nie może zostać uszkodzone lub z rootowane |Tak|Tak|Tak|

## <a name="managed-email-profile-option"></a>Opcja profilu zarządzanego poczty e-mail

Następująca opcja może zablokować użytkownikom dostęp do swoich Microsoft 365 e-mail, jeśli korzystasz z ręcznie utworzonego profilu poczty e-mail. Użytkownicy urządzeń z systemem iOS muszą usunąć ręcznie utworzony profil poczty e-mail, aby uzyskać dostęp do poczty e-mail. Po usunięciu profilu na urządzeniu zostanie automatycznie utworzony nowy profil. Aby uzyskać instrukcje dotyczące sposobu zgodności użytkowników końcowych, zobacz [Odnaleziono istniejące konto e-mail](/intune-user-help/existing-company-email-account-found).

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Profil poczty e-mail jest zarządzany |Tak|Nie|Nie|

## <a name="cloud-settings"></a>Ustawienia chmury

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Wymagaj zaszyfrowanej kopii zapasowej |Tak|Nie|Nie|
|Blokowanie kopii zapasowej w chmurze |Tak|Nie|Nie|
|Blokowanie synchronizacji dokumentów |Tak|Nie|Nie|
|Blokowanie synchronizacji zdjęć  |Tak|Nie|Nie|
|Zezwalaj na tworzenie kopii zapasowej w usłudze Google  |Nie dotyczy|Nie|Tak|
|Zezwalaj na automatyczną synchronizację konta Google  |Nie dotyczy|Nie|Tak|

## <a name="system-settings"></a>Ustawienia systemu

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Zablokuj przechwytywanie ekranu |Tak|Nie|Tak|
|Blokowanie wysyłania danych diagnostycznych z urządzenia |Tak|Nie|Tak|

## <a name="application-settings"></a>Ustawienia aplikacji

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Blokowanie konferencji wideo na urządzeniu |Tak|Nie|Nie|
|Blokowanie dostępu do magazynu aplikacji |Tak|Nie|Tak|
|Wymaganie hasła podczas uzyskiwania dostępu do magazynu aplikacji |Nie|Tak|Tak|

## <a name="device-capabilities-settings"></a>Ustawienia funkcji urządzenia

|**Nazwa ustawienia**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Połączenie blokowe z magazynem wymiennym |Tak|Tak|Nie|
|Blokowanie Bluetooth sieci |Tak|Tak|Nie|

## <a name="additional-settings"></a>Dodatkowe ustawienia

Poniższe dodatkowe ustawienia zasad można ustawić za pomocą poleceń cmdlet programu PowerShell centrum & zgodności. Aby uzyskać więcej informacji, zobacz  [& Centrum zgodności w programie PowerShell](/powershell/exchange/scc-powershell).

|**Nazwa ustawienia**|**iOS** |**Android**|
|:-----|:-----|:-----|
|CameraEnabled|Tak|Tak|
|RegionRatings|Tak|Nie|
|MoviesRatings|Tak|Nie|
|TVShowsRating |Tak|Nie|
|AppsRatings |Tak|Nie|
|AllowVoiceDialing |Tak|Nie|
|AllowVoiceAssistant |Tak|Nie|
|AllowAssistantWhileLocked  |Tak|Nie|
|AllowPassbookWhileLocked |Tak|Nie|
|MaxPasswordGracePeriod |Tak|Nie|
|PasswordQuality |Nie|Tak|
|SystemSecurityTLS  |Tak|Nie|
|WLANEnabled  |Nie|Nie|

## <a name="settings-supported-by-windows"></a>Ustawienia obsługiwane przez Windows

Możesz zarządzać Windows 10, rejestrując je jako urządzenia przenośne. Po wdrożeniu odpowiednich zasad użytkownicy korzystający z urządzeń z systemem Windows 10 będą zobowiązani do zarejestrowania się w pakietach Basic Mobility and Security, gdy pierwszy raz używają wbudowanej aplikacji poczty e-mail w celu uzyskania dostępu do poczty e-mail usługi Microsoft 365 (wymagana jest subskrypcja Premium usługi Azure AD).

Poniższe ustawienia są obsługiwane dla Windows 10 zarejestrowanych jako urządzenia przenośne. To ustawienie nie zablokuje użytkownikom dostępu do Microsoft 365 zasobów.

### <a name="security-settings"></a>Ustawienia zabezpieczeń

- Wymaganie hasła alfanumeryczne

- Minimalna długość hasła

- Liczba niepowodzeń logowania przed wyczyszczeniem urządzenia

- Minuty braku aktywności przed zablokowaniem urządzenia

- Wygasanie hasła (dni)

- Zapamiętuj historię haseł i zapobiegaj ponownemu używaniu

> [!NOTE]
> Poniższe ustawienia dotyczące regulowania haseł sterują tylko lokalnymi Windows kontach. Windows, które są dostarczane za pośrednictwem Azure Active Directory domeny lub kont, nie mają wpływu na te ustawienia.

### <a name="system-settings"></a>Ustawienia systemu

Blokowanie wysyłania danych diagnostycznych z urządzenia.

### <a name="additional-settings"></a>Dodatkowe ustawienia

Możesz skonfigurować te dodatkowe ustawienia zasad przy użyciu poleceń cmdlet programu PowerShell:

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus (Statystyka zapory)

- AutoUpdateStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>Zdalne czyszczenie urządzenia przenośnego

W przypadku zgubienia lub kradzieży urządzenia możesz usunąć poufne dane organizacyjne i uniemożliwić dostęp do zasobów organizacji programu Microsoft 365, wykonując czyszczenie z Centrum zgodności & Zabezpieczeń > **Zapobieganie** >  **utracie** danych Zarządzanie urządzeniami. Możesz wykonać czyszczenie selektywne w celu usunięcia tylko danych organizacyjnych lub pełne, aby usunąć wszystkie informacje z urządzenia i przywrócić je do ustawień fabrycznych.

Aby uzyskać więcej informacji,  [zobaczWipeanie urządzenia przenośnego w programie Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-content"></a>Zawartość pokrewna

[Omówienie mobilności podstawowej i zabezpieczeń dla Microsoft 365](overview.md) (artykuł)\
[Tworzenie zasad zabezpieczeń urządzeń w mobilności podstawowej i zabezpieczeniach](create-device-security-policies.md) (artykuł)
