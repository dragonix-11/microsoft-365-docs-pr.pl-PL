---
title: Wyświetlanie licencji i usług Microsoft 365 przy użyciu programu PowerShell
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
description: Objaśnienie sposobu używania programu PowerShell do wyświetlania informacji o planach licencjonowania, usługach i licencjach dostępnych w organizacji Microsoft 365.
ms.openlocfilehash: 8b5ff01f15e4dea7a44b423609b6533cc5729a5f
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823899"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>Wyświetlanie licencji i usług Microsoft 365 przy użyciu programu PowerShell

*Ten artykuł dotyczy zarówno Microsoft 365 Enterprise, jak i Office 365 Enterprise.*

Każda subskrypcja Microsoft 365 składa się z następujących elementów:

- **Plany licencjonowania** Są one również nazywane planami licencji lub planami Microsoft 365. Plany licencjonowania definiują usługi Microsoft 365 dostępne dla użytkowników. Subskrypcja Microsoft 365 może zawierać wiele planów licencjonowania. Przykładowy plan licencjonowania byłby Microsoft 365 E3.
    
- **Usług** Są one również nazywane planami usług. Usługi to Microsoft 365 produktów, funkcji i możliwości, które są dostępne w każdym planie licencjonowania, na przykład Exchange Online i Aplikacje Microsoft 365 dla przedsiębiorstw (wcześniej nazwane Office 365 ProPlus). Użytkownicy mogą mieć przypisanych do nich wiele licencji z różnych planów licencjonowania, które udzielają dostępu do różnych usług.
    
- **Licencje** Każdy plan licencjonowania zawiera liczbę zakupionych licencji. Licencje są przypisywane do użytkowników, aby mogli oni korzystać z usług Microsoft 365 zdefiniowanych w planie licencjonowania. Każde konto użytkownika wymaga co najmniej jednej licencji z jednego planu licencjonowania, aby mógł zalogować się do Microsoft 365 i korzystać z usług.
    
Program PowerShell umożliwia Microsoft 365 wyświetlanie szczegółowych informacji o dostępnych planach licencjonowania, licencjach i usługach w organizacji Microsoft 365. Aby uzyskać więcej informacji o produktach, funkcjach i usługach dostępnych w różnych subskrypcjach Office 365, zobacz [Office 365 Opcje planu](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-microsoft-graph-powershell-sdk"></a>Korzystanie z zestawu SDK programu PowerShell firmy Microsoft Graph

Najpierw [połącz się z dzierżawą Microsoft 365](/graph/powershell/get-started#authentication).

Odczytywanie planów licencji subskrypcji wymaga zakresu uprawnień Organization.Read.All lub jednego z innych uprawnień wymienionych na [stronie referencyjnej interfejs Graph API "List subscribedSkus"](/graph/api/subscribedsku-list).

```powershell
Connect-Graph -Scopes Organization.Read.All
```

Aby wyświetlić podsumowanie informacji o bieżących planach licencjonowania i dostępnych licencjach dla każdego planu, uruchom następujące polecenie:
  
```powershell
Get-MgSubscribedSku | Select -Property Sku*, ConsumedUnits -ExpandProperty PrepaidUnits | Format-List
```

Wyniki zawierają:
  
- **SkuPartNumber:** Przedstawia dostępne plany licencjonowania dla organizacji. Na przykład `ENTERPRISEPACK` jest to nazwa planu licencji dla Office 365 Enterprise E3.
    
- **Włączone:** Liczba licencji zakupionych dla określonego planu licencjonowania.
    
- **ConsumedUnits:** Liczba licencji przypisanych do użytkowników z określonego planu licencjonowania.
    
Aby wyświetlić szczegółowe informacje o usługach Microsoft 365, które są dostępne we wszystkich planach licencji, najpierw wyświetl listę planów licencji.

```powershell
Get-MgSubscribedSku
```

Następnie zapisz informacje o planach licencji w zmiennej.

```powershell
$licenses = Get-MgSubscribedSku
```

Następnie wyświetl usługi w określonym planie licencji.

```powershell
$licenses[<index>].ServicePlans
```

\<index> jest liczbą całkowitą, która określa numer wiersza planu licencji z wyświetlania `Get-MgSubscribedSku | Select SkuPartNumber` polecenia, minus 1.

Jeśli na przykład wyświetlenie `Get-MgSubscribedSku | Select SkuPartNumber` polecenia jest następujące:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Następnie polecenie wyświetlania usług dla planu licencji ENTERPRISEPREMIUM jest następujące:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM to trzeci wiersz. W związku z tym wartość indeksu to (3–1) lub 2.

Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), ich dołączone plany usług i odpowiadające im przyjazne nazwy, zobacz [Nazwy produktów i identyfikatory planów usług na potrzeby licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Korzystanie z modułu Azure Active Directory programu PowerShell dla Graph

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Aby wyświetlić podsumowanie informacji o bieżących planach licencjonowania i dostępnych licencjach dla każdego planu, uruchom następujące polecenie:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Wyniki zawierają:
  
- **SkuPartNumber:** Przedstawia dostępne plany licencjonowania dla organizacji. Na przykład `ENTERPRISEPACK` jest to nazwa planu licencji dla Office 365 Enterprise E3.
    
- **Włączone:** Liczba licencji zakupionych dla określonego planu licencjonowania.
    
- **ConsumedUnits:** Liczba licencji przypisanych do użytkowników z określonego planu licencjonowania.
    
Aby wyświetlić szczegółowe informacje o usługach Microsoft 365, które są dostępne we wszystkich planach licencji, najpierw wyświetl listę planów licencji.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Następnie zapisz informacje o planach licencji w zmiennej.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Następnie wyświetl usługi w określonym planie licencji.

```powershell
$licenses[<index>].ServicePlans
```

\<index> jest liczbą całkowitą, która określa numer wiersza planu licencji z wyświetlania `Get-AzureADSubscribedSku | Select SkuPartNumber` polecenia, minus 1.

Jeśli na przykład wyświetlenie `Get-AzureADSubscribedSku | Select SkuPartNumber` polecenia jest następujące:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Następnie polecenie wyświetlania usług dla planu licencji ENTERPRISEPREMIUM jest następujące:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM to trzeci wiersz. W związku z tym wartość indeksu to (3–1) lub 2.

Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), ich dołączone plany usług i odpowiadające im przyjazne nazwy, zobacz [Nazwy produktów i identyfikatory planów usług na potrzeby licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Użyj modułu Microsoft Azure Active Directory dla Windows PowerShell

Najpierw [połącz się z dzierżawą Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Dostępny jest skrypt programu PowerShell, który automatyzuje procedury opisane w tym temacie. W szczególności skrypt umożliwia wyświetlanie i wyłączanie usług w organizacji Microsoft 365, w tym Sway. Aby uzyskać więcej informacji, zobacz [Wyłączanie dostępu do Sway za pomocą programu PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
Aby wyświetlić podsumowanie informacji o bieżących planach licencjonowania i dostępnych licencjach dla każdego planu, uruchom następujące polecenie:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>Program PowerShell Core nie obsługuje modułu Microsoft Azure Active Directory dla modułu Windows PowerShell i poleceń cmdlet z nazwą **msol**. Aby kontynuować korzystanie z tych poleceń cmdlet, należy uruchomić je z Windows PowerShell.
>

Wyniki zawierają następujące informacje:
  
- **AccountSkuId:** Pokaż dostępne plany licencjonowania dla organizacji przy użyciu składni `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ to wartość podana podczas rejestracji w Microsoft 365 i jest unikatowa dla Twojej organizacji. Wartość _\<LicensingPlan>_ jest taka sama dla wszystkich. Na przykład w wartości `litwareinc:ENTERPRISEPACK`nazwa firmy to `litwareinc`, i nazwa `ENTERPRISEPACK`planu licencjonowania , która jest nazwą systemu Office 365 Enterprise E3.
    
- **ActiveUnits:** Liczba licencji zakupionych dla określonego planu licencjonowania.
    
- **WarningUnits:** Liczba licencji w planie licencjonowania, które nie zostały odnowione, a które wygasną po upływie 30-dniowego okresu prolongaty.
    
- **ConsumedUnits:** Liczba licencji przypisanych do użytkowników z określonego planu licencjonowania.
    
Aby wyświetlić szczegółowe informacje o usługach Microsoft 365 dostępnych we wszystkich planach licencji, uruchom następujące polecenie:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

W poniższej tabeli przedstawiono plany usług Microsoft 365 i ich przyjazne nazwy dla najpopularniejszych usług. Lista planów usług może być inna. 
  
|**Plan usługi**|**Opis**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Aplikacje Microsoft 365 dla przedsiębiorstw *(wcześniej o nazwie Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype dla firm Online  <br/> |
| `SHAREPOINTWAC` <br/> |Pakiet Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online plan 2  <br/> |
   
Aby uzyskać pełną listę planów licencji (znanych również jako nazwy produktów), ich dołączone plany usług i odpowiadające im przyjazne nazwy, zobacz [Nazwy produktów i identyfikatory planów usług na potrzeby licencjonowania](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Aby wyświetlić szczegółowe informacje o usługach Microsoft 365, które są dostępne w określonym planie licencjonowania, użyj następującej składni.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

W tym przykładzie przedstawiono usługi dostępne w planie licencjonowania litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie Microsoft 365 kontami użytkowników, licencjami i grupami przy użyciu programu PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[Zarządzanie platformą Microsoft 365 za pomocą programu PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Wprowadzenie do programu PowerShell dla Microsoft 365](getting-started-with-microsoft-365-powershell.md)