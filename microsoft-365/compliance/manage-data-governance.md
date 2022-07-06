---
title: zarządzanie cyklem życia danych Microsoft Purview & Zarządzanie rekordami w Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
recommendations: false
description: Zaimplementuj możliwości z zarządzanie cyklem życia danych Microsoft Purview & Zarządzanie rekordami w Microsoft Purview, aby zarządzać danymi pod kątem zgodności lub wymagań prawnych.
ms.openlocfilehash: 7578aad4bdbb44bf0937a58343fc05462449688f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635990"
---
# <a name="govern-your-data-with-microsoft-purview"></a>Zarządzanie danymi za pomocą usługi Microsoft Purview

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Skorzystaj z możliwości **zarządzanie cyklem życia danych Microsoft Purview** (dawniej Microsoft Information Governance) i **Zarządzanie rekordami w Microsoft Purview**, aby zarządzać danymi pod kątem zgodności lub wymagań prawnych.

> [!TIP]
> Chcesz mapować dane i zarządzać nimi w całej infrastrukturze danych, w tym w wielu chmurach i oprogramowaniu jako usłudze (SaaS)? Użyj [Mapa danych w Microsoft Purview, Wykaz danych w Microsoft Purview i Analiza obszaru danych w Microsoft Purview](/azure/purview/overview).

Z [punktu widzenia licencjonowania](#licensing-requirements) zarządzanie cyklem życia danych i zarządzanie rekordami może znacznie się nakładać. Oba rozwiązania obsługują przechowywanie i usuwanie danych dla aplikacji i usług platformy Microsoft 365.

Poniższa grafika ułatwia zidentyfikowanie głównych składników konfigurowalnych dla tych rozwiązań, z których każdy ma swój własny obszar konfiguracji w portal zgodności Microsoft Purview:

![Główne składniki do konfigurowania i używania do zarządzania danymi za pomocą usługi Microsoft Purview.](../media/govern-your-data.png)

W poniższych sekcjach szczegółowo opisano główne możliwości każdego rozwiązania z linkami, aby dowiedzieć się więcej. Jeśli jednak szukasz wdrożenia z przewodnikiem, zobacz [Wdrażanie rozwiązania do zarządzania danymi za pomocą usługi Microsoft Purview](data-governance-solution.md).

Szukasz uzupełniających możliwości ochrony danych? Zobacz [Ochrona danych za pomocą usługi Microsoft Purview](information-protection.md).

## <a name="microsoft-purview-data-lifecycle-management"></a>Zarządzanie cyklem życia danych Microsoft Purview

Aby zachować to, czego potrzebujesz, i usunąć to, czego nie potrzebujesz:
 
|Możliwości|Jakie problemy rozwiązuje?|
|:------|:------------|:----------------|
|[Zasady przechowywania dla obciążeń platformy Microsoft 365 z etykietami przechowywania dla wyjątków](retention.md) | Umożliwia zachowywanie lub usuwanie zawartości za pomocą zarządzania zasadami dla wiadomości e-mail, dokumentów, aplikacji Teams i wiadomości yammer. |
|[Nieaktywne skrzynki pocztowe](inactive-mailboxes-in-office-365.md)| Umożliwia zachowanie zawartości skrzynki pocztowej po opuszczeniu organizacji przez pracowników, dzięki czemu ta zawartość pozostanie dostępna dla administratorów, urzędników ds. zgodności i menedżerów rekordów. |
|[Archiwizowanie skrzynek pocztowych](archive-mailboxes.md)| Zapewnia dodatkowe miejsce do magazynowania skrzynki pocztowej dla użytkowników.|
|[Importowanie usługi dla plików PST](importing-pst-files-to-office-365.md)| Obsługuje zbiorcze importowanie plików PST do Exchange Online skrzynek pocztowych w celu przechowywania i wyszukiwania wiadomości e-mail pod kątem zgodności lub wymagań prawnych. |

Chcesz dowiedzieć się więcej? Zobacz [Informacje o zarządzaniu cyklem życia danych](data-lifecycle-management.md).

Chcesz rozpocząć korzystanie z niektórych lub wszystkich tych funkcji? Zobacz [Wprowadzenie do zarządzania cyklem życia danych](get-started-with-data-lifecycle-management.md).


## <a name="microsoft-purview-records-management"></a>Zarządzanie rekordami w Microsoft Purview

Zarządzanie elementami o wysokiej wartości dla wymagań biznesowych, prawnych lub regulacyjnych dotyczących prowadzenia dokumentacji:

|Możliwości|Jakie problemy rozwiązuje?|
|:---------|:---------------------------|
|[Plan plików](file-plan-manager.md)| Umożliwia interaktywne tworzenie etykiet przechowywania lub zbiorcze importowanie i eksportowanie do analizy. Etykiety obsługują dodatkowe informacje administracyjne (opcjonalnie), które ułatwiają identyfikowanie i śledzenie wymagań biznesowych lub regulacyjnych. |
|[Etykiety przechowywania dla poszczególnych elementów, zasady przechowywania w razie potrzeby przechowywania według planu bazowego](retention.md)| Etykiety obsługują elastyczne harmonogramy przechowywania i usuwania, które można stosować ręcznie lub automatycznie z deklaracją rekordów w razie potrzeby. |
|[Przegląd dyspozycji i dowód dyspozycji](disposition.md)| Ręczne przeglądanie zawartości przed jej trwałym usunięciem z potwierdzeniem dyspozycji rekordów.|

Chcesz dowiedzieć się więcej? Zobacz [Informacje o zarządzaniu rekordami](records-management.md).

Chcesz rozpocząć korzystanie z niektórych lub wszystkich tych funkcji? Zobacz [Wprowadzenie do zarządzania rekordami](get-started-with-records-management.md).


## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Aby zrozumieć wymagania i opcje licencjonowania, zapoznaj się z następującymi sekcjami w [dokumentacji licencjonowania platformy Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Zarządzanie cyklem życia danych Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management)
- [Zarządzanie rekordami w Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management)

Wszelkie dodatkowe wymagania licencyjne zostaną uwzględnione w instrukcjach dokumentacji. Na przykład licencjonowanie specyficzne dla zarządzania skrzynkami pocztowymi może wymagać licencji od Exchange Online.