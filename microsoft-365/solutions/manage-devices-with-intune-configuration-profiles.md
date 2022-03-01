---
title: Krok nr 5. Wdrażanie profilów urządzeń w aplikacji Microsoft Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
audience: ITPro
description: Wprowadzenie do profilów konfiguracji w celu wymuszania bezpiecznych ustawień na urządzeniach za pomocą usługi Intune w celu przejścia tych kontrolek zabezpieczeń do chmury.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: d44d70c50db5c086e24af575677d5d51e1b33357
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2022
ms.locfileid: "63015776"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>Krok nr 5. Wdrażanie profilów urządzeń w aplikacji Microsoft Intune

Microsoft Intune zawiera ustawienia i funkcje, które można włączać lub wyłączać na różnych urządzeniach w organizacji. Te ustawienia i funkcje zostaną dodane do "profilów konfiguracji". Możesz tworzyć profile dla różnych urządzeń i różnych platform, takich jak systemy iOS/iPadOS, administrator urządzeń z systemem Android, urządzenia z systemem Android Enterprise i Windows. Następnie zastosuj profil do urządzeń lub "przypisz" go do urządzeń za pomocą usługi Intune.

Ten artykuł zawiera wskazówki dotyczące rozpoczynania pracy z profilami konfiguracji. 


![Procedura zarządzania urządzeniami](../media/devices/intune-mdm-step-4.png#lightbox)

Profile konfiguracji zapewniają możliwość skonfigurowania ważnej ochrony i zapewnienia zgodności urządzeń, dzięki czemu mogą uzyskać dostęp do Twoich zasobów. Wcześniej tego typu zmiany konfiguracji były konfigurowane przy użyciu zasady grupy w programie Usługi domenowe w usłudze Active Directory. Nowoczesna strategia zabezpieczeń obejmuje przenoszenie kontrolek zabezpieczeń do chmury, gdzie wymuszanie tych kontroli nie zależy od zasobów lokalnych i dostępu. Profile konfiguracji usługi Intune są sposobem na przejście tych kontrolek zabezpieczeń do chmury. 

Aby uzyskać informacje na temat rodzaju profilów konfiguracji, które można utworzyć, zobacz Stosowanie funkcji i ustawień na urządzeniach przy użyciu profilów urządzeń w [aplikacji Microsoft Intune](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>Wdrażanie Windows podstawowych zabezpieczeń w usłudze Intune

Na początek zalecamy wyrównanie konfiguracji urządzeń do planu bazowego zabezpieczeń firmy Microsoft w ramach usługi Microsoft Endpoint Manager. Zaletą tego rozwiązania jest to, że firma Microsoft może polegać na tym, że w przypadku wydania Windows 10 i 11 funkcji bazowych jest aktualnych. 

Aby wdrożyć podstawowe Windows zabezpieczeń w usłudze Intune dostępne dla Windows 10 i Windows 11. Aby [dowiedzieć się więcej o dostępnych](/mem/intune/protect/security-baselines) planach bazowych, Windows w usłudze Intune, zobacz Używanie planu bazowego zabezpieczeń do konfigurowania urządzeń przenośnych w usłudze Intune.

Obecnie wystarczy wdrożyć najbardziej odpowiedni plan bazowy zabezpieczeń MDM. Zobacz [Zarządzanie profilami planu bazowego zabezpieczeń Microsoft Intune ](/mem/intune/protect/security-baselines-configure)aby utworzyć profil i wybrać wersję podstawową.

Później, po skonfigurowaniu programu Microsoft Defender dla punktu końcowego i połączeniu usługi Intune, wdeksuj usługę Defender dla punktów bazowych punktów końcowych. Ten temat dotyczy następnego artykułu z tej serii: [Krok 6. Monitorowanie ryzyka urządzenia i zgodności z planami bazowymi zabezpieczeń](manage-devices-with-intune-monitor-risk.md).

Ważne jest, aby zrozumieć, że te linie bazowe zabezpieczeń nie są zgodne ze standardem CIS ani NIST, ale dokładnie odzwierciedlają ich rekomendacje. Aby uzyskać więcej informacji, zobacz [Czy plan bazowy zabezpieczeń usługi Intune jest zgodny z usługą CIS lub NIST](/mem/intune/protect/security-baselines)?

## <a name="customize-configuration-profiles-for-your-organization"></a>Dostosowywanie profilów konfiguracji dla organizacji

Oprócz wdrażania wstępnie skonfigurowanych linii bazowych wiele organizacji klasy przedsiębiorstw implementuje profile konfiguracji w celu bardziej szczegółowej kontroli. Ta konfiguracja pozwala zmniejszyć zależność od obiektów zasady grupy w lokalnym środowisku usługi Active Directory i przenieść kontrolki zabezpieczeń do chmury. 

Wiele ustawień, które można skonfigurować przy użyciu profilów konfiguracji, można pogrupować w cztery kategorie, jak pokazano poniżej.

![Kategorie profilów urządzeń w usłudze Intune](../media/devices/intune-device-profile-categories.png#lightbox)

W poniższej tabeli opisano ilustrację.


|Kategoria |Opis |Przykłady  |
|---------|---------|---------|
|Funkcje urządzenia     | Steruje funkcjami na urządzeniu. Ta kategoria dotyczy tylko urządzeń z systemami iOS/iPadOS i macOS.        | Airprint, powiadomienia, wiadomości ekranu blokady        |
|Ograniczenia urządzenia     | Steruje zabezpieczeniami, sprzętem, udostępnianiem danych i nie tylko ustawieniami na urządzeniach        | Wymaganie numeru PIN, szyfrowania danych        |
|Konfiguracja programu Access     |  Konfiguruje urządzenie w celu uzyskiwania dostępu do zasobów organizacji.        | Profile poczty e-mail, profile sieci VPN, Wi-Fi ustawień poczty e-mail, certyfikaty        |
|Niestandardowe     | Konfigurowanie konfiguracji niestandardowej lub wykonywanie niestandardowych akcji konfiguracji       | Ustawianie ustawień OEM, wykonywanie skryptów programu PowerShell        |
|    |         |         |

Podczas dostosowywania profilów konfiguracji dla organizacji używaj następujących wskazówek:
- Uprość strategię zarządzania zabezpieczeniami, zachowując małą ogólną liczbę zasad.
- Pogrupuj ustawienia według kategorii wymienionych powyżej lub kategorii, które są sensowne dla Twojej organizacji.
- Podczas przenoszenia kontrolek zabezpieczeń z obiektu zasad zasady grupy Objects (GPO) do profilów konfiguracji usługi Intune należy rozważyć, czy ustawienia skonfigurowane przez każdy obiekt zasad grupy są nadal istotne i potrzebne do uwzględnienia ogólnej strategii zabezpieczeń w chmurze. Dostęp warunkowy i wiele zasad, które można skonfigurować we wszystkich usługach w chmurze, w tym w usłudze Intune, zapewniają bardziej zaawansowaną ochronę niż można skonfigurować w środowisku lokalnym, w którym pierwotnie zaprojektowano niestandardowe urządzenia GPOs.
- Użyj zasady grupy Analytics, aby porównać i zamapować bieżące ustawienia zasad grupy na funkcje w Microsoft Endpoint Manager. Zobacz [Analizowanie lokalnych obiektów zasad grupy przy użyciu](/mem/intune/configuration/group-policy-analytics) analizy zasady grupy w programie Microsoft Endpoint Manager.
- Podczas korzystania z niestandardowych profilów konfiguracji pamiętaj o skorzystaniu z wskazówek tutaj: Tworzenie profilu za pomocą ustawień niestandardowych [w usłudze Intune](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>Dodatkowe materiały

Jeśli nie masz pewności, od czego zacząć od profilów urządzeń, pomocne mogą być poniższe informacje:

- [Scenariusze z przewodnikiem](/mem/intune/fundamentals/guided-scenarios-overview) 
- [Linie bazowe zabezpieczeń](/mem/intune/protect/security-baselines)

Jeśli Twoje środowisko zawiera własne urządzenia gpOs, dobrym rozwiązaniem jest przejście do chmury przy następujących funkcjach:

- [zasady grupy analizy](/mem/intune/configuration/group-policy-analytics)
- [Szablony administracyjne (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [Ustawienia usługi](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>Następne kroki
Przejdź do [kroku 6. Monitorowanie ryzyka urządzenia i zgodności z planami bazowymi zabezpieczeń](manage-devices-with-intune-monitor-risk.md).
