---
title: Konfigurowanie domyślnego typu łącza udostępniania przy użyciu etykiet poufności
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Użyj etykiet poufności, aby skonfigurować domyślny typ łącza udostępniania dla witryn i dokumentów w programach SharePoint i OneDrive.
ms.openlocfilehash: ca4b74c2fb25c4f1f1ef96b8ae0241481358797d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628578"
---
# <a name="use-sensitivity-labels-to-configure-the-default-sharing-link-type-for-sites-and-documents-in-sharepoint-and-onedrive"></a>Użyj etykiet poufności, aby skonfigurować domyślny typ łącza udostępniania dla witryn i dokumentów w programach SharePoint i OneDrive

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Jako dodatkową konfigurację ustawień widocznych w portal zgodności Microsoft Purview [etykiet poufności](sensitivity-labels.md) możesz użyć tych etykiet, aby skonfigurować ustawienia domyślnego typu linku udostępniania dla witryny programu SharePoint lub konta usługi OneDrive oraz dla poszczególnych dokumentów. Te ustawienia są wybierane automatycznie, ale nie są bardzo widoczne dla użytkowników po wybraniu przycisku **Udostępnij** w aplikacjach pakietu Office. Na przykład:

![Przykładowy domyślny link do udostępniania— okno dialogowe.](../media/default-sharing-link-example.png)

Domyślny typ łącza udostępniania ustawia zakres (kto) i uprawnienia (wyświetlanie lub edytowanie), które są automatycznie wybierane, gdy użytkownicy udostępniają pliki i foldery. Mimo że użytkownicy zawsze mogą zastąpić te ustawienia domyślne przed wysłaniem linku udostępniania, ustawienia, które wybierzesz, zapewniają bezpieczny punkt odniesienia. Zazwyczaj użytkownicy nie zmieniają ustawień przed udostępnieniem.

Na poziomie witryny (witryny programu SharePoint lub konta usługi OneDrive) etykiety poufności stanowią wygodną alternatywę dla ustawienia domyślnego typu łącza udostępniania, który można skonfigurować dla witryny w centrum administracyjnym programu SharePoint. Aby uzyskać więcej informacji, zobacz [Zmienianie domyślnego typu linku dla witryny](/sharepoint/change-default-sharing-link) z dokumentacji programu SharePoint.

Ta konfiguracja na poziomie witryny działa dobrze w przypadku witryn programu SharePoint, które mają dokumenty o tym samym poziomie poufności. Jeśli jednak witryny zawierają dokumenty o wyższym poziomie poufności, które wymagają bardziej restrykcyjnych ustawień, możesz skonfigurować etykietę poufności z różnymi ustawieniami domyślnego typu łącza udostępniania, a następnie zastosować tę etykietę do dokumentów.

W tym scenariuszu, w którym witryna ma domyślne ustawienia typu łącza udostępniania, a dokument w tej witrynie ma inne domyślne ustawienia typu łącza, bardziej restrykcyjne ustawienia zakresu zostaną zastosowane w momencie, gdy użytkownik wybierze opcję udostępniania dokumentu. Przykład:

- Domyślny typ łącza udostępniania witryny jest ograniczony do wszystkich użytkowników w organizacji. Dokument w tej witrynie ma etykietę z domyślnym typem łącza udostępniania ustawionym na określone osoby. Gdy użytkownik udostępni ten dokument, wybrany domyślny typ łącza udostępniania będzie ograniczony do określonych osób.

- Domyślny typ łącza udostępniania dla witryny jest ograniczony do określonych osób z uprawnieniami do edycji. Dokument w tej witrynie jest oznaczony etykietą z domyślnym typem łącza udostępniania ustawionym dla każdego w organizacji z uprawnieniami do wyświetlania. Gdy użytkownik udostępni ten dokument, wybrany domyślny typ łącza udostępniania będzie ograniczony do określonych osób z uprawnieniami do edycji.

Konfigurowanie domyślnego typu łącza dla dokumentów może być również odpowiednie bez ustawienia na poziomie lokacji. Na przykład chociaż witryny programu SharePoint są zwykle zorganizowane w celu hostowania tego samego typu dokumentów, nie dotyczy to kont usługi OneDrive. Użytkownicy zazwyczaj zapisują szeroką gamę plików w usłudze OneDrive, często w tym wiele dokumentów osobistych i biznesowych. Ustawienie domyślnego typu łącza dla wszystkich dokumentów dla konta użytkownika w usłudze OneDrive prawdopodobnie nie jest praktyczne, ale poszczególne dokumenty nadal mogą korzystać z tych ustawień. Przykład:

- Dokumenty oznaczone etykietą **Wysoce poufne** mają domyślny typ linku udostępniania, który ogranicza udostępnianie do określonych osób, a nie do kogokolwiek w organizacji.
- Dokumenty z etykietą **Ogólne** mają domyślny typ linku udostępniania, który ogranicza udostępnianie do osób w organizacji.
- Dokumenty z etykietą **Osobiste** mają domyślny typ linku udostępniania, który umożliwia udostępnianie wszystkim osobom z linkiem.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zastosować domyślny typ łącza udostępniania dla witryn, etykiety poufności muszą być włączone dla kontenerów. Jeśli ta funkcja nie jest jeszcze włączona dla dzierżawy, zobacz [Jak włączyć etykiety poufności dla kontenerów i zsynchronizować etykiety](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

Aby zastosować domyślny typ łącza udostępniania dla dokumentów w programach SharePoint i OneDrive, należy włączyć etykiety poufności dla tych usług. Jeśli ta funkcja nie jest jeszcze włączona dla dzierżawy, zobacz [Jak włączyć etykiety poufności dla programu SharePoint i usługi OneDrive (zgoda)](sensitivity-labels-sharepoint-onedrive-files.md#how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in).

W sesji programu PowerShell należy [nawiązać połączenie z programem PowerShell Office 365 Security & Compliance](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell), aby skonfigurować ustawienia domyślnego typu łącza udostępniania.

> [!NOTE]
> Chociaż nie jest to wymagane, najłatwiej jest najpierw [utworzyć i skonfigurować etykiety poufności w portal zgodności Microsoft Purview](create-sensitivity-labels.md), a następnie zmodyfikować te etykiety przy użyciu ustawień, które konfigurują domyślny typ łącza udostępniania.

## <a name="how-to-configure-settings-for-the-default-sharing-link-type"></a>Jak skonfigurować ustawienia domyślnego typu linku udostępniania

Ustawienia konfiguracji domyślnego typu łącza udostępniania używają parametru *AdvancedSettings* programu PowerShell z poleceniami cmdlet [Set-Label](/powershell/module/exchange/set-label) i [New-Label](/powershell/module/exchange/new-labelpolicy) z programu [PowerShell Security & Compliance](/powershell/exchange/scc-powershell):

- **DefaultSharingScope**: Dostępne wartości to:
    - **SpecificPeople**: ustawia domyślny link udostępniania witryny na link "Określone osoby"
    - **Organizacja**: ustawia domyślny link do udostępniania witryny na link "organizacja" lub link do udostępniania firmy
    - **Dowolna osoba**: ustawia domyślny link udostępniania witryny na link Dostęp anonimowy lub Dowolna osoba

- **DefaultShareLinkPermission**: Dostępne wartości to:
    - **Widok**: ustawia domyślne uprawnienie linku dla witryny na uprawnienia "wyświetlenia"
    - **Edytuj**: ustawia domyślne uprawnienie linku dla witryny na uprawnienia do "edycji"

Te dwa ustawienia i wartości są równoważne parametrom *DefaultSharingScope* i *DefaultShareLinkPermission* z polecenia cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) .

Przykłady programu PowerShell, w których identyfikator GUID etykiety poufności to **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

- Aby ustawić domyślny typ linku udostępniania na SpecificPeople:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- Aby ustawić domyślne uprawnienia typu łącza udostępniania na Edytuj:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

Aby uzyskać więcej informacji na temat określania ustawień zaawansowanych programu [PowerShell, zobacz Porady programu PowerShell dotyczące określania ustawień zaawansowanych](create-sensitivity-labels.md#powershell-tips-for-specifying-the-advanced-settings).

Aby skonfigurować ustawienia domyślnego typu łącza udostępniania dla witryny, [zakres etykiety poufności](sensitivity-labels.md#label-scopes) musi zawierać **grupy & lokacje** podczas tworzenia etykiety poufności w portal zgodności Microsoft Purview. Po jego utworzeniu zobaczysz, że jest ona wyświetlana jako **Witryna, UnifiedGroup** w kolumnie **Zakres** na stronie **Etykiety** , a ustawienie *ContentType* programu PowerShell również wyświetla tę samą wartość. W przypadku dokumentów zakres musi zawierać **pliki & wiadomości e-mail**, które są wyświetlane jako **Plik, Wiadomość e-mail**. Następnie:

- Gdy zakres obejmuje **grupy & lokacje**, można zastosować etykietę do witryny, która ustawia domyślny typ łącza udostępniania dla tej witryny. Aby uzyskać informacje na temat stosowania etykiety poufności do lokacji, zobacz [Jak stosować etykiety poufności do kontenerów](sensitivity-labels-teams-groups-sites.md#how-to-apply-sensitivity-labels-to-containers).

- Gdy zakres etykiety poufności zawiera pliki **& wiadomości e-mail**, możesz zastosować etykietę do dokumentów, która ustawia domyślny typ linku udostępniania dla tego dokumentu. Etykietę można zastosować [ręcznie](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) lub [automatycznie](apply-sensitivity-label-automatically.md).

> [!TIP]
> Można również określić, że etykieta jest domyślną etykietą poufności, która ma być stosowana dla nowych witryn lub nowych dokumentów, jako [ustawienie zasad etykiety](sensitivity-labels.md#what-label-policies-can-do).
