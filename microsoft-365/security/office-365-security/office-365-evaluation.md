---
title: Oceń program Microsoft Defender pod Office 365
description: Defender for Office 365 in evaluation mode creates Defender for Office 365 email policies that log verdicts, such as malware, but don't act on messages.
keywords: oceń Office 365 usługę Microsoft Defender dla Office 365, ocenę usługi Office 365, wypróbuj usługę Office 365, Microsoft Defender, Microsoft Defender for Endpoint
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0f5d82e9baaca7209f8a91a7f1984aa38e3102e6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681749"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Oceń program Microsoft Defender pod Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Program Microsoft Defender for Office 365 oceny jest w publicznej wersji zapoznawczej. Ta wersja Preview jest dostępna bez umowy na poziomie usługi. Niektóre funkcje mogą nie być obsługiwane lub mogą mieć ograniczone możliwości.

Dokładne przeprowadzenie oceny produktu zabezpieczającego może ułatwić podejmowanie przeszłych decyzji dotyczących uaktualnień i zakupów. Warto wypróbować funkcje produktu zabezpieczającego, aby ocenić, jak może to ułatwić zespołowi ds. bezpieczeństwa wykonywanie codziennych zadań.

Środowisko [oceny programu Microsoft Defender for Office 365](defender-for-office-365.md) zostało zaprojektowane tak, aby wyeliminować złożoną konfigurację urządzenia i środowiska, dzięki czemu możesz skoncentrować się na ocenianiu możliwości usługi Microsoft Defender dla systemu Office 365. W trybie oceny wszystkie wiadomości wysyłane do Exchange Online można ocenić bez wskazania rekordów MX firmie Microsoft. Ta funkcja dotyczy tylko ochrony poczty e-mail i nie dotyczy Office klientów, takich jak word, SharePoint, czy Teams.

Jeśli nie masz jeszcze licencji obsługującej program Microsoft Defender dla systemu Office 365, możesz rozpocząć bezpłatną [30-dniową](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) ocenę i przetestować możliwości w portalu Microsoft 365 Defender w <https://security.microsoft.com>witrynie . Będziesz mieć możliwość szybkiej skonfigurowania tej opcji i w razie potrzeby możesz ją łatwo wyłączyć.

> [!NOTE]
> Jeśli jesteś w portalu usługi Microsoft 365 Defender    <https://security.microsoft.com>pod adresem , możesz uruchomić usługę Defender for Office 365 evaluation tutaj: Zasady współpracy z pocztą e-mail **&** \> **&** \> \> Tryb oceny zagrożeń reguł w sekcji Inne. Aby przejść bezpośrednio do strony Tryb **oceny**, użyj .<https://security.microsoft.com/atpEvaluation>

## <a name="how-the-evaluation-works"></a>Jak działa ocena

Defender for Office 365 in evaluation mode creates Defender for Office 365 email policies that log verdicts, such as malware, but don't act on messages. Nie musisz zmieniać konfiguracji rekordu MX.

W trybie oceny Sejf [załączniki](safe-attachments.md), linki [Sejf](safe-links.md) i analiza skrzynek pocztowych w zasadach [](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ochrony przed komputerami są ustawiane w Twoim imieniu. Wszystkie zasady usługi Defender Office 365 są tworzone w tle w trybie niewymuzywu i nie są widoczne dla Ciebie.

W ramach konfiguracji tryb oceny konfiguruje również rozszerzone [filtrowanie](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) łączników (nazywane również _pomiń na liście_). Ta konfiguracja zwiększa dokładność filtrowania, zachowując informacje o adresie IP i nadawcy, które w przeciwnym razie zostaną utracone, gdy poczta przechodzi przez bramę zabezpieczeń poczty e-mail (ESG) przed usługą Defender for Office 365. Ulepszone filtrowanie łączników zwiększa również dokładność filtrowania istniejących zasad ochrony przed spamem i wyłudzaniem informacji Exchange Online Protection (EOP).

Ulepszone filtrowanie łączników zwiększa dokładność filtrowania, ale może zmienić dostarczenie niektórych wiadomości, jeśli masz ESG przed programem Defender for Office 365 i obecnie nie pomijasz filtrowania usługi EOP. Wpływ jest ograniczony do zasad EOP. Defender for Office 365 policies set in part of the evaluation are created in non-enforcement mode. Aby zminimalizować potencjalny wpływ na produkcję, można pominąć większość filtrowania usługi EOP, tworząc regułę przepływu poczty (z znaną również regułą transportu) w celu ustawienia poziomu ufności filtru spamu dla wiadomości na -1. Aby [uzyskać szczegółowe informacje, zobacz](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) Ustawianie poziomu ufności filtru spamu w wiadomościach w programie Exchange Online użyciu reguł przepływu poczty e-mail.

Po skonfigurowaniu trybu oceny będziesz mieć dzienny raport z danymi do 90 dni, który będzie określać wiadomości, które zostałyby zablokowane, jeśli zasady zostałyby zaimplementowane (na przykład usuwanie, wysyłanie do wiadomości-śmieci, kwarantanna). Raporty są generowane dla wszystkich wykrywanie usługi Defender Office 365 i EOP. Raporty są agregowane według technologii wykrywania (na przykład personifikacji) i można je filtrować według przedziału czasu. Ponadto można tworzyć raporty wiadomości na żądanie w celu utworzenia niestandardowych tabel przestawnych lub w celu utworzenia bardziej dogłębnych wiadomości za pomocą Eksploratora.

W uproszczonym interfejsie użytkownika możesz skoncentrować się na:

- Uruchamianie oceny
- Uzyskiwanie szczegółowego raportu
- Analizowanie raportu pod celu jego działania
- Prezentowanie wyniku oceny

## <a name="before-you-begin"></a>Przed rozpoczęciem

### <a name="licensing"></a>Licencjonowanie

Aby uzyskać dostęp do oceny, musisz spełniać wymagania licencyjne. Dowolna z następujących licencji będzie działać:

- Microsoft Defender dla Office 365 Plan 1
- Microsoft Defender dla Office 365 Plan 2
- Microsoft 365 E5, Zabezpieczenia platformy Microsoft 365 E5
- Office 365 E5

Jeśli nie masz jednej z tych licencji, musisz uzyskać licencję próbną.

#### <a name="trial"></a>Wersja próbna

Aby uzyskać licencję wersji próbnej usługi Microsoft Defender dla usługi Office 365, musisz mieć rolę administratora rozliczeń  lub administratora **globalnego**. Poproś o uprawnienia osoby pełniejejce rolę administratora globalnego. [Informacje o subskrypcjach i licencjach](../../commerce/licenses/subscriptions-and-licenses.md)

Po uzyskaniu odpowiedniej roli zalecaną ścieżką jest uzyskanie licencji wersji próbnej programu Microsoft Defender dla programu Office 365 (plan 2) w sklepie centrum administracyjne platformy Microsoft 365, a następnie <https://admin.microsoft.com>  \> przejdź do tematu Zakup rozliczeń usług, a następnie znajdź i wybierz program Microsoft Defender dla programu Office 365 (plan 2) w wersji próbnej. Aby przejść bezpośrednio do strony wersji próbnej, <https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)> użyj wersji próbnej Ta wersja próbna obejmuje 30-dniową bezpłatną wersję próbną dla 25 licencji.

Będziesz mieć 30-dniowy okres z ocenymi, aby monitorować zaawansowane zagrożenia i raportować na ich temat. Będziesz także mieć możliwość zakupu płatnej subskrypcji, jeśli chcesz uzyskać pełną wersję programu Defender, Office 365 funkcje.

### <a name="roles"></a>Role

**Exchange Online są wymagane** do skonfigurowania usługi Defender dla Office 365 w trybie oceny. Przypisanie Microsoft 365 administratora zabezpieczeń lub zgodności nie będzie działać.

- [Informacje o uprawnieniach w aplikacji Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Informacje o przypisywaniu ról administratora](../../admin/add-users/assign-admin-roles.md)

Potrzebne są następujące role:

|Zadanie|Rola (w Exchange Online)|
|---|---|
|Uzyskaj bezpłatną wersję próbną lub kup program Microsoft Defender dla Office 365 (plan 2)|Rola administratora rozliczeń LUB rola administratora globalnego|
|Tworzenie zasad oceny|Rola zdalnej i zaakceptowanych domen; Rola administratora zabezpieczeń|
|Edytowanie zasad oceny|Rola zdalnej i zaakceptowanych domen; Rola administratora zabezpieczeń|
|Usuwanie zasad oceny|Rola zdalnej i zaakceptowanych domen; Rola administratora zabezpieczeń |
|Wyświetlanie raportu oceny|Rola administratora zabezpieczeń LUB rola czytnika zabezpieczeń|

### <a name="enhanced-filtering-for-connectors"></a>Ulepszone filtrowanie łączników

Zasady Exchange Online Protection, takie jak ochrona poczty masowej i spamu, pozostaną takie same. Jednak ocena zostanie w trybie rozszerzonego filtrowania dla łączników, co może mieć wpływ na przepływ poczty e-mail i zasady Exchange Online Protection o ile nie zostaną pominięte.

Ulepszone filtrowanie łączników umożliwia dzierżawom korzystanie z ochrony przed fałszerami. Ochrona przed fałszowaniem nie jest obsługiwana, jeśli korzystasz z bramy zabezpieczeń poczty e-mail (ESG) bez włączonego rozszerzonego filtrowania dla łączników.

### <a name="urls"></a>Adresy URL

Adresy URL będą detonowane podczas przepływu poczty. Jeśli nie chcesz detonować określonych adresów URL, odpowiednio zarządzaj listą dozwolonych adresów URL. Aby [uzyskać szczegółowe informacje, zobacz Zarządzanie listą zezwalania/blokowania](tenant-allow-block-list.md) dzierżawy.

Linki adresów URL w treści wiadomości e-mail nie będą zawijać się, aby mniej wpłynąć na klientów.

### <a name="email-routing"></a>Routing poczty e-mail

Przygotuj odpowiednie szczegóły, które będą potrzebne do skonfigurowania sposobu, w jaki poczta e-mail jest obecnie rozsyłana, łącznie z nazwą łącznika ruchu przychodzącego, który rozsyła pocztę. Jeśli tylko korzystasz z Exchange Online Protection, nie będziesz mieć łącznika. [Informacje na temat przepływu poczty e-mail i routingu poczty e-mail](/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Obsługiwane scenariusze routingu poczty e-mail obejmują:

- **Partner** z innej firmy i/lub rozwiązanie lokalne usługodawca: Łącznik ruchu przychodzącego, który chcesz ocenić, korzysta z dostawcy innego producenta i/lub korzystasz z rozwiązania do zabezpieczenia poczty e-mail lokalnie.
- **Microsoft Exchange Online informacji**: Dzierżawa, którą chcesz ocenić, korzysta Office 365 zabezpieczeń poczty e-mail, a rekord poczty e-mail Exchange (MX) wskazuje firmę Microsoft.

### <a name="email-security-gateway"></a>Brama zabezpieczeń poczty e-mail

Jeśli używasz innej bramy zabezpieczeń poczty e-mail (ESG), musisz znać nazwę dostawcy. Jeśli korzystasz z lokalnej sieci ESG lub innych dostawców, których nie obsługujesz, musisz znać publiczne adresy IP tych urządzeń.

Obsługiwani partnerzy innej firmy to:

- Barracuda
- IronPort
- Mimecast
- Punkt kontrolny
- Sophos
- Do tej 20
- Trend Micro

### <a name="scoping"></a>Określanie zakresu

Będzie można zawęzać ocenę do łącznika ruchu przychodzącego. Jeśli nie skonfigurowano łącznika, zakres oceny umożliwi administratorom zbieranie danych od dowolnego użytkownika w dzierżawie na ocenę usługi Defender pod Office 365.

## <a name="get-started-with-the-evaluation"></a>Wprowadzenie do oceny

Znajdź w portalu programu Microsoft Defender Office 365 kartę konfigurowanie oceny w portalu Microsoft 365 Defender od następujących punktów dostępu:

- **Punkty końcowe** \> **Zarządzanie lukami w zabezpieczeniach** \> **Pulpit nawigacyjny** (<https://security.microsoft.com/tvm_dashboard>)
- **Współpraca za & e-mail** \> **Zasady & reguł** \> **Zasady zagrożeń** (<https://security.microsoft.com/threatpolicy>)
- **Raporty** \> **Współpraca za & e-mail** \> **Raporty & e-mail** (<https://security.microsoft.com/emailandcollabreport>)

## <a name="setting-up-the-evaluation"></a>Konfigurowanie oceny

Po rozpoczęciu procesu konfiguracji oceny będziesz mieć dwie opcje routingu. W zależności od konfiguracji routingu poczty i potrzeb oceny w organizacji możesz wybrać, czy korzystasz z usługi innej firmy i(lub lokalnej), czy usługodawca tylko Microsoft Exchange Online.

- Jeśli korzystasz z usług partnera innej firmy i/lub lokalnego usługodawca, musisz wybrać nazwę dostawcy z menu rozwijanego. Podaj inne szczegóły dotyczące łącznika.

- Zaznacz **Microsoft Exchange Online**, jeśli rekord MX wskazuje firmę Microsoft i masz Exchange Online pocztową.

Przejrzyj ustawienia i w razie potrzeby je edytuj. Następnie wybierz pozycję **Utwórz ocenę**. Powinien zostać wyświetlony komunikat z potwierdzeniem informujący, że konfiguracja została ukończona.

Raport oceny usługi Microsoft Defender Office 365 jest generowany raz dziennie. Może upłynieć do 24 godzin, aż dane zostaną wypełnione.

### <a name="exchange-mail-flow-rules-optional"></a>Exchange przepływu poczty e-mail (opcjonalne)

Jeśli masz istniejącą bramę, włączenie trybu oceny spowoduje aktywowanie funkcji rozszerzonego filtrowania dla łączników. Ta funkcja zwiększa dokładność filtrowania, zmieniając adres IP przychodzącego nadawcy. Ta funkcja może zmienić werdykty filtrów i jeśli nie pomijasz Exchange Online Protection, może to zmienić dostarczenie niektórych wiadomości. W takim przypadku możesz chcieć tymczasowo pominąć filtrowanie, aby przeanalizować skutki. Aby pominąć filtrowanie, w centrum administracyjnym programu Exchange (EAC) <https://admin.exchange.microsoft.com/#/transportrules> utwórz regułę przepływu poczty e-mail, która będzie ustawiać 1 SCL wiadomości (jeśli jeszcze jej nie masz). Aby uzyskać instrukcje, zobacz Ustawianie poziomu ufności filtru spamu [(SCL)](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) w wiadomościach w Exchange Online.

## <a name="evaluate-capabilities"></a>Ocenianie możliwości

Po wygenerowaniu raportu oceny sprawdź, ile zaawansowanych linków do zagrożeń, zaawansowanych załączników zagrożeń i potencjalnych personifikacji zidentyfikowano w wiadomościach e-mail i obszarach roboczych współpracy w organizacji.

Po wygaśnięciu wersji próbnej możesz nadal korzystać z raportu przez 90 dni. Nie będą jednak zbierane żadne dodatkowe informacje. Jeśli chcesz nadal korzystać z programu Microsoft Defender dla systemu Office 365 po wygaśnięciu wersji próbnej, kup płatną subskrypcję usługi [Microsoft Defender dla programu Office 365 (plan 2).](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA).

W dowolnym momencie **możesz przejść Ustawienia** zaktualizować routing lub wyłączyć ocenę. Należy jednak ponownie przejść przez ten sam proces instalacji, jeśli zdecydujesz się kontynuować ocenę po jej wyłączeniach.

## <a name="provide-feedback"></a>Opinie

Twoja opinia pomoże nam lepiej chronić Twoje środowisko przed zaawansowanymi atakami. Podziel się swoimi doświadczeniami i analizami możliwości produktu i wyników oceny.

Wybierz **pozycję Opinie** , aby przekazać nam swoją opinię.
