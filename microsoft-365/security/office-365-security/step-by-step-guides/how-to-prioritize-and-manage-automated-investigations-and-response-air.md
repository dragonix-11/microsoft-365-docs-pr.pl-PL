---
title: Jak nadać priorytet zautomatyzowanym badaniom i reagowaniu (AIR) i zarządzać nimi.
description: Instrukcje analizowania i zatwierdzania akcji AIR bezpośrednio z Centrum akcji. Po wyzwoleniu alertów automatyczne badanie i reagowanie (AIR) określa zakres wpływu zagrożenia w organizacji i udostępnia zalecane akcje korygowania.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 3a26f20946be39074a18df1b09d392464193599c
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842526"
---
# <a name="prioritize-and-manage-automated-investigations-and-response-air"></a>Określanie priorytetów i zarządzanie zautomatyzowanymi badaniami i odpowiedziami (AIR)

Zautomatyzowane badanie i reagowanie (AIR) pozwala zaoszczędzić czas i nakład pracy zespołu ds. operacji zabezpieczeń.

- Po wyzwoleniu alertów zautomatyzowane badanie określi zakres wpływu zagrożenia w organizacji i zapewni zalecane akcje korygowania.
- Zespoły ds. zabezpieczeń mogą zaoszczędzić czas, wykorzystując automatyzację AIR, aby zmniejszyć potrzebę ręcznego wyszukiwania zagrożeń.
- Te badania mogą identyfikować wiadomości e-mail, które nie zostały oczyszczone przez automatyczne przeczyszczanie o zerowej godzinie (ZAP) lub inne korygowanie.
- Badania AIR identyfikują również konfiguracje skrzynek pocztowych, które mogą być ryzykowne lub wskazują na naruszona skrzynkę pocztową.

Akcje badania (i badania) są dostępne z kilku punktów w witrynie Microsoft Security Portal: za pośrednictwem *zdarzeń*, *alertów* lub *centrum akcji*. Którego użycia używają administratorzy, zależy od przepływu pracy, który realizuje administrator.

## <a name="why-use-the-action-center-workflow"></a>Dlaczego warto używać przepływu pracy centrum akcji

Ponieważ automatyczne badania dotyczące zawartości *funkcji współpracy & poczty e-mail* skutkują werdyktami, takimi jak *Złośliwe* lub *Podejrzane*, są tworzone pewne akcje korygowania. Sugerowane akcje korygowania nie są wykonywane automatycznie. SecOps musi przejść do każdego badania, aby *zatwierdzić* te sugerowane akcje. W *Centrum akcji* wszystkie oczekujące akcje są agregowane w celu szybkiego zatwierdzenia.

## <a name="what-youll-need"></a>Co będzie potrzebne

- Ochrona usługi Office 365 w usłudze Microsoft Defender plan 2 lub nowszy
- Wystarczające uprawnienia (czytelnik zabezpieczeń, operacje zabezpieczeń lub administrator zabezpieczeń oraz rola [wyszukiwania i przeczyszczania](../permissions-microsoft-365-security-center.md) )

## <a name="steps-to-analyze-and-approve-air-actions-directly-from-the-action-center"></a>Kroki analizowania i zatwierdzania akcji AIR bezpośrednio z Centrum akcji

1. Przejdź do [portalu Microsoft 365 Defender](https://security.microsoft.com/action-center) i zaloguj się.
2. Gdy centrum akcji jest ładowane, filtruj i ustalaj priorytety, klikając kolumny w celu sortowania akcji lub naciskając pozycję **Filtry** , aby zastosować filtr, taki jak *typ jednostki* (dla określonego adresu URL) lub typ akcji (np. wiadomość e-mail usuwania nietrwałego).
3. Po kliknięciu akcji zostanie otwarte okno wysuwane. Zostanie on wyświetlony po prawej stronie ekranu do przeglądu.
4. Aby uzyskać więcej informacji o tym, dlaczego jest żądana akcja, wybierz pozycję **Otwórz stronę badania** w wysuwanym oknie, aby dowiedzieć się więcej o badaniu lub alertach połączonych z tą akcją. (Administratorzy mogą również zatwierdzać akcje widoczne na stronie badania, wybierając kartę *Oczekujące akcje* ).
5. W przeciwnym razie wybierz pozycję **Zatwierdź** , aby wykonać zalecaną akcję bezpośrednio z Centrum akcji.
6. Odrzuć akcję, jeśli uznasz, że jest ona niepotrzebna.

## <a name="check-air-history"></a>Sprawdzanie historii AIR

1. Przejdź do [portalu Microsoft 365 Defender](https://security.microsoft.com) i zaloguj się.
2. W okienku nawigacji po lewej stronie rozwiń węzeł **Akcja & przesłania,** a następnie kliknij pozycję **Centrum akcji**.
3. Po załadowaniu centrum akcji naciśnij kartę **Historia** .
4. Przejrzyj historię środowiska AIR, w tym podjęte decyzje, źródło działania i administratora, który podjął decyzję, jeśli jest to konieczne.

## <a name="more-information"></a>Więcej informacji

[Wyświetlanie wyników zautomatyzowanego badania w Microsoft 365 — Office 365 | Microsoft Docs](../air-view-investigation-results.md)

[Dowiedz się więcej o zatwierdzaniu i odrzucaniu oczekujących akcji na stronie Badanie](../air-review-approve-pending-completed-actions.md)