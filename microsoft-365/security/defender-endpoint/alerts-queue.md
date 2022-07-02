---
title: Wyświetlanie i organizowanie kolejki alertów Ochrona punktu końcowego w usłudze Microsoft Defender
description: Dowiedz się, jak działają kolejki alertów Ochrona punktu końcowego w usłudze Microsoft Defender oraz jak sortować i filtrować listy alertów.
keywords: alerty, kolejki, kolejka alertów, sortowanie, kolejność, filtrowanie, zarządzanie alertami, nowe, w toku, rozwiązane, najnowsze, czas w kolejce, ważność, okres, alerty ekspertów od zagrożeń firmy Microsoft
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
ms.topic: article
ms.date: 03/27/2020
ms.technology: mde
ms.openlocfilehash: 13959666f0c44f83fcb938db010ed30d5e5056b4
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607537"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Wyświetlanie i organizowanie kolejki alertów Ochrona punktu końcowego w usłudze Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**
- [Ochrona punktu końcowego w usłudze Microsoft Defender (plan 2)](https://go.microsoft.com/fwlink/?linkid=2154037) 

> Chcesz poznać usługę ochrony punktu końcowego w usłudze Microsoft Defender? [Utwórz konto, aby skorzystać z bezpłatnej wersji próbnej.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

**Kolejka Alerty** zawiera listę alertów, które zostały oflagowane z urządzeń w sieci. Domyślnie kolejka wyświetla alerty widoczne w ciągu ostatnich 30 dni w widoku zgrupowanym. Najnowsze alerty są wyświetlane w górnej części listy, co ułatwia wyświetlanie najnowszych alertów w pierwszej kolejności.

> [!NOTE]
> Alerty są znacznie ograniczone dzięki zautomatyzowanemu badaniu i korygowaniu, dzięki czemu eksperci ds. operacji zabezpieczeń mogą skupić się na bardziej zaawansowanych zagrożeniach i innych inicjatywach o wysokiej wartości. Jeśli alert zawiera obsługiwaną jednostkę do automatycznego badania (na przykład pliku) na urządzeniu z obsługiwanym systemem operacyjnym, można rozpocząć zautomatyzowane badanie i korygowanie. Aby uzyskać więcej informacji na temat zautomatyzowanych badań, zobacz [Omówienie zautomatyzowanych dochodzeń](automated-investigations.md).

Istnieje kilka opcji, które można wybrać, aby dostosować widok alertów.

Na górnym pasku nawigacyjnym można:

- Dostosowywanie kolumn w celu dodawania lub usuwania kolumn
- Stosowanie filtrów
- Wyświetl alerty dla określonego czasu trwania, takiego jak 1 dzień, 3 dni, 1 tydzień, 30 dni i 6 miesięcy
- Eksportowanie listy alertów do programu Excel
- Zarządzanie alertami

:::image type="content" source="images/alerts-queue-list.png" alt-text="Strona kolejki alertów" lightbox="images/alerts-queue-list.png":::

## <a name="sort-and-filter-alerts"></a>Sortowanie i filtrowanie alertów 

Możesz zastosować następujące filtry, aby ograniczyć listę alertów i uzyskać bardziej skoncentrowany widok alertów.

### <a name="severity"></a>Waga

Ważność alertu|Opis
---|---
High (Wysoki) <br> (Czerwony)|Alerty często spotykane związane z zaawansowanymi trwałymi zagrożeniami (APT). Te alerty wskazują na wysokie ryzyko ze względu na ważność szkód, jakie mogą wyrządzić urządzeniom. Oto kilka przykładów: działania narzędzi do kradzieży poświadczeń, działania wymuszające okup, które nie są skojarzone z żadną grupą, manipulowanie czujnikami zabezpieczeń lub złośliwe działania wskazujące na atak człowieka.
Średni <br> (Pomarańczowy)|Alerty z wykrywania punktów końcowych i reagowania na zachowania po naruszeniu zabezpieczeń, które mogą być częścią zaawansowanego trwałego zagrożenia (APT). Te zachowania obejmują obserwowane zachowania typowe dla etapów ataku, nietypową zmianę rejestru, wykonywanie podejrzanych plików itd. Chociaż niektóre z nich mogą być częścią testów bezpieczeństwa wewnętrznego, wymagają zbadania, ponieważ mogą być również częścią zaawansowanego ataku.
Niskie <br> (Żółty)|Alerty dotyczące zagrożeń związanych z powszechnym złośliwym oprogramowaniem. Na przykład narzędzia hack-tools, narzędzia hack innych niż złośliwe oprogramowanie, takie jak uruchamianie poleceń eksploracji, czyszczenie dzienników itp., które często nie wskazują na zaawansowane zagrożenie skierowane do organizacji. Może również pochodzić z izolowanego narzędzia do testowania zabezpieczeń przez użytkownika w organizacji.
Informacyjny <br> (Szary)|Alerty, które mogą nie być uważane za szkodliwe dla sieci, ale mogą prowadzić do świadomości zabezpieczeń organizacji w przypadku potencjalnych problemów z zabezpieczeniami.

#### <a name="understanding-alert-severity"></a>Informacje o ważności alertu

Ważność alertów programu antywirusowego Microsoft Defender (Microsoft Defender AV) i alertów usługi Defender for Endpoint jest różna, ponieważ reprezentują różne zakresy.

Ważność zagrożenia programu antywirusowego Microsoft Defender reprezentuje bezwzględną ważność wykrytego zagrożenia (złośliwego oprogramowania) i jest przypisywana na podstawie potencjalnego ryzyka dla poszczególnych urządzeń, jeśli zostanie zainfekowane.

Ważność alertu usługi Defender for Endpoint reprezentuje ważność wykrytego zachowania, rzeczywiste ryzyko dla urządzenia, ale co ważniejsze potencjalne zagrożenie dla organizacji.

Tak więc, na przykład:

- Ważność alertu usługi Defender for Endpoint dotyczącego programu antywirusowego Microsoft Defender wykryła zagrożenie, które zostało uniemożliwione i nie zainfekowało urządzenia, jest klasyfikowane jako "Informacyjne", ponieważ nie wystąpiło żadne rzeczywiste uszkodzenie.
- Alert dotyczący komercyjnego złośliwego oprogramowania został wykryty podczas wykonywania, ale zablokowany i skorygowany przez usługę Microsoft Defender AV, jest skategoryzowany jako "niski", ponieważ mógł spowodować pewne uszkodzenie poszczególnych urządzeń, ale nie stanowi zagrożenia organizacyjnego.
- Alert dotyczący wykrytego złośliwego oprogramowania podczas wykonywania, który może stanowić zagrożenie nie tylko dla poszczególnych urządzeń, ale także dla organizacji, niezależnie od tego, czy zostało ostatecznie zablokowane, może zostać sklasyfikowany jako "Średni" lub "Wysoki".
- Podejrzane alerty behawioralne, które nie zostały zablokowane lub skorygowane, zostaną sklasyfikowane jako "Niskie", "Średnie" lub "Wysokie" zgodnie z tymi samymi zagadnieniami dotyczącymi zagrożeń organizacyjnych.

### <a name="status"></a>Stan

Możesz filtrować listę alertów na podstawie ich stanu.

> [!NOTE]
> Jeśli widzisz stan alertu *Nieobsługiwany typ alertu* , oznacza to, że funkcje zautomatyzowanego badania nie mogą odebrać tego alertu w celu uruchomienia zautomatyzowanego badania. Można jednak [zbadać te alerty ręcznie](../defender/investigate-incidents.md#alerts).

### <a name="categories"></a>Kategorie

Na nowo zdefiniowaliśmy kategorie alertów, aby dostosować się do [taktyki ataku przedsiębiorstwa](https://attack.mitre.org/tactics/enterprise/) w [macierzy MITRE ATT&CK](https://attack.mitre.org/). Nowe nazwy kategorii mają zastosowanie do wszystkich nowych alertów. Istniejące alerty zachowają nazwy poprzednich kategorii.

### <a name="service-sources"></a>Źródła usług

Microsoft Threat Experts wersji zapoznawczej uczestnicy mogą teraz filtrować i wyświetlać wykrycia z nowej usługi wyszukiwania zagrożeń zarządzanej przez ekspertów.

Filtruj alerty na podstawie następujących źródeł usług:

- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Ochrona punktu końcowego w usłudze Microsoft Defender
- Microsoft 365 Defender
- Ochrona usługi Office 365 w usłudze Microsoft Defender
- Zarządzanie aplikacjami
- Ochrona tożsamości usługi AAD

> [!NOTE]
> Filtr antywirusowy będzie wyświetlany tylko wtedy, gdy urządzenia używają programu antywirusowego Microsoft Defender jako domyślnego produktu ochrony przed złośliwym kodem w czasie rzeczywistym.

### <a name="tags"></a>Tagi

Alerty można filtrować na podstawie tagów przypisanych do alertów.

### <a name="policy"></a>Zasad 

Alerty można filtrować na podstawie następujących zasad:

|Źródło wykrywania|Wartość interfejsu API|
|---|---|
|Czujniki innych firm|ThirdPartySensors|
|Antivirus|WindowsDefenderAv|
|Zautomatyzowane badanie|AutomatedInvestigation|
|Wykrywanie niestandardowe|CustomDetection|
|Niestandardowy identyfikator TI|CustomerTI|
|EDR|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Ochrona usługi Office 365 w usłudze Microsoft Defender|OfficeATP|
|Microsoft Threat Experts|ThreatExperts|
|Filtr smartscreen|WindowsDefenderSmartScreen|

### <a name="entities"></a>Podmioty

Alerty można filtrować na podstawie nazwy jednostki lub identyfikatora. 

### <a name="automated-investigation-state"></a>Stan zautomatyzowanego badania

Alerty można filtrować na podstawie ich stanu zautomatyzowanego badania.



## <a name="related-topics"></a>Tematy pokrewne

- [Zarządzanie alertami Ochrona punktu końcowego w usłudze Microsoft Defender](manage-alerts.md)
- [Badanie alertów Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-alerts.md)
- [Badanie pliku skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-files.md)
- [Badanie urządzeń na liście urządzeń Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-machines.md)
- [Badanie adresu IP skojarzonego z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-ip.md)
- [Badanie domeny skojarzonej z alertem Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-domain.md)
- [Badanie konta użytkownika w Ochrona punktu końcowego w usłudze Microsoft Defender](investigate-user.md)
