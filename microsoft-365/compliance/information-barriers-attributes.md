---
title: Atrybuty barier informacyjnych
description: Ten artykuł zawiera informacje o atrybutach konta Azure Active Directory, które mogą być służące do definiowania segmentów bariery informacyjnej.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 33143e85bf17a707ade6dd0d6d0c66886fd85373
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985232"
---
# <a name="information-barriers-attributes"></a>Atrybuty barier informacyjnych

Niektórych atrybutów w Azure Active Directory można używać do segmentacji użytkowników. Po zdefiniowanym segmentach można ich używać jako filtrów w celu filtrowania barier informacyjnych. Można na przykład użyć funkcji Dział  do zdefiniowania segmentów użytkowników według działów w organizacji (przy założeniu, że żaden pracownik nie pracuje jednocześnie dla dwóch działów).

W tym artykule opisano sposób używania atrybutów z barierami informacyjnymi oraz przedstawiono listę atrybutów, których można użyć. Aby dowiedzieć się więcej o barierach informacyjnych, zobacz następujące zasoby:

- [Bariery informacyjne](information-barriers.md)
- [Definiowanie zasad dla barier informacyjnych w Microsoft Teams](information-barriers-policies.md)
- [Edytowanie (lub usuwanie) zasad bariery informacyjnej](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-information-barrier-policies"></a>Jak korzystać z atrybutów w zasadach bariery informacyjnej

Atrybuty wymienione w tym artykule mogą służyć do definiowania lub edytowania segmentów użytkowników. Zdefiniowane segmenty służą jako parametry (określane jako *wartości FiltrUgrupy* Użytkowników) w zasadach [bariery informacyjnej](information-barriers-policies.md).

1. Określ atrybut, którego chcesz użyć do zdefiniowania segmentów. (Zobacz [sekcję Reference](#reference) (Odwołanie) w tym artykule).

2. Upewnij się, że konta użytkowników mają wypełnione wartości atrybutów wybranych w kroku 1. Wyświetl szczegóły konta użytkownika i w razie potrzeby edytuj konta użytkowników, aby uwzględnić wartości atrybutów. 

    - Aby edytować wiele kont (lub edytować jedno konto za pomocą programu PowerShell), zobacz Konfigurowanie właściwości konta użytkownika za [pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - Aby edytować jedno konto, zobacz Dodawanie [lub aktualizowanie informacji o profilu użytkownika przy](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) użyciu Azure Active Directory.

3. [Segmenty można definiować przy użyciu programu PowerShell](information-barriers-policies.md#define-segments-using-powershell), podobnie jak w poniższych przykładach:

    |**Przykład**|**Polecenie cmdlet**|
    |:----------|:---------|
    | Definiowanie segmentu o nazwie Segment1 przy użyciu atrybutu Department | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | Definiowanie segmentu o nazwie SegmentA przy użyciu atrybutu MemberOf (załóżmy, że ten atrybut zawiera nazwy grup, na przykład "BlueGroup") | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | Definiowanie segmentu o nazwie Day Jak przy użyciu atrybutu ExtensionAttribute1 (załóżmy, że ten atrybut zawiera tytuły zadań, na przykład "Day Jakasło") | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Po zdefiniowaniu segmentów należy użyć tego samego atrybutu dla wszystkich segmentów. Jeśli na przykład dla niektórych segmentów zdefiniowano segmenty za pomocą narzędzia *Dział*, zdefiniuj wszystkie segmenty za pomocą funkcji *Dział*. Nie definiuj niektórych segmentów przy *użyciu funkcji Department (Dział* ), a innych za pomocą *funkcji MemberOf (Członek*). Upewnij się, że segmenty nie nakładają się; każdy użytkownik powinien mieć przypisany dokładnie jeden segment.

## <a name="reference"></a>Odwołanie

W poniższej tabeli wymieniono atrybuty, których można używać z barierami informacyjnymi.

|**Azure Active Directory właściwości<br/>(nazwa wyświetlana LDAP)**|**Exchange nazwy właściwości**|
|:---------------------------------------------------------------|:-------------------------|
| Co | Co |
| Company | Company |
| Department | Department |
| ExtensionAttribute1 | CustomAttribute1 |
| ExtensionAttribute2 | CustomAttribute2 |
| ExtensionAttribute3 | CustomAttribute3 |
| ExtensionAttribute4 | CustomAttribute4 |
| ExtensionAttribute5 | CustomAttribute5 |
| ExtensionAttribute6 | CustomAttribute6 |
| ExtensionAttribute7 | CustomAttribute7 |
| ExtensionAttribute8 | CustomAttribute8 |
| ExtensionAttribute9 | CustomAttribute9 |
| ExtensionAttribute10 | CustomAttribute10 |
| ExtensionAttribute11 | CustomAttribute11 |
| ExtensionAttribute12 | CustomAttribute12 |
| ExtensionAttribute13 | CustomAttribute13 |
| ExtensionAttribute14 | CustomAttribute14 |
| ExtensionAttribute15 | CustomAttribute15 |
| MSExchExtensionCustomAttribute1 | ExtensionCustomAttribute1 |
| MSExchExtensionCustomAttribute2 | ExtensionCustomAttribute2 |
| MSExchExtensionCustomAttribute3 | ExtensionCustomAttribute3 |
| MSExchExtensionCustomAttribute4 | ExtensionCustomAttribute4 |
| MSExchExtensionCustomAttribute5 | ExtensionCustomAttribute5 |
| MailNickname | Alias |
| PhysicalDeliveryOfficeName | Pakiet Office |
| Kod Pocztowy | Kod Pocztowy |
| ProxyAddresses | EmailAddresses |
| StreetAddress | StreetAddress |
| TargetAddress | ExternalEmailAddress |
| Lokalizacja użytkowania | Lokalizacja użytkowania |
| UserPrincipalName (Nazwa użytkownika) | UserPrincipalName (Nazwa użytkownika) |
| Poczta | WindowsEmailAddress |
| Opis | Opis |
| MemberOf | MemberOfGroup |

## <a name="resources"></a>Zasoby

- [Definiowanie zasad dla barier informacyjnych w Microsoft Teams](information-barriers-policies.md)
- [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Bariery informacyjne](information-barriers.md)