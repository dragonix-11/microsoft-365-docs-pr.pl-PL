---
title: Zarządzanie cyklem życia danych usługi Microsoft Purview & zarządzania rekordami usługi Microsoft Purview
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
description: Zaimplementuj możliwości zarządzania cyklem życia danych usługi Microsoft Purview & zarządzania rekordami usługi Microsoft Purview, aby zarządzać danymi pod kątem zgodności lub wymagań prawnych.
ms.openlocfilehash: 2eff1aea82575a8364eb05f91652a089efbbe833
ms.sourcegitcommit: f723ebbc56db8013598a88b0d7f13214d9d3eb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2022
ms.locfileid: "65294739"
---
# <a name="govern-your-data-with-microsoft-purview"></a>Zarządzanie danymi za pomocą usługi Microsoft Purview

>*[Microsoft 365 wskazówki dotyczące licencjonowania dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Skorzystaj z możliwości **zarządzania cyklem życia danych usługi Microsoft Purview** (dawniej Microsoft Information Governance) i **zarządzania rekordami usługi Microsoft Purview** , aby zarządzać danymi pod kątem zgodności lub wymagań prawnych.

> [!TIP]
> Chcesz mapować dane i zarządzać nimi w całej infrastrukturze danych, w tym w wielu chmurach i oprogramowaniu jako usłudze (SaaS)? Użyj usług [Microsoft Purview Data Map, Microsoft Purview Data Catalog i Microsoft Purview Data Estate Szczegółowe informacje](/azure/purview/overview).

Z [punktu widzenia licencjonowania](#licensing-requirements) zarządzanie cyklem życia danych i zarządzanie rekordami może znacznie się nakładać. Oba rozwiązania obsługują przechowywanie i usuwanie danych dla Microsoft 365 aplikacji i usług.

Poniższa grafika ułatwia zidentyfikowanie głównych składników konfigurowalnych dla tych rozwiązań, z których każdy ma własny obszar konfiguracji w portalu zgodności usługi Microsoft Purview:

![Główne składniki do konfigurowania i używania do zarządzania danymi za pomocą usługi Microsoft Purview.](../media/govern-your-data.png)

W poniższych sekcjach szczegółowo opisano główne możliwości każdego rozwiązania z linkami, aby dowiedzieć się więcej. Jeśli jednak szukasz wdrożenia z przewodnikiem, zobacz [Wdrażanie rozwiązania do zarządzania danymi za pomocą usługi Microsoft Purview](data-governance-solution.md).

Szukasz uzupełniających możliwości ochrony danych? Zobacz [Ochrona danych za pomocą usługi Microsoft Purview](information-protection.md).

## <a name="microsoft-purview-data-lifecycle-management"></a>Zarządzanie cyklem życia danych usługi Microsoft Purview

Aby zachować to, czego potrzebujesz, i usunąć to, czego nie potrzebujesz:
 
|Możliwości|Jakie problemy rozwiązuje?|
|:------|:------------|:----------------|
|[Zasady przechowywania dla obciążeń Microsoft 365 z etykietami przechowywania dla wyjątków](retention.md) | Umożliwia zachowywanie lub usuwanie zawartości za pomocą zarządzania zasadami dla wiadomości e-mail, dokumentów, Teams i wiadomości Yammer. |
|[Nieaktywne skrzynki pocztowe](inactive-mailboxes-in-office-365.md)| Umożliwia zachowanie zawartości skrzynki pocztowej po opuszczeniu organizacji przez pracowników, dzięki czemu ta zawartość pozostanie dostępna dla administratorów, urzędników ds. zgodności i menedżerów rekordów. |
|[Archiwizowanie skrzynek pocztowych](archive-mailboxes.md)| Zapewnia dodatkowe miejsce do magazynowania skrzynki pocztowej dla użytkowników.|
|[Importowanie usługi dla plików PST](importing-pst-files-to-office-365.md)| Obsługuje zbiorcze importowanie plików PST do Exchange Online skrzynek pocztowych w celu przechowywania i wyszukiwania wiadomości e-mail pod kątem zgodności lub wymagań prawnych. |

Chcesz dowiedzieć się więcej? Zobacz [Informacje o zarządzaniu cyklem życia danych](data-lifecycle-management.md).

Chcesz rozpocząć korzystanie z niektórych lub wszystkich tych funkcji? Zobacz [Wprowadzenie z zarządzaniem cyklem życia danych](get-started-with-data-lifecycle-management.md).


## <a name="microsoft-purview-records-management"></a>Zarządzanie rekordami usługi Microsoft Purview

Zarządzanie elementami o wysokiej wartości dla wymagań biznesowych, prawnych lub regulacyjnych dotyczących prowadzenia dokumentacji:

|Możliwości|Jakie problemy rozwiązuje?|
|:---------|:---------------------------|
|[Plan plików](file-plan-manager.md)| Umożliwia interaktywne tworzenie etykiet przechowywania lub zbiorcze importowanie i eksportowanie do analizy. Etykiety obsługują dodatkowe informacje administracyjne (opcjonalnie), które ułatwiają identyfikowanie i śledzenie wymagań biznesowych lub regulacyjnych. |
|[Etykiety przechowywania dla poszczególnych elementów, zasady przechowywania w razie potrzeby przechowywania według planu bazowego](retention.md)| Etykiety obsługują elastyczne harmonogramy przechowywania i usuwania, które można stosować ręcznie lub automatycznie z deklaracją rekordów w razie potrzeby. |
|[Przegląd dyspozycji i dowód dyspozycji](disposition.md)| Ręczne przeglądanie zawartości przed jej trwałym usunięciem z potwierdzeniem dyspozycji rekordów.|

Chcesz dowiedzieć się więcej? Zobacz [Informacje o zarządzaniu rekordami](records-management.md).

Chcesz rozpocząć korzystanie z niektórych lub wszystkich tych funkcji? Zobacz [Wprowadzenie z zarządzaniem rekordami](get-started-with-records-management.md).


## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Aby zrozumieć wymagania i opcje licencjonowania, zapoznaj się z następującymi sekcjami w [dokumentacji licencjonowania Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Zarządzanie cyklem życia danych usługi Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management)
- [Zarządzanie rekordami usługi Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management)

Wszelkie dodatkowe wymagania licencyjne zostaną uwzględnione w instrukcjach dokumentacji. Na przykład licencjonowanie specyficzne dla zarządzania skrzynkami pocztowymi może wymagać licencji od Exchange Online.