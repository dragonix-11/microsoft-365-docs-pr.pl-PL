---
title: Rejestracja partnera
description: Partnerzy mogą rejestrować urządzenia, które mają być zarządzane przez Microsoft Managed Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: af1e187c77acde257fa3458709fae50616cf810d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704840"
---
# <a name="partner-registration"></a>Rejestracja partnera

W tym artykule opisano kroki rejestrowania urządzeń przez partnerów. Proces rejestrowania urządzeń samodzielnie jest dokumentowany w te sposób: [Ręczna rejestracja](manual-registration.md).

## <a name="prepare-for-registration"></a>Przygotuj się do rejestracji

Przed zakończeniem rejestracji klienta należy ustanowić z nim relację w [Centrum partnerskim](https://partner.microsoft.com/dashboard). Aby uzyskać więcej informacji na temat tego procesu, zapoznaj się z [dokumentacją zgody](/windows/deployment/windows-autopilot/registration-auth#csp-authorization). Każdy partner CSP może dodawać urządzenia w imieniu dowolnego klienta, o ile klient na to nie wyraża zgody. Aby uzyskać więcej informacji na temat relacji partnerów i uprawnień rozwiązania Autopilot, zobacz Pomoc [Centrum partnerskiego](/partner-center/customers_revoke_admin_privileges#windows-autopilot).

> [!NOTE]
> Ta dokumentacja jest wyłącznie dla partnerów i producentów OEM. Proces samodzielnej rejestracji jest dokumentowany w te [sposób: Rejestracja ręczna](manual-registration.md).

## <a name="register-devices-using-the-partner-center"></a>Rejestrowanie urządzeń za pomocą Centrum partnerskiego

Po nawiązyciu relacji z klientami możesz za pomocą Centrum partnerskiego dodać urządzenia do rozwiązania Autopilot dla dowolnego z klientów.

**Aby zarejestrować urządzenia za pomocą Centrum partnerskiego:**

1. Przejdź do [Centrum partnerskiego](https://partner.microsoft.com/dashboard).
2. Wybierz **pozycję** Klienci z menu Centrum partnerskie, a następnie wybierz klienta, którego urządzeniami chcesz zarządzać.
3. Na stronie szczegółów klienta wybierz pozycję **Urządzenia**.
4. W **obszarze Zastosuj profile** do urządzeń wybierz **pozycję Dodaj urządzenia**.
5. Wprowadź odpowiedni tag grupy dla wybranego profilu urządzenia (jak pokazano w poniższej tabeli), a następnie wybierz pozycję Przeglądaj,  aby przekazać listę klientów (w formacie pliku .csv) do Centrum partnerskiego.

| [Profil urządzenia](../service-description/profiles.md) | Tag grupy |
| ----- | -----|
| Poufne dane | **Microsoft365ManagedSensitiveData\_** |
| Użytkownik zasilania | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> Nazwa grupy musi dokładnie odpowiadać tym, które są wymienione w tabeli, z uwzględnieniem w nich liter i znaków specjalnych. Umożliwi to przypisanie nowo zarejestrowanych urządzeń za pomocą profilu rozwiązania Microsoft Managed Desktop Autopilot.

>[!NOTE]
> Ten plik powinien zostać .csv wraz z zakupem urządzenia. Jeśli plik nie został .csv, możesz utworzyć go samodzielnie, korzystając z procedury opisanej w sekcji Dodawanie urządzeń do rozwiązania [Windows Autopilot](/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell). Wymagania: <ul><li>Dodatkowe kolumny nie są obsługiwane.</li> <li>Oferty nie są obsługiwane.</li> <li>Można używać tylko plików tekstowych w formacie ANSI (nie unicode).</li> <li>W nagłówkach jest wielkość liter.</li></ul> Edytowanie pliku w Excel zapisaniu go jako pliku CSV nie spowoduje wygenerowania pliku do użytku z powodu tych wymagań. Upewnij się, że zachowywane są wszystkie zera wiodące w numerach seryjnych urządzeń. Partnerzy powinni używać rozwiązania [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) do rejestrowania urządzeń Microsoft Managed Desktop w Centrum partnerskim.

Jeśli podczas próby przekazania pliku .csv zostanie wyświetlony komunikat o błędzie, sprawdź jego format. Upewnij się, że kolejność kolumn jest dopasowana do tego, co opisano w te Windows Korzystanie z profilów rozwiązania [Autopilot](/partner-center/autopilot#add-devices-to-a-customers-account) na nowych urządzeniach w celu dostosowania funkcji klienta. Możesz również użyć przykładowego pliku .csv dostępnego za pomocą linku obok przycisku **Dodaj** urządzenia, aby utworzyć listę urządzeń.

Aby uzyskać więcej informacji na temat rozwiązania Autopilot w scenariuszach partnera, zobacz [Dodawanie urządzeń do konta klienta](/partner-center/autopilot#add-devices-to-a-customers-account).

## <a name="register-devices-by-using-the-oem-api"></a>Rejestrowanie urządzeń przy użyciu interfejsu API OEM

Przed zakończeniem rejestracji klienta należy najpierw ustanowić z nim relację. Musisz mieć unikatowy link do świadczenia usług dla swoich klientów. Zobacz [Jak ustanowić relację OEM](/windows/deployment/windows-autopilot/registration-auth#oem-authorization).

Po nawiązyniu relacji możesz rozpocząć rejestrację urządzeń dla klientów przy użyciu odpowiedniego tagu grupy dla każdego wybranego profilu urządzenia:

| Profil urządzenia | Tag grupy |
| ----- | ----- |
| Poufne dane | **Microsoft365ManagedSensitiveData\_** |
| Użytkownik zasilania | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> Tagi grupy muszą dokładnie odpowiadać tym, które są wymienione w tabeli, łącznie ze znakami specjalnymi i kapitalikami. Umożliwi to przypisanie nowo zarejestrowanych urządzeń za pomocą profilu rozwiązania Microsoft Managed Desktop Autopilot.
