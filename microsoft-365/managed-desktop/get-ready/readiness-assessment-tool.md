---
title: Narzędzia do oceny gotowości
description: Objaśnienia obu narzędzi, uruchomionych testów oraz znaczenia wyników
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 96bd667cf5d3661476111f7593632f0e5362cf45
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011380"
---
# <a name="readiness-assessment-tools"></a>Narzędzia do oceny gotowości

Aby zapewnić jak najs wygładzone środowisko podczas rejestracji w aplikacji Microsoft Managed Desktop, musisz wcześniej ustawić ustawienia i inne parametry oraz pewne wymagania dotyczące urządzenia i sieci.

Jedno narzędzie dostępne za pośrednictwem Microsoft Managed Desktop administracyjnego sprawdza ustawienia związane z zarządzaniem. Inne narzędzie, które można pobrać, sprawdza wymagania dotyczące poszczególnych urządzeń i ustawienia sieciowe. Za pomocą tych narzędzi możesz sprawdzić te ustawienia i uzyskać szczegółowe instrukcje dotyczące rozwiązywania problemów, które są jakikolwiek.

## <a name="downloadable-readiness-assessment-checker-for-devices-and-network"></a>Sprawdzanie gotowości na urządzeniach i w sieci do pobrania

Aby uzyskać szczegółowe informacje na temat korzystania z narzędzia do sprawdzania gotowości do pobrania, zobacz Sprawdzanie gotowości [do pobrania](readiness-assessment-downloadable.md).

## <a name="online-readiness-assessment-tool-for-management-settings"></a>Narzędzie do oceny gotowości online dla ustawień zarządzania

Narzędzie [online](https://aka.ms/mmdart) sprawdza ustawienia w usługach Microsoft Endpoint Manager (w szczególności Microsoft Intune), Azure Active Directory (Azure AD) i Microsoft 365, aby upewnić się, że będą one współpracować z usługami Microsoft Managed Desktop .

Microsoft Managed Desktop przechowuje dane skojarzone z tymi testami przez 12 miesięcy od ostatniego uruchomienia kontroli w organizacji usługi Azure AD (dzierżawie). Po upływie 12 miesięcy przechowujemy ją w postaci odszukajmy. Możesz wybrać opcję usunięcia zbieranych przez nas danych.

To narzędzie będzie mógł uruchomić każdy, kto ma co najmniej rolę czytelnika globalnego lub administratora usługi Intune, ale dwie z tych [testów (zasady](readiness-assessment-fix.md#conditional-access-policies) dostępu warunkowego i uwierzytelnianie wieloskładnikowe [wymagają dodatkowych](readiness-assessment-fix.md#multi-factor-authentication) uprawnień.

> [!IMPORTANT]  
> Narzędzie do oceny gotowości w trybie online ułatwia sprawdzenie gotowości do zarejestrowania się Microsoft Managed Desktop po raz pierwszy. Jeśli Twoja organizacja jest już zarejestrowany w programie Microsoft Managed Desktop, nie używaj tego narzędzia.

Narzędzie do oceny sprawdza następujące elementy:

## <a name="microsoft-intune-settings"></a>Microsoft Intune sieci Microsoft Intune

Poniżej przedstawiono Microsoft Intune ustawienia:

| Czek | Opis |
| ------ | ------ |
| Profil wdrożenia z autopilotem | Sprawdza, czy przypisanie profilu wdrożenia z zastosowaniem funkcji Autopilot nie ma zastosowania do wszystkich urządzeń. <br><br> Profil nie **powinien być** przypisany do żadnych Microsoft Managed Desktop urządzeniach. |
| Łączniki certyfikatów | Sprawdza stan łączników certyfikatów, aby upewnić się, że są aktywne. |
| Dostęp warunkowy | Sprawdza, czy zasady dostępu warunkowego nie są przypisane do wszystkich użytkowników. <br><br> Zasady dostępu **warunkowego nie** powinny być przypisywane do Microsoft Managed Desktop usług. |
| Zasady zgodności urządzeń | Sprawdza, czy zasady zgodności usługi Intune nie są przypisane do wszystkich użytkowników. <br><br> Zasady nie **powinny być** przypisywane do żadnych Microsoft Managed Desktop urządzeniach. |
| Profile konfiguracji urządzenia | Potwierdza, że profile konfiguracji nie są przypisane do wszystkich użytkowników lub wszystkich urządzeń. <br><br> Profile konfiguracji nie **powinny być** przypisywane do żadnych Microsoft Managed Desktop urządzeniach. |
| Ograniczenia typu urządzenia | Sprawdza, Windows 10 urządzenia w Twojej organizacji mogą zarejestrować się w usłudze Intune. |
| Strona stanu rejestracji | Potwierdza, że strona Stan rejestracji nie jest włączona. |
| Rejestracja w usłudze Intune | Sprawdza, czy Windows 10 w organizacji usługi Azure AD są automatycznie zarejestrowane w usłudze Intune. |
| Microsoft Store dla Firm | Potwierdza, że Microsoft Store dla Firm jest włączona i zsynchronizowana z usługą Intune. |
| Uwierzytelnianie wieloskładnikowe | Sprawdza, czy uwierzytelnianie wieloskładnikowe nie jest stosowane Microsoft Managed Desktop kontach usług. |
| Skrypty programu PowerShell | Sprawdza, Windows PowerShell **skryptów nie** są przypisywane w sposób docelowy Microsoft Managed Desktop urządzeniach. |
| Region | Sprawdza, czy Twój region jest obsługiwany przez Microsoft Managed Desktop. |
| Linie bazowe zabezpieczeń | Sprawdza, czy profil planu bazowego zabezpieczeń nie jest docelowy dla wszystkich użytkowników ani wszystkich urządzeń. <br><br> Zasady planu bazowego zabezpieczeń **nie powinny być** kierowane Microsoft Managed Desktop urządzeniach. |
| Windows aplikacji | Przejrzyj aplikacje, które chcesz przypisać do Microsoft Managed Desktop urządzeniach. |
| Windows Hello dla firm | Sprawdza, czy Windows Hello dla firm jest włączone. |
| Windows 10 pierścienia aktualizacji | Sprawdza, czy zasady "Windows 10 pierścienia aktualizacji usługi Intune" nie są kierowane do wszystkich użytkowników lub wszystkich urządzeń. <br><br> Zasady nie **powinny być kierowane do** żadnych Microsoft Managed Desktop urządzeniach. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory ustawień

Poniżej przedstawiono Azure Active Directory ustawienia:

| Czek | Opis |
| ----- | ----- |
| Subskrypcje "Ad hoc" dla roamingu Enterprise stanowego | Zaleca się sprawdzenie ustawienia, które w przypadku ustawienia wartości "fałsz" może uniemożliwić poprawne działanie roamingu Enterprise roamingu województwa. |
| Enterprise roamingu województwa | Zaleca się sprawdzenie, czy jest włączone Enterprise Roamingu województwa. |
| Licencje | Sprawdza, czy uzyskano niezbędne [licencje](prerequisites.md#more-about-licenses). |
| Uwierzytelnianie wieloskładnikowe | Sprawdza, czy uwierzytelnianie wieloskładnikowe nie jest stosowane do wszystkich użytkowników. <br><br> Uwierzytelnianie wieloskładnikowe **nie** może zostać przypadkowo zastosowane Microsoft Managed Desktop kontach usług. |
| Nazwy kont zabezpieczeń | Sprawdza, czy nazwy użytkowników nie są w konflikcie z Microsoft Managed Desktop zarezerwowanymi do użytku własnego. |
| Role administratora zabezpieczeń | Potwierdza, że użytkownikom korzystającym z czytnika zabezpieczeń, operatorowi zabezpieczeń lub czytelnikowi globalnemu przypisano te role w programie Microsoft Defender for Endpoint. |
| Domyślne ustawienia zabezpieczeń | Sprawdza, czy w organizacji usługi Azure AD włączono domyślne ustawienia domyślne zabezpieczeń w usłudze Azure Active Directory. |
| Samodzielne resetowanie hasła | Potwierdza, że funkcja samodzielnego resetowania hasła jest włączona. |
| Standardowa rola użytkownika | Sprawdza, czy użytkownicy są użytkownikami standardowymi i nie mają uprawnień administratora lokalnego. |

## <a name="microsoft-365-apps-for-enterprise-settings"></a>Aplikacje Microsoft 365 dla Enterprise ustawień

Poniżej przedstawiono Aplikacje Microsoft 365 ustawień Enterprise sieci:

| Czek | Opis |
| ----- | ----- |
| OneDrive dla Firm | Sprawdza, OneDrive dla Firm korzysta z nieobsługiwanych ustawień. |

Dla każdego sprawdzenia narzędzie raportuje jeden z czterech możliwych wyników:

| Result (Wynik) | Znaczenie |
| ----- | ----- |
| Gotowe | Przed ukończeniem rejestracji nie jest wymagane żadne działanie. |
| Porada | Postępuj zgodnie z instrukcjami w narzędziu, aby uzyskać najlepsze środowisko rejestracji i dla użytkowników. <br><br> Możesz *zakończyć* rejestrację, ale musisz rozwiązać te problemy przed wdrożeniem pierwszego urządzenia. |
| Jeszcze nie gotowe | **Rejestracja nie powiedzie się** , jeśli nie rozwiążesz tych problemów. <br><br> Postępuj zgodnie z instrukcjami narzędzia, aby je rozwiązać. |
| Error | Rola Azure Active Director (AD, Azure Active Director) nie ma wystarczających uprawnień do uruchomienia tego sprawdzania. |

## <a name="after-enrollment"></a>Po rejestracji

Po zakończeniu rejestracji w usłudze Microsoft Managed Desktop pamiętaj, aby wrócić i dostosować pewne ustawienia usługi Intune i Azure AD. Aby uzyskać więcej informacji, [zobacz Dostosowywanie ustawień po rejestracji](../get-started/conditional-access.md).

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Procedura przygotuj się do Microsoft Managed Desktop

1. Przejrzyj [wymagania wstępne dotyczące Microsoft Managed Desktop](prerequisites.md).
2. Uruchom narzędzia do oceny gotowości (ten artykuł).
3. Kup [Portal firmy](../get-started/company-portal.md).
4. Przejrzyj [wymagania wstępne dotyczące kont gości](guest-accounts.md).
5. Sprawdź [konfigurację sieci](network.md).
6. [Przygotowywanie certyfikatów i profilów sieci](certs-wifi-lan.md).
7. [Przygotowywanie dostępu użytkownika do danych](authentication.md).
8. [Przygotowywanie aplikacji](apps.md).
9. [Przygotowywanie zamapowanych dysków](mapped-drives.md).
10. [Przygotowywanie zasobów do drukowania](printing.md).
11. Nazwy [urządzeń adresowych](address-device-names.md).
