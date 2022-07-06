---
title: Atrybuty barier informacyjnych
description: Ten artykuł zawiera dokumentację atrybutów konta użytkownika usługi Azure Active Directory, których można użyć do definiowania segmentów barier informacyjnych.
keywords: Microsoft 365, Microsoft Purview, zgodność, bariery informacyjne
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
ms.openlocfilehash: a1549a0cb3bf03056b37a75175c3b24416bec7b5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639781"
---
# <a name="information-barriers-attributes"></a>Atrybuty barier informacyjnych

Niektóre atrybuty w usłudze Azure Active Directory mogą służyć do segmentacji użytkowników w barierach informacyjnych (IB). Po zdefiniowaniu segmentów te segmenty mogą być używane jako filtry dla zasad IB. Na przykład możesz użyć **działu** , aby zdefiniować segmenty użytkowników według działu w organizacji (przy założeniu, że żaden jeden pracownik nie pracuje w tym samym czasie dla dwóch działów).

W tym artykule opisano sposób używania atrybutów z barierami informacyjnymi i przedstawiono listę atrybutów, których można użyć. Aby dowiedzieć się więcej o barierach informacyjnych, zobacz następujące zasoby:

- [Bariery informacyjne](information-barriers.md)
- [Definiowanie zasad dla barier informacyjnych w usłudze Microsoft Teams](information-barriers-policies.md)
- [Edytowanie (lub usuwanie) zasad IB](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-ib-policies"></a>Jak używać atrybutów w zasadach IB

Atrybuty wymienione w tym artykule mogą służyć do definiowania lub edytowania segmentów użytkowników. Zdefiniowane segmenty służą jako parametry (nazywane wartościami *UserGroupFilter* ) w [zasadach IB](information-barriers-policies.md).

1. Określ atrybut, którego chcesz użyć do definiowania segmentów. (Zobacz sekcję [Dokumentacja](#reference) w tym artykule).

2. Upewnij się, że na kontach użytkowników są wypełnione wartości atrybutów wybranych w kroku 1. Wyświetl szczegóły konta użytkownika i w razie potrzeby edytuj konta użytkowników, aby uwzględnić wartości atrybutów. 

    - Aby edytować wiele kont (lub edytować pojedyncze konto przy użyciu programu PowerShell), zobacz [Konfigurowanie właściwości konta użytkownika za pomocą Office 365 programu PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - Aby edytować pojedyncze konto, zobacz [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu usługi Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [Definiowanie segmentów przy użyciu programu PowerShell](information-barriers-policies.md#define-segments-using-powershell), podobnie jak w następujących przykładach:

    |**Przykład**|**Polecenie cmdlet**|
    |:----------|:---------|
    | Definiowanie segmentu o nazwie Segment1 przy użyciu atrybutu Dział | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | Zdefiniuj segment o nazwie SegmentA przy użyciu atrybutu MemberOf (załóżmy, że ten atrybut zawiera nazwy grup, takie jak "BlueGroup") | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | Definiowanie segmentu o nazwie DayTraders przy użyciu elementu ExtensionAttribute1 (załóżmy, że ten atrybut zawiera tytuły zadań, takie jak "DayTrader") | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > Podczas definiowania segmentów użyj tego samego atrybutu dla wszystkich segmentów. Jeśli na przykład zdefiniujesz niektóre segmenty przy użyciu *działu*, zdefiniuj wszystkie segmenty przy użyciu *działu*. Nie należy definiować niektórych segmentów przy użyciu *działu* , a inne przy użyciu *elementu MemberOf*. Upewnij się, że segmenty nie nakładają się na siebie; każdy użytkownik powinien zostać przypisany do dokładnie jednego segmentu.

## <a name="reference"></a>Odwołanie

W poniższej tabeli wymieniono atrybuty, których można użyć z barierami informacyjnymi.

|**Nazwa<br/> właściwości usługi Azure Active Directory (nazwa wyświetlana LDAP)**|**Nazwa właściwości programu Exchange**|
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
| Postalcode | Postalcode |
| Proxyaddresses | EmailAddresses |
| Streetaddress | Streetaddress |
| Targetaddress | Externalemailaddress |
| UsageLocation | UsageLocation |
| Userprincipalname | Userprincipalname |
| Poczty | WindowsEmailAddress |
| Opis | Opis |
| Memberof | MemberOfGroup |

## <a name="resources"></a>Zasoby

- [Definiowanie zasad dla barier informacyjnych w usłudze Microsoft Teams](information-barriers-policies.md)
- [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [Bariery informacyjne](information-barriers.md)
