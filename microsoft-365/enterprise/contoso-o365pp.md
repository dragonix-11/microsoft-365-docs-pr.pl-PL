---
title: wdrożenie Aplikacje Microsoft 365 dla przedsiębiorstw dla firmy Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Dowiedz się, jak firma Contoso używa Microsoft Endpoint Configuration Manager do wdrażania Aplikacje Microsoft 365 dla przedsiębiorstw.
ms.openlocfilehash: 8b6fb639083145c728870156d848b75897483d25
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096551"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>wdrożenie Aplikacje Microsoft 365 dla przedsiębiorstw dla firmy Contoso

Firma Contoso uaktualniła swoje komputery do Windows 10 Enterprise i Aplikacje Microsoft 365 dla przedsiębiorstw, aby umożliwić skuteczniejszą współpracę, lepsze zabezpieczenia i bardziej nowoczesne środowisko pulpitu. Po dokonaniu oceny infrastruktury i potrzeb biznesowych firma Contoso określiła następujące kluczowe wymagania dotyczące wdrożenia:

- Wszystkie komputery powinny działać Aplikacje Microsoft 365 dla przedsiębiorstw.
- Wdrożenie powinno używać istniejących narzędzi do zarządzania i infrastruktury, jeśli jest to możliwe.
- Wdrożenie musi obsługiwać wiele języków i istniejących architektur na urządzeniach użytkowników.
- Komputery powinny być aktualne i bezpieczne przy minimalnych kosztach administracyjnych IT i minimalnym wpływie na użytkowników.

## <a name="deployment-tools"></a>Narzędzia wdrażania

Na podstawie wymagań firma Contoso zdecydowała się wdrożyć Windows 10 Enterprise i Aplikacje Microsoft 365 dla przedsiębiorstw za pośrednictwem Configuration Manager (Current Branch). Configuration Manager skalowania dla dużych środowisk i zapewnia szeroką kontrolę nad instalacją, aktualizacjami i ustawieniami. Ma również wbudowane funkcje ułatwiające i wydajniejsze wdrażanie Office oraz zarządzanie nimi, w tym:

- Równorzędna pamięć podręczna, która może pomóc w ograniczeniu pojemności sieci podczas wdrażania na urządzeniach w lokalizacjach zdalnych.
- Pulpit nawigacyjny zarządzania klientami Office, który ułatwia wdrażanie Office i monitorowanie aktualizacji oraz zapewnia administratorom dostęp do najnowszych funkcji wdrażania i zarządzania.
- Inteligentne wdrażanie pakietu językowego, w tym automatyczne wdrażanie tego samego języka co system operacyjny.
- W pełni obsługiwana i łatwa w użyciu metoda usuwania istniejących wersji Office z klienta podczas wdrażania.

Oprócz Configuration Manager firma Contoso użyła [zestawu narzędzi Readiness Toolkit dla dodatków Office i VBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps), bezpłatnego narzędzia firmy Microsoft, aby ocenić problemy ze zgodnością z makrami i dodatkami Office.

## <a name="managing-deployment-and-updates"></a>Zarządzanie wdrażaniem i aktualizacjami

Aplikacje Microsoft 365 dla przedsiębiorstw ma nowy model wydania: Office jako usługa. Model usługi ułatwia aktualizowanie nowych funkcji. Jednak często wymaga to od działów IT zmiany sposobu wdrażania i testowania nowych wersji. Aby zminimalizować problemy ze zgodnością i zapewnić aktualność komputerów, firma Contoso wdrożyła Windows i Office w dwóch etapach:

- Najpierw wdrożyli Aplikacje Microsoft 365 dla przedsiębiorstw na małym zestawie reprezentatywnych urządzeń w całej organizacji. Ta grupa pilotażowa została użyta do testowania aplikacji, dodatków i sprzętu przy użyciu Aplikacje Microsoft 365 dla przedsiębiorstw.
- Cztery miesiące później, po rozwiązaniu wszystkich krytycznych problemów z aplikacjami, dodatkami i sprzętem w grupie pilotażowej, firma Contoso wdrożyła Aplikacje Microsoft 365 dla przedsiębiorstw na pozostałych urządzeniach w organizacji (szerokiej grupie).

Zamiast zarządzać aktualizacjami Office przy użyciu Configuration Manager firma Contoso włączyła automatyczne aktualizacje z chmury. Aktualizacje oparte na chmurze zmniejszają obciążenie administracyjne przy jednoczesnym zapewnieniu, że urządzenia będą na bieżąco.

Firma Contoso zastosowała to samo dwuetapowe podejście do aktualizacji funkcji, które były używane do wdrażania Office: urządzenia w grupie pilotażowej otrzymały aktualizacje funkcji cztery miesiące wcześniej niż urządzenia w pozostałej części organizacji (szeroka grupa). Aby włączyć tę funkcję dla Office, firma Contoso użyła dwóch zalecanych [kanałów aktualizacji](/DeployOffice/overview-update-channels):

- kanał Semi-Annual Enterprise (wersja zapoznawcza) dla aktualizacji grupy pilotażowej
- Semi-Annual Enterprise kanału aktualizacji dla szerokiej grupy

Ponieważ kanał Semi-Annual Enterprise (wersja zapoznawcza) wydaje wersję Aplikacje Microsoft 365 dla przedsiębiorstw cztery miesiące wcześniej niż kanał Semi-Annual Enterprise, firma Contoso ma czas na zweryfikowanie aktualizacji bez konieczności zarządzania nimi.

## <a name="deployment-process"></a>Proces wdrażania

Aby ukończyć wdrażanie Office, firma Contoso wdrożyła następujący proces, który obejmuje zalecenia dotyczące najlepszych rozwiązań firmy Microsoft:

1. Przed wdrożeniem firma Contoso użyła zestawu narzędzi Readiness Toolkit for Office Add-in i VBA do testowania aplikacji i Office dodatków w celu oceny ich zgodności z Aplikacje Microsoft 365 dla przedsiębiorstw.
1. W Configuration Manager włączyli równorzędne buforowanie na swoich urządzeniach klienckich, co pomaga w ograniczeniu pojemności sieci podczas wdrażania na urządzeniach klienckich w lokalizacjach zdalnych. 
1. Firma Contoso zdefiniowała dwie grupy wdrożeń jako kolekcje urządzeń w Configuration Manager: grupę pilotażową i szeroką grupę. Grupa pilotażowa, która zawierała niewielki zestaw reprezentatywnych urządzeń w całej organizacji, została użyta do dodatkowego testowania aplikacji, dodatków i sprzętu z Windows 10 Enterprise i Aplikacje Microsoft 365 dla przedsiębiorstw.
1. Pakiety wdrożeniowe dla Office zostały utworzone przy użyciu pulpitu nawigacyjnego zarządzania klientami Office i kreatora instalatora Office 365, które są częścią konsoli Configuration Manager. Zbudowali dwa pakiety Aplikacje Microsoft 365 dla przedsiębiorstw, jeden dla grupy pilotażowej na kanale Semi-Annual Enterprise (wersja zapoznawcza) i jeden dla szerokiej grupy na kanale Semi-Annual Enterprise.
2. Każdy pakiet Office zawiera pakiety języka angielskiego, francuskiego i niemieckiego. Jeśli urządzenie wymaga języka, który nie został uwzględniony w pakiecie Office, ten pakiet językowy został automatycznie pobrany z Office Content Delivery Network (CDN).
3. Użyli wbudowanej funkcji w pakiecie Office, aby automatycznie usunąć wszystkie istniejące wersje msi Office przed zainstalowaniem Aplikacje Microsoft 365 dla przedsiębiorstw.
4. W Configuration Manager wdrożyli pakiety Windows i Office w punktach dystrybucji w sieci. Następnie uruchomili sekwencje zadań wdrażania Configuration Manager, aby wdrożyć pakiet Aplikacje Microsoft 365 dla przedsiębiorstw pilotażowy w grupie pilotażowej.
5. Po rozwiązaniu problemów ze zgodnością z grupą pilotażową firma Contoso uruchomiła sekwencje zadań, aby wdrożyć pakiet Aplikacje Microsoft 365 dla przedsiębiorstw w szerokiej grupie.

Ponieważ firma Contoso zdecydowała się automatycznie aktualizować urządzenia z chmury, nie było potrzeby zarządzania procesem w Configuration Manager. Ich urządzenia są automatycznie aktualizowane bezpośrednio z poziomu opartego na chmurze kanału aktualizacji, który został zdefiniowany we wstępnym wdrożeniu.

Oto architektura wdrażania Aplikacje Microsoft 365 dla przedsiębiorstw firmy Contoso i bieżące aktualizacje.

![Infrastruktura wdrażania firmy Contoso dla Aplikacje Microsoft 365 dla przedsiębiorstw.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso [używa Microsoft Intune](contoso-mdm.md) w Microsoft 365 dla przedsiębiorstw do zarządzania swoimi urządzeniami i aplikacjami, które są uruchamiane w całej organizacji.

## <a name="see-also"></a>Zobacz też

[Aplikacje usługi Microsoft 365 dla przedsiębiorstw](/deployoffice/deployment-guide-microsoft-365-apps)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Przewodniki po laboratorium testowym](m365-enterprise-test-lab-guides.md)