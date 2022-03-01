---
title: Jak za pomocą do Power Automate Connector skonfigurować Flow zdarzeń
ms.reviewer: ''
description: Użyj programu Microsoft Defender for Endpoint Flow łącznika, aby utworzyć przepływ, który będzie wyzwalany za każdym razem, gdy w dzierżawie wystąpi nowe zdarzenie.
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
ms.openlocfilehash: fdb3876de6f74c95858dee01aba9615198282b16
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010428"
---
# <a name="how-to-use-power-automate-connector-to-set-up-a-flow-for-events"></a>Jak za pomocą do Power Automate Connector skonfigurować Flow zdarzeń

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Chcesz mieć dostęp do programu Microsoft Defender dla punktu końcowego? [Zarejestruj się, aby korzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


Automatyzowanie procedur zabezpieczeń to standardowe wymaganie dla każdego nowoczesnego centrum operacji zabezpieczeń (SOC, Security Operations Center). Aby zespoły SOC działały w najskuteczniejszy sposób, automatyzacja jest musi. Skorzystaj z Power Automate Microsoft Power Automate tworzenia zautomatyzowanych przepływów pracy i tworzenia end-to-end procedury automatyzacji w ciągu kilku minut. Aplikacja Microsoft Power Automate obsługuje różne łączniki, które zostały właśnie do tego celu zbudowane.  

Ten artykuł zawiera wskazówki dotyczące tworzenia automatyzacji wyzwalanych przez zdarzenie, na przykład utworzenie nowego alertu w dzierżawie. Interfejs Microsoft Defender API ma oficjalny Power Automate Connector z wieloma możliwościami. 



:::image type="content" alt-text="Obraz poświadczeń edycji1." source="images/api-flow-0.png":::

> [!NOTE]
> Aby uzyskać więcej szczegółowych informacji na temat wymagań wstępnych licencjonowania łączników premium, zobacz [Licencjonowanie łączników premium](/power-automate/triggers-introduction#licensing-for-premium-connectors).


## <a name="usage-example"></a>Przykład użycia

W poniższym przykładzie pokazano sposób tworzenia reguły Flow która jest wyzwalana za każdym razem, gdy w dzierżawie występuje nowy alert. Będziesz mieć przewodnik na temat definiowania zdarzenia, które rozpoczyna przepływ, i co będzie podejmowane w przypadku wystąpienia wyzwalacza.  

1. Zaloguj się do [usługi Microsoft Power Automate](https://flow.microsoft.com).

2. Przejdź do **strony Moje przepływy** \> **New** \> **Automated-from blank (Nowe zautomatyzowane-z pustej**).

    :::image type="content" alt-text="Obraz poświadczeń edycji2." source="images/api-flow-1.png":::

3. Wybierz nazwę wyzwalacza, Flow wyzwalaczem "Microsoft Defender ATP Triggers", a następnie wybierz nowy wyzwalacz Alerty.

    :::image type="content" alt-text="Obraz poświadczeń edycji3." source="images/api-flow-2.png":::

Teraz istnieje błąd Flow który jest wyzwalany za każdym razem, gdy pojawia się nowy alert.

:::image type="content" alt-text="Obraz poświadczeń edycji4." source="images/api-flow-3.png":::

Teraz wystarczy wybrać kolejne kroki.
Na przykład możesz odizolować urządzenie, jeśli poziom ważności alertu jest wysoki, i wysłać wiadomość e-mail na ten temat.
Wyzwalacz alertu dostarcza tylko identyfikator alertu i identyfikator komputera. Możesz użyć łącznika, aby rozwinąć te jednostki.

### <a name="get-the-alert-entity-using-the-connector"></a>Uzyskiwanie encji alertu przy użyciu łącznika

1. Wybierz **pozycję Microsoft Defender ATP** , aby wybrać nowy krok.

2. Wybierz **pozycję Alerty — uzyskaj pojedynczy interfejs API alertów**.

3. Ustaw identyfikator **alertu** z ostatniego kroku jako **Wartość wejściowa**.

    :::image type="content" alt-text="Obraz poświadczeń edycji5." source="images/api-flow-4.png" lightbox="images/api-flow-4.png":::

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>Wyizoluj urządzenie, jeśli poziom ważności alertu to Wysoka

1. Dodaj **warunek** jako nowy krok.

2. Sprawdź, czy ważność **alertu jest równa wysoka** .

   Jeśli tak, dodaj **akcję Microsoft Defender ATP — Odizolowanie** akcji komputera za pomocą identyfikatora komputera i komentarza.

    :::image type="content" alt-text="Obraz poświadczeń edycji6." source="images/api-flow-5.png" lightbox="images/api-flow-5.png":::

3. Dodaj nowy krok, aby wysłać wiadomość e-mail na temat alertu i izolacji. Istnieje wiele łączników wiadomości e-mail, które są bardzo łatwe w użyciu, takich jak Outlook lub Gmail.

4. Zapisz swój przepływ.

Możesz również utworzyć przepływ według **harmonogramu,** który będzie uruchamiał zapytania zaawansowanego wyszukiwania i nie tylko!

## <a name="related-topic"></a>Temat pokrewny
- [Interfejsy API programu Microsoft Defender dla punktów końcowych](apis-intro.md)
