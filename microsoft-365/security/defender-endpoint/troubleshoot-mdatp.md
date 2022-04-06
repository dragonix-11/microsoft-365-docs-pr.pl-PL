---
title: Rozwiąż problemy z usługą ochrony punktu końcowego w usłudze Microsoft Defender
description: Znajdź rozwiązania i obejścia znanych problemów, takich jak błędy serwera podczas próby uzyskania dostępu do usługi.
keywords: rozwiązywanie problemów z Ochrona punktu końcowego w usłudze Microsoft Defender, błędem serwera, odmową dostępu, nieprawidłowymi poświadczeniami, brakiem danych, portalem pulpitu nawigacyjnego, zezwoleniem, podglądem zdarzeń
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
ms.openlocfilehash: bcd0f5ba70d154c40972c0b8035d1617a9e71966
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665849"
---
# <a name="troubleshoot-service-issues"></a>Rozwiąż problemy z usługami

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/p/?linkid=2154037) 
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz poznać usługę Defender for Endpoint? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

W tej sekcji rozwiązano problemy, które mogą wystąpić podczas korzystania z usługi Ochrona punktu końcowego w usłudze Microsoft Defender.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Błąd serwera — odmowa dostępu z powodu nieprawidłowych poświadczeń

Jeśli podczas próby uzyskania dostępu do usługi wystąpi błąd serwera, musisz zmienić ustawienia plików cookie przeglądarki.
Skonfiguruj przeglądarkę tak, aby zezwalała na pliki cookie.

## <a name="elements-or-data-missing-on-the-portal"></a>Brak elementów lub danych w portalu

Jeśli w Microsoft 365 Defender brakuje niektórych elementów lub danych, możliwe, że ustawienia serwera proxy go blokują.

Upewnij się, że `*.security.microsoft.com` dołączono listę dozwolonych serwerów proxy.

> [!NOTE]
> Podczas dodawania następujących punktów końcowych należy użyć protokołu HTTPS.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>usługa Ochrona punktu końcowego w usłudze Microsoft Defender wyświetla dzienniki zdarzeń lub błędów w Podgląd zdarzeń

Aby uzyskać listę identyfikatorów zdarzeń zgłaszanych przez usługę Ochrona punktu końcowego w usłudze Microsoft Defender, zobacz [Przeglądanie zdarzeń i błędów przy użyciu Podgląd zdarzeń](event-error-codes.md). Artykuł zawiera również kroki rozwiązywania problemów z błędami zdarzeń.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Ochrona punktu końcowego w usłudze Microsoft Defender nie można uruchomić usługi po ponownym uruchomieniu i zostanie wyświetlony błąd 577

Jeśli dołączanie urządzeń zakończy się pomyślnie, ale Ochrona punktu końcowego w usłudze Microsoft Defender nie zostanie uruchomione po ponownym uruchomieniu i zostanie wyświetlony błąd 577, sprawdź, czy Windows Defender nie jest wyłączona przez zasady.

Aby uzyskać więcej informacji, zobacz [Upewnij się, że Program antywirusowy Microsoft Defender nie jest wyłączona przez zasady](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="known-issues-with-regional-formats"></a>Znane problemy z formatami regionalnymi

### <a name="date-and-time-formats"></a>Formaty daty i godziny

Istnieją znane problemy z formatami godziny i daty.

Obsługiwane są następujące formaty dat:

- MM/dd/rrrr
- dd/MM/rrrr

Następujące formaty daty i godziny nie są obecnie obsługiwane:

- Format daty rrrr/MM/dd
- Format daty dd/MM/yy
- Format daty z yy. Pokaże tylko rrrr.
- Format czasu HH:mm:ss nie jest obsługiwany (format 12 godzin am/PM nie jest obsługiwany). Obsługiwany jest tylko format 24-godzinny.

### <a name="use-of-comma-to-indicate-thousand"></a>Użycie przecinka do wskazania tysiąca

Obsługa używania przecinka jako separatora w liczbach nie jest obsługiwana. Regiony, w których liczba jest oddzielona przecinkiem wskazującym tysiąc, będą widzieć tylko użycie kropki jako separatora. Na przykład 15,5 tys. jest wyświetlane jako 15,5 tys.

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Utwórz konto bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Ochrona punktu końcowego w usłudze Microsoft Defender dzierżawa została utworzona automatycznie w Europie

W przypadku używania Microsoft Defender dla Chmury do monitorowania serwerów dzierżawa Ochrona punktu końcowego w usłudze Microsoft Defender jest tworzona automatycznie. Dane Ochrona punktu końcowego w usłudze Microsoft Defender są domyślnie przechowywane w Europie.

## <a name="related-topics"></a>Tematy pokrewne

- [Rozwiązywanie problemów z dołączaniem Ochrona punktu końcowego w usłudze Microsoft Defender](troubleshoot-onboarding.md)
- [Przeglądanie zdarzeń i błędów przy użyciu Podgląd zdarzeń](event-error-codes.md)
