---
title: Użyj etykiet wrażliwości, aby skonfigurować domyślny typ linku udostępniania dla witryn i dokumentów w SharePoint i OneDrive
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
description: Etykiety wrażliwości konfigurują domyślny typ linku udostępniania dla witryn i dokumentów w SharePoint i OneDrive.
ms.openlocfilehash: 122a8846893b97146dc74d3a9d30ccbfe050525b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704720"
---
# <a name="use-sensitivity-labels-to-configure-the-default-sharing-link-type-for-sites-and-documents-in-sharepoint-and-onedrive"></a>Użyj etykiet wrażliwości, aby skonfigurować domyślny typ linku udostępniania dla witryn i dokumentów w SharePoint i OneDrive

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Etykiety te mogą stanowić dodatkową konfigurację ustawień etykiet wrażliwości w Centrum zgodności platformy Microsoft 365, dzięki [](sensitivity-labels.md)temu można skonfigurować ustawienia domyślnego typu linku udostępniania dla witryny SharePoint lub konta OneDrive oraz poszczególnych dokumentów. Te ustawienia są wybierane automatycznie, ale nie są dobrze widoczne dla użytkowników po wybraniu  przycisku Udostępnij w Office aplikacjach. Jako przykład:

![Przykład domyślnego okna dialogowego linku udostępniania.](../media/default-sharing-link-example.png)

Domyślny typ linku udostępniania określa zakres (kto) i uprawnienia (wyświetlanie lub edytowanie) wybierane automatycznie, gdy użytkownicy współużytkują pliki i foldery. Mimo że użytkownicy zawsze mogą zastąpić te ustawienia domyślne przed wysłaniem linku do udostępniania, wybrać ustawienia dotyczące bezpiecznego planu bazowego. Zazwyczaj użytkownicy nie zmieniają ustawień przed udostępnieniem.

Etykiety wrażliwości na poziomie witryny (konta SharePoint lub OneDrive) stanowią wygodną alternatywę dla ustawienia domyślnego typu linku udostępniania, który można skonfigurować dla witryny w centrum administracyjnym usługi SharePoint. Aby uzyskać więcej informacji, [zobacz Zmienianie domyślnego typu linku witryny](/sharepoint/change-default-sharing-link) w SharePoint dokumentacji.

Ta konfiguracja na poziomie witryny sprawdza się dobrze w SharePoint, w których wszystkie dokumenty mają taki sam poziom wrażliwości. Jeśli jednak witryny zawierają niektóre dokumenty o wyższym poziomie wrażliwości, które wymagają bardziej restrykcyjnych ustawień, możesz skonfigurować etykietę wrażliwości z innymi ustawieniami domyślnego typu linku udostępniania, a następnie zastosować tę etykietę do dokumentów.

W tym scenariuszu, w którym witryna ma domyślne ustawienia typu linku udostępniania, a dokument w tej witrynie ma inne domyślne ustawienia typu linku, bardziej restrykcyjne ustawienia zakresu zostaną zastosowane w momencie wybrania przez użytkownika opcji udostępniania dokumentu. Przykład:

- Domyślny typ linku udostępniania dla witryny jest ograniczony do każdego użytkownika w organizacji. Dokument w tej witrynie jest oznaczony domyślnym typem linku udostępniania ustawionym dla określonych osób. Gdy użytkownik udostępni ten dokument, wybrany domyślny typ linku udostępniania będzie określony dla określonych osób.

- Domyślny typ linku udostępniania witryny jest określony dla określonych osób z uprawnieniami do edytowania. Dokument w tej witrynie ma etykietę z domyślnym typem linku udostępniania ustawionym dla każdego użytkownika w organizacji z uprawnieniami do wyświetlania. Gdy użytkownik udostępni ten dokument, wybrany domyślny typ linku udostępniania będzie określony dla określonych osób z uprawnieniami do edytowania.

Skonfigurowanie domyślnego typu linku dla dokumentów może być również odpowiednie bez ustawienia na poziomie witryny. Na przykład witryny SharePoint zwykle są zorganizowane tak, aby hostować dokumenty tego samego typu, ale nie dotyczy to OneDrive kont. Użytkownicy zazwyczaj zapisują różnego rodzaju pliki w OneDrive, często łącznie z dokumentami osobistymi i służbowych. Ustawienie domyślnego typu linku dla wszystkich dokumentów na koncie OneDrive użytkownika jest prawdopodobnie niepraktyczne, ale poszczególne dokumenty nadal mogą korzystać z tych ustawień. Przykład:

- Dokumenty o etykiecie **Wysoce poufne** mają domyślny typ linku udostępniania, który ogranicza udostępnianie tylko do określonych osób, a nie do nikogo w organizacji.
- Dokumenty z **etykietą Ogólne** mają domyślny typ linku udostępniania, który ogranicza udostępnianie osobom w organizacji.
- Dokumenty o **etykiecie Osobiste** mają domyślny typ linku udostępniania, który umożliwia udostępnianie wszystkim osobom, które mają link.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zastosować domyślny typ linku udostępniania dla witryn, etykiety wrażliwości muszą być włączone dla kontenerów. Jeśli ta funkcja nie jest jeszcze włączona dla dzierżawy, zobacz Jak włączyć etykiety wrażliwości dla kontenerów i [synchronizować etykiety](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels).

Aby zastosować domyślny typ linku udostępniania do dokumentów w SharePoint i OneDrive, dla tych usług musi być włączone etykiety wrażliwości. Jeśli ta funkcja nie jest jeszcze włączona dla Twojej dzierżawy, zobacz Jak włączyć etykiety wrażliwości dla SharePoint i OneDrive [(opt-in)](sensitivity-labels-sharepoint-onedrive-files.md#how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in).

W sesji programu PowerShell musisz połączyć się z programem [Office 365 Security & Compliance Center,](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) aby skonfigurować ustawienia domyślnego typu linku udostępniania.

> [!NOTE]
> Mimo że nie jest to wymagane, najłatwiej jest najpierw utworzyć i skonfigurować etykiety wrażliwości w Centrum zgodności platformy Microsoft 365, [a](create-sensitivity-labels.md) następnie zmodyfikować te etykiety przy użyciu ustawień, które konfigurują domyślny typ linku udostępniania.

## <a name="how-to-configure-settings-for-the-default-sharing-link-type"></a>Jak skonfigurować ustawienia domyślnego typu linku udostępniania

Ustawienia konfiguracji domyślnego typu linku udostępniania używają parametru PowerShell *AdvancedSettings* z poleceniami cmdlet [Set-Label](/powershell/module/exchange/set-label) i [New-Label](/powershell/module/exchange/new-labelpolicy) z programu [Security & Compliance Center w programie PowerShell](/powershell/exchange/scc-powershell):

- **DefaultSharingScope**: Dostępne wartości:
    - **SpecificPeople**: Ustawia domyślny link udostępniania witryny do linku "Konkretne osoby"
    - **Organizacja**: ustawia domyślny link udostępniania witryny do linku "organizacja" lub linku firmowego, który można udostępnić
    - **Każda** osoba: ustawia domyślny link udostępniania witryny na link Dostęp anonimowy lub Każda osoba.

- **DefaultShareLinkPermission**: Dostępne wartości:
    - **Widok**: ustawia domyślne uprawnienie do wyświetlania linku w witrynie
    - **Edycja**: ustawia domyślne uprawnienie do edytowania linku w witrynie

Te dwa ustawienia i wartości są równoważne parametrom *DefaultSharingScope* i *DefaultShareLinkPermission* z polecenia cmdlet [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) .

Przykłady programu PowerShell, w których identyfikator GUID wrażliwości to **8faca7b8-8d20-48a3-8ea2-0f96310a848e**:

- Aby ustawić domyślny typ linku udostępniania na określonyOple:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope="SpecificPeople"}
    ````

- Aby ustawić dla domyślnych uprawnień typu linku udostępniania wartość Edytuj:
    
    ````powershell
    Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultShareLinkPermission="Edit"}
    ````

Aby skonfigurować ustawienia domyślnego typu linku udostępniania dla witryny, zakres etykiety [](sensitivity-labels.md#label-scopes) wrażliwości musi obejmować grupy **&** witryn internetowych podczas tworzenia etykiety wrażliwości w Centrum zgodności platformy Microsoft 365. Po utworzeniu tej właściwości jest ona wyświetlana jako Witryna **, Grupa Ujednolicona** w kolumnie Zakres  na stronie Etykiety, a ustawienie *ContentType* programu PowerShell również wyświetla tę samą wartość. W przypadku dokumentów ten zakres musi obejmować pliki i **& e-mail**, które są wyświetlane jako **Plik, Poczta e-mail**. Następnie:

- Jeśli zakres obejmuje **grupy & witryn**, możesz zastosować etykietę do witryny, co pozwala ustawić domyślny typ linku udostępniania dla tej witryny. Aby uzyskać informacje na temat stosowania etykiet wrażliwości do witryny, zobacz [Jak stosować etykiety wrażliwości do kontenerów](sensitivity-labels-teams-groups-sites.md#how-to-apply-sensitivity-labels-to-containers).

- Jeśli zakres etykiety wrażliwości obejmuje folder Pliki & e-mail **, możesz** zastosować etykietę do dokumentów, co pozwala ustawić domyślny typ linku udostępniania dla tego dokumentu. Etykietę można stosować [ręcznie lub](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) [automatycznie](apply-sensitivity-label-automatically.md).

> [!TIP]
> Możesz również określić, że etykieta jest domyślną etykietą wrażliwości, która ma być stosowana w nowych witrynach lub dokumentach, jako ustawienie [zasad etykiet](sensitivity-labels.md#what-label-policies-can-do).

### <a name="powershell-tips-for-specifying-the-advanced-settings"></a>Porady dotyczące programu PowerShell dotyczące określania ustawień zaawansowanych

Etykietę wrażliwości można określić według jej nazwy, jednak zalecane jest użycie identyfikatora GUID etykiety w celu uniknięcia potencjalnego zamieszania w określeniu nazwy etykiety lub nazwy wyświetlanej. Aby znaleźć identyfikator GUID i potwierdzić zakres etykiety:

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid, ContentType
````

Aby usunąć którekolwiek z tych ustawień zaawansowanych z etykiety wrażliwości, użyj tej samej składni parametru AdvancedSettings, ale określ wartość ciągu null. Przykład:

````powershell
Set-Label -Identity 8faca7b8-8d20-48a3-8ea2-0f96310a848e -AdvancedSettings @{DefaultSharingScope=""}
````

