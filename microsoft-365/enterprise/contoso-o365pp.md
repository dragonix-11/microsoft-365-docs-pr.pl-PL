---
title: Aplikacje Microsoft 365 dla przedsiębiorstw dla firmy Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Dowiedz się, jak firma Contoso Microsoft Endpoint Configuration Manager do wdrażania Aplikacje Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: 6442deb0c6b7dce83a997bab28aa1c9cc85e8564
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983439"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Aplikacje Microsoft 365 dla przedsiębiorstw dla firmy Contoso

Firma Contoso uaktualniła komputery do Windows 10 Enterprise i Aplikacje Microsoft 365 dla przedsiębiorstw, aby umożliwić efektywnszą współpracę, lepsze zabezpieczenia i bardziej nowoczesne środowisko pulpitu. Po ocenie infrastruktury i potrzeb biznesowych firma Contoso zidentyfikowała następujące kluczowe wymagania dotyczące wdrożenia:

- Wszystkie komputery powinny być uruchamiane Aplikacje Microsoft 365 dla przedsiębiorstw.
- Wdrożenie powinno używać istniejących narzędzi do zarządzania i infrastruktury, jeśli to możliwe.
- Wdrażanie musi obsługiwać wiele języków i istniejących architektur na urządzeniach użytkowników.
- Komputery powinny być zawsze aktualne i bezpieczne, przy minimalnych kosztach administracyjnych i minimalnym wpływie na użytkowników.

## <a name="deployment-tools"></a>Narzędzia wdrażania

W zależności od wymagań firma Contoso wybrała opcję wdrożenia usługi Windows 10 Enterprise i Aplikacje Microsoft 365 dla przedsiębiorstw za pośrednictwem Menedżer konfiguracji (Bieżąca gałąź). Menedżer konfiguracji dla dużych środowisk i zapewnia pełną kontrolę nad instalacją, aktualizacjami i ustawieniami. Zawiera również wbudowane funkcje, które ułatwiają wdrażanie i zarządzanie nimi oraz zarządzanie nimi Office, w tym:

- Pamięć podręczna równorzędna, która może pomóc w ograniczaniu pojemności sieci podczas wdrażania na urządzeniach w lokalizacjach zdalnych.
- Pulpit Office zarządzanie klientami, który ułatwia wdrażanie i Office monitorowanie aktualizacji oraz zapewnia administratorom dostęp do najnowszych funkcji wdrażania i zarządzania.
- Inteligentne wdrażanie pakietu językowego, w tym automatyczne wdrażanie tego samego języka co system operacyjny.
- W pełni obsługiwana i łatwa w użyciu metoda usuwania istniejących wersji pakietu Office z klienta podczas wdrażania.

Oprócz pakietu Menedżer konfiguracji firma Contoso użyła zestawu [narzędzi Readiness Toolkit dla dodatków Office i VBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps), bezpłatnego narzędzia firmy Microsoft do oceny problemów ze zgodnością z ich makrami Office i dodatkami.

## <a name="managing-deployment-and-updates"></a>Zarządzanie wdrożeniem i aktualizacjami

Aplikacje Microsoft 365 dla przedsiębiorstw ma nowy model wersji: Office jako usługę. Model usługi ułatwia pozostawanie na bieżąco z nowymi funkcjami. Często jednak działy IT muszą zmieniać sposób wdrażania i testowania nowych wersji. Aby zminimalizować problemy ze zgodnością i zapewnić, że ich komputery będą aktualne, firma Contoso Windows i Office w dwóch etapach:

- Po pierwsze wdrożono Aplikacje Microsoft 365 dla przedsiębiorstw w niewielkim zestawie urządzeń reprezentatywnych w całej organizacji. Ta grupa pilotażowa została użyta do przetestowania aplikacji, dodatków i sprzętu z Aplikacje Microsoft 365 dla przedsiębiorstw.
- Cztery miesiące później, po rozwiązaniu wszystkich krytycznych problemów z aplikacjami, dodatki i sprzętem w grupie pilotażowej, firma Contoso wdrożyła usługę Aplikacje Microsoft 365 dla przedsiębiorstw na pozostałych urządzeniach w organizacji (w grupie szerokiej).

Zamiast zarządzać aktualizacjami do Office za pomocą Menedżer konfiguracji, firma Contoso włączyła automatyczne aktualizacje z chmury. Aktualizacje oparte na chmurze ograniczają obciążenie administracyjne, a jednocześnie zapewniają, że urządzenia są zawsze aktualne.

Firma Contoso użyła tego samego dwuetapowego podejścia do aktualizacji funkcji, co używanego do wdrażania programu Office: Urządzenia w grupie pilotażowej otrzymały aktualizacje funkcji cztery miesiące wcześniej niż urządzenia w pozostałej części organizacji (w grupie szerokiej). Aby włączyć tę funkcję dla Office, contoso użył dwóch zalecanych [kanałów aktualizacji](/DeployOffice/overview-update-channels):

- Semi-Annual Enterprise kanału (wersja zapoznawcza) dla aktualizacji dla grupy pilotażowej
- Semi-Annual Enterprise kanał na aktualizacje dla grupy szerokiej grupy

Ponieważ kanał Semi-Annual Enterprise (wersja zapoznawcza) wydaje wersję programu Aplikacje Microsoft 365 dla przedsiębiorstw o cztery miesiące wcześniej niż kanał Semi-Annual Enterprise, firma Contoso ma czas na weryfikację aktualizacji bez konieczności zarządzania nimi.

## <a name="deployment-process"></a>Proces wdrażania

Aby ukończyć wdrażanie pakietu Office, firma Contoso wdrożyła następujący proces, który zawiera zalecenia dotyczące najlepszych rozwiązań od firmy Microsoft:

1. Przed wdrożeniem firma Contoso użyła zestawu narzędzi Readiness Toolkit dla dodatków Office i VBA do przetestowania ich aplikacji i dodatków Office w celu oceny ich zgodności z Aplikacje Microsoft 365 dla przedsiębiorstw.
1. W Menedżer konfiguracji włączono pamięć podręczną komunikacji równorzędnej na urządzeniach klienckich, co pomaga przy ograniczonej pojemności sieci podczas wdrażania na urządzeniach klienckich w lokalizacjach zdalnych. 
1. Firma Contoso zdefiniuje dwie grupy wdrażania jako kolekcje urządzeń Menedżer konfiguracji: grupę pilotażową i grupę. Grupa pilotażowa, która obejmowała niewielki zestaw urządzeń reprezentatywnych w całej organizacji, została użyta do dodatkowego testowania aplikacji, dodatków i sprzętu z systemem Windows 10 Enterprise i Aplikacje Microsoft 365 dla przedsiębiorstw.
1. Pakiety wdrożeniowe dla Office utworzono za pomocą pulpitu nawigacyjnego zarządzanie Office klienta i kreatora Instalatora Office 365, które są częścią konsoli Menedżer konfiguracji. Powstały dwa pakiety Aplikacje Microsoft 365 dla przedsiębiorstw: jeden dla grupy pilotażowej w kanale Semi-Annual Enterprise (wersja Zapoznawcza) i jeden dla szerokiej grupy na Semi-Annual Enterprise Channel.
2. Każdy Office pakietów językowych: angielski, francuski i niemiecki. Jeśli urządzenie wymagało języka, który nie został dołączony do pakietu pakietu Office, ten pakiet językowy został automatycznie pobrany z aplikacji pakietu Office Content Delivery Network (CDN).
3. Używali funkcji wbudowanej w pakiecie Office, aby automatycznie usuwać wszystkie istniejące wersje MSI programu Office przed zainstalowaniem Aplikacje Microsoft 365 dla przedsiębiorstw.
4. W Menedżer konfiguracji wdrożono pakiety Windows i Office w punktach dystrybucji w ich sieci. Następnie uruchomili oni Menedżer konfiguracji zadań wdrażania w celu wdrożenia pakietu Aplikacje Microsoft 365 dla przedsiębiorstw pilotażowego w grupie pilotażowej.
5. Gdy zajęli się problemami ze zgodnością w grupie pilotażowej, firma Contoso uruchomiła sekwencje zadań w celu wdrożenia pakietu Aplikacje Microsoft 365 dla przedsiębiorstw w szerokiej grupie.

Firma Contoso wybrała opcję automatycznej aktualizacji urządzeń z chmury, dlatego nie trzeba było zarządzać tym procesem w Menedżer konfiguracji. Ich urządzenia są automatycznie aktualizowane bezpośrednio z chmury w zależności od kanału aktualizacji zdefiniowanego w wdrożenie wstępne.

Oto architektura instalacji i bieżących aktualizacji Aplikacje Microsoft 365 dla przedsiębiorstw Contoso.

![Infrastruktura wdrażania firmy Contoso dla Aplikacje Microsoft 365 dla przedsiębiorstw.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Następny krok

Dowiedz się[, jak firma](contoso-mdm.md) Contoso Microsoft Intune w Microsoft 365 dla przedsiębiorstw do zarządzania swoimi urządzeniami i aplikacjami, które uruchamiają w całej organizacji.

## <a name="see-also"></a>Zobacz też

[Aplikacje usługi Microsoft 365 dla przedsiębiorstw](/deployoffice/deployment-guide-microsoft-365-apps)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)