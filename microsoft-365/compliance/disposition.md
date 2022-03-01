---
title: Disposition of content
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Monitoruj usuwanie zawartości i zarządzaj nimi podczas korzystania z recenzji usuwania lub elementów oznaczonych jako rekordy są automatycznie usuwane zgodnie z skonfigurowanymi ustawieniami.
ms.openlocfilehash: 5ee5af04b399d7f7d0ba94dc3b943d259d57ff34
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033748"
---
# <a name="disposition-of-content"></a>Disposition of content

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Za pomocą strony **Usuwaj** rekordy z zarządzania rekordami w Centrum zgodności platformy Microsoft 365 i wyświetlania metadanych rekordów, które zostały automatycznie [](records-management.md#records) usunięte po zakończeniu okresu przechowywania.

## <a name="prerequisites-for-viewing-content-dispositions"></a>Wymagania wstępne dotyczące wyświetlania zawartości rozsyłania

Aby zarządzać recenzjami usunięcia i potwierdzać, że rekordy zostały usunięte, musisz mieć wystarczające uprawnienia i włączyć inspekcję. Należy również pamiętać o wszelkich [ograniczeniach](retention-limits.md#maximum-number-of-items-for-disposition) dotyczących ich rozsyłania.

### <a name="permissions-for-disposition"></a>Uprawnienia dotyczące rozsyłania

Aby pomyślnie uzyskać dostęp do karty **Disposition** w Centrum zgodności platformy Microsoft 365, użytkownicy muszą mieć rolę **Zarządzanie nimi**. Od grudnia 2020 r. ta rola jest teraz uwzględniana w domyślnej **grupie ról Zarządzanie** rekordami.

> [!NOTE]
> Administrator globalny nie ma domyślnie roli **Zarządzanie rozsyłaniem** . 

Aby przyznać użytkownikom tylko te uprawnienia, których potrzebują do przeglądania rozsyłania, bez udzielania im uprawnień do wyświetlania i konfigurowania innych funkcji na potrzeby przechowywania i zarządzania rekordami, utwórz niestandardową grupę ról (na przykład  "Recenzenty rozsyłania") i nadaj tej grupie rolę Zarządzanie nimi.

Aby uzyskać instrukcje dotyczące dodawania użytkowników do ról domyślnych lub tworzenia własnych grup ról, zobacz Uprawnienia [w Centrum zgodności platformy Microsoft 365](microsoft-365-compliance-center-permissions.md).

Dodatkowo:

- Aby wyświetlić zawartość elementów podczas procesu ich rozsyłania, dodaj użytkowników do grupy ról Podgląd **zawartości Eksploratora** zawartości. Użytkownicy, którzy nie mają uprawnień z tej grupy ról, nadal mogą wybrać akcję recenzji rozsyłania, aby ukończyć recenzję rozsyłania, ale musi to robić bez możliwości wyświetlania zawartości elementu z poziomu mini-podglądu w centrum zgodności.

- Domyślnie każda osoba mająca dostęp **do strony Disposition** widzi tylko te elementy, do których została przypisana. Aby administrator zarządzania rekordami mógł wyświetlić wszystkie elementy przypisane do wszystkich użytkowników oraz wszystkie etykiety przechowywania skonfigurowane do przeglądania rozsyłania: Przejdź  >  do ustawień zarządzania rekordamiWyświetlanie w celu wybrania, a następnie włączenia grupy zabezpieczeń z obsługą poczty, która zawiera konta administratora.
    
    Microsoft 365 grupy i grupy zabezpieczeń, które nie mają włączonej obsługi poczty, nie obsługują tej funkcji i nie są wyświetlane na liście do wybrania. Jeśli chcesz utworzyć nową grupę zabezpieczeń z obsługą poczty, użyj linku do centrum administracyjne platformy Microsoft 365, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> aby utworzyć nową grupę. 
    
    > [!IMPORTANT]
    > Po włączeniu grupy nie można jej zmienić w centrum zgodności. W następnej sekcji opisano sposób włączania innej grupy przy użyciu programu PowerShell.

- Opcja **Ustawienia zarządzania rekordami** jest widoczna tylko dla administratorów zarządzania rekordami. 

#### <a name="enabling-another-security-group-for-disposition"></a>Włączanie innej grupy zabezpieczeń do ich rozsyłania

Po włączeniu grupy zabezpieczeń do obsługi rozsyłania  z ustawień zarządzania rekordami w centrum Centrum zgodności platformy Microsoft 365 nie można wyłączyć tego uprawnienia dla grupy ani zamienić wybranej grupy w Centrum zgodności. Jednak inną grupę zabezpieczeń z obsługą poczty można włączyć przy użyciu polecenia cmdlet [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) .

Przykład: 

```PowerShell
Enable-ComplianceTagStorage -RecordsManagementSecurityGroupEmail dispositionreviewers@contosoi.com
````

### <a name="enable-auditing"></a>Włączanie inspekcji

Upewnij się, że inspekcja jest włączona co najmniej dzień przed pierwszą akcją rozsyłania. Aby uzyskać więcej informacji, zobacz [Przeszukiwanie dziennika inspekcji w Centrum zgodności](search-the-audit-log-in-security-and-compliance.md). 

## <a name="disposition-reviews"></a>Recenzje rozsyłania

Gdy kończy się okres przechowywania zawartości, istnieje kilka powodów, dla których warto przejrzeć tę zawartość i potwierdzić, czy można ją trwale usunąć ("usunięto"). Na przykład zamiast usuwać zawartość, może być konieczne:
  
- Wstrzymanie usuwania odpowiedniej zawartości w przypadku sporu sądowego lub inspekcji.

- Przypisz do zawartości inny okres przechowywania, na przykład dlatego, że oryginalne ustawienia przechowywania były rozwiązaniem tymczasowym lub częściowym.

- Przenieś zawartość z istniejącej lokalizacji do lokalizacji archiwum, jeśli na przykład ta zawartość ma wartość badawczą lub historyczny.

Gdy na koniec okresu przechowywania zostanie wyzwolona recenzja rozsyłania, wybieranie recenzentów powoduje otrzymywanie wiadomości e-mail z powiadomieniem, że mają zawartość do przejrzenia. Tymi recenzentami mogą być poszczegłoni użytkownicy lub grupy zabezpieczeń z włączoną obsługą poczty.

Możesz dostosować wiadomość e-mail z powiadomieniem obierania przez recenzentów, łącznie z instrukcjami w różnych językach. Aby zapewnić obsługę wielu języków, musisz samodzielnie określić tłumaczenia, a ten niestandardowy tekst będzie wyświetlany wszystkim recenzentom niezależnie od ich ustawień regionalnych.

Na koniec okresu przechowywania elementu użytkownicy otrzymują początkowe powiadomienie e-mail z powiadomieniem na każdej etykiecie, z przypomnieniem na każdej etykiecie raz w tygodniu podczas wszystkich przypisanych przez nich recenzji dotyczących rozsyłania. Mogą kliknąć link  >  w wiadomościach e-mail z przypomnieniem i przejść bezpośrednio do strony Zarządzanie rekordami w Centrum zgodności platformy Microsoft 365, aby przejrzeć zawartość i podjąć działanie. Recenzentzy mogą również przejść do tej strony **Disposition** (Ustawienia) w Centrum zgodności. Następnie:

- Recenzentzy widzą tylko recenzje rozsyłania, które są do nich przypisane, natomiast administratorzy dodani do wybranej grupy zabezpieczeń dla menedżera rekordów widzą wszystkie recenzje rozsyłania.

- Recenzentzy mogą dodawać nowych użytkowników do tego samego recenzji rozsyłania. Ta akcja nie spowoduje automatycznego udzielenia tym dodanym użytkownikom [wymaganych uprawnień](#permissions-for-disposition).

- W przypadku procesu przeglądania zawartości dla każdego elementu w mini okienku przeglądu jest wyświetlony podgląd zawartości, o ile mają uprawnienia do jej wyświetlania. Jeśli użytkownik nie ma uprawnień, może wybrać link do zawartości i zażądać uprawnień. To mini-okienko recenzji zawiera również karty z dodatkowymi informacjami na temat zawartości:
   - **Szczegóły** dotyczące wyświetlania właściwości indeksowanych, miejsca i miejsca jego utworzenia, daty i czasie oraz osoby, która ostatnio ją zmodyfikowała i kiedy.
   - **Historia** , która zawiera historię wszystkich do tej pory akcji re przeglądu operacji ich operacji rozsyłania z komentarzami recenzentów, jeśli są dostępne.

Recenzja rozsyłania może obejmować zawartość Exchange skrzynek pocztowych, SharePoint witryn i OneDrive kontach. Zawartość oczekująca na sprawdzenie usuwania w tych lokalizacjach jest trwale usuwana dopiero po ostatecznym etapie usuwania recenzenta zdecyduje o trwałym usunięciu zawartości.

> [!NOTE]
> Skrzynka pocztowa musi mieć co najmniej 10 MB danych do obsługi recenzji rozsyłania.

Administratorzy mogą zobaczyć przegląd wszystkich oczekujących rozsyłań na **karcie** Omówienie. Recenzentzy widzą tylko elementy oczekujące na ich rozsyłanie. Przykład:

![Oczekujące zmiany rozsyłania w przeglądzie zarządzania rekordami.](../media/dispositions-overview.png)

Po wybraniu opcji **Wyświetl wszystkie oczekujące** rozsyłania jest przekierowywana strona **Disposition (Disposition).** Przykład:

![Strona Dispositions w Centrum zgodności platformy Microsoft 365.](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Przepływ pracy do przeglądania rozsyłania

Na poniższym diagramie przedstawiono podstawowy przepływ pracy do przeglądania rozsyłania (jednoetapowego) w przypadku opublikowania etykiety przechowywania, a następnie zastosowania jej ręcznie przez użytkownika. Ewentualnie etykieta przechowywania skonfigurowana do przeglądania zawartości może być automatycznie stosowana do zawartości.
  
![Wykres przedstawiający sposób działania ich rozsyłania.](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)

### <a name="how-to-configure-a-retention-label-for-disposition-review"></a>Jak skonfigurować etykietę przechowywania do przeglądania rozsyłania

Wyzwalanie recenzji rozsyłania na koniec okresu przechowywania jest opcją konfiguracji, która jest dostępna tylko z etykietą przechowywania. Recenzja rozsyłania nie jest dostępna w przypadku zasad przechowywania. Aby uzyskać więcej informacji na temat tych dwóch rozwiązań przechowywania, zobacz Informacje [o zasadach przechowywania i etykietach przechowywania](retention.md).

Na stronie **Definiowanie ustawień przechowywania** dla etykiety przechowywania:

![Ustawienia przechowywania dla etykiety.](../media/disposition-review-option.png)
 
Po wybraniu tej opcji  Wyzwolij recenzję rozsyłania na następnej stronie konfiguracji możesz określić liczbę kolejnych etapów procesu ich określania oraz recenzentów rozsyłania dla poszczególnych etapów:

![Określanie recenzentów rozsyłania.](../media/disposition-reviewers.png) 

Wybierz **pozycję Dodaj etap** i nadaj etapowi nazwę na potrzeby identyfikacji. Następnie określ recenzentów dla tego etapu.

Dla recenzentów określ użytkownika lub grupę zabezpieczeń z włączoną obsługą poczty. Microsoft 365 tej opcji nie [są obsługiwane Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601) (dawniej grupy grup grupowych).

Jeśli na koniec okresu przechowywania konieczne jest przejrzenie elementu przez więcej niż jedną osobę, wybierz ponownie pozycję Dodaj  etap i powtórz proces konfiguracji dla liczby potrzebnych etapów (maksymalnie pięć etapów). 

W ramach każdego etapu przechowywania każdy użytkownik określony dla tego etapu jest uprawniony do podjęcia następnej czynności dotyczącej danego elementu po zakończeniu okresu przechowywania. Ci użytkownicy mogą także dodawać innych użytkowników do etapu recenzji ich rozsyłania.

> [!NOTE]
> Jeśli etykiety przechowywania skonfigurowano przed dostępem do wieloetapowego przeglądu rozsyłania, możesz uaktualnić etykiety, aby obsługiły tę funkcję: W kreatorze etykiet wybierz pozycję Dodaj scenę **, edytuj** istniejących recenzentów lub dodaj nowych recenzentów.

W fazie konfiguracji, dla każdego etapu, który jest określony, możesz zmienić jego nazwę, zmienić jego kolejność lub usunąć go, wybierając opcję Akcje etapu (**...**): 

![Akcje etapowe do recenzy rozsyłania.](../media/stage-actions-disposition-review.png)

Po utworzeniu etykiety przechowywania nie można jednak zmienić kolejności ani usunąć etapu.

Po określonym recenzentach należy pamiętać o przyznaniu im uprawnień roli **Zarządzanie rozsyłaniem** . Aby uzyskać więcej informacji, zobacz [sekcję Uprawnienia](#permissions-for-disposition) do rozsyłania na tej stronie.

### <a name="how-to-customize-email-messages-for-disposition-review"></a>Jak dostosować wiadomości e-mail do przeglądania ich rozsyłania

Przykład domyślnego powiadomienia e-mail wysyłanego do recenzenta:

![Przykład powiadomienia e-mail z tekstem domyślnym, gdy element jest gotowy do recenzji rozsyłania.](../media/disposition-review-email.png)

Możesz dostosować wiadomości e-mail wysyłane do recenzentów rozsyłania początkowego powiadomienia, a następnie przypomnień.

Na dowolnej stronie Zarządzanie rekordami w Centrum zgodności wybierz pozycję **Ustawienia zarządzania rekordami**:  

![Ustawienia zarządzania rekordami.](../media/record-management-settings.png)

Na karcie **Rozsuń** w  sekcji Powiadomienia e-mail dotyczące recenzji dotyczących rozsyłania wybierz i określ, czy chcesz używać tylko domyślnej wiadomości e-mail, czy też chcesz dodać własny tekst do wiadomości domyślnej. Niestandardowy tekst zostanie dodany do wiadomości e-mail po informacjach dotyczących etykiety przechowywania i przed kolejnymi instrukcjami dotyczącymi tych kroków.

Można dodawać tekst dla wszystkich języków, ale formatowanie i obrazy są nieobsługiwane. Adresy URL i adresy e-mail mogą być wprowadzane jako tekst i, w zależności od klienta poczty e-mail, wyświetlane jako hiperlinki lub niesformatowany tekst w dostosowanej wiadomości e-mail.

Przykładowy tekst do dodania:

```console
If you need additional information, visit the helpdesk website (https://support.contoso.com) or send them an email (helpdesk@contoso.com).
```

Wybierz **pozycję Zapisz** , aby zapisać zmiany.

### <a name="viewing-and-disposing-of-content"></a>Wyświetlanie i rozsyłanie zawartości

Gdy recenzent zostanie powiadomiony pocztą e-mail, że zawartość jest gotowa do przejrzenia, może kliknąć w wiadomości e-mail link, który  przenosi go bezpośrednio  do strony Disposition (Zarządzanie rekordami) w Centrum zgodności platformy Microsoft 365. W tym miejscu recenzentzy mogą sprawdzić, ile elementów dla każdej etykiety przechowywania czeka na ich zasiecie, przy użyciu pozycji **Typ** z wyświetlonym **komunikatem Oczekiwanie na wysyłkę**. Następnie wybierzą etykietę przechowywania i pozycję **Otwórz w nowym** oknie, aby wyświetlić całą zawartość, która ma tę etykietę:

![Otwórz w nowym oknie do przejrzenia rozsyłania.](../media/open-in-new-window.png)

Na stronie **Oczekujące dispositions** widzą wszystkie oczekujące dispositions dla tej etykiety. Jeśli jest zaznaczony jeden lub więcej elementów, mogą oni sprawdzać zawartość przed podjęciem większej liczby działań w związku z tym, korzystając z mini okienka podglądu oraz karty **Źródło, Szczegóły** i Historia:

![Opcje ich rozsyłania.](../media/retention-disposition-options.png)

Jeśli używasz poziomego paska przewijania lub zamkniesz okienko przeglądu min, zobaczysz więcej kolumn z datą wygaśnięcia i nazwą etapu przeglądu rozsyłania.

Jak widać w przedstawionym przykładzie, obsługiwane akcje to: 
  
- **Zatwierdzanie usuwania**:
    - Jeśli ta akcja jest wybrana na pośredni etap przeglądu rozsyłania (skonfigurowano wiele etapów): Element przechodzi do następnego etapu procesu ich rozsyłania.
    - Jeśli ta akcja jest zaznaczona do końcowego etapu przeglądania usuwania lub istnieje tylko jeden etap usuwania: Element jest oznaczony jako kwalifikuje się do trwałego usunięcia. Dokładne chronometraż tego usunięcia zależy od obciążenia pracą. Aby uzyskać więcej informacji, zobacz [Jak działają ustawienia przechowywania z zawartością w miejscu](retention.md#how-retention-settings-work-with-content-in-place).
- **Etykieta ponownie**:
    - Jeśli ta akcja jest zaznaczona, element kończy proces przeglądania ich rozsyłania oryginalnej etykiety. Następnie element podlega ustawień przechowywania na nowo wybranej etykiecie przechowywania.
- **Rozszerz**:
    - Po wybraniu tej akcji przegląd rozsyłania jest w praktyce zawieszany do końca rozszerzonego okresu, a następnie przegląd rozsyłania jest wyzwalany ponownie od pierwszego etapu.
- **Dodaj recenzentów**:
    - Po wybraniu tej akcji użytkownik jest monitowany o określenie i dodanie innych użytkowników do recenzji.
    
    > [!NOTE]
    > Ta akcja nie spowoduje automatycznego udzielenia [wymaganych uprawnień](#permissions-for-disposition) dodanym użytkownikom. Osoby, które nie mają tych uprawnień, nie mogą uczestniczyć w recenzji rozsyłania.

Każde wykonane działanie ma odpowiednie zdarzenie inspekcji [w grupie Działania](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities) inspekcji działań inspekcji działań inspekcji dotyczących czynności dotyczących ich działania.

Podczas przeglądania usuwania zawartość nigdy nie jest przesuowana z pierwotnej lokalizacji i nie jest oznaczona do trwałego usunięcia, dopóki ta akcja nie zostanie wybrana przez recenzenta na ostatni lub tylko etap usuwania.

## <a name="disposition-of-records"></a>Disposition of records

Na stronie **głównej Zarządzanie rekordami** > **karcie Disposition** możesz znaleźć:

- Elementy usunięte w wyniku kontroli usunięcia.
- Elementy oznaczone jako rekord lub rekord przepisów prawa, które zostały automatycznie usunięte po zakończeniu okresu przechowywania.

W tych elementach **są wyświetlane rekordy usunięte** w **kolumnie** Typ. Przykład:

![Elementy, które zostały usunięte bez recenzji usuwania.](../media/records-disposed2.png)

> [!NOTE]
> Ta funkcja korzysta z informacji z [](search-the-audit-log-in-security-and-compliance.md) ujednoliconego dziennika inspekcji i dlatego wymaga włączenia inspekcji i [](turn-audit-log-search-on-or-off.md) możliwości wyszukiwania w celu przechwycenia odpowiednich zdarzeń.

W przypadku inspekcji usuniętych elementów oznaczonych jako rekordy lub rekordy prawne wyszukaj pozycję Usunięty plik  oznaczony jako rekord w kategorii Działania na pliku **i na stronie**. To zdarzenie inspekcji dotyczy dokumentów i wiadomości e-mail.

## <a name="filter-and-export-the-views"></a>Filtrowanie i eksportowanie widoków

Po wybraniu etykiety przechowywania na stronie Usuwania karty Oczekiwanie na  usuwania (jeśli dotyczy) i Usunięte elementy umożliwiają  filtrowanie widoków, aby ułatwić znajdowanie elementów.

W przypadku oczekujących dispositions przedział czasu jest oparty na dacie wygaśnięcia. W przypadku elementów usuniętych przedział czasu jest oparty na dacie usunięcia.
  
Informacje o elementach w obu widokach można wyeksportować jako plik .csv, który można następnie sortować i zarządzać przy użyciu programu Excel.
