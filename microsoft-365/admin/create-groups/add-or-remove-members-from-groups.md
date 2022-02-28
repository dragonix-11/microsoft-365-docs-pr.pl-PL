---
title: Dodawanie lub usuwanie członków z Microsoft 365 grup
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
ms.assetid: e186d224-a324-4afa-8300-0e4fc0c3000a
description: Dowiedz się, jak dodać członka do grupy, usunąć członka z grupy i zarządzać statusem właściciela grupy w centrum administracyjne platformy Microsoft 365.
ms.openlocfilehash: 610da28d6282cb45cb43e086fb3f80acaf18bb05
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983922"
---
# <a name="add-or-remove-members-from-microsoft-365-groups-using-the-admin-center"></a>Dodawanie lub usuwanie członków z Microsoft 365 przy użyciu centrum administracyjnego

Na Microsoft 365 członkowie grupy zazwyczaj tworzą własne grupy, dodają siebie do grup, do których chcą dołączyć, lub są zapraszani przez właścicieli grup. Jeśli właściciel grupy się zmieni lub członek powinien zostać dodany lub usunięty, jako administrator możesz również wprowadzić zmianę. Te zmiany może wprowadzić tylko administrator globalny, administrator Exchange, administrator grup lub administrator użytkownika. [Co to jest Microsoft 365 grupy?](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

> [!TIP]
> Jeśli nie jesteś administratorem, możesz [dodawać lub usuwać członków za pomocą programu Outlook](https://support.microsoft.com/office/3b650f4a-5c9b-4f94-a1bb-0cca4b1091de).
  
## <a name="add-a-member-to-a-group-in-the-admin-center"></a>Dodawanie członka do grupy w centrum administracyjnym

1. W centrum administracyjnym przejdź do [**strony Aktywne**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupy.  

2. Kliknij nazwę grupy.

3. W okienku szczegółów na karcie **Członkowie** wybierz pozycję Wyświetl **wszystkich** członków i zarządzaj nimi, a następnie wybierz pozycję **Dodaj członków**.

4. Wyszukaj lub wybierz nazwę członka, którego chcesz dodać.

5. Wybierz **Zapisz**.

## <a name="add-a-group-to-a-member-in-the-admin-center"></a>Dodawanie grupy do członka w centrum administracyjnym

1. W centrum administracyjnym przejdź do strony [**Aktywni użytkownicy**](https://admin.microsoft.com/Adminportal/Home?#/users) .  

2. Kliknij użytkownika.

3. W okienku szczegółów na karcie **Konto** wybierz pozycję **Zarządzaj grupami**.

4. Wyszukaj lub wybierz nazwę grupy, którą chcesz dodać.

5. Wybierz **Zapisz**.

## <a name="remove-a-member-from-a-group-in-the-admin-center"></a>Usuwanie członka z grupy w centrum administracyjnym

> [!NOTE]
> Gdy usuniesz członka z grupy prywatnej, zablokowanie tej osoby w grupie trwa 5 minut.

1. W centrum administracyjnym przejdź do [**strony Aktywne**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupy.  

2. Kliknij nazwę grupy.

3. W okienku szczegółów na karcie **Członkowie** wybierz pozycję **Wyświetl wszystkich członków i zarządzaj nimi**.

4. Wybierz znak X obok członka, którego chcesz usunąć.

5. Wybierz **pozycję Zapisz** , aby usunąć członka.

## <a name="manage-group-owner-status"></a>Zarządzanie stanem właściciela grupy

Osoba, która utworzyła grupę, jest domyślnie jej właścicielem. Często grupa ma wielu właścicieli w celu zapewnienia zapasowej pomocy technicznej lub z innych powodów. Status członka grupy można podwyższyć do poziomu właściciela grupy, a status właściciela grupy można obniżyć do poziomu członka.
  
### <a name="promote-a-member-to-owner-status-in-the-admin-center"></a>Podsuń status członka do statusu właściciela w centrum administracyjnym

1. W centrum administracyjnym przejdź do [**strony Aktywne**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupy.  

2. Kliknij nazwę grupy.

3. W okienku szczegółów na karcie **Członkowie** wybierz pozycję **Wyświetl wszystkie właścicieli i zarządzaj nimi**.

4. Wybierz **pozycję Dodaj właścicieli**.

5. Zaznacz pole wyboru obok nazwy członka, którego chcesz dodać.

6. Wybierz **pozycję Zapisz**, a następnie **pozycję Zamknij**.

### <a name="remove-owner-status-in-the-admin-center"></a>Usuwanie stanu właściciela w centrum administracyjnym

1. W centrum administracyjnym przejdź do [**strony Aktywne**](https://admin.microsoft.com/Adminportal/Home?#/groups) grupy.  

2. Kliknij nazwę grupy.

3. W okienku szczegółów na karcie **Członkowie** wybierz pozycję **Wyświetl wszystkie właścicieli i zarządzaj nimi**.

4. Wybierz pozycję X obok nazwy właściciela.

5. Wybierz **Zapisz**.

## <a name="next-steps"></a>Następne kroki

- [Dynamiczne zarządzanie grupami w usłudze Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal): zobacz sekcję „Jak dynamicznie zarządzać członkostwem w grupie?".

- Aby dodać setki lub tysiące użytkowników do grup, użyj funkcji [Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks).

- [Przypisywanie nowego właściciela do grupy oddzielonej](https://support.microsoft.com/office/86bb3db6-8857-45d1-95c8-f6d540e45732)

## <a name="related-content"></a>Zawartość pokrewna

[Uaktualnianie list dystrybucyjnych Microsoft 365 grup w Outlook](../manage/upgrade-distribution-lists.md) (artykuł)\
[Dlaczego warto uaktualnić listy dystrybucyjne do grup w Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188) (artykuł)\
[Zarządzanie dostępem gości w Microsoft 365](manage-guest-access-in-groups.md) grup (artykuł)\
[Zarządzanie Microsoft 365 grupami za pomocą programu PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md): ten artykuł zawiera wprowadzenie do kluczowych poleceń cmdlet i przykłady (artykuł)\
[Microsoft 365 nazewnictwa grup](../../solutions/groups-naming-policy.md) (artykuł)