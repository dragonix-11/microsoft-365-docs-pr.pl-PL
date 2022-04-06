---
title: Zarządzanie zasadami barier informacyjnych
description: Dowiedz się, jak edytować lub usuwać zasady i segmenty z barier informacyjnych.
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
ms.openlocfilehash: fc8cc7e4fcbfb9fe9c2ee0f1c531511d9c2fa0b6
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634366"
---
# <a name="manage-information-barriers-policies"></a>Zarządzanie zasadami barier informacyjnych

Po [zdefiniowanych zasadach barier](information-barriers-policies.md) informacyjnych może być konieczne wprowadzanie zmian w zasadach lub segmentach użytkowników w ramach rozwiązywania [](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) problemów lub regularnej konserwacji.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|**Akcja**|**Opis**|
|:---------|:--------------|
| [Edytowanie atrybutów konta użytkownika](#edit-user-account-attributes) | Wypełnij atrybuty w Azure Active Directory których można używać do definiowania segmentów. <br> Edytuj atrybuty konta użytkownika, gdy użytkownicy nie są uwzględnieni w segmentach, w których powinni się znaleźć, aby zmienić segmenty, w których znajdują się użytkownicy, lub zdefiniować segmenty za pomocą różnych atrybutów. |
| [Edytowanie segmentu](#edit-a-segment) | Edytuj segmenty, jeśli chcesz zmienić sposób zdefiniowanego segmentu. <br> Na przykład możesz mieć pierwotnie zdefiniowane segmenty przy użyciu *funkcji Department* i teraz chcesz użyć innego atrybutu, na przykład *MemberOf*. |
| [Edytowanie zasad](#edit-a-policy) | Edytuj zasady zawarte w barierach informacyjnych, jeśli chcesz zmienić sposób działania zasad.<br> Na przykład zamiast blokowania komunikacji między dwoma segmentami możesz zezwolić na komunikację tylko między określonymi segmentami. |
| [Ustawianie zasad jako nieaktywnych](#set-a-policy-to-inactive-status) |Ustaw dla zasad status nieaktywny, jeśli chcesz wprowadzić zmiany w zasadach lub gdy nie chcesz, aby były obowiązywać. |
| [Usuwanie zasad](#remove-a-policy) | Usuwaj bariery informacyjne, gdy nie potrzebujesz już określonej zasady. |
| [Usuwanie segmentu](#remove-a-segment) | Usuwanie segmentu barier informacyjnych, gdy nie potrzebujesz już konkretnego segmentu. |
| [Usuwanie zasad i segmentu](#remove-a-policy-and-segment) | Jednocześnie usuń zasady i segment informacji. |
| [Zatrzymywanie aplikacji zasad](#stop-a-policy-application) | To działanie należy podjąć, aby zatrzymać proces stosowania barier informacyjnych. <br> Zatrzymywanie aplikacji zasad nie jest natychmiastowe i nie umożliwia cofnięcia zasad, które zostały już zastosowane do użytkowników. |
| [Definiowanie zasad na barierach informacyjnych](information-barriers-policies.md) | Zdefiniuj zasady dotyczące informacji, które nie są jeszcze przez Ciebie zawarte, i musisz ograniczyć lub ograniczyć komunikację między określonymi grupami użytkowników. |
| [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Zapoznaj się z tym artykułem w przypadku nieoczekiwanych problemów z barierami informacyjnymi. |

>[!IMPORTANT]
>Aby wykonać zadania opisane w tym artykule, musisz mieć przypisaną odpowiednią rolę, taką jak jedna z następujących czynności:<br>— Microsoft 365 Enterprise administrator globalny<br>— Administrator globalny<br>- Administrator zgodności<br>- Zarządzanie zgodnością IB (jest to nowa rola!)<br><br>Aby dowiedzieć się więcej o wymaganiach wstępnych dotyczących barier informacyjnych, zobacz [Wymagania wstępne (w przypadku zasad barier informacyjnych).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> Upewnij się, [że łączysz się z Centrum & zgodności programu PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Edytowanie atrybutów konta użytkownika

Ta procedura umożliwia edytowanie atrybutów, które są używane do segmentowania użytkowników. Jeśli na przykład używasz atrybutu Department (Dział), a co najmniej jedno konto użytkownika nie zawiera obecnie żadnych wartości wymienionych dla ustawienia Department (Dział), musisz edytować te konta, aby uwzględnić informacje z działu. Atrybuty konta użytkownika służą do definiowania segmentów, aby można było przypisywać zasady zawarte w informacjach.

1. Aby wyświetlić szczegóły określonego konta użytkownika, takie jak wartości atrybutów i przypisane segmenty, użyj polecenia cmdlet **Get-InformationBarrierRecipientStatus** z parametrami tożsamości.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, na przykład nazwy, aliasu, nazwy odróżnianej, kanonicznego nazwy domeny, adresu e-mail lub identyfikatora GUID. <br> (Możesz też użyć tego polecenia cmdlet dla jednego użytkownika: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> W tym przykładzie używamy dwóch kont użytkowników w programie Office 365: *meganb* dla *Megan* i *alexa dla* *Alexa*. |

2. Określ atrybuty, które chcesz edytować dla swoich profilów kont użytkowników. Aby uzyskać więcej informacji, [zobacz Atrybuty, aby uzyskać informacje na temat zasad.](information-barriers-attributes.md)

3. Edytuj co najmniej jedno konto użytkownika, aby uwzględnić wartości atrybutu wybranego w poprzednim kroku. Aby podjąć tę czynność, należy skorzystać z jednej z następujących procedur:

    - Aby edytować jedno konto, zobacz Dodawanie [lub aktualizowanie informacji o profilu użytkownika przy](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) użyciu Azure Active Directory.

    - Aby edytować wiele kont (lub edytować jedno konto za pomocą programu PowerShell), zobacz Konfigurowanie właściwości konta użytkownika za [pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Edytowanie segmentu

Ta procedura umożliwia edytowanie definicji segmentu użytkownika. Na przykład można zmienić nazwę segmentu lub filtr używany do określenia, kto jest uwzględniony w tym segmencie.

1. Aby wyświetlić wszystkie istniejące segmenty, użyj polecenia cmdlet **Get-OrganizationSegment** .

    Składnia: `Get-OrganizationSegment`

    Zostanie wyświetlona lista segmentów i szczegółów poszczególnych segmentów, takich jak typ segmentu, jego wartość UserGroupFilter, nazwa użytkownika, który go utworzył lub ostatnio zmodyfikował, identyfikator GUID i tak dalej.

    > [!TIP]
    > Wydrukuj lub zapisz listę segmentów do późniejszego odwołania. Jeśli na przykład chcesz edytować segment, musisz znać jego nazwę lub zidentyfikować wartość (jest to używane z parametrem Identity).

2. Aby edytować segment, użyj polecenia cmdlet **Set-OrganizationSegment** z **parametrem Identity** i odpowiednimi szczegółami.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> W tym przykładzie zaktualizowano nazwę działu na *HRDept* dla segmentu przy użyciu identyfikatora GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. Po zakończeniu edytowania segmentów w organizacji można zdefiniować lub [](information-barriers-policies.md#step-3-define-information-barrier-policies) [edytować](#edit-a-policy) zasady informacyjne.

## <a name="edit-a-policy"></a>Edytowanie zasad

1. Aby wyświetlić listę bieżących barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składnia: `Get-InformationBarrierPolicy`

    Na liście wyników znajdź zasady, które chcesz zmienić. Zanotuj identyfikator GUID i nazwę zasad.

2. Użyj **polecenia cmdlet Set-InformationBarrierPolicy** z parametrem **Identity** i określ zmiany, które chcesz wprowadzić.

    Przykład: Załóżmy, że zdefiniowano zasady *blokowania segmentu* Badania w celu komunikowania się z *segmentami* Sprzedaż *i Marketing* . Zasady zostały zdefiniowane przy użyciu tego polecenia cmdlet: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Załóżmy, że chcemy go zmienić, aby osoby w  segmencie badań mogą komunikować się tylko z osobami *w tym* segmencie. Aby wprowadzić tę zmianę, użyjmy tego polecenia cmdlet: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    W tym przykładzie zmieniliśmy segment *SegmentyBlokowane* na *SegmentyWszystkie* i określono *segment KADR* .

3. Po zakończeniu edytowania zasad zastosuj zmiany. (Zobacz [Stosowanie zasad barier informacyjnych](information-barriers-policies.md#step-4-apply-information-barrier-policies)).

## <a name="set-a-policy-to-inactive-status"></a>Ustawianie zasad jako nieaktywnych

1. Aby wyświetlić listę bieżących barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składnia: `Get-InformationBarrierPolicy`

    Na liście wyników znajdź zasady, które chcesz zmienić (lub usunąć). Zanotuj identyfikator GUID i nazwę zasad.

2. Aby ustawić stan zasad jako nieaktywny, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem *Identity* i parametrem *State* ustawionym na wartość *Nieaktywny*.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> W tym przykładzie zasady informacyjne, które mają identyfikator GUID *43c37853-ea10-4b90-a23d-ab8c9377247* , są ustawione na status nieaktywny. |

3. Aby zastosować zmiany, użyj polecenia **cmdlet Start-InformationBarrierPoliciesApplication** .

    Składnia: `Start-InformationBarrierPoliciesApplication`

    Zmiany są stosowane w organizacji użytkownika po użytkowniku. Jeśli Twoja organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

4. W tym momencie jedną lub więcej barier informacyjnych jest ustawionych jako nieaktywny status. W tym miejscu możesz wykonać dowolną z następujących czynności:

    - Zachowanie jej bez wpływu na użytkowników (zasada ustawiona na "status nieaktywny" nie ma wpływu na użytkowników)
    - [Edytowanie zasad](#edit-a-policy) 
    - [Usuwanie zasad](#remove-a-policy)

## <a name="remove-a-policy"></a>Usuwanie zasad

1. Aby wyświetlić listę bieżących barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składnia: `Get-InformationBarrierPolicy`

    Na liście wyników znajdź zasady, które chcesz usunąć. Zanotuj identyfikator GUID i nazwę zasad. 

2. Upewnij się, że zasady są ustawione na status nieaktywny. Aby ustawić stan zasad jako nieaktywny, użyj Set-InformationBarrierPolicy cmdlet z parametrem Identity i parametrem State ustawionym na wartość Nieaktywny.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> W tym przykładzie zasady dotyczące barier informacyjnych, które mają identyfikator GUID *43c37853-ea10-4b90-a23d-ab8c9377247* , są statusem nieaktywnym. |

3. Aby zastosować zmiany do zasad, użyj polecenia **cmdlet Start-InformationBarrierPoliciesApplication** .

    Składnia: `Start-InformationBarrierPoliciesApplication`

    Zmiany są stosowane w organizacji użytkownika po użytkowniku. Jeśli Twoja organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

4. Użyj polecenia **cmdlet Remove-InformationBarrierPolicy** z parametrem Identity.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> W tym przykładzie usuwamy zasady o identyfikatorze GUID *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    Gdy zostanie wyświetlony monit, potwierdź zmianę.

## <a name="remove-a-segment"></a>Usuwanie segmentu

1. Aby wyświetlić wszystkie istniejące segmenty, użyj polecenia cmdlet **Get-OrganizationSegment** .

    Składnia: `Get-OrganizationSegment`

    Zostanie wyświetlona lista segmentów i szczegółów poszczególnych segmentów, takich jak typ segmentu, jego wartość UserGroupFilter, nazwa użytkownika, który go utworzył lub ostatnio zmodyfikował, identyfikator GUID i tak dalej.

    >[!TIP]
    >Wydrukuj lub zapisz listę segmentów do późniejszego odwołania. Jeśli na przykład chcesz edytować segment, musisz znać jego nazwę lub zidentyfikować wartość (jest to używane z parametrem Identity).

2. Określ segment do usunięcia i upewnij się, że zasady IB skojarzone z tym segmentem zostały usunięte. Aby uzyskać [szczegółowe informacje, zobacz](#remove-a-policy) procedurę Usuwania zasad.

3. Edytuj segment, który zostanie usunięty, aby usunąć relację użytkowników z tym segmentem. Ta akcja aktualizuje definicję segmentu i usuwa wszystkich użytkowników z tego segmentu. W celu usunięcia użytkowników z segmentu przed usunięciem użyjesz parametru UserGroupFilter.

    Aby edytować segment, użyj polecenia cmdlet **Set-OrganizationSegment** z *parametrem Identity* i odpowiednimi szczegółami.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> W tym przykładzie dla segmentu, który ma identyfikator GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, zdefiniowali nazwę działu jako *Fałszywy* Dział w celu usunięcia użytkowników z tego segmentu. W tym przykładzie jest używany *atrybut Department* , ale możesz użyć innych atrybutów, jeśli to konieczne. W tym przykładzie *użyto usługi FakeDept* , ponieważ nie istnieje i z pewnością nie zawiera żadnych użytkowników. |

4. Aby zastosować zmiany, użyj polecenia **cmdlet Start-InformationBarrierPoliciesApplication** .

    Składnia: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >Atrybut *CleanupGroupSegmentLink* usuwa skojarzenia grup z segmentem bez skojarzeń użytkowników.

    Zmiany są stosowane w organizacji użytkownika po użytkowniku. Jeśli Twoja organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

5. Aby usunąć segment, użyj polecenia cmdlet **Remove-OrganizationSegment** z *parametrem Identity* i odpowiednimi szczegółami.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> W tym przykładzie segment, który ma identyfikator GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, został usunięty. |

## <a name="remove-a-policy-and-segment"></a>Usuwanie zasad i segmentu

1. Aby wyświetlić listę bieżących barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPolicy** .

    Składnia: `Get-InformationBarrierPolicy`

    Na liście wyników znajdź zasady, które chcesz usunąć. Zanotuj identyfikator GUID i nazwę zasad.

2. Aby wyświetlić wszystkie istniejące segmenty, użyj polecenia cmdlet **Get-OrganizationSegment** .

    Składnia: `Get-OrganizationSegment`

    Zostanie wyświetlona lista segmentów i szczegółów poszczególnych segmentów, takich jak typ segmentu, jego wartość parametru *UserGroupFilter* , nazwa użytkownika, który go utworzył lub ostatnio zmodyfikował, identyfikator GUID i tak dalej.

    >[!TIP]
    >Wydrukuj lub zapisz listę segmentów do późniejszego odwołania. Jeśli na przykład chcesz edytować segment, musisz znać jego nazwę lub zidentyfikować wartość (jest to używane z parametrem Identity).

3. Aby ustawić stan zasad, które mają zostać usunięte jako nieaktywne, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem *Identity* i parametrem *State* ustawionym na Wartość nieaktywny *.*

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> W tym przykładzie ustawiono zasady dotyczące barier informacyjnych, które mają identyfikator GUID 43c37853-ea10-4b90-a23d-ab8c93772471 na status nieaktywny. |

4. Edytuj segment, który zostanie usunięty, aby usunąć relację użytkowników z tym segmentem. Ta akcja aktualizuje definicję segmentu i usuwa wszystkich użytkowników z tego segmentu. W celu usunięcia użytkowników z segmentu przed usunięciem użyjesz parametru *UserGroupFilter* .

    Aby edytować segment, użyj polecenia cmdlet **Set-OrganizationSegment** z *parametrem Identity* i odpowiednimi szczegółami.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> W tym przykładzie dla segmentu, który ma identyfikator GUID c96e0837-c232-4a8a-841e-ef45787d8fcd, zaktualizowaliśmy nazwę działu na *FakeDept* , aby usunąć użytkowników z tego segmentu. W tym przykładzie jest używany *atrybut Department* , ale możesz użyć innych atrybutów, jeśli to konieczne. W tym przykładzie *użyto systemu FakeDept* , ponieważ takie dane nie istnieją i z pewnością nie zawierają żadnych użytkowników. |

5. Aby zastosować zmiany, użyj polecenia **cmdlet Start-InformationBarrierPoliciesApplication** .

    Składnia: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >Atrybut *CleanupGroupSegmentLink* usuwa skojarzenia grup z segmentem bez skojarzeń użytkowników.

    Zmiany są stosowane w organizacji użytkownika po użytkowniku. Jeśli Twoja organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

6. Użyj polecenia **cmdlet Remove-InformationBarrierPolicy** z *parametrem Identity* .

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> W tym przykładzie zasady z identyfikatorem GUID *43c37853-ea10-4b90-a23d-ab8c93772471* zostaną usunięte. |

    Gdy zostanie wyświetlony monit, potwierdź zmianę.

7. Aby usunąć segment, użyj polecenia cmdlet **Remove-OrganizationSegment** z *parametrem Identity* i odpowiednimi szczegółami.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> W tym przykładzie segment o identyfikatorze GUID c96e0837-c232-4a8a-841e-ef45787d8fcd został usunięty. |

## <a name="stop-a-policy-application"></a>Zatrzymywanie aplikacji zasad

Jeśli po włożeniu barier informacyjnych chcesz zatrzymać ich stosowanie, skorzystaj z poniższej procedury. Rozpoczęcie procesu potrwa około 30–35 minut.

1. Aby wyświetlić stan najnowszej aplikacji zasad barier informacyjnych, użyj polecenia cmdlet **Get-InformationBarrierPoliciesApplicationStatus** .

    Składnia: `Get-InformationBarrierPoliciesApplicationStatus`

    Zanotuj identyfikator GUID aplikacji.

2. Użyj **polecenia cmdlet Stop-InformationBarrierPoliciesApplication** z parametrem Identity.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> W tym przykładzie zatrzymujemy bariery informacyjne przed zastosowaniem zasad. |

## <a name="resources"></a>Zasoby

- [Omówienie barier informacyjnych](information-barriers.md)
- [Definiowanie zasad na barierach informacyjnych](information-barriers-policies.md)
- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w programie OneDrive](/onedrive/information-barriers)
- [Atrybuty zasad barier informacyjnych](information-barriers-attributes.md)
- [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)