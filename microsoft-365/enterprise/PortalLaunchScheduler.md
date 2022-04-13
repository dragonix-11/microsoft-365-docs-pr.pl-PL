---
title: Uruchamianie portalu przy użyciu harmonogramu uruchamiania portalu
ms.author: jhendr
author: jhendr
manager: pamgreen
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: W tym artykule opisano sposób uruchamiania portalu przy użyciu harmonogramu uruchamiania portalu
ms.openlocfilehash: 74de87a41f0b8b29dd901e757e410ff57f8f1d39
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824141"
---
# <a name="launch-your-portal-using-the-sharepoint-portal-launch-scheduler"></a>Uruchamianie portalu przy użyciu harmonogramu uruchamiania portalu SharePoint

Portal to witryna SharePoint komunikacji w intranecie o dużym natężeniu ruchu — witryna, która ma od 10 000 do ponad 100 000 widzów w ciągu kilku tygodni. Użyj harmonogramu uruchamiania portalu, aby uruchomić portal, aby zapewnić użytkownikom bezproblemowe środowisko wyświetlania podczas uzyskiwania dostępu do nowego portalu SharePoint.
<br>
<br>
Harmonogram uruchamiania portalu został zaprojektowany tak, aby ułatwić śledzenie stopniowego wdrażania przez grupowanie osób przeglądających falami i zarządzanie przekierowaniami adresów URL dla nowego portalu. Podczas uruchamiania każdej fali możesz zbierać opinie użytkowników, monitorować wydajność portalu i wstrzymywać uruchamianie, aby rozwiązać problemy przed kontynuowaniem następnej fali. Dowiedz się więcej na temat [planowania uruchamiania portalu w SharePoint](/microsoft-365/Enterprise/Planportallaunchroll-out).

**Istnieją dwa typy przekierowań:**

- **Dwukierunkowa**: uruchom nowy nowoczesny portal SharePoint, aby zastąpić istniejący SharePoint portal klasyczny lub nowoczesny
- **Przekierowanie do strony tymczasowej**: uruchom nowy nowoczesny portal SharePoint bez istniejącego portalu SharePoint

Uprawnienia witryny muszą być skonfigurowane oddzielnie od fal w ramach uruchamiania. Jeśli na przykład udostępniasz portal dla całej organizacji, możesz ustawić uprawnienia na "Wszyscy oprócz użytkowników zewnętrznych", a następnie podzielić użytkowników na fale przy użyciu grup zabezpieczeń. Dodanie grupy zabezpieczeń do fali nie daje tej grupie zabezpieczeń dostępu do lokacji.

> [!NOTE]
>
> - Ta funkcja będzie dostępna z panelu **Ustawienia** na stronie głównej witryn SharePoint komunikacji.
> - Tej funkcji można używać tylko w nowoczesnych witrynach komunikacji SharePoint przy użyciu stron witryny, ponieważ są one domyślnym i zalecanym typem używanym w portalach.
> - Musisz mieć uprawnienia właściciela witryny do dostosowywania i planowania uruchamiania portalu.
> - Starty muszą być zaplanowane z co najmniej siedmiodniowym wyprzedzeniem, a każda fala może trwać od jednego do siedmiu dni.
> - Liczba wymaganych fal jest automatycznie określana przez oczekiwaną liczbę użytkowników.
> - Przed zaplanowaniem uruchomienia portalu należy uruchomić [narzędzie Diagnostyka strony dla SharePoint](https://aka.ms/perftool), aby sprawdzić, czy strona główna witryny jest w dobrej kondycji.
> - Po zakończeniu uruchamiania wszyscy użytkownicy z uprawnieniami do witryny będą mogli uzyskać dostęp do nowej witryny.
> - Jeśli Twoja organizacja korzysta z [Zasoby Viva](/SharePoint/viva-connections), użytkownicy mogą zobaczyć ikonę organizacji na pasku aplikacji Microsoft Teams, jednak po wybraniu ikony użytkownicy nie będą mogli uzyskać dostępu do portalu, dopóki ich fala nie zostanie uruchomiona.
> - Ta funkcja nie jest dostępna dla Office 365 Niemczech, Office 365 obsługiwanych przez 21Vianet (Chiny) lub Microsoft 365 planów rządu USA.

## <a name="understand-the-differences-between-portal-launch-scheduler-options"></a>Omówienie różnic między opcjami harmonogramu uruchamiania portalu:

Wcześniej uruchamianie portalu można było zaplanować tylko za pośrednictwem SharePoint programu PowerShell. Teraz masz dwie opcje ułatwiające zaplanowanie uruchamiania portalu i zarządzanie nimi. Dowiedz się więcej o kluczowych różnicach między obydwoma narzędziami:

**SharePoint wersji programu PowerShell:**

- Poświadczenia administratora są wymagane do używania [SharePoint programu PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell)
- Minimalne wymaganie jednej fali
- Planowanie uruchamiania na podstawie strefy czasowej uniwersalnego czasu koordynowanego (UTC)

**Wersja w produkcie:**

- Wymagane są poświadczenia właściciela witryny
- Minimalne wymaganie dwóch fal
- Planowanie uruchamiania na podstawie lokalnej strefy czasowej portalu zgodnie z ustawieniami regionalnymi

## <a name="get-started-using-the-portal-launch-scheduler"></a>Wprowadzenie przy użyciu harmonogramu uruchamiania portalu

1. Przed użyciem narzędzia harmonogramu uruchamiania portalu [dodaj wszystkich użytkowników, którzy będą potrzebować dostępu do tej witryny](https://support.microsoft.com/office/share-a-site-958771a8-d041-4eb8-b51c-afea2eae3658) za pośrednictwem **uprawnień witryny** jako właściciel witryny, członek witryny lub gość.

2. Następnie rozpocznij planowanie uruchamiania portalu, uzyskując dostęp do harmonogramu uruchamiania portalu na jeden z dwóch sposobów:

   **Opcja 1**. Kilka pierwszych edycji i ponownego publikowania zmian na stronie głównej — lub do wersji 3.0 strony głównej — zostanie wyświetlony monit o użycie narzędzia harmonogramu uruchamiania portalu. Wybierz pozycję **Zaplanuj uruchamianie** , aby przejść do przodu z harmonogramem. Możesz też wybrać pozycję **Publikuj** ponownie, aby ponownie opublikować zmiany strony bez planowania uruchomienia.

   ![Obraz przedstawiający monit o użycie harmonogramu uruchamiania portalu podczas ponownego publikowania strony głównej.](../media/portal-launch-republish-2.png)

   **Opcja 2**: W dowolnym momencie możesz przejść do strony głównej witryny SharePoint komunikacji, wybrać **pozycję Ustawienia**, a następnie **zaplanować uruchomienie witryny**, aby zaplanować uruchomienie portalu.

   ![Obraz przedstawiający okienko Ustawienia z wyróżnionym harmonogramem uruchamiania witryny.](../media/portal-launch-settings-2.png)

3. Następnie potwierdź wynik kondycji portalu i w razie potrzeby wprowadź ulepszenia portalu przy użyciu narzędzia [Diagnostyka strony dla SharePoint](https://aka.ms/perftool), dopóki portal nie otrzyma wyniku **w dobrej kondycji**. Następnie wybierz pozycję **Dalej**.

   ![Obraz przedstawiający narzędzie harmonogramu uruchamiania portalu.](../media/portal-launch-panel-2.png)

   > [!NOTE]
   > Nie można edytować nazwy i opisu witryny z harmonogramu uruchamiania portalu i zamiast tego można go zmienić, wybierając **pozycję Ustawienia**, a następnie **informacje o witrynie** na stronie głównej.

4. Wybierz z listy rozwijanej **pozycję Liczba oczekiwanych użytkowników** . Na tej ilustracji przedstawiono liczbę użytkowników, którzy najprawdopodobniej będą potrzebować dostępu do witryny. Harmonogram uruchamiania portalu automatycznie określi idealną liczbę fal w zależności od oczekiwanych użytkowników w następujący sposób:

   - Mniej niż 10 tys. użytkowników: dwie fale
   - Od 10 tys. do 30 tys. użytkowników: trzy fale
   - Od 30 tys. do 100 tys. użytkowników: pięć fal
   - Ponad 100 tys. użytkowników: Pięć fal i skontaktuj się z pomocą techniczną firmy Microsoft, wykonując kroki wymienione w sekcji Uruchamianie portalu z ponad 100 tys. użytkowników.

5. Następnie określ **typ potrzebnego przekierowania** :

   **Opcja 1. Wysyłanie użytkowników do istniejącej strony SharePoint (dwukierunkowej)** — użyj tej opcji podczas uruchamiania nowego nowoczesnego portalu SharePoint, aby zastąpić istniejący portal SharePoint. Użytkownicy w aktywnych falach będą przekierowywani do nowej witryny niezależnie od tego, czy nawigują do starej, czy nowej witryny. Użytkownicy na fali, która nie została uruchomiona, którzy próbują uzyskać dostęp do nowej witryny, zostaną przekierowani z powrotem do starej witryny, dopóki nie zostanie uruchomiona ich fala.

   > [!NOTE]
   > W przypadku korzystania z opcji dwukierunkowej osoba planująca uruchomienie musi mieć również uprawnienia właściciela witryny do innego portalu SharePoint.

   **Opcja 2. Wysyłanie użytkowników do automatycznie wygenerowanej strony tymczasowej (tymczasowe przekierowanie strony)** — użyj tymczasowego przekierowania strony, jeśli nie istnieje żaden istniejący portal SharePoint. Użytkownicy są kierowani do nowego nowoczesnego portalu SharePoint, a jeśli użytkownik znajduje się w fali, która nie została uruchomiona, zostanie przekierowany do strony tymczasowej.

   **Opcja 3. Wysyłanie użytkowników na stronę zewnętrzną** — podaj zewnętrzny adres URL do tymczasowego środowiska strony docelowej do momentu uruchomienia fali użytkownika.

6. Podziel odbiorców na fale. Dodaj maksymalnie 20 grup zabezpieczeń na falę. Szczegóły fal można edytować aż do uruchomienia każdej fali. Każda fala może trwać co najmniej jeden dzień (24 godziny) i co najwyżej siedem dni. Umożliwia to SharePoint i środowisku technicznym aklimatyzowanie i skalowanie do dużej liczby użytkowników witryny. Podczas planowania uruchamiania za pośrednictwem interfejsu użytkownika strefa czasowa jest oparta na ustawieniach regionalnych witryny.

   > [!NOTE]
   >
   > - Harmonogram uruchamiania portalu automatycznie domyślnie będzie miał co najmniej 2 fale. Jednak wersja programu PowerShell tego narzędzia będzie zezwalać na 1 falę.
   > - Microsoft 365 grupy nie są obsługiwane przez tę wersję harmonogramu uruchamiania portalu.

7. Określ, kto musi od razu wyświetlić witrynę, i wprowadź swoje informacje w polu **Użytkownicy wykluczeni z fal** . Ci użytkownicy są wykluczeni z fal i nie będą przekierowywani przed, w trakcie lub po uruchomieniu.

    >[!NOTE]
    > Można dodać maksymalnie 50 unikatowych użytkowników lub grup zabezpieczeń. Użyj grup zabezpieczeń, gdy potrzebujesz więcej niż 50 osób, aby uzyskać dostęp do portalu przed rozpoczęciem uruchamiania fal.

8. Potwierdź szczegóły uruchomienia portalu i wybierz pozycję **Harmonogram**. Po zaplanowaniu uruchomienia wszelkie zmiany na stronie głównej portalu SharePoint muszą otrzymać wynik diagnostyki w dobrej kondycji, zanim uruchomienie portalu zostanie wznowione.

### <a name="launch-a-portal-with-over-100k-users"></a>Uruchamianie portalu z ponad 100 tys. użytkowników

Jeśli planujesz uruchomić portal z ponad 100 000 użytkowników, prześlij wniosek o pomoc techniczną, wykonując kroki wymienione poniżej. Pamiętaj, aby uwzględnić wszystkie żądane informacje.

> [!NOTE]
>
> - Ten proces powinien być przestrzegany tylko wtedy, gdy spełniasz następujące wymagania:
> - Strona uruchamiania została ukończona.
> - [Zostały wykonane wskazówki dotyczące kondycji portalu](https://aka.ms/portalhealth) .
> - Data uruchomienia jest w ciągu 14 dni.

**Wykonaj następujące czynności:**

1. Jako administrator kliknij następujący link, który wypełni zapytanie pomocy w centrum administracyjnym.

[Uruchamianie portalu SharePoint z 100 tys. użytkowników](https://admin.microsoft.com/AdminPortal/?searchSolutions=Launch%20SharePoint%20Portal%20with%20100k%20users)

2. W dolnej części okienka wybierz pozycję **Skontaktuj się z pomocą techniczną**, a następnie wybierz pozycję **Nowe żądanie obsługi**.

3. W obszarze **Opis** wprowadź ciąg "Uruchom portal SharePoint z 100 000 użytkowników".

4. Wypełnij pozostałe informacje i wybierz pozycję **Skontaktuj się ze mną**.

5. Po utworzeniu biletu upewnij się, że podasz agentowi pomocy technicznej następujące informacje:
   - Adres URL portalu
   - Oczekiwana liczba użytkowników
   - Szacowany harmonogram uruchamiania (z wyszczególnionymi rozmiarami fal)
   - Użyj narzędzia diagnostyki strony, aby "wyeksportować plik HAR" strony uruchamiania i udostępnić plik z obsługą

## <a name="make-changes-to-a-scheduled-portal-launch"></a>Wprowadzanie zmian w zaplanowanym uruchomieniu portalu

Szczegóły uruchamiania można edytować dla każdej fali aż do daty premiery fali.

1. Aby edytować szczegóły uruchamiania portalu, przejdź do **Ustawienia** i wybierz pozycję **Zaplanuj uruchamianie witryny**.
2. Następnie wybierz pozycję **Edytuj**.
3. Po zakończeniu wprowadzania zmian wybierz pozycję **Aktualizuj**.

## <a name="delete-a-scheduled-portal-launch"></a>Usuwanie zaplanowanego uruchomienia portalu

Uruchomienia zaplanowane przy użyciu narzędzia harmonogramu uruchamiania portalu można anulować lub usunąć w dowolnym momencie, nawet jeśli niektóre fale zostały już uruchomione.

1. Aby anulować uruchamianie portalu, przejdź do **obszaru Ustawienia** i **Zaplanuj uruchamianie witryny**.

2. Następnie wybierz pozycję **Usuń** , a następnie po wyświetleniu poniższego komunikatu wybierz ponownie pozycję **Usuń** .

   ![Obraz przedstawiający monit z pytaniem, czy chcesz usunąć lub zachować zaplanowane uruchomienie.](../media/portal-launch-delete-2.png)

## <a name="use-the-powershell-portal-launch-scheduler"></a>Używanie harmonogramu uruchamiania portalu programu PowerShell

Narzędzie harmonogramu uruchamiania portalu SharePoint było pierwotnie dostępne tylko za pośrednictwem [SharePoint programu PowerShell](/powershell/sharepoint/sharepoint-online/introduction-sharepoint-online-management-shell) i będzie nadal obsługiwane za pośrednictwem programu PowerShell dla klientów, którzy preferują tę metodę. Te same uwagi na początku tego artykułu dotyczą obu wersji harmonogramu uruchamiania portalu.

> [!NOTE]
> Do korzystania z programu SharePoint programu PowerShell potrzebne są uprawnienia administratora.
> Zostaną wyświetlone szczegóły uruchamiania portalu dla uruchomień utworzonych w programie PowerShell i można nimi zarządzać w nowym narzędziu harmonogramu uruchamiania portalu w SharePoint.

### <a name="app-setup-and-connecting-to-sharepoint-online"></a>Konfigurowanie aplikacji i nawiązywanie połączenia z usługą SharePoint Online

1. [Pobierz najnowszą powłokę zarządzania SharePoint Online](https://go.microsoft.com/fwlink/p/?LinkId=255251).

    > [!NOTE]
    > Jeśli zainstalowano poprzednią wersję powłoki zarządzania SharePoint Online, przejdź do pozycji Dodaj lub usuń programy i odinstaluj polecenie "SharePoint Powłoka zarządzania online".
    >
    > Na stronie Centrum pobierania wybierz swój język, a następnie kliknij przycisk Pobierz. Zostanie wyświetlony monit o wybranie między pobraniem pliku .msi x64 i x86. Pobierz plik x64, jeśli używasz 64-bitowej wersji Windows lub pliku x86, jeśli używasz wersji 32-bitowej. Jeśli nie wiesz, zobacz[, która wersja systemu operacyjnego Windows jest uruchomiona?](https://support.microsoft.com/help/13443/windows-which-operating-system). Po pobraniu pliku uruchom go i wykonaj kroki opisane w Kreatorze instalacji.

2. Połączenie SharePoint jako [administrator globalny lub administrator SharePoint](/sharepoint/sharepoint-admin-role) w Microsoft 365. Aby dowiedzieć się, jak to zrobić, zobacz [Wprowadzenie do usługi SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

### <a name="view-any-existing-portal-launch-setups"></a>Wyświetlanie wszelkich istniejących ustawień uruchamiania portalu

Aby sprawdzić, czy istnieją konfiguracje uruchamiania portalu:

   ```PowerShell
   Get-SPOPortalLaunchWaves -LaunchSiteUrl <object> -DisplayFormat <object>
   ```

### <a name="schedule-a-portal-launch-on-the-site"></a>Planowanie uruchamiania portalu w witrynie

Liczba wymaganych fal zależy od oczekiwanego rozmiaru startu.

- Mniej niż 10 tys. użytkowników: jedna fala
- Od 10 tys. do 30 tys. użytkowników: trzy fale
- Od 30 tys. do 100 tys. użytkowników: pięć fal
- Ponad 100 tys. użytkowników: pięć fal i skontaktuj się z zespołem ds. konta Microsoft

#### <a name="steps-for-bidirectional-redirection"></a>Kroki przekierowania dwukierunkowego

Przekierowanie dwukierunkowe obejmuje uruchomienie nowego nowoczesnego portalu SharePoint Online w celu zastąpienia istniejącego SharePoint portalu klasycznego lub nowoczesnego. Użytkownicy w aktywnych falach będą przekierowywani do nowej witryny niezależnie od tego, czy nawigują do starej, czy nowej witryny. Użytkownicy na fali, która nie została uruchomiona, którzy próbują uzyskać dostęp do nowej witryny, zostaną przekierowani z powrotem do starej witryny, dopóki nie zostanie uruchomiona ich fala.

Obsługujemy tylko przekierowanie między domyślną stroną główną w starej witrynie a domyślną stroną główną w nowej witrynie. Jeśli masz administratorów lub właścicieli, którzy potrzebują dostępu do starych i nowych witryn bez przekierowywania, upewnij się, że są one wymienione przy użyciu parametru `WaveOverrideUsers` .

Aby przeprowadzić migrację użytkowników z istniejącej witryny SharePoint do nowej witryny SharePoint w sposób etapowy:

1. Uruchom następujące polecenie, aby wyznaczyć fale uruchamiania portalu.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType Bidirectional -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Przykład:

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType Bidirectional -RedirectUrl "https://contoso.sharepoint.com/teams/oldsite" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves '
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"},
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Zakończ walidację. Ukończenie konfiguracji w usłudze może potrwać od 5 do 10 minut.

#### <a name="steps-for-redirection-to-temporary-page"></a>Kroki przekierowania do strony tymczasowej

Tymczasowe przekierowanie stron powinno być używane, gdy nie istnieje żaden istniejący portal SharePoint. Użytkownicy są kierowani do nowego nowoczesnego portalu SharePoint Online w sposób etapowy. Jeśli użytkownik znajduje się w fali, która nie została uruchomiona, zostanie przekierowany do strony tymczasowej (dowolny adres URL).

1. Uruchom następujące polecenie, aby wyznaczyć fale uruchamiania portalu.

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl <object> -RedirectionType ToTemporaryPage -RedirectUrl <string> -ExpectedNumberOfUsers <object> -WaveOverrideUsers <object> -Waves <object>
   ```

   Przykład:

   ```PowerShell
   New-SPOPortalLaunchWaves -LaunchSiteUrl "https://contoso.sharepoint.com/teams/newsite" -RedirectionType ToTemporaryPage -RedirectUrl "https://portal.contoso.com/UnderConstruction.aspx" -ExpectedNumberOfUsers 10kTo30kUsers -WaveOverrideUsers "admin@contoso.com" -Waves '
   [{Name:"Wave 1", Groups:["Viewers 1"], LaunchDateUtc:"2020/10/14"},
   {Name:"Wave 2", Groups:["Viewers 2"], LaunchDateUtc:"2020/10/15"},
   {Name:"Wave 3", Groups:["Viewers 3"], LaunchDateUtc:"2020/10/16"}]'
   ```

2. Zakończ walidację. Ukończenie konfiguracji w usłudze może potrwać od 5 do 10 minut.

### <a name="pause-or-restart-a-portal-launch-on-the-site"></a>Wstrzymywanie lub ponowne uruchamianie portalu w witrynie

1. Aby wstrzymać uruchamianie portalu w toku i tymczasowo zapobiec wystąpieniu nadchodzących postępów fal, uruchom następujące polecenie:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Pause - LaunchSiteUrl <object>
   ```

2. Sprawdź, czy wszyscy użytkownicy są przekierowywani do starej witryny.

3. Aby ponownie uruchomić portal, który został wstrzymany, uruchom następujące polecenie:

   ```PowerShell
   Set-SPOPortalLaunchWaves -Status Restart - LaunchSiteUrl <object>
   ```

4. Sprawdź, czy przekierowanie zostało przywrócone.

### <a name="delete-a-portal-launch-on-the-site"></a>Usuwanie uruchamiania portalu w witrynie

1. Uruchom następujące polecenie, aby usunąć uruchomienie portalu zaplanowane lub w toku dla witryny.

   ```PowerShell
   Remove-SPOPortalLaunchWaves -LaunchSiteUrl <object>
   ```

2. Sprawdź, czy nie nastąpi przekierowanie dla wszystkich użytkowników.

## <a name="learn-more"></a>Dowiedz się więcej

[Planowanie planu wdrożenia uruchamiania portalu w usłudze SharePoint Online](./planportallaunchroll-out.md)

[Planowanie witryny komunikacji](https://support.microsoft.com/office/plan-your-sharepoint-communication-site-35d9adfe-d5cc-462f-a63a-bae7f2529182)
