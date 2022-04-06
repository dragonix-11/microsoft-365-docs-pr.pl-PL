---
title: Informacje na temat przechowywania danych dla Yammer
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
description: Dowiedz się więcej o zasadach przechowywania, które dotyczą Yammer.
ms.openlocfilehash: 48b7f00df2f01d1b84af1962d91551752334c8b1
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595109"
---
# <a name="learn-about-retention-for-yammer"></a>Informacje na temat przechowywania danych dla Yammer

>*[Microsoft 365 licencjonowania w zakresie zabezpieczeń & zgodności](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Informacje zawarte w tym artykule uzupełnia informacje [dotyczące przechowywania,](retention.md) ponieważ zawierają informacje specyficzne dla Yammer.

W przypadku innych obciążeń, zobacz:

- [Dowiedz się więcej na temat przechowywania SharePoint i OneDrive](retention-policies-sharepoint.md)
- [Dowiedz się więcej na temat przechowywania Microsoft Teams](retention-policies-teams.md)
- [Dowiedz się więcej na temat przechowywania Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Co obejmuje przechowywanie i usuwanie

Yammer wiadomości użytkowników i wiadomości społeczności można usuwać przy użyciu zasad przechowywania dla programu Yammer, a ponadto, oprócz tekstu w tych wiadomościach, w celu zachowania zgodności mogą być zachowywane następujące elementy: linki hipertekstowe i linki do innych wiadomości Yammer wiadomości.

> [!NOTE]
> Jak wyjaśniono w poniższej sekcji, wiadomości użytkowników obejmują wiadomości prywatne dla poszczególnych użytkowników oraz wszystkie wiadomości społeczności skojarzone z tym użytkownikiem.

Wiadomości użytkowników zawierają wszystkie nazwy osób w konwersacji, a wiadomości społeczności zawierają nazwę społeczności i tytuł wiadomości (jeśli po pojęli).

Reakcje innych osób w formie emotikonów nie są zachowywane, gdy używasz zasad przechowywania na Yammer.

Pliki, z których korzystasz Yammer, nie są uwzględniane w zasadach przechowywania dla Yammer. Te elementy mają własne zasady przechowywania.

## <a name="how-retention-works-with-yammer"></a>Jak działa przechowywanie na Yammer

W tej sekcji opisano, w jaki sposób są spełnione wymagania dotyczące zgodności przez wewnętrzne magazyny i procesy. Powinny one być weryfikowane przez narzędzia zbierania elektronicznych materiałów dowodowych, a nie przez wiadomości obecnie widoczne w Yammer aplikacji.

Przy użyciu zasad przechowywania można zachować dane z wiadomości społeczności i wiadomości użytkowników w Yammer i usunąć te wiadomości. W tle dane Exchange są używane do przechowywania danych skopiowanych z tych wiadomości. Dane Yammer wiadomości od użytkowników są przechowywane w ukrytym folderze w skrzynce pocztowej każdego użytkownika zawartego w wiadomości użytkownika, a podobny ukryty folder w skrzynce pocztowej grupy jest używany do obsługi wiadomości społeczności.

Kopie wiadomości społeczności mogą być również przechowywane w ukrytym folderze skrzynek pocztowych użytkowników, gdy @wzmiankują użytkowników lub informują użytkownika o odpowiedzi. Mimo że te wiadomości są wiadomościami wysyłanymi do społeczności, zasady przechowywania Yammer wiadomości użytkowników będą często zawierać kopie wiadomości od społeczności. W efekcie wiadomości użytkowników nie są ograniczone do wiadomości prywatnych.

Te ukryte foldery nie są przeznaczone do bezpośredniego dostępu dla użytkowników lub administratorów, ale zamiast tego przechowuj dane, które administratorzy zgodności mogą wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

Mimo że wiadomości są przechowywane w programie Exchange, wiadomości Yammer są uwzględniane tylko w zasadach przechowywania skonfigurowanych dla wiadomości społeczności usługi **Yammer** lub lokalizacji wiadomości Yammer użytkowników.

> [!NOTE]
> Jeśli użytkownik jest uwzględniony w aktywnych zasadach przechowywania, które zachowują dane programu Yammer, Yammer użytkownik usunie skrzynkę pocztową użytkownika uwzględnionego w tych zasadach, w celu zachowania danych z usługi Yammer zostanie ona przekonwertowana na nieaktywną skrzynkę [pocztową](inactive-mailboxes-in-office-365.md). Jeśli nie chcesz zachowywać tych danych Yammer, wyklucz konto użytkownika z zasad przechowywania przed usunięciem jego skrzynki pocztowej.

Po skonfigurowaniu zasad przechowywania dla wiadomości Yammer zadanie czasomierza z usługi Exchange okresowo ocenia elementy w ukrytym folderze, w którym są przechowywane Yammer wiadomości. Zadanie czasomierza może potrwać do siedmiu dni. Po wygaśnięciu okresu przechowywania elementy te są przenoszone do folderu Holds — folderu ukrytego w skrzynce pocztowej każdego użytkownika lub grupy w celu przechowywania elementów "miękkiego usunięcia" przed ich trwałym usunięciem.

> [!IMPORTANT]
> Ze względu na [](retention.md#the-principles-of-retention-or-what-takes-precedence) pierwszą zasadę przechowywania i ze względu na to, że wiadomości Yammer są przechowywane w skrzynkach pocztowych programu Exchange Online, trwałe usuwanie z folderuHolds jest zawsze zawieszone, jeśli na skrzynkę pocztową mają wpływ inne zasady przechowywania (w tym zasady stosowane do Exchange  lokalizację), zawieszenie w związku z postępowaniem sądowym, opóźnienie lub zastosowanie do skrzynki pocztowej zbierania elektronicznych materiałów dowodowych ze względów prawnych lub dochodzenia.
>
> Gdy skrzynka pocztowa jest zawarta w stosownym zarchiwiwi, Yammer usunięte wiadomości nie będą już widoczne w programie Yammer ale nadal będą wykrywane za pomocą zbierania elektronicznych materiałów dowodowych.

Po skonfigurowaniu zasad przechowywania dla wiadomości Yammer ścieżki, których zawartość przyjmuje, zależą od tego, czy zasady przechowywania mają być zachowywane, a następnie usuwane, zachowywać tylko lub usuwać.

Jeśli zasady przechowywania mają być zachowywane, a następnie usuwane:

![Diagram przepływu przechowywania dla Yammer wiadomości.](../media/yammerretentionlifecycle.png)

W przypadku dwóch ścieżek na diagramie:

1. Jeśli wiadomość **Yammer** jest edytowana lub usuwana przez użytkownika w trakcie okresu przechowywania, wiadomość oryginalna jest natychmiast kopiowana (jeśli edytowana) lub przenoszony (jeśli została usunięta) do folderuHolds. Wiadomość jest przechowywana do momentu wygaśnięcia okresu przechowywania i natychmiastowego trwałego usunięcia wiadomości.

2. **Jeśli wiadomość Yammer** nie zostanie usunięta, a bieżące wiadomości będą wyświetlane po zakończeniu edycji, po upływie okresu przechowywania jest ona przenoszony do folderu. To działanie trwa do siedmiu dni od daty wygaśnięcia. Gdy wiadomość znajduje się w folderzeHolds, jest natychmiast trwale usuwana. 

> [!NOTE]
> Wiadomości w folderzeHolds Można wyszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych. Dopóki wiadomości nie zostaną trwale usunięte (w folderzeHolds), pozostaną one przeszukiwane przez narzędzia zbierania elektronicznych materiałów dowodowych.

Gdy zasady przechowywania są tylko do zachowywania lub usuwania, ścieżki zawartości są odmianami zachowania i usuwania.

### <a name="content-paths-for-retain-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do przechowywania

1. **Jeśli Yammer** wiadomości e-mail jest edytowana lub usuwana: Kopia oryginalnej wiadomości jest od razu tworzona w folderzeHolds i zachowywana w tym folderze do momentu wygaśnięcia okresu przechowywania. Następnie wiadomość zostanie natychmiast trwale usunięta z folderuHolds.

2. **Jeśli wiadomość Yammer** nie została zmodyfikowana ani usunięta oraz dla bieżących wiadomości po zakończeniu edycji w okresie przechowywania: Nic się nie dzieje przed i po okresie przechowywania; wiadomość pozostaje w pierwotnej lokalizacji.

### <a name="content-paths-for-delete-only-retention-policy"></a>Ścieżki zawartości dla zasad przechowywania tylko do usuwania

1. **Jeśli wiadomość Yammer** nie zostanie usunięta w trakcie okresu przechowywania: Na koniec okresu przechowywania wiadomość jest przenoszony do folderu Holds. To działanie trwa do siedmiu dni od daty wygaśnięcia. Następnie wiadomość zostanie natychmiast trwale usunięta z folderuHolds.

2. **Jeśli Yammer wiadomość** e-mail zostanie usunięta przez użytkownika w tym okresie, element zostanie natychmiast przeniesiony do folderu Holds, gdzie zostanie natychmiast trwale usunięty.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Przykładowe przepływy i chronometrażu zasad przechowywania

Skorzystaj z poniższych przykładów, aby zobaczyć, jak procesy i chronometraż opisane w poprzednich sekcjach mają zastosowanie do zasad przechowywania, które mają następujące konfiguracje:

- [Przykład 1. Zachowywanie tylko przez 7 lat](#example-1-retain-only-for-7-years)
- [Przykład 2. Zachowywanie przez 30 dni, a następnie usuwanie](#example-2-retain-for-30-days-and-then-delete)
- [Przykład 3. Usuwanie tylko po 1 dniu](#example-3-delete-only-after-1-day)

Ze względu na zasady przechowywania wszystkie przykłady dotyczące trwałego usuwania są zawieszane [, jeśli](retention.md#the-principles-of-retention-or-what-takes-precedence) wiadomość podlega innym zasadom przechowywania w celu zachowania elementu lub podlega zawieszeniu zbierania elektronicznych materiałów dowodowych.

##### <a name="example-1-retain-only-for-7-years"></a>Przykład 1. Zachowywanie tylko przez 7 lat

W dniu 1 użytkownik publikuje nową wiadomość Yammer wiadomości.

W dniu 5 użytkownik edytuje tę wiadomość.

W dniu 30 użytkownik usunie bieżącą wiadomość.

Wyniki przechowywania:

- W przypadku oryginalnej wiadomości:
    - W dniu 5 wiadomość jest kopiowana do folderu. W którym nadal można ją przeszukiwać za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez okres co najmniej 7 lat od dnia 1 (okresu przechowywania).

- W przypadku bieżącej (edytowanej) wiadomości:
    - W dniu 30 wiadomość jest przenoszona do folderu. W tym miejscu nadal można wyszukiwać pliki za pomocą narzędzi zbierania elektronicznych materiałów dowodowych przez okres co najmniej 7 lat od dnia 1 (okresu przechowywania).

Jeśli użytkownik usunął bieżącą wiadomość po upływie określonego okresu przechowywania, a nie w okresie przechowywania, wiadomość zostałaby nadal przeniesiona do folderu Holds. Jednak teraz okres przechowywania wygasł, wiadomość zostanie trwale usunięta po co najmniej 1 dniu, a następnie zwykle w ciągu 1–7 dni.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Przykład 2. Zachowywanie przez 30 dni, a następnie usuwanie

W dniu 1 użytkownik publikuje nową wiadomość Yammer wiadomości.

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

W dniu 1 użytkownik publikuje nową wiadomość Yammer wiadomości.

Przykład wyniku przechowywania, jeśli użytkownik nie edytuje ani nie usuwa wiadomości:

- Dzień 5 (zazwyczaj 1–7 dni po rozpoczęciu okresu przechowywania w dniu 2):
    - Wiadomość zostanie przeniesiony do folderu Holds i pozostanie tam przez co najmniej 1 dzień, gdzie nadal może być przeszukiwana za pomocą narzędzi zbierania elektronicznych materiałów dowodowych.

- Dzień 9 (zazwyczaj 1–7 dni po co najmniej 1 dniu w folderzeHolds):
    - Wiadomość zostanie trwale usunięta, a następnie nie zostanie zwrócona za pomocą wyszukiwania zbierania elektronicznych materiałów dowodowych.

Jak pokazano w tym przykładzie, chociaż można skonfigurować zasady przechowywania tak, aby usuwać wiadomości po upływie zaledwie jednego dnia, usługa podlega wielu procesom w celu zapewnienia zgodnego usuwania. W efekcie akcja usunięcia po 1 dniu może potrwać 16 dni, zanim wiadomość zostanie trwale usunięta, aby nie była już zwracana w wyszukiwaniach zbierania elektronicznych materiałów dowodowych.

## <a name="messages-and-external-users"></a>Wiadomości i użytkownicy zewnętrzni

Domyślnie zasady przechowywania wiadomości e-Yammer użytkowników dotyczą wszystkich użytkowników w organizacji, ale nie do użytkowników zewnętrznych. Zasady przechowywania można zastosować do użytkowników zewnętrznych, jeśli użyjesz opcji Edytuj  dla uwzględnionych użytkowników i określisz ich konto.

Obecnie użytkownicy goście B2B usługi Azure nie są obsługiwani.

## <a name="when-a-user-leaves-the-organization"></a>Kiedy użytkownik odchodzi z organizacji 

Jeśli użytkownik opuści organizację i jego konto Microsoft 365 zostanie usunięte, jego Yammer, które podlegają przechowywaniu, są przechowywane w nieaktywnej skrzynce pocztowej. Te wiadomości pozostają objęte zasadami przechowywania, które zostały umieszczone na użytkowniku przed tym, gdy jego skrzynka pocztowa została nieaktywna, a zawartość jest dostępna podczas wyszukiwania zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Nieaktywne skrzynki pocztowe w Exchange Online](inactive-mailboxes-in-office-365.md). 

Jeśli użytkownik przechowył jakiekolwiek pliki w u Yammer, [zobacz sekcję](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) równoważną dla pliku SharePoint i OneDrive.

## <a name="limitations"></a>Ograniczenia

Korzystając z przechowywania wiadomości e-mail i wiadomości Yammer użytkowników, należy pamiętać o następujących ograniczeniach:

- Po wybraniu pozycji **Edytuj** dla lokalizacji **Yammer wiadomości od** użytkowników mogą być wyświetlane goście i użytkownicy niebędący skrzynkami pocztowymi. Zasady przechowywania nie są przeznaczone dla tych użytkowników, więc ich nie wybieraj.

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Jeśli nie wiesz, jak konfigurować przechowywanie w aplikacji Microsoft 365, zobacz zarządzanie Wprowadzenie [informacjami](get-started-with-information-governance.md).

Jeśli możesz już skonfigurować zasady przechowywania dla aplikacji Yammer, zobacz [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md).