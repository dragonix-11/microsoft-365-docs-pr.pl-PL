---
title: Dowiedz się więcej na temat przechowywania w usłudze Teams
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Dowiedz się więcej o zasadach przechowywania, które mają zastosowanie do usługi Microsoft Teams.
ms.openlocfilehash: c7f60dbb29d2755ba41661ab3aea6b20b97cef06
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640527"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>Dowiedz się więcej o przechowywaniu w usłudze Microsoft Teams

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Jeśli w usłudze Teams jest wyświetlany komunikat informujący o tym, że twoje czaty lub wiadomości zostały usunięte przez zasady przechowywania, zobacz [Komunikaty usługi Teams dotyczące zasad przechowywania](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> Informacje na tej stronie dotyczą administratorów IT, którzy zarządzają tymi zasadami przechowywania.

Informacje zawarte w tym artykule uzupełniają informacje [na temat przechowywania](retention.md) , ponieważ zawierają informacje specyficzne dla komunikatów usługi Microsoft Teams.

W przypadku innych obciążeń zobacz:

- [Dowiedz się więcej o przechowywaniu dla programu SharePoint i usługi OneDrive](retention-policies-sharepoint.md)
- [Dowiedz się więcej na temat przechowywania usługi Yammer](retention-policies-yammer.md)
- [Dowiedz się więcej o przechowywaniu dla programu Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Co jest dołączone do przechowywania i usuwania

> [!NOTE]
> Zasady przechowywania obsługują teraz [kanały udostępnione](/MicrosoftTeams/shared-channels) w wersji zapoznawczej. Wszystkie kanały udostępnione dziedziczą ustawienia przechowywania z kanału nadrzędnego.

Komunikaty czatów, wiadomości kanałów i wiadomości kanału prywatnego można usunąć za pomocą zasad przechowywania aplikacji Teams, a oprócz tekstu w wiadomościach można przechowywać następujące elementy ze względów zgodności: obrazy osadzone, tabele, linki hipertekstowe, linki do innych wiadomości i plików usługi Teams oraz [zawartość karty](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Wiadomości czatu i wiadomości kanału prywatnego zawierają wszystkie nazwy osób w konwersacji, a komunikaty kanału obejmują nazwę zespołu i tytuł wiadomości (jeśli zostały podane). 

Fragmenty kodu, zarejestrowane notatki głosowe z klienta mobilnego usługi Teams, miniatury, obrazy anonsów i reakcje innych osób w postaci emotikonów nie są zachowywane podczas korzystania z zasad przechowywania w usłudze Teams.

Wiadomości e-mail i pliki używane w usłudze Teams nie są uwzględniane w zasadach przechowywania aplikacji Teams. Te elementy mają własne zasady przechowywania.

## <a name="how-retention-works-with-microsoft-teams"></a>Jak przechowywanie działa w usłudze Microsoft Teams

Ta sekcja służy do zrozumienia, w jaki sposób wymagania dotyczące zgodności są spełniane przez magazyn zaplecza i procesy, i powinny być weryfikowane przez narzędzia zbierania elektronicznych materiałów dowodowych, a nie przez komunikaty, które są obecnie widoczne w aplikacji Teams.

Zasady przechowywania umożliwiają przechowywanie danych z czatów i komunikatów kanałów w usłudze Teams oraz usuwanie tych czatów i wiadomości. W tle skrzynki pocztowe programu Exchange są używane do przechowywania danych skopiowanych z tych wiadomości. Dane z czatów w usłudze Teams są przechowywane w ukrytym folderze w skrzynce pocztowej każdego użytkownika uwzględnionego w czacie, a podobny ukryty folder w skrzynce pocztowej grupy jest używany dla wiadomości kanału usługi Teams. Te ukryte foldery nie są przeznaczone do bezpośredniego dostępu do użytkowników lub administratorów, ale zamiast tego przechowują dane, które administratorzy zgodności mogą wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

Te skrzynki pocztowe są wymienione według atrybutu RecipientTypeDetails:

- **UserMailbox**: te skrzynki pocztowe przechowują dane wiadomości dla użytkowników aplikacji Teams opartych na chmurze.
- **MailUser**: te skrzynki pocztowe przechowują dane wiadomości dla [użytkowników lokalnej usługi Teams](search-cloud-based-mailboxes-for-on-premises-users.md).
- **GroupMailbox**: te skrzynki pocztowe przechowują dane wiadomości dla standardowych kanałów usługi Teams.
- **SubstrateGroup**: te skrzynki pocztowe przechowują dane wiadomości dla udostępnionych kanałów usługi Teams.

Inne typy skrzynek pocztowych, takie jak RoomMailbox używane w salach konferencyjnych usługi Teams, nie są obsługiwane w przypadku zasad przechowywania usługi Teams.

Usługa Teams używa usługi czatu opartej na platformie Azure jako podstawowego magazynu dla wszystkich komunikatów (czatów i wiadomości kanału). Jeśli chcesz usunąć komunikaty usługi Teams ze względu na zgodność, zasady przechowywania dla usługi Teams mogą usuwać komunikaty po określonym okresie na podstawie czasu ich utworzenia. Wiadomości są następnie trwale usuwane zarówno ze skrzynek pocztowych programu Exchange, w których są przechowywane na potrzeby operacji zgodności, jak i z magazynu podstawowego używanego przez podstawową usługę czatu opartą na platformie Azure. Aby uzyskać więcej informacji na temat architektury bazowej, zobacz [Zabezpieczenia i zgodność w usłudze Microsoft Teams](/MicrosoftTeams/security-compliance-overview), a w szczególności sekcja [architektury Information Protection](/MicrosoftTeams/security-compliance-overview#information-protection-architecture).

Mimo że te dane z czatów i wiadomości kanałów usługi Teams są przechowywane w skrzynkach pocztowych, należy skonfigurować zasady przechowywania **dla wiadomości kanału usługi Teams** i lokalizacji **czatów usługi Teams** . Czaty i wiadomości kanałów w usłudze Teams nie są uwzględniane w zasadach przechowywania skonfigurowanych dla skrzynek pocztowych użytkowników lub grup programu Exchange. Podobnie zasady przechowywania aplikacji Teams nie mają wpływu na inne elementy poczty e-mail przechowywane w skrzynkach pocztowych.

Jeśli użytkownik zostanie dodany do czatu, kopia wszystkich udostępnionych mu wiadomości zostanie pozyskiwana do skrzynki pocztowej. Data utworzenia tych komunikatów nie zmienia się dla nowego użytkownika i pozostaje taka sama dla wszystkich użytkowników.

> [!NOTE]
> Jeśli użytkownik jest uwzględniony w aktywnych zasadach przechowywania, które przechowują komunikaty usługi Teams i usuwasz skrzynkę pocztową użytkownika uwzględnionego w tych zasadach, skrzynka pocztowa jest konwertowana na [nieaktywną skrzynkę pocztową w](inactive-mailboxes-in-office-365.md) celu zachowania danych usługi Teams. Jeśli nie musisz zachowywać tych danych usługi Teams dla użytkownika, wyklucz konto użytkownika z zasad przechowywania i [poczekaj, aż ta zmiana zacznie obowiązywać](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect) przed usunięciem jego skrzynki pocztowej.

Po skonfigurowaniu zasad przechowywania wiadomości czatu i kanału zadanie czasomierza z usługi Exchange okresowo ocenia elementy w ukrytym folderze skrzynki pocztowej, w którym są przechowywane te wiadomości usługi Teams. Uruchomienie zadania czasomierza zwykle trwa od 1 do 7 dni. Po wygaśnięciu okresu przechowywania tych elementów są one przenoszone do folderu SubstrateHolds — innego ukrytego folderu, który znajduje się w każdej skrzynce pocztowej każdego użytkownika lub grupy w celu przechowywania elementów "nietrwale usuniętych", zanim zostaną trwale usunięte. 

Komunikaty pozostają w folderze SubstrateHolds przez co najmniej 1 dzień, a następnie jeśli kwalifikują się do usunięcia, zadanie czasomierza trwale usuwa je przy następnym uruchomieniu.

> [!IMPORTANT]
> Ze względu na [pierwszą zasadę przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence) i ponieważ wiadomości czatu i kanału usługi Teams są przechowywane w Exchange Online skrzynkach pocztowych, trwałe usunięcie z folderu SubstrateHolds jest zawsze zawieszone, jeśli na skrzynkę pocztową mają wpływ inne zasady przechowywania usługi Teams dla tej samej lokalizacji, blokada postępowania sądowego, wstrzymanie opóźnień lub jeśli do skrzynki pocztowej zastosowano blokadę zbierania elektronicznych materiałów dowodowych ze względów prawnych lub śledczych.
>
> Chociaż skrzynka pocztowa znajduje się w odpowiedniej blokadzie, wiadomości czatu i kanału usługi Teams, które zostały usunięte, nie będą już widoczne w aplikacji Teams, ale będą nadal wykrywalne za pomocą zbierania elektronicznych materiałów dowodowych.

Po skonfigurowaniu zasad przechowywania dla komunikatów czatu i kanału ścieżki, które pobiera zawartość, zależą od tego, czy zasady przechowywania mają zostać zachowane, a następnie usunięte, tylko do zachowania lub usunięcia.

Gdy zasady przechowywania mają zostać zachowane, a następnie usunięte:

![Diagram przepływu przechowywania komunikatów czatu i kanału usługi Teams.](../media/teamsretentionlifecycle.png)

Dla dwóch ścieżek na diagramie:

1. **Jeśli wiadomość czatu lub kanału jest edytowana lub usuwana** przez użytkownika w okresie przechowywania, oryginalna wiadomość jest kopiowana (jeśli jest edytowana) lub przenoszona (jeśli została usunięta) do folderu SubstrateHolds. Wiadomość jest tam przechowywana przez co najmniej 1 dzień. Gdy okres przechowywania wygaśnie, komunikat zostanie trwale usunięty przy następnym uruchomieniu zadania czasomierza (zazwyczaj od 1 do 7 dni).

2. **Jeśli komunikat czatu lub kanału nie zostanie usunięty** przez użytkownika i dla bieżących komunikatów po edycji, wiadomość zostanie przeniesiona do folderu SubstrateHolds po upływie okresu przechowywania. Ta akcja zwykle trwa od 1 do 7 dni od daty wygaśnięcia. Gdy komunikat znajduje się w folderze SubstrateHolds, jest przechowywany przez co najmniej 1 dzień, a następnie komunikat zostanie trwale usunięty przy następnym uruchomieniu zadania czasomierza (zazwyczaj od 1 do 7 dni). 

> [!NOTE]
> Wiadomości przechowywane w skrzynkach pocztowych, w tym w ukrytych folderach, można wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych. Dopóki komunikaty nie zostaną trwale usunięte z folderu SubstrateHolds, nadal można je przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

Gdy okres przechowywania wygaśnie i przeniesie komunikat do folderu SubstrateHolds, operacja usuwania jest przekazywana do usługi czatu platformy Azure zaplecza, która następnie przekazuje tę samą operację do aplikacji klienckiej usługi Teams. Opóźnienia w tej komunikacji lub buforowaniu mogą wyjaśniać, dlaczego przez krótki czas użytkownicy nadal widzą te komunikaty w swojej aplikacji Teams.

W tym scenariuszu, w którym usługa czatu platformy Azure otrzymuje polecenie usuwania z powodu zasad przechowywania, odpowiedni komunikat w aplikacji klienckiej usługi Teams jest usuwany dla wszystkich użytkowników w konwersacji. Niektórzy z tych użytkowników mogą pochodzić z innej organizacji, mają zasady przechowywania z dłuższym okresem przechowywania lub nie są do nich przypisane żadne zasady przechowywania. W przypadku tych użytkowników kopie wiadomości są nadal przechowywane w ich skrzynkach pocztowych i pozostają możliwe do wyszukiwania pod kątem zbierania elektronicznych materiałów dowodowych, dopóki wiadomości nie zostaną trwale usunięte przez inne zasady przechowywania.

> [!IMPORTANT]
> Komunikaty widoczne w aplikacji Teams nie są dokładnym odzwierciedleniem tego, czy są zachowywane, czy trwale usuwane w celu spełnienia wymagań dotyczących zgodności.

Jeśli zasady przechowywania są tylko do zachowania lub tylko do usuwania, ścieżki zawartości są odmianami zachowywania i usuwania.

### <a name="content-paths-for-retain-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do zachowania

1. **Jeśli wiadomość czatu lub kanału jest edytowana lub usuwana** przez użytkownika w okresie przechowywania: oryginalna wiadomość jest kopiowana (jeśli jest edytowana) lub przenoszona (jeśli została usunięta) do folderu SubstrateHolds i przechowywana tam przez co najmniej 1 dzień. Jeśli zasady przechowywania są skonfigurowane tak, aby były zachowywane na zawsze, element pozostanie w tym miejscu. Jeśli zasady przechowywania mają datę zakończenia okresu przechowywania i wygasają, komunikat zostanie trwale usunięty przy następnym uruchomieniu zadania czasomierza (zazwyczaj od 1 do 7 dni).

2. **Jeśli komunikat czatu lub kanału nie został zmodyfikowany lub usunięty** przez użytkownika i dla bieżących wiadomości po edycji w okresie przechowywania: Nic się nie dzieje przed i po okresie przechowywania; komunikat pozostaje w oryginalnej lokalizacji.

### <a name="content-paths-for-delete-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do usuwania

1. **Jeśli wiadomość czatu lub kanału jest edytowana lub usuwana** przez użytkownika w okresie przechowywania: oryginalna wiadomość jest kopiowana (jeśli jest edytowana) lub przenoszona (jeśli została usunięta) do folderu SubstrateHolds. Komunikat jest tam przechowywany przez co najmniej 1 dzień i trwale usunięty przy następnym uruchomieniu zadania czasomierza (zazwyczaj od 1 do 7 dni).

2. **Jeśli komunikat czatu lub kanału nie zostanie usunięty** przez użytkownika w okresie przechowywania: po zakończeniu okresu przechowywania komunikat zostanie przeniesiony do folderu SubstrateHolds. Ta akcja zwykle trwa od 1 do 7 dni od daty wygaśnięcia. Komunikat jest tam przechowywany przez co najmniej 1 dzień, a następnie trwale usunięty przy następnym uruchomieniu zadania czasomierza (zazwyczaj od 1 do 7 dni).

#### <a name="example-flows-and-timings-for-retention-policies"></a>Przykładowe przepływy i chronometraż zasad przechowywania

Skorzystaj z poniższych przykładów, aby zobaczyć, jak procesy i chronometraż wyjaśnione w poprzednich sekcjach mają zastosowanie do zasad przechowywania, które mają następujące konfiguracje:

- [Przykład 1: Zachowaj tylko przez 7 lat](#example-1-retain-only-for-7-years)
- [Przykład 2: Zachowaj przez 30 dni, a następnie usuń](#example-2-retain-for-30-days-and-then-delete)
- [Przykład 3: Usuwanie tylko po 1 dniu](#example-3-delete-only-after-1-day)

Dla wszystkich przykładów, które odwołują się do trwałego usunięcia, ze względu na [zasady przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence), ta akcja jest zawieszona, jeśli komunikat podlega innym zasadom przechowywania w celu zachowania elementu lub podlega blokadzie zbierania elektronicznych materiałów dowodowych.

##### <a name="example-1-retain-only-for-7-years"></a>Przykład 1: Zachowaj tylko przez 7 lat

W dniu 1 użytkownik tworzy komunikat czatu lub kanału.

W dniu 5 użytkownik edytuje ten komunikat.

W dniu 30 użytkownik usuwa bieżący komunikat.

Wyniki przechowywania:

- W przypadku oryginalnej wiadomości:
    - W dniu 5 komunikat jest kopiowany do folderu SubstrateHolds, w którym nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez co najmniej 7 lat od dnia 1 (okres przechowywania).

- Dla bieżącego (edytowanego) komunikatu:
    - W dniu 30 komunikat przechodzi do folderu SubstrateHolds, w którym nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez co najmniej 7 lat od dnia 1 (okres przechowywania).

Jeśli użytkownik usunął bieżący komunikat po określonym okresie przechowywania, zamiast w okresie przechowywania, komunikat nadal będzie przenoszony do folderu SubstrateHolds. Jednak teraz okres przechowywania wygasł, komunikat zostanie trwale usunięty po upływie co najmniej 1 dnia, a następnie zazwyczaj w ciągu 1–7 dni.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Przykład 2: Zachowaj przez 30 dni, a następnie usuń

W dniu 1 użytkownik tworzy komunikat czatu lub kanału.

W dniu 10 użytkownik edytuje ten komunikat.

Użytkownik nie wprowadza dalszych zmian i nie usuwa komunikatu.

Wyniki przechowywania:

- W przypadku oryginalnej wiadomości:
    - W dniu 10 komunikat jest kopiowany do folderu SubstrateHolds, gdzie nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.
    - Po zakończeniu okresu przechowywania (30 dni od dnia 1) komunikat jest trwale usuwany zazwyczaj w ciągu 1–7 dni od co najmniej 1 dnia, a następnie nie zostanie zwrócony z wyszukiwaniem zbierania elektronicznych materiałów dowodowych.

- Dla bieżącego (edytowanego) komunikatu:
    - Po zakończeniu okresu przechowywania (30 dni od dnia 1) komunikat przechodzi do folderu SubstrateHolds zazwyczaj w ciągu 1–7 dni, gdzie nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.
    - Komunikat jest następnie trwale usuwany zwykle w ciągu 1–7 dni od co najmniej 1 dnia, a następnie nie będzie zwracany z wyszukiwaniem zbierania elektronicznych materiałów dowodowych.

##### <a name="example-3-delete-only-after-1-day"></a>Przykład 3: Usuwanie tylko po 1 dniu

> [!NOTE]
> Ze względu na krótki jednodniowy czas trwania tej konfiguracji i procesów przechowywania, które działają w okresie od 1 do 7 dni, w tej sekcji przedstawiono przykładowe chronometraży, które mieszczą się w typowych zakresach czasu.

W dniu 1 użytkownik tworzy komunikat czatu lub kanału.

Przykładowy wynik przechowywania, jeśli użytkownik nie edytuje ani nie usunie komunikatu:

- Dzień 5 (zazwyczaj 1–7 dni po rozpoczęciu okresu przechowywania w dniu 2):
    - Komunikat jest przenoszony do folderu SubstrateHolds i pozostaje tam przez co najmniej 1 dzień, w którym nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

- Dzień 9 (zazwyczaj 1–7 dni po co najmniej 1 dniu w folderze SubstrateHolds):
    - Wiadomość zostanie trwale usunięta, a następnie nie zostanie zwrócona z wyszukiwaniem zbierania elektronicznych materiałów dowodowych.

Jak pokazano w tym przykładzie, mimo że można skonfigurować zasady przechowywania w celu usuwania komunikatów po zaledwie jednym dniu, usługa przechodzi wiele procesów w celu zapewnienia zgodnego usunięcia. W związku z tym akcja usuwania po upływie 1 dnia może potrwać 16 dni, zanim wiadomość zostanie trwale usunięta, aby nie była już zwracana w wyszukiwaniach zbierania elektronicznych materiałów dowodowych.

## <a name="skype-for-business-and-teams-interop-chats"></a>czaty międzyoperacyjnymi Skype dla firm i Teams

Gdy czat Skype dla firm przychodzi do aplikacji Teams, staje się on komunikatem w wątku czatu usługi Teams i jest pozyskiwany do odpowiedniej skrzynki pocztowej. Zasady przechowywania aplikacji Teams będą stosowane do tych komunikatów z wątku usługi Teams. 

Jeśli jednak historia konwersacji jest włączona dla Skype dla firm i po stronie klienta Skype dla firm, że historia jest zapisywana w skrzynce pocztowej, te dane rozmów nie są obsługiwane przez zasady przechowywania usługi Teams. Dla tej zawartości użyj zasad przechowywania skonfigurowanych dla Skype dla firm.

## <a name="meetings-and-external-users"></a>Spotkania i użytkownicy zewnętrzni

Komunikaty ze spotkań kanału są przechowywane w taki sam sposób jak komunikaty kanału, dlatego w przypadku tych danych wybierz lokalizację **komunikatów kanału usługi Teams** podczas konfigurowania zasad przechowywania.

Komunikaty o zaimprowizowanych i zaplanowanych spotkaniach są przechowywane w taki sam sposób jak komunikaty rozmów grupowych, dlatego w przypadku tych danych wybierz lokalizację **czatów w** usłudze Teams podczas konfigurowania zasad przechowywania.

Gdy użytkownicy zewnętrzni zostaną uwzględnieni w spotkaniu hostującym organizację:

- Jeśli użytkownik zewnętrzny przyłącza się przy użyciu konta gościa w dzierżawie, wszystkie wiadomości ze spotkania są przechowywane zarówno w skrzynce pocztowej użytkowników, jak i w tle skrzynki pocztowej, która jest przyznawana kontu gościa. Zasady przechowywania nie są jednak obsługiwane w przypadku skrzynek pocztowych w tle, mimo że można je zgłaszać jako uwzględnione w zasadach przechowywania dla całej lokalizacji (czasami nazywanej "zasadami w całej organizacji").

- Jeśli użytkownik zewnętrzny dołączy przy użyciu konta z innej organizacji platformy Microsoft 365, zasady przechowywania nie mogą usuwać wiadomości dla tego użytkownika, ponieważ są one przechowywane w skrzynce pocztowej tego użytkownika w innej dzierżawie. Jednak w przypadku tego samego spotkania zasady przechowywania mogą usuwać komunikaty dla użytkowników.

## <a name="when-a-user-leaves-the-organization"></a>Gdy użytkownik opuszcza organizację 

Jeśli użytkownik, który ma skrzynkę pocztową w Exchange Online opuszcza organizację, a jego konto platformy Microsoft 365 zostanie usunięty, wiadomości czatu, które podlegają przechowywaniu, są przechowywane w nieaktywnej skrzynce pocztowej. Wiadomości czatu pozostają objęte wszelkimi zasadami przechowywania, które zostały umieszczone na użytkowniku, zanim jego skrzynka pocztowa została nieaktywna, a zawartość jest dostępna dla wyszukiwania zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md). 

Jeśli użytkownik przechowywał pliki w usłudze Teams, zobacz [równoważną sekcję](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) dotyczącą programu SharePoint i usługi OneDrive.

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Jeśli dopiero zaczynasz konfigurować przechowywanie w usłudze Microsoft 365, zobacz [Wprowadzenie do zarządzania cyklem życia danych](get-started-with-data-lifecycle-management.md).

Jeśli wszystko jest gotowe do skonfigurowania zasad przechowywania dla usługi Teams, zobacz [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md).
