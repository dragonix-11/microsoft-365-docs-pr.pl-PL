---
title: Windows 10 Enterprise dla firmy Contoso
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
description: Dowiedz się, jak firma Contoso Microsoft Endpoint Configuration Manager do wdrażania uaktualnień w miejscu dla Windows 10 Enterprise.
ms.openlocfilehash: 7fe6efd176e156b75337ba79db6c1db839b0ed03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988373"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>Windows 10 Enterprise dla firmy Contoso

Przed rozpoczęciem szerokiego uruchomienia usługi Microsoft 365 dla przedsiębiorstw firma Contoso miała komputery i urządzenia zgodne ze standardem Windows, na których pracuje mieszanina komputerów i urządzeń o pracuje z mieszaniną produktów Windows 7 (10%), Windows 8.1 (65%) i Windows 10 (25%). Firma Contoso chciała uaktualnić swoje komputery Windows 10 Enterprise korzystać z zaawansowanych zabezpieczeń i obniżyć koszty systemu IT związane z automatycznymi wdrożeniami aktualizacji. 

Po ocenie infrastruktury i potrzeb biznesowych firma Contoso zidentyfikuje następujące kluczowe wymagania dotyczące wdrożenia:

- Na wszystkich komputerach i urządzeniach powinno być uruchomionych Windows 10 Enterprise
- Uaktualnienie w miejscu na miejscu wykorzystuje istniejącą infrastrukturę Menedżer konfiguracji w miejscu
- Kontrola nad tym, które wersje Windows 10 Enterprise wdrażać i aktualizacje są wykonywane za pomocą pierścienia
- Komputery i urządzenia powinny być na bieżąco z minimalnymi kosztami administracyjnymi i z minimalnym skutkiem dla użytkowników końcowych

Ten typ aktualizacji to obsługiwana wersja programu Windows 10 Enterprise spełniająca potrzeby biznesowe firmy Contoso. Może Windows się ona różnić od wersji zgodnej z najnowszą wersją pakietu Windows 10 Enterprise.

## <a name="deployment-tools"></a>Narzędzia wdrażania

Przed uaktualnieniem oprogramowania i podczas jego uaktualniania w miejscu firma Contoso Windows 10 Enterprise następujących rozwiązań do analizy Windows w miejscu:

- Upgrade Readiness  

  Zbiera dane systemu, aplikacji i sterowników do analizy, a następnie identyfikuje problemy ze zgodnością, które mogą zablokować uaktualnienie, oraz sugerowane rozwiązania znane firmie Microsoft.

- Aktualizowanie zgodności  

  Przedstawia stan urządzeń w odniesieniu do aktualnych Windows, dzięki czemu można upewnić się, że są one zainstalowane w najbardziej aktualnych aktualizacjach.

- Kondycja urządzenia  

  Określa urządzenia, które często ulegają awarii, przez co może być konieczne ich odbudowane lub zastąpienie, a także sterowniki urządzeń powodujące awarie urządzeń, z sugestiami wersji alternatywnych tych sterowników, które mogą zmniejszyć liczbę awarii. Powiadomienia o błędnych Windows informacji, które wysyłają monity do użytkowników końcowych w celu powiadomienia o błędnych konfiguracjach usługi Information Protection.
 
Firma Contoso ma istniejącą Menedżer konfiguracji (Bieżąca gałąź). Menedżer konfiguracji dla dużych środowisk i zapewnia pełną kontrolę nad instalacją, aktualizacjami i ustawieniami. Zawiera również wbudowane funkcje, które ułatwiają wdrażanie i zarządzanie nimi oraz zarządzanie nimi Windows 10 Enterprise.

## <a name="planning-process"></a>Proces planowania

Firma Contoso użyła narzędzia Upgrade Readiness w p Windows Analytics do określenia zestawu zainstalowanych aplikacji i ich zgodności z Windows 10 Enterprise.

## <a name="deployment-process"></a>Proces wdrażania

Aby ukończyć wdrożenie uaktualniania w miejscu pakietu Windows 10 Enterprise, firma Contoso zaimplementowała następujący proces, który zawiera zalecenia dotyczące najlepszych rozwiązań od firmy Microsoft:

1. Włączono pamięć podręczną Menedżer konfiguracji.
2. Utworzono niestandardowe Windows pakietów na podstawie obrazów z centrum Volume Licensing Service Center.
3. Używano Menedżer konfiguracji wdrażania pakietów Windows w punktach dystrybucji w ich sieci, a także wdrożono kompilacje w trzech grupach sprawdzania poprawności i wdrażania.
4. Przeprowadzono ocenę sukcesu komputerów i urządzeń w trzech pierścieniach sprawdzania poprawności i wdrażania za pomocą rozwiązań do sprawdzania kondycji urządzenia i aktualizacji zgodności usługi Windows Analytics.
5. Na podstawie Windows analizy biznesowej firma Contoso określa wersję pakietu Windows 10 Enterprise do wdrożenia w szerokiej grupie wdrażania.
6. Uruchomiono Menedżer konfiguracji zadań wdrażania w celu wdrożenia wybranego pakietu Windows w szerokiej grupie wdrażania.
7. Monitorowane komputery i urządzenia w szerokiej grupie wdrożeniowej przy użyciu rozwiązań kondycji urządzenia i aktualizacji zgodności w celu rozwiązania problemów.

Oto przykład uaktualniania w miejscu firmy Contoso oraz architektury wdrażania bieżących aktualizacji.

![Infrastruktura wdrażania Windows 10 Enterprise firmy Contoso.](../media/contoso-win10/contoso-win10-fig1.png)

Ta infrastruktura składa się z:

- Menedżer konfiguracji, co:
  - Uzyskuje obrazy dla Windows 10 Enterprise z Centrum licencjonowania zbiorowego firmy Microsoft w sieci Microsoft.
  - Jest centralnym punktem administracji pakietów wdrożeniowych.
- Regionalne punkty dystrybucyjne, które zwykle znajdują się w oddziałach regionalnych firmy Contoso.
- Windows komputerach i urządzeniach w różnych lokalizacjach, które otrzymują i instalują pakiety wdrożewne w celu uaktualnienia w miejscu lub bieżących aktualizacji w zależności od członkostwa w grupie.

## <a name="next-step"></a>Następny krok

Dowiedz się, jak firma Contoso korzysta z Menedżer konfiguracji firmy Contoso w celu [wdrażania](contoso-o365pp.md) i Aplikacje Microsoft 365 dla przedsiębiorstw bieżącej wersji w całej organizacji. 

## <a name="see-also"></a>Zobacz też

[System Windows10 dla firm](/windows/deployment/)

[Omówienie Microsoft 365 dla przedsiębiorstw](microsoft-365-overview.md)

[Przewodniki laboratorium testowego](m365-enterprise-test-lab-guides.md)