---
title: Konfigurowanie zespołów z ochroną danych poufnych
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
- admindeeplinkSPO
recommendations: false
description: Dowiedz się, jak wdrażać zespoły z ochroną danych poufnych.
ms.openlocfilehash: 2ea13fbf8a677ba4a04efbd0b2a6fdfed7d80644
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941286"
---
# <a name="configure-teams-with-protection-for-sensitive-data"></a>Konfigurowanie zespołów z ochroną danych poufnych

W tym artykule przyjrzymy się konfigurowaniu zespołu pod kątem wrażliwego poziomu ochrony. Przed wykonaniem kroków opisanych w tym artykule upewnij się, że wykonano kroki opisane w [temacie Wdrażanie zespołów z ochroną punktu odniesienia](configure-teams-baseline-protection.md) . Warstwa wrażliwa oferuje następujące dodatkowe zabezpieczenia w warstwie odniesienia:

- Etykieta poufności dla zespołu, która umożliwia włączanie lub wyłączanie udostępniania gości oraz ogranicza dostęp do zawartości SharePoint tylko do sieci Web dla urządzeń niezarządzanych. Ta etykieta może być również używana do klasyfikowania plików.
- Bardziej restrykcyjny domyślny typ linku udostępniania
- Tylko właściciele zespołów mogą tworzyć kanały prywatne.

## <a name="video-demonstration"></a>Pokaz wideo

Obejrzyj ten film wideo, aby zapoznać się z procedurami opisanymi w tym artykule.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NMS6]

## <a name="guest-sharing"></a>Udostępnianie gościa

W zależności od charakteru firmy możesz lub nie chcesz włączać udostępniania gości dla zespołów zawierających poufne dane. Jeśli planujesz współpracę z osobami spoza organizacji w zespole, zalecamy włączenie udostępniania gości. Microsoft 365 obejmuje różne funkcje zabezpieczeń i zgodności, które ułatwiają bezpieczne udostępnianie poufnych zawartości. Jest to zazwyczaj bezpieczniejsza opcja niż wysyłanie zawartości pocztą e-mail bezpośrednio do osób spoza organizacji.

Aby uzyskać szczegółowe informacje na temat bezpiecznego udostępniania gościom, zobacz następujące zasoby:

- [Ograniczanie przypadkowego narażenia na pliki podczas udostępniania osobom spoza organizacji](./share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gościa](./create-secure-guest-sharing-environment.md)

Aby zezwolić na udostępnianie gościom lub zablokować go, używamy kombinacji etykiety poufności dla zespołu i kontrolek udostępniania na poziomie witryny dla skojarzonej witryny SharePoint, które zostały omówione później.

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

W przypadku wrażliwego poziomu ochrony będziemy używać etykiety poufności do klasyfikowania zespołu. Ta etykieta może być również używana do klasyfikowania pojedynczych plików w tym lub innych zespołach lub w innych lokalizacjach plików, takich jak SharePoint lub OneDrive. 

W pierwszym kroku należy włączyć etykiety poufności dla Teams. Aby uzyskać szczegółowe informacje[, zobacz Używanie etykiet poufności do ochrony zawartości w witrynach Microsoft Teams, grup Office 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

Jeśli masz już etykiety poufności wdrożone w organizacji, zastanów się, jak ta etykieta pasuje do ogólnej strategii etykiet. W razie potrzeby możesz zmienić nazwę lub ustawienia, aby spełnić potrzeby organizacji.

Po włączeniu etykiet poufności dla Teams następnym krokiem jest utworzenie etykiety.

Aby utworzyć etykietę poufności
1. Otwórz [portal zgodności usługi Microsoft Purview](https://compliance.microsoft.com).
2. W obszarze **Rozwiązania** kliknij pozycję **Ochrona informacji**.
3. Kliknij **pozycję Utwórz etykietę**.
4. Nadaj etykiecie nazwę. Sugerujemy **poufne**, ale możesz wybrać inną nazwę, jeśli ta jest już używana.
5. Dodaj nazwę wyświetlaną i opis, a następnie kliknij przycisk **Dalej**.
6. Na **stronie Definiowanie zakresu dla tej etykiety** wybierz pozycję **Pliki & wiadomości e-mail** i **grupy & witrynach** , a następnie kliknij przycisk **Dalej**.
7. Na stronie **Wybieranie ustawień ochrony plików i wiadomości e-mail** kliknij przycisk **Dalej**.
8. Na stronie *Automatyczne etykietowanie plików i wiadomości e-mail** kliknij przycisk **Dalej**.
9. Na stronie **Definiowanie ustawień ochrony dla grup i witryn** wybierz pozycję **Ustawienia prywatności i dostępu użytkowników zewnętrznych** oraz **Ustawienia dostępu urządzeń i udostępniania zewnętrznego** , a następnie kliknij przycisk **Dalej**.
10. Na stronie **Definiowanie ustawień prywatności i dostępu użytkowników zewnętrznych** w obszarze **Prywatność** wybierz opcję **Prywatny** .
11. Jeśli chcesz zezwolić na dostęp gościa, w obszarze **Dostęp użytkowników zewnętrznych** wybierz pozycję **Zezwalaj właścicielom grupy Microsoft 365 dodawanie osób spoza organizacji do grupy jako gości**.
12. Kliknij **Dalej**.
13. Na **stronie Definiowanie ustawień udostępniania zewnętrznego i dostępu do urządzeń** wybierz pozycję **Kontroluj udostępnianie zewnętrzne z witryn z etykietą SharePoint**.
14. W obszarze **Zawartość można udostępniać**, wybierz pozycję **Nowi i istniejący goście** , jeśli zezwalasz na dostęp gościa lub **tylko osoby w organizacji,** jeśli nie.
15. W obszarze **Dostęp z urządzeń niezarządzanych** wybierz pozycję **Zezwalaj na ograniczony dostęp tylko do Internetu**.
16. Kliknij **Dalej**.
17. Na stronie **Automatyczne etykietowanie kolumn bazy danych** kliknij przycisk **Dalej**.
18. Kliknij **pozycję Utwórz etykietę**, a następnie kliknij pozycję **Gotowe**.

Po utworzeniu etykiety musisz opublikować ją dla użytkowników, którzy będą z niej korzystać. W celu ochrony poufnej udostępnimy etykietę wszystkim użytkownikom. Etykietę można opublikować w portalu zgodności usługi Microsoft Purview na karcie **Zasady etykiet** na stronie **Ochrona informacji** . Jeśli masz istniejące zasady, które mają zastosowanie do wszystkich użytkowników, dodaj tę etykietę do tych zasad. Jeśli musisz utworzyć nowe zasady, zobacz [Publikowanie etykiet poufności przez utworzenie zasad etykiet](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Tworzenie zespołu

Dalsza konfiguracja poufnego scenariusza jest wykonywana w SharePoint lokacji skojarzonej z zespołem, więc następnym krokiem jest utworzenie zespołu.

Aby utworzyć zespół na potrzeby informacji poufnych
1. W Teams kliknij **pozycję Teams** po lewej stronie aplikacji, a następnie kliknij **pozycję Dołącz lub utwórz zespół** w dolnej części listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Skompiluj zespół od podstaw**.
4. Na liście **Czułość** wybierz właśnie utworzoną etykietę **poufną** .
5. W obszarze **Prywatność** kliknij pozycję **Prywatny**.
6. Wpisz nazwę zespołu, a następnie kliknij przycisk **Utwórz**.
7. Dodaj użytkowników do zespołu, a następnie kliknij przycisk **Zamknij**.

## <a name="private-channel-settings"></a>Ustawienia kanału prywatnego

W tej warstwie ograniczamy tworzenie kanałów prywatnych do właścicieli zespołów.

Aby ograniczyć tworzenie kanału prywatnego
1. W zespole kliknij pozycję **Więcej opcji**, a następnie kliknij pozycję **Zarządzaj zespołem**.
2. Na karcie **Ustawienia** rozwiń pozycję **Uprawnienia członka**.
3. Wyczyść pole wyboru **Zezwalaj członkom na tworzenie kanałów prywatnych** .

Zasady [aplikacji Teams](/MicrosoftTeams/teams-policies) umożliwiają również kontrolowanie, kto może tworzyć kanały prywatne.

## <a name="shared-channel-settings"></a>Ustawienia kanału udostępnionego

[Kanały udostępnione](/MicrosoftTeams/shared-channels) nie mają ustawień na poziomie zespołu. Ustawienia kanału udostępnionego skonfigurowane w centrum administracyjnym Teams i usłudze Azure AD mają zastosowanie do wszystkich zespołów niezależnie od poufności.

## <a name="sharepoint-settings"></a>ustawienia SharePoint

Za każdym razem, gdy tworzysz nowy zespół z etykietą wrażliwą, istnieją dwa kroki do wykonania w SharePoint:

- Zaktualizuj ustawienia udostępniania gościa dla witryny w centrum administracyjnym SharePoint, aby zaktualizować domyślny link udostępniania do *określonych osób*.
- Zaktualizuj ustawienia udostępniania witryny w samej witrynie, aby uniemożliwić członkom udostępnianie witryny.

### <a name="site-default-sharing-link-settings"></a>Domyślne ustawienia linku udostępniania witryny

Aby zaktualizować domyślny typ linku udostępniania witryny

1. Otwórz centrum administracyjne SharePoint, a następnie w obszarze **Witryny** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
1. Wybierz witrynę skojarzoną z zespołem.
1. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** kliknij pozycję **Edytuj**.
1. W obszarze Domyślny typ łącza udostępniania wyczyść pole wyboru **To samo co ustawienie na poziomie organizacji** , a następnie wybierz pozycję **Określone osoby (tylko osoby określone przez użytkownika)**.
1. Wybierz **Zapisz**.

Jeśli chcesz wykonać skrypt w ramach procesu tworzenia zespołu, możesz użyć polecenia [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) z parametrem `-DefaultSharingLinkType Direct` , aby zmienić domyślny link udostępniania na *Określone osoby*.

Należy pamiętać, że w przypadku dodawania prywatnych lub udostępnionych kanałów do zespołu każda z nich tworzy nową witrynę SharePoint z domyślnymi ustawieniami udostępniania. Możesz je zaktualizować w centrum administracyjnym SharePoint, wybierając witryny skojarzone z zespołem.

### <a name="site-sharing-settings"></a>Ustawienia udostępniania witryny

Aby zapewnić, że witryna SharePoint nie zostanie udostępniona osobom, które nie są członkami zespołu, ograniczamy takie udostępnianie do właścicieli. Jest to konieczne tylko w przypadku witryny SharePoint utworzonej razem z zespołem. Nie można udostępniać dodatkowych witryn utworzonych w ramach kanałów prywatnych lub udostępnionych poza zespołem lub kanałem.

Aby skonfigurować udostępnianie witryn tylko dla właścicieli
1. W Teams przejdź do karty **Ogólne** zespołu, który chcesz zaktualizować.
2. Na pasku narzędzi dla zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij przycisk **Otwórz w SharePoint**.
4. Na pasku narzędzi bazowej witryny SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W okienku **Uprawnienia witryny** w obszarze **Udostępnianie witryny** kliknij pozycję **Zmień sposób udostępniania elementów członkowskich**.
6. W obszarze **Uprawnienia do udostępniania** wybierz pozycję **Właściciele i członkowie witryny, a osoby z uprawnieniami do edycji mogą udostępniać pliki i foldery, ale tylko właściciele witryn mogą udostępniać witrynę**, a następnie kliknij przycisk **Zapisz**.


## <a name="related-topics"></a>Tematy pokrewne

[Tworzenie i konfigurowanie etykiet poufności i ich zasad](../compliance/create-sensitivity-labels.md)
