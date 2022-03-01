---
title: Rozwiązywanie problemów z integracją narzędzia SIEM w programie Microsoft Defender for Endpoint
description: Rozwiązywanie problemów, które mogą wystąpić podczas korzystania z narzędzi SIEM w programie Microsoft Defender for Endpoint.
keywords: troubleshoot, siem, client secret, secret
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
ms.openlocfilehash: b6ed0342183734d9b4feb1c20a6c4059b77e64d6
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010433"
---
# <a name="troubleshoot-siem-tool-integration-issues"></a>Rozwiązywanie problemów z integracją narzędzia SIEM

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do usługi Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Podczas wciągania wykrywania w narzędziach SIEM może być konieczne rozwiązanie problemów.

Ta strona zawiera szczegółowe kroki rozwiązywania napotkanych problemów.

## <a name="learn-how-to-get-a-new-client-secret"></a>Dowiedz się, jak uzyskać klucz tajny nowego klienta

Jeśli klucz tajny klienta wygaśnie lub jeśli kopia została zagubiona podczas włączania aplikacji narzędzia SIEM, musisz uzyskać nową tajemnicę.

1. Zaloguj się do [Portalu zarządzania Azure](https://portal.azure.com).

2. Wybierz pozycję **Azure Active Directory**.

3. Wybierz dzierżawę.

4. Kliknij **pozycję Rejestracje aplikacji**. Następnie na liście aplikacji wybierz aplikację.

5. Wybierz **pozycję Certyfikaty & Tajemnice** , kliknij pozycję Klucz tajny nowego klienta, a następnie podaj opis i określ czas ważności.

6. Kliknij **Zapisz**. Zostanie wyświetlona wartość klucza.

7. Skopiuj wartość i zapisz ją w bezpiecznym miejscu.

## <a name="error-when-getting-a-refresh-access-token"></a>Błąd podczas uzyskiwania tokenu dostępu odświeżania

Jeśli napotkasz błąd podczas próby uzyskania tokenu odświeżania podczas korzystania z interfejsu API analizy zagrożeń lub narzędzi SIEM, musisz dodać adres URL odpowiedzi dla odpowiedniej aplikacji w aplikacji Azure Active Directory.

1. Zaloguj się do [Portalu zarządzania Azure](https://ms.portal.azure.com).

2. Wybierz pozycję **Azure Active Directory**.

3. Wybierz dzierżawę.

4. Kliknij **pozycję Rejestracja aplikacji**. Następnie na liście aplikacji wybierz aplikację.

5. Dodaj następujący adres URL:
   - W przypadku Unii Europejskiej: `https://winatpmanagement-eu.securitycenter.windows.com/UserAuthenticationCallback`
   - W przypadku Zjednoczonego Królestwa: `https://winatpmanagement-uk.securitycenter.windows.com/UserAuthenticationCallback`
   - Dla Stanów Zjednoczonych:  `https://winatpmanagement-us.securitycenter.windows.com/UserAuthenticationCallback`.

6. Kliknij **Zapisz**.

## <a name="error-while-enabling-the-siem-connector-application"></a>Błąd podczas włączania aplikacji łącznika SIEM

Jeśli napotkasz błąd podczas próby włączenia aplikacji łącznika SIEM, sprawdź ustawienia blokowania wyskakujących okienek w przeglądarce. Po włączeniu funkcji może on blokować nowe okno otwierane.

> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshootsiem-belowfoldlink)

## <a name="related-topics"></a>Tematy pokrewne

- [Wykrywanie do narzędzi SIEM](configure-siem.md)

