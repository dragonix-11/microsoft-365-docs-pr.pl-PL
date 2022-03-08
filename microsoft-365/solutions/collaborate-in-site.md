---
title: Współpraca z gośćmi w witrynie
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
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
description: Dowiedz się więcej Microsoft 365 czynności konfiguracyjnych niezbędne do skonfigurowania witryny SharePoint do współpracy z gośćmi.
ms.openlocfilehash: 7187149324f88c64570549429f86291320431566
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318543"
---
# <a name="collaborate-with-guests-in-a-site"></a>Współpraca z gośćmi w witrynie

Jeśli chcesz współpracować z gośćmi w dokumentach, danych i na listach, możesz użyć SharePoint sieci Web. Nowoczesne SharePoint są połączone z grupami Microsoft 365 i mogą zarządzać członkostwem w witrynie oraz zapewniać dodatkowe narzędzia do współpracy, takie jak udostępniona skrzynka pocztowa i kalendarz.

W tym artykule o krokach konfiguracji Microsoft 365 celu skonfigurowania witryny SharePoint do współpracy z gośćmi.

## <a name="video-demonstration"></a>Pokaz wideo

W tym klipie wideo przedstawiono kroki konfiguracji opisane w tym dokumencie.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Ustawienia współpracy zewnętrznej na platformie Azure

Udostępnianie w Microsoft 365 jest zarządzane na najwyższym poziomie przez ustawienia współpracy zewnętrznej [B2B w programie Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Jeśli udostępnianie gości jest wyłączone lub ograniczone w usłudze Azure AD, to ustawienie zastępuje wszystkie ustawienia udostępniania skonfigurowane w usłudze Microsoft 365.

Sprawdź ustawienia współpracy zewnętrznej B2B, aby upewnić się, że udostępnianie gościom nie jest zablokowane.

![Zrzut ekranu Azure Active Directory stronę Ustawienia współpracy zewnętrznej.](../media/azure-ad-organizational-relationships-settings.png)

Aby skonfigurować ustawienia współpracy zewnętrznej

1. Zaloguj się w Azure Active Directory stronie [https://aad.portal.azure.com](https://aad.portal.azure.com).
2. W lewym okienku nawigacji kliknij pozycję **Azure Active Directory**.
3. Kliknij **pozycję Tożsamości zewnętrzne**.
4. Na **ekranie Wprowadzenie** w lewym okienku nawigacji kliknij pozycję **Ustawienia współpracy zewnętrznej**.
5. Upewnij się,  że zarówno użytkownicy, jak i użytkownicy przypisani do określonych ról administratora mogą zapraszać użytkowników gości, w  tym gości z uprawnieniami członków, lub każda osoba w organizacji może zapraszać gości, w tym gości i osób niebędących administratorami.
6. Jeśli zostały wprowadzone zmiany, kliknij przycisk **Zapisz**.

Zwróć uwagę na ustawienia w **sekcji Ograniczenia współpracy** . Upewnij się, że domeny gości, z którymi chcesz współpracować, nie są zablokowane.

Jeśli pracujesz z gośćmi z wielu organizacji, możesz ograniczyć im dostęp do danych katalogowych. Uniemożliwi to tej osobie wyświetlanie w katalogu, kto jeszcze jest gościem. W tym celu w obszarze Ograniczenia dostępu użytkowników gości zaznacz pozycję  Użytkownicy goście mają ograniczony dostęp do właściwości i członkostwa w ustawieniach obiektów katalogu lub Dostęp użytkownika gościa jest ograniczony do właściwości i członkostwa we własnych obiektach **katalogu**.

## <a name="microsoft-365-groups-guest-settings"></a>Microsoft 365 grup gości

Nowoczesne SharePoint witryn korzystają Microsoft 365 grupy w celu kontrolowania dostępu do witryny. Ustawienia Microsoft 365 grupy gości muszą być włączone, aby dostęp gościa w witrynach SharePoint działał.

![Zrzut ekranu przedstawiający Microsoft 365 gości grup w aplikacji centrum administracyjne platformy Microsoft 365.](../media/office-365-groups-guest-settings.png)

Aby skonfigurować Microsoft 365 gości grup

1. W okienku centrum administracyjne platformy Microsoft 365 w lewym okienku nawigacji rozwiń pozycję **Ustawienia**.
2. Kliknij **pozycję Ustawienia organizacji**.
3. Na liście kliknij pozycję Microsoft 365 **grupy**.
4. Upewnij się, **że pola wyboru** Pozwól właścicielom grup dodawać osoby spoza organizacji do grupy Microsoft 365 jako gości  i Pozwól członkom grupy gości na dostęp do zawartości grupy są zaznaczone.
5. Jeśli zostały wprowadzone zmiany, kliknij **pozycję Zapisz zmiany**.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint ustawienia udostępniania na poziomie organizacji

Aby goście mieli dostęp do witryn SharePoint, ustawienia udostępniania na SharePoint na poziomie organizacji muszą zezwalać na udostępnianie gościom.

Ustawienia na poziomie organizacji określają ustawienia, które będą dostępne dla poszczególnych witryn. Ustawienia witryny nie mogą być bardziej przesądne niż ustawienia na poziomie organizacji.

Jeśli chcesz zezwolić na udostępnianie nieuwierzytanych plików i folderów, wybierz pozycję **Każdy**. Jeśli chcesz się upewnić, że wszystkie osoby spoza organizacji muszą zostać uwierzytelnione, wybierz pozycję **Nowi i istniejący goście**. Wybierz najbardziej permisyjne ustawienie, które będzie potrzebne w dowolnej witrynie w organizacji.

![Zrzut ekranu SharePoint ustawień udostępniania na poziomie organizacji.](../media/sharepoint-organization-external-sharing-controls.png)


Aby skonfigurować SharePoint udostępniania na poziomie organizacji

1. W okienku centrum administracyjne platformy Microsoft 365 nawigacji po lewej stronie w obszarze **Centra** administracyjne **wybierz pozycję SharePoint**.
2. W centrum SharePoint w lewym okienku nawigacji w **obszarze Zasady** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Udostępnianie**</a>.
3. Upewnij się, że dla udostępniania SharePoint **jest ustawiona** wartość Każdy lub **Nowy i istniejący goście**.
4. Jeśli zostały wprowadzone zmiany, wybierz pozycję **Zapisz**.

## <a name="create-a-site"></a>Tworzenie witryny

Następnym krokiem jest utworzenie witryny, za pomocą której planujesz współpracować z gośćmi.

Aby utworzyć witrynę
1. W centrum SharePoint w **obszarze Witryny** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
2. Wybierz pozycję **Utwórz**.
3. Wybierz **pozycję Witryna zespołu**.
4. Wpisz nazwę witryny i wprowadź nazwę właściciela grupy (właściciela witryny).
5. W **obszarze Ustawienia zaawansowane** określ, czy ta witryna ma być publiczna, czy prywatna.
6. Wybierz pozycję **Dalej**.
7. Wybierz **Zakończ**.

Zaprosimy użytkowników później. Następnie należy sprawdzić ustawienia udostępniania na poziomie witryny dla tej witryny.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint udostępniania na poziomie witryny

Sprawdź ustawienia udostępniania na poziomie witryny, aby upewnić się, że zezwalają one na typ dostępu dla tej witryny. Jeśli na przykład w ustawieniach na poziomie organizacji ustawisz wartość **Każdy, ale** chcesz, aby wszyscy goście uwierzytelnili się w tej witrynie, upewnij się, że ustawienia udostępniania na poziomie witryny są ustawione na Nowi i istniejący **goście**.

Pamiętaj, że witryny nie można udostępniać osobom bez **uwierzytelniania (ustawienie** Każda osoba), ale można udostępniać pojedyncze pliki i foldery.

Etykiety wrażliwości można też [używać do kontrolowania ustawień udostępniania zewnętrznego SharePoint witryn](../compliance/sensitivity-labels-teams-groups-sites.md).

![Zrzut ekranu SharePoint ustawień udostępniania zewnętrznego witryny.](../media/sharepoint-site-external-sharing-settings.png)

Aby skonfigurować ustawienia udostępniania na poziomie witryny
1. W centrum SharePoint w lewym okienku nawigacji rozwiń pozycję **Witryny** i wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
2. Wybierz witrynę, którą chcesz udostępnić.
3. Wybierz pozycję ..., a następnie wybierz **pozycję Udostępnianie**.
4. Upewnij się, że udostępnianie jest ustawione na **Każdy** lub **Nowy i istniejący goście**.
5. Jeśli zostały wprowadzone zmiany, wybierz pozycję **Zapisz**.

## <a name="invite-users"></a>Zaproś użytkowników

Ustawienia udostępniania gościa są teraz skonfigurowane, więc możesz zacząć dodawać do witryny użytkowników wewnętrznych i gości. Dostęp do witryny jest kontrolowany za pośrednictwem skojarzonej Microsoft 365 grupy użytkowników, więc dodamy tam użytkowników.

Aby zaprosić użytkowników wewnętrznych do grupy

1. Przejdź do witryny, w której chcesz dodać użytkowników.
2. Wybierz **link** Członkowie w prawym górnym rogu, co oznacza liczbę członków.
3. Wybierz **pozycję Dodaj członków**.
4. Wpisz nazwy lub adresy e-mail użytkowników, których chcesz zaprosić do witryny, a następnie wybierz pozycję **Zapisz**.

Gości nie można dodawać z witryny. Musisz je dodać przy użyciu Outlook w sieci Web. Dlatego w celu dodawania gości do grupy i zapraszania ich do grupy należy kliknąć adres URL witryny w kolumnie Adres **URL**  , aby przejść do strony specyficznej dla witryny. Na tej stronie kliknij ikonę **Uruchamianie aplikacji** i **wybierz pozycję Outlook**. Jest to ekran, z którego możesz zaprosić gości do grupy, co opisano poniżej.

Aby zaprosić gości do grupy
1. W **obszarze** Grupy kliknij grupę, do której chcesz zaprosić gości.
2. Otwórz wizytówkę grupy, kliknij link **Członkowie** w prawym górnym rogu (link, który oznacza liczbę członków).
3. Kliknij **pozycję Dodaj członków**.
4. Wpisz adresy e-mail gości, których chcesz zaprosić, a następnie kliknij przycisk **Dodaj**.
5. Kliknij przycisk **Zamknij**.
Pamiętaj, że klikanie przycisku Zamknij jest konieczne tylko wtedy, gdy nie jesteś właścicielem grupy, dlatego nie możesz dodać gościa do grupy. W takich przypadkach żądanie dodania gościa do grupy jest przekazywane do właściciela grupy w celu zatwierdzenia.

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytanych użytkownikom](best-practices-anonymous-sharing.md)

[Ograniczanie przypadkowego udostępnienia plików podczas udostępniania gościom](share-limit-accidental-exposure.md)

[Tworzenie bezpiecznego środowiska udostępniania gości](create-secure-guest-sharing-environment.md)

[Tworzenie ekstranetu B2B z gośćmi zarządzanymi](b2b-extranet.md)

[Integracja programu SharePoint i usługi OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)
