---
title: Wymagania wstępne dotyczące Microsoft Managed Desktop
description: Licencje, konta Azure, ustawienia uwierzytelniania i ustawienia Microsoft 365, które należy skonfigurować przed zarejestrowaniem się w usłudze Microsoft Managed Desktop
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 495aa7e505bdcec8b5848499ac688847afa129bc
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011324"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Wymagania wstępne dotyczące Microsoft Managed Desktop

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure). DO NOT DELETE.-->
<!--from Prerequisites -->

W tym artykule przedstawiono wymagania dotyczące infrastruktury, które musisz spełnić, aby zapewnić sukces Microsoft Managed Desktop.

| Obszar | Szczegóły wymagań wstępnych |
| ----- | ----- |
| Licencjonowanie | Microsoft Managed Desktop do użytkowników jest wymagana licencja Microsoft 365 E3 usługi Microsoft Defender for Endpoint (lub jej odpowiedników). <ul><li>Aby uzyskać szczegółowe informacje o poszczególnych planach usług, zobacz [Więcej informacji o licencjach](#more-about-licenses).</li><li> Aby uzyskać więcej informacji na temat dostępnych licencji, [zobacz Microsoft 365 licencji](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans).</li></ul>
| Łączność | Wszystkie Microsoft Managed Desktop wymagają łączności z wieloma punktami końcowymi usługi firmy Microsoft z sieci firmowej.<br><br> Aby uzyskać pełną listę wymaganych adresów IP i adresów URL, zobacz [Konfiguracja sieci](../get-ready/network.md).
| Azure Active Directory | Azure Active Directory (Azure AD) musi być źródłem uprawnień dla wszystkich kont użytkowników lub konta użytkowników muszą być synchronizowane z lokalnej usługi Active Directory przy użyciu najnowszej obsługiwanej wersji usługi Azure AD Połączenie. <ul><li>Aby uzyskać więcej informacji, zobacz [Usługa Azure AD Połączenie](/azure/active-directory/hybrid/whatis-azure-ad-connect).</li><li> Aby uzyskać więcej informacji na temat obsługiwanych wersji Połączenie usługi Azure AD, zobacz Usługa [Azure AD Połączenie:Historia wersji](/azure/active-directory/hybrid/reference-connect-version-history).</li></ul>
| Uwierzytelnianie | Jeśli usługa Azure AD nie jest źródłem uwierzytelniania podstawowego dla kont użytkowników, musisz skonfigurować jedną z następujących metod uwierzytelniania w usłudze Azure AD Połączenie:<ul><li> Synchronizacja skrótów haseł.</li> <li> Uwierzytelnianie przekaże.</li><li>Dostawca tożsamości zewnętrznej (w tym Windows usług ADFS serwera i dostawców tożsamości innych niż microsoft) skonfigurowany do spełnienia wymagań integracji usługi Azure AD. Aby uzyskać więcej informacji, zobacz [wytyczne](https://www.microsoft.com/download/details.aspx?id=56843).</li></ul> <br> Podczas ustawiania opcji uwierzytelniania przy użyciu usługi Azure AD Połączenie zalecane jest również pisanie hasła. Aby uzyskać więcej informacji, zobacz [Pisanie hasła](/azure/active-directory/authentication/howto-sspr-writeback). <br><br> Jeśli dostawca tożsamości zewnętrznej jest zaimplementowany, musisz zweryfikować rozwiązanie:<ul><li>Spełnia wymagania dotyczące integracji z usługą Azure AD.</li><li>Obsługuje dostęp warunkowy usługi Azure AD, co pozwala na skonfigurowanie Microsoft Managed Desktop zgodności urządzenia.</li><li>Umożliwia rejestrację urządzenia, korzystanie Microsoft 365 usług lub funkcji wymaganych w ramach Microsoft Managed Desktop.</li></ul> <br>Aby uzyskać więcej informacji na temat opcji uwierzytelniania w usłudze Azure AD, zobacz opcje logowania [Połączenie użytkownika usługi Azure AD](/azure/active-directory/connect/active-directory-aadconnect-user-signin).
| Microsoft 365 | OneDrive dla Firm włączone dla Microsoft Managed Desktop użytkowników.<br><br>Mimo że rejestrowanie się w usłudze Microsoft Managed Desktop nie jest konieczne, zaleca się migrowanie do chmury następujących usług:<ul><li>Poczta e-mail: Migruj do chmurowych skrzynek pocztowych, Exchange w trybie online lub konfiguruj za pomocą środowiska hybrydowego programu Exchange Online z programem Exchange 2013 lub wyższymi lokalnie.</li><li>Pliki i foldery: Migruj OneDrive dla Firm lub SharePoint Online.</li><li>Narzędzia do współpracy online: Migrowanie do Teams.</ul> |
| Zarządzanie urządzeniami | Microsoft Managed Desktop wymagają zarządzania przy użyciu Microsoft Intune. Intune must be set as the Mobile Device Management authority.<br><br> Aby uzyskać więcej informacji, zobacz [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).
| Tworzenie kopii zapasowych i odzyskiwanie danych | Microsoft Managed Desktop wymaga synchronizowania plików z usługą OneDrive dla Firm ochrony. Wszystkie pliki, które nie są synchronizowane OneDrive dla Firm, nie są gwarantowane przez Microsoft Managed Desktop. Pliki mogą zostać utracone podczas wymiany urządzeń lub obsługi połączeń wymagających resetowania urządzenia.<br><br>Chociaż nie jest to wymagane, Microsoft Managed Desktop zdecydowanie zaleca migrację z zamapowanych dysków sieciowych do odpowiedniego rozwiązania w chmurze. Aby uzyskać więcej informacji, [zobacz Przygotowanie zamapowanych dysków dla Microsoft Managed Desktop](mapped-drives.md)

Gdy wszystko będzie gotowe do rozpoczęcia pracy z usługą Microsoft Managed Desktop, skontaktuj się ze swoim Menedżerem konta Microsoft.

## <a name="more-about-licenses"></a>Więcej informacji o licencjach

Microsoft Managed Desktop funkcji wymagane są pewne opcje licencji. Zobacz [Microsoft Managed Desktop technologii,](../intro/technologies.md) aby uzyskać informacje na temat sposobu, w jaki te licencje są używane.

> [!TIP]
> Aby przypisać te opcje licencji określonym użytkownikom, zalecamy korzystanie z funkcji licencjonowania grupowego [](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal) programu Azure Active Directory.

- Azure Active Directory — wersja Premium P1
- Microsoft Intune
- System Windows10 dla firm  
- Ochrona punktu końcowego w usłudze Microsoft Defender
- Aplikacje usługi Microsoft 365 dla przedsiębiorstw
- Microsoft Teams
- [SharePoint Online (Plan 2)](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online Plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans)

> [!TIP]
> Menedżer konta Microsoft pomoże Ci przejrzeć bieżące licencje i plany usług oraz znaleźć najbardziej skuteczną ścieżkę do uzyskania dodatkowych licencji lub planów usług, unikając duplikowania.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Procedura przygotuj się do Microsoft Managed Desktop

1. Przejrzyj wymagania wstępne (ten artykuł).
1. Uruchom [narzędzia do oceny gotowości](readiness-assessment-tool.md).
1. Kup [Portal firmy](../get-started/company-portal.md).
1. Przejrzyj [wymagania wstępne dotyczące kont gości](guest-accounts.md).
1. Sprawdź [konfigurację sieci](network.md).
1. [Przygotowywanie certyfikatów i profilów sieci](certs-wifi-lan.md).
1. [Przygotowywanie dostępu użytkownika do danych](authentication.md).
1. [Przygotowywanie aplikacji](apps.md).
1. [Przygotowywanie zamapowanych dysków](mapped-drives.md).
1. [Przygotowywanie zasobów do drukowania](printing.md).
1. Nazwy [urządzeń adresowych](address-device-names.md).
