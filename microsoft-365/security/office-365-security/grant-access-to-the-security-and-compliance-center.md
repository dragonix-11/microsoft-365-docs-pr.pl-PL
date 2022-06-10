---
title: Udzielanie użytkownikom dostępu do Centrum zabezpieczeń i zgodności
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
description: Użytkownicy muszą mieć przypisane uprawnienia w centrum Microsoft 365 Security & Compliance Center, zanim będą mogli zarządzać dowolną z jej funkcji zabezpieczeń lub zgodności.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e0ca3874f03d9f0c386a84c9e8b56ea58bbfe72
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66018013"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Udzielanie użytkownikom dostępu do Centrum zabezpieczeń i zgodności

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Użytkownicy muszą mieć przypisane uprawnienia w Centrum zgodności & zabezpieczeń, zanim będą mogli zarządzać dowolną z jej funkcji zabezpieczeń lub zgodności. Jako administrator globalny lub członek grupy ról OrganizacjaZarządzanie w Centrum zgodności & zabezpieczeń możesz przyznać te uprawnienia użytkownikom. Użytkownicy będą mogli zarządzać tylko funkcjami zabezpieczeń lub zgodności, do których mają dostęp.

Aby uzyskać więcej informacji o różnych uprawnieniach, które można przyznać użytkownikom w Centrum zgodności & zabezpieczeń, zapoznaj się z tematem [Uprawnienia w Centrum zgodności & zabezpieczeń](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Co należy wiedzieć przed rozpoczęciem?

- Aby wykonać kroki opisane w tym artykule, musisz być administratorem globalnym lub członkiem grupy ról OrganizacjaZarządzanie w Centrum zgodności & zabezpieczeń.

- Grupy ról centrum zgodności & zabezpieczeń mogą mieć podobne nazwy do grup ról w Exchange Online, ale nie są takie same.

- Członkostwa w grupach ról nie są współużytkowane między Exchange Online i Centrum zgodności & zabezpieczeń.

- Partnerzy uprawnień dostępu delegowanego (DAP) z uprawnieniami administrowania w imieniu (AOBO) nie mogą uzyskać dostępu do Centrum zgodności & zabezpieczeń.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Użyj Centrum zgodności & zabezpieczeń, aby udzielić innemu użytkownikowi dostępu do Centrum zgodności & zabezpieczeń

1. Otwórz centrum zgodności & zabezpieczeń pod adresem <https://protection.office.com> , a następnie przejdź do pozycji **Uprawnienia**. Aby przejść bezpośrednio do karty **Uprawnienia** , otwórz pozycję <https://protection.office.com/permissions>.

2. Z listy grup ról wybierz grupę ról, a następnie kliknij pozycję **Edytuj ikonę Edytuj**![.](../../media/O365-MDM-CreatePolicy-EditIcon.gif)

3. Na stronie właściwości grupy ról w obszarze **Członkowie** kliknij pozycję **Dodaj**![ikonę.](../../media/ITPro-EAC-AddIcon.gif) i wybierz nazwę użytkownika (lub użytkowników), którego chcesz dodać.

4. Po wybraniu wszystkich użytkowników, których chcesz dodać do grupy ról, kliknij przycisk **dodaj,\>** a następnie przycisk **OK**.

5. Po zakończeniu kliknij przycisk **Zapisz**.

## <a name="use-security--compliance-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Użyj programu PowerShell zgodności & zabezpieczeń, aby udzielić innemu użytkownikowi dostępu do Centrum zgodności & zabezpieczeń

1. [Połączenie do programu PowerShell zgodności & zabezpieczeń](/powershell/exchange/connect-to-scc-powershell).

2. Należy stosować następującą składnię:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Aby uzyskać szczegółowe informacje o problemach ze składnią i parametrami, zobacz [Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Skąd wiadomo, że to działanie się powiodło?

Aby sprawdzić, czy pomyślnie udzielono dostępu do Centrum zgodności & zabezpieczeń, wykonaj jedną z następujących czynności:

- W Centrum zgodności & zabezpieczeń przejdź do pozycji **Uprawnienia** i wybierz grupę ról. W wyświetlonym wysuwu szczegółów sprawdź członków grupy ról.

- W obszarze Security & Compliance PowerShell zastąp \<RoleGroupName\> ciąg nazwą grupy ról i uruchom następujące polecenie:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Aby uzyskać szczegółowe informacje o składni i parametrach, zobacz [Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).
