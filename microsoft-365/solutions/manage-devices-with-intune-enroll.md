---
title: Krok nr 2. Rejestrowanie urządzeń w zarządzaniu przy użyciu Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into management
- enroll devices to Intune
- Intune mobile device platforms
manager: dougeby
audience: ITPro
description: Użyj Intune i rozwiązania Autopilot, aby zarejestrować urządzenia w zarządzaniu, aby zapewnić zgodność uruchomionych na nich aplikacji i zapobiec wyciekom danych firmowych.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 98c98298b5bb6728a0f8526e0406fb1fe02654f0
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2022
ms.locfileid: "64704719"
---
# <a name="step-2-enroll-devices-to-intune"></a>Krok nr 2. Rejestrowanie urządzeń do Intune

Istnieje kilka sposobów zabezpieczenia punktu końcowego— termin często używany do odwoływania się do połączonej jednostki, w tym urządzeń, aplikacji i tożsamości użytkownika. Zasady zabezpieczeń muszą być wymuszane spójnie i niezawodnie nie tylko w aplikacjach, ale na samym urządzeniu. Rejestrowanie urządzenia w celu Intune i rejestrowanie u dostawcy tożsamości w chmurze, takiego jak Azure Active Directory, to świetny początek.

Niezależnie od tego, czy urządzenie jest urządzeniem należącym do użytkownika, czy urządzeniem należącym do firmy i w pełni zarządzanym, dobrze jest mieć wgląd w punkty końcowe uzyskujące dostęp do zasobów organizacji, aby upewnić się, że zezwalasz tylko na urządzenia w dobrej kondycji i zgodne. Obejmuje to kondycję i wiarygodność aplikacji mobilnych i klasycznych uruchamianych w punktach końcowych. Chcesz mieć pewność, że te aplikacje są w dobrej kondycji i zgodne oraz że zapobiegają wyciekowi danych firmowych do aplikacji lub usług konsumenckich za pośrednictwem złośliwych intencji lub przypadkowych środków.

Proces rejestracji urządzenia ustanawia relację między użytkownikiem, urządzeniem i usługą Microsoft Intune. Użycie Microsoft Intune jako usługi autonomicznej umożliwia korzystanie z jednej internetowej konsoli administracyjnej do zarządzania komputerami Windows, macOS i najpopularniejszymi platformami urządzeń przenośnych.

W tym artykule zaleca się metody rejestrowania urządzeń do Intune. Aby uzyskać więcej informacji na temat tych metod i sposobu wdrażania poszczególnych metod, zobacz [Wskazówki dotyczące wdrażania: Rejestrowanie urządzeń w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment).

![Kroki zarządzania urządzeniami](../media/devices/intune-mdm-steps-1.png#lightbox)

## <a name="windows-enrollment"></a>rejestracja Windows
Istnieje kilka opcji rejestrowania urządzeń Windows 10 i Windows 11. Najczęstsze metody obejmują następujące dwie metody:

- Azure Active Directory (Azure AD) Join — dołącza urządzenie do Azure Active Directory i umożliwia użytkownikom logowanie się do Windows przy użyciu poświadczeń usługi Azure AD. Jeśli rejestracja automatyczna jest włączona, urządzenie zostanie automatycznie zarejestrowane w Intune. Zaletą automatycznej rejestracji jest proces jednoetapowy dla użytkownika. W przeciwnym razie będą musieli zarejestrować się osobno tylko za pośrednictwem rejestracji mdm i ponownie wprowadzić swoje poświadczenia. Użytkownicy rejestrują się w ten sposób podczas początkowego Windows OOBE lub z Ustawienia. Urządzenie jest oznaczone jako urządzenie należące do firmy w Intune.
- Rozwiązanie Autopilot — automatyzuje dołączanie do usługi Azure AD i rejestruje nowe urządzenia należące do firmy w Intune. Ta metoda upraszcza środowisko out-of-box i eliminuje konieczność stosowania niestandardowych obrazów systemu operacyjnego na urządzeniach. Gdy administratorzy używają Intune do zarządzania urządzeniami rozwiązania Autopilot, mogą zarządzać zasadami, profilami, aplikacjami i nie tylko po ich zarejestrowaniu. Istnieją cztery typy wdrażania rozwiązania Autopilot: tryb Self-Deploying (dla kiosków, oznakowania cyfrowego lub urządzenia udostępnionego), tryb sterowany przez użytkownika (dla tradycyjnych użytkowników), Windows Autopilot dla wstępnie aprowizowanego wdrożenia umożliwia partnerom lub pracownikom IT wstępne aprowizowanie komputera z systemem Windows 10 lub Windows 11  dzięki temu jest w pełni skonfigurowany i gotowy do działania, a rozwiązanie Autopilot dla istniejących urządzeń umożliwia łatwe wdrażanie najnowszej wersji Windows na istniejących urządzeniach.

Aby uzyskać dodatkowe opcje, w tym rejestrowanie urządzeń Windows BYOD, zobacz [Rejestrowanie urządzeń Windows w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows).

## <a name="ios-and-ipados-enrollment"></a>Rejestracja w systemach iOS i iPadOS

W przypadku urządzeń należących do użytkownika (BYOD) można zezwolić użytkownikom na rejestrowanie urządzeń osobistych przy użyciu Intune przy użyciu jednej z następujących metod.
- Rejestracja urządzenia jest typową rejestracją BYOD. Zapewnia administratorom szeroką gamę opcji zarządzania.
- Rejestracja użytkowników to usprawniony proces rejestracji, który zapewnia administratorom podzbiór opcji zarządzania urządzeniami. Ta funkcja jest obecnie dostępna w wersji zapoznawczej.

W przypadku organizacji, które kupują urządzenia dla swoich użytkowników, Intune obsługuje następujące metody rejestracji urządzeń należących do firmy z systemem iOS/iPadOS:
- Automatyczna rejestracja urządzeń firmy Apple (ADE)
- Apple School Manager
- Rejestracja asystenta ustawień programu Apple Configurator
- Rejestracja bezpośrednia programu Apple Configurator

Aby uzyskać więcej informacji, zobacz [Rejestrowanie urządzeń z systemem iOS i iPadOS w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados).

## <a name="android-enrollment"></a>Rejestracja w systemie Android 

Istnieje kilka opcji rejestracji systemu Android w zależności od typu urządzenia, typu rejestracji, który chcesz obsługiwać, a także takich elementów jak używana wersja systemu Android, a nawet producent (szczególnie Samsung). Większość organizacji używa profilów służbowych systemu Android dla swoich użytkowników końcowych, w szczególności w scenariuszach BYOD. 

Dzięki profilowi służbowemu systemu Android informacje użytkownika końcowego są odrębnie oddzielone kontenerami danych, a także oddzielnymi aplikacjami do użytku służbowego i osobistego. Jest to idealny sposób rejestrowania urządzenia przez użytkowników przy zachowaniu prywatności własnych danych i bezpieczeństwa danych firmowych. 

Jeśli jednak organizacja udostępnia urządzenia z systemem Android, możesz użyć urządzenia nazywanego w pełni zarządzanym (koligacja użytkownika) lub dedykowanym urządzeniem (bez koligacji użytkownika).

Aby dowiedzieć się więcej na temat rejestracji w systemie Android, zobacz [Rejestrowanie urządzeń z systemem Android w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android).

## <a name="macos-enrollment"></a>Rejestracja w systemie macOS

Rejestracja w systemie macOS może być trudnym tematem dla wielu organizacji IT. Chyba że większość użytkowników to użytkownicy komputerów Mac, niż ty może nie zarządzać tego typu urządzeniami w dużym stopniu. Jeśli masz niewielką liczbę użytkowników systemu macOS, zalecamy Intune Tylko rejestracja. Jeśli masz dużą liczbę użytkowników systemu macOS, zalecamy Intune + Rejestrowanie jamf.  
- Intune Tylko rejestracja — dotyczy to podstawowego zarządzania urządzeniami z systemem macOS. Będzie to wymagało ręcznego procesu, podobnie jak większość innych opcji rejestracji opartych na użytkownikach. Jeśli jednak masz niewielką liczbę urządzeń Mac, może to być łatwiejsze niż skonfigurowanie całej zautomatyzowanej infrastruktury tylko dla tych nielicznych użytkowników. Dzięki Intune tylko rejestracji można wdrażać takie elementy, jak certyfikaty, konfiguracje haseł i aplikacje. Można również skonfigurować zasady zgodności i oświecić dostęp warunkowy, a także możliwość wymuszania szyfrowania i czyszczenia urządzeń. 
- Intune i rejestrowanie jamf — dla tych, którzy szukają najgłębszej obsługi zarządzania komputerami Mac, z narzędziem Jamf + Intune dostępu warunkowego, mamy doskonałe rozwiązanie, które łączy w sobie rozbudowane możliwości zarządzania komputerami Mac narzędzia Jamf z Intune zgodności w celu włączenia dostępu warunkowego. W tym scenariuszu nadal w pełni zarządzasz urządzeniem za pomocą narzędzia Jamf, jednocześnie będąc w stanie pobrać te sygnały z narzędzia Jamf w celu zwiększenia bezpieczeństwa.

Aby dowiedzieć się więcej na temat rejestracji w systemie macOS, zobacz [Rejestrowanie urządzeń z systemem macOS w Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-macos).

## <a name="next-steps"></a>Następne kroki

Przejdź do kroku [3. Konfigurowanie zasad zgodności dla urządzeń z Intune](manage-devices-with-intune-compliance-policies.md).

