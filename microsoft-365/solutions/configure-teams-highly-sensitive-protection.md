---
title: Konfigurowanie zespołów z ochroną danych wysoce poufnych
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
description: Dowiedz się, jak wdrażać zespoły z ochroną danych wysoce poufnych.
ms.openlocfilehash: b104828f5437b9389e83379984a40edf33340f33
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947566"
---
# <a name="configure-teams-with-protection-for-highly-sensitive-data"></a>Konfigurowanie zespołów z ochroną danych wysoce poufnych

W tym artykule przyjrzymy się konfigurowaniu zespołu pod kątem wysoce wrażliwego poziomu ochrony. Przed wykonaniem kroków opisanych w tym artykule upewnij się, że wykonano kroki opisane w [temacie Wdrażanie zespołów z ochroną punktu odniesienia](configure-teams-baseline-protection.md) .

W przypadku tej warstwy ochrony tworzymy etykietę poufności, która może być używana w całej organizacji dla wysoce poufnych zespołów i plików. Tylko członkowie określonej organizacji i goście będą mogli odszyfrować pliki korzystające z tej etykiety. Jeśli konieczne jest dalsze izolowanie uprawnień, aby tylko członkowie określonego zespołu mogli odszyfrowywać pliki, zobacz  [Wdrażanie zespołu z izolacją zabezpieczeń](secure-teams-security-isolation.md).

Warstwa wysoce wrażliwa oferuje następujące dodatkowe zabezpieczenia w warstwie odniesienia:

- Etykieta poufności dla zespołu, która umożliwia włączanie lub wyłączanie udostępniania gości i blokuje dostęp do zawartości SharePoint dla urządzeń niezarządzanych. Ta etykieta może być również używana do klasyfikowania i szyfrowania plików.
- Bardziej restrykcyjny domyślny typ linku udostępniania
- Tylko właściciele zespołów mogą tworzyć kanały prywatne.
- Żądania dostępu do skojarzonej witryny SharePoint są wyłączone.

## <a name="video-demonstration"></a>Pokaz wideo

Obejrzyj ten film wideo, aby zapoznać się z procedurami opisanymi w tym artykule.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzI7]

## <a name="guest-sharing"></a>Udostępnianie gościa

W zależności od charakteru firmy możesz lub nie chcesz włączać udostępniania gości dla zespołów, które zawierają wysoce poufne dane. Jeśli planujesz współpracę z osobami spoza organizacji w zespole, zalecamy włączenie udostępniania gości. Microsoft 365 obejmuje różne funkcje zabezpieczeń i zgodności, które ułatwiają bezpieczne udostępnianie poufnych zawartości. Jest to zazwyczaj bezpieczniejsza opcja niż wysyłanie zawartości pocztą e-mail bezpośrednio do osób spoza organizacji.

Aby uzyskać szczegółowe informacje na temat bezpiecznego udostępniania gościom, zobacz następujące zasoby:

- [Ograniczanie przypadkowego narażenia na pliki podczas udostępniania osobom spoza organizacji](./share-limit-accidental-exposure.md)
- [Tworzenie bezpiecznego środowiska udostępniania gościa](./create-secure-guest-sharing-environment.md)

Aby zezwolić na udostępnianie gościom lub zablokować go, używamy kombinacji etykiety poufności dla zespołu i kontrolek udostępniania na poziomie witryny dla skojarzonej witryny SharePoint, które zostały omówione później.

## <a name="sensitivity-labels"></a>Etykiety wrażliwości

W przypadku wysoce wrażliwego poziomu ochrony będziemy używać etykiety poufności do klasyfikowania zespołu. Ta etykieta może być również używana do klasyfikowania i szyfrowania pojedynczych plików w tym lub innych zespołach lub w innych lokalizacjach plików, takich jak SharePoint lub OneDrive. 

W pierwszym kroku należy włączyć etykiety poufności dla Teams. Aby uzyskać szczegółowe informacje[, zobacz Używanie etykiet poufności do ochrony zawartości w witrynach Microsoft Teams, grup Office 365 i SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

Jeśli masz już etykiety poufności wdrożone w organizacji, zastanów się, jak ta etykieta pasuje do ogólnej strategii etykiet. W razie potrzeby możesz zmienić nazwę lub ustawienia, aby spełnić potrzeby organizacji.

Po włączeniu etykiet poufności dla Teams następnym krokiem jest utworzenie etykiety.

Aby utworzyć etykietę poufności
1. Otwórz [portal zgodności usługi Microsoft Purview](https://compliance.microsoft.com).
2. W obszarze **Rozwiązania** kliknij pozycję **Ochrona informacji**.
3. Kliknij **pozycję Utwórz etykietę**.
4. Nadaj etykiecie nazwę. Sugerujemy **wysoce wrażliwe**, ale możesz wybrać inną nazwę, jeśli ta jest już używana.
5. Dodaj nazwę wyświetlaną i opis, a następnie kliknij przycisk **Dalej**.
6. Na **stronie Definiowanie zakresu dla tej etykiety** wybierz pozycję **Pliki & wiadomości e-mail** i **grupy & witrynach** , a następnie kliknij przycisk **Dalej**.
7. Na stronie **Wybieranie ustawień ochrony plików i wiadomości e-mail** wybierz pozycję **Szyfruj pliki i wiadomości e-mail**, a następnie kliknij przycisk **Dalej**.
8. Na stronie **Szyfrowanie** wybierz pozycję **Konfiguruj ustawienia szyfrowania**.
9. W obszarze **Przypisywanie uprawnień do określonych użytkowników i grup** kliknij pozycję **Przypisz uprawnienia**.
10. Kliknij **pozycję Dodaj wszystkich użytkowników i grupy w organizacji**.
11. Jeśli są goście, którzy powinni mieć uprawnienia do odszyfrowywania plików, kliknij pozycję **Dodaj użytkowników lub grupy** i dodaj je.
12.  Kliknij przycisk **Zapisz**, a następnie kliknij przycisk **Dalej**.
13. Na stronie *Automatyczne etykietowanie plików i wiadomości e-mail** kliknij przycisk **Dalej**.
14. Na stronie **Definiowanie ustawień ochrony dla grup i witryn** wybierz pozycję **Ustawienia prywatności i dostępu użytkowników zewnętrznych** oraz **Ustawienia dostępu urządzeń i udostępniania zewnętrznego** , a następnie kliknij przycisk **Dalej**.
15. Na stronie **Definiowanie ustawień prywatności i dostępu użytkowników zewnętrznych** w obszarze **Prywatność** wybierz opcję **Prywatny** .
16. Jeśli chcesz zezwolić na dostęp gościa, w obszarze **Dostęp użytkowników zewnętrznych** wybierz pozycję **Zezwalaj właścicielom grupy Microsoft 365 dodawanie osób spoza organizacji do grupy jako gości**.
17. Kliknij **Dalej**.
18. Na **stronie Definiowanie ustawień udostępniania zewnętrznego i dostępu do urządzeń** wybierz pozycję **Kontroluj udostępnianie zewnętrzne z witryn z etykietą SharePoint**.
19. W obszarze **Zawartość można udostępniać**, wybierz pozycję **Nowi i istniejący goście** , jeśli zezwalasz na dostęp gościa lub **tylko osoby w organizacji,** jeśli nie.
20. W obszarze **Dostęp z urządzeń niezarządzanych** wybierz pozycję **Blokuj dostęp**. (Jeśli zezwalasz gościom i nie mają oni zarządzanych urządzeń, możesz wybrać opcję **Zezwalaj na ograniczony dostęp tylko do Internetu**).
21. Kliknij **Dalej**.
22. Na stronie **Automatyczne etykietowanie kolumn bazy danych** kliknij przycisk **Dalej**.
23. Kliknij **pozycję Utwórz etykietę**, a następnie kliknij pozycję **Gotowe**.

Po utworzeniu etykiety musisz opublikować ją dla użytkowników, którzy będą z niej korzystać. W celu ochrony poufnej udostępnimy etykietę wszystkim użytkownikom. Etykietę można opublikować w portalu zgodności usługi Microsoft Purview na karcie **Zasady etykiet** na stronie **Ochrona informacji** . Jeśli masz istniejące zasady, które mają zastosowanie do wszystkich użytkowników, dodaj tę etykietę do tych zasad. Jeśli musisz utworzyć nowe zasady, zobacz [Publikowanie etykiet poufności przez utworzenie zasad etykiet](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Tworzenie zespołu

Dalsza konfiguracja wysoce wrażliwego scenariusza jest wykonywana w SharePoint lokacji skojarzonej z zespołem, więc następnym krokiem jest utworzenie zespołu.

Aby utworzyć zespół na potrzeby wysoce poufnych informacji
1. W Teams kliknij **pozycję Teams** po lewej stronie aplikacji, a następnie kliknij **pozycję Dołącz lub utwórz zespół** w dolnej części listy zespołów.
2. Kliknij **pozycję Utwórz zespół** (pierwsza karta, lewy górny róg).
3. Wybierz **pozycję Skompiluj zespół od podstaw**.
4. Na liście **Czułość** wybierz właśnie utworzoną etykietę **Wysoce wrażliwa** .
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

[Kanały udostępnione](/MicrosoftTeams/shared-channels) nie mają ustawień na poziomie zespołu. Ustawienia kanału udostępnionego skonfigurowane w centrum administracyjnym Teams i usłudze Azure AD będą dostępne dla wszystkich zespołów niezależnie od poufności.

## <a name="sharepoint-settings"></a>ustawienia SharePoint

Za każdym razem, gdy tworzysz nowy zespół z etykietą wysoce wrażliwą, w SharePoint należy wykonać dwa kroki:

- Zaktualizuj ustawienia udostępniania gościa dla witryny w centrum administracyjnym SharePoint, aby zaktualizować domyślny link udostępniania do *pozycji Osoby z istniejącym dostępem*.
- Zaktualizuj ustawienia udostępniania witryn w samej witrynie, aby uniemożliwić członkom udostępnianie plików, folderów lub witryny oraz wyłączanie żądań dostępu.

### <a name="site-default-sharing-link-settings"></a>Domyślne ustawienia linku udostępniania witryny

Aby zaktualizować domyślny typ linku udostępniania witryny

1. Otwórz centrum administracyjne SharePoint, a następnie w obszarze **Witryny** wybierz pozycję <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktywne witryny**</a>.
1. Wybierz witrynę skojarzoną z zespołem.
1. Na karcie **Zasady** w obszarze **Udostępnianie zewnętrzne** wybierz pozycję **Edytuj**.
1. W obszarze Domyślny typ łącza udostępniania wyczyść pole wyboru **To samo co ustawienie na poziomie organizacji** , a następnie wybierz pozycję **Osoby z istniejącym dostępem**.
1. Wybierz **Zapisz**.

Należy pamiętać, że w przypadku dodawania prywatnych lub udostępnionych kanałów do zespołu każda z nich tworzy nową witrynę SharePoint z domyślnymi ustawieniami udostępniania. Możesz je zaktualizować w centrum administracyjnym SharePoint, wybierając witryny skojarzone z zespołem.

### <a name="site-sharing-settings"></a>Ustawienia udostępniania witryny

Aby zapewnić, że witryna SharePoint nie zostanie udostępniona osobom, które nie są członkami zespołu, ograniczamy takie udostępnianie do właścicieli. Ograniczamy również udostępnianie plików i folderów właścicielom zespołów. Dzięki temu właściciele są świadomi, kiedy plik jest udostępniany osobie spoza zespołu.

Aby skonfigurować udostępnianie witryn tylko dla właścicieli
1. W Teams przejdź do karty **Ogólne** zespołu, który chcesz zaktualizować.
2. Na pasku narzędzi dla zespołu kliknij pozycję **Pliki**.
3. Kliknij wielokropek, a następnie kliknij przycisk **Otwórz w SharePoint**.
4. Na pasku narzędzi bazowej witryny SharePoint kliknij ikonę ustawień, a następnie kliknij pozycję **Uprawnienia witryny**.
5. W okienku **Uprawnienia witryny** w obszarze **Udostępnianie witryny** kliknij pozycję **Zmień sposób udostępniania elementów członkowskich**.
6. W obszarze **Uprawnienia do udostępniania** wybierz pozycję **Tylko właściciele witryn mogą udostępniać pliki, foldery i witrynę**.
7. Ustaw **opcję Zezwalaj na żądania dostępu** na **wartość Wyłączone**, a następnie kliknij pozycję **Zapisz**.

## <a name="see-also"></a>Zobacz też

[Tworzenie i konfigurowanie etykiet poufności i ich zasad](../compliance/create-sensitivity-labels.md)
