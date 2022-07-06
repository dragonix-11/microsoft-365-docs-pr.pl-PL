---
title: Uprawnienia w portalu zgodności usługi Microsoft Purview
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
description: Dowiedz się więcej o zarządzaniu uprawnieniami w portal zgodności Microsoft Purview.
ms.collection: M365-security-compliance
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
ms.openlocfilehash: b8e7f17ef22163e091307fda7cd0beb6659022dc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623858"
---
# <a name="permissions-in-the-microsoft-purview-compliance-portal"></a>Uprawnienia w portalu zgodności usługi Microsoft Purview

Portal zgodności Microsoft Purview obsługuje bezpośrednie zarządzanie uprawnieniami dla użytkowników, którzy wykonują zadania zgodności na platformie Microsoft 365. Ta aktualizacja oznacza, że do zarządzania uprawnieniami dla rozwiązań zgodności nie będzie już trzeba używać centrum Office 365 Security & Compliance Center. Przy użyciu nowej strony **Uprawnienia** w portalu zgodności można zarządzać uprawnieniami użytkowników do zadań zgodności w funkcjach takich jak zarządzanie urządzeniami, Ochrona przed utratą danych w Microsoft Purview, wykrywanie elektroniczne, zarządzanie ryzykiem wewnętrznym, przechowywanie i wiele innych. Użytkownicy mogą wykonywać tylko zadania zgodności, do których jawnie udzielasz im dostępu.

Aby wyświetlić kartę **Uprawnienia** w portalu zgodności, użytkownicy muszą być administratorami globalnymi lub muszą mieć przypisaną rolę *Zarządzanie rolami* (rola jest przypisywana tylko do grupy ról *zarządzanie organizacją* ). Rola *Zarządzanie rolami* umożliwia użytkownikom wyświetlanie, tworzenie i modyfikowanie grup ról.

![Strona uprawnienia w portal zgodności Microsoft Purview.](../media/m365-compliance-center-permissions.png)

Uprawnienia w portalu zgodności są oparte na modelu uprawnień kontroli dostępu opartej na rolach (RBAC). Kontrola dostępu oparta na rolach to ten sam model uprawnień, który jest używany przez większość usług Platformy Microsoft 365, więc jeśli znasz strukturę uprawnień w tych usługach, udzielanie uprawnień w portalu zgodności będzie znane. Należy pamiętać, że uprawnienia zarządzane w portalu zgodności nie obejmują zarządzania wszystkimi uprawnieniami wymaganymi w poszczególnych usługach. Nadal musisz zarządzać określonymi uprawnieniami specyficznymi dla usługi w centrum administracyjnym dla określonej usługi. Jeśli na przykład musisz przypisać uprawnienia do archiwizacji, inspekcji i zasad przechowywania mrm, musisz zarządzać tymi uprawnieniami w <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnym programu Exchange</a>.

## <a name="relationship-of-members-roles-and-role-groups"></a>Relacja członków, ról i grup ról

Rola udziela uprawnień do wykonywania zestawu zadań; Na przykład rola Zarządzanie przypadkami umożliwia użytkownikom pracę z przypadkami zbierania elektronicznych materiałów dowodowych.

Grupa ról to zestaw ról, które umożliwiają użytkownikom wykonywanie zadań w różnych rozwiązaniach zgodności w portalu zgodności. Na przykład dodając użytkowników do grupy ról *Insider Risk Management* , wyznaczeni administratorzy, analitycy, badacze i audytorzy są konfigurowane pod kątem niezbędnych uprawnień do zarządzania ryzykiem wewnętrznym w jednej grupie. Portal zgodności zawiera domyślne grupy ról dla zadań i funkcji dla każdego rozwiązania zgodności, do którego należy przypisać osoby. Ogólnie rzecz biorąc, zalecamy po prostu dodanie poszczególnych użytkowników jako członków do domyślnych grup ról zgodności zgodnie z potrzebami.

![Diagram przedstawiający relację grup ról z rolami i elementami członkowskimi.](../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="permissions-needed-to-use-features-in-the-compliance-portal"></a>Uprawnienia wymagane do korzystania z funkcji w portalu zgodności

Aby wyświetlić wszystkie domyślne grupy ról dostępne w portalu zgodności i role domyślnie przypisane do grup ról, zobacz [Uprawnienia w Centrum zgodności & zabezpieczeń](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

Zarządzanie uprawnieniami w portalu zgodności zapewnia użytkownikom dostęp tylko do funkcji zgodności dostępnych w portalu zgodności. Jeśli chcesz udzielić uprawnień innym funkcjom, które nie znajdują się w portalu zgodności, takim jak reguły przepływu poczty programu Exchange (nazywane również regułami transportu), musisz użyć <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centrum administracyjnego programu Exchange</a>.

## <a name="azure-roles-in-the-compliance-portal"></a>Role platformy Azure w portalu zgodności

Role wyświetlane w sekcji **Azure AD** >  **Roles** na stronie **Uprawnienia** portalu zgodności to role usługi Azure Active Directory. Te role zostały zaprojektowane tak, aby były zgodne z funkcjami zadań w grupie IT organizacji, co ułatwia przyznanie osobie wszystkich uprawnień niezbędnych do wykonania zadania. Użytkownicy aktualnie przypisani do każdej roli można wyświetlić, wybierając rolę Administracja i wyświetlając szczegóły panelu roli. Aby zarządzać członkami roli Azure AD, wybierz pozycję Zarządzaj członkami w Azure AD. Ten wybór przekierowuje Cię do portalu zarządzania platformy Azure.

|Rola|Opis|
|:---|:----------|
|**administrator globalny**|Dostęp do wszystkich funkcji administracyjnych we wszystkich usługach platformy Microsoft 365. Tylko administratorzy globalni mogą przypisywać inne role administratora. Aby uzyskać więcej informacji, zobacz [Administrator globalny/ Administrator firmy](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrator danych zgodności**|Śledź dane organizacji na platformie Microsoft 365, upewnij się, że są chronione, i uzyskaj szczegółowe informacje na temat wszelkich problemów ułatwiających ograniczenie ryzyka. Aby uzyskać więcej informacji, zobacz [Administrator danych zgodności](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Administrator zgodności**|Pomóż swojej organizacji zachować zgodność z wszelkimi wymaganiami prawnymi, zarządzać przypadkami zbierania elektronicznych materiałów dowodowych i obsługiwać zasady ładu danych w lokalizacjach, tożsamościach i aplikacjach platformy Microsoft 365. Aby uzyskać więcej informacji, zobacz [Administrator zgodności](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Operator zabezpieczeń**|Wyświetlanie, badanie i reagowanie na aktywne zagrożenia dla użytkowników, urządzeń i zawartości platformy Microsoft 365 oraz reagowanie na nie. Aby uzyskać więcej informacji, zobacz [Operator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Czytelnik zabezpieczeń**|Wyświetlanie i badanie aktywnych zagrożeń dla użytkowników, urządzeń i zawartości platformy Microsoft 365, ale (w przeciwieństwie do operatora zabezpieczeń) nie mają oni uprawnień do reagowania, podejmując działania. Aby uzyskać więcej informacji, zobacz [Czytelnik zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Administrator zabezpieczeń**|Kontrolowanie ogólnego bezpieczeństwa organizacji przez zarządzanie zasadami zabezpieczeń, przeglądanie analizy zabezpieczeń i raportów w produktach platformy Microsoft 365 oraz szybkie reagowanie na zagrożenia. Aby uzyskać więcej informacji, zobacz [Administrator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Czytelnik globalny**|Wersja tylko do odczytu roli **administrator globalny**. Wyświetl wszystkie ustawienia i informacje administracyjne na platformie Microsoft 365. Aby uzyskać więcej informacji, zobacz [Czytelnik globalny](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrator symulacji ataków**|Tworzenie i zarządzanie wszystkimi aspektami tworzenia symulacji ataku, uruchamiania/planowania symulacji oraz przeglądu wyników symulacji. Aby uzyskać więcej informacji, zobacz [Administrator symulacji ataków](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Autor ładunku ataku**|Twórz ładunki ataku, ale nie uruchamiaj ich ani nie planuj. Aby uzyskać więcej informacji, zobacz [Attack Payload Author (Autor ładunku ataku](/azure/active-directory/roles/permissions-reference#attack-payload-author)).|
|

## <a name="add-users-to-a-compliance-role-group"></a>Dodawanie użytkowników do grupy ról zgodności

Wykonaj następujące kroki, aby dodać użytkowników do grupy ról zgodności:

1. Zaloguj się do obszaru uprawnień portalu zgodności przy użyciu poświadczeń dla konta administratora w organizacji platformy Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a> , aby wybrać link do wyświetlania ról zgodności i zarządzania nimi na platformie Microsoft 365.
1. Rozwiń sekcję **Centrum zgodności** i wybierz pozycję **Role**.
1. Na stronie **Role Centrum zgodności** wybierz grupę ról zgodności, do którą chcesz dodać użytkowników, a następnie wybierz pozycję **Edytuj grupę ról** w okienku szczegółów.
1. Wybierz pozycję **Wybierz członków** w okienku nawigacji po lewej stronie, a następnie wybierz pozycję **Edytuj**.
1. Wybierz pozycję **Dodaj** , a następnie zaznacz pole wyboru dla wszystkich użytkowników, którzy chcesz dodać do grupy ról.
1. Wybierz pozycję **Dodaj**, a następnie wybierz pozycję **Gotowe**.
1. Wybierz pozycję **Zapisz** , aby dodać użytkowników do grupy ról. Wybierz pozycję **Zamknij** , aby wykonać kroki.

## <a name="remove-users-from-a-compliance-role-group"></a>Usuwanie użytkowników z grupy ról zgodności

Wykonaj następujące kroki, aby usunąć użytkowników z grupy ról zgodności:

1. Zaloguj się do obszaru uprawnień portalu zgodności przy użyciu poświadczeń dla konta administratora w organizacji platformy Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a> , aby wybrać link do wyświetlania ról zgodności i zarządzania nimi na platformie Microsoft 365.
1. Rozwiń sekcję Centrum zgodności i wybierz pozycję **Role**.
1. Na stronie **Role Centrum zgodności** wybierz grupę ról zgodności, z którą chcesz usunąć użytkowników, a następnie wybierz pozycję **Edytuj grupę ról** w okienku szczegółów.
1. Wybierz pozycję **Wybierz członków** w okienku nawigacji po lewej stronie, a następnie wybierz pozycję **Edytuj**.
1. Wybierz pozycję **Usuń** , a następnie zaznacz pole wyboru dla wszystkich użytkowników, którzy mają zostać usunięci z grupy ról.
1. Wybierz pozycję **Usuń**, a następnie wybierz pozycję **Gotowe**.
1. Wybierz pozycję **Zapisz** , aby usunąć użytkowników z grupy ról. Wybierz pozycję **Zamknij** , aby wykonać kroki.

## <a name="create-a-custom-role-group"></a>Tworzenie niestandardowej grupy ról

Wykonaj następujące kroki, aby utworzyć niestandardową grupę ról:

1. Zaloguj się do obszaru uprawnień portalu zgodności przy użyciu poświadczeń dla konta administratora w organizacji platformy Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.
1. Na stronie **Uprawnienia & ról** wybierz pozycję **Centrum zgodności > role**.
1. Na stronie **Role Centrum zgodności** wybierz pozycję **Utwórz**.
1. Na stronie **Nazwa grupy ról** wprowadź nazwę niestandardowej grupy ról w polu **Nazwa** . Nie można zmienić nazwy grupy ról po utworzeniu grupy ról. W razie potrzeby wprowadź opis niestandardowej grupy ról w polu **Opis** . Wybierz przycisk **Dalej**, aby kontynuować.
1. Na stronie **Wybieranie ról** wybierz pozycję **Wybierz role**.
1. Wybierz pozycję **Dodaj**, a następnie wybierz role, które mają zostać dodane do niestandardowej grupy ról. Wybierz pozycję **Dodaj** , aby dodać grupę ról, a następnie wybierz pozycję **Gotowe**.
1. Wybierz przycisk **Dalej**, aby kontynuować.
1. Na stronie **Wybieranie członków** wybierz pozycję **Wybierz członków**.
1. Wybierz pozycję **Dodaj**, a następnie wybierz członków do dodania do niestandardowej grupy ról. Wybierz pozycję **Dodaj** , aby dodać członków, a następnie wybierz pozycję **Gotowe**.
1. Wybierz przycisk **Dalej**, aby kontynuować.
1. Na stronie **Przeglądanie ustawień przejrzyj** szczegóły niestandardowej grupy ról. Jeśli chcesz edytować informacje, wybierz pozycję **Edytuj** w odpowiedniej sekcji. Gdy wszystkie ustawienia są poprawne, wybierz pozycję **Utwórz grupę ról** , aby utworzyć niestandardową grupę ról, lub wybierz pozycję **Anuluj** , aby odrzucić zmiany i nie utworzyć niestandardowej grupy ról.

## <a name="update-a-custom-role-group"></a>Aktualizowanie niestandardowej grupy ról

Wykonaj następujące kroki, aby zaktualizować niestandardową grupę ról:

1. Zaloguj się do obszaru uprawnień portalu zgodności przy użyciu poświadczeń dla konta administratora w organizacji platformy Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.
1. Na stronie **Uprawnienia & ról** wybierz pozycję **Centrum zgodności > role**.
1. Na stronie **Role Centrum zgodności** wybierz grupę ról do zaktualizowania.
1. W okienku szczegółów wybranej grupy ról wybierz pozycję **Edytuj grupę ról**.
1. Na stronie **Edytowanie nazwy grupy ról** zaktualizuj opis niestandardowej grupy ról w polu **Opis** . Nie można zmienić nazwy niestandardowej grupy ról.
1. Na stronie **Wybieranie ról** wybierz pozycję **Edytuj** , aby zaktualizować role przypisane do grup ról.
1. Wybierz pozycję **Dodaj**, a następnie wybierz role, które mają zostać dodane do niestandardowej grupy ról. Wybierz pozycję **Dodaj** , aby dodać grupę ról, a następnie wybierz pozycję **Gotowe**.
1. Na stronie **Wybieranie członków** wybierz pozycję **Edytuj**.
1. Wybierz pozycję **Dodaj**, a następnie wybierz członków do dodania do niestandardowej grupy ról. Wybierz pozycję **Dodaj** , aby dodać członków, a następnie wybierz pozycję **Gotowe**.
1. Wybierz pozycję **Zapisz** , aby zapisać zaktualizowane wartości *Opis*, *Grupy ról* i *Członkowie* .
1. W okienku szczegółów wybranej grupy ról wybierz pozycję **Zamknij**.

## <a name="delete-a-custom-role-group"></a>Usuwanie niestandardowej grupy ról

Wykonaj następujące kroki, aby zaktualizować niestandardową grupę ról:

1. Zaloguj się do obszaru uprawnień portalu zgodności przy użyciu poświadczeń dla konta administratora w organizacji platformy Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.
1. Na stronie **Uprawnienia & ról** wybierz pozycję **Centrum zgodności > role**.
1. Na stronie **Role Centrum zgodności** wybierz grupę ról do zaktualizowania.
1. W okienku szczegółów wybranej grupy ról wybierz pozycję **Usuń grupę ról**.
1. W oknie dialogowym **Ostrzeżenie** wybierz pozycję **Tak** , aby usunąć grupę ról, lub wybierz pozycję **Nie** , aby anulować proces usuwania.
