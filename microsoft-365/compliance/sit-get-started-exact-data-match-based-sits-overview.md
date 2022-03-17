---
title: Wprowadzenie do dokładnych typów informacji poufnych opartych na danych
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Wprowadzenie do tworzenia dokładnych typów informacji poufnych opartych na danych.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a75650484368b6ccbaf6f6d39aeead133403f5b8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526280"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Wprowadzenie do dokładnych typów informacji poufnych opartych na danych

Tworzenie i dokładne dopasowanie danych (EDM) na podstawie typu informacji poufnych (SIT) jest procesem wielofazowym. Mogą być używane w zasadach ochrony przed utratą danych, zbierania elektronicznych materiałów dowodowych i niektórych zadaniach związanych z zarządzaniem zawartością Ten artykuł zawiera konspekt przepływu pracy i linki do procedur dla poszczególnych faz.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zapoznaj się z pojęciami i terminologiią w tych artykułach:

- [Informacje o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>Wymagane licencje i uprawnienia

Aby wykonać zadania opisane w tym artykule, musisz być administratorem globalnym, administratorem Exchange Online zgodnością lub administratorem globalnym. Aby dowiedzieć się więcej o uprawnieniach DLP, zobacz [Uprawnienia](data-loss-prevention-policies.md#permissions).

Pełne informacje dotyczące [licencjonowania można znaleźć](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) w opisie usługi ochrony przed utratą danych.

## <a name="portal-links-for-your-subscription"></a>Linki portalu dla Twojej subskrypcji

|Portal|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Microsoft 365 Defender portalu|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Microsoft 365 zgodności|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Szybki przepływ pracy

![dokładne dopasowanie danych do faz przepływu pracy](..\media\swimlane_edm_process.png)


|Faza|Wymagane informacje|
|---|---|
|[Etap 1. Eksportowanie danych źródłowych w celu dokładnego dopasowania danych na podstawie typu informacji poufnych](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|- Odczytywanie dostępu do danych poufnych|
|[Etap 2. Tworzenie schematu w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|— dostęp do kreatora typów informacji poufnych w centrum administracyjne platformy Microsoft 365 </br>- dostęp do centrum administracyjne platformy Microsoft 365 [za pośrednictwem programu PowerShell & do zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell) |
|[Etap 3. Skrót i przekazanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|— Niestandardowa grupa zabezpieczeń i konto użytkownika </br>- **Skróty i przekazywanie z jednego komputera**: lokalny dostęp administratora do komputera z bezpośrednim dostępem do Internetu i hostowane agenta usługi EDM Upload usługi </br>- **Skróty** i przekazywanie z osobnych komputerów: lokalny dostęp administratora do komputera z bezpośrednim dostępem do Internetu i hostowany agent programu EDM Upload na temat przekazywania i lokalny dostęp administratora do bezpiecznego komputera na celu hostować agenta usługi Upload usługi EDM w celu skrótu tabeli źródła informacji poufnych </br>- Odczytywanie dostępu do pliku tabeli źródła informacji poufnych </br> plik schematu |
|[Etap 4. Tworzenie dokładnego dopasowania danych do typu informacji poufnych/pakietu reguł](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- Dostęp do Centrum Microsoft 365 zgodności |
|[Testowanie dokładnego dopasowania danych do typu informacji poufnych](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - Dostęp do Centrum Microsoft 365 zgodności

## <a name="see-also"></a>Zobacz też

- [Informacje o dokładnie tych typach informacji poufnych na podstawie danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Eksportowanie danych źródłowych w celu dokładnego dopasowania danych na podstawie typu informacji poufnych](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
