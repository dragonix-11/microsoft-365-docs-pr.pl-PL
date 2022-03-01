---
title: Krok nr 2. Rejestrowanie urządzeń do zarządzania za pomocą usługi Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into management
- enroll devices with Intune
- Intune mobile device platforms
manager: dougeby
audience: ITPro
description: Skorzystaj z usługi Intune i rozwiązania Autopilot, aby zarejestrować urządzenia do zarządzania, aby zapewnić zgodność uruchomionych na nich aplikacji oraz aby zapobiec wyciekom firmowych danych.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 5810513cd3aa4fccd8ce0100f22c708c53527c42
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/02/2022
ms.locfileid: "63009838"
---
# <a name="step-2-enroll-devices-into-management-with-intune"></a>Krok nr 2. Rejestrowanie urządzeń do zarządzania za pomocą usługi Intune

Istnieje kilka sposobów zabezpieczania punktu końcowego. Termin często używany do odwoływać się do połączonej jednostki, w tym urządzenia, aplikacje i tożsamość użytkownika. Zasady zabezpieczeń muszą być wymuszane spójnie i niezawodnie nie tylko w aplikacjach, ale również na samym urządzeniu. Zarejestrowanie urządzenia w zarządzaniu i zarejestrowanie się u dostawcy tożsamości w chmurze, takiego Azure Active Directory, to dobry początek.

Niezależnie od tego, czy urządzenie należy do Ciebie, czy do firmy i jest w pełni zarządzane, warto mieć wgląd w punkty końcowe uzyskiwania dostępu do zasobów organizacji, aby upewnić się, że zezwalasz tylko na prawidłowe i zgodne urządzenia. Obejmuje to kondycję i wiarygodności aplikacji mobilnych i klasycznych uruchamianych w punktach końcowych. Chcesz zapewnić, że te aplikacje są w dobrej kondycji i zgodne oraz że zapobiegają wyciekowi danych firmowych do aplikacji lub usług dla klientów konsumenckich w ramach złośliwych intencji lub przypadkowych środków.

Proces rejestracji urządzenia ustanawia relację między użytkownikiem, urządzeniem i usługą Microsoft Intune urządzenia. Używanie Microsoft Intune jako usługi autonomicznej umożliwia zarządzanie komputerami Windows PC, macOS i najpopularniejszymi platformami urządzeń przenośnych za pomocą jednej internetowej konsoli administracyjnej.

W tym artykule zaleca się metody rejestrowania urządzeń do zarządzania za pomocą usługi Intune. Aby uzyskać więcej informacji na temat tych metod i sposobu wdrażania każdej z nich, zobacz Wskazówki dotyczące wdrażania[: Rejestrowanie urządzeń](/mem/intune/fundamentals/deployment-guide-enrollment) w aplikacji Microsoft Intune.

![Procedura zarządzania urządzeniami](../media/devices/intune-mdm-steps-1.png#lightbox)

## <a name="windows-enrollment"></a>Windows rejestracji
Istnieje kilka możliwości zarejestrowania nowych Windows 10 i Windows 11 urządzeń. Najczęściej stosowane metody to:

- Azure Active Directory (Azure AD) — dołącza do urządzenia za pomocą programu Azure Active Directory i umożliwia użytkownikom logowanie się do usługi Windows przy użyciu poświadczeń usługi Azure AD. Jeśli funkcja Automatycznego rejestrowania jest włączona, urządzenie jest automatycznie zarejestrowane w usłudze Intune. Zaletą rejestracji automatycznej jest proces jednoetapowy dla użytkownika. W przeciwnym razie będą oni muszą zarejestrować się oddzielnie za pośrednictwem rejestracji mdM tylko i ponownie do swoich poświadczeń. Użytkownicy zarejestrują się w ten sposób podczas początkowego Windows OOBE lub z Ustawienia. W usłudze Intune urządzenie jest oznaczone jako urządzenie firmowe.
- Autopilot — automatyzuje dołączanie do usługi Azure AD i zapisuje nowe urządzenia firmowe w usłudze Intune. Ta metoda upraszcza takie środowisko pracy i usuwa konieczność stosowania na urządzeniach niestandardowych obrazów systemu operacyjnego. Gdy administratorzy zarządzają urządzeniami z rozwiązaniami Autopilot za pomocą usługi Intune, mogą zarządzać zasadami, profilami, aplikacjami i nie tylko po ich zarejestrowaniu. Istnieją cztery typy wdrożenia z programem Autopilot: tryb Self-Deploying (w przypadku kiosków, podpisów cyfrowych lub urządzenia udostępnionego), Tryb oparty na użytkowniku (dla użytkowników tradycyjnych), rozwiązania Windows Autopilot w celu wdrożenia wstępnie aprowizowego umożliwia partnerom lub personelowi IT wstępne inicjowanie obsługi administracyjnej komputera z systemem Windows 10 lub Windows  11 Tak, aby była w pełni skonfigurowana i gotowa do pracy, a rozwiązania Autopilot dla istniejących urządzeń umożliwiają łatwe wdrożenie najnowszej wersji pakietu Windows na istniejących urządzeniach.

Aby uzyskać dodatkowe opcje, takie jak rejestrowanie byOD Windows urządzeniach, zobacz Rejestrowanie Windows [urządzeniach w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows).

## <a name="ios-and-ipados-enrollment"></a>Rejestracja w systemach iOS i iPadOS

W przypadku urządzeń należących do użytkownika (BYOD) możesz pozwolić użytkownikom na zarejestrowanie swoich urządzeń osobistych w usłudze Intune za pomocą jednej z następujących metod.
- Rejestracja urządzeń to, co możesz sądzić jako typowa rejestracja BYOD. Zapewnia on administratorom szereg opcji zarządzania.
- Rejestracja użytkowników to usprawniony proces rejestracji, który zapewnia administratorom podzbiór opcji zarządzania urządzeniami. Ta funkcja jest obecnie w wersji Preview.

W przypadku organizacji, które kupują urządzenia dla swoich użytkowników, usługa Intune obsługuje następujące metody rejestracji urządzeń należące do firmy dla systemu iOS/iPadOS:
- ADE (Automated Device Enrollment) firmy Apple
- Apple School Manager
- Rejestracja asystenta konfiguracji programu Apple Configurator
- Rejestracja bezpośrednia w programie Apple Configurator

Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń z systemami iOS i iPadOS w aplikacji Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados).

## <a name="android-enrollment"></a>Rejestracja w systemie Android 

Istnieje kilka opcji rejestracji na Androida w zależności od typu urządzenia, typu rejestracji, które chcesz obsługiwać, a także takich rzeczy, jak wersja systemu Android, z których korzystasz, a nawet producent (zwłaszcza Samsung). Większość organizacji używa profilów służbowych systemu Android dla użytkowników końcowych, w szczególności w scenariuszach byOD. 

W profilu służbowym systemu Android informacje użytkownika końcowego są oddzielone odrębnie kontenerami danych, a także osobne aplikacje do użytku służbowego i osobistego. Jest to doskonały sposób na zarejestrowanie urządzenia przy zachowaniu prywatności własnych danych i bezpieczeństwa danych firmowych. 

Jeśli jednak Twoja organizacja udostępnia urządzenia z systemem Android, możesz zdecydować się na użycie urządzenia w pełni zarządzanego (User Affinity) lub dedykowanego (bez chętnych użytkowników).

Aby dowiedzieć się więcej o rejestracji w systemie Android, zobacz [Rejestrowanie urządzeń z systemem Android w aplikacji Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android).

## <a name="macos-enrollment"></a>rejestracja w systemie macOS

Rejestracja w systemie macOS może być kłopotliwa dla wielu organizacji IT. O ile większość użytkowników nie jest użytkownikami komputerów Mac, niż zarządza się tymi typami urządzeń w dużej mierze. Jeśli masz małą liczbę użytkowników macOS, zalecamy skorzystanie z usługi Intune Only Enrollment (Rejestracja w usłudze Intune). Jeśli masz dużą liczbę użytkowników macOS, zalecamy rejestrację w usłudze Intune + Jamf.  
- Rejestracja tylko w usłudze Intune — ta funkcja umożliwia podstawowe zarządzanie urządzeniami z systemem macOS. Proces ten będzie wymagał ręcznego przetwarzania podobnie jak większość innych opcji rejestracji opartej na użytkownikach. Jeśli jednak masz małą liczbę urządzeń Mac, może to być łatwiejsze niż skonfigurowanie całej automatycznej infrastruktury tylko dla tych kilku użytkowników. W usłudze Intune możesz wdrażać tylko takie funkcje jak certyfikaty, konfiguracje haseł i aplikacje. Możesz również skonfigurować zasady zgodności i dostęp warunkowy oraz możliwość wymuszania szyfrowania i czyszczenia urządzenia. 
- Rejestracja w usłudze Intune i programie Jamf — dla osób szukających najgłębszej obsługi zarządzania dla komputerów Mac dzięki usługom Jamf + Intune for Conditional Access udostępniamy doskonałe rozwiązanie, które łączy rozbudowane funkcje zarządzania komputerem Mac usługi Jamf ze zgodnością Intune, aby włączyć dostęp warunkowy. W tym scenariuszu nadal w pełni zarządzasz urządzeniem za pomocą urządzenia Jamf, jednocześnie mając możliwość zasyłania tych sygnałów z firmy Jamf w celu zwiększenia bezpieczeństwa.

Aby dowiedzieć się więcej o rejestracji w systemie macOS, zobacz [Rejestrowanie urządzeń z systemem macOS w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-macos).

## <a name="next-steps"></a>Następne kroki

Przejdź do kroku [3. Skonfiguruj zasady zgodności dla urządzeń za pomocą usługi Intune](manage-devices-with-intune-compliance-policies.md).

