---
title: Zarządzanie urządzeniami przy użyciu Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into Intune
- manage device endpoints
- zero trust deployment stack
- device management with zero trust
manager: dougeby
audience: ITPro
ms.topic: article
description: Zarejestruj urządzenia punktu końcowego w Microsoft Intune w ramach architektury zabezpieczeń Zero Trust, chroniąc przed oprogramowaniem wymuszającym okup podczas tworzenia ochrony pracowników zdalnych.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: 218ffa6ba9b2e7a4eb5fcd2f042b77b207ab8594
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468047"
---
# <a name="manage-devices-with-intune-overview"></a>Omówienie zarządzania urządzeniami za pomocą Intune

Podstawowy składnik zabezpieczeń na poziomie przedsiębiorstwa obejmuje zarządzanie urządzeniami i ich ochronę. Niezależnie od tego, czy tworzysz Zero Trust architekturę zabezpieczeń, wzmacniasz ochronę środowiska przed oprogramowaniem wymuszającym okup, czy tworzysz ochronę w celu obsługi pracowników zdalnych, zarządzanie urządzeniami jest częścią strategii.
Chociaż Microsoft 365 obejmuje kilka narzędzi i metodologii zarządzania urządzeniami i ich ochrony, te wskazówki przedstawiają zalecenia firmy Microsoft dotyczące Microsoft Intune. Są to odpowiednie wskazówki dla Ciebie, jeśli:

- Zaplanuj rejestrowanie urządzeń w Intune za pośrednictwem Azure AD Join (w tym dołączania hybrydowego Azure AD).
- Zaplanuj ręczne rejestrowanie urządzeń w Intune.
- Zezwalaj urządzeniom BYOD z planami na implementowanie ochrony aplikacji i danych i/lub rejestrowanie tych urządzeń w celu Intune.

Z drugiej strony, jeśli środowisko zawiera plany współzarządzania, w tym Microsoft Endpoint Configuration Manager, zobacz [dokumentację współzarządzania](/mem/configmgr/comanage/), aby opracować najlepszą ścieżkę dla organizacji. Jeśli środowisko zawiera plany Komputer w chmurze Windows 365, zobacz [Windows 365 Enterprise dokumentację](/windows-365/enterprise/), aby opracować najlepszą ścieżkę dla organizacji.

Obejrzyj to wideo, aby zapoznać się z omówieniem procesu wdrażania.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4F1af]

## <a name="why-manage-endpoints"></a>Dlaczego warto zarządzać punktami końcowymi?

Nowoczesne przedsiębiorstwo ma niesamowitą różnorodność punktów końcowych uzyskujących dostęp do danych. Ta konfiguracja tworzy ogromną powierzchnię ataku i w rezultacie punkty końcowe mogą łatwo stać się najsłabszym linkiem w strategii zabezpieczeń Zero Trust.

Głównie z powodu konieczności, gdy świat przechodzi do zdalnego lub hybrydowego modelu pracy, użytkownicy pracują z dowolnego miejsca, z dowolnego urządzenia, bardziej niż kiedykolwiek w historii. Atakujący szybko dostosowują taktykę, aby skorzystać z tej zmiany. Wiele organizacji boryka się z ograniczonymi zasobami podczas poruszania się po tych nowych wyzwaniach biznesowych. Praktycznie z dnia na dzień firmy przyspieszyły transformację cyfrową. Mówiąc najprościej, sposób pracy ludzi uległ zmianie — nie oczekujemy już dostępu do niezliczonych zasobów firmy tylko z biura i na urządzeniach należących do firmy.

Uzyskanie wglądu w punkty końcowe uzyskujące dostęp do zasobów firmy jest pierwszym krokiem w strategii Zero Trust urządzenia. Zazwyczaj firmy aktywnie chronią komputery przed lukami w zabezpieczeniach i atakami, podczas gdy urządzenia przenośne często nie sąmonitorowane i bez ochrony. Aby upewnić się, że nie narażasz danych na ryzyko, musimy monitorować każdy punkt końcowy pod kątem zagrożeń i stosować szczegółowe mechanizmy kontroli dostępu, aby zapewnić odpowiedni poziom dostępu na podstawie zasad organizacji. Jeśli na przykład urządzenie osobiste zostało zdjęte z zabezpieczeniami systemu, możesz zablokować dostęp, aby upewnić się, że aplikacje dla przedsiębiorstw nie są narażone na znane luki w zabezpieczeniach.

W tej serii artykułów przedstawiono zalecany proces zarządzania urządzeniami uzyskującymi dostęp do zasobów. Jeśli wykonasz zalecane kroki, twoja organizacja osiągnie bardzo zaawansowaną ochronę urządzeń i zasobów, do których uzyskują dostęp.

## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Implementowanie warstw ochrony na urządzeniach i dla nich

Ochrona danych i aplikacji na urządzeniach i samych urządzeniach jest procesem wielowarstwowym. Istnieją pewne zabezpieczenia, które można uzyskać na urządzeniach niezarządzanych. Po zarejestrowaniu urządzeń w systemie zarządzania można zaimplementować bardziej zaawansowane mechanizmy kontroli. Gdy ochrona przed zagrożeniami jest wdrażana w punktach końcowych, uzyskujesz jeszcze więcej szczegółowych informacji i możliwość automatycznego korygowania niektórych ataków. Na koniec, jeśli organizacja włożyła pracę w identyfikowanie poufnych danych, stosowanie klasyfikacji i etykiet oraz konfigurowanie zasad ochrony przed utratą danych Microsoft Purview, możesz uzyskać jeszcze bardziej szczegółową ochronę danych w punktach końcowych.

Na poniższym diagramie przedstawiono bloki konstrukcyjne umożliwiające osiągnięcie Zero Trust stanu zabezpieczeń dla Microsoft 365 i innych aplikacji SaaS wprowadzonych w tym środowisku. Elementy związane z urządzeniami są ponumerowane od 1 do 7. Są to warstwy ochrony, które administratorzy urządzeń będą koordynować z innymi administratorami.

![stos wdrażania Microsoft 365 Zero Trust](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

Na tej ilustracji:

|&nbsp;|Krok|Opis|Wymagania dotyczące licencjonowania|
|---|---|---|---|
|1|Konfigurowanie zasad Zero Trust tożsamości i dostępu urządzeń do punktu początkowego|Skontaktuj się z administratorem tożsamości, aby [**zaimplementować ochronę danych zasad ochrony aplikacji (APP) na poziomie 2**](manage-devices-with-intune-app-protection.md). Te zasady nie wymagają zarządzania urządzeniami. Zasady aplikacji można skonfigurować w Intune. Administrator tożsamości konfiguruje zasady dostępu warunkowego, aby wymagać zatwierdzonych aplikacji.|E3, E5, F1, F3, F5|
|2|Rejestrowanie urządzeń do Intune|To zadanie wymaga więcej czasu i planowania do zaimplementowania. Firma Microsoft zaleca używanie Intune do rejestrowania urządzeń, ponieważ to narzędzie zapewnia optymalną integrację. Istnieje kilka opcji rejestrowania urządzeń, w zależności od platformy. Na przykład urządzenia Windows można zarejestrować przy użyciu Azure AD Join lub przy użyciu rozwiązania Autopilot. Musisz przejrzeć opcje dla każdej platformy i zdecydować, która opcja rejestracji jest najlepsza dla Twojego środowiska. Zobacz [**Krok 2. Aby uzyskać więcej informacji, zarejestruj urządzenia do Intune**](manage-devices-with-intune-enroll.md).|E3, E5, F1, F3, F5|
|3|Konfigurowanie zasad zgodności|Chcesz mieć pewność, że urządzenia uzyskujące dostęp do aplikacji i danych spełniają minimalne wymagania, na przykład urządzenia są chronione hasłem lub przypinaniem, a system operacyjny jest aktualny. Zasady zgodności to sposób definiowania wymagań, które muszą spełniać urządzenia. [**Krok 3. Konfigurowanie zasad zgodności**](manage-devices-with-intune-compliance-policies.md) ułatwia skonfigurowanie tych zasad.|E3, E5, F3, F5|
|4|Konfigurowanie zasad Enterprise (zalecane) Zero Trust tożsamości i dostępu do urządzeń|Po zarejestrowaniu urządzeń możesz współpracować z administratorem tożsamości, aby [**dostosować zasady dostępu warunkowego, aby wymagać urządzeń w dobrej kondycji i zgodnych**](manage-devices-with-intune-require-compliance.md).|E3, E5, F3, F5|
|5|Wdrażanie profilów konfiguracji|W przeciwieństwie do zasad zgodności urządzeń, które po prostu oznaczają urządzenie jako zgodne lub nie na podstawie skonfigurowanych kryteriów, profile konfiguracji faktycznie zmieniają konfigurację ustawień na urządzeniu. Zasady konfiguracji umożliwiają zabezpieczenie urządzeń przed zagrożeniami cybernetycznymi. Zobacz [**Krok 5. Wdrażanie profilów konfiguracji**](manage-devices-with-intune-configuration-profiles.md).|E3, E5, F3, F5|
|6|Monitorowanie ryzyka i zgodności urządzenia za pomocą punktów odniesienia zabezpieczeń|W tym kroku połączysz Intune z Ochrona punktu końcowego w usłudze Microsoft Defender. Dzięki tej integracji można monitorować ryzyko urządzenia jako warunek dostępu. Urządzenia, które są w stanie ryzykownym, zostaną zablokowane. Można również monitorować zgodność z punktami odniesienia zabezpieczeń. Zobacz [**Krok 6. Monitorowanie ryzyka urządzenia i zgodności z punktami odniesienia zabezpieczeń**](manage-devices-with-intune-monitor-risk.md).|E5, F5|
|7|Wdrażanie funkcji ochrony przed utratą danych (DLP, data loss prevention) za pomocą funkcji ochrony informacji|Jeśli Twoja organizacja włożyła pracę w identyfikowanie poufnych danych i etykietowanie dokumentów, możesz współpracować z administratorem ochrony informacji, aby [**chronić poufne informacje i dokumenty na urządzeniach**](manage-devices-with-intune-dlp-mip.md).|Dodatek zgodności E5, F5|

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Koordynowanie zarządzania punktami końcowymi za pomocą zasad tożsamości Zero Trust i dostępu do urządzeń

Te wskazówki są ściśle skoordynowane z zalecanymi [**zasadami Zero Trust tożsamości i dostępu do urządzeń**](../security/office-365-security/microsoft-365-policies-configurations.md). Będziesz współpracować z zespołem ds. tożsamości w celu przeprowadzenia ochrony skonfigurowanej za pomocą Intune do zasad dostępu warunkowego w Azure AD.

Oto ilustracja zalecanego zestawu zasad z objaśnieniami kroków do pracy wykonywanej w Intune/MEM oraz powiązanych zasad dostępu warunkowego, które pomogą Ci koordynować Azure AD.

[![Zero Trust zasad dostępu do tożsamości i urządzeń](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)

Na tej ilustracji:

- W kroku 1 [**zaimplementuj zasady ochrony aplikacji (APP) poziomu 2**](manage-devices-with-intune-app-protection.md) , aby skonfigurować zalecany poziom ochrony danych za pomocą zasad aplikacji. Następnie współpracujesz z zespołem ds. tożsamości, aby skonfigurować powiązaną regułę dostępu warunkowego w celu wymagania korzystania z tej ochrony.
- W krokach 2, 3 i 4 rejestrujesz urządzenia do zarządzania za pomocą Intune, definiujesz zasady zgodności urządzeń, a następnie koordynujesz z zespołem ds. tożsamości konfigurację powiązanej reguły dostępu warunkowego tak, aby zezwalała tylko na dostęp do zgodnych urządzeń.

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Rejestrowanie urządzeń a dołączanie urządzeń

Jeśli zastosujesz się do tych wskazówek, zarejestrujesz urządzenia w zarządzaniu przy użyciu Intune i dołączysz urządzenia do następujących funkcji Microsoft 365:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft Purview (w celu zapobiegania utracie danych punktu końcowego (DLP)) 

Poniższa ilustracja zawiera szczegółowe informacje o tym, jak to działa przy użyciu Intune.

![Proces rejestrowania i dołączania urządzeń](../media/devices/devices-enroll-onboard-process.png#lightbox)

Na ilustracji:

1. Rejestrowanie urządzeń do zarządzania przy użyciu Intune.
2. Użyj Intune, aby dołączyć urządzenia do usługi Defender for Endpoint.
3. Urządzenia dołączone do usługi Defender for Endpoint są również dołączane do funkcji Microsoft Purview, w tym programu Endpoint DLP.
 
Należy pamiętać, że tylko Intune zarządza urządzeniami. Dołączanie odnosi się do możliwości udostępniania informacji przez urządzenie określonej usłudze. Poniższa tabela zawiera podsumowanie różnic między rejestrowaniem urządzeń do zarządzania i dołączaniem urządzeń do określonej usługi.


|         |Zarejestrować     |Onboard  |
|---------|---------|---------|
|Opis     |  Rejestracja dotyczy zarządzania urządzeniami. Urządzenia są rejestrowane do zarządzania za pomocą Intune lub Configuration Manager.        | Dołączanie konfiguruje urządzenie do pracy z określonym zestawem możliwości w Microsoft 365. Obecnie dołączanie ma zastosowanie do Ochrona punktu końcowego w usłudze Microsoft Defender i możliwości zgodności firmy Microsoft. <br><br>Na urządzeniach Windows dołączanie obejmuje przełączanie ustawienia w Windows Defender, które umożliwia usłudze Defender nawiązywanie połączenia z usługą online i akceptowanie zasad, które mają zastosowanie do urządzenia.        |
|Zakres     | Te narzędzia do zarządzania urządzeniami zarządzają całym urządzeniem, w tym konfigurują urządzenie tak, aby spełniało określone cele, takie jak zabezpieczenia.        |Dołączanie ma wpływ tylko na usługi, które mają zastosowanie.     |
|Zalecana metoda     | Azure Active Directory dołączanie automatycznie rejestruje urządzenia w Intune.        | Intune jest preferowaną metodą dołączania urządzeń do Windows Defender dla punktu końcowego, a w konsekwencji Microsoft Purview możliwości.<br><br>Należy pamiętać, że urządzenia dołączone do Microsoft Purview możliwości przy użyciu innych metod nie są automatycznie rejestrowane w usłudze Defender for Endpoint.        |
|Inne metody     |   Inne metody rejestracji zależą od platformy urządzenia i od tego, czy jest to model BYOD, czy też jest zarządzany przez organizację.      | Inne metody dołączania urządzeń obejmują, w zalecanej kolejności:<br><li>Menedżer konfiguracji<li>Inne narzędzie do zarządzania urządzeniami przenośnymi (jeśli urządzenie jest zarządzane przez jedno)<li>Skrypt lokalny<li>Pakiet konfiguracji interfejsu VDI do dołączania nietrwałych urządzeń infrastruktury pulpitu wirtualnego (VDI)<li>Zasady grupy|
| | |     |

Należy pamiętać, że tylko Intune zarządza urządzeniami. Dołączanie odnosi się do możliwości udostępniania informacji przez urządzenie określonej funkcji usługi. Poniższa tabela zawiera podsumowanie różnic między rejestrowaniem urządzeń do zarządzania i dołączaniem urządzeń w celu określonej możliwości.

|&nbsp;|Zarejestrować|Onboard|
|---|---|---|
|Opis|Rejestracja dotyczy zarządzania urządzeniami. Urządzenia są rejestrowane do zarządzania za pomocą Intune lub Configuration Manager.|Dołączanie konfiguruje urządzenie do pracy z określonym zestawem możliwości w Microsoft 365. Obecnie dołączanie ma zastosowanie do Ochrona punktu końcowego w usłudze Microsoft Defender i możliwości zgodności firmy Microsoft. <br/><br/> Na urządzeniach Windows dołączanie obejmuje przełączanie ustawienia w Windows Defender, które umożliwia usłudze Defender nawiązywanie połączenia z usługą online i akceptowanie zasad, które mają zastosowanie do urządzenia.|
|Zakres|Te narzędzia do zarządzania urządzeniami zarządzają całym urządzeniem, w tym konfigurują urządzenie tak, aby spełniało określone cele, takie jak zabezpieczenia.|Dołączanie ma wpływ tylko na zastosowane możliwości.|
|Zalecana metoda|Azure Active Directory dołączanie automatycznie rejestruje urządzenia w Intune.|Intune jest preferowaną metodą dołączania urządzeń do Windows Defender dla punktu końcowego, a w konsekwencji Microsoft Purview możliwości. <br/><br/> Należy pamiętać, że urządzenia dołączone do Microsoft Purview możliwości przy użyciu innych metod nie są automatycznie rejestrowane w usłudze Defender for Endpoint.|
|Inne metody|Inne metody rejestracji zależą od platformy urządzenia i od tego, czy jest to model BYOD, czy też jest zarządzany przez organizację.|Inne metody dołączania urządzeń obejmują, w zalecanej kolejności: <ul><li>Menedżer konfiguracji</li><li>Inne narzędzie do zarządzania urządzeniami przenośnymi (jeśli urządzenie jest zarządzane przez jedno)</li><li>Skrypt lokalny</li><li>Pakiet konfiguracji interfejsu VDI do dołączania nietrwałych urządzeń infrastruktury pulpitu wirtualnego (VDI)</li><li>Zasady grupy</li></ul>|

## <a name="learning-for-administrators"></a>Edukacja dla administratorów

Poniższe zasoby ułatwiają administratorom poznawanie pojęć dotyczących korzystania z rozwiązania MEM i Intune.

[Uproszczenie zarządzania urządzeniami za pomocą Microsoft Endpoint Manager](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) Opis: informacje o nowoczesnym zarządzaniu i Microsoft Endpoint Manager oraz o tym, jak narzędzia do zarządzania firmami w Microsoft 365 mogą uprościć zarządzanie wszystkimi urządzeniami.

[Skonfiguruj Microsoft Intune](/learn/modules/set-up-microsoft-intune/) Description: Microsoft Intune, który jest częścią Microsoft Endpoint Manager, pomaga chronić urządzenia, aplikacje i dane używane przez osoby w organizacji, aby zapewnić produktywność. Po ukończeniu tego modułu skonfigurowano Microsoft Intune. Konfiguracja obejmuje przeglądanie obsługiwanych konfiguracji, rejestrowanie się w celu Intune, dodawanie użytkowników i grup, przypisywanie licencji do użytkowników, udzielanie uprawnień administratora i ustawianie urzędu MDM.
