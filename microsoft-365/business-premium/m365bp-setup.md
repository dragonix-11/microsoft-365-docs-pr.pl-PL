---
title: Konfigurowanie Microsoft 365 Business Premium
description: Zobacz, jak skonfigurować Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/01/2022
ms.service: o365-administration
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 5b6f187f93e8a135bfb67c78509553d2963b011b
ms.sourcegitcommit: b67385243fb56ad20f2a6f1c40be46f5691c1c2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705640"
---
# <a name="set-up-microsoft-365-business-premium"></a>Konfigurowanie Microsoft 365 Business Premium

Dostępnych jest kilka opcji konfigurowania i konfigurowania Microsoft 365 Business Premium. Można:

- [Używanie konfiguracji podstawowej ze przewodnikiem](#guided-process-for-basic-setup)
- [Współpraca z partnerem, takim jak Microsoft Cloud Solution Provider (CSP)](#work-with-a-microsoft-partner)
- [Ręczne przetwarzanie procesu konfiguracji](#manual-setup-and-configuration)


Skorzystaj z tego artykułu jako przewodnika.

## <a name="guided-process-for-basic-setup"></a>Proces konfiguracji podstawowej z przewodnikiem

Microsoft 365 Business Premium zawiera przewodnik po konfiguracji podstawowej. Zadania te obejmują nawiązywanie połączenia z domeną niestandardową, dodawanie użytkowników, przypisywanie licencji, Outlook na urządzeniach przenośnych, przeglądanie ustawień ochrony danych i stosowanie zasad ochrony aplikacji dla urządzeń przenośnych. 

Aby zobaczyć, jak działa instalacja z przewodnikiem, obejrzyj następujący klip wideo: <br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

Po zakończeniu konfiguracji ze przewodnikiem należy wykonać dodatkowe czynności, aby upewnić się, że funkcje zabezpieczeń i zgodności są poprawnie skonfigurowane i zastosowane. Do tych czynności należą:

- [Zabezpieczanie Windows urządzenia](m365bp-secure-windows-devices.md)
- [Wdrażanie Microsoft 365 aplikacji](../admin/setup/install-applications.md)
- [Konfigurowanie nowych funkcji usługi Defender dla firm](../security/defender-business/mdb-setup-configuration.md)

[Dowiedz się więcej o różnicach między procesem konfiguracji ze przewodnikiem a stroną Konfiguracja](../admin/setup/o365-setup-wizard-and-setup-page.md).

> [!TIP]
> Zobacz następującą sekcję, aby uzyskać więcej informacji na temat konfigurowania i konfigurowania Microsoft 365 Business Premium.


## <a name="work-with-a-microsoft-partner"></a>Współpraca z partnerem firmy Microsoft

Firma Microsoft zawiera listę dostawców rozwiązań, którzy są upoważnieni do sprzedaży ofert, w tym Microsoft 365 Business Premium. 

Aby znaleźć dostawcę rozwiązań w swoim obszarze, zrób tak:

1. Przejdź do strony **Dostawcy rozwiązań firmy Microsoft** ([https://www.microsoft.com/solution-providers](https://www.microsoft.com/solution-providers)).
 
2. W polu wyszukiwania wprowadź informacje o lokalizacji i rozmiarze firmy. 

3. W **polu Wyszukaj produkty, usługi, umiejętności, branże** , `Microsoft 365`umieść pozycję , a następnie wybierz pozycję **Przejdź**.

4. Przejrzyj listę wyników. Wybierz dostawcę, aby dowiedzieć się więcej o jego doświadczeniu i oferowanych przez nim usługach.

Zobacz też [Znajdowanie partnera lub odsprzedawcy](../admin/manage/find-your-partner-or-reseller.md).

## <a name="manual-setup-and-configuration"></a>Ręczna konfiguracja i konfiguracja

Jeśli wolisz ręcznie zakończyć proces konfiguracji i konfiguracji, użyj poniższej tabeli jako przewodnika:

| Faza  | Zadanie  | Zasoby, aby dowiedzieć się więcej  |
|---------|---------|---------|
| **Planowanie**     | Planowanie procesu konfiguracji i konfiguracji  | [Planowanie konfiguracji usługi Microsoft 365 dla firm](../admin/setup/plan-your-setup.md)   |
|  | Przejrzyj wymagania | [Microsoft 365 Business Premium wymagań](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:overviewtab) |
| **Konfiguracja podstawowa**     | Używanie domeny niestandardowej, na przykład w `rob@contoso.com` Microsoft 365 | [Dodawanie domeny do Microsoft 365](../admin/setup/add-domain.md) |
|      | Dodawanie użytkowników i przypisywanie licencji w aplikacji Microsoft 365      | [Dodawanie użytkowników i przypisywanie licencji w tym samym czasie](../admin/add-users/add-users.md)        |
|  | Przypisz role administratora użytkownikom, którzy będą wykonywać określone funkcje, takie jak: <br/>- Zarządzanie funkcjami<br/>- Zarządzanie kontami użytkowników<br/>- Zarządzanie urządzeniami<br/>— Wyświetlanie informacji o zabezpieczeniach i zgodności organizacji oraz zarządzanie nimi | [Informacje o rolach administratorów](../admin/add-users/about-admin-roles.md) <br/><br/> [Przypisywanie ról administratora](../admin/add-users/assign-admin-roles.md)  |
|  | Instalowanie Aplikacje Microsoft 365 (takich jak word, Excel, PowerPoint i nie tylko) | [Instalowanie aplikacji pakietu Office](../admin/setup/install-applications.md) |
| **Zabezpieczanie organizacji** | Zobacz 10 pierwszych dni, aby zabezpieczyć swoją Microsoft 365 subskrypcji |  [10 najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Wymagaj od wszystkich osób korzystania z dodatkowej metody weryfikacji po zalogowaniu się do usługi Microsoft 365 | [Konfigurowanie uwierzytelniania wieloskładnikowego](../admin/security-and-compliance/set-up-multi-factor-authentication.md) | 
| **Ochrona poczty e-mail i zawartości** |  Skonfiguruj zaawansowaną ochronę przed wyłudzaniem informacji, aby chronić się przed atakami wyłudzania informacji opartymi na złośliwej personifikacji i innymi atakami wyłudzających informacje | [Ochrona poczty e-mail przed atakami wyłudzających informacje](../admin/security-and-compliance/secure-your-business-data.md) |
|   | Konfigurowanie załączników Sejf w celu ochrony organizacji przed złośliwymi załącznikami wiadomości e-mail | [Ochrona przed złośliwymi załącznikami i plikami za pomocą Sejf załączników](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Konfigurowanie linków Sejf w celu ochrony przed złośliwymi witrynami sieci Web (adresami URL) w wiadomościach e-mail i Office dokumentach | [Konfigurowanie linków Sejf internetowych](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Konfigurowanie zasad ochrony przed utratą danych w celu ochrony przed udostępniać informacje poufne | [Konfigurowanie funkcji zgodności](../admin/security-and-compliance/set-up-compliance.md) |
| **Zarządzanie urządzeniami i ich ochrona** | Zabezpieczanie urządzeń przenośnych Windows organizacji | [Zabezpieczanie Windows urządzeniach](m365bp-secure-windows-devices.md) <br/><br/>[Ustawianie lub edytowanie ustawień ochrony aplikacji dla Windows 10 urządzeniach](../admin/devices/protection-settings-for-windows-10-devices.md) |
|   | Zabezpieczanie Microsoft 365 na urządzeniach przenośnych | [Konfigurowanie ustawień ochrony aplikacji dla urządzeń z systemem Android lub iOS](../admin/devices/app-protection-settings-for-android-and-ios.md) |
|  | Konfigurowanie usługi Microsoft Defender dla firm (jeśli jest dostępna dla Twojej dzierżawy) | [Omówienie usługi Microsoft Defender dla firm](../security/defender-business/mdb-overview.md)<br/><br/>[Konfigurowanie usługi Defender dla firm za pomocą kreatora](../security/defender-business/mdb-use-wizard.md) |
| **Przechowywanie plików i migrowanie zawartości** | Konfigurowanie przechowywania plików i sposobu działania udostępniania w organizacji | [Konfigurowanie przechowywania i udostępniania plików w aplikacji Microsoft 365](../admin/setup/set-up-file-storage-and-sharing.md) |
| | Importowanie lub migrowanie wiadomości e-mail i kontaktów | [Migrowanie wiadomości e-mail i kontaktów do Microsoft 365](../admin/setup/migrate-email-and-contacts-admin.md) |
|  | Przenoszenie firmowych plików, do których mają dostęp wszyscy SharePoint (SharePoint zwykle zastępuje użycie udziału plików lub dysku sieciowego) | [Przenoszenie plików do SharePoint](../admin/setup/files-to-sharepoint.md) |
|  | Przenieś istniejące pliki służbowe, takie jak osobiste lub poufne pliki firmowe, do OneDrive | [Przenoszenie plików do OneDrive](../admin/setup/files-to-onedrive.md) |
| **Administratorzy szkoleń i Twój zespół zabezpieczeń** | Dowiedz się, jak korzystać z centrum administracyjnego | [Omówienie centrum administracyjne platformy Microsoft 365](../admin/admin-overview/admin-center-overview.md) |
|  | Korzystanie z bezpłatnej biblioteki szkoleniowej wideo dla Microsoft 365 administratorów | [Biblioteka szkoleniowa dla administratorów](../admin/admin-video-library.yml)  |
|  | Dowiedz się, jak używać portalu Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | [Rozpoczynanie korzystania z portalu Microsoft 365 Defender-](../security/defender-business/mdb-get-started.md) |

> [!TIP]
> Potrzebujesz pomocy? Rozważ uzyskanie [pomocy biznesowej dla Microsoft 365](https://support.microsoft.com/en-us/office/business-assist-for-microsoft-365-37deb8fe-61cc-4cf9-9ad1-1c8d93475070)

## <a name="see-also"></a>Zobacz też

- [Omówienie programu Microsoft Defender dla firm](../security/defender-business/mdb-overview.md) (teraz dostępnego Microsoft 365 Business Premium!)

- [Subskrypcje biznesowe i dokumentacja rozliczeniowa](../commerce/index.yml)

- [Omówienie Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-overview.md) (dla CSP firmy Microsoft)

- [10 najlepszych sposobów zabezpieczania planów Microsoft 365 dla firm](../admin/security-and-compliance/secure-your-business-data.md)
