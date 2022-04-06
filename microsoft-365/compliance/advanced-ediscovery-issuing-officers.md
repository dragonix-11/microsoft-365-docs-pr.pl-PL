---
title: Zarządzanie organami wydającym w programie Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: W programie w programie Advanced eDiscovery możesz dodać pracowników do komunikacji z użytkownikami w całej organizacji.
ms.openlocfilehash: 21c5a3db9cb0cfefb26bc75537f298c7e8a5c09a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704800"
---
# <a name="manage-issuing-officers-in-advanced-ediscovery"></a>Zarządzanie organami wydającym w programie Advanced eDiscovery

W przypadku utworzenia przez Ciebie lub inne osoby powiadomienia o wstrzymaniu lub innego rodzaju komunikacji wysyłanej na wypadek użytkownika, który jest przechwycący, musisz określić inspektora rozsyłającego informacje. Powiadomienie jest wysyłane do organizatora w imieniu określonego inspektora wydania. Na przykład paralegal w Twojej organizacji może być odpowiedzialny za tworzenie i wysyłanie powiadomień o wstrzymaniu w związku ze sprawą. W tym scenariuszu pełnomocnik może wskazać pełnomocnika jako pełnomocnika. KtoTo może zostać określona jako dyrektor ds. wydania? Istnieją dwa typy użytkowników, których można wybrać jako inspektora ds. komunikacji komunikacyjnej:

- Każdy członek konkretnej sprawy, w imieniu których jest wysyłana komunikacja.

- Każdy użytkownik dodany do listy służbowych w całej organizacji. Użytkowników z tej listy można dodać do dowolnej sprawy w organizacji.

W tym artykule wyjaśniono, jak dodawać użytkowników do listy ekspertów wydających informacje w całej organizacji i usuwać ich.

## <a name="before-you-add-an-issuing-officer"></a>Przed dodaniu inspektora wydania

- Musisz być administratorem zbierania elektronicznych materiałów dowodowych w Twojej organizacji, aby dodawać lub usuwać niejawnych administratorów. Aby uzyskać więcej informacji, [zobacz Przypisywanie uprawnień zbierania](assign-ediscovery-permissions.md) elektronicznych materiałów dowodowych w Centrum zgodności platformy Microsoft 365  

- Użytkownik dodany jako dyrektor ds. wydania musi mieć aktywną skrzynkę pocztową w Microsoft 365 organizacji.

- Organizacja może mieć maksymalnie 15 lekarzów wydających kartę. Członkowie sprawy, którzy mogą zostać wskazany jako dyrektor ds. wydania, nie są doliczane do tego limitu. Ten limit dotyczy tylko liczby użytkowników, których można dodać do strony **issuing officers** (Sporządzanie listów) w programie Advanced eDiscovery.

## <a name="add-an-issuing-officer"></a>Dodawanie inspektora wydania

1. W Centrum zgodności platformy Microsoft 365 przejdź do strony [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764), a następnie kliknij pozycję **Advanced eDiscovery ustawienia**.

   ![Wybierz Advanced eDiscovery ustawienia](..\media\HistoricalVersions1.png)

2. Na stronie **Ustawienia** wybierz kartę **Issuing officers (** Sporządzanie slajdów), aby wyświetlić stronę **Manage issuing officers (Zarządzaj sporządzaniem selektorów**).

   ![Strona ustawień służbowych.](..\media\AeDIssuingOfficers1.png)

3. Kliknij **przycisk** Dodaj, a następnie wyszukaj i dodaj jednego lub więcej użytkowników do listy insektantów.

Po dodaniu użytkowników jako inspektorów ds. wydawania wiadomości Ty i inni użytkownicy będziecie mogli określić tych użytkowników jako inspektora ds. komunikacji w dowolnej sprawie w organizacji. Aby uzyskać więcej informacji na temat tworzenia komunikacji w związku z wiadomościami, zobacz [Tworzenie powiadomienia o zerowym zeru.](create-hold-notification.md)

## <a name="remove-an-issuing-officer"></a>Usuwanie inspektora wydania

1. W Centrum zgodności platformy Microsoft 365 przejdź do strony [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764), a następnie kliknij pozycję **Advanced eDiscovery ustawienia**.

2. Na stronie **Ustawienia** wybierz kartę **Selektorzy**.

3. Wybierz co najmniej jednego użytkownika z listy iniektorów, a następnie kliknij pozycję **Usuń**.

Po usunięciu użytkowników z listy dyrektorów ds. wydawania wiadomości nie można już ich określać jako inspektora ds. komunikacji w nowym szybkim szycie, chyba że jest członkiem konkretnej sprawy, z która jest wystawiana korespondencja. Ponadto usunięcie inspektora wydania nie ma wpływu na żadne wiadomości wysłane przed usunięciem użytkownika jako inspektora wydania.
