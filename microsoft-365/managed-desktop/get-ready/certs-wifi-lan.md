---
title: Przygotowywanie certyfikatów i profilów sieci dla Microsoft Managed Desktop
description: Wymagania dotyczące certyfikatów i łączności Wi-Fi
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ccdd9f390c794590eed6cbe11d169430f92bdf55
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027127"
---
# <a name="prepare-certificates-and-network-profiles-for-microsoft-managed-desktop"></a>Przygotowywanie certyfikatów i profilów sieci dla Microsoft Managed Desktop  

Uwierzytelnianie oparte na certyfikatach to typowe wymaganie dla klientów korzystających z Microsoft Managed Desktop. Certyfikaty mogą być wymagane do:

- Program Access Wi-Fi sieci LAN
- Połączenie rozwiązania vpn
- Uzyskiwanie dostępu do zasobów wewnętrznych w organizacji

Ponieważ Microsoft Managed Desktop są połączone z usługą Azure Active Directory (Azure AD) i są zarządzane przez usługę Microsoft Intune, należy wdrożyć takie certyfikaty przy użyciu:

- SCEPT (Simple Certificate Enrollment Protocol) lub
- Infrastruktura certyfikatów PKCS (Public Key Cryptography Standard) zintegrowana z usługą Intune.

## <a name="certificate-requirements"></a>Wymagania dotyczące certyfikatu

Certyfikaty główne są wymagane do wdrażania certyfikatów za pośrednictwem infrastruktury SCEP lub PKCS. Inne aplikacje i usługi w organizacji mogą wymagać wdrożenia certyfikatów głównych na Twoich Microsoft Managed Desktop urządzeniach.

Przed wdrożeniem certyfikatów SCEPT lub PKCS w programie Microsoft Managed Desktop należy zebrać wymagania dotyczące każdej usługi, która wymaga certyfikatu użytkownika lub urządzenia w organizacji. Aby ułatwić to działanie, możesz użyć jednego z następujących szablonów planowania:  

- [Szablon certyfikatu PKCS](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/PKCS-certificate-template.xlsx)
- [Szablon certyfikatu SCEPT](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/SCEP-certificate-template.xlsx)

## <a name="wi-fi-connectivity-requirements"></a>Wi-Fi wymagań dotyczących łączności

Aby umożliwić automatyczne zapewnianie urządzenia do wymaganej Wi-Fi konfiguracji sieci przedsiębiorstwa, może być potrzebny profil konfiguracji Wi-Fi przedsiębiorstwa.

Możesz skonfigurować Microsoft Managed Desktop tych profilów na swoich urządzeniach. Jeśli bezpieczeństwo sieci wymaga, aby urządzenia były częścią domeny lokalnej, może być konieczne oszacowanie infrastruktury sieciowej usługi Wi-Fi w celu zapewnienia jej zgodności z Microsoft Managed Desktop urządzeniami. Microsoft Managed Desktop są tylko urządzeniami z systemem Azure AD.

Przed wdrożeniem konfiguracji Wi-Fi na Microsoft Managed Desktop, musisz zebrać informacje o wymaganiach organizacji dotyczących poszczególnych Wi-Fi sieci. Aby ułatwić tę aktywność, możesz użyć tego szablonu profilu [Wi-Fi](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/WiFi-profile-template.xlsx).

## <a name="wired-connectivity-requirements-and-8021x-authentication"></a>Wymagania dotyczące łączności przewodowej i uwierzytelniania 802.1x

Jeśli do zabezpieczenia dostępu z urządzeń do sieci lokalnej używasz uwierzytelniania 802.1x, musisz wypchnąć wymagane szczegóły konfiguracji do swoich Microsoft Managed Desktop sieci.

Microsoft Managed Desktop z systemem Windows 10, wersja 1809 lub nowszym obsługują wdrażanie konfiguracji 802.1x za pośrednictwem programu Konfiguracji przewodowej sieci usługodawca (CSP). Aby uzyskać więcej informacji, zobacz [Dokumentacja programu WiredNetwork CSP](/windows/client-management/mdm/wirednetwork-csp) .

Przed wdrożeniem profilu konfiguracji sieci przewodowej w Microsoft Managed Desktop zbierz wymagania organizacji dotyczące sieci przewodowej.

**Aby zebrać wymagania dotyczące przewodowej sieci firmowej:**

1. Zaloguj się na urządzeniu, które ma skonfigurowany profil 802.1x i jest połączone z siecią LAN.  
2. Otwórz wiersz polecenia z poświadczeniami administracyjnymi.
3. Znajdź nazwę interfejsu sieci LAN, uruchamiając program `netsh interface show interface`.
4. Wyeksportuj kod XML profilu sieci LAN, uruchamiając program `netsh lan export profile folder=.  Interface=”interface_name”`.
5. Jeśli chcesz przetestować wyeksportowany profil na Microsoft Managed Desktop, uruchom .`netsh lan add profile filename="PATH_AND_FILENAME.xml" interface="INTERFACE_NAME"`

## <a name="deploy-certificate-infrastructure"></a>Wdrażanie infrastruktury certyfikatów  

Jeśli masz już istniejącą infrastrukturę SCEPT lub PKCS z usługą Intune i ta metoda spełnia Twoje wymagania, możesz użyć jej także do Microsoft Managed Desktop.

Jeśli nie istnieje jeszcze infrastruktura SCEPT lub PKCS, musisz przygotować jedną z nich. Aby uzyskać więcej informacji, [zobacz Konfigurowanie profilu certyfikatu dla urządzeń w aplikacji Microsoft Intune](/intune/certificates-configure).

## <a name="deploy-a-lan-profile"></a>Wdrażanie profilu SIECI LAN

Po wyeksportowania profilu sieci LAN możesz przygotować zasady dla sieci Microsoft Managed Desktop.

**Aby przygotować zasady dla Microsoft Managed Desktop:**

1. Utwórz profil niestandardowy dla profilu Microsoft Intune LAN przy użyciu następujących ustawień (zobacz Używanie ustawień niestandardowych dla urządzeń Windows 10 [w usłudze Intune](/intune/custom-settings-windows-10)). W **niestandardowym uri OMA-URI Ustawienia** wybierz **pozycję Dodaj**, a następnie wprowadź następujące wartości:
    - Nazwa: Nowoczesny profil Workplace-Windows LAN 10
    - Opis. Wprowadź opis, który zawiera omówienie ustawienia i inne ważne informacje.
    - OMA-URI (zróżnicowa wielkość liter): Enter `./Device/Vendor/MSFT/WiredNetwork/LanXML`
    - Typ danych: Wybierz **pozycję Ciąg (plik XML).**
    - Niestandardowy xml: Upload wyeksportowany plik XML.
2. Przypisywanie profilu niestandardowego do **grupy Nowoczesne urządzenia miejsca pracy — Testowanie** .
3. Przetestuj, jaki uważasz za niezbędny, przy użyciu urządzenia z grupy Testowanie wdrożenia. Jeśli to się powiedzie, przypisz profil niestandardowy do następujących grup:
    - Nowoczesne urządzenia w miejscu pracy — pierwsze
    - Nowoczesne urządzenia w miejscu pracy — szybkie
    - Nowoczesne urządzenia w miejscu pracy — Ogólne

## <a name="deploy-certificates-and-wi-fivpn-profile"></a>Wdrażanie certyfikatów i profilu Wi-Fi/VPN

**Aby wdrożyć certyfikaty i profile:**

1. Utwórz profil dla każdego certyfikatu głównego i pośredniego (zobacz [Tworzenie zaufanych profilów certyfikatów](/intune/protect/certificates-configure#step-3-create-trusted-certificate-profiles)). Każdy z tych profilów musi zawierać opis, który zawiera datę wygaśnięcia w formacie DD/MM/YYYY. **Profile certyfikatów muszą mieć datę wygaśnięcia.**
2. Utwórz profil dla każdego certyfikatu SCEPT lub PKCS (zobacz Tworzenie [profilu certyfikatu SCEPT](/intune/protect/certificates-scep-configure#create-a-scep-certificate-profile) lub [Tworzenie profilu certyfikatu PKCS](/intune/protect/certficates-pfx-configure#create-a-pkcs-certificate-profile)). Każdy z tych profilów musi zawierać opis, który zawiera datę wygaśnięcia w formacie DD/MM/YYYY. **Profile certyfikatów muszą mieć datę wygaśnięcia.**
3. Utwórz profil dla każdej firmowej sieci [Wi-Fi (zobacz Ustawienia sieci Wi-Fi dla Windows 10 i nowszych urządzeń](/intune/wi-fi-settings-windows)).
4. Utwórz profil dla każdego firmowego połączenia VPN (zobacz Windows 10 ustawienia urządzenia [Holographic i Windows](/intune/vpn-settings-windows-10), aby dodać połączenia VPN przy użyciu usługi Intune).
5. Przypisz profile do grupy **Nowoczesne urządzenia w miejscu pracy — testowanie** .
6. Przetestuj, jaki uważasz za niezbędny, przy użyciu urządzenia z grupy Testowanie wdrożenia. Jeśli to się powiedzie, przypisz profil niestandardowy do następujących grup:
    - Nowoczesne urządzenia w miejscu pracy — pierwsze
    - Nowoczesne urządzenia w miejscu pracy — szybkie
    - Nowoczesne urządzenia w miejscu pracy — Ogólne

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Procedura przygotuj się do Microsoft Managed Desktop

1. Przejrzyj [wymagania wstępne dotyczące Microsoft Managed Desktop](prerequisites.md).
1. Uruchom [narzędzia do oceny gotowości](readiness-assessment-tool.md).
1. Kup [Portal firmy](../get-started/company-portal.md).
1. Przejrzyj [wymagania wstępne dotyczące kont gości](guest-accounts.md).
1. Sprawdź [konfigurację sieci](network.md).
1. Przygotowywanie certyfikatów i profilów sieci (ten artykuł).
1. [Przygotowywanie dostępu użytkownika do danych](authentication.md).
1. [Przygotowywanie aplikacji](apps.md).
1. [Przygotowywanie zamapowanych dysków](mapped-drives.md).
1. [Przygotowywanie zasobów do drukowania](printing.md).
1. Nazwy [urządzeń adresowych](address-device-names.md).
