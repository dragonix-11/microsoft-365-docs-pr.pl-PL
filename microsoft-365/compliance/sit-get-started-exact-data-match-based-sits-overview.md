---
title: Wprowadzenie do dokładnych typów informacji poufnych opartych na dopasowaniu danych
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
description: Wprowadzenie tworzenie dokładnych typów informacji poufnych zgodnych z danymi.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0f221ba0521a50f484bfb9a8d5030e33b495c495
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759750"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>Wprowadzenie do dokładnych typów informacji poufnych opartych na dopasowaniu danych

Tworzenie i udostępnianie dokładnego typu informacji poufnych (SIT) opartego na danych (EDM) jest procesem wielofazowym. Mogą być używane w zasadach zapobiegania utracie danych, zbierania elektronicznych materiałów dowodowych i niektórych zadaniach związanych z zarządzaniem zawartością W tym artykule opisano przepływ pracy i linki do procedur dla każdej fazy

## <a name="before-you-begin"></a>Przed rozpoczęciem

Zapoznaj się z pojęciami i terminologią w następujących artykułach:

- [Dowiedz się więcej o typach informacji poufnych](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>Wymagane licencje i uprawnienia

Aby wykonywać zadania opisane w tym artykule, musisz być administratorem globalnym, administratorem zgodności lub administratorem Exchange Online. Aby dowiedzieć się więcej o uprawnieniach DLP, zobacz [Uprawnienia](data-loss-prevention-policies.md#permissions).

Zobacz [opis usługi ochrony przed utratą danych](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) , aby uzyskać pełne informacje o licencjonowaniu

## <a name="portal-links-for-your-subscription"></a>Linki portalu dla subskrypcji

|Portal|World Wide/GCC|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|portal Microsoft 365 Defender|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Centrum zgodności Microsoft 365|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>Przepływ pracy w skrócie

![dokładne fazy przepływu pracy dopasowania danych](..\media\swimlane_edm_process.png)


|Fazy|Co jest potrzebne|
|---|---|
|[Faza 1. Eksportowanie danych źródłowych pod kątem dokładnego typu informacji poufnych zgodnych z danymi](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|— Odczyt dostępu do poufnych danych|
|[Faza 2. Tworzenie schematu dla dokładnych typów informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|— Dostęp do kreatora typów informacji poufnych w Centrum administracyjne platformy Microsoft 365 </br>— dostęp do [Centrum administracyjne platformy Microsoft 365 za pośrednictwem programu PowerShell & Security & Compliance](/powershell/exchange/connect-to-scc-powershell) |
|[Faza 3. Skrót i przekazywanie tabeli źródła informacji poufnych w celu dokładnego dopasowania danych do typów informacji poufnych](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|— Niestandardowa grupa zabezpieczeń i konto użytkownika </br>- **Skrót i przekazywanie z jednego komputera**: dostęp administratora lokalnego do komputera z bezpośrednim dostępem do Internetu i hostowanie agenta Upload EDM </br>- **Skrót i przekazywanie z oddzielnych komputerów**: dostęp administratora lokalnego do komputera z bezpośrednim dostępem do Internetu i hostowanie agenta Upload EDM na potrzeby przekazywania i dostępu administratora lokalnego do bezpiecznego komputera w celu hostowania agenta Upload EDM w celu skrótu tabeli źródła informacji poufnych </br>— Odczytywanie dostępu do pliku tabeli źródła informacji poufnych </br> plik schematu |
|[Faza 4. Tworzenie dokładnego dopasowania danych do informacji poufnych typu/pakietu reguł](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |— Dostęp do Centrum zgodności Microsoft 365 |
|[Testuj dokładny typ informacji poufnych oparty na dopasowaniu danych](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| — Dostęp do Centrum zgodności Microsoft 365

## <a name="see-also"></a>Zobacz też

- [Dowiedz się więcej o dokładnych typach informacji poufnych opartych na dopasowaniu danych](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Eksportuj dane źródłowe dla dokładnego typu informacji poufnych opartych na dopasowaniu danych](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
