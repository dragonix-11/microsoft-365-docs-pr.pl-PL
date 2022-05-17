---
title: Usuwanie byłego pracownika — omówienie
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- m365solution-removeemployee
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
description: Blokuj dostęp do Microsoft 365, aby były pracownik nie mógł się logować, zabezpieczać danych organizacji i zezwalać innym pracownikom na dostęp do poczty e-mail i danych OneDrive.
ms.openlocfilehash: 3bff5812d1efd6b38f05303de7ec2c078b31cf01
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436322"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Omówienie: Usuwanie byłego pracownika i zabezpieczanie danych

Często pojawia się pytanie: "Co należy zrobić, aby zabezpieczyć dane i chronić dostęp, gdy pracownik opuści moją organizację?" W tej serii artykułów wyjaśniono, jak zablokować dostęp do Microsoft 365, aby ci użytkownicy nie mogli zalogować się do Microsoft 365, czynności, które należy wykonać w celu zabezpieczenia danych organizacji oraz jak zezwolić innym pracownikom na dostęp do poczty e-mail i danych OneDrive.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej kroków opisanych w tym temacie, rozważ [współpracę ze specjalistą ds. małych firm firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej uzyskasz wraz ze swoimi pracownikami całodobowy dostęp do wsparcia ze strony specjalistów ds. małych firm potrzebnego w miarę rozwoju Twojej firmy — od dołączania po codzienne użytkowanie.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wykonać kroki opisane w tym rozwiązaniu, musisz być administratorem globalnym.

Aby wykonać kroki opisane w tej serii, należy użyć tych Microsoft 365 możliwości i funkcji.

|Produkt lub składnik|Możliwość lub funkcja|
|---|---|
|Centrum administracyjne platformy Microsoft 365|Konwertowanie skrzynki pocztowej, przekazywanie wiadomości e-mail, odwoływanie dostępu, usuwanie użytkownika |
|centrum administracyjne Exchange|Blokowanie użytkownika, blokowanie dostępu do poczty e-mail, czyszczenie urządzenia |
|OneDrive i SharePoint |Udzielanie dostępu innym użytkownikom |
|Outlook|Importowanie plików pst, dodawanie skrzynki pocztowej |
|Active Directory|Usuwanie użytkowników w środowiskach hybrydowych |


## <a name="solution-remove-a-former-employee"></a>Rozwiązanie: Usuwanie byłego pracownika

> [!IMPORTANT]
> Mimo że ponumerowaliśmy kroki w tym rozwiązaniu i nie musisz wykonywać rozwiązania przy użyciu dokładnej kolejności, zalecamy wykonanie kroków w ten sposób.

:::image type="content" source="../../media/delete-user-account.png" alt-text="Zrzut ekranu: Kroki usuwania byłego pracownika z organizacji":::

<br>

****

|Krok|Uzasadnienie|
|---|---|
|[Krok 1. Uniemożliwianie byłym pracownikom logowania się i blokowania dostępu do usług Microsoft 365](remove-former-employee-step-1.md)|Uniemożliwia to byłym pracownikom logowanie się do Microsoft 365 i uniemożliwia danej osobie dostęp do usług Microsoft 365.|
|[Krok 2. Zapisywanie zawartości skrzynki pocztowej byłego pracownika](remove-former-employee-step-2.md)|Jest to przydatne dla osoby, która zamierza przejąć pracę pracownika lub w przypadku sporu sądowego.|
|[Krok 3. Czyszczenie i blokowanie urządzenia przenośnego byłego pracownika](remove-former-employee-step-3.md)|Spowoduje to usunięcie danych biznesowych z telefonu lub tabletu.|
|[Krok 4. Przekazywanie wiadomości e-mail byłego pracownika do innego pracownika lub konwertowanie na udostępnioną skrzynkę pocztową](remove-former-employee-step-4.md)|W ten sposób adres e-mail byłego pracownika pozostanie aktywny. Dzięki temu klienci lub partnerzy, którzy nadal wysyłają wiadomości e-mail na adres byłego pracownika, będą mogli skontaktować się z osobą, która przejęła jego obowiązki.|
|[Krok 5. Udzielanie innym pracownikom dostępu do danych OneDrive i Outlook](remove-former-employee-step-5.md)|Jeśli tylko usuniesz licencję użytkownika, ale nie usuniesz konta, zawartość w usłudze OneDrive użytkownika pozostanie dla Ciebie dostępna nawet po upływie 30 dni. <p> Przed usunięciem konta należy udzielić dostępu do ich OneDrive i Outlook innemu użytkownikowi. Po usunięciu konta pracownika zawartość w OneDrive i Outlook jest przechowywana przez **30** dni. Jednak w ciągu tych 30 dni możesz przywrócić konto użytkownika i uzyskać dostęp do jego zawartości. W przypadku przywrócenia konta użytkownika zawartość OneDrive i Outlook pozostanie dostępna nawet po 30 dniach.| 
|[Krok 6. Usuwanie i usuwanie licencji Microsoft 365 od byłego pracownika](remove-former-employee-step-6.md)|Po odebraniu licencji możesz ją przypisać innej osobie. Możesz też usunąć licencję, aby nie płacić za nią do czasu zatrudnienia nowej osoby.  <p> Po odebraniu lub usunięciu licencji stare wiadomości e-mail, kontakty i kalendarz użytkownika będą przechowywane przez okres **30 dni**, po czym zostaną trwale usunięte. Jeśli tylko usuniesz licencję, ale nie usuniesz konta, zawartość w usłudze OneDrive użytkownika pozostanie dla Ciebie dostępna nawet po upływie 30 dni.  |
|[Krok 7. Usuwanie konta użytkownika byłego pracownika](remove-former-employee-step-7.md)|Spowoduje to usunięcie konta z centrum administracyjnego. Dzięki temu zostanie zachowany porządek.|

 ## <a name="watch-delete-a-user"></a>Obejrzyj: Usuwanie użytkownika

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR?autoplay=false]

Gdy pracownik odejdzie z firmy, musisz usunąć go z Microsoft 365 dla firm. Przed wykonaniem tej czynności należy zablokować im dostęp do plików firmowych, zachować utworzone dokumenty i wykonać kilka innych zadań administracyjnych związanych z usuwaniem użytkownika.

1. W centrum administracyjnym wybierz pozycję **Użytkownicy**, a następnie wybierz pozycję **Aktywni użytkownicy**.
1. Wybierz użytkownika, który chcesz usunąć, a następnie wybierz pozycję **Usuń użytkownika**.
1. Zaznacz pole wyboru, aby usunąć licencję, i zaznacz pole wyboru, aby usunąć aliasy poczty e-mail.
1. Zaznacz pole wyboru, aby udzielić innemu użytkownikowi dostępu do poczty e-mail byłego pracownika, a następnie wybierz **pozycję Wybierz użytkownika i ustaw opcje poczty e-mail**.
1. Aby usunąć skojarzone aliasy poczty e-mail, wybierz pozycję **X** obok ich aliasów.
1. Przejrzyj informacje o udostępnionej skrzynce pocztowej i wybierz pozycję **Zakończ**.
1. Upewnij się, że opcje są ustawione poprawnie, a następnie wybierz pozycję **Przypisz i konwertuj**.
1. Przejrzyj wyniki i wybierz pozycję **Zamknij**.

Po usunięciu użytkownika masz do 30 dni na przywrócenie jego konta.
## <a name="related-content"></a>Zawartość pokrewna

[Przywracanie użytkownika](restore-user.md) (artykuł)\
[Dodawanie nowego pracownika do platformy Microsoft 365](add-new-employee.md) (artykuł)\
[Przypisywanie licencji do użytkowników](../manage/assign-licenses-to-users.md) (artykuł)\
[Anulowanie przypisywania licencji od użytkowników](../manage/remove-licenses-from-users.md) (artykuł)
