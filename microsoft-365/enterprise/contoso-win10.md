---
title: wdrożenie Windows 10 Enterprise dla firmy Contoso
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
description: Dowiedz się, jak firma Contoso używała Microsoft Endpoint Configuration Manager do wdrażania uaktualnień w miejscu dla Windows 10 Enterprise.
ms.openlocfilehash: 082c60de614c5a125a1fd2af6ba9d187f21ca39e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095361"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>wdrożenie Windows 10 Enterprise dla firmy Contoso

Przed szerokim wdrożeniem Microsoft 365 dla przedsiębiorstw firma Contoso miała komputery i urządzenia zgodne z Windows, na których działa mieszanka Windows 7 (10%), Windows 8.1 (65%) i Windows 10 (25%). Firma Contoso chciała uaktualnić swoje komputery do Windows 10 Enterprise skorzystać z zaawansowanych zabezpieczeń i zmniejszyć obciążenie it z zautomatyzowanych wdrożeń aktualizacji. 

Po dokonaniu oceny infrastruktury i potrzeb biznesowych firma Contoso określiła następujące kluczowe wymagania dotyczące wdrożenia:

- Jak najwięcej komputerów i urządzeń powinno działać Windows 10 Enterprise
- Wdrożenie uaktualnień w miejscu korzysta z istniejącej infrastruktury Configuration Manager
- Kontrola nad tym, które wersje Windows 10 Enterprise do wdrożenia i aktualizacje są wykonywane za pośrednictwem pierścieni
- Komputery i urządzenia powinny być na bieżąco z minimalnymi kosztami administracyjnymi IT i mieć minimalny wpływ na użytkowników końcowych

Aktualna wersja jest definiowana jako obsługiwana wersja Windows 10 Enterprise spełniająca potrzeby biznesowe firmy Contoso, która może różnić się od posiadania wszystkich komputerów zgodnych z Windows z najnowszą wersją Windows 10 Enterprise.

## <a name="deployment-tools"></a>Narzędzia wdrażania

Przed uaktualnieniami Windows 10 Enterprise i w ich trakcie firma Contoso korzystała z następujących rozwiązań usługi Windows Analytics:

- Gotowość do uaktualnienia  

  Zbiera dane systemowe, aplikacje i sterowniki do analizy, a następnie identyfikuje problemy ze zgodnością, które mogą blokować uaktualnienie i sugerowane poprawki, które są znane firmie Microsoft.

- Aktualizowanie zgodności  

  Pokazuje stan urządzeń w odniesieniu do aktualizacji Windows, dzięki czemu można upewnić się, że są one na najbardziej bieżących aktualizacji, zgodnie z potrzebami.

- Kondycja urządzenia  

  Identyfikuje urządzenia, które często ulegają awarii i dlatego mogą wymagać ponownej przebudowy lub wymiany, oraz sterowniki urządzeń, które powodują awarie urządzeń, wraz z sugestiami alternatywnych wersji tych sterowników, które mogą zmniejszyć liczbę awarii. Zawiera powiadomienie o błędach konfiguracji Windows Information Protection, które wysyłają monity do użytkowników końcowych.
 
Firma Contoso ma istniejącą infrastrukturę Configuration Manager (Current Branch). Configuration Manager skalowania dla dużych środowisk i zapewnia szeroką kontrolę nad instalacją, aktualizacjami i ustawieniami. Ma również wbudowane funkcje ułatwiające i wydajniejsze wdrażanie Windows 10 Enterprise i zarządzanie nimi.

## <a name="planning-process"></a>Proces planowania

Firma Contoso wykorzystała gotowość do uaktualnienia w usłudze Windows Analytics, aby określić zestaw zainstalowanych aplikacji i ich zgodność z Windows 10 Enterprise.

## <a name="deployment-process"></a>Proces wdrażania

Aby ukończyć wdrożenie uaktualnienia w miejscu Windows 10 Enterprise, firma Contoso wdrożyła następujący proces, który obejmuje zalecenia dotyczące najlepszych rozwiązań firmy Microsoft:

1. Włączona równorzędna pamięć podręczna dla Configuration Manager.
2. Utworzono dostosowane pakiety Windows na podstawie obrazów z Centrum usługi licencjonowania zbiorowego.
3. Używane Configuration Manager do wdrażania pakietów Windows w punktach dystrybucji w sieci i wdrożonych kompilacji w trzech grupach przejściowych weryfikacji i wdrażania.
4. Przeprowadzono ocenę powodzenia dla komputerów i urządzeń w trzech pierścieniach przejściowych weryfikacji i wdrażania przy użyciu rozwiązań kondycji urządzenia i zgodności aktualizacji w usłudze Windows Analytics.
5. Na podstawie informacji Windows Analytics firma Contoso określiła wersję Windows 10 Enterprise do wdrożenia w szerokiej grupie wdrożeń.
6. Uruchomiono sekwencje zadań wdrażania Configuration Manager, aby wdrożyć wybrany pakiet Windows w szerokiej grupie wdrożeń.
7. Monitorowane komputery i urządzenia w szerokiej grupie wdrożeń przy użyciu rozwiązań kondycji urządzeń i zgodności aktualizacji w celu rozwiązania problemów.

Oto architektura wdrażania uaktualniania w miejscu i bieżących aktualizacji firmy Contoso.

![Infrastruktura wdrażania Windows 10 Enterprise firmy Contoso.](../media/contoso-win10/contoso-win10-fig1.png)

Ta infrastruktura składa się z następujących elementów:

- Configuration Manager, które:
  - Uzyskuje obrazy dla pakietów Windows 10 Enterprise z Centrum licencjonowania zbiorowego firmy Microsoft w usłudze Microsoft Network.
  - Jest centralnym punktem administracyjnym pakietów wdrożeniowych.
- Regionalne punkty dystrybucji, które zwykle znajdują się w regionalnych biurach centrów firmy Contoso.
- Windows komputery i urządzenia w różnych lokalizacjach, które odbierają i instalują pakiety wdrożeniowe na potrzeby uaktualniania w miejscu lub bieżących aktualizacji na podstawie członkostwa w grupie.

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso wykorzystuje swoją infrastrukturę Configuration Manager do [wdrażania i utrzymywania bieżących Aplikacje Microsoft 365 dla przedsiębiorstw](contoso-o365pp.md) w całej organizacji. 

## <a name="see-also"></a>Zobacz też

[System Windows10 dla firm](/windows/deployment/)

[Microsoft 365 dla przedsiębiorstw — omówienie](microsoft-365-overview.md)

[Przewodniki po laboratorium testowym](m365-enterprise-test-lab-guides.md)