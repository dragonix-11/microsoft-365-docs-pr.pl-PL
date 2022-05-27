---
title: Zarządzanie zdarzeniami w Microsoft 365 Defender
description: Dowiedz się, jak przypisać, zaktualizować stan,
keywords: zdarzenie, incydenty, analizowanie, reagowanie, alerty, skorelowane alerty, przypisywanie, aktualizowanie, stan, zarządzanie, klasyfikacja, microsoft, 365, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 9aa293a84f3bdca6988b1bf8437906f8b1cfbd39
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2022
ms.locfileid: "65740005"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Zarządzanie zdarzeniami w Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Dotyczy:**
- Microsoft 365 Defender

Zarządzanie zdarzeniami ma kluczowe znaczenie dla zapewnienia, że zdarzenia są nazwane, przypisane i oznakowane, aby zoptymalizować czas w przepływie pracy zdarzenia oraz szybciej zawierać zagrożenia i rozwiązywać je.

Zdarzeniami można zarządzać z poziomu **alertów & zdarzeń > zdarzeń** przy szybkim uruchomieniu portalu Microsoft 365 Defender ([security.microsoft.com](https://security.microsoft.com)). Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Strona Zdarzenia w portalu Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Oto sposoby zarządzania zdarzeniami:

- [Edytowanie nazwy zdarzenia](#edit-the-incident-name)
- [Dodawanie tagów zdarzeń](#add-incident-tags)
- [Przypisywanie zdarzenia do konta użytkownika](#assign-an-incident)
- [Rozwiąż te problemy](#resolve-an-incident)
- [Określ jego klasyfikację](#specify-the-classification)
- [Dodawanie komentarzy](#add-comments)

Zdarzeniami można zarządzać w okienku **Zarządzanie zdarzeniami** dla zdarzenia. Oto przykład.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Okienko Zarządzanie incydentami w portalu Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

To okienko można wyświetlić za pomocą linku **Zarządzaj zdarzeniem** na stronie:

- Okienko właściwości zdarzenia w kolejce zdarzeń.
- **Strona podsumowania** zdarzenia.

W przypadkach, gdy chcesz przenieść alerty z jednego zdarzenia do innego, możesz to zrobić również na **karcie Alerty** , tworząc w ten sposób większe lub mniejsze zdarzenie zawierające wszystkie odpowiednie alerty.

## <a name="edit-the-incident-name"></a>Edytowanie nazwy zdarzenia

Microsoft 365 Defender automatycznie przypisuje nazwę na podstawie atrybutów alertów, takich jak liczba punktów końcowych, których dotyczy problem, użytkowników, których dotyczy problem, źródła wykrywania lub kategorie. Dzięki temu można szybko zrozumieć zakres zdarzenia. Na przykład: *Zdarzenie wieloetapowe w wielu punktach końcowych zgłaszanych przez wiele źródeł.*

Nazwę zdarzenia można edytować z pola **Nazwa zdarzenia** w okienku **Zarządzanie zdarzeniem** .

> [!NOTE]
> Zdarzenia, które istniały przed wdrożeniem funkcji automatycznego nazewnictwa zdarzeń, zachowają swoją nazwę.

## <a name="add-incident-tags"></a>Dodawanie tagów zdarzeń

Możesz dodać tagi niestandardowe do zdarzenia, na przykład w celu oznaczania grupy zdarzeń o wspólnej cechie. Później można filtrować kolejkę zdarzeń pod kątem wszystkich zdarzeń, które zawierają określony tag.

Po rozpoczęciu wpisywania możesz wybrać opcję z listy wcześniej używanych i wybranych tagów.

## <a name="assign-an-incident"></a>Przypisywanie zdarzenia

Jeśli zdarzenie nie zostało jeszcze przypisane, możesz wybrać pole **Przypisz do i określić** konto użytkownika. Aby ponownie przypisać zdarzenie, usuń bieżące konto przypisania, wybierając znak "x" obok nazwy konta, a następnie zaznacz pole **Przypisz do** . Przypisanie własności zdarzenia przypisuje tę samą własność do wszystkich alertów z nim skojarzonych.

Listę zdarzeń przypisanych do Ciebie można uzyskać, filtrując kolejkę zdarzeń. 

1. W kolejce zdarzeń wybierz pozycję **Filtry**.
2. W sekcji **Przypisanie zdarzenia** **wyczyść pozycję Zaznacz wszystko** i wybierz pozycję **Przypisano do mnie**.
3. Wybierz pozycję **Zastosuj**, a następnie zamknij okienko **Filtry** .

Następnie możesz zapisać wynikowy adres URL w przeglądarce jako zakładkę, aby szybko wyświetlić listę przypisanych do Ciebie zdarzeń.

## <a name="resolve-an-incident"></a>Rozwiązywanie zdarzenia

Jeśli zdarzenie zostało skorygowane, wybierz pozycję **Rozwiąż zdarzenie** , aby przenieść przełącznik w prawo. Należy pamiętać, że rozwiązanie zdarzenia rozwiązuje również wszystkie połączone i aktywne alerty związane ze zdarzeniem.

Zdarzenie, które nie zostało rozwiązane, jest wyświetlane jako **Aktywne**.

## <a name="specify-the-classification"></a>Określanie klasyfikacji

W polu **Klasyfikacja** określasz, czy zdarzenie jest następujące:

- **Nie ustawiono** (wartość domyślna).
- **Wartość prawdziwie dodatnia** z typem zagrożenia. Użyj tej klasyfikacji w przypadku zdarzeń, które dokładnie wskazują rzeczywiste zagrożenie. Określenie typu zagrożenia ułatwia zespołowi ds. zabezpieczeń wyświetlanie wzorców zagrożeń i działanie w celu obrony organizacji przed nimi.
- **Działanie informacyjne, oczekiwane** z typem działania. Użyj opcji w tej kategorii, aby sklasyfikować zdarzenia na potrzeby testów zabezpieczeń, działania czerwonego zespołu i oczekiwanego nietypowego zachowania zaufanych aplikacji i użytkowników.
- **Wyniki fałszywie dodatnie** dla typów zdarzeń, które można określić, mogą być ignorowane, ponieważ są technicznie niedokładne lub wprowadzające w błąd.

Klasyfikowanie zdarzeń oraz określanie ich stanu i typu pomaga dostroić Microsoft 365 Defender w celu zapewnienia lepszego wykrywania w czasie.

Obejrzyj ten krótki film wideo, aby dowiedzieć się, jak używać klasyfikacji w celu zwiększenia wydajności klasyfikacji.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LHJq]

## <a name="add-comments"></a>Dodawanie komentarzy

Możesz dodać wiele komentarzy do zdarzenia za pomocą pola **Komentarz** . Każdy komentarz jest dodawany do historycznych wydarzeń zdarzenia. Komentarze i historia zdarzenia można wyświetlić za pomocą linku **Komentarze i historia** na stronie **Podsumowanie** .

## <a name="next-steps"></a>Następne kroki

W przypadku nowych zdarzeń rozpocznij [badanie](investigate-incidents.md).

W przypadku zdarzeń w procesie kontynuuj [badanie](investigate-incidents.md).

W przypadku rozwiązanych zdarzeń wykonaj [przegląd po zdarzeniu](first-incident-post.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Określanie priorytetów zdarzeń](incident-queue.md)
- [Badanie zdarzeń](investigate-incidents.md)
