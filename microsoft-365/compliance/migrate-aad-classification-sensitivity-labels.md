---
title: Azure Active Directory klasyfikacji i wrażliwości grup Microsoft 365 grupy
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: W tym artykule omówiono klasyczną Azure Active Directory klasyfikację i etykiety wrażliwości.
ms.openlocfilehash: 0a8c12d3d133000a880c58366a9f2b13ed8cbf49
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988024"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Azure Active Directory klasyfikacji i wrażliwości grup Microsoft 365 grupy

W tym artykule omówiono klasyczną Azure Active Directory klasyfikację i etykiety wrażliwości.

Etykiety wrażliwości są obsługiwane przez [te usługi](./sensitivity-labels-teams-groups-sites.md).

Aby uzyskać pełne informacje na temat etykiet wrażliwości, zobacz [Informacje o etykietach wrażliwości](sensitivity-labels.md).

Aby dowiedzieć się więcej o etykietach wrażliwości i ich zachowaniu dla witryn i grup Microsoft 365, zobacz Chroninie zawartości w witrynach sieci Microsoft Teams, grup Microsoft 365 i grup SharePoint [sieci Web](sensitivity-labels-teams-groups-sites.md).

Zapoznaj się z poniższymi scenariuszami, aby uzyskać najlepsze rozwiązania dotyczące migracji z klasyfikacji AAD do etykiet wrażliwości.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Scenariusz 1. Dzierżawa nigdy nie używała klasyfikacji AAD ani etykiet wrażliwości w dokumentach i wiadomościach e-mail

- Administrator dzierżawy włącza etykiety wrażliwości dla grup, ustawiając flagę dzierżawy "EnableMIPLabels" na true za pomocą AAD cmdlet programu PowerShell.
- Administrator dzierżawy utworzy etykiety wrażliwości w [Centrum zgodności platformy Microsoft 365.](https://compliance.microsoft.com)
    - Administrator dzierżawy może wybrać akcje związane z plikami i pocztą e-mail, takie jak szyfrowanie i znakowanie.
    - Administrator dzierżawy może wybrać Microsoft 365 grupy i SharePoint online akcje związane z witryną do etykiet wrażliwości.
- Administrator dzierżawy publikuje zasady.
- **Zgodne obciążenia pracą pokazują** etykiety wrażliwości. Do tworzenia grup użyj etykiet wrażliwości. Zgodne obciążenia pracą to usługi, które obsługują etykiety wrażliwości.
- **Niezgodne obciążenia pracą to** usługi, które jeszcze nie obsługują etykiet wrażliwości. Można tworzyć grupy, jednak nie można ich skojarzyć z etykietą wrażliwości za pośrednictwem niezgodnych obciążeń. Aby skojarzyć takie grupy z etykietami wrażliwości, administratorzy dzierżawy mogą uruchamiać polecenia cmdlet programu PowerShell.

Tabela 1. Zachowanie zgodnych i niezgodnych obciążeń — tworzenie, edytowanie lub usuwanie grup

|Obciążenie pracą|Jaka lista etykiet jest wyświetlona przez użytkownika w oknie grupy?|Tworzenie nowej grupy |Edytuj grupę |Usuwanie grupy |
|:-------|:-------|:--------|:--------|:--------|   
|Zgodny   |etykiety wrażliwości. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |
|Niezgodne |Etykiety wrażliwości nie są widoczne. |Użytkownik może utworzyć grupę bez wybierania etykiety wrażliwości. <br><br> Uwaga: administrator może uruchamiać polecenia cmdlet w celu stosowania etykiet wrażliwości w tle. |**Case 1**: Brak wcześniej zaznaczonej etykiety wrażliwości. Użytkownik może edytować grupę.<br><br> **Case 2**: sensitivity label applied previously in the background using cmdlet. Użytkownik może pomyślnie edytować grupę, wyłączając przypadek, w którym użytkownik wybierze nieprawidłową kombinację ustawień prywatności względem etykiety. |Brak zmian w zachowaniu.|

> [!NOTE]
> W przypadku klienta Outlook (Win 32) po włączenie przez administratora etykiet wrażliwości w dzierżawie, a użytkownik korzysta ze starszej wersji klienta klasycznego pakietu Outlook (Win 32):
>
> - Etykiety wrażliwości są wyświetlane w starszej wersji klienta Outlook klasycznego.
> - Jednak gdy użytkownik edytuje grupę i zapisuje grupę z etykietą poufności, wybrane ustawienie prywatności zostanie zastąpione ustawieniem prywatności zastosowanej etykiety wrażliwości.
>
> Zalecamy, aby użytkownicy korzystający ze starej wersji Outlook uaktualniali klienta do nowszej wersji.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Scenariusz 2. Dzierżawa już używa klasyfikacji klasycznych AAD [dzierżawy](../enterprise/manage-microsoft-365-groups-with-powershell.md)

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Przypadek A. Dzierżawa nigdy nie użyła etykiet wrażliwości w dokumentach i wiadomościach e-mail

1. W tym [Centrum zgodności platformy Microsoft 365](https://compliance.microsoft.com) zalecamy utworzenie etykiet wrażliwości o takiej samej nazwie jak istniejące klasyczne etykiety usługi Azure AD.
2. Użyj polecenia cmdlet programu PowerShell, aby zastosować te etykiety wrażliwości do istniejących grup Microsoft 365 i SharePoint przy użyciu mapowania nazw.
3. Administrator może usunąć klasyczne etykiety usługi Azure AD:
    - Zgodne obciążenia pracą pokazują etykiety wrażliwości i grupy, które są tworzone razem z nimi.
    - Niezgodne obciążenia pracą działają podczas tworzenia grup, ale do grup nie jest do nich dołączona żadna etykieta wrażliwości.
4. Administratorzy mogą uruchamiać polecenia cmdlet programu PowerShell w celu zastosowania etykiet wrażliwości do tych grup bez etykiet.
    - Ewentualnie administrator może wybrać zachowanie klasycznych etykiet usługi Azure AD:
        - Zgodne obciążenia pracą pokazują etykiety wrażliwości, a grupy są tworzone razem z nimi. Zgodne obciążenia pracą to usługi, które obsługują etykiety wrażliwości.
        - Niezgodne obciążenia pracą podczas tworzenia grup i wyświetlanie klasycznych etykiet usługi Azure AD. Te klasyczne etykiety usługi Azure AD są dołączane do tych grup utworzonych za pomocą niezgodnych obciążeń.
5. Zdecydowanie zalecamy, aby administratorzy uruchamiali polecenia cmdlet programu PowerShell w celu zastosowania etykiet wrażliwości do tych grup przy użyciu klasycznych etykiet usługi Azure AD.

Tabela 2. Zachowanie zgodnych i niezgodnych obciążeń — tworzenie, edytowanie lub usuwanie grup

|Obciążenie pracą|Jaka lista etykiet jest wyświetlona przez użytkownika w oknie grupy?|Tworzenie nowej grupy |Edytuj grupę |Usuwanie grupy |
|:-------|:-------|:--------|:--------|:--------|   
|Zgodny   |etykiety wrażliwości. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |
|Niezgodne |Stare klasyczne AAD etykiety. |Użytkownik może utworzyć grupę z zaznaczoną etykietą klasyczną usługi Azure AD. <br><br>Uwaga: administrator może uruchamiać polecenia cmdlet w celu stosowania etykiet wrażliwości w tle. |**Case 1**: Brak wcześniej zaznaczonej etykiety wrażliwości. Użytkownik może edytować grupę.<br><br> **Case 2**: Classic AAD labels previously selected. Użytkownik może edytować grupę.<br><br> **Case 3**: sensitivity label applied previously in the background using cmdlet. Użytkownik powinien mieć możliwość edytowania grupy, z wyjątkiem jednego przypadku, w którym użytkownik wybierze nieprawidłową kombinację ustawień prywatności względem etykiety. |Użytkownik może usunąć grupę. |

> [!NOTE]
> W przypadku klienta Outlook (Win 32) po włączenie przez administratora etykiet wrażliwości w dzierżawie, a użytkownik korzysta ze starszej wersji klienta klasycznego pakietu Outlook (Win 32):
>
> - Etykiety wrażliwości są wyświetlane w starszej wersji klienta Outlook klasycznego.
> - Jednak gdy użytkownik edytuje grupę i zapisuje grupę z etykietą poufności, wybrane ustawienie prywatności zostanie zastąpione ustawieniem prywatności zastosowanej etykiety wrażliwości.
>
> Zalecamy, aby użytkownicy korzystający ze starej wersji Outlook uaktualniali klienta do nowszej wersji.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Przypadek B. Dzierżawa użyła etykiet wrażliwości do dokumentów i wiadomości e-mail

1. Gdy tylko administrator włączy funkcję etykiet wrażliwości w dzierżawie, ustawiając flagę dzierżawy "EnableMIPLabels" na prawda, zostaną wyświetlone etykiety dokumentów i wiadomości e-mail wrażliwości w oknach dialogowych tworzenia i edytowania grupy/witryny/zespołu.
2. Administrator może użyć tego samego dokumentu i etykiet wrażliwości poczty e-mail, aby wymusić prywatność i dostęp użytkowników zewnętrznych w grupie/witrynie/zespole, określając powiązane ustawienia grupy:
    1. W [Centrum zgodności platformy Microsoft 365 wybierz](https://compliance.microsoft.com) **kartę Witryny i** grupy.
    2. Edytowanie etykiety wrażliwości dokumentu lub wiadomości e-mail.

## <a name="sample-script"></a>Przykładowy skrypt

Aby uzyskać przykładowy skrypt migracji grup z klasycznymi AAD etykietami wrażliwości, zobacz Klasyfikacja grup w [klasycznej usłudze Azure AD](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification).