---
title: Włączanie środowiska oceny dla programu Microsoft Defender dla tożsamości
description: Skonfiguruj usługę Microsoft Defender for Identity w laboratorium Microsoft 365 Defender testowym lub środowisku pilotażowym, instalując & czujnik i wykrywając administratorów lokalnych na innych komputerach.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6910336dea0559ad241c240cde09d3929fe2e422
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63013370"
---
# <a name="enable-the-evaluation-environment-for-microsoft-defender-for-identity"></a>Włączanie środowiska oceny dla programu Microsoft Defender dla tożsamości

**Dotyczy:**
- Microsoft 365 Defender

Ten artykuł dotyczy [kroku 2 z 2](eval-defender-identity-overview.md) w procesie konfigurowania środowiska oceny dla programu Microsoft Defender dla tożsamości. Aby uzyskać więcej informacji na temat tego procesu, zobacz artykuł [z omówieniem](eval-defender-identity-overview.md).

Aby skonfigurować środowisko usługi Microsoft Defender dla tożsamości, należy wykonać poniższe czynności. 

![Procedura włączania usługi Microsoft Defender dla tożsamości w środowisku oceny programu Microsoft Defender.](../../media/defender/m365-defender-identity-eval-enable-steps.png)

- [Krok 1. Konfigurowanie wystąpienia usługi Defender for Identity](#step-1-set-up-the-defender-for-identity-instance)
- [Krok 2. Instalowanie i konfigurowanie czujnika](#step-2-install-and-configure-the-sensor)
- [Krok 3. Konfigurowanie dziennika zdarzeń i ustawień serwera proxy na komputerach za pomocą czujnika](#step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor)
- [Krok 4. Zezwalanie u defenderowi na tożsamości na identyfikowanie administratorów lokalnych na innych komputerach](#step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers)

## <a name="step-1-set-up-the-defender-for-identity-instance"></a>Krok nr 1. Konfigurowanie wystąpienia usługi Defender for Identity

Zaloguj się do portalu usługi Defender for Identity, aby utworzyć wystąpienie, a następnie połączyć to wystąpienie ze środowiskiem usługi Active Directory. 

|  |Krok     |Więcej informacji  |
|---------|---------|---------|
|1     | Tworzenie wystąpienia usługi Defender for Identity        | [Szybki start: tworzenie wystąpienia usługi Microsoft Defender dla tożsamości](/defender-for-identity/install-step1)        |
|2     | Połączenie wystąpienia usługi Defender for Identity do lasu usługi Active Directory   | [Szybki start: Połączenie do lasu usługi Active Directory](/defender-for-identity/install-step2)  |
| | |

## <a name="step-2-install-and-configure-the-sensor"></a>Krok nr 2. Instalowanie i konfigurowanie czujnika

Następnie pobierz, zainstaluj i skonfiguruj czujnik defender dla tożsamości w kontrolerach domeny i serwerach usług AD FS w środowisku lokalnym.

|  |Krok     |Więcej informacji  |
|---------|---------|---------|
|1     | Określ, ile czujnika usługi Microsoft Defender dla tożsamości jest potrzebnych.        | [Planowanie pojemności usługi Microsoft Defender dla tożsamości](/defender-for-identity/capacity-planning)   |
|2     | Pobierz pakiet instalacyjny czujnika  |  [Szybki start: Pobieranie pakietu instalacyjnego czujnika tożsamości usługi Microsoft Defender for Identity](/defender-for-identity/install-step3)   |
|3     | Zainstaluj czujnik usługi Defender for Identity    |  [Szybki start: instalowanie czujnika usługi Microsoft Defender for Identity](/defender-for-identity/install-step4)       |
|4     | Konfigurowanie czujnika       |  [Konfigurowanie ustawień czujnika tożsamości usługi Microsoft Defender ](/defender-for-identity/install-step5)   |
|   |         |         |

## <a name="step-3-configure-event-log-and-proxy-settings-on-machines-with-the-sensor"></a>Krok nr 3. Konfigurowanie dziennika zdarzeń i ustawień serwera proxy na komputerach za pomocą czujnika

Na komputerach, na których został zainstalowany czujnik, skonfiguruj ustawienia dziennika Windows i internetowego serwera proxy, aby włączyć i ulepszyć funkcje wykrywania.

|  |Krok     |Więcej informacji  |
|---------|---------|---------|
|1     | Konfigurowanie Windows dziennika zdarzeń         | [Konfigurowanie Windows zdarzeń](/defender-for-identity/configure-windows-event-collection)        |
|2     | Konfigurowanie ustawień internetowego serwera proxy        | [Konfigurowanie ustawień serwera proxy punktu końcowego i łączności internetowej dla czujnika tożsamości programu Microsoft Defender](/defender-for-identity/configure-proxy)        |
|   |         |         |

## <a name="step-4-allow-defender-for-identity-to-identify-local-admins-on-other-computers"></a>Krok nr 4. Zezwalanie u defenderowi na tożsamości na identyfikowanie administratorów lokalnych na innych komputerach

Wykrywanie późniejszych ścieżek ruchu usługi Microsoft Defender for Identity jest używane na podstawie zapytań identyfikujące administratorów lokalnych na określonych komputerach. Te zapytania są wykonywane za pomocą protokołu SAM-R przy użyciu konta usługi Defender dla tożsamości. 

Aby zapewnić, Windows klienci i serwery umożliwiają kontu Usługi Defender dla tożsamości wykonywanie operacji SAM-R, należy przeprowadzić modyfikację programu zasady grupy, aby oprócz skonfigurowanych kont wymienionych w zasadach dostępu do sieci dodać konto usługi Defender for Identity. Upewnij się, że zasady grupy mają zastosowanie do wszystkich komputerów z **wyjątkiem kontrolerów domeny**.

Aby dowiedzieć się, jak to zrobić, zobacz [Konfigurowanie usługi Microsoft Defender dla tożsamości](/defender-for-identity/install-step8-samr) w celu zdalnego dzwoninia do SAM. 

## <a name="next-steps"></a>Następne kroki

Krok 3 z 3: [Pilotażowa usługa Microsoft Defender dla tożsamości](eval-defender-identity-pilot.md)

Wróć do przeglądu programu [Evaluate Microsoft Defender for Identity](eval-defender-identity-overview.md)

Wróć do przeglądu projektów [oceniania i Microsoft 365 Defender](eval-overview.md)