---
title: Przekierowywanie kont z Office 365 zabezpieczeń i zgodności do nowego Microsoft 365 Defender
description: Jak przekierować z usługi Defender w celu Office 365 do Microsoft 365 Defender.
keywords: Microsoft 365 Defender Wprowadzenie do Microsoft 365 Defender, przekierowywanie centrum zabezpieczeń
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom:
- admindeeplinkDEFENDER
- admindeeplinkEXCHANGE
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: fc49494d924129ed2771bc399467f3e9101e7620
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2022
ms.locfileid: "63010381"
---
# <a name="redirecting-accounts-from-office-365-security-and-compliance-center-to-microsoft-365-defender"></a>Przekierowywanie kont z Office 365 zabezpieczeń i zgodności do Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- Microsoft 365 Defender
- Defender for Office 365

W tym artykule wyjaśniono, jak przekierować konta do Microsoft 365 Defender, włączając automatyczne przekierowywanie z byłego Centrum zabezpieczeń i zgodności Office 365 (protection.office.com) do Microsoft 365 Defender (security.microsoft.com).

## <a name="what-to-expect"></a>Czego można się spodziewać

Gdy funkcja automatycznego przekierowywania będzie włączona i aktywna, użytkownicy uzyskają dostęp do funkcji związanych z zabezpieczeniami w programie Office 365 Security and Compliance (protection.office.com), zostaną automatycznie przekierowani do usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

Dowiedz się więcej o tym, co się zmieniło: [Program Microsoft Defender dla Office 365 w Microsoft 365 Defender](microsoft-365-security-center-mdo.md).

Gdy jest włączone automatyczne przekierowywanie, użytkownicy będą przekierowani do Microsoft 365 Defender, gdy będą korzystać z funkcji zabezpieczeń w Centrum zabezpieczeń Office 365 zabezpieczeń i zgodności.

Obejmują one funkcje w sekcji Zarządzanie zagrożeniami, Alerty (Wyświetlanie alertów i zasad alertów) oraz pulpitu nawigacyjnego i raportów Zarządzania zagrożeniami. Elementy w Centrum zabezpieczeń Office 365 zgodności, które nie są związane z zabezpieczeniami, nie są przekierowywany do Microsoft 365 Defender.

Elementy związane ze zgodnością można znaleźć w centrum Centrum zgodności platformy Microsoft 365, a elementy związane z przepływem poczty e-mail można znaleźć w centrum <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange administracyjnego</a>.

Przekierowywanie nie wpływa na wszystkie inne funkcje, niezależnie od tego, czy są związane ze zgodnością, czy też funkcje, które obie są do nich dostępne.

### <a name="set-up-portal-redirection"></a>Konfigurowanie przekierowywania portalu

Od października 2021 r. przekierowywanie portalu jest teraz wykonywane automatycznie lub domyślnie. Jeśli jednak wymaga to tymczasowego wyłączenia, zostaną one opisane poniżej.

<!--To start routing accounts to Microsoft 365 Defender at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">security.microsoft.com</a>:

1. Make sure you're a global administrator or have security administrator permissions in Azure Active directory.
2. Sign in to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.
3. Go to **Settings** > **Email & collaboration** > **Portal redirection**.  
4. Toggle the Automatic redirection setting to **On**.
5. Click **Enable** to apply automatic redirection to Microsoft 365 Defender.

> [!NOTE]
> After redirection is enabled, accounts in active sessions while this setting is applied will not be ejected from their session and will only be routed to Microsoft 365 Defender after ending their current session and signing back in again.-->

## <a name="can-i-go-back-to-using-the-former-portal"></a>Czy mogę wrócić do korzystania z poprzedniego portalu?

Jeśli coś u Ciebie nie działa lub jeśli nie możesz ukończyć niczego za pośrednictwem programu Microsoft 365 Defender, chcemy uzyskać informacje na ten temat za pomocą opcji opinii o portalu. Jeśli masz problemy z przekierowywaniem, po daj nam znać.

Aby przywrócić poprzedni portal:

1. Zaloguj się, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> administrator globalny lub używając konta i z uprawnieniami administratora zabezpieczeń w usłudze Azure Active Directory.

2. Przejdź do **Ustawienia** >  **Mail & Mail Przekierowywanieportowe** > .

3. Przełącz ustawienie Automatyczne przekierowywanie na **Wyłączone**.

4. Po **wyświetleniu** monitu & wyłącz lub udostępnij opinię.

To ustawienie można włączyć ponownie w dowolnym momencie.

## <a name="related-information"></a>Informacje pokrewne
- [Microsoft 365 Defender omówienie](microsoft-365-defender.md)
- [Program Microsoft Defender dla punktu końcowego w programie Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Firma Microsoft zapewnia ujednolicone zabezpieczenia SIEM i XDR w celu unowocześnienia operacji zabezpieczeń](https://www.microsoft.com/security/blog/?p=91813) 
- [XDR a SIEM infografika](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [Informacje Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [Portale zabezpieczeń firmy Microsoft i centra administracyjne](portals.md)
