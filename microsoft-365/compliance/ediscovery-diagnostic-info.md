---
title: Zbieraj informacje diagnostyczne dotyczące zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Dowiedz się, jak zbierać informacje diagnostyczne zbierania elektronicznych materiałów dowodowych dla pomoc techniczna firmy Microsoft przypadku.
ms.openlocfilehash: f5dba88a598a73441c67e3eaa08a59b7258ea712
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014437"
---
# <a name="collect-ediscovery-diagnostic-information"></a>Zbieraj informacje diagnostyczne dotyczące zbierania elektronicznych materiałów dowodowych

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Czasami inżynierowie pomoc techniczna firmy Microsoft wymagają konkretnych informacji o problemie podczas otwierania zgłoszenia do pomocy technicznej związanego zbierania elektronicznych materiałów dowodowych w usłudze Microsoft Purview (Standard) lub microsoft Purview eDiscovery (Premium). Ten artykuł zawiera wskazówki dotyczące gromadzenia informacji diagnostycznych, które ułatwiają inżynierom pomocy technicznej badanie i rozwiązywanie problemów. Zazwyczaj nie trzeba zbierać tych informacji, dopóki nie zostanie o to poproszony inżynier pomoc techniczna firmy Microsoft.

> [!IMPORTANT]
> Dane wyjściowe poleceń cmdlet i informacji diagnostycznych opisanych w tym artykule mogą zawierać poufne informacje na temat sporów sądowych lub wewnętrznych dochodzeń w organizacji. Przed wysłaniem nieprzetworzonych informacji diagnostycznych do pomoc techniczna firmy Microsoft należy przejrzeć informacje i zredagować wszelkie poufne informacje (takie jak nazwy lub inne informacje dotyczące stron sporu sądowego lub dochodzenia), zastępując je `XXXXXXX`. Użycie tej metody będzie również wskazywać inżynierowi pomoc techniczna firmy Microsoft, że informacje zostały zredagowane.

## <a name="collect-diagnostic-information-for-ediscovery-standard"></a>Zbieranie informacji diagnostycznych dotyczących zbierania elektronicznych materiałów dowodowych (standard)

Zbieranie informacji diagnostycznych dotyczących zbierania elektronicznych materiałów dowodowych (Standard) jest oparte na poleceniach cmdlet, dlatego należy użyć programu PowerShell security & Compliance. W poniższych przykładach programu PowerShell zostaną uruchomione polecenia cmdlet, a następnie zapiszą dane wyjściowe w określonym pliku tekstowym. W większości przypadków pomocy technicznej należy uruchomić tylko jedno z tych poleceń.

Aby uruchomić następujące polecenia cmdlet, [połącz się z programem PowerShell</span> Security & Compliance](/powershell/exchange/connect-to-scc-powershell). Po nawiązaniu połączenia uruchom co najmniej jedno z następujących poleceń i zastąp symbole zastępcze rzeczywistymi nazwami obiektów.

Po przejrzeniu wygenerowanego pliku tekstowego i zredagowaniu poufnych informacji wyślij go do inżyniera pomoc techniczna firmy Microsoft pracującego nad Twoją sprawą.

> [!NOTE]
> Możesz również uruchomić polecenia w tej sekcji, aby zebrać informacje diagnostyczne dotyczące wyszukiwań i eksportów wymienionych na stronie **wyszukiwania zawartości** w portalu zgodności usługi Microsoft Purview.

### <a name="collect-information-about-searches"></a>Zbieranie informacji o wyszukiwaniach

Poniższe polecenie zbiera informacje przydatne podczas badania problemów z wyszukiwaniem zawartości lub wyszukiwaniem skojarzonym ze sprawą zbierania elektronicznych materiałów dowodowych (Standardowa).

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Zbieranie informacji o akcjach wyszukiwania

Poniższe polecenie zbiera informacje w celu zbadania problemów z podglądem, eksportowaniem lub przeczyszczaniem wyników wyszukiwania zawartości lub wyszukiwania skojarzonego ze sprawą zbierania elektronicznych materiałów dowodowych (standardowa). Nazwę akcji wyszukiwania można zidentyfikować, klikając eksport wymieniony na **karcie Eksporty** . Aby zidentyfikować nazwy akcji podglądu i przeczyszczania, możesz uruchomić polecenie cmdlet **Get-ComplianceSearchAction** , aby wyświetlić listę wszystkich akcji. Format nazwy akcji wyszukiwania jest konstruowany przez dołączenie `_Preview`, `_Export`lub `_Purge` do nazwy odpowiedniego wyszukiwania.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>Zbieranie informacji o blokadach zbierania elektronicznych materiałów dowodowych

Jeśli blokada zbierania elektronicznych materiałów dowodowych skojarzona z przypadkiem zbierania elektronicznych materiałów dowodowych (w warstwie Standardowa) nie działa zgodnie z oczekiwaniami, uruchom następujące polecenie, aby zebrać informacje o zasadach blokady sprawy i skojarzonej regule blokady sprawy dla blokady zbierania elektronicznych materiałów dowodowych. *Nazwa zasad przechowywania przypadku* w poniższym poleceniu jest taka sama jak nazwa blokady zbierania elektronicznych materiałów dowodowych. Tę nazwę można zidentyfikować na kartach **Blokady** w przypadku zbierania elektronicznych materiałów dowodowych (Standardowa).

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Zbieranie wszystkich informacji o przypadku

Czasami nie jest jasne, jakie informacje są wymagane przez pomoc techniczna firmy Microsoft do zbadania problemu. W takiej sytuacji możesz zebrać wszystkie informacje diagnostyczne dla przypadku zbierania elektronicznych materiałów dowodowych (Standardowa). *Nazwa przypadku zbierania elektronicznych materiałów dowodowych (Standardowa)* w poniższym poleceniu jest taka sama jak nazwa przypadku wyświetlanego na stronie **eDiscovery (Standard)** w portalu zgodności.

```powershell
Get-ComplianceCase "<eDiscovery (Standard) case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-ediscovery-premium"></a>Zbieranie informacji diagnostycznych dotyczących zbierania elektronicznych materiałów dowodowych (Premium)

Karta **Ustawienia** w przypadku zbierania elektronicznych materiałów dowodowych (Premium) umożliwia szybkie skopiowanie informacji diagnostycznych dla sprawy. Informacje diagnostyczne są zapisywane w schowku, dzięki czemu można je wkleić do pliku tekstowego i wysłać do pomoc techniczna firmy Microsoft.

1. Przejdź do portalu zgodności i wybierz pozycję **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank">**Advanced**</a>.

2. Wybierz przypadek, a następnie kliknij kartę **Ustawienia**.

3. W obszarze **Informacje o wielkości liter** kliknij **pozycję Wybierz**.

4. Na stronie wysuwanej kliknij pozycję **Akcje** > **Kopiuj informacje o pomocy technicznej** , aby skopiować informacje do schowka.

5. Otwórz plik tekstowy (w Notatnik), a następnie wklej informacje w pliku tekstowym.

6. Zapisz plik tekstowy i nadaj mu nazwę podobną `AeD Diagnostic Info YYYY.MM.DD` (na przykład `AeD Diagnostic Info 2020.11.03`).

Po przejrzeniu pliku i zredagowaniu poufnych informacji wyślij go do inżyniera pomoc techniczna firmy Microsoft pracującego nad Twoją sprawą.
