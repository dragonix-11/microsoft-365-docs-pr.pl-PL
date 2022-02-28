---
title: Tworzenie ekstranetu B2B z gośćmi zarządzanymi
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
ms.custom: ''
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Dowiedz się, jak utworzyć witrynę ekstranetową B2B lub zespół z zarządzanymi gośćmi z organizacji partnerskiej.
ms.openlocfilehash: ab8bba31538b9e79ed198f65349f14d8211f81f7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983679"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>Tworzenie ekstranetu B2B z gośćmi zarządzanymi

Za pomocą zarządzania Azure Active Directory [uprawnieniami](/azure/active-directory/governance/entitlement-management-overview) możesz utworzyć ekstranet B2B do współpracy z organizacją partnerską, która korzysta z Azure Active Directory. Dzięki temu użytkownicy mogą samodzielnie zarejestrować się w witrynie ekstranetowej lub zespole i uzyskać dostęp za pośrednictwem przepływu pracy zatwierdzania.

Dzięki tej metodzie udostępniania zasobów do współpracy organizacja partnerska może pomóc w konserwacji i zatwierdzaniu gości po ich stronie, zmniejszając obciążenie działu IT i pozwalając osobom najbardziej zaznajomieni z umową o współpracy na zarządzanie dostępem użytkowników.

Ten artykuł zawiera kroki tworzenia pakietu zasobów (w tym przypadku witryny lub zespołu), które można udostępnić organizacji partnerskiej za pomocą modelu samodzielnej rejestracji dostępu. 

Przed rozpoczęciem utwórz witrynę lub zespół, który chcesz udostępnić organizacji partnerskiej, i włącz go do udostępniania gościom. Aby [uzyskać więcej informacji, zobacz Współpraca z gośćmi w](collaborate-in-site.md) witrynie lub Współpraca [z](collaborate-as-team.md) gośćmi w zespole. Zalecamy również zapoznanie się z tematem Tworzenie bezpiecznego środowiska udostępniania gościa, aby uzyskać informacje o funkcjach zabezpieczeń i zgodności, których można używać do obsługi zasad zarządzania podczas współpracy z gośćmi.[](create-secure-guest-sharing-environment.md)

## <a name="license-requirements"></a>Wymagania dotyczące licencji

Korzystanie z tej funkcji wymaga licencji Azure AD — wersja Premium P2 licencji. 

Specjalistyczne chmury, takie jak Azure Germany i Azure China 21Vianet, nie są obecnie dostępne do użycia.

## <a name="video-demonstration"></a>Pokaz wideo

Ten klip wideo przedstawia procedury objęte tym artykułem.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wKUj?autoplay=false]

## <a name="connect-the-partner-organization"></a>Połączenie organizacji partnerskiej

Aby zaprosić gości z organizacji partnerskiej, musisz dodać domenę tego partnera jako połączną organizację w Azure Active Directory.

Aby dodać połączną organizację
1. W [Azure Active Directory](https://aad.portal.azure.com) kliknij pozycję **Zarządzanie tożsamością**.
2. Kliknij **pozycję Połączone organizacje**.
4. Kliknij **pozycję Dodaj połączną organizację**.
5. Wpisz nazwę i opis organizacji, a następnie kliknij pozycję **Dalej: Katalog + domena**.
6. Kliknij **pozycję Dodaj katalog + domenę**.
7. Wpisz domenę organizacji, którą chcesz połączyć, a następnie kliknij przycisk **Dodaj**.
8. Kliknij **Połączenie**, a następnie kliknij pozycję **Dalej: Sponsorzy**.
9. Dodaj osoby ze swojej organizacji lub organizacji, z którą chcesz się połączyć, aby zatwierdzić dostęp dla gości.
10. Kliknij **pozycję Następny: Recenzja + Utwórz**.
11. Przejrzyj wybrane ustawienia, a następnie kliknij przycisk **Utwórz**.

    ![Zrzut ekranu przedstawiający stronę połączonej organizacji w aplikacji Azure Active Directory.](../media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>Wybieranie zasobów do udostępnienia

Pierwszym krokiem podczas wybierania zasobów do udostępnienia organizacji partnerskiej jest utworzenie katalogu zawierającego te zasoby.

Aby utworzyć wykaz
1. W [Azure Active Directory](https://aad.portal.azure.com) kliknij pozycję **Zarządzanie tożsamością**.
2. Kliknij **pozycję Wykazy**.
3. Kliknij **pozycję Nowy wykaz**.
4. Wpisz nazwę i opis wykazu, a następnie upewnij się,  że dla  użytkowników zewnętrznych włączono i włączono wartość **Tak**.
5. Kliknij **przycisk Utwórz**.

   ![Zrzut ekranu przedstawiający stronę wykazów w programie Azure Active Directory tożsamości.](../media/identity-governance-catalogs.png)

Po utworzeniu wykazu dodaj witrynę SharePoint zespołu, którą chcesz udostępnić organizacji partnerskiej.

Aby dodać zasoby do wykazu
1. W usłudze Azure AD Identity Governance (Zarządzanie tożsamościami) kliknij pozycję **Catalogs (Wykazy**), a następnie kliknij katalog, do którego chcesz dodać zasoby.
2. Kliknij **pozycję Zasoby** , a następnie **kliknij pozycję Dodaj zasoby**.
3. Wybierz zespoły lub SharePoint, które chcesz dołączyć do ekstranetu, a następnie kliknij przycisk **Dodaj**.

   ![Zrzut ekranu przedstawiający stronę zasobów wykazu w programie Azure Active Directory zarządzanie tożsamością.](../media/identity-governance-catalog-resource.png)

Po zdefiniowaniu zasobów, które chcesz udostępnić, następnym krokiem jest utworzenie pakietu dostępu definiującego typ dostępu udzielanego użytkownikom partnerów oraz proces zatwierdzania dla nowych użytkowników partnerów żądających dostępu.

Aby utworzyć pakiet dostępu
1. W usłudze Azure AD Identity Governance (Zarządzanie tożsamościami) kliknij pozycję **Catalogs (Wykazy**), a następnie kliknij wykaz, w którym chcesz utworzyć pakiet dostępu.
2. Kliknij **pozycję Pakiety programu Access**, a następnie kliknij **pozycję Nowy pakiet dostępu**.
3. Wpisz nazwę i opis pakietu dostępu, a następnie kliknij przycisk **Dalej: Role zasobów**.
4. Wybierz zasoby z wykazu, którego chcesz użyć w ekstranetu.
5. Dla każdego zasobu w kolumnie **Rola** wybierz rolę użytkownika, którą chcesz przyznać gościom, którzy korzystają z ekstranetu.
6. Kliknij **przycisk Dalej: Żądania**.
7. W **obszarze Użytkownicy, którzy mogą zażądać dostępu** wybierz **pozycję Dla użytkowników nieuzysłychanych w katalogu**.
8. Upewnij się, **że jest zaznaczona opcja Określone połączone organizacje** , a następnie kliknij **pozycję Dodaj katalogi**.
9. Wybierz połączną organizację, która zostanie wcześniej dołączona, a następnie kliknij pozycję **Wybierz.**
10. W **obszarze Zatwierdzanie** wybierz pozycję **Tak** dla **opcji Wymagaj zatwierdzenia**.
11. W **obszarze Pierwsza osoba** zatwierdzająca wybierz jednego ze sponsorów dodanych wcześniej lub wybierz określonego użytkownika.
12. Kliknij **pozycję Dodaj rezerwowy** i wybierz osoby zatwierdzające rezerwowe.
13. W **obszarze Włącz** wybierz pozycję **Tak**.
14. Kliknij **przycisk Dalej: Cykl życia**.
15. Wybierz ustawienia wygasania i przeglądania dostępu, których chcesz użyć, a następnie kliknij pozycję Dalej **: Recenzja + Utwórz**.
16. Przejrzyj ustawienia, a następnie kliknij przycisk **Utwórz**.

    ![Zrzut ekranu przedstawiający ekran pakietów dostępu w programie Azure Active Directory tożsamości.](../media/identity-governance-access-packages.png)

Jeśli współpracujesz z dużą organizacją, możesz ukryć pakiet dostępu. Jeśli pakiet jest ukryty, użytkownicy w organizacji partnerskiej nie zobaczą pakietu w swoim portalu *Mój* dostęp. Zamiast tego należy wysłać im bezpośredni link, aby zapisać się na pakiet. Ukrycie pakietu dostępu może zmniejszyć liczbę nieodpowiednich żądań dostępu, a także pomóc w zorganizowaniu dostępnych pakietów dostępu w portalu organizacji partnerskiej.

Aby ustawić pakiet dostępu jako ukryty
1. W usłudze Azure AD Identity Governance kliknij pozycję **Pakiety programu Access**, a następnie kliknij pakiet dostępu.
2. Na stronie **Przegląd** kliknij pozycję **Edytuj**.
3. W **obszarze Właściwości** wybierz pozycję **Tak** dla **opcji Ukryte**, a następnie kliknij przycisk **Zapisz**.

   ![Zrzut ekranu przedstawiający ekran edytowania właściwości pakietu dostępu.](../media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>Zapraszanie użytkowników partnerów

Jeśli ustawisz pakiet dostępu jako ukryty, musisz wysłać bezpośredni link do organizacji partnerskiej, aby ten użytkownik może zażądać dostępu do twojej witryny lub zespołu.

Aby znaleźć link do portalu dostępu
1. W usłudze Azure AD Identity Governance kliknij pozycję **Pakiety programu Access**, a następnie kliknij pakiet dostępu.
2. Na stronie **Omówienie** kliknij pozycję Kopiuj do **schowka** dla **linku Mój portal programu Access**.

   ![Zrzut ekranu przedstawiający właściwości pakietu programu Access z linkiem do portalu programu Access.](../media/identity-governance-access-portal-link.png)

Po skopiowaniu linku możesz udostępnić go kontaktowi w organizacji partnerskiej, a następnie wysłać go do użytkowników w zespole współpracy.

## <a name="see-also"></a>Zobacz też

[Tworzenie bezpiecznego środowiska udostępniania gości](create-secure-guest-sharing-environment.md)