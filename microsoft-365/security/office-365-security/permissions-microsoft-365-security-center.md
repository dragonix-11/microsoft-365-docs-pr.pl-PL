---
title: Uprawnienia w Microsoft 365 Defender portalu
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
description: Administratorzy mogą dowiedzieć się, jak zarządzać uprawnieniami w portalu Microsoft 365 Defender wszystkich zadań związanych z zabezpieczeniami.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e819a9de9d5ccd66caab4bc13d8b11c1a95ab03
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681727"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Uprawnienia w Microsoft 365 Defender portalu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Dotyczy**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender dla Office 365 plan 1 i plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Musisz zarządzać scenariuszami zabezpieczeń, które obejmują wszystkie Microsoft 365 zabezpieczeń. Potrzebujesz też elastycznego nadawać odpowiednie uprawnienia administratora odpowiednim osobom w organizacji.

Portal Microsoft 365 Defender obsługuje bezpośrednie <https://security.microsoft.com> zarządzanie uprawnieniami użytkowników, którzy wykonują zadania związane z zabezpieczeniami w Microsoft 365. Zarządzanie uprawnieniami za pomocą portalu Microsoft 365 Defender umożliwia centralne zarządzanie uprawnieniami do wszystkich zadań związanych z zabezpieczeniami.

Aby zarządzać uprawnieniami w portalu Microsoft 365 Defender, przejdź do **& uprawnienia lub** <https://security.microsoft.com/securitypermissions>. Musisz być administratorem **globalnym** lub członkiem grupy ról Zarządzanie organizacją  w portalu Microsoft 365 Defender sieci. W szczególności rola Zarządzanie **rolami** umożliwia użytkownikom wyświetlanie, tworzenie i modyfikowanie grup ról w portalu Microsoft 365 Defender i domyślnie ta rola jest przypisywana tylko do grupy ról **Zarządzanie organizacją.**

> [!NOTE]
> Aby uzyskać informacje o uprawnieniach w Centrum zgodności platformy Microsoft 365, zobacz [Uprawnienia w Centrum zgodności platformy Microsoft 365](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Relacja między członkami, rolami i grupami ról

Uprawnienia w portalu Microsoft 365 Defender są oparte na modelu uprawnień kontroli dostępu opartej na rolach (RBAC). RBAC to ten sam model uprawnień, który jest używany przez większość usług firmy Microsoft 365, więc jeśli znasz strukturę uprawnień w tych usługach, udzielanie uprawnień w portalu Microsoft 365 Defender będzie dobrze znane.

Rola **udziela** uprawnień do wykonywania zestawu zadań.

Grupa **ról to** zestaw ról, które umożliwiają innym osobom pełninie swoich zadań w portalu Microsoft 365 Defender zadań.

Portal Microsoft 365 Defender zawiera> domyślnych grup ról dla typowych zadań i funkcji, które musisz przypisać. Ogólnie rzecz biorąc, zalecamy po prostu dodawanie pojedynczych użytkowników jako **członków** do domyślnych grup ról.

![Diagram przedstawiający relację grup ról z rolami i członkami.](../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Role i grupy ról w portalu Microsoft 365 Defender grupy

Następujące typy ról i grup ról są dostępne na stronie Uprawnienia **& w** <https://security.microsoft.com/securitypermissions> portalu Microsoft 365 Defender ról:

- **Role usługi Azure AD**: Możesz wyświetlać role i przypisanych użytkowników, ale nie możesz zarządzać nimi bezpośrednio w portalu Microsoft 365 Defender sieci. Role usługi Azure AD to centralne role, które przypisują uprawnienia do wszystkich **Microsoft 365** usług.

- **Współpraca przy &** e-mail: są to te same grupy ról, które są dostępne w Centrum zgodności usługi & Security &, ale możesz nimi zarządzać bezpośrednio w portalu Microsoft 365 Defender zabezpieczeń. Przypisane tutaj uprawnienia są specyficzne dla portalu usługi Microsoft 365 Defender, usługi Centrum zgodności platformy Microsoft 365 i Centrum zgodności usługi Security & i nie obejmują wszystkich uprawnień, które są potrzebne w innych obciążeniach Microsoft 365.

![Uprawnienia & w portalu Microsoft 365 Defender sieci Web.](../../media/m365-sc-permissions-and-roles-page.png)

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Role usługi Azure AD w portalu Microsoft 365 Defender sieci Microsoft 365 Defender

Po otwarciu portalu usługi Microsoft 365 Defender <https://security.microsoft.com> w witrynie i przejdź **do** \> sekcji Role współpracy usługi & e-mail Uprawnienia **&** \> Role usługi **Azure AD** \> **Role (**<https://security.microsoft.com/aadpermissions>lub bezpośrednio do) zostaną zobaczysz role usługi Azure AD opisane w tej sekcji.

Po wybraniu roli zostanie wyświetlone wysuwne okno wysuwu szczegółów zawierające opis roli i przypisań użytkowników. Aby jednak zarządzać tymi zadaniami, musisz kliknąć pozycję Zarządzaj członkami w **usłudze Azure AD** w wysuwanych szczegółach.

![Link do zarządzania uprawnieniami w aplikacji Azure Active Directory.](../../media/permissions-manage-in-azure-ad-link.png)

Aby uzyskać więcej informacji, [zobacz Wyświetlanie i przypisywanie ról administratora w Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|Rola|Opis|
|---|---|
|**Administrator globalny**|Dostęp do wszystkich funkcji administracyjnych we wszystkich Microsoft 365 usługach. Tylko administratorzy globalni mogą przypisywać inne role administratora. Aby uzyskać więcej informacji, zobacz [Administrator globalny /Administrator firmy](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrator danych zgodności**|Monitoruj dane organizacji w różnych Microsoft 365, upewnij się, że są chronione, i uzyskaj szczegółowe informacje na temat wszelkich problemów, aby zmniejszyć ryzyko. Aby uzyskać więcej informacji, zobacz [Administrator danych zgodności](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Administrator zgodności**|Pomóż organizacji zachować zgodność z wymaganiami prawnymi, zarządzać sprawami zbierania elektronicznych materiałów dowodowych i utrzymywać zasady zarządzania danymi w Microsoft 365 lokalizacjach, tożsamościach i aplikacjach. Aby uzyskać więcej informacji, zobacz [Administrator zgodności](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Operator zabezpieczeń**|Wyświetlaj i badaj aktywne zagrożenia oraz odpowiadaj na nie Microsoft 365 użytkowników, urządzeń i zawartości. Aby uzyskać więcej informacji, zobacz [Operator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Czytelnik zabezpieczeń**|Wyświetlaj i badaj aktywne zagrożenia dla użytkowników Microsoft 365, urządzeń i zawartości, ale (w przeciwieństwie do operatora zabezpieczeń) nie mają one uprawnień do reagowania poprzez podejmowanie działań. Aby uzyskać więcej informacji, zobacz [Czytnik zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Administrator zabezpieczeń**|Możesz kontrolować ogólne bezpieczeństwo organizacji, zarządzając zasadami zabezpieczeń, przeglądając analizy zabezpieczeń i raporty w różnych Microsoft 365 produktach oraz na bieżąco kontrolować zagrożenia. Aby uzyskać więcej informacji, zobacz [Administrator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Czytelnik globalny**|Wersja tylko do odczytu roli **administratora globalnego** . Wyświetlanie wszystkich ustawień i informacji administracyjnych w Microsoft 365. Aby uzyskać więcej informacji, zobacz [Czytnik globalny](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrator symezyjki ataków**|Tworzenie wszystkich aspektów tworzenia symydyty ataków i zarządzanie nimi, uruchamianie/planowanie symulacyjnej oraz przeglądanie wyników symulacyjnych.[](attack-simulation-training.md) Aby uzyskać więcej informacji, zobacz [Administrator symulowania ataków](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Autor ataku ładu**|Twórz łady ataków, ale nie uruchamiaj ich ani nie planuj. Aby uzyskać więcej informacji, zobacz [Autorem ataku opłaty](/azure/active-directory/roles/permissions-reference#attack-payload-author).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>Wysyłanie & e-mail do ról współpracy w portalu Microsoft 365 Defender-mail

Po otwarciu portalu Microsoft 365 Defender <https://security.microsoft.com> w witrynie i przejdź do poczty e-mail **&** \> ról współpracy Uprawnienia **&** \> Role poczty **e-mail** \> & Role **współpracy (**<https://security.microsoft.com/emailandcollabpermissions>lub bezpośrednio do) zobaczysz te same grupy ról, które są dostępne w Centrum zgodności usługi & zabezpieczeń.

Aby uzyskać pełne informacje na temat tych grup ról, zobacz [Uprawnienia w Centrum & zabezpieczeń.](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Modyfikowanie członkostwa w & współpracy za pomocą poczty e-mail w portalu Microsoft 365 Defender-mail

1. W portalu Microsoft 365 Defender pod adresem <https://security.microsoft.com>przejdź do tematu Role &-mail i **współpracy** \> Uprawnienia **&** \> U role w u kontie e-mail & **role współpracy**\>. Aby przejść bezpośrednio do **strony Uprawnienia**, użyj .<https://security.microsoft.com/emailandcollabpermissions>

2. Na **stronie Uprawnienia** wybierz z listy grupę ról, którą chcesz zmodyfikować. Możesz kliknąć nagłówek **kolumny** Nazwa, aby posortować listę według nazw, lub kliknąć **ikonę** ![Wyszukaj.](../../media/m365-cc-sc-search-icon.png) aby znaleźć grupę ról.

3. W wyświetlonym wysuwanych szczegółach grupy ról kliknij pozycję **Edytuj** w **sekcji** Członkowie.

4. Na **wyświetlonej stronie Edytowanie** wybierz członków wykonaj jedną z następujących czynności:
   - Jeśli nie ma członków grupy ról, kliknij pozycję **Wybierz członków**.
   - Jeśli istnieją członkowie grupy ról, kliknij pozycję **Edytuj.**

5. W **wyświetlonym wysuwam** menu Wybierz członków wykonaj jedną z następujących czynności:

   - Kliknij pozycję **Dodaj**. Na wyświetlonej liście użytkowników wybierz co najmniej jednego użytkownika. Możesz też kliknąć **ikonę Wyszukaj**![.](../../media/m365-cc-sc-search-icon.png) w celu znalezienia i wybrania użytkowników.

     Po wybraniu użytkowników, których chcesz dodać, kliknij pozycję **Dodaj**.

   - Kliknij **Usuń**. Zaznacz co najmniej jednego z istniejących członków. Możesz też kliknąć **ikonę Wyszukaj**![.](../../media/m365-cc-sc-search-icon.png) aby znaleźć i wybrać członków.

     Po wybraniu użytkowników, których chcesz usunąć, kliknij pozycję **Usuń**.

6. Wróć na **wysuwną pozycję Wybierz członków** i kliknij pozycję **Gotowe**.

7. Na stronie Edytowanie **wybierz członków** kliknij pozycję **Zapisz**.

8. Na wysuwanych szczegółach grupy ról kliknij pozycję **Gotowe**.
