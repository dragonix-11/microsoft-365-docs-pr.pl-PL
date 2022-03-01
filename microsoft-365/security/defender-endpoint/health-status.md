---
title: Badanie problemów dotyczących kondycji agenta
description: Informacje na temat wartości zwracanych po uruchomieniu polecenia kondycji mdatp
keywords: kondycja mdatp, polecenie, kondycja, stan, polecenie, stan dołączania
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 13407c78f89058efe15ed0f5d8f23272716e0237
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028100"
---
# <a name="investigate-agent-health-issues"></a>Badanie problemów dotyczących kondycji agenta

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

W poniższej tabeli przedstawiono informacje o wartościach zwracanych po uruchomieniu polecenia `mdatp health` i odpowiadających im opisów.

<br>

****

|Value|Opis|
|---|---|
|automatic_definition_update_enabled|Ma wartość True (Prawda), jeśli automatyczne aktualizacje definicji oprogramowania antywirusowego są włączone, w przeciwnym razie false (fałsz).|
|cloud_automatic_sample_submission_consent|Bieżący przykładowy poziom przesyłania. Może być jedną z następujących wartości: <ul><li>**Brak**: Podejrzane próbki nie są przesyłane do firmy Microsoft.</li><li>**Sejf**: Automatycznie przesyłane są tylko podejrzane próbki, które nie zawierają danych umożliwiających identyfikację użytkownika. Jest to wartość domyślna dla tego ustawienia.</li><li>**Wszystkie**: Wszystkie podejrzane próbki są przesyłane do firmy Microsoft.</li></ul>|
|cloud_diagnostic_enabled|Ma wartość True (Prawda), jeśli jest włączone opcjonalne zbieranie danych diagnostycznych, a w przeciwnym razie fałsz. Aby uzyskać więcej informacji dotyczących programu Defender for Endpoint oraz innych produktów i usług, takich jak Program antywirusowy Microsoft Defender i Windows, zobacz [Oświadczenie o ochronie prywatności firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=827576).|
|cloud_enabled|Ma wartość True (Prawda), jeśli ochrona dostarczana w chmurze jest włączona, w przeciwnym razie fałsz.|
|conflicting_applications|Lista aplikacji, które mogą być w konflikcie z usługą Microsoft Defender for Endpoint. Ta lista zawiera między innymi inne produkty zabezpieczające i inne aplikacje, o których wiadomo, że powodują problemy ze zgodnością.|
|definitions_status|Stan definicji oprogramowania antywirusowego.|
|definitions_updated|Data i godzina ostatniej aktualizacji definicji oprogramowania antywirusowego.|
|definitions_updated_minutes_ago|Liczba minut od ostatniej aktualizacji definicji oprogramowania antywirusowego.|
|definitions_version|Wersja definicji oprogramowania antywirusowego.|
|edr_client_version|Wersja klienta EDR uruchomionego na urządzeniu.|
|edr_configuration_version|EDR wersji konfiguracji.|
|edr_device_tags|Lista tagów skojarzonych z urządzeniem.|
|edr_group_ids|Identyfikator grupy, z który jest skojarzone urządzenie.|
|edr_machine_id|Identyfikator urządzenia używany w programie Microsoft 365 Defender.|
|engine_version|Wersja aparatu antywirusowego.|
|zdrowe|Ma wartość True (Prawda), jeśli produkt jest dobrej kondycji, lub false (fałsz).|
|licencjonowana|Ma wartość True (Prawda), jeśli urządzenie jest wnoszone do dzierżawy, lub false (fałsz).|
|log_level|Bieżący poziom dziennika produktu.|
|machine_guid|Unikatowy identyfikator komputera używany przez składnik oprogramowania antywirusowego.|
|network_protection_status|Stan składnika ochrony sieci (tylko system macOS). Może być jedną z następujących wartości: <ul><li>**uruchamianie** — rozpoczyna się ochrona sieci</li><li>**failed_to_start** — nie można wystartować ochrony sieci z powodu błędu</li><li>**uruchomiono** — ochrona sieci jest obecnie uruchomiona na urządzeniu</li><li>**Ponowne uruchamianie —** ochrona sieci jest obecnie ponownie uruchamiana</li><li>**zatrzymywanie** — ochrona sieci jest zatrzymywana</li><li>**zatrzymano** — ochrona sieci nie jest uruchomiona</li></ul>|
|org_id|Organizacja, do których urządzenie zostało naniesone. Jeśli urządzenie nie zostało jeszcze naniesone do żadnej organizacji, to drukowanie jest niedostępne. Aby uzyskać więcej informacji na temat dołączania, zobacz [Dołączanie do programu Microsoft Defender dla punktu końcowego](onboarding.md).|
|passive_mode_enabled|Ma wartość True (Prawda), jeśli składnik oprogramowania antywirusowego jest ustawiony do działania w trybie pasywnym, lub false (fałsz).|
|product_expiration|Data i godzina zakończenia wsparcia technicznego dla bieżącej wersji produktu.|
|real_time_protection_available|Ma wartość True (Prawda), jeśli składnik ochrony w czasie rzeczywistym jest dobrej kondycji, a w przeciwnym razie fałsz.|
|real_time_protection_enabled|Ma wartość True (Prawda), jeśli ochrona antywirusowa w czasie rzeczywistym jest włączona, w przeciwnym razie false (fałsz).|
|real_time_protection_subsystem|Podsystem używany do obsługi ochrony w czasie rzeczywistym. Jeśli ochrona w czasie rzeczywistym nie działa zgodnie z oczekiwaniami, drukowanie jest niedostępne.|
|release_ring|Pierścień wydania. Aby uzyskać więcej informacji, zobacz [Pierścienie wdrażania](deployment-rings.md).|
|
