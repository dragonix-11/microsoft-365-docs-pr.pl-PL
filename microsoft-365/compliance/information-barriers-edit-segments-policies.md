---
title: Zarządzanie zasadami barier informacyjnych
description: Dowiedz się, jak edytować lub usuwać zasady z barier informacyjnych.
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
ms.openlocfilehash: e5a8eac15ebb76d9b3c2c95b3eff2cf3bd29772e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985305"
---
# <a name="manage-information-barrier-policies"></a>Zarządzanie zasadami barier informacyjnych

Po [zdefiniowanych zasadach bariery](information-barriers-policies.md) informacyjnej może być konieczne wstanie wprowadzić zmiany w tych zasadach lub segmentach użytkowników w ramach rozwiązywania problemów lub regularnej konserwacji.[](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

|**Akcja**|**Opis**|
|:---------|:--------------|
| [Edytowanie atrybutów konta użytkownika](#edit-user-account-attributes) | Wypełnij atrybuty w Azure Active Directory których można używać do definiowania segmentów.<br/>Edytowanie atrybutów konta użytkownika, gdy użytkownicy nie są uwzględniane w segmentach, w których powinni się znaleźć, zmienianie segmentów, w których znajdują się użytkownicy, lub definiowanie segmentów przy użyciu różnych atrybutów. |
| [Edytowanie segmentu](#edit-a-segment) | Edytuj segmenty, jeśli chcesz zmienić sposób zdefiniowanego segmentu. <br/>Na przykład możesz mieć pierwotnie zdefiniowane segmenty przy użyciu *funkcji Department* i teraz chcesz użyć innego atrybutu, na przykład *MemberOf*. |
| [Edytowanie zasad](#edit-a-policy) | Edytuj zasady barier informacyjnej, jeśli chcesz zmienić sposób działania zasad.<br/>Na przykład zamiast blokowania komunikacji między dwoma segmentami możesz zezwolić na komunikację tylko między określonymi segmentami. |
| [Ustawianie zasad jako nieaktywnych](#set-a-policy-to-inactive-status) |Ustaw dla zasad status nieaktywny, jeśli chcesz wprowadzić zmiany w zasadach lub gdy nie chcesz, aby były obowiązywać. |
| [Usuwanie zasad](#remove-a-policy) | Usuń zasady barier informacyjnej, gdy nie potrzebujesz już konkretnych zasad. |
| [Zatrzymywanie aplikacji zasad](#stop-a-policy-application) | To działanie należy podjąć, aby zatrzymać proces stosowania zasad barier informacyjnych.<br/> Zatrzymanie aplikacji zasad nie jest natychmiastowe i nie powoduje cofnięcia zasad już zastosowanych do użytkowników. |
| [Definiowanie zasad na barierach informacyjnych](information-barriers-policies.md) | Zdefiniuj zasady barier informacyjnej, jeśli takie zasady nie są jeszcze przez Ciebie określone, i musisz ograniczyć lub ograniczyć komunikację między określonymi grupami użytkowników. |
| [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | Zapoznaj się z tym artykułem w przypadku nieoczekiwanych problemów z barierami informacyjnymi. |

> [!IMPORTANT]
> Aby wykonać zadania opisane w tym artykule, musisz mieć przypisaną odpowiednią rolę, taką jak jedna z następujących czynności:<br/>— Microsoft 365 Enterprise administrator globalny<br/>— Administrator globalny<br/>- Administrator zgodności<br/>- Zarządzanie zgodnością IB (jest to nowa rola!)<br><br>Aby dowiedzieć się więcej o wymaganiach wstępnych dla barier informacyjnych, zobacz Wymagania wstępne (aby poznać zasady barier [informacyjnej).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> Upewnij się, [że łączysz się z Centrum & zgodności programu PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>Edytowanie atrybutów konta użytkownika

Ta procedura umożliwia edytowanie atrybutów, które są używane do segmentowania użytkowników. Jeśli na przykład używasz atrybutu Department (Dział), a co najmniej jedno konto użytkownika nie ma obecnie żadnych wartości wymienionych jako Department (Dział), musisz edytować te konta, aby uwzględnić informacje z działu. Atrybuty konta użytkownika służą do definiowania segmentów, dzięki czemu można przypisywać zasady bariery informacyjnej.

1. Aby wyświetlić szczegóły określonego konta użytkownika, takie jak wartości atrybutów i przypisane segmenty, użyj polecenia cmdlet **Get-InformationBarrierRecipientStatus** z parametrami tożsamości.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Możesz użyć dowolnej wartości, która jednoznacznie identyfikuje każdego użytkownika, na przykład nazwy, aliasu, nazwy odróżnianej, kanonicznego nazwy domeny, adresu e-mail lub identyfikatora GUID. <p> (Możesz też użyć tego polecenia cmdlet dla jednego użytkownika: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> W tym przykładzie używamy dwóch kont użytkowników w programie Office 365: *meganb* dla *Megan* i *alexa dla* *Alexa*. |

2. Określ atrybuty, które chcesz edytować dla swoich profilów kont użytkowników. Aby uzyskać więcej informacji, zobacz [Atrybuty, aby uzyskać informacje na temat zasad bariery informacyjnej](information-barriers-attributes.md). 

3. Edytuj co najmniej jedno konto użytkownika, aby uwzględnić wartości atrybutu wybranego w poprzednim kroku. Aby podjąć tę czynność, należy skorzystać z jednej z następujących procedur:

    - Aby edytować jedno konto, zobacz Dodawanie [lub aktualizowanie informacji o profilu użytkownika przy](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) użyciu Azure Active Directory.

    - Aby edytować wiele kont (lub edytować jedno konto za pomocą programu PowerShell), zobacz Konfigurowanie właściwości konta użytkownika za [pomocą programu Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>Edytowanie segmentu

Ta procedura umożliwia edytowanie definicji segmentu użytkownika. Na przykład można zmienić nazwę segmentu lub filtr używany do określenia, kto jest uwzględniony w tym segmencie.

1. Aby wyświetlić wszystkie istniejące segmenty, użyj polecenia cmdlet **Get-OrganizationSegment** .

    Składnia: `Get-OrganizationSegment`

    Zostanie wyświetlona lista segmentów i szczegółów poszczególnych segmentów, takich jak typ segmentu, jego wartość UserGroupFilter, kto go utworzył lub ostatnio zmodyfikował, identyfikator GUID i tak dalej.

    > [!TIP]
    > Wydrukuj lub zapisz listę segmentów do późniejszego odwołania. Jeśli na przykład chcesz edytować segment, musisz znać jego nazwę lub zidentyfikować wartość (jest to używane z parametrem Identity).

2. Aby edytować segment, użyj polecenia cmdlet **Set-OrganizationSegment** z **parametrem Identity** i odpowiednimi szczegółami.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <p> W tym przykładzie dla segmentu, który ma identyfikator GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*, zaktualizowaliśmy nazwę działu na "HRDept". |

Po zakończeniu edytowania segmentów w organizacji można zdefiniować lub [](information-barriers-policies.md#step-3-define-information-barrier-policies) [edytować zasady zawarte w](#edit-a-policy) informacjach.

## <a name="edit-a-policy"></a>Edytowanie zasad

1. Aby wyświetlić listę bieżących zasad bariery informacyjnej, użyj polecenia **cmdlet Get-InformationBarrierPolicy** .

    Składnia: `Get-InformationBarrierPolicy`

    Na liście wyników znajdź zasady, które chcesz zmienić. Zanotuj identyfikator GUID i nazwę zasad.

2. Użyj **polecenia cmdlet Set-InformationBarrierPolicy** z parametrem **Identity** i określ zmiany, które chcesz wprowadzić.

    Przykład: Załóżmy, że zdefiniowano zasady *blokowania segmentu* Badania w celu komunikowania się z *segmentami* Sprzedaż *i Marketing* . Zasady zostały zdefiniowane przy użyciu tego polecenia cmdlet: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    Załóżmy, że chcemy go zmienić, aby osoby w  segmencie badań mogą komunikować się tylko z osobami *w tym* segmencie. Aby wprowadzić tę zmianę, użyjmy tego polecenia cmdlet: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    W tym przykładzie zmieniliśmy segment "SegmentsBlocked" na "SegmentsAllowed" i określono segment *KADR* .

3. Po zakończeniu edytowania zasad zastosuj zmiany. (Zobacz [Stosowanie zasad bariery informacyjnej](information-barriers-policies.md#step-4-apply-information-barrier-policies)).

## <a name="set-a-policy-to-inactive-status"></a>Ustawianie zasad jako nieaktywnych

1. Aby wyświetlić listę bieżących zasad bariery informacyjnej, użyj polecenia **cmdlet Get-InformationBarrierPolicy** .

    Składnia: `Get-InformationBarrierPolicy`

    Na liście wyników znajdź zasady, które chcesz zmienić (lub usunąć). Zanotuj identyfikator GUID i nazwę zasad.

2. Aby ustawić stan zasad jako nieaktywny, użyj polecenia cmdlet **Set-InformationBarrierPolicy** z parametrem Identity i parametrem State ustawionym na wartość Nieaktywny.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <p> W tym przykładzie ustawiono zasady bariery informacyjnej, które mają identyfikator GUID *43c37853-ea10-4b90-a23d-ab8c9377247* jako nieaktywny. |

3. Aby zastosować zmiany, użyj polecenia **cmdlet Start-InformationBarrierPoliciesApplication** .

    Składnia: `Start-InformationBarrierPoliciesApplication`

    Zmiany są stosowane w organizacji przez  użytkowników. Jeśli Twoja organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny. Zgodnie z ogólnymi wytycznymi przetwarzanie 5000 kont użytkowników trwa około godziny.

W tym momencie jedną lub więcej zasad dotyczących informacji jest ustawiony status nieaktywny. W tym miejscu możesz wykonać dowolną z następujących czynności:

- Zachowanie jej bez wpływu na użytkowników (zasada ustawiona na "status nieaktywny" nie ma wpływu na użytkowników)
- [Edytowanie zasad](#edit-a-policy) 
- [Usuwanie zasad](#remove-a-policy)

## <a name="remove-a-policy"></a>Usuwanie zasad

1. Aby wyświetlić listę bieżących zasad bariery informacyjnej, użyj polecenia **cmdlet Get-InformationBarrierPolicy** .

    Składnia: `Get-InformationBarrierPolicy`

    Na liście wyników znajdź zasady, które chcesz usunąć. Zanotuj identyfikator GUID i nazwę zasad. Upewnij się, że zasady są ustawione na status nieaktywny.

2. Użyj polecenia **cmdlet Remove-InformationBarrierPolicy** z parametrem Identity.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <p> W tym przykładzie usuwamy zasady o identyfikatorze GUID *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    Gdy zostanie wyświetlony monit, potwierdź zmianę.

3. Powtórz kroki 1–2 dla każdej zasady, którą chcesz usunąć.

4. Po zakończeniu usuwania zasad zastosuj zmiany. Aby to zrobić, użyj **polecenia cmdlet Start-InformationBarrierPoliciesApplication** .

    Składnia: `Start-InformationBarrierPoliciesApplication`

    Zmiany są stosowane w organizacji przez  użytkowników. Jeśli Twoja organizacja jest duża, ukończenie tego procesu może potrwać co najmniej 24 godziny.

## <a name="stop-a-policy-application"></a>Zatrzymywanie aplikacji zasad

Jeśli po zastosowaniu zasad bariery informacyjnej chcesz zatrzymać ich stosowanie, skorzystaj z poniższej procedury. Rozpoczęcie procesu potrwa około 30–35 minut.

1. Aby wyświetlić stan najnowszej aplikacji zasad bariery informacyjnej, użyj polecenia cmdlet **Get-InformationBarrierPoliciesApplicationStatus** .

    Składnia: `Get-InformationBarrierPoliciesApplicationStatus`

    Zanotuj identyfikator GUID aplikacji.

2. Użyj **polecenia cmdlet Stop-InformationBarrierPoliciesApplication** z parametrem Identity.

    |**Składnia**|**Przykład**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> W tym przykładzie powstrzymuje się zastosowanie zasad bariery informacyjnej. |

## <a name="resources"></a>Zasoby

- [Omówienie barier informacyjnych](information-barriers.md)
- [Definiowanie zasad na barierach informacyjnych](information-barriers-policies.md)
- [Dowiedz się więcej o barierach informacyjnych w Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Dowiedz się więcej o barierach informacyjnych w SharePoint Online](/sharepoint/information-barriers)
- [Dowiedz się więcej o barierach informacyjnych w programie OneDrive](/onedrive/information-barriers)
- [Atrybuty zasad bariery informacyjnej](information-barriers-attributes.md)
- [Rozwiązywanie problemów z barierami informacyjnymi](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)