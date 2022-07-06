---
title: Menedżer zgodności w Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Program Microsoft Purview Compliance Manager ułatwia organizacjom upraszczanie i automatyzowanie ocen ryzyka oraz sugeruje zalecane działania ułatwiające rozwiązanie problemów z ryzykiem.
ms.openlocfilehash: 74783c99873b76d3b3637947203bb58d4a656b13
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634748"
---
# <a name="microsoft-purview-compliance-manager"></a>Menedżer zgodności w Microsoft Purview

> [!TIP]
> *Czy wiesz, że możesz bezpłatnie wypróbować wersje premium wszystkich dziewięciu rozwiązań Usługi Microsoft Purview?* Skorzystaj z 90-dniowej wersji próbnej rozwiązań Purview, aby dowiedzieć się, jak niezawodne możliwości usługi Purview mogą pomóc organizacji spełnić jej potrzeby w zakresie zgodności. Microsoft 365 E3 i Office 365 E3 klienci mogą rozpocząć pracę w [centrum portal zgodności Microsoft Purview prób](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Dowiedz się więcej o [tym, kto może zarejestrować się i zapoznać się z postanowieniami dotyczącymi wersji próbnej](compliance-easy-trials.md).

**W tym artykule:** Dowiedz się, czym jest Menedżer zgodności, jak pomaga uprościć zgodność i zmniejszyć ryzyko oraz jego kluczowe składniki.

## <a name="what-is-compliance-manager"></a>Co to jest Menedżer zgodności?

[Microsoft Purview Compliance Manager](https://compliance.microsoft.com/compliancemanager) to funkcja w <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portal zgodności Microsoft Purview</a>, która ułatwia zarządzanie wymaganiami organizacji w zakresie zgodności z większą łatwością i wygodą. Menedżer zgodności może pomóc w całym procesie zapewniania zgodności, od tworzenia spisu zagrożeń związanych z ochroną danych po zarządzanie złożonością wdrażania mechanizmów kontroli, zachowanie aktualności z przepisami i certyfikatami oraz raportowanie do audytorów.

Obejrzyj poniższy film wideo, aby dowiedzieć się, w jaki sposób Menedżer zgodności może pomóc uprościć zarządzanie zgodnością w organizacji:
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4VdoO]

Menedżer zgodności pomaga uprościć zgodność i zmniejszyć ryzyko, zapewniając:

- Wstępnie utworzone oceny dla typowych standardów branżowych i regionalnych oraz przepisów lub niestandardowych ocen spełniających twoje unikatowe potrzeby w zakresie zgodności (dostępne oceny zależą od umowy licencyjnej; [dowiedz się więcej](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)).

- Funkcje przepływu pracy ułatwiające efektywne wykonywanie ocen ryzyka za pomocą jednego narzędzia.

- Szczegółowe wskazówki krok po kroku dotyczące sugerowanych działań ulepszeń, które pomogą Ci zachować zgodność ze standardami i przepisami, które są najbardziej istotne dla Twojej organizacji. W przypadku akcji zarządzanych przez firmę Microsoft zobaczysz szczegóły implementacji i wyniki inspekcji.

- Ocena zgodności oparta na ryzyku, która pomoże Ci zrozumieć stan zgodności, mierząc postęp w wykonywaniu akcji poprawy.

Na stronie przeglądu programu Compliance Manager przedstawiono bieżący wynik zgodności, który ułatwia sprawdzenie, co wymaga uwagi, oraz wskazówki dotyczące kluczowych akcji poprawy. Poniżej przedstawiono przykład strony przeglądu:

![Menedżer zgodności — pulpit nawigacyjny.](../media/compliance-manager-overview.png "Strona przeglądu programu Compliance Manager")

## <a name="understanding-your-compliance-score"></a>Omówienie oceny zgodności

Menedżer zgodności przyznaje punkty za ukończenie działań ulepszeń podjętych w celu zachowania zgodności z przepisami, standardami lub zasadami oraz łączy te punkty w ogólny wynik zgodności. Każda akcja ma inny wpływ na wynik w zależności od potencjalnego ryzyka. Wynik zgodności może pomóc określić priorytety akcji, na których należy się skupić, aby poprawić ogólną postawę zgodności.

Menedżer zgodności zapewnia wstępny wynik na podstawie punktu odniesienia ochrony danych platformy Microsoft 365. Ten punkt odniesienia to zestaw mechanizmów kontroli, które obejmują kluczowe przepisy i standardy dotyczące ochrony danych i ogólnego ładu danych.

##### <a name="learn-more"></a>Dowiedz się więcej

[Dowiedz się, jak jest obliczany wynik zgodności](compliance-score-calculation.md).

[Dowiedz się, jak pracować z akcjami poprawy](compliance-manager-improvement-actions.md).

## <a name="key-elements-controls-assessments-templates-improvement-actions"></a>Kluczowe elementy: kontrolki, oceny, szablony, akcje poprawy

Menedżer zgodności używa kilku elementów danych, aby ułatwić zarządzanie działaniami dotyczącymi zgodności. W miarę używania Menedżera zgodności do przypisywania, testowania i monitorowania działań związanych ze zgodnością warto mieć podstawową wiedzę na temat kluczowych elementów: kontrolek, ocen, szablonów i akcji ulepszania.

### <a name="controls"></a>Formantów

Kontrola jest wymaganiem rozporządzenia, standardu lub zasad. Definiuje ona sposób oceniania konfiguracji systemu, procesu organizacyjnego i zarządzania nimi oraz osób odpowiedzialnych za spełnienie określonego wymagania dotyczącego regulacji, standardu lub zasad.

Menedżer zgodności śledzi następujące typy kontrolek:

1. **Kontrolki zarządzane przez firmę Microsoft**: mechanizmy kontroli usług w chmurze firmy Microsoft, które firma Microsoft jest odpowiedzialna za implementację
2. **Kontrolki**: czasami nazywane kontrolkami zarządzanymi przez klienta, są to kontrolki implementowane i zarządzane przez organizację
3. **Kontrolki udostępnione**: są to kontrolki, za które odpowiedzialność za implementację ponoszą zarówno organizacja, jak i firma Microsoft

##### <a name="learn-more"></a>Dowiedz się więcej

[Monitorowanie postępu kontrolek](compliance-manager-assessments.md#monitor-assessment-progress-and-controls).

[Dowiedz się, jak Menedżer zgodności stale ocenia mechanizmy kontroli](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

### <a name="assessments"></a>Oceny

Ocena polega na grupowaniu mechanizmów kontroli na podstawie określonego rozporządzenia, normy lub zasad. Ukończenie działań w ramach oceny pomaga spełnić wymagania normy, regulacji lub prawa. Na przykład możesz mieć ocenę, która po wykonaniu wszystkich w nim akcji pomaga dostosować ustawienia platformy Microsoft 365 do wymagań iso 27001.

Oceny mają kilka składników:

- **Usługi w zakresie**: określony zestaw usług firmy Microsoft mających zastosowanie do oceny
- **Kontrolki zarządzane przez firmę Microsoft**: mechanizmy kontroli usług w chmurze firmy Microsoft, które firma Microsoft implementuje w Twoim imieniu
- **Kontrolki**: czasami nazywane kontrolkami zarządzanymi przez klienta, są to kontrolki implementowane i zarządzane przez organizację
- **Kontrolki udostępnione**: są to kontrolki, za które odpowiedzialność za implementację ponoszą zarówno organizacja, jak i firma Microsoft
- **Ocena**: pokazuje postęp w osiąganiu łącznej liczby możliwych punktów z akcji w ramach oceny, które są zarządzane przez organizację i firmę Microsoft

Podczas tworzenia ocen przypiszesz je do grupy. Grupy można skonfigurować w dowolny sposób, co jest najbardziej logiczne dla Twojej organizacji. Można na przykład grupować oceny według roku inspekcji, regionu, rozwiązania, zespołów w organizacji lub w inny sposób. Po utworzeniu grup możesz [filtrować pulpit nawigacyjny Programu Compliance Manager](compliance-manager-setup.md#filtering-your-dashboard-view) , aby wyświetlić wynik według co najmniej jednej grupy.

##### <a name="learn-more"></a>Dowiedz się więcej

[Twórz oceny i zarządzaj nimi w menedżerze zgodności](compliance-manager-assessments.md).

### <a name="templates"></a>Szablony

Menedżer zgodności udostępnia szablony ułatwiające szybkie tworzenie ocen. Możesz zmodyfikować te szablony, aby utworzyć ocenę zoptymalizowaną pod kątem twoich potrzeb. Możesz również utworzyć niestandardową ocenę, tworząc szablon z własnymi kontrolkami i akcjami. Na przykład możesz chcieć, aby szablon obejmował wewnętrzną kontrolę procesów biznesowych lub regionalny standard ochrony danych, który nie jest objęty jednym z naszych wstępnie utworzonych szablonów oceny 325+.

##### <a name="learn-more"></a>Dowiedz się więcej

[Wyświetl listę szablonów oceny dostarczonych przez menedżera zgodności](compliance-manager-templates-list.md).

[Uzyskaj szczegółowe instrukcje dotyczące tworzenia i modyfikowania szablonów dla ocen](compliance-manager-templates.md).

### <a name="improvement-actions"></a>Akcje ulepszania

Akcje poprawy ułatwiają scentralizowanie działań związanych ze zgodnością. Każda akcja poprawy zawiera zalecane wskazówki, które mają ułatwić dostosowanie do przepisów i standardów ochrony danych. Akcje poprawy można przypisać do użytkowników w organizacji w celu wykonywania zadań implementacji i testowania. W ramach akcji poprawy można również przechowywać dokumentację, notatki i aktualizacje stanu rekordów.

##### <a name="learn-more"></a>Dowiedz się więcej

[Aby zarządzać przepływem pracy zgodności, użyj akcji poprawy](compliance-manager-improvement-actions.md).

[Dowiedz się, jak akcje wpływają na wynik zgodności](compliance-score-calculation.md#action-types-and-points).

## <a name="supported-languages"></a>Obsługiwane języki

Menedżer zgodności jest dostępny w następujących językach:

- English
- Bahasa Indonezyjski
- Bahasa Malajski
- Chiński (uproszczony)
- Chiński (tradycyjny)
- Czech
- Danish
- Dutch
- Finnish
- French
- German
- Hebrew
- Hungarian
- Italian
- Japanese
- Korean
- Norweski
- Polish
- Portugalski (brazylijski)
- Russian
- Spanish
- Swedish
- Thai
- Turkish

## <a name="next-steps-set-up-and-customize"></a>Następne kroki: konfigurowanie i dostosowywanie

Dowiedz się, jak logować się, przypisywać uprawnienia i role, konfigurować ustawienia i personalizować widok pulpitu nawigacyjnego w [temacie Rozpoczynanie pracy z Menedżerem zgodności](compliance-manager-setup.md).

Następnie rozpocznij dostosowywanie Menedżera zgodności, aby zapewnić zgodność ze standardami branżowymi, które mają największe znaczenie dla Twojej organizacji, [konfigurując oceny](compliance-manager-assessments.md).

Aby zapewnić zgodność z przepisami dotyczącymi prywatności danych, opracowaliśmy przepływ pracy, który przeprowadzi Cię przez kompleksowy proces planowania i implementowania możliwości w usłudze Microsoft 365, w tym przy użyciu Menedżera zgodności. Aby uzyskać więcej informacji, zobacz [Deploy information protection for data privacy regulations with Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy). 
