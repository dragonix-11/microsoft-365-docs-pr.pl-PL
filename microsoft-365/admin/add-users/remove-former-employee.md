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
description: Wykonaj czynności opisane w tym rozwiązaniu, aby usunąć byłego pracownika z Microsoft 365 i zabezpieczyć dane organizacji.
ms.openlocfilehash: 799a946c85da94fcc3d9e53a4015697d124192ce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315179"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Omówienie: usuwanie byłego pracownika i zabezpieczanie danych

Często pojawia się pytanie "Co mam zrobić, aby zabezpieczyć dane i zabezpieczyć dostęp, gdy pracownik odchodzi z organizacji?". W tej serii artykułów wyjaśniono, jak zablokować dostęp do usługi Microsoft 365, aby ci użytkownicy nie mogą logować się do usługi Microsoft 365, jakie czynności należy wykonać, aby zabezpieczyć dane organizacji, oraz jak zezwolić innym pracownikom na dostęp do poczty e-mail i OneDrive danych.

> [!TIP]
> Jeśli potrzebujesz pomocy dotyczącej czynności opisanej w tym temacie, rozważ współpracę z specjalistą [ds. małej firmy Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Dzięki Pomocy biznesowej Ty i Twoi pracownicy możecie uzyskać całodobowy dostęp do małych ekspertów biznesowych, gdy rozwijasz swoją firmę, od dołączania do codziennego użytku.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Aby wykonać czynności opisane w tym rozwiązaniu, musisz być administratorem globalnym.

Do wykonania kroków z tej serii należy użyć tych Microsoft 365 i funkcji.

|Produkt lub składnik|Funkcja lub funkcja|
|---|---|
|Centrum administracyjne platformy Microsoft 365|Konwertowanie skrzynki pocztowej, przesyłanie dalej wiadomości e-mail, odwoływanie dostępu, usuwanie użytkownika |
|Exchange administracyjne|Blokowanie użytkownika, blokowanie dostępu do poczty e-mail, czyszczenie urządzenia |
|OneDrive i SharePoint |Daj dostęp innym użytkownikom |
|Outlook|Importowanie plików pst, dodawanie skrzynki pocztowej |
|Active Directory|Usuwanie użytkowników w środowiskach hybrydowych |


## <a name="solution-remove-a-former-employee"></a>Rozwiązanie: Usuwanie byłego pracownika

> [!IMPORTANT]
> Mimo że w tym rozwiązaniu po numerowaliśmy kroki i nie trzeba go kończyć zgodnie z dokładną kolejnością, zalecamy wykonanie tych czynności w ten sposób.

:::image type="content" source="../../media/delete-user-account.png" alt-text="Zrzut ekranu: procedura usuwania byłego pracownika z organizacji":::

<br>

****

|Krok|Uzasadnienie|
|---|---|
|[Krok 1. Uniemożliwianie byłemu pracownikowi logowania się i blokowanie dostępu do Microsoft 365 usług](remove-former-employee-step-1.md)|Uniemożliwi to byłemu pracownikowi zalogowanie się do Microsoft 365 i uniemożliwia danej osobie dostęp do Microsoft 365 usług.|
|[Krok 2. Zapisywanie zawartości skrzynki pocztowej byłego pracownika](remove-former-employee-step-2.md)|Jest to przydatne dla osoby, która przejmie pracę pracownika, lub w przypadku sporu sądowego.|
|[Krok 3. Czyszczenie i blokowanie urządzenia przenośnego byłego pracownika](remove-former-employee-step-3.md)|Spowoduje to usunięcie danych biznesowych z telefonu lub tabletu.|
|[Krok 4. Przesyłanie dalej wiadomości e-mail byłego pracownika do innego pracownika lub konwertowanie na udostępnioną skrzynkę pocztową](remove-former-employee-step-4.md)|W ten sposób adres e-mail byłego pracownika pozostanie aktywny. Dzięki temu klienci lub partnerzy, którzy nadal wysyłają wiadomości e-mail na adres byłego pracownika, będą mogli skontaktować się z osobą, która przejęła jego obowiązki.|
|[Krok 5. Nadaj innecie pracownika dostęp do OneDrive i Outlook danych](remove-former-employee-step-5.md)|Jeśli tylko usuniesz licencję użytkownika, ale nie usuniesz konta, zawartość w usłudze OneDrive użytkownika pozostanie dla Ciebie dostępna nawet po upływie 30 dni. <p> Przed usunięciem konta należy udzielić dostępu do jego konta OneDrive i Outlook inowi użytkownikowi. Po usunięciu konta pracownika zawartość w jego OneDrive i Outlook jest zachowywana **przez 30** dni. Jednak w ciągu tych 30 dni możesz przywrócić konto użytkownika i uzyskać dostęp do jego zawartości. Jeśli przywrócisz konto użytkownika, zawartość OneDrive i Outlook pozostanie dla Ciebie dostępna nawet po upływie 30 dni.| 
|[Krok 6. Usunięcie licencji Microsoft 365 byłego pracownika](remove-former-employee-step-6.md)|Po odebraniu licencji możesz ją przypisać innej osobie. Możesz też usunąć licencję, aby nie płacić za nią do czasu zatrudnienia nowej osoby.  <p> Po odebraniu lub usunięciu licencji stare wiadomości e-mail, kontakty i kalendarz użytkownika będą przechowywane przez okres **30 dni**, po czym zostaną trwale usunięte. Jeśli tylko usuniesz licencję, ale nie usuniesz konta, zawartość w usłudze OneDrive użytkownika pozostanie dla Ciebie dostępna nawet po upływie 30 dni.  |
|[Krok 7. Usuwanie konta użytkownika byłego pracownika](remove-former-employee-step-7.md)|Spowoduje to usunięcie konta z Centrum administracyjnego. Dzięki temu zostanie zachowany porządek.|

 ## <a name="watch-delete-a-user"></a>Obejrzyj: Usuwanie użytkownika

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR?autoplay=false]

Gdy pracownik odchodzi z firmy, musisz usunąć go z Microsoft 365 dla firm. Zanim to zrobisz, należy zablokować im dostęp do plików firmy, zachować utworzone przez niego dokumenty i wykonać kilka innych zadań administracyjnych związanych z usuwaniem użytkownika.

1. W centrum administracyjnym wybierz pozycję **Użytkownicy** i wybierz pozycję **Aktywni użytkownicy**.
1. Wybierz użytkownika, którego chcesz usunąć, a następnie wybierz pozycję **Usuń użytkownika**.
1. Zaznacz pole wyboru, aby usunąć jego licencję, a następnie zaznacz to pole wyboru, aby usunąć aliasy e-mail tych osób.
1. Zaznacz to pole wyboru, aby dać iniutorowi dostęp do poczty e-mail byłego pracownika, a następnie wybierz pozycję Wybierz użytkownika **i ustaw opcje poczty e-mail**.
1. Aby usunąć skojarzone aliasy e-mail, wybierz **pozycję X** obok skojarzonych aliasów.
1. Przejrzyj informacje o udostępnionej skrzynce pocztowej i wybierz pozycję **Zakończ**.
1. Upewnij się, że opcje są ustawione poprawnie, a następnie wybierz pozycję **Przypisz i przekonwertuj**.
1. Przejrzyj wyniki, a następnie wybierz **pozycję Zamknij**.

Po usunięciu użytkownika masz maksymalnie 30 dni na przywrócenie jego konta.
## <a name="related-content"></a>Zawartość pokrewna

[Przywracanie użytkownika](restore-user.md) (artykuł)\
[Dodawanie nowego pracownika do Microsoft 365](add-new-employee.md) (artykuł)\
[Przypisywanie licencji użytkownikom](../manage/assign-licenses-to-users.md) (artykuł)\
[Odsyłanie licencji użytkownikom](../manage/remove-licenses-from-users.md) (artykuł)
