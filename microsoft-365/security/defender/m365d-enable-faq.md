---
title: Często zadawane pytania podczas włączania Microsoft 365 Defender
description: Uzyskaj odpowiedzi na najczęściej zadawane pytania dotyczące licencjonowania, uprawnień, ustawień początkowych oraz innych produktów i usług związanych z włączaniem Microsoft 365 Defender
keywords: często zadawane pytania, często zadawane pytania, GCC, rozpoczynanie pracy, włączanie Microsoft 365 Defender, Microsoft 365 Defender, M365, zabezpieczenia, lokalizacja danych, wymagane uprawnienia, uprawnienia do licencji, strona ustawień
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 73dddcfc1389eb5bb0b0115f0666c413dc7d2a01
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663209"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Często zadawane pytania podczas włączania Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Przeczytaj odpowiedzi na najczęściej zadawane pytania dotyczące włączania [Microsoft 365 Defender](microsoft-365-defender.md), w tym wymagane licencje i uprawnienia, wdrażanie usług pomocy technicznej i ustawienia początkowe.

Aby uzyskać instrukcje dotyczące włączania usługi, [zobacz Włączanie Microsoft 365 Defender](m365d-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Nie mam licencji Microsoft 365 E5. Czy nadal mogę używać Microsoft 365 Defender?

Klienci z następującymi licencjami spoza E5 mogą używać Microsoft 365 Defender:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Ochrona usługi Office 365 w usłudze Defender (plan 2)

Aby uzyskać pełną listę obsługiwanych licencji, [zapoznaj się z wymaganiami dotyczącymi licencjonowania](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Czy muszę zainstalować lub wdrożyć coś, aby rozpocząć korzystanie z Microsoft 365 Defender?

Nie, Microsoft 365 Defender konsoliduje dane z Microsoft 365 usług zabezpieczeń, które zostały już wdrożone. Po włączeniu środowiska zdarzeń, automatyzacji i wyszukiwania zagrożeń rozpoczną pracę w zakresie wdrożonych produktów. Jeśli żaden z tych produktów nie zostanie prawidłowo wdrożony, Microsoft 365 Defender nie wyświetli żadnych danych i nie będzie w stanie podjąć żadnych działań.

Aby zoptymalizować środowisko Microsoft 365 Defender, zalecamy wdrożenie *wszystkich* obsługiwanych [Microsoft 365 produktów i usług zabezpieczeń](deploy-supported-services.md).

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Gdzie Microsoft 365 Defender przetwarza i przechowuje moje dane?

Microsoft 365 Defender automatycznie wybiera optymalną lokalizację centrum danych, w którym są przetwarzane i przechowywane skonsolidowane dane. Jeśli masz Ochrona punktu końcowego w usłudze Microsoft Defender, wybiera tę samą lokalizację używaną przez usługę Defender dla punktu końcowego.

>[!NOTE]
>Ochrona punktu końcowego w usłudze Microsoft Defender automatycznie przepisy w centrach danych Unii Europejskiej (UE) po włączeniu za pośrednictwem Microsoft Defender dla Chmury. Microsoft 365 Defender będzie automatycznie aprowizować w tym samym centrum danych UE dla klientów, którzy aprowizowali Ochrona punktu końcowego w usłudze Microsoft Defender w ten sposób.

Lokalizacja centrum danych jest wyświetlana przed usługą i po jej zainicjowaniu na stronie ustawień dla Microsoft 365 Defender (**Ustawienia > Microsoft 365 Defender**). Jeśli wolisz korzystać z innej lokalizacji centrum danych, wybierz pozycję **Potrzebujesz pomocy?** w portalu Microsoft 365 Defender, aby skontaktować się z pomocą techniczną firmy Microsoft.

## <a name="where-can-i-access-microsoft-365-defender"></a>Gdzie mogę uzyskać dostęp do Microsoft 365 Defender?

Microsoft 365 Defender jest dostępna pod adresem: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>Jakich uprawnień potrzebuję, aby uzyskać dostęp do Microsoft 365 Defender?

Konta przypisane do następujących ról Azure Active Directory (Azure AD) mogą uzyskiwać dostęp do Microsoft 365 Defender funkcji i danych:

- Administrator globalny
- Administrator zabezpieczeń
- Operator zabezpieczeń
- Czytelnik globalny
- Czytelnik zabezpieczeń
- Administrator zgodności
- Administrator danych zgodności
- Administrator aplikacji
- Administrator aplikacji w chmurze


> [!NOTE]
> Ustawienia kontroli dostępu na podstawie ról w Ochrona punktu końcowego w usłudze Microsoft Defender wpływają na dostęp do danych. Aby uzyskać więcej informacji, przeczytaj o [zarządzaniu dostępem do Microsoft 365 Defender](m365d-permissions.md).

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>Jaka strefa czasowa Microsoft 365 Defender domyślna?

Domyślnie Microsoft 365 Defender wyświetla informacje o czasie w strefie czasowej UTC. To ustawienie można zmienić, aby używać lokalnej strefy czasowej. [Dowiedz się więcej o ustawianiu strefy czasowej](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Jak mogę dowiedzieć się więcej o nowych funkcjach Microsoft 365 Defender i aktualizacjach interfejsu użytkownika?

Firma Microsoft regularnie udostępnia informacje za pośrednictwem różnych kanałów, w tym:

- [Centrum komunikatów](../../admin/manage/message-center.md) w Centrum administracyjne platformy Microsoft 365
- Blogposts in the [Microsoft 365 security & compliance tech community (Blogposts in the Microsoft 365 security & compliance tech community (Blogposts in the Microsoft 365 security & compliance tech community](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Uzyskaj najnowsze publicznie dostępne środowiska, włączając [funkcje w wersji zapoznawczej](preview.md).

## <a name="related-topics"></a>Tematy pokrewne

- [omówienie Microsoft 365 Defender](microsoft-365-defender.md)
- [Włącz Microsoft 365 Defender](m365d-enable.md).
- [Wymagania licencyjne i inne wymagania wstępne](prerequisites.md)
- [Wdrażanie obsługiwanych usług](deploy-supported-services.md)
- [Włączanie funkcji w wersji zapoznawczej](preview.md)
