---
title: Zarządzanie zdarzeniami w Microsoft 365 Defender
description: Dowiedz się, jak przypisywać, aktualizować stan,
keywords: zdarzenie, zdarzenia, analiza, odpowiedź, alerty, skorelowane alerty, przypisywanie, aktualizowanie, stan, zarządzanie, klasyfikacja, microsoft, 365, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: b9cc3e0ab911515d010b1a6e7feaac5cff8aed51
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015387"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Zarządzanie zdarzeniami w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Zarządzanie zdarzeniami ma kluczowe znaczenie dla zapewniania nazwania, przypisania i tagowania zdarzeń w celu zoptymalizowania czasu w przepływie pracy związanej z incydentami oraz zapewnienia szybkiego blokowania zagrożeń i  adresem ich.

Możesz zarządzać zdarzeniami z & i **alertami >** zdarzeniami po szybkim uruchomieniu portalu Microsoft 365 Defender ([security.microsoft.com](https://security.microsoft.com)). Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Przykład kolejki zdarzeń." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Oto sposoby zarządzania zdarzeniami:

- [Edytowanie nazwy zdarzenia](#edit-the-incident-name)
- [Dodawanie tagów zdarzeń](#add-incident-tags)
- [Przypisywanie zdarzenia do konta użytkownika](#assign-an-incident)
- [Rozwiąż je](#resolve-an-incident)
- [Ustawianie klasyfikacji i wyznaczania jej](#set-the-classification-and-determination)
- [Dodawanie komentarzy](#add-comments)

Możesz zarządzać zdarzeniami z **okienka Zarządzanie zdarzeniami** w przypadku zdarzenia. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Przykład okienka Zarządzanie zdarzeniem w przypadku zdarzenia." lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

To okienko można wyświetlić za pomocą **linku Zarządzaj incydentem** na stronie:

- Okienko Właściwości zdarzenia w kolejce zdarzenia.
- **Strona** podsumowania zdarzenia.

W przypadkach, gdy chcesz przenieść alerty między zdarzeniami, możesz to również zrobić z karty Alerty,  tworząc większe lub mniejsze zdarzenie, które zawiera wszystkie alerty.

## <a name="edit-the-incident-name"></a>Edytowanie nazwy zdarzenia

Microsoft 365 Defender automatycznie przypisuje nazwę na podstawie atrybutów alertów, takich jak liczba punktów końcowych, których dotyczy problem, użytkowników, źródeł wykrywania lub kategorii. Umożliwia to szybkie zrozumienie zakresu zdarzenia. Przykład: *Wieloetapowe zdarzenie dotyczące wielu punktów końcowych zgłoszonych przez wiele źródeł.*

Nazwę zdarzenia można edytować w polu **Nazwa zdarzenia** w **okienku Zarządzanie zdarzeniem** .

> [!NOTE]
> Zdarzenia, które istniały przed rozpoczęciem funkcji automatycznego nazewnictwa zdarzeń, zachowają swoje imię i nazwisko.

## <a name="add-incident-tags"></a>Dodawanie tagów zdarzeń

Możesz dodać tagi niestandardowe do zdarzenia, na przykład aby oflagować grupę zdarzeń o wspólnym cechu. Możesz później filtrować kolejkę zdarzeń pod celu filtrowania wszystkich zdarzeń zawierających określony tag.

Po rozpoczęciu wpisywania możesz wybrać pozycję z listy wcześniej używanych i zaznaczonych tagów.

## <a name="assign-an-incident"></a>Przypisywanie zdarzenia

Jeśli zdarzenie nie zostało jeszcze przypisane, możesz zaznaczyć pole **Przypisz** do i określić konto użytkownika. Aby ponownie przypisać zdarzenie, usuń bieżące konto zadania, wybierając znak "x" obok nazwy konta, a następnie pole **Wyboru** przypisz do. Przypisanie własności zdarzenia przypisuje tę samą własność wszystkim skojarzonym z nim alertom.

Możesz uzyskać listę przydzielonych Ci zdarzeń, filtrując kolejkę zdarzeń. 

1. W kolejce zdarzeń wybierz pozycję **Filtry**.
2. w sekcji **Zadanie na zdarzenie** wyczyść pozycję **Zaznacz wszystko** i wybierz **pozycję Przypisane do mnie**.
3. Wybierz **pozycję Zastosuj**, a następnie zamknij **okienko** Filtry.

Wynikowy adres URL możesz zapisać w przeglądarce jako zakładkę, aby szybko wyświetlić listę przydzielonych Ci zdarzeń.

## <a name="resolve-an-incident"></a>Rozwiązywanie zdarzenia

Jeśli zdarzenie zostało rozwiązane, wybierz pozycję Rozwiąż  zdarzenie, aby przenieść przełącznik w prawo. Zauważ, że rozwiązanie zdarzenia rozwiązuje również wszystkie połączone i aktywne alerty związane z tym zdarzeniem.

Zdarzenie, które nie zostanie rozpoznane, jest wyświetlane jako **Aktywne**.

## <a name="set-the-classification-and-determination"></a>Ustawianie klasyfikacji i wyznaczania

Klasyfikacja zdarzenia określa, czy był to prawdziwy alert, czy fałszywy alert skonfigurowany z **pola Klasyfikacja** . 

Jeśli był to prawdziwy alert, należy również określić typ zagrożenia za pomocą pola **Wyznaczanie** . Określenie typu zagrożeń ułatwia zespołowi zabezpieczeń wykrywanie wzorców zagrożeń i działania w obronie przed nimi organizacji. 

## <a name="add-comments"></a>Dodawanie komentarzy

Za pomocą pola Komentarz możesz dodać wiele komentarzy do zdarzenia. Każdy komentarz zostanie dodany do historycznych zdarzeń zdarzenia. Komentarze i historię zdarzenia można wyświetlić za **pomocą linku** Komentarze i historia na **stronie Podsumowanie** .

## <a name="next-steps"></a>Następne kroki

W przypadku nowych zdarzeń rozpocznij [badanie.](investigate-incidents.md)

W przypadku zdarzeń w trakcie procesu kontynuuj [badanie](investigate-incidents.md).

W przypadku rozwiązanych zdarzeń przejdę [recenzję po zdarzeniu](first-incident-post.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Określanie priorytetów zdarzeń](incident-queue.md)
- [Badanie zdarzeń](investigate-incidents.md)
