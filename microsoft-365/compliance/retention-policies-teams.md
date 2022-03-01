---
title: Dowiedz się więcej na temat przechowywania Teams
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
description: Dowiedz się więcej o zasadach przechowywania, które dotyczą Microsoft Teams.
ms.openlocfilehash: d3562126a678e486fd97f3c760841f9ba4de7193
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2022
ms.locfileid: "63014808"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>Dowiedz się więcej na temat przechowywania Microsoft Teams

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Jeśli w twoim oknie Teams zostanie wyświetlony komunikat informujący o tym, że Twoje czaty lub wiadomości zostały usunięte przez zasady przechowywania, zobacz wiadomości dotyczące zasad przechowywania Teams [wiadomości](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> Informacje na tej stronie są dla administratorów informatycznych, którzy zarządzają tymi zasadami przechowywania.

Informacje zawarte w tym artykule uzupełnia informacje [dotyczące przechowywania,](retention.md) ponieważ zawierają informacje specyficzne dla poszczególnych wiadomości Microsoft Teams wiadomości.

W przypadku innych obciążeń, zobacz:

- [Dowiedz się więcej na temat przechowywania SharePoint i OneDrive](retention-policies-sharepoint.md)
- [Informacje na temat przechowywania danych dla Yammer](retention-policies-yammer.md)
- [Dowiedz się więcej na temat przechowywania Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Co obejmuje przechowywanie i usuwanie

Teams czatów, wiadomości kanałów i wiadomości w kanałach prywatnych można usuwać przy użyciu zasad przechowywania dla programu Teams, a oprócz tekstu w wiadomościach, ze względu na zgodność z przepisami, mogą być zachowywane następujące elementy: Osadzone obrazy, tabele, linki hipertekstowe, linki do innych wiadomości i plików programu Teams oraz [zawartość](/microsoftteams/platform/task-modules-and-cards/what-are-cards) kart. Wiadomości na czacie i wiadomości w kanale prywatnym obejmują wszystkie nazwiska osób w konwersacji, a wiadomości kanału zawierają nazwę zespołu i tytuł wiadomości (jeśli zostały podane). 

Fragmenty kodu, zarejestrowane notatki głosowe z klienta mobilnego usługi Teams, miniatury, obrazy ogłoszeń i reakcje od innych osób w formie emotikonów nie są zachowywane, gdy korzystasz z zasad przechowywania na Teams.

Wiadomości e-mail i pliki, z Teams są uwzględniane w zasadach przechowywania dla Teams. Te elementy mają własne zasady przechowywania.

## <a name="how-retention-works-with-microsoft-teams"></a>Jak działa przechowywanie na Microsoft Teams

Skorzystaj z tej sekcji, aby zrozumieć, jak są spełnione Wymagania dotyczące zgodności przez wewnętrzne magazyn i procesy oraz powinny być weryfikowane przez narzędzia zbierania elektronicznych materiałów dowodowych, a nie przez wiadomości obecnie widoczne w aplikacji Teams aplikacji.

Przy użyciu zasad przechowywania możesz zachować dane z czatów i wiadomości kanałów w Teams oraz usunąć te czaty i wiadomości. W tle dane Exchange są używane do przechowywania danych skopiowanych z tych wiadomości. Dane z Teams są przechowywane w ukrytym folderze w skrzynce pocztowej każdego użytkownika uwzględnionego w czacie, a podobny ukryty folder w skrzynce pocztowej grupy jest używany do Teams wiadomości na kanale. Te ukryte foldery nie są przeznaczone do bezpośredniego dostępu dla użytkowników lub administratorów, ale zamiast tego przechowuj dane, które administratorzy zgodności mogą wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

Te skrzynki pocztowe są wymienione według ich atrybutu RecipientTypeDetails:

- **UserMailbox**: Te skrzynki pocztowe przechowują dane wiadomości dla użytkowników usługi Teams w chmurze.
- **MailUser**: Te skrzynki pocztowe przechowują dane wiadomości dla [użytkowników Teams lokalnych](search-cloud-based-mailboxes-for-on-premises-users.md).
- **GroupMailbox**: Te skrzynki pocztowe przechowują dane wiadomości dla Teams standardowych kanałów.

Inne typy skrzynek pocztowych, takie jak RoomMailbox, które są używane w Teams konferencyjnych, nie są obsługiwane Teams przechowywania.

Teams używa usługi czatu obsługiwanej przez platformę Azure jako podstawowej przestrzeni dyskowej dla wszystkich wiadomości (czatów i wiadomości kanałów). Jeśli ze względu na zgodność Teams wiadomości musisz usunąć takie wiadomości, zasady przechowywania dotyczące Teams mogą usuwać wiadomości po określonym czasie, zależnie od tego, kiedy zostały utworzone. Wiadomości są następnie trwale usuwane zarówno ze skrzynek pocztowych usługi Exchange, w których były przechowywane na poziomie operacji zgodności, jak i z podstawowego miejsca do magazynowania używanego przez podstawową usługę czatu obsługiwanej przez platformę Azure. Aby uzyskać więcej informacji na temat architektury źródłowej, zobacz Zabezpieczenia i zgodność [z przepisami w programie Microsoft Teams](/MicrosoftTeams/security-compliance-overview), a w szczególności [sekcję Architektura ochrony informacji](/MicrosoftTeams/security-compliance-overview#information-protection-architecture).

Mimo że te dane z Teams i wiadomości kanałów są przechowywane w skrzynkach pocztowych, musisz skonfigurować zasady przechowywania dla wiadomości Teams kanałów  i Teams lokalizacji czatów. Teams czatów i wiadomości kanałów nie są uwzględniane w zasadach przechowywania, które są skonfigurowane Exchange skrzynek pocztowych użytkowników lub grup. Podobnie zasady przechowywania dla Teams nie mają wpływu na inne elementy poczty e-mail przechowywane skrzynki pocztowe.

Jeśli użytkownik zostanie dodany do czatu, do jego skrzynki pocztowej zostanie dodana kopia wszystkich wiadomości, które zostały im udostępnione. Data utworzenia tych wiadomości nie zmienia się dla nowego użytkownika i pozostaje taka sama dla wszystkich użytkowników.

> [!NOTE]
> Jeśli użytkownik jest uwzględniony w aktywnych zasadach przechowywania, które zachowują wiadomości programu Teams i usuwasz skrzynkę pocztową użytkownika uwzględnionego w tych zasadach, skrzynka pocztowa jest konwertowana na nieaktywną skrzynkę pocztową w celu zachowania Teams danych.[](inactive-mailboxes-in-office-365.md) Jeśli nie chcesz zachowywać tych danych Teams użytkownika, wyklucz konto użytkownika z zasad przechowywania i poczekaj, aż ta zmiana zostanie w związku [](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect) z nim w związku z usunięciem jego skrzynki pocztowej.

Po skonfigurowaniu zasad przechowywania dla wiadomości czatu i kanałów zadanie czasomierza z usługi Exchange okresowo ocenia elementy w folderze ukrytej skrzynki pocztowej, w którym są przechowywane Teams wiadomości. Zadanie czasomierza zwykle trwa 1–7 dni. Gdy te elementy wygasną w okresie przechowywania, są one przenoszone do folderu. Jest to inny folder ukryty, który znajduje się w każdej skrzynce pocztowej użytkownika lub grupy w celu przechowywania elementów "miękkiego usunięcia", zanim zostaną one trwale usunięte. 

Wiadomości pozostają w folderzeHolds Przez co najmniej 1 dzień, a następnie, jeśli można je usunąć, zadanie czasomierza usuwa je trwale przy następnym uruchamianiu.

> [!IMPORTANT]
> Ze względu na [](retention.md#the-principles-of-retention-or-what-takes-precedence) pierwszą zasadę przechowywania i ponieważ wiadomości na czacie i w kanałach programu Teams są przechowywane w skrzynkach pocztowych programu Exchange Online, trwałe usuwanie z folderuHolds jest zawsze zawieszone, jeśli na skrzynkę pocztową mają wpływ inne zasady przechowywania (w tym zasady stosowane do Exchange  lokalizację), zawieszenie w związku z postępowaniem sądowym, opóźnienie lub zastosowanie do skrzynki pocztowej zbierania elektronicznych materiałów dowodowych ze względów prawnych lub dochodzenia.
>
> Gdy skrzynka pocztowa jest zawarta w stosownym zarchiwiwi, wiadomości na czacie i w kanałach, które zostały usunięte Teams, nie będą już widoczne w aplikacji Teams, ale nadal będą wykrywalne przy użyciu zbierania elektronicznych materiałów dowodowych.

Po skonfigurowaniu zasad przechowywania dla czatu i wiadomości kanałów ścieżki, których zawartość przyjmuje, zależą od tego, czy zasady przechowywania mają być zachowywane, a następnie usuwane, zachowywać tylko lub usuwać tylko.

Jeśli zasady przechowywania mają być zachowywane, a następnie usuwane:

![Diagram przepływu przechowywania dla wiadomości Teams i kanałów.](../media/teamsretentionlifecycle.png)

W przypadku dwóch ścieżek na diagramie:

1. **Jeśli** czat lub wiadomość kanału jest edytowana lub usuwana przez użytkownika w trakcie okresu przechowywania, oryginalna wiadomość jest kopiowana (jeśli jest edytowana) lub przenoszony (jeśli została usunięta) do folderuHolds. Wiadomość jest tam przechowywana przez co najmniej 1 dzień. Po wygaśnięciu okresu przechowywania wiadomość jest trwale usuwana przy następnym uruchamianiu zadania czasomierza (zazwyczaj między 1 a 7 dniami).

2. **Jeśli wiadomość na** czacie lub w kanale nie zostanie usunięta przez użytkownika i bieżące wiadomości po zakończeniu edycji zostanie przeniesiona do folderuHolds. Ta czynność zazwyczaj trwa od 1 do 7 dni od daty wygaśnięcia. Gdy wiadomość znajduje się w folderze NimSzybki, jest tam przechowywana przez co najmniej 1 dzień, a następnie jest trwale usuwana przy następnym uruchamiam zadania czasomierza (zazwyczaj między 1 a 7 dniami). 

> [!NOTE]
> Wiadomości przechowywane w skrzynkach pocztowych, w tym foldery ukryte, można wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych. Dopóki wiadomości nie zostaną trwale usunięte z folderuHolds, pozostaną one przeszukiwane przez narzędzia zbierania elektronicznych materiałów dowodowych.

Podczas trwałego usuwania wiadomości z folderu Holds. Operacja usunięcia jest powiadamiana o operacji usuwania w usłudze czatu Azure, która następnie przekazuje tę samą operację do Teams klienckiej. Opóźnienia w komunikacji lub buforowaniu mogą wyjaśniać, dlaczego przez krótki czas użytkownicy przypisani do zasad mogą nadal widzieć te wiadomości w swoich aplikacjach usługi Teams, ale dane z tych wiadomości nie są zwracane podczas wyszukiwania zbierania elektronicznych materiałów dowodowych.

W tym scenariuszu, w którym usługa czatu Azure otrzymuje polecenie usuwania ze względu na zasady przechowywania, odpowiadająca jej wiadomość w aplikacji klienckiej usługi Teams jest usuwana dla wszystkich użytkowników w konwersacji. Niektórzy z tych użytkowników mogą pochodzić z innej organizacji, mają zasady przechowywania z dłuższym okresem przechowywania lub nie są do nich przypisane żadne zasady przechowywania. W przypadku tych użytkowników kopie wiadomości są nadal przechowywane w ich skrzynkach pocztowych i można nadal wyszukiwać zbierania elektronicznych materiałów dowodowych do momentu trwałego usunięcia wiadomości przez inne zasady przechowywania.

> [!IMPORTANT]
> Wiadomości widoczne w aplikacji Teams nie są dokładnym odzwierciedleniem tego, czy są zachowywane, czy trwale usuwane w celu zapewnienia zgodności z przepisami.

Gdy zasady przechowywania są tylko do zachowywania lub usuwania, ścieżki zawartości są odmianami zachowania i usuwania.

### <a name="content-paths-for-retain-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do przechowywania

1.  Jeśli czat lub wiadomość kanału jest edytowana lub usuwana przez użytkownika w trakcie okresu przechowywania: Oryginalna wiadomość jest kopiowana (jeśli edytowana) lub przenoszony (jeśli została usunięta) do folderuHolds i jest tam zachowywana przez co najmniej 1 dzień. Jeśli zasady przechowywania skonfigurowano tak, aby zachowywały bez końca, element pozostaje tam. Jeśli zasady przechowywania mają datę zakończenia okresu przechowywania i wygasają, wiadomość zostanie trwale usunięta przy następnym uruchamianiu zadania czasomierza (zazwyczaj między 1 a 7 dniem).

2. **Jeśli wiadomość czatu lub kanału nie została zmodyfikowana** ani usunięta przez użytkownika oraz dla bieżących wiadomości po zakończeniu edycji w trakcie okresu przechowywania: Nic się nie dzieje przed i po okresie przechowywania; wiadomość pozostanie w pierwotnej lokalizacji.

### <a name="content-paths-for-delete-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do usuwania

1. **Jeśli** wiadomość czatu lub kanału jest edytowana lub usuwana przez użytkownika w trakcie okresu przechowywania: Oryginalna wiadomość zostanie skopiowana (jeśli edytujesz) lub przeniesiona (jeśli została usunięta) do folderuHolds. Wiadomość jest tam zachowywana przez co najmniej 1 dzień i trwale usuwana przy następnym uruchamiam zadania czasomierza (zazwyczaj między 1 a 7 dniami).

2. **Jeśli wiadomość czatu lub** wiadomości kanału nie zostanie usunięta przez użytkownika w trakcie okresu przechowywania: Po zakończeniu okresu przechowywania wiadomość jest przenoszony do folderuHolds. Ta czynność zazwyczaj trwa od 1 do 7 dni od daty wygaśnięcia. Wiadomość jest tam zachowywana przez co najmniej 1 dzień, a następnie trwale usuwana przy następnym uruchamiam zadania czasomierza (zazwyczaj między 1 a 7 dniami).

#### <a name="example-flows-and-timings-for-retention-policies"></a>Przykładowe przepływy i chronometrażu zasad przechowywania

Skorzystaj z poniższych przykładów, aby zobaczyć, jak procesy i chronometraż opisane w poprzednich sekcjach mają zastosowanie do zasad przechowywania, które mają następujące konfiguracje:

- [Przykład 1. Zachowywanie tylko przez 7 lat](#example-1-retain-only-for-7-years)
- [Przykład 2. Zachowywanie przez 30 dni, a następnie usuwanie](#example-2-retain-for-30-days-and-then-delete)
- [Przykład 3. Usuwanie tylko po 1 dniu](#example-3-delete-only-after-1-day)

Ze względu na zasady przechowywania wszystkie przykłady dotyczące trwałego usuwania są zawieszane [, jeśli](retention.md#the-principles-of-retention-or-what-takes-precedence) wiadomość podlega innym zasadom przechowywania w celu zachowania elementu lub podlega zawieszeniu zbierania elektronicznych materiałów dowodowych.

##### <a name="example-1-retain-only-for-7-years"></a>Przykład 1. Zachowywanie tylko przez 7 lat

W dniu 1 użytkownik tworzy czat lub wiadomość w kanale.

W dniu 5 użytkownik edytuje tę wiadomość.

W dniu 30 użytkownik usunie bieżącą wiadomość.

Wyniki przechowywania:

- W przypadku oryginalnej wiadomości:
    - W dniu 5 wiadomość jest kopiowana do folderu. W którym nadal można ją przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez okres co najmniej 7 lat od dnia 1 (okresu przechowywania).

- W przypadku bieżącej (edytowanej) wiadomości:
    - W dniu 30 wiadomość jest przenoszona do folderu. W tym miejscu nadal można wyszukiwać pliki za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez okres co najmniej 7 lat od dnia 1 (okresu przechowywania).

Jeśli użytkownik usunął bieżącą wiadomość po upływie określonego okresu przechowywania, a nie w okresie przechowywania, wiadomość zostałaby nadal przeniesiona do folderu Holds. Jednak teraz okres przechowywania wygasł, wiadomość zostanie trwale usunięta po co najmniej 1 dniu, a następnie zwykle w ciągu 1–7 dni.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Przykład 2. Zachowywanie przez 30 dni, a następnie usuwanie

W dniu 1 użytkownik tworzy czat lub wiadomość w kanale.

W dniu 10 użytkownik edytuje tę wiadomość.

Użytkownik nie dokona dalszych zmian i nie usunie wiadomości.

Wyniki przechowywania:

- W przypadku oryginalnej wiadomości:
    - W dniu 10 wiadomość jest kopiowana do folderu OwaSS, gdzie nadal można ją przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.
    - Po upływie okresu przechowywania (30 dni od dnia 1) wiadomość jest zwykle trwale usuwana w ciągu 1–7 dni po co najmniej 1 dniu, a następnie nie zostanie zwrócona podczas wyszukiwania zbierania elektronicznych materiałów dowodowych.

- W przypadku bieżącej (edytowanej) wiadomości:
    - Po zakończeniu okresu przechowywania (30 dni od dnia 1) wiadomość jest przenoszona do folderu 1–7 dni, gdzie nadal może być przeszukiwana za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.
    - Wiadomość jest następnie trwale usuwana zwykle w ciągu 1–7 dni po co najmniej 1 dniu i nie zostanie zwrócona za pomocą wyszukiwań zbierania elektronicznych materiałów dowodowych.

##### <a name="example-3-delete-only-after-1-day"></a>Przykład 3. Usuwanie tylko po 1 dniu

> [!NOTE]
> Z powodu krótkiego, jednodniowego czasu trwania tych procesów konfiguracji i przechowywania, które działają w okresie 1–7 dni, w tej sekcji pokazano przykładowe chronometrażu z typowych przedziałów czasowych.

W dniu 1 użytkownik tworzy czat lub wiadomość w kanale.

Przykład wyniku przechowywania, jeśli użytkownik nie edytuje ani nie usuwa wiadomości:

- Dzień 5 (zazwyczaj 1–7 dni po rozpoczęciu okresu przechowywania w dniu 2):
    - Wiadomość zostanie przeniesiony do folderu Holds i pozostanie tam przez co najmniej 1 dzień, gdzie nadal może być przeszukiwana za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

- Dzień 9 (zazwyczaj 1–7 dni po co najmniej 1 dniu w folderzeHolds):
    - Wiadomość zostanie trwale usunięta, a następnie nie zostanie zwrócona za pomocą wyszukiwania zbierania elektronicznych materiałów dowodowych.

Jak pokazano w tym przykładzie, chociaż można skonfigurować zasady przechowywania tak, aby usuwać wiadomości po upływie zaledwie jednego dnia, usługa podlega wielu procesom w celu zapewnienia zgodnego usuwania. W efekcie akcja usunięcia po 1 dniu może potrwać 16 dni, zanim wiadomość zostanie trwale usunięta, aby nie była już zwracana w wyszukiwaniach zbierania elektronicznych materiałów dowodowych.

## <a name="skype-for-business-and-teams-interop-chats"></a>Skype dla firm i Teams czatów międzyplatplatowych

Gdy czat Skype dla firm się w Teams, staje się on wiadomością w Teams wątku czatu i jest przenoszony do odpowiedniej skrzynki pocztowej. Teams zasad przechowywania będą stosowane do tych wiadomości z Teams wątku. 

Jednak jeśli historia konwersacji jest włączona dla usługi Skype dla firm i po stronie klienta programu Skype dla firm, ta historia jest zapisywana w skrzynce pocztowej, te dane czatu nie są obsługiwane przez zasady przechowywania Teams wiadomości. W przypadku tej zawartości użyj zasad przechowywania skonfigurowanych dla tych Skype dla firm.

## <a name="meetings-and-external-users"></a>Spotkania i użytkownicy zewnętrzni

Wiadomości o spotkaniach w kanale są przechowywane w taki sam sposób jak wiadomości w kanałach, więc  dla tych danych podczas konfigurowania zasad przechowywania wybierz Teams wiadomości w kanale.

Wiadomości o spotkaniach niezapomnianych i zaplanowanych są przechowywane w taki sam sposób jak wiadomości czatu grupowego, więc aby  uzyskać te dane, podczas konfigurowania zasad przechowywania wybierz lokalizację Teams czatów.

Jeśli w spotkaniu hostowym twojej organizacji są dostępni użytkownicy zewnętrzni:

- Jeśli użytkownik zewnętrzny dołączy przy użyciu konta gościa w Twojej dzierżawie, wszystkie wiadomości ze spotkania będą przechowywane zarówno w skrzynce pocztowej twoich użytkowników, jak i w skrzynce pocztowej w tle, która zostanie nadana kontu gościa. Zasady przechowywania nie są jednak obsługiwane w przypadku skrzynek pocztowych w tle, mimo że można je zgłaszać jako objęte zasadami przechowywania dla całej lokalizacji (czasami nazywane "zasadami dla całej organizacji").

- Jeśli użytkownik zewnętrzny dołączy przy użyciu konta z innej organizacji programu Microsoft 365, zasady przechowywania nie mogą usuwać wiadomości dla tego użytkownika, ponieważ są one przechowywane w skrzynce pocztowej tego użytkownika w innej dzierżawie. Jednak w przypadku tego samego spotkania zasady przechowywania mogą usuwać wiadomości od użytkowników.

## <a name="when-a-user-leaves-the-organization"></a>Kiedy użytkownik odchodzi z organizacji 

Jeśli użytkownik, który ma skrzynkę pocztową w programie Exchange Online opuści organizację, Microsoft 365 jego konto zostanie usunięte, jego wiadomości na czacie, które podlegają przechowywaniu, są przechowywane w nieaktywnej skrzynce pocztowej. Wiadomości czatu podlegają wszelkim zasadom przechowywania, które zostały umieszczone na użytkowniku przed tym, gdy jego skrzynka pocztowa została nieaktywna, a zawartość jest dostępna podczas wyszukiwania zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Nieaktywne skrzynki pocztowe w Exchange Online](inactive-mailboxes-in-office-365.md). 

Jeśli użytkownik przechowył jakiekolwiek pliki w Teams, [zobacz sekcję](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) SharePoint i OneDrive.

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Jeśli nie wiesz, jak konfigurować przechowywanie w aplikacji Microsoft 365, zobacz [Wprowadzenie do zarządzania informacjami](get-started-with-information-governance.md).

Jeśli możesz już skonfigurować zasady przechowywania dla aplikacji Teams, zobacz Tworzenie [i konfigurowanie zasad przechowywania](create-retention-policies.md).