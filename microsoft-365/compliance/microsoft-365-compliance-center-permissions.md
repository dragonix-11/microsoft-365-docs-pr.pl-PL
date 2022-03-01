---
title: Uprawnienia w Centrum zgodności platformy Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
description: Dowiedz się więcej o zarządzaniu uprawnieniami w Centrum zgodności platformy Microsoft 365.
ms.collection: M365-security-compliance
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
ms.openlocfilehash: 45540713452b91da171f6fc52eef8210fa256c4e
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2021
ms.locfileid: "63017795"
---
# <a name="permissions-in-the-microsoft-365-compliance-center"></a>Uprawnienia w Centrum zgodności platformy Microsoft 365

Ta Centrum zgodności platformy Microsoft 365 została niedawno zaktualizowana i obsługuje bezpośrednio zarządzanie uprawnieniami dla użytkowników, którzy wykonują zadania związane ze zgodnością w Microsoft 365. Ta aktualizacja oznacza, że nie musisz już używać Centrum zgodności usługi Office 365 Security & do zarządzania uprawnieniami do rozwiązań zgodności. Za pomocą nowej  strony Uprawnienia w aplikacji Centrum zgodności platformy Microsoft 365 możesz zarządzać uprawnieniami użytkowników do wykonywania zadań dotyczących zgodności w funkcjach takich jak zarządzanie urządzeniami, ochrona przed utratą danych, zbierania elektronicznych materiałów dowodowych, zarządzanie ryzykiem niejawnego programu testów, przechowywanie i wiele innych. Użytkownicy mogą wykonywać tylko zadania związane ze zgodnością, do których jawnie im przyznajesz dostęp.

Aby wyświetlić kartę Uprawnienia w Centrum zgodności platformy Microsoft 365, użytkownicy muszą być administratorami globalnymi lub muszą mieć przypisaną rolę Zarządzanie rolami (rola  jest przypisana tylko do grupy ról *Zarządzanie organizacją).*  Rola *Zarządzanie rolami* umożliwia użytkownikom wyświetlanie, tworzenie i modyfikowanie grup ról.

![Strona uprawnień w programie Centrum zgodności platformy Microsoft 365.](../media/m365-compliance-center-permissions.png)

Uprawnienia w Centrum zgodności platformy Microsoft 365 są oparte na modelu uprawnień kontroli dostępu opartej na rolach (RBAC). RBAC to ten sam model uprawnień, który jest używany przez większość usług firmy Microsoft 365, więc jeśli znasz strukturę uprawnień w tych usługach, udzielanie uprawnień w Centrum zgodności platformy Microsoft 365 będzie znane. Należy pamiętać, że uprawnienia zarządzane w usłudze Centrum zgodności platformy Microsoft 365 nie obejmują zarządzania wszystkimi uprawnieniami potrzebnymi w poszczególnych usługach. Nadal musisz zarządzać określonymi uprawnieniami usługi w centrum administracyjnym konkretnej usługi. Jeśli na przykład chcesz przypisać uprawnienia do archiwizacji, inspekcji i zasad przechowywania MRM, musisz zarządzać tymi uprawnieniami w centrum administracyjnym usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a>.

## <a name="relationship-of-members-roles-and-role-groups"></a>Relacja między członkami, rolami i grupami ról

Rola udziela uprawnień do wykonywania zestawu zadań. Na przykład rola Zarządzanie sprawami umożliwia użytkownikom pracę ze sprawami zbierania elektronicznych materiałów dowodowych.

Grupa ról to zestaw ról umożliwiających użytkownikom spełnianie swoich zadań za różnych rozwiązaniach zgodności, które Centrum zgodności platformy Microsoft 365. Na przykład dodając użytkowników do grupy ról Zarządzanie  ryzykiem w ramach niejawnego programu testów, wyznaczeni administratorzy, analitycy, testerzy i audytorzy są skonfigurowani na potrzeby niezbędnych uprawnień do zarządzania ryzykiem w ramach niejawnego programu testów w jednej grupie. Ten Centrum zgodności platformy Microsoft 365 zawiera domyślne grupy ról dla zadań i funkcji dla każdego rozwiązania do zachowania zgodności, do których będzie konieczne przypisanie osób. Ogólnie rzecz biorąc, zalecamy po prostu dodawanie pojedynczych użytkowników jako członków do domyślnych grup ról zgodności zgodnie z potrzebami.

![Diagram przedstawiający relację grup ról z rolami i członkami.](../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="permissions-needed-to-use-features-in-the-microsoft-365-compliance-center"></a>Uprawnienia wymagane do korzystania z funkcji w Centrum zgodności platformy Microsoft 365

Aby wyświetlić wszystkie domyślne grupy ról dostępne w aplikacji Centrum zgodności platformy Microsoft 365 oraz role, które są domyślnie przypisane do tych grup ról, zobacz Uprawnienia w Centrum zgodności usługi [&](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) zabezpieczeń.

Zarządzanie uprawnieniami w Centrum zgodności platformy Microsoft 365 umożliwia użytkownikom dostęp tylko do funkcji zgodności dostępnych w ramach Centrum zgodności platformy Microsoft 365. Jeśli chcesz przyznać uprawnienia do innych funkcji, które nie znajdują się w skoroszycie Centrum zgodności platformy Microsoft 365, takich jak reguły przepływu poczty e-mail programu Exchange (nazywane także regułami transportu), musisz użyć centrum administracyjnego usługi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a>.

## <a name="azure-roles-in-the-microsoft-365-compliance-center"></a>Role platformy Azure w Centrum zgodności platformy Microsoft 365

Role wyświetlane w sekcji **Azure** **ADRoles** >  na stronie uprawnienia usługi Centrum zgodności platformy Microsoft 365 **są** Azure Active Directory role. Te role są zaprojektowane tak, aby były zgodne z funkcjami funkcji w grupie IT organizacji, dzięki czemu można łatwo nadać osobie wszystkie uprawnienia niezbędne do wykonywania swojej pracy. Możesz wyświetlić użytkowników aktualnie przypisanych do poszczególnych ról, wybierając rolę administratora i wyświetlając szczegóły panelu ról. Aby zarządzać członkami roli usługi Azure AD, wybierz pozycję Zarządzaj członkami w usłudze Azure AD. Ta możliwość przekierowuje Cię do Portalu zarządzania Azure.

|Rola|Opis|
|:---|:----------|
|**Administrator globalny**|Dostęp do wszystkich funkcji administracyjnych we wszystkich Microsoft 365 usługach. Tylko administratorzy globalni mogą przypisywać inne role administratora. Aby uzyskać więcej informacji, zobacz [Administrator globalny /Administrator firmy](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrator danych zgodności**|Monitoruj dane organizacji w różnych Microsoft 365, upewnij się, że są chronione, i uzyskaj szczegółowe informacje na temat wszelkich problemów, aby zmniejszyć ryzyko. Aby uzyskać więcej informacji, zobacz [Administrator danych zgodności](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Administrator zgodności**|Pomóż organizacji zachować zgodność z wymaganiami prawnymi, zarządzać sprawami zbierania elektronicznych materiałów dowodowych i utrzymywać zasady zarządzania danymi w Microsoft 365 lokalizacjach, tożsamościach i aplikacjach. Aby uzyskać więcej informacji, zobacz [Administrator zgodności](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Operator zabezpieczeń**|Wyświetlaj i badaj aktywne zagrożenia oraz odpowiadaj na nie Microsoft 365 użytkowników, urządzeń i zawartości. Aby uzyskać więcej informacji, zobacz [Operator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Czytelnik zabezpieczeń**|Wyświetlaj i badaj aktywne zagrożenia dla użytkowników Microsoft 365, urządzeń i zawartości, ale (w przeciwieństwie do operatora zabezpieczeń) nie mają one uprawnień do reagowania poprzez podejmowanie działań. Aby uzyskać więcej informacji, zobacz [Czytnik zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Administrator zabezpieczeń**|Możesz kontrolować ogólne bezpieczeństwo organizacji, zarządzając zasadami zabezpieczeń, przeglądając analizy zabezpieczeń i raporty w różnych Microsoft 365 produktach oraz na bieżąco kontrolować zagrożenia. Aby uzyskać więcej informacji, zobacz [Administrator zabezpieczeń](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Czytelnik globalny**|Wersja tylko do odczytu roli **administratora globalnego** . Wyświetlanie wszystkich ustawień i informacji administracyjnych w Microsoft 365. Aby uzyskać więcej informacji, zobacz [Czytnik globalny](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrator symezyjki ataków**|Tworzenie wszystkich aspektów tworzenia symydyty ataków i zarządzanie nimi, uruchamianie/planowanie symulacyjnej oraz przeglądanie wyników symulacyjnych. Aby uzyskać więcej informacji, zobacz [Administrator symulowania ataków](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Autor ataku ładu**|Twórz łady ataków, ale nie uruchamiaj ich ani nie planuj. Aby uzyskać więcej informacji, zobacz [Autorem ataku opłaty](/azure/active-directory/roles/permissions-reference#attack-payload-author).|
|

## <a name="add-users-to-a-compliance-role-group"></a>Dodawanie użytkowników do grupy ról zgodności

Wykonaj następujące czynności, aby dodać użytkowników do grupy ról zgodności:

1. Zaloguj się do obszaru uprawnień usługi Centrum zgodności platformy Microsoft 365 przy użyciu poświadczeń konta administratora w Twojej organizacji usługi Microsoft 365 i przejdź do obszaru Uprawnienia, aby wybrać link w celu <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank"></a> wyświetlenia ról zgodności i zarządzania nimi w Microsoft 365.
1. Rozwiń **sekcję Centrum zgodności** i wybierz pozycję **Role**.
1. Na stronie **Role w Centrum zgodności** wybierz grupę ról zgodności, do której chcesz dodać użytkowników, a następnie **wybierz pozycję Edytuj** grupę ról w okienku szczegółów.
1. Wybierz **pozycję Wybierz członków** w lewym okienku nawigacji, a następnie wybierz pozycję **Edytuj**.
1. Wybierz **pozycję** Dodaj, a następnie zaznacz pole wyboru dla wszystkich użytkowników, których chcesz dodać do grupy ról.
1. Wybierz **pozycję Dodaj**, a następnie pozycję **Gotowe**.
1. Wybierz **pozycję Zapisz** , aby dodać użytkowników do grupy ról. Wybierz **pozycję Zamknij** , aby ukończyć procedurę.

## <a name="remove-users-from-a-compliance-role-group"></a>Usuwanie użytkowników z grupy ról zgodności

Wykonaj następujące czynności, aby usunąć użytkowników z grupy ról zgodności:

1. Zaloguj się do obszaru uprawnień usługi Centrum zgodności platformy Microsoft 365 przy użyciu poświadczeń konta administratora w Twojej organizacji usługi Microsoft 365 i przejdź do obszaru Uprawnienia, aby wybrać link w celu <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank"></a> wyświetlenia ról zgodności i zarządzania nimi w Microsoft 365.
1. Rozwiń sekcję Centrum zgodności i wybierz pozycję **Role**.
1. Na stronie **Role w Centrum zgodności** wybierz grupę ról zgodności, z której chcesz usunąć użytkowników, a następnie **wybierz pozycję Edytuj** grupę ról w okienku szczegółów.
1. Wybierz **pozycję Wybierz członków** w lewym okienku nawigacji, a następnie wybierz pozycję **Edytuj**.
1. Wybierz **pozycję** Usuń, a następnie zaznacz pole wyboru dla wszystkich użytkowników, których chcesz usunąć z grupy ról.
1. Wybierz **pozycję Usuń**, a następnie pozycję **Gotowe**.
1. Wybierz **pozycję Zapisz** , aby usunąć użytkowników z grupy ról. Wybierz **pozycję Zamknij** , aby ukończyć procedurę.

## <a name="create-a-custom-role-group"></a>Tworzenie niestandardowej grupy ról

Wykonaj następujące czynności, aby utworzyć niestandardową grupę ról:

1. Zaloguj się do obszaru uprawnień w centrum Centrum zgodności platformy Microsoft 365 przy użyciu poświadczeń konta administratora w Twojej organizacji Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.
1. Na stronie **Uprawnienia & wybierz** pozycję **Centrum zgodności > ról**.
1. Na stronie **Role w Centrum zgodności** wybierz pozycję **Utwórz**.
1. Na stronie **Nadaj nazwę grupie** ról wprowadź nazwę niestandardowej grupy ról w **polu Nazwa** . Po utworzeniu grupy ról nie można zmienić nazwy grupy ról. W razie potrzeby wprowadź opis niestandardowej grupy ról w **polu Opis** . Wybierz przycisk **Dalej**, aby kontynuować.
1. Na stronie **Wybieranie ról** wybierz pozycję **Wybierz role**.
1. Wybierz **pozycję** Dodaj, a następnie wybierz role, które chcesz dodać do niestandardowej grupy ról. Wybierz **pozycję Dodaj** , aby dodać grupę ról, a następnie wybierz pozycję **Gotowe**.
1. Wybierz przycisk **Dalej**, aby kontynuować.
1. Na stronie **Wybieranie członków** wybierz pozycję **Wybierz członków**.
1. Wybierz **pozycję** Dodaj, a następnie wybierz członków, których chcesz dodać do niestandardowej grupy ról. Wybierz **pozycję Dodaj** , aby dodać członków, a następnie wybierz pozycję **Gotowe**.
1. Wybierz przycisk **Dalej**, aby kontynuować.
1. Na **stronie Przeglądanie ustawień** przejrzyj szczegóły niestandardowej grupy ról. Jeśli chcesz edytować informacje, wybierz pozycję **Edytuj w** odpowiedniej sekcji. Gdy wszystkie ustawienia są poprawne, wybierz pozycję  Utwórz grupę ról, aby utworzyć niestandardową grupę ról,  lub pozycję Anuluj, aby odrzucić zmiany, a nie utworzyć niestandardową grupę ról.

## <a name="update-a-custom-role-group"></a>Aktualizowanie niestandardowej grupy ról

Wykonaj następujące czynności, aby zaktualizować niestandardową grupę ról:

1. Zaloguj się do obszaru uprawnień w centrum Centrum zgodności platformy Microsoft 365 przy użyciu poświadczeń konta administratora w Twojej organizacji Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.
1. Na stronie **Uprawnienia & wybierz** pozycję **Centrum zgodności > ról**.
1. Na stronie **Role w Centrum zgodności** wybierz grupę ról do zaktualizowania.
1. W okienku szczegółów dla wybranej grupy ról wybierz pozycję **Edytuj grupę ról**.
1. Na stronie **Nazwa grupy ról edytowania** zaktualizuj opis niestandardowej grupy ról w **polu Opis** . Nie można zmienić nazwy niestandardowej grupy ról.
1. Na stronie **Wybieranie ról** wybierz pozycję **Edytuj** , aby zaktualizować role przypisane do grup ról.
1. Wybierz **pozycję** Dodaj, a następnie wybierz role, które chcesz dodać do niestandardowej grupy ról. Wybierz **pozycję Dodaj** , aby dodać grupę ról, a następnie wybierz pozycję **Gotowe**.
1. Na stronie **Wybieranie członków** wybierz pozycję **Edytuj**.
1. Wybierz **pozycję** Dodaj, a następnie wybierz członków, których chcesz dodać do niestandardowej grupy ról. Wybierz **pozycję Dodaj** , aby dodać członków, a następnie wybierz pozycję **Gotowe**.
1. Wybierz **pozycję Zapisz** , aby zapisać zaktualizowane *wartości Opis*, *Grupy ról* *i Członkowie* .
1. W okienku szczegółów dla wybranej grupy ról wybierz pozycję **Zamknij**.

## <a name="delete-a-custom-role-group"></a>Usuwanie niestandardowej grupy ról

Wykonaj następujące czynności, aby zaktualizować niestandardową grupę ról:

1. Zaloguj się do obszaru uprawnień w centrum Centrum zgodności platformy Microsoft 365 przy użyciu poświadczeń konta administratora w Twojej organizacji Microsoft 365 i przejdź do pozycji <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Uprawnienia**</a>.
1. Na stronie **Uprawnienia & wybierz** pozycję **Centrum zgodności > ról**.
1. Na stronie **Role w Centrum zgodności** wybierz grupę ról do zaktualizowania.
1. W okienku szczegółów dla wybranej grupy ról wybierz pozycję **Usuń grupę ról**.
1. W **oknie dialogowym** Ostrzeżenie wybierz pozycję **Tak** , aby usunąć grupę ról, lub pozycję **Nie** , aby anulować proces usuwania.
