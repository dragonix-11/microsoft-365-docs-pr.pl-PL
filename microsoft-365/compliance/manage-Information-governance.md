---
title: Microsoft Information Governance in Microsoft 365
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
description: Wdrażanie funkcji zarządzania informacjami firmy Microsoft w celu zarządzania danymi w celu zachowania zgodności z przepisami lub wymogów prawnych.
ms.openlocfilehash: b99d073817dc0ef899f448fb6a21619b08806759
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009553"
---
# <a name="microsoft-information-governance-in-microsoft-365"></a>Microsoft Information Governance in Microsoft 365

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Korzystanie z funkcji zarządzania informacjami firmy Microsoft (czasami skróconych do funkcji MIG) do zarządzania danymi w zakresie zgodności z przepisami lub przepisami.

Z perspektywy [licencjonowania](#licensing-requirements) łączniki między zarządzaniem informacjami, zarządzaniem rekordami i łącznikami danych mogą się znacząco nakładać. Wszystkie trzy obszary obsługują przechowywanie i usuwanie danych w Microsoft 365. Łączniki są używane przez rozwiązania zgodności inne niż zarządzanie informacjami i zarządzanie rekordami. 

Skorzystaj z poniższej grafiki, aby ułatwić identyfikowanie głównych konfigurowanych składników dla tych trzech różnych rozwiązań, które mają własny węzeł w centrum zgodności:

![Główne składniki do zarządzania dla usługi Microsoft Information Goevernance.](../media/information-governance-components.png)

Chcesz chronić swoje dane? Zobacz [Microsoft Information Protection w programie Microsoft 365](information-protection.md).

## <a name="information-governance"></a>Zarządzanie informacjami

Aby zachować to, czego potrzebujesz, i usunąć to, czego nie potrzebujesz:
 
|Funkcja|Jakie problemy rozwiązuje?|Wprowadzenie|
|:------|:------------|:--------------------|:-----------------------------|
|[Zasady przechowywania dla Microsoft 365 z etykietami przechowywania dla wyjątków](retention.md) | Zachowywanie lub usuwanie zawartości za pomocą zarządzania zasadami w wiadomościach e-mail, dokumentach, Teams i Yammer wiadomościach | [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md) <br /><br /> [Tworzenie etykiet przechowywania dla wyjątków od zasad przechowywania](create-retention-labels-information-governance.md)|
|[Archiwalne skrzynki pocztowe](archive-mailboxes.md)| Zapewnia użytkownikom dodatkowe miejsce do magazynowania skrzynki pocztowej | [Włączanie archiwalnych skrzynek pocztowych](enable-archive-mailboxes.md) |
|[Nieaktywne skrzynki pocztowe](inactive-mailboxes-in-office-365.md)| Zachowywanie zawartości skrzynki pocztowej po opuszczeniu organizacji przez pracowników, aby ta zawartość była nadal dostępna dla administratorów, kierowników ds. zgodności i menedżerów rekordów | [Tworzenie nieaktywnych skrzynek pocztowych i zarządzanie nimi](create-and-manage-inactive-mailboxes.md)|
|[Usługa importowania plików PST](importing-pst-files-to-office-365.md)| Zbiorcze importowanie plików PST do skrzynek Exchange Online w celu przechowywania i wyszukiwania wiadomości e-mail w celu zachowania zgodności z przepisami lub wymogów prawnych | [Użyj przekazywania sieciowego, aby zaimportować pliki PST twojej organizacji do Microsoft 365](use-network-upload-to-import-pst-files.md)|

## <a name="records-management"></a>Zarządzanie rekordami

Zarządzanie cyklem życia elementów o wysokiej wartości w zobowiązaniach prawnych, biznesowych lub prawnych:

|Funkcja|Jakie problemy rozwiązuje?|Wprowadzenie|
|:------|:------------|---------------------|:----------------------------|
|[Zarządzanie rekordami](records-management.md)| Jedno rozwiązanie do obsługi poczty e-mail i dokumentów, które zawiera elastyczne harmonogramy przechowywania i usuwania oraz wymagania w celu obsługi pełnego cyklu życia zawartości z deklarą rekordów i ich usuwaniem w razie potrzeby przez ich usuwanie w razie potrzeby. |[Wprowadzenie do zarządzania rekordami](get-started-with-records-management.md) |

## <a name="connectors-for-third-party-data"></a>Łączniki dla danych innych firm

Rozszerzanie narzędzi do zgodności na zaimportowane i zarchiwizowane dane innych firm z platform mediów społecznościowych, platform do obsługi wiadomości błyskawicznych i platform współpracy nad dokumentami:

|Funkcja|Jakie problemy rozwiązuje?|Wprowadzenie|
|:------|:------------|:--------------------|:-----------------------------|
|[Łączniki danych](archiving-third-party-data.md)| Importowanie, archiwizowanie i stosowanie rozwiązań zgodności do danych innych firm z platform mediów społecznościowych, platform do obsługi wiadomości błyskawicznych i platform współpracy nad dokumentami| [Łączniki innych firm](archiving-third-party-data.md#third-party-data-connectors)|

## <a name="licensing-requirements"></a>Wymagania dotyczące licencjonowania

Wymagania licencyjne dotyczące zarządzania informacjami firmy Microsoft zależą od scenariuszy i funkcji, z których korzystasz, zamiast ustawiać wymagania licencjonowania dla każdej funkcji wymienionej na tej stronie. Aby poznać wymagania i opcje licencjonowania, zobacz następujące sekcje w dokumentacji Microsoft 365 [licencjonowania](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Zarządzanie informacjami](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) 
- [Zarządzanie rekordami](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) 
- [Łączniki danych](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-connectors)

Wszelkie dodatkowe wymagania licencyjne będą zawarte w instrukcjach dokumentacji. Na przykład licencjonowanie specyficzne dla zarządzania skrzynkami pocztowymi może wymagać licencji z usługi Exchange Online.

