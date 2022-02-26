---
title: Włączanie zarządzania przez Windows 10 przyłączone do domeny przez Microsoft 365 dla firm
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
description: Dowiedz się, jak Microsoft 365 chronić lokalne urządzenia Windows 10 przyłączone do usługi Active-Directory w kilku krokach.
ms.openlocfilehash: f0af270bc46d09de84e57ffb63c3b72e351c5bfa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973526"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-business-premium"></a>Włączanie zarządzania przez Windows 10 przyłączone do domeny Microsoft 365 Business Premium

Jeśli Twoja organizacja korzysta Windows Server Active Directory lokalnym, możesz skonfigurować usługę Microsoft 365 Business Premium w celu ochrony urządzeń z systemem Windows 10, zachowując dostęp do zasobów lokalnych, które wymagają uwierzytelniania lokalnego.
Aby skonfigurować tę ochronę, możesz zaimplementować urządzenia sprzężenia **hybrydowego usługi Azure AD**. Te urządzenia są połączone zarówno z lokalną usługą Active Directory, jak i Twoją Azure Active Directory.

## <a name="watch-configure-hybrid-azure-active-directory-join"></a>Obejrzyj: Konfigurowanie dołączania do Azure Active Directory hybrydowych

W tym klipie wideo opisano kroki, które należy wykonać w celu skonfigurowania najbardziej typowego scenariusza, a także szczegółowo opisano w poniższych krokach.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  
## <a name="before-you-begin"></a>Przed rozpoczęciem

- Zsynchronizowanie użytkowników z usługą Azure AD z usługą Azure AD Połączenie.
- Ukończ synchronizację Połączenie organizacyjnej usługi Azure AD.
- Upewnij się, że wszyscy użytkownicy domeny, których synchronizujesz, mają licencje Microsoft 365 Business Premium.

Aby [uzyskać odpowiednie instrukcje, zobacz Synchronizowanie](manage-domain-users.md) użytkowników domeny z firmą Microsoft.

## <a name="1-verify-mdm-authority-in-intune"></a>1. Weryfikowanie urzędu zarządzania usługą MDM w usłudze Intune

Przejdź do [Endpoint Manager](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview) i na stronie Microsoft Intune rejestracja **urządzeń, a** następnie na stronie Omówienie upewnij się, że uprawnienia **mdM** to **Intune**.

- Jeśli **dla uprawnienia MDM jest** ustawiona wartość **Brak**, kliknij je w usłudze **MdM** , aby ustawić dla niego pozycję **Intune**.
- Jeśli uprawnienia **MDM** Microsoft Office 365,  >  przejdź **do** strony **DevicesEnroll devices** i użyj okna dialogowego Dodawanie urzędu zarządzania **mdM** po prawej stronie, aby dodać uprawnienia usługi **Intune MDM** (okno dialogowe Dodawanie uprawnień **MDM** jest dostępne tylko wtedy, gdy dla uprawnienia **MDM** ustawiono Microsoft Office 365).

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. Sprawdź, czy włączono usługę Azure AD, aby dołączać do komputerów

- Przejdź do centrum administracyjnego w miejscu <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> i **Azure Active Directory pozycję Pokaż** wszystko, Azure Active Directory nie jest widoczna) na liście **Centra** administracyjne. 
- W centrum **Azure Active Directory przejdź** do pozycji Azure Active Directory **, wybierz** **pozycję Urządzenia**, a następnie **pozycję Ustawienia urządzenia**.
- Weryfikowanie **, czy włączono urządzenia dołączania użytkowników do usługi Azure AD** 
    1. Aby włączyć wszystkich użytkowników, ustaw wartość **Wszystkie**.
    2. Aby włączyć określonych użytkowników, ustaw wartość **Wybrani** , aby włączyć konkretną grupę użytkowników.
        - Dodaj do grupy zabezpieczeń żądanych użytkowników domeny zsynchronizowanych w [usłudze](../../admin/create-groups/create-groups.md) Azure AD.
        - Wybierz **pozycję Wybierz grupy** , aby włączyć zakres użytkowników usługi MDM dla tej grupy zabezpieczeń.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. Sprawdzanie, czy usługa Azure AD jest włączona dla usługi MDM

- Przejdź do centrum administracyjnego w miejscu i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> wybierz pozycję **Zarządzanie punktem** końcowym (wybierz pozycję Pokaż wszystko, **Endpoint Manager** nie jest widoczna)
- W centrum **Microsoft Endpoint Manager przejdź** do **pozycji** >  Urządzenia **Windows** >  **Windows** **Rejestracjaautomatyczna** > .
- Sprawdź, czy jest włączony zakres użytkowników usługi MDM.

    1. Aby zarejestrować wszystkie komputery, ustaw wartość  Wszystkie tak, aby wszystkie komputery użytkowników, które są przyłączone do usługi Azure AD, i nowe komputery, gdy użytkownicy dodają konto służbowe do usługi Windows.
    2. Ustaw wartość **Some** (Niektóre), aby zarejestrować komputery określonej grupy użytkowników.
        -  Dodaj do grupy zabezpieczeń żądanych użytkowników domeny zsynchronizowanych w [usłudze](../create-groups/create-groups.md) Azure AD.
        -  Wybierz **pozycję Wybierz grupy** , aby włączyć zakres użytkowników usługi MDM dla tej grupy zabezpieczeń.

## <a name="4-create-the-required-resources"></a>4. Tworzenie wymaganych zasobów 

Wykonywanie wymaganych zadań w celu skonfigurowania hybrydowego sprzężenia usługi [Azure AD](/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) zostało uproszczone dzięki użyciu polecenia cmdlet [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) w module [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell. Wywoływanie tego polecenia cmdlet spowoduje utworzenie i skonfigurowanie wymaganego punktu połączenia usługi oraz zasad grupy.

Ten moduł można zainstalować, odwołując się do następującego wystąpienia programu PowerShell:

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> Zalecane jest zainstalowanie tego modułu na serwerze usługi Windows z uruchomionym programem Azure AD Połączenie.

Aby utworzyć wymagany punkt połączenia usługi i zasady grupy, należy wywołać polecenie cmdlet  [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) . Podczas wykonywania tego Microsoft 365 Business Premium będziesz potrzebować poświadczeń administratora globalnego. Gdy wszystko będzie gotowe do utworzenia zasobów, wywołaj następujące kwestie:

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

Pierwsze polecenie nawiązuje połączenie z chmurą firmy Microsoft, a po wyświetleniu monitu określ swoje Microsoft 365 Business Premium poświadczenia administratora globalnego.

## <a name="5-link-the-group-policy"></a>5. Łączenie zasady grupy

1. W konsoli zasady grupy zarządzania (GPMC) kliknij prawym przyciskiem myszy lokalizację, w której chcesz połączyć zasady, i wybierz z menu kontekstowego pozycję Połącz istniejący element *zasad* grupy.
2. Wybierz zasady utworzone w powyższym kroku, a następnie kliknij przycisk **OK**.

## <a name="get-the-latest-administrative-templates"></a>Pobierz najnowsze szablony administracyjne

Jeśli nie widzisz zasad Włącz automatyczne rejestrowanie **MDM** przy użyciu domyślnych poświadczeń usługi Azure AD, może to być spowodowane tym, że nie masz zainstalowanego narzędzia ADMX dla programu Windows 10 w wersji 1803 lub nowszej. Aby rozwiązać ten problem, wykonaj następujące czynności (Uwaga: najnowsza wersja pliku MDM.admx jest zgodna z poprzednimi wersjami):

1. Pobierz: [Szablony administracyjne (admx) dla systemu Windows 10 października 2020 r. (20h2)](https://www.microsoft.com/download/102157).
2. Zainstaluj pakiet na Kontroler domeny.
3. Zależnie od wersji szablonów administracyjnych przejdź do folderu: **C:\Program Files (x86)\Microsoft zasady grupy\Windows 10 Aktualizacja z października 2020 r. (20h2)**.
4. Zmień nazwę **folderu Definicje** zasad na powyższej ścieżce do **folderu Definicje Zasad**.
5. Skopiuj folder **PolicyDefinitions** do swojego udziału SYSVOL, domyślnie znajdującego się w folderze **C:\Windows\SYSVOL\domain\Policies**.
   - Jeśli planujesz używać centralnego magazynu zasad dla całej domeny, dodaj tam zawartość PolaOkreślenia Zasad.
6. Jeśli masz kilka kontrolerów domeny, poczekaj, aż narzędzie SYSVOL zreplikuje te zasady, które będą dostępne. Ta procedura będzie działać również w przypadku każdej przyszłej wersji szablonów administracyjnych.

Na tym etapie powinny być dostępne zasady Włącz automatyczną rejestrację **w usłudze MDM przy użyciu domyślnych dostępnych poświadczeń usługi Azure** AD.

## <a name="related-content"></a>Zawartość pokrewna

[Synchronizowanie użytkowników domeny z Microsoft 365](manage-domain-users.md) (artykuł)\
[Tworzenie grupy w centrum administracyjnym](../create-groups/create-groups.md) (artykuł)\
[Samouczek: konfigurowanie dołączania Azure Active Directory hybrydowego dla domen zarządzanych](/azure/active-directory/devices/hybrid-azuread-join-managed-domains) (artykuł)