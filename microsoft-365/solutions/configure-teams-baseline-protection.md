---
title: Konfigurowanie zespołów przy użyciu ochrony linii bazowej
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkTEAMS
- admindeeplinkSPO
recommendations: false
description: Dowiedz się, jak wdrażać zespoły z bazowym poziomem ochrony.
ms.openlocfilehash: 21fe46a9df9b67c41ff2c0a21fbbe175295e1fdf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312743"
---
# <a name="configure-teams-with-baseline-protection"></a>Konfigurowanie zespołów przy użyciu ochrony linii bazowej

W tym artykule opisano sposób wdrażania zespołów z bazowym poziomem ochrony. Ten poziom umożliwia użytkownikom korzystanie z szerokiej gamy opcji współpracy przy jednoczesnym ulepszaniu zarządzania uprawnieniami i zapewnieniu podstawowej ochrony przed zbytnim udostępnianiem. Zalecanymi zabezpieczeniami na tym poziomie są zasady tożsamości i dostępu do urządzeń oraz ochrona przed złośliwym oprogramowaniem. Ponadto można w razie potrzeby stosować zasady dostępu warunkowego i ochronę przed utratą danych.

## <a name="initial-protections"></a>Ochrona początkowa

Pierwszym krokiem jest skonfigurowanie podstawowych zasad dostępu do tożsamości i urządzeń. Aby [uzyskać szczegółowe informacje, zobacz Zalecenia dotyczące zasad Teams czatów, grup i](../security/office-365-security/teams-access-policies.md) plików.

Zalecamy również włączenie podstawowego programu Defender dla Office 365 w celu ochrony przed złośliwym oprogramowaniem w dokumentach, załącznikach i linkach. Zalecamy włączenie każdej z opcji w poniższej tabeli.

|Opcja|Informacje|
|:------|:-----------|
|Sejf załączników dla spo, OneDrive i Teams|[Sejf załączników](../security/office-365-security/safe-attachments.md) <p> [Defender for Office 365 - SharePoint, OneDrive, and Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md)|
|Bezpieczne dokumenty|[Sejf programu Microsoft Defender dla systemu Office 365](../security/office-365-security/safe-docs.md)|
|Sejf linków dla Teams|[Office 365 Sejf w programie Teams](../security/office-365-security/safe-links.md) <p> [Bezpieczne linki](../security/office-365-security/safe-links.md)|

## <a name="teams-guest-sharing"></a>Teams udostępniania gościa

Na każdej z tych warstw mamy możliwość udostępnienia osobom spoza Twojej organizacji. W przypadku warstw poufnych i bardzo poufnych będziemy mieć możliwość wyłączenia udostępniania gościa na poziomie zespołu przy użyciu etykiet wrażliwości. Jednak aby udostępnianie gości działało w całym programie, ustawienie udostępniania gości na poziomie organizacji musi być Teams.

![Zrzut ekranu Teams przełącznik dostępu gościa.](../media/teams-guest-access-toggle-on.png)

Aby skonfigurować Teams dostępu gościa

1. Zaloguj się do centrum administracyjne platformy Microsoft 365 na stronie [https://admin.microsoft.com](https://admin.microsoft.com).
2. W lewym okienku nawigacji kliknij pozycję **Pokaż wszystko**.
3. W **obszarze Centra administracyjne** kliknij pozycję **Teams**.
4. W centrum Teams w lewym okienku nawigacji rozwiń pozycję Ustawienia **dla całej** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**organizacjiNajśniejszy dostęp**</a>.
5. Upewnij się **, że ustawienie Zezwalaj** na dostęp Teams w programie jest **ustawione na wartość Wł**.
6. Wprowadzić odpowiednie zmiany w dodatkowych ustawieniach gościa, a następnie kliknąć przycisk **Zapisz**.

> [!NOTE]
> Może upłynie do dwudziestu czterech godzin, Teams ustawienie gościa zostanie aktywne po jego włączeniu.

Udostępnianie gości jest domyślnie włączone dla grup programu Office 365 i programu SharePoint, jednak jeśli wcześniej zmieniono dowolne ustawienia udostępniania gości w organizacji, zalecamy zapoznanie się z tematem Współpraca z gośćmi w zespole w celu zapewnienia [](./collaborate-as-team.md) udostępniania gościom w aplikacji Teams.

## <a name="site-and-file-sharing"></a>Udostępnianie witryn i plików

Aby ograniczyć ryzyko przypadkowego udostępniania plików lub folderów osobom spoza organizacji, zalecamy zmianę domyślnego linku udostępniania dla kontaktów SharePoint na Tylko osoby *w Twojej organizacji*. (Jeśli użytkownicy będą musieli udostępniać zewnętrznie i włączysz udostępnianie gości, nadal mogą zmienić typ linku podczas udostępniania).

Aby zmienić domyślny link udostępniania

1. Otwórz centrum SharePoint w obszarze **Zasady** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Udostępnianie**</a>.
1. W **obszarze Linki do plików i folderów** wybierz pozycję **Tylko osoby w Twojej organizacji**.
1. Wybierz **Zapisz**.

W celu najlepszego środowiska udostępniania gościa zalecamy również włączenie integracji usług [SharePoint i OneDrive z usługą Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview).

## <a name="create-a-team"></a>Tworzenie zespołu

Dodatkowa konfiguracja podstawowego poziomu ochrony jest wykonywana w witrynie SharePoint skojarzonej z zespołem. [Przed przystąpieniem do następnej](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b) sekcji utwórz publiczny lub prywatny zespół.

## <a name="site-sharing-settings"></a>Ustawienia udostępniania witryn

Domyślnie członkowie witryny sieci SharePoint mogą zapraszać inne osoby do witryny. Gdy witryna należy do zespołu, członkowie zespołu są uwzględniani jako członkowie witryny. Jednak osoby dodane bezpośrednio do witryny nie mają dostępu do pozostałych członków zespołu. Dlatego zalecamy zarządzanie uprawnieniami wyłącznie za pośrednictwem zespołu.

Aby ułatwić zarządzanie uprawnieniami, zalecamy skonfigurowanie skojarzonej witryny tak, aby umożliwić udostępnianie witryny tylko właścicielom. Upraszcza to zarządzanie uprawnieniami i pomaga zapobiegać dostępowi osób bez wiedzy właściciela zespołu. Zrób to dla każdego zespołu, który wymaga ochrony według planu bazowego.

Aby zaktualizować ustawienia udostępniania witryny
1. Na pasku narzędzi zespołu kliknij pozycję **Pliki**.
2. Kliknij **pozycję Otwórz w SharePoint**.
3. Na pasku narzędzi witryny SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
4. W **okienku Uprawnienia** witryny w obszarze **Udostępnianie witryny** kliknij pozycję Zmień sposób udostępniania **przez członków**.
5. W **obszarze Uprawnienia udostępniania** wybierz pozycję Właściciele i członkowie witryny, a osoby z uprawnieniami do edytowania mogą udostępniać pliki i foldery **,** ale tylko właściciele witryn mogą udostępniać witrynę, a następnie kliknij pozycję **Zapisz**.

## <a name="additional-protections"></a>Dodatkowe zabezpieczenia

Microsoft 365 oferuje dodatkowe metody zabezpieczania zawartości. Rozważ, czy poniższe opcje zwiększą bezpieczeństwo Twojej organizacji.

- Goście muszą zaakceptować [warunki użytkowania](/azure/active-directory/conditional-access/terms-of-use).
- Konfigurowanie zasad [limitu czasu sesji](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) dla gości.
- Utwórz [typy informacji poufnych i](../compliance/sensitive-information-type-learn-about.md) korzystaj [z ochrony przed utratą danych](../compliance/dlp-learn-about-dlp.md) , aby ustawić zasady dotyczące uzyskiwania dostępu do informacji poufnych.

## <a name="see-also"></a>Zobacz też

[Zarządzanie zasadami spotkań w programie Teams](/microsoftteams/meeting-policies-in-teams)

[Wprowadzenie do zarządzania ryzykiem w niejawnym programie testów](../compliance/insider-risk-management-configure.md)