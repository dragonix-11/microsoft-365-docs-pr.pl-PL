---
title: Współpraca z gośćmi w zespole
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
- admindeeplinkMAC
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się więcej Microsoft 365 czynnościach konfiguracyjnych niezbędnych do skonfigurowania zespołu do współpracy nad zadaniami, konwersacjami i dokumentacją z gośćmi w Teams.
ms.openlocfilehash: bb6ccf4f3e17192d86675d99072eca8b836973e2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324553"
---
# <a name="collaborate-with-guests-in-a-team"></a>Współpraca z gośćmi w zespole

Jeśli chcesz współpracować z gośćmi w dokumentach, zadaniach i konwersacjach, zalecamy skorzystanie z Microsoft Teams. Teams udostępnia wszystkie funkcje współpracy dostępne w usługach Office i SharePoint za pomocą rozmów trwałych oraz dostosowywalny i rozszerzalny zestaw narzędzi do współpracy w ujednoliconym interfejsie użytkownika.

W tym artykule o krokach konfigurowania zespołu Microsoft 365 czynności niezbędne do skonfigurowania zespołu do współpracy z gośćmi. Po skonfigurowaniu dostępu gości możesz zaprosić gości do zespołów, korzystając z procedury opisanej w te sposób: Dodawanie gości do zespołu w [aplikacji Teams](https://support.microsoft.com/office/fccb4fa6-f864-4508-bdde-256e7384a14f).

## <a name="video-demonstration"></a>Pokaz wideo

W tym klipie wideo przedstawiono kroki konfiguracji opisane w tym dokumencie.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Ustawienia współpracy zewnętrznej na platformie Azure

Udostępnianie w Microsoft 365 jest zarządzane na najwyższym poziomie przez ustawienia współpracy zewnętrznej [B2B w programie Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Jeśli udostępnianie gości jest wyłączone lub ograniczone w usłudze Azure AD, to ustawienie zastępuje wszystkie ustawienia udostępniania skonfigurowane w usłudze Microsoft 365.

Sprawdź ustawienia zewnętrznych ustawień współpracy B2B, aby upewnić się, że udostępnianie gościom nie jest zablokowane.

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

## <a name="teams-guest-access-settings"></a>Teams dostępu gościa

Teams ma włączony/wyłączony główny przełącznik dostępu gościa oraz różne ustawienia dostępne w celu kontrolowania, co goście mogą robić w zespole. Przełącznik główny **Zezwalaj na dostęp gościa w programie Teams** musi być  włączony, aby dostęp gościa działał w Teams.

Upewnij się, że dostęp gościa jest włączony w aplikacji Teams i w zależności od potrzeb biznesowych możesz wprowadzić odpowiednie zmiany w ustawieniach gościa. Pamiętaj, że te ustawienia wpływają na wszystkie zespoły.

![Zrzut ekranu Teams przełącznik dostępu gościa.](../media/teams-guest-access-toggle-on.png)

Aby skonfigurować Teams dostępu gościa

1. Zaloguj się do centrum administracyjne platformy Microsoft 365 na stronie [https://admin.microsoft.com](https://admin.microsoft.com).
2. W lewym okienku nawigacji kliknij pozycję **Pokaż wszystko**.
3. W **obszarze Centra administracyjne** kliknij pozycję **Teams**.
4. W centrum Teams w okienku nawigacji po lewej stronie wybierz pozycję **UżytkownicyO** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**dostępu**</a>.
5. Upewnij się **, że ustawienie Zezwalaj** na dostęp Teams w programie jest **ustawione na wartość Wł**.
6. Wprowadzić odpowiednie zmiany w dodatkowych ustawieniach gościa, a następnie kliknąć przycisk **Zapisz**.

Po Teams dostępu gościa możesz opcjonalnie kontrolować dostęp gościa do poszczególnych zespołów i powiązanych z nimi witryn SharePoint przy użyciu etykiet wrażliwości. Aby uzyskać więcej informacji, zobacz Chroninie zawartości w witrynach sieci [Microsoft Teams, Microsoft 365 i SharePoint zawartości za pomocą etykiet wrażliwości](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> Może upłynie do dwudziestu czterech godzin, Teams ustawienia gościa staną się aktywne po jego włączeniu.

## <a name="microsoft-365-groups-guest-settings"></a>Microsoft 365 grup gości

Teams członków Microsoft 365 grupy. Ustawienia Microsoft 365 grupy gości muszą być włączone, aby dostęp gościa Teams działał.

![Zrzut ekranu przedstawiający Microsoft 365 gości grup w aplikacji centrum administracyjne platformy Microsoft 365.](../media/office-365-groups-guest-settings.png)

Aby skonfigurować Microsoft 365 gości grup

1. W okienku centrum administracyjne platformy Microsoft 365 w lewym okienku nawigacji rozwiń pozycję **Ustawienia**.
2. Kliknij **pozycję Ustawienia organizacji**.
3. Na liście kliknij pozycję Microsoft 365 **grupy**.
4. Upewnij się, **że pola wyboru** Pozwól właścicielom grup dodawać osoby spoza organizacji do grupy Microsoft 365 jako gości  i Pozwól członkom grupy gości na dostęp do zawartości grupy są zaznaczone.
5. Jeśli zostały wprowadzone zmiany, kliknij **pozycję Zapisz zmiany**.


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint ustawień udostępniania na poziomie organizacji

Teams, jak pliki, foldery i listy, są przechowywane w SharePoint. Aby goście mieli dostęp do tych elementów w programie Teams, ustawienia udostępniania na SharePoint na poziomie organizacji muszą zezwalać na udostępnianie gościom.

Ustawienia na poziomie organizacji określają, jakie ustawienia są dostępne dla poszczególnych witryn, w tym witryn skojarzonych z zespołami. Ustawienia witryny nie mogą być bardziej przesądne niż ustawienia na poziomie organizacji.

Jeśli chcesz zezwolić na udostępnianie plików i folderów osobom bez uwierzytelniania, wybierz pozycję **Każdy**. Jeśli chcesz się upewnić, że wszyscy goście muszą zostać uwierzytelnieni, wybierz **pozycję Nowi i istniejący goście**. Wybierz najbardziej permisyjne ustawienie, które będzie potrzebne w dowolnej witrynie w organizacji.

![Zrzut ekranu SharePoint ustawień udostępniania na poziomie organizacji.](../media/sharepoint-organization-external-sharing-controls.png)


Aby skonfigurować SharePoint udostępniania na poziomie organizacji

1. W <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">centrum administracyjne platformy Microsoft 365 nawigacji</a> w lewym okienku nawigacji w obszarze **Centra** administracyjne **wybierz pozycję SharePoint**.
2. W centrum SharePoint w lewym okienku nawigacji rozwiń pozycję **Zasady**, a następnie wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Udostępnianie**</a>.
3. Upewnij się, że dla udostępniania SharePoint **jest ustawiona** wartość Każdy lub **Nowy i istniejący goście**.
4. Jeśli zostały wprowadzone zmiany, wybierz pozycję **Zapisz**.


## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint domyślnych ustawień linku na poziomie organizacji

Domyślne ustawienia linku do plików i folderów określają opcję linku, która będzie domyślnie wyświetlana użytkownikom, gdy udostępnią plik lub folder. W razie potrzeby użytkownicy mogą zmienić typ linku na jedną z pozostałych opcji przed udostępnieniem.

Pamiętaj, że to ustawienie ma wpływ na wszystkie zespoły i witryny SharePoint organizacji.

Wybierz dowolny z następujących typów linków, które będą domyślnie wybierane, gdy użytkownicy będą udostępniać pliki i foldery:

- **Każda osoba z linkiem** — wybierz tę opcję, jeśli chcesz wykonać wiele nieuwierzytanych udostępniania plików i folderów. Jeśli chcesz zezwolić na linki *Anyone* (Każda osoba), ale martwi Cię o przypadkowe nieuwierzysfanie udostępniania, jako domyślną rozważ jedną z pozostałych opcji. Ten typ linku jest dostępny tylko w przypadku, gdy włączono **udostępnianie każda** osoba.
- **Tylko osoby w Twojej organizacji** — wybierz tę opcję, jeśli oczekujesz, że większość udostępniania plików i folderów będzie dotyczyć osób w Twojej organizacji.
- **Określone osoby** — rozważ tę opcję, jeśli spodziewasz się udostępniać dużo plików i folderów gościom. Ten typ linku działa z gośćmi i wymaga uwierzytelnienia.
 
![Zrzut ekranu SharePoint ustawień udostępniania plików i folderów na poziomie organizacji.](../media/sharepoint-organization-files-folders-sharing-settings.png)


Aby skonfigurować SharePoint domyślnych ustawień linku na poziomie organizacji

1. Przejdź do <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**pozycji Udostępnianie**</a> w SharePoint administracyjnego.
2. W **obszarze Linki do plików i folderów** wybierz domyślny link udostępniania, którego chcesz użyć.
3. Jeśli zostały wprowadzone zmiany, wybierz pozycję **Zapisz**.

## <a name="create-a-team"></a>Tworzenie zespołu

Następnym krokiem jest utworzenie zespołu, który będzie można wykorzystać do współpracy z gośćmi.

Aby utworzyć zespół
1. W Teams zaawansowanej na **Teams** kliknij pozycję Dołącz do zespołu lub utwórz zespół  u dołu lewego okienka.
2. Kliknij **pozycję Utwórz zespół**.
3. Kliknij **pozycję Zbuduj zespół od podstaw**.
4. Wybierz **pozycję Prywatne** lub **Publiczne**.
5. Wpisz nazwę i opis zespołu, a następnie kliknij pozycję **Utwórz**.
6. Kliknij **przycisk Pomiń**.

Zaprosimy użytkowników później. Następnie należy sprawdzić ustawienia udostępniania na poziomie witryny SharePoint skojarzonej z zespołem.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint udostępniania na poziomie witryny

Sprawdź ustawienia udostępniania na poziomie witryny, aby upewnić się, że zezwalają one na typ dostępu, jaki chcesz uzyskać dla tego zespołu. Jeśli na przykład w ustawieniach na poziomie organizacji ustawisz wartość **Każdy, ale** chcesz, aby wszyscy goście uwierzytelnili się w tym zespole, upewnij się, że ustawienia udostępniania na poziomie witryny są ustawione na Nowi i istniejący **goście**.

![Zrzut ekranu SharePoint ustawień udostępniania zewnętrznego witryny.](../media/sharepoint-site-external-sharing-settings.png)

Aby skonfigurować ustawienia udostępniania na poziomie witryny
1. W centrum SharePoint w lewym okienku nawigacji rozwiń pozycję Witryny **i wybierz pozycję** <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
2. Wybierz witrynę dla właśnie utworzonego zespołu.
3. Wybierz pozycję ... i wybierz **pozycję Udostępnianie**.
4. Upewnij się, że udostępnianie jest ustawione na **Każdy** lub **Nowy i istniejący goście**.
5. Jeśli zostały wprowadzone zmiany, wybierz pozycję **Zapisz**.

## <a name="invite-users"></a>Zaproś użytkowników

Ustawienia udostępniania gościa są teraz skonfigurowane, więc możesz rozpocząć dodawanie do zespołu użytkowników wewnętrznych i gości. 

Aby zaprosić użytkowników wewnętrznych do zespołu
1. W zespole kliknij pozycję **Więcej opcji** (**\*\*\***), a następnie kliknij pozycję **Dodaj członka**.
2. Wpisz imię i nazwisko osoby, którą chcesz zaprosić.
3. Kliknij **przycisk Dodaj**, a następnie kliknij przycisk **Zamknij**.

Aby zaprosić gości do zespołu
1. W zespole kliknij pozycję **Więcej opcji** (**\*\*\***), a następnie kliknij pozycję **Dodaj członka**.
2. Wpisz adres e-mail gościa, którego chcesz zaprosić.
3. Kliknij **pozycję Edytuj informacje o gościu**.
4. Wpisz imię i nazwisko gościa i kliknij znacznik wyboru.
5. Kliknij **przycisk Dodaj**, a następnie kliknij przycisk **Zamknij**.

> [!NOTE]
> Gości z kontem służbowym można zaprosić jedynie za pomocą głównych nazw użytkowników (UPN) (na przykład adele@contoso.com). Zapraszanie gości przy użyciu identyfikatora EAS lub innych formatów poczty e-mail nie jest obsługiwane.

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania dotyczące udostępniania plików i folderów nieuwierzytanych użytkownikom](best-practices-anonymous-sharing.md)

[Ograniczanie przypadkowego udostępnienia plików podczas udostępniania gościom](share-limit-accidental-exposure.md)

[Tworzenie bezpiecznego środowiska udostępniania gości](create-secure-guest-sharing-environment.md)

[Tworzenie ekstranetu B2B z gośćmi zarządzanymi](b2b-extranet.md)

[Integracja programu SharePoint i usługi OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview)

[Opcje udostępniania są wyszzarowane podczas udostępniania z SharePoint lub OneDrive](/sharepoint/troubleshoot/administration/sharing-options-grayed-out-when-sharing-from-sharepoint-online-or-onedrive)
