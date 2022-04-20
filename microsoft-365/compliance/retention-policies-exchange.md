---
title: Dowiedz się więcej na temat przechowywania Exchange
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
description: Dowiedz się, jak działa przechowywanie dla Exchange.
ms.openlocfilehash: 66b7ad888e62ff84b6a2de49714bbbdf96268312
ms.sourcegitcommit: 1d972f15a45204e89e268c5ff257021aced5e775
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2022
ms.locfileid: "64911429"
---
# <a name="learn-about-retention-for-exchange"></a>Dowiedz się więcej na temat przechowywania Exchange

Informacje zawarte w tym artykule [uzupełniają informacje na temat przechowywania](retention.md), ponieważ zawierają informacje specyficzne dla Exchange.  W przypadku innych obciążeń zobacz:

- [Dowiedz się więcej na temat przechowywania SharePoint i OneDrive](retention-policies-sharepoint.md)
- [Dowiedz się więcej na temat przechowywania Microsoft Teams](retention-policies-teams.md)
- [Dowiedz się więcej na temat przechowywania Yammer](retention-policies-yammer.md)

## <a name="whats-included-for-retention-and-deletion"></a>Co jest dołączone do przechowywania i usuwania

Następujące Exchange elementów ze skrzynek pocztowych użytkownika i udostępnionych skrzynek pocztowych można przechowywać i usuwać przy użyciu zasad przechowywania i etykiet przechowywania: Wiadomości e-mail (w tym odebrane wiadomości, wersje robocze, wysłane wiadomości) z załącznikami, zadaniami, gdy mają datę zakończenia i notatki. 

Elementy kalendarza, które mają datę końcową, są obsługiwane w przypadku zasad przechowywania, ale nie są obsługiwane w przypadku etykiet przechowywania.

Kontakty oraz wszystkie zadania i elementy kalendarza, które nie mają daty zakończenia, nie są obsługiwane.

Inne elementy przechowywane w skrzynce pocztowej, takie jak wiadomości Skype i Teams, nie są uwzględniane w zasadach przechowywania ani etykietach dla Exchange. Te elementy mają własne zasady przechowywania.

## <a name="how-retention-works-for-exchange"></a>Jak działa przechowywanie dla Exchange

Zarówno skrzynka pocztowa, jak i folder publiczny używają [folderu Elementy możliwe do odzyskania](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) do przechowywania elementów. Tylko osoby, które mają przypisane uprawnienia do zbierania elektronicznych materiałów dowodowych, mogą wyświetlać elementy w folderze Elementy możliwe do odzyskania innego użytkownika.
  
Gdy użytkownik usunie komunikat w folderze innym niż folder Elementy usunięte, domyślnie komunikat zostanie przeniesiony do folderu Elementy usunięte. Użytkownik może jednak usunąć nietrwale element (Shift+Delete) w dowolnym folderze, który pomija folder Elementy usunięte i przenosi element bezpośrednio do folderu Elementy możliwe do odzyskania.
  
Po zastosowaniu ustawień przechowywania do Exchange danych zadanie czasomierza okresowo ocenia elementy w folderze Elementy możliwe do odzyskania. Jeśli element nie jest zgodny z regułami co najmniej jednej zasady przechowywania lub etykiety przechowywania w celu zachowania elementu, zostanie on trwale usunięty (nazywany również twardym usunięciem) z folderu Elementy możliwe do odzyskania.

> [!NOTE]
> Ze względu na [pierwszą zasadę przechowywania](retention.md#the-principles-of-retention-or-what-takes-precedence) trwałe usunięcie jest zawsze zawieszone, jeśli ten sam element musi zostać zachowany z powodu innych zasad przechowywania lub etykiety przechowywania lub jest objęty blokadą zbierania elektronicznych materiałów dowodowych ze względów prawnych lub śledczych.

Uruchomienie zadania czasomierza może potrwać do siedmiu dni, a lokalizacja Exchange musi zawierać co najmniej 10 MB.
  
Gdy użytkownik próbuje zmienić właściwości elementu skrzynki pocztowej — na przykład temat, treść, załączniki, nadawców i adresatów albo datę wysłania lub odebrania wiadomości — kopia oryginalnego elementu jest zapisywana w folderze Elementy możliwe do odzyskania, zanim zmiana zostanie zatwierdzona. Ta akcja jest wykonywana dla każdej kolejnej zmiany. Po zakończeniu okresu przechowywania kopie w folderze Elementy możliwe do odzyskania zostaną trwale usunięte.

Po zastosowaniu ustawień przechowywania do Exchange zawartości ścieżki, które pobiera zawartość, zależą od tego, czy ustawienia przechowywania mają być zachowywane i usuwane, tylko do zachowania, czy usuwania.

Gdy ustawienia przechowywania mają zostać zachowane i usunięte:

![Diagram przepływu przechowywania w wiadomościach e-mail i folderach publicznych.](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1. **Jeśli element zostanie zmodyfikowany lub trwale usunięty** przez użytkownika (SHIFT+DELETE lub usunięty z elementów usuniętych) w okresie przechowywania: element zostanie przeniesiony (lub skopiowany w przypadku edycji) do folderu Elementy możliwe do odzyskania. W tym miejscu zadanie czasomierza jest uruchamiane okresowo i identyfikuje elementy, których okres przechowywania wygasł, a te elementy są trwale usuwane w ciągu 14 dni od zakończenia okresu przechowywania. Pamiętaj, że ustawienie domyślne to 14 dni, ale można je skonfigurować do 30 dni.

2. **Jeśli element nie zostanie zmodyfikowany lub usunięty** w okresie przechowywania: ten sam proces jest okresowo uruchamiany we wszystkich folderach w skrzynce pocztowej i identyfikuje elementy, których okres przechowywania wygasł, a te elementy są trwale usuwane w ciągu 14 dni od zakończenia okresu przechowywania. Pamiętaj, że ustawienie domyślne to 14 dni, ale można je skonfigurować do 30 dni. 

Jeśli ustawienia przechowywania są tylko do zachowania lub tylko do usuwania, ścieżki zawartości są odmianami zachowywania i usuwania:

### <a name="content-paths-for-retain-only-retention-settings"></a>Ścieżki zawartości dla ustawień przechowywania tylko do zachowania

1. **Jeśli element zostanie zmodyfikowany lub usunięty** w okresie przechowywania: kopia oryginalnego elementu zostanie utworzona w folderze Elementy możliwe do odzyskania i zachowana do końca okresu przechowywania, gdy kopia w folderze Elementy możliwe do odzyskania zostanie trwale usunięta w ciągu 14 dni od wygaśnięcia elementu. 

2. **Jeśli element nie został zmodyfikowany lub usunięty** w okresie przechowywania: Nic się nie dzieje przed i po okresie przechowywania; element pozostaje w oryginalnej lokalizacji.

### <a name="content-paths-for-delete-only-retention-settings"></a>Ścieżki zawartości dla ustawień przechowywania tylko do usuwania

1. **Jeśli element nie zostanie usunięty** w skonfigurowanym okresie: na końcu skonfigurowanego okresu w zasadach przechowywania element zostanie przeniesiony do folderu Elementy możliwe do odzyskania. 

2. **Jeśli element zostanie usunięty** w skonfigurowanym okresie: element zostanie natychmiast przeniesiony do folderu Elementy możliwe do odzyskania. Jeśli użytkownik usunie element z tego miejsca lub opróżni folder Elementy możliwe do odzyskania, element zostanie trwale usunięty. W przeciwnym razie element zostanie trwale usunięty po 14 dniach w folderze Elementy do odzyskania. 

## <a name="user-notification-of-expiry-date"></a>Powiadomienie użytkownika o dacie wygaśnięcia

Zasady przechowywania dla Exchange, w przeciwieństwie do zasad przechowywania dla innych obciążeń Microsoft 365, mają obecność użytkownika, wyświetlając w górnej części każdej wiadomości e-mail nazwę zasad przechowywania, która ma najkrótszą datę wygaśnięcia elementu, oraz obliczoną datę wygaśnięcia dla tego elementu. Użytkownicy nie widzą tego powiadomienia, jeśli zasady przechowywania nie usuwają elementów (tylko do zachowania).

Jeśli etykieta przechowywania jest stosowana do wiadomości e-mail, nazwa tej etykiety i odpowiadająca jej data wygaśnięcia są zawsze wyświetlane i zastąpią nazwę i datę z wszelkich zasad przechowywania stosowanych do skrzynki pocztowej.

Pamiętaj, że w tym kontekście datą wygaśnięcia daty usunięcia wiadomości e-mail jest to, kiedy użytkownicy mogą oczekiwać, że wiadomość e-mail zostanie automatycznie przeniesiona do folderu Elementy możliwe do odzyskania (jeśli jeszcze nie istnieje). Wiadomości e-mail w folderze Elementy możliwe do odzyskania nie zostaną trwale usunięte, ale pozostaną tam do celów zgodności, jeśli podlegają wszelkim ustawieniu przechowywania, aby je zachować, lub znajdują się w archiwum zbierania elektronicznych materiałów dowodowych ze względów prawnych lub śledczych.

## <a name="when-a-user-leaves-the-organization"></a>Gdy użytkownik opuszcza organizację 

Jeśli użytkownik opuści organizację, a skrzynka pocztowa użytkownika zostanie uwzględniona w zasadach przechowywania, skrzynka pocztowa stanie się nieaktywną skrzynką pocztową po usunięciu konta Microsoft 365 użytkownika. Zawartość nieaktywnej skrzynki pocztowej nadal podlega wszelkim zasadom przechowywania, które zostały umieszczone w skrzynce pocztowej przed jej nieaktywnością, a zawartość jest dostępna dla wyszukiwania zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Nieaktywne skrzynki pocztowe w Exchange Online](inactive-mailboxes-in-office-365.md).

Jeśli ustawienia przechowywania nie mają już zastosowania, ponieważ dane zostały trwale usunięte lub okres przechowywania wygasł, administrator Exchange może teraz [usunąć nieaktywną skrzynkę pocztową](delete-an-inactive-mailbox.md). W tym scenariuszu nieaktywna skrzynka pocztowa nie jest automatycznie usuwana.

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Jeśli dopiero zaczynasz konfigurować przechowywanie w Microsoft 365, zobacz [Wprowadzenie z zarządzaniem informacjami](get-started-with-information-governance.md).

Jeśli wszystko jest gotowe do skonfigurowania zasad przechowywania lub etykiety przechowywania dla Exchange, zobacz następujące instrukcje:
- [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md)
- [Publikowanie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)