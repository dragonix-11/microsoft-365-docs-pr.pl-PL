---
title: Jak za pomocą do Power Automate Connector skonfigurować Flow zdarzeń
ms.reviewer: ''
description: Za Ochrona punktu końcowego w usłudze Microsoft Defender Flow utwórz przepływ, który będzie wyzwalany za każdym razem, gdy w dzierżawie wystąpi nowe zdarzenie.
keywords: flow, obsługiwane api, api, microsoft flow, query, automation, power automate
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 63626978311b679d0f8b520e4b041d92942bd1fd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468000"
---
# <a name="how-to-use-power-automate-connector-to-set-up-a-flow-for-events"></a>Jak za pomocą do Power Automate Connector skonfigurować Flow zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Ochrona punktu końcowego w usłudze Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Chcesz doświadczyć Ochrona punktu końcowego w usłudze Microsoft Defender? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Automatyzowanie procedur zabezpieczeń to standardowe wymaganie dla każdego nowoczesnego centrum operacji zabezpieczeń (SOC, Security Operations Center). Aby zespoły SOC działały w najskuteczniejszy sposób, automatyzacja jest musi. Skorzystaj z Power Automate Microsoft Power Automate tworzenia zautomatyzowanych przepływów pracy i tworzenia end-to-end procedury automatyzacji w ciągu kilku minut. Aplikacja Microsoft Power Automate obsługuje różne łączniki, które zostały właśnie do tego celu zbudowane.  

Ten artykuł zawiera wskazówki dotyczące tworzenia automatyzacji wyzwalanych przez zdarzenie, takie jak utworzenie nowego alertu w dzierżawie. Interfejs Microsoft Defender API ma oficjalny Power Automate Connector z wieloma możliwościami. 

:::image type="content" source="images/api-flow-0.png" alt-text="Strona Akcje w portalu usługi Microsoft Defender 365" lightbox="images/api-flow-0.png" :::

> [!NOTE]
> Aby uzyskać więcej szczegółowych informacji na temat wymagań wstępnych licencjonowania łączników premium, zobacz [Licencjonowanie łączników premium](/power-automate/triggers-introduction#licensing-for-premium-connectors).

## <a name="usage-example"></a>Przykład użycia

W poniższym przykładzie pokazano sposób tworzenia reguły Flow która jest wyzwalana za każdym razem, gdy w dzierżawie występuje nowy alert. Będziesz mieć przewodnik na temat definiowania zdarzenia, które rozpoczyna przepływ, i co będzie podejmowane w przypadku wystąpienia wyzwalacza.  

1. Zaloguj się do [usługi Microsoft Power Automate](https://flow.microsoft.com).

2. Przejdź do **strony Moje przepływy** \> **New** \> **Automated-from blank (Nowe zautomatyzowane-z pustej**).

    :::image type="content" source="images/api-flow-1.png" alt-text="Okienko Nowy przepływ w obszarze elementu menu Moje przepływy w portalu usługi Microsoft Defender 365" lightbox="images/api-flow-1.png":::

3. Wybierz nazwę wyzwalacza, Flow wyzwalaczem "Microsoft Defender ATP Triggers", a następnie wybierz nowy wyzwalacz Alerty.

    :::image type="content" source="images/api-flow-2.png" alt-text=" Sekcja Wybierz wyzwalacz przepływu w portalu usługi Microsoft Defender 365" lightbox="images/api-flow-2.png" :::

Teraz istnieje błąd Flow który jest wyzwalany za każdym razem, gdy pojawia się nowy alert.

:::image type="content" source="images/api-flow-3.png" alt-text="Opis wyzwalacza" lightbox="images/api-flow-3.png":::

Teraz wystarczy wybrać kolejne kroki.
Na przykład możesz odizolować urządzenie, jeśli poziom ważności alertu jest wysoki, i wysłać wiadomość e-mail na ten temat.
Wyzwalacz alertu dostarcza tylko identyfikator alertu i identyfikator komputera. Możesz użyć łącznika, aby rozwinąć te jednostki.

### <a name="get-the-alert-entity-using-the-connector"></a>Uzyskiwanie encji alertu przy użyciu łącznika

1. Wybierz **pozycję Microsoft Defender ATP** , aby wybrać nowy krok.

2. Wybierz **pozycję Alerty — uzyskaj pojedynczy interfejs API alertów**.

3. Ustaw identyfikator **alertu** z ostatniego kroku jako **Wartość wejściowa**.

    :::image type="content" source="images/api-flow-4.png" alt-text="Okienko Alerty"  lightbox="images/api-flow-4.png":::

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>Wyizoluj urządzenie, jeśli poziom ważności alertu to Wysoka

1. Dodaj **warunek** jako nowy krok.

2. Sprawdź, czy ważność **alertu jest równa wysoka** .

   Jeśli tak, dodaj **akcję Microsoft Defender ATP — Odizolowanie** akcji komputera za pomocą identyfikatora komputera i komentarza.

    :::image type="content" source="images/api-flow-5.png" alt-text="Okienko Akcje"  lightbox="images/api-flow-5.png":::

3. Dodaj nowy krok, aby wysłać wiadomość e-mail na temat alertu i izolacji. Istnieje wiele łączników wiadomości e-mail, które są bardzo łatwe w użyciu, takich jak Outlook lub Gmail.

4. Zapisz swój przepływ.

Możesz również utworzyć przepływ według **harmonogramu,** który będzie uruchamiał zapytania zaawansowanego wyszukiwania i nie tylko!

## <a name="related-topic"></a>Temat pokrewny
- [Ochrona punktu końcowego w usłudze Microsoft Defender interfejsów API](apis-intro.md)
