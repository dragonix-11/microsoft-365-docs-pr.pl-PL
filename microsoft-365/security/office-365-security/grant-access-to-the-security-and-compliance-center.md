---
title: Umożliwianie użytkownikom dostępu do Centrum & zgodności
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.PermissionsHelp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: Aby użytkownicy mieli dostęp do jakichkolwiek funkcji zabezpieczeń lub zgodności, Microsoft 365 w Centrum zgodności usługi Microsoft 365 & i zgodności muszą mieć przypisane uprawnienia.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5af3d045b174c4405dc2060fea1db22b3b4066ac
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680692"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Umożliwianie użytkownikom dostępu do Centrum & zgodności

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Użytkownicy muszą mieć przypisane uprawnienia w Centrum zabezpieczeń & zgodności, aby mogą zarządzać dowolnymi jego funkcjami zabezpieczeń lub zgodności. Te uprawnienia możesz nadać użytkownikom jako administrator globalny lub członek grupy ról OrganizationManagement w Centrum & zabezpieczeń i zgodności. Użytkownicy będą mogli zarządzać tylko funkcjami zabezpieczeń lub zgodności, do których mają dostęp.

Aby uzyskać więcej informacji na temat poszczególnych uprawnień, które można nadać użytkownikom w Centrum zabezpieczeń & zgodności, zobacz Uprawnienia w Centrum zabezpieczeń & [zgodności](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby wykonać czynności opisane w tym artykule, musisz być administratorem globalnym lub członkiem grupy ról OrganizationManagement w Centrum & zabezpieczeń i zgodności.

- Grupy ról w Centrum & zabezpieczeń mogą mieć podobne nazwy jak grupy ról w programie Exchange Online, ale nie są takie same.

- Członkostwa w grupach ról nie są udostępniane między Exchange Online a Centrum & zgodności.

- Partnerzy dap (Delegated Access Permission) z uprawnieniami administrować w imieniu (AOBO) nie mogą uzyskać dostępu do Centrum zabezpieczeń & zgodności.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Korzystanie z Centrum & zgodności w celu zapewnienia iniu użytkownikowi dostępu do Centrum zgodności & zabezpieczeń

1. Otwórz Centrum zabezpieczeń & zgodności, <https://protection.office.com> a następnie przejdź do okna **Uprawnienia**. Aby przejść bezpośrednio do karty **Uprawnienia** , otwórz pozycję <https://protection.office.com/permissions>.

2. Na liście grup ról wybierz grupę ról, a następnie kliknij pozycję **Edytuj ikonę** ![Edytuj](../../media/O365-MDM-CreatePolicy-EditIcon.gif).

3. Na stronie właściwości grupy ról w obszarze **Członkowie** kliknij pozycję **AddAdd**![ Icon.](../../media/ITPro-EAC-AddIcon.gif) i wybierz nazwę użytkownika (lub użytkowników), którego chcesz dodać.

4. Po wybraniu wszystkich użytkowników, których chcesz dodać do grupy ról, kliknij pozycję **dodaj -\>** i **OK**.

5. Po zakończeniu kliknij przycisk **Zapisz**.

## <a name="use-security--compliance-center-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Użyj programu PowerShell & zabezpieczeń i zgodności, aby dać iniu mu dostęp do Centrum & zabezpieczeń i zgodności

1. [Połączenie do programu PowerShell & w Centrum zabezpieczeń i zgodności](/powershell/exchange/connect-to-scc-powershell).

2. Należy stosować następującą składnię:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Aby uzyskać szczegółowe informacje na temat problemów ze składnią i parametrami, [zobacz Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Skąd wiadomo, że to działanie się powiodło?

Aby sprawdzić, czy pomyślnie udzielono dostępu do Centrum zgodności & zabezpieczeń, wykonaj jedną z następujących czynności:

- W Centrum zabezpieczeń & zgodności przejdź do **przycisku** Uprawnienia i wybierz grupę ról. W czacie wysuwu szczegółów sprawdź członków grupy ról.

- W & zabezpieczeń i zgodności programu PowerShell \<RoleGroupName\> zastąp nazwę grupy ról i uruchom następujące polecenie:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, [zobacz Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).