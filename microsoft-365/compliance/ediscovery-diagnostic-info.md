---
title: Zbieranie informacji diagnostycznych zbierania elektronicznych materiałów dowodowych
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Dowiedz się, jak zbierać informacje diagnostyczne zbierania elektronicznych materiałów dowodowych dla sprawy pomocy technicznej firmy Microsoft.
ms.openlocfilehash: cab21c71168119b27a478b99a19ad5693ffb678e
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021164"
---
# <a name="collect-ediscovery-diagnostic-information"></a>Zbieranie informacji diagnostycznych zbierania elektronicznych materiałów dowodowych

Czasami inżynierowie pomocy technicznej firmy Microsoft wymagają szczegółowych informacji o problemie podczas otwierania sprawy pomocy technicznej związanej z core eDiscovery lub Advanced eDiscovery. Ten artykuł zawiera wskazówki dotyczące zbierania informacji diagnostycznych, które ułatwiają inżynierom pomocy technicznej w zbadaniu i rozwiązaniu problemów. Zazwyczaj nie musisz zbierać tych informacji, dopóki nie poprosi o to inżynier pomocy technicznej firmy Microsoft.

> [!IMPORTANT]
> Dane wyjściowe z polecenia cmdlet i informacji diagnostycznych opisanych w tym artykule mogą zawierać informacje poufne dotyczące sporu sądowego lub dochodzenia wewnętrznego w organizacji. Przed wysłaniem nieprzetworzonych informacji diagnostycznych do pomocy technicznej firmy Microsoft należy przejrzeć te informacje i ponownie przejrzeć wszelkie poufne informacje (na przykład nazwiska lub inne informacje na temat stron sporu sądowego lub śledztwa), `XXXXXXX`zastępując je . Zastosowanie tej metody będzie również wskazywać inżynierowi pomocy technicznej firmy Microsoft, że informacje były redagowane.

## <a name="collect-diagnostic-information-for-core-ediscovery"></a>Zbieranie informacji diagnostycznych na temat podstawowych zbierania elektronicznych materiałów dowodowych

Zbieranie informacji diagnostycznych na temat zbierania elektronicznych materiałów dowodowych jest oparte na poleceniach cmdlet, więc musisz użyć programu PowerShell w centrum zabezpieczeń & zgodności. Poniższe przykłady programu PowerShell zawierają polecenia cmdlet, a następnie zapisują dane wyjściowe w określonym pliku tekstowym. W większości przypadków pomocy technicznej wystarczy uruchomić tylko jedno z tych poleceń.

Aby uruchomić następujące polecenia cmdlet, połącz [się z programem PowerShell w & zabezpieczeń i zgodności</span>](/powershell/exchange/connect-to-scc-powershell). Po na połączeniu uruchom jedno lub więcej z poniższych poleceń i zastąp symbole zastępcze rzeczywistymi nazwami obiektów.

Po przejrzeniu wygenerowanego pliku tekstowego i redagowania informacji poufnych wyślij go do inżyniera pomocy technicznej firmy Microsoft pracującego nad sprawą.

> [!NOTE]
> Polecenia zawarte w tej sekcji można także uruchomić w celu zbierania informacji diagnostycznych dotyczących wyszukiwań i eksportów wymienionych na  stronie Przeszukiwanie zawartości w Centrum zgodności platformy Microsoft 365.

### <a name="collect-information-about-searches"></a>Zbieranie informacji o wyszukiwaniach

Poniższe polecenie zbiera informacje, które są przydatne podczas badania problemów z wyszukiwaniem zawartości lub wyszukiwaniem skojarzonym z podstawową sprawą zbierania elektronicznych materiałów dowodowych.

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Zbieranie informacji o akcjach wyszukiwania

Poniższe polecenie zbiera informacje w celu zbadania problemów dotyczących wyświetlania podglądu, eksportowania lub przeczyszczania wyników wyszukiwania zawartości lub wyszukiwania skojarzonego ze sprawą core eDiscovery. Nazwę akcji wyszukiwania można określić, klikając eksport wymieniony na karcie **Eksporty** . Aby zidentyfikować nazwy akcji podglądu i przeczyszczania, możesz uruchomić polecenie cmdlet **Get-ComplianceSearchAction** w celu wyświetlenia listy wszystkich akcji. Format nazwy akcji wyszukiwania jest tworzony na przykład przez dołączenie `_Preview``_Export``_Purge` lub nazwy odpowiadającej jej nazwy.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>Zbieranie informacji o zbierania elektronicznych materiałów dowodowych

Jeśli hold eDiscovery associated with a Core eDiscovery case isn't functioning as expected, run the following command to collect information about the Case Hold Policy and associated Case Hold Rule for the eDiscovery hold. Nazwa *zasad przechowywania sprawy w następującym* poleceniu jest taka sama jak nazwa przechowywania zbierania elektronicznych materiałów dowodowych. Możesz określić tę nazwę na kartach **Zarchiwniaki** w podstawowej sprawie zbierania elektronicznych materiałów dowodowych.

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Zbierz wszystkie informacje o sprawy

Czasami nie wiadomo, jakie informacje są wymagane przez pomoc techniczną firmy Microsoft do zbadania problemu. W takiej sytuacji możesz zebrać wszystkie informacje diagnostyczne dla podstawowej sprawy zbierania elektronicznych materiałów dowodowych. Nazwa *sprawy core eDiscovery* w następującym poleceniu jest taka sama jak nazwa sprawy wyświetlanej na stronie Podstawowe sprawy zbierania elektronicznych  materiałów dowodowych w Centrum zgodności platformy Microsoft 365.

```powershell
Get-ComplianceCase "<Core eDiscovery case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-advanced-ediscovery"></a>Zbieranie informacji diagnostycznych dla Advanced eDiscovery

Karta **Ustawienia** w przypadku Advanced eDiscovery umożliwia szybkie skopiowanie informacji diagnostycznych dotyczących sprawy. Informacje diagnostyczne są zapisywane w schowku, dzięki czemu można je wkleić do pliku tekstowego i wysłać do pomocy technicznej firmy Microsoft.

1. Przejdź do Centrum zgodności platformy Microsoft 365 i wybierz **pozycję eDiscoveryAdvanced** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

2. Zaznacz sprawę, a następnie kliknij **kartę Ustawienia** sprawy.

3. W **obszarze Informacje o przypadku** kliknij przycisk **Wybierz**.

4. Na stronie wysuwu kliknij pozycję **AkcjeKopiowanie**  >  informacji o pomocy technicznej, aby skopiować informacje do schowka.

5. Otwórz plik tekstowy (w programie Notatnik), a następnie wklej informacje z tego pliku.

6. Zapisz plik tekstowy i nadaj plikowi `AeD Diagnostic Info YYYY.MM.DD` nazwę w podobny sposób `AeD Diagnostic Info 2020.11.03`(na przykład ).

Po przejrzeniu pliku i redagowania informacji poufnych wyślij go do inżyniera pomocy technicznej firmy Microsoft pracującego nad sprawą.
