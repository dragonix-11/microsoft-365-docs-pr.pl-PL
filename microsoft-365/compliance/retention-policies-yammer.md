---
title: Dowiedz się więcej na temat przechowywania usługi Yammer
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
description: Dowiedz się więcej o zasadach przechowywania, które mają zastosowanie do usługi Yammer.
ms.openlocfilehash: d2703947d2cebc5818793362e55b8eae9cec2ed8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639627"
---
# <a name="learn-about-retention-for-yammer"></a>Dowiedz się więcej na temat przechowywania usługi Yammer

>*[Wskazówki dotyczące licencjonowania platformy Microsoft 365 dotyczące zgodności & zabezpieczeń](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Informacje zawarte w tym artykule [uzupełniają informacje na temat przechowywania](retention.md) , ponieważ zawierają informacje specyficzne dla usługi Yammer.

W przypadku innych obciążeń zobacz:

- [Dowiedz się więcej o przechowywaniu dla programu SharePoint i usługi OneDrive](retention-policies-sharepoint.md)
- [Dowiedz się więcej o przechowywaniu w usłudze Microsoft Teams](retention-policies-teams.md)
- [Dowiedz się więcej o przechowywaniu dla programu Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Co jest dołączone do przechowywania i usuwania

Komunikaty użytkowników i wiadomości społeczności usługi Yammer można usuwać przy użyciu zasad przechowywania dla usługi Yammer, a oprócz tekstu w tych wiadomościach następujące elementy można przechowywać ze względów zgodności: linki hipertekstu i linki do innych komunikatów usługi Yammer.

> [!NOTE]
> Jak wyjaśniono w poniższej sekcji, komunikaty użytkowników zawierają wiadomości prywatne dla poszczególnych użytkowników oraz wszelkie komunikaty społeczności skojarzone z tym użytkownikiem.

Komunikaty użytkowników zawierają wszystkie nazwy osób w konwersacji, a wiadomości społeczności zawierają nazwę społeczności i tytuł wiadomości (jeśli zostały podane).

Reakcje innych osób w postaci emotikonów nie są zachowywane podczas korzystania z zasad przechowywania dla usługi Yammer.

Pliki używane w usłudze Yammer nie są uwzględniane w zasadach przechowywania usługi Yammer. Te elementy mają własne zasady przechowywania.

## <a name="how-retention-works-with-yammer"></a>Jak działa przechowywanie w usłudze Yammer

Ta sekcja służy do zrozumienia, w jaki sposób wymagania dotyczące zgodności są spełniane przez magazyn zaplecza i procesy, i powinny być weryfikowane przez narzędzia zbierania elektronicznych materiałów dowodowych, a nie przez komunikaty, które są obecnie widoczne w aplikacji Yammer.

Zasady przechowywania umożliwiają przechowywanie danych z komunikatów społeczności i komunikatów użytkowników w usłudze Yammer oraz usuwanie tych komunikatów. W tle skrzynki pocztowe programu Exchange są używane do przechowywania danych skopiowanych z tych wiadomości. Dane z komunikatów użytkowników usługi Yammer są przechowywane w ukrytym folderze w skrzynce pocztowej każdego użytkownika dołączonego do wiadomości użytkownika, a podobny ukryty folder w skrzynce pocztowej grupy jest używany na potrzeby wiadomości społeczności.

Kopie wiadomości społeczności mogą być również przechowywane w ukrytym folderze skrzynek pocztowych użytkownika, gdy @ wspomnieć użytkowników lub powiadomić użytkownika o odpowiedzi. Mimo że te komunikaty pochodzą z wiadomości społeczności, zasady przechowywania komunikatów użytkowników usługi Yammer często zawierają kopie komunikatów społeczności. W związku z tym komunikaty użytkowników nie są ograniczone do wiadomości prywatnych.

Te ukryte foldery nie są przeznaczone do bezpośredniego dostępu do użytkowników lub administratorów, ale zamiast tego przechowują dane, które administratorzy zgodności mogą wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

Mimo że są one przechowywane w programie Exchange, komunikaty usługi Yammer są uwzględniane tylko w zasadach przechowywania skonfigurowanych dla **komunikatów społeczności usługi Yammer** lub lokalizacji **komunikatów użytkowników usługi Yammer** .

> [!NOTE]
> Jeśli użytkownik jest uwzględniony w aktywnych zasadach przechowywania, które przechowują dane usługi Yammer, a ty usuniesz skrzynkę pocztową użytkownika uwzględnionego w tych zasadach, aby zachować dane usługi Yammer, skrzynka pocztowa zostanie przekonwertowana na [nieaktywną skrzynkę pocztową](inactive-mailboxes-in-office-365.md). Jeśli nie musisz zachowywać tych danych usługi Yammer dla użytkownika, przed usunięciem skrzynki pocztowej wyklucz konto użytkownika z zasad przechowywania.

Po skonfigurowaniu zasad przechowywania komunikatów usługi Yammer zadanie czasomierza z usługi Exchange okresowo ocenia elementy w ukrytym folderze, w którym są przechowywane te komunikaty usługi Yammer. Uruchomienie zadania czasomierza trwa do siedmiu dni. Po wygaśnięciu okresu przechowywania tych elementów są one przenoszone do folderu SubstrateHolds — ukrytego folderu, który znajduje się w każdej skrzynce pocztowej użytkownika lub grupy w celu przechowywania elementów "nietrwale usuniętych", zanim zostaną trwale usunięte.

> [!IMPORTANT]
> Ze względu na [pierwszą zasadę przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence) i ponieważ wiadomości usługi Yammer są przechowywane w Exchange Online skrzynkach pocztowych, trwałe usunięcie z folderu SubstrateHolds jest zawsze zawieszone, jeśli na skrzynkę pocztową mają wpływ inne zasady przechowywania usługi Yammer dla tej samej lokalizacji, blokada postępowania sądowego, wstrzymanie opóźnienia lub jeśli do skrzynki pocztowej zastosowano blokadę zbierania elektronicznych materiałów dowodowych ze względów prawnych lub śledczych.
>
> Chociaż skrzynka pocztowa znajduje się w odpowiednim archiwum, wiadomości usługi Yammer, które zostały usunięte, nie będą już widoczne w usłudze Yammer, ale będą nadal wykrywalne za pomocą elektronicznego zbierania elektronicznych materiałów dowodowych.

Po skonfigurowaniu zasad przechowywania dla komunikatów usługi Yammer ścieżki, które pobiera zawartość, zależą od tego, czy zasady przechowywania mają być zachowywane, a następnie usuwane, tylko do zachowania lub usuwania.

Gdy zasady przechowywania mają zostać zachowane, a następnie usunięte:

![Diagram przepływu przechowywania komunikatów usługi Yammer.](../media/yammerretentionlifecycle.png)

Dla dwóch ścieżek na diagramie:

1. **Jeśli komunikat usługi Yammer jest edytowany lub usuwany** przez użytkownika w okresie przechowywania, oryginalna wiadomość jest natychmiast kopiowana (jeśli jest edytowana) lub przenoszona (jeśli została usunięta) do folderu SubstrateHolds. Komunikat jest tam przechowywany do czasu wygaśnięcia okresu przechowywania, a następnie komunikat zostanie natychmiast trwale usunięty.

2. **Jeśli komunikat usługi Yammer nie zostanie usunięty** i dla bieżących komunikatów po edycji komunikat zostanie przeniesiony do folderu SubstrateHolds po upływie okresu przechowywania. Ta akcja trwa do siedmiu dni od daty wygaśnięcia. Gdy komunikat znajduje się w folderze SubstrateHolds, zostanie on natychmiast trwale usunięty. 

> [!NOTE]
> Komunikaty w folderze SubstrateHolds można wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych. Dopóki komunikaty nie zostaną trwale usunięte z folderu SubstrateHolds, nadal można je przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

Gdy okres przechowywania wygaśnie i przeniesie komunikat do folderu SubstrateHolds, operacja usuwania jest przekazywana do usługi Yammer, która następnie przekazuje tę samą operację do aplikacji klienckiej usługi Yammer. Opóźnienia w tej komunikacji lub buforowaniu mogą wyjaśniać, dlaczego przez krótki czas użytkownicy nadal widzą te komunikaty w swojej aplikacji Yammer.

W tym scenariuszu, w którym usługa Yammer otrzymuje polecenie usuwania z powodu zasad przechowywania, odpowiedni komunikat w aplikacji Yammer jest usuwany dla wszystkich użytkowników w konwersacji. Niektórzy z tych użytkowników mogą pochodzić z innej organizacji, mają zasady przechowywania z dłuższym okresem przechowywania lub nie są do nich przypisane żadne zasady przechowywania. W przypadku tych użytkowników kopie wiadomości są nadal przechowywane w ich skrzynkach pocztowych i pozostają możliwe do wyszukiwania pod kątem zbierania elektronicznych materiałów dowodowych, dopóki wiadomości nie zostaną trwale usunięte przez inne zasady przechowywania.

> [!IMPORTANT]
> Komunikaty widoczne w aplikacji Yammer nie są dokładnym odzwierciedleniem tego, czy są zachowywane, czy trwale usuwane w celu spełnienia wymagań dotyczących zgodności.

Jeśli zasady przechowywania są tylko do zachowania lub tylko do usuwania, ścieżki zawartości są odmianami zachowywania i usuwania.

### <a name="content-paths-for-retain-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do zachowania

1. **Jeśli komunikat usługi Yammer jest edytowany lub usuwany**: kopia oryginalnej wiadomości jest natychmiast tworzona w folderze SubstrateHolds i przechowywana do czasu wygaśnięcia okresu przechowywania. Następnie komunikat zostanie natychmiast trwale usunięty z folderu SubstrateHolds.

2. **Jeśli komunikat usługi Yammer nie został zmodyfikowany lub usunięty** oraz dla bieżących komunikatów po edycji w okresie przechowywania: Nic się nie dzieje przed i po okresie przechowywania; komunikat pozostaje w oryginalnej lokalizacji.

### <a name="content-paths-for-delete-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do usuwania

1. **Jeśli komunikat usługi Yammer nie zostanie usunięty** w okresie przechowywania: po zakończeniu okresu przechowywania komunikat zostanie przeniesiony do folderu SubstrateHolds. Ta akcja trwa do siedmiu dni od daty wygaśnięcia. Następnie komunikat zostanie natychmiast trwale usunięty z folderu SubstrateHolds.

2. **Jeśli komunikat usługi Yammer zostanie usunięty przez użytkownika w** tym okresie, element zostanie natychmiast przeniesiony do folderu SubstrateHolds, w którym zostanie natychmiast trwale usunięty.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Przykładowe przepływy i chronometraż zasad przechowywania

Skorzystaj z poniższych przykładów, aby zobaczyć, jak procesy i chronometraż wyjaśnione w poprzednich sekcjach mają zastosowanie do zasad przechowywania, które mają następujące konfiguracje:

- [Przykład 1: Zachowaj tylko przez 7 lat](#example-1-retain-only-for-7-years)
- [Przykład 2: Zachowaj przez 30 dni, a następnie usuń](#example-2-retain-for-30-days-and-then-delete)
- [Przykład 3: Usuwanie tylko po 1 dniu](#example-3-delete-only-after-1-day)

Dla wszystkich przykładów, które odwołują się do trwałego usunięcia, ze względu na [zasady przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence), ta akcja jest zawieszona, jeśli komunikat podlega innym zasadom przechowywania w celu zachowania elementu lub podlega blokadzie zbierania elektronicznych materiałów dowodowych.

##### <a name="example-1-retain-only-for-7-years"></a>Przykład 1: Zachowaj tylko przez 7 lat

W dniu 1 użytkownik publikuje nową wiadomość usługi Yammer.

W dniu 5 użytkownik edytuje ten komunikat.

W dniu 30 użytkownik usuwa bieżący komunikat.

Wyniki przechowywania:

- W przypadku oryginalnej wiadomości:
    - W dniu 5 komunikat jest kopiowany do folderu SubstrateHolds, w którym nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez co najmniej 7 lat od dnia 1 (okres przechowywania).

- Dla bieżącego (edytowanego) komunikatu:
    - W dniu 30 komunikat przechodzi do folderu SubstrateHolds, w którym nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez co najmniej 7 lat od dnia 1 (okres przechowywania).

Jeśli użytkownik usunął bieżący komunikat po określonym okresie przechowywania, zamiast w okresie przechowywania, komunikat nadal będzie przenoszony do folderu SubstrateHolds. Jednak teraz okres przechowywania wygasł, komunikat zostanie trwale usunięty po upływie co najmniej 1 dnia, a następnie zazwyczaj w ciągu 1–7 dni.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Przykład 2: Zachowaj przez 30 dni, a następnie usuń

W dniu 1 użytkownik publikuje nową wiadomość usługi Yammer.

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

W dniu 1 użytkownik publikuje nową wiadomość usługi Yammer.

Przykładowy wynik przechowywania, jeśli użytkownik nie edytuje ani nie usunie komunikatu:

- Dzień 5 (zazwyczaj 1–7 dni po rozpoczęciu okresu przechowywania w dniu 2):
    - Komunikat jest przenoszony do folderu SubstrateHolds i pozostaje tam przez co najmniej 1 dzień, w którym nadal można go przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

- Dzień 9 (zazwyczaj 1–7 dni po co najmniej 1 dniu w folderze SubstrateHolds):
    - Wiadomość zostanie trwale usunięta, a następnie nie zostanie zwrócona z wyszukiwaniem zbierania elektronicznych materiałów dowodowych.

Jak pokazano w tym przykładzie, mimo że można skonfigurować zasady przechowywania w celu usuwania komunikatów po zaledwie jednym dniu, usługa przechodzi wiele procesów w celu zapewnienia zgodnego usunięcia. W związku z tym akcja usuwania po upływie 1 dnia może potrwać 16 dni, zanim wiadomość zostanie trwale usunięta, aby nie była już zwracana w wyszukiwaniach zbierania elektronicznych materiałów dowodowych.

## <a name="messages-and-external-users"></a>Komunikaty i użytkownicy zewnętrzni

Domyślnie zasady przechowywania komunikatów użytkowników usługi Yammer mają zastosowanie do wszystkich użytkowników w organizacji, ale nie do użytkowników zewnętrznych. Zasady przechowywania można zastosować do użytkowników zewnętrznych, jeśli używasz opcji **Edytuj** dla dołączonych użytkowników i określasz ich konto.

Obecnie użytkownicy-goście usługi Azure B2B nie są obsługiwana.

## <a name="when-a-user-leaves-the-organization"></a>Gdy użytkownik opuszcza organizację 

Jeśli użytkownik opuści organizację, a jego konto platformy Microsoft 365 zostanie usunięte, wiadomości użytkowników usługi Yammer, które podlegają przechowywaniu, są przechowywane w nieaktywnej skrzynce pocztowej. Te wiadomości pozostają objęte wszelkimi zasadami przechowywania, które zostały umieszczone na użytkowniku, zanim jego skrzynka pocztowa została nieaktywna, a zawartość jest dostępna dla wyszukiwania zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Dowiedz się więcej o nieaktywnych skrzynkach pocztowych](inactive-mailboxes-in-office-365.md).

Jeśli użytkownik przechowywał jakiekolwiek pliki w usłudze Yammer, zobacz [równoważną sekcję](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) programu SharePoint i usługi OneDrive.

## <a name="limitations"></a>Ograniczenia

Podczas korzystania z przechowywania komunikatów społeczności i komunikatów użytkowników usługi Yammer należy pamiętać o następującym ograniczeniu:

- Po wybraniu pozycji **Edytuj** dla lokalizacji **wiadomości użytkowników usługi Yammer** mogą być widoczni goście i użytkownicy bez skrzynki pocztowej. Zasady przechowywania nie są przeznaczone dla tych użytkowników, więc nie wybieraj ich.

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Jeśli dopiero zaczynasz konfigurować przechowywanie w usłudze Microsoft 365, zobacz [Wprowadzenie do zarządzania cyklem życia danych](get-started-with-data-lifecycle-management.md).

Jeśli wszystko jest gotowe do skonfigurowania zasad przechowywania usługi Yammer, zobacz [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md).
