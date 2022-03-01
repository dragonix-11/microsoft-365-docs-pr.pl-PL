---
title: Często zadawane pytania po włączeniu Microsoft 365 Defender
description: Uzyskaj odpowiedzi na najczęściej zadawane pytania dotyczące licencjonowania, uprawnień, ustawień początkowych i innych produktów i usług związanych z włączaniem Microsoft 365 Defender
keywords: często zadawane pytania, często zadawane pytania, GCC, wprowadzenie, włączanie Microsoft 365 Defender, Microsoft 365 Defender, M365, zabezpieczenia, lokalizacja danych, wymagane uprawnienia, uprawnienia do licencji, strona ustawień
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
ms.openlocfilehash: e5ed41f400c24a2522ea49f2524d0fe629bdbb9f
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2021
ms.locfileid: "63012499"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Często zadawane pytania po włączeniu Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Zapoznaj się z odpowiedziami na najczęściej zadawane pytania dotyczące włączania [Microsoft 365 Defender, w](microsoft-365-defender.md) tym wymaganych licencji i uprawnień, wdrażania usług pomocy technicznej oraz ustawień początkowych.

Aby uzyskać instrukcje dotyczące sposobu jej włączania, [zobacz Włączanie i Microsoft 365 Defender](m365d-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Nie mam licencji Microsoft 365 E5 licencji. Czy mimo to mogę używać Microsoft 365 Defender?

Klienci z następującymi licencjami innymi niż E5 mogą używać Microsoft 365 Defender:

- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft Defender for Identity
- Usługa Microsoft Defender dla aplikacji w chmurze
- Defender for Office 365 (Plan 2)

Aby uzyskać pełną listę obsługiwanych licencji, [przeczytaj wymagania dotyczące licencjonowania](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Czy muszę zainstalować lub wdrożyć wszystko, aby zacząć korzystać z Microsoft 365 Defender?

Nie, Microsoft 365 Defender konsoliduje dane z Microsoft 365 zabezpieczeń, które zostały już wdrożone. Po włączeniu tego rozwiązania środowiska pracy dotyczącej zdarzeń, automatyzacji i pracy myśliwskiej zaczną działać w zakresie wdrożonych produktów. Jeśli żaden z tych produktów nie został poprawnie wdrożony, Microsoft 365 Defender nie będą wyświetlane żadne dane i nie będzie można podjąć żadnych działań.

Aby zoptymalizować swoje Microsoft 365 Defender, zalecamy wdrożenie wszystkich obsługiwanych Microsoft 365 [usług i produktów zabezpieczających](deploy-supported-services.md).

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Gdzie są Microsoft 365 Defender i przechowywu moich danych?

Microsoft 365 Defender wybiera optymalną lokalizację dla centrum danych, w którym są przetwarzane i przechowywane skonsolidowane dane. Jeśli masz usługę Microsoft Defender for Endpoint, wybiera ona tę samą lokalizację, która jest używana przez usługę Defender for Endpoint.

>[!NOTE]
>Program Microsoft Defender for Endpoint automatycznie incyguje centra danych Unii Europejskiej ,gdy jest włączona za pośrednictwem programu Microsoft Defender dla chmury. Microsoft 365 Defender będzie automatycznie zapewniana w tym samym centrum danych UE dla klientów, którzy obsługili usługę Microsoft Defender for Endpoint w ten sposób.

Lokalizacja centrum danych jest wyświetlana przed i po inicjowaniu obsługi administracyjnej usługi na stronie ustawień Microsoft 365 Defender (**Ustawienia > Microsoft 365 Defender**). Jeśli wolisz używać innej lokalizacji centrum danych, wybierz pozycję Potrzebujesz **pomocy?** w portalu Microsoft 365 Defender, aby skontaktować się z pomocą techniczną firmy Microsoft.

## <a name="where-can-i-access-microsoft-365-defender"></a>Gdzie mogę uzyskać dostęp do Microsoft 365 Defender?

Microsoft 365 Defender jest dostępna w: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>Jakich uprawnień potrzebuję, aby uzyskać dostęp do Microsoft 365 Defender?

Konta z przypisanymi następującymi rolami Azure Active Directory (Azure AD) mają dostęp Microsoft 365 Defender funkcji i danych:

- Administrator globalny
- Administrator zabezpieczeń
- Operator zabezpieczeń
- Czytnik globalny
- Czytnik zabezpieczeń
- Administrator zgodności
- Administrator danych dotyczących zgodności
- Administrator aplikacji
- Administrator aplikacji w chmurze


> [!NOTE]
> Ustawienia kontroli dostępu oparte na rolach w programie Microsoft Defender for Endpoint wpływają na dostęp do danych. Aby uzyskać więcej informacji, przeczytaj [o zarządzaniu dostępem do Microsoft 365 Defender](m365d-permissions.md).

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>Która strefa czasowa Microsoft 365 Defender domyślną?

Domyślnie program Microsoft 365 Defender informacje o czasie w strefie czasowej UTC. Możesz zmienić to ustawienie, aby używać lokalnej strefy czasowej. [Dowiedz się więcej o ustawianiu strefy czasowej](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Jak mogę uzyskać informacje na temat nowych funkcji Microsoft 365 Defender aktualizacji interfejsu użytkownika?

Firma Microsoft regularnie udostępnia informacje za pośrednictwem różnych kanałów, między innymi:

- Centrum [wiadomości w](../../admin/manage/message-center.md) centrum administracyjne platformy Microsoft 365
- Wpisy na blogu w społeczności [Microsoft 365 społeczności & dotyczącej zabezpieczeń i zgodności](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

Uzyskaj dostęp do najnowszych publicznie dostępnych funkcji, włączając funkcje [wersji Preview](preview.md).

## <a name="related-topics"></a>Tematy pokrewne

- [Microsoft 365 Defender omówienie](microsoft-365-defender.md)
- [Włącz Microsoft 365 Defender](m365d-enable.md).
- [Wymagania licencyjne i inne wymagania wstępne](prerequisites.md)
- [Wdrażanie obsługiwanych usług](deploy-supported-services.md)
- [Włączanie funkcji wersji Preview](preview.md)
