---
title: Microsoft Purview — rozwiązania dotyczące zgodności i ryzyka
description: Skorzystaj z tego artykułu, aby dowiedzieć się więcej o rozwiązaniach dotyczących ryzyka i zgodności usługi Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, zgodność, rozwiązania
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: m365-security-compliance
ms.openlocfilehash: 96b1efdddcf8a0b2e1034c392c27f160137379de
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635663"
---
# <a name="microsoft-purview-risk-and-compliance-solutions"></a>Microsoft Purview — rozwiązania dotyczące zgodności i ryzyka

Rozwiązania dotyczące ryzyka i zgodności usługi [Microsoft Purview](/purview/purview) pomagają zarządzać danymi i monitorować je, chronić informacje, minimalizować ryzyko związane ze zgodnością i spełniać wymagania prawne. Ten artykuł pomoże Ci dowiedzieć się więcej o rozwiązaniach dotyczących ryzyka i zgodności usługi Microsoft Purview oraz szybko rozpocząć wdrażanie tych rozwiązań w celu spełnienia określonych potrzeb dotyczących zgodności w organizacji.

## <a name="protect-sensitive-data-across-clouds-apps-and-devices"></a>Ochrona poufnych danych w chmurach, aplikacjach i na urządzeniach

Strategia ochrony informacji powinna być oparta na potrzebach biznesowych, ale każda organizacja musi chronić niektóre lub wszystkie dane. Skorzystaj z możliwości [Microsoft Purview Information Protection](/microsoft-365/compliance/information-protection) (dawniej Microsoft Information Protection), aby ułatwić odnajdywanie, klasyfikowanie, ochronę i zarządzanie poufnymi informacjami wszędzie tam, gdzie się znajdują lub podróżują.

### <a name="know-your-data"></a>Poznaj swoje dane

Informacje znajdują się we wszystkich usługach platformy Microsoft 365 i w środowisku lokalnym. Określenie, które elementy są poufne i uzyska wgląd w sposób ich użycia, ma kluczowe znaczenie dla twojej praktyki ochrony informacji. Usługa Microsoft Purview obejmuje:

- [Typy informacji poufnych](/microsoft-365/compliance/sensitive-information-type-learn-about) umożliwiające identyfikowanie poufnych elementów przy użyciu wbudowanych lub niestandardowych wyrażeń regularnych lub funkcji.
- [Klasyfikatory z możliwością trenowania](/microsoft-365/compliance/classifier-learn-about) do identyfikowania poufnych elementów przy użyciu przykładów danych, które Cię interesują, zamiast identyfikować elementy w elemencie.
- [Klasyfikacja danych](/microsoft-365/compliance/data-classification-overview) zapewnia graficzną identyfikację elementów w organizacji, które mają etykietę poufności, etykietę przechowywania lub zostały sklasyfikowane oraz akcje, które podejmują użytkownicy

### <a name="protect-your-data"></a>Chroń swoje dane

Istnieje wiele możliwości, których można użyć z rozwiązania Microsoft Purview Information Protection, aby chronić dane, niezależnie od tego, gdzie są przechowywane i dostępne. Jednak etykiety poufności to podstawowa funkcja, która zapewnia akcje ochrony i współdziała z innymi rozwiązaniami i możliwościami usługi Purview.

Etykiety poufności zapewniają użytkownikom i administratorom wgląd w poufność używanych danych, a same etykiety mogą stosować akcje ochrony, które obejmują szyfrowanie, ograniczenia dostępu i oznaczenia wizualne. Aby uzyskać więcej informacji na temat zakresu obsługiwanych scenariuszy etykietowania, zobacz sekcję [Typowe scenariusze etykiet poufności](/microsoft-365/compliance/get-started-with-sensitivity-labels#common-scenarios-for-sensitivity-labels) w dokumentacji wprowadzającej. Aby uzyskać więcej informacji na temat etykiet poufności, zobacz [Dowiedz się więcej o etykietach poufności](/microsoft-365/compliance/sensitivity-labels).

### <a name="prevent-data-loss"></a>Zapobieganie utracie danych

Niezamierzone udostępnianie poufnych elementów może spowodować szkodę finansową organizacji i może spowodować naruszenie przepisów prawnych i wykonawczych. [Ochrona przed utratą danych w Microsoft Purview](/microsoft-365/compliance/dlp-learn-about-dlp) może pomóc chronić organizację przed niezamierzonym lub przypadkowym udostępnianiem poufnych informacji zarówno wewnątrz organizacji, jak i poza nią. W zasadach ochrony przed utratą danych:

- Zdefiniuj informacje poufne, które chcesz monitorować, takie jak dane finansowe, zdrowotne, medyczne i dane dotyczące prywatności.
- Gdzie monitorować, na przykład usługi Platformy Microsoft 365 lub urządzenia z systemem Windows i macOS.
- Warunki, które muszą być dopasowane do zasad, które mają być stosowane do elementu, takich jak elementy zawierające kartę kredytową, prawo jazdy lub numery ubezpieczenia społecznego.
- Akcje, które należy wykonać po znalezieniu dopasowania, takie jak inspekcja, blokują działanie i blokują działanie za pomocą przesłonięcia.

### <a name="manage-your-data-lifecycle"></a>Zarządzanie cyklem życia danych

[zarządzanie cyklem życia danych Microsoft Purview](/microsoft-365/compliance/manage-data-governance#microsoft-purview-data-lifecycle-management) (dawniej Microsoft Information Governance) udostępnia narzędzia i możliwości przechowywania i usuwania zawartości w programach Exchange, SharePoint, OneDrive, Grupy Microsoft 365, Teams i Yammer. Przechowywanie i usuwanie wiadomości e-mail, dokumentów i wiadomości jest często potrzebne w celu spełnienia wymagań dotyczących zgodności i przepisów. Jednak usunięcie zawartości, która nie ma już wartości biznesowej, zmniejsza również obszar ataków.

Aby uzyskać więcej informacji, zobacz [Informacje o zarządzaniu cyklem życia danych](/microsoft-365/compliance/data-lifecycle-management).

### <a name="encrypt-your-data-and-control-your-encryption-keys"></a>Szyfrowanie danych i kontrola kluczy szyfrowania

[Szyfrowanie](/microsoft-365/compliance/encryption) jest ważną częścią strategii ochrony plików i ochrony informacji. Proces szyfrowania koduje dane (nazywane zwykłego tekstu) do szyfru. W przeciwieństwie do zwykłego tekstu, szyfrowanie nie może być używane przez osoby lub komputery, chyba że i dopóki nie zostanie odszyfrowany szyfrowany. Odszyfrowywanie wymaga klucza szyfrowania, który mają tylko autoryzowani użytkownicy. Szyfrowanie pomaga zagwarantować, że tylko autoryzowani adresaci mogą odszyfrować twoją zawartość.

[Podwójne szyfrowanie kluczy w usłudze Microsoft Purview](/microsoft-365/compliance/double-key-encryption) pomaga zabezpieczyć najbardziej poufne dane, które podlegają najsurowszym wymaganiom ochrony. [Klucz klienta usługi Microsoft Purview](/microsoft-365/compliance/customer-key-overview) pomaga spełnić wymagania prawne lub zgodności dotyczące kontrolowania kluczy głównych. Jawnie autoryzujesz usługi Platformy Microsoft 365 do używania kluczy szyfrowania w celu dostarczania usług w chmurze o wartości dodanej, takich jak elektroniczne wykrywanie, ochrona przed złośliwym oprogramowaniem, ochrona przed spamem, indeksowanie wyszukiwania itd.

## <a name="identify-data-risks-and-manage-regulatory-compliance-requirements"></a>Określanie ryzyka związanego z danymi i zarządzanie wymogami zgodności z przepisami

Ryzyko związane z wewnętrznymi informacjami to jedna z najważniejszych kwestii specjalistów ds. bezpieczeństwa i zgodności w nowoczesnym miejscu pracy. Badania branżowe wykazały, że ryzyko wewnętrzne jest często związane z określonymi zdarzeniami lub działaniami użytkowników. Ochrona organizacji przed tymi zagrożeniami może być trudna do zidentyfikowania i trudna do wyeliminowania. Zagrożenia wewnętrzne obejmują luki w zabezpieczeniach w różnych obszarach i mogą powodować poważne problemy dla organizacji, od utraty własności intelektualnej po nękanie w miejscu pracy i nie tylko.

Usługa Microsoft Purview oferuje następujące rozwiązania do zapewniania zgodności, które ułatwiają organizacji zarządzanie ryzykiem i wymaganiami dotyczącymi zgodności danych:

- [Zarządzanie ryzykiem wewnętrznym](#detect-and-act-on-risk-activities-with-insider-risk-management)
- [Zgodność w komunikacji](#detect-and-act-on-inappropriate-and-sensitive-messages-with-communication-compliance)
- [Bariery informacyjne](#restrict-communication-and-collaboration-between-users-with-information-barriers)
- [Zarządzanie rekordami](#manage-business-legal-or-regulatory-record-keeping-requirements-with-records-management)
- [Inspekcja (Premium) i inspekcja (standardowa)](#log-and-search-for-audited-activities-in-sharepoint-and-onedrive-with-audit-premium-or-audit-standard)
- [eDiscovery (Premium) i eDiscovery (Standard)](#identify-and-manage-data-for-legal-cases-with-ediscovery-premium-or-ediscovery-standard)

### <a name="detect-and-act-on-risk-activities-with-insider-risk-management"></a>Wykrywanie działań związanych z ryzykiem i reagowanie na nie przy użyciu zarządzania ryzykiem wewnętrznym

[Zarządzanie ryzykiem wewnętrznym w Microsoft Purview](/microsoft-365/compliance/insider-risk-management) korzysta z pełnego zakresu wskaźników usługi i innych firm, aby ułatwić szybkie identyfikowanie, klasyfikowanie i działanie na ryzykownych działaniach użytkowników w organizacji. Dzięki użyciu dzienników z platformy Microsoft 365 i programu Microsoft Graph zarządzanie ryzykiem wewnętrznym umożliwia definiowanie określonych zasad w celu identyfikowania wskaźników ryzyka. Po zidentyfikowaniu ryzykownych działań można podjąć działania w celu ograniczenia tych zagrożeń.

### <a name="detect-and-act-on-inappropriate-and-sensitive-messages-with-communication-compliance"></a>Wykrywanie i działanie na nieodpowiednich i poufnych komunikatach ze zgodnością z komunikacją

Ochrona poufnych informacji oraz wykrywanie i działanie w przypadku przypadków molestowania w miejscu pracy jest ważnym elementem zgodności z wewnętrznymi zasadami i standardami. [Zgodność w komunikacji w Microsoft Purview](/microsoft-365/compliance/communication-compliance-policies) pomaga zminimalizować te zagrożenia, pomagając szybko wykrywać, przechwytywać i podejmować działania korygowania dotyczące poczty e-mail i komunikacji w usłudze Microsoft Teams. Obejmują one niewłaściwą komunikację zawierającą wulgaryzmy, groźby oraz nękanie i komunikację, które udostępniają poufne informacje wewnątrz organizacji i poza nią.

### <a name="restrict-communication-and-collaboration-between-users-with-information-barriers"></a>Ograniczanie komunikacji i współpracy między użytkownikami przy użyciu barier informacyjnych

[Microsoft Purview Information Barriers (IB)](/microsoft-365/compliance/information-barriers) to rozwiązanie do zapewniania zgodności, które umożliwia ograniczenie dwukierunkowej komunikacji i współpracy między grupami i użytkownikami w usługach Microsoft Teams, SharePoint Online i OneDrive dla Firm. Często używane w wysoce regulowanych branżach, IB może pomóc uniknąć konfliktów interesów i chronić informacje wewnętrzne między użytkownikami a obszarami organizacyjnymi.

### <a name="manage-business-legal-or-regulatory-record-keeping-requirements-with-records-management"></a>Zarządzanie wymaganiami dotyczącymi prowadzenia dokumentacji biznesowej, prawnej lub regulacyjnej przy użyciu zarządzania rekordami

[Zarządzanie rekordami w Microsoft Purview](/microsoft-365/compliance/manage-data-governance#microsoft-purview-records-management) pomaga organizacji zarządzać swoimi zobowiązaniami prawnymi, umożliwia demonstrowanie zgodności z przepisami i zwiększa wydajność przy regularnym rozporządzaniu elementami, które nie są już wymagane do przechowywania, nie mają już wartości lub nie są już wymagane do celów biznesowych. Aby uzyskać więcej informacji, zobacz [Informacje o zarządzaniu rekordami](/microsoft-365/compliance/records-management).

### <a name="log-and-search-for-audited-activities-in-sharepoint-and-onedrive-with-audit-premium-or-audit-standard"></a>Rejestrowanie i wyszukiwanie inspekcji działań w programach SharePoint i OneDrive za pomocą inspekcji (Premium) lub Inspekcji (Standardowa)

[Rozwiązania do inspekcji usługi Microsoft Purview](/microsoft-365/compliance/auditing-solutions-overview) zapewniają zintegrowane rozwiązania ułatwiające organizacjom skuteczne reagowanie na zdarzenia zabezpieczeń, badania kryminalistyczne, dochodzenia wewnętrzne i obowiązki w zakresie zgodności. Tysiące operacji użytkowników i administratorów wykonywanych w dziesiątkach usług i rozwiązań platformy Microsoft 365 jest przechwytywanych, rejestrowanych i przechowywanych w ujednoliconym dzienniku inspekcji organizacji. Rekordy inspekcji dla tych zdarzeń można przeszukiwać za pomocą operacji zabezpieczeń, administratorów IT, zespołów ds. ryzyka dotyczącego informacji poufnych oraz badaczy zgodności i prawnych w organizacji. Ta funkcja zapewnia wgląd w działania wykonywane w organizacji platformy Microsoft 365.

Aby uzyskać więcej informacji na temat rozwiązań do inspekcji, zobacz [Audit (Premium)](/microsoft-365/compliance/advanced-audit) and [Audit (Standard)](/microsoft-365/compliance/set-up-basic-audit).

### <a name="identify-and-manage-data-for-legal-cases-with-ediscovery-premium-or-ediscovery-standard"></a>Identyfikowanie danych w sprawach prawnych i zarządzanie nimi za pomocą zbierania elektronicznych materiałów dowodowych (Premium) lub eDiscovery (Standard)

Odnajdywanie elektroniczne to proces identyfikowania, zbierania i inspekcji informacji elektronicznych ze względów prawnych, regulacyjnych lub biznesowych. Za pomocą [rozwiązań Zbieranie elektronicznych materiałów dowodowych w Microsoft Purview](/microsoft-365/compliance/ediscovery) można wyszukiwać dane i zawartość w Exchange Online, OneDrive dla Firm, SharePoint Online, Microsoft Teams, Grupy Microsoft 365 i zespoły usługi Yammer. Możesz wyszukać skrzynki pocztowe i witryny w tym samym wyszukiwaniu zbierania elektronicznych materiałów dowodowych, a następnie wyeksportować wyniki wyszukiwania do analizy i przeglądu.

Aby uzyskać więcej informacji na temat rozwiązań zbierania elektronicznych materiałów dowodowych, zobacz [eDiscovery (Premium)](/microsoft-365/compliance/overview-ediscovery-20) i [eDiscovery (Standard)](/microsoft-365/compliance/get-started-core-ediscovery).

## <a name="get-started-with-regulatory-compliance"></a>Wprowadzenie do zgodności z przepisami

Organizacje muszą przestrzegać złożonej i rozwijającej się sieci zasad, standardów branżowych i przepisów regionalnych, a także radzić sobie z rosnącymi kosztami potencjalnej niezgodności. W rzeczywistości istnieją setki aktualizacji dziennie od tysięcy organów regulacyjnych, co utrudnia aktualizowanie szybko zmieniającego się krajobrazu zgodności. Program Microsoft Purview Compliance Manager i szczegółowa kolekcja ofert zgodności mogą pomóc organizacji w zarządzaniu tymi wymaganiami prawnymi.

### <a name="get-started-with-compliance-manager"></a>Wprowadzenie do Menedżera zgodności

[Microsoft Purview Compliance Manager](/microsoft-365/compliance/compliance-manager) to funkcja w portal zgodności Microsoft Purview, która ułatwia zarządzanie wymaganiami organizacji dotyczącymi zgodności z większą łatwością i wygodą. Menedżer zgodności może pomóc w całym procesie zapewniania zgodności, od tworzenia spisu zagrożeń związanych z ochroną danych po zarządzanie złożonością wdrażania mechanizmów kontroli, zachowanie aktualności z przepisami i certyfikatami oraz raportowanie do audytorów.

### <a name="learn-about-microsoft-regulatory-compliance-offerings"></a>Dowiedz się o ofercie firmy Microsoft w zakresie zgodności z przepisami

Firma Microsoft oferuje kompleksowy zestaw [ofert zgodności](/compliance/regulatory/offering-home) , które pomogą Twojej organizacji spełnić krajowe, regionalne, międzynarodowe i branżowe wymagania dotyczące gromadzenia i wykorzystywania danych.

## <a name="deploy-purview-compliance-solutions"></a>Wdrażanie rozwiązań do zapewniania zgodności w usłudze Purview

Rozwiązania specyficzne dla obszaru zawierają wskazówki techniczne potrzebne do zrozumienia, zaplanowania i zaimplementowania zintegrowanych rozwiązań zgodności w celu zapewnienia bezpiecznej i zgodnej współpracy danych:

- [Zabezpieczanie danych przy użyciu modelu Zero Trust](/security/zero-trust/deploy/data)
- [Wdrażanie rozwiązania do ochrony informacji](/microsoft-365/compliance/information-protection-solution)
- [Wdrażanie rozwiązania do zarządzania danymi](/microsoft-365/compliance/data-governance-solution)
- [Wdrażanie ochrony informacji na potrzeby przepisów dotyczących prywatności danych](/microsoft-365/solutions/information-protection-deploy)
- [Zapoznaj się z ilustracjami dotyczącymi zgodności & ochrony informacji](/microsoft-365/solutions/productivity-illustrations)

## <a name="next-steps-for-organizations-new-to-risk-and-compliance-solutions"></a>Następne kroki dla nowych organizacji w zakresie rozwiązań dotyczących ryzyka i zgodności

- [Dowiedz się więcej o wersji próbnej rozwiązania Microsoft Purview](/microsoft-365/compliance/compliance-easy-trials)
- [Szybkie zadania umożliwiające rozpoczęcie pracy ze zgodnością w usłudze Microsoft Purview](/microsoft-365/compliance/compliance-quick-tasks)
