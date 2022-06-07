---
title: Zarządzanie urządzeniami za pomocą usługi Intune
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
description: Zarejestruj urządzenia punktu końcowego w usłudze Microsoft Intune w ramach architektury zabezpieczeń Zero Trust, chroniąc przed oprogramowaniem wymuszającym okup podczas tworzenia ochrony pracowników zdalnych.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: 1f5b512c18c1ca6014881f93714320a6887bd9df
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923373"
---
# <a name="manage-devices-with-intune-overview"></a>Omówienie zarządzania urządzeniami za pomocą usługi Intune

Podstawowy składnik zabezpieczeń na poziomie przedsiębiorstwa obejmuje zarządzanie urządzeniami i ich ochronę. Niezależnie od tego, czy tworzysz architekturę zabezpieczeń zero zaufania, wzmacniasz ochronę środowiska przed oprogramowaniem wymuszającym okup, czy tworzysz ochronę w celu obsługi pracowników zdalnych, zarządzanie urządzeniami jest częścią strategii.
Chociaż platforma Microsoft 365 zawiera kilka narzędzi i metodologii zarządzania urządzeniami i ich ochrony, w tych wskazówkach przedstawiono zalecenia firmy Microsoft dotyczące korzystania z usługi Microsoft Intune. Są to odpowiednie wskazówki dla Ciebie, jeśli:

- Zaplanuj rejestrowanie urządzeń w usłudze Intune za pośrednictwem usługi Azure AD Join (w tym dołączenia hybrydowego do usługi Azure AD).
- Zaplanuj ręczne rejestrowanie urządzeń w usłudze Intune.
- Zezwalaj urządzeniom BYOD z planami na implementowanie ochrony aplikacji i danych i/lub rejestrowanie tych urządzeń w usłudze Intune.

Z drugiej strony, jeśli środowisko zawiera plany współzarządzania, w tym program Microsoft Endpoint Configuration Manager, zobacz [dokumentację współzarządzania](/mem/configmgr/comanage/) , aby opracować najlepszą ścieżkę dla organizacji. Jeśli środowisko zawiera plany dla komputera z systemem Windows 365 Cloud, zobacz [dokumentację systemu Windows 365 Enterprise](/windows-365/enterprise/) , aby opracować najlepszą ścieżkę dla organizacji.

Obejrzyj to wideo, aby zapoznać się z omówieniem procesu wdrażania.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Y4fC]


## <a name="why-manage-endpoints"></a>Dlaczego warto zarządzać punktami końcowymi?

Nowoczesne przedsiębiorstwo ma niesamowitą różnorodność punktów końcowych uzyskujących dostęp do danych. Ta konfiguracja tworzy ogromną powierzchnię ataku i w rezultacie punkty końcowe mogą łatwo stać się najsłabszym linkiem w strategii zabezpieczeń Zero Trust.

Głównie z powodu konieczności, gdy świat przechodzi do zdalnego lub hybrydowego modelu pracy, użytkownicy pracują z dowolnego miejsca, z dowolnego urządzenia, bardziej niż kiedykolwiek w historii. Atakujący szybko dostosowują taktykę, aby skorzystać z tej zmiany. Wiele organizacji boryka się z ograniczonymi zasobami podczas poruszania się po tych nowych wyzwaniach biznesowych. Praktycznie z dnia na dzień firmy przyspieszyły transformację cyfrową. Mówiąc najprościej, sposób pracy ludzi uległ zmianie — nie oczekujemy już dostępu do niezliczonych zasobów firmy tylko z biura i na urządzeniach należących do firmy.

Uzyskanie wglądu w punkty końcowe uzyskujące dostęp do zasobów firmy jest pierwszym krokiem w strategii urządzenia Zero Trust. Zazwyczaj firmy aktywnie chronią komputery przed lukami w zabezpieczeniach i atakami, podczas gdy urządzenia przenośne często nie sąmonitorowane i bez ochrony. Aby upewnić się, że nie narażasz danych na ryzyko, musimy monitorować każdy punkt końcowy pod kątem zagrożeń i stosować szczegółowe mechanizmy kontroli dostępu, aby zapewnić odpowiedni poziom dostępu na podstawie zasad organizacji. Jeśli na przykład urządzenie osobiste zostało zdjęte z zabezpieczeniami systemu, możesz zablokować dostęp, aby upewnić się, że aplikacje dla przedsiębiorstw nie są narażone na znane luki w zabezpieczeniach.

W tej serii artykułów przedstawiono zalecany proces zarządzania urządzeniami uzyskującymi dostęp do zasobów. Jeśli wykonasz zalecane kroki, twoja organizacja osiągnie bardzo zaawansowaną ochronę urządzeń i zasobów, do których uzyskują dostęp.

## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Implementowanie warstw ochrony na urządzeniach i dla nich

Ochrona danych i aplikacji na urządzeniach i samych urządzeniach jest procesem wielowarstwowym. Istnieją pewne zabezpieczenia, które można uzyskać na urządzeniach niezarządzanych. Po zarejestrowaniu urządzeń w systemie zarządzania można zaimplementować bardziej zaawansowane mechanizmy kontroli. Gdy ochrona przed zagrożeniami jest wdrażana w punktach końcowych, uzyskujesz jeszcze więcej szczegółowych informacji i możliwość automatycznego korygowania niektórych ataków. Na koniec, jeśli Twoja organizacja włożyła pracę w identyfikowanie poufnych danych, stosowanie klasyfikacji i etykiet oraz konfigurowanie zasad ochrony przed utratą danych w usłudze Microsoft Purview, możesz uzyskać jeszcze bardziej szczegółową ochronę danych w punktach końcowych.

Na poniższym diagramie przedstawiono bloki konstrukcyjne w celu osiągnięcia stanu zabezpieczeń zero zaufania dla platformy Microsoft 365 i innych aplikacji SaaS wprowadzonych w tym środowisku. Elementy związane z urządzeniami są ponumerowane od 1 do 7. Są to warstwy ochrony, które administratorzy urządzeń będą koordynować z innymi administratorami.

![Stos wdrażania rozwiązania Microsoft 365 Zero Trust](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

Na tej ilustracji:

|&nbsp;|Krok|Opis|Wymagania dotyczące licencjonowania|
|---|---|---|---|
|1|Konfigurowanie tożsamości zero zaufania punktu początkowego i zasad dostępu urządzeń|Skontaktuj się z administratorem tożsamości, aby [**zaimplementować ochronę danych zasad ochrony aplikacji (APP) na poziomie 2**](manage-devices-with-intune-app-protection.md). Te zasady nie wymagają zarządzania urządzeniami. Zasady aplikacji można skonfigurować w usłudze Intune. Administrator tożsamości konfiguruje zasady dostępu warunkowego, aby wymagać zatwierdzonych aplikacji.|E3, E5, F1, F3, F5|
|2|Rejestrowanie urządzeń w usłudze Intune|To zadanie wymaga więcej czasu i planowania do zaimplementowania. Firma Microsoft zaleca rejestrowanie urządzeń przy użyciu usługi Intune, ponieważ to narzędzie zapewnia optymalną integrację. Istnieje kilka opcji rejestrowania urządzeń, w zależności od platformy. Na przykład urządzenia z systemem Windows można zarejestrować przy użyciu funkcji Dołączanie do usługi Azure AD lub przy użyciu rozwiązania Autopilot. Musisz przejrzeć opcje dla każdej platformy i zdecydować, która opcja rejestracji jest najlepsza dla Twojego środowiska. Zobacz [**Krok 2. Aby uzyskać więcej informacji, zarejestruj urządzenia w usłudze Intune**](manage-devices-with-intune-enroll.md) .|E3, E5, F1, F3, F5|
|3|Konfigurowanie zasad zgodności|Chcesz mieć pewność, że urządzenia uzyskujące dostęp do aplikacji i danych spełniają minimalne wymagania, na przykład urządzenia są chronione hasłem lub przypinaniem, a system operacyjny jest aktualny. Zasady zgodności to sposób definiowania wymagań, które muszą spełniać urządzenia. [**Krok 3. Konfigurowanie zasad zgodności**](manage-devices-with-intune-compliance-policies.md) ułatwia skonfigurowanie tych zasad.|E3, E5, F3, F5|
|4|Konfigurowanie zasad dostępu do urządzeń i tożsamości zero zaufania w przedsiębiorstwie (zalecane)|Po zarejestrowaniu urządzeń możesz współpracować z administratorem tożsamości, aby [**dostosować zasady dostępu warunkowego, aby wymagać urządzeń w dobrej kondycji i zgodnych**](manage-devices-with-intune-require-compliance.md).|E3, E5, F3, F5|
|5|Wdrażanie profilów konfiguracji|W przeciwieństwie do zasad zgodności urządzeń, które po prostu oznaczają urządzenie jako zgodne lub nie na podstawie skonfigurowanych kryteriów, profile konfiguracji faktycznie zmieniają konfigurację ustawień na urządzeniu. Zasady konfiguracji umożliwiają zabezpieczenie urządzeń przed zagrożeniami cybernetycznymi. Zobacz [**Krok 5. Wdrażanie profilów konfiguracji**](manage-devices-with-intune-configuration-profiles.md).|E3, E5, F3, F5|
|6|Monitorowanie ryzyka i zgodności urządzenia za pomocą punktów odniesienia zabezpieczeń|W tym kroku połączysz usługę Intune z usługą Microsoft Defender for Endpoint. Dzięki tej integracji można monitorować ryzyko urządzenia jako warunek dostępu. Urządzenia, które są w stanie ryzykownym, zostaną zablokowane. Można również monitorować zgodność z punktami odniesienia zabezpieczeń. Zobacz [**Krok 6. Monitorowanie ryzyka urządzenia i zgodności z punktami odniesienia zabezpieczeń**](manage-devices-with-intune-monitor-risk.md).|E5, F5|
|7|Wdrażanie funkcji ochrony przed utratą danych (DLP, data loss prevention) za pomocą funkcji ochrony informacji|Jeśli Twoja organizacja włożyła pracę w identyfikowanie poufnych danych i etykietowanie dokumentów, możesz współpracować z administratorem ochrony informacji, aby [**chronić poufne informacje i dokumenty na urządzeniach**](manage-devices-with-intune-dlp-mip.md).|Dodatek zgodności E5, F5|

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Koordynowanie zarządzania punktami końcowymi przy użyciu zasad zero zaufania i dostępu do urządzeń

Te wskazówki są ściśle skoordynowane z zalecanymi [**zasadami dotyczącymi tożsamości zero zaufania i dostępu do urządzeń**](../security/office-365-security/microsoft-365-policies-configurations.md). Będziesz współpracować z zespołem ds. tożsamości, aby zapewnić ochronę skonfigurowaną za pomocą usługi Intune w zasadach dostępu warunkowego w usłudze Azure AD.

Oto ilustracja zalecanego zestawu zasad z objaśnieniami kroków dotyczącymi pracy wykonywanej w usłudze Intune/MEM oraz powiązanych zasad dostępu warunkowego, które ułatwiają koordynowanie w usłudze Azure AD.

[![Zasady zerowej tożsamości zaufania i dostępu do urządzeń](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)

Na tej ilustracji:

- W kroku 1 [**zaimplementuj zasady ochrony aplikacji (APP) poziomu 2**](manage-devices-with-intune-app-protection.md) , aby skonfigurować zalecany poziom ochrony danych za pomocą zasad aplikacji. Następnie współpracujesz z zespołem ds. tożsamości, aby skonfigurować powiązaną regułę dostępu warunkowego w celu wymagania korzystania z tej ochrony.
- W krokach 2, 3 i 4 rejestrujesz urządzenia do zarządzania za pomocą usługi Intune, definiujesz zasady zgodności urządzeń, a następnie koordynujesz je z zespołem ds. tożsamości, aby skonfigurować powiązaną regułę dostępu warunkowego tak, aby zezwalała tylko na dostęp do zgodnych urządzeń.

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Rejestrowanie urządzeń a dołączanie urządzeń

Jeśli zastosujesz się do tych wskazówek, zarejestrujesz urządzenia do zarządzania przy użyciu usługi Intune i dołączysz urządzenia do następujących możliwości platformy Microsoft 365:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft Purview (w celu zapobiegania utracie danych punktu końcowego (DLP)) 

Na poniższej ilustracji przedstawiono sposób działania tej usługi przy użyciu usługi Intune.

![Proces rejestrowania i dołączania urządzeń](../media/devices/devices-enroll-onboard-process.png#lightbox)

Na ilustracji:

1. Rejestrowanie urządzeń do zarządzania za pomocą usługi Intune.
2. Użyj usługi Intune, aby dołączyć urządzenia do usługi Defender for Endpoint.
3. Urządzenia dołączone do usługi Defender for Endpoint są również dołączane do funkcji usługi Microsoft Purview, w tym programu Endpoint DLP.
 
Należy pamiętać, że tylko usługa Intune zarządza urządzeniami. Dołączanie odnosi się do możliwości udostępniania informacji przez urządzenie określonej usłudze. Poniższa tabela zawiera podsumowanie różnic między rejestrowaniem urządzeń do zarządzania i dołączaniem urządzeń do określonej usługi.


| &nbsp; |Zarejestrować     |Onboard  |
|---------|---------|---------|
|Opis     |  Rejestracja dotyczy zarządzania urządzeniami. Urządzenia są rejestrowane do zarządzania za pomocą usługi Intune lub programu Configuration Manager.        | Dołączanie konfiguruje urządzenie do pracy z określonym zestawem możliwości na platformie Microsoft 365. Obecnie dołączanie ma zastosowanie do funkcji zgodności usługi Microsoft Defender for Endpoint i Microsoft. <br><br>Na urządzeniach z systemem Windows dołączanie obejmuje przełączanie ustawienia w usłudze Windows Defender, które umożliwia usłudze Defender łączenie się z usługą online i akceptowanie zasad, które mają zastosowanie do urządzenia.        |
|Zakres     | Te narzędzia do zarządzania urządzeniami zarządzają całym urządzeniem, w tym konfigurują urządzenie tak, aby spełniało określone cele, takie jak zabezpieczenia.        |Dołączanie ma wpływ tylko na usługi, które mają zastosowanie.     |
|Zalecana metoda     | Dołączanie do usługi Azure Active Directory automatycznie rejestruje urządzenia w usłudze Intune.        | Usługa Intune jest preferowaną metodą dołączania urządzeń do usługi Windows Defender for Endpoint, a w związku z tym możliwości usługi Microsoft Purview.<br><br>Należy pamiętać, że urządzenia dołączone do funkcji usługi Microsoft Purview przy użyciu innych metod nie są automatycznie rejestrowane w usłudze Defender for Endpoint.        |
|Inne metody     |   Inne metody rejestracji zależą od platformy urządzenia i od tego, czy jest to model BYOD, czy też jest zarządzany przez organizację.      | Inne metody dołączania urządzeń obejmują, w zalecanej kolejności:<br><li>Menedżer konfiguracji<li>Inne narzędzie do zarządzania urządzeniami przenośnymi (jeśli urządzenie jest zarządzane przez jedno)<li>Skrypt lokalny<li>Pakiet konfiguracji interfejsu VDI do dołączania nietrwałych urządzeń infrastruktury pulpitu wirtualnego (VDI)<li>Zasady grupy|
| | |     |


## <a name="learning-for-administrators"></a>Nauka dla administratorów

Poniższe zasoby ułatwiają administratorom poznawanie pojęć dotyczących korzystania z usługi MEM i usługi Intune.

[Upraszczanie zarządzania urządzeniami za pomocą programu Microsoft Endpoint Manager](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) Opis: Dowiedz się więcej o nowoczesnym zarządzaniu i programie Microsoft Endpoint Manager oraz o tym, jak narzędzia do zarządzania biznesowego na platformie Microsoft 365 mogą uprościć zarządzanie wszystkimi urządzeniami.

[Konfigurowanie usługi Microsoft Intune](/learn/modules/set-up-microsoft-intune/) Opis: Usługa Microsoft Intune, która jest częścią programu Microsoft Endpoint Manager, pomaga chronić urządzenia, aplikacje i dane używane przez osoby w organizacji w celu zapewnienia produktywności. Po ukończeniu tego modułu skonfigurowano usługę Microsoft Intune. Konfiguracja obejmuje przeglądanie obsługiwanych konfiguracji, rejestrowanie się w usłudze Intune, dodawanie użytkowników i grup, przypisywanie licencji do użytkowników, udzielanie uprawnień administratora i ustawianie urzędu MDM.
