---
title: Wyświetlanie Microsoft 365 i usług za pomocą programu PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: W tym artykule wyjaśniono, jak za pomocą programu PowerShell wyświetlać informacje o planach licencjonowania, usługach i licencjach dostępnych w Twojej Microsoft 365 organizacji.
ms.openlocfilehash: 3b90596c68e3beadcc2b33ef59ff9c3503b84f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986588"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>Wyświetlanie Microsoft 365 i usług za pomocą programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Każda Microsoft 365 składa się z następujących elementów:

- **Plany licencjonowania** Te plany są również nazywane planami Microsoft 365 licencji. Plany licencjonowania określają Microsoft 365 usługach, które są dostępne dla użytkowników. Subskrypcja Microsoft 365 może zawierać wiele planów licencjonowania. Przykładowy plan licencjonowania zostałby Microsoft 365 E3.
    
- **Usługi** Te plany są również nazywane planami usług. Usługi to Microsoft 365, funkcje i możliwości dostępne w każdym planie licencjonowania, na przykład usługi Exchange Online i Aplikacje Microsoft 365 dla przedsiębiorstw (o nazwie Office 365 ProPlus). Użytkownicy mogą mieć przypisane wiele licencji z różnych planów licencjonowania, które udzielają dostępu do różnych usług.
    
- **Licencje** Każdy plan licencjonowania zawiera liczbę zakupionych licencji. Licencje przypisuje się do użytkowników, aby można było Microsoft 365 usługach zdefiniowanych w planie licencjonowania. Każde konto użytkownika wymaga co najmniej jednej licencji z jednego planu licencjonowania, aby każdy użytkownik Microsoft 365 korzystać z usług.
    
Za pomocą programu PowerShell dla Microsoft 365 możesz wyświetlić szczegółowe informacje o dostępnych planach licencjonowania, licencjach i usługach w Twojej Microsoft 365 organizacji. Aby uzyskać więcej informacji o produktach, funkcjach i usługach dostępnych w różnych Office 365 subskrypcji, zobacz Office 365 [Opcje planu](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Używanie modułu Azure Active Directory PowerShell dla Graph danych

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Aby wyświetlić informacje podsumowujące dotyczące bieżących planów licencjonowania i dostępnych licencji dla każdego planu, uruchom to polecenie:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Wyniki zawierają:
  
- **SkuPartNumber:** Pokazuje dostępne plany licencjonowania dla organizacji. Na przykład nazwa `ENTERPRISEPACK` planu licencji dla planu Office 365 Enterprise E3.
    
- **Włączone:** Liczba licencji zakupionych dla określonego planu licencjonowania.
    
- **ConsumedUnits:** Liczba licencji przypisanych do użytkowników z określonego planu licencjonowania.
    
Aby wyświetlić szczegółowe informacje o Microsoft 365, które są dostępne we wszystkich planach licencyjnych, najpierw wyświetl listę planów licencji.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie przechowuj informacje o planach licencji w zmiennej.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Następnie wyświetl usługi w określonym planie licencyjnym.

```powershell
$licenses[<index>].ServicePlans
```

\<index> jest liczbą całkowitą określającą numer wiersza `Get-AzureADSubscribedSku | Select SkuPartNumber` planu licencji z wyświetlanego polecenia minus 1.

Jeśli na przykład polecenie jest wyświetlane w `Get-AzureADSubscribedSku | Select SkuPartNumber` ten sposób:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Następnie polecenie wyświetlania usług dla planu licencji ENTERPRISEPREMIUM jest takie:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM to trzeci wiersz. Dlatego wartość indeksu wynosi (3 – 1) lub 2.

Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), dołączone do nich plany usług i odpowiadające im przyjazne nazwy, zobacz Nazwy produktów i identyfikatory planów usług w celu [licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365 dzierżawy](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Dostępny jest skrypt programu PowerShell automatyzujący procedury opisane w tym temacie. W szczególności skrypt umożliwia wyświetlanie i wyłączanie usług w Twojej organizacji Microsoft 365, w tym aplikacji Sway. Aby uzyskać więcej informacji, zobacz [Wyłączanie dostępu do aplikacji Sway za pomocą programu PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
Aby wyświetlić podsumowanie bieżących planów licencjonowania i dostępnych licencji dla każdego planu, uruchom następujące polecenie:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla programu Windows PowerShell i poleceń cmdlet z **nazwą Msol**. Aby nadal korzystać z tych cmdlet, należy je uruchomić z Windows PowerShell.
>

Wyniki zawierają następujące informacje:
  
- **AccountSkuId:** Pokaż dostępne plany licencjonowania dla organizacji przy użyciu składni `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ jest wartością podaną podczas zarejestrowania w usłudze Microsoft 365 i jest unikatowa dla Twojej organizacji. Wartość _\<LicensingPlan>_ jest taka sama dla wszystkich. Na przykład w wartości `litwareinc:ENTERPRISEPACK`, nazwa `litwareinc`firmy to , a nazwa planu `ENTERPRISEPACK`licencjonowania , która jest nazwą systemu dla planu Office 365 Enterprise E3.
    
- **ActiveUnits:** Liczba licencji zakupionych dla określonego planu licencjonowania.
    
- **OstrzeżenieJednostki:** Liczba nie odnowień licencji w planie licencjonowania, które wygasną po 30-dniowym okresie prolongaty.
    
- **ConsumedUnits:** Liczba licencji przypisanych do użytkowników z określonego planu licencjonowania.
    
Aby wyświetlić szczegółowe informacje o Microsoft 365, które są dostępne we wszystkich planach licencyjnych, uruchom następujące polecenie:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

W poniższej tabeli przedstawiono Microsoft 365 usług oraz ich przyjazne nazwy dla najczęściej oferowanych usług. Lista planów usług może się różnić. 
  
|**Plan serwisowy**|**Opis**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Aplikacje Microsoft 365 dla przedsiębiorstw *(wcześniej Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype dla firm Online  <br/> |
| `SHAREPOINTWAC` <br/> |Pakiet Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), dołączone do nich plany usług i odpowiadające im przyjazne nazwy, zobacz Nazwy produktów i identyfikatory planów usług w celu [licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Aby wyświetlić szczegółowe informacje o usługach Microsoft 365 dostępnych w określonym planie licencjonowania, użyj następującej składni.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

W tym przykładzie pokazano usługi dostępne w planie licencjonowania litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 użytkownikami, licencjami i grupami za pomocą programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)