---
title: Raporty i rozwiązywanie problemów dotyczących programu Microsoft Defender dla reguł ASR punktu końcowego
description: W tym temacie opisano, jak raportować reguły ASR punktu końcowego i rozwiązywać problemy z programem Microsoft Defender
keywords: Reguły zmniejszania powierzchni ataków, asr, hips, host intrusion prevention system, protection rules, anti-exploit, antiexploit, exploit, prevention, microsoft defender for endpoint
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 63c23b0ab0188abe0fb33d27789a437e1e445a2b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998111"
---
# <a name="report-and-troubleshoot-microsoft-defender-for-endpoint-asr-rules"></a>Raporty i rozwiązywanie problemów dotyczących programu Microsoft Defender dla reguł ASR punktu końcowego

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Dotyczy:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Portal <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> to nowy interfejs do monitorowania zabezpieczeń tożsamości, danych, urządzeń, aplikacji i infrastruktury firmy Microsoft i zarządzania nimi. Tutaj możesz łatwo wyświetlać kondycję zabezpieczeń organizacji, działać na urządzeniach, użytkownikach i aplikacjach oraz wyświetlać alerty o podejrzanych działaniach. Portal Microsoft 365 Defender jest przeznaczony dla administratorów zabezpieczeń i zespołów ds. operacji zabezpieczeń, w celu lepszego zarządzania ich organizacją i ochrony. Odwiedź Microsoft 365 Defender witryny<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

W <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> portalu oferujemy pełny wygląd bieżących reguł asr i zdarzeń w Twoim miejscu. Pamiętaj, że te raporty muszą być wypełnione w usłudze Microsoft Defender for Endpoint, która musi być wnosowana do usługi Microsoft Defender for Endpoint.
Oto zrzut ekranu z portalu Microsoft 365 Defender (w obszarze Zmniejszenie **obszarze** \>  \> **ataków urządzeń raportów**). Na poziomie urządzenia wybierz pozycję **Konfiguracja w** **okienku reguł zmniejszania powierzchni ataków** . Zostanie wyświetlony poniższy ekran, na którym możesz wybrać określone urządzenie i sprawdzić jego konfigurację reguł ASR.

:::image type="content" source="images/asrrulesnew.png" lightbox="images/asrrulesnew.png" alt-text="Ekran reguł asr.":::

## <a name="microsoft-defender-for-endpoint---advanced-hunting"></a>Program Microsoft Defender dla punktu końcowego — szukanie zaawansowane

Jedną z najbardziej zaawansowanych funkcji programu Microsoft Defender for Endpoint jest zaawansowane szukanie. Jeśli nie wiesz, jak działa zaawansowane szukanie, możesz aktywnie poszukać zagrożeń [, gdy gonisz](advanced-hunting-overview.md).

Szukanie zaawansowane to oparte na zapytaniach (Język Kusto Query) narzędzie do wyszukiwania zagrożeń, które pozwala eksplorować nawet 30 dni przechwyconych (nieprzetworzonych) danych, które program Defender for Endpoint zbiera z Twoich urządzeń. W ramach zaawansowanego wyszukiwania możesz aktywnie sprawdzać zdarzenia, aby znaleźć interesujące wskaźniki i jednostki. Elastyczny dostęp do danych pomaga bez przeszkolenia w zakresie ochrony przed znanymi i potencjalnymi zagrożeniami.

Dzięki zaawansowanej czacie można wyodrębniać informacje reguł asr, tworzyć raporty i uzyskać szczegółowe informacje na temat kontekstu danej inspekcji reguły asr lub blokowania zdarzenia.

Zdarzenia reguł ASR są dostępne do zapytania z tabeli DeviceEvents w sekcji zaawansowanego wyszukiwania w Microsoft 365 Defender. Na przykład proste zapytanie, takie jak poniższe, może raportować wszystkie zdarzenia, dla których jako źródło danych są używane reguły ASR z ostatnich 30 dni i podsumowuje je przez liczbę Akcji, że w tym przypadku będzie to rzeczywista nazwa kodowa reguły ASR.

:::image type="content" source="images/adv-hunt-querynew.png" alt-text="Zaawansowane zapytanie myśliwskie.":::

:::image type="content" source="images/adv-hunt-sc-2new.png" lightbox="images/adv-hunt-sc-2new.png" alt-text="zaawansowany ekran wyszukiwania.":::

Zaawansowane wyszukiwania mogą kształtować zapytania tak, aby można było zobaczyć, co się dzieje, niezależnie od tego, czy chcesz przypinać coś na poszczególnych komputerach, czy też chcesz wyodrębnić wnioski z całego środowiska.

## <a name="microsoft-defender-for-endpoint-machine-timeline"></a>Oś czasu komputera programu Microsoft Defender dla punktu końcowego

Alternatywą dla zaawansowanego wyszukiwania, ale o węższym zakresie, jest oś czasu maszynowego programu Microsoft Defender for Endpoint. Możesz wyświetlić wszystkie zdarzenia zebrane przez urządzenie z ostatnich sześciu miesięcy na Microsoft 365 Defender, przechodząc do listy Komputery, wybierz dany komputer, a następnie kliknij kartę Oś czasu.

Poniższy obraz przedstawia zrzut ekranu przedstawiający widok osi czasu tych zdarzeń dla danego punktu końcowego. W tym widoku możesz filtrować listę zdarzeń według dowolnej grupy zdarzeń w okienku po prawej stronie. Możesz również włączyć lub wyłączyć zdarzenia oflagowane i pełne podczas wyświetlania alertów i przewijania historycznej osi czasu.

:::image type="content" source="images/mic-sec-def-timelinenew.png" lightbox="images/mic-sec-def-timelinenew.png" alt-text="Microsoft 365 Defender osi czasu.":::

## <a name="how-to-troubleshoot-asr-rules"></a>Jak rozwiązywać problemy z regułami asr?

Pierwszym i najbardziej natychmiastowym sposobem jest sprawdzenie lokalnie na urządzeniu z systemem Windows, na którym są włączone reguły asr (i ich konfiguracja) za pomocą poleceń cmdlet programu PowerShell.

Oto kilka innych źródeł informacji, które można Windows, aby rozwiązać problemy z działaniem i działaniem reguł ASR.

### <a name="querying-which-rules-are-active"></a>Kwerenda, które reguły są aktywne

Jednym z najłatwiejszych sposobów określenia, czy reguły ASR są już włączone, jest polecenie cmdlet programu PowerShell, Get-MpPreference.

Oto przykład:

:::image type="content" source="images/getmpreferencescriptnew.png" lightbox="images/getmpreferencescriptnew.png" alt-text="pobierz skrypt mppreference.":::

Istnieje wiele aktywnych reguł asr z różnymi skonfigurowanymi akcjami.

Aby rozwinąć powyższe informacje dotyczące reguł ASR, możesz użyć właściwości **AttackSurfaceReductionRules_Ids i/** lub **AttackSurfaceReductionRules_Actions**.

Przykład:

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Ids
```

:::image type="content" source="images/getmpref-examplenew.png" alt-text="Uzyskaj przykład mpreference.":::

Powyżej przedstawiono wszystkie identyfikatory reguł ASR, dla których ustawienie jest inne niż 0 (Nieskonfigurowane).

Następnym krokiem jest wówczas lista rzeczywistych akcji (blokowania lub inspekcji), w których skonfigurowano każdą regułę.

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Actions
```

:::image type="content" source="images/getmpref-example2new.png" alt-text="pobierz mppreference example2.":::

### <a name="querying-blocking-and-auditing-events"></a>Blokowanie zapytań i inspekcja zdarzeń

Zdarzenia reguły ASR można wyświetlać w Windows Defender dziennika.

Aby uzyskać do niego dostęp, otwórz Windows Podgląd zdarzeń i przejdź do strony Dzienniki  aplikacji i usług,  \>  \> \> Windows **Windows Defender** \> **operacyjne.**

:::image type="content" source="images/eventviewerscrnew.png" lightbox="images/eventviewerscrnew.png" alt-text="Scr w podglądzie zdarzeń.":::

## <a name="microsoft-defender-antimalware-protection-logs"></a>Dzienniki ochrony przed złośliwym oprogramowaniem programu Microsoft Defender

Zdarzenia reguł można także wyświetlać za pomocą dedykowanego narzędzia wiersza Program antywirusowy Microsoft Defender, `*mpcmdrun.exe*`nazywanego , które może służyć do zarządzania i konfigurowania zadań oraz automatyzowania ich w razie potrzeby.

To narzędzie można znaleźć w *folderze %ProgramFiles%\Windows Defender\MpCmdRun.exe*. Należy go uruchomić z poziomu wiersza polecenia z podwyższonym poziomem uprawnień (który oznacza uruchomienie jako administrator).

Aby wygenerować informacje o pomocy technicznej, wpisz *MpCmdRun.exe -getfiles*. Po chwili kilka dzienników zostanie spakowane do archiwum (MpSupportFiles.cab) i udostępnione w folderze *C:\ProgramData\Microsoft\Windows Defender\Support*.

:::image type="content" source="images/malware-prot-logsnew.png" alt-text="dzienniki ochrony przed złośliwym oprogramowaniem.":::

Wyodrębnij to archiwum, a będziesz mieć wiele plików dostępnych na potrzeby rozwiązywania problemów.

Najbardziej odpowiednie pliki są następujące:

- **MPOperationalEvents.txt**: Ten plik zawiera taki sam poziom informacji, jak w podglądzie zdarzeń Windows Defender dziennik operacyjny użytkownika.
- **MPRegistry.txt**: W tym pliku możesz analizować wszystkie bieżące Windows Defender konfiguracji od momentu przechwycenia dzienników pomocy technicznej.
- **MPLog.txt**: Ten dziennik zawiera bardziej szczegółowe informacje o wszystkich akcjach/operacjach Windows Defender.
