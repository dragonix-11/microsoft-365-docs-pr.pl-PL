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
description: Dowiedz się, jak działa przechowywanie w Exchange.
ms.openlocfilehash: f92df4bd25ddeff44472865c9ae221014050afaa
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009549"
---
# <a name="learn-about-retention-for-exchange"></a>Dowiedz się więcej na temat przechowywania Exchange

Informacje zawarte w tym artykule uzupełnia informacje [dotyczące przechowywania,](retention.md) ponieważ zawierają informacje specyficzne dla Exchange.  W przypadku innych obciążeń, zobacz:

- [Dowiedz się więcej na temat przechowywania SharePoint i OneDrive](retention-policies-sharepoint.md)
- [Dowiedz się więcej na temat przechowywania Microsoft Teams](retention-policies-teams.md)
- [Informacje na temat przechowywania danych dla Yammer](retention-policies-yammer.md)

## <a name="whats-included-for-retention-and-deletion"></a>Co obejmuje przechowywanie i usuwanie

Za pomocą zasad przechowywania i etykiet przechowywania można zachowywać i usuwać następujące elementy Exchange ze skrzynek pocztowych użytkowników i udostępnionych skrzynek pocztowych: wiadomości e-mail (obejmuje odebrane wiadomości, wersje robocze, wiadomości wysłane) z dowolnymi załącznikami, zadania, gdy mają datę zakończenia i notatki. 

Elementy kalendarza, które mają datę zakończenia, są obsługiwane w zasadach przechowywania, ale nie są obsługiwane w przypadku etykiet przechowywania.

Kontakty ani żadne zadania i elementy kalendarza, które nie mają daty zakończenia, nie są obsługiwane.

Inne elementy przechowywane w skrzynce pocztowej, takie jak wiadomości Skype i wiadomości Teams, nie są uwzględniane w zasadach przechowywania ani etykietach wiadomości Exchange. Te elementy mają własne zasady przechowywania.

## <a name="how-retention-works-for-exchange"></a>Jak działa przechowywanie w Exchange

Zarówno skrzynka pocztowa, jak i folder publiczny, używają [folderu Elementy do odzyskania](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) do przechowywania elementów. Tylko osoby, którym przypisano uprawnienia zbierania elektronicznych materiałów dowodowych, mogą wyświetlać elementy w folderze Elementy do odzyskania innego użytkownika.
  
Gdy użytkownik usunie wiadomość w folderze innym niż folder Elementy usunięte, domyślnie wiadomość jest przesunęła się do folderu Elementy usunięte. Jednak użytkownik może niechcący usunąć element (Shift+Delete) w dowolnym folderze, pomijając folder Elementy usunięte i przesunął go bezpośrednio do folderu Elementy do odzyskania.
  
Po zastosowaniu ustawień przechowywania do Exchange zadania czasomierza okresowo ocenia elementy w folderze Elementy do odzyskania. Jeśli element nie jest zgodne z regułami co najmniej jednej zasady przechowywania lub etykiety przechowywania w celu zachowania tego elementu, zostanie on trwale usunięty (nazywany również trwałym usunięciem) z folderu Elementy do odzyskania.

> [!NOTE]
> Ze względu na pierwszą zasadę przechowywania trwałe usuwanie jest zawsze [zawieszone, jeśli](retention.md#the-principles-of-retention-or-what-takes-precedence) ten sam element musi zostać zachowany ze względu na inne zasady przechowywania lub etykietę przechowywania albo jest on w ramach zbierania elektronicznych materiałów dowodowych ze względów prawnych lub badawczych.

Zadanie czasomierza może potrwać do siedmiu dni, a lokalizacja Exchange musi zawierać co najmniej 10 MB.
  
Gdy użytkownik próbuje zmienić właściwości elementu skrzynki pocztowej, takie jak temat, treść, załączniki, nadawcy i adresaci lub data wysłania lub odebrania wiadomości, kopia oryginalnego elementu jest zapisywana w folderze Elementy do odzyskania przed podjęciem tej zmiany. Ta czynność jest dzieje w przypadku każdej kolejnej zmiany. Po zakończeniu okresu przechowywania kopie w folderze Elementy do odzyskania zostaną trwale usunięte.

Po zastosowaniu ustawień przechowywania do Exchange ścieżki, których zawartość przyjmuje, zależą od tego, czy ustawienia przechowywania mają być zachowywane i usuwane, zachowywać tylko, czy tylko usuwać.

Zachowanie i usunięcie ustawień przechowywania:

![Diagram przepływu przechowywania w wiadomościach e-mail i folderach publicznych.](../media/88f174cc-bbf4-4305-93d7-0515f496c8f9.png)

1.  Jeśli element został zmodyfikowany lub trwale usunięty przez użytkownika (SHIFT+DELETE lub usunięty z elementów usuniętych) w okresie przechowywania: Element jest przenoszony (lub kopiowany w przypadku edycji) do folderu Elementy do odzyskania. W tym miejscu zadanie czasomierza działa okresowo i identyfikuje elementy, których okres przechowywania wygasł, a te elementy są trwale usuwane w ciągu 14 dni od końca okresu przechowywania. Domyślnie jest to ustawienie 14 dni, ale można je skonfigurować na maksymalnie 30 dni.

2.  Jeśli element nie został zmodyfikowany ani usunięty w trakcie okresu przechowywania: Ten sam proces jest uruchamiany okresowo we wszystkich folderach w skrzynce pocztowej i identyfikuje elementy, których okres przechowywania wygasł, a te elementy zostaną trwale usunięte w ciągu 14 dni od zakończenia okresu przechowywania. Domyślnie jest to ustawienie 14 dni, ale można je skonfigurować na maksymalnie 30 dni. 

Jeśli ustawienia przechowywania są dostępne tylko do zachowania lub tylko do usuwania, ścieżki zawartości są odmianami zachowania i usuwania:

### <a name="content-paths-for-retain-only-retention-settings"></a>Ścieżki zawartości dla ustawień przechowywania z zachowaniem tylko

1.  Jeśli element został zmodyfikowany lub usunięty w okresie przechowywania: Kopia oryginalnego elementu jest tworzona w folderze Elementy do odzyskania i zachowywana do końca okresu przechowywania, gdy kopia w folderze Elementy do odzyskania zostanie trwale usunięta w ciągu 14 dni od wygaśnięcia elementu. 

2. **Jeśli element nie został zmodyfikowany ani usunięty w** trakcie okresu przechowywania: Nic się nie dzieje przed i po okresie przechowywania; element pozostanie w jego pierwotnej lokalizacji.

### <a name="content-paths-for-delete-only-retention-settings"></a>Ścieżki zawartości dla ustawień przechowywania tylko do usuwania

1. **Jeśli element nie zostanie usunięty** w trakcie skonfigurowanego okresu: Na koniec skonfigurowanego okresu w zasadach przechowywania element jest przenoszony do folderu Elementy do odzyskania. 

2. **Jeśli element zostanie usunięty w** skonfigurowanym okresie: Element zostanie natychmiast przeniesiony do folderu Elementy do odzyskania. Jeśli użytkownik usunie z tego miejsca element lub opróżni folder Elementy do odzyskania, element zostanie trwale usunięty. W przeciwnym razie element zostanie trwale usunięty po upływie 14 dni od folderu Elementy do odzyskania. 

## <a name="user-notification-of-expiry-date"></a>Powiadomienie użytkownika o dacie wygaśnięcia

Zasady przechowywania dla usługi Exchange, w przeciwieństwie do zasad przechowywania dla innych obciążeń programu Microsoft 365, mają obecność użytkownika, wyświetlając u góry każdej wiadomości e-mail nazwę zasad przechowywania, które mają najkrótszą datę wygaśnięcia dla elementu, i obliczoną datę wygaśnięcia dla tego elementu. Użytkownicy nie zobaczą tego powiadomienia, jeśli zasady przechowywania nie usuwają elementów (zachowaj-tylko).

Jeśli etykieta przechowywania jest stosowana do wiadomości e-mail, nazwa tej etykiety i odpowiadająca jej data wygaśnięcia są zawsze wyświetlane i zastąpią nazwę i datę wszystkich zasad przechowywania zastosowanych do skrzynki pocztowej.

Pamiętaj, że w tym kontekście datą wygaśnięcia wiadomości e-mail, która zostanie usunięta, jest taka, kiedy użytkownicy mogą oczekiwać automatycznego przenoszenia tej wiadomości do folderu Elementy do odzyskania (jeśli jeszcze tam nie ma). Wiadomości e-mail w folderze Elementy do odzyskania nie zostaną trwale usunięte, ale pozostaną w nim w celu zachowania zgodności, jeśli podlegają one wszelkim ustawieniom przechowywania w celu zachowania go lub są objęte okresem zbierania elektronicznych materiałów dowodowych ze względów prawnych lub badawczych.

## <a name="when-a-user-leaves-the-organization"></a>Kiedy użytkownik odchodzi z organizacji 

Jeśli użytkownik opuści organizację, a jego skrzynka pocztowa zostanie uwzględniona w zasadach przechowywania, skrzynka pocztowa staje się nieaktywną skrzynką pocztową po usunięciu konta Microsoft 365 użytkownika. Zawartość nieaktywnej skrzynki pocztowej nadal podlega wszelkim zasadom przechowywania, które zostały umieszczone w skrzynce pocztowej przed jej nieaktywnością, a zawartość jest dostępna podczas wyszukiwania zbierania elektronicznych materiałów dowodowych. Aby uzyskać więcej informacji, zobacz [Nieaktywne skrzynki pocztowe w Exchange Online](inactive-mailboxes-in-office-365.md).

Gdy ustawienia przechowywania nie mają już zastosowania, ponieważ dane zostaną trwale usunięte lub okres przechowywania wygasł, administrator usługi Exchange może teraz usunąć nieaktywną [skrzynkę pocztową](delete-an-inactive-mailbox.md). W tym scenariuszu nieaktywna skrzynka pocztowa nie jest usuwana automatycznie.

## <a name="configuration-guidance"></a>Wskazówki dotyczące konfiguracji

Jeśli nie wiesz, jak konfigurować przechowywanie w aplikacji Microsoft 365, zobacz [Wprowadzenie do zarządzania informacjami](get-started-with-information-governance.md).

Jeśli możesz już skonfigurować zasady przechowywania lub etykiety przechowywania dla aplikacji Exchange, zobacz następujące instrukcje:
- [Tworzenie i konfigurowanie zasad przechowywania](create-retention-policies.md)
- [Tworzenie etykiet przechowywania i stosowanie ich w aplikacjach](create-apply-retention-labels.md)
- [Automatyczne stosowanie etykiety przechowywania do zawartości](apply-retention-labels-automatically.md)