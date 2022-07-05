---
title: Microsoft Defender for Cloud Apps w Microsoft 365 Defender (wersja zapoznawcza)
description: Dowiedz się więcej o zmianach z Microsoft Defender for Cloud Apps na Microsoft 365 Defender
keywords: Wprowadzenie do Microsoft 365 Defender, Microsoft Defender for Cloud Apps
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 05/03/2022
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 9113e3f06ba0f9c8cbec0da6d738cc170a215771
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617002"
---
# <a name="microsoft-defender-for-cloud-apps-in-microsoft-365-defender-preview"></a>Microsoft Defender for Cloud Apps w Microsoft 365 Defender (wersja zapoznawcza)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Cloud Apps](/defender-cloud-apps/)

Microsoft Defender for Cloud Apps jest teraz częścią Microsoft 365 Defender. Portal Microsoft 365 Defender umożliwia administratorom zabezpieczeń wykonywanie zadań zabezpieczeń w jednej lokalizacji. Uprości to przepływy pracy i doda funkcje innych usług Microsoft 365 Defender. Microsoft 365 Defender będzie miejscem do monitorowania zabezpieczeń i zarządzania nimi w ramach tożsamości, danych, urządzeń, aplikacji i infrastruktury firmy Microsoft.

Analitycy SOC będą mogli klasyfikować, badać i polować na wszystkie obciążenia Microsoft 365 Defender, w tym aplikacje w chmurze.
Alerty usługi Defender for Cloud Apps będą nadal wyświetlane w kolejce zdarzeń Microsoft 365 Defender i w kolejce alertów, ale teraz z odpowiednią zawartością na stronach alertów dostępnych w portalu Microsoft 365 Defender w ujednoliconym formacie z odpowiednimi dostosowaniami do każdego typu alertów.

Przyjrzyj się Microsoft 365 Defender pod adresem <https://security.microsoft.com>.

Dowiedz się więcej o korzyściach: [Omówienie Microsoft 365 Defender](microsoft-365-defender.md).

## <a name="quick-reference"></a>Szybkie odwołanie

Obraz i poniższa tabela zawierają listę zmian w nawigacji między Microsoft Defender for Cloud Apps i Microsoft 365 Defender.

> [!NOTE]
> Niektóre strony nie zostały jeszcze zmigrowane i powinny być dostępne w portalu usługi Defender for Cloud Apps.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender.png" alt-text="Nowe lokalizacje w portalu Microsoft 365 Defender" lightbox="../../media/defender-cloud-apps-m365-defender.png":::

| Defender for Cloud Apps | Microsoft 365 Defender |
|---------|---------|
| Pulpit nawigacyjny usługi Cloud Discover | Aplikacje w chmurze — odnajdywanie chmury > |
| Odnalezione aplikacje | karta na stronie usługi Cloud Discovery |
| Odnalezione zasoby | karta na stronie usługi Cloud Discovery |
| Adresy IP | karta na stronie usługi Cloud Discovery |
| Użytkownicy | karta na stronie usługi Cloud Discovery |
| Urządzeń | karta na stronie usługi Cloud Discovery |
| Wykaz aplikacji w chmurze |  Aplikacje w chmurze — wykaz aplikacji > Cloud |
| Tworzenie raportu migawki usługi Cloud Discovery | Na stronie Cloud Discovery w obszarze Akcje |
| Dziennik aktywności | Aplikacje w chmurze — dziennik aktywności > |
| Pliki | pozostanie w portalu usługi Defender for Cloud Apps |
| Użytkownicy i konta | Tożsamości > zasobów |
| Konfiguracja zabezpieczeń | pozostanie w portalu usługi Defender for Cloud Apps |
| Stan zabezpieczeń tożsamości | [Oceny stanu zabezpieczeń tożsamości Microsoft Defender for Identity](/defender-for-identity/isp-overview) |
| Aplikacje OAuth | Aplikacje w chmurze — > aplikacje OAuth |
| Połączone aplikacje | pozostanie w portalu usługi Defender for Cloud Apps |

> [!NOTE]
> Nowe środowisko usługi Defender for Cloud Apps w portalu Microsoft 365 Defender jest obecnie dostępne dla wszystkich użytkowników opisanych w [temacie Zarządzanie dostępem administratora](/defender-cloud-apps/manage-admins), z wyjątkiem:
> * **Administrator aplikacji/wystąpienia**, **administrator grupy użytkowników**, **administrator globalny usługi Cloud Discovery** i **administrator raportu usługi Cloud Discovery**, zgodnie z definicją w obszarze [Wbudowane role administratora w usłudze Defender for Cloud Apps](/defender-cloud-apps/manage-admins#built-in-admin-roles-in-defender-for-cloud-apps).
> * Grupy prywatności użytkowników zgodnie z definicją w [obszarze Prywatność działań](/defender-cloud-apps/activity-privacy)

## <a name="whats-changed"></a>Co się zmieniło

Dowiedz się więcej o zmianach wprowadzonych dzięki integracji usługi Defender for Cloud Apps i Microsoft 365 Defender.

### <a name="global-search"></a>Wyszukiwanie globalne

Wyszukiwanie globalne w Microsoft 365 Defender (przy użyciu paska wyszukiwania w górnej części strony) zawiera teraz dodatkową jednostkę z możliwością wyszukiwania: umożliwia wyszukiwanie połączonych aplikacji w usłudze Defender for Cloud Apps.

:::image type="content" source="../../media/global-search-apps.png" alt-text="Wyszukaj połączone aplikacje.":::

### <a name="assets-and-identities"></a>Zasoby i tożsamości

W ramach tworzenia dedykowanej sekcji **Zasobów** obejmującej całe środowisko Microsoft 365 Defender sekcja **Użytkownicy i konta** usługi Defender for Cloud Apps została zmieniona na sekcję **Tożsamości**. Nie są oczekiwane żadne zmiany funkcjonalności.

## <a name="related-information"></a>Informacje pokrewne

- [Microsoft 365 Defender](microsoft-365-defender.md)
