---
title: Krok nr 5. Wdrażanie profilów urządzeń w Microsoft Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
audience: ITPro
description: Wprowadzenie z profilami konfiguracji w celu wymuszania bezpiecznych ustawień na urządzeniach przy użyciu Intune w celu przeniesienia tych mechanizmów kontroli zabezpieczeń do chmury.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: fe137e626d5199f1709504d025411586965ae9fd
ms.sourcegitcommit: 6fefc15dd78139316597083b702286097d45d4dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737424"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>Krok nr 5. Wdrażanie profilów urządzeń w Microsoft Intune

Microsoft Intune zawiera ustawienia i funkcje, które można włączyć lub wyłączyć na różnych urządzeniach w organizacji. Te ustawienia i funkcje są dodawane do "profilów konfiguracji". Profile można tworzyć dla różnych urządzeń i różnych platform, w tym systemów iOS/iPadOS, administratora urządzeń z systemem Android, Enterprise systemu Android i Windows. Następnie użyj Intune, aby zastosować lub "przypisać" profil do urządzeń.

Ten artykuł zawiera wskazówki dotyczące rozpoczynania pracy z profilami konfiguracji. 


![Kroki zarządzania urządzeniami](../media/devices/intune-mdm-step-4.png#lightbox)

Profile konfiguracji umożliwiają konfigurowanie ważnej ochrony i zapewnianie zgodności urządzeń w celu uzyskania dostępu do zasobów. Wcześniej tego rodzaju zmiany konfiguracji były konfigurowane przy użyciu ustawień zasady grupy w Active Directory Domain Services. Nowoczesna strategia zabezpieczeń obejmuje przenoszenie mechanizmów kontroli zabezpieczeń do chmury, w której wymuszanie tych mechanizmów kontroli nie jest zależne od zasobów lokalnych i dostępu. Intune profile konfiguracji to sposób na przeniesienie tych mechanizmów kontroli zabezpieczeń do chmury. 

Aby zapoznać się z rodzajem profilów konfiguracji, które można utworzyć, zobacz [Stosowanie funkcji i ustawień na urządzeniach przy użyciu profilów urządzeń w Microsoft Intune](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>Wdrażanie Windows punktów odniesienia zabezpieczeń dla Intune

Jeśli chcesz dostosować konfiguracje urządzeń do punktów odniesienia zabezpieczeń firmy Microsoft, zalecamy użycie punktów odniesienia zabezpieczeń w ramach Microsoft Endpoint Manager. Zaletą tego podejścia jest to, że możesz polegać na firmie Microsoft, aby zapewnić aktualność punktów odniesienia w miarę Windows 10 i wydaniu 11 funkcji. 

Aby wdrożyć Windows punkty odniesienia zabezpieczeń dla Intune, dostępne dla Windows 10 i Windows 11. Zobacz [Konfigurowanie urządzeń Windows w Intune przy użyciu punktów odniesienia zabezpieczeń](/mem/intune/protect/security-baselines), aby dowiedzieć się więcej o dostępnych punktach odniesienia.

Na razie wystarczy wdrożyć najbardziej odpowiedni punkt odniesienia zabezpieczeń mdm. Zobacz [Zarządzanie profilami punktów odniesienia zabezpieczeń w Microsoft Intune](/mem/intune/protect/security-baselines-configure), aby utworzyć profil i wybrać wersję punktu odniesienia.

Później, po skonfigurowaniu Ochrona punktu końcowego w usłudze Microsoft Defender i nawiązaniu połączenia z Intune, wdróż punkty odniesienia usługi Defender dla punktów końcowych. Ten temat został omówiony w następnym artykule z tej serii: [Krok 6. Monitorowanie ryzyka urządzenia i zgodności z punktami odniesienia zabezpieczeń](manage-devices-with-intune-monitor-risk.md).

Ważne jest, aby zrozumieć, że te punkty odniesienia zabezpieczeń nie są zgodne ze standardem CIS lub NIST, ale ściśle odzwierciedlają ich zalecenia. Aby uzyskać więcej informacji, zobacz [Czy Intune punkty odniesienia zabezpieczeń cis lub NIST są zgodne?](https://docs.microsoft.com/mem/intune/protect/security-baselines#are-the-intune-security-baselines-cis-or-nist-compliant)

## <a name="customize-configuration-profiles-for-your-organization"></a>Dostosowywanie profilów konfiguracji dla organizacji

Oprócz wdrażania wstępnie skonfigurowanych punktów odniesienia wiele organizacji w skali przedsiębiorstwa implementuje profile konfiguracji w celu bardziej szczegółowej kontroli. Ta konfiguracja pomaga zmniejszyć zależność od obiektów zasady grupy w środowisku lokalna usługa Active Directory i przenieść mechanizmy kontroli zabezpieczeń do chmury. 

Wiele ustawień, które można skonfigurować przy użyciu profilów konfiguracji, można pogrupować na cztery kategorie, jak pokazano poniżej.

![Intune kategorii profilów urządzeń](../media/devices/intune-device-profile-categories.png#lightbox)

W poniższej tabeli opisano ilustrację.


|Kategoria |Opis |Przykłady  |
|---------|---------|---------|
|Funkcje urządzenia     | Steruje funkcjami na urządzeniu. Ta kategoria dotyczy tylko urządzeń z systemami iOS/iPadOS i macOS.        | Airprint, powiadomienia, komunikaty ekranu blokady        |
|Ograniczenia urządzenia     | Steruje zabezpieczeniami, sprzętem, udostępnianiem danych i innymi ustawieniami na urządzeniach        | Wymaganie numeru PIN i szyfrowania danych        |
|Konfiguracja dostępu     |  Konfiguruje urządzenie w celu uzyskania dostępu do zasobów organizacji        | Profile poczty e-mail, profile sieci VPN, ustawienia Wi-Fi, certyfikaty        |
|Niestandardowe     | Ustawianie konfiguracji niestandardowej lub wykonywanie niestandardowych akcji konfiguracji       | Ustawianie ustawień OEM, wykonywanie skryptów programu PowerShell        |
|    |         |         |

Podczas dostosowywania profilów konfiguracji dla organizacji skorzystaj z następujących wskazówek:
- Uprość strategię zapewniania ładu w zakresie zabezpieczeń, utrzymując ogólną liczbę zasad na małym poziomie.
- Grupuj ustawienia w kategorie wymienione powyżej lub kategorie, które mają sens dla Twojej organizacji.
- Podczas przenoszenia mechanizmów kontroli zabezpieczeń z obiektów zasady grupy (GPO) do profilów konfiguracji Intune należy rozważyć, czy ustawienia skonfigurowane przez poszczególne obiekty zasad grupy są nadal istotne i potrzebne do współtworzenia ogólnej strategii zabezpieczeń w chmurze. Dostęp warunkowy i wiele zasad, które można skonfigurować w usługach w chmurze, w tym Intune, zapewniają bardziej zaawansowaną ochronę niż można skonfigurować w środowisku lokalnym, w którym pierwotnie zaprojektowano niestandardowe obiekty zasad grupy.
- Użyj usługi zasady grupy Analytics, aby porównać i zamapować bieżące ustawienia obiektu zasad grupy na możliwości w ramach Microsoft Endpoint Manager. Zobacz [Analizowanie lokalnych obiektów zasad grupy (GPO) przy użyciu analizy zasady grupy](/mem/intune/configuration/group-policy-analytics) w Microsoft Endpoint Manager.
- Korzystając z niestandardowych profilów konfiguracji, skorzystaj ze wskazówek w tym miejscu: [Tworzenie profilu z ustawieniami niestandardowymi w Intune](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>Dodatkowe materiały

Jeśli nie masz pewności, od czego zacząć od profilów urządzeń, może to pomóc w następujących kwestiach:

- [Scenariusze z przewodnikiem](/mem/intune/fundamentals/guided-scenarios-overview) 
- [Punkty odniesienia zabezpieczeń](/mem/intune/protect/security-baselines)

Jeśli środowisko zawiera lokalne obiekty zasad grupy, następujące funkcje są dobrym przejściem do chmury:

- [analiza zasady grupy](/mem/intune/configuration/group-policy-analytics)
- [Szablony administratorów (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [wykaz Ustawienia](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>Następne kroki
Przejdź do [kroku 6. Monitorowanie ryzyka urządzenia i zgodności z punktami odniesienia zabezpieczeń](manage-devices-with-intune-monitor-risk.md).
