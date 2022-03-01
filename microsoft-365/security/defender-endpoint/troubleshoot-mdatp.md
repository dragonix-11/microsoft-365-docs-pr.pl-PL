---
title: Rozwiązywanie problemów z usługą Programu Microsoft Defender dla punktu końcowego
description: Znajdź rozwiązania i obejścia znanych problemów, takich jak błędy serwera podczas próby dostępu do usługi.
keywords: rozwiązywanie problemów z usługą Microsoft Defender dla punktu końcowego, błąd serwera, odmowa dostępu, nieprawidłowe poświadczenia, brak danych, portal pulpitu nawigacyjnego, zezwalanie, przeglądarka zdarzeń
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: e9a0fdb1bd10d734da95ba88c459ec665635f40e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997867"
---
# <a name="troubleshoot-service-issues"></a>Rozwiązywanie problemów z usługami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Ta sekcja dotyczy problemów, które mogą się pojawić w przypadku używania usługi Microsoft Defender for Endpoint.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Błąd serwera — odmowa dostępu z powodu nieprawidłowych poświadczeń

Jeśli wystąpi błąd serwera podczas próby uzyskania dostępu do usługi, musisz zmienić ustawienia plików cookie przeglądarki.
Skonfiguruj przeglądarkę tak, aby zezwalała na pliki cookie.

## <a name="elements-or-data-missing-on-the-portal"></a>Brakujące elementy lub dane w portalu

Jeśli na ekranie brakuje niektórych Microsoft 365 Defender lub danych, może to oznaczać, że ustawienia serwera proxy je blokują.

Upewnij się, że ta `*.security.microsoft.com` lista zawiera listę zezwalań serwera proxy.

> [!NOTE]
> Należy używać protokołu HTTPS podczas dodawania następujących punktów końcowych.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Usługa Microsoft Defender for Endpoint wyświetla dzienniki zdarzeń lub błędów w Podglądzie zdarzeń

Zobacz [Przeglądanie zdarzeń i błędów za pomocą Podglądu](event-error-codes.md) zdarzeń, aby uzyskać listę identyfikatorów zdarzeń zgłoszonych przez usługę Microsoft Defender for Endpoint. Ten artykuł zawiera również procedurę rozwiązywania problemów z błędami zdarzeń.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Nie można uruchomić usługi Microsoft Defender dla punktu końcowego po ponownym uruchomieniu komputera i jest wyświetlany błąd 577

Jeśli urządzenia dołączające zostały pomyślnie ukończone, ale program Microsoft Defender for Endpoint nie uruchamia się po ponownym uruchomieniu i jest wyświetlany błąd 577, sprawdź, Windows Defender nie jest wyłączona przez zasady.

Aby uzyskać więcej informacji, [zobacz Program antywirusowy Microsoft Defender wyłączyć zasady](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="known-issues-with-regional-formats"></a>Znane problemy dotyczące formatów regionalnych

### <a name="date-and-time-formats"></a>Formaty daty i godziny

Istnieją pewne znane problemy dotyczące formatów daty i godziny.

Obsługiwane są następujące formaty dat:

- MM/dd/yyyy
- dd/MM/yyyy

Następujące formaty daty i godziny nie są obecnie obsługiwane:

- Format daty yyyy/MM/dd
- Format daty dd/MM/yy
- Format daty z formatem yy. Będzie pokazywać tylko yyyy.
- Format godziny HH:mm:ss nie jest obsługiwany (format 12-godzinny am/pm nie jest obsługiwany). Obsługiwany jest tylko format 24-godzinny.

### <a name="use-of-comma-to-indicate-thousand"></a>Użycie przecinka do wskazania tysięcy

Obsługa używania przecinka jako separatora w liczbach nie jest obsługiwana. W regionach, w których liczba jest rozdzielona przecinkiem wskazującym tysiąc, jako separatora będzie tylko kropka. Na przykład 15,5K jest wyświetlane jako 15,5K.

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Dzierżawa programu Microsoft Defender dla punktu końcowego została automatycznie utworzona w Europie

Gdy do monitorowania serwerów używasz programu Microsoft Defender for Cloud, automatycznie tworzona jest dzierżawa programu Microsoft Defender dla punktu końcowego. Dane programu Microsoft Defender dla punktu końcowego są domyślnie przechowywane w Europie.

## <a name="related-topics"></a>Tematy pokrewne

- [Rozwiązywanie problemów z dołączaniem do programu Microsoft Defender for Endpoint](troubleshoot-onboarding.md)
- [Przeglądanie zdarzeń i błędów przy użyciu Podglądu zdarzeń](event-error-codes.md)
