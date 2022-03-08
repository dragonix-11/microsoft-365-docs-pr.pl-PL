---
title: Współpraca z gośćmi nad dokumentem
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: W tym artykule dowiesz się, jak współpracować z gośćmi nad dokumentem w programie SharePoint i OneDrive.
ms.openlocfilehash: f27c47403e63c19bf341c69d8dffbe2ea450e1d4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324436"
---
# <a name="collaborate-with-guests-on-a-document"></a>Współpraca z gośćmi nad dokumentem

Jeśli chcesz współpracować z osobami spoza organizacji nad dokumentami w programie SharePoint lub OneDrive, możesz wysłać im link do udostępniania dokumentu. W tym artykule o firmie Microsoft 365 kroki konfiguracji niezbędne do skonfigurowania linków do udostępniania dla SharePoint i OneDrive na potrzeby Twojej organizacji.

## <a name="video-demonstration"></a>Pokaz wideo

W tym klipie wideo przedstawiono kroki konfiguracji opisane w tym dokumencie.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Ustawienia współpracy zewnętrznej na platformie Azure

Udostępnianie w Microsoft 365 jest zarządzane na najwyższym poziomie przez ustawienia współpracy zewnętrznej [B2B w programie Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Jeśli udostępnianie gości jest wyłączone lub ograniczone w usłudze Azure AD, to ustawienie zastępuje wszystkie ustawienia udostępniania skonfigurowane w usłudze Microsoft 365.

Sprawdź ustawienia współpracy zewnętrznej B2B, aby upewnić się, że udostępnianie gościom nie jest zablokowane.

![Zrzut ekranu przedstawiający Azure Active Directory relacje organizacyjne Ustawienia stronie.](../media/azure-ad-organizational-relationships-settings.png)

Aby skonfigurować ustawienia współpracy zewnętrznej

1. Zaloguj się w Azure Active Directory stronie [https://aad.portal.azure.com](https://aad.portal.azure.com).
2. W lewym okienku nawigacji kliknij pozycję **Azure Active Directory**.
3. Kliknij **pozycję Tożsamości zewnętrzne**.
4. Na **ekranie Wprowadzenie** w lewym okienku nawigacji kliknij pozycję **Ustawienia współpracy zewnętrznej**.
5. Upewnij się,  że zarówno użytkownicy, jak i użytkownicy przypisani do określonych ról administratora mogą zapraszać użytkowników gości, w  tym gości z uprawnieniami członków, lub każda osoba w organizacji może zapraszać gości, w tym gości i osób niebędących administratorami.
6. Jeśli zostały wprowadzone zmiany, kliknij przycisk **Zapisz**.

Zwróć uwagę na ustawienia w **sekcji Ograniczenia współpracy** . Upewnij się, że domeny gości, z którymi chcesz współpracować, nie są zablokowane.

Jeśli pracujesz z gośćmi z wielu organizacji, możesz ograniczyć im dostęp do danych katalogowych. Uniemożliwi to tej osobie wyświetlanie w katalogu, kto jeszcze jest gościem. W tym celu w obszarze Ograniczenia dostępu użytkowników gości zaznacz pozycję  Użytkownicy goście mają ograniczony dostęp do właściwości i członkostwa w ustawieniach obiektów katalogu lub Dostęp użytkownika gościa jest ograniczony do właściwości i członkostwa we własnych obiektach **katalogu**.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint ustawienia udostępniania na poziomie organizacji

Aby osoby spoza organizacji mają dostęp do dokumentu w programie SharePoint lub OneDrive, ustawienia udostępniania na poziomie organizacji SharePoint i OneDrive muszą zezwalać na udostępnianie osobom spoza organizacji.

Ustawienia witryny na poziomie organizacji SharePoint ustawienia, które będą dostępne dla poszczególnych SharePoint witryn. Ustawienia witryny nie mogą być bardziej przesądne niż ustawienia na poziomie organizacji. Ustawienie udostępniania na poziomie organizacji OneDrive poziom udostępniania, który będzie dostępny w bibliotekach OneDrive użytkownika.

Aby SharePoint i OneDrive, jeśli chcesz zezwolić na udostępnianie nieuwierzytanych plików i folderów, wybierz pozycję **Wszyscy**. Jeśli chcesz się upewnić, że osoby spoza organizacji muszą się uwierzytelnić, wybierz pozycję **Nowi i istniejący goście**. *Linki Każdy* to najprostszy sposób udostępniania: osoby spoza organizacji mogą otworzyć link bez uwierzytelniania i mogą go przekazać innym osobom.

Na SharePoint wybierz ustawienie najbardziej permisyjne, które będzie wymagane przez dowolną witrynę w organizacji.

![Zrzut ekranu SharePoint ustawień udostępniania na poziomie organizacji.](../media/sharepoint-organization-external-sharing-controls.png)


Aby skonfigurować SharePoint udostępniania na poziomie organizacji

1. W okienku centrum administracyjne platformy Microsoft 365 nawigacji po lewej stronie w obszarze **Centra** administracyjne **kliknij pozycję SharePoint**.
2. W centrum SharePoint w lewym okienku nawigacji w **obszarze Zasady** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Udostępnianie**</a>.
3. Upewnij się, że dla udostępniania SharePoint lub **OneDrive jest** ustawiona wartość Każdy lub **Nowy i istniejący goście**. (Zwróć uwagę, że OneDrive nie może być bardziej przemowy niż SharePoint).
4. Jeśli zostały wprowadzone zmiany, wybierz pozycję **Zapisz**.

## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint domyślnych ustawień linku na poziomie organizacji

Domyślne ustawienia linku do plików i folderów określają opcję linku, która będzie domyślnie wyświetlana użytkownikom, gdy udostępnią plik lub folder. W razie potrzeby użytkownicy mogą zmienić typ linku na jedną z pozostałych opcji przed udostępnieniem.

Pamiętaj, że to ustawienie ma wpływ na SharePoint witryn w organizacji, a także na OneDrive.

Wybierz link z dowolnego z następujących typów, który jest następnie domyślnie wybierany, gdy użytkownicy współużytkuje pliki i foldery:

- **Każda osoba z linkiem** — wybierz tę opcję, jeśli chcesz wykonać wiele nieuwierzytanych plików i folderów. Jeśli chcesz zezwolić na linki *Anyone* (Każda osoba), ale martwi Cię o przypadkowe nieuwierzysfanie udostępniania, jako domyślną rozważ jedną z pozostałych opcji. Ten typ linku jest dostępny tylko w przypadku, gdy włączono **udostępnianie każda** osoba.
- **Tylko osoby w Twojej organizacji** — wybierz tę opcję, jeśli oczekujesz, że większość udostępniania plików i folderów będzie dotyczyć osób w Twojej organizacji.
- **Określone osoby** — rozważ tę opcję, jeśli spodziewasz się udostępniać dużo plików i folderów gościom. Ten typ linku działa z gośćmi i wymaga uwierzytelnienia.
 
![Zrzut ekranu SharePoint ustawień udostępniania plików i folderów na poziomie organizacji.](../media/sharepoint-organization-files-folders-sharing-settings.png)


Aby ustawić domyślne SharePoint i OneDrive na poziomie organizacji

1. Przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**pozycji Udostępnianie**</a> w SharePoint administracyjnego.
2. W **obszarze Linki do plików i folderów** wybierz domyślny link udostępniania, którego chcesz użyć.
3. Jeśli zostały wprowadzone zmiany, kliknij przycisk **Zapisz**.

Aby ustawić uprawnienia linku udostępniania, w obszarze Wybierz uprawnienie wybrane domyślnie do udostępniania **linków.**

1. Wybierz **pozycję** Wyświetl, jeśli nie chcesz, aby nieuwierzytani użytkownicy wprowadzali zmiany w plikach i folderach.
2. Wybierz **pozycję** Edytuj, jeśli chcesz zezwolić nieuwierzytanych użytkowników na zmiany w plikach i folderach.

Pamiętaj, że powyższe dwie opcje dotyczące pominięcia mogą być stosowane nie tylko w przypadku gości/użytkowników zewnętrznych, ale również dla użytkowników wewnętrznych. Wybór opcji uprawnień zależy od uznania użytkownika.

Aby ustawić uprawnienia dla linków, które umożliwiają udostępnianie innym osobom

1. W obszarze **Te linki mogą nadać następujące uprawnienia:** pod-okienko, 
    1. Z **listy** rozwijanej Pliki 
        - Wybierz **pozycję Wyświetl i edytuj** , jeśli chcesz zezwolić nieuwierzytnionym użytkownikom na zmiany w plikach.
        - Wybierz **pozycję** Wyświetl, jeśli nie chcesz, aby nieuwierzytani użytkownicy wprowadzali zmiany w plikach.
    2. Z **listy** rozwijanej Foldery
        - Wybierz **pozycję Wyświetl, edytuj i przekaż,** jeśli chcesz zezwolić nieuwierzytnionym użytkownikom na zmiany w folderach.
        - Wybierz **pozycję** Wyświetl, jeśli nie chcesz, aby nieuwierzytani użytkownicy wprowadzali zmiany w folderach.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint udostępniania na poziomie witryny

Jeśli udostępniasz pliki i foldery, które znajdują się w SharePoint, musisz również sprawdzić ustawienia udostępniania na poziomie witryny dla tej witryny.

![Zrzut ekranu SharePoint ustawień udostępniania zewnętrznego witryny.](../media/sharepoint-site-external-sharing-settings.png)

Aby skonfigurować ustawienia udostępniania na poziomie witryny

1. W centrum SharePoint w lewym okienku nawigacji rozwiń pozycję Witryny **i wybierz pozycję** <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
2. Wybierz witrynę, w której chcesz udostępnić pliki i foldery gościom.
3. Przewiń w prawo wiersz (w którym znajduje się wybrana witryna) i kliknij dowolne miejsce w kolumnie **Udostępnianie** zewnętrzne.
4. Na stronie, która się pojawi, kliknij **kartę** Zasady.
5. W **okienku Udostępnianie zewnętrzne** kliknij pozycję **Edytuj**.
6. Upewnij się, że udostępnianie jest ustawione na **Każdy** lub **Nowy i istniejący goście**.
7. Jeśli zostały wprowadzone zmiany, kliknij przycisk **Zapisz**.

## <a name="invite-users"></a>Zaproś użytkowników

Ustawienia udostępniania gościa są teraz skonfigurowane. dzięki czemu użytkownicy mogą teraz udostępniać pliki i foldery osobom spoza organizacji. Aby [uzyskać więcej informacji OneDrive](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) zobacz SharePoint i Udostępnianie plików [i](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) folderów.

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytanych użytkownikom](best-practices-anonymous-sharing.md)

[Ograniczanie przypadkowego udostępnienia plików podczas udostępniania gościom](share-limit-accidental-exposure.md)

[Integracja programu SharePoint i usługi OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)
