---
title: Wymagania wstępne & — Zarządzanie zagrożeniami i lukami
description: Przed rozpoczęciem korzystania z Zarządzanie zagrożeniami i lukami upewnij się, że masz odpowiednie konfiguracje i uprawnienia.
keywords: wymagań wstępnych & zarządzanie lukami w zabezpieczeniach programu Threat Zarządzanie zagrożeniami i lukami, wymagań wstępnych uprawnień programu Microsoft Defender for Endpoint TVM, zarządzanie lukami w zabezpieczeniach
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 343a5fd1033a6d954c7cd62e2558a4b401f69b20
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997861"
---
# <a name="prerequisites--permissions---threat-and-vulnerability-management"></a>Wymagania wstępne & — Zarządzanie zagrożeniami i lukami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Upewnij się, że Twoje urządzenia:

- Są one wnoszone do programu Microsoft Defender for Endpoint

- Uruchamianie [obsługiwanych systemów operacyjnych i platform](tvm-supported-os.md)

- Zainstaluj i wdrażaj w sieci następujące wymagane aktualizacje, aby zwiększyć wskaźniki wykrywania oceny luk:

  > Wydanie | Numer bazy wiedzy i link aktualizacji zabezpieczeń
  > :---|:---
  > Windows 10 wersji 1709 | [Kb4493441 i](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
  > Windows 10 wersji 1803 | [Kb4493464](https://support.microsoft.com/help/4493464) i [kb 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
  > Windows 10 1809 | [Bazy 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
  > Windows 10 wersji 1903 | [Kb 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)

- Są one dostępne na [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) i [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection-configure), aby pomóc w rozwiązywaniu problemów znalezionych przez użytkowników Zarządzanie zagrożeniami i lukami. Jeśli korzystasz z Menedżer konfiguracji, zaktualizuj konsolę do najnowszej wersji.

  > [!NOTE]
  > Jeśli włączono połączenie usługi Intune, podczas tworzenia żądania zaradczego jest dostępna opcja utworzenia zadania zabezpieczeń usługi Intune. Ta opcja nie jest wyświetlana, jeśli nie ustawiono połączenia.

- Mieć co najmniej jedno zalecenie zabezpieczeń, które można wyświetlić na stronie urządzenia

- Są oznakowane lub oznaczone jako współzadaży

## <a name="relevant-permission-options"></a>Odpowiednie opcje uprawnień

1. Zaloguj się do portalu Microsoft 365 Defender przy użyciu konta z przypisaną rolą administratora zabezpieczeń lub administratora globalnego.
2. W okienku nawigacji wybierz pozycję Ustawienia > **punkty końcowe > role.**

Aby uzyskać więcej informacji, zobacz [Tworzenie ról w kontrolach dostępu opartych na rolach i zarządzanie nimi](user-roles.md).

### <a name="view-data"></a>Wyświetlanie danych

- **Operacje zabezpieczeń** — wyświetlanie wszystkich danych operacji zabezpieczeń w portalu
- **Zagrożenia i zarządzanie lukami w zabezpieczeniach** — wyświetlanie Zarządzanie zagrożeniami i lukami danych w portalu

### <a name="active-remediation-actions"></a>Aktywne działania naprawcze

- **Operacje zabezpieczeń** — działanie w odpowiedzi, zatwierdzanie lub odrzucanie oczekujących działań naprawczych, zarządzanie listami dozwolonymi/zablokowanymi w celu automatyzacji i wskaźników
- **Zagrożenia i zarządzanie lukami w zabezpieczeniach — Obsługa wyjątków** — Tworzenie nowych wyjątków i zarządzanie aktywnymi wyjątkami
- **Zagrożenia i zarządzanie lukami w zabezpieczeniach —** Obsługa działań naprawczych — przesyłanie nowych żądań rozwiązywania problemów, tworzenie biletów i zarządzanie istniejącymi działaniami naprawczymi

Aby uzyskać więcej informacji, zobacz [Opcje uprawnień RBAC](user-roles.md#permission-options)

## <a name="related-articles"></a>Artykuły pokrewne

- [Omówienie zagrożeń i zarządzanie lukami w zabezpieczeniach wiadomości](next-gen-threat-and-vuln-mgt.md)
- [Obsługiwane systemy operacyjne i platformy](tvm-supported-os.md)
- [Przypisz wartość urządzenia](tvm-assign-device-value.md)
- [Zagrożenia i zarządzanie lukami w zabezpieczeniach nawigacyjny](tvm-dashboard-insights.md)

