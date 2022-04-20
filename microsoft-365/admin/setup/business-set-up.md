---
title: Konfigurowanie usługi Microsoft 365 Business Premium
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- TRN_SMB
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Zapoznaj się z krokami konfiguracji Microsoft 365 Business Premium, w tym dodawaniem domeny i użytkowników, konfigurowaniem zasad zabezpieczeń i nie tylko.
ms.openlocfilehash: 69d158d7193a2f07c6b4c23557474f1458e2fb51
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935900"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>Konfigurowanie Microsoft 365 Business Premium w kreatorze instalacji

## <a name="watch-overview-of-microsoft-365-setup"></a>Obejrzyj: Omówienie konfiguracji Microsoft 365

Obejrzyj ten film wideo, aby zapoznać się z omówieniem konfiguracji Microsoft 365 Business Premium.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="watch-set-up-microsoft-365-business-premium"></a>Obejrzyj: Konfigurowanie Microsoft 365 Business Premium

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

1. Zaloguj się do <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centrum administracyjne platformy Microsoft 365</a> i wybierz pozycję **Przejdź do konfiguracji**. Zostanie uruchomiony kreator instalacji.
1. Po zakończeniu konfiguracji wróć do centrum administracyjnego firmy Microsoft. W centrum administracyjnym możesz kontynuować konfigurowanie funkcji, takich jak zasady Windows 10, DLP itp., na stronie **Konfiguracja**.

## <a name="add-your-domain-users-and-set-up-policies"></a>Dodawanie domeny, użytkowników i konfigurowanie zasad

Podczas zakupu Microsoft 365 Business Premium masz możliwość korzystania z posiadanej domeny lub zakupu jej podczas [rejestracji](../admin-overview/sign-up-for-office-365.md).

- Jeśli nowa domena została zakupiona podczas tworzenia konta, twoja domena jest skonfigurowana i możesz przejść do [pozycji Dodaj użytkowników i przypisać licencje](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Dodawanie domeny w celu spersonalizowania logowania

1. Zaloguj się do [Centrum administracyjne platformy Microsoft 365](https://admin.microsoft.com) przy użyciu poświadczeń administratora globalnego. 

2. Wybierz **pozycję Przejdź do konfiguracji** , aby uruchomić kreatora.

    ![Wybierz pozycję Przejdź do konfiguracji.](../../media/gotosetupinadmincenter.png)

3. Na stronie **Instalowanie aplikacji Office** możesz opcjonalnie zainstalować aplikacje na własnym komputerze.
    
4. W kroku **Dodawanie domeny** wprowadź nazwę domeny, która ma być używana (na przykład contoso.com).

    > [!IMPORTANT]
    > Jeśli domena została zakupiona podczas tworzenia konta, nie zobaczysz tutaj kroku **Dodawanie domeny** . Zamiast tego przejdź do [pozycji Dodaj użytkowników](#add-users-and-assign-licenses) .

    ![Zrzut ekranu przedstawiający stronę Personalizowanie logowania.](../../media/adddomain.png)

    
4. Wykonaj kroki opisane w kreatorze, aby [utworzyć rekordy DNS u dowolnego dostawcy hostingu DNS dla Microsoft 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), który weryfikuje, czy jesteś właścicielem domeny. Jeśli znasz hosta domeny, zobacz również [Dodawanie domeny do Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Jeśli dostawca hostingu to GoDaddy lub inny host z włączoną obsługą [połączenia z domeną](/office365/admin/get-help-with-domains/domain-connect), proces jest łatwy i zostanie automatycznie poproszony o zalogowanie się i umożliwienie firmie Microsoft uwierzytelniania w Twoim imieniu.

    ![Na stronie GoDaddy Confirm Access (Potwierdź dostęp) wybierz pozycję Autoryzuj.](../../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Dodawanie użytkowników i przypisywanie licencji

Możesz dodać użytkowników w kreatorze, ale możesz również [dodać użytkowników w dalszej](../add-users/add-users.md) części centrum administracyjnego. Ponadto jeśli masz lokalny kontroler domeny, możesz dodać użytkowników za pomocą [usługi Azure AD Połączenie](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Dodawanie użytkowników w kreatorze

Wszyscy użytkownicy dodawani w kreatorze otrzymują automatycznie przypisaną licencję Microsoft 365 Business Premium.

![Zrzut ekranu przedstawiający stronę Dodawanie nowych użytkowników w kreatorze.](../../media/addnewuserspage.png)

1. Jeśli twoja subskrypcja Microsoft 365 Business Premium ma istniejących użytkowników (na przykład jeśli używasz usługi Azure AD Połączenie), możesz teraz przypisać do nich licencje. Możesz dodać licencje dla tych użytkowników.

2. Po dodaniu użytkowników otrzymasz również opcję udostępniania poświadczeń nowym dodanym użytkownikom. Możesz wydrukować te informacje, wysłać je pocztą e-mail lub pobrać.

### <a name="connect-your-domain"></a>Łączenie domeny

> [!NOTE]
> Jeśli wybrano opcję używania domeny .onmicrosoft lub użyto usługi Azure AD Połączenie do konfigurowania użytkowników, ten krok nie zostanie wyświetlony.
  
Aby skonfigurować usługi, musisz zaktualizować niektóre rekordy na swoim hoście DNS lub u rejestratora domen.
  
1. Kreator konfiguracji zwykle wykrywa rejestratora i udostępnia linki do instrukcji krok po kroku dotyczących aktualizowania rekordów serwera nazw w witrynie internetowej rejestratora. Jeśli tak się nie stanie, [zmień serwery nazw, aby skonfigurować Microsoft 365 z dowolnym rejestratorem domen](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Jeśli masz istniejące rekordy DNS, na przykład istniejącą witrynę internetową, ale host DNS jest włączony na potrzeby [nawiązywania połączenia z domeną](/office365/admin/get-help-with-domains/domain-connect), wybierz pozycję **Dodaj rekordy dla mnie**. Na stronie **Wybierz Usługi online** zaakceptuj wszystkie wartości domyślne, a następnie wybierz pozycję **Dalej**, a następnie wybierz pozycję **Autoryzuj** na stronie hosta DNS.
    - Jeśli masz istniejące rekordy DNS z innymi hostami DNS (nie włączono połączenia z domeną), chcesz zarządzać własnymi rekordami DNS, aby upewnić się, że istniejące usługi pozostają połączone. Aby uzyskać więcej informacji [, zobacz podstawy domeny](/office365/admin/get-help-with-domains/dns-basics) .

        ![Strona Aktywuj rekordy.](../../media/activaterecords.png)

2. Wykonaj kroki opisane w kreatorze, a adres e-mail i inne usługi zostaną skonfigurowane dla Ciebie.

### <a name="protect-your-organization"></a>Ochrona organizacji 

Zasady skonfigurowane w kreatorze są automatycznie stosowane do [grupy zabezpieczeń](/office365/admin/create-groups/compare-groups#security-groups) o nazwie *Wszyscy użytkownicy*. Można również utworzyć dodatkowe grupy do przypisywania zasad w centrum administracyjnym.

1. W obszarze **Zwiększanie ochrony przed zaawansowanymi zagrożeniami cybernetycznymi** zaleca się zaakceptowanie wartości domyślnych umożliwiających [Office 365 usługi Advance Threat Protection](../../security/office-365-security/defender-for-office-365.md) skanowanie plików i linków w aplikacjach Office.

    ![Zrzut ekranu przedstawiający stronę Zwiększanie ochrony.](../../media/increasetreatprotection.png)


2. Na stronie **Zapobieganie wyciekom poufnych danych** zaakceptuj wartości domyślne, aby włączyć ochronę przed utratą danych usługi Microsoft Purview w celu śledzenia poufnych danych w aplikacjach Office i zapobiegania przypadkowemu udostępnieniu ich poza organizacją.

3. Na stronie **Ochrona danych w Office dla urządzeń przenośnych** pozostaw włączone zarządzanie aplikacjami mobilnymi, rozwiń ustawienia i przejrzyj je, a następnie wybierz pozycję **Utwórz zasady zarządzania aplikacjami mobilnymi**.

    ![Zrzut ekranu przedstawiający stronę Ochrona danych w Office dla urządzeń przenośnych.](../../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>Bezpieczne komputery Windows 10

Na lewym pasku nawigacyjnym wybierz pozycję **Konfiguracja**, a następnie **w obszarze Logowanie i zabezpieczenia** wybierz pozycję **Zabezpieczanie Windows 10 komputerów**. Wybierz pozycję **Widok** , aby rozpocząć pracę. Aby uzyskać pełne instrukcje, zobacz [zabezpieczanie komputerów Windows 10](secure-win-10-pcs.md).

## <a name="deploy-office-365-client-apps"></a>Wdrażanie aplikacji klienckich Office 365

Jeśli podczas instalacji wybrano opcję automatycznego instalowania aplikacji Office, aplikacje zostaną zainstalowane na urządzeniach Windows 10 po zalogowaniu się użytkowników do usługi Azure AD z urządzeń Windows przy użyciu poświadczeń służbowych.

Aby zainstalować Office na urządzeniach przenośnych z systemem iOS lub Android, zobacz [Konfigurowanie urządzeń przenośnych dla użytkowników Microsoft 365 Business Premium](set-up-mobile-devices.md).

Można również zainstalować Office osobno. Aby uzyskać instrukcje, zobacz [instalowanie Office na komputerze PC lub Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658).

## <a name="related-content"></a>Zawartość pokrewna

[Microsoft 365 wideo z szkoleniami biznesowymi](../../business-video/index.yml) (strona linku)
