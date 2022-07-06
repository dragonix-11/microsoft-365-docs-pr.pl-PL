---
title: Etykiety klasyfikacji i poufności usługi AAD dla grup platformy Microsoft 365
ms.reviewer: vijagan
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
f1.keywords: NOCSH
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
description: W tym artykule omówiono klasyczne etykiety klasyfikacji i poufności usługi Azure Active Directory.
ms.openlocfilehash: 260b71d703f2534e5e2ddcf4ef45fe28a914eeab
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623788"
---
# <a name="azure-active-directory-classification-and-sensitivity-labels-for-microsoft-365-groups"></a>Etykiety klasyfikacji i poufności usługi Azure Active Directory dla grup platformy Microsoft 365

W tym artykule omówiono klasyczne etykiety klasyfikacji i poufności usługi Azure Active Directory.

Etykiety poufności są obsługiwane przez [te usługi](./sensitivity-labels-teams-groups-sites.md).

Aby uzyskać pełne informacje o etykietach poufności, zobacz [Dowiedz się więcej o etykietach poufności](sensitivity-labels.md).

Aby dowiedzieć się więcej o etykietach poufności i ich zachowaniu w witrynach i grupach platformy Microsoft 365, zobacz [Używanie etykiet poufności do ochrony zawartości w usłudze Microsoft Teams, grupach platformy Microsoft 365 i witrynach programu SharePoint](sensitivity-labels-teams-groups-sites.md).

Zapoznaj się z poniższymi scenariuszami, aby zapoznać się z najlepszymi rozwiązaniami dotyczącymi migracji z klasycznej klasyfikacji usługi AAD do etykiet poufności.

## <a name="scenario-1-tenant-never-used-classic-aad-classifications-or-sensitivity-labels-for-documents-and-emails"></a>Scenariusz 1. Dzierżawa nigdy nie używała klasycznych klasyfikacji usługi AAD ani etykiet poufności dla dokumentów i wiadomości e-mail

- Administracja dzierżawy włącza etykiety poufności dla grup, ustawiając flagę dzierżawy "EnableMIPLabels" na wartość true za pomocą polecenia cmdlet programu PowerShell usługi AAD.
- Administracja dzierżawy tworzy etykiety poufności w [portal zgodności Microsoft Purview](https://compliance.microsoft.com).
    - Administrator dzierżawy może wybrać akcje związane z plikami i wiadomościami e-mail, takie jak szyfrowanie i znak wodny.
    - Administrator dzierżawy może wybrać akcje związane z witryną usługi Grupy Microsoft 365 i SharePoint Online do etykiet poufności.
- Administracja dzierżawy publikuje zasady.
- **Zgodne obciążenia** pokazują etykiety poufności. Użyj etykiet poufności, aby utworzyć grupy. Zgodne obciążenia to usługi, które obsługują etykiety poufności.
- **Niezgodne obciążenia** to usługi, które nie obsługują jeszcze etykiet poufności. Można jednak tworzyć grupy, ale nie można ich skojarzyć z etykietą poufności za pośrednictwem niezgodnych obciążeń. Aby skojarzyć takie grupy z etykietami poufności, administratorzy dzierżawy mogą uruchamiać polecenia cmdlet programu PowerShell.

Tabela 1. Zachowanie zgodnych i niezgodnych obciążeń — tworzenie, edytowanie lub usuwanie grup

|Obciążenia|Jaka lista etykiet jest widoczna dla użytkownika w oknie grupy?|Tworzenie nowej grupy |Edytuj grupę |Usuń grupę |
|:-------|:-------|:--------|:--------|:--------|   
|Zgodny   |etykiety poufności. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |
|Niezgodne |Brak widocznych etykiet poufności. |Użytkownik może utworzyć grupę bez wybierania etykiety poufności. <br><br> Pamiętaj, że administrator może uruchamiać polecenia cmdlet, aby zastosować etykiety poufności w tle. |**Przypadek 1**. Nie wybrano wcześniej żadnej etykiety poufności. Użytkownik może edytować grupę.<br><br> **Przypadek 2**: etykieta poufności zastosowana wcześniej w tle przy użyciu polecenia cmdlet. Użytkownik może pomyślnie edytować grupę, z wyłączeniem przypadku, w którym użytkownik wybiera nieprawidłową kombinację ustawień prywatności w odniesieniu do etykiety. |Brak zmian w zachowaniu.|

> [!NOTE]
> W przypadku klienta klasycznego programu Outlook (Win 32) po włączeniu przez administratora etykiet poufności w dzierżawie, a jego użytkownik jest w starszej wersji klienta klasycznego programu Outlook (Win 32):
>
> - Użytkownik widzi etykiety poufności wyświetlane w starszej wersji klienta klasycznego programu Outlook.
> - Jednak gdy użytkownik edytuje grupę i zapisuje grupę z etykietą poufności, wybrane ustawienie prywatności jest zastępowane przez ustawienie prywatności zastosowanej etykiety poufności.
>
> Zalecamy, aby użytkownicy w starej wersji klienta programu Outlook uaktualnili się do nowszej wersji.

## <a name="scenario-2-tenant-is-already-using-classic-aad-classifications"></a>Scenariusz 2. Dzierżawa korzysta już z [klasycznych klasyfikacji](../enterprise/manage-microsoft-365-groups-with-powershell.md) usługi AAD

### <a name="case-a-tenant-never-used-sensitivity-labels-for-documents-and-emails"></a>Przypadek A: dzierżawa nigdy nie używała etykiet poufności dla dokumentów i wiadomości e-mail

1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) zalecamy utworzenie etykiet poufności o takiej samej nazwie jak istniejące klasyczne etykiety Azure AD.
2. Użyj polecenia cmdlet programu PowerShell, aby zastosować te etykiety poufności do istniejących grup platformy Microsoft 365 i witryn programu SharePoint przy użyciu mapowania nazw.
3. Administracja można usunąć klasyczne etykiety Azure AD:
    - Zgodne obciążenia pokazują, że te etykiety poufności i grupy są tworzone razem z nimi.
    - Niezgodne obciążenia działają podczas tworzenia grup, ale nie jest do nich dołączona żadna etykieta poufności.
4. Administratorzy mogą uruchamiać polecenia cmdlet programu PowerShell, aby zastosować etykiety poufności do tych grup bez etykiet.
    - Alternatywnie administrator może zachować klasyczne etykiety Azure AD:
        - Zgodne obciążenia pokazują te etykiety poufności, a grupy są tworzone razem z nimi. Zgodne obciążenia to usługi, które obsługują etykiety poufności.
        - Niezgodne obciążenia działają podczas tworzenia grup i pokazują klasyczne etykiety Azure AD. Te klasyczne etykiety Azure AD są dołączane do tych grup utworzonych przy użyciu niezgodnych obciążeń.
5. Zdecydowanie zalecamy, aby administratorzy uruchamiali polecenia cmdlet programu PowerShell, aby stosować etykiety poufności do tych grup przy użyciu klasycznych etykiet Azure AD.

Tabela 2. Zachowanie zgodnych i niezgodnych obciążeń — tworzenie, edytowanie lub usuwanie grup

|Obciążenia|Jaka lista etykiet jest widoczna dla użytkownika w oknie grupy?|Tworzenie nowej grupy |Edytuj grupę |Usuń grupę |
|:-------|:-------|:--------|:--------|:--------|   
|Zgodny   |etykiety poufności. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |Brak zmian w zachowaniu. |
|Niezgodne |Stare klasyczne etykiety usługi AAD. |Użytkownik może utworzyć grupę z wybraną klasyczną etykietą Azure AD. <br><br>Pamiętaj, że administrator może uruchamiać polecenia cmdlet, aby zastosować etykiety poufności w tle. |**Przypadek 1**. Nie wybrano wcześniej żadnej etykiety poufności. Użytkownik może edytować grupę.<br><br> **Przypadek 2**. Wcześniej zaznaczono klasyczne etykiety usługi AAD. Użytkownik może edytować grupę.<br><br> **Przypadek 3**: etykieta poufności zastosowana wcześniej w tle przy użyciu polecenia cmdlet. Użytkownik powinien mieć możliwość edytowania grupy, z wyłączeniem jednego przypadku, w którym użytkownik wybiera nieprawidłową kombinację ustawień prywatności w odniesieniu do etykiety. |Użytkownik może usunąć grupę. |

> [!NOTE]
> W przypadku klienta klasycznego programu Outlook (Win 32) po włączeniu przez administratora etykiet poufności w dzierżawie, a jego użytkownik jest w starszej wersji klienta klasycznego programu Outlook (Win 32):
>
> - Użytkownik widzi etykiety poufności wyświetlane w starszej wersji klienta klasycznego programu Outlook.
> - Jednak gdy użytkownik edytuje grupę i zapisuje grupę z etykietą poufności, wybrane ustawienie prywatności jest zastępowane przez ustawienie prywatności zastosowanej etykiety poufności.
>
> Zalecamy, aby użytkownicy w starej wersji klienta programu Outlook uaktualnili się do nowszej wersji.

### <a name="case-b-tenant-used-sensitivity-labels-for-documents-and-emails"></a>Przypadek B: Dzierżawa używała etykiet poufności dla dokumentów i wiadomości e-mail

1. Gdy tylko administrator włączy funkcję etykiet poufności w dzierżawie, ustawiając flagę dzierżawy "EnableMIPLabels" na wartość true, zostaną wyświetlone etykiety poufności dokumentów i wiadomości e-mail w oknach dialogowych tworzenia i edytowania grup/lokacji/zespołu.
2. Administrator może używać tych samych etykiet poufności dokumentów i wiadomości e-mail, aby wymusić prywatność i dostęp użytkowników zewnętrznych w grupie/witrynie/zespole, określając powiązane ustawienia grupy:
    1. W [portal zgodności Microsoft Purview](https://compliance.microsoft.com) wybierz kartę **Witryny i grupy**.
    2. Edytuj etykietę poufności dokumentu lub wiadomości e-mail.

## <a name="sample-script"></a>Przykładowy skrypt

Aby uzyskać przykładowy skrypt do migrowania grup z klasycznymi etykietami usługi AAD do etykiet poufności, zobacz [Klasyczna klasyfikacja grup Azure AD](./sensitivity-labels-teams-groups-sites.md#classic-azure-ad-group-classification).
