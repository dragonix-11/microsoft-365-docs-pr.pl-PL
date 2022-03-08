---
title: Technologie zabezpieczeń w Microsoft Managed Desktop
description: Technologie używane do zabezpieczeń urządzeń, zarządzania tożsamościami i dostępem, zabezpieczeń sieci i zabezpieczeń informacji
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 4a6eb73a172ecfb680cbc48367851e40b1a54401
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315417"
---
# <a name="security-technologies-in-microsoft-managed-desktop"></a>Technologie zabezpieczeń w Microsoft Managed Desktop

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

Microsoft Managed Desktop korzysta z kilku technologii firmy Microsoft, aby chronić zarządzane urządzenia i dane. Ponadto Centrum Microsoft Managed Desktop Security Operations Center używa różnych [procesów](security-operations.md) w tych technologiach. Konkretnie:

| Proces | Opis |
| ------ | ------ |
| [Zabezpieczenia urządzeń](#device-security)| Zabezpieczenia i ochrona na Microsoft Managed Desktop urządzeniach. |
| [Zarządzanie tożsamościami i dostępem](#identity-and-access-management) | Zarządzanie bezpiecznym użyciem urządzeń za pośrednictwem Azure Active Directory tożsamości. |
| [Zabezpieczenia sieci](#network-security)| Informacje o sieci VPN Microsoft Managed Desktop zalecane rozwiązanie i ustawienia. |
| [Bezpieczeństwo informacji](#information-security)| Opcjonalne dostępne usługi do dalszej ochrony informacji poufnych. |

Aby uzyskać informacje na temat zasad przechowywania danych, używania i zabezpieczeń używanych przez firmę Microsoft Managed Desktop, zobacz nasz oficjalny oficjalny Microsoft Managed Desktop[https://aka.ms/mmd-data](https://aka.ms/mmd-data).

## <a name="device-security"></a>Zabezpieczenia urządzeń

Microsoft Managed Desktop zapewnia, że wszystkie zarządzane urządzenia są zabezpieczone i chronione oraz wykrywają zagrożenia jak najwcześniej przy użyciu następujących usług:

| Usługa | Opis |
| ----- | ----- |
| Oprogramowanie antywirusowe | Program antywirusowy Microsoft Defender jest zainstalowany i skonfigurowany<br>Program antywirusowy Microsoft Defender definicje są aktualne. |
| Pełne szyfrowanie woluminów | Windows BitLocker to rozwiązanie do szyfrowania woluminów dla Microsoft Managed Desktop przenośnych.<br><br>Po zarejestrowaniu organizacji w usłudze urządzenia będą szyfrowane przy użyciu funkcji Windows BitLocker z wbudowanym modułem platformy zaufania (TPM), aby uniemożliwić nieautoryzowany dostęp do danych lokalnych, gdy urządzenie jest w trybie uśpienia lub wyłączone.
| Monitorowanie | Program Microsoft Defender for Endpoint jest używany do monitorowania zagrożeń bezpieczeństwa na Microsoft Managed Desktop urządzeniach. Program Defender for Endpoint pozwala klientom korporacyjnym wykrywać zaawansowane zagrożenia w swojej sieci firmowej, badać je i reagować na nie. Aby uzyskać więcej informacji, zobacz [Program Microsoft Defender dla punktu końcowego.](/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) |
| Aktualizacje systemu operacyjnego | Microsoft Managed Desktop są zawsze zabezpieczone najnowszymi aktualizacjami zabezpieczeń. |
| Bezpieczna konfiguracja urządzenia | Microsoft Managed Desktop planu bazowego firmy Microsoft. Aby uzyskać więcej informacji, [zobacz Windows planu bazowego zabezpieczeń.](/windows/security/threat-protection/windows-security-baselines)|

## <a name="identity-and-access-management"></a>Zarządzanie tożsamością i dostępem

Zarządzanie tożsamością i dostępem chroni zasoby firmy i dane o krytycznym znaczeniu dla firmy. Microsoft Managed Desktop urządzenia w celu zapewnienia bezpiecznego używania z tożsamościami zarządzanymi przez Azure Active Directory usługi Azure AD. Zapewnienie dokładnych informacji w dzierżawie usługi Azure AD spoczywa na kliencie.

| Usługa | Opis |
| ----- | ----- |
| Uwierzytelnianie biometryczne | Windows Hello użytkownicy mogą się zalogować przy użyciu twarzy lub numeru PIN, co utrudnia zapomnienie lub kradzież hasła. Klienci są odpowiedzialni za zaimplementowanie niezbędnych wymagań wstępnych dla lokalnej usługi Active Directory w celu używania tej usługi w konfiguracji hybrydowej. Aby uzyskać więcej informacji, [zobacz Windows Hello.](/windows-hardware/design/device-experiences/windows-hello) |
| Standardowe uprawnienie użytkownika | Aby chronić system i go zabezpieczyć, użytkownikowi zostaną przypisane uprawnienia użytkownika standardowego. To uprawnienie jest przypisywane w ramach rozwiązania Windows rozwiązania Autopilot.

## <a name="network-security"></a>Zabezpieczenia sieci

Klienci są odpowiedzialni za bezpieczeństwo sieci.

| Usługa | Opis |
| ----- | ----- |
| VPN | Klienci są właścicielami swojej infrastruktury VPN, aby mieć pewność, że ograniczone zasoby firmowe mogą być udostępniane poza intranetem.<br><br>Minimalne wymaganie: Microsoft Managed Desktop wymaga Windows 10 zgodnego i obsługiwanego rozwiązania VPN. Jeśli Twoja organizacja potrzebuje rozwiązania VPN, musi ona obsługiwać sieć Windows 10 być pakowana i wdrażana za pośrednictwem usługi Intune. Aby uzyskać więcej informacji, skontaktuj się z wydawcą oprogramowania.<br><br>Zalecenie:<br><ul><li> Firma Microsoft zaleca nowoczesne rozwiązanie VPN, które można łatwo wdrożyć za pośrednictwem usługi Intune w celu wypchania profilów VPN. To rozwiązanie zapewnia zawsze łatwy, niezawodny i bezpieczny sposób dostępu do sieci firmowej. Aby uzyskać więcej informacji, zobacz [Ustawienia sieci VPN w usłudze Intune](/intune/vpn-settings-configure).</li><li>Grubi klienci SIECI VPN lub starsi klienci SIECI VPN nie są zalecane przez firmę Microsoft podczas Microsoft Managed Desktop ponieważ może to wpłynąć na środowisko użytkownika.</li><li>Firma Microsoft zaleca, aby wychodzący ruch w sieci Web przechodził bezpośrednio do Internetu bez pośrednictwa sieci VPN w celu uniknięcia problemów z wydajnością.</li><li>Najlepiej, jeśli firma Microsoft zaleca korzystanie z Azure Active Directory proxy aplikacji zamiast połączenia VPN.</li></ul>

## <a name="information-security"></a>Bezpieczeństwo informacji

Te opcjonalne usługi można skonfigurować w celu ochrony firmowych zasobów o wysokiej wartości.

| Usługa | Opis |
| ----- | ----- |
| Odzyskiwanie danych | Kopii zapasowe informacji przechowywanych w kluczowych folderach na urządzeniu to OneDrive dla Firm. Microsoft Managed Desktop nie ponosi odpowiedzialności za dane, które nie są synchronizowane z OneDrive dla Firm.
| Windows informacji | W przypadku firm wymagających wysokiego poziomu zabezpieczeń informacji zalecamy korzystanie z usługi [Windows Information Protection](/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) i [Azure Information Protection.](https://www.microsoft.com/cloud-platform/azure-information-protection)
