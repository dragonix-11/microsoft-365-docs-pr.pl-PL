---
title: Uprawnienia w portalu usługi Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Administratorzy mogą dowiedzieć się, jak zarządzać uprawnieniami w portalu Microsoft 365 Defender dla wszystkich zadań związanych z zabezpieczeniami.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3381d3eb823b818aec01a181f176cb56f6af310c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939196"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Uprawnienia w portalu usługi Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Usługi Microsoft Defender dla usługi Office 365 (plan 1 i plan 2)](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Musisz zarządzać scenariuszami zabezpieczeń obejmującymi wszystkie usługi Microsoft 365. Potrzebujesz też elastyczności, aby przyznać odpowiednie uprawnienia administratora odpowiednim osobom w organizacji.

Portal Microsoft 365 Defender w witrynie <https://security.microsoft.com> obsługuje bezpośrednie zarządzanie uprawnieniami dla użytkowników wykonujących zadania zabezpieczeń w Microsoft 365. Za pomocą portalu Microsoft 365 Defender do zarządzania uprawnieniami można centralnie zarządzać uprawnieniami dla wszystkich zadań związanych z zabezpieczeniami.

Aby zarządzać uprawnieniami w portalu Microsoft 365 Defender, przejdź do pozycji **Uprawnienia & ról** lub <https://security.microsoft.com/securitypermissions>. Musisz być **administratorem globalnym** lub członkiem grupy ról **Zarządzanie organizacją** w portalu Microsoft 365 Defender. W szczególności rola **Zarządzanie rolami** umożliwia użytkownikom wyświetlanie, tworzenie i modyfikowanie grup ról w portalu Microsoft 365 Defender, a domyślnie ta rola jest przypisywana tylko do grupy ról **Zarządzanie organizacją**.

> [!NOTE]
> Aby uzyskać informacje o uprawnieniach w portalu zgodności usługi Microsoft Purview, zobacz [Uprawnienia w portalu zgodności usługi Microsoft Purview](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Relacja członków, ról i grup ról

Uprawnienia w portalu Microsoft 365 Defender są oparte na modelu uprawnień kontroli dostępu opartej na rolach (RBAC). Kontrola dostępu oparta na rolach to ten sam model uprawnień, który jest używany przez większość usług Microsoft 365, więc jeśli znasz strukturę uprawnień w tych usługach, udzielanie uprawnień w portalu Microsoft 365 Defender będzie bardzo znane.

**Rola** udziela uprawnień do wykonywania zestawu zadań.

**Grupa ról** to zestaw ról, który umożliwia użytkownikom wykonywanie zadań w portalu Microsoft 365 Defender.

Portal Microsoft 365 Defender> zawiera domyślne grupy ról dla najbardziej typowych zadań i funkcji, które należy przypisać. Ogólnie rzecz biorąc, zalecamy po prostu dodanie poszczególnych użytkowników jako **członków** do domyślnych grup ról.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="Relacja grupy ról z jej rolami i członkami" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Role i grupy ról w portalu Microsoft 365 Defender

Następujące typy ról i grup ról są dostępne na stronie <https://security.microsoft.com/securitypermissions> **Uprawnienia & ról** w portalu Microsoft 365 Defender:

- **Role usługi Azure AD**: możesz wyświetlać role i przypisanych użytkowników, ale nie możesz zarządzać nimi bezpośrednio w portalu Microsoft 365 Defender. Role usługi Azure AD to role centralne, które przypisują uprawnienia do **wszystkich** usług Microsoft 365.

- **Role współpracy & poczty e-mail**: są to te same grupy ról, które są dostępne w Centrum zgodności & zabezpieczeń, ale można nimi zarządzać bezpośrednio w portalu Microsoft 365 Defender. Uprawnienia przypisane w tym miejscu są specyficzne dla portalu Microsoft 365 Defender, portalu zgodności usługi Microsoft Purview i Centrum zgodności & zabezpieczeń i nie obejmują wszystkich uprawnień wymaganych w innych obciążeniach Microsoft 365.

:::image type="content" source="../../media/m365-sc-permissions-and-roles-page.png" alt-text="Strona Uprawnienia & role w portalu Microsoft 365 Defender" lightbox="../../media/m365-sc-permissions-and-roles-page.png":::

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Role usługi Azure AD w portalu Microsoft 365 Defender

Po otwarciu portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>  i przejściu do ról \> **współpracy & poczty e-mail** **uprawnienia & ról** \> **usługi Azure AD** \> (lub bezpośrednio do <https://security.microsoft.com/aadpermissions>) zostaną wyświetlone role usługi Azure AD opisane w tej sekcji.

Po wybraniu roli zostanie wyświetlony wysuwany szczegół zawierający opis roli i przypisania użytkownika. Aby jednak zarządzać tymi przydziałami, należy kliknąć pozycję **Zarządzaj członkami w usłudze Azure AD** w wysuwnym oknie szczegółów.

:::image type="content" source="../../media/permissions-manage-in-azure-ad-link.png" alt-text="Link do zarządzania uprawnieniami w Azure Active Directory" lightbox="../../media/permissions-manage-in-azure-ad-link.png":::

Aby uzyskać więcej informacji, zobacz [Wyświetlanie i przypisywanie ról administratora w Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|Rola|Opis|
|---|---|
|**Administrator globalny**|Dostęp do wszystkich funkcji administracyjnych we wszystkich usługach Microsoft 365. Tylko administratorzy globalni mogą przypisywać inne role administratora. Aby uzyskać więcej informacji, zobacz [Administrator globalny/ Administrator firmy](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrator danych zgodności**|Śledź dane organizacji w Microsoft 365, upewnij się, że są chronione, i uzyskaj wgląd w wszelkie problemy, które pomogą ograniczyć ryzyko. Aby uzyskać więcej informacji, zobacz [Administrator danych zgodności](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Administrator zgodności**|Pomóż organizacji zachować zgodność z wszelkimi wymaganiami prawnymi, zarządzaj przypadkami zbierania elektronicznych materiałów dowodowych i zachowaj zasady ładu danych w Microsoft 365 lokalizacjach, tożsamościach i aplikacjach. Aby uzyskać więcej informacji, zobacz [Administrator zgodności](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Operator zabezpieczeń**|Wyświetlanie, badanie i reagowanie na aktywne zagrożenia dla Microsoft 365 użytkowników, urządzeń i zawartości. Aby uzyskać więcej informacji, zobacz [Operator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Czytelnik zabezpieczeń**|Wyświetlanie i badanie aktywnych zagrożeń dla Microsoft 365 użytkowników, urządzeń i zawartości, ale (w przeciwieństwie do operatora zabezpieczeń) nie mają oni uprawnień do reagowania, podejmując działania. Aby uzyskać więcej informacji, zobacz [Czytelnik zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Administrator zabezpieczeń**|Kontroluj ogólne bezpieczeństwo organizacji, zarządzając zasadami zabezpieczeń, przeglądając analizę zabezpieczeń i raporty w Microsoft 365 produktach oraz pozostając na bieżąco z poziomem zagrożeń. Aby uzyskać więcej informacji, zobacz [Administrator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Czytelnik globalny**|Wersja tylko do odczytu roli **administrator globalny**. Wyświetl wszystkie ustawienia i informacje administracyjne w Microsoft 365. Aby uzyskać więcej informacji, zobacz [Czytelnik globalny](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrator symulacji ataków**|Tworzenie i zarządzanie wszystkimi aspektami tworzenia [symulacji ataku](attack-simulation-training.md) , uruchamiania/planowania symulacji oraz przeglądu wyników symulacji. Aby uzyskać więcej informacji, zobacz [Administrator symulacji ataków](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Autor ładunku ataku**|Twórz ładunki ataku, ale nie uruchamiaj ich ani nie planuj. Aby uzyskać więcej informacji, zobacz [Attack Payload Author (Autor ładunku ataku](/azure/active-directory/roles/permissions-reference#attack-payload-author)).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>Role współpracy & poczty e-mail w portalu Microsoft 365 Defender

Po otwarciu portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>  i przejściu do ról \> **współpracy & poczty e-mail** **uprawnienia & ról** \> **e-mail & role** \> współpracy (lub bezpośrednio do <https://security.microsoft.com/emailandcollabpermissions>) zostaną wyświetlone te same grupy ról, które są dostępne w Centrum zgodności & zabezpieczeń.

Aby uzyskać pełne informacje o tych grupach ról, zobacz [Uprawnienia w Centrum zgodności & zabezpieczeń](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Modyfikowanie członkostwa w roli współpracy & poczty e-mail w portalu Microsoft 365 Defender

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do ról \> **współpracy & poczty e-mail** **Uprawnienia & ról** \> **E-mail & role** \> współpracy. Aby przejść bezpośrednio do strony **Uprawnienia** , użyj polecenia <https://security.microsoft.com/emailandcollabpermissions>.

2. Na stronie **Uprawnienia** wybierz grupę ról, którą chcesz zmodyfikować z listy. Możesz kliknąć nagłówek kolumny **Nazwa**, aby posortować listę według nazwy, lub kliknąć ikonę **Wyszukaj**![.](../../media/m365-cc-sc-search-icon.png) , aby znaleźć grupę ról.

3. W wyświetlonym wysuwu szczegółów grupy ról kliknij pozycję **Edytuj** w sekcji **Członkowie** .

4. Na wyświetlonej stronie **Edytowanie wybierz członków** wykonaj jedną z następujących czynności:
   - Jeśli nie ma żadnych członków grupy ról, kliknij pozycję **Wybierz członków**.
   - Jeśli istnieją członkowie grupy ról, kliknij przycisk **Edytuj**

5. W wyświetlonym wysuwu **Wybieranie członków** wykonaj jedną z następujących czynności:

   - Kliknij pozycję **Dodaj**. Na wyświetlonej liście użytkowników wybierz co najmniej jednego użytkownika. Możesz też kliknąć ikonę **Wyszukaj**![.](../../media/m365-cc-sc-search-icon.png) aby znaleźć i wybrać użytkowników.

     Po wybraniu użytkowników, których chcesz dodać, kliknij przycisk **Dodaj**.

   - Kliknij **Usuń**. Wybierz co najmniej jeden z istniejących elementów członkowskich. Możesz też kliknąć ikonę **Wyszukaj**![.](../../media/m365-cc-sc-search-icon.png) , aby znaleźć i wybrać członków.

     Po wybraniu użytkowników, których chcesz usunąć, kliknij przycisk **Usuń**.

6. Po powrocie do wysuwanego **wybierania członków** kliknij pozycję **Gotowe**.

7. Na stronie **Edytowanie wybierz członków** kliknij pozycję **Zapisz**.

8. Po powrocie do wysuwanego szczegółów grupy ról kliknij pozycję **Gotowe**.
