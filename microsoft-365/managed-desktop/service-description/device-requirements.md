---
title: Wymagania dotyczące urządzeń
description: Podsumowanie minimalnych wymagań dotyczących sprzętu i oprogramowania, które muszą być spełnione, aby urządzenia pracowały z Microsoft Managed Desktop
keywords: Microsoft Managed Desktop, Microsoft 365, usługa, dokumentacja
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 5fb600434c8f6d7b62e7fd7408c3567a34c0eda0
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010420"
---
# <a name="device-requirements"></a>Wymagania dotyczące urządzeń

Microsoft Managed Desktop regularnie ocenia wymagania dotyczące urządzeń uwzględniane w usłudze. W tym artykule opisano wymagania dotyczące sprzętu i oprogramowania, które musi spełnić urządzenie, aby móc pracować z Microsoft Managed Desktop. W zależności od tych wymagań możesz zapoznać się z listą urządzeń już zatwierdzonych do używania z usługą. Filtrowanie listy Microsoft Managed Desktop w [witrynie sklepu Windows Pro firmowego](https://www.microsoft.com/en-us/windows/business/devices)

> [!NOTE]
> Te wymagania mogą się zmienić w dowolnym momencie, ale z 30-dniowym powiadomieniem o wszelkich zmianach wymagań dotyczących sprzętu. Ostatnio zmienione wymagania są oznaczone znakiem <b>\*</b>. 

## <a name="check-hardware-requirements"></a>Sprawdzanie wymagań sprzętowych

Oprócz sprawdzania specyfikacji urządzenia możesz również użyć do pobrania funkcji sprawdzania gotowości w celu sprawdzenia[](../get-ready/readiness-assessment-downloadable.md), czy dane urządzenie spełnia niezbędne wymagania. To narzędzie sprawdza również ustawienia i punkty końcowe sieci, które są również niezbędne do działania usługi.

## <a name="minimum-requirements"></a>Wymagania minimalne

Aby zostać zarejestrowanym Microsoft Managed Desktop, urządzenie musi spełniać lub przekraczać wszystkie te wymagania.

### <a name="manufacturer"></a>Producent

Urządzenie musi zostać wykonane przez jednego z tych producentów:

- Dell
- HP
- Lenovo
- Microsoft

> [!NOTE] 
> Od 1 marca 2022 r. urządzenia zarządzane przez Microsoft Managed Desktop muszą być obsługiwane przez OEM. We współpracy ze swoim producentem OEM dowiedz się, kiedy wsparcie techniczne dla urządzeń w Twoim portfelu zostanie wyeks obsługi. Klienci będą odpowiedzialni za zapewnienie wymiany urządzeń przed zakończeniem użytkowania pomocy technicznej. Wszelkie urządzenia, które nie obsługują producentów OEM, nadal będą zarządzane przez firmę Microsoft Managed Desktop, ale pomoc techniczna dla tych urządzeń może być ograniczona, ponieważ mogą one stanowić ryzyko problemów z zabezpieczeniami i wydajnością, które mogą nie być w stanie zmniejszyć naszą usługę.
</b>

### <a name="installed-software"></a>Zainstalowane oprogramowanie

To oprogramowanie musi być preinstalowane na urządzeniu:

- <b>\*</b>Windows 10 lub Windows 11: Enterprise, Pro lub Pro Workstation edition
- 64-bitowa wersja Aplikacje Microsoft 365 dla przedsiębiorstw 
- Wszystkie odpowiednie sterowniki urządzeń


### <a name="physical-features"></a>Funkcje fizyczne

Urządzenia muszą mieć następujące funkcje:

- Włączono bezpieczny rozruch z interfejsem UEFI 
- Moduł Zaufane platformy 2.0 
- Możliwość zabezpieczenia opartego na wirtualizacji 
- [Integralność kodu chroniona przez hipervisor, obsługiwana](/windows-hardware/drivers/bringup/device-guard-and-credential-guard) przez

Aby uzyskać więcej informacji na temat tych funkcji i związanych z nimi technologii, z których korzysta Microsoft Managed Desktop [techniczne](../intro/technologies.md), zobacz informacje.

> [!NOTE]
>- ARM nie są obsługiwane.
>- <b>\*</b>Windows 11 ma dodatkowe [wymagania sprzętowe](/windows/whats-new/windows-11-requirements).

Urządzenia powinny spełniać lub przekraczać następujące limity pamięci i pamięci:

- Dysk rozruchowy musi być dowolnym typem innym niż dysk twardy. Na przykład prawidłowe są dyski SSD, NVMe i eMMC.
- Dysk rozruchowy musi mieć pojemność co najmniej 128 GB.
- Pamięć wewnętrzna urządzenia (RAM) musi być równa lub 8 GB.

Jeśli urządzenie zostało wykonane po 1 lipca 2020 r., powinno również mieć kamerę na podczerwień, czytnik linii papilarnych lub oba te urządzenia w celu obsługi [Windows Hello.](/windows-hardware/design/device-experiences/windows-hello-enhanced-sign-in-security)

## <a name="recommended-features"></a>Zalecane funkcje

Użytkownicy będą mieli o wiele lepsze środowisko, jeśli wybierzesz urządzenia z tymi funkcjami:

- Procesor platformy Intel vPro lub procesor AMD Ryzen Pro firmy Intel
- Dysk startowy typu SSD o pojemności co najmniej 256 GB
- Pamięć ram urządzenia wewnętrznego o pojemności co najmniej 16 GB
- Obsługa nowoczesnego wstrzymania
- Urządzenie jest typu Komputer typu Zabezpieczona podstawowa (Secured-core)
- Obsługa kernelu DMA Protection
