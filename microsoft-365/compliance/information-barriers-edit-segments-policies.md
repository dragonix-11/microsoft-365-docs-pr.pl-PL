---
title: Zarządzanie zasadami barier informacyjnych
description: Dowiedz się, jak edytować lub usuwać zasady dotyczące barier informacyjnych.
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
ms.openlocfilehash: eaaa98233a839f41c008052ab91c5c0f45f8eb13
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014185"
---
# <a name="manage-information-barriers-policies"></a>Zarządzanie zasadami barier informacyjnych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Po [zdefiniowaniu zasad barier informacyjnych](information-barriers-policies.md) może być konieczne wprowadzenie zmian w tych zasadach lub segmentach użytkowników w ramach [rozwiązywania problemów](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) lub regularnej konserwacji.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|**Akcja**|**Opis**|
|:---------|:--------------|
| [Edytowanie atrybutów konta użytkownika](#edit-user-account-attributes) | Wypełnij atrybuty w Azure Active Directory, które mogą służyć do definiowania segmentów. <br> Edytuj atrybuty konta użytkownika, gdy użytkownicy nie są uwzględniane w segmentach, w których powinni być, aby zmienić segmenty, w których znajdują się użytkownicy, lub zdefiniować segmenty przy użyciu różnych atrybutów. |
| [Edytowanie segmentu](#edit-a-segment) | Edytuj segmenty, gdy chcesz zmienić sposób definiowania segmentu. <br> Na przykład możesz mieć pierwotnie zdefiniowane segmenty przy użyciu *działu* , a teraz chcesz użyć innego atrybutu, takiego jak *MemberOf*. |
| [Edytowanie zasad](#edit-a-policy) | Edytuj zasady barier informacyjnych, gdy chcesz zmienić sposób działania zasad.<br> Na przykład zamiast blokować komunikację między dwoma segmentami, możesz zdecydować, że chcesz zezwolić na komunikację tylko między niektórymi segmentami. |
| [Ustawianie stanu nieaktywnych zasad](#set-a-policy-to-inactive-status) |Ustaw zasady na stan nieaktywny, jeśli chcesz wprowadzić zmiany w zasadach lub jeśli nie chcesz, aby zasady obowiązywać. |
| [Usuwanie zasad](#remove-a-policy) | Usuń zasady barier informacyjnych, gdy nie potrzebujesz już określonych zasad. |
| [Usuwanie segmentu](#remove-a-segment) | Usuń segment barier informacyjnych, gdy nie potrzebujesz już określonego segmentu. |
| [Usuwanie zasad i segmentu](#remove-a-policy-and-segment) | Jednocześnie usuń zasady barier informacyjnych i segment. |
| [Zatrzymywanie aplikacji zasad](#stop-a-policy-application) | Wykonaj tę akcję, jeśli chcesz zatrzymać proces stosowania zasad barier informacyjnych. <br> Zatrzymywanie aplikacji zasad nie jest natychmiastowe i nie cofa zasad, które są już stosowane do użytkowników. |
| [Definiowanie zasad dla barier informacyjnych](information-barriers-policies.md) | Zdefiniuj zasady barier informacyjnych, jeśli nie masz jeszcze takich zasad i musisz ograniczyć lub ograniczyć komunikację między określonymi grupami użytkowników. |
| [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Zapoznaj się z tym artykułem, gdy wystąpią nieoczekiwane problemy z barierami informacyjnymi. |

>[!IMPORTANT]
>Aby wykonać zadania opisane w tym artykule, musisz mieć przypisaną odpowiednią rolę, taką jak jedna z następujących:<br>— administrator globalny Microsoft 365 Enterprise<br>— Administrator globalny<br>— Administrator zgodności<br>— Zarządzanie zgodnością IB (jest to nowa rola!)<br><br>Aby dowiedzieć się więcej o wymaganiach wstępnych dotyczących barier informacyjnych, zobacz [Wymagania wstępne (zasady dotyczące barier informacyjnych).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> Upewnij się, że [nawiązaliśmy połączenie z programem PowerShell security & Compliance](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Edytowanie atrybutów konta użytkownika

Ta procedura służy do edytowania atrybutów używanych do segmentowania użytkowników. Jeśli na przykład używasz atrybutu Dział i co najmniej jedno konto użytkownika nie ma obecnie żadnych wartości wymienionych dla działu, musisz edytować te konta użytkowników, aby uwzględnić informacje o dziale. Atrybuty konta użytkownika są używane do definiowania segmentów, aby można było przypisać zasady barier informacyjnych.

1. Aby wyświetlić szczegóły dla określonego konta użytkownika, takie jak wartości atrybutów i przypisane segmenty, użyj polecenia cmdlet **Get-InformationBarrierRecipientStatus** z parametrami tożsamości.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, takiej jak nazwa, alias, nazwa wyróżniająca, nazwa domeny kanonicznej, adres e-mail lub identyfikator GUID. <br> (Możesz również użyć tego polecenia cmdlet dla jednego użytkownika: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> W tym przykładzie odwołujemy się do dwóch kont użytkowników w Office 365: *meganb* dla *Megan* i *alexw* dla *Alex*. |

2. Określanie atrybutu, który chcesz edytować dla profilów konta użytkownika. Aby uzyskać więcej informacji, zobacz [Atrybuty zasad barier informacyjnych](information-barriers-attributes.md).

3. Edytuj co najmniej jedno konto użytkownika, aby uwzględnić wartości atrybutu wybranego w poprzednim kroku. Aby wykonać tę akcję, użyj jednej z następujących procedur:

    - Aby edytować pojedyncze konto, zobacz [Dodawanie lub aktualizowanie informacji o profilu użytkownika przy użyciu Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - Aby edytować wiele kont (lub edytować pojedyncze konto przy użyciu programu PowerShell), zobacz [Konfigurowanie właściwości konta użytkownika za pomocą Office 365 programu PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Edytowanie segmentu

Użyj tej procedury, aby edytować definicję segmentu użytkownika. Na przykład możesz zmienić nazwę segmentu lub filtr używany do określania, kto jest uwzględniony w segmencie.

1. Aby wyświetlić wszystkie istniejące segmenty, użyj polecenia cmdlet **Get-OrganizationSegment** .

    Składni: `Get-OrganizationSegment`

    Zostanie wyświetlona lista segmentów i szczegółów dla każdego z nich, takich jak typ segmentu, jego wartość UserGroupFilter, kto ją utworzył lub ostatnio zmodyfikował, identyfikator GUID itd.

    > [!TIP]
    > Drukuj lub zapisz listę segmentów do późniejszego odwołania. Jeśli na przykład chcesz edytować segment, musisz znać jego nazwę lub zidentyfikować wartość (jest ona używana z parametrem Identity).

2. Aby edytować segment, użyj polecenia cmdlet **Set-OrganizationSegment** z parametrem **Identity** i odpowiednimi szczegółami.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> W tym przykładzie zaktualizowaliśmy nazwę działu do *hrdept* dla segmentu o identyfikator GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. Po zakończeniu edytowania segmentów dla organizacji można [zdefiniować](information-barriers-policies.md#step-3-create-ib-policies) lub [edytować](#edit-a-policy) zasady barier informacyjnych.

## <a name="edit-a-policy"></a>Edytowanie zasad

1. Aby wyświetlić listę bieżących zasad barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składni: `Get-InformationBarrierPolicy`

    Na liście wyników zidentyfikuj zasady, które chcesz zmienić. Zanotuj identyfikator GUID i nazwę zasad.

2. Użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem **Identity** i określ zmiany, które chcesz wprowadzić.

    Przykład: Załóżmy, że zdefiniowano zasady blokujące komunikację segmentu *Badania* z segmentami *Sales* and *Marketing* . Zasady zostały zdefiniowane przy użyciu tego polecenia cmdlet: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Załóżmy, że chcemy go zmienić, aby osoby w segmencie *Badania* mogły komunikować się tylko z osobami w segmencie *kadr* . Aby wprowadzić tę zmianę, użyjemy tego polecenia cmdlet: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    W tym przykładzie zmieniliśmy *pozycję SegmentsBlocked* na *SegmentsAllowed* i określiliśmy segment *HR* .

3. Po zakończeniu edytowania zasad upewnij się, że zostały zastosowane zmiany. (Zobacz [Stosowanie zasad barier informacyjnych](information-barriers-policies.md#step-4-apply-ib-policies)).

## <a name="set-a-policy-to-inactive-status"></a>Ustawianie stanu nieaktywnych zasad

1. Aby wyświetlić listę bieżących zasad barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składni: `Get-InformationBarrierPolicy`

    Na liście wyników zidentyfikuj zasady, które chcesz zmienić (lub usunąć). Zanotuj identyfikator GUID i nazwę zasad.

2. Aby ustawić stan zasad na nieaktywny, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem *Identity* i parametrem *State* ustawionym na *Nieaktywne*.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> W tym przykładzie zasady barier informacyjnych z identyfikatorem GUID *43c37853-ea10-4b90-a23d-ab8c9377247* są ustawione na stan nieaktywny. |

3. Aby zastosować zmiany, użyj polecenia cmdlet **Start-InformationBarrierPoliciesApplication** .

    Składni: `Start-InformationBarrierPoliciesApplication`

    Zmiany są stosowane przez użytkownika w organizacji. Jeśli organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

4. W tym momencie jedna lub więcej zasad barier informacyjnych jest ustawionych na stan nieaktywny. W tym miejscu możesz wykonać dowolną z następujących akcji:

    - Zachowaj stan tak, jak jest (ustawienie zasad stanu nieaktywnego nie ma wpływu na użytkowników)
    - [Edytowanie zasad](#edit-a-policy) 
    - [Usuwanie zasad](#remove-a-policy)

## <a name="remove-a-policy"></a>Usuwanie zasad

1. Aby wyświetlić listę bieżących zasad barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składni: `Get-InformationBarrierPolicy`

    Na liście wyników zidentyfikuj zasady, które chcesz usunąć. Zanotuj identyfikator GUID i nazwę zasad. 

2. Upewnij się, że zasady są ustawione na stan nieaktywny. Aby ustawić stan zasad na nieaktywny, użyj polecenia cmdlet Set-InformationBarrierPolicy z parametrem Identity i parametrem State ustawionym na Nieaktywne.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> W tym przykładzie ustawiliśmy zasady barier informacyjnych z identyfikatorem GUID *43c37853-ea10-4b90-a23d-ab8c9377247* jako stan nieaktywny. |

3. Aby zastosować zmiany w zasadach, użyj polecenia cmdlet **Start-InformationBarrierPoliciesApplication** .

    Składni: `Start-InformationBarrierPoliciesApplication`

    Zmiany są stosowane przez użytkownika w organizacji. Jeśli organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

4. Użyj polecenia cmdlet **Remove-InformationBarrierPolicy** z parametrem Identity.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> W tym przykładzie usuwamy zasady z identyfikatorem GUID *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    Po wyświetleniu monitu potwierdź zmianę.

## <a name="remove-a-segment"></a>Usuwanie segmentu

1. Aby wyświetlić wszystkie istniejące segmenty, użyj polecenia cmdlet **Get-OrganizationSegment** .

    Składni: `Get-OrganizationSegment`

    Zostanie wyświetlona lista segmentów i szczegółów dla każdego z nich, takich jak typ segmentu, jego wartość UserGroupFilter, kto ją utworzył lub ostatnio zmodyfikował, identyfikator GUID itd.

    >[!TIP]
    >Drukuj lub zapisz listę segmentów do późniejszego odwołania. Jeśli na przykład chcesz edytować segment, musisz znać jego nazwę lub zidentyfikować wartość (jest ona używana z parametrem Identity).

2. Zidentyfikuj segment do usunięcia i upewnij się, że zasady IB skojarzone z segmentem zostały usunięte. Aby uzyskać szczegółowe informacje [, zobacz Procedurę usuwania zasad](#remove-a-policy) .

3. Edytuj segment, który zostanie usunięty, aby usunąć relację użytkowników z tym segmentem. Ta akcja aktualizuje definicję segmentu i usuwa wszystkich użytkowników z segmentu. Użyjesz parametru UserGroupFilter, aby oddzielić użytkowników od segmentu przed usunięciem.

    Aby edytować segment, użyj polecenia cmdlet **Set-OrganizationSegment** z parametrem *Identity* i odpowiednimi szczegółami.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> W tym przykładzie dla segmentu, który ma identyfikator GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, zdefiniowaliśmy nazwę działu jako *FakeDept* , aby usunąć użytkowników z segmentu. W tym *przykładzie* użyto atrybutu Dział, ale w razie potrzeby można użyć innych atrybutów. W przykładzie użyto *narzędzia FakeDept* , ponieważ nie istnieje i na pewno nie zawiera żadnych użytkowników. |

4. Aby zastosować zmiany, użyj polecenia cmdlet **Start-InformationBarrierPoliciesApplication** .

    Składni: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >Atrybut *CleanupGroupSegmentLink* usuwa skojarzenia grup z segmentem bez skojarzeń użytkowników.

    Zmiany są stosowane przez użytkownika w organizacji. Jeśli organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

5. Aby usunąć segment, użyj polecenia cmdlet **Remove-OrganizationSegment** z parametrem *Identity* i odpowiednimi szczegółami.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> W tym przykładzie usunięto segment o identyfikatorze GUID c96e0837-c232-4a8a-841e-ef45787d8fcd. |

## <a name="remove-a-policy-and-segment"></a>Usuwanie zasad i segmentu

1. Aby wyświetlić listę bieżących zasad barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składni: `Get-InformationBarrierPolicy`

    Na liście wyników zidentyfikuj zasady, które chcesz usunąć. Zanotuj identyfikator GUID i nazwę zasad.

2. Aby wyświetlić wszystkie istniejące segmenty, użyj polecenia cmdlet **Get-OrganizationSegment** .

    Składni: `Get-OrganizationSegment`

    Zostanie wyświetlona lista segmentów i szczegółów dla każdego z nich, takich jak typ segmentu, jego wartość parametru *UserGroupFilter* , kto ją utworzył lub ostatnio zmodyfikował, identyfikator GUID itd.

    >[!TIP]
    >Drukuj lub zapisz listę segmentów do późniejszego odwołania. Jeśli na przykład chcesz edytować segment, musisz znać jego nazwę lub zidentyfikować wartość (jest ona używana z parametrem Identity).

3. Aby ustawić stan usuwania zasad na nieaktywny, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem *Identity* i parametrem *State* ustawionym na *Nieaktywne*.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> W tym przykładzie ustawiliśmy zasady barier informacyjnych o identyfikatorze GUID 43c37853-ea10-4b90-a23d-ab8c93772471 jako stan nieaktywny. |

4. Edytuj segment, który zostanie usunięty, aby usunąć relację użytkowników z tym segmentem. Ta akcja aktualizuje definicję segmentu i usuwa wszystkich użytkowników z segmentu. Użyjesz parametru *UserGroupFilter* , aby oddzielić użytkowników od segmentu przed usunięciem.

    Aby edytować segment, użyj polecenia cmdlet **Set-OrganizationSegment** z parametrem *Identity* i odpowiednimi szczegółami.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> W tym przykładzie dla segmentu, który ma identyfikator GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, zaktualizowaliśmy nazwę działu na *FakeDept* , aby usunąć użytkowników z segmentu. W tym *przykładzie* użyto atrybutu Dział, ale w razie potrzeby można użyć innych atrybutów. W przykładzie *użyto narzędzia FakeDept* , ponieważ nie istnieje i na pewno nie zawiera żadnych użytkowników. |

5. Aby zastosować zmiany, użyj polecenia cmdlet **Start-InformationBarrierPoliciesApplication** .

    Składni: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >Atrybut *CleanupGroupSegmentLink* usuwa skojarzenia grup z segmentem bez skojarzeń użytkowników.

    Zmiany są stosowane przez użytkownika w organizacji. Jeśli organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

6. Użyj polecenia cmdlet **Remove-InformationBarrierPolicy** z parametrem *Identity* .

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> W tym przykładzie zasady o identyfikatorze GUID *43c37853-ea10-4b90-a23d-ab8c93772471* zostaną usunięte. |

    Po wyświetleniu monitu potwierdź zmianę.

7. Aby usunąć segment, użyj polecenia cmdlet **Remove-OrganizationSegment** z parametrem *Identity* i odpowiednimi szczegółami.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> W tym przykładzie segment z identyfikatorem GUID c96e0837-c232-4a8a-841e-ef45787d8fcd został usunięty. |

## <a name="stop-a-policy-application"></a>Zatrzymywanie aplikacji zasad

Po rozpoczęciu stosowania zasad barier informacyjnych, jeśli chcesz zatrzymać stosowanie tych zasad, skorzystaj z poniższej procedury. Rozpoczęcie procesu potrwa około 30–35 minut.

1. Aby wyświetlić stan najnowszej aplikacji zasad barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPoliciesApplicationStatus** .

    Składni: `Get-InformationBarrierPoliciesApplicationStatus`

    Zanotuj identyfikator GUID aplikacji.

2. Użyj polecenia cmdlet **Stop-InformationBarrierPoliciesApplication** z parametrem Identity.

    |**Składni**|**Przykład**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> W tym przykładzie zatrzymujemy stosowanie zasad barier informacyjnych. |

## <a name="resources"></a>Zasoby

- [Omówienie barier informacyjnych](information-barriers.md)
- [Definiowanie zasad dla barier informacyjnych](information-barriers-policies.md)
- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w usłudze SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w OneDrive](/onedrive/information-barriers)
- [Atrybuty zasad IB](information-barriers-attributes.md)
- [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
